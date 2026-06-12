---
title: "Creating a USB Windows Installer in Ubuntu"
date: 2010-04-09
forum: General Help
---

### Post by Happyfase on 2010-04-09
I need to install windows on my machine through a USB but I'm struggling to make the USB bootable in linux. I can do this on Windows but I don't have access to a windows machine. I have the install disc and large enough USB which I have booted from before. My bios does allow for booting from flash memory. I've scoured the internet but I can only find articles on making Linux usb installers.

---

### Post by darolu on 2010-04-09
I haven't tried this but it may work, dump the cd to the pendrive:
```
$ dd if=/dev/cdrom0 of=/dev/sdb1
```
Of course you may need to change the paths accordingly. You may need to add the boot flag to your pendrive partition using gparted too.

---

### Post by halj32 on 2010-04-09
you could try using "Windows 7 USB DVD Download Tool" running in wine or crosssover

---

### Post by Happyfase on 2010-04-10
No use, I think I'll just have to find a windows machine and do it on that.

---

