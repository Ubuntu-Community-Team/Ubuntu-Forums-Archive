---
title: "How to make ubuntu 11.10 mount all partitions at start up automatically ?"
date: 2012-05-17
forum: General Help
---

### Post by Docmero on 2012-05-17
Hi , how to make ubuntu 11.10 mount all partitions at start up automatically ?
I need an easy method please because I'm a very beginner in this system ?
Thanks

---

### Post by carl4926 on 2012-05-17
You'd need to edit /etc/fstab
But it's not for the novice.
And what you are asking for might not be a good idea. There is a reason it's the way it is.

You should post theresult of

```
cat /etc/fstab
```
and
```
sudo fdisk -l
```

Tell us what each partition is, even if it looks obvious to you.

---

### Post by Docmero on 2012-05-17
```
**cat /etc/fstab**
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb3 during installation
UUID=ee9603e7-f9e7-4acf-85a2-0e40342a7dec /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb6 during installation
UUID=ba6ca202-8dde-400c-be28-8977a0218396 /home           ext4    defaults        0       2
# swap was on /dev/sdb4 during installation
UUID=750e1331-ac2c-40af-bd2b-e2703b9d413b none            swap    sw   
```and
```
**sudo fdisk -l**
Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7c562b93

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   327679999   163736576    7  HPFS/NTFS/exFAT
/dev/sda3       327680000   850745343   261532672    7  HPFS/NTFS/exFAT
/dev/sda4       850745344  1465145343   307200000    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1d34d691

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   307194929   153597433+   7  HPFS/NTFS/exFAT
/dev/sdb2       372625406   976768064   302071329+   f  W95 Ext'd (LBA)
/dev/sdb3   *   307195904   356999167    24901632   83  Linux
/dev/sdb4       356999168   372623359     7812096   82  Linux swap / Solaris
/dev/sdb5       634872798   976768064   170947633+   7  HPFS/NTFS/exFAT
/dev/sdb6       372625408   634871807   131123200   83  Linux

Partition table entries are not in disk order

```I want to mount ***_all partitions_*** because I need them to run my virtual system .If I mount the partitions where the virtual system file is located ***_only_*** , my shared folders on other partitions will disappear from the virtual system and then I'll have to mount them all manually to reach my files in the virtual system . So I must mount all partitions at system start up .
What is the reason for not making Ubuntu to mount them all at start up ?!!!!
Thanks

---

### Post by laliperro on 2012-05-17
Hi. For mount all partitions at start up I always do this :

1- Go to the software center and install a program called PySDM

Pysdm is a PyGTK-based Storage Device Manager that allows full customization of hard disk mount points without the need to edit fstab manually. It also allows the creation of udev rules for dynamic configuration of storage devices.

2- After installation, enter into the program, and click "by default" at each partition. It`s very easy, you will see.

Regards.

---

### Post by Docmero on 2012-05-18
I tried using the app , but I couldn't !! I didn't find any auto mount option !!
Thanks

---

### Post by Docmero on 2012-05-18
any other method ?

---

