---
title: "Screen Resolution Query"
date: 2010-07-07
forum: General Help
---

### Post by vanspud on 2010-07-07
Hi,

I recently installed Ubuntu 10.04 on my laptop that already has Vista on it. I have always wanted to make the leap to Linux since I got interested in computers.

The installation went well apart from 2 issues I'm having. The major issue is to do with my screen resolution. When I am in Ubuntu the screen resolution is zoomed in way to much, it's most notable when in firefox, the google logo nearly takes up the hole screen so I can't really use the internet.

I tried setting the resolution myself but the highest option it gives me is "800x600 (4:3)", but when I am in Vista it's set at "1280x800".

So my question is, is there a command I can type for Ubuntu to set the correct resolution(1280x800) or is it the case that a part is not compatible with Ubuntu and I need to get a new part, graphics card or whatever it may be.

Thanks for any help in advance, is greatly appreciated.

---

### Post by SmokeyThePanda on 2010-07-07
Easy fix mate. :)

```
sudo nano /etc/X11/xorg.conf
```Then edit the following with the specifications of your monitor. You can change the modes to whatever your monitor supports. You will need the vertical refresh and horizontal sync of your monitor. 

```
Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Generic Monitor"
    HorizSync     30 - 60
    VertRefresh   60 - 75
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Configured Video Device"
    Monitor        "Generic Monitor"
    DefaultDepth    16
    SubSection "Display"
        Depth        16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
```After you have edited it, simply save and restart your computer. (If you do not have an xorg.conf, create one and put it in there.)

Hope this helps.

---

