---
title: "Need to recover the MBR of Windows."
date: 2012-08-21
forum: General Help
---

### Post by AADAS on 2012-08-21
When i try to recover the mbr of the windows with root@ubuntu:~/Downloads/ms-sys-2.2.1# ms-sys --mbr /media/2664D21C64D1EF15
i get an error:
Unable to open /media/2664D21C64D1EF15, Is a directory
How ubuntu sees my c drive?

btw. i need to recover my windows emergency!!!

---

### Post by AADAS on 2012-08-21
here is the partition table

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    74043584    37021761    7  HPFS/NTFS/exFAT
/dev/sda2        74043585   156301487    41128951+   5  Extended
/dev/sda3              64     4194367     2097152   a6  OpenBSD
/dev/sda5        74043648   156280319    41118336    7  HPFS/NTFS/exFAT

Partition table entries are not in disk order

---

### Post by coffeecat on 2012-08-21
This:

> **AADAS said:**
>  root@ubuntu:~/Downloads/ms-sys-2.2.1# ms-sys --mbr /media/2664D21C64D1EF15

...looks as though you are trying to write the Windows mbr code to your Windows C: partition. This is an extremely bad idea - it doesn't belong there. If you are trying to restore the Windows MBR, it needs to be written to the - MBR! Which is the first 440 or so bytes of the hard drive, not in a partition.

Is this what you are trying to do? If so, you need to write the mbr code to /dev/sda. I have no experience of the ms-sys utility, but there are other ways of restoring the Windows MBR. The best way is to use the recovery console from a Microsoft Windows install disc, the same version as your installation, i.e. XP for XP and Windows 7 for Windows 7. If you do not have a Microsoft installation disc, then you can use an Ubuntu live CD. See here:

[http://ubuntuforums.org/showpost.php?p=8950739&postcount=7](http://ubuntuforums.org/showpost.php?p=8950739&postcount=7)

Three alternative methods. For the third you do not have to "sudo apt-get install syslinux" because the file /usr/lib/syslinux/mbr.bin is already there. If you do choose the third, be very very careful. The command dd has the potential to be destructive if you make a typo. 

Be sure that you really want to restore the Windows MBR. If you are not sure, post back with more details.

---

### Post by AADAS on 2012-08-21
Ok I have tried to install openBSD on hdd with already existing windows(and even now i don`t know why i did not install it on vmware:D ).There is option to make manual the mbr for the openbsd i have used the 2 slot but also i have set the start offset to 65(guess where is the start offset for windows:D).

---

### Post by coffeecat on 2012-08-21
I have no experience of OpenBSD, nor do I know which bootloader it uses, but the link I provided should enable you to restore the Windows MBR. That should get you booting into Windows but not OpenBSD.

---

