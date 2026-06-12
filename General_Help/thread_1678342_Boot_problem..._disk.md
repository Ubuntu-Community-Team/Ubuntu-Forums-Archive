---
title: "Boot problem... disk ?"
date: 2011-01-30
forum: General Help
---

### Post by aqwadon on 2011-01-30
Hi all !

Got a boot problem on a sony vaio with ubuntu 10.04
All was working fine, and now, suddenly, it can't boot anymore.... :(

Sometime, i get 
> Error : hd0,2 Out of diskmost of the time, i get

> udevd[87]: worker [94] unexpectedly returned with status 0x100
udevd[87]: worker [94] failed while handling '/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda2'
udevd[87]: worker [97] unexpectedly returned with status 0x100
udevd[87]: worker [97] failed while handling '/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda5'

ALERT! /dev/disk/by_uuid/fc478e75-0c7e-4dec-abf1-a2c4b8fd2b87 does not exist. Dropping to a shell!

Busybox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in-shell (ash)
Enter 'help' for a list of built-in commands.

initramfs
It looks like there is no disk in the machine. yesterday, there was one... So i boot with a liveCD. and have a look with fdisk...

> ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x598c9b19

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     7813119     3905536   82  Linux swap / Solaris
Partition 1 does not end on cylinder boundary.
/dev/sda2   *     7813120    46874623    19530752   83  Linux
/dev/sda3        46876670   976773119   464948225    5  Extended
/dev/sda5        46876672   976773119   464948224   83  Linux
ubuntu@ubuntu:~$ 
with disk utility, i can find my swap partition 4Gb, my system partition (Ext4, 20Gb), and 476Gb of freespace.....

It's driving me crazy !
Anyone can help ????? Please !
Gabriel

---

### Post by aqwadon on 2011-01-30
up !

---

### Post by aqwadon on 2011-01-30
nobody ?
ram seems to be ok....  please................. is there a way to test the drive ?

---

