---
title: "Cannot get widescreen resolution"
date: 2009-08-03
forum: General Help
---

### Post by Semmelweis on 2009-08-03
I would really like to my screen res up to 1280x768, but so far no amount of tinkering has gotten me close. I have tried the Gnome display utility, also I have tried the config utility that comes with Nvidia drivers with no luck. I even tried to manually edit my xorg.conf, that only resulted in a headache and a strange entry at the bottom of my .conf. (listed at the bottom of the post, as a "removed option")

Here are some details:

* Ubuntu 9.04
* Nvidia 9800 GTX+ video card
* 180.44-0ubuntu1 vid card drivers
* Monitor is an oldish HDTV (up to 1280x178 res)

Here is some info from my current xorg.conf: 

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "UseFBDev" "true"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9800 GTX/9800 GTX+"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"

# Removed Option "metamodes" "1280x768 +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1152x864 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Any ideas?

---

### Post by Semmelweis on 2009-08-03
Please advise

---

