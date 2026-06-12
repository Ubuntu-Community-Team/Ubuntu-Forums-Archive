---
title: "cannot mount Win95 FAT32 imagefile for data recovery"
date: 2011-03-04
forum: General Help
---

### Post by 97wideglide on 2011-03-04
I am tryiing to recover data on an iPod Classic hard drive which will not sync anymore with iTunes.  I pulled the drive and connected it directly to the usb port on my Ubuntu system.  

I used ddrescue to image the drive and fdisk -l to try to understand where the partitions were.  I got the following:
-----------------------------------------------
Disk /dev/sdg: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xac8a13eb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   *           4        1217     9744203+   c  W95 FAT32 (LBA)
Partition 1 does not end on cylinder boundary.
/dev/sdg2               1           4       24576   3f  Unknown
Partition 2 does not end on cylinder boundary.

Partition table entries are not in disk order
--------------------------------------------------

Then I ran "mmls imagefile -b" on the image and got :

DOS Partition Table
Offset Sector: 0
Units are in 512-byte sectors

     Slot    Start        End          Length       Size    Description
00:  Meta    0000000000   0000000000   0000000001   0512B   Primary Table (#0)
01:  -----   0000000000   0000000062   0000000063   0031K   Unallocated
02:  00:01   0000000063   0000049214   0000049152   0024M   Unknown Type (0x3F)
03:  -----   0000049215   0000049277   0000000063   0031K   Unallocated
04:  00:00   0000049278   0019537684   0019488407   0009G   Win95 FAT32 (0x0C)
05:  -----   0019537685   0156301487   0136763803   0065G   Unallocated

So, to mount the Win95 FAT32 partition I used :

mount -t vfat -o loop,offset=25230336 imagefile /media/E

But I got the error, "mount: wrong fs type, bad option, bad superblock, ..."

Can anyone please tell me where I went wrong?

Thank you,
Curt

---

### Post by john_spiral on 2011-06-22
use the below command to see why the mount is failing:

dmesg |tail

---

