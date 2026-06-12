---
title: "hide windows from boot menu"
date: 2011-02-09
forum: General Help
---

### Post by sanjuk2010 on 2011-02-09
hi
i have installed ubuntu netbook remix and windows7 starter in same drive,i.e 'C'.
now i want to hide windows from boot menu so as to enable others to use ubuntu. is there some way out....

---

### Post by decrepit on 2011-02-09
There's probably a few ways of doing this.
If you're using old grub, (before version 2) you can just comment out, windows in /boot/grub/menulist
If you have grub 2 this may get undone every time you update your kernnel, (I'm not sure about this).
If you have grub2, I'd try setting ubuntu as default, then either hide the grub menu, or reduce it's time to a few seconds.
This is done by editing /etc/default/grub.

---

