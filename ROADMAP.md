# ROADMAP

+ [ ] Rename
+ [ ] Normalize
+ [ ] XML
+ [ ] Priority

## Rename soundclips
This convention will be used: [Art File Naming Convention](https://trac.wildfiregames.com/wiki/ArtFileNamingConventions)

When renaming soundclips, **also** have to be changed:
+ **XML files** referencing them
+ **Templates**

## Normalize soundclips
> dBTP will be used, because RMS won't fit due to the short length and silences on soundclips

_The values are being tested_

| Sound type                  | Value (dBTP) 
| :-:                         | :-:          
| Alarms, notifications...    | -6
| Music                       | -8
| Units, resources, attack... | -12
| Ambient                     | -18

I would **not** use any compression, to maintain the more dynamic range on original sounds.

## Set XMLs properly
1. Remove unused parameters (`cone`, `threshold`...)
2. Set `Gain = 1`. Once having made this, we should start testing and redefining Gain for each clip/group
3. Set `Priority` parameter, according to these values:

        80: Environmental background sound (including on-screen non-periodic emitters like waterfalls and rivers)
        70: Unit and building selection and orders, UI interactions (confirmatory responses essential to gameplay)
        60: Alarms, notifications, and warnings (very useful, but not genuinely essential)
        50: Structure destruction/capture, unit deaths (important cues into the direction of the battle)
        40: General weapon sounds and impacts (nice 'window-dressing' but not completely essential)
        30: Gathering, building, and movement noises (non-essential)
        20: Incidental, periodic ambiance (a gust of wind, birds chirping by trees, etc.)

## Code Priority parameter

This parameter sets which sound have priority towards other, if all of them can not be played. This is not implemented on code (or we did not find it out).

## Code Threshold parameter

This parameter will be used to prevent too many sounds of the same time to be played at once.
