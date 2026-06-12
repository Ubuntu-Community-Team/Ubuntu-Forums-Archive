---
title: "Question about Dual Booting"
date: 2010-01-10
forum: General Help
---

### Post by Keikowned on 2010-01-10
Can I assign an unlimited about of space for the ubuntu partition 

Let's say it's a 500 gb hd, can I assign 100 for w7 and 400 for ubuntu or will it choose a specific size by default

---

### Post by TCSnyder on 2010-01-10
yes, you can split your hard drive anyway you like. I like to have a windows partition, a linux partition, and a media partition so i can share files and dont need to backup if i reinstall

---

### Post by Sef on 2010-01-10
Yes, here is my paritions:

> Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6e929b2e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       12779   102647286    7  HPFS/NTFS
/dev/sda2   *       12780       14691    15358140   83  Linux
/dev/sda3           14692       60801   370378575    5  Extended
/dev/sda5           14692       16603    15358108+  83  Linux
/dev/sda6           16604       16730     1020096   82  Linux swap / Solaris
/dev/sda7           16731       60801   354000276   83  Linux


Put Windows on the first primary parition.  Note: I have Karmic installed on sda2 and Lucid Lynx (the development version) installed on sda5.

---

