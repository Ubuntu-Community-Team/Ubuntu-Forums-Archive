---
title: "How to configure Ubuntu Display for widescreen?"
date: 2011-02-03
forum: General Help
---

### Post by windyweather on 2011-02-03
I've built a system using the JetWay JNC98-525E-LF - with atom D525 and ION2.
Running Ubuntu 10.04. No problem to find Nvidia driver: 195.36.24 from Ubuntu package archives.

[LIST]
[*]Worked fine on Acer monitor P205 via DVI while I was setting it up. 1600x900.
[*]Needed to move it to complete WiFi and moved it to VGA 1280x1024 monitor.
[*]Now connected it Via HDMI and HDMI switch to Fujitsu PlasmaVision 42" monitor, and it works, but only in 1024 mode.
[*]Also, when I connect back to DVI I get nothing. Apparently either connection to VGA or HDMI has disabled DVI connector. Strange.
[/LIST]

Two problems:

(1) How to adjust configuration for Plasma screen to get widescreen format. Based on the plasma screen manual, it supports the following modes:

```
Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200@60" "1600x1200@85" "1280x1024@60" "1280x1024@75" "1360x768@60" "800x600@60" "800x600@75" 
    EndSubSection
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Default Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
EndSection
```

but setting /etc/X11/xorg.conf to this has no effect. And configuration via X or Nvidia ignores these so I cannot choose from this list. The highest resolution I get is 1024x768 when clearly the monitor and driver will support higher. I assume I need to edit some private Nvidia config file, but I don't know what file to edit. Nvidia driver settings application has no Override for what is thinks is some default set of resolutions.


(2) How can I re-enable the DVI connector, and why doesn't it work now that the device has been connected to a VGA and HDMI display? Shouldn't it automatically put out video on the connected DVI connector when that is the only one connected? Where do I change a setting to re-enable DVI so I can boot with a DVI connected monitor?

Thanks,
Windy

---

