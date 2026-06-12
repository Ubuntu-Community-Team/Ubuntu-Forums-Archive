---
title: "Mouse scrolling changed after upgrade to 9.10"
date: 2009-11-01
forum: General Help
---

### Post by frank4360 on 2009-11-01
With 9.04 I had smooth scrolling using the mouse scroll wheel - after upgrading to 9.10 the scrolling is jerky (complete screen refreshes on each line scrolled).

I can't see how to change the mouse behaviour (System - Preferences - Mouse doesn't allow any changes to scrolling).

Any ideas?

---

### Post by frank4360 on 2009-11-03
This problem has resolved itself with the fixing of the booting problem


[I]

I have edited the /boot/grub/menu.lst file and removed "splash" from the default boot line.

The entry was:-

title Ubuntu 9.10, kernel 2.6.31-14-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.31-14-generic root=UUID=d268c13e-75b3-4ab0-81cc-11feb01f2beb ro quiet splash
initrd /boot/initrd.img-2.6.31-14-generic
quiet

it is now:-

title Ubuntu 9.10, kernel 2.6.31-14-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.31-14-generic root=UUID=d268c13e-75b3-4ab0-81cc-11feb01f2beb ro quiet
initrd /boot/initrd.img-2.6.31-14-generic
quiet

The boot now works - but I don't know what effect, if any, the "splash" parameter had!!![/I]

---

