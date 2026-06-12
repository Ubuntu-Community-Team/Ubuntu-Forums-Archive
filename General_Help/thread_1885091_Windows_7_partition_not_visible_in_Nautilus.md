---
title: "Windows 7 partition not visible in Nautilus"
date: 2011-11-22
forum: General Help
---

### Post by Quatrix on 2011-11-22
I have Windows 7 on an SSD (sda) and everything else on a conventional hard disk (sdb):

```
   Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *        2048   250066943   125032448    7  HPFS/NTFS/exFAT

/dev/sdb1   *        2048    46651391    23324672   83  Linux
/dev/sdb3        46652760  2930272064  1441809652+   f  W95 Ext'd (LBA)
/dev/sdb5        46652823   130544189    41945683+   7  HPFS/NTFS/exFAT
/dev/sdb6       130544254  1598563889   734009818    7  HPFS/NTFS/exFAT
/dev/sdb7      1598563973  2856871079   629153553+   7  HPFS/NTFS/exFAT
/dev/sdb8      2856871162  2930272064    36700451+   7  HPFS/NTFS/exFAT
```

All of the NTFS partitions, including WIN7, are listed in /dev/disk/by-label/:

```
lrwxrwxrwx 1 root root  10 2011-11-22 13:42 DATA -> ../../sdb7
lrwxrwxrwx 1 root root  10 2011-11-22 13:42 GAMES -> ../../sdb6
lrwxrwxrwx 1 root root  10 2011-11-22 13:42 TEMP -> ../../sdb8
lrwxrwxrwx 1 root root  10 2011-11-22 13:42 UBUNTU -> ../../sdb1
lrwxrwxrwx 1 root root  10 2011-11-22 13:42 WIN7 -> ../../sda1
lrwxrwxrwx 1 root root  10 2011-11-22 13:42 WINXP -> ../../sdb5
```

However, Nautilus automatically shows all of the NTFS partitions except the Windows 7 partition /dev/sda1.  I see this in /etc/fstab:

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
```

I tried forcing fsck, but it made no difference.  Why doesn't the WIN7 partition appear automatically?

---

### Post by Quatrix on 2011-12-02
Okay, I simply commented out that line in fstab and now the Windows 7 partition appears in Nautilus.  It's not clear why the line is there in the first place, but everything seems okay now.

---

### Post by Quatrix on 2011-12-02
Okay, I simply commented out that line in fstab and now the Windows 7 partition appears in Nautilus.  It's not clear why the line is there in the first place, but everything seems okay now.

---

