---
title: "Having a little trouble running an extended desktop"
date: 2012-01-11
forum: General Help
---

### Post by cptrohn on 2012-01-11
Hi, and thanks for reading, I am having just a little trouble setting up an extended desktop with dual monitors in 11.10....  Both monitors can run as a clone but when I go to set up the extended desktop I get this error message [CODE]requested position/size for CRTC 147 is outside the allowed limit: position=(1600, 0), size=(1280, 960), maximum=(1920, 1920)[/CODE..  Now I do have 2 different size monitors that are capable of different resolutions, but I have both set to the same resolution....

Here is a screenshot of what I see in the display manager when I try to move the monitors around to get the extended desktop.

I am simply just wanting to move the Acer 20 to the right of the Acer 22...

This was working just fine before I updated my system (fresh install)  after the updates can't get it moved at all.  Any ideas?

---

### Post by Buntumatic on 2012-01-11
I ran two different displays with different resolutions for long time, using Xinerama.
What method you are using?

---

### Post by cptrohn on 2012-01-11
> **Buntumatic said:**
> I ran two different displays with different resolutions for long time, using Xinerama.
What method you are using?

All I am doing is running basic display manager from the settings...

---

### Post by Buntumatic on 2012-01-11
I assume Display Manager is some GUI frontend to edit Xorg settings. As usual, frontends are limited and often buggy.

There are several ways to do it, with xrandr, xinerama, twinview (nVidia proprietary). It all comes down to editing xorg.conf.

---

### Post by cptrohn on 2012-01-11
> **Buntumatic said:**
> I assume Display Manager is some GUI frontend to edit Xorg settings. As usual, frontends are limited and often buggy.

There are several ways to do it, with xrandr, xinerama, twinview (nVidia proprietary). It all comes down to editing xorg.conf.

OK, so what would I need to edit in xorg.cong?  I google xineral and at sourceforge it says it is no longer active and hasn't been since 2009  I will take a look at xrandr, maybe that is the solution for me.  I'm using the ATI fglrx drivers for my video....  I wonder if that had anything to do with it?

---

### Post by cptrohn on 2012-01-11
Ok so I have a friend with the exact same model monitor that I have.....  hooked up his monitor in place of the 20" and am still having the same problem trying to run an extended desktop....

---

### Post by Buntumatic on 2012-01-11
Xorg works without xorg.conf, true. 
xorg.conf is ignored by Xorg, false.
You still can create xorg.conf and put your customization in there.

Below is my working configuration with Screen0 in front of me and Screen1 on left, as an example.
```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 1680 0
    Screen      1  "Screen1" LeftOf "Screen0"
    Option         "Xinerama" "1"
EndSection


Section "Monitor"
    Identifier     "Monitor0"
    ModelName      "Westinghouse Digital Electronics LCM-22w2"
    HorizSync       30.0 - 82.0
    VertRefresh     56.0 - 67.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    ModelName      "DELL E228WFP"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8500 GT"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8500 GT"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection


Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "DFP: 1680x1050_60 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "metamodes" "CRT: 1680x1050_60 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

---

### Post by cptrohn on 2012-01-11
Thanks for the information...  But after doing some testing and trial and error my problem is a bug with the ATI driver that I mentioned before.  With just the open source drivers I am able to run an extended desktop.... as soon as I activate that proprietery driver I am only able to run a clone of the primary desktop....  I'll just have to submit it as a bug report I guess...

---

