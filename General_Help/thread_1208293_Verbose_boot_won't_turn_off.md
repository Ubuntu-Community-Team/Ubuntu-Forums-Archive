---
title: "Verbose boot won't turn off"
date: 2009-07-09
forum: General Help
---

### Post by SaxMeister13 on 2009-07-09
I'm a fairly new Ubuntu user, and with the help of some tutorials I've been tweaking my GRUB and boot options (I'm dual-booting with XP).  Recently I noticed that after the GRUB loader, the screen would display the graphical "ubuntu" with the loading bar, but it would immediately be replaced with the verbose text loading progress.

Here is the entry in /boot/grub/menu.lst: 

```
title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        36f967b8-0f1d-49b2-b269-a60c552ef346
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=36f967b8-0f1d-49b2-b269-a60c552ef346 ro quiet splash acpi=off
initrd        /boot/initrd.img-2.6.28-13-generic
ro
quiet
splash
```Any help would be grealy appreciated.  Thanks in advance!

---

### Post by nikgare on 2009-07-09
Install StartUp-Manager, this should give you some options to make the boot up how you want it.

---

### Post by SaxMeister13 on 2009-07-09
Already done.  I have the box for "Show text during boot" unchecked, but it doesn't seem to make a difference.

---

