---
title: "no keyboard and mouse input after reboot"
date: 2009-11-17
forum: General Help
---

### Post by monkey d luffy on 2009-11-17
Hello,

I have installed ubuntu 9.10 karmic koala.
After a few reboots my keyboard and mouse stopped working.
I have been looking around on topics. i found the following information:
Getting to the terminal with: alt+sysreq+r and then ctrl+alt+f1.
I tried a few things in the terminal:
sudo hald --verbose=yes
sudo dbus-daemon
sudo restart gdm
I aslo tried:
/etc/init.d/dbus start or restart
/etc/init.d/hal start or restart
and alot of variants:
start dbus, start hal. (or restart)
I get the following messages:
dbus and hal already started.

further information:
Im using a laptop and a usb mouse (and unable to use touchpad).

Can anyone help me out please?
Thanks for reading.

---

### Post by monkey d luffy on 2009-11-19
[LEFT]Close this thread please, a fresh installation solved this.
[/LEFT]

---

