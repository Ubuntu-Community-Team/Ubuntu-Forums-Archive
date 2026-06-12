---
title: "How can I restrict XFree86 to certain allowed monitor modes?"
date: 2005-02-05
forum: General Help
---

### Post by Colin on 2005-02-05
(My first post to the forum. Impressed with Ubuntu Warty so far...)
This may be pedantic but I'm eager to know...

I have manged to add Nvidia drivers and increase my monitor resolution.
I'm running GDM at 1600x1200@75Hz using an old Philips 201B monitor; I'm happy to stay at that res/mode.

I can't find any monitor documentation as it is quite old (manuf 1996), so I don't know HorizSync and VertRefresh values.
To set the monitor modes up, I ran sudo dpkg-reconfigure xserver-xfree86.
During that config, I chose the 'medium' config path for the monitor and specified the maximum rate as 1600x1200@75Hz

ddcprobe says that mode is supported.

Now in GDM under *Computer > System Configuration > Screen Resolution*, taking resolution 1600x1200 for example, I can select a number of refresh rates: 75, 70, 65, 60Hz.

A glance at my ddcprobe says only 75, 60Hz are supported at 1600x1200.
My question is: Is there a way to tell XFree to not allow 1600x1200@70Hz and 1600x1200@65Hz?

(I have tried to follow the mode and modeline details in the XF86Config-4 man page. I'm not sure if that is the bit to use, and if it is, where I can find values for DotClock, HTimings etc. Layout examples are welcome.)

I expect this problem also happens for other resolutions.
Previously with Suse 7.1, I was able to select some unsupported modes using SaX2, and that lead to my monitor playing up for a while (flicker and poor colour).

My need to know is so that I can block these unsupported modes out if possible.
It's  unlikely that I will select the incorrect mode, but maybe another user in my house will.

Useful files below, also attached is my XFree86.0.log

Another question for anybody: I have followed advice on the forum and removed GLcore and dri modules. Given that I have a 32MB Geforce 2 MX, was I right to remove the items?


My XF86Config-4:
```
Section "Files"
        FontPath        "unix/:7100"                    # local font server
        # if the local font server has problems, we can fall back on these
        FontPath        "/usr/lib/X11/fonts/misc"
        FontPath        "/usr/lib/X11/fonts/cyrillic"
        FontPath        "/usr/lib/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/lib/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/lib/X11/fonts/Type1"
        FontPath        "/usr/lib/X11/fonts/CID"
        FontPath        "/usr/lib/X11/fonts/Speedo"
        FontPath        "/usr/lib/X11/fonts/100dpi"
        FontPath        "/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "record"
        Load    "speedo"
        Load    "type1"
        Load    "v4l"
        Load    "vbe"
        Load    "xtt"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "keyboard"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xfree86"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "gb"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "Device"
        Identifier      "NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "NoLogo"                "true"
        Option          "RenderAccel"           "true"
        Option          "NvAGP"                 "1"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        HorizSync       30-75
        VertRefresh     50-85
        Option          "DPMS"
EndSection

Section "Monitor"
        Identifier      "Philips 201B"
        HorizSync       30-94
        VertRefresh     50-75
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
        Monitor         "Philips 201B"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

```
My ddcprobe:
```
vbe: VESA 3.0 detected.
oem: NVidia
vendor: NVidia Corporation
product: NV10 Reference Board Chip Rev A1
memory: 32768kb
mode: 640x400x256
mode: 640x480x256
mode: 800x600x16
mode: 800x600x256
mode: 1024x768x16
mode: 1024x768x256
mode: 1280x1024x16
mode: 1280x1024x256
mode: 80x60 (text)
mode: 132x25 (text)
mode: 132x43 (text)
mode: 132x50 (text)
mode: 132x60 (text)
mode: 320x200x64k
mode: 320x200x16m
mode: 640x480x64k
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 1024x768x64k
mode: 1024x768x16m
mode: 1280x1024x64k
edid: 1 0
id: 201b
eisa: PHL201b
serial: 000009b3
manufacture: 45 1996
input: separate sync, composite sync, sync on green, analog signal.
screensize: 38 29
gamma: 2.800000
dpms: RGB, active off, suspend, standby
timing: 720x400@70 Hz (VGA 640x400, IBM)
timing: 720x400@88 Hz (XGA2)
timing: 640x480@75 Hz (VESA)
timing: 800x600@72 Hz (VESA)
timing: 800x600@75 Hz (VESA)
timing: 1024x768@70 Hz (VESA)
timing: 1024x768@75 Hz (VESA)
timing: 1280x1024@75 (VESA)
ctiming: 1024x768@85
ctiming: 1280x1024@60
ctiming: 1280x1024@85
ctiming: 1600x1200@60
ctiming: 1600x1200@75
dtiming: 640x400@70
dtiming: 1152x900@91

```

---

### Post by daniels on 2005-02-05
If your monitor can deal with 1600x1200 @ 75Hz, it can also deal with 70 and 65 Hz just fine.

---

