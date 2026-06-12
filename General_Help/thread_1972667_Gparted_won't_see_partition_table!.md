---
title: "Gparted won't see partition table!"
date: 2012-05-03
forum: General Help
---

### Post by GameX2 on 2012-05-03
Hi,


I've tried installing Windows Server 2003 on my laptop.  I've did some ressearch before, and the advantage of installing Server 2003 over XP was that 2003 would manage my 8GB of RAM and 4 edCPUs without any problem.  I really grew tired of the 20-30 GB wasted by Windows 7, while Server 2003 could do the same with least disk space.

So knowing where I was going, knowing that Server 2003 would erased my Windows 7 bootloader as well as GRUB, I installed it in another partition.  Things didn't worked well.  The first part of the setup worked, the files got copied from the CD to the partition, but the next part failed.

So I restored 7 bootloader succesfully, and I am willing to restore GRUB now from Ubuntu, but there is a major problem, Gparted would not detect anymore partition! :O

The partitions are still there: they are detected by Super GRUB Disk, and Windows 7.  Ubuntu does detect my Windows 7 partition (SDA2), because it was mounted at boot time, but that's all.  GParted just show a "Unallocated Space" on all the disk.  Before restoring GRUB and forget about Server 2003, I need to fix this problem.  Another thing, Server 2003 seems to have erased a Recovery partition for Windows 7 !  Not visible by Windows, nor my GRUB CD..  Is there any way to recover it?

Which command should I enter in the terminal?


Thanks a bunch for helping me!

EDIT: Here's the output of sudo fdisk -l :


```
partition vide ignorée (5)

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 têtes, 63 secteurs/piste, 38913 cylindres, total 625142448 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Taille de secteur (logique / physique)*: 512*octets / 512*octets
taille d'E/S (minimale / optimale)*: 512*octets / 512*octets
Identifiant de disque*: 0xc88c59eb

Périphérique Amorce  Start        End      Blocs     Id  System
/dev/sda1   *        2048     3074047     1536000    7  HPFS/NTFS/exFAT
/dev/sda2         3074048   385523711   191224832    7  HPFS/NTFS/exFAT
/dev/sda3       385523712   592371711   103424000    5  Extended
/dev/sda4       467445760   508405759    20480000   83  Linux
/dev/sda5       385525760   467443711    40958976    7  HPFS/NTFS/exFAT
/dev/sda6       508407808   570865663    31228928   83  Linux
/dev/sda7       570867712   571891711      512000   82  partition d'échange Linux / Solaris
/dev/sda8       571893760   592371711    10238976    7  HPFS/NTFS/exFAT
```

Sda1 : System_DRV (Boot partition for Windows 7);
Sda2 : Windows7_OS;
Sda3 : An Extended partition;
Sda4 : Ubuntu_OS;
Sda5 : Windows Server 2003 partition I created..
Sda6 : Ubuntu_Home (Strange, because in the partition table, the partition for Windows 2003 was placed *before* Ubuntu OS and Home, not in between.
Sda7 : Linux_Swap;
Sda8 : Backups;

---

### Post by GameX2 on 2012-05-04
Can anyone help?

Thanks :)

EDIT: Solved; I used a recovery partition utily, and deleting a useless partition fixed GParted, simply.  As for the lost partition, it seems that it's recoverable.  It's found as "Deleted" by this utility!

---

