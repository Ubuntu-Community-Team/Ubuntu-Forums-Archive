---
title: "Weird login screen."
date: 2011-03-11
forum: General Help
---

### Post by deadstarr on 2011-03-11
I've been trying to change my login screen for the past two hours.
It's not the normal purple-ish one, it's this blue one that is really ugly.
I've tried about everything, Including Ubuntu Tweak and yes I put the background in the background folder as a admin. I'm running Ubuntu 10.10. The install I used was the netbook edition, but i'm using the desktop edition through it... Any help at all would be great... btw I've read almost every forum on this topic... I haven't seen anyone even mention that they have a blue login screen.

---

### Post by deadstarr on 2011-03-11
Ok, I'm self bumping. I want to figure this out before I go to bed.

---

### Post by Megaptera on 2011-03-11
Would Grub Customiser be any help perhaps? 
[http://www.webupd8.org/2010/11/grub-customizer-20-can-change-default.html](http://www.webupd8.org/2010/11/grub-customizer-20-can-change-default.html)
Quote and caps not mine!
GRUB CUSTOMIZER 2.0 CAN CHANGE THE DEFAULT GRUB2 BOOT ENTRY, MENU COLORS, BACKGROUND IMAGE AND LOTS MORE

---

### Post by deadstarr on 2011-03-11
I got that and everything, But does that change my login screen background? That and why is mine blue instead of the purpleish that it is for everyone else?

---

### Post by Krytarik on 2011-03-12
It may be that you are using another display manager than GDM, maybe KDM or XDM.
Please check the content of "/etc/X11/default-display-manager".

---

### Post by deadstarr on 2011-03-12
Ok it says /usr/bin/kdm... which means I'm using KDM right... If I switch that to /usr/bin/gdm will that change it?

---

### Post by deadstarr on 2011-03-12
Ok I figured it out. Thanks very much... All I had to do was type sudo dpkg-reconfigure gdm in terminal... that was actually really easy.

---

### Post by Krytarik on 2011-03-12
> **deadstarr said:**
> Ok it says /usr/bin/kdm... which means I'm using KDM right... If I switch that to /usr/bin/gdm will that change it?
I would instead change it that way:
```
sudo dpkg-reconfigure gdm
```
Then follow the first steps of my guide to modify the login screen:
[http://ubuntuforums.org/showthread.php?p=10468340](http://ubuntuforums.org/showthread.php?p=10468340)

---

