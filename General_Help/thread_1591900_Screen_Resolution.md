---
title: "Screen Resolution"
date: 2010-10-10
forum: General Help
---

### Post by Purpleandblue on 2010-10-10
Hi there,

I've been using Ubunutu for almost a year now, but I've  recently had a problem with my screen resolution.  I hooked my laptop  up to a TV using an HDMI cable and nothing outputted to it, but after  unhooking it from the TV my laptop's resolution went from 1920x1080 to a  max of 1280x720.  I'm not sure how to fix it.  I'm currently running  Ubuntu 10.04 Lucid Lynx.

Edit:
The output for my xorg.conf is:

Section "Files"
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "ServerFlags"
    Option        "Xinerama" "off"
EndSection

Section "Device"
    Identifier  "Configured Video Device"
    Driver      "fglrx"
EndSection

Section "Screen"
    Identifier "Configured Screen Device"
    Device     "Configured Video Device"
    DefaultDepth     24
    SubSection "Display"
        Virtual   2560 729
    EndSubSection
EndSection

Thanks so much in advance
-Purpleandblue

---

### Post by Purpleandblue on 2010-10-10
I'm bumping this since I really need help.

---

### Post by Purpleandblue on 2010-10-11
Bump.  I'm not sure what other info to give or how to get it so I appreciate any help.

---

### Post by gerowen on 2010-10-11
What kind of video card do you use?  Are you using Ubuntu's "Monitors" app or a proprietary management tools such as the Catalyst software for ATI cards?

---

### Post by Purpleandblue on 2010-10-11
Thanks for responding,
I have a  ATI Mobility Radeon™ HD 5470, 1GB.  I have the proprietary drivers enabled and I've used both the "Monitors" app and the ATI Catalyst Control Center.

---

### Post by Purpleandblue on 2010-10-12
bump

---

### Post by Purpleandblue on 2010-10-13
bump again

---

