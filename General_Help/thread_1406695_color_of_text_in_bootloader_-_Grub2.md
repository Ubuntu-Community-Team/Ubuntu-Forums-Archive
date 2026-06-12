---
title: "color of text in bootloader - Grub2"
date: 2010-02-14
forum: General Help
---

### Post by rs422 on 2010-02-14
Hi:

I'm trying to change the font color of the text of the bootloader in Grub2. I'm running 9.10.
I successfully edited the Grub cfg file change the colors of the Grub menu, but I'd like to change the text color as I watch the modules load and can't seem to do it. I'd also like to password protect the bootloader if possible. I installed startupmanager but the new version won't allow these changes. I like to see my modules as they load and wanted to change the color from white to blue.

Any tips would be appreciated.

---

### Post by ironclaw on 2010-02-16
The information on the [Grub2]("https://help.ubuntu.com/community/Grub2") page at the Ubuntu Community Documentation should answer your questions.

Also, for GRUB 2, it is recommended not to manually edit the /boot/grub/grub.cfg file, and instead edit /etc/default/grub and /etc/grub.d/40_custom for customizations.

---

### Post by rnerwein on 2010-02-16
hi
you must have "very" important data on your box.
why you will change grub. all you have to do is give your bios "boot" a password.
be happy that grub comes up ! 
don't change a running system !
ciao

---

