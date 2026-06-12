---
title: "Set the default boot loader to Windows' Boot loader?"
date: 2012-09-18
forum: General Help
---

### Post by ojdon on 2012-09-18
I have always wondered how I would set the default boot loader to Windows' boot loader instead of grub being the default one? I assume I use something like EasyBCD but I just thought I'd ask before risking damaging my system. 

Thanks!

---

### Post by iponeverything on 2012-09-18
> **ojdon said:**
> I have always wondered how I would set the default boot loader to Windows' boot loader instead of grub being the default one? I assume I use something like EasyBCD but I just thought I'd ask before risking damaging my system. 

Thanks!

is grub working? you can change the default in grub to boot anything and set the timeout to 0 so you don't even know its there..

If you are changing it just "because" - this seems more to like a pointless exercise.. regardless - google will offer plenty of ideas on restoring the bootloader..

---

### Post by Mark Phelps on 2012-09-18
IF you don't like hand-editing boot config files, then install Grub-Customizer.  When you launch it, it will put up menus that will allow you to set the default boot options.

EasyBCD is a Windows product, and if you already have GRUB installed, you would first have to remove GRUB to use that, and then figure out how to configure it to work with Ubuntu.

Using Grub-Customizer to change the GRUB boot defaults is a lot less work.

---

