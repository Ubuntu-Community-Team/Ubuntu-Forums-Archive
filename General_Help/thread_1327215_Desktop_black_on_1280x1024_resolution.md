---
title: "Desktop black on 1280x1024 resolution"
date: 2009-11-15
forum: General Help
---

### Post by simartem on 2009-11-15
I am using Ubuntu 9.10
I had to create an xorg.conf file in order to use 1280x1024 resolution with my HP 1740 LCD monitor. My xorg.conf is as following :

```


Section "Monitor"
Identifier "HP"
ModelName "1740"
Option "DPMS"
HorizSync 30.0-83.0
VertRefresh 56-76
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    SubSection "Display"
    Depth 24
    Modes "1280x1024@60" "1280x900@60" "1024x768@60"
    EndSubSection
EndSection


```If i switch to 1280x900.. The wallpaper will show up. If i switch to 1280x1024 resolution which i am willing to use,  there is no wallpaper (black desktop background).

Edit : The desktop shortcuts also wont show up on 1280x1024 resolution. They are visible on 1280x900

 This seems weird to me. Any ideas why this occur and how to solve ?

---

### Post by simartem on 2009-11-15
problem solved with ATI driver and xorg-ati updates.. (from synaptic package manager..)

---

