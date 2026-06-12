---
title: "Problem with one disk in LVM"
date: 2011-11-07
forum: General Help
---

### Post by zuku on 2011-11-07
Hello,
please help me with my LVM, probably one disk died, computer is booting normally but then stops with this info:
"dev/mapper/vgroup does not exist. Dropping to a shell"

This is what pvscan give me from LIVECD:

```
root@ubuntu:/home/ubuntu# pvscan
  Couldn't find device with uuid '8aq9y7-m6wg-SWeQ-udyZ-dXvR-pFv5-Hi0UOb'.
  Couldn't find device with uuid '8aq9y7-m6wg-SWeQ-udyZ-dXvR-pFv5-Hi0UOb'.
  Couldn't find device with uuid '8aq9y7-m6wg-SWeQ-udyZ-dXvR-pFv5-Hi0UOb'.
  Couldn't find device with uuid '8aq9y7-m6wg-SWeQ-udyZ-dXvR-pFv5-Hi0UOb'.
  Couldn't find device with uuid '8aq9y7-m6wg-SWeQ-udyZ-dXvR-pFv5-Hi0UOb'.
  Couldn't find device with uuid '8aq9y7-m6wg-SWeQ-udyZ-dXvR-pFv5-Hi0UOb'.
  Couldn't find device with uuid '8aq9y7-m6wg-SWeQ-udyZ-dXvR-pFv5-Hi0UOb'.
  PV /dev/sda2        VG vgroup   lvm2 [931,28 GiB / 0    free]
  PV /dev/sdc1        VG vgroup   lvm2 [372,61 GiB / 0    free]
  PV /dev/sdb1        VG vgroup   lvm2 [372,61 GiB / 0    free]
  PV /dev/sdd1        VG vgroup   lvm2 [372,61 GiB / 0    free]
  PV /dev/sde1        VG vgroup   lvm2 [372,61 GiB / 0    free]
  PV /dev/sdf1        VG vgroup   lvm2 [465,76 GiB / 0    free]
  PV unknown device   VG vgroup   lvm2 [465,76 GiB / 0    free]
  PV /dev/sdg1        VG vgroup   lvm2 [372,61 GiB / 0    free]
  Total: 8 [3,64 TiB] / in use: 8 [3,64 TiB] / in no VG: 0 [0   ]
root@ubuntu:/home/ubuntu# pvdisplay
  Couldn't find device with uuid '8aq9y7-m6wg-SWeQ-udyZ-dXvR-pFv5-Hi0UOb'.
  Couldn't find device with uuid '8aq9y7-m6wg-SWeQ-udyZ-dXvR-pFv5-Hi0UOb'.
  Couldn't find device with uuid '8aq9y7-m6wg-SWeQ-udyZ-dXvR-pFv5-Hi0UOb'.
  Couldn't find device with uuid '8aq9y7-m6wg-SWeQ-udyZ-dXvR-pFv5-Hi0UOb'.
  Couldn't find device with uuid '8aq9y7-m6wg-SWeQ-udyZ-dXvR-pFv5-Hi0UOb'.
  Couldn't find device with uuid '8aq9y7-m6wg-SWeQ-udyZ-dXvR-pFv5-Hi0UOb'.
  Couldn't find device with uuid '8aq9y7-m6wg-SWeQ-udyZ-dXvR-pFv5-Hi0UOb'.
  Couldn't find device with uuid '8aq9y7-m6wg-SWeQ-udyZ-dXvR-pFv5-Hi0UOb'.
  --- Physical volume ---
  PV Name               /dev/sda2
  VG Name               vgroup
  PV Size               931,28 GiB / not usable 3,89 MiB
  Allocatable           yes (but full)
  PE Size               4,00 MiB
  Total PE              238407
  Free PE               0
  Allocated PE          238407
  PV UUID               V9RqSk-u05R-Co0t-ItgM-e4t8-9YGb-UpkM8u
   
  Couldn't find device with uuid '8aq9y7-m6wg-SWeQ-udyZ-dXvR-pFv5-Hi0UOb'.
  --- Physical volume ---
  PV Name               /dev/sdc1
  VG Name               vgroup
  PV Size               372,61 GiB / not usable 3,56 MiB
  Allocatable           yes (but full)
  PE Size               4,00 MiB
  Total PE              95387
  Free PE               0
  Allocated PE          95387
  PV UUID               NDRlzH-MQFw-p00k-oLYf-SeBO-RDr8-78MDcF
   
  Couldn't find device with uuid '8aq9y7-m6wg-SWeQ-udyZ-dXvR-pFv5-Hi0UOb'.
  --- Physical volume ---
  PV Name               /dev/sdb1
  VG Name               vgroup
  PV Size               372,61 GiB / not usable 3,56 MiB
  Allocatable           yes (but full)
  PE Size               4,00 MiB
  Total PE              95387
  Free PE               0
  Allocated PE          95387
  PV UUID               2I87ES-oS6z-vQ1D-SEPs-70uS-coV2-YdMiy3
   
  Couldn't find device with uuid '8aq9y7-m6wg-SWeQ-udyZ-dXvR-pFv5-Hi0UOb'.
  --- Physical volume ---
  PV Name               /dev/sdd1
  VG Name               vgroup
  PV Size               372,61 GiB / not usable 3,56 MiB
  Allocatable           yes (but full)
  PE Size               4,00 MiB
  Total PE              95387
  Free PE               0
  Allocated PE          95387
  PV UUID               fnY5Y9-7roZ-yNA1-k324-dVZN-Cc2X-ZJkIvj
   
  Couldn't find device with uuid '8aq9y7-m6wg-SWeQ-udyZ-dXvR-pFv5-Hi0UOb'.
  --- Physical volume ---
  PV Name               /dev/sde1
  VG Name               vgroup
  PV Size               372,61 GiB / not usable 3,56 MiB
  Allocatable           yes (but full)
  PE Size               4,00 MiB
  Total PE              95387
  Free PE               0
  Allocated PE          95387
  PV UUID               lQcvgm-exOt-Ased-ZyFF-gT3y-GOOR-IFOJWq
   
  Couldn't find device with uuid '8aq9y7-m6wg-SWeQ-udyZ-dXvR-pFv5-Hi0UOb'.
  --- Physical volume ---
  PV Name               /dev/sdf1
  VG Name               vgroup
  PV Size               465,76 GiB / not usable 1,50 MiB
  Allocatable           yes (but full)
  PE Size               4,00 MiB
  Total PE              119234
  Free PE               0
  Allocated PE          119234
  PV UUID               EVKwBL-XHUS-hFWV-QOuO-hqP5-DE7f-GYmaPS
   
  Couldn't find device with uuid '8aq9y7-m6wg-SWeQ-udyZ-dXvR-pFv5-Hi0UOb'.
  --- Physical volume ---
  PV Name               unknown device
  VG Name               vgroup
  PV Size               465,76 GiB / not usable 1,50 MiB
  Allocatable           yes (but full)
  PE Size               4,00 MiB
  Total PE              119234
  Free PE               0
  Allocated PE          119234
  PV UUID               8aq9y7-m6wg-SWeQ-udyZ-dXvR-pFv5-Hi0UOb
   
  Couldn't find device with uuid '8aq9y7-m6wg-SWeQ-udyZ-dXvR-pFv5-Hi0UOb'.
  --- Physical volume ---
  PV Name               /dev/sdg1
  VG Name               vgroup
  PV Size               372,61 GiB / not usable 3,56 MiB
  Allocatable           yes (but full)
  PE Size               4,00 MiB
  Total PE              95387
  Free PE               0
  Allocated PE          95387
  PV UUID               cBkHH0-qHkc-n4M0-UMbp-Cwcb-A4eq-zK0ORT
   
root@ubuntu:/home/ubuntu# fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00037231

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          30      240943+  83  Linux
/dev/sda2              31      121601   976519057+  8e  Linux LVM

Disk /dev/sdb: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001f9b4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       48641   390708801   8e  Linux LVM

Disk /dev/sdc: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001a0a0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       48641   390708801   8e  Linux LVM

Disk /dev/sdd: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00023d51

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       48641   390708801   8e  Linux LVM

Disk /dev/sde: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00028e67

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       48641   390708801   8e  Linux LVM

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8ef78ef7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       60801   488384001   8e  Linux LVM

Disk /dev/sdg: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001555e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1       48641   390708801   8e  Linux LVM
```

is any way to fix this problem? It's looks that's my /dev/sda1 partition is dead right?

---

