---
title: "Removing ubuntu's default hard drive labels"
date: 2009-07-01
forum: General Help
---

### Post by Bohemenian on 2009-07-01
After some digging, if I've gotten it right "***GB Media" is a label of a hard drive.
Now I want to get rid of that for "naming/labelling" the drive after the folder I mount it in. I've done some searching about, but I didn't find any great documentation on the topic, so if someone would care to guide me through it or in the right direction, that would be swell.
cheers

---

### Post by cariboo on 2009-07-01
> **Bohemenian said:**
> After some digging, if I've gotten it right "***GB Media" is a label of a hard drive.
Now I want to get rid of that for "naming/labelling" the drive after the folder I mount it in. I've done some searching about, but I didn't find any great documentation on the topic, so if someone would care to guide me through it or in the right direction, that would be swell.
cheers

Give your drives labels, if you have gparted installed, use the partition editor to add labels to drives formated as ext3. To change ntfs drive lables, install ntfsprogs and use ntfslabel to change the labels. Both packages can be installed using Add/Remove Applications or Syanptic Package Manager.

---

### Post by michy99 on 2009-07-01
tune2fs will also label partitions.

---

### Post by Bohemenian on 2009-07-01
but if ubuntu doesn't come with these programs, there must be some file i can edit (fstab-like), right?

or is this hard-programmed default behaviour to assign each new drive the same label-model?

---

### Post by drs305 on 2009-07-01
Recent versions of gparted can label most formats if the proper software is installed. You can check from within gparted: View, Filesystem Support. If it can't label it, gparted will tell you what software you need to install (right side of display).

Install ntfsprogs and you will be able to label ntfs, as well as ext2/3/4, fat16/32 and reiserfs/reiser4 formatted partitions from within gparted.

---

### Post by Bohemenian on 2009-07-01
but there's is no file to edit?

---

