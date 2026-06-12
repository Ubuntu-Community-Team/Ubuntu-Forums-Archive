---
title: "Issue with grub again!"
date: 2010-06-29
forum: General Help
---

### Post by redcodefinal on 2010-06-29
Hi again,
I ha a successful dual boot with win 7 and ubuntu 10.04. I just moved computers from a dell XPS witha P4 to a Xeon. I switched the hard drives between the machines. As I expected GRUB somehow imploded on the idea and now only displays a cruel "No such disk" message. Anyways, I was hoping to tap into someones vast knowledge of grub and help me re-configure it. It would make my day. I am also using a LiveCD so any commands I would use must be able to work on a LiveCD
fdisk -l
```
Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xdf29521d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       23781   191020851   83  Linux
/dev/sda2           23782       24792     8120857+   5  Extended
/dev/sda5           23782       24792     8120826   82  Linux swap / Solaris

Disk /dev/sdc: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f0422

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdb: 300.1 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe3b8e3b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3863    31029516    7  HPFS/NTFS
/dev/sdb2            3864       36483   262020150    f  W95 Ext'd (LBA)
/dev/sdb5            3864       36483   262020118+   7  HPFS/NTFS

```sudo update-grub
```
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

```

---

### Post by oldfred on 2010-06-30
Install from LiveCD:
Find linux partition change sda5 if not correct or even sda if sdb wanted:
sudo fdisk -l
sudo mkdir /mnt/sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo grub-install --recheck --root-directory=/mnt /dev/sda

reinstall grub2 -------------------------------
Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
full chroot version:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

