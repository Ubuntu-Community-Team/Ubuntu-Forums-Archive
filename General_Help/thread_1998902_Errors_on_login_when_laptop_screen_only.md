---
title: "Errors on login when laptop screen only"
date: 2012-06-07
forum: General Help
---

### Post by buffalobillion on 2012-06-07
Using Ubuntu 12.04, nvidia drivers. I have dual monitors when my laptop is docked, works great. Here is the relevant section of my xorg.conf file:

```
Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "DFP-2: nvidia-auto-select +0+0, DFP-3: nvidia-auto-select +1600+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

However, if I boot undocked, I get the following error dialog box on login:

**Could not apply the stored configuration for monitors**

none of the selected modes were compatible with the possible modes:
Trying modes for CRTC 642
CRTC 642: trying mode 1920x1080@50Hz with output at 3200x1200@50Hz (pass 0)
CRTC 642: trying mode 1920x1080@51Hz with output at 3200x1200@50Hz (pass 0)
CRTC 642: trying mode 1920x1080@52Hz with output at 3200x1200@50Hz (pass 0)
CRTC 642: trying mode 1920x1080@53Hz with output at 3200x1200@50Hz (pass 0)
CRTC 642: trying mode 1680x1050@54Hz with output at 3200x1200@50Hz (pass 0)
CRTC 642: trying mode 1600x1024@55Hz with output at 3200x1200@50Hz (pass 0)
CRTC 642: trying mode 1440x900@56Hz with output at 3200x1200@50Hz (pass 0)
CRTC 642: trying mode 1400x1050@57Hz with output at 3200x1200@50Hz (pass 0)
CRTC 642: trying mode 1360x768@58Hz with output at 3200x1200@50Hz (pass 0)
CRTC 642: trying mode 1360x768@59Hz with output at 3200x1200@50Hz (pass 0)
CRTC 642: trying mode 1280x1024@60Hz with output at 3200x1200@50Hz (pass 0)
CRTC 642: trying mode 1280x1024@61Hz with output at 3200x1200@50Hz (pass 0)
CRTC 642: trying mode 1280x960@62Hz with output at 3200x1200@50Hz (pass 0)
CRTC 642: trying mode 1152x864@63Hz with output at 3200x1200@50Hz (pass 0)
CRTC 642: trying mode 1152x864@64Hz with output at 3200x1200@50Hz (pass 0)
CRTC 642: trying mode 1152x864@65Hz with output at 3200x1200@50Hz (pass 0)
CRTC 642: trying mode 1152x864@66Hz with output at 3200x1200@50Hz (pass 0)

And my fonts look all big.

Is there a way to easily move between mobile (laptop screen) and docked (dual screens)?

---

