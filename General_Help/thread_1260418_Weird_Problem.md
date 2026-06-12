---
title: "Weird Problem"
date: 2009-09-07
forum: General Help
---

### Post by psychofish25 on 2009-09-07
I woke up today to find my partitions were completely erased, yet my files were still in tact. 

I went into GParted (on my live CD because I cannot boot to any partitions) and found that my second hard drive (OS X, Ubuntu, Windows 7) was completely gone and displayed as "unallocated."

Then I tried TestDisk, which found my partitions, yet when I selected WRITE, my partitions still seemed to be missing. Even weirder, on my Live CD I can clearly see my partitions now, and access my files. 

OUTPUT of sudo fdisk -l

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18534   148874323+   7  HPFS/NTFS
/dev/sda2           18535       19457     7413997+   7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xde8d5746

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       10309    82807011   83  Linux
/dev/sdb2           10310       27713   139797630    7  HPFS/NTFS
/dev/sdb3           27714       38155    83875365   af  Unknown
/dev/sdb4           38156       38914     6096667+   f  W95 Ext'd (LBA)
/dev/sdb5           38157       38913     6080571   82  Linux swap / Solaris
``` 

Clearly my partitions are there, but GParted still won't display them, and I cannot boot to them.

PLEASE HELP!
Jordan

---

### Post by ozorba on 2009-09-07
First, check your Grub settings. menu.lst file should be in /boot/grub directory.
Second check that you have not deleted your /etc/fstab file as the file structure is define in this.

---

### Post by psychofish25 on 2009-09-07
I believe the problem occured when I was attempting to make more room for my Mac OS X partition. In doing so, I may have formatted my Ubuntu partition. Is there a way I can recover from this?

---

