---
title: "Fixing Windows with Ubuntu Live CD..."
date: 2009-09-21
forum: General Help
---

### Post by BarefootSoul83 on 2009-09-21
Is there a way to access the C:\ (on a Windows machine) through a Ubuntu Live CD?

nasty trojan horse....

Note: it is not in Places---->Computer (unfortunately)

---

### Post by chriskin on 2009-09-21
> **BarefootSoul83 said:**
> Is there a way to access the C:\ (on a Windows machine) through a Ubuntu Live CD?

nasty trojan horse....

Note: it is not in Places---->Computer (unfortunately)

it wouldn't be called C:/ , are you sure you checked them all?

---

### Post by GrfyGrumpyBear on 2009-09-21
You should mount the partition first.

Install the NTFS Configuration Tool i think it's

> Sudo apt-get install ntfs-3g

Then you would see a disk called "hd#" (#=the partition number)

---

### Post by cybergalvez on 2009-09-21
> **BarefootSoul83 said:**
> Is there a way to access the C:\ (on a Windows machine) through a Ubuntu Live CD?

nasty trojan horse....

Note: it is not in Places---->Computer (unfortunately)

just use the live disk, open nautilus (places->home) and look for the name of your infected HD in the list of on the left, double click and it should just mount.

---

### Post by Marlonsm on 2009-09-21
I've already done it sometimes.
The live CD will see the Windows partition (C:\) as an external media device, it'll show as "160Gb Media", for example.

---

