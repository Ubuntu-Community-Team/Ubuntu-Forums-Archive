---
title: "stop screen panning"
date: 2009-10-12
forum: General Help
---

### Post by pandaweb on 2009-10-12
today i decided to swap my pci wirless card and my pci nvidia graphics card so that my wireless cards antenna could have more room to move around. when i booted back up my screen was huge and cut off on all sides. when i moved my mouse it would pan over to reveal that portion of the screen. so i went into xorg.conf to see if i could fix this, nope... then installed the nvidia drivers which made things worse. anyways i ended up messing around with xorg.conf for a while, mainly HorizSync, until i got it about 98% fixed. the screen nearly fits once again, except for about 2mm that hangs off the left or right side of the screen, which pans over when i move my mouse to the edge of the screen. google is no help on this...

also, if this helps, ive tried running off my onboard graphics card, same exact problem.

monitor: 32" Vizio VO320e
graphic card: Nvidia GeForce FX 5200

thanks in advance

```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Vizio"
    ModelName      "VO320E"
    HorizSync       47.550
    VertRefresh     59.810
EndSection

Section "Device"
    Identifier     "Videocard0"
#    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
#    Option         "TwinView" "0"
#    Option         "TwinViewXineramaInfoOrder" "CRT-0"
#    Option         "metamodes" "CRT: nvidia-auto-select @1366x768 +0+0"
    SubSection     "Display"
        Depth		24
	Modes		"1366x768@60"
	Virtual		1366 768
    EndSubSection
EndSection
```

---

### Post by pandaweb on 2009-10-15
bump

---

### Post by pandaweb on 2009-10-29
installed 9.10 today hoping it would fix the issue, but it didnt. so i did a little bit of thinking and it hit me! if its too big, make it smaller... how simple is that? so here is what i did

created xorg.conf in /etc/X11/ and added the following lines from my original xorg.conf on 9.04

```

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Vizio"
    ModelName      "VO320E"
    HorizSync       47.550
#    VertRefresh     59.810 (didnt need this)
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth		24
	Modes		"1360x768@60"
	Virtual		1360 768
    EndSubSection
EndSection
```

if you compare this with the original youll see that i changed the resolution from 1366x768 to 1360x768. my monitor is rated at 1366x768 but for some reason it just was too big.

hope this helps someone

---

### Post by darb_dabney on 2009-11-03
Thanks, Pandaweb.  I got my display tweaked during 9.10 update where the virtual screen was set to 2048 x whatever, and my real display was 1600x1200.  It seemed hopeful when I switched back to the native Nvidia driver 185.18.36 for my GeForce 8600 GT, but every time I started up, even after setting the display correctly in Gnome, it went back.

After editing /etc/X11/xorg.conf it is now properly behaved.
Thanks for posting your experience, it helped me tonight.
-=Darb

---

