---
title: "External Hard Drive Won't Mount"
date: 2011-06-08
forum: General Help
---

### Post by mbusha on 2011-06-08
I recently wiped and re-installed Ubuntu on my system Lenovo Thinkpak T510, now running 11.04.  Before formatting my hard drive, I backed up all my information to an external USB Seagate FreeAgent Drive, which I reformatted to ext4 before copying my data there using a rsync command.  After reinalling the operating system, I'm no longer able to get the drive to mount.  I'm not quite sure what's going on.  Here are the results of a fdisk command:

```
$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5b247c03

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         154     1228800    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2             154        8184    64501150    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3            8184       59527   412412929    5  Extended
Partition 3 does not end on cylinder boundary.
/dev/sda4           59527       60802    10240000    7  HPFS/NTFS
Partition 4 does not end on cylinder boundary.
/dev/sda5           57612       59527    15382528   82  Linux swap / Solaris
/dev/sda6            8184       57612   397029376   83  Linux

Partition table entries are not in disk order

Disk /dev/dm-0: 15.8 GB, 15751708672 bytes
255 heads, 63 sectors/track, 1915 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8f6d4b2e

Disk /dev/dm-0 doesn't contain a valid partition table

Disk /dev/sdb: 2000.4 GB, 2000398933504 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004f7b0

   Device Boot      Start         End      Blocks   Id  System
$
```I'm not able to mount the drive from my mac either.  Did I do something wrong when backing up my data and loose everything (fortunately, most of it is also backed up elsewhere, just not all in a single place), or is there something else I can try to get it back?  Any help would be greatly appreciated.

---

### Post by blueridgedog on 2011-06-08
The system sees no partitions on sdb.  Apparently your mac also fails to see any partitions.  I would run testdisk and see if it sees partitions that were deleted.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

You can either install it or run it from a boot image.

---

### Post by mbusha on 2011-06-08
Thanks.  It looks like TestDisk didn't find any partitions either, so I'm guessing I'm out of luck :(

---

