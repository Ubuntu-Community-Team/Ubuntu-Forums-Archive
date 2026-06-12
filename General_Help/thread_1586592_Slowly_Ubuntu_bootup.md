---
title: "Slowly Ubuntu bootup"
date: 2010-10-02
forum: General Help
---

### Post by Dwigatjel on 2010-10-02
Hi all.
I have a problem with my ubuntu.
I have intel core 2 duo 2.2Ghz 2 Gb ram. 
160GB SATA Fat32
250GB SATA NTFS (wind*ws instalation)
and 500GB for Ubuntu (/; /home; /data ;swap)
And when i install ubuntu on this opposite the wind*ws it starts over 7 minutes (7:17)
GRUB menu shows on 1:15 minutes
I tested this disk with hdparm and it shows:
> 
Disk / dev / sda: 160.0 GB, bytes: 160041885696
255 heads, sectors / track: 63 Cylinders: 19457
Units = cylinders of 16065 * 512 = 8225280 bytes
The sector size (logical / physical) in bytes: 512 / 512
Size of I / O (the minimum / optimum) in bytes: 512 / 512
Disk identifier: 0x00000001

Device Boot Start End Blocks Id System
/ Dev/sda1 * 1 19457 156288321 b W95 FAT32

Disk / dev / sdb: 250.1 GB, bytes: 250059350016
255 heads, sectors / track: 63 Cylinders: 30401
Units = cylinders of 16065 * 512 = 8225280 bytes
The sector size (logical / physical) in bytes: 512 / 512
Size of I / O (the minimum / optimum) in bytes: 512 / 512
Disk identifier: 0x91339133

Device Boot Start End Blocks Id System
/ Dev/sdb1 * 1 8286 66557263 7 HPFS / NTFS
/ Dev/sdb2 8287 30400 177630705 f W95 of linear. (LBA)
/ 8287 30 400 177 630 673 dev/sdb5 7 HPFS / NTFS

Disk / dev / sdc: 500.1 GB, bytes: 500107862016
255 heads, sectors / track: 63 Cylinders: 60801
Units = cylinders of 16065 * 512 = 8225280 bytes
The sector size (logical / physical) in bytes: 512 / 512
Size of I / O (the minimum / optimum) in bytes: 512 / 512
Disk identifier: 0x0005f341

Device Boot Start End Blocks Id System
/ Dev/sdc1 1 2490 19998720 83 Linux
/ Dev/sdc2 2490 60754 467998721 5 Extended
/ 2490 39 839 299 999 232 dev/sdc5 83 Linux
/ Dev/sdc6 39,839 60,505 165 998 592 83 Linux
/ Dev/sdc7 60505 60754 1998848 82 Linux swap / Solaris
filip @ ragebuntu: ~ $ sudo hdparm-tT / dev / sda

/ Dev / sda:
 Timing cached reads: 1566 MB in 2.00 seconds = 783.11 MB / sec
 Timing buffered disk reads: 14 MB in 3.18 seconds = 4.40 MB / sec
filip @ ragebuntu: ~ $ sudo hdparm-tT / dev / sdb

/ Dev / sdb:
 Timing cached reads: 1918 MB in 2.00 seconds = 959.19 MB / sec
 Timing buffered disk reads: 302 MB in 3.01 seconds = 100.49 MB / sec
filip @ ragebuntu: ~ $ sudo hdparm-tT / dev / sdc

/ Dev / sdc:
 Timing cached reads: 1960 MB in 2.00 seconds = 979.99 MB / sec
 Timing buffered disk reads: 154 MB in 3.12 seconds = 49.28 MB / sec
filip @ ragebuntu: ~ $
(I have a polish edition of Ubuntu it was translated by google translate :) ) 
and in BIOS settings there are:
first: 500GB's Disk
second: 160GB's Disk
third: 250GB's Disk
It happens from beginning. Now it has some programs in bootup and there is the same
And can someone help me and make it bootup in less then 2 minutes
or say to me smt like "you need new hard drive for ubuntu" or "install GRUB in MBR" or something
My bootchart: [http://img299.imageshack.us/i/ragebuntulucid201010022.png/](http://img299.imageshack.us/i/ragebuntulucid201010022.png/)
Bests,
Dwig

---

