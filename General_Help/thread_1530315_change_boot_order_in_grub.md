---
title: "change boot order in grub"
date: 2010-07-13
forum: General Help
---

### Post by Namarpus on 2010-07-13
I want to change the default boot from Ubuntu to windows xp.  What file do I need to edit to make that change?  In other distros the file is grub.lst but I can not locate that file name in Ubuntu.

I can find the file /boot/grub/grub.cfg that looks like what I need but has a warning "DO NOT EDIT",

Thanks ... Mike

---

### Post by pbolle on 2010-07-13
/boot/grub/grub.conf
/etc/grub.conf

look in either of those.
Im guessing it will be in the second one.

Look for a line that says
default=0

If you want the default operating system to be windows, and on your grub menu, windows is 2nd on the list, change that line to be

default=2
(it could be 1 or 2, im not sure if it counts 0 or not)
hope i helped :D

---

### Post by mike555 on 2010-07-13
or install "startup manager "...........

---

### Post by mikewhatever on 2010-07-13
The tile to edit would be /etc/default/grub. The way to change the default boot option to Windows is to edit the first line:
```
GRUB_DEFAULT="insert menu entry for Windows here"
```
The menu entry is the text in quotes from /boot/grub/grub.cfg.
The one for Ubuntu looks like this (don't have Windows):
```
menuentry 'Ubuntu, with Linux 2.6.32-23-generic'
```
You can easily lookup all menu entries with this command:
```
cat /boot/grub/grub.cfg | grep menuentry
```

---

### Post by pbolle on 2010-07-13
> **mike555 said:**
> or install "startup manager "...........
or that :P

---

### Post by Namarpus on 2010-07-13
I finally made the change to grub and all is well. 

Thanks for all the great assistance.

Mike

---

