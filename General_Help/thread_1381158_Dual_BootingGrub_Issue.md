---
title: "Dual Booting/Grub Issue"
date: 2010-01-14
forum: General Help
---

### Post by Gaddorm on 2010-01-14
Hey there,

I'm having an issue installing 2 different distributions onto my laptop.

I have a version of Mandriva InstantOn that when I install, works fine, but once I install Ubuntu 9.10, it disappears from the boot menu.  The same thing happens if I reverse the install and go with Ubuntu first.

I'm using 2 different partitions on the same drive.

When I install Mandriva, I'm installing the bootloader onto the MBR.

Does anyone have any incite that could possibly make this work?

---

### Post by Leppie on 2010-01-14
which bootloader are you using at the moment?
could you post the output of:
```
sudo blkid
```

---

