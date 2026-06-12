---
title: "Error while resizing partition with GParted"
date: 2010-09-29
forum: General Help
---

### Post by roberpreston on 2010-09-29
Hi, I was resizing a partition of my hard drive with GParted in an Ubuntu LiveCD. The hard drive has Windows 7, Linux Mint y Ubuntu 10.04. My intention was to get rid of Ubuntu and make some space for Linux Mint. There was an error while resizing, and the GRUB is gone, but also GParted shows no partition. I want, at least, to recover the data (specially sda2 i think is my linux mint partition) and then I can install Ubuntu again. 

I have run fdisk -l -u and this was the result:

ubuntu@ubuntu:~$ sudo fdisk -l
Warning: ignoring extra data in partition table 7
Warning: ignoring extra data in partition table 7
Warning: invalid flag 0x460c of partition table 7 will be corrected by w(rite)

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1549f232

Device Boot Start End Blocks Id System
/dev/sda1 * 1 6377 51223221 7 HPFS/NTFS
/dev/sda2 6378 23201 135138780 83 Linux
/dev/sda3 23202 38913 126206640 5 Extended
/dev/sda5 37785 38913 9068661 82 Linux swap / Solaris
/dev/sda6 23202 34475 90558342 83 Linux
/dev/sda7 ? 252667 290159 301153333 c7 Syrinx

I need some help please.

---

### Post by srs5694 on 2010-09-29
Your partition table is definitely damaged. Your disk has 38,913 cylinders, but /dev/sda7 begins on cylinder 252,677 and ends on 290,159. Chances are this partition is just plain bad data; however, it could be a corruption of a real partition. There does appear to be space that's unallocated, but that could be normal since you were in the process of repartitioning. I'd recommend you do the following:


[list=1]
[*]Back up any important data from the drive that you can access. Anything you try to fix the problem at this point is risky, so you could make matters worse, and a backup can save you from the worst of the possible consequences.
[*]Use fdisk to delete /dev/sda7.
[*]Use [TestDisk](http://www.cgsecurity.org/wiki/TestDisk) on the disk. That *may* recover your lost partition(s).
[*]Back up any data that you can access now but that you couldn't before.
[*]Try again with GParted, but do it in smaller steps, and if possible in a different order than you did before to minimize the risk of running into the same problem you did the first time around.
[/list]

---

### Post by roberpreston on 2010-09-30
Thank you for your help. I did recover some data.
Cheers

---

