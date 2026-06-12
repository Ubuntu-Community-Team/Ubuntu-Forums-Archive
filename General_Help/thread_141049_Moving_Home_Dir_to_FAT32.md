---
title: "Moving Home Dir to FAT32"
date: 2006-03-07
forum: General Help
---

### Post by TomAnthony on 2006-03-07
I am going to buy a hard drive for my home directory, and I was wondering if there are any issues in using a FAT32 file system instead of ext3. I would like to share my data with my XP install.

---

### Post by aysiu on 2006-03-07
You can't install /home on a FAT32 partition--it just can't be done.

There's no reason you can't make the FAT32 partition a data partition mounted at /home/data, though.

---

### Post by Rizado on 2006-03-07
[This](http://www.fs-driver.org/) is what you want. It works great for me.

---

### Post by patrixl on 2006-03-07
[QUOTE=TomAnthony]I am going to buy a hard drive for my home directory, and I was wondering if there are any issues in using a FAT32 file system instead of ext3. I would like to share my data with my XP install.[/QUOTE]

Not a good idea at all:

- ext2/3 support longer filenames than FAT32
- ext2/3 support many file attributes that FAT doesnt' support (all the permissions for example)
- ext2/3 are more robust than FAT32

Like others have suggested, you might as well have an extra partition mounted somewhere in your linux system where you can copy files you wanna transfer, or use one of the windows ext2fs drivers.

A long time ago, there was a driver for Linux called umsdos, which simulated ext2 attributes/permissions/longfilenames on a FAT partition, but they have officially stopped development now and the driver doesnt' work with linux kernel 2.6.x...

---

### Post by TomAnthony on 2006-03-07
Thanks for all the replys. I think I will just format it with ext3 and use the previously mentioned windows driver to read the drive from XP. I tried them, and they seem to work well. I just hope they won't hurt my ext3 file system. I am 1 step away from blowing away my XP install anyway, but I haven't been able to get my iPod working with Kubuntu yet. I'm sure something will come along soon to fix that, but untill then I will just use my iTunes in XP. Long live Linux!

---

