---
title: "Just changed graphics rosolution in STARTUP MANAGER!   ooooops!"
date: 2010-01-18
forum: General Help
---

### Post by benrufus on 2010-01-18
Hi

I just stupidly changed my graphics resolution in System - Preferences - Startup Manager, now i dont get a login window or anything just a black screen. I also disabled the splash but i assume this just gets rid of the ubuntu loading line thingy? any help would be much appreciated......

the weird thing is that the resolution was set to 640x800 or something like that in the Startup Manager as default and the laptop im using (an old Toshiba Amilo P4) supports 1024x768. the System - Preferences - Display menu wouldnt let me change any display settings which is why i was messing about here. I havent got any backed up x org file and only a live usb of super os/ubuntu - no cd or floppy drive. Please please help

---

### Post by spiderbatdad on 2010-01-18
Boot into recovery mode. Edit /boot/grub/menu.lst or /etc/default/grub (depending on your release).
See startup manager documentation for where to edit.
[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)

---

