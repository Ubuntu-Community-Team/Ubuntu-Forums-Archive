---
title: "Disable read only files for editing for GRUB2?"
date: 2010-01-15
forum: General Help
---

### Post by talkingtree on 2010-01-15
Hi,

I tried to follow "Configuring GRUB 2" at /etc/default/grub (file) in the instruction at [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

But the file is read only? How do I make it so that it can be modified

ie GRUB_DEFAULT=0 to GRUB_DEFAULT=1

---

### Post by efflandt on 2010-01-15
It is probably only "read only" for the user you are trying to edit it from.  You need to use sudo to edit and save it as root.  So either run **gksudo gedit /etc/default/grub** from a terminal, or **sudo nano -w /etc/default/grub**.

PS: I changed mine to **GRUB_DEFAULT=saved** so the default is whatever successfully booted last

---

### Post by talkingtree on 2010-01-15
oh wow this is so cool! thanks for teaching =saved function!

---

### Post by Leppie on 2010-01-15
it's easier to use menu entries instead of numbers for GRUB_DEFAULT. for example:
```
GRUB_DEFAULT="Microsoft Windows XP (loader) (on /dev/sda1)"
```
would boot xp on my machine. you need the exact menu entry for this however. you can find it like this:
```
cat /boot/grub/grub.cfg | grep Windows
```

---

### Post by talkingtree on 2010-01-15
wow so many cool options, thanks for sharing

---

