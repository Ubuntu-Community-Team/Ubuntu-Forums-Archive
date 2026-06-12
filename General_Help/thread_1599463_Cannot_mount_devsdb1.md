---
title: "Cannot mount /dev/sdb1"
date: 2010-10-17
forum: General Help
---

### Post by Cobracommand0 on 2010-10-17
My 160gb hard drive was functioning fine until this afternoon, while I was doing restarts after editing my compiz settings.  I'm pretty sure that I didn't touch anything during this process to affect the drive, but after one of the restarts my drive no longer mounted.  I tried ```
sudo mount /dev/sdb1
``` without success, the output was: ```
 skert@HMSDEVASTATOR:~$ sudo mount /dev/sdb1 
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
  
```my fdisk -l output is:
```
skert@HMSDEVASTATOR:~$ sudo fdisk -l

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x18d018d0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321    b  W95 FAT32

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000269b9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9328    74920960   83  Linux
/dev/sda2            9328        9730     3227649    5  Extended
/dev/sda5            9328        9730     3227648   82  Linux swap / Solaris 
```Does anyone have an idea what the issue could be? As I said, it was working fine this afternoon.. The drive I am trying to mount is the 160 /dev/sdb1.

Cheers

---

### Post by spikoley on 2010-10-17
With the *mount* command you have to specify which directory you want to mount it to.

First create a directory to mount the drive to:
```
sudo mkdir /media/USB
```
Mount the drive:
```
sudo mount /dev/sdb1 /media/USB
```

You unmount the drive without the directory:
```
sudo umount /dev/sdb1
```

---

### Post by Cobracommand0 on 2010-10-17
That worked, thanks!

CC

---

