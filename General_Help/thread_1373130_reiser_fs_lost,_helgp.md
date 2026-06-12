---
title: "reiser fs lost, helgp"
date: 2010-01-05
forum: General Help
---

### Post by FlemmingJ on 2010-01-05
hi there

within the last 24 hours I have lost a reiser formatted disk. It is not visible not with df or fdisk.
Which tools do you normally use in a situation like that.

fdisk goes like this / thanks in advance

Disk /dev/sda: 40.0 Gb, 40020664320 byte
255 heads, 63 sectors/track, 4865 cylinders
Units = cylindre of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4f14da63

    Enhed Opstart   Start         Slut     Blokke   Id  System
/dev/sda1   *           1        4660    37431418+  83  Linux
/dev/sda2            4661        4865     1646662+   5  Udvidet
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 Gb, 250059350016 byte
255 heads, 63 sectors/track, 30401 cylinders
Units = cylindre of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3718746d

    Enhed Opstart   Start         Slut     Blokke   Id  System
/dev/sdb1               1       30401   244196001    b  W95 FAT32

Disk /dev/sdc: 1000.2 Gb, 1000204886016 byte
255 heads, 63 sectors/track, 121601 cylinders
Units = cylindre of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00026685

    Enhed Opstart   Start         Slut     Blokke   Id  System
/dev/sdc1               1      121601   976760001   83  Linux

Disk /dev/sdd: 1000.2 Gb, 1000204886016 byte
255 heads, 63 sectors/track, 121601 cylinders
Units = cylindre of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003b0fb

    Enhed Opstart   Start         Slut     Blokke   Id  System
/dev/sdd1               1      121601   976760001   83  Linux

---

### Post by audiomick on 2010-01-05
Hallo.
There are four drives listed in your output. Is the one that is missing one of the four, or is it number 5?

---

### Post by Leppie on 2010-01-05
could you post the output of the following command:
```
$sudo blkid -c /etc/blkid.tab
```

---

### Post by FlemmingJ on 2010-01-06
> **Leppie said:**
> could you post the output of the following command:
```
$sudo blkid -c /etc/blkid.tab
```

here you are:

/dev/sdb1: UUID="4923-F93E" TYPE="vfat" 
/dev/sdc1: UUID="97a3c7ae-6e16-43ab-9727-ac184a37dc95" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdd1: UUID="63434818-46de-4957-956d-3894499f7c72" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda1: UUID="3ca363d6-e79d-40cd-b048-55b29a89a9a3" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sda5: TYPE="swap" UUID="8838f9f8-9e4e-3e81-b6b4-b2237694aa99" 


regards Flemming

---

### Post by FlemmingJ on 2010-01-06
> **audiomick said:**
> Hallo.
There are four drives listed in your output. Is the one that is missing one of the four, or is it number 5?

number 5 I'm affraid.

regards Flemming

---

### Post by Leppie on 2010-01-06
is the reiserfs module loaded?
```
$lsmod | grep reiser
```

---

