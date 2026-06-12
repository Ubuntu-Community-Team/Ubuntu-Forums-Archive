---
title: "Displaying ATI catalyst control centre in menu bar"
date: 2010-08-21
forum: General Help
---

### Post by DanH860 on 2010-08-21
Hi,

I've recently installed Ubuntu 10.04 onto a PC that has a Radeon HD2600 XT graphics card. I tried to install the proprietary driver from the AMD website and from what I can tell, it seemed to work (my xorg.conf file is shown below)

```
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
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
```The problem is that the catalyst control centre does not show up anywhere on the menu bar (such as in system>administration etc.). From advice given on a seperate post ([link]("http://ubuntuforums.org/showthread.php?t=512500")), I can load up the control centre from typing in a command in terminal, but is there a way to put this in the menu bar?

Thanks in advance,
Dan

---

### Post by magereaux on 2010-09-18
Same problem here. catalyst control disappeared after I did an update. All of my compiz affects stopped working,I removed FGLRX driver and re-installed. Everything seems to be working fine other than catalyst control centre missing from System Preferences.

---

### Post by dcstar on 2010-09-18
> **magereaux said:**
> Same problem here. catalyst control disappeared after I did an update. All of my compiz affects stopped working,I removed FGLRX driver and re-installed. Everything seems to be working fine other than catalyst control centre missing from System Preferences.

Install this package: **fglrx-amdcccle**

---

