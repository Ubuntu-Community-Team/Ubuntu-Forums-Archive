---
title: "Can't see DVD Properties"
date: 2012-01-21
forum: General Help
---

### Post by uRock on 2012-01-21
I am using ubuntu 11.10.

There is no longer an icon on the desktop for inserted disks and going to /Media and right clicking the image does not show the disk's properties.

Is there any way to get the system to place an icon on the desktop, such was the default in previous editions, or is there another way to get to disk properties?

Thanks:D

---

### Post by howefield on 2012-01-21
Try running this in terminal..

```
gsettings set org.gnome.nautilus.desktop volumes-visible true
```

---

### Post by uRock on 2012-01-21
That worked! Thanks howefield! :P

---

### Post by howefield on 2012-01-22
You're welcome, glad to help :)

---

