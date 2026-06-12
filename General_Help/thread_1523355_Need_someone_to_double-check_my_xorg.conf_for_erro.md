---
title: "Need someone to double-check my xorg.conf for errors"
date: 2010-07-03
forum: General Help
---

### Post by Lolpanda on 2010-07-03
Im using Arch Linux right now, but their forums aren't  being helpful.  I was wondering if someone would be kind enough to double check my xorg.conf for errors. I had to create it with aticonfig --intial, aticonfig -v, then edit it manually and somewhere along the way...things got messed up. Compositing is working fine, but I'm having issues with Firefox and Termainl and X redrawing the windows. 

Like sometimes if I open up a new tab, or refresh a google search, the entire window except for the menu area goes black. if I resize the window by even one pixel, Xorg redraws it and it clears it up. While I could definity do that over and over and over anytime it happens..id rather a real fix. 

```
Section "ServerLayout"
        Identifier     "aticonfig Layout"
        Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
        Load    "glx"
        Load    "dri"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]-0"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection
Section "Device"
        Identifier  "aticonfig-Device[0]-0"
        Driver      "fglrx"
        BusID       "PCI:1:5:0"
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]-0"
        Device     "aticonfig-Device[0]-0"
        Monitor    "aticonfig-Monitor[0]-0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection


```

Its a single monitor setup, refresh rates can be 50, 60 or 75. Any help is desperately appreciated

---

