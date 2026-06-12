---
title: "Resizing ext4 File system ubuntu 11.04"
date: 2011-08-25
forum: General Help
---

### Post by nemz on 2011-08-25
I recently moved to ubuntu after Windows user all my life.

I have completely switched to Ubuntu, and have no windows installs on this pc.

I followed a guide while setting up my hard drive partitions and ended up with 3 partitions, a swap file 16gb, 16gb file system, and then an extra partition which used the remainder of the 500gb drive. (I am pretty sure I just wanted ubuntu to use all my disk with a 16gb swap file though, and thought I was just going to have 2 partitions? confusing =]?)

Been using Ubuntu for a bit now, and have set up most things how I would like, and I am enjoying my install.

But I have now come across an issue, I have found that my 16gb file system is full, and everything seems to be saved to the file system.

Ubuntu some times crashes after entering password for login, and may need to be restarted a few times before it boots. I am guessing it may also be related to the file system being full

now I have tried a few things to grow my file system using gnome partition editor, I have deleted the extra 400gb partition to try merge it into the file system, but I just cant seem to do it.

Here is a screen shot in disk utility.

[IMG]http://img571.imageshack.us/img571/4366/parion.jpg[/IMG]

---

### Post by nemz on 2011-08-25
more info on disk


Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00060e0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1946    15624193    5  Extended
/dev/sdb5               1        1946    15624192   83  Linux

---

