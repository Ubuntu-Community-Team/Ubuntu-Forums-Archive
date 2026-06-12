---
title: "Logitech Cordless Trackman Optical"
date: 2005-03-15
forum: General Help
---

### Post by IdoMcFly on 2005-03-15
Hi!

I have a Logitech Cordless Trackman Optical which have 8 physical buttons on it so 10 buttons (with the up and down of the wheel) for X.

My problem is that I can't get the 10 buttons to work.

I was on Debian Sarge on my old computer and I installed Ubuntu Hoary Preview Release on my brand new case and put the same configuration in my xorg.conf :
```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "Dev Name"              "Logitech USB Receiver"
        Option          "Dev Phys"              "usb-0000:00:02.0-8/input0"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/event0"
        Option          "Protocol"              "evdev"
        Option          "Buttons"               "10"
        Option          "Emulate3Buttons"       "false"
        Option          "ZAxisMapping"          "9 10"
        Option          "AngleOffset"           "-32"
EndSection

```

but xev don't give me the 10 buttons.

To get this configuration I followed [linuX-Gamer](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=46) instructions.

note that the ```
sudo strings /usr/X11R6/bin/X | grep evdev
``` didn't give me any output but it was the same on my Debian Sarge with XFree 4.3.0.

Any help appreciate

---

### Post by IdoMcFly on 2005-03-15
[QUOTE=IdoMcFly]Hi!

I have a Logitech Cordless Trackman Optical which have 8 physical buttons on it so 10 buttons (with the up and down of the wheel) for X.

My problem is that I can't get the 10 buttons to work.

I was on Debian Sarge on my old computer and I installed Ubuntu Hoary Preview Release on my brand new case and put the same configuration in my xorg.conf :
```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "Dev Name"              "Logitech USB Receiver"
        Option          "Dev Phys"              "usb-0000:00:02.0-8/input0"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/event0"
        Option          "Protocol"              "evdev"
        Option          "Buttons"               "10"
        Option          "Emulate3Buttons"       "false"
        Option          "ZAxisMapping"          "9 10"
        Option          "AngleOffset"           "-32"
EndSection

```

but xev don't give me the 10 buttons.

To get this configuration I followed [linuX-Gamer](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=46) instructions.

note that the ```
sudo strings /usr/X11R6/bin/X | grep evdev
``` didn't give me any output but it was the same on my Debian Sarge with XFree 4.3.0.

Any help appreciate[/QUOTE]
 forget me... I forgot to install xvkdb (as I've imported some old xbindkeys configuration files...)

---

