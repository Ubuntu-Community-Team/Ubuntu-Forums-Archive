---
title: "hal-device-manager and other flakiness"
date: 2006-02-27
forum: General Help
---

### Post by Zeroangel on 2006-02-27
Hey all, I was messing around with some experimental upgrades and somehow managed to get my system to act flakey. Now Device Manager won't open and I get all sorts of wierd glitchy errors, so I decided to open up the device manager in the console to see what it would tell me and...```
dave@ubuntu:~$ hal-device-manager
Traceback (most recent call last):
  File "/usr/bin/hal-device-manager", line 8, in ?
    import gtk
  File "/usr/lib/python2.4/site-packages/gtk-2.0/gtk/__init__.py", line 37, in ?
    from _gtk import *
ImportError: /usr/lib/libcairo.so.2: undefined symbol: FT_GlyphSlot_Embolden
```

Well, the package in question was an upgraded Cairo theme I installed from MighMoS's site (gtk2-engines-clearlooks_2.7.4-0ubuntu1_i386). So I uninstalled it (it took gdm and gnome-desktop with it) and reinstalled the official version + gdm + gnome-desktop. But the errors still won't go away!

Can anyone help me narrow down what I might do to fix this problem?

---

