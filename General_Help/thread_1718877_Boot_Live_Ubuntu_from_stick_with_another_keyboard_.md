---
title: "Boot Live Ubuntu from stick with another keyboard layout?"
date: 2011-04-01
forum: General Help
---

### Post by spielball on 2011-04-01
Is there a way to tell Ubuntu which locale / keyboard layout to use when starting it as a Live system from usb stick? I have a multiboot stick and in my menu.lst the following entry for Ubuntu 10.10 Live:

```
title Ubuntu 10.10 Live 
find --set-root /ubuntu-10.10-desktop-i386.iso 
map /ubuntu-10.10-desktop-i386.iso (0xff) 
map --hook 
root (0xff) 
kernel /casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper iso-scan/filename=/ubuntu-10.10-desktop-i386.iso quiet splash -- 
initrd /casper/initrd.lz
```Is there a parameter to start the live desktop with a German keyboard layout?

---

### Post by spielball on 2011-04-01
Problem solved.

```
-- locale=de_DE console-setup/layoutcode=de 
```Result:

```
title Ubuntu 10.10 Live (without installing) German 
find --set-root /ubuntu-10.10-desktop-i386.iso 
map /ubuntu-10.10-desktop-i386.iso (0xff) 
map --hook 
root (0xff) 
kernel /casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper iso-scan/filename=/ubuntu-10.10-desktop-i386.iso quiet splash -- locale=de_DE console-setup/layoutcode=de 
initrd /casper/initrd.lz
```:D

---

