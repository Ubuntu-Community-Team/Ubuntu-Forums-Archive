---
title: "Silicon Image Raid 5"
date: 2010-08-14
forum: General Help
---

### Post by ElJollyRancher on 2010-08-14
Hi,
 
Very new to Linux, but lots of Windows experience. I am getting tired of Windows and want a more open OS, so I installed Ubuntu as a dual boot with my Vista box. Install was great and most everything is working. I do however have a Silcon Image PCI Raid controller card with 4 500gb drives in a Raid5 array on this system. My windows box sees the raid array just fine, but I cannot see it in Ubuntu. In the disk management window, Ubuntu sees that the SI3114 driver is installed and sees the controller, it also sees 4 drives. How do I see this array in Ubuntu? Thank you for your help.

---

### Post by m1lkman on 2011-01-19
bump

Same issue - 4x drives in RAID 5.  Individual drives and controller are visible in disk utility.

```

hwinfo --storage

36: PCI 304.0: 0104 RAID bus controller
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_1095_3124
  Unique ID: AMUB.FE9tEZ91SW0
  Parent ID: B35A.2_Jx267KDMD
  SysFS ID: /devices/pci0000:00/0000:00:04.0/0000:02:00.0/0000:03:04.0
  SysFS BusID: 0000:03:04.0
  Hardware Class: storage
  Model: "Silicon Image SiI 3124 PCI-X Serial ATA Controller"
  Vendor: pci 0x1095 "Silicon Image, Inc."
  Device: pci 0x3124 "SiI 3124 PCI-X Serial ATA Controller"
  SubVendor: pci 0x1095 "Silicon Image, Inc."
  SubDevice: pci 0x7124 
  Revision: 0x02
  Driver: "sata_sil24"
  Driver Modules: "sata_sil24"
  Memory Range: 0xfbcffc00-0xfbcffc7f (rw,non-prefetchable)
  Memory Range: 0xfbcf0000-0xfbcf7fff (rw,non-prefetchable)
  I/O Ports: 0xcc00-0xcc0f (rw)
  Memory Range: 0xfbc00000-0xfbc7ffff (ro,prefetchable,disabled)
  IRQ: 16 (6742 events)
  Module Alias: "pci:v00001095d00003124sv00001095sd00007124bc01sc04i00"
  Driver Info #0:
    Driver Status: sata_sil24 is active
    Driver Activation Cmd: "modprobe sata_sil24"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #35 (PCI bridge)


```

```

fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2e022e03

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2e022e02

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2e022e01

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdc: 16.0 GB, 16039018496 bytes
22 heads, 48 sectors/track, 29664 cylinders
Units = cylinders of 1056 * 512 = 540672 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           6       29665    15659976    c  W95 FAT32 (LBA)

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2e022e04

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008785f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1       59583   478597120   83  Linux
/dev/sdf2           59583       60802     9787393    5  Extended
/dev/sdf5           59583       60802     9787392   82  Linux swap / Solaris

Disk /dev/sdg: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bad10

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1       59570   478491648   83  Linux
/dev/sdg2           59570       60789     9787393    5  Extended
/dev/sdg5           59570       60789     9787392   82  Linux swap / Solaris


```

---

