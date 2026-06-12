---
title: "EXT4-fs, LVM problems... ?"
date: 2011-08-01
forum: General Help
---

### Post by led_belly on 2011-08-01
Hello,

I am experiencing a problem on my machine where X fails to run on start up, instead I am given a login prompt. When I attempt to login the computer pauses for a while then says something like "Login timed out after 60 seconds". I booted the computer with a live CD and found the following in the syslog:

```
kernel: [   67.189968] EXT4-fs (dm-1): re-mounted. Opts: errors=remount-ro,commit=0
```

```
ubuntu@ubuntu:~$ sudo sfdisk -uS -l /dev/sda

Disk /dev/sda: 7296 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *      2048    499711     497664  83  Linux
/dev/sda2        501758 117209087  116707330   5  Extended
/dev/sda3             0         -          0   0  Empty
/dev/sda4             0         -          0   0  Empty
/dev/sda5        501760 117209087  116707328  83  Linux
```

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001c4e8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          32      248832   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              32        7296    58353665    5  Extended
/dev/sda5              32        7296    58353664   83  Linux
```

The ext4 filesystems are encrypted LVM...

Particularly, what's up with /dev/sda2 and /dev/sda5? Where's 3 & 4?

Any help would be appreciated!

---

