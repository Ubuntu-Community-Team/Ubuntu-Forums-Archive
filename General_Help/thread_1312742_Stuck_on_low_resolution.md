---
title: "Stuck on low resolution"
date: 2009-11-03
forum: General Help
---

### Post by Vaeil on 2009-11-03
Hi!

I just upgraded from 9.04 to 9.10, leaving my home partition intact.
When I logged in, I noticed that I was on an extremely low resolution (640x480), while the monitor is supposed to do 1280x1024.
The nVidia drivers weren't loaded, so I enabled them through "Hardware Drivers", and rebooted cleanly.

This however did not fix the problem. nvidia-settings still only allows 'auto', 640, and 320. My xorg.conf was curiously empty (Bottom of post).
Adding modes manually does not allow nvidia-settings to go any higher (Nor the default tool). Using a 'virtual' option changed the virtual resolution, but the nvidia-settings was still stuck on 640, giving it an effect not quite unlike magnify.

Adding 'HorizSync   30.0 - 82.0' prevented Xorg from being started again, and bumped me to a terminal - Removing the option gave me back gdm, at the horrendous resolution. running nvidia-xconfig does nothing whatsoever.

Thank you for your time reading, any help is greatly appreciated.

Xorg.conf:
```
Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Default Device"
        Option  "NoLogo"        "True"
        Driver  "nvidia"
EndSection


```

ddcprobe
```
$ sudo ddcprobe
vbe: VESA 3.0 detected.
oem: NVIDIA
vendor: NVIDIA Corporation
product: NV31 Board - p141n Chip Rev
memory: 131072kb
mode: 640x400x256
mode: 640x480x256
mode: 800x600x16
mode: 800x600x256
mode: 1024x768x16
mode: 1024x768x256
mode: 1280x1024x16
mode: 1280x1024x256
mode: 320x200x64k
mode: 320x200x16m
mode: 640x480x64k
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 1024x768x64k
mode: 1024x768x16m
mode: 1280x1024x64k
mode: 1280x1024x16m
edid: 
edidfail

```

---

### Post by Vaeil on 2009-11-03
Fixed by adding:

SubSection "Display"
Viewport 0 0
Depth 24
Modes "1024x768x60Hz" "1280x1024x60Hz"
EndSubSection

For some reason, it wouldn't work as a modeline, but as a seperate subsection it does.

---

