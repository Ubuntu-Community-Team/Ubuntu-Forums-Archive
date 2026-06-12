---
title: "Dual Booting SUSE/Ubuntu"
date: 2010-08-23
forum: General Help
---

### Post by fleamour on 2010-08-23
Is it possible to dual boot openSUSE & Ubuntu through GRUB 2?  Apparently SUSE uses standard GRUB.  I installed SUSE but only have Ubuntu options displayed on boot.

---

### Post by anirudhtomer on 2010-08-23
I have RedHat, Ubuntu, SUSE and windows 7 on my machine so its possible & also my boot loader is GRUB 2. Even if u install SUSE at the end it should not give a problem coz whatever the bootloader is , its job is to show to entries from the 4 "16 bytes portion of MBR".

Donno why ur system is behaving differently.

---

### Post by fleamour on 2010-08-23
Well the SUSE installer is more complicated & less user friendly then Ubuntu's.  Will have another go.

I boot from 2nd dedicated Linux HDD from F11 pop up menu at POST because Windows 7 is not GRUB friendly. AFAIK I installed SUSE GRUB to 2nd HDD's MBR rather than 1st HDD where Windows resides.

I set up equal partitions for "/" & "/home" for both Ubuntu & SUSE sharing swap:

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7ffd62f1

Device Boot Start End Blocks Id System
/dev/sdb1 31374 60802 236382937+ 5 Extended
/dev/sdb2 1 1216 9766496 83 Linux
/dev/sdb3 2432 31373 232471846+ 83 Linux
/dev/sdb4 * 1217 2431 9759487+ 83 Linux
/dev/sdb5 60315 60802 3906560 82 Linux swap / Solaris
/dev/sdb6 31374 60314 232468519+ 83 Linux

Partition table entries are not in disk order

Disk /dev/sda: 160.0 GB, 160041885696 bytes
100 heads, 5 sectors/track, 625163 cylinders
Units = cylinders of 500 * 512 = 256000 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa10bd000



Device Boot Start End Blocks Id System
/dev/sda1 * 1 163840 40959997+ 7 HPFS/NTFS
/dev/sda2 163841 625157 115329024 7 HPFS/NTFS

---

### Post by fleamour on 2010-08-23
I think all was needed was:

```
sudo update-grub
```

---

