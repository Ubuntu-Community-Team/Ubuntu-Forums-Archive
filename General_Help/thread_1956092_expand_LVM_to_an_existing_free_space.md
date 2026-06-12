---
title: "expand LVM to an existing free space"
date: 2012-04-10
forum: General Help
---

### Post by mrwolf76 on 2012-04-10
Hello,
I read lot of threads about LVM extending but they are all about adding new partitions and merge to the existing LVM.

My situation is different. This is the actual schema: 200Gb partition with a 100Gb LVM volume on it.
```
# fdisk -l

Disk /dev/sda: 214.7 GB, 214748364800 bytes
255 heads, 63 sectors/track, 26108 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d940d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          66      530113+  83  Linux
/dev/sda2              67       26109   209185024+   5  Extended
/dev/sda5              67       13054   104326078+  8e  Linux LVM
```Here's other useful outputs:
```
# pvdisplay
  --- Physical volume ---
  PV Name               /dev/sda5
  VG Name               volumename1
  PV Size               99.49 GiB / not usable 766.50 KiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              25470
  Free PE               0
  Allocated PE          25470
  PV UUID               NTnf7B-0yOp-8s69-C0FH-85U2-nZwF-lRGqu6
   
``````
# lvdisplay
  --- Logical volume ---
  LV Name                /dev/volumename1/root1
  VG Name                volumename1
  LV UUID                WcZheQ-2L5k-Kq84-n8Ld-7GoW-3ON0-OwNjuf
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                9.31 GiB
  Current LE             2384
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           251:0
   
  --- Logical volume ---
  LV Name                /dev/volumename1/swap1
  VG Name                volumename1
  LV UUID                fr2QLY-ARw4-aN0C-086J-WjUG-4VrG-e174Op
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                3.72 GiB
  Current LE             953
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           251:1
   
  --- Logical volume ---
  LV Name                /dev/volumename1/opt1
  VG Name                volumename1
  LV UUID                52uTT2-yNea-R1Se-FESc-ArF9-a1Ja-EGqw5D
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                86.46 GiB
  Current LE             22133
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           251:2
```I don't know what to do to extend this volume group to 200Gb.

Thank you for your help.

---

### Post by skabople on 2012-04-10
vgextend

---

### Post by mrwolf76 on 2012-04-10
afaik, vgextend is useful to add a PhysicalDevicePath to a VolumeGroupName.
I don't have a Physical device to add to the VG...

---

### Post by skabople on 2012-04-10
Oh ok now I see what you're talking about....

---

