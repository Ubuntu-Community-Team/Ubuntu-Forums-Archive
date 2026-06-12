---
title: "Grub errors"
date: 2009-06-30
forum: General Help
---

### Post by illbashu on 2009-06-30
I am getting Grub error 17 when i try to boot into ubuntu and grub error 22 when i try to boot into windows. how do i fix this? :(

I tried to reintall ubuntu a couple of times but it didn't work. I also tried to reinstall Grub but when i do "find /boot/grub/stage1" i get this.

```
 
grub> find /boot/grub/stage1

Error 15: File not found

```

partitions

```

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2              63  1250258624   625129281    f  W95 Ext'd (LBA)
/dev/sda5       129869523  1250258624   560194551   83  Linux
/dev/sda6             189   129580289    64790050+  83  Linux
/dev/sda7       129580353   129869459      144553+  83  Linux

Partition table entries are not in disk order

Disk /dev/hdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders, total 80293248 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x15f415f3

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1              63    41383439    20691688+   7  HPFS/NTFS
/dev/hdb2        41383440    80292869    19454715    5  Extended
/dev/hdb5        41383503    70525349    14570923+   7  HPFS/NTFS
/dev/hdb6   *    70525413    71103689      289138+  83  Linux
/dev/hdb7        71103753    80292869     4594558+  82  Linux swap / Solaris

```

---

### Post by illbashu on 2009-06-30
bump...

---

