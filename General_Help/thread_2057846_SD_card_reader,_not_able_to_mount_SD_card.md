---
title: "SD card reader, not able to mount SD card"
date: 2012-09-14
forum: General Help
---

### Post by micahpage on 2012-09-14
The frontal SD card readers and USB. The USB works every time. However the SD card will occasionally read and sometimes not read. I noticed that if i reboot the PC and log back in with the card in it, it will mount, but at any time I safely remove hte card and take it out....The only way I can get it to mount again is to reboot.

What might I do to fix this?

---

### Post by angry_johnnie on 2012-09-14
Does it show the SD card if you run this?

```
sudo fdisk -l
```

If it does, you can just mount it manually:

```
sudo mount /dev/sdX /path/to/mountpoint
```

where /dev/sdX is whatever fdisk shows for your card, and /path/to/mountpoint is any existing, empty, directory you can use for mounting, like /media/usb /mnt/usb or anything you may have.

It still doesn't solve the fact it's not automatically mounting, but it'll let you work with it :)

---

### Post by micahpage on 2012-09-14
i do not see it

```
metulburr@ubuntu:~$ sudo fdisk -l
[sudo] password for metulburr: 

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcb5bd2b2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    29747199    14872576   1b  Hidden W95 FAT32
/dev/sda2   *    29747200   783071231   376662016    7  HPFS/NTFS/exFAT
/dev/sda3       783075326  1953523711   585224193    5  Extended
/dev/sda5      1936932864  1953523711     8295424   82  Linux swap / Solaris
/dev/sda6      1223170048  1657468927   217149440   83  Linux
/dev/sda7       783077376  1223167999   220045312   83  Linux
/dev/sda8      1657470976  1936930815   139729920   83  Linux

Partition table entries are not in disk order
Note: sector size is 4096 (not 512)

Disk /dev/sdf: 3000.6 GB, 3000558944256 bytes
255 heads, 63 sectors/track, 45599 cylinders, total 732558336 sectors
Units = sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00074d0d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1             256 
metulburr@ubuntu:~$ 

```

---

### Post by tea for one on 2012-09-14
> **micahpage said:**
> The frontal SD card readers and USB. The USB works every time. However the SD card will occasionally read and sometimes not read. I noticed that if i reboot the PC and log back in with the card in it, it will mount, but at any time I safely remove hte card and take it out....The only way I can get it to mount again is to reboot.

What might I do to fix this?

Good evening

In nautilus, when you select the SD card drive with a "right click",
do you have options of:-

(a) eject
(b) safely remove drive

If you "eject" the SD card, the drive will hopefully remain active.

If you "safely remove drive", the drive is disabled (inactive) until you reboot.

I do not not why this occurs but I suspect that it is related to hardware.

SD cards often need to be treated like removable CDs.

Admittedly, the syntax is baffling.........

I would be interested to know what happens if you select "eject"

---

### Post by micahpage on 2012-09-14
that i did not know, thanks

I will post back when I get it to work. I actually haven't been able to get it to mount in awhile.

---

