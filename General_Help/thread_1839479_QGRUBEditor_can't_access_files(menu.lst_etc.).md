---
title: "QGRUBEditor can't access files(menu.lst etc.)"
date: 2011-09-05
forum: General Help
---

### Post by al1x on 2011-09-05
Hello there, I've just installed QGRUBEditor and I can't run the program because I get the following message:

QGRUBEditor was unable to read/write access to one of the following files:
/boot/grub/menu.lst
/boot/grub/device.map
/etc/mtab

Then, I run sudo qgrubeditor and the same message appears...How can I give privileges to qgrubeditor to access this files?

---

### Post by ajgreeny on 2011-09-05
The error message is because neither  /boot/grub/menu.lst  nor  /boot/grub/device.map  exist in a 10.04 installation of Ubuntu./  Those files are present in systems using legacy grub, Ubuntu 10.04 uses grub2.

What are you trying to do with QGRUBEditor?  It can probably still be done, but in a different way.

---

### Post by drs305 on 2011-09-05
For modiftying Grub 2 menus and options a good app is Grub Customizer. See the link in my signature line.

For repairing Grub 2, YannBuntu has developed the Boot Repair app:
[http://ubuntuforums.org/showthread.php?t=1769482#post10976174]("http://ubuntuforums.org/showthread.php?t=1769482#post10976174")

---

### Post by al1x on 2011-09-05
> What are you trying to do with QGRUBEditor? It can probably still be done, but in a different way.

I would like to have a program with GUI to configure Grub instead of doing this manually(editing the menu.lst), so as to change the timeout, the priority of menu entry and to be able to add an image in the background.

---

### Post by drs305 on 2011-09-05
> **al1x said:**
> I would like to have a program with GUI to configure Grub instead of doing this manually(editing the menu.lst), so as to change the timeout, the priority of menu entry and to be able to add an image in the background.

Take a look at Grub Customizer then. It can do all those things.

---

### Post by al1x on 2011-09-05
Thanks a lot, I just installed it! So QGRUBEditor doesn't work anymore with the new Grub2?

---

### Post by drs305 on 2011-09-05
> **al1x said:**
> Thanks a lot, I just installed it! So QGRUBEditor doesn't work anymore with the new Grub2?

Just checking Launchpad, the last upload was in 2007 for Hardy. So I seriously doubt it would work with Grub 2 unless there was a later version kicking around somewhere else. The Launchpad version is 2.5.0.

---

### Post by al1x on 2011-09-05
Oh ok, the GC seems pretty good anyway!:D

---

