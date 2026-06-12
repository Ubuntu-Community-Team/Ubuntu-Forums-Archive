---
title: "HDMI broken after update"
date: 2010-10-24
forum: General Help
---

### Post by spvo on 2010-10-24
Hello,

I have an acer revo with XBMC installed that I use for a media center PC.  Last night I updated it for the first time in a while, and now the HDMI output no longer works correctly.  It displays video up until the ubuntu splash screen, then the screen goes blank and the television reports that signal has been lost.  I can still ssh into the machine, and I've even tried VNC and get an error: ```
xtightvncviewer: ConnectToTcpAddr: connect: Connection refused
Unable to connect to VNC server
```

The VGA output still works perfectly, but I need to get the hdmi up and running again for my television.  Any suggestions as to what may be causing this?  Thanks.

---

### Post by spvo on 2010-10-31
I have sort of figured out what happened and hopefully this will help someone else.  For some reason the newer nvidia drivers, I even tried installing directly from nvidia, no longer recognize the EDID for my television using HDMI, but does read it fine using the VGA port.  The error in the x11 log was
```
Unable to read EDID for display device CRT-0
```  After much trial and error I discovered that the HDMI port uses different frequencies than the vga for the same resolution screen.  And, the tv would just display 'no signal' unless the resolution and frequencies were a perfect match.  I looked for televisions with the same brand, and just started working through the modlines listed [here, http://www.mythtv.org/wiki/Modeline_Database, ]("http://www.mythtv.org/wiki/Modeline_Database") until eventually I got lucky and found one that actually worked.  So, in case someone has a toshiba 32AV52R, here are the relevant parts of my xorg.conf that fixed the problem.
```
Section "Monitor"
        Identifier   "Monitor0"

        VendorName   "Toshiba"
        ModelName    "Toshiba"

        Option "ConnectedMonitor" "DFP"
        Option "USEEDIDDpi" "FALSE"
        Option "DPI" "100 x 100"
        Option "UseEDIDFreqs" "FALSE"
        Option "ModeValidation" "NoDFPNativeResolutionCheck"
        Option "ExactModeTimingsDVI" "true"

        HorizSync   15.000 - 68.000
        VertRefresh 23.000 - 61.000

	Option         "PreferredMode" "1280x720"

        ModeLine  "1920x1080" 148.50 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync
        ModeLine  "1280x720"   74.25 1280 1390 1430 1650  720  725  730  750 +hsync +vsync
        ModeLine  "720x480"    27.00  720  736  798  858  480  489  495  525 -hsync -vsync
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
	Modes      "1280x720"
    EndSubSection
EndSection
```

I'm still having a problem with getting sound to work over HDMI though.  The analog out on the computer works fine, so for the time being I've just connected some computer speakers.  I've tried selecting the HDMI digital output, and when I do I get no sound output at all.  Anyone know where to start troubleshooting?

---

### Post by efflandt on 2010-11-01
[http://us.download.nvidia.com/XFree86/Linux-x86/173.14.09/README/appendix-b.html](http://us.download.nvidia.com/XFree86/Linux-x86/173.14.09/README/appendix-b.html) says about "ConnectedMonitor": **It is generally recommended to not use this option, but instead use the "UseDisplayDevice" option.**

I had to use **Option "UseDisplayDevice" "DFP"** for an old laptop with nvidia when I got a blank laptop screen, because the nvidia 96 driver defaulted to its VGA port (CRT-0).

---

