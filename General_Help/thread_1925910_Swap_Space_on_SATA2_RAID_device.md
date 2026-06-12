---
title: "Swap Space on SATA2 RAID device"
date: 2012-02-15
forum: General Help
---

### Post by capecodbay on 2012-02-15
I installed onto two 500GB SATA2 hard drives in RAID 1 configuration. I partitioned and formatted swap space during the installation. But now swapon -s, top and free -m are reporting no swap space and I can't get it to work by troubleshooting via previous answers. 

I've tried using mkswap /dev/mapper/isw_bjcefhejeg_Volume0p5, mkswap isw_bjcefhejeg_Volume5, mkswap /dev/sda5, mkswap /dev/dm-0p5 and every  other reference to the existing partition I can find.

The following are my setting:

/etc/fstab
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/isw_bjcefhejeg_Volume0p1 /               ext3    errors=remount-ro 0       1
/dev/mapper/isw_bjcefhejeg_Volume0p5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sdc1       /tbdrv-1        ext3    defaults,errors=remount-ro      0       1
/dev/sdd1       /tbdrv-2        ext3    defaults,errors=remount-ro      0       1

```

fdisk -l shows the following:
```

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ca2e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       58810   472385536   83  Linux
/dev/sdb2           58810       60801    15995905    5  Extended
/dev/sdb5           58810       60801    15995904   82  Linux swap / Solaris

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ca2e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       58810   472385536   83  Linux
/dev/sda2           58810       60801    15995905    5  Extended
/dev/sda5           58810       60801    15995904   82  Linux swap / Solaris

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001   83  Linux

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      121601   976760001   83  Linux

Disk /dev/dm-0: 500.1 GB, 500104826880 bytes
255 heads, 63 sectors/track, 60800 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ca2e4

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-0p1   *           1       58810   472385536   83  Linux
/dev/dm-0p2           58810       60801    15995905    5  Extended
/dev/dm-0p5           58810       60801    15995904   82  Linux swap / Solaris

Disk /dev/dm-2: 483.7 GB, 483722788864 bytes
255 heads, 63 sectors/track, 58809 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/dm-3: 16.4 GB, 16379805696 bytes
255 heads, 63 sectors/track, 1991 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


```

ls -lah /dev/disk/by-uuid shows the following:
```

lrwxrwxrwx 1 root root  10 Feb 15 09:12 0960ed9a-894a-47e8-bce6-fa703f1b9992 -> ../../sda5
lrwxrwxrwx 1 root root  10 Jan 27 18:02 25a5a006-7654-4728-82f7-6dcc89f77d0f -> ../../sdc1
lrwxrwxrwx 1 root root  10 Jan 27 18:02 e621d9be-50dd-4200-904f-04b4b5215753 -> ../../sda1
lrwxrwxrwx 1 root root  10 Jan 27 18:02 f3af3557-fd54-4c37-8508-12546b6800a0 -> ../../sdd1
```

blkid shows following:
```
/dev/mapper/isw_bjcefhejeg_Volume01: UUID="e621d9be-50dd-4200-904f-04b4b5215753" SEC_TYPE="ext2" TYPE="ext3" 
/dev/mapper/isw_bjcefhejeg_Volume05: UUID="0960ed9a-894a-47e8-bce6-fa703f1b9992" TYPE="swap" 
/dev/sdb1: UUID="e621d9be-50dd-4200-904f-04b4b5215753" TYPE="ext3" 
/dev/sdb5: UUID="0960ed9a-894a-47e8-bce6-fa703f1b9992" TYPE="swap" 
/dev/sda1: UUID="e621d9be-50dd-4200-904f-04b4b5215753" TYPE="ext3" 
/dev/sda5: UUID="0960ed9a-894a-47e8-bce6-fa703f1b9992" TYPE="swap" 
/dev/sdc1: UUID="25a5a006-7654-4728-82f7-6dcc89f77d0f" TYPE="ext3" 
/dev/sdd1: UUID="f3af3557-fd54-4c37-8508-12546b6800a0" TYPE="ext3" 

```

free -m show:
```

             total       used       free     shared    buffers     cached
Mem:          7998       7905         93          0        854       6129
-/+ buffers/cache:        921       7077
Swap:            0          0          0

```

---

### Post by dcstar on 2012-02-16
> **capecodbay said:**
> I installed onto two 500GB SATA2 hard drives in RAID 1 configuration. I partitioned and formatted swap space during the installation. But now swapon -s, top and free -m are reporting no swap space and I can't get it to work by troubleshooting via previous answers. 
..........

There is no sane reason to put Swap on a RAID device, this is ephemeral data that does not have to survive disk failure and will only slow down your system.

Simply change the /etc/fstab file to use the appropriate Swap partition on one of your disks.

---

### Post by capecodbay on 2012-02-16
I realize swap is ephemeral and probably shouldn't be on a RAID device. The RAID device was the only disk installed in the machine when I installed the OS. And those disks have better performance, although maybe not in RAID mode. I will likely change it but I'd also like to learn how make it work as it is currently setup to work.

---

