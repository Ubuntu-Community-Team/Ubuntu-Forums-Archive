---
title: "sfdisk -l question ?"
date: 2010-11-20
forum: General Help
---

### Post by whitetimer on 2010-11-20
Ok i have just run the following command and got this out put
Disk /dev/sda: 30401 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0
   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+   9725    9726-  78124063+   7  HPFS/NTFS
/dev/sda2       9726   13372    3647   29294527+  83  Linux
/dev/sda3      13373   30400   17028  136777410   83  Linux
/dev/sda4          0       -       0          0    0  Empty
I have no idea what the sda4 partition is .....
Is it safe to delete & what is the best way to delete this partition ?
Many Thanks

---

### Post by coffeecat on 2010-11-20
> **whitetimer said:**
> dev/sda4          0       -       0          0    0  Empty
I have no idea what the sda4 partition is .....
Is it safe to delete & what is the best way to delete this partition ?

That's just a quirk of the way sfdisk outputs. It's telling you there is no sda4, so there's nothing to delete. You are allowed four primary partitions with the mbr partition table, one of which can be an extended partition. It's simply that slot 4, as it were, is unused. Try...

```
sudo fdisk -lu
```

... and you will get a more reassuring output.

---

### Post by whitetimer on 2010-11-20
> **coffeecat said:**
> That's just a quirk of the way sfdisk outputs. It's telling you there is no sda4, so there's nothing to delete. You are allowed four primary partitions with the mbr partition table, one of which can be an extended partition. It's simply that slot 4, as it were, is unused. Try...

```
sudo fdisk -lu
```

... and you will get a more reassuring output.

Many thanks for the Advice ... I can rest in peace now ;)

---

