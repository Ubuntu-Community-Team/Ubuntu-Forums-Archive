---
title: "Native Display resolution not detected with DVI cable"
date: 2009-09-30
forum: General Help
---

### Post by samlinux2 on 2009-09-30
I have a new HD Digital Flat Panel (asus vh226h) that is not behaving well under Ubuntu (9.04).  When connected via the DVI cable, the native resolution (1920x1080) is not recognized.  When connected with the VGA cable, it works fine.  For various reasons, I need it to work with the DVI cable.  Note that it works in Windows at full native resolution with either cable.  I've attached some facts below.  If, after reviewing the facts, you can tell me what I'm doing wrong or, even better, how to fix it, I'd appreciate it.  ...and, PS, I searched high and low for a solution before posting - and yes, I've seen others with Nvidia FX5200 problems, but please read on...

HW: Nvidia FX 5200 graphics card, ASUS VH226H display
SW: Nvidia's latest driver 173.14.16 (as of September 28, 2009)
The EDID file reflects a native resolution of 1920 x 1080 pixels (in both cases)
The main difference in the Xorg log files (attached below) is that the VGA connects to CRT-0, the DVI connects to DFP-0.  Is this where the problem lies?
NOTE: The Metamodes (commented out in xorg.conf) did not work, thus they are commented out).

Xorg.0.log for the DVI cable connection (doesn't work) (relevant portion only):
```
(**) NVIDIA(0): Option "CustomEDID" "DFP-0:/etc/X11/edid.bin"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce FX 5200 (NV34) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 04.34.20.87.00
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce FX 5200 at PCI:1:0:0:
(--) NVIDIA(0):     ACI VH226 (DFP-0)
(--) NVIDIA(0): ACI VH226 (DFP-0): 135.0 MHz maximum pixel clock
(--) NVIDIA(0): ACI VH226 (DFP-0): Internal Single Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(==) NVIDIA(0): 
(==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) NVIDIA(0):     will be used as the requested mode.
(==) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1600 x 1200
(--) NVIDIA(0): DPI set to (84, 112); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
```
Xorg.0.log for the VGA cable (this one works) (equivalent lines):
```
(**) NVIDIA(0): Option "CustomEDID" "DFP-0:/etc/X11/edid.bin"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce FX 5200 (NV34) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 04.34.20.87.00
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce FX 5200 at PCI:1:0:0:
(--) NVIDIA(0):     ACI VH226 (CRT-0)
(--) NVIDIA(0): ACI VH226 (CRT-0): 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(==) NVIDIA(0): 
(==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) NVIDIA(0):     will be used as the requested mode.
(==) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
(--) NVIDIA(0): DPI set to (101, 101); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
```xorg.conf (updated by nvidia-settings):
```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Asus"
    ModelName      "ACI VH226"
    HorizSync       31.0 - 83.0
    VertRefresh     50.0 - 76.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
    Option         "NoLogo" "True"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "TwinView" "0"
#   Option         "metamodes" "1600x1200 +0+0"
#   Option         "metamodes" "1920x1080 +0+0"
    Option         "CustomEDID" "DFP-0:/etc/X11/edid.bin"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```Any help you can provide would be appreciated.

---

### Post by samlinux2 on 2009-10-02
Bump

---

### Post by IanUK on 2009-12-29
I am about to purchase a ASUS VH226H monitor - has anyone got this working ok with Ubuntu?
Cheers, Ian
.

---

### Post by IanUK on 2010-01-06
Ref the ASUS VH226H, see the comments here -

[http://www.newegg.com/Product/ProductReview.aspx?Item=24-236-051&SortField=0&SummaryType=0&Pagesize=10&SelectedRating=3&PurchaseMark=&VideoOnlyMark=False&VendorMark=&Keywords=%28keywords%29&Page=3](http://www.newegg.com/Product/ProductReview.aspx?Item=24-236-051&SortField=0&SummaryType=0&Pagesize=10&SelectedRating=3&PurchaseMark=&VideoOnlyMark=False&VendorMark=&Keywords=%28keywords%29&Page=3)

It looks like this screen does not do black very well.
I have yet to workout if you can or can not use resolutions other then the native one - it looks like that may be the only choice.

There are also the usual gripes about backlight bleed with TN screens and about the built in speakers being small - what do they expect......!

Ian
.

---

### Post by wkulecz on 2010-01-06
I filed a bug report about this on 6.06 for my Sony 1920x1200 LCD display which could only show 1600x1200 :(

Resolution was it was not a bug as the monitor "lies" about it capability over DVI :(   But Windows manages to figure things out and show 1920x1200 over DVI.

I suspect you are in the same boat.  I get 1920x1600 over analog through a KVM switch just fine with no loss of quality I can see.  To be honest this experience has soured me completely on DVI at least until monitors get to resolutions greater than 1920x1200.  I'd be miffed if I had gone out and purchased a DVI cable, but fortunately one came with the monitor.

--wally.

---

### Post by nigeldodd on 2010-01-29
> **wkulecz said:**
> To be honest this experience has soured me completely on DVI at least until monitors get to resolutions greater than 1920x1200.  I'd be miffed if I had gone out and purchased a DVI cable, but fortunately one came with the monitor.

--wally.

Slightly similar experience: I had a Nvidia GF 6500 working fine at 1920x1200 over DVI-D, then the DVI-D output from the card stopped working. The cable and the monitor checked out ok on other systems. So I bought a Nvidia GeForce 8400 GS to replace it. Works fine on analog D-sub VGA port but only runs at 640x480 on the DVI. The Nvidia drivers (185) ARE being used at this low resolution and the problem appears to be that the driver does not properly interrogate the monitor when the DVI-D connection is used. When I use the VGA connector, the driver correctly reports Samsung SyncMaster 1920x1080 but when I use the DVI-D connector it  reports only DFP-0 i.e. generic digital flat panel and it presumably cannot detect the resolution of this monitor.

This vidia GeForce 8400 GS has a DVI-I (i.e. integrated analog and digital) connector whereas the Nvidia GF 6500 has a DVI-D which is the same as the monitor. I wonder if this integrated DVI connector is somehow unable to pass back the monitor's details to the graphics card. Or is there another solution that I have missed?

The digital picture was slightly sharper than the analog so I would still like to get this working.

---

### Post by nigeldodd on 2010-02-05
I have at last got DVI working from my Nvidia Geforce 8400 under Ubuntu 9.10 64 bit. It involved getting the EDID data while using the analog connector which allowed the card and monitor to work at 1920x1080. Then, rebooting and using the DVI connector, which only worked at 640x480 because it could not detect the monitor, forcing it to use the previously obtained EDID data file. This was done by putting an extra line in xorg.conf.

Full details at [http://forums.nvidia.com/lofiversion/index.php?t73027.html](http://forums.nvidia.com/lofiversion/index.php?t73027.html)

I still do not understand why the Nvidia Geforce 8400 cannot detect through its DVI connector the specifics of the Samsung SyncMaster monitor. It did with a Nvidia Geforce 6500 using DVI.

---

### Post by mikeh on 2010-04-28
If the monitor auto-detect does not work, you can always do it the old-fashioned way and edit /etc/X11/xorg.conf

Just add some lines in the "Monitor" section. e.g.

    HorizSync       31.0 - 83.0
    VertRefresh     50.0 - 76.0

Or whatever your monitor supports.

Then restart X, and the GUI should offere suitable settings.

---

