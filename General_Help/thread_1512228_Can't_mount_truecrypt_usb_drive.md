---
title: "Can't mount truecrypt usb drive"
date: 2010-06-17
forum: General Help
---

### Post by Frenky893 on 2010-06-17
Hi everyone,

I made a truecrypt volume on my usb drive on windows a while ago, and it worked fine. Then I switched to linux (yes ubuntu) and it still worked fine, when using the GUI of Truecrypt. Now, I want to mount it on my ubuntu server, so I'm using the CLI version, and I just can't mount it. Here's some more info:

```

**$ sudo mount -t vfat /dev/sdf1 /media/encrypted**
mount: wrong fs type, bad option, bad superblock on /dev/sdf1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

``````

**$ dmesg | tail**
[  170.523939] FAT: invalid media value (0x12)
[  170.525064] VFS: Can't find a valid FAT filesystem on dev sdf1.
[ 1970.405035] FAT: invalid media value (0x12)
[ 1970.406304] VFS: Can't find a valid FAT filesystem on dev sdf1.
[ 2336.366994] FAT: invalid media value (0x12)
[ 2336.368239] VFS: Can't find a valid FAT filesystem on dev sdf1.
[ 2440.574426] FAT: invalid media value (0x12)
[ 2440.575562] VFS: Can't find a valid FAT filesystem on dev sdf1.
[ 2790.266103] FAT: invalid media value (0x12)
[ 2790.267196] VFS: Can't find a valid FAT filesystem on dev sdf1.
``````

**$ truecrypt /dev/sdf1 /media/encrypted**
Enter password for /dev/sdf1: 
Enter keyfile [none]: 
Protect hidden volume (if any)? (y=Yes/n=No) [No]: 
Enter your user password or administrator password: 
Incorrect password or not a TrueCrypt volume.
``````
**$ sudo fdisk -l**

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005822e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          32      248832   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              32        9730    77899777    5  Extended
/dev/sda5              32        9730    77899776   83  Linux

Disk /dev/sdf: 529 MB, 529530880 bytes
32 heads, 32 sectors/track, 1010 cylinders
Units = cylinders of 1024 * 512 = 524288 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1        1010      517104    6  FAT16        ** <--------------------**
Partition 1 has different physical/logical endings:
     phys=(1023, 31, 32) logical=(1009, 31, 32)
```I'm going insane! Any truecrypt experts here? I don't understand what I'm doing wrong. I'm sure the usb drive is fine because it worked great on windows and my ubuntu desktop. Thanks in advance!

---

