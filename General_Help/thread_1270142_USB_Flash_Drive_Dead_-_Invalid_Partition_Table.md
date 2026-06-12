---
title: "USB Flash Drive Dead - Invalid Partition Table"
date: 2009-09-19
forum: General Help
---

### Post by ks07 on 2009-09-19
I haven't used my flash drive in a while, so when I plugged it into my PC today I was confused after it did not auto-mount the drive, trying to mount it from "Computer" failed with an error message. I also tried it in my XP install, but it failed also. Looking at it through fdisk gave me this output:
```
Disk /dev/sdg: 8 MB, 8388608 bytes
1 heads, 16 sectors/track, 1024 cylinders
Units = cylinders of 16 * 512 = 8192 bytes
Disk identifier: 0xce23f4e2

Disk /dev/sdg doesn't contain a valid partition table

```I have absolutely no idea what was on the drive (if anything) before it died, so I don't really care about data recovery. I would just simply re-format the drive, but if you look at the above code it shows only 8MB of capacity. Last time I checked, this drive was 128 MB (maybe 256, the numbers on the front have all been rubbed off XD). Any idea how to 'unlock' the remaining 120MB of space so I can reformat? Or is this just hardware failure?

EDIT: I have tried to fix the problem, but to no avail. I have:
-Tried to create a new partition table in gparted and cfdisk. Both failed. 
-Tried blanking the drive by writing 0s to the disk using dd. Appeared to work but gave some error messages and no change.

EDIT2: Have marked as solved, after trying to rewrite the partition table with various utilities I guess this stick is dead. Anyway, grabbed a new 2GB one.

---

