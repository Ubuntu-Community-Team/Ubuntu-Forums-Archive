---
title: "What the H. am I doing? fsck"
date: 2010-05-06
forum: General Help
---

### Post by zoomiest on 2010-05-06
I am going through a LPI tutorial, and is suggests the fsck can check a file system, so I run the following, and get the following

```
allan@xu:~$ fsck -t ext4 /dev/sda5
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
/dev/sda5 is mounted.  

WARNING!!!  The filesystem is mounted.   If you continue you ***WILL***
cause ***SEVERE*** filesystem damage.

Do you really want to continue (y/n)? no

check aborted.

```

So, why am I getting such ominous messages? Can I check the file system while I am on it?

Background: Its a dual boot laptop... HP-G60
My partitions look like this:
```
allan@xu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa9c8c3bf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12078    97016503+   7  HPFS/NTFS
/dev/sda2           29086       30401    10564608    7  HPFS/NTFS
/dev/sda3           12079       29085   136608727+   5  Extended
/dev/sda5           12079       28390   131026108+  83  Linux
/dev/sda6           28391       29085     5582556   82  Linux swap / Solaris

```
Question again: isn't this a safe thing to do? Why the warnings?

---

### Post by philinux on 2010-05-06
WARNING!!!  The filesystem is mounted.   If you continue you ***WILL***
cause ***SEVERE*** filesystem damage.

Fair warning that. You need to have the filesystem **[COLOR="Red"]unmounted[/COLOR]**. Try using the livecd.

---

