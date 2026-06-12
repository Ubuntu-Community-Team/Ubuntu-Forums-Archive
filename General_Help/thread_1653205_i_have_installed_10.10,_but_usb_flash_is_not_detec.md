---
title: "i have installed 10.10, but usb flash is not detected"
date: 2010-12-26
forum: General Help
---

### Post by doron387 on 2010-12-26
i have installed a fresh install of 10.10 on a hp pavillion dv6000 laptop.
everything works fine except detecting my usb flash devices.
when i plug in my 8 GB flashdisk, nothing appeares on the desktop.
when i go to terminal and type sudo 'fdisk -l' i get : 

[COLOR="Blue"]:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000db696

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9328    74920960   83  Linux
/dev/sda2            9328        9730     3227649    5  Extended
/dev/sda5            9328        9730     3227648   82  Linux swap / Solaris

Disk /dev/sdb: 8029 MB, 8029470208 bytes
255 heads, 63 sectors/track, 976 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x58f8a4bd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         977     7841248    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(975, 254, 63) logical=(976, 49, 32)[/COLOR]

which means that is being detected.
something is missing, will ya help me guys ?

---

### Post by doron387 on 2010-12-26
bump

---

### Post by mikewhatever on 2010-12-27
It looks like there are some filesystem errors. Open the Disk Utility under System->Administration and check that device filesystem for errors.

---

