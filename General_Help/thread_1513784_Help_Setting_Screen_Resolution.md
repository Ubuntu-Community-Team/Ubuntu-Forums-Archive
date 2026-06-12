---
title: "Help Setting Screen Resolution"
date: 2010-06-20
forum: General Help
---

### Post by IMSargon on 2010-06-20
Monitor: Asus VH242H
Graphics: XGI Volari Z9s

The native resolution of my monitor is 1920x1080. I can't get Ubuntu 10.04 to display at this resolution.

Current xorg.conf (relevant sections):
```
Section "Monitor"
        #DisplaySize      520   290     # mm
        Identifier   "Monitor0"
        VendorName   "ACI"
        ModelName    "ASUS VH242H"
        HorizSync    30.0 - 85.0
        VertRefresh  55.0 - 75.0
        Option      "DPMS"
EndSection
Section "Device"
        Identifier  "Card0"
        Driver      "sis"
        VendorName  "XGI Technology Inc. (eXtreme Graphics Innovation)"
        BoardName   "Z7/Z9 (XG20 core)"
        BusID       "PCI:1:3:0"

```

I have also tried:
```
Section "Monitor"
        #DisplaySize      520   290     # mm
        Identifier   "Monitor0"
        VendorName   "ACI"
        ModelName    "ASUS VH242H"
        HorizSync    67.16
        VertRefresh  59.96
        Modeline "1920x1080_60.00" 173.00 1920 2048 2248 2576 1080 1083 1088 1120 -hsync +vsync
        Option      "DPMS"
```

I was able to get the terminals to run at 1920x1080 by adding ```
video=sisfb:mode:1920x1080x32,rate:70,mem:4096
```
to my grub command. That's nice, but I really want Xorg running at that resolution, and it didn't.

I've been working on this for hours, through dozens of gdm restarts with every variation of the above I can think of. Does anyone have and ideas?

---

### Post by IMSargon on 2010-06-20
```
(II) SIS(0): Not using mode "1920x1080_60.00" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using driver mode "1920x1080" (bad mode clock/interlace/doublescan)

```

How is my clock/interlace/doublescan bad if I got my output right from cvt or gtf?

---

