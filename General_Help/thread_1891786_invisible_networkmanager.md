---
title: "invisible networkmanager?"
date: 2011-12-06
forum: General Help
---

### Post by xi109 on 2011-12-06
So I just installed Lubuntu-minimal 11.10 on my friends asus eeepc 701, and then did sudo apt-get install lubuntu-desktop and it's working nicely but nm-applet appears as a blank space in the tray and when I click on this it says that ethernet and wireless are not managed.
Any idea what's going on?
thanks in advance

edit: sudo ifconfig wlan0 down doesnt help either

---

### Post by Spyderkid on 2011-12-06
do you need to install additional packages?

also sometimes the apps in the app tray just conk out, don't know why restart usually fixes

---

### Post by aeiah on 2011-12-06
you're perhaps missing a daemon that takes control of these things. ive always used wicd and wicd-daemon with this kinda setup but it isn't necessarily better

---

