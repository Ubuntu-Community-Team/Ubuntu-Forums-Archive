---
title: "GRUB menu.lst command not found"
date: 2009-10-25
forum: General Help
---

### Post by Nckprgo on 2009-10-25
Hello I was recently playing in my grub/boot/menu.lst in order to change the primary boot to vista.  I went through and changed the last 1 in VISTA to 0 which after doing reading I believe I told the grub that vista is on a partition which it is not as opposed to changing it to my primary boot.  This isn't too big of a deal because I figured I could just change it back if it didnt work.  Well instead what happens is now I go to terminal type in sudo /grub/boot/menu.lst and i get command not found.  So ive completely lost my vista and can not load the menu.lst file to change it back.  I have tried doing a GRUB repair from boot up and its not doing anything.  I have the live CD but I do not know what to do with it.  Can someone please help I do not think I am quite experienced enough to use Ubuntu yet and would like to get back into my vista.  So please anyone know how to give me access to my /grub/boot/menu.lst file it would be very helpful.

---

### Post by collinp on 2009-10-25
Huh?

If you are trying "sudo /grub/boot/menu.lst" exactly, that is not the right command. It should be "sudo gedit /grub/boot/menu.lst" or "sudo nano /grub/boot/menu.lst" (if you are in terminal only).

---

### Post by ajgreeny on 2009-10-25
To be absolutely exact it should be ```
gksudo gedit /boot/grub/menu.lst
```Using sudo for graphical (gui) applications as opposed to cli apps can cause big problems, though thankfully, very seldom, and luckily not with gedit.
```
sudo nano /boot/grub/menu.lst
``` is fine as nano is a cli terminal application

---

### Post by ranch hand on 2009-10-25
> **ajgreeny said:**
> to be absolutely exact it should be ```
gksudo gedit /boot/grub/menu.lst
```using sudo for graphical (gui) applications as opposed to cli apps can cause big problems, though thankfully, very seldom, and luckily not with gedit.
```
sudo nano /boot/grub/menu.lst
``` is fine as nano is a cli terminal application
+1

---

