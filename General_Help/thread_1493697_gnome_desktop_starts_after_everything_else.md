---
title: "gnome desktop starts after everything else"
date: 2010-05-26
forum: General Help
---

### Post by todosmentira on 2010-05-26
Hi all 

I love Ubuntu but since upgrading to 10.04 have 2 probs. The first, which I have posted in another thread, is the splash screen. The second is this:
with compiz,  startup occurs in this order:

1. Gnome do dock and pointer appear on black background with no panels or desktop
2. Some hard drive activity
3. 10 secs no hard drive activity still no desktop
4.  Gnome Desktop and panels finally appear with wireless already connected

It seems to me that the Gnome/compiz desktop is loaded only after everything else, including wireless and all services/processes. Compiz works fine, I am not short of ram or resources (2 Gb + Core 2 duo@2.7ghz). My question is then, is there a way to change the order of startup so that the desktop/compiz appears more quickly?

---

### Post by garvinrick4 on 2010-05-26
If you need  splash screen to show up on boot then open a terminal and use this Code.

go to root
     Code:
     sudo -s 

fix from Scott James Remnant bug #540801
      Code:
     echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash
  update-initramfs -u 

out of root
Code:
Ctrl/D

   reboot and graphics drivers will start before mounting of  partition and you
will have a splash screen. If you want to read about boot up process the  packages are
ureadahead, mountall and plymouth.
                                                                                               
For GUI starting weird I would just go to startup Applications in Preferences menu and start turning one thing off at a time and restarting until I find the culpret that is making my desktop do strange things. Good luck and have a nice day.
__________________

---

### Post by todosmentira on 2010-05-26
Hi thanks - I have tried this - even when all other startup applications are disabled there is still a long pause before loading of gnome/compiz desktop

---

### Post by todosmentira on 2010-05-28
bump

---

