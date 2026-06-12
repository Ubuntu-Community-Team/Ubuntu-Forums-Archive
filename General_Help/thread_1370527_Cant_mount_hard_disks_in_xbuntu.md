---
title: "Cant mount hard disks in xbuntu"
date: 2010-01-02
forum: General Help
---

### Post by dysvir on 2010-01-02
Xbuntu wont pic up my internal ide harddisks how do i mount them? need help pronto the hard disk is FAT32 and there is an Ext3 NTFS and linux-swap partitioned onto the system disk

---

### Post by MooPi on 2010-01-02
```
sudo fdisk -l 
```
type this in terminal and print response back here

---

### Post by dysvir on 2010-01-02
here is what i get:
```

root@username-desktop-01:~# sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0ed40ed3

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1785    14337981    7  HPFS/NTFS
/dev/sda2            1786        2040     2048287+  82  Linux swap / Solaris
/dev/sda3            2041        3869    14691442+  83  Linux
/dev/sda4            3870        4599     5863725   83  Linux

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xea88ea88

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241    b  W95 FAT32
Note: sector size is 2048 (not 512)

Disk /dev/sdc: 988 MB, 988807168 bytes
256 heads, 46 sectors/track, 41 cylinders
Units = cylinders of 11776 * 2048 = 24117248 bytes
Disk identifier: 0x00000000

Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1          41      965540    b  W95 FAT32
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 0, 46) logical=(0, 1, 1)
root@username-desktop-01:~#
```

---

### Post by dysvir on 2010-01-02
chrz for your help, where do i go from here

---

### Post by MooPi on 2010-01-02
I'll give you and example for sdb1.
```
sudo mkdir /media/95fat
``````
sudo mount /dev/sdb1 /media/95fat
```to unmount 
```
sudo umount /dev/sdb1
```
I'd like to add that these drives should be accessible already through Thunar your file manager. Why they aren't showing up I don't know. How were they added to the computer?

---

### Post by Leppie on 2010-01-02
> **MooPi said:**
> I'd like to add that these drives should be accessible already through Thunar your file manager. Why they aren't showing up I don't know. How were they added to the computer?
Thunar doesn't show not mounted internal disks/partitions on any of my Xubuntu systems (I have 3 different machines running Xubuntu). Nautilus does and has other options Thunar does not have (like the extra option "savely remove device", even though I'm not quite sure what advantage that gives over unmount).

---

### Post by MooPi on 2010-01-02
If I used Xubuntu I'd probably switch to pcmanfm for that convenience. Pcmanfm is my favorite for several reasons but on gnome systems it's a bit redundant.

---

### Post by dysvir on 2010-01-06
at the moment all my hard disks are ide based thanks for all your help

---

### Post by Leppie on 2010-01-06
so have you been able to mount the partitions?

---

### Post by dysvir on 2010-01-07
no it says it cant mount a special device :$

---

