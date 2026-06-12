---
title: "ATI Dual Monitor Left/Right"
date: 2011-01-20
forum: General Help
---

### Post by Cuco3 on 2011-01-20
Ubuntu 10.04

I have the ATI proprietary drivers installed. I have a dual monitor set up: laptop on my left, and LCD on the right. I have the LCD set up as the main screen, but I want to be able to move my mouse to the left onto the other screen. As of right now, I have to go to the right in order to get on to the other screen.

The ATI GUI tool, even w/ Administrative privileges, does not apply the changes I want it to. I can't even enable somethings like Xinerama. Weird.

Here's my xorg.conf

```
Section "ServerLayout"
    Identifier     "amdcccle Layout"
    Screen      0  "amdcccle-Screen[1]-0" 0 0
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
    Identifier   "0-CRT1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1680x1050"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "0-LVDS"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "TargetRefresh" "60"
    Option        "Position" "1680 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
    Option        "PreferredMode" "1366x768"
EndSection

Section "Device"
    Identifier  "Default Device"
    Driver      "fglrx"
    BusID       "PCI:1:5:0"
EndSection

Section "Device"
    Identifier  "amdcccle-Device[1]-0"
    Driver      "fglrx"
    Option        "Monitor-CRT1" "0-CRT1"
    Option        "Monitor-LVDS" "0-LVDS"    
    BusID       "PCI:1:5:0"
EndSection

Section "Device"
    Identifier  "amdcccle-Device[1]-1"
    Driver      "fglrx"
    Option        "Monitor-LVDS" "0-LVDS"
    BusID       "PCI:1:5:0"
    Screen      1
EndSection

Section "Screen"
    Identifier "Default Screen"
    DefaultDepth     24
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[1]-0"
    Device     "amdcccle-Device[1]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Virtual   3046 3046
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[1]-1"
    Device     "amdcccle-Device[1]-1"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

```Here's a weird thing also: I can only enable/disable monitors using the default "Monitors" tool. And when I arrange the monitors there, it still doesn't apply the changes.

---

### Post by Cuco3 on 2011-01-21
any1?

---

### Post by Cuco3 on 2011-01-21
Any1 please?

---

### Post by corncob on 2011-01-21
> **Cuco3 said:**
> Any1 please?

Not that this will be much help but when I was setting up an extra monitor, plugging it into the VGA port of a laptop, I read somewhere that the main screen had to be on the left.  I don't know if you'd call this a glitch, bug, shortcoming, or what -- I just accepted it and went on.

---

