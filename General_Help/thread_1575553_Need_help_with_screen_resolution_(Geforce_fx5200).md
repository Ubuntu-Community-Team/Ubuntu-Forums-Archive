---
title: "Need help with screen resolution (Geforce fx5200)"
date: 2010-09-15
forum: General Help
---

### Post by Lurker4hire on 2010-09-15
Hey guys I've been trying a bunch of different solutions to get this fixed.  Let me give you the details:  

I'm currently on Ubuntu 10.04 Lucid Lynx.   I have a Geforce FX 5200 graphics card and I have the nvidia proprietary drivers installed (version 96, I tried 173 as well but there's doesn't seem to be a difference).   

My monitors native resolution is 1680x1050 but since my graphics card cannot handle that resolution I use 1280x1024. I've had this resolution working before on Ubuntu as well as Windows with the same graphics card.  

My problem is that in nvidia-control, the list of resolutions does not include 1280x1024, and the closest to that is 1280x900 which is not supported by my monitor. So the only tolerable resolution I can get is 1024x768.. if you've used this resolution then you know that it is not tolerable for long.  So I tried to force the resolution by using xorg.conf.. Here it is:  

>  Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Samsung"
    ModelName      "Series 3 330"
    HorizSync       30.0 - 60.0
    VertRefresh     60.0 - 75.0
    Option         "DPMS"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option    "AddARGBGLXVisuals"    "True"
    SubSection "Display"
        Depth    24
        Modes    "1280x1024"
    EndSubSection
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier     "Device0"
    VendorName     "NVIDIA Corporation"
    Option    "UseEDID"    "FALSE"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection
 

For some reason this isn't forcing 1280x1024.. I'm still in 1024x768 and it still doesn't list it in nvidia-control.. What's weird is that on the previous release (Jaunty or Hardy) this xorg.conf worked fined and got me my 1280x1024.

 I'd really appreciate any insight into this. Thanks a bunch.

---

### Post by Lurker4hire on 2010-09-16
After messing around a bit, I realize that it doesn't matter what resolution I put in my xorg.conf it doesn't effect anything. Why isn't my xorg.conf file overriding nvidia-control?

---

### Post by papibe on 2010-09-16
Why are you not letting the driver to read the monitor info?
> Option "UseEDID" "FALSE"
I assume you tried it, didn't work and then you decided not to get it.

The first place to look is the log of X. Right after you restart, check this:
```
$ more /var/log/Xorg.0.log
```
Check for errors (EE). You may want to check this both with the UseEDID as it is, and then commenting that line.

Regards.

---

### Post by Lurker4hire on 2010-09-16
Thanks for the response. From previous escapades I determined that it's best to ignore EDID with this monitor. I checked my logs both times with and without that line commented, didn't change anything. Both times I've gotten this:

> (II) NVIDIA(0): NVIDIA GPU GeForce FX 5200 (NV34) at PCI:4:1:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 04.34.20.69.51
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce FX 5200 at PCI:4:1:0:
(--) NVIDIA(0):     CRT-0
(--) NVIDIA(0): CRT-0: 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(WW) NVIDIA(0): No valid modes for "1280x1024"; removing.
(WW) NVIDIA(0): No valid modes for "1680x1050"; removing.
(WW) NVIDIA(0): 
(WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(0):     "nvidia-auto-select".
(WW) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
(WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
(WW) NVIDIA(0):     from CRT-0's EDID.


Not sure what the deal is...

---

### Post by Lurker4hire on 2010-09-16
Alright I fixed the problem. After reading about How modes are validated on Nvidia's website here:

[ftp://download.nvidia.com/XFree86/Linux-x86/169.04/README/chapter-19.html](ftp://download.nvidia.com/XFree86/Linux-x86/169.04/README/chapter-19.html)

I realized it must have something to do with the frequencies I've set. So I was messing around with them and ended up fixing the problem.

Here's the critical part of the readme:

>  
**How Modes Are Validated**

 In traditional XFree86/X.Org mode validation, the X server takes as a starting point the X server's internal list of VESA standard modes, plus any modes specified with special ModeLines in the X configuration file's Monitor section. These modes are validated against criteria such as the valid HorizSync/VertRefresh frequency ranges for the user's monitor (as specified in the Monitor section of the X configuration file), as well as the maximum pixel clock of the GPU.
 Once the X server has determined the set of valid modes, it takes the list of user requested modes (i.e., the set of modes named in the "Modes" line in the Display subsection of the Screen section of X configuration file), and finds the "best" validated mode with the requested name.
 The NVIDIA X driver uses a variation on the above approach to perform mode validation. During X server initialization, the NVIDIA X driver builds a pool of valid modes for each display device. It gathers all possible modes from several sources:
  
[LIST]
[*] The display device's EDID
[*] The X server's built-in list
[*] Any user-specified ModeLines in the X configuration file
[*] The VESA standard modes
[/LIST]
 
 For every possible mode, the mode is run through mode validation. The core of mode validation is still performed similarly to traditional XFree86/X.Org mode validation: the mode timings are checked against things such as the valid HorizSync and VertRefresh ranges and the maximum pixelclock. Note that each individual stage of mode validation can be independently controlled through the "ModeValidation" X configuration option.
 Invalid modes are discarded; valid modes are inserted into the mode pool. See MODE VALIDATION REPORTING for how to get more details on mode validation results for each considered mode.


Damn 1280x1024 feels SO MUCH BETTER than 1024x768. 



Also for anyone else who may have a similar problem in the future, here is my final working xorg.conf



> Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Samsung"
    ModelName      "Series 3 330"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    VendorName     "NVIDIA Corporation"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
#    Option    "UseEDID"    "FALSE"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    Option    "AddARGBGLXVisuals"    "True"
    DefaultDepth    24
    SubSection "Display"
        Depth    24
        Modes    "1280x1024" 
    EndSubSection
EndSection

Section "Module"
    Load    "glx"
EndSection


Thanks for the help.

---

