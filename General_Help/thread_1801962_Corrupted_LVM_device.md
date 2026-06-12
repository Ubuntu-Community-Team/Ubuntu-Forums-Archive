---
title: "Corrupted LVM device"
date: 2011-07-11
forum: General Help
---

### Post by dziring on 2011-07-11
I'm hoping, now that I've recovered my partition tables, that someone can help me rebuild my LVM volume group.
The trouble is that one of the volumes lost its partition table, and after rebuilding the table, LVM can no longer identify the drive.  
I'm trying to rebuild the 'fileserver' volume group.

pvscan produces the following:


  Couldn't find device with uuid 'jsZAMq-LSa1-87Zb-WoGs-oi6v-u1As-h7YZMl'.
  PV /dev/sdc5        VG dev          lvm2 [232.64 GiB / 0    free]
  PV unknown device   VG fileserver   lvm2 [1.36 TiB / 556.00 MiB free]
  PV /dev/sda1        VG fileserver   lvm2 [1.36 TiB / 556.00 MiB free]
  Total: 3 [2.96 TiB] / in use: 3 [2.96 TiB] / in no VG: 0 [0   ]

---

### Post by dziring on 2011-07-11
The errant drive, per fdisk (my emphasis added):


Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
[COLOR="Red"]Disk identifier: 0x00000000[/COLOR]

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      182402  1465138583+  8e  Linux LVM

---EDIT (Added)---
I saw on another forum that it looks I can remove the logical volume, and recreate, but I'd like to confirm this before I do something stupid and permanent (again).

---

### Post by dziring on 2011-07-11
I've found the following instructions elsewhere, but I"d really like to know whether this is likely to help, or wipe out my data, before i try it.  Any input?

Delete the partition (/dev/sdc1) with fdisk (because pvcreate won't let you create a physical volume using the entire disk unless there are no partitions).

Use 'pvcreate' to recreate the physical volume with the same uuid that was used previously.

recreate a volume group on the physical volume with 'vgcreate'

restore the logical volume config with 'vgcfgrestore'

The instructions I found are at [http://www.barryodonovan.com/index.php/2007/12/08/lvm-recovery](http://www.barryodonovan.com/index.php/2007/12/08/lvm-recovery)

---

