---
title: "totem could not read from resource"
date: 2010-01-27
forum: General Help
---

### Post by llawwehttam on 2010-01-27
I have a good dvd player and the ubuntu-restricted-extras libdvdread4 vlc css and totem-xine installed.

I can play a dvd but if I try to fast forward or rewind I get the error

"Could not read from resource"

In vlc the sound is also very jerky and I cannot fast forward or rewind either.

Any ideas?

EDIT: sorry about the typo in the title. It should say " totem Could not read from resource"

---

### Post by llawwehttam on 2010-01-27
Sorry about this, I should have done more testing before posting.

This problem is only with 1 dvd "stealth". Just tried Lord of the Rings and it was fine.

Bit strange, its nothing to do with regions as it is 'pal' and region 2 just like all my other movies. 

Windows 7 with power dvd can play it though on my sister's laptop ( I didn't tell her I was using it and I sort of had to steal it form under her bed LOL) .

Maybe just my laptop dvd drive not coping with it. Strange though, never seen this before.

EDIT: just tried that disk with MPlayer and I get the error 'seek failed!'

would like to get this disk working as well if possible.

VLC is still problematic with the audio though. It sounds like it plays the audio in 1 second 'chunks' with a little pause invbetween. Not sure how best to describe it. Movie plays fine though.

EDIT: VLC is doing this with all media including avi files , wmv files, dvd's , iso's , mpeg's .
Has anyone else experienced this prolem. I'm just interested to see if anyone's in the same boat.

---

### Post by llawwehttam on 2010-01-27
I'm starting to think its the disk. I just got this from gnomebaker:
```
Read  speed:  8310 kB/s (CD  47x, DVD  6x).
Write speed: 11080 kB/s (CD  62x, DVD  8x).
Capacity: 4169920 Blocks = 8339840 kBytes = 8144 MBytes = 8539 prMB
Sectorsize: 2048 Bytes
Copy from SCSI (4,0,0) disk to file '/home/llawwehttam/Videos/Movies/Stealth.iso'
end:   4169920
addr:        0 cnt: 64 Errno: 5 (Input/output error), read_g1 scsi sendcmd: no error
CDB:  28 00 00 04 1A 00 00 00 40 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 6F 03 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x6F Qual 0x03 (read of scrambled sector without authentication) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.044s timeout 40s
readom: Input/output error. Cannot read source disk
readom: Retrying from sector 268800.
..............................~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~
readom: Input/output error. Error on sector 268829 not corrected. Total of 1 errors.

Time total: 298.852sec
Read 537600.00 kB at 1798.9 kB/sec.
Max corected retry count was 0 (limited to 128).
The following 1 sector(s) could not be read correctly:
268829
```

Should I ask the store for a replacement as it is quite new?

---

