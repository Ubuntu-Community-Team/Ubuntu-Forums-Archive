---
title: "xorg / display resolution"
date: 2010-11-05
forum: General Help
---

### Post by binaryPanda on 2010-11-05
Hi,

Since having my new monitor and upgrading to 10.10 I've not been able to keep my resolution at 1920x1080, even when I load nvidia-settings by root and save the xorg.

Has the xorg.conf been changed since the previous versions?

I did a search and the one in /etc/X11 mentions this:

> Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "HKC"
    HorizSync       30.0 - 83.0
    VertRefresh     60.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 210"
EndSection

Section "Screen"

# Removed Option "metamodes" "1920x1080 +0+0; 1280x1024_85 +0+0; nvidia-auto-select +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1920x1080_60 +0+0; 1280x1024_85 +0+0; nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Not sure if that's any help, but would like to be able to keep the 1920x1080 constant :confused:

Cheers

---

### Post by Barriehie on 2010-11-06
Try: (after backing up the original)

```

Section "Screen"
#
# Removed Option "metamodes" "1920x1080 +0+0; 1280x1024_85 +0+0; nvidia-auto-select +0+0"
#
Identifier "Screen0"
Device "Device0"
Monitor "Monitor0"
DefaultDepth 24
Option "TwinView" "0"
Option "metamodes" "1920x1080_60 +0+0; 1280x1024_85 +0+0; nvidia-auto-select +0+0"
SubSection "Display"
  Depth 24
  [color=Red]Mode "1920x1080"[/color]
EndSubSection
EndSection
```

---

### Post by binaryPanda on 2010-11-06
Hi Barriehie, gave that a try as you mentioned but X failed to load up then so had to remove the line from xorg :(

---

### Post by Barriehie on 2010-11-06
Have you tried:
```

sudo dpkg-reconfigure xserver-xorg
```

---

