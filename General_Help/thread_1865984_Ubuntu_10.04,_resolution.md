---
title: "Ubuntu 10.04, resolution"
date: 2011-10-20
forum: General Help
---

### Post by Dannny213 on 2011-10-20
OS Version: Ubuntu 10.04
PC: Emachines E1401
Graphics Driver: NVIDIA 195.36.24 for GeForce 9200 (Proprietary)
TV: Sony Bravia 40" 1080p HDTV Version: KDL-40V4000

Okay, I am incredibly frustrated with this.

No matter WHAT I change to xorg.conf, X Server Settings, Monitors - upon reboot I get sent back to 1440x900 screen resolution.

I am in 1920x1080 resolution RIGHT NOW, and it works fine. All I have to do is change it. Everytime.

How can I force this to STAY in 1920x1080?

I have tried various techniques in xorg.conf and none of them seem to have worked. In fact, this is the message I get after making the resolution change:



-------------------------------
Section "Screen"

**# Removed Option "metamodes" "1920x1080 +0+0"**
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1440x900 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
-------------------------------

Note the **bold**. It pops up every god damn time.


Please, my friends, I know there is a fix for this, there just has to be. It's probably extremely simple. Help a brother out. 

(I can post my entire xorg.conf file, if that helps)

---

### Post by Dannny213 on 2011-10-21
bump

---

### Post by Dannny213 on 2011-10-22
Thanks for the reply. How do I know what refresh rate (Hz) is?

I do not want to set it too high incase it doesn't show up, or damage the screen.

---

