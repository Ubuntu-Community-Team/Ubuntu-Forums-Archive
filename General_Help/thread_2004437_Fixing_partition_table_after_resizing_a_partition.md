---
title: "Fixing partition table after resizing a partition"
date: 2012-06-15
forum: General Help
---

### Post by Jary316 on 2012-06-15
Hi,

I was running two OS, Ubuntu and Windows 7, and another partition in NTFS (/dev/sda5) was used to store my personal between both OS. I wanted to divide it in half to install a third OS.

I used "Resize/Move" in GParted, and slide the bar from the right towards the middle. I did that and hit apply, but the drive could not be mounted afterwards. In Windows 7, I tried deleting the new partition and expanding my old drive so it takes all it's size back, but I realize there are still 1 or 2 unallocated block, as shown on the picture: [IMG]http://img51.imageshack.us/img51/3739/screenshotfrom201206141.png[/IMG] (On windows 7, the partition is RAW, on Ubuntu it is detected as NTFS).

I believe the unallocated that is 9 MB was part of the drive, and also the 1.02 MB unallocated at the bottom (I have no idea how this one got there).

When trying to open DATA from Ubuntu I get the following error:

> 
Error mounting: mount exited with exit code 12: Failed to read last sector (365685320): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sda5': Invalid argument
The device '/dev/sda5' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?


Running "sudo fdisk -l" gives me the following output:

> 
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x76692ca8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    34812854    17405403+  1c  Hidden W95 FAT32 (LBA)
/dev/sda2   *    34812855   279000854   122094000    7  HPFS/NTFS/exFAT
/dev/sda3       279000916   976771071   348885078    f  W95 Ext'd (LBA)
/dev/sda5       279000918   644669439   182834261    7  HPFS/NTFS/exFAT
/dev/sda6       644687872   968540159   161926144   83  Linux
/dev/sda7       968542208   976771071     4114432   82  Linux swap / Solaris


On the good side, I have a recent backup on an external drive, but I would still like to get back to my previous state and be able to partition my /dev/sda5 for my new OS later on. Maybe the files are still intact on /dev/sda5? It would be nice to salvage them if that is the case.

I believe that fixing the partition table would put me in a clean state where I was before doing the "Resize/Move" but I do not know how to.

Could anyone please give me some help? It would be really useful!

Thank you really much for your help!

---

