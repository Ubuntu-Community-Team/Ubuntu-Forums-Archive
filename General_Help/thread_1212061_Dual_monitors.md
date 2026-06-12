---
title: "Dual monitors?"
date: 2009-07-13
forum: General Help
---

### Post by ngardner on 2009-07-13
I've been doing lots of searching, and have found lots of answers - but none of them seem to work.

I'm trying to get multi display working, so I can have more workspace. Right now the displays are just mirrored.

I have a fresh install of Ubuntu 9.04, and have a ATI Radeon HD 3450. It has a DVI and VGA output on it, I have two identical monitors hooked up, one as DVI, one as VGA. I have the fglrx driver installed. When I open "ATI Catayst Control Center" the section for Multi-display is disabled, as well as the Xinerama section. Ive ran it as root with same results. Here is my xorg.conf...

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver  "fglrx"
EndSection


Any help would be appericated!

---

### Post by realzippy on 2009-07-13
Hello,

google for "xrandr"....

E.G. :

[http://navetz.com/v/132/Simple-dual-monitor-setup-with-XrandR-in-Ubuntu-Linux](http://navetz.com/v/132/Simple-dual-monitor-setup-with-XrandR-in-Ubuntu-Linux)

;-)

---

