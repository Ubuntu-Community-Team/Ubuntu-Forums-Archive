---
title: "Fstab: Entry for dev/!! !!UNKNOWN DEVICE!!"
date: 2009-11-06
forum: General Help
---

### Post by [=Vion=] on 2009-11-06
In 9.10 I can only boot in text via recovery mode and when i go to etc/fstab this shows up:

Entry for /dev/sda6:
UUID=(Lots of weird numbers) /ext3 relatime,errors=remount/ro 01
#Entry for /dev/ !!UNKNOWN DEVICE!! :
UUID= (More numbers) none swap sw 00
/dev/scd0/ media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 
/dev/scd0/ media/HQ
/dev/scd0/ media/XP

Help me plz

---

### Post by pastalavista on 2009-11-06
Please post the output from ```
sudo fdisk -l
```

---

### Post by ranch hand on 2009-11-06
ext3?

This is an upgrade from 9.04 (installed on ext3 for some reason) isn't it?

---

### Post by [=Vion=] on 2009-11-06
> **pastalavista said:**
> Please post the output from ```
sudo fdisk -l
```

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 secvtors/tracks, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier : 0x1549f232

/dev/sda1   * 1        12748   102398278+    7   HPFS/NTFS
/dev/sda2     12749    30401   141797722+    5   Extended
/dev/sda5     12749    19856   57094978+     7   HPFS/NTFS
/dev/sda6     19857    29888   80582008+     83  Linux
/dev/sda7     29889    30401   4120641       82  Linux swap / Solaris

---

### Post by [=Vion=] on 2009-11-06
> **ranch hand said:**
> ext3?

This is an upgrade from 9.04 (installed on ext3 for some reason) isn't it?

yup

---

### Post by [=Vion=] on 2009-11-06
bump?

---

### Post by ranch hand on 2009-11-06
I think the output of;
```

blkid

```would be helpful.

It is a bunch of weird numbers.

Do you have MS on sda1?  What flavor?

A little more info on your box would be nice too.

---

