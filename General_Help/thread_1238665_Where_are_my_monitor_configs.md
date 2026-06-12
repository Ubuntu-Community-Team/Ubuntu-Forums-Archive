---
title: "Where are my monitor configs?"
date: 2009-08-12
forum: General Help
---

### Post by scaramanzia on 2009-08-12
Hello. I've just installed a nvidia driver using the Ubuntu's hardware drivers utility, and everything seems to work right. But when I've tried to look into my xorg.conf I've found there's no significant changes made to it. My monitor are using a different resolution, and I want to find how did ubuntu configure it. But I've found just this:
```
Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

```
I'm not getting any trouble with this. I'm just trying to understand where are my configs, and how Ubuntu knows how did configured my monitor

---

### Post by CatKiller on 2009-08-12
Automagic. 

I don't fully understand the new process either, but [code]     Driver        "nvidia"[code] is sufficient to load the NVidia driver, if it's installed, and the per-user monitor resolution is kept in ~/.config/monitors.xml.

---

