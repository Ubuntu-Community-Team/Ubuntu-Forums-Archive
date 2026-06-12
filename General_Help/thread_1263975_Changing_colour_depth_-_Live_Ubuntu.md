---
title: "Changing colour depth - Live Ubuntu"
date: 2009-09-11
forum: General Help
---

### Post by dark2025 on 2009-09-11
I'm using Persistent Live Ubuntu on a USB stick. Is there a way I can change the colour depth from 32bit to 16bit? I don't think I can change the xorg file since it's not a regular installation. Can anybody help me out?

---

### Post by XDevHald on 2009-09-11
Great question, see: [http://ubuntuforums.org/showthread.php?t=268150](http://ubuntuforums.org/showthread.php?t=268150)

Let us know if you have any other questions.

---

### Post by dark2025 on 2009-09-17
Thanks for the response, but I don't think that works because it's a Live version. For example, my xorg.conf file is as follows:
> Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
So is there another way to do this?

---

