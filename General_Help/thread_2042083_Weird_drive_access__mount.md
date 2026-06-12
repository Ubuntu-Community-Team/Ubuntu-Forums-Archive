---
title: "Weird drive access / mount?"
date: 2012-08-13
forum: General Help
---

### Post by vivienneanthony on 2012-08-13
Hi

I have a weird problem. I have Ubuntu installed on my SSD drive and then mounted a HD which I created a home directory instead of using the SSD for non-operating system related programs and data.

I been having this problem where to access any executable software from a icon. I must  open Dolphin and access the mounted drive. I think I would have to go to Xterm and do the same.

Do anyone know what might be the problem?

Vivienne

---

### Post by bchurchill on 2012-08-14
Perhaps you could post the results of 'sudo fdisk -l'?  Could you give a more specific example of an icon that's being problematic?  What path did it try to access?  What was the working directory set to?  Any issues running executables from the terminal?

---

### Post by vivienneanthony on 2012-08-14
This is the fdisk and mount output. I have apps and data at /media/home2/vivienne2 which is /dev/sda1. I can access everything on it. Just when I login on the desktop it seems Kwin can't launch the apps. I usually go to Dolphin then I am able to hit the icon. 

It might be a problem with the Kwin or KDE window manager?

---------------------------------------------------------------

Fdisk
---------
Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00018097

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   849782783   424890368   83  Linux

Disk /dev/sdb: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006291b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   116850687    58424320   83  Linux
/dev/sdb2       116852734   125044735     4096001    5  Extended
/dev/sdb5       116852736   125044735     4096000   82  Linux swap / Solaris

Mounts
---------
/dev/sdb1 on / type ext4 (rw,errors=remount-ro)
/dev/sda1 on /media/home2 type ext4 (rw,nosuid,nodev,uhelper=udisks)

---

