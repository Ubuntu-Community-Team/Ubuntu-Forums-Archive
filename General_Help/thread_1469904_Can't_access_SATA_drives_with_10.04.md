---
title: "Can't access SATA drives with 10.04"
date: 2010-05-02
forum: General Help
---

### Post by tames on 2010-05-02
I have two, bootable IDE hard drives that I can physically swap out, to keep different versions of ubuntu linux on each. Version 8.04 has had no problem accessing a separate SATA hard drive, mounted as /home1 for years. When I swap in the IDE drive containing my new installation of ubuntu 10.04, I cannot mount the ext2 partition on the SATA drive. fdisk -l from 10.04 "sees" the SATA drive, and partitions:

Disk /dev/sdd: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2e187bce

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1         131     1052226   82  Linux swap / Solaris
/dev/sdd2             132        4500    35093992+  83  Linux

but I cannot mount it up on existing directory /home1.
sudo mount /dev/sdd2 /home1
returns mount: special device /dev/sdd2 does not exist.

The Disk Utility GUI shows Device /dev/sdd with all the correct info, except it shows it as "Not Partitioned", and does not appear to recognize the sdd1 and sdd2 partitions. Swapping back my bootable 8.04 IDE hard drive, and starting 8.04, it continues to recognize and mount the partition on the SATA hard drive just fine. How do I troubleshoot this, and get 10.04 to mount my existing ext2 partition on the SATA drive?

Thanks.

---

### Post by tames on 2010-05-02
I should add, that although fdisk and gparted both report the partition I'm trying to mount as /dev/sdd2, the /dev/sdd2 device file does not exist, only /dev/sdd. Maybe this is what "mount" is complaining about, that it can't find the /dev/sdd2 device file. Don't know why the /dev/sdd2 device file was not created at installation. Could this be the cause of the problem, and if so, how do I created the /dev/sdd2 device file? Earlier versions of ubuntu had no apparent problem in detecting and creating these device files. If I recall, the SATA controller on my motherboard, to which my two SATA drives are attached, is a RAID-capable controller, but that RAID is turned off. Can this be part of the problem? I don't want to actually use RAID, and it has been no problem in the past to have one SATA drive used for linux, and the other SATA drive for Windows.

---

### Post by tames on 2010-05-04
I found the problem. I confirmed my built-in motherboard SATA disk controller is RAID-capable, but the RAID function was turned off in the BIOS. I was using 2 SATA drives indendently, the 1st with a FAT partition for use with Windows, the 2nd with an ext3 partition for use with linux. On doing a fresh install, and choosing to manually partition, I noticed the partitions on the two SATA drives were being treated as an actual RAID array, as device /dev/mapper/something-or-other, with the partition on the first drive listed as "FAT" (correct) and the partition on the 2nd drive listed as "unformatted" (not correct).

There may be a more elegant solution, but just removing the dmraid package (since I don't need hardware or software RAID) allowed me to mount up the existing ext3 partition on the 2nd SATA drive in the normal way.

Anyone see any problem with this solution, or can suggest a way of configuring the kernel and/or dmraid to leave the non-RAID SATA drives alone (without needing to actually deinstall dmraid)?

---

