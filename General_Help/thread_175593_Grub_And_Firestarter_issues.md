---
title: "Grub And Firestarter issues"
date: 2006-05-13
forum: General Help
---

### Post by learning curve on 2006-05-13
1. How do i get grub to stop.  I only want to load Ubuntu automatically?

2.  Why does Firestarter ask for a password and how do I get it to stop and just load automatically?

---

### Post by xXx 0wn3d xXx on 2006-05-13
[QUOTE=learning curve]1. How do i get grub to stop.  I only want to load Ubuntu automatically?

2.  Why does Firestarter ask for a password and how do I get it to stop and just load automatically?[/QUOTE]
You need grub to load Ubuntu. It's a bootloader. Refer to [http://ubuntuforums.org/showthread.php?t=173420&highlight=firestarter+startup](http://ubuntuforums.org/showthread.php?t=173420&highlight=firestarter+startup) to get firestarter at startup with no password.

---

### Post by duff on 2006-05-13
[QUOTE=learning curve]1. How do i get grub to stop.  I only want to load Ubuntu automatically?[/QUOTE]

edit /boot/grub/menu.lst
look for the line  "timeout 10" and change the 10 to a 1.  That won't get rid of the grub screen, but it'll go by faster

---

