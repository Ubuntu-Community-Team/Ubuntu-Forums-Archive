---
title: "Xpress 1200 and ubuntu 9.04"
date: 2010-03-02
forum: General Help
---

### Post by Silenus on 2010-03-02
I finally got wifi working on my a215-s7422. Then I hear the restricted fglrx proprietary drivers for my video card are all ready, so I try them. The next thing I know I'm getting an error "No screens detected" and xserver won't start at all.

So, I remove those drivers, and try the opensource ati ones, again, no screens detected.

Is there something I am missing? 


```
Section "Device"
        Identifier      "Xpress 1200"
        Driver          "ati"
        BusID           "PCI:01:05.0"
        Option          "XAANoOffscreenPixmaps"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Xpress 1200"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1440x900" "1024x768"
        EndSubSection
EndSection

Section "DRI"
        Mode 0666
EndSection
        
Section "Extensions"
        Option "Composite" "Enable"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

```

Every time I try to edit it to use a different driver or follow the guide ([https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)) I end up getting no where.

---

