---
title: "Grub Loader"
date: 2009-08-06
forum: General Help
---

### Post by KostamojeN on 2009-08-06
Hi,
I'd like to remove one OS from Grub so that it can work standalone.

This is the setup...

SATA_01: UBUNTU

IDE_01: UBUNTU/ XP

I want to take out the UBUNTU/ XP drive so that the Sata drive can work standalone...

Currently if I just remove the IDE drive, Ubuntu refuses to load. The last thing that appears on the screen is the word "GRUB".

Thanks in advance for any help.
-Marc

---

### Post by baliganikhil on 2009-08-06
Edit the menu.lst and comment the lines that point to the OS that you want to block from appearing. Read how to go about it here.

[http://boff.wordpress.com/2007/01/17/editing-bootgrubmenulst-to-change-the-grub-boot-menu/](http://boff.wordpress.com/2007/01/17/editing-bootgrubmenulst-to-change-the-grub-boot-menu/)

---

### Post by KostamojeN on 2009-08-12
> **baliganikhil said:**
> Edit the menu.lst and comment the lines that point to the OS that you want to block from appearing. Read how to go about it here.

[http://boff.wordpress.com/2007/01/17/editing-bootgrubmenulst-to-change-the-grub-boot-menu/](http://boff.wordpress.com/2007/01/17/editing-bootgrubmenulst-to-change-the-grub-boot-menu/)

Thanks for your advice. I'm not sure how that will help. Since if I remove the 2nd drive, it doesn't even get to the menu... It just says GRUB at the bottom of the screen and stops.

Cheers
-Marc

---

