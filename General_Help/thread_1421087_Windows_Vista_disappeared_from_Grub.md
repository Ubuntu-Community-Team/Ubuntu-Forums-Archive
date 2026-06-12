---
title: "Windows Vista disappeared from Grub"
date: 2010-03-03
forum: General Help
---

### Post by tharpa on 2010-03-03
In trying to fix Windows suddenly not booting, I have arrived at the point where it does not even appear in Grub, and I cannot even begin to start it.

Any suggestions?

Thanks.

---

### Post by Sef on 2010-03-03
Applications > Accessories > Terminal

then copy and paste this code:

```
sudo fdisk -l
```

Then copy and paste the results here.

Note: The code will tell us what partitions you have and where they are.

---

### Post by tharpa on 2010-03-03
> **Sef said:**
> Applications > Accessories > Terminal

then copy and paste this code:

```
sudo fdisk -l
```Then copy and paste the results here.

Note: The code will tell us what partitions you have and where they are.

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           8       64228+  de  Dell Utility
/dev/sda2               9        1967    15728640    7  HPFS/NTFS
/dev/sda3   *        1967       60802   472592384    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8d399bc0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       59672   479315308+  83  Linux
/dev/sdb2           59673       60801     9068692+   5  Extended
/dev/sdb5           59673       60801     9068661   82  Linux swap / Solaris

---

### Post by oldfred on 2010-03-04
Are you booting from sda or sdb. If may be difficult to tell in BIOS since they are both 500GB. With my two 160GB drives I just choose one if that does not work choose the other. 
It would be best to have grub in sdb the Ubuntu drive (and in BIOS be first) and you can leave the windows boot loader in sda.
If you do not have the windows loader in sda and cannot boot windows you will need to repair windows. Set sda as the first drive in BIOS and do the windows repairs. Then once it works set sdb as first and boot Ubuntu.

---

