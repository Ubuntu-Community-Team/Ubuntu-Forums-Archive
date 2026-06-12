---
title: "Identify current linux installation partition"
date: 2011-03-15
forum: General Help
---

### Post by ondemanddesign on 2011-03-15
Is there a command to identify my current Ubuntu partition?

As you can see from my fdisk listing, I have 3 OS's currently running (Windows XP, Ubuntu Desktop, and Ubuntu Server). I need to identify which one is Ubuntu server so I can make backups of only that partition.

```
ubuntu@ubuntuDev2:/$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x28000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3794    30468750    7  HPFS/NTFS
/dev/sda2            3794        7296    28135425    5  Extended
/dev/sda5            4940        7193    18091008   83  Linux
/dev/sda6            7193        7296      833536   82  Linux swap / Solaris
/dev/sda7            3794        4885     8767488   83  Linux
/dev/sda8            4885        4940      435200   82  Linux swap / Solaris

```

Hope someone can help, thanks.

---

### Post by TeoBigusGeekus on 2011-03-15
```
df -h
```
will show you your partitions and where they're mounted, as well as their sizes.
The partition mounted on /, will be your root partition.

---

### Post by ondemanddesign on 2011-03-15
> **TeoBigusGeekus said:**
> ```
df -h
```
will show you your partitions and where they're mounted, as well as their sizes.
The partition mounted on /, will be your root partition.

Awesome, thanks for the very quick response. This is solved.

---

