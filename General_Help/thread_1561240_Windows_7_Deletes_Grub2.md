---
title: "Windows 7 Deletes Grub2"
date: 2010-08-26
forum: General Help
---

### Post by dankdave on 2010-08-26
I booted into Windows 7 three times this summer and each time I did, upon restart grub was missing.  In fact, the computer couldn't find any operating system, and displayed an error "No Module Name Found".

Any ideas on how to make windoze not commit suicide and delete grub?

I have a Dell Studio 1557.

:~$ uname -a
Linux dell-monsters 2.6.32-24-generic #41-Ubuntu SMP Thu Aug 19 01:38:40 UTC 2010 x86_64 GNU/Linux

:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe64000e2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        1918    15360000    7  HPFS/NTFS
/dev/sda3            1918       11689    78487034+   7  HPFS/NTFS
/dev/sda4           11689       60802   394499073    5  Extended
/dev/sda5           11689       58809   378488832   83  Linux
/dev/sda6           58809       60802    16009216   82  Linux swap / Solaris

:~$ grub-setup -V
grub-setup (GRUB) 1.98-1ubuntu7

---

### Post by dankdave on 2010-08-26
PS - this is a return of the earlier problem I posted here:

[http://ubuntuforums.org/showthread.php?t=1522219](http://ubuntuforums.org/showthread.php?t=1522219)

---

### Post by dankdave on 2010-08-26
It turns out removing Dell DataSafe from the windows side solves the problem.

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1459782](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1459782)
[http://ubuntuforums.org/showthread.php?t=1343851](http://ubuntuforums.org/showthread.php?t=1343851)

If you have a Dell laptop, and want to run a dual boot with grub2, remove Dell Data Safe!

---

