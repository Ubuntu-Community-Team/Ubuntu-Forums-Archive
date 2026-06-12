---
title: "How to find mountable devices and their device files in Linux"
date: 2010-11-22
forum: General Help
---

### Post by ravindasenarath on 2010-11-22
Hi I want to know How to find mountable devices and their device files in Linux.

Thanks

---

### Post by germanix on 2010-11-22
Should all be under "places". Find it, left click and it opens up to show you the files.

---

### Post by chickenSandwich on 2010-11-25
You might enjoy the command line: **mount**

---

### Post by efflandt on 2010-11-25
**sudo fdisk -l** (small L) will list all partitions on any connected devices that Linux can see (unless they are Windows Dynamic Volumes).  But as mentioned, **Places** can mount anything Linux is familiar with using a click of the mouse.

---

### Post by Morbius1 on 2010-11-25
And don't forget about the ever popular:
```
sudo blkid -c /dev/null
```

---

