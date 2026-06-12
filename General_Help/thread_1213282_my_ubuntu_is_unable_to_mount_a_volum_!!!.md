---
title: "my ubuntu is unable to mount a volum !!!"
date: 2009-07-14
forum: General Help
---

### Post by drwolf on 2009-07-14
today my ubuntu  new surprise was  this : unable to mount all other volumes on my laptop 
i did 
sudo fdisk -l

and i got this : 

zazo@zazo-laptop:~$ sudo fdisk -l
[sudo] password for zazo: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5db65db6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5855    47022636    7  HPFS/NTFS
/dev/sda2            5855       10714    39036928    7  HPFS/NTFS
/dev/sda3           10714       14594    31158272   83  Linux
zazo@zazo-laptop:~$ 

any comment to solve this problem ?

---

### Post by cosine352 on 2009-07-14
Is the other volume is of windows? Make sure to shutdown windows properly. Then boot to ubuntu and it should mount automatically.

---

### Post by drwolf on 2009-07-14
yes it is windows 
i followed you recommendation:lolflag: 
the problem solved 
thanks

---

