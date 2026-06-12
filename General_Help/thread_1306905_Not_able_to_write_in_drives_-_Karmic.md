---
title: "Not able to write in drives - Karmic"
date: 2009-10-30
forum: General Help
---

### Post by bruno321 on 2009-10-30
Hi, I've just done a clean install of Kubuntu 9.10. I'm having a little problem:

First of all, it didn't automatically recognize and mount my FAT32 and NTFS partitions. That's just... wrong. Well, I started messing with fstab: I mounted the partitions, the problem is, I can't write to them. Here's my fstab:

proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=77225cc7-a19c-4dd0-b039-212f300bdeaf /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda4 during installation
UUID=3427543d-902f-499b-a72e-6a0f95dd88b1 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=24346361-6d94-4798-9614-c1ed01980aa4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdc1	/media/sdc1	auto	defaults	0	0
/dev/sda8	/media/sda8	vfat	defaults	0	0
/dev/sdb5	/media/sdb5	auto	defaults	0	0
/dev/sdb6	/media/sdb6	auto	defaults	0	0
/dev/sda1	/media/sda1	auto	defaults	0	0

Here's the output of fdisk -l:

Disco /dev/sda: 320.1 GB, 320072933376 bytes
255 cabezas, 63 sectores/pista, 38913 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0xe1c7e1c7                 

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        1913    15366141    7  HPFS/NTFS
/dev/sda2            1914       26563   198001125    f  W95 Ext'd (LBA)
/dev/sda3           26564       28387    14651280   83  Linux
/dev/sda4           28388       38913    84550095   83  Linux
/dev/sda5            1914       14662   102406311    7  HPFS/NTFS
/dev/sda6           14663       14924     2104483+  82  Linux swap / Solaris
/dev/sda7           14925       20510    44869513+  83  Linux
/dev/sda8           20511       26563    48620691    b  W95 FAT32

Disco /dev/sdb: 250.1 GB, 250059350016 bytes
255 cabezas, 63 sectores/pista, 30401 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x65968677

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1               1       29126   233954563+   f  W95 Ext'd (LBA)
/dev/sdb5               1       15201   122101969+   b  W95 FAT32
/dev/sdb6           15202       29126   111852531    b  W95 FAT32

Disco /dev/sdc: 122.9 GB, 122942324736 bytes
240 cabezas, 63 sectores/pista, 15881 cilindros
Unidades = cilindros de 15120 * 512 = 7741440 bytes
Identificador de disco: 0xe0b6b1d7

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdc1   *           2       15881   120052296    c  W95 FAT32 (LBA)



Anyway, I was trying to solve it first for sda8: I 777-chmodded the folder /media/sda8, to no avail (after umounting and mounting), etc.

---

### Post by bruno321 on 2009-10-30
It seems to have been solved with changing "defaults" to "rw,iocharset=utf8,umask=000". That's pretty incomprehensible to me, but I found it in another thread.

---

