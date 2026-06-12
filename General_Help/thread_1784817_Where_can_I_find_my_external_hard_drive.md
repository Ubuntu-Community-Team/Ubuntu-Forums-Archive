---
title: "Where can I find my external hard drive?"
date: 2011-06-17
forum: General Help
---

### Post by MasterZii on 2011-06-17
I just plugged in a 698GB external hard drive into my computer and ran Xubuntu. But it doesn't show up on the desktop. I am new to this OS, where can I find it? I would like to make some backups.

---

### Post by Zero2Nine on 2011-06-17
> **MasterZii said:**
> I just plugged in a 698GB external hard drive into my computer and ran Xubuntu. But it doesn't show up on the desktop. I am new to this OS, where can I find it? I would like to make some backups.

Is it listed when you run:
```
ls /media
```?

Does it show up in Thunar (the file manager) on the left side somewhere?

Are there other icons on your desktop or is it without any icons? Maybe desktop icons are disabled. This is a possible setting in XFCE, just don't know exactly where to find it (not using Xubuntu now).

---

### Post by pqwoerituytrueiwoq on 2011-06-17
you may need to mount it
never have to do that with a non-internal drive on xubuntu before

---

### Post by MasterZii on 2011-06-17
It doesn't show up anywhere. Like it's not even plugged in. There are other icons on the desktop, like the home icon, and my internal drive icon. And a couple others. But the external isn't anywhere to be found. I can't mount it because it doesn't show up in file manager or anything either. But I will try using the code, i'm just new to the Ubuntu OS's so I have no idea what I am doing.

---

### Post by Zero2Nine on 2011-06-17
If it is plugged in run

```
sudo fdisk -l
```

This lists all drives and partitions. it should be there. For example I have an external drive with two partitions listed as dev/sde1 and dev/sde2

---

### Post by pqwoerituytrueiwoq on 2011-06-17
> **MasterZii said:**
> It doesn't show up anywhere. Like it's not even plugged in. There are other icons on the desktop, like the home icon, and my internal drive icon. And a couple others. But the external isn't anywhere to be found. I can't mount it because it doesn't show up in file manager or anything either. But I will try using the code, i'm just new to the Ubuntu OS's so I have no idea what I am doing.
i meant from the command line
although gparted should be able to mount it

---

