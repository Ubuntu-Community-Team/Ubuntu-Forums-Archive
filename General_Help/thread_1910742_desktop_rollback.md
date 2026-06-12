---
title: "desktop rollback"
date: 2012-01-17
forum: General Help
---

### Post by sweetmax on 2012-01-17
Hi,

for 1 H ago installed ubuntu 11.10 and I realy hate this version of gnome. it's slow and ohhhh
however how can I switch back to old style? 

thanks in advance

---

### Post by Double.J on 2012-01-17
Hi there, Don't want to risk this ending up in recurring so i'll point you towards [CharlesA's thread]("http://ubuntuforums.org/showthread.php?t=1859960")

---

### Post by Scott Baker on 2012-01-17
Question here. Is it the speed of the system, or the interface of the new version? Some people don't dig the new Unity interface. If it's the interface, and not the actual speed that's making you crazy, go to the terminal and type the following; [COLOR=Blue]sudo apt-get install gnome- panel[/COLOR]. Log out, then when you see the gear show up on your log in screen, click that and you'll be offered the option to log back into the "classic session." Try that before "rolling back" your distro to see if that feels better. Good luck.

---

### Post by epic.mint on 2012-01-18
you can get back gnome 2.3 by installing the MATE desktop environment from the linux mint repositories here's a guide
[HTML]http://ubuntuguide.net/ubuntu-11-10-install-classic-gnome2-desktop-linux-mint-mate[/HTML]WARNING:this may harm your system. i have tried it and it works for me but it might not for you.

Edit: forgot to mention MATE is the fork of gnome 2.3 used in linux mint 12

---

### Post by sweetmax on 2012-01-18
thank you guys. I hate everything about this interface. this command solved my problem. sudo apt-get install gnome- panel
thanks again :)

---

