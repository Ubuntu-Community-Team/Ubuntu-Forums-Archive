---
title: "Monitor (Sony FW900) not identified problem"
date: 2010-11-30
forum: General Help
---

### Post by Dada__ on 2010-11-30
Hello there, I just installed Ubuntu 10.10 on my Compaq Mini 110c, and it seems to work perfectly fine. Everything works and the system is nice and snappy. However, there's one problem with a piece of external hardware: my monitor.

I've connected a monitor via VGA cable, and while I'm getting an image, it only has a very limited resolution (the max is 1360x768 at 60 hz). When booting into Windows XP, I can easily use resolutions up to 1920x1200 and larger. It also calls my monitor "unknown".

So, I tried searching Google for some configuration information and was able to easily find it, and now my xorg.conf contains this:

```
Section "Monitor"
#    HorizSync    30-70        # Sony CDP 200ES
#    VertRefresh    50-120        # Sony CDP 200ES
#    HorizSync    30-85        # Sony CDP 200E
#    VertRefresh    48-120        # Sony CDP 200E
#    HorizSync    30-96        # Sony CDP 400E
#    VertRefresh    48-160        # Sony CDP 400E
#    HorizSync    30-95        # KFC 19"
#    VertRefresh    50-150        # KFC 19"
    VendorName    "Sony"
    ModelName    "GDM-FW900"
    Identifier    "FW900"
    UseModes    "tk"
    HorizSync    30-121        # Sony FW900
    VertRefresh    48-160        # Sony FW900
EndSection

```I found this exact section online. Unfortunately, it doesn't seem to be working or even doing anything.

I have no idea how to solve this, perhaps someone can tell me where to look next?

Thanks!

---

### Post by Dada__ on 2010-12-04
I was able to fix the problem by following the wiki's advice. [https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions](https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions)  Used cvt to get a modeline and xrandr to set it up.

---

