---
title: "Partition too slow"
date: 2010-03-20
forum: General Help
---

### Post by Gegenzeit on 2010-03-20
Hello,

My main data partition is too slow. Whenever I copy to or from it, I just get about 1.1 MiB/sec. Anyone knows something to do about it?

I use Ubuntu 9.1. Here a list of my partitions - the one I'm having trouble with is sda8:

[SIZE=2]sda1: Windows 7, nfts, 200 GiB, not mounted

sda3: Data, nfts, 250 GiB, mountpoint: /mnt/LinWin

sda2: Extended, 947 GiB
.......sda6: Linux system partition, ext4, 75 GiB, mountpoint: /
.......**sda8: Data, ext4, 700 GiB, mountpoint: /media/data**
.......sda9: not in use, ext4, not mounted
.......sda7: Linux Swap
.......unallocated
.......sda5: Recovery, fat32
[/SIZE] 
Thanks

Jörg

---

### Post by bobcollard on 2010-03-20
EXT4 is about as fast as you get, in Linux.  You might have a problem with drive speed. Average is 4200. 6400 or 7200 depending on how they are set up and their actual size, see link below:
[http://www.mactech.com/articles/mactech/Vol.23/23.01/2301LaptopHardDriveSpeed/index.html](http://www.mactech.com/articles/mactech/Vol.23/23.01/2301LaptopHardDriveSpeed/index.html)

---

### Post by Gegenzeit on 2010-03-20
Hmm... all partitions are on the same drive - but only sda8 is that slow. All other partitions give me 25+ MB/s (at the very least).

This is my drive: [http://www.seagate.com/ww/v/index.jsp?vgnextoid=511a8cf6a794b110VgnVCM100000f5ee0a0aRCRD](http://www.seagate.com/ww/v/index.jsp?vgnextoid=511a8cf6a794b110VgnVCM100000f5ee0a0aRCRD)

_____
EDIT - PROBLEM SOLVED

I unmounted the partition and checked it with gparted (right klick on the partition, then chose check). After that everything is working perfectly and inhumanly fast ;)

---

