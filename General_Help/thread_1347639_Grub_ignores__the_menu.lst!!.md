---
title: "Grub ignores  the menu.lst?!??!"
date: 2009-12-06
forum: General Help
---

### Post by xc8 on 2009-12-06
Hi,

I have the 9.10 (clean installed).
When I boot the system the Grub DOES NOT display the entries of the menu.lst.. it just displays what the grub.cfg has!

I mean when I boot the system and press the ESC (to see the grub menu) I see:

Ubuntu, Linux 2.6.31-14-generic
Ubuntu, Linux 2.6.31-14-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)

(as they are on the grub.cfg !

The menu.lst has 

Ubuntu 9.10, kernel 2.6.31-16-generic
Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
Ubuntu 9.10, kernel 2.6.31-15-generic
Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
Ubuntu 9.10, kernel 2.6.31-14-generic
Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
Chainload into GRUB 2
Ubuntu 9.10, memtest86+

of course the 9.10 boots all the time from the 'default' 
2.6.31-14-generic

I even tried the 'sudo update-grub', but in vain.. the grub just 'reads' the menu from the grub.cfg and ignores the menu.lst

any help/ideas?

thank you in advance

chris

---

### Post by oldos2er on 2009-12-06
Grub2 doesn't use menu.lst. See [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

