---
title: "USB devices only mount at startup"
date: 2011-02-21
forum: General Help
---

### Post by stdrogo on 2011-02-21
After reformatting a usb drive with gparted, no usb stick will automount when I plug it in anymore. If the usb is in place at startup, however, it is recognized and mounted. The media will show up in fdisk and disk utility, but there is no link to it in Places > Computer. I have no trouble manually mounting, but I would rather not have to go through the hassle each time I plug in my flash stick. I am running Ubuntu 10.10 64bit. Thank-you in advance.

---

### Post by adduds on 2011-03-11
I'll bump ya on this post i can only get the usb stick to mount through

sudo mount /dev/sdb1 /media/usb

ubuntu see's it in lsusb and sudo fdisk -l

but won't automount?

have you checked alt+f2 gconf-editor --> apps--> nautilus --> preferences --> media_automount is checked?

i did and it is but still won't work...

formatted to ext4 and fat32 neither worked...

drive works as soon as i plug it into my laptop though

---

