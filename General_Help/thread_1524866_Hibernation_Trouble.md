---
title: "Hibernation Trouble"
date: 2010-07-05
forum: General Help
---

### Post by phinfinity on 2010-07-05
I used to be able to hibernate and resume properly with the exception of a stuck up touch-pad after resume. However once while repartitioning the location of my swap partition got shifted and hence i manually edited /etc/fstab to point to it again. but now whenever I Hibernate it does so and powers off. but when I try to resume it comes with a clean fresh boot with a login display. my hibernate states are lost. the only difference when i login is that my network adapters are disabled. today i upgraded to the 2.6.32-23 kernel from the 2.6.32-22. Now I can't even Hibernate It seems to write to the harddisk for a long time and then my screen saver starts up again my screen locked. I can login and everything is as i left it. Now it doesn't even hibernate. Can someone help me with this?

```
uname -a
Linux phinfinity-laptop 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 i686 GNU/Linux

```
```

sudo fdisk -l
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          49      393561   de  Dell Utility
/dev/sda2   *          50          62      102400    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3              62        5149    40857600    7  HPFS/NTFS
/dev/sda4            5149       38914   271215617    f  W95 Ext'd (LBA)
/dev/sda5            5149       20088   120000000    7  HPFS/NTFS
/dev/sda6           32938       35428    19999744   83  Linux
/dev/sda7           20088       32937   103209984    b  W95 FAT32
/dev/sda8           38131       38913     6289416   82  Linux swap / Solaris
/dev/sda9           35429       38130    21703783+  83  Linux

Partition table entries are not in disk order

```
```

sudo blkid
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07DA-0406" TYPE="vfat" 
/dev/sda2: LABEL="System Reserved" UUID="A02C752C2C74FF1A" TYPE="ntfs" 
/dev/sda3: UUID="BED87EC4D87E7B0B" TYPE="ntfs" 
/dev/sda5: LABEL="STOR" UUID="CEF2EF29F2EF148D" TYPE="ntfs" 
/dev/sda6: UUID="e78ed638-8ed6-487a-9932-5fe954ce63ca" TYPE="ext3" 
/dev/sda7: LABEL="TOFORMAT" UUID="6319-4463" TYPE="vfat" 
/dev/sda8: UUID="c01b8b4b-6dbc-4df7-9425-0b41b2bae7c5" TYPE="swap" 
/dev/sda9: UUID="b987679c-5b82-4ffe-98fa-c8648eddc67e" SEC_TYPE="ext2" TYPE="ext3" 

```
```

cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=e78ed638-8ed6-487a-9932-5fe954ce63ca /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
# swap shifted by error to /dev/sda8
/dev/sda8 none swap sw 0 0
#UUID=c01b8b4b-6dbc-4df7-9425-0b41b2bae7c5 none swap sw 0 0

```
I Have tried using UUID as well instead of /dev/sda8 in fstab

---

