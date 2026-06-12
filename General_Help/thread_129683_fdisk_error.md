---
title: "fdisk error"
date: 2006-02-14
forum: General Help
---

### Post by bigblop on 2006-02-14
I have just bought an used IBM T40 P.

I have made 2 NTFS partitions with the WinXP CD-ROM and leaved 6 GB unallocated space.

The I have formatted the second partition and installed WinXP on the first.

Afterwards I booted with the Ubuntu 5.10 CD and installed Ubuntu on the unallocated area. Installation worked fine an winXP was also added to the GRUB menu.

I can now both boot winXP and Ubuntu without any errors.

But When I type sudo fdisk -l in ubuntu I get this error:

Disk /dev/hda: 80.0 GB, 80026361856 bytes
16 heads, 63 sectors/track, 155061 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

Device Boot Start End Blocks Id System
/dev/hda1 1 60945 30716248+ 7 HPFS/NTFS
Partition 1 does not end on cylinder boundary.

/dev/hda2 60946 142832 41270985 f W95 Ext'd (LBA)
Partition 2 does not end on cylinder boundary.

/dev/hda3 * 142832 155056 6160927+ 83 Linux
Partition 3 does not end on cylinder boundary.

/dev/hda5 60946 142215 40960048+ 7 HPFS/NTFS
/dev/hda6 142227 142832 305203+ 82 Linux swap / Solaris


I have read through google that this should be considered a rather serious problem so I am kinda nervous that the laptop is defect.

If I try to start Partition Magic from winXP I get:

init failed error 117
partition drive letter cannot be identified


Does anyone know of a reason for these errors? I have heard about IBM having a hidden partition, maybe its this that Ubuntu cannot figure out?

Really hope someone can help!!

---

### Post by dcstar on 2006-02-14
[QUOTE=bigblop]I have just bought an used IBM T40 P.
.....
/dev/hda3 * 142832 155056 6160927+ 83 Linux
**Partition 3 does not end on cylinder boundary.**
.......
Does anyone know of a reason for these errors? I have heard about IBM having a hidden partition, maybe its this that Ubuntu cannot figure out?

Really hope someone can help!![/QUOTE]
Some OSs/utilities are fussy about where partitions begin and end, some others aren't.

The only issue is the one you have encountered, a utility don't like what works fine with something else and won't run!

---

