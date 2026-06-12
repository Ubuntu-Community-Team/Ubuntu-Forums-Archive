---
title: "error message when inserting usb device"
date: 2009-07-17
forum: General Help
---

### Post by pythonscript on 2009-07-17
I get this error message when I insert my 16 GB ntfs flash drive. Any ideas how I can fix this? I've tried reformatting the whole device and creating a new partition table with GParted, but that doesn't work. The device works in other computers (both ubuntu and windows). Thanks!

[IMG]http://img30.imageshack.us/img30/3078/errorkgj.png[/IMG]

---

### Post by 67GTA on 2009-07-17
Make sure you have ntfs-3g installed. Then open a terminal and run ```
sudo fdisk -l
``` with the drive plugged in. Post the output here.

---

### Post by pythonscript on 2009-07-17
ntfs-3g is properly installed, and I can mount the device manually from the terminal after I accept the error message. I guess my main problem is that it won't automatically mount and that it gives an error message. sudo fdisk -l gives this:

```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe728f646

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           1        8001   83  Linux
/dev/sda2   *           2        1568    12586927+  83  Linux
/dev/sda4            1569       18911   139307647+   5  Extended
/dev/sda5            1569       10747    73730286   83  Linux
/dev/sda6           10748       17634    55319796   83  Linux
/dev/sda7           17635       18182     4401778+  82  Linux swap / Solaris

Disk /dev/sdb: 16.3 GB, 16368271360 bytes
255 heads, 63 sectors/track, 1989 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007c4df

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1989    15976611    7  HPFS/NTFS
```
Also, I can't write to it... even as sudo...

EDIT:  Also, all my other ntfs usb devices work fine. I have multiple other usb flash drives and several usb external hard drives that all function exactly as they should and don't produce any errors.

---

