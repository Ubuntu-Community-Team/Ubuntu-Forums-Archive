---
title: "Overlapping partitions - Really?"
date: 2010-09-29
forum: General Help
---

### Post by ghedda on 2010-09-29
Hi, i have my wonderful laptop working as a charm. There are quite many partitions on one single drive:

Vista factory recovery, Windows Vista, Windows Xp, Windows swap;
Documents (NTFS), Data (NTFS);
Ubuntu Linux, Linux swap.

I don't use the first two (Vista) at all, bu everything works fine.

Any way, Gparted states for that drive:
"Not allocated" (so I cannot, if I ever would, resize etc.)
And parted doesn't print the partition list:
"Errore: Impossibile avere partizioni che si sovrappongono." (IT)
that means: "Error, you cannot have overlapping partitions."

There must be something wrong, but I'm not able to work with partition tables, so here it is
$sudo fdisk -l

```

omitting empty partition (5)

Disco /dev/sda: 160.0 GB, 160041885696 byte
255 testine, 63 settori/tracce, 19457 cilindri
Unità = cilindri di 16065 * 512 = 8225280 byte
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Identificativo disco: 0x80d2f3ee

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4186    33622012    7  HPFS/NTFS
La partizione 1 non termina al limite del cilindro.
/dev/sda2            4186       10560    51200000    7  HPFS/NTFS
La partizione 2 non termina al limite del cilindro.
/dev/sda3           10561       18282    62026965    f  W95 Esteso (LBA)
/dev/sda4           11836       14385    20480000    7  HPFS/NTFS
La partizione 4 non termina al limite del cilindro.
/dev/sda5           10562       11835    10233373+  83  Linux
/dev/sda6           14385       17955    28672000    7  HPFS/NTFS
/dev/sda7           17955       18146     1536000    7  HPFS/NTFS
/dev/sda8           18147       18282     1092388+  82  Linux swap / Solaris

Disco /dev/sdb: 60.1 GB, 60060155904 byte
255 testine, 63 settori/tracce, 7301 cilindri
Unità = cilindri di 16065 * 512 = 8225280 byte
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Identificativo disco: 0x956f956f

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7300    58637218+   7  HPFS/NTFS

```

where "La partizione # non termina al limite del cilindro." means:
"Partition # doesn't end at cylinder limit."

Should I fix this? Or don't worry about this? Or don't touch this 'cause I risk to mess up everything?

---

### Post by oldfred on 2010-09-29
Not ending on cylinders is an old issue when partitions were set up that way. Not normally an issue now.

But you you do have a partition problem. Primary partitions are sda1-4 and you have sda3 as the extended partition. sda5 and up will then be inside the primary partition. But you also have sda4 inside the extended which is not possible.

I would see if testdisk will resort this out, but you should have good backups before any changes.

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

