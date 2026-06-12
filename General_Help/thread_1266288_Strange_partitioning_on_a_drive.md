---
title: "Strange partitioning on a drive"
date: 2009-09-14
forum: General Help
---

### Post by joeinbend on 2009-09-14
Hi all,
I was wiping a drive to install Win7 for one of my systems at home (dont fret, it will be a dual boot w/ Ubuntu!), but I ran into some strange partition behavior, and could use some help:

The drive is a 400G SATA drive, that it's last use was with "ZoneMinder" for my security DVR. I have since moved ZM to another server and am recycling the hardware resources.

I went to install Win7 on it, and it gets to the partitioning info part, and as expected it sees 3 partitions, a la standard Linux arrangements. I deleted all partitions so I could use the whole drive, but it gave me errors saying it couldn't write to/create a new partition table. Odd I thought. this first time around was actually on the older 80G drive in the system, and this error prompted me to go ahead and put the 400G drive in it, and I encountered the same issue.

So, I live booted Ubuntu Desktop so I could fdisk it and just make it a clean drive with no paritions. wrong. Ubuntu sees "two drives"... sda and sdb. whaaat? sda is 16MB (sounds like MBR to me) and sdb is the remaining 392G. Careful examination with fdisk shows both sda and sdb are void of any partitions.

Why is Ubuntu recognizing what I am presuming to be the MBR as a separate physical disk? I was expecting to see sda1 and sda2, but not this!  How do I clean up this hard disk?!  :confused:

---

### Post by NightwishFan on 2009-09-14
Perhaps just create the blank msdos partition table manually with Gparted on the Ubuntu live CD. Then you can install Windows on the blank disk. After Windows in installed, then you can resize the drive (using Windows) to install Ubuntu in the blank space.

---

### Post by joeinbend on 2009-09-14
I figured this one out -- one of those forehead-slap moments! The 16MB "drive" was my MagicJack device, and somehow the partitioner was deciding that it was a higher priority device than the SATA drive, thus trying to create partitions on it, and thus the "cannot create or modify partition table" error, as it is a read-only flash device! Issue resolved.

---

