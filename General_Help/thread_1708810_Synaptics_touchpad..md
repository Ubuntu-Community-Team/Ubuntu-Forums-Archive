---
title: "Synaptics touchpad."
date: 2011-03-17
forum: General Help
---

### Post by Firbewn9 on 2011-03-17
I have some problems with configuring multitouch's two fingers  double click on regular 10.10.

On my previous installation I was able to achieve this (or so I remember) by installing some package that I can't recollect, therefore I a fighting with Xorg.

Despite xorg.conf fails with my eeepc the /etc/X11/xorg.conf.d/synaptics.conf does the trick, however it could have been more responsive.

Any this is my question: what do I need to add/modify in order for two fingers click work every time, and not every 1/3 attempts.

This is my conf:

```
Section "InputClass"
        Identifier      "Touchpad"                      # required
        MatchIsTouchpad "yes"                           # required
        Driver          "synaptics"                     # required
        Option          "TapButton1"            "1"
        Option          "TapButton2"            "2"     # multitouch
        Option          "TapButton3"            "3"     # multitouch
        Option          "VertTwoFingerScroll"   "1"     # multitouch
        Option          "HorizTwoFingerScroll"  "1"     # multitouch
        Option          "LBCornerButton"        "3"     
        Option          "RBCornerButton"        "8"     
        Option          "EmulateTwoFingerMinZ"  "35"
        Option          "EmulateTwoFingerMinW"  "5"
EndSection

```

---

