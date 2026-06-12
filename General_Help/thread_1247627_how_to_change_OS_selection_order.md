---
title: "how to change OS selection order"
date: 2009-08-23
forum: General Help
---

### Post by ivine on 2009-08-23
Hi everyone,
I have installed Ubuntu as well as windows XP in my laptop.
I want to change the order of appearence.
Can anyone tell me how to do that.

---

### Post by t4ggs on 2009-08-23
yes edit /boot/grub/menu.lst

u can do that by entering this command in a terminal
sudo gedit /boot/grub/menu.lst
then enter your password

say if you need more help

---

### Post by ks07 on 2009-08-23
> **t4ggs said:**
> yes edit /boot/grub/menu.lst

u can do that by entering this command in a terminal
sudo gedit /boot/grub/menu.lst
then enter your password

say if you need more help
Just a quick point. Use
```
gksudo gedit /boot/grub/menu.lst
```
at the terminal. Sudo is for command line, gksudo for graphical applications.

---

