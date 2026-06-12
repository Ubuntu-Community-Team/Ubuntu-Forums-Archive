---
title: "USB Help Please..."
date: 2011-09-21
forum: General Help
---

### Post by manthanm on 2011-09-21
i tried installing ubuntu on my usb, but some things failed. now i deleted all the ubuntu files, but when i was installing ubuntu is split up my usb into two. Is there any way i can fix this???

---

### Post by wolfen69 on 2011-09-21
You can use Gparted to reformat the drive.
```
sudo apt-get install gparted
```
Then
```
gksu gparted
```
Then in the upper right hand corner of gparted, select your usb drive from the pull down menu. Delete all partitions and reformat it to fat32.

---

