---
title: "Xorg!"
date: 2009-09-27
forum: General Help
---

### Post by Taj1993 on 2009-09-27
Hi, recently I reinstalled 9.04 and basically im stuck at installing the video drivers because I forgot to backup the Xorg.conf. I installed them all correctly, Its just X will not load up.

Basically what I remember being the problem was I had my BusID undeclared. But this time no luck. can anyone post their Xorg.conf files so I can see what I am forgetting. (Oh, I am using SLI 9800's)

Section "Device"

    Identifier    "Configured Video Device"
    Drive         "nvidia"
    BusID         "PCI:3:0:0"
EndSection

---

