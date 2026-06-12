---
title: "dual boot ubuntu and XP"
date: 2009-10-23
forum: General Help
---

### Post by nicol_bolas on 2009-10-23
Ok I have ubuntu installed on an encrypted LVM hard drive, and I recently added a hard drive with XP on it and was wondering how to add windows to my boot record?

---

### Post by blazemore on 2009-10-23
Okay firstly, open up a terminal and type
```
sudo fdisk -l
```

Please post the output here

---

### Post by nicol_bolas on 2009-10-23
sudo fdisk -l


```

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00320031

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          31      248976   83  Linux
/dev/sda2              32       10011    80164350    5  Extended
/dev/sda5              32       10011    80164318+  83  Linux

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3bb63bb6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       13722   110221933+   c  W95 FAT32 (LBA)

```

---

### Post by blazemore on 2009-10-23
Do you have your XP drive connected? That should be showing up as well.

---

### Post by nicol_bolas on 2009-10-23
The XP Drive is
/dev/sdb1   *           1       13722   110221933+   c  W95 FAT32 (LBA)

---

### Post by egalvan on 2009-10-23
> **nicol_bolas said:**
> The [COLOR="Red"]XP[/COLOR] Drive is
/dev/sdb1   *           1       13722   110221933+   c  W95 [COLOR="Red"]FAT32[/COLOR] (LBA)

XP on FAT32 is asking for trouble.

FAT32 does not have the extended file attributes that NTFS has,
and that XP relies on.

Take care.

---

### Post by nicol_bolas on 2009-10-23
Yea, It came like that and I don't have the disks to reinstall

---

