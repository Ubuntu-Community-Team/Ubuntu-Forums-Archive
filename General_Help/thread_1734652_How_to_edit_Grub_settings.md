---
title: "How to edit Grub settings"
date: 2011-04-20
forum: General Help
---

### Post by soulcat on 2011-04-20
hi

tried to edit boot time from 10 secs, used correct commands in terminal, then the menu.lst appears but the screen is blank there is no text to edit :confused:.....help

---

### Post by Ad@m on 2011-04-20
What commands did you run and what version of ubuntu?

---

### Post by soulcat on 2011-04-20
hi

ubuntu 10.10

command: sudo gedit /boot/grub/menu.lst 

menu.lst appears blank, no text

cheers

---

### Post by Ad@m on 2011-04-20
From 10.x Ubuntu now uses grub2. You can edit the /boot/grub/grub.cfg file but this will always automatically be over written after a kernel update.

For permanent changes edit the /etc/default/grub file. Then once you have saved your changes run the command,

sudo update-grub

This will put your changes into effect.

---

### Post by soulcat on 2011-04-20
hi

cheers sorted thanx for your help......:D

---

### Post by Rubi1200 on 2011-04-20
If you are interested in a nice GUI application for editing the GRUB menu, see here:
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

---

