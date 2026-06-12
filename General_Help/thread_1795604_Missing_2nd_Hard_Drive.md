---
title: "Missing 2nd Hard Drive"
date: 2011-07-03
forum: General Help
---

### Post by russellsteapot on 2011-07-03
The system monitor and file folders don't show that I have a second hard drive. I tried 
sudo fdisk -l
which gave me:


Disk /dev/sda: 115.0 GB, 115033153536 bytes
255 heads, 63 sectors/track, 13985 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ab4b9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12942   103949312   83  Linux
/dev/sda2           12942       13986     8385537    5  Extended
/dev/sda5           12942       13986     8385536   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ef078


so I know it's there. The question is how do I get it to show up?

---

### Post by TeoBigusGeekus on 2011-07-03
Have you mounted it?

---

### Post by prodigy_ on 2011-07-03
Your fdisk shows no partitions on /dev/sdb. Are you sure you partitioned it? If yes, try to re-check with **sudo parted -l** command.

Any disk must have a valid partition table with at least one partition. And any newly created partition must be formatted before you'll be able to use it.

---

