---
title: "Force a refresh rate?"
date: 2009-11-02
forum: General Help
---

### Post by doomshd on 2009-11-02
I looked around on this and other various forums but still the issue is persisting. I have a GTX 280 and am using two Dell 2209WA's for my displays. They are supposed to do 1680x1050@75hz... but everytime I try to change the refresh rate in the nvidia panel it only shows 60hz. I tried editing the xorg.conf and that left me in the same spot I started. 

```

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
SubSection "Display"
    Depth        24
    Modes        "1680x1050_75" "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Dell"
    ModelName      "2209WA"
    HorizSync       32.0
    VertRefresh     75.0
EndSection
```I manually put in the "Monitor" section values... and I also manually put in the sub section under "Screen". Am still having no results on forcing it into 75hz though.

I'm using 9.10.

---

### Post by LanceyD on 2009-11-03
I too would like to force a refresh rate, this really should be in the panel.  I'm using nvidia 7900 GTO on 185 drivers and Ubuntu 9.10 and a Belinea 19" CRT and i am stuck to 60hz, eyes are watering writing this.

---

