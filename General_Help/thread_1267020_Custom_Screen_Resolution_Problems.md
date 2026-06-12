---
title: "Custom Screen Resolution Problems"
date: 2009-09-15
forum: General Help
---

### Post by Mach1723 on 2009-09-15
I use version 180 of the nvidia drivers and cant get a custom resolution set, xrandr doesnt work and heres my xorg.conf which was located in etc/X11.
I have done some custom naming of the identifiers.
```
# xorg.conf (X.Org X Window System server configuration file)

#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
    Identifier    "Monitor"

    Modeline "1280x960_60.00"  102.10  1280 1360 1496 1712  960 961 964 994  -HSync +Vsync
    Option    "PreferredMode" "1280x960_60.00"
    
EndSection

Section "Screen"
    Identifier    "Screen"
    Monitor        "Monitor"
    Device        "nvid"
    DefaultDepth    24
    SubSection "Display"
        Depth 24
        Modes        "1280x960""1024x768""800x600"
        Virtual        1280 960
    EndSubSection
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "nvid"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

```

I have been trying to fix this problem for the last day searched google and found plenty of posts on these forums but none of them helped me.

---

### Post by Mach1723 on 2009-09-15
any solutions?

---

### Post by Mach1723 on 2009-09-15
Just realized the Multimedia and Video forum is for Nvidia and video issues can a Moderator move this thread(if it ever stays on the front page long enough to be seen)

---

