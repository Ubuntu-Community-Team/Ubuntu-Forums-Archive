---
title: "Bootmanager"
date: 2006-05-17
forum: General Help
---

### Post by tris203 on 2006-05-17
I tried to install another boot manager (GAG) instead of the standard GRUB, but that was unable to find my Linux distro, only my win XP. Is it possible to install GRUB again without re-installing Ubuntu?

Also, once Grub is installed is it possible to set a timer so that it loads XP after 10 seconds?

Or could someone recomend another Boot loader that will recognise my Linux and my windows, and give me a timer. I would like it saved in the MBR not on a removable drive too.

---

### Post by frodon on 2006-05-17
You can set the timer and the boot order in the /boot/grub/menu.lst file, this thread will help you : 
[http://ubuntuforums.org/showthread.php?t=146162](http://ubuntuforums.org/showthread.php?t=146162)

To re-install GRUB you can follow this guide : 
[http://ubuntuforums.org/showthread.php?t=76652](http://ubuntuforums.org/showthread.php?t=76652)

Feel free to ask for help editing the menu.lst file, don't forget to post it here if you need help.

Good luck ;)

---

