---
title: "3ware raid setup"
date: 2011-04-05
forum: General Help
---

### Post by oldfart101 on 2011-04-05
Newbie, so be gentle!
I have Ubuntu 10.10 Maverick Meerkat
Just installed 3ware 9650SE controller (8 port) with 6 x 2TB drives. The OS boots on a seperate drive. My intention is to run Freenas in VM player.
So far, I have initialised the disks (but I didn't carve them) and mounted to /media/raid
using```
mount /dev/sdb /media/raid ufs2
```fdisk -l
```
Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000677d5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6994    56174592   83  Linux
/dev/sda2            6994        7298     2438145    5  Extended
/dev/sda5            6994        7298     2438144   82  Linux swap / Solaris

Disk /dev/sdb: 9999.9 GB, 9999944253440 bytes
255 heads, 63 sectors/track, 1215757 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

```so, did I do the right thing in mounting to /media/raid
and
do I format, or get round the 'valid partition table' error.

---

