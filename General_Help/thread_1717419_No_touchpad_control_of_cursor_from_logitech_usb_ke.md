---
title: "No touchpad control of cursor from logitech usb keyboard"
date: 2011-03-29
forum: General Help
---

### Post by zoggnoff on 2011-03-29
I'm using Desktop PowerPC PS3 9.10 Ubuntu Karmic Koala and I can not access the mouse in the GUI. doing cat /dev/input/mouse1 definitely produces a response indicative to a fully recognized device alas i have no control over the cursor. How can I tell the GUI, which I assume is X11 or xserver or gnome to see this device and utilize it? Thanks


```
Section    "ServerLayout"
    Identifier    "Xorg Configured"
    InputDevice    "Logitech"
EndSection

Section    "InputDevice"
    Identifier    "Logitech"
    Driver        "mouse"
    Option        "Device"    "/dev/input/mouse1"
EndSection
```Why doesn't this work?

Update: if you are experiencing the same problem forget all that xorg.conf stuff, remove that conf file and do this:
```
sudo apt-get purge xserver-xorg-input-synaptics
```removing this package removes the conflict and frees up the mouse usage in Karmic Koala 9.10

---

