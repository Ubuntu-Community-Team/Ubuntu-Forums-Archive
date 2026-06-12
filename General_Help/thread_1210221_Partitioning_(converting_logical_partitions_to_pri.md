---
title: "Partitioning (converting logical partitions to primary)"
date: 2009-07-11
forum: General Help
---

### Post by wiatrak_ on 2009-07-11
Hi !
I tried to convert sda2 to 3 primary partitions. I want to install windows on sda6, but it must be primary.

[[IMG]http://images44.fotosik.pl/161/49558d73350cb648m.png[/IMG]]("http://www.fotosik.pl/showFullSize.php?id=49558d73350cb648")

I saw [http://ubuntuforums.org/showthread.php?t=1008458](http://ubuntuforums.org/showthread.php?t=1008458), where[[COLOR=#d40000]** caljohnsmith**[/COLOR]]("http://ubuntuforums.org/member.php?u=530779") forced it.

```
grzesiek@Grzesiek:~$ sudo sfdisk -d /dev/sda
[sudo] password for grzesiek: 
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 61432497, Id= c, bootable
/dev/sda2 : start= 61432560, size=563704785, Id= f
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start= 61432623, size=409593177, Id= 7
/dev/sda6 : start=471025863, size= 82124217, Id= 7
/dev/sda7 : start=553150143, size= 71987202, Id=83
grzesiek@Grzesiek:~$ sudo fdisk -lu

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x95c495c4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    61432559    30716248+   c  W95 FAT32 (LBA)
/dev/sda2        61432560   625137344   281852392+   f  W95 Ext'd (LBA)
/dev/sda5        61432623   471025799   204796588+   7  HPFS/NTFS
/dev/sda6       471025863   553150079    41062108+   7  HPFS/NTFS
/dev/sda7       553150143   625137344    35993601   83  Linux
```Please help.

---

### Post by carml on 2009-07-11
Backup all important data first.

---

### Post by wiatrak_ on 2009-07-11
But how to do that?
There was only 1 logic to 1 primary.

And this process can be undone, can't it?

---

### Post by wiatrak_ on 2009-07-12
Can someone help me?

Should it be looking like that:
```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 61432497, Id= c, bootable
/dev/sda2 : start= 61432623, size=409593177, Id= 7
/dev/sda3 : start=471025863, size= 82124217, Id= 7
/dev/sda4 : start=553150143, size= 71987202, Id=83
```?

---

