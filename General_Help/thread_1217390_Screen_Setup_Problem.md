---
title: "Screen Setup Problem"
date: 2009-07-19
forum: General Help
---

### Post by mavix on 2009-07-19
Hi guys,
I'm trying to set up my two monitors on Ubuntu, but I'm having very little success.
So for now I'm trying to sort out the root of the problem, which is my primary screen.
Ubuntu (9.04) seems to completely disregard xorg.conf, and the best resolution I can get is 800x600. After messing around with xorg.conf it set's the resolution to an obscure 832x624 resolution. My monitor (LG Studioworks 552V - Found a thread about it here before), supports 1024x768 at 60Hz, but I just cannot get it to go that high. I have a suspician that it might be that Ubuntu isn't detecting my monitor correctly; It sees it as a 14" (System->Preferences->Display), however I'm quite sure it's a 15".
My graphics card is a Radeon X1650 Pro AGP, if that makes any difference.
Below is the contents of my xorg.conf file:

```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen1" 0 0
EndSection

Section "Module"
    Load           "glx"
    Load           "v4l"
EndSection

Section "Monitor"
    Identifier     "Left Monitor"
    VendorName     "Generic CRT Display"
    ModelName      "Monitor 1024x768"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "radeon"
    BoardName      "radeon"
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Left Monitor"
    DefaultDepth    16
    Option         "HorizSync" "30-54"
    Option         "VertRefresh" "50-120"
    SubSection     "Display"
        Viewport    0 0
        Depth       16
        Modes      "1024x768_60.00" "800x600_60.00"
	Virtual	    1024	768
    EndSubSection
EndSection
```

Any ideas on how to get it working properly?

---

