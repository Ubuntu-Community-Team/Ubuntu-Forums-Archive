---
title: "Mounting External Hard Drive"
date: 2010-07-16
forum: General Help
---

### Post by RedSingularity on 2010-07-16
Hey everyone.  I have recently run into a problem with my external hard drive.  When I turn it on Ubuntu doesn't recognize it.  Even if I do "sudo fdisk -l" in a terminal it doesn't come up.  I have to turn the computer off and restart it for Ubuntu to recognize it.  Anyone have any ideas as to why this is happening?

---

### Post by ukblacknight on 2010-07-21
I've got the same problem, except it's specific to my girlfriends laptop.  She's got a 250GB USB HDD in ntfs.  If I plug it into my computer (Ubuntu 10.04), it mounts fine, but on her laptop (Ubuntu 10.04), it's not recognised in fdisk -l. It mounts on her laptop in Windows 7.

The device *is* recongised in lsusb:

```
tom@maria-laptop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 002 Device 005: ID 0930:0b03 Toshiba Corp.** 
Bus 002 Device 003: ID 0bda:0159 Realtek Semiconductor Corp. 
Bus 002 Device 002: ID 04f2:b044 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1e325cea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1275    10240000   27  Unknown
/dev/sda2   *        1275       50881   398460195    7  HPFS/NTFS
/dev/sda3           50882       60801    79682369+   5  Extended
/dev/sda5           50882       51005      995998+  82  Linux swap / Solaris
/dev/sda6           51006       60801    78686338+  83  Linux
```

**Edit:** Her laptop doesn't have a floppy drive, nor any options about floppy drives/controllers in the BIOS.

---

