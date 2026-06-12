---
title: "RAID, mdadm, 'resource busy' - ???"
date: 2006-04-08
forum: General Help
---

### Post by golfinguy on 2006-04-08
Here's the brief background:

NEW system, 5.10 AMD64 install
OS filesystem on /dev/hda
5 drives for RAID 5 all freshly partitioned for Linux raid autodetect:
/dev/sda
/dev/sdb
/dev/sdc
/dev/sdd
/dev/sde

Here's fdisk -l:

```
root@rahserver:~# fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7295    58597056   83  Linux
/dev/hda2            7296        9729    19551105    5  Extended
/dev/hda5            7296        9483    17575078+  83  Linux
/dev/hda6            9484        9729     1975963+  82  Linux swap / Solaris

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       48641   390708801   fd  Linux raid autodetect

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       48641   390708801   fd  Linux raid autodetect

Disk /dev/sdc: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       48641   390708801   fd  Linux raid autodetect

Disk /dev/sdd: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       48641   390708801   fd  Linux raid autodetect

Disk /dev/sde: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       48641   390708801   fd  Linux raid autodetect

```


When I attempt to create the array I get the following:

```
root@rahserver:~# mdadm -v --create /dev/md0 --force --chunk=32 --level=5 --spare-devices=0 --raid-devices=5 /dev/sda /dev/sdb /dev/sdc /dev/sdd /dev/sde
mdadm: layout defaults to left-symmetric
mdadm: Cannot open /dev/sda: Device or resource busy
mdadm: Cannot open /dev/sdb: Device or resource busy
mdadm: Cannot open /dev/sdc: Device or resource busy
mdadm: Cannot open /dev/sdd: Device or resource busy
mdadm: Cannot open /dev/sde: Device or resource busy
mdadm: create aborted

```

So - with NEW drives freshly partitioned and unused/mounted - what would make them appear busy??

PLEASE - any ideas?

Thanks

---

