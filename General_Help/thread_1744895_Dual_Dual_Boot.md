---
title: "Dual Dual Boot"
date: 2011-04-30
forum: General Help
---

### Post by porksoda on 2011-04-30
I have two Boot Loaders running for some reason.

The first boot loader to appear is Windows Boot Manager with the option of loading either Ubuntu or Windows 7.

If I choose Windows 7, it will boot Windows 7 right away.

BUT! If I choose Ubuntu, it loads yet another boot loader, GRUB, with the option of loading Ubuntu, Ubuntu Safe boot, and Windows 7.

I like GRUB better. How do I get rid of Windows Boot Manager?

I've tried using msconfig>boot, but it only shows Windows 7.

---

### Post by Rubi1200 on 2011-04-30
Hi and welcome to the forums :-)

This is a Wubi install correct?

If yes, that is just the way it works. Wubi uses the Windows bootloader to do its thing. If you were to try and use GRUB as the primary bootloader, neither Windows nor Wubi would boot.

Therefore, my advice is to leave things as they are unless you want to do a proper dual-boot with Ubuntu installed to the hard-drive. In that case, GRUB would be installed to the MBR, thus allowing you to use it to choose which OS to boot.

---

### Post by porksoda on 2011-04-30
OOOOOOOOOOHhhhhhhhhhhhhhhhhh... Thanks! ^_^

---

