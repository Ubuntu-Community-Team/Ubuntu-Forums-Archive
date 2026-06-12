---
title: "Invisible Grub"
date: 2010-10-27
forum: General Help
---

### Post by The Eight-Bit Link on 2010-10-27
I have Xubuntu 10.04, an upgrade from 9.10
Grub is not, and never has, been visible, save for an error:
Error: Unknown command 'Terminal'
Dell Inspiron 2500
I need it to change my password.

---

### Post by AlphaLexman on 2010-10-27
Do you have grub1 or grub2?
```
ls /boot/grub/
```
and look for:
menu.lst
or
grub.cfg

Post the contents of whichever one you have.

---

### Post by cgroza on 2010-10-27
Hold the Shift key during boot to make it show up.

---

