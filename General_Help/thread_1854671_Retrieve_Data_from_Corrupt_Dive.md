---
title: "Retrieve Data from Corrupt Dive"
date: 2011-10-04
forum: General Help
---

### Post by FraggedLocust on 2011-10-04
I have a USB drive from Western Digital that seems to have failed. I would like to try to retrieve any data I can from the dive before attempting a reformat. 

The drive is a WD MyBook. Plugging it in should mount two drives: a virtual CD partition and the data partition. In Ubuntu, the CD drive mounts properly, but the data partition fails because the same device attempts to mount twice to sr0/1. Or that's what Ubuntu tells me. But I can access the CD partition fine.

In Windows, however, the drive takes forever to mount the data partition, and I can see the CD partition fine as usual. Trying any program that will attempt to scan the drives (Partition software, undelete software) locks up the program until the drive is disconnected, at which point the computer returns to normal and launches or quits the program.

A similar effect is noticed when running GPartEd.

Is there any way to get such a drive to read properly to retrieve data?

---

### Post by mikewhatever on 2011-10-04
Try mounting the partition manually to a different mount point, for example to /mnt:
```
sudo mount /dev/sdXY /mnt
```

To figure out what the X and Y are, run **sudo fdisk -l** (<- that's small L, not one).

PS: From your description, the hard drive obviously hasn't failed, at least not yet.

---

### Post by FraggedLocust on 2011-10-07
```
Disk /dev/sdc: 499.4 GB, 499405291520 bytes
255 heads, 63 sectors/track, 60715 cylinders, total 975400960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000487a0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048   975400959   487699456    7  HPFS/NTFS/exFAT

```

Mounting /dev/sdc1 takes forever. I'll post when it's done.

---

