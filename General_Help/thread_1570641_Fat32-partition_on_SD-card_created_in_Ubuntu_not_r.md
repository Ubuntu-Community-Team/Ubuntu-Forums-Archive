---
title: "Fat32-partition on SD-card created in Ubuntu not recognized in Windows XP"
date: 2010-09-08
forum: General Help
---

### Post by Aybara on 2010-09-08
I've created 4-partitions on my micro-sd card. fat32,ext3,ext3,fat32, and my aim was to be able to read the fat32-partitions in WinXP. Sadly it says that the card is not formatted. fdisk gives the following output:

$ sudo fdisk -l /dev/sdb

Disk /dev/sdb: 16.0 GB, 16039018496 bytes
255 heads, 63 sectors/track, 1949 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1           9       72261    c  W95 FAT32 (LBA)
/dev/sdb2              10         140     1052257+  83  Linux
/dev/sdb3             141         271     1052257+  83  Linux
/dev/sdb4             272        1949    13478535    c  W95 FAT32 (LBA)

I tried skipping the ext3-partitions and use only fat32, but that didn't change anything.

Any ideas?

---

