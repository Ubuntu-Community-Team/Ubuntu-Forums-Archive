---
title: "i update and got a new bar"
date: 2012-02-15
forum: General Help
---

### Post by cold37 on 2012-02-15
i update monday and got a new bar and i hate this thing how to i delete it i upload a pic of it im trying to keep the the Classic gnome on ununtu 11-10

---

### Post by wildmanne39 on 2012-02-15
Hi, here is a link that should help.

Edit: Here is the link.
[http://ubuntuforums.org/showthread.php?t=1859961](http://ubuntuforums.org/showthread.php?t=1859961)
Thanks

---

### Post by cold37 on 2012-02-16
i try that i even sign in the Classic mode with no Effects and its still here i try hold alt down and right click it and delete it but nothing is working i disable everything in Compiz its still there it mess up my wallpaper it sucks i dont know why there change the Classic mode anyway i like the way it not new junk im just happy i find this --> sudo apt-get install gnome-session-fallback < --- love it.. please some help

---

### Post by wildmanne39 on 2012-02-16
Hi, this should disable the global menu.
```
sudo su
echo "export UBUNTU_MENUPROXY=0" > /etc/X11/Xsession.d/81ubuntumenuproxy
```
Then reboot.
Thanks

---

### Post by cold37 on 2012-02-16
no its still there :confused:

---

### Post by cold37 on 2012-02-16
OMG cant they leave anything alone the new bar is apart of firefox Ubuntu 11.04 and 11.10 feature a Global Menu (AppMenu) in firefox 10.0.1 
[http://www.liberiangeek.net/2011/10/disable-the-global-menu-in-ubuntu-11-04-11-10-oneiric-ocelot/](http://www.liberiangeek.net/2011/10/disable-the-global-menu-in-ubuntu-11-04-11-10-oneiric-ocelot/)  :mad:

---

### Post by cold37 on 2012-02-16
remove it from fire fox but i can not remove appmenu-qt
i have try--> sudo apt-get remove appmenu-qt <-- dont work

---

### Post by cold37 on 2012-02-24
i found it :D its --> AppMenu Partial Removal

- To disable this feature without uninstalling it, use these commands, then reboot:

sudo su
echo "export UBUNTU_MENUPROXY=0" > /etc/X11/Xsession.d/81ubuntumenuproxy

:KS:KS:KS:KS:

---

### Post by wildmanne39 on 2012-02-24
Hi, glad it worked, please use thread tools at the top of the page and mark the thread solved.
Thanks

---

