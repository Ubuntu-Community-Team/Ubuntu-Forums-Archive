---
title: "How can i change Dual boot order in ubuntu 9.10 karmic koala"
date: 2009-11-01
forum: General Help
---

### Post by Leapz4fun on 2009-11-01
hi iam a noob in ubuntu.. i want to ask a question:
How i can change the dualboot order in my ubuntu 9.10.. (Iam using ubuntu and windows xp) when i start the computer the grub also point to ubuntu first. How i can change that windows xp is my first boot order.. and how can i set the countdown time in grub?.

---

### Post by anishd on 2009-11-14
I am not a noob to ubuntu. They have complicated the thing too much that this kind of simple things which were possible previously has become too obscure. I am also searching for an answer.

---

### Post by GermanJew on 2009-12-16
After reading [http://ubuntuforums.org/showthread.php?t=34393](http://ubuntuforums.org/showthread.php?t=34393) and trying all of the approaches (except grubconf) the grub menu on boot up just doesn't change! The changes I made in menu.lst does not show in the grub menu on bootup. 

Is this a new issue with 9.10? What else can i try?

---

### Post by tomian67 on 2009-12-30
I am a newbie to linux.  It took me about an hour to figure out how to change the boot order in ubunta or linux mint 8.  The simplest way to do it is go into TERMINAL and type sudo gedit /etc/default/grub.  You will come up with a menu that you can change the boot order plus time out.  After you make your changes, you exit out of the menu and click save at the top of the menu.  You come back to TERMINAL and type sudo update-grub, and your set to go.  If i can do it, anyone can.

---

### Post by MelDJ on 2009-12-30
install startup-manager from synaptic....

---

