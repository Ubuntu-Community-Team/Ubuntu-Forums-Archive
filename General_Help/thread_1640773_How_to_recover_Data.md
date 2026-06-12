---
title: "How to recover Data"
date: 2010-12-08
forum: General Help
---

### Post by sm_ashiq on 2010-12-08
I  unknowingly formatted my whole 160GB hard disk to ext4 file system from Fat while installing Ubuntu. Now my hard disk has only one ext4 partition. Please help me to recover my old data.
Thank you in anticipation.

---

### Post by I'mGeorge on 2010-12-08
> **sm_ashiq said:**
> I  unknowingly formatted my whole 160GB hard disk to ext4 file system from Fat while installing Ubuntu. Now my hard disk has only one ext4 partition. Please help me to recover my old data.
Thank you in anticipation.

If it was about completely deleting something than there are some recovery programs, but if it's about formating a partition and changing it's file system from windows to a linux specific one than I'm pretty sure you can say R.I.P to your lost data.

---

### Post by philinux on 2010-12-08
> **sm_ashiq said:**
> I  unknowingly formatted my whole 160GB hard disk to ext4 file system from Fat while installing Ubuntu. Now my hard disk has only one ext4 partition. Please help me to recover my old data.
Thank you in anticipation.

Whatever you do dont use the drive. You'll need an external drive and the livecd. You need this. [http://www.cgsecurity.org/](http://www.cgsecurity.org/)

Install testdisc when in the livecd and use photorec, which is part of testdisc, to recover any data to the external hard drive.

From the livecd open a terminal and post back with what this shows.

```
sudo fdisk -l
```

---

