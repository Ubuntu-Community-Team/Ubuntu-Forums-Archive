---
title: "Help with xorg.conf"
date: 2010-02-28
forum: General Help
---

### Post by TomyVk on 2010-02-28
Well i have a ati radeon hd 4650 and ive kinda altered my xorg.conf
The thing i want to know if i should do more tweaking in the xorg.conf
I'm kinda new to this so any help would be nice.

i'm using the newest ati drivers 10.2

Here is what i got:

```
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "ServerFlags"
    Option        "Xinerama" "off"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "0-LCD"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1280x1024"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    Option        "Monitor-LCD" "0-LCD"
    BusID       "PCI:2:00:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
        Modes    "1280x960"
    EndSubSection
EndSection

```

---

### Post by TomyVk on 2010-02-28
Bump

---

### Post by spikyjt on 2010-02-28
That's a pretty quick bump!

You probably need to give more info. Is the display working at all? Are you getting the resolutions you expected? Is 3D working? If yes to all those, what else are you trying to achieve?

Bear in mind that X.org doesn't need a config file for the current version in Karmic (not since Intrepid or at least Jaunty I think). The proprietary ATI drivers may need it of course, but they are notoriously flaky. On the few laptops I support that have ATI cards (I avoid them now) all I needed was
```

Section "Device"
    Identifier  "ati-Device-0"
    Driver      "fglrx"
EndSection

```
the autoconfig in X.org did the rest. YMMV

---

### Post by TomyVk on 2010-02-28
Well, everything is working well, i'm just trying to improve my opengl performance if its even possible.
i'm using the proprietary ATI driver, so i was asking if i'm missing something. And its not a laptop :)

---

### Post by warp99 on 2010-02-28
You can try some of these options under the device section to try and increase performance:

```
        Option	    "PseudoColorVisuals" "off"
	Option	    "OpenGLOverlay" "off"
	Option	    "VideoOverlay" "on"
	Option	    "UseFastTLS" "1"
	Option	    "EnablePrivateBackZ" "on"
```

I would suggest one at a time. Depending on your card some may work, some may be ignored, and some may even degrade performance. After making a change check your /var/log/Xorg.log file to see if the option has taken effect.

---

