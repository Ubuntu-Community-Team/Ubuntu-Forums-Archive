---
title: "Trouble with windows"
date: 2010-12-07
forum: General Help
---

### Post by cheezburga on 2010-12-07
So recently my windows hard drive partion was getting rather full, i decided to move partitions around to give it more space, unfortunately a family member powered off my computer during the working time of the partitioning program, lucky me i have a dedicated linux mint back up hdd, any way here is the data as a result of "sudo fdisk -l" and "sudo blkid" really need the partitions from before the move and help on recovering partitons, i seem to be able to access the data on my original windows 7 hdd but anytime i try to boot it i get this error message "No such device:e81887a01887c7e
Invalid signature" any help would be greatly appreciated 
                                          - a rather novice linux user looking for help


Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytesDisk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005f31c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        6994    56174592   83  Linux
/dev/sda2            6994        7298     2438145    5  Extended
/dev/sda5            6994        7298     2438144   82  Linux swap / Solaris
Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4a7b4a7b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1           66541       90383   191518866    7  HPFS/NTFS
/dev/sdb2           57748       72729   120334882+   5  Extended

Partition table entries are not in disk order
miles@12verses ~ $ sudo blkid
/dev/sda1: UUID="3c7069f2-4579-4f45-90d3-d6ae6782143b" TYPE="ext4" 
/dev/sda5: UUID="ebe0581d-33dc-42fb-83ab-f5ee1cc6352b" TYPE="swap" 
/dev/sdb1: LABEL="Win 7 miles" UUID="01CA9478D7893400" TYPE="ntfs" 

Disk identifier: 0x0005f31c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        6994    56174592   83  Linux
/dev/sda2            6994        7298     2438145    5  Extended
/dev/sda5            6994        7298     2438144   82  Linux swap / Solaris
Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4a7b4a7b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1           66541       90383   191518866    7  HPFS/NTFS
/dev/sdb2           57748       72729   120334882+   5  Extended

Partition table entries are not in disk order
miles@12verses ~ $ sudo blkid
/dev/sda1: UUID="3c7069f2-4579-4f45-90d3-d6ae6782143b" TYPE="ext4" 
/dev/sda5: UUID="ebe0581d-33dc-42fb-83ab-f5ee1cc6352b" TYPE="swap" 
/dev/sdb1: LABEL="Win 7 miles" UUID="01CA9478D7893400" TYPE="ntfs"

---

