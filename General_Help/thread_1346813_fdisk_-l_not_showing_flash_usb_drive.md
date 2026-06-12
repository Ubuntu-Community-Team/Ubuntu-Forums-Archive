---
title: "fdisk -l not showing flash usb drive"
date: 2009-12-05
forum: General Help
---

### Post by jmz2 on 2009-12-05
My system is an ubuntu remix 9.10

Since few days my USB flash drive is not showing on the system.

I can not mount it and when I do 'fdisk -l' the USB flash info is not commind up:

> xxx@akoya:~$  sudo fdisk -l
[sudo] password for xxx: 

Disco /dev/sda: 160.0 GB, 160041885696 bytes
255 cabezas, 63 sectores/pista, 19457 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x7ea727c6

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1               1        2008    16129228+   7  HPFS/NTFS
/dev/sda2   *        2009        4175    17404928    7  HPFS/NTFS
/dev/sda3            4176       16023    95169060    5  Extendida
/dev/sda4           16024       19457    27583605    c  W95 FAT32 (LBA)
/dev/sda5           14662       15901     9960268+  83  Linux
/dev/sda6           15902       16023      979933+  82  Linux swap / Solaris
/dev/sda7            5740       14661    71665902   83  Linux
/dev/sda8            4176        4940     6144799+  83  Linux

Las entradas de la tabla de particiones no están en el orden del disco



What can I do to solve this?

Is not a problem of the USB drive or the computer because it is working when I boot my windows partition in the same computer.

Another strange thing is that an icon for cdrom0 is apperaring in the 'files and folders' menu area. How can I remove this icon and why is it appearing if don't have a cd on my netbook?

---

