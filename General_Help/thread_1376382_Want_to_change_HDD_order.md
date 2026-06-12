---
title: "Want to change HDD order"
date: 2010-01-09
forum: General Help
---

### Post by bimaljr on 2010-01-09
Hello 

I have one 160GB ATA HDD and ubuntu is installed on this hdd.

Now this HDD has some bad sectors so I need to send this HDD to company to replace.

I have inserted a new 320GB SATA hdd and installed Ubuntu on it to start my work. 

Here is my "fdisk -l" output :

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d1b9f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+   7  HPFS/NTFS
/dev/sda2            2433       19457   136753312+   5  Extended
/dev/sda5            2433        4864    19535008+   7  HPFS/NTFS
/dev/sda6            4865        9727    39062016    7  HPFS/NTFS
/dev/sda7            9728       14590    39062016    7  HPFS/NTFS
/dev/sda8           14591       19251    37439451   83  Linux
/dev/sda9           19252       19457     1654663+  82  Linux swap / Solaris

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e9099

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3039    24410736    b  W95 FAT32
/dev/sdb2            3040       38913   288157905    5  Extended
/dev/sdb5            3040       15197    97659103+   b  W95 FAT32
/dev/sdb6           15198       27355    97659103+   b  W95 FAT32
/dev/sdb7           27356       33434    48829536    b  W95 FAT32
/dev/sdb8           33435       33556      979933+  82  Linux swap / Solaris
/dev/sdb9           33557       38913    43030071   83  Linux
bimal@bimal-desktop:~$ 

```

Now I want to remove the old 160GB hdd. But when I remove it Grub cannot start.

How can I make it work?

Thanks

---

### Post by ajgreeny on 2010-01-09
You should be able to simply go into the BIOS and change the first boot device to the other hard disk, as I suspect that with only the one disk the system is being confused.  I admit I do not know what the disk possibilities in BIOS will be once you have removed the original disk, but I can think of nothing else to do.

---

### Post by QLee on 2010-01-09
bimaljr,
From your description, there is a good chance that when you installed Ubuntu to the second HDD you installed GRUB to the MBR of the first HDD. Thus when no first HDD, no GRUB.

It's likely that with just the second HDD in the system you could install GRUB to the MBR of that drive and solve your problem.

---

### Post by Leppie on 2010-01-09
boot into the linux install on sdb, then install grub to the mbr of sdb:
```
sudo grub-install /dev/sdb
```

check that the references to the partitions in grub.cfg or menu.lst are UUID and not /dev/xxxx

---

