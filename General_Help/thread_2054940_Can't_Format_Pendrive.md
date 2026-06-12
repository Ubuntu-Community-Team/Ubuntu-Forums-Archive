---
title: "Can't Format Pendrive"
date: 2012-09-08
forum: General Help
---

### Post by Raihan004 on 2012-09-08
how i format pendrive from kubuntu/linux mint kde using dolpin file manager .
I didnt find any option for format pendrive .
guys any one help me?

---

### Post by vasilbelarus on 2012-09-08
You cann`t do that with dolphin, try special app(K partition manager, gparted) instead.

---

### Post by Raihan004 on 2012-09-08
> **vasilbelarus said:**
> You cann`t do that with dolphin, try special app(K partition manager, gparted) instead.
how i format using k partion manager step by step?

---

### Post by The Cog on 2012-09-08
I don't think dolphin can do it. I would use either gparted or gnome-disk-utility, both packages are in the repositories. If you use gnome-disk-utility, it might appear in the menu as Disk Utility, or if not the command to start it is **palimpsest**. There might be a KDE based utility but if so I don't know its name.

You could always just use the command line - use ```
sudo fdisk -l
``` to see what device the pendrive is, and then something like ```
sudo mkfs.vfat /dev/sdb1
```to do the formatting - just make sure you get the device letter/number right.

---

### Post by Raihan004 on 2012-09-08
> **The Cog said:**
> I don't think dolphin can do it. I would use either gparted or gnome-disk-utility, both packages are in the repositories. If you use gnome-disk-utility, it might appear in the menu as Disk Utility, or if not the command to start it is **palimpsest**. There might be a KDE based utility but if so I don't know its name.

You could always just use the command line - use ```
sudo fdisk -l
``` to see what device the pendrive is, and then something like ```
sudo mkfs.vfat /dev/sdb1
```to do the formatting - just make sure you get the device letter/number right.
how i unmount pendrive ?

sudo mkfs.vfat /dev/sdb1
mkfs.vfat 3.0.12 (29 Oct 2011)
mkfs.vfat: /dev/sdb1 contains a mounted file system.
raihan@raihan-desktop ~ $ 
 if multiple pendrive connect then how i find my desire pendrive which i want format .

---

### Post by The Cog on 2012-09-08
You can unmount the pendrive with the command ```
sudo umount /dev/sdb1
```
As for knowing which pendrive is which device, that can be tricky. the command **mount** will list all the mounted partitions, and you can then try to match the device names with the contents you see in /media with your file manager. Actually, in the side panel of your file manager (nautilus?) you may find the option to unmount the drive without having to use the command line.

---

### Post by vasilbelarus on 2012-09-08
I don`t use kde now so I can`t give you step by step instructions. But you should find app in your menu (named like partition manager) and then use it`s user frendly interface.

---

### Post by Epodx64 on 2012-09-08
From the K menu go to Systems--->KDE Partition Manager then it's pretty straight forward from there make sure you're formatting the pendrive and not your hdds.

---

### Post by tienlbhoc on 2012-09-08
can use hirentboot, it have many strong tools.
But maybe your pendriver is error driver, window have some tool to reinstall usb driver :guitar:

---

### Post by Raihan004 on 2012-09-08
> **Epodx64 said:**
> From the K menu go to Systems--->KDE Partition Manager then it's pretty straight forward from there make sure you're formatting the pendrive and not your hdds.

here cant find format option just find delet and creat option !?
can you tell me which option work for format?

---

### Post by Raihan004 on 2012-09-08
> **The Cog said:**
> You can unmount the pendrive with the command ```
sudo umount /dev/sdb1
```As for knowing which pendrive is which device, that can be tricky. the command **mount** will list all the mounted partitions, and you can then try to match the device names with the contents you see in /media with your file manager. Actually, in the side panel of your file manager (nautilus?) you may find the option to unmount the drive without having to use the command line.

nope my file manager dolpin .

after unmount how i mount my pendrive again?

---

### Post by The Cog on 2012-09-08
> **Raihan004 said:**
> after unmount how i mount my pendrive again?
To be honest, the easiest way is to unplug and re-plug it in the USB port. But the traditional way would be to create a directory for it to mount to, and then mount it there, like this:
```
sudo mkdir /mnt/mypen
sudo mount /dev/sdb1 /mnt/mypen
```

---

### Post by vasilbelarus on 2012-09-11
> **The Cog said:**
> To be honest, the easiest way is to unplug and re-plug it in the USB port. 

Fully agree!

---

