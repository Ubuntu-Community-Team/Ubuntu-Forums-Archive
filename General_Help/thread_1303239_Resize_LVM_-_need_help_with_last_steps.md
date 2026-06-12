---
title: "Resize LVM - need help with last steps"
date: 2009-10-28
forum: General Help
---

### Post by MountainX on 2009-10-28
I have already resized the file system and the logical volumes. Now I have free PEs. What are the next steps to reduce the volume group?

My setup is 1 HDD with 2 partitions:
sda1 (/boot)
sda2 (LVM inside crypto)

inside the LVM are these logical volumes
/
/home
swap
These now take up on 16.92 GB.

I want to shrink the VG from 109.42 GB to 20 GB.
Then I want to shrink sda2 down from 109 GB to 20 GB -- and keep the crypto and VG.

Here's some relevant info:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xxxxx

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         309     2474010   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2             310       14593   114736230   8e  Linux LVM

root@ubuntu:/# vgdisplay
  --- Volume group ---
  VG Name               VgOne
  System ID             
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  6
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                3
  Open LV               0
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               109.42 GB
  PE Size               4.00 MB
  Total PE              28011
  Alloc PE / Size       4331 / 16.92 GB
  Free  PE / Size       23680 / 92.50 GB
  VG UUID              xxxxx


Basically, I want to use the free space to make a new partition, sda3 (outside this LVM, of course). Thanks.

---

### Post by MountainX on 2009-10-28
solved

[http://www.linuxquestions.org/questions/linux-general-1/how-do-i-shrink-a-volume-group-once-i-have-created-free-space-in-it-765047/](http://www.linuxquestions.org/questions/linux-general-1/how-do-i-shrink-a-volume-group-once-i-have-created-free-space-in-it-765047/)

---

