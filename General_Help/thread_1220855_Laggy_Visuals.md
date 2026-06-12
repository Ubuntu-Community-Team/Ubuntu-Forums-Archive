---
title: "Laggy Visuals"
date: 2009-07-23
forum: General Help
---

### Post by born2rule on 2009-07-23
Hi all ! I`m on Ubuntu 9.04 for about 2 weeks now, and i`m experiencing some nasty delays when i have the visuals enabled to extra and even normal. I have installed compiz fusion  and avant window manager and whenever i want to maximize a full screen window i have about 1 sec delay before the animation starts(this happens with all smaller windows but the delay is smaller). I`ve tried with all settings possible, the only way to stop the delay is to turn off animations.

 Also i am experiencing general poor performance as well. When i am listening to music via Rythmbox( or something like that) and i start firefox up, the music stops a few times as if the cpu is used at 100%. Also i have a very big problem with HD movies (i tried KMPlayer, VLC, SMPlayer, Mplayer, etc), they are extremly choppy (the 720p one that is, the 1080p ones won`t even start). I have the video drivers enabled, i have all the updates installed and still the same. 

I don`t know why this could be, and it`s not because of the system itselft (i have an e7300, HD4850, 4gb ram, and a p5q mb). I am quite surprised because i was hoping at least the same performance as windows7.

---

### Post by tsali on 2009-08-30
Sorry you haven't received any responses.

I am experiencing the same issue.

I have an nvidia 7600GT and a Sceptre monitor combination that requires me to use an older nvidia driver.

I set up nvidia using envy.

Everything worked great in Ibex. Now that I've installed Jaunty, the system is all but unusable with desktop effects enabled.

This is big for me, because I've gotten used to using the AWN dock, which doesn't run at all without compiz.

Anyone have any ideas? Where to start?

---

### Post by Liolikas on 2009-08-30
Do you use the latest proprietary nvidia drivers?

---

### Post by CatKiller on 2009-08-30
> **tsali said:**
>  This is big for me, because I've gotten used to using the AWN dock, which doesn't run at all without compiz.

AWN doesn't run without a compositing window manager. It doesn't have to be Compiz.

You might find you get better performance if you turn off some of the Compiz plugins. Any of the blur effects seem to run particularly badly on nVidia cards; I don't think they get passed to the graphics card, which means that they are run on the processor instead.

Having the animation times set too long (which is the default) makes the system feel really unresponsive, too. Increasing the speed will help.

---

### Post by P4man on 2009-08-30
> **tsali said:**
> 

I have an nvidia 7600GT and a Sceptre monitor combination that requires me to use an older nvidia driver.

Your videocard **is** supported by all the latest nvidia drivers. They support down to the geforce 6 series. 

FWIW, I have a 7900GS which is quite comparable to your card, it runs all compiz effects effortlessly on 2 big monitors (200+ FPS). The monitor shouldn't be an issue.

---

### Post by tsali on 2009-08-30
> **P4man said:**
> Your videocard **is** supported by all the latest nvidia drivers. They support down to the geforce 6 series. 

FWIW, I have a 7900GS which is quite comparable to your card, it runs all compiz effects effortlessly on 2 big monitors (200+ FPS). The monitor shouldn't be an issue.

The card is supported but the monitor is not. The later drivers are dependent on monitor EDID data to configure correctly. The Sceptre monitor doesn't pass edid to the drivers correctly.

Therefore, I'm forced to use the last series of nvidia drivers that didn't require this function.

---

### Post by tsali on 2009-08-30
> **Liolikas said:**
> Do you use the latest proprietary nvidia drivers?

I cannot run the latest drivers because they dependent on monitor edid data. Sceptre monitor does not pass these correctly.

---

### Post by tsali on 2009-08-30
> **CatKiller said:**
> AWN doesn't run without a compositing window manager. It doesn't have to be Compiz.

You might find you get better performance if you turn off some of the Compiz plugins. Any of the blur effects seem to run particularly badly on nVidia cards; I don't think they get passed to the graphics card, which means that they are run on the processor instead.

Having the animation times set too long (which is the default) makes the system feel really unresponsive, too. Increasing the speed will help.

There were no plug-ins installed other than the default "normal" set. Doesn't appear to be a control panel for those.

What went wrong in Jaunty? everything worked fine in Ibex.

---

### Post by CatKiller on 2009-08-30
> **tsali said:**
> The card is supported but the monitor is not. The later drivers are dependent on monitor EDID data to configure correctly. The Sceptre monitor doesn't pass edid to the drivers correctly.

You can give the numbers manually, you know. You haven't said what the model of your monitor is, so we can't help you search, but the most critical values are the refresh rate ranges that your monitor can do. You should be able to find them in the monitor manual or documentation. They go in the Monitor section of your xorg.conf like so:

```
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       aa-bb
        VertRefresh     cc-dd
EndSection

```You'll need to replace aa-dd with the values for **your** monitor.

If your monitor gives erroneous numbers instead of no numbers at all (as mine does) you may find that you need to tell X to ignore everything it receives and just use the numbers you've given it. You can do this by putting 

```
        Option          "UseEDID"                       "False"
``` in the Device section.

> **tsali said:**
> There were no plug-ins installed other than the default "normal" set. Doesn't appear to be a control panel for those.

Install CompizConfig Settings Manager. All the options you can eat.

---

### Post by tsali on 2009-09-01
> **CatKiller said:**
> You can give the numbers manually, you know. You haven't said what the model of your monitor is, so we can't help you search, but the most critical values are the refresh rate ranges that your monitor can do. You should be able to find them in the monitor manual or documentation. They go in the Monitor section of your xorg.conf like so:

```
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       aa-bb
        VertRefresh     cc-dd
EndSection

```You'll need to replace aa-dd with the values for **your** monitor.

If your monitor gives erroneous numbers instead of no numbers at all (as mine does) you may find that you need to tell X to ignore everything it receives and just use the numbers you've given it. You can do this by putting 

```
        Option          "UseEDID"                       "False"
``` in the Device section.



Install CompizConfig Settings Manager. All the options you can eat.

Been there and done that to no avail. The late nvidia drivers seem to ignore the x configuration or it writes it on the fly...I'm not sure which. Adjustments to it when using the late nvidia drivers make no difference whatsoever.

The Sceptre monitor is an X20. It is SUPPOSED to provide EDID data but apparently has corrupt EDID from the factory. I'll likely replace it at some point, but it displays too good an image otherwise. Sceptre will not provide me with an EDID image to reflash the chip.

---

### Post by CatKiller on 2009-09-01
> **tsali said:**
> The late nvidia drivers seem to ignore the x configuration or it writes it on the fly...I'm not sure which.

No they don't. I'm using the 180 driver and my customised xorg.conf works fine. My monitor also returns incorrect EDID values, which is why I know that you can specify them yourself.

You can put ```
        Option          "ModeDebug"                     "True"
``` in the Device section if you want /var/log/Xorg.0.log to have verbose output about the modes it's using and the modes it isn't.

> 
The Sceptre monitor is an X20.

Is it [this one]("http://www.sceptre.com/Products/LCD/Specifications/spec_x20sv_naga.htm")? According to that page the values you need are ```
        HorizSync       21-82
        VertRefresh     50-75
```

I'm assuming that the problem you are experiencing is a resolution problem. If the problem is that the refresh rates being reported are in the 50s, then that isn't a problem at all. That is deliberate on nVidia's part.

---

### Post by tsali on 2009-09-01
I'm also using the 180 driver.

I loaded those values exactly...only to have it return "out of range". I also tried the digital spec values of 31-80. Same.
I have to ctrl-alt f1 to get a session and revise the file from there to get anything back.

What did I do wrong? Here is my xorg.conf file without the modifications (after nvidia install):

```

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
        Disable "dri2"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver  "nvidia"
EndSection


```

---

### Post by CatKiller on 2009-09-02
> **tsali said:**
>  What did I do wrong? 

What does the log file say about the mode that it's picked?

---

### Post by tsali on 2009-09-02
It has rejected all modes except 640x480

```

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux ubuntu-desktop 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Sep  2 05:48:34 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@1:0:0) nVidia Corporation G70 [GeForce 7300 GT] rev 161, Mem @ 0xfa000000/16777216, 0xd0000000/268435456, 0xfb000000/16777216, I/O @ 0x0000cf00/128, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(WW) "dri2" will not be loaded unless you've specified it to be loaded elsewhere.
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded even though the default is to disable it.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  180.44  Mon Mar 23 15:29:02 PST 2009
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  180.44  Mon Mar 23 15:05:32 PST 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "ModeDebug" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(WW) NVIDIA(GPU-0): Unable to read EDID for display device DFP-0
(II) NVIDIA(0): NVIDIA GPU GeForce 7300 GT (G73) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.73.22.40.00
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7300 GT at PCI:1:0:0:
(--) NVIDIA(0):     DFP-0
(--) NVIDIA(0): DFP-0: 330.0 MHz maximum pixel clock
(--) NVIDIA(0): DFP-0: Internal Dual Link TMDS
(--) NVIDIA(0): 
(--) NVIDIA(0): --- EDID for DFP-0 ---
(--) NVIDIA(0): 
(--) NVIDIA(0): No EDID Available.
(--) NVIDIA(0): 
(--) NVIDIA(0): --- End of EDID for DFP-0 ---
(--) NVIDIA(0): 
(II) NVIDIA(0): Frequency information for DFP-0:
(II) NVIDIA(0):   HorizSync   : 28.000-55.000 kHz
(II) NVIDIA(0):   VertRefresh : 43.000-72.000 Hz
(II) NVIDIA(0):     (HorizSync from Conservative Defaults)
(II) NVIDIA(0):     (VertRefresh from Conservative Defaults)
(II) NVIDIA(0): 
(II) NVIDIA(0): --- Building ModePool for DFP-0 ---
(II) NVIDIA(0): 
(II) NVIDIA(0): Native backend timings for DFP-0:
(II) NVIDIA(0):   640 x 480 @ 60 Hz
(II) NVIDIA(0):     Pixel Clock      : 25.175 MHz
(II) NVIDIA(0):     HRes, HSyncStart :  640,  656
(II) NVIDIA(0):     HSyncEnd, HTotal :  752,  800
(II) NVIDIA(0):     VRes, VSyncStart :  480,  490
(II) NVIDIA(0):     VSyncEnd, VTotal :  492,  525
(II) NVIDIA(0):     H/V Polarity     : -/-
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x350":
(II) NVIDIA(0):     640 x 350 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  672
(II) NVIDIA(0):       HSyncEnd, HTotal :  736,  832
(II) NVIDIA(0):       VRes, VSyncStart :  350,  382
(II) NVIDIA(0):       VSyncEnd, VTotal :  385,  445
(II) NVIDIA(0):       H/V Polarity     : +/-
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.1 Hz) out of range
(WW) NVIDIA(0):     (43.000-72.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "320x175":
(II) NVIDIA(0):     320 x 175 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 15.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  320,  336
(II) NVIDIA(0):       HSyncEnd, HTotal :  368,  416
(II) NVIDIA(0):       VRes, VSyncStart :  175,  191
(II) NVIDIA(0):       VSyncEnd, VTotal :  192,  222
(II) NVIDIA(0):       H/V Polarity     : +/-
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.3 Hz) out of range
(WW) NVIDIA(0):     (43.000-72.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x400":
(II) NVIDIA(0):     640 x 400 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  672
(II) NVIDIA(0):       HSyncEnd, HTotal :  736,  832
(II) NVIDIA(0):       VRes, VSyncStart :  400,  401
(II) NVIDIA(0):       VSyncEnd, VTotal :  404,  445
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.1 Hz) out of range
(WW) NVIDIA(0):     (43.000-72.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "320x200":
(II) NVIDIA(0):     320 x 200 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 15.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  320,  336
(II) NVIDIA(0):       HSyncEnd, HTotal :  368,  416
(II) NVIDIA(0):       VRes, VSyncStart :  200,  200
(II) NVIDIA(0):       VSyncEnd, VTotal :  202,  222
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.3 Hz) out of range
(WW) NVIDIA(0):     (43.000-72.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "720x400":
(II) NVIDIA(0):     720 x 400 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 35.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  720,  756
(II) NVIDIA(0):       HSyncEnd, HTotal :  828,  936
(II) NVIDIA(0):       VRes, VSyncStart :  400,  401
(II) NVIDIA(0):       VSyncEnd, VTotal :  404,  446
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.0 Hz) out of range
(WW) NVIDIA(0):     (43.000-72.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "360x200":
(II) NVIDIA(0):     360 x 200 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 17.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  360,  378
(II) NVIDIA(0):       HSyncEnd, HTotal :  414,  468
(II) NVIDIA(0):       VRes, VSyncStart :  200,  200
(II) NVIDIA(0):       VSyncEnd, VTotal :  202,  223
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.0 Hz) out of range
(WW) NVIDIA(0):     (43.000-72.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 25.18 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  656
(II) NVIDIA(0):       HSyncEnd, HTotal :  752,  800
(II) NVIDIA(0):       VRes, VSyncStart :  480,  490
(II) NVIDIA(0):       VSyncEnd, VTotal :  492,  525
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     BestFit Backend for "640x480": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "320x240":
(II) NVIDIA(0):     320 x 240 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 12.59 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  320,  328
(II) NVIDIA(0):       HSyncEnd, HTotal :  376,  400
(II) NVIDIA(0):       VRes, VSyncStart :  240,  245
(II) NVIDIA(0):       VSyncEnd, VTotal :  246,  262
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "320x240": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 73 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  664
(II) NVIDIA(0):       HSyncEnd, HTotal :  704,  832
(II) NVIDIA(0):       VRes, VSyncStart :  480,  489
(II) NVIDIA(0):       VSyncEnd, VTotal :  492,  520
(II) NVIDIA(0):       H/V Polarity     : -/-
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (72.8 Hz) out of range
(WW) NVIDIA(0):     (43.000-72.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "320x240":
(II) NVIDIA(0):     320 x 240 @ 73 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 15.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  320,  332
(II) NVIDIA(0):       HSyncEnd, HTotal :  352,  416
(II) NVIDIA(0):       VRes, VSyncStart :  240,  244
(II) NVIDIA(0):       VSyncEnd, VTotal :  246,  260
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (72.8 Hz) out of range
(WW) NVIDIA(0):     (43.000-72.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  656
(II) NVIDIA(0):       HSyncEnd, HTotal :  720,  840
(II) NVIDIA(0):       VRes, VSyncStart :  480,  481
(II) NVIDIA(0):       VSyncEnd, VTotal :  484,  500
(II) NVIDIA(0):       H/V Polarity     : -/-
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (75.0 Hz) out of range
(WW) NVIDIA(0):     (43.000-72.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "320x240":
(II) NVIDIA(0):     320 x 240 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 15.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  320,  328
(II) NVIDIA(0):       HSyncEnd, HTotal :  360,  420
(II) NVIDIA(0):       VRes, VSyncStart :  240,  240
(II) NVIDIA(0):       VSyncEnd, VTotal :  242,  250
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (75.0 Hz) out of range
(WW) NVIDIA(0):     (43.000-72.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 36.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  696
(II) NVIDIA(0):       HSyncEnd, HTotal :  752,  832
(II) NVIDIA(0):       VRes, VSyncStart :  480,  481
(II) NVIDIA(0):       VSyncEnd, VTotal :  484,  509
(II) NVIDIA(0):       H/V Polarity     : -/-
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.0 Hz) out of range
(WW) NVIDIA(0):     (43.000-72.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "320x240":
(II) NVIDIA(0):     320 x 240 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 18.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  320,  348
(II) NVIDIA(0):       HSyncEnd, HTotal :  376,  416
(II) NVIDIA(0):       VRes, VSyncStart :  240,  240
(II) NVIDIA(0):       VSyncEnd, VTotal :  242,  254
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.2 Hz) out of range
(WW) NVIDIA(0):     (43.000-72.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 56 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 36.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  824
(II) NVIDIA(0):       HSyncEnd, HTotal :  896, 1024
(II) NVIDIA(0):       VRes, VSyncStart :  600,  601
(II) NVIDIA(0):       VSyncEnd, VTotal :  603,  625
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode (800 x 600) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "800x600" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "400x300":
(II) NVIDIA(0):     400 x 300 @ 56 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 18.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  400,  412
(II) NVIDIA(0):       HSyncEnd, HTotal :  448,  512
(II) NVIDIA(0):       VRes, VSyncStart :  300,  300
(II) NVIDIA(0):       VSyncEnd, VTotal :  301,  312
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "400x300": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 40.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  840
(II) NVIDIA(0):       HSyncEnd, HTotal :  968, 1056
(II) NVIDIA(0):       VRes, VSyncStart :  600,  601
(II) NVIDIA(0):       VSyncEnd, VTotal :  605,  628
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode (800 x 600) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "800x600" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "400x300":
(II) NVIDIA(0):     400 x 300 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 20.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  400,  420
(II) NVIDIA(0):       HSyncEnd, HTotal :  484,  528
(II) NVIDIA(0):       VRes, VSyncStart :  300,  300
(II) NVIDIA(0):       VSyncEnd, VTotal :  302,  314
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "400x300": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 72 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 50.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  856
(II) NVIDIA(0):       HSyncEnd, HTotal :  976, 1040
(II) NVIDIA(0):       VRes, VSyncStart :  600,  637
(II) NVIDIA(0):       VSyncEnd, VTotal :  643,  666
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode (800 x 600) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "800x600" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "400x300":
(II) NVIDIA(0):     400 x 300 @ 72 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 25.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  400,  428
(II) NVIDIA(0):       HSyncEnd, HTotal :  488,  520
(II) NVIDIA(0):       VRes, VSyncStart :  300,  318
(II) NVIDIA(0):       VSyncEnd, VTotal :  321,  333
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "400x300": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 49.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  816
(II) NVIDIA(0):       HSyncEnd, HTotal :  896, 1056
(II) NVIDIA(0):       VRes, VSyncStart :  600,  601
(II) NVIDIA(0):       VSyncEnd, VTotal :  604,  625
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (75.0 Hz) out of range
(WW) NVIDIA(0):     (43.000-72.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "400x300":
(II) NVIDIA(0):     400 x 300 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 24.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  400,  408
(II) NVIDIA(0):       HSyncEnd, HTotal :  448,  528
(II) NVIDIA(0):       VRes, VSyncStart :  300,  300
(II) NVIDIA(0):       VSyncEnd, VTotal :  302,  312
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (75.1 Hz) out of range
(WW) NVIDIA(0):     (43.000-72.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 56.30 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  832
(II) NVIDIA(0):       HSyncEnd, HTotal :  896, 1048
(II) NVIDIA(0):       VRes, VSyncStart :  600,  601
(II) NVIDIA(0):       VSyncEnd, VTotal :  604,  631
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.1 Hz) out of range
(WW) NVIDIA(0):     (43.000-72.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "400x300":
(II) NVIDIA(0):     400 x 300 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 28.15 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  400,  416
(II) NVIDIA(0):       HSyncEnd, HTotal :  448,  524
(II) NVIDIA(0):       VRes, VSyncStart :  300,  300
(II) NVIDIA(0):       VSyncEnd, VTotal :  302,  315
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.3 Hz) out of range
(WW) NVIDIA(0):     (43.000-72.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 87 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 44.90 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1032
(II) NVIDIA(0):       HSyncEnd, HTotal : 1208, 1264
(II) NVIDIA(0):       VRes, VSyncStart :  768,  768
(II) NVIDIA(0):       VSyncEnd, VTotal :  776,  817
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : Interlace
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (87.0 Hz) out of range
(WW) NVIDIA(0):     (43.000-72.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "512x384":
(II) NVIDIA(0):     512 x 384 @ 87 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 22.45 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  512,  516
(II) NVIDIA(0):       HSyncEnd, HTotal :  604,  632
(II) NVIDIA(0):       VRes, VSyncStart :  384,  384
(II) NVIDIA(0):       VSyncEnd, VTotal :  388,  408
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : Interlace DoubleScan
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (87.1 Hz) out of range
(WW) NVIDIA(0):     (43.000-72.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 65.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1048
(II) NVIDIA(0):       HSyncEnd, HTotal : 1184, 1344
(II) NVIDIA(0):       VRes, VSyncStart :  768,  771
(II) NVIDIA(0):       VSyncEnd, VTotal :  777,  806
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     Mode (1024 x 768) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1024x768" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "512x384":
(II) NVIDIA(0):     512 x 384 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 32.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  512,  524
(II) NVIDIA(0):       HSyncEnd, HTotal :  592,  672
(II) NVIDIA(0):       VRes, VSyncStart :  384,  385
(II) NVIDIA(0):       VSyncEnd, VTotal :  388,  403
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "512x384": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 70 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 75.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1048
(II) NVIDIA(0):       HSyncEnd, HTotal : 1184, 1328
(II) NVIDIA(0):       VRes, VSyncStart :  768,  771
(II) NVIDIA(0):       VSyncEnd, VTotal :  777,  806
(II) NVIDIA(0):       H/V Polarity     : -/-
(WW) NVIDIA(0):     Mode is rejected: HorizSync (56.5 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "512x384":
(II) NVIDIA(0):     512 x 384 @ 70 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 37.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  512,  524
(II) NVIDIA(0):       HSyncEnd, HTotal :  592,  664
(II) NVIDIA(0):       VRes, VSyncStart :  384,  385
(II) NVIDIA(0):       VSyncEnd, VTotal :  388,  403
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (56.5 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 78.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1040
(II) NVIDIA(0):       HSyncEnd, HTotal : 1136, 1312
(II) NVIDIA(0):       VRes, VSyncStart :  768,  769
(II) NVIDIA(0):       VSyncEnd, VTotal :  772,  800
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (60.0 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "512x384":
(II) NVIDIA(0):     512 x 384 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 39.38 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  512,  520
(II) NVIDIA(0):       HSyncEnd, HTotal :  568,  656
(II) NVIDIA(0):       VRes, VSyncStart :  384,  384
(II) NVIDIA(0):       VSyncEnd, VTotal :  386,  400
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (60.0 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 94.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1072
(II) NVIDIA(0):       HSyncEnd, HTotal : 1168, 1376
(II) NVIDIA(0):       VRes, VSyncStart :  768,  769
(II) NVIDIA(0):       VSyncEnd, VTotal :  772,  808
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (68.7 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "512x384":
(II) NVIDIA(0):     512 x 384 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 47.25 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  512,  536
(II) NVIDIA(0):       HSyncEnd, HTotal :  584,  688
(II) NVIDIA(0):       VRes, VSyncStart :  384,  384
(II) NVIDIA(0):       VSyncEnd, VTotal :  386,  404
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (68.7 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1152x864":
(II) NVIDIA(0):     1152 x 864 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 108.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1152, 1216
(II) NVIDIA(0):       HSyncEnd, HTotal : 1344, 1600
(II) NVIDIA(0):       VRes, VSyncStart :  864,  865
(II) NVIDIA(0):       VSyncEnd, VTotal :  868,  900
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (67.5 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "576x432":
(II) NVIDIA(0):     576 x 432 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 54.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  576,  608
(II) NVIDIA(0):       HSyncEnd, HTotal :  672,  800
(II) NVIDIA(0):       VRes, VSyncStart :  432,  432
(II) NVIDIA(0):       VSyncEnd, VTotal :  434,  450
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (67.5 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x960":
(II) NVIDIA(0):     1280 x 960 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 108.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1376
(II) NVIDIA(0):       HSyncEnd, HTotal : 1488, 1800
(II) NVIDIA(0):       VRes, VSyncStart :  960,  961
(II) NVIDIA(0):       VSyncEnd, VTotal :  964, 1000
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (60.0 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 54.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  688
(II) NVIDIA(0):       HSyncEnd, HTotal :  744,  900
(II) NVIDIA(0):       VRes, VSyncStart :  480,  480
(II) NVIDIA(0):       VSyncEnd, VTotal :  482,  500
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (60.0 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x960":
(II) NVIDIA(0):     1280 x 960 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 148.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1344
(II) NVIDIA(0):       HSyncEnd, HTotal : 1504, 1728
(II) NVIDIA(0):       VRes, VSyncStart :  960,  961
(II) NVIDIA(0):       VSyncEnd, VTotal :  964, 1011
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (85.9 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 74.25 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  672
(II) NVIDIA(0):       HSyncEnd, HTotal :  752,  864
(II) NVIDIA(0):       VRes, VSyncStart :  480,  480
(II) NVIDIA(0):       VSyncEnd, VTotal :  482,  505
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (85.9 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x1024":
(II) NVIDIA(0):     1280 x 1024 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 108.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1328
(II) NVIDIA(0):       HSyncEnd, HTotal : 1440, 1688
(II) NVIDIA(0):       VRes, VSyncStart : 1024, 1025
(II) NVIDIA(0):       VSyncEnd, VTotal : 1028, 1066
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (64.0 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x512":
(II) NVIDIA(0):     640 x 512 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 54.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  664
(II) NVIDIA(0):       HSyncEnd, HTotal :  720,  844
(II) NVIDIA(0):       VRes, VSyncStart :  512,  512
(II) NVIDIA(0):       VSyncEnd, VTotal :  514,  533
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (64.0 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x1024":
(II) NVIDIA(0):     1280 x 1024 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 135.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1296
(II) NVIDIA(0):       HSyncEnd, HTotal : 1440, 1688
(II) NVIDIA(0):       VRes, VSyncStart : 1024, 1025
(II) NVIDIA(0):       VSyncEnd, VTotal : 1028, 1066
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (80.0 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x512":
(II) NVIDIA(0):     640 x 512 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 67.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  648
(II) NVIDIA(0):       HSyncEnd, HTotal :  720,  844
(II) NVIDIA(0):       VRes, VSyncStart :  512,  512
(II) NVIDIA(0):       VSyncEnd, VTotal :  514,  533
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (80.0 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x1024":
(II) NVIDIA(0):     1280 x 1024 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 157.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1344
(II) NVIDIA(0):       HSyncEnd, HTotal : 1504, 1728
(II) NVIDIA(0):       VRes, VSyncStart : 1024, 1025
(II) NVIDIA(0):       VSyncEnd, VTotal : 1028, 1072
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (91.1 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x512":
(II) NVIDIA(0):     640 x 512 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 78.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  672
(II) NVIDIA(0):       HSyncEnd, HTotal :  752,  864
(II) NVIDIA(0):       VRes, VSyncStart :  512,  512
(II) NVIDIA(0):       VSyncEnd, VTotal :  514,  536
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (91.1 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1200":
(II) NVIDIA(0):     1600 x 1200 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 162.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
(II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
(II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (75.0 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 81.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  832
(II) NVIDIA(0):       HSyncEnd, HTotal :  928, 1080
(II) NVIDIA(0):       VRes, VSyncStart :  600,  600
(II) NVIDIA(0):       VSyncEnd, VTotal :  602,  625
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (75.0 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1200":
(II) NVIDIA(0):     1600 x 1200 @ 65 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 175.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
(II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
(II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (81.2 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 65 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 87.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  832
(II) NVIDIA(0):       HSyncEnd, HTotal :  928, 1080
(II) NVIDIA(0):       VRes, VSyncStart :  600,  600
(II) NVIDIA(0):       VSyncEnd, VTotal :  602,  625
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (81.2 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1200":
(II) NVIDIA(0):     1600 x 1200 @ 70 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 189.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
(II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
(II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (87.5 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 70 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 94.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  832
(II) NVIDIA(0):       HSyncEnd, HTotal :  928, 1080
(II) NVIDIA(0):       VRes, VSyncStart :  600,  600
(II) NVIDIA(0):       VSyncEnd, VTotal :  602,  625
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (87.5 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1200":
(II) NVIDIA(0):     1600 x 1200 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 202.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
(II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
(II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (93.8 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 101.25 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  832
(II) NVIDIA(0):       HSyncEnd, HTotal :  928, 1080
(II) NVIDIA(0):       VRes, VSyncStart :  600,  600
(II) NVIDIA(0):       VSyncEnd, VTotal :  602,  625
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (93.8 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1200":
(II) NVIDIA(0):     1600 x 1200 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 229.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
(II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
(II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (106.2 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 114.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  832
(II) NVIDIA(0):       HSyncEnd, HTotal :  928, 1080
(II) NVIDIA(0):       VRes, VSyncStart :  600,  600
(II) NVIDIA(0):       VSyncEnd, VTotal :  602,  625
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (106.2 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1792x1344":
(II) NVIDIA(0):     1792 x 1344 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 204.80 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1792, 1920
(II) NVIDIA(0):       HSyncEnd, HTotal : 2120, 2448
(II) NVIDIA(0):       VRes, VSyncStart : 1344, 1345
(II) NVIDIA(0):       VSyncEnd, VTotal : 1348, 1394
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (83.7 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "896x672":
(II) NVIDIA(0):     896 x 672 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 102.40 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  896,  960
(II) NVIDIA(0):       HSyncEnd, HTotal : 1060, 1224
(II) NVIDIA(0):       VRes, VSyncStart :  672,  672
(II) NVIDIA(0):       VSyncEnd, VTotal :  674,  697
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (83.7 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1792x1344":
(II) NVIDIA(0):     1792 x 1344 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 261.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1792, 1888
(II) NVIDIA(0):       HSyncEnd, HTotal : 2104, 2456
(II) NVIDIA(0):       VRes, VSyncStart : 1344, 1345
(II) NVIDIA(0):       VSyncEnd, VTotal : 1348, 1417
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (106.3 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "896x672":
(II) NVIDIA(0):     896 x 672 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 130.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  896,  944
(II) NVIDIA(0):       HSyncEnd, HTotal : 1052, 1228
(II) NVIDIA(0):       VRes, VSyncStart :  672,  672
(II) NVIDIA(0):       VSyncEnd, VTotal :  674,  708
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (106.3 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1856x1392":
(II) NVIDIA(0):     1856 x 1392 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 218.30 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1856, 1952
(II) NVIDIA(0):       HSyncEnd, HTotal : 2176, 2528
(II) NVIDIA(0):       VRes, VSyncStart : 1392, 1393
(II) NVIDIA(0):       VSyncEnd, VTotal : 1396, 1439
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (86.4 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "928x696":
(II) NVIDIA(0):     928 x 696 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 109.15 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  928,  976
(II) NVIDIA(0):       HSyncEnd, HTotal : 1088, 1264
(II) NVIDIA(0):       VRes, VSyncStart :  696,  696
(II) NVIDIA(0):       VSyncEnd, VTotal :  698,  719
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (86.4 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1856x1392":
(II) NVIDIA(0):     1856 x 1392 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 288.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1856, 1984
(II) NVIDIA(0):       HSyncEnd, HTotal : 2208, 2560
(II) NVIDIA(0):       VRes, VSyncStart : 1392, 1393
(II) NVIDIA(0):       VSyncEnd, VTotal : 1396, 1500
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (112.5 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "928x696":
(II) NVIDIA(0):     928 x 696 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 144.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  928,  992
(II) NVIDIA(0):       HSyncEnd, HTotal : 1104, 1280
(II) NVIDIA(0):       VRes, VSyncStart :  696,  696
(II) NVIDIA(0):       VSyncEnd, VTotal :  698,  750
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (112.5 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1920x1440":
(II) NVIDIA(0):     1920 x 1440 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 234.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1920, 2048
(II) NVIDIA(0):       HSyncEnd, HTotal : 2256, 2600
(II) NVIDIA(0):       VRes, VSyncStart : 1440, 1441
(II) NVIDIA(0):       VSyncEnd, VTotal : 1444, 1500
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (90.0 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "960x720":
(II) NVIDIA(0):     960 x 720 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 117.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  960, 1024
(II) NVIDIA(0):       HSyncEnd, HTotal : 1128, 1300
(II) NVIDIA(0):       VRes, VSyncStart :  720,  720
(II) NVIDIA(0):       VSyncEnd, VTotal :  722,  750
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (90.0 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1920x1440":
(II) NVIDIA(0):     1920 x 1440 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 297.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1920, 2064
(II) NVIDIA(0):       HSyncEnd, HTotal : 2288, 2640
(II) NVIDIA(0):       VRes, VSyncStart : 1440, 1441
(II) NVIDIA(0):       VSyncEnd, VTotal : 1444, 1500
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (112.5 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "960x720":
(II) NVIDIA(0):     960 x 720 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 148.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  960, 1032
(II) NVIDIA(0):       HSyncEnd, HTotal : 1144, 1320
(II) NVIDIA(0):       VRes, VSyncStart :  720,  720
(II) NVIDIA(0):       VSyncEnd, VTotal :  722,  750
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (112.5 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "832x624":
(II) NVIDIA(0):     832 x 624 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 57.28 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  832,  864
(II) NVIDIA(0):       HSyncEnd, HTotal :  928, 1152
(II) NVIDIA(0):       VRes, VSyncStart :  624,  625
(II) NVIDIA(0):       VSyncEnd, VTotal :  628,  667
(II) NVIDIA(0):       H/V Polarity     : -/-
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (74.6 Hz) out of range
(WW) NVIDIA(0):     (43.000-72.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "416x312":
(II) NVIDIA(0):     416 x 312 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 28.64 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  416,  432
(II) NVIDIA(0):       HSyncEnd, HTotal :  464,  576
(II) NVIDIA(0):       VRes, VSyncStart :  312,  312
(II) NVIDIA(0):       VSyncEnd, VTotal :  314,  333
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (74.7 Hz) out of range
(WW) NVIDIA(0):     (43.000-72.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1152x864":
(II) NVIDIA(0):     1152 x 864 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 81.62 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1152, 1216
(II) NVIDIA(0):       HSyncEnd, HTotal : 1336, 1520
(II) NVIDIA(0):       VRes, VSyncStart :  864,  865
(II) NVIDIA(0):       VSyncEnd, VTotal :  868,  895
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):     Mode (1152 x 864) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1152x864" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "576x432":
(II) NVIDIA(0):     576 x 432 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 40.81 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  576,  608
(II) NVIDIA(0):       HSyncEnd, HTotal :  668,  760
(II) NVIDIA(0):       VRes, VSyncStart :  432,  432
(II) NVIDIA(0):       VSyncEnd, VTotal :  434,  447
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "576x432": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1152x864":
(II) NVIDIA(0):     1152 x 864 @ 70 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 96.77 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1152, 1224
(II) NVIDIA(0):       HSyncEnd, HTotal : 1344, 1536
(II) NVIDIA(0):       VRes, VSyncStart :  864,  865
(II) NVIDIA(0):       VSyncEnd, VTotal :  868,  900
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (63.0 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "576x432":
(II) NVIDIA(0):     576 x 432 @ 70 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 48.38 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  576,  612
(II) NVIDIA(0):       HSyncEnd, HTotal :  672,  768
(II) NVIDIA(0):       VRes, VSyncStart :  432,  432
(II) NVIDIA(0):       VSyncEnd, VTotal :  434,  450
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (63.0 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1152x864":
(II) NVIDIA(0):     1152 x 864 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 104.99 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1152, 1224
(II) NVIDIA(0):       HSyncEnd, HTotal : 1352, 1552
(II) NVIDIA(0):       VRes, VSyncStart :  864,  865
(II) NVIDIA(0):       VSyncEnd, VTotal :  868,  902
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (67.6 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "576x432":
(II) NVIDIA(0):     576 x 432 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 52.49 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  576,  612
(II) NVIDIA(0):       HSyncEnd, HTotal :  676,  776
(II) NVIDIA(0):       VRes, VSyncStart :  432,  432
(II) NVIDIA(0):       VSyncEnd, VTotal :  434,  451
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (67.6 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1152x864":
(II) NVIDIA(0):     1152 x 864 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 119.65 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1152, 1224
(II) NVIDIA(0):       HSyncEnd, HTotal : 1352, 1552
(II) NVIDIA(0):       VRes, VSyncStart :  864,  865
(II) NVIDIA(0):       VSyncEnd, VTotal :  868,  907
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (77.1 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "576x432":
(II) NVIDIA(0):     576 x 432 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 59.83 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  576,  612
(II) NVIDIA(0):       HSyncEnd, HTotal :  676,  776
(II) NVIDIA(0):       VRes, VSyncStart :  432,  432
(II) NVIDIA(0):       VSyncEnd, VTotal :  434,  453
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (77.1 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1152x864":
(II) NVIDIA(0):     1152 x 864 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 121.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1152, 1216
(II) NVIDIA(0):       HSyncEnd, HTotal : 1344, 1568
(II) NVIDIA(0):       VRes, VSyncStart :  864,  865
(II) NVIDIA(0):       VSyncEnd, VTotal :  868,  911
(II) NVIDIA(0):       H/V Polarity     : +/-
(WW) NVIDIA(0):     Mode is rejected: HorizSync (77.5 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "576x432":
(II) NVIDIA(0):     576 x 432 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 60.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  576,  608
(II) NVIDIA(0):       HSyncEnd, HTotal :  672,  784
(II) NVIDIA(0):       VRes, VSyncStart :  432,  432
(II) NVIDIA(0):       VSyncEnd, VTotal :  434,  455
(II) NVIDIA(0):       H/V Polarity     : +/-
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (77.5 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1152x864":
(II) NVIDIA(0):     1152 x 864 @ 100 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 143.47 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1152, 1232
(II) NVIDIA(0):       HSyncEnd, HTotal : 1360, 1568
(II) NVIDIA(0):       VRes, VSyncStart :  864,  865
(II) NVIDIA(0):       VSyncEnd, VTotal :  868,  915
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (91.5 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "576x432":
(II) NVIDIA(0):     576 x 432 @ 100 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 71.73 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  576,  616
(II) NVIDIA(0):       HSyncEnd, HTotal :  680,  784
(II) NVIDIA(0):       VRes, VSyncStart :  432,  432
(II) NVIDIA(0):       VSyncEnd, VTotal :  434,  457
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (91.5 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1360x768":
(II) NVIDIA(0):     1360 x 768 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 72.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1360, 1408
(II) NVIDIA(0):       HSyncEnd, HTotal : 1440, 1520
(II) NVIDIA(0):       VRes, VSyncStart :  768,  771
(II) NVIDIA(0):       VSyncEnd, VTotal :  781,  790
(II) NVIDIA(0):       H/V Polarity     : +/-
(II) NVIDIA(0):     Mode (1360 x 768) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1360x768" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "680x384":
(II) NVIDIA(0):     680 x 384 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 36.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  680,  704
(II) NVIDIA(0):       HSyncEnd, HTotal :  720,  760
(II) NVIDIA(0):       VRes, VSyncStart :  384,  385
(II) NVIDIA(0):       VSyncEnd, VTotal :  390,  395
(II) NVIDIA(0):       H/V Polarity     : +/-
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     Mode (680 x 384) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "680x384" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1360x768":
(II) NVIDIA(0):     1360 x 768 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 84.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1360, 1432
(II) NVIDIA(0):       HSyncEnd, HTotal : 1568, 1776
(II) NVIDIA(0):       VRes, VSyncStart :  768,  771
(II) NVIDIA(0):       VSyncEnd, VTotal :  781,  798
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):     Mode (1360 x 768) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1360x768" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "680x384":
(II) NVIDIA(0):     680 x 384 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 42.38 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  680,  716
(II) NVIDIA(0):       HSyncEnd, HTotal :  784,  888
(II) NVIDIA(0):       VRes, VSyncStart :  384,  385
(II) NVIDIA(0):       VSyncEnd, VTotal :  390,  399
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     Mode (680 x 384) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "680x384" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1400x1050":
(II) NVIDIA(0):     1400 x 1050 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 122.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1400, 1488
(II) NVIDIA(0):       HSyncEnd, HTotal : 1640, 1880
(II) NVIDIA(0):       VRes, VSyncStart : 1050, 1052
(II) NVIDIA(0):       VSyncEnd, VTotal : 1064, 1082
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (64.9 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "700x525":
(II) NVIDIA(0):     700 x 525 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 61.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  700,  744
(II) NVIDIA(0):       HSyncEnd, HTotal :  820,  940
(II) NVIDIA(0):       VRes, VSyncStart :  525,  526
(II) NVIDIA(0):       VSyncEnd, VTotal :  532,  541
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (64.9 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1400x1050":
(II) NVIDIA(0):     1400 x 1050 @ 70 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 145.06 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1400, 1496
(II) NVIDIA(0):       HSyncEnd, HTotal : 1648, 1896
(II) NVIDIA(0):       VRes, VSyncStart : 1050, 1051
(II) NVIDIA(0):       VSyncEnd, VTotal : 1054, 1093
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (76.5 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "700x525":
(II) NVIDIA(0):     700 x 525 @ 70 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 72.53 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  700,  748
(II) NVIDIA(0):       HSyncEnd, HTotal :  824,  948
(II) NVIDIA(0):       VRes, VSyncStart :  525,  525
(II) NVIDIA(0):       VSyncEnd, VTotal :  527,  546
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (76.5 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1400x1050":
(II) NVIDIA(0):     1400 x 1050 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 155.80 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1400, 1464
(II) NVIDIA(0):       HSyncEnd, HTotal : 1784, 1912
(II) NVIDIA(0):       VRes, VSyncStart : 1050, 1052
(II) NVIDIA(0):       VSyncEnd, VTotal : 1064, 1090
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (81.5 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "700x525":
(II) NVIDIA(0):     700 x 525 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 77.90 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  700,  732
(II) NVIDIA(0):       HSyncEnd, HTotal :  892,  956
(II) NVIDIA(0):       VRes, VSyncStart :  525,  526
(II) NVIDIA(0):       VSyncEnd, VTotal :  532,  545
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (81.5 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1400x1050":
(II) NVIDIA(0):     1400 x 1050 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 179.26 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1400, 1504
(II) NVIDIA(0):       HSyncEnd, HTotal : 1656, 1912
(II) NVIDIA(0):       VRes, VSyncStart : 1050, 1051
(II) NVIDIA(0):       VSyncEnd, VTotal : 1054, 1103
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (93.8 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "700x525":
(II) NVIDIA(0):     700 x 525 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 89.63 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  700,  752
(II) NVIDIA(0):       HSyncEnd, HTotal :  828,  956
(II) NVIDIA(0):       VRes, VSyncStart :  525,  525
(II) NVIDIA(0):       VSyncEnd, VTotal :  527,  551
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (93.8 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1440x900":
(II) NVIDIA(0):     1440 x 900 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 106.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1440, 1520
(II) NVIDIA(0):       HSyncEnd, HTotal : 1672, 1904
(II) NVIDIA(0):       VRes, VSyncStart :  900,  903
(II) NVIDIA(0):       VSyncEnd, VTotal :  909,  934
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (55.9 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "720x450":
(II) NVIDIA(0):     720 x 450 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 53.25 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  720,  760
(II) NVIDIA(0):       HSyncEnd, HTotal :  836,  952
(II) NVIDIA(0):       VRes, VSyncStart :  450,  451
(II) NVIDIA(0):       VSyncEnd, VTotal :  454,  467
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (55.9 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1024":
(II) NVIDIA(0):     1600 x 1024 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 103.12 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1600
(II) NVIDIA(0):       HSyncEnd, HTotal : 1656, 1664
(II) NVIDIA(0):       VRes, VSyncStart : 1024, 1024
(II) NVIDIA(0):       VSyncEnd, VTotal : 1029, 1030
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (62.0 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x512":
(II) NVIDIA(0):     800 x 512 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 51.56 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  800
(II) NVIDIA(0):       HSyncEnd, HTotal :  828,  832
(II) NVIDIA(0):       VRes, VSyncStart :  512,  512
(II) NVIDIA(0):       VSyncEnd, VTotal :  514,  515
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (62.0 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1680x1050":
(II) NVIDIA(0):     1680 x 1050 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 119.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1680, 1728
(II) NVIDIA(0):       HSyncEnd, HTotal : 1760, 1840
(II) NVIDIA(0):       VRes, VSyncStart : 1050, 1053
(II) NVIDIA(0):       VSyncEnd, VTotal : 1059, 1080
(II) NVIDIA(0):       H/V Polarity     : +/-
(WW) NVIDIA(0):     Mode is rejected: HorizSync (64.7 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "840x525":
(II) NVIDIA(0):     840 x 525 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 59.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  840,  864
(II) NVIDIA(0):       HSyncEnd, HTotal :  880,  920
(II) NVIDIA(0):       VRes, VSyncStart :  525,  526
(II) NVIDIA(0):       VSyncEnd, VTotal :  529,  540
(II) NVIDIA(0):       H/V Polarity     : +/-
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (64.7 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1680x1050":
(II) NVIDIA(0):     1680 x 1050 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 146.25 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1680, 1784
(II) NVIDIA(0):       HSyncEnd, HTotal : 1960, 2240
(II) NVIDIA(0):       VRes, VSyncStart : 1050, 1053
(II) NVIDIA(0):       VSyncEnd, VTotal : 1059, 1089
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (65.3 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "840x525":
(II) NVIDIA(0):     840 x 525 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 73.12 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  840,  892
(II) NVIDIA(0):       HSyncEnd, HTotal :  980, 1120
(II) NVIDIA(0):       VRes, VSyncStart :  525,  526
(II) NVIDIA(0):       VSyncEnd, VTotal :  529,  544
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (65.3 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1680x1050":
(II) NVIDIA(0):     1680 x 1050 @ 70 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 174.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1680, 1800
(II) NVIDIA(0):       HSyncEnd, HTotal : 1976, 2272
(II) NVIDIA(0):       VRes, VSyncStart : 1050, 1053
(II) NVIDIA(0):       VSyncEnd, VTotal : 1059, 1096
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (76.6 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "840x525":
(II) NVIDIA(0):     840 x 525 @ 70 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 87.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  840,  900
(II) NVIDIA(0):       HSyncEnd, HTotal :  988, 1136
(II) NVIDIA(0):       VRes, VSyncStart :  525,  526
(II) NVIDIA(0):       VSyncEnd, VTotal :  529,  548
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (76.6 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1680x1050":
(II) NVIDIA(0):     1680 x 1050 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 187.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1680, 1800
(II) NVIDIA(0):       HSyncEnd, HTotal : 1976, 2272
(II) NVIDIA(0):       VRes, VSyncStart : 1050, 1053
(II) NVIDIA(0):       VSyncEnd, VTotal : 1059, 1099
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (82.3 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "840x525":
(II) NVIDIA(0):     840 x 525 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 93.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  840,  900
(II) NVIDIA(0):       HSyncEnd, HTotal :  988, 1136
(II) NVIDIA(0):       VRes, VSyncStart :  525,  526
(II) NVIDIA(0):       VSyncEnd, VTotal :  529,  549
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (82.3 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1680x1050":
(II) NVIDIA(0):     1680 x 1050 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 214.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1680, 1808
(II) NVIDIA(0):       HSyncEnd, HTotal : 1984, 2288
(II) NVIDIA(0):       VRes, VSyncStart : 1050, 1053
(II) NVIDIA(0):       VSyncEnd, VTotal : 1059, 1105
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (93.9 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "840x525":
(II) NVIDIA(0):     840 x 525 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 107.38 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  840,  904
(II) NVIDIA(0):       HSyncEnd, HTotal :  992, 1144
(II) NVIDIA(0):       VRes, VSyncStart :  525,  526
(II) NVIDIA(0):       VSyncEnd, VTotal :  529,  552
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (93.9 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1920x1080":
(II) NVIDIA(0):     1920 x 1080 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 138.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1920, 1968
(II) NVIDIA(0):       HSyncEnd, HTotal : 2000, 2080
(II) NVIDIA(0):       VRes, VSyncStart : 1080, 1083
(II) NVIDIA(0):       VSyncEnd, VTotal : 1088, 1111
(II) NVIDIA(0):       H/V Polarity     : +/-
(WW) NVIDIA(0):     Mode is rejected: HorizSync (66.6 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "960x540":
(II) NVIDIA(0):     960 x 540 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 69.25 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  960,  984
(II) NVIDIA(0):       HSyncEnd, HTotal : 1000, 1040
(II) NVIDIA(0):       VRes, VSyncStart :  540,  541
(II) NVIDIA(0):       VSyncEnd, VTotal :  544,  555
(II) NVIDIA(0):       H/V Polarity     : +/-
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (66.6 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1920x1200":
(II) NVIDIA(0):     1920 x 1200 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 154.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1920, 1968
(II) NVIDIA(0):       HSyncEnd, HTotal : 2000, 2080
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1203
(II) NVIDIA(0):       VSyncEnd, VTotal : 1209, 1235
(II) NVIDIA(0):       H/V Polarity     : +/-
(WW) NVIDIA(0):     Mode is rejected: HorizSync (74.0 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "960x600":
(II) NVIDIA(0):     960 x 600 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 77.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  960,  984
(II) NVIDIA(0):       HSyncEnd, HTotal : 1000, 1040
(II) NVIDIA(0):       VRes, VSyncStart :  600,  601
(II) NVIDIA(0):       VSyncEnd, VTotal :  604,  617
(II) NVIDIA(0):       H/V Polarity     : +/-
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (74.0 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1920x1440":
(II) NVIDIA(0):     1920 x 1440 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 341.35 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1920, 2072
(II) NVIDIA(0):       HSyncEnd, HTotal : 2288, 2656
(II) NVIDIA(0):       VRes, VSyncStart : 1440, 1441
(II) NVIDIA(0):       VSyncEnd, VTotal : 1444, 1512
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (341.4 MHz) too high for
(WW) NVIDIA(0):     Display Device (Max: 330.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "960x720":
(II) NVIDIA(0):     960 x 720 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 170.68 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  960, 1036
(II) NVIDIA(0):       HSyncEnd, HTotal : 1144, 1328
(II) NVIDIA(0):       VRes, VSyncStart :  720,  720
(II) NVIDIA(0):       VSyncEnd, VTotal :  722,  756
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (128.5 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "2048x1536":
(II) NVIDIA(0):     2048 x 1536 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 266.95 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 2048, 2200
(II) NVIDIA(0):       HSyncEnd, HTotal : 2424, 2800
(II) NVIDIA(0):       VRes, VSyncStart : 1536, 1537
(II) NVIDIA(0):       VSyncEnd, VTotal : 1540, 1589
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (95.3 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 133.47 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1100
(II) NVIDIA(0):       HSyncEnd, HTotal : 1212, 1400
(II) NVIDIA(0):       VRes, VSyncStart :  768,  768
(II) NVIDIA(0):       VSyncEnd, VTotal :  770,  794
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (95.3 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "2048x1536":
(II) NVIDIA(0):     2048 x 1536 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 340.48 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 2048, 2216
(II) NVIDIA(0):       HSyncEnd, HTotal : 2440, 2832
(II) NVIDIA(0):       VRes, VSyncStart : 1536, 1537
(II) NVIDIA(0):       VSyncEnd, VTotal : 1540, 1603
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (340.5 MHz) too high for
(WW) NVIDIA(0):     Display Device (Max: 330.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 170.24 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1108
(II) NVIDIA(0):       HSyncEnd, HTotal : 1220, 1416
(II) NVIDIA(0):       VRes, VSyncStart :  768,  768
(II) NVIDIA(0):       VSyncEnd, VTotal :  770,  801
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (120.2 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "2048x1536":
(II) NVIDIA(0):     2048 x 1536 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 388.04 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 2048, 2216
(II) NVIDIA(0):       HSyncEnd, HTotal : 2440, 2832
(II) NVIDIA(0):       VRes, VSyncStart : 1536, 1537
(II) NVIDIA(0):       VSyncEnd, VTotal : 1540, 1612
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (388.0 MHz) too high for
(WW) NVIDIA(0):     Display Device (Max: 330.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 194.02 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1108
(II) NVIDIA(0):       HSyncEnd, HTotal : 1220, 1416
(II) NVIDIA(0):       VRes, VSyncStart :  768,  768
(II) NVIDIA(0):       VSyncEnd, VTotal :  770,  806
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (137.0 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x350":
(II) NVIDIA(0):     640 x 350 @ 85 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  672
(II) NVIDIA(0):       HSyncEnd, HTotal :  736,  832
(II) NVIDIA(0):       VRes, VSyncStart :  350,  382
(II) NVIDIA(0):       VSyncEnd, VTotal :  385,  445
(II) NVIDIA(0):       H/V Polarity     : +/-
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.1 Hz) out of range
(WW) NVIDIA(0):     (43.000-72.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x400":
(II) NVIDIA(0):     640 x 400 @ 85 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  672
(II) NVIDIA(0):       HSyncEnd, HTotal :  736,  832
(II) NVIDIA(0):       VRes, VSyncStart :  400,  401
(II) NVIDIA(0):       VSyncEnd, VTotal :  404,  445
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.1 Hz) out of range
(WW) NVIDIA(0):     (43.000-72.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "720x400":
(II) NVIDIA(0):     720 x 400 @ 85 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 35.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  720,  756
(II) NVIDIA(0):       HSyncEnd, HTotal :  828,  936
(II) NVIDIA(0):       VRes, VSyncStart :  400,  401
(II) NVIDIA(0):       VSyncEnd, VTotal :  404,  446
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.0 Hz) out of range
(WW) NVIDIA(0):     (43.000-72.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 60 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 25.18 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  656
(II) NVIDIA(0):       HSyncEnd, HTotal :  752,  800
(II) NVIDIA(0):       VRes, VSyncStart :  480,  490
(II) NVIDIA(0):       VSyncEnd, VTotal :  492,  525
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     BestFit Backend for "640x480": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 73 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  664
(II) NVIDIA(0):       HSyncEnd, HTotal :  704,  832
(II) NVIDIA(0):       VRes, VSyncStart :  480,  489
(II) NVIDIA(0):       VSyncEnd, VTotal :  492,  520
(II) NVIDIA(0):       H/V Polarity     : -/-
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (72.8 Hz) out of range
(WW) NVIDIA(0):     (43.000-72.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 75 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  656
(II) NVIDIA(0):       HSyncEnd, HTotal :  720,  840
(II) NVIDIA(0):       VRes, VSyncStart :  480,  481
(II) NVIDIA(0):       VSyncEnd, VTotal :  484,  500
(II) NVIDIA(0):       H/V Polarity     : -/-
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (75.0 Hz) out of range
(WW) NVIDIA(0):     (43.000-72.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 85 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 36.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  696
(II) NVIDIA(0):       HSyncEnd, HTotal :  752,  832
(II) NVIDIA(0):       VRes, VSyncStart :  480,  481
(II) NVIDIA(0):       VSyncEnd, VTotal :  484,  509
(II) NVIDIA(0):       H/V Polarity     : -/-
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.0 Hz) out of range
(WW) NVIDIA(0):     (43.000-72.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 56 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 36.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  824
(II) NVIDIA(0):       HSyncEnd, HTotal :  896, 1024
(II) NVIDIA(0):       VRes, VSyncStart :  600,  601
(II) NVIDIA(0):       VSyncEnd, VTotal :  603,  625
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode (800 x 600) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "800x600" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 60 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 40.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  840
(II) NVIDIA(0):       HSyncEnd, HTotal :  968, 1056
(II) NVIDIA(0):       VRes, VSyncStart :  600,  601
(II) NVIDIA(0):       VSyncEnd, VTotal :  605,  628
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode (800 x 600) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "800x600" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 72 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 50.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  856
(II) NVIDIA(0):       HSyncEnd, HTotal :  976, 1040
(II) NVIDIA(0):       VRes, VSyncStart :  600,  637
(II) NVIDIA(0):       VSyncEnd, VTotal :  643,  666
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode (800 x 600) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "800x600" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 75 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 49.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  816
(II) NVIDIA(0):       HSyncEnd, HTotal :  896, 1056
(II) NVIDIA(0):       VRes, VSyncStart :  600,  601
(II) NVIDIA(0):       VSyncEnd, VTotal :  604,  625
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (75.0 Hz) out of range
(WW) NVIDIA(0):     (43.000-72.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 85 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 56.30 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  832
(II) NVIDIA(0):       HSyncEnd, HTotal :  896, 1048
(II) NVIDIA(0):       VRes, VSyncStart :  600,  601
(II) NVIDIA(0):       VSyncEnd, VTotal :  604,  631
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.1 Hz) out of range
(WW) NVIDIA(0):     (43.000-72.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 87 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 44.90 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1032
(II) NVIDIA(0):       HSyncEnd, HTotal : 1208, 1264
(II) NVIDIA(0):       VRes, VSyncStart :  768,  768
(II) NVIDIA(0):       VSyncEnd, VTotal :  776,  817
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : Interlace
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (87.0 Hz) out of range
(WW) NVIDIA(0):     (43.000-72.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 60 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 65.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1048
(II) NVIDIA(0):       HSyncEnd, HTotal : 1184, 1344
(II) NVIDIA(0):       VRes, VSyncStart :  768,  771
(II) NVIDIA(0):       VSyncEnd, VTotal :  777,  806
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     Mode (1024 x 768) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1024x768" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 70 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 75.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1048
(II) NVIDIA(0):       HSyncEnd, HTotal : 1184, 1328
(II) NVIDIA(0):       VRes, VSyncStart :  768,  771
(II) NVIDIA(0):       VSyncEnd, VTotal :  777,  806
(II) NVIDIA(0):       H/V Polarity     : -/-
(WW) NVIDIA(0):     Mode is rejected: HorizSync (56.5 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 75 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 78.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1040
(II) NVIDIA(0):       HSyncEnd, HTotal : 1136, 1312
(II) NVIDIA(0):       VRes, VSyncStart :  768,  769
(II) NVIDIA(0):       VSyncEnd, VTotal :  772,  800
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (60.0 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 85 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 94.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1072
(II) NVIDIA(0):       HSyncEnd, HTotal : 1168, 1376
(II) NVIDIA(0):       VRes, VSyncStart :  768,  769
(II) NVIDIA(0):       VSyncEnd, VTotal :  772,  808
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (68.7 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1152x864":
(II) NVIDIA(0):     1152 x 864 @ 75 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 108.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1152, 1216
(II) NVIDIA(0):       HSyncEnd, HTotal : 1344, 1600
(II) NVIDIA(0):       VRes, VSyncStart :  864,  865
(II) NVIDIA(0):       VSyncEnd, VTotal :  868,  900
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (67.5 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x960":
(II) NVIDIA(0):     1280 x 960 @ 60 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 108.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1376
(II) NVIDIA(0):       HSyncEnd, HTotal : 1488, 1800
(II) NVIDIA(0):       VRes, VSyncStart :  960,  961
(II) NVIDIA(0):       VSyncEnd, VTotal :  964, 1000
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (60.0 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x960":
(II) NVIDIA(0):     1280 x 960 @ 85 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 148.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1344
(II) NVIDIA(0):       HSyncEnd, HTotal : 1504, 1728
(II) NVIDIA(0):       VRes, VSyncStart :  960,  961
(II) NVIDIA(0):       VSyncEnd, VTotal :  964, 1011
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (85.9 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x1024":
(II) NVIDIA(0):     1280 x 1024 @ 60 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 108.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1328
(II) NVIDIA(0):       HSyncEnd, HTotal : 1440, 1688
(II) NVIDIA(0):       VRes, VSyncStart : 1024, 1025
(II) NVIDIA(0):       VSyncEnd, VTotal : 1028, 1066
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (64.0 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x1024":
(II) NVIDIA(0):     1280 x 1024 @ 75 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 135.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1296
(II) NVIDIA(0):       HSyncEnd, HTotal : 1440, 1688
(II) NVIDIA(0):       VRes, VSyncStart : 1024, 1025
(II) NVIDIA(0):       VSyncEnd, VTotal : 1028, 1066
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (80.0 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x1024":
(II) NVIDIA(0):     1280 x 1024 @ 85 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 157.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1344
(II) NVIDIA(0):       HSyncEnd, HTotal : 1504, 1728
(II) NVIDIA(0):       VRes, VSyncStart : 1024, 1025
(II) NVIDIA(0):       VSyncEnd, VTotal : 1028, 1072
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (91.1 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1200":
(II) NVIDIA(0):     1600 x 1200 @ 60 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 162.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
(II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
(II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (75.0 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1200":
(II) NVIDIA(0):     1600 x 1200 @ 65 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 175.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
(II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
(II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (81.2 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1200":
(II) NVIDIA(0):     1600 x 1200 @ 70 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 189.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
(II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
(II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (87.5 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1200":
(II) NVIDIA(0):     1600 x 1200 @ 75 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 202.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
(II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
(II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (93.8 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1200":
(II) NVIDIA(0):     1600 x 1200 @ 85 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 229.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
(II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
(II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (106.2 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1792x1344":
(II) NVIDIA(0):     1792 x 1344 @ 60 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 204.80 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1792, 1920
(II) NVIDIA(0):       HSyncEnd, HTotal : 2120, 2448
(II) NVIDIA(0):       VRes, VSyncStart : 1344, 1345
(II) NVIDIA(0):       VSyncEnd, VTotal : 1348, 1394
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (83.7 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1792x1344":
(II) NVIDIA(0):     1792 x 1344 @ 75 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 261.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1792, 1888
(II) NVIDIA(0):       HSyncEnd, HTotal : 2104, 2456
(II) NVIDIA(0):       VRes, VSyncStart : 1344, 1345
(II) NVIDIA(0):       VSyncEnd, VTotal : 1348, 1417
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (106.3 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1856x1392":
(II) NVIDIA(0):     1856 x 1392 @ 60 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 218.30 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1856, 1952
(II) NVIDIA(0):       HSyncEnd, HTotal : 2176, 2528
(II) NVIDIA(0):       VRes, VSyncStart : 1392, 1393
(II) NVIDIA(0):       VSyncEnd, VTotal : 1396, 1439
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (86.4 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1856x1392":
(II) NVIDIA(0):     1856 x 1392 @ 75 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 288.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1856, 1984
(II) NVIDIA(0):       HSyncEnd, HTotal : 2208, 2560
(II) NVIDIA(0):       VRes, VSyncStart : 1392, 1393
(II) NVIDIA(0):       VSyncEnd, VTotal : 1396, 1500
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (112.5 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1920x1440":
(II) NVIDIA(0):     1920 x 1440 @ 60 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 234.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1920, 2048
(II) NVIDIA(0):       HSyncEnd, HTotal : 2256, 2600
(II) NVIDIA(0):       VRes, VSyncStart : 1440, 1441
(II) NVIDIA(0):       VSyncEnd, VTotal : 1444, 1500
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (90.0 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1920x1440":
(II) NVIDIA(0):     1920 x 1440 @ 75 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 297.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1920, 2064
(II) NVIDIA(0):       HSyncEnd, HTotal : 2288, 2640
(II) NVIDIA(0):       VRes, VSyncStart : 1440, 1441
(II) NVIDIA(0):       VSyncEnd, VTotal : 1444, 1500
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (112.5 kHz) out of range
(WW) NVIDIA(0):     (28.000-55.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0): --- Done building ModePool for DFP-0 ---
(II) NVIDIA(0): 
(II) NVIDIA(0): 
(II) NVIDIA(0): --- Modes in ModePool for DFP-0 ---
(II) NVIDIA(0): "nvidia-auto-select" :  640 x  480 @  59.9 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "640x480"            :  640 x  480 @  59.9 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "640x480_60"         :  640 x  480 @  59.9 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "576x432"            :  576 x  432 @  60.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "576x432d60"         :  576 x  432 @  60.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "512x384"            :  512 x  384 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "512x384d60"         :  512 x  384 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "400x300"            :  400 x  300 @  72.2 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "400x300d72"         :  400 x  300 @  72.2 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "400x300d60"         :  400 x  300 @  60.3 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "400x300d56"         :  400 x  300 @  56.3 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "320x240"            :  320 x  240 @  60.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "320x240d60"         :  320 x  240 @  60.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): --- End of ModePool for DFP-0: ---
(II) NVIDIA(0): 
(II) NVIDIA(0): Assigned Display Device: DFP-0
(==) NVIDIA(0): 
(==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) NVIDIA(0):     will be used as the requested mode.
(==) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0): Virtual screen size determined to be 640 x 480
(II) NVIDIA(0): 
(II) NVIDIA(0): Implicitly adding the following modes to X Screen 0 (these
(II) NVIDIA(0):     will be available via XRandR and XF86VidMode):
(II) NVIDIA(0): 
(II) NVIDIA(0): "576x432"    :  576 x  432 @  60.1 Hz DoubleScan 
(II) NVIDIA(0): "512x384"    :  512 x  384 @  60.0 Hz DoubleScan 
(II) NVIDIA(0): "400x300"    :  400 x  300 @  72.2 Hz DoubleScan 
(II) NVIDIA(0): "400x300d60" :  400 x  300 @  60.3 Hz DoubleScan 
(II) NVIDIA(0): "400x300d56" :  400 x  300 @  56.3 Hz DoubleScan 
(II) NVIDIA(0): "320x240"    :  320 x  240 @  60.1 Hz DoubleScan 
(II) NVIDIA(0): 
(WW) NVIDIA(0): Unable to get display device DFP-0's EDID; cannot compute DPI
(WW) NVIDIA(0):     from DFP-0's EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) NVIDIA(0): Built-in logo is bigger than the screen.
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing extension GLX
(II) config/hal: Adding input device Macintosh mouse button emulation
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) config/hal: Adding input device Microsoft Comfort Curve Keyboard 2000
(**) Microsoft Comfort Curve Keyboard 2000: always reports core events
(**) Microsoft Comfort Curve Keyboard 2000: Device: "/dev/input/event4"
(II) Microsoft Comfort Curve Keyboard 2000: Found keys
(II) Microsoft Comfort Curve Keyboard 2000: Configuring as keyboard
(II) XINPUT: Adding extended input device "Microsoft Comfort Curve Keyboard 2000" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Microsoft Comfort Curve Keyboard 2000: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Microsoft Comfort Curve Keyboard 2000: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Microsoft Comfort Curve Keyboard 2000: xkb_layout: "us"
(II) config/hal: Adding input device Microsoft Comfort Curve Keyboard 2000
(**) Microsoft Comfort Curve Keyboard 2000: always reports core events
(**) Microsoft Comfort Curve Keyboard 2000: Device: "/dev/input/event6"
(II) Microsoft Comfort Curve Keyboard 2000: Found 1 mouse buttons
(II) Microsoft Comfort Curve Keyboard 2000: Found keys
(II) Microsoft Comfort Curve Keyboard 2000: Configuring as keyboard
(**) Microsoft Comfort Curve Keyboard 2000: YAxisMapping: buttons 4 and 5
(**) Microsoft Comfort Curve Keyboard 2000: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Microsoft Comfort Curve Keyboard 2000" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Microsoft Comfort Curve Keyboard 2000: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Microsoft Comfort Curve Keyboard 2000: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Microsoft Comfort Curve Keyboard 2000: xkb_layout: "us"
(II) config/hal: Adding input device Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): always reports core events
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Device: "/dev/input/event7"
(II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found 3 mouse buttons
(II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found x and y relative axes
(II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Configuring as mouse
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): YAxisMapping: buttons 4 and 5
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)" (type: MOUSE)
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): (accel) keeping acceleration scheme 1
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): (accel) filter chain progression: 2.00
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): (accel) filter stage 0: 20.00 ms
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): (accel) set acceleration profile 0
```

---

### Post by CatKiller on 2009-09-02
> **tsali said:**
> 
```

(--) NVIDIA(0): --- EDID for DFP-0 ---
(--) NVIDIA(0): 
(--) NVIDIA(0): No EDID Available.
(--) NVIDIA(0): 
(--) NVIDIA(0): --- End of EDID for DFP-0 ---
(--) NVIDIA(0): 
 (II) NVIDIA(0): Frequency information for DFP-0:
(II) NVIDIA(0):   HorizSync   : 28.000-55.000 kHz
(II) NVIDIA(0):   VertRefresh : 43.000-72.000 Hz
(II) NVIDIA(0):     (HorizSync from Conservative Defaults)
(II) NVIDIA(0):     (VertRefresh from Conservative Defaults)

```

So what does it say when you've specified the HorizSync & VertRefresh values yourself?

If you've got the out-of-range error message on your monitor, Ctrl-Alt-F1 should still get you a command line. You can grab the log and stick a copy on your Desktop from there with ```
cat /var/log/Xorg.0.log > ~/Desktop/xorg.log.manual
``` Then you can undo your changes to xorg.conf to get your graphical environment back to look at it and/or post it here.

There are several Sceptre products listed as having a model number with X20 in. Some of them have different maximum resolutions, so it's worth checking for your actual monitor there so that you know what mode it is that you're trying to get X to pick.

---

### Post by P4man on 2009-09-02
all those failed modes tried running your monitor at 85Hz. You should specify a maximum  VertRefresh of 75 for your monitor, as Catkiller suggested earlier.

---

### Post by tsali on 2009-09-04
> **CatKiller said:**
> So what does it say when you've specified the HorizSync & VertRefresh values yourself?

If you've got the out-of-range error message on your monitor, Ctrl-Alt-F1 should still get you a command line. You can grab the log and stick a copy on your Desktop from there with ```
cat /var/log/Xorg.0.log > ~/Desktop/xorg.log.manual
``` Then you can undo your changes to xorg.conf to get your graphical environment back to look at it and/or post it here.

There are several Sceptre products listed as having a model number with X20 in. Some of them have different maximum resolutions, so it's worth checking for your actual monitor there so that you know what mode it is that you're trying to get X to pick.

Mine is the X20G Naga III 1080i/1080p capable of 1680 x 1050

I get exactly that in Vista.

I tried what you suggested immediately after the last post and it was showing that it had rejected EVERY mode...bizarre, eh?

---

### Post by CatKiller on 2009-09-04
> **tsali said:**
>  I tried what you suggested immediately after the last post

Which bit? Just copying the log won't help, because we've already seen that one. What we need to know is which mode X is choosing when your monitor displays "out of range;" when you've put in the refresh rates manually, and told X to ignore the EDID values.

According to the [specifications]("http://www.sceptre.com/Products/LCD/Specifications/spec_x20g_NagaIII.htm") for that monitor you want ```
        HorizSync       24-82
        VertRefresh     50-75
``` in the Monitor section as well as ```
        Option          "UseEDID"                       "False"
``` in the Device section, although I'm not sure that the 3kHz at the bottom end will make that much difference.

Once we know the problem with those values, we can adjust the settings further; specifying the Clock rate, for example, or giving it a preferred mode. But until we know what the problem is, we can't fix it.

---

### Post by tsali on 2009-09-04
Ok, I'm using the DVI port, so I tried both the analog and digital timings. Both result in an "out of range" displayed.

This is the first log with 24-82:

```

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux ubuntu-desktop 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Sep  4 13:39:06 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@1:0:0) nVidia Corporation G70 [GeForce 7300 GT] rev 161, Mem @ 0xfa000000/16777216, 0xd0000000/268435456, 0xfb000000/16777216, I/O @ 0x0000cf00/128, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(WW) "dri2" will not be loaded unless you've specified it to be loaded elsewhere.
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded even though the default is to disable it.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  180.44  Mon Mar 23 15:29:02 PST 2009
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  180.44  Mon Mar 23 15:05:32 PST 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "UseEDID" "False"
(**) NVIDIA(0): Option "ModeDebug" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): Ignoring EDIDs
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(GPU-0): Not probing EDID on DFP-0.
(II) NVIDIA(0): NVIDIA GPU GeForce 7300 GT (G73) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.73.22.40.00
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7300 GT at PCI:1:0:0:
(--) NVIDIA(0):     DFP-0
(--) NVIDIA(0): DFP-0: 330.0 MHz maximum pixel clock
(--) NVIDIA(0): DFP-0: Internal Dual Link TMDS
(--) NVIDIA(0): 
(--) NVIDIA(0): --- EDID for DFP-0 ---
(--) NVIDIA(0): 
(--) NVIDIA(0): No EDID Available.
(--) NVIDIA(0): 
(--) NVIDIA(0): --- End of EDID for DFP-0 ---
(--) NVIDIA(0): 
(II) NVIDIA(0): Frequency information for DFP-0:
(II) NVIDIA(0):   HorizSync   : 24.000-82.000 kHz
(II) NVIDIA(0):   VertRefresh : 50.000-75.000 Hz
(II) NVIDIA(0):     (HorizSync from HorizSync in X Config Monitor section)
(II) NVIDIA(0):     (VertRefresh from VertRefresh in X Config Monitor
(II) NVIDIA(0):     section)
(II) NVIDIA(0): 
(II) NVIDIA(0): --- Building ModePool for DFP-0 ---
(II) NVIDIA(0): 
(II) NVIDIA(0): Native backend timings for DFP-0:
(II) NVIDIA(0):   640 x 480 @ 60 Hz
(II) NVIDIA(0):     Pixel Clock      : 25.175 MHz
(II) NVIDIA(0):     HRes, HSyncStart :  640,  656
(II) NVIDIA(0):     HSyncEnd, HTotal :  752,  800
(II) NVIDIA(0):     VRes, VSyncStart :  480,  490
(II) NVIDIA(0):     VSyncEnd, VTotal :  492,  525
(II) NVIDIA(0):     H/V Polarity     : -/-
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x350":
(II) NVIDIA(0):     640 x 350 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  672
(II) NVIDIA(0):       HSyncEnd, HTotal :  736,  832
(II) NVIDIA(0):       VRes, VSyncStart :  350,  382
(II) NVIDIA(0):       VSyncEnd, VTotal :  385,  445
(II) NVIDIA(0):       H/V Polarity     : +/-
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.1 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "320x175":
(II) NVIDIA(0):     320 x 175 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 15.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  320,  336
(II) NVIDIA(0):       HSyncEnd, HTotal :  368,  416
(II) NVIDIA(0):       VRes, VSyncStart :  175,  191
(II) NVIDIA(0):       VSyncEnd, VTotal :  192,  222
(II) NVIDIA(0):       H/V Polarity     : +/-
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.3 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x400":
(II) NVIDIA(0):     640 x 400 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  672
(II) NVIDIA(0):       HSyncEnd, HTotal :  736,  832
(II) NVIDIA(0):       VRes, VSyncStart :  400,  401
(II) NVIDIA(0):       VSyncEnd, VTotal :  404,  445
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.1 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "320x200":
(II) NVIDIA(0):     320 x 200 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 15.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  320,  336
(II) NVIDIA(0):       HSyncEnd, HTotal :  368,  416
(II) NVIDIA(0):       VRes, VSyncStart :  200,  200
(II) NVIDIA(0):       VSyncEnd, VTotal :  202,  222
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.3 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "720x400":
(II) NVIDIA(0):     720 x 400 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 35.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  720,  756
(II) NVIDIA(0):       HSyncEnd, HTotal :  828,  936
(II) NVIDIA(0):       VRes, VSyncStart :  400,  401
(II) NVIDIA(0):       VSyncEnd, VTotal :  404,  446
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.0 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "360x200":
(II) NVIDIA(0):     360 x 200 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 17.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  360,  378
(II) NVIDIA(0):       HSyncEnd, HTotal :  414,  468
(II) NVIDIA(0):       VRes, VSyncStart :  200,  200
(II) NVIDIA(0):       VSyncEnd, VTotal :  202,  223
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.0 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 25.18 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  656
(II) NVIDIA(0):       HSyncEnd, HTotal :  752,  800
(II) NVIDIA(0):       VRes, VSyncStart :  480,  490
(II) NVIDIA(0):       VSyncEnd, VTotal :  492,  525
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     BestFit Backend for "640x480": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "320x240":
(II) NVIDIA(0):     320 x 240 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 12.59 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  320,  328
(II) NVIDIA(0):       HSyncEnd, HTotal :  376,  400
(II) NVIDIA(0):       VRes, VSyncStart :  240,  245
(II) NVIDIA(0):       VSyncEnd, VTotal :  246,  262
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "320x240": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 73 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  664
(II) NVIDIA(0):       HSyncEnd, HTotal :  704,  832
(II) NVIDIA(0):       VRes, VSyncStart :  480,  489
(II) NVIDIA(0):       VSyncEnd, VTotal :  492,  520
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     BestFit Backend for "640x480": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "320x240":
(II) NVIDIA(0):     320 x 240 @ 73 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 15.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  320,  332
(II) NVIDIA(0):       HSyncEnd, HTotal :  352,  416
(II) NVIDIA(0):       VRes, VSyncStart :  240,  244
(II) NVIDIA(0):       VSyncEnd, VTotal :  246,  260
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "320x240": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  656
(II) NVIDIA(0):       HSyncEnd, HTotal :  720,  840
(II) NVIDIA(0):       VRes, VSyncStart :  480,  481
(II) NVIDIA(0):       VSyncEnd, VTotal :  484,  500
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     BestFit Backend for "640x480": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "320x240":
(II) NVIDIA(0):     320 x 240 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 15.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  320,  328
(II) NVIDIA(0):       HSyncEnd, HTotal :  360,  420
(II) NVIDIA(0):       VRes, VSyncStart :  240,  240
(II) NVIDIA(0):       VSyncEnd, VTotal :  242,  250
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "320x240": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 36.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  696
(II) NVIDIA(0):       HSyncEnd, HTotal :  752,  832
(II) NVIDIA(0):       VRes, VSyncStart :  480,  481
(II) NVIDIA(0):       VSyncEnd, VTotal :  484,  509
(II) NVIDIA(0):       H/V Polarity     : -/-
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.0 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "320x240":
(II) NVIDIA(0):     320 x 240 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 18.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  320,  348
(II) NVIDIA(0):       HSyncEnd, HTotal :  376,  416
(II) NVIDIA(0):       VRes, VSyncStart :  240,  240
(II) NVIDIA(0):       VSyncEnd, VTotal :  242,  254
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.2 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 56 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 36.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  824
(II) NVIDIA(0):       HSyncEnd, HTotal :  896, 1024
(II) NVIDIA(0):       VRes, VSyncStart :  600,  601
(II) NVIDIA(0):       VSyncEnd, VTotal :  603,  625
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode (800 x 600) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "800x600" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "400x300":
(II) NVIDIA(0):     400 x 300 @ 56 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 18.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  400,  412
(II) NVIDIA(0):       HSyncEnd, HTotal :  448,  512
(II) NVIDIA(0):       VRes, VSyncStart :  300,  300
(II) NVIDIA(0):       VSyncEnd, VTotal :  301,  312
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "400x300": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 40.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  840
(II) NVIDIA(0):       HSyncEnd, HTotal :  968, 1056
(II) NVIDIA(0):       VRes, VSyncStart :  600,  601
(II) NVIDIA(0):       VSyncEnd, VTotal :  605,  628
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode (800 x 600) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "800x600" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "400x300":
(II) NVIDIA(0):     400 x 300 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 20.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  400,  420
(II) NVIDIA(0):       HSyncEnd, HTotal :  484,  528
(II) NVIDIA(0):       VRes, VSyncStart :  300,  300
(II) NVIDIA(0):       VSyncEnd, VTotal :  302,  314
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "400x300": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 72 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 50.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  856
(II) NVIDIA(0):       HSyncEnd, HTotal :  976, 1040
(II) NVIDIA(0):       VRes, VSyncStart :  600,  637
(II) NVIDIA(0):       VSyncEnd, VTotal :  643,  666
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode (800 x 600) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "800x600" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "400x300":
(II) NVIDIA(0):     400 x 300 @ 72 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 25.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  400,  428
(II) NVIDIA(0):       HSyncEnd, HTotal :  488,  520
(II) NVIDIA(0):       VRes, VSyncStart :  300,  318
(II) NVIDIA(0):       VSyncEnd, VTotal :  321,  333
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "400x300": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 49.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  816
(II) NVIDIA(0):       HSyncEnd, HTotal :  896, 1056
(II) NVIDIA(0):       VRes, VSyncStart :  600,  601
(II) NVIDIA(0):       VSyncEnd, VTotal :  604,  625
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode (800 x 600) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "800x600" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "400x300":
(II) NVIDIA(0):     400 x 300 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 24.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  400,  408
(II) NVIDIA(0):       HSyncEnd, HTotal :  448,  528
(II) NVIDIA(0):       VRes, VSyncStart :  300,  300
(II) NVIDIA(0):       VSyncEnd, VTotal :  302,  312
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "400x300": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 56.30 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  832
(II) NVIDIA(0):       HSyncEnd, HTotal :  896, 1048
(II) NVIDIA(0):       VRes, VSyncStart :  600,  601
(II) NVIDIA(0):       VSyncEnd, VTotal :  604,  631
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.1 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "400x300":
(II) NVIDIA(0):     400 x 300 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 28.15 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  400,  416
(II) NVIDIA(0):       HSyncEnd, HTotal :  448,  524
(II) NVIDIA(0):       VRes, VSyncStart :  300,  300
(II) NVIDIA(0):       VSyncEnd, VTotal :  302,  315
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.3 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 87 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 44.90 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1032
(II) NVIDIA(0):       HSyncEnd, HTotal : 1208, 1264
(II) NVIDIA(0):       VRes, VSyncStart :  768,  768
(II) NVIDIA(0):       VSyncEnd, VTotal :  776,  817
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : Interlace
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (87.0 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "512x384":
(II) NVIDIA(0):     512 x 384 @ 87 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 22.45 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  512,  516
(II) NVIDIA(0):       HSyncEnd, HTotal :  604,  632
(II) NVIDIA(0):       VRes, VSyncStart :  384,  384
(II) NVIDIA(0):       VSyncEnd, VTotal :  388,  408
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : Interlace DoubleScan
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (87.1 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 65.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1048
(II) NVIDIA(0):       HSyncEnd, HTotal : 1184, 1344
(II) NVIDIA(0):       VRes, VSyncStart :  768,  771
(II) NVIDIA(0):       VSyncEnd, VTotal :  777,  806
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     Mode (1024 x 768) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1024x768" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "512x384":
(II) NVIDIA(0):     512 x 384 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 32.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  512,  524
(II) NVIDIA(0):       HSyncEnd, HTotal :  592,  672
(II) NVIDIA(0):       VRes, VSyncStart :  384,  385
(II) NVIDIA(0):       VSyncEnd, VTotal :  388,  403
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "512x384": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 70 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 75.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1048
(II) NVIDIA(0):       HSyncEnd, HTotal : 1184, 1328
(II) NVIDIA(0):       VRes, VSyncStart :  768,  771
(II) NVIDIA(0):       VSyncEnd, VTotal :  777,  806
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     Mode (1024 x 768) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1024x768" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "512x384":
(II) NVIDIA(0):     512 x 384 @ 70 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 37.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  512,  524
(II) NVIDIA(0):       HSyncEnd, HTotal :  592,  664
(II) NVIDIA(0):       VRes, VSyncStart :  384,  385
(II) NVIDIA(0):       VSyncEnd, VTotal :  388,  403
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "512x384": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 78.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1040
(II) NVIDIA(0):       HSyncEnd, HTotal : 1136, 1312
(II) NVIDIA(0):       VRes, VSyncStart :  768,  769
(II) NVIDIA(0):       VSyncEnd, VTotal :  772,  800
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode (1024 x 768) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1024x768" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "512x384":
(II) NVIDIA(0):     512 x 384 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 39.38 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  512,  520
(II) NVIDIA(0):       HSyncEnd, HTotal :  568,  656
(II) NVIDIA(0):       VRes, VSyncStart :  384,  384
(II) NVIDIA(0):       VSyncEnd, VTotal :  386,  400
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "512x384": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 94.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1072
(II) NVIDIA(0):       HSyncEnd, HTotal : 1168, 1376
(II) NVIDIA(0):       VRes, VSyncStart :  768,  769
(II) NVIDIA(0):       VSyncEnd, VTotal :  772,  808
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.0 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "512x384":
(II) NVIDIA(0):     512 x 384 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 47.25 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  512,  536
(II) NVIDIA(0):       HSyncEnd, HTotal :  584,  688
(II) NVIDIA(0):       VRes, VSyncStart :  384,  384
(II) NVIDIA(0):       VSyncEnd, VTotal :  386,  404
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.0 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1152x864":
(II) NVIDIA(0):     1152 x 864 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 108.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1152, 1216
(II) NVIDIA(0):       HSyncEnd, HTotal : 1344, 1600
(II) NVIDIA(0):       VRes, VSyncStart :  864,  865
(II) NVIDIA(0):       VSyncEnd, VTotal :  868,  900
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode (1152 x 864) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1152x864" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "576x432":
(II) NVIDIA(0):     576 x 432 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 54.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  576,  608
(II) NVIDIA(0):       HSyncEnd, HTotal :  672,  800
(II) NVIDIA(0):       VRes, VSyncStart :  432,  432
(II) NVIDIA(0):       VSyncEnd, VTotal :  434,  450
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "576x432": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x960":
(II) NVIDIA(0):     1280 x 960 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 108.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1376
(II) NVIDIA(0):       HSyncEnd, HTotal : 1488, 1800
(II) NVIDIA(0):       VRes, VSyncStart :  960,  961
(II) NVIDIA(0):       VSyncEnd, VTotal :  964, 1000
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode (1280 x 960) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1280x960" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 54.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  688
(II) NVIDIA(0):       HSyncEnd, HTotal :  744,  900
(II) NVIDIA(0):       VRes, VSyncStart :  480,  480
(II) NVIDIA(0):       VSyncEnd, VTotal :  482,  500
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "640x480": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x960":
(II) NVIDIA(0):     1280 x 960 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 148.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1344
(II) NVIDIA(0):       HSyncEnd, HTotal : 1504, 1728
(II) NVIDIA(0):       VRes, VSyncStart :  960,  961
(II) NVIDIA(0):       VSyncEnd, VTotal :  964, 1011
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (85.9 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 74.25 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  672
(II) NVIDIA(0):       HSyncEnd, HTotal :  752,  864
(II) NVIDIA(0):       VRes, VSyncStart :  480,  480
(II) NVIDIA(0):       VSyncEnd, VTotal :  482,  505
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (85.9 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x1024":
(II) NVIDIA(0):     1280 x 1024 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 108.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1328
(II) NVIDIA(0):       HSyncEnd, HTotal : 1440, 1688
(II) NVIDIA(0):       VRes, VSyncStart : 1024, 1025
(II) NVIDIA(0):       VSyncEnd, VTotal : 1028, 1066
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode (1280 x 1024) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1280x1024" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x512":
(II) NVIDIA(0):     640 x 512 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 54.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  664
(II) NVIDIA(0):       HSyncEnd, HTotal :  720,  844
(II) NVIDIA(0):       VRes, VSyncStart :  512,  512
(II) NVIDIA(0):       VSyncEnd, VTotal :  514,  533
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     Mode (640 x 512) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "640x512" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x1024":
(II) NVIDIA(0):     1280 x 1024 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 135.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1296
(II) NVIDIA(0):       HSyncEnd, HTotal : 1440, 1688
(II) NVIDIA(0):       VRes, VSyncStart : 1024, 1025
(II) NVIDIA(0):       VSyncEnd, VTotal : 1028, 1066
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode (1280 x 1024) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1280x1024" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x512":
(II) NVIDIA(0):     640 x 512 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 67.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  648
(II) NVIDIA(0):       HSyncEnd, HTotal :  720,  844
(II) NVIDIA(0):       VRes, VSyncStart :  512,  512
(II) NVIDIA(0):       VSyncEnd, VTotal :  514,  533
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     Mode (640 x 512) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "640x512" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x1024":
(II) NVIDIA(0):     1280 x 1024 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 157.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1344
(II) NVIDIA(0):       HSyncEnd, HTotal : 1504, 1728
(II) NVIDIA(0):       VRes, VSyncStart : 1024, 1025
(II) NVIDIA(0):       VSyncEnd, VTotal : 1028, 1072
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (91.1 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x512":
(II) NVIDIA(0):     640 x 512 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 78.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  672
(II) NVIDIA(0):       HSyncEnd, HTotal :  752,  864
(II) NVIDIA(0):       VRes, VSyncStart :  512,  512
(II) NVIDIA(0):       VSyncEnd, VTotal :  514,  536
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (91.1 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1200":
(II) NVIDIA(0):     1600 x 1200 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 162.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
(II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
(II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode (1600 x 1200) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1600x1200" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 81.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  832
(II) NVIDIA(0):       HSyncEnd, HTotal :  928, 1080
(II) NVIDIA(0):       VRes, VSyncStart :  600,  600
(II) NVIDIA(0):       VSyncEnd, VTotal :  602,  625
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     Mode (800 x 600) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "800x600" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1200":
(II) NVIDIA(0):     1600 x 1200 @ 65 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 175.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
(II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
(II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode (1600 x 1200) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1600x1200" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 65 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 87.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  832
(II) NVIDIA(0):       HSyncEnd, HTotal :  928, 1080
(II) NVIDIA(0):       VRes, VSyncStart :  600,  600
(II) NVIDIA(0):       VSyncEnd, VTotal :  602,  625
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     Mode (800 x 600) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "800x600" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1200":
(II) NVIDIA(0):     1600 x 1200 @ 70 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 189.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
(II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
(II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (87.5 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 70 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 94.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  832
(II) NVIDIA(0):       HSyncEnd, HTotal :  928, 1080
(II) NVIDIA(0):       VRes, VSyncStart :  600,  600
(II) NVIDIA(0):       VSyncEnd, VTotal :  602,  625
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (87.5 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1200":
(II) NVIDIA(0):     1600 x 1200 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 202.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
(II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
(II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (93.8 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 101.25 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  832
(II) NVIDIA(0):       HSyncEnd, HTotal :  928, 1080
(II) NVIDIA(0):       VRes, VSyncStart :  600,  600
(II) NVIDIA(0):       VSyncEnd, VTotal :  602,  625
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (93.8 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1200":
(II) NVIDIA(0):     1600 x 1200 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 229.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
(II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
(II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (106.2 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 114.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  832
(II) NVIDIA(0):       HSyncEnd, HTotal :  928, 1080
(II) NVIDIA(0):       VRes, VSyncStart :  600,  600
(II) NVIDIA(0):       VSyncEnd, VTotal :  602,  625
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (106.2 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1792x1344":
(II) NVIDIA(0):     1792 x 1344 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 204.80 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1792, 1920
(II) NVIDIA(0):       HSyncEnd, HTotal : 2120, 2448
(II) NVIDIA(0):       VRes, VSyncStart : 1344, 1345
(II) NVIDIA(0):       VSyncEnd, VTotal : 1348, 1394
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (83.7 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "896x672":
(II) NVIDIA(0):     896 x 672 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 102.40 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  896,  960
(II) NVIDIA(0):       HSyncEnd, HTotal : 1060, 1224
(II) NVIDIA(0):       VRes, VSyncStart :  672,  672
(II) NVIDIA(0):       VSyncEnd, VTotal :  674,  697
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (83.7 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1792x1344":
(II) NVIDIA(0):     1792 x 1344 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 261.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1792, 1888
(II) NVIDIA(0):       HSyncEnd, HTotal : 2104, 2456
(II) NVIDIA(0):       VRes, VSyncStart : 1344, 1345
(II) NVIDIA(0):       VSyncEnd, VTotal : 1348, 1417
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (106.3 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "896x672":
(II) NVIDIA(0):     896 x 672 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 130.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  896,  944
(II) NVIDIA(0):       HSyncEnd, HTotal : 1052, 1228
(II) NVIDIA(0):       VRes, VSyncStart :  672,  672
(II) NVIDIA(0):       VSyncEnd, VTotal :  674,  708
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (106.3 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1856x1392":
(II) NVIDIA(0):     1856 x 1392 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 218.30 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1856, 1952
(II) NVIDIA(0):       HSyncEnd, HTotal : 2176, 2528
(II) NVIDIA(0):       VRes, VSyncStart : 1392, 1393
(II) NVIDIA(0):       VSyncEnd, VTotal : 1396, 1439
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (86.4 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "928x696":
(II) NVIDIA(0):     928 x 696 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 109.15 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  928,  976
(II) NVIDIA(0):       HSyncEnd, HTotal : 1088, 1264
(II) NVIDIA(0):       VRes, VSyncStart :  696,  696
(II) NVIDIA(0):       VSyncEnd, VTotal :  698,  719
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (86.4 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1856x1392":
(II) NVIDIA(0):     1856 x 1392 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 288.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1856, 1984
(II) NVIDIA(0):       HSyncEnd, HTotal : 2208, 2560
(II) NVIDIA(0):       VRes, VSyncStart : 1392, 1393
(II) NVIDIA(0):       VSyncEnd, VTotal : 1396, 1500
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (112.5 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "928x696":
(II) NVIDIA(0):     928 x 696 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 144.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  928,  992
(II) NVIDIA(0):       HSyncEnd, HTotal : 1104, 1280
(II) NVIDIA(0):       VRes, VSyncStart :  696,  696
(II) NVIDIA(0):       VSyncEnd, VTotal :  698,  750
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (112.5 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1920x1440":
(II) NVIDIA(0):     1920 x 1440 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 234.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1920, 2048
(II) NVIDIA(0):       HSyncEnd, HTotal : 2256, 2600
(II) NVIDIA(0):       VRes, VSyncStart : 1440, 1441
(II) NVIDIA(0):       VSyncEnd, VTotal : 1444, 1500
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (90.0 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "960x720":
(II) NVIDIA(0):     960 x 720 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 117.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  960, 1024
(II) NVIDIA(0):       HSyncEnd, HTotal : 1128, 1300
(II) NVIDIA(0):       VRes, VSyncStart :  720,  720
(II) NVIDIA(0):       VSyncEnd, VTotal :  722,  750
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (90.0 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1920x1440":
(II) NVIDIA(0):     1920 x 1440 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 297.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1920, 2064
(II) NVIDIA(0):       HSyncEnd, HTotal : 2288, 2640
(II) NVIDIA(0):       VRes, VSyncStart : 1440, 1441
(II) NVIDIA(0):       VSyncEnd, VTotal : 1444, 1500
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (112.5 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "960x720":
(II) NVIDIA(0):     960 x 720 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 148.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  960, 1032
(II) NVIDIA(0):       HSyncEnd, HTotal : 1144, 1320
(II) NVIDIA(0):       VRes, VSyncStart :  720,  720
(II) NVIDIA(0):       VSyncEnd, VTotal :  722,  750
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (112.5 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "832x624":
(II) NVIDIA(0):     832 x 624 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 57.28 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  832,  864
(II) NVIDIA(0):       HSyncEnd, HTotal :  928, 1152
(II) NVIDIA(0):       VRes, VSyncStart :  624,  625
(II) NVIDIA(0):       VSyncEnd, VTotal :  628,  667
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     Mode (832 x 624) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "832x624" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "416x312":
(II) NVIDIA(0):     416 x 312 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 28.64 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  416,  432
(II) NVIDIA(0):       HSyncEnd, HTotal :  464,  576
(II) NVIDIA(0):       VRes, VSyncStart :  312,  312
(II) NVIDIA(0):       VSyncEnd, VTotal :  314,  333
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "416x312": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1152x864":
(II) NVIDIA(0):     1152 x 864 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 81.62 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1152, 1216
(II) NVIDIA(0):       HSyncEnd, HTotal : 1336, 1520
(II) NVIDIA(0):       VRes, VSyncStart :  864,  865
(II) NVIDIA(0):       VSyncEnd, VTotal :  868,  895
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):     Mode (1152 x 864) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1152x864" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "576x432":
(II) NVIDIA(0):     576 x 432 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 40.81 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  576,  608
(II) NVIDIA(0):       HSyncEnd, HTotal :  668,  760
(II) NVIDIA(0):       VRes, VSyncStart :  432,  432
(II) NVIDIA(0):       VSyncEnd, VTotal :  434,  447
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "576x432": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1152x864":
(II) NVIDIA(0):     1152 x 864 @ 70 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 96.77 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1152, 1224
(II) NVIDIA(0):       HSyncEnd, HTotal : 1344, 1536
(II) NVIDIA(0):       VRes, VSyncStart :  864,  865
(II) NVIDIA(0):       VSyncEnd, VTotal :  868,  900
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):     Mode (1152 x 864) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1152x864" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "576x432":
(II) NVIDIA(0):     576 x 432 @ 70 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 48.38 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  576,  612
(II) NVIDIA(0):       HSyncEnd, HTotal :  672,  768
(II) NVIDIA(0):       VRes, VSyncStart :  432,  432
(II) NVIDIA(0):       VSyncEnd, VTotal :  434,  450
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "576x432": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1152x864":
(II) NVIDIA(0):     1152 x 864 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 104.99 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1152, 1224
(II) NVIDIA(0):       HSyncEnd, HTotal : 1352, 1552
(II) NVIDIA(0):       VRes, VSyncStart :  864,  865
(II) NVIDIA(0):       VSyncEnd, VTotal :  868,  902
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):     Mode (1152 x 864) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1152x864" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "576x432":
(II) NVIDIA(0):     576 x 432 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 52.49 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  576,  612
(II) NVIDIA(0):       HSyncEnd, HTotal :  676,  776
(II) NVIDIA(0):       VRes, VSyncStart :  432,  432
(II) NVIDIA(0):       VSyncEnd, VTotal :  434,  451
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "576x432": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1152x864":
(II) NVIDIA(0):     1152 x 864 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 119.65 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1152, 1224
(II) NVIDIA(0):       HSyncEnd, HTotal : 1352, 1552
(II) NVIDIA(0):       VRes, VSyncStart :  864,  865
(II) NVIDIA(0):       VSyncEnd, VTotal :  868,  907
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.0 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "576x432":
(II) NVIDIA(0):     576 x 432 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 59.83 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  576,  612
(II) NVIDIA(0):       HSyncEnd, HTotal :  676,  776
(II) NVIDIA(0):       VRes, VSyncStart :  432,  432
(II) NVIDIA(0):       VSyncEnd, VTotal :  434,  453
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.1 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1152x864":
(II) NVIDIA(0):     1152 x 864 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 121.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1152, 1216
(II) NVIDIA(0):       HSyncEnd, HTotal : 1344, 1568
(II) NVIDIA(0):       VRes, VSyncStart :  864,  865
(II) NVIDIA(0):       VSyncEnd, VTotal :  868,  911
(II) NVIDIA(0):       H/V Polarity     : +/-
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.1 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "576x432":
(II) NVIDIA(0):     576 x 432 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 60.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  576,  608
(II) NVIDIA(0):       HSyncEnd, HTotal :  672,  784
(II) NVIDIA(0):       VRes, VSyncStart :  432,  432
(II) NVIDIA(0):       VSyncEnd, VTotal :  434,  455
(II) NVIDIA(0):       H/V Polarity     : +/-
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.2 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1152x864":
(II) NVIDIA(0):     1152 x 864 @ 100 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 143.47 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1152, 1232
(II) NVIDIA(0):       HSyncEnd, HTotal : 1360, 1568
(II) NVIDIA(0):       VRes, VSyncStart :  864,  865
(II) NVIDIA(0):       VSyncEnd, VTotal :  868,  915
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (91.5 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "576x432":
(II) NVIDIA(0):     576 x 432 @ 100 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 71.73 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  576,  616
(II) NVIDIA(0):       HSyncEnd, HTotal :  680,  784
(II) NVIDIA(0):       VRes, VSyncStart :  432,  432
(II) NVIDIA(0):       VSyncEnd, VTotal :  434,  457
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (91.5 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1360x768":
(II) NVIDIA(0):     1360 x 768 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 72.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1360, 1408
(II) NVIDIA(0):       HSyncEnd, HTotal : 1440, 1520
(II) NVIDIA(0):       VRes, VSyncStart :  768,  771
(II) NVIDIA(0):       VSyncEnd, VTotal :  781,  790
(II) NVIDIA(0):       H/V Polarity     : +/-
(II) NVIDIA(0):     Mode (1360 x 768) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1360x768" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "680x384":
(II) NVIDIA(0):     680 x 384 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 36.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  680,  704
(II) NVIDIA(0):       HSyncEnd, HTotal :  720,  760
(II) NVIDIA(0):       VRes, VSyncStart :  384,  385
(II) NVIDIA(0):       VSyncEnd, VTotal :  390,  395
(II) NVIDIA(0):       H/V Polarity     : +/-
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     Mode (680 x 384) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "680x384" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1360x768":
(II) NVIDIA(0):     1360 x 768 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 84.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1360, 1432
(II) NVIDIA(0):       HSyncEnd, HTotal : 1568, 1776
(II) NVIDIA(0):       VRes, VSyncStart :  768,  771
(II) NVIDIA(0):       VSyncEnd, VTotal :  781,  798
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):     Mode (1360 x 768) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1360x768" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "680x384":
(II) NVIDIA(0):     680 x 384 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 42.38 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  680,  716
(II) NVIDIA(0):       HSyncEnd, HTotal :  784,  888
(II) NVIDIA(0):       VRes, VSyncStart :  384,  385
(II) NVIDIA(0):       VSyncEnd, VTotal :  390,  399
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     Mode (680 x 384) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "680x384" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1400x1050":
(II) NVIDIA(0):     1400 x 1050 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 122.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1400, 1488
(II) NVIDIA(0):       HSyncEnd, HTotal : 1640, 1880
(II) NVIDIA(0):       VRes, VSyncStart : 1050, 1052
(II) NVIDIA(0):       VSyncEnd, VTotal : 1064, 1082
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode (1400 x 1050) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1400x1050" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "700x525":
(II) NVIDIA(0):     700 x 525 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 61.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  700,  744
(II) NVIDIA(0):       HSyncEnd, HTotal :  820,  940
(II) NVIDIA(0):       VRes, VSyncStart :  525,  526
(II) NVIDIA(0):       VSyncEnd, VTotal :  532,  541
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     Mode (700 x 525) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Mode is rejected: Mode's width (700) is not a multiple of
(WW) NVIDIA(0):     8.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1400x1050":
(II) NVIDIA(0):     1400 x 1050 @ 70 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 145.06 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1400, 1496
(II) NVIDIA(0):       HSyncEnd, HTotal : 1648, 1896
(II) NVIDIA(0):       VRes, VSyncStart : 1050, 1051
(II) NVIDIA(0):       VSyncEnd, VTotal : 1054, 1093
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):     Mode (1400 x 1050) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1400x1050" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "700x525":
(II) NVIDIA(0):     700 x 525 @ 70 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 72.53 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  700,  748
(II) NVIDIA(0):       HSyncEnd, HTotal :  824,  948
(II) NVIDIA(0):       VRes, VSyncStart :  525,  525
(II) NVIDIA(0):       VSyncEnd, VTotal :  527,  546
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     Mode (700 x 525) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Mode is rejected: Mode's width (700) is not a multiple of
(WW) NVIDIA(0):     8.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1400x1050":
(II) NVIDIA(0):     1400 x 1050 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 155.80 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1400, 1464
(II) NVIDIA(0):       HSyncEnd, HTotal : 1784, 1912
(II) NVIDIA(0):       VRes, VSyncStart : 1050, 1052
(II) NVIDIA(0):       VSyncEnd, VTotal : 1064, 1090
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode (1400 x 1050) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1400x1050" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "700x525":
(II) NVIDIA(0):     700 x 525 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 77.90 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  700,  732
(II) NVIDIA(0):       HSyncEnd, HTotal :  892,  956
(II) NVIDIA(0):       VRes, VSyncStart :  525,  526
(II) NVIDIA(0):       VSyncEnd, VTotal :  532,  545
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     Mode (700 x 525) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Mode is rejected: Mode's width (700) is not a multiple of
(WW) NVIDIA(0):     8.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1400x1050":
(II) NVIDIA(0):     1400 x 1050 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 179.26 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1400, 1504
(II) NVIDIA(0):       HSyncEnd, HTotal : 1656, 1912
(II) NVIDIA(0):       VRes, VSyncStart : 1050, 1051
(II) NVIDIA(0):       VSyncEnd, VTotal : 1054, 1103
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (93.8 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "700x525":
(II) NVIDIA(0):     700 x 525 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 89.63 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  700,  752
(II) NVIDIA(0):       HSyncEnd, HTotal :  828,  956
(II) NVIDIA(0):       VRes, VSyncStart :  525,  525
(II) NVIDIA(0):       VSyncEnd, VTotal :  527,  551
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (93.8 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1440x900":
(II) NVIDIA(0):     1440 x 900 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 106.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1440, 1520
(II) NVIDIA(0):       HSyncEnd, HTotal : 1672, 1904
(II) NVIDIA(0):       VRes, VSyncStart :  900,  903
(II) NVIDIA(0):       VSyncEnd, VTotal :  909,  934
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):     Mode (1440 x 900) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1440x900" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "720x450":
(II) NVIDIA(0):     720 x 450 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 53.25 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  720,  760
(II) NVIDIA(0):       HSyncEnd, HTotal :  836,  952
(II) NVIDIA(0):       VRes, VSyncStart :  450,  451
(II) NVIDIA(0):       VSyncEnd, VTotal :  454,  467
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     Mode (720 x 450) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "720x450" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1024":
(II) NVIDIA(0):     1600 x 1024 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 103.12 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1600
(II) NVIDIA(0):       HSyncEnd, HTotal : 1656, 1664
(II) NVIDIA(0):       VRes, VSyncStart : 1024, 1024
(II) NVIDIA(0):       VSyncEnd, VTotal : 1029, 1030
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode (1600 x 1024) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1600x1024" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x512":
(II) NVIDIA(0):     800 x 512 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 51.56 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  800
(II) NVIDIA(0):       HSyncEnd, HTotal :  828,  832
(II) NVIDIA(0):       VRes, VSyncStart :  512,  512
(II) NVIDIA(0):       VSyncEnd, VTotal :  514,  515
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     Mode (800 x 512) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "800x512" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1680x1050":
(II) NVIDIA(0):     1680 x 1050 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 119.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1680, 1728
(II) NVIDIA(0):       HSyncEnd, HTotal : 1760, 1840
(II) NVIDIA(0):       VRes, VSyncStart : 1050, 1053
(II) NVIDIA(0):       VSyncEnd, VTotal : 1059, 1080
(II) NVIDIA(0):       H/V Polarity     : +/-
(II) NVIDIA(0):     Mode (1680 x 1050) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1680x1050" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "840x525":
(II) NVIDIA(0):     840 x 525 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 59.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  840,  864
(II) NVIDIA(0):       HSyncEnd, HTotal :  880,  920
(II) NVIDIA(0):       VRes, VSyncStart :  525,  526
(II) NVIDIA(0):       VSyncEnd, VTotal :  529,  540
(II) NVIDIA(0):       H/V Polarity     : +/-
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     Mode (840 x 525) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "840x525" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1680x1050":
(II) NVIDIA(0):     1680 x 1050 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 146.25 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1680, 1784
(II) NVIDIA(0):       HSyncEnd, HTotal : 1960, 2240
(II) NVIDIA(0):       VRes, VSyncStart : 1050, 1053
(II) NVIDIA(0):       VSyncEnd, VTotal : 1059, 1089
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):     Mode (1680 x 1050) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1680x1050" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "840x525":
(II) NVIDIA(0):     840 x 525 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 73.12 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  840,  892
(II) NVIDIA(0):       HSyncEnd, HTotal :  980, 1120
(II) NVIDIA(0):       VRes, VSyncStart :  525,  526
(II) NVIDIA(0):       VSyncEnd, VTotal :  529,  544
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     Mode (840 x 525) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "840x525" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1680x1050":
(II) NVIDIA(0):     1680 x 1050 @ 70 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 174.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1680, 1800
(II) NVIDIA(0):       HSyncEnd, HTotal : 1976, 2272
(II) NVIDIA(0):       VRes, VSyncStart : 1050, 1053
(II) NVIDIA(0):       VSyncEnd, VTotal : 1059, 1096
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):     Mode (1680 x 1050) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1680x1050" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "840x525":
(II) NVIDIA(0):     840 x 525 @ 70 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 87.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  840,  900
(II) NVIDIA(0):       HSyncEnd, HTotal :  988, 1136
(II) NVIDIA(0):       VRes, VSyncStart :  525,  526
(II) NVIDIA(0):       VSyncEnd, VTotal :  529,  548
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     Mode (840 x 525) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "840x525" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1680x1050":
(II) NVIDIA(0):     1680 x 1050 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 187.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1680, 1800
(II) NVIDIA(0):       HSyncEnd, HTotal : 1976, 2272
(II) NVIDIA(0):       VRes, VSyncStart : 1050, 1053
(II) NVIDIA(0):       VSyncEnd, VTotal : 1059, 1099
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):     Mode (1680 x 1050) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1680x1050" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "840x525":
(II) NVIDIA(0):     840 x 525 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 93.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  840,  900
(II) NVIDIA(0):       HSyncEnd, HTotal :  988, 1136
(II) NVIDIA(0):       VRes, VSyncStart :  525,  526
(II) NVIDIA(0):       VSyncEnd, VTotal :  529,  549
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     Mode (840 x 525) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "840x525" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1680x1050":
(II) NVIDIA(0):     1680 x 1050 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 214.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1680, 1808
(II) NVIDIA(0):       HSyncEnd, HTotal : 1984, 2288
(II) NVIDIA(0):       VRes, VSyncStart : 1050, 1053
(II) NVIDIA(0):       VSyncEnd, VTotal : 1059, 1105
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (93.9 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "840x525":
(II) NVIDIA(0):     840 x 525 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 107.38 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  840,  904
(II) NVIDIA(0):       HSyncEnd, HTotal :  992, 1144
(II) NVIDIA(0):       VRes, VSyncStart :  525,  526
(II) NVIDIA(0):       VSyncEnd, VTotal :  529,  552
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (93.9 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1920x1080":
(II) NVIDIA(0):     1920 x 1080 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 138.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1920, 1968
(II) NVIDIA(0):       HSyncEnd, HTotal : 2000, 2080
(II) NVIDIA(0):       VRes, VSyncStart : 1080, 1083
(II) NVIDIA(0):       VSyncEnd, VTotal : 1088, 1111
(II) NVIDIA(0):       H/V Polarity     : +/-
(II) NVIDIA(0):     Mode (1920 x 1080) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1920x1080" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "960x540":
(II) NVIDIA(0):     960 x 540 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 69.25 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  960,  984
(II) NVIDIA(0):       HSyncEnd, HTotal : 1000, 1040
(II) NVIDIA(0):       VRes, VSyncStart :  540,  541
(II) NVIDIA(0):       VSyncEnd, VTotal :  544,  555
(II) NVIDIA(0):       H/V Polarity     : +/-
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     Mode (960 x 540) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "960x540" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1920x1200":
(II) NVIDIA(0):     1920 x 1200 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 154.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1920, 1968
(II) NVIDIA(0):       HSyncEnd, HTotal : 2000, 2080
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1203
(II) NVIDIA(0):       VSyncEnd, VTotal : 1209, 1235
(II) NVIDIA(0):       H/V Polarity     : +/-
(II) NVIDIA(0):     Mode (1920 x 1200) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1920x1200" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "960x600":
(II) NVIDIA(0):     960 x 600 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 77.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  960,  984
(II) NVIDIA(0):       HSyncEnd, HTotal : 1000, 1040
(II) NVIDIA(0):       VRes, VSyncStart :  600,  601
(II) NVIDIA(0):       VSyncEnd, VTotal :  604,  617
(II) NVIDIA(0):       H/V Polarity     : +/-
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     Mode (960 x 600) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "960x600" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1920x1440":
(II) NVIDIA(0):     1920 x 1440 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 341.35 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1920, 2072
(II) NVIDIA(0):       HSyncEnd, HTotal : 2288, 2656
(II) NVIDIA(0):       VRes, VSyncStart : 1440, 1441
(II) NVIDIA(0):       VSyncEnd, VTotal : 1444, 1512
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (341.4 MHz) too high for
(WW) NVIDIA(0):     Display Device (Max: 330.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "960x720":
(II) NVIDIA(0):     960 x 720 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 170.68 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  960, 1036
(II) NVIDIA(0):       HSyncEnd, HTotal : 1144, 1328
(II) NVIDIA(0):       VRes, VSyncStart :  720,  720
(II) NVIDIA(0):       VSyncEnd, VTotal :  722,  756
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (128.5 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "2048x1536":
(II) NVIDIA(0):     2048 x 1536 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 266.95 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 2048, 2200
(II) NVIDIA(0):       HSyncEnd, HTotal : 2424, 2800
(II) NVIDIA(0):       VRes, VSyncStart : 1536, 1537
(II) NVIDIA(0):       VSyncEnd, VTotal : 1540, 1589
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (95.3 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 133.47 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1100
(II) NVIDIA(0):       HSyncEnd, HTotal : 1212, 1400
(II) NVIDIA(0):       VRes, VSyncStart :  768,  768
(II) NVIDIA(0):       VSyncEnd, VTotal :  770,  794
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (95.3 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "2048x1536":
(II) NVIDIA(0):     2048 x 1536 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 340.48 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 2048, 2216
(II) NVIDIA(0):       HSyncEnd, HTotal : 2440, 2832
(II) NVIDIA(0):       VRes, VSyncStart : 1536, 1537
(II) NVIDIA(0):       VSyncEnd, VTotal : 1540, 1603
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (340.5 MHz) too high for
(WW) NVIDIA(0):     Display Device (Max: 330.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 170.24 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1108
(II) NVIDIA(0):       HSyncEnd, HTotal : 1220, 1416
(II) NVIDIA(0):       VRes, VSyncStart :  768,  768
(II) NVIDIA(0):       VSyncEnd, VTotal :  770,  801
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (120.2 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "2048x1536":
(II) NVIDIA(0):     2048 x 1536 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 388.04 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 2048, 2216
(II) NVIDIA(0):       HSyncEnd, HTotal : 2440, 2832
(II) NVIDIA(0):       VRes, VSyncStart : 1536, 1537
(II) NVIDIA(0):       VSyncEnd, VTotal : 1540, 1612
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (388.0 MHz) too high for
(WW) NVIDIA(0):     Display Device (Max: 330.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 194.02 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1108
(II) NVIDIA(0):       HSyncEnd, HTotal : 1220, 1416
(II) NVIDIA(0):       VRes, VSyncStart :  768,  768
(II) NVIDIA(0):       VSyncEnd, VTotal :  770,  806
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (137.0 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x350":
(II) NVIDIA(0):     640 x 350 @ 85 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  672
(II) NVIDIA(0):       HSyncEnd, HTotal :  736,  832
(II) NVIDIA(0):       VRes, VSyncStart :  350,  382
(II) NVIDIA(0):       VSyncEnd, VTotal :  385,  445
(II) NVIDIA(0):       H/V Polarity     : +/-
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.1 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x400":
(II) NVIDIA(0):     640 x 400 @ 85 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  672
(II) NVIDIA(0):       HSyncEnd, HTotal :  736,  832
(II) NVIDIA(0):       VRes, VSyncStart :  400,  401
(II) NVIDIA(0):       VSyncEnd, VTotal :  404,  445
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.1 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "720x400":
(II) NVIDIA(0):     720 x 400 @ 85 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 35.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  720,  756
(II) NVIDIA(0):       HSyncEnd, HTotal :  828,  936
(II) NVIDIA(0):       VRes, VSyncStart :  400,  401
(II) NVIDIA(0):       VSyncEnd, VTotal :  404,  446
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.0 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 60 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 25.18 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  656
(II) NVIDIA(0):       HSyncEnd, HTotal :  752,  800
(II) NVIDIA(0):       VRes, VSyncStart :  480,  490
(II) NVIDIA(0):       VSyncEnd, VTotal :  492,  525
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     BestFit Backend for "640x480": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 73 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  664
(II) NVIDIA(0):       HSyncEnd, HTotal :  704,  832
(II) NVIDIA(0):       VRes, VSyncStart :  480,  489
(II) NVIDIA(0):       VSyncEnd, VTotal :  492,  520
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     BestFit Backend for "640x480": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 75 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  656
(II) NVIDIA(0):       HSyncEnd, HTotal :  720,  840
(II) NVIDIA(0):       VRes, VSyncStart :  480,  481
(II) NVIDIA(0):       VSyncEnd, VTotal :  484,  500
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     BestFit Backend for "640x480": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 85 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 36.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  696
(II) NVIDIA(0):       HSyncEnd, HTotal :  752,  832
(II) NVIDIA(0):       VRes, VSyncStart :  480,  481
(II) NVIDIA(0):       VSyncEnd, VTotal :  484,  509
(II) NVIDIA(0):       H/V Polarity     : -/-
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.0 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 56 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 36.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  824
(II) NVIDIA(0):       HSyncEnd, HTotal :  896, 1024
(II) NVIDIA(0):       VRes, VSyncStart :  600,  601
(II) NVIDIA(0):       VSyncEnd, VTotal :  603,  625
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode (800 x 600) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "800x600" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 60 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 40.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  840
(II) NVIDIA(0):       HSyncEnd, HTotal :  968, 1056
(II) NVIDIA(0):       VRes, VSyncStart :  600,  601
(II) NVIDIA(0):       VSyncEnd, VTotal :  605,  628
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode (800 x 600) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "800x600" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 72 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 50.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  856
(II) NVIDIA(0):       HSyncEnd, HTotal :  976, 1040
(II) NVIDIA(0):       VRes, VSyncStart :  600,  637
(II) NVIDIA(0):       VSyncEnd, VTotal :  643,  666
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode (800 x 600) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "800x600" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 75 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 49.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  816
(II) NVIDIA(0):       HSyncEnd, HTotal :  896, 1056
(II) NVIDIA(0):       VRes, VSyncStart :  600,  601
(II) NVIDIA(0):       VSyncEnd, VTotal :  604,  625
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode (800 x 600) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "800x600" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 85 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 56.30 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  832
(II) NVIDIA(0):       HSyncEnd, HTotal :  896, 1048
(II) NVIDIA(0):       VRes, VSyncStart :  600,  601
(II) NVIDIA(0):       VSyncEnd, VTotal :  604,  631
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.1 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 87 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 44.90 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1032
(II) NVIDIA(0):       HSyncEnd, HTotal : 1208, 1264
(II) NVIDIA(0):       VRes, VSyncStart :  768,  768
(II) NVIDIA(0):       VSyncEnd, VTotal :  776,  817
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : Interlace
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (87.0 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 60 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 65.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1048
(II) NVIDIA(0):       HSyncEnd, HTotal : 1184, 1344
(II) NVIDIA(0):       VRes, VSyncStart :  768,  771
(II) NVIDIA(0):       VSyncEnd, VTotal :  777,  806
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     Mode (1024 x 768) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1024x768" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 70 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 75.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1048
(II) NVIDIA(0):       HSyncEnd, HTotal : 1184, 1328
(II) NVIDIA(0):       VRes, VSyncStart :  768,  771
(II) NVIDIA(0):       VSyncEnd, VTotal :  777,  806
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     Mode (1024 x 768) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1024x768" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 75 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 78.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1040
(II) NVIDIA(0):       HSyncEnd, HTotal : 1136, 1312
(II) NVIDIA(0):       VRes, VSyncStart :  768,  769
(II) NVIDIA(0):       VSyncEnd, VTotal :  772,  800
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode (1024 x 768) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1024x768" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 85 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 94.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1072
(II) NVIDIA(0):       HSyncEnd, HTotal : 1168, 1376
(II) NVIDIA(0):       VRes, VSyncStart :  768,  769
(II) NVIDIA(0):       VSyncEnd, VTotal :  772,  808
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.0 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1152x864":
(II) NVIDIA(0):     1152 x 864 @ 75 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 108.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1152, 1216
(II) NVIDIA(0):       HSyncEnd, HTotal : 1344, 1600
(II) NVIDIA(0):       VRes, VSyncStart :  864,  865
(II) NVIDIA(0):       VSyncEnd, VTotal :  868,  900
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode (1152 x 864) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1152x864" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x960":
(II) NVIDIA(0):     1280 x 960 @ 60 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 108.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1376
(II) NVIDIA(0):       HSyncEnd, HTotal : 1488, 1800
(II) NVIDIA(0):       VRes, VSyncStart :  960,  961
(II) NVIDIA(0):       VSyncEnd, VTotal :  964, 1000
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode (1280 x 960) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1280x960" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x960":
(II) NVIDIA(0):     1280 x 960 @ 85 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 148.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1344
(II) NVIDIA(0):       HSyncEnd, HTotal : 1504, 1728
(II) NVIDIA(0):       VRes, VSyncStart :  960,  961
(II) NVIDIA(0):       VSyncEnd, VTotal :  964, 1011
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (85.9 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x1024":
(II) NVIDIA(0):     1280 x 1024 @ 60 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 108.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1328
(II) NVIDIA(0):       HSyncEnd, HTotal : 1440, 1688
(II) NVIDIA(0):       VRes, VSyncStart : 1024, 1025
(II) NVIDIA(0):       VSyncEnd, VTotal : 1028, 1066
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode (1280 x 1024) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1280x1024" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x1024":
(II) NVIDIA(0):     1280 x 1024 @ 75 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 135.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1296
(II) NVIDIA(0):       HSyncEnd, HTotal : 1440, 1688
(II) NVIDIA(0):       VRes, VSyncStart : 1024, 1025
(II) NVIDIA(0):       VSyncEnd, VTotal : 1028, 1066
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode (1280 x 1024) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1280x1024" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x1024":
(II) NVIDIA(0):     1280 x 1024 @ 85 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 157.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1344
(II) NVIDIA(0):       HSyncEnd, HTotal : 1504, 1728
(II) NVIDIA(0):       VRes, VSyncStart : 1024, 1025
(II) NVIDIA(0):       VSyncEnd, VTotal : 1028, 1072
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (91.1 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1200":
(II) NVIDIA(0):     1600 x 1200 @ 60 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 162.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
(II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
(II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode (1600 x 1200) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1600x1200" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1200":
(II) NVIDIA(0):     1600 x 1200 @ 65 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 175.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
(II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
(II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode (1600 x 1200) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1600x1200" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1200":
(II) NVIDIA(0):     1600 x 1200 @ 70 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 189.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
(II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
(II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (87.5 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1200":
(II) NVIDIA(0):     1600 x 1200 @ 75 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 202.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
(II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
(II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (93.8 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1200":
(II) NVIDIA(0):     1600 x 1200 @ 85 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 229.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
(II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
(II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (106.2 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1792x1344":
(II) NVIDIA(0):     1792 x 1344 @ 60 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 204.80 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1792, 1920
(II) NVIDIA(0):       HSyncEnd, HTotal : 2120, 2448
(II) NVIDIA(0):       VRes, VSyncStart : 1344, 1345
(II) NVIDIA(0):       VSyncEnd, VTotal : 1348, 1394
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (83.7 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1792x1344":
(II) NVIDIA(0):     1792 x 1344 @ 75 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 261.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1792, 1888
(II) NVIDIA(0):       HSyncEnd, HTotal : 2104, 2456
(II) NVIDIA(0):       VRes, VSyncStart : 1344, 1345
(II) NVIDIA(0):       VSyncEnd, VTotal : 1348, 1417
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (106.3 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1856x1392":
(II) NVIDIA(0):     1856 x 1392 @ 60 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 218.30 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1856, 1952
(II) NVIDIA(0):       HSyncEnd, HTotal : 2176, 2528
(II) NVIDIA(0):       VRes, VSyncStart : 1392, 1393
(II) NVIDIA(0):       VSyncEnd, VTotal : 1396, 1439
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (86.4 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1856x1392":
(II) NVIDIA(0):     1856 x 1392 @ 75 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 288.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1856, 1984
(II) NVIDIA(0):       HSyncEnd, HTotal : 2208, 2560
(II) NVIDIA(0):       VRes, VSyncStart : 1392, 1393
(II) NVIDIA(0):       VSyncEnd, VTotal : 1396, 1500
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (112.5 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1920x1440":
(II) NVIDIA(0):     1920 x 1440 @ 60 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 234.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1920, 2048
(II) NVIDIA(0):       HSyncEnd, HTotal : 2256, 2600
(II) NVIDIA(0):       VRes, VSyncStart : 1440, 1441
(II) NVIDIA(0):       VSyncEnd, VTotal : 1444, 1500
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (90.0 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1920x1440":
(II) NVIDIA(0):     1920 x 1440 @ 75 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 297.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1920, 2064
(II) NVIDIA(0):       HSyncEnd, HTotal : 2288, 2640
(II) NVIDIA(0):       VRes, VSyncStart : 1440, 1441
(II) NVIDIA(0):       VSyncEnd, VTotal : 1444, 1500
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (112.5 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0): --- Done building ModePool for DFP-0 ---
(II) NVIDIA(0): 
(II) NVIDIA(0): 
(II) NVIDIA(0): --- Modes in ModePool for DFP-0 ---
(II) NVIDIA(0): "nvidia-auto-select" :  640 x  480 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "640x480"            :  640 x  480 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "640x480d60"         :  640 x  480 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "640x480_75"         :  640 x  480 @  75.0 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "640x480_73"         :  640 x  480 @  72.8 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "640x480_60"         :  640 x  480 @  59.9 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "576x432"            :  576 x  432 @  75.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "576x432d75"         :  576 x  432 @  75.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "576x432d75_0"       :  576 x  432 @  75.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "576x432d70"         :  576 x  432 @  70.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "576x432d60"         :  576 x  432 @  60.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "512x384"            :  512 x  384 @  75.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "512x384d75"         :  512 x  384 @  75.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "512x384d70"         :  512 x  384 @  70.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "512x384d60"         :  512 x  384 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "416x312"            :  416 x  312 @  74.7 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "416x312d75"         :  416 x  312 @  74.7 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "400x300"            :  400 x  300 @  75.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "400x300d75"         :  400 x  300 @  75.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "400x300d72"         :  400 x  300 @  72.2 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "400x300d60"         :  400 x  300 @  60.3 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "400x300d56"         :  400 x  300 @  56.3 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "320x240"            :  320 x  240 @  75.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "320x240d75"         :  320 x  240 @  75.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "320x240d73"         :  320 x  240 @  72.8 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "320x240d60"         :  320 x  240 @  60.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): --- End of ModePool for DFP-0: ---
(II) NVIDIA(0): 
(II) NVIDIA(0): Assigned Display Device: DFP-0
(==) NVIDIA(0): 
(==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) NVIDIA(0):     will be used as the requested mode.
(==) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0): Virtual screen size determined to be 640 x 480
(II) NVIDIA(0): 
(II) NVIDIA(0): Implicitly adding the following modes to X Screen 0 (these
(II) NVIDIA(0):     will be available via XRandR and XF86VidMode):
(II) NVIDIA(0): 
(II) NVIDIA(0): "640x480_75"   :  640 x  480 @  75.0 Hz 
(II) NVIDIA(0): "640x480_73"   :  640 x  480 @  72.8 Hz 
(II) NVIDIA(0): "640x480_60"   :  640 x  480 @  59.9 Hz 
(II) NVIDIA(0): "576x432"      :  576 x  432 @  75.0 Hz DoubleScan 
(II) NVIDIA(0): "576x432d75_0" :  576 x  432 @  75.0 Hz DoubleScan 
(II) NVIDIA(0): "576x432d70"   :  576 x  432 @  70.0 Hz DoubleScan 
(II) NVIDIA(0): "576x432d60"   :  576 x  432 @  60.1 Hz DoubleScan 
(II) NVIDIA(0): "512x384"      :  512 x  384 @  75.0 Hz DoubleScan 
(II) NVIDIA(0): "512x384d70"   :  512 x  384 @  70.1 Hz DoubleScan 
(II) NVIDIA(0): "512x384d60"   :  512 x  384 @  60.0 Hz DoubleScan 
(II) NVIDIA(0): "416x312"      :  416 x  312 @  74.7 Hz DoubleScan 
(II) NVIDIA(0): "400x300"      :  400 x  300 @  75.1 Hz DoubleScan 
(II) NVIDIA(0): "400x300d72"   :  400 x  300 @  72.2 Hz DoubleScan 
(II) NVIDIA(0): "400x300d60"   :  400 x  300 @  60.3 Hz DoubleScan 
(II) NVIDIA(0): "400x300d56"   :  400 x  300 @  56.3 Hz DoubleScan 
(II) NVIDIA(0): "320x240"      :  320 x  240 @  75.0 Hz DoubleScan 
(II) NVIDIA(0): "320x240d73"   :  320 x  240 @  72.8 Hz DoubleScan 
(II) NVIDIA(0): "320x240d60"   :  320 x  240 @  60.1 Hz DoubleScan 
(II) NVIDIA(0): 
(WW) NVIDIA(0): Unable to get display device DFP-0's EDID; cannot compute DPI
(WW) NVIDIA(0):     from DFP-0's EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) NVIDIA(0): Built-in logo is bigger than the screen.
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing extension GLX
(II) config/hal: Adding input device Macintosh mouse button emulation
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) config/hal: Adding input device Microsoft Comfort Curve Keyboard 2000
(**) Microsoft Comfort Curve Keyboard 2000: always reports core events
(**) Microsoft Comfort Curve Keyboard 2000: Device: "/dev/input/event6"
(II) Microsoft Comfort Curve Keyboard 2000: Found 1 mouse buttons
(II) Microsoft Comfort Curve Keyboard 2000: Found keys
(II) Microsoft Comfort Curve Keyboard 2000: Configuring as keyboard
(**) Microsoft Comfort Curve Keyboard 2000: YAxisMapping: buttons 4 and 5
(**) Microsoft Comfort Curve Keyboard 2000: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Microsoft Comfort Curve Keyboard 2000" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Microsoft Comfort Curve Keyboard 2000: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Microsoft Comfort Curve Keyboard 2000: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Microsoft Comfort Curve Keyboard 2000: xkb_layout: "us"
(II) config/hal: Adding input device Microsoft Comfort Curve Keyboard 2000
(**) Microsoft Comfort Curve Keyboard 2000: always reports core events
(**) Microsoft Comfort Curve Keyboard 2000: Device: "/dev/input/event5"
(II) Microsoft Comfort Curve Keyboard 2000: Found keys
(II) Microsoft Comfort Curve Keyboard 2000: Configuring as keyboard
(II) XINPUT: Adding extended input device "Microsoft Comfort Curve Keyboard 2000" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Microsoft Comfort Curve Keyboard 2000: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Microsoft Comfort Curve Keyboard 2000: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Microsoft Comfort Curve Keyboard 2000: xkb_layout: "us"
(II) config/hal: Adding input device Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): always reports core events
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Device: "/dev/input/event7"
(II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found 3 mouse buttons
(II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found x and y relative axes
(II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Configuring as mouse
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): YAxisMapping: buttons 4 and 5
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)" (type: MOUSE)
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): (accel) keeping acceleration scheme 1
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): (accel) filter chain progression: 2.00
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): (accel) filter stage 0: 20.00 ms
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): (accel) set acceleration profile 0
```

This is the log when it is set for 31-80 (digital):

```

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux ubuntu-desktop 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Sep  4 13:44:13 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@1:0:0) nVidia Corporation G70 [GeForce 7300 GT] rev 161, Mem @ 0xfa000000/16777216, 0xd0000000/268435456, 0xfb000000/16777216, I/O @ 0x0000cf00/128, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(WW) "dri2" will not be loaded unless you've specified it to be loaded elsewhere.
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded even though the default is to disable it.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  180.44  Mon Mar 23 15:29:02 PST 2009
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  180.44  Mon Mar 23 15:05:32 PST 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "UseEDID" "False"
(**) NVIDIA(0): Option "ModeDebug" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): Ignoring EDIDs
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(GPU-0): Not probing EDID on DFP-0.
(II) NVIDIA(0): NVIDIA GPU GeForce 7300 GT (G73) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.73.22.40.00
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7300 GT at PCI:1:0:0:
(--) NVIDIA(0):     DFP-0
(--) NVIDIA(0): DFP-0: 330.0 MHz maximum pixel clock
(--) NVIDIA(0): DFP-0: Internal Dual Link TMDS
(--) NVIDIA(0): 
(--) NVIDIA(0): --- EDID for DFP-0 ---
(--) NVIDIA(0): 
(--) NVIDIA(0): No EDID Available.
(--) NVIDIA(0): 
(--) NVIDIA(0): --- End of EDID for DFP-0 ---
(--) NVIDIA(0): 
(II) NVIDIA(0): Frequency information for DFP-0:
(II) NVIDIA(0):   HorizSync   : 31.000-80.000 kHz
(II) NVIDIA(0):   VertRefresh : 50.000-75.000 Hz
(II) NVIDIA(0):     (HorizSync from HorizSync in X Config Monitor section)
(II) NVIDIA(0):     (VertRefresh from VertRefresh in X Config Monitor
(II) NVIDIA(0):     section)
(II) NVIDIA(0): 
(II) NVIDIA(0): --- Building ModePool for DFP-0 ---
(II) NVIDIA(0): 
(II) NVIDIA(0): Native backend timings for DFP-0:
(II) NVIDIA(0):   640 x 480 @ 60 Hz
(II) NVIDIA(0):     Pixel Clock      : 25.175 MHz
(II) NVIDIA(0):     HRes, HSyncStart :  640,  656
(II) NVIDIA(0):     HSyncEnd, HTotal :  752,  800
(II) NVIDIA(0):     VRes, VSyncStart :  480,  490
(II) NVIDIA(0):     VSyncEnd, VTotal :  492,  525
(II) NVIDIA(0):     H/V Polarity     : -/-
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x350":
(II) NVIDIA(0):     640 x 350 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  672
(II) NVIDIA(0):       HSyncEnd, HTotal :  736,  832
(II) NVIDIA(0):       VRes, VSyncStart :  350,  382
(II) NVIDIA(0):       VSyncEnd, VTotal :  385,  445
(II) NVIDIA(0):       H/V Polarity     : +/-
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.1 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "320x175":
(II) NVIDIA(0):     320 x 175 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 15.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  320,  336
(II) NVIDIA(0):       HSyncEnd, HTotal :  368,  416
(II) NVIDIA(0):       VRes, VSyncStart :  175,  191
(II) NVIDIA(0):       VSyncEnd, VTotal :  192,  222
(II) NVIDIA(0):       H/V Polarity     : +/-
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.3 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x400":
(II) NVIDIA(0):     640 x 400 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  672
(II) NVIDIA(0):       HSyncEnd, HTotal :  736,  832
(II) NVIDIA(0):       VRes, VSyncStart :  400,  401
(II) NVIDIA(0):       VSyncEnd, VTotal :  404,  445
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.1 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "320x200":
(II) NVIDIA(0):     320 x 200 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 15.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  320,  336
(II) NVIDIA(0):       HSyncEnd, HTotal :  368,  416
(II) NVIDIA(0):       VRes, VSyncStart :  200,  200
(II) NVIDIA(0):       VSyncEnd, VTotal :  202,  222
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.3 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "720x400":
(II) NVIDIA(0):     720 x 400 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 35.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  720,  756
(II) NVIDIA(0):       HSyncEnd, HTotal :  828,  936
(II) NVIDIA(0):       VRes, VSyncStart :  400,  401
(II) NVIDIA(0):       VSyncEnd, VTotal :  404,  446
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.0 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "360x200":
(II) NVIDIA(0):     360 x 200 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 17.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  360,  378
(II) NVIDIA(0):       HSyncEnd, HTotal :  414,  468
(II) NVIDIA(0):       VRes, VSyncStart :  200,  200
(II) NVIDIA(0):       VSyncEnd, VTotal :  202,  223
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.0 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 25.18 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  656
(II) NVIDIA(0):       HSyncEnd, HTotal :  752,  800
(II) NVIDIA(0):       VRes, VSyncStart :  480,  490
(II) NVIDIA(0):       VSyncEnd, VTotal :  492,  525
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     BestFit Backend for "640x480": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "320x240":
(II) NVIDIA(0):     320 x 240 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 12.59 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  320,  328
(II) NVIDIA(0):       HSyncEnd, HTotal :  376,  400
(II) NVIDIA(0):       VRes, VSyncStart :  240,  245
(II) NVIDIA(0):       VSyncEnd, VTotal :  246,  262
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "320x240": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 73 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  664
(II) NVIDIA(0):       HSyncEnd, HTotal :  704,  832
(II) NVIDIA(0):       VRes, VSyncStart :  480,  489
(II) NVIDIA(0):       VSyncEnd, VTotal :  492,  520
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     BestFit Backend for "640x480": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "320x240":
(II) NVIDIA(0):     320 x 240 @ 73 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 15.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  320,  332
(II) NVIDIA(0):       HSyncEnd, HTotal :  352,  416
(II) NVIDIA(0):       VRes, VSyncStart :  240,  244
(II) NVIDIA(0):       VSyncEnd, VTotal :  246,  260
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "320x240": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  656
(II) NVIDIA(0):       HSyncEnd, HTotal :  720,  840
(II) NVIDIA(0):       VRes, VSyncStart :  480,  481
(II) NVIDIA(0):       VSyncEnd, VTotal :  484,  500
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     BestFit Backend for "640x480": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "320x240":
(II) NVIDIA(0):     320 x 240 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 15.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  320,  328
(II) NVIDIA(0):       HSyncEnd, HTotal :  360,  420
(II) NVIDIA(0):       VRes, VSyncStart :  240,  240
(II) NVIDIA(0):       VSyncEnd, VTotal :  242,  250
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "320x240": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 36.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  696
(II) NVIDIA(0):       HSyncEnd, HTotal :  752,  832
(II) NVIDIA(0):       VRes, VSyncStart :  480,  481
(II) NVIDIA(0):       VSyncEnd, VTotal :  484,  509
(II) NVIDIA(0):       H/V Polarity     : -/-
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.0 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "320x240":
(II) NVIDIA(0):     320 x 240 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 18.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  320,  348
(II) NVIDIA(0):       HSyncEnd, HTotal :  376,  416
(II) NVIDIA(0):       VRes, VSyncStart :  240,  240
(II) NVIDIA(0):       VSyncEnd, VTotal :  242,  254
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.2 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 56 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 36.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  824
(II) NVIDIA(0):       HSyncEnd, HTotal :  896, 1024
(II) NVIDIA(0):       VRes, VSyncStart :  600,  601
(II) NVIDIA(0):       VSyncEnd, VTotal :  603,  625
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode (800 x 600) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "800x600" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "400x300":
(II) NVIDIA(0):     400 x 300 @ 56 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 18.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  400,  412
(II) NVIDIA(0):       HSyncEnd, HTotal :  448,  512
(II) NVIDIA(0):       VRes, VSyncStart :  300,  300
(II) NVIDIA(0):       VSyncEnd, VTotal :  301,  312
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "400x300": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 40.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  840
(II) NVIDIA(0):       HSyncEnd, HTotal :  968, 1056
(II) NVIDIA(0):       VRes, VSyncStart :  600,  601
(II) NVIDIA(0):       VSyncEnd, VTotal :  605,  628
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode (800 x 600) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "800x600" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "400x300":
(II) NVIDIA(0):     400 x 300 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 20.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  400,  420
(II) NVIDIA(0):       HSyncEnd, HTotal :  484,  528
(II) NVIDIA(0):       VRes, VSyncStart :  300,  300
(II) NVIDIA(0):       VSyncEnd, VTotal :  302,  314
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "400x300": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 72 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 50.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  856
(II) NVIDIA(0):       HSyncEnd, HTotal :  976, 1040
(II) NVIDIA(0):       VRes, VSyncStart :  600,  637
(II) NVIDIA(0):       VSyncEnd, VTotal :  643,  666
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode (800 x 600) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "800x600" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "400x300":
(II) NVIDIA(0):     400 x 300 @ 72 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 25.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  400,  428
(II) NVIDIA(0):       HSyncEnd, HTotal :  488,  520
(II) NVIDIA(0):       VRes, VSyncStart :  300,  318
(II) NVIDIA(0):       VSyncEnd, VTotal :  321,  333
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "400x300": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 49.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  816
(II) NVIDIA(0):       HSyncEnd, HTotal :  896, 1056
(II) NVIDIA(0):       VRes, VSyncStart :  600,  601
(II) NVIDIA(0):       VSyncEnd, VTotal :  604,  625
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode (800 x 600) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "800x600" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "400x300":
(II) NVIDIA(0):     400 x 300 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 24.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  400,  408
(II) NVIDIA(0):       HSyncEnd, HTotal :  448,  528
(II) NVIDIA(0):       VRes, VSyncStart :  300,  300
(II) NVIDIA(0):       VSyncEnd, VTotal :  302,  312
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "400x300": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 56.30 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  832
(II) NVIDIA(0):       HSyncEnd, HTotal :  896, 1048
(II) NVIDIA(0):       VRes, VSyncStart :  600,  601
(II) NVIDIA(0):       VSyncEnd, VTotal :  604,  631
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.1 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "400x300":
(II) NVIDIA(0):     400 x 300 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 28.15 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  400,  416
(II) NVIDIA(0):       HSyncEnd, HTotal :  448,  524
(II) NVIDIA(0):       VRes, VSyncStart :  300,  300
(II) NVIDIA(0):       VSyncEnd, VTotal :  302,  315
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.3 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 87 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 44.90 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1032
(II) NVIDIA(0):       HSyncEnd, HTotal : 1208, 1264
(II) NVIDIA(0):       VRes, VSyncStart :  768,  768
(II) NVIDIA(0):       VSyncEnd, VTotal :  776,  817
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : Interlace
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (87.0 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "512x384":
(II) NVIDIA(0):     512 x 384 @ 87 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 22.45 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  512,  516
(II) NVIDIA(0):       HSyncEnd, HTotal :  604,  632
(II) NVIDIA(0):       VRes, VSyncStart :  384,  384
(II) NVIDIA(0):       VSyncEnd, VTotal :  388,  408
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : Interlace DoubleScan
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (87.1 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 65.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1048
(II) NVIDIA(0):       HSyncEnd, HTotal : 1184, 1344
(II) NVIDIA(0):       VRes, VSyncStart :  768,  771
(II) NVIDIA(0):       VSyncEnd, VTotal :  777,  806
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     Mode (1024 x 768) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1024x768" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "512x384":
(II) NVIDIA(0):     512 x 384 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 32.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  512,  524
(II) NVIDIA(0):       HSyncEnd, HTotal :  592,  672
(II) NVIDIA(0):       VRes, VSyncStart :  384,  385
(II) NVIDIA(0):       VSyncEnd, VTotal :  388,  403
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "512x384": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 70 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 75.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1048
(II) NVIDIA(0):       HSyncEnd, HTotal : 1184, 1328
(II) NVIDIA(0):       VRes, VSyncStart :  768,  771
(II) NVIDIA(0):       VSyncEnd, VTotal :  777,  806
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     Mode (1024 x 768) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1024x768" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "512x384":
(II) NVIDIA(0):     512 x 384 @ 70 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 37.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  512,  524
(II) NVIDIA(0):       HSyncEnd, HTotal :  592,  664
(II) NVIDIA(0):       VRes, VSyncStart :  384,  385
(II) NVIDIA(0):       VSyncEnd, VTotal :  388,  403
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "512x384": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 78.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1040
(II) NVIDIA(0):       HSyncEnd, HTotal : 1136, 1312
(II) NVIDIA(0):       VRes, VSyncStart :  768,  769
(II) NVIDIA(0):       VSyncEnd, VTotal :  772,  800
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode (1024 x 768) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1024x768" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "512x384":
(II) NVIDIA(0):     512 x 384 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 39.38 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  512,  520
(II) NVIDIA(0):       HSyncEnd, HTotal :  568,  656
(II) NVIDIA(0):       VRes, VSyncStart :  384,  384
(II) NVIDIA(0):       VSyncEnd, VTotal :  386,  400
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "512x384": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 94.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1072
(II) NVIDIA(0):       HSyncEnd, HTotal : 1168, 1376
(II) NVIDIA(0):       VRes, VSyncStart :  768,  769
(II) NVIDIA(0):       VSyncEnd, VTotal :  772,  808
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.0 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "512x384":
(II) NVIDIA(0):     512 x 384 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 47.25 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  512,  536
(II) NVIDIA(0):       HSyncEnd, HTotal :  584,  688
(II) NVIDIA(0):       VRes, VSyncStart :  384,  384
(II) NVIDIA(0):       VSyncEnd, VTotal :  386,  404
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.0 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1152x864":
(II) NVIDIA(0):     1152 x 864 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 108.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1152, 1216
(II) NVIDIA(0):       HSyncEnd, HTotal : 1344, 1600
(II) NVIDIA(0):       VRes, VSyncStart :  864,  865
(II) NVIDIA(0):       VSyncEnd, VTotal :  868,  900
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode (1152 x 864) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1152x864" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "576x432":
(II) NVIDIA(0):     576 x 432 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 54.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  576,  608
(II) NVIDIA(0):       HSyncEnd, HTotal :  672,  800
(II) NVIDIA(0):       VRes, VSyncStart :  432,  432
(II) NVIDIA(0):       VSyncEnd, VTotal :  434,  450
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "576x432": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x960":
(II) NVIDIA(0):     1280 x 960 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 108.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1376
(II) NVIDIA(0):       HSyncEnd, HTotal : 1488, 1800
(II) NVIDIA(0):       VRes, VSyncStart :  960,  961
(II) NVIDIA(0):       VSyncEnd, VTotal :  964, 1000
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode (1280 x 960) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1280x960" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 54.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  688
(II) NVIDIA(0):       HSyncEnd, HTotal :  744,  900
(II) NVIDIA(0):       VRes, VSyncStart :  480,  480
(II) NVIDIA(0):       VSyncEnd, VTotal :  482,  500
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "640x480": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x960":
(II) NVIDIA(0):     1280 x 960 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 148.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1344
(II) NVIDIA(0):       HSyncEnd, HTotal : 1504, 1728
(II) NVIDIA(0):       VRes, VSyncStart :  960,  961
(II) NVIDIA(0):       VSyncEnd, VTotal :  964, 1011
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (85.9 kHz) out of range
(WW) NVIDIA(0):     (31.000-80.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 74.25 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  672
(II) NVIDIA(0):       HSyncEnd, HTotal :  752,  864
(II) NVIDIA(0):       VRes, VSyncStart :  480,  480
(II) NVIDIA(0):       VSyncEnd, VTotal :  482,  505
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (85.9 kHz) out of range
(WW) NVIDIA(0):     (31.000-80.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x1024":
(II) NVIDIA(0):     1280 x 1024 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 108.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1328
(II) NVIDIA(0):       HSyncEnd, HTotal : 1440, 1688
(II) NVIDIA(0):       VRes, VSyncStart : 1024, 1025
(II) NVIDIA(0):       VSyncEnd, VTotal : 1028, 1066
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode (1280 x 1024) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1280x1024" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x512":
(II) NVIDIA(0):     640 x 512 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 54.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  664
(II) NVIDIA(0):       HSyncEnd, HTotal :  720,  844
(II) NVIDIA(0):       VRes, VSyncStart :  512,  512
(II) NVIDIA(0):       VSyncEnd, VTotal :  514,  533
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     Mode (640 x 512) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "640x512" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x1024":
(II) NVIDIA(0):     1280 x 1024 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 135.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1296
(II) NVIDIA(0):       HSyncEnd, HTotal : 1440, 1688
(II) NVIDIA(0):       VRes, VSyncStart : 1024, 1025
(II) NVIDIA(0):       VSyncEnd, VTotal : 1028, 1066
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode (1280 x 1024) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1280x1024" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x512":
(II) NVIDIA(0):     640 x 512 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 67.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  648
(II) NVIDIA(0):       HSyncEnd, HTotal :  720,  844
(II) NVIDIA(0):       VRes, VSyncStart :  512,  512
(II) NVIDIA(0):       VSyncEnd, VTotal :  514,  533
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     Mode (640 x 512) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "640x512" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x1024":
(II) NVIDIA(0):     1280 x 1024 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 157.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1344
(II) NVIDIA(0):       HSyncEnd, HTotal : 1504, 1728
(II) NVIDIA(0):       VRes, VSyncStart : 1024, 1025
(II) NVIDIA(0):       VSyncEnd, VTotal : 1028, 1072
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (91.1 kHz) out of range
(WW) NVIDIA(0):     (31.000-80.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x512":
(II) NVIDIA(0):     640 x 512 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 78.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  672
(II) NVIDIA(0):       HSyncEnd, HTotal :  752,  864
(II) NVIDIA(0):       VRes, VSyncStart :  512,  512
(II) NVIDIA(0):       VSyncEnd, VTotal :  514,  536
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (91.1 kHz) out of range
(WW) NVIDIA(0):     (31.000-80.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1200":
(II) NVIDIA(0):     1600 x 1200 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 162.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
(II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
(II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode (1600 x 1200) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1600x1200" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 81.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  832
(II) NVIDIA(0):       HSyncEnd, HTotal :  928, 1080
(II) NVIDIA(0):       VRes, VSyncStart :  600,  600
(II) NVIDIA(0):       VSyncEnd, VTotal :  602,  625
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     Mode (800 x 600) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "800x600" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1200":
(II) NVIDIA(0):     1600 x 1200 @ 65 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 175.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
(II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
(II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (81.2 kHz) out of range
(WW) NVIDIA(0):     (31.000-80.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 65 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 87.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  832
(II) NVIDIA(0):       HSyncEnd, HTotal :  928, 1080
(II) NVIDIA(0):       VRes, VSyncStart :  600,  600
(II) NVIDIA(0):       VSyncEnd, VTotal :  602,  625
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (81.2 kHz) out of range
(WW) NVIDIA(0):     (31.000-80.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1200":
(II) NVIDIA(0):     1600 x 1200 @ 70 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 189.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
(II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
(II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (87.5 kHz) out of range
(WW) NVIDIA(0):     (31.000-80.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 70 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 94.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  832
(II) NVIDIA(0):       HSyncEnd, HTotal :  928, 1080
(II) NVIDIA(0):       VRes, VSyncStart :  600,  600
(II) NVIDIA(0):       VSyncEnd, VTotal :  602,  625
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (87.5 kHz) out of range
(WW) NVIDIA(0):     (31.000-80.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1200":
(II) NVIDIA(0):     1600 x 1200 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 202.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
(II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
(II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (93.8 kHz) out of range
(WW) NVIDIA(0):     (31.000-80.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 101.25 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  832
(II) NVIDIA(0):       HSyncEnd, HTotal :  928, 1080
(II) NVIDIA(0):       VRes, VSyncStart :  600,  600
(II) NVIDIA(0):       VSyncEnd, VTotal :  602,  625
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (93.8 kHz) out of range
(WW) NVIDIA(0):     (31.000-80.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1200":
(II) NVIDIA(0):     1600 x 1200 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 229.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
(II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
(II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (106.2 kHz) out of range
(WW) NVIDIA(0):     (31.000-80.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 114.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  832
(II) NVIDIA(0):       HSyncEnd, HTotal :  928, 1080
(II) NVIDIA(0):       VRes, VSyncStart :  600,  600
(II) NVIDIA(0):       VSyncEnd, VTotal :  602,  625
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (106.2 kHz) out of range
(WW) NVIDIA(0):     (31.000-80.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1792x1344":
(II) NVIDIA(0):     1792 x 1344 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 204.80 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1792, 1920
(II) NVIDIA(0):       HSyncEnd, HTotal : 2120, 2448
(II) NVIDIA(0):       VRes, VSyncStart : 1344, 1345
(II) NVIDIA(0):       VSyncEnd, VTotal : 1348, 1394
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (83.7 kHz) out of range
(WW) NVIDIA(0):     (31.000-80.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "896x672":
(II) NVIDIA(0):     896 x 672 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 102.40 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  896,  960
(II) NVIDIA(0):       HSyncEnd, HTotal : 1060, 1224
(II) NVIDIA(0):       VRes, VSyncStart :  672,  672
(II) NVIDIA(0):       VSyncEnd, VTotal :  674,  697
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (83.7 kHz) out of range
(WW) NVIDIA(0):     (31.000-80.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1792x1344":
(II) NVIDIA(0):     1792 x 1344 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 261.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1792, 1888
(II) NVIDIA(0):       HSyncEnd, HTotal : 2104, 2456
(II) NVIDIA(0):       VRes, VSyncStart : 1344, 1345
(II) NVIDIA(0):       VSyncEnd, VTotal : 1348, 1417
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (106.3 kHz) out of range
(WW) NVIDIA(0):     (31.000-80.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "896x672":
(II) NVIDIA(0):     896 x 672 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 130.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  896,  944
(II) NVIDIA(0):       HSyncEnd, HTotal : 1052, 1228
(II) NVIDIA(0):       VRes, VSyncStart :  672,  672
(II) NVIDIA(0):       VSyncEnd, VTotal :  674,  708
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (106.3 kHz) out of range
(WW) NVIDIA(0):     (31.000-80.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1856x1392":
(II) NVIDIA(0):     1856 x 1392 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 218.30 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1856, 1952
(II) NVIDIA(0):       HSyncEnd, HTotal : 2176, 2528
(II) NVIDIA(0):       VRes, VSyncStart : 1392, 1393
(II) NVIDIA(0):       VSyncEnd, VTotal : 1396, 1439
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (86.4 kHz) out of range
(WW) NVIDIA(0):     (31.000-80.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "928x696":
(II) NVIDIA(0):     928 x 696 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 109.15 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  928,  976
(II) NVIDIA(0):       HSyncEnd, HTotal : 1088, 1264
(II) NVIDIA(0):       VRes, VSyncStart :  696,  696
(II) NVIDIA(0):       VSyncEnd, VTotal :  698,  719
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (86.4 kHz) out of range
(WW) NVIDIA(0):     (31.000-80.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1856x1392":
(II) NVIDIA(0):     1856 x 1392 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 288.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1856, 1984
(II) NVIDIA(0):       HSyncEnd, HTotal : 2208, 2560
(II) NVIDIA(0):       VRes, VSyncStart : 1392, 1393
(II) NVIDIA(0):       VSyncEnd, VTotal : 1396, 1500
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (112.5 kHz) out of range
(WW) NVIDIA(0):     (31.000-80.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "928x696":
(II) NVIDIA(0):     928 x 696 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 144.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  928,  992
(II) NVIDIA(0):       HSyncEnd, HTotal : 1104, 1280
(II) NVIDIA(0):       VRes, VSyncStart :  696,  696
(II) NVIDIA(0):       VSyncEnd, VTotal :  698,  750
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (112.5 kHz) out of range
(WW) NVIDIA(0):     (31.000-80.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1920x1440":
(II) NVIDIA(0):     1920 x 1440 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 234.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1920, 2048
(II) NVIDIA(0):       HSyncEnd, HTotal : 2256, 2600
(II) NVIDIA(0):       VRes, VSyncStart : 1440, 1441
(II) NVIDIA(0):       VSyncEnd, VTotal : 1444, 1500
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (90.0 kHz) out of range
(WW) NVIDIA(0):     (31.000-80.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "960x720":
(II) NVIDIA(0):     960 x 720 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 117.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  960, 1024
(II) NVIDIA(0):       HSyncEnd, HTotal : 1128, 1300
(II) NVIDIA(0):       VRes, VSyncStart :  720,  720
(II) NVIDIA(0):       VSyncEnd, VTotal :  722,  750
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (90.0 kHz) out of range
(WW) NVIDIA(0):     (31.000-80.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1920x1440":
(II) NVIDIA(0):     1920 x 1440 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 297.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1920, 2064
(II) NVIDIA(0):       HSyncEnd, HTotal : 2288, 2640
(II) NVIDIA(0):       VRes, VSyncStart : 1440, 1441
(II) NVIDIA(0):       VSyncEnd, VTotal : 1444, 1500
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (112.5 kHz) out of range
(WW) NVIDIA(0):     (31.000-80.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "960x720":
(II) NVIDIA(0):     960 x 720 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 148.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  960, 1032
(II) NVIDIA(0):       HSyncEnd, HTotal : 1144, 1320
(II) NVIDIA(0):       VRes, VSyncStart :  720,  720
(II) NVIDIA(0):       VSyncEnd, VTotal :  722,  750
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (112.5 kHz) out of range
(WW) NVIDIA(0):     (31.000-80.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "832x624":
(II) NVIDIA(0):     832 x 624 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 57.28 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  832,  864
(II) NVIDIA(0):       HSyncEnd, HTotal :  928, 1152
(II) NVIDIA(0):       VRes, VSyncStart :  624,  625
(II) NVIDIA(0):       VSyncEnd, VTotal :  628,  667
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     Mode (832 x 624) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "832x624" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "416x312":
(II) NVIDIA(0):     416 x 312 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 28.64 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  416,  432
(II) NVIDIA(0):       HSyncEnd, HTotal :  464,  576
(II) NVIDIA(0):       VRes, VSyncStart :  312,  312
(II) NVIDIA(0):       VSyncEnd, VTotal :  314,  333
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "416x312": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1152x864":
(II) NVIDIA(0):     1152 x 864 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 81.62 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1152, 1216
(II) NVIDIA(0):       HSyncEnd, HTotal : 1336, 1520
(II) NVIDIA(0):       VRes, VSyncStart :  864,  865
(II) NVIDIA(0):       VSyncEnd, VTotal :  868,  895
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):     Mode (1152 x 864) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1152x864" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "576x432":
(II) NVIDIA(0):     576 x 432 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 40.81 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  576,  608
(II) NVIDIA(0):       HSyncEnd, HTotal :  668,  760
(II) NVIDIA(0):       VRes, VSyncStart :  432,  432
(II) NVIDIA(0):       VSyncEnd, VTotal :  434,  447
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "576x432": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1152x864":
(II) NVIDIA(0):     1152 x 864 @ 70 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 96.77 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1152, 1224
(II) NVIDIA(0):       HSyncEnd, HTotal : 1344, 1536
(II) NVIDIA(0):       VRes, VSyncStart :  864,  865
(II) NVIDIA(0):       VSyncEnd, VTotal :  868,  900
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):     Mode (1152 x 864) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1152x864" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "576x432":
(II) NVIDIA(0):     576 x 432 @ 70 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 48.38 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  576,  612
(II) NVIDIA(0):       HSyncEnd, HTotal :  672,  768
(II) NVIDIA(0):       VRes, VSyncStart :  432,  432
(II) NVIDIA(0):       VSyncEnd, VTotal :  434,  450
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "576x432": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1152x864":
(II) NVIDIA(0):     1152 x 864 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 104.99 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1152, 1224
(II) NVIDIA(0):       HSyncEnd, HTotal : 1352, 1552
(II) NVIDIA(0):       VRes, VSyncStart :  864,  865
(II) NVIDIA(0):       VSyncEnd, VTotal :  868,  902
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):     Mode (1152 x 864) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1152x864" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "576x432":
(II) NVIDIA(0):     576 x 432 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 52.49 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  576,  612
(II) NVIDIA(0):       HSyncEnd, HTotal :  676,  776
(II) NVIDIA(0):       VRes, VSyncStart :  432,  432
(II) NVIDIA(0):       VSyncEnd, VTotal :  434,  451
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "576x432": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1152x864":
(II) NVIDIA(0):     1152 x 864 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 119.65 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1152, 1224
(II) NVIDIA(0):       HSyncEnd, HTotal : 1352, 1552
(II) NVIDIA(0):       VRes, VSyncStart :  864,  865
(II) NVIDIA(0):       VSyncEnd, VTotal :  868,  907
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.0 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "576x432":
(II) NVIDIA(0):     576 x 432 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 59.83 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  576,  612
(II) NVIDIA(0):       HSyncEnd, HTotal :  676,  776
(II) NVIDIA(0):       VRes, VSyncStart :  432,  432
(II) NVIDIA(0):       VSyncEnd, VTotal :  434,  453
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.1 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1152x864":
(II) NVIDIA(0):     1152 x 864 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 121.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1152, 1216
(II) NVIDIA(0):       HSyncEnd, HTotal : 1344, 1568
(II) NVIDIA(0):       VRes, VSyncStart :  864,  865
(II) NVIDIA(0):       VSyncEnd, VTotal :  868,  911
(II) NVIDIA(0):       H/V Polarity     : +/-
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.1 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "576x432":
(II) NVIDIA(0):     576 x 432 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 60.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  576,  608
(II) NVIDIA(0):       HSyncEnd, HTotal :  672,  784
(II) NVIDIA(0):       VRes, VSyncStart :  432,  432
(II) NVIDIA(0):       VSyncEnd, VTotal :  434,  455
(II) NVIDIA(0):       H/V Polarity     : +/-
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.2 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1152x864":
(II) NVIDIA(0):     1152 x 864 @ 100 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 143.47 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1152, 1232
(II) NVIDIA(0):       HSyncEnd, HTotal : 1360, 1568
(II) NVIDIA(0):       VRes, VSyncStart :  864,  865
(II) NVIDIA(0):       VSyncEnd, VTotal :  868,  915
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (91.5 kHz) out of range
(WW) NVIDIA(0):     (31.000-80.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "576x432":
(II) NVIDIA(0):     576 x 432 @ 100 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 71.73 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  576,  616
(II) NVIDIA(0):       HSyncEnd, HTotal :  680,  784
(II) NVIDIA(0):       VRes, VSyncStart :  432,  432
(II) NVIDIA(0):       VSyncEnd, VTotal :  434,  457
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (91.5 kHz) out of range
(WW) NVIDIA(0):     (31.000-80.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1360x768":
(II) NVIDIA(0):     1360 x 768 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 72.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1360, 1408
(II) NVIDIA(0):       HSyncEnd, HTotal : 1440, 1520
(II) NVIDIA(0):       VRes, VSyncStart :  768,  771
(II) NVIDIA(0):       VSyncEnd, VTotal :  781,  790
(II) NVIDIA(0):       H/V Polarity     : +/-
(II) NVIDIA(0):     Mode (1360 x 768) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1360x768" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "680x384":
(II) NVIDIA(0):     680 x 384 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 36.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  680,  704
(II) NVIDIA(0):       HSyncEnd, HTotal :  720,  760
(II) NVIDIA(0):       VRes, VSyncStart :  384,  385
(II) NVIDIA(0):       VSyncEnd, VTotal :  390,  395
(II) NVIDIA(0):       H/V Polarity     : +/-
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     Mode (680 x 384) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "680x384" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1360x768":
(II) NVIDIA(0):     1360 x 768 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 84.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1360, 1432
(II) NVIDIA(0):       HSyncEnd, HTotal : 1568, 1776
(II) NVIDIA(0):       VRes, VSyncStart :  768,  771
(II) NVIDIA(0):       VSyncEnd, VTotal :  781,  798
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):     Mode (1360 x 768) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1360x768" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "680x384":
(II) NVIDIA(0):     680 x 384 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 42.38 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  680,  716
(II) NVIDIA(0):       HSyncEnd, HTotal :  784,  888
(II) NVIDIA(0):       VRes, VSyncStart :  384,  385
(II) NVIDIA(0):       VSyncEnd, VTotal :  390,  399
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     Mode (680 x 384) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "680x384" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1400x1050":
(II) NVIDIA(0):     1400 x 1050 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 122.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1400, 1488
(II) NVIDIA(0):       HSyncEnd, HTotal : 1640, 1880
(II) NVIDIA(0):       VRes, VSyncStart : 1050, 1052
(II) NVIDIA(0):       VSyncEnd, VTotal : 1064, 1082
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode (1400 x 1050) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1400x1050" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "700x525":
(II) NVIDIA(0):     700 x 525 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 61.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  700,  744
(II) NVIDIA(0):       HSyncEnd, HTotal :  820,  940
(II) NVIDIA(0):       VRes, VSyncStart :  525,  526
(II) NVIDIA(0):       VSyncEnd, VTotal :  532,  541
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     Mode (700 x 525) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Mode is rejected: Mode's width (700) is not a multiple of
(WW) NVIDIA(0):     8.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1400x1050":
(II) NVIDIA(0):     1400 x 1050 @ 70 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 145.06 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1400, 1496
(II) NVIDIA(0):       HSyncEnd, HTotal : 1648, 1896
(II) NVIDIA(0):       VRes, VSyncStart : 1050, 1051
(II) NVIDIA(0):       VSyncEnd, VTotal : 1054, 1093
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):     Mode (1400 x 1050) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1400x1050" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "700x525":
(II) NVIDIA(0):     700 x 525 @ 70 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 72.53 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  700,  748
(II) NVIDIA(0):       HSyncEnd, HTotal :  824,  948
(II) NVIDIA(0):       VRes, VSyncStart :  525,  525
(II) NVIDIA(0):       VSyncEnd, VTotal :  527,  546
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     Mode (700 x 525) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Mode is rejected: Mode's width (700) is not a multiple of
(WW) NVIDIA(0):     8.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1400x1050":
(II) NVIDIA(0):     1400 x 1050 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 155.80 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1400, 1464
(II) NVIDIA(0):       HSyncEnd, HTotal : 1784, 1912
(II) NVIDIA(0):       VRes, VSyncStart : 1050, 1052
(II) NVIDIA(0):       VSyncEnd, VTotal : 1064, 1090
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (81.5 kHz) out of range
(WW) NVIDIA(0):     (31.000-80.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "700x525":
(II) NVIDIA(0):     700 x 525 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 77.90 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  700,  732
(II) NVIDIA(0):       HSyncEnd, HTotal :  892,  956
(II) NVIDIA(0):       VRes, VSyncStart :  525,  526
(II) NVIDIA(0):       VSyncEnd, VTotal :  532,  545
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (81.5 kHz) out of range
(WW) NVIDIA(0):     (31.000-80.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1400x1050":
(II) NVIDIA(0):     1400 x 1050 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 179.26 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1400, 1504
(II) NVIDIA(0):       HSyncEnd, HTotal : 1656, 1912
(II) NVIDIA(0):       VRes, VSyncStart : 1050, 1051
(II) NVIDIA(0):       VSyncEnd, VTotal : 1054, 1103
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (93.8 kHz) out of range
(WW) NVIDIA(0):     (31.000-80.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "700x525":
(II) NVIDIA(0):     700 x 525 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 89.63 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  700,  752
(II) NVIDIA(0):       HSyncEnd, HTotal :  828,  956
(II) NVIDIA(0):       VRes, VSyncStart :  525,  525
(II) NVIDIA(0):       VSyncEnd, VTotal :  527,  551
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (93.8 kHz) out of range
(WW) NVIDIA(0):     (31.000-80.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1440x900":
(II) NVIDIA(0):     1440 x 900 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 106.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1440, 1520
(II) NVIDIA(0):       HSyncEnd, HTotal : 1672, 1904
(II) NVIDIA(0):       VRes, VSyncStart :  900,  903
(II) NVIDIA(0):       VSyncEnd, VTotal :  909,  934
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):     Mode (1440 x 900) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1440x900" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "720x450":
(II) NVIDIA(0):     720 x 450 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 53.25 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  720,  760
(II) NVIDIA(0):       HSyncEnd, HTotal :  836,  952
(II) NVIDIA(0):       VRes, VSyncStart :  450,  451
(II) NVIDIA(0):       VSyncEnd, VTotal :  454,  467
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     Mode (720 x 450) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "720x450" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1024":
(II) NVIDIA(0):     1600 x 1024 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 103.12 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1600
(II) NVIDIA(0):       HSyncEnd, HTotal : 1656, 1664
(II) NVIDIA(0):       VRes, VSyncStart : 1024, 1024
(II) NVIDIA(0):       VSyncEnd, VTotal : 1029, 1030
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode (1600 x 1024) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1600x1024" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x512":
(II) NVIDIA(0):     800 x 512 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 51.56 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  800
(II) NVIDIA(0):       HSyncEnd, HTotal :  828,  832
(II) NVIDIA(0):       VRes, VSyncStart :  512,  512
(II) NVIDIA(0):       VSyncEnd, VTotal :  514,  515
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     Mode (800 x 512) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "800x512" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1680x1050":
(II) NVIDIA(0):     1680 x 1050 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 119.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1680, 1728
(II) NVIDIA(0):       HSyncEnd, HTotal : 1760, 1840
(II) NVIDIA(0):       VRes, VSyncStart : 1050, 1053
(II) NVIDIA(0):       VSyncEnd, VTotal : 1059, 1080
(II) NVIDIA(0):       H/V Polarity     : +/-
(II) NVIDIA(0):     Mode (1680 x 1050) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1680x1050" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "840x525":
(II) NVIDIA(0):     840 x 525 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 59.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  840,  864
(II) NVIDIA(0):       HSyncEnd, HTotal :  880,  920
(II) NVIDIA(0):       VRes, VSyncStart :  525,  526
(II) NVIDIA(0):       VSyncEnd, VTotal :  529,  540
(II) NVIDIA(0):       H/V Polarity     : +/-
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     Mode (840 x 525) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "840x525" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1680x1050":
(II) NVIDIA(0):     1680 x 1050 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 146.25 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1680, 1784
(II) NVIDIA(0):       HSyncEnd, HTotal : 1960, 2240
(II) NVIDIA(0):       VRes, VSyncStart : 1050, 1053
(II) NVIDIA(0):       VSyncEnd, VTotal : 1059, 1089
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):     Mode (1680 x 1050) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1680x1050" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "840x525":
(II) NVIDIA(0):     840 x 525 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 73.12 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  840,  892
(II) NVIDIA(0):       HSyncEnd, HTotal :  980, 1120
(II) NVIDIA(0):       VRes, VSyncStart :  525,  526
(II) NVIDIA(0):       VSyncEnd, VTotal :  529,  544
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     Mode (840 x 525) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "840x525" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1680x1050":
(II) NVIDIA(0):     1680 x 1050 @ 70 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 174.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1680, 1800
(II) NVIDIA(0):       HSyncEnd, HTotal : 1976, 2272
(II) NVIDIA(0):       VRes, VSyncStart : 1050, 1053
(II) NVIDIA(0):       VSyncEnd, VTotal : 1059, 1096
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):     Mode (1680 x 1050) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1680x1050" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "840x525":
(II) NVIDIA(0):     840 x 525 @ 70 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 87.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  840,  900
(II) NVIDIA(0):       HSyncEnd, HTotal :  988, 1136
(II) NVIDIA(0):       VRes, VSyncStart :  525,  526
(II) NVIDIA(0):       VSyncEnd, VTotal :  529,  548
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     Mode (840 x 525) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "840x525" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1680x1050":
(II) NVIDIA(0):     1680 x 1050 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 187.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1680, 1800
(II) NVIDIA(0):       HSyncEnd, HTotal : 1976, 2272
(II) NVIDIA(0):       VRes, VSyncStart : 1050, 1053
(II) NVIDIA(0):       VSyncEnd, VTotal : 1059, 1099
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (82.3 kHz) out of range
(WW) NVIDIA(0):     (31.000-80.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "840x525":
(II) NVIDIA(0):     840 x 525 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 93.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  840,  900
(II) NVIDIA(0):       HSyncEnd, HTotal :  988, 1136
(II) NVIDIA(0):       VRes, VSyncStart :  525,  526
(II) NVIDIA(0):       VSyncEnd, VTotal :  529,  549
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (82.3 kHz) out of range
(WW) NVIDIA(0):     (31.000-80.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1680x1050":
(II) NVIDIA(0):     1680 x 1050 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 214.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1680, 1808
(II) NVIDIA(0):       HSyncEnd, HTotal : 1984, 2288
(II) NVIDIA(0):       VRes, VSyncStart : 1050, 1053
(II) NVIDIA(0):       VSyncEnd, VTotal : 1059, 1105
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (93.9 kHz) out of range
(WW) NVIDIA(0):     (31.000-80.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "840x525":
(II) NVIDIA(0):     840 x 525 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 107.38 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  840,  904
(II) NVIDIA(0):       HSyncEnd, HTotal :  992, 1144
(II) NVIDIA(0):       VRes, VSyncStart :  525,  526
(II) NVIDIA(0):       VSyncEnd, VTotal :  529,  552
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (93.9 kHz) out of range
(WW) NVIDIA(0):     (31.000-80.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1920x1080":
(II) NVIDIA(0):     1920 x 1080 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 138.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1920, 1968
(II) NVIDIA(0):       HSyncEnd, HTotal : 2000, 2080
(II) NVIDIA(0):       VRes, VSyncStart : 1080, 1083
(II) NVIDIA(0):       VSyncEnd, VTotal : 1088, 1111
(II) NVIDIA(0):       H/V Polarity     : +/-
(II) NVIDIA(0):     Mode (1920 x 1080) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1920x1080" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "960x540":
(II) NVIDIA(0):     960 x 540 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 69.25 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  960,  984
(II) NVIDIA(0):       HSyncEnd, HTotal : 1000, 1040
(II) NVIDIA(0):       VRes, VSyncStart :  540,  541
(II) NVIDIA(0):       VSyncEnd, VTotal :  544,  555
(II) NVIDIA(0):       H/V Polarity     : +/-
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     Mode (960 x 540) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "960x540" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1920x1200":
(II) NVIDIA(0):     1920 x 1200 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 154.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1920, 1968
(II) NVIDIA(0):       HSyncEnd, HTotal : 2000, 2080
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1203
(II) NVIDIA(0):       VSyncEnd, VTotal : 1209, 1235
(II) NVIDIA(0):       H/V Polarity     : +/-
(II) NVIDIA(0):     Mode (1920 x 1200) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1920x1200" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "960x600":
(II) NVIDIA(0):     960 x 600 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 77.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  960,  984
(II) NVIDIA(0):       HSyncEnd, HTotal : 1000, 1040
(II) NVIDIA(0):       VRes, VSyncStart :  600,  601
(II) NVIDIA(0):       VSyncEnd, VTotal :  604,  617
(II) NVIDIA(0):       H/V Polarity     : +/-
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     Mode (960 x 600) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "960x600" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1920x1440":
(II) NVIDIA(0):     1920 x 1440 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 341.35 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1920, 2072
(II) NVIDIA(0):       HSyncEnd, HTotal : 2288, 2656
(II) NVIDIA(0):       VRes, VSyncStart : 1440, 1441
(II) NVIDIA(0):       VSyncEnd, VTotal : 1444, 1512
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (341.4 MHz) too high for
(WW) NVIDIA(0):     Display Device (Max: 330.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "960x720":
(II) NVIDIA(0):     960 x 720 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 170.68 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  960, 1036
(II) NVIDIA(0):       HSyncEnd, HTotal : 1144, 1328
(II) NVIDIA(0):       VRes, VSyncStart :  720,  720
(II) NVIDIA(0):       VSyncEnd, VTotal :  722,  756
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (128.5 kHz) out of range
(WW) NVIDIA(0):     (31.000-80.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "2048x1536":
(II) NVIDIA(0):     2048 x 1536 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 266.95 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 2048, 2200
(II) NVIDIA(0):       HSyncEnd, HTotal : 2424, 2800
(II) NVIDIA(0):       VRes, VSyncStart : 1536, 1537
(II) NVIDIA(0):       VSyncEnd, VTotal : 1540, 1589
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (95.3 kHz) out of range
(WW) NVIDIA(0):     (31.000-80.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 133.47 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1100
(II) NVIDIA(0):       HSyncEnd, HTotal : 1212, 1400
(II) NVIDIA(0):       VRes, VSyncStart :  768,  768
(II) NVIDIA(0):       VSyncEnd, VTotal :  770,  794
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (95.3 kHz) out of range
(WW) NVIDIA(0):     (31.000-80.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "2048x1536":
(II) NVIDIA(0):     2048 x 1536 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 340.48 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 2048, 2216
(II) NVIDIA(0):       HSyncEnd, HTotal : 2440, 2832
(II) NVIDIA(0):       VRes, VSyncStart : 1536, 1537
(II) NVIDIA(0):       VSyncEnd, VTotal : 1540, 1603
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (340.5 MHz) too high for
(WW) NVIDIA(0):     Display Device (Max: 330.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 170.24 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1108
(II) NVIDIA(0):       HSyncEnd, HTotal : 1220, 1416
(II) NVIDIA(0):       VRes, VSyncStart :  768,  768
(II) NVIDIA(0):       VSyncEnd, VTotal :  770,  801
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (120.2 kHz) out of range
(WW) NVIDIA(0):     (31.000-80.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "2048x1536":
(II) NVIDIA(0):     2048 x 1536 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 388.04 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 2048, 2216
(II) NVIDIA(0):       HSyncEnd, HTotal : 2440, 2832
(II) NVIDIA(0):       VRes, VSyncStart : 1536, 1537
(II) NVIDIA(0):       VSyncEnd, VTotal : 1540, 1612
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (388.0 MHz) too high for
(WW) NVIDIA(0):     Display Device (Max: 330.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 194.02 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1108
(II) NVIDIA(0):       HSyncEnd, HTotal : 1220, 1416
(II) NVIDIA(0):       VRes, VSyncStart :  768,  768
(II) NVIDIA(0):       VSyncEnd, VTotal :  770,  806
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (137.0 kHz) out of range
(WW) NVIDIA(0):     (31.000-80.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x350":
(II) NVIDIA(0):     640 x 350 @ 85 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  672
(II) NVIDIA(0):       HSyncEnd, HTotal :  736,  832
(II) NVIDIA(0):       VRes, VSyncStart :  350,  382
(II) NVIDIA(0):       VSyncEnd, VTotal :  385,  445
(II) NVIDIA(0):       H/V Polarity     : +/-
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.1 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x400":
(II) NVIDIA(0):     640 x 400 @ 85 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  672
(II) NVIDIA(0):       HSyncEnd, HTotal :  736,  832
(II) NVIDIA(0):       VRes, VSyncStart :  400,  401
(II) NVIDIA(0):       VSyncEnd, VTotal :  404,  445
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.1 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "720x400":
(II) NVIDIA(0):     720 x 400 @ 85 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 35.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  720,  756
(II) NVIDIA(0):       HSyncEnd, HTotal :  828,  936
(II) NVIDIA(0):       VRes, VSyncStart :  400,  401
(II) NVIDIA(0):       VSyncEnd, VTotal :  404,  446
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.0 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 60 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 25.18 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  656
(II) NVIDIA(0):       HSyncEnd, HTotal :  752,  800
(II) NVIDIA(0):       VRes, VSyncStart :  480,  490
(II) NVIDIA(0):       VSyncEnd, VTotal :  492,  525
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     BestFit Backend for "640x480": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 73 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  664
(II) NVIDIA(0):       HSyncEnd, HTotal :  704,  832
(II) NVIDIA(0):       VRes, VSyncStart :  480,  489
(II) NVIDIA(0):       VSyncEnd, VTotal :  492,  520
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     BestFit Backend for "640x480": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 75 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  656
(II) NVIDIA(0):       HSyncEnd, HTotal :  720,  840
(II) NVIDIA(0):       VRes, VSyncStart :  480,  481
(II) NVIDIA(0):       VSyncEnd, VTotal :  484,  500
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     BestFit Backend for "640x480": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 85 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 36.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  696
(II) NVIDIA(0):       HSyncEnd, HTotal :  752,  832
(II) NVIDIA(0):       VRes, VSyncStart :  480,  481
(II) NVIDIA(0):       VSyncEnd, VTotal :  484,  509
(II) NVIDIA(0):       H/V Polarity     : -/-
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.0 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 56 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 36.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  824
(II) NVIDIA(0):       HSyncEnd, HTotal :  896, 1024
(II) NVIDIA(0):       VRes, VSyncStart :  600,  601
(II) NVIDIA(0):       VSyncEnd, VTotal :  603,  625
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode (800 x 600) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "800x600" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 60 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 40.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  840
(II) NVIDIA(0):       HSyncEnd, HTotal :  968, 1056
(II) NVIDIA(0):       VRes, VSyncStart :  600,  601
(II) NVIDIA(0):       VSyncEnd, VTotal :  605,  628
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode (800 x 600) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "800x600" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 72 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 50.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  856
(II) NVIDIA(0):       HSyncEnd, HTotal :  976, 1040
(II) NVIDIA(0):       VRes, VSyncStart :  600,  637
(II) NVIDIA(0):       VSyncEnd, VTotal :  643,  666
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode (800 x 600) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "800x600" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 75 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 49.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  816
(II) NVIDIA(0):       HSyncEnd, HTotal :  896, 1056
(II) NVIDIA(0):       VRes, VSyncStart :  600,  601
(II) NVIDIA(0):       VSyncEnd, VTotal :  604,  625
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode (800 x 600) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "800x600" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 85 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 56.30 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  832
(II) NVIDIA(0):       HSyncEnd, HTotal :  896, 1048
(II) NVIDIA(0):       VRes, VSyncStart :  600,  601
(II) NVIDIA(0):       VSyncEnd, VTotal :  604,  631
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.1 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 87 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 44.90 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1032
(II) NVIDIA(0):       HSyncEnd, HTotal : 1208, 1264
(II) NVIDIA(0):       VRes, VSyncStart :  768,  768
(II) NVIDIA(0):       VSyncEnd, VTotal :  776,  817
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : Interlace
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (87.0 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 60 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 65.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1048
(II) NVIDIA(0):       HSyncEnd, HTotal : 1184, 1344
(II) NVIDIA(0):       VRes, VSyncStart :  768,  771
(II) NVIDIA(0):       VSyncEnd, VTotal :  777,  806
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     Mode (1024 x 768) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1024x768" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 70 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 75.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1048
(II) NVIDIA(0):       HSyncEnd, HTotal : 1184, 1328
(II) NVIDIA(0):       VRes, VSyncStart :  768,  771
(II) NVIDIA(0):       VSyncEnd, VTotal :  777,  806
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     Mode (1024 x 768) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1024x768" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 75 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 78.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1040
(II) NVIDIA(0):       HSyncEnd, HTotal : 1136, 1312
(II) NVIDIA(0):       VRes, VSyncStart :  768,  769
(II) NVIDIA(0):       VSyncEnd, VTotal :  772,  800
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode (1024 x 768) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1024x768" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 85 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 94.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1072
(II) NVIDIA(0):       HSyncEnd, HTotal : 1168, 1376
(II) NVIDIA(0):       VRes, VSyncStart :  768,  769
(II) NVIDIA(0):       VSyncEnd, VTotal :  772,  808
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.0 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1152x864":
(II) NVIDIA(0):     1152 x 864 @ 75 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 108.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1152, 1216
(II) NVIDIA(0):       HSyncEnd, HTotal : 1344, 1600
(II) NVIDIA(0):       VRes, VSyncStart :  864,  865
(II) NVIDIA(0):       VSyncEnd, VTotal :  868,  900
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode (1152 x 864) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1152x864" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x960":
(II) NVIDIA(0):     1280 x 960 @ 60 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 108.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1376
(II) NVIDIA(0):       HSyncEnd, HTotal : 1488, 1800
(II) NVIDIA(0):       VRes, VSyncStart :  960,  961
(II) NVIDIA(0):       VSyncEnd, VTotal :  964, 1000
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode (1280 x 960) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1280x960" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x960":
(II) NVIDIA(0):     1280 x 960 @ 85 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 148.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1344
(II) NVIDIA(0):       HSyncEnd, HTotal : 1504, 1728
(II) NVIDIA(0):       VRes, VSyncStart :  960,  961
(II) NVIDIA(0):       VSyncEnd, VTotal :  964, 1011
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (85.9 kHz) out of range
(WW) NVIDIA(0):     (31.000-80.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x1024":
(II) NVIDIA(0):     1280 x 1024 @ 60 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 108.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1328
(II) NVIDIA(0):       HSyncEnd, HTotal : 1440, 1688
(II) NVIDIA(0):       VRes, VSyncStart : 1024, 1025
(II) NVIDIA(0):       VSyncEnd, VTotal : 1028, 1066
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode (1280 x 1024) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1280x1024" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x1024":
(II) NVIDIA(0):     1280 x 1024 @ 75 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 135.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1296
(II) NVIDIA(0):       HSyncEnd, HTotal : 1440, 1688
(II) NVIDIA(0):       VRes, VSyncStart : 1024, 1025
(II) NVIDIA(0):       VSyncEnd, VTotal : 1028, 1066
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode (1280 x 1024) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1280x1024" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x1024":
(II) NVIDIA(0):     1280 x 1024 @ 85 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 157.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1344
(II) NVIDIA(0):       HSyncEnd, HTotal : 1504, 1728
(II) NVIDIA(0):       VRes, VSyncStart : 1024, 1025
(II) NVIDIA(0):       VSyncEnd, VTotal : 1028, 1072
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (91.1 kHz) out of range
(WW) NVIDIA(0):     (31.000-80.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1200":
(II) NVIDIA(0):     1600 x 1200 @ 60 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 162.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
(II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
(II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode (1600 x 1200) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "1600x1200" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1200":
(II) NVIDIA(0):     1600 x 1200 @ 65 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 175.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
(II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
(II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (81.2 kHz) out of range
(WW) NVIDIA(0):     (31.000-80.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1200":
(II) NVIDIA(0):     1600 x 1200 @ 70 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 189.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
(II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
(II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (87.5 kHz) out of range
(WW) NVIDIA(0):     (31.000-80.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1200":
(II) NVIDIA(0):     1600 x 1200 @ 75 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 202.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
(II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
(II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (93.8 kHz) out of range
(WW) NVIDIA(0):     (31.000-80.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1200":
(II) NVIDIA(0):     1600 x 1200 @ 85 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 229.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
(II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
(II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (106.2 kHz) out of range
(WW) NVIDIA(0):     (31.000-80.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1792x1344":
(II) NVIDIA(0):     1792 x 1344 @ 60 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 204.80 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1792, 1920
(II) NVIDIA(0):       HSyncEnd, HTotal : 2120, 2448
(II) NVIDIA(0):       VRes, VSyncStart : 1344, 1345
(II) NVIDIA(0):       VSyncEnd, VTotal : 1348, 1394
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (83.7 kHz) out of range
(WW) NVIDIA(0):     (31.000-80.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1792x1344":
(II) NVIDIA(0):     1792 x 1344 @ 75 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 261.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1792, 1888
(II) NVIDIA(0):       HSyncEnd, HTotal : 2104, 2456
(II) NVIDIA(0):       VRes, VSyncStart : 1344, 1345
(II) NVIDIA(0):       VSyncEnd, VTotal : 1348, 1417
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (106.3 kHz) out of range
(WW) NVIDIA(0):     (31.000-80.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1856x1392":
(II) NVIDIA(0):     1856 x 1392 @ 60 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 218.30 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1856, 1952
(II) NVIDIA(0):       HSyncEnd, HTotal : 2176, 2528
(II) NVIDIA(0):       VRes, VSyncStart : 1392, 1393
(II) NVIDIA(0):       VSyncEnd, VTotal : 1396, 1439
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (86.4 kHz) out of range
(WW) NVIDIA(0):     (31.000-80.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1856x1392":
(II) NVIDIA(0):     1856 x 1392 @ 75 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 288.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1856, 1984
(II) NVIDIA(0):       HSyncEnd, HTotal : 2208, 2560
(II) NVIDIA(0):       VRes, VSyncStart : 1392, 1393
(II) NVIDIA(0):       VSyncEnd, VTotal : 1396, 1500
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (112.5 kHz) out of range
(WW) NVIDIA(0):     (31.000-80.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1920x1440":
(II) NVIDIA(0):     1920 x 1440 @ 60 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 234.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1920, 2048
(II) NVIDIA(0):       HSyncEnd, HTotal : 2256, 2600
(II) NVIDIA(0):       VRes, VSyncStart : 1440, 1441
(II) NVIDIA(0):       VSyncEnd, VTotal : 1444, 1500
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (90.0 kHz) out of range
(WW) NVIDIA(0):     (31.000-80.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1920x1440":
(II) NVIDIA(0):     1920 x 1440 @ 75 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 297.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1920, 2064
(II) NVIDIA(0):       HSyncEnd, HTotal : 2288, 2640
(II) NVIDIA(0):       VRes, VSyncStart : 1440, 1441
(II) NVIDIA(0):       VSyncEnd, VTotal : 1444, 1500
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (112.5 kHz) out of range
(WW) NVIDIA(0):     (31.000-80.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0): --- Done building ModePool for DFP-0 ---
(II) NVIDIA(0): 
(II) NVIDIA(0): 
(II) NVIDIA(0): --- Modes in ModePool for DFP-0 ---
(II) NVIDIA(0): "nvidia-auto-select" :  640 x  480 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "640x480"            :  640 x  480 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "640x480d60"         :  640 x  480 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "640x480_75"         :  640 x  480 @  75.0 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "640x480_73"         :  640 x  480 @  72.8 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "640x480_60"         :  640 x  480 @  59.9 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "576x432"            :  576 x  432 @  75.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "576x432d75"         :  576 x  432 @  75.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "576x432d75_0"       :  576 x  432 @  75.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "576x432d70"         :  576 x  432 @  70.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "576x432d60"         :  576 x  432 @  60.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "512x384"            :  512 x  384 @  75.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "512x384d75"         :  512 x  384 @  75.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "512x384d70"         :  512 x  384 @  70.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "512x384d60"         :  512 x  384 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "416x312"            :  416 x  312 @  74.7 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "416x312d75"         :  416 x  312 @  74.7 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "400x300"            :  400 x  300 @  75.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "400x300d75"         :  400 x  300 @  75.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "400x300d72"         :  400 x  300 @  72.2 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "400x300d60"         :  400 x  300 @  60.3 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "400x300d56"         :  400 x  300 @  56.3 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "320x240"            :  320 x  240 @  75.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "320x240d75"         :  320 x  240 @  75.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "320x240d73"         :  320 x  240 @  72.8 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "320x240d60"         :  320 x  240 @  60.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): --- End of ModePool for DFP-0: ---
(II) NVIDIA(0): 
(II) NVIDIA(0): Assigned Display Device: DFP-0
(==) NVIDIA(0): 
(==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) NVIDIA(0):     will be used as the requested mode.
(==) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0): Virtual screen size determined to be 640 x 480
(II) NVIDIA(0): 
(II) NVIDIA(0): Implicitly adding the following modes to X Screen 0 (these
(II) NVIDIA(0):     will be available via XRandR and XF86VidMode):
(II) NVIDIA(0): 
(II) NVIDIA(0): "640x480_75"   :  640 x  480 @  75.0 Hz 
(II) NVIDIA(0): "640x480_73"   :  640 x  480 @  72.8 Hz 
(II) NVIDIA(0): "640x480_60"   :  640 x  480 @  59.9 Hz 
(II) NVIDIA(0): "576x432"      :  576 x  432 @  75.0 Hz DoubleScan 
(II) NVIDIA(0): "576x432d75_0" :  576 x  432 @  75.0 Hz DoubleScan 
(II) NVIDIA(0): "576x432d70"   :  576 x  432 @  70.0 Hz DoubleScan 
(II) NVIDIA(0): "576x432d60"   :  576 x  432 @  60.1 Hz DoubleScan 
(II) NVIDIA(0): "512x384"      :  512 x  384 @  75.0 Hz DoubleScan 
(II) NVIDIA(0): "512x384d70"   :  512 x  384 @  70.1 Hz DoubleScan 
(II) NVIDIA(0): "512x384d60"   :  512 x  384 @  60.0 Hz DoubleScan 
(II) NVIDIA(0): "416x312"      :  416 x  312 @  74.7 Hz DoubleScan 
(II) NVIDIA(0): "400x300"      :  400 x  300 @  75.1 Hz DoubleScan 
(II) NVIDIA(0): "400x300d72"   :  400 x  300 @  72.2 Hz DoubleScan 
(II) NVIDIA(0): "400x300d60"   :  400 x  300 @  60.3 Hz DoubleScan 
(II) NVIDIA(0): "400x300d56"   :  400 x  300 @  56.3 Hz DoubleScan 
(II) NVIDIA(0): "320x240"      :  320 x  240 @  75.0 Hz DoubleScan 
(II) NVIDIA(0): "320x240d73"   :  320 x  240 @  72.8 Hz DoubleScan 
(II) NVIDIA(0): "320x240d60"   :  320 x  240 @  60.1 Hz DoubleScan 
(II) NVIDIA(0): 
(WW) NVIDIA(0): Unable to get display device DFP-0's EDID; cannot compute DPI
(WW) NVIDIA(0):     from DFP-0's EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) NVIDIA(0): Built-in logo is bigger than the screen.
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing extension GLX
(II) config/hal: Adding input device Macintosh mouse button emulation
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) config/hal: Adding input device Microsoft Comfort Curve Keyboard 2000
(**) Microsoft Comfort Curve Keyboard 2000: always reports core events
(**) Microsoft Comfort Curve Keyboard 2000: Device: "/dev/input/event5"
(II) Microsoft Comfort Curve Keyboard 2000: Found 1 mouse buttons
(II) Microsoft Comfort Curve Keyboard 2000: Found keys
(II) Microsoft Comfort Curve Keyboard 2000: Configuring as keyboard
(**) Microsoft Comfort Curve Keyboard 2000: YAxisMapping: buttons 4 and 5
(**) Microsoft Comfort Curve Keyboard 2000: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Microsoft Comfort Curve Keyboard 2000" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Microsoft Comfort Curve Keyboard 2000: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Microsoft Comfort Curve Keyboard 2000: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Microsoft Comfort Curve Keyboard 2000: xkb_layout: "us"
(II) config/hal: Adding input device Microsoft Comfort Curve Keyboard 2000
(**) Microsoft Comfort Curve Keyboard 2000: always reports core events
(**) Microsoft Comfort Curve Keyboard 2000: Device: "/dev/input/event4"
(II) Microsoft Comfort Curve Keyboard 2000: Found keys
(II) Microsoft Comfort Curve Keyboard 2000: Configuring as keyboard
(II) XINPUT: Adding extended input device "Microsoft Comfort Curve Keyboard 2000" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Microsoft Comfort Curve Keyboard 2000: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Microsoft Comfort Curve Keyboard 2000: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Microsoft Comfort Curve Keyboard 2000: xkb_layout: "us"
(II) config/hal: Adding input device Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): always reports core events
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Device: "/dev/input/event7"
(II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found 3 mouse buttons
(II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found x and y relative axes
(II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Configuring as mouse
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): YAxisMapping: buttons 4 and 5
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)" (type: MOUSE)
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): (accel) keeping acceleration scheme 1
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): (accel) filter chain progression: 2.00
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): (accel) filter stage 0: 20.00 ms
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): (accel) set acceleration profile 0
```

Thanks for your help.

There is so much muck in these files that I can't tell what it's using and what it isn't.

---

### Post by P4man on 2009-09-04
you still have

>  NVIDIA(0):     Mode is rejected: **VertRefresh (85.3 Hz) **out of range

in your logs.

Are you sure you put

```
 **VertRefresh**     50-75
```

in your xorg.conf as catkiller requested?

---

### Post by CatKiller on 2009-09-04
> **P4man said:**
> Are you sure you put

```
 **VertRefresh**     50-75
```in your xorg.conf as catkiller requested?

It's there.

```
(II) NVIDIA(0): Frequency information for DFP-0:
(II) NVIDIA(0):   HorizSync   : 24.000-82.000 kHz
(II) NVIDIA(0):   VertRefresh : 50.000-75.000 Hz
(II) NVIDIA(0):     (HorizSync from HorizSync in X Config Monitor section)
(II) NVIDIA(0):     (VertRefresh from VertRefresh in X Config Monitor
(II) NVIDIA(0):     section)
```Just having a look through the logs now.

EDIT: That's a bit weird;
```
(II) NVIDIA(0):     Mode (800 x 600) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 640 x 480); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
```How does it know what the native resolution should be?

EDIT 2: OK, so X has decided that the monitor's native resolution is 640×480 for some reason, and so it's rejecting all the higher modes since obviously you can't display a resolution that's higher than the native resolution. Out of interest, does it work if you use a VGA connection instead?

Anyway, you can disable the does-this-mode-scale-properly-to-the-native-resolution check by putting ```
        Option          "ModeValidation"     "NoDFPNativeResolutionCheck"
``` (I think) in the Device section.

The logs don't say which mode it is that the driver has picked that your monitor doesn't like. It just says 

```
 (II) NVIDIA(0): Setting mode "nvidia-auto-select"
``` which isn't helpful, really. You can specify a mode, though, which will hopefully over-ride whatever the nvidia driver has decided it should be, by putting a Display SubSection in the Monitor section;

```
        SubSection "Display"
                Depth           24
                Modes           "1680x1050"
        EndSubSection
```You can put different modes in as well, separated by a space, and you can specify different modes for different colour depths, but I figured this was the mode you were after.

Hopefully this will help.

EDIT 3: Once you've got the right resolution, if you find that the text is a weird size, it may be because of this

```
(WW) NVIDIA(0): Unable to get display device DFP-0's EDID; cannot compute DPI
(WW) NVIDIA(0):     from DFP-0's EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
```You can use DisplaySize in the Monitor section to give X something better to work with to calculate the DPI for your display.

```
        DisplaySize     433 271
``` The numbers are the width and height of the visible area of your display in mm.

---

### Post by tsali on 2009-09-05
> **P4man said:**
> you still have



in your logs.

Are you sure you put

```
 **VertRefresh**     50-75
```

in your xorg.conf as catkiller requested?

Absolutely positive. You will see that referenced in the early section of the logs.

---

### Post by tsali on 2009-09-05
Ok...that didn't work...Ubuntu failed to start the xserver, then offered to do so in low graphics mode.

Something about parsing the xorg.conf file...

I used the DVI settings.

BTW, VGA connection behaves the same way.

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier	"Configured Monitor"
	HorizSync       31.0 - 80.0
	VertRefresh     50.0 - 75.0
        SubSection "Display"
                Depth           24
                Modes           "1680x1050"
        EndSubSection
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
	Disable	"dri2"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option          "ModeDebug"          "True"
	Option		"UseEDID"	     "False"
	Option          "ModeValidation"     "NoDFPNativeResolutionCheck"
EndSection

```

Here's the log:

```

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux ubuntu-desktop 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Sep  5 17:09:14 2009
(==) Using config file: "/etc/X11/xorg.conf"
Parse error on line 25 of section Monitor in file /etc/X11/xorg.conf
	"SubSection" is not a valid keyword in this section.
(EE) Problem parsing the config file
(EE) Error parsing the config file

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

(WW) xf86CloseConsole: KDSETMODE failed: Bad file descriptor
(WW) xf86CloseConsole: VT_GETMODE failed: Bad file descriptor
(WW) xf86OpenConsole: VT_GETSTATE failed: Bad file descriptor
 ddxSigGiveUp: Closing log
```

Seems to hate the "subsection" identifier.

---

### Post by CatKiller on 2009-09-05
> **tsali said:**
> Seems to hate the "subsection" identifier.

Sorry, my mistake. The Display SubSection should be in the Screen Section. Reading log files really dulls the brain...

---

### Post by tsali on 2009-09-06
Ok, changes made and still get an "out of range"

Here's the xorg.conf (I posted the analog values but tried with both - same results)

```
Section "Monitor"
	Identifier	"Configured Monitor"
	HorizSync       24.0 - 82.0
	VertRefresh     50.0 - 75.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
        SubSection "Display"
                Depth           24
                Modes           "1680x1050"
        EndSubSection
EndSection

Section "Module"
	Load	"glx"
	Disable	"dri2"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option          "ModeDebug"          "True"
	Option		"UseEDID"	     "False"
	Option          "ModeValidation"     "NoDFPNativeResolutionCheck"
EndSection
```

And the log:

```

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux ubuntu-desktop 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Sep  6 07:48:32 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@1:0:0) nVidia Corporation G70 [GeForce 7300 GT] rev 161, Mem @ 0xfa000000/16777216, 0xd0000000/268435456, 0xfb000000/16777216, I/O @ 0x0000cf00/128, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(WW) "dri2" will not be loaded unless you've specified it to be loaded elsewhere.
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded even though the default is to disable it.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  180.44  Mon Mar 23 15:29:02 PST 2009
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  180.44  Mon Mar 23 15:05:32 PST 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "UseEDID" "False"
(**) NVIDIA(0): Option "ModeValidation" "NoDFPNativeResolutionCheck"
(**) NVIDIA(0): Option "ModeDebug" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): Ignoring EDIDs
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(GPU-0): Not probing EDID on DFP-0.
(II) NVIDIA(0): NVIDIA GPU GeForce 7300 GT (G73) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.73.22.40.00
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7300 GT at PCI:1:0:0:
(--) NVIDIA(0):     DFP-0
(--) NVIDIA(0): DFP-0: 330.0 MHz maximum pixel clock
(--) NVIDIA(0): DFP-0: Internal Dual Link TMDS
(--) NVIDIA(0): 
(--) NVIDIA(0): --- EDID for DFP-0 ---
(--) NVIDIA(0): 
(--) NVIDIA(0): No EDID Available.
(--) NVIDIA(0): 
(--) NVIDIA(0): --- End of EDID for DFP-0 ---
(--) NVIDIA(0): 
(II) NVIDIA(0): Mode Validation Overrides for DFP-0:
(II) NVIDIA(0):     NoDFPNativeResolutionCheck
(II) NVIDIA(0): Frequency information for DFP-0:
(II) NVIDIA(0):   HorizSync   : 24.000-82.000 kHz
(II) NVIDIA(0):   VertRefresh : 50.000-75.000 Hz
(II) NVIDIA(0):     (HorizSync from HorizSync in X Config Monitor section)
(II) NVIDIA(0):     (VertRefresh from VertRefresh in X Config Monitor
(II) NVIDIA(0):     section)
(II) NVIDIA(0): 
(II) NVIDIA(0): --- Building ModePool for DFP-0 ---
(II) NVIDIA(0): 
(II) NVIDIA(0): Native backend timings for DFP-0:
(II) NVIDIA(0):   640 x 480 @ 60 Hz
(II) NVIDIA(0):     Pixel Clock      : 25.175 MHz
(II) NVIDIA(0):     HRes, HSyncStart :  640,  656
(II) NVIDIA(0):     HSyncEnd, HTotal :  752,  800
(II) NVIDIA(0):     VRes, VSyncStart :  480,  490
(II) NVIDIA(0):     VSyncEnd, VTotal :  492,  525
(II) NVIDIA(0):     H/V Polarity     : -/-
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x350":
(II) NVIDIA(0):     640 x 350 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  672
(II) NVIDIA(0):       HSyncEnd, HTotal :  736,  832
(II) NVIDIA(0):       VRes, VSyncStart :  350,  382
(II) NVIDIA(0):       VSyncEnd, VTotal :  385,  445
(II) NVIDIA(0):       H/V Polarity     : +/-
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.1 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "320x175":
(II) NVIDIA(0):     320 x 175 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 15.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  320,  336
(II) NVIDIA(0):       HSyncEnd, HTotal :  368,  416
(II) NVIDIA(0):       VRes, VSyncStart :  175,  191
(II) NVIDIA(0):       VSyncEnd, VTotal :  192,  222
(II) NVIDIA(0):       H/V Polarity     : +/-
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.3 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x400":
(II) NVIDIA(0):     640 x 400 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  672
(II) NVIDIA(0):       HSyncEnd, HTotal :  736,  832
(II) NVIDIA(0):       VRes, VSyncStart :  400,  401
(II) NVIDIA(0):       VSyncEnd, VTotal :  404,  445
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.1 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "320x200":
(II) NVIDIA(0):     320 x 200 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 15.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  320,  336
(II) NVIDIA(0):       HSyncEnd, HTotal :  368,  416
(II) NVIDIA(0):       VRes, VSyncStart :  200,  200
(II) NVIDIA(0):       VSyncEnd, VTotal :  202,  222
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.3 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "720x400":
(II) NVIDIA(0):     720 x 400 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 35.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  720,  756
(II) NVIDIA(0):       HSyncEnd, HTotal :  828,  936
(II) NVIDIA(0):       VRes, VSyncStart :  400,  401
(II) NVIDIA(0):       VSyncEnd, VTotal :  404,  446
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.0 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "360x200":
(II) NVIDIA(0):     360 x 200 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 17.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  360,  378
(II) NVIDIA(0):       HSyncEnd, HTotal :  414,  468
(II) NVIDIA(0):       VRes, VSyncStart :  200,  200
(II) NVIDIA(0):       VSyncEnd, VTotal :  202,  223
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.0 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 25.18 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  656
(II) NVIDIA(0):       HSyncEnd, HTotal :  752,  800
(II) NVIDIA(0):       VRes, VSyncStart :  480,  490
(II) NVIDIA(0):       VSyncEnd, VTotal :  492,  525
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     BestFit Backend for "640x480": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "320x240":
(II) NVIDIA(0):     320 x 240 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 12.59 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  320,  328
(II) NVIDIA(0):       HSyncEnd, HTotal :  376,  400
(II) NVIDIA(0):       VRes, VSyncStart :  240,  245
(II) NVIDIA(0):       VSyncEnd, VTotal :  246,  262
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "320x240": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 73 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  664
(II) NVIDIA(0):       HSyncEnd, HTotal :  704,  832
(II) NVIDIA(0):       VRes, VSyncStart :  480,  489
(II) NVIDIA(0):       VSyncEnd, VTotal :  492,  520
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     BestFit Backend for "640x480": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "320x240":
(II) NVIDIA(0):     320 x 240 @ 73 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 15.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  320,  332
(II) NVIDIA(0):       HSyncEnd, HTotal :  352,  416
(II) NVIDIA(0):       VRes, VSyncStart :  240,  244
(II) NVIDIA(0):       VSyncEnd, VTotal :  246,  260
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "320x240": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  656
(II) NVIDIA(0):       HSyncEnd, HTotal :  720,  840
(II) NVIDIA(0):       VRes, VSyncStart :  480,  481
(II) NVIDIA(0):       VSyncEnd, VTotal :  484,  500
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     BestFit Backend for "640x480": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "320x240":
(II) NVIDIA(0):     320 x 240 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 15.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  320,  328
(II) NVIDIA(0):       HSyncEnd, HTotal :  360,  420
(II) NVIDIA(0):       VRes, VSyncStart :  240,  240
(II) NVIDIA(0):       VSyncEnd, VTotal :  242,  250
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "320x240": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 36.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  696
(II) NVIDIA(0):       HSyncEnd, HTotal :  752,  832
(II) NVIDIA(0):       VRes, VSyncStart :  480,  481
(II) NVIDIA(0):       VSyncEnd, VTotal :  484,  509
(II) NVIDIA(0):       H/V Polarity     : -/-
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.0 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "320x240":
(II) NVIDIA(0):     320 x 240 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 18.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  320,  348
(II) NVIDIA(0):       HSyncEnd, HTotal :  376,  416
(II) NVIDIA(0):       VRes, VSyncStart :  240,  240
(II) NVIDIA(0):       VSyncEnd, VTotal :  242,  254
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.2 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 56 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 36.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  824
(II) NVIDIA(0):       HSyncEnd, HTotal :  896, 1024
(II) NVIDIA(0):       VRes, VSyncStart :  600,  601
(II) NVIDIA(0):       VSyncEnd, VTotal :  603,  625
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Unable to use mode "800x600" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "400x300":
(II) NVIDIA(0):     400 x 300 @ 56 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 18.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  400,  412
(II) NVIDIA(0):       HSyncEnd, HTotal :  448,  512
(II) NVIDIA(0):       VRes, VSyncStart :  300,  300
(II) NVIDIA(0):       VSyncEnd, VTotal :  301,  312
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "400x300": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 40.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  840
(II) NVIDIA(0):       HSyncEnd, HTotal :  968, 1056
(II) NVIDIA(0):       VRes, VSyncStart :  600,  601
(II) NVIDIA(0):       VSyncEnd, VTotal :  605,  628
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Unable to use mode "800x600" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "400x300":
(II) NVIDIA(0):     400 x 300 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 20.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  400,  420
(II) NVIDIA(0):       HSyncEnd, HTotal :  484,  528
(II) NVIDIA(0):       VRes, VSyncStart :  300,  300
(II) NVIDIA(0):       VSyncEnd, VTotal :  302,  314
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "400x300": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 72 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 50.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  856
(II) NVIDIA(0):       HSyncEnd, HTotal :  976, 1040
(II) NVIDIA(0):       VRes, VSyncStart :  600,  637
(II) NVIDIA(0):       VSyncEnd, VTotal :  643,  666
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Unable to use mode "800x600" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "400x300":
(II) NVIDIA(0):     400 x 300 @ 72 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 25.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  400,  428
(II) NVIDIA(0):       HSyncEnd, HTotal :  488,  520
(II) NVIDIA(0):       VRes, VSyncStart :  300,  318
(II) NVIDIA(0):       VSyncEnd, VTotal :  321,  333
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "400x300": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 49.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  816
(II) NVIDIA(0):       HSyncEnd, HTotal :  896, 1056
(II) NVIDIA(0):       VRes, VSyncStart :  600,  601
(II) NVIDIA(0):       VSyncEnd, VTotal :  604,  625
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Unable to use mode "800x600" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "400x300":
(II) NVIDIA(0):     400 x 300 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 24.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  400,  408
(II) NVIDIA(0):       HSyncEnd, HTotal :  448,  528
(II) NVIDIA(0):       VRes, VSyncStart :  300,  300
(II) NVIDIA(0):       VSyncEnd, VTotal :  302,  312
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "400x300": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 56.30 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  832
(II) NVIDIA(0):       HSyncEnd, HTotal :  896, 1048
(II) NVIDIA(0):       VRes, VSyncStart :  600,  601
(II) NVIDIA(0):       VSyncEnd, VTotal :  604,  631
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.1 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "400x300":
(II) NVIDIA(0):     400 x 300 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 28.15 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  400,  416
(II) NVIDIA(0):       HSyncEnd, HTotal :  448,  524
(II) NVIDIA(0):       VRes, VSyncStart :  300,  300
(II) NVIDIA(0):       VSyncEnd, VTotal :  302,  315
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.3 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 87 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 44.90 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1032
(II) NVIDIA(0):       HSyncEnd, HTotal : 1208, 1264
(II) NVIDIA(0):       VRes, VSyncStart :  768,  768
(II) NVIDIA(0):       VSyncEnd, VTotal :  776,  817
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : Interlace
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (87.0 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "512x384":
(II) NVIDIA(0):     512 x 384 @ 87 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 22.45 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  512,  516
(II) NVIDIA(0):       HSyncEnd, HTotal :  604,  632
(II) NVIDIA(0):       VRes, VSyncStart :  384,  384
(II) NVIDIA(0):       VSyncEnd, VTotal :  388,  408
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : Interlace DoubleScan
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (87.1 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 65.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1048
(II) NVIDIA(0):       HSyncEnd, HTotal : 1184, 1344
(II) NVIDIA(0):       VRes, VSyncStart :  768,  771
(II) NVIDIA(0):       VSyncEnd, VTotal :  777,  806
(II) NVIDIA(0):       H/V Polarity     : -/-
(WW) NVIDIA(0):     Unable to use mode "1024x768" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "512x384":
(II) NVIDIA(0):     512 x 384 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 32.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  512,  524
(II) NVIDIA(0):       HSyncEnd, HTotal :  592,  672
(II) NVIDIA(0):       VRes, VSyncStart :  384,  385
(II) NVIDIA(0):       VSyncEnd, VTotal :  388,  403
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "512x384": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 70 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 75.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1048
(II) NVIDIA(0):       HSyncEnd, HTotal : 1184, 1328
(II) NVIDIA(0):       VRes, VSyncStart :  768,  771
(II) NVIDIA(0):       VSyncEnd, VTotal :  777,  806
(II) NVIDIA(0):       H/V Polarity     : -/-
(WW) NVIDIA(0):     Unable to use mode "1024x768" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "512x384":
(II) NVIDIA(0):     512 x 384 @ 70 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 37.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  512,  524
(II) NVIDIA(0):       HSyncEnd, HTotal :  592,  664
(II) NVIDIA(0):       VRes, VSyncStart :  384,  385
(II) NVIDIA(0):       VSyncEnd, VTotal :  388,  403
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "512x384": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 78.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1040
(II) NVIDIA(0):       HSyncEnd, HTotal : 1136, 1312
(II) NVIDIA(0):       VRes, VSyncStart :  768,  769
(II) NVIDIA(0):       VSyncEnd, VTotal :  772,  800
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Unable to use mode "1024x768" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "512x384":
(II) NVIDIA(0):     512 x 384 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 39.38 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  512,  520
(II) NVIDIA(0):       HSyncEnd, HTotal :  568,  656
(II) NVIDIA(0):       VRes, VSyncStart :  384,  384
(II) NVIDIA(0):       VSyncEnd, VTotal :  386,  400
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "512x384": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 94.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1072
(II) NVIDIA(0):       HSyncEnd, HTotal : 1168, 1376
(II) NVIDIA(0):       VRes, VSyncStart :  768,  769
(II) NVIDIA(0):       VSyncEnd, VTotal :  772,  808
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.0 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "512x384":
(II) NVIDIA(0):     512 x 384 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 47.25 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  512,  536
(II) NVIDIA(0):       HSyncEnd, HTotal :  584,  688
(II) NVIDIA(0):       VRes, VSyncStart :  384,  384
(II) NVIDIA(0):       VSyncEnd, VTotal :  386,  404
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.0 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1152x864":
(II) NVIDIA(0):     1152 x 864 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 108.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1152, 1216
(II) NVIDIA(0):       HSyncEnd, HTotal : 1344, 1600
(II) NVIDIA(0):       VRes, VSyncStart :  864,  865
(II) NVIDIA(0):       VSyncEnd, VTotal :  868,  900
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Unable to use mode "1152x864" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "576x432":
(II) NVIDIA(0):     576 x 432 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 54.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  576,  608
(II) NVIDIA(0):       HSyncEnd, HTotal :  672,  800
(II) NVIDIA(0):       VRes, VSyncStart :  432,  432
(II) NVIDIA(0):       VSyncEnd, VTotal :  434,  450
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "576x432": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x960":
(II) NVIDIA(0):     1280 x 960 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 108.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1376
(II) NVIDIA(0):       HSyncEnd, HTotal : 1488, 1800
(II) NVIDIA(0):       VRes, VSyncStart :  960,  961
(II) NVIDIA(0):       VSyncEnd, VTotal :  964, 1000
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Unable to use mode "1280x960" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 54.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  688
(II) NVIDIA(0):       HSyncEnd, HTotal :  744,  900
(II) NVIDIA(0):       VRes, VSyncStart :  480,  480
(II) NVIDIA(0):       VSyncEnd, VTotal :  482,  500
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "640x480": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x960":
(II) NVIDIA(0):     1280 x 960 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 148.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1344
(II) NVIDIA(0):       HSyncEnd, HTotal : 1504, 1728
(II) NVIDIA(0):       VRes, VSyncStart :  960,  961
(II) NVIDIA(0):       VSyncEnd, VTotal :  964, 1011
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (85.9 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 74.25 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  672
(II) NVIDIA(0):       HSyncEnd, HTotal :  752,  864
(II) NVIDIA(0):       VRes, VSyncStart :  480,  480
(II) NVIDIA(0):       VSyncEnd, VTotal :  482,  505
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (85.9 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x1024":
(II) NVIDIA(0):     1280 x 1024 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 108.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1328
(II) NVIDIA(0):       HSyncEnd, HTotal : 1440, 1688
(II) NVIDIA(0):       VRes, VSyncStart : 1024, 1025
(II) NVIDIA(0):       VSyncEnd, VTotal : 1028, 1066
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Unable to use mode "1280x1024" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x512":
(II) NVIDIA(0):     640 x 512 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 54.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  664
(II) NVIDIA(0):       HSyncEnd, HTotal :  720,  844
(II) NVIDIA(0):       VRes, VSyncStart :  512,  512
(II) NVIDIA(0):       VSyncEnd, VTotal :  514,  533
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Unable to use mode "640x512" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x1024":
(II) NVIDIA(0):     1280 x 1024 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 135.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1296
(II) NVIDIA(0):       HSyncEnd, HTotal : 1440, 1688
(II) NVIDIA(0):       VRes, VSyncStart : 1024, 1025
(II) NVIDIA(0):       VSyncEnd, VTotal : 1028, 1066
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Unable to use mode "1280x1024" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x512":
(II) NVIDIA(0):     640 x 512 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 67.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  648
(II) NVIDIA(0):       HSyncEnd, HTotal :  720,  844
(II) NVIDIA(0):       VRes, VSyncStart :  512,  512
(II) NVIDIA(0):       VSyncEnd, VTotal :  514,  533
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Unable to use mode "640x512" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x1024":
(II) NVIDIA(0):     1280 x 1024 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 157.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1344
(II) NVIDIA(0):       HSyncEnd, HTotal : 1504, 1728
(II) NVIDIA(0):       VRes, VSyncStart : 1024, 1025
(II) NVIDIA(0):       VSyncEnd, VTotal : 1028, 1072
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (91.1 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x512":
(II) NVIDIA(0):     640 x 512 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 78.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  672
(II) NVIDIA(0):       HSyncEnd, HTotal :  752,  864
(II) NVIDIA(0):       VRes, VSyncStart :  512,  512
(II) NVIDIA(0):       VSyncEnd, VTotal :  514,  536
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (91.1 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1200":
(II) NVIDIA(0):     1600 x 1200 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 162.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
(II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
(II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Unable to use mode "1600x1200" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 81.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  832
(II) NVIDIA(0):       HSyncEnd, HTotal :  928, 1080
(II) NVIDIA(0):       VRes, VSyncStart :  600,  600
(II) NVIDIA(0):       VSyncEnd, VTotal :  602,  625
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Unable to use mode "800x600" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1200":
(II) NVIDIA(0):     1600 x 1200 @ 65 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 175.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
(II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
(II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Unable to use mode "1600x1200" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 65 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 87.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  832
(II) NVIDIA(0):       HSyncEnd, HTotal :  928, 1080
(II) NVIDIA(0):       VRes, VSyncStart :  600,  600
(II) NVIDIA(0):       VSyncEnd, VTotal :  602,  625
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Unable to use mode "800x600" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1200":
(II) NVIDIA(0):     1600 x 1200 @ 70 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 189.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
(II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
(II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (87.5 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 70 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 94.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  832
(II) NVIDIA(0):       HSyncEnd, HTotal :  928, 1080
(II) NVIDIA(0):       VRes, VSyncStart :  600,  600
(II) NVIDIA(0):       VSyncEnd, VTotal :  602,  625
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (87.5 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1200":
(II) NVIDIA(0):     1600 x 1200 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 202.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
(II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
(II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (93.8 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 101.25 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  832
(II) NVIDIA(0):       HSyncEnd, HTotal :  928, 1080
(II) NVIDIA(0):       VRes, VSyncStart :  600,  600
(II) NVIDIA(0):       VSyncEnd, VTotal :  602,  625
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (93.8 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1200":
(II) NVIDIA(0):     1600 x 1200 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 229.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
(II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
(II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (106.2 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 114.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  832
(II) NVIDIA(0):       HSyncEnd, HTotal :  928, 1080
(II) NVIDIA(0):       VRes, VSyncStart :  600,  600
(II) NVIDIA(0):       VSyncEnd, VTotal :  602,  625
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (106.2 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1792x1344":
(II) NVIDIA(0):     1792 x 1344 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 204.80 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1792, 1920
(II) NVIDIA(0):       HSyncEnd, HTotal : 2120, 2448
(II) NVIDIA(0):       VRes, VSyncStart : 1344, 1345
(II) NVIDIA(0):       VSyncEnd, VTotal : 1348, 1394
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (83.7 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "896x672":
(II) NVIDIA(0):     896 x 672 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 102.40 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  896,  960
(II) NVIDIA(0):       HSyncEnd, HTotal : 1060, 1224
(II) NVIDIA(0):       VRes, VSyncStart :  672,  672
(II) NVIDIA(0):       VSyncEnd, VTotal :  674,  697
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (83.7 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1792x1344":
(II) NVIDIA(0):     1792 x 1344 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 261.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1792, 1888
(II) NVIDIA(0):       HSyncEnd, HTotal : 2104, 2456
(II) NVIDIA(0):       VRes, VSyncStart : 1344, 1345
(II) NVIDIA(0):       VSyncEnd, VTotal : 1348, 1417
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (106.3 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "896x672":
(II) NVIDIA(0):     896 x 672 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 130.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  896,  944
(II) NVIDIA(0):       HSyncEnd, HTotal : 1052, 1228
(II) NVIDIA(0):       VRes, VSyncStart :  672,  672
(II) NVIDIA(0):       VSyncEnd, VTotal :  674,  708
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (106.3 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1856x1392":
(II) NVIDIA(0):     1856 x 1392 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 218.30 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1856, 1952
(II) NVIDIA(0):       HSyncEnd, HTotal : 2176, 2528
(II) NVIDIA(0):       VRes, VSyncStart : 1392, 1393
(II) NVIDIA(0):       VSyncEnd, VTotal : 1396, 1439
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (86.4 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "928x696":
(II) NVIDIA(0):     928 x 696 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 109.15 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  928,  976
(II) NVIDIA(0):       HSyncEnd, HTotal : 1088, 1264
(II) NVIDIA(0):       VRes, VSyncStart :  696,  696
(II) NVIDIA(0):       VSyncEnd, VTotal :  698,  719
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (86.4 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1856x1392":
(II) NVIDIA(0):     1856 x 1392 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 288.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1856, 1984
(II) NVIDIA(0):       HSyncEnd, HTotal : 2208, 2560
(II) NVIDIA(0):       VRes, VSyncStart : 1392, 1393
(II) NVIDIA(0):       VSyncEnd, VTotal : 1396, 1500
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (112.5 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "928x696":
(II) NVIDIA(0):     928 x 696 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 144.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  928,  992
(II) NVIDIA(0):       HSyncEnd, HTotal : 1104, 1280
(II) NVIDIA(0):       VRes, VSyncStart :  696,  696
(II) NVIDIA(0):       VSyncEnd, VTotal :  698,  750
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (112.5 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1920x1440":
(II) NVIDIA(0):     1920 x 1440 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 234.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1920, 2048
(II) NVIDIA(0):       HSyncEnd, HTotal : 2256, 2600
(II) NVIDIA(0):       VRes, VSyncStart : 1440, 1441
(II) NVIDIA(0):       VSyncEnd, VTotal : 1444, 1500
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (90.0 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "960x720":
(II) NVIDIA(0):     960 x 720 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 117.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  960, 1024
(II) NVIDIA(0):       HSyncEnd, HTotal : 1128, 1300
(II) NVIDIA(0):       VRes, VSyncStart :  720,  720
(II) NVIDIA(0):       VSyncEnd, VTotal :  722,  750
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (90.0 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1920x1440":
(II) NVIDIA(0):     1920 x 1440 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 297.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1920, 2064
(II) NVIDIA(0):       HSyncEnd, HTotal : 2288, 2640
(II) NVIDIA(0):       VRes, VSyncStart : 1440, 1441
(II) NVIDIA(0):       VSyncEnd, VTotal : 1444, 1500
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (112.5 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "960x720":
(II) NVIDIA(0):     960 x 720 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 148.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  960, 1032
(II) NVIDIA(0):       HSyncEnd, HTotal : 1144, 1320
(II) NVIDIA(0):       VRes, VSyncStart :  720,  720
(II) NVIDIA(0):       VSyncEnd, VTotal :  722,  750
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (112.5 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "832x624":
(II) NVIDIA(0):     832 x 624 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 57.28 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  832,  864
(II) NVIDIA(0):       HSyncEnd, HTotal :  928, 1152
(II) NVIDIA(0):       VRes, VSyncStart :  624,  625
(II) NVIDIA(0):       VSyncEnd, VTotal :  628,  667
(II) NVIDIA(0):       H/V Polarity     : -/-
(WW) NVIDIA(0):     Unable to use mode "832x624" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "416x312":
(II) NVIDIA(0):     416 x 312 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 28.64 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  416,  432
(II) NVIDIA(0):       HSyncEnd, HTotal :  464,  576
(II) NVIDIA(0):       VRes, VSyncStart :  312,  312
(II) NVIDIA(0):       VSyncEnd, VTotal :  314,  333
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "416x312": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1152x864":
(II) NVIDIA(0):     1152 x 864 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 81.62 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1152, 1216
(II) NVIDIA(0):       HSyncEnd, HTotal : 1336, 1520
(II) NVIDIA(0):       VRes, VSyncStart :  864,  865
(II) NVIDIA(0):       VSyncEnd, VTotal :  868,  895
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Unable to use mode "1152x864" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "576x432":
(II) NVIDIA(0):     576 x 432 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 40.81 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  576,  608
(II) NVIDIA(0):       HSyncEnd, HTotal :  668,  760
(II) NVIDIA(0):       VRes, VSyncStart :  432,  432
(II) NVIDIA(0):       VSyncEnd, VTotal :  434,  447
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "576x432": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1152x864":
(II) NVIDIA(0):     1152 x 864 @ 70 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 96.77 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1152, 1224
(II) NVIDIA(0):       HSyncEnd, HTotal : 1344, 1536
(II) NVIDIA(0):       VRes, VSyncStart :  864,  865
(II) NVIDIA(0):       VSyncEnd, VTotal :  868,  900
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Unable to use mode "1152x864" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "576x432":
(II) NVIDIA(0):     576 x 432 @ 70 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 48.38 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  576,  612
(II) NVIDIA(0):       HSyncEnd, HTotal :  672,  768
(II) NVIDIA(0):       VRes, VSyncStart :  432,  432
(II) NVIDIA(0):       VSyncEnd, VTotal :  434,  450
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "576x432": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1152x864":
(II) NVIDIA(0):     1152 x 864 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 104.99 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1152, 1224
(II) NVIDIA(0):       HSyncEnd, HTotal : 1352, 1552
(II) NVIDIA(0):       VRes, VSyncStart :  864,  865
(II) NVIDIA(0):       VSyncEnd, VTotal :  868,  902
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Unable to use mode "1152x864" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "576x432":
(II) NVIDIA(0):     576 x 432 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 52.49 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  576,  612
(II) NVIDIA(0):       HSyncEnd, HTotal :  676,  776
(II) NVIDIA(0):       VRes, VSyncStart :  432,  432
(II) NVIDIA(0):       VSyncEnd, VTotal :  434,  451
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "576x432": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1152x864":
(II) NVIDIA(0):     1152 x 864 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 119.65 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1152, 1224
(II) NVIDIA(0):       HSyncEnd, HTotal : 1352, 1552
(II) NVIDIA(0):       VRes, VSyncStart :  864,  865
(II) NVIDIA(0):       VSyncEnd, VTotal :  868,  907
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.0 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "576x432":
(II) NVIDIA(0):     576 x 432 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 59.83 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  576,  612
(II) NVIDIA(0):       HSyncEnd, HTotal :  676,  776
(II) NVIDIA(0):       VRes, VSyncStart :  432,  432
(II) NVIDIA(0):       VSyncEnd, VTotal :  434,  453
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.1 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1152x864":
(II) NVIDIA(0):     1152 x 864 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 121.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1152, 1216
(II) NVIDIA(0):       HSyncEnd, HTotal : 1344, 1568
(II) NVIDIA(0):       VRes, VSyncStart :  864,  865
(II) NVIDIA(0):       VSyncEnd, VTotal :  868,  911
(II) NVIDIA(0):       H/V Polarity     : +/-
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.1 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "576x432":
(II) NVIDIA(0):     576 x 432 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 60.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  576,  608
(II) NVIDIA(0):       HSyncEnd, HTotal :  672,  784
(II) NVIDIA(0):       VRes, VSyncStart :  432,  432
(II) NVIDIA(0):       VSyncEnd, VTotal :  434,  455
(II) NVIDIA(0):       H/V Polarity     : +/-
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.2 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1152x864":
(II) NVIDIA(0):     1152 x 864 @ 100 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 143.47 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1152, 1232
(II) NVIDIA(0):       HSyncEnd, HTotal : 1360, 1568
(II) NVIDIA(0):       VRes, VSyncStart :  864,  865
(II) NVIDIA(0):       VSyncEnd, VTotal :  868,  915
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (91.5 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "576x432":
(II) NVIDIA(0):     576 x 432 @ 100 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 71.73 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  576,  616
(II) NVIDIA(0):       HSyncEnd, HTotal :  680,  784
(II) NVIDIA(0):       VRes, VSyncStart :  432,  432
(II) NVIDIA(0):       VSyncEnd, VTotal :  434,  457
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (91.5 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1360x768":
(II) NVIDIA(0):     1360 x 768 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 72.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1360, 1408
(II) NVIDIA(0):       HSyncEnd, HTotal : 1440, 1520
(II) NVIDIA(0):       VRes, VSyncStart :  768,  771
(II) NVIDIA(0):       VSyncEnd, VTotal :  781,  790
(II) NVIDIA(0):       H/V Polarity     : +/-
(WW) NVIDIA(0):     Unable to use mode "1360x768" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "680x384":
(II) NVIDIA(0):     680 x 384 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 36.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  680,  704
(II) NVIDIA(0):       HSyncEnd, HTotal :  720,  760
(II) NVIDIA(0):       VRes, VSyncStart :  384,  385
(II) NVIDIA(0):       VSyncEnd, VTotal :  390,  395
(II) NVIDIA(0):       H/V Polarity     : +/-
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Unable to use mode "680x384" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1360x768":
(II) NVIDIA(0):     1360 x 768 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 84.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1360, 1432
(II) NVIDIA(0):       HSyncEnd, HTotal : 1568, 1776
(II) NVIDIA(0):       VRes, VSyncStart :  768,  771
(II) NVIDIA(0):       VSyncEnd, VTotal :  781,  798
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Unable to use mode "1360x768" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "680x384":
(II) NVIDIA(0):     680 x 384 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 42.38 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  680,  716
(II) NVIDIA(0):       HSyncEnd, HTotal :  784,  888
(II) NVIDIA(0):       VRes, VSyncStart :  384,  385
(II) NVIDIA(0):       VSyncEnd, VTotal :  390,  399
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Unable to use mode "680x384" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1400x1050":
(II) NVIDIA(0):     1400 x 1050 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 122.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1400, 1488
(II) NVIDIA(0):       HSyncEnd, HTotal : 1640, 1880
(II) NVIDIA(0):       VRes, VSyncStart : 1050, 1052
(II) NVIDIA(0):       VSyncEnd, VTotal : 1064, 1082
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Unable to use mode "1400x1050" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "700x525":
(II) NVIDIA(0):     700 x 525 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 61.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  700,  744
(II) NVIDIA(0):       HSyncEnd, HTotal :  820,  940
(II) NVIDIA(0):       VRes, VSyncStart :  525,  526
(II) NVIDIA(0):       VSyncEnd, VTotal :  532,  541
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: Mode's width (700) is not a multiple of
(WW) NVIDIA(0):     8.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1400x1050":
(II) NVIDIA(0):     1400 x 1050 @ 70 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 145.06 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1400, 1496
(II) NVIDIA(0):       HSyncEnd, HTotal : 1648, 1896
(II) NVIDIA(0):       VRes, VSyncStart : 1050, 1051
(II) NVIDIA(0):       VSyncEnd, VTotal : 1054, 1093
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Unable to use mode "1400x1050" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "700x525":
(II) NVIDIA(0):     700 x 525 @ 70 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 72.53 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  700,  748
(II) NVIDIA(0):       HSyncEnd, HTotal :  824,  948
(II) NVIDIA(0):       VRes, VSyncStart :  525,  525
(II) NVIDIA(0):       VSyncEnd, VTotal :  527,  546
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: Mode's width (700) is not a multiple of
(WW) NVIDIA(0):     8.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1400x1050":
(II) NVIDIA(0):     1400 x 1050 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 155.80 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1400, 1464
(II) NVIDIA(0):       HSyncEnd, HTotal : 1784, 1912
(II) NVIDIA(0):       VRes, VSyncStart : 1050, 1052
(II) NVIDIA(0):       VSyncEnd, VTotal : 1064, 1090
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Unable to use mode "1400x1050" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "700x525":
(II) NVIDIA(0):     700 x 525 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 77.90 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  700,  732
(II) NVIDIA(0):       HSyncEnd, HTotal :  892,  956
(II) NVIDIA(0):       VRes, VSyncStart :  525,  526
(II) NVIDIA(0):       VSyncEnd, VTotal :  532,  545
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: Mode's width (700) is not a multiple of
(WW) NVIDIA(0):     8.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1400x1050":
(II) NVIDIA(0):     1400 x 1050 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 179.26 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1400, 1504
(II) NVIDIA(0):       HSyncEnd, HTotal : 1656, 1912
(II) NVIDIA(0):       VRes, VSyncStart : 1050, 1051
(II) NVIDIA(0):       VSyncEnd, VTotal : 1054, 1103
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (93.8 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "700x525":
(II) NVIDIA(0):     700 x 525 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 89.63 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  700,  752
(II) NVIDIA(0):       HSyncEnd, HTotal :  828,  956
(II) NVIDIA(0):       VRes, VSyncStart :  525,  525
(II) NVIDIA(0):       VSyncEnd, VTotal :  527,  551
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (93.8 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1440x900":
(II) NVIDIA(0):     1440 x 900 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 106.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1440, 1520
(II) NVIDIA(0):       HSyncEnd, HTotal : 1672, 1904
(II) NVIDIA(0):       VRes, VSyncStart :  900,  903
(II) NVIDIA(0):       VSyncEnd, VTotal :  909,  934
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Unable to use mode "1440x900" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "720x450":
(II) NVIDIA(0):     720 x 450 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 53.25 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  720,  760
(II) NVIDIA(0):       HSyncEnd, HTotal :  836,  952
(II) NVIDIA(0):       VRes, VSyncStart :  450,  451
(II) NVIDIA(0):       VSyncEnd, VTotal :  454,  467
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Unable to use mode "720x450" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1024":
(II) NVIDIA(0):     1600 x 1024 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 103.12 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1600
(II) NVIDIA(0):       HSyncEnd, HTotal : 1656, 1664
(II) NVIDIA(0):       VRes, VSyncStart : 1024, 1024
(II) NVIDIA(0):       VSyncEnd, VTotal : 1029, 1030
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Unable to use mode "1600x1024" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x512":
(II) NVIDIA(0):     800 x 512 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 51.56 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  800
(II) NVIDIA(0):       HSyncEnd, HTotal :  828,  832
(II) NVIDIA(0):       VRes, VSyncStart :  512,  512
(II) NVIDIA(0):       VSyncEnd, VTotal :  514,  515
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Unable to use mode "800x512" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1680x1050":
(II) NVIDIA(0):     1680 x 1050 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 119.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1680, 1728
(II) NVIDIA(0):       HSyncEnd, HTotal : 1760, 1840
(II) NVIDIA(0):       VRes, VSyncStart : 1050, 1053
(II) NVIDIA(0):       VSyncEnd, VTotal : 1059, 1080
(II) NVIDIA(0):       H/V Polarity     : +/-
(WW) NVIDIA(0):     Unable to use mode "1680x1050" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "840x525":
(II) NVIDIA(0):     840 x 525 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 59.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  840,  864
(II) NVIDIA(0):       HSyncEnd, HTotal :  880,  920
(II) NVIDIA(0):       VRes, VSyncStart :  525,  526
(II) NVIDIA(0):       VSyncEnd, VTotal :  529,  540
(II) NVIDIA(0):       H/V Polarity     : +/-
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Unable to use mode "840x525" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1680x1050":
(II) NVIDIA(0):     1680 x 1050 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 146.25 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1680, 1784
(II) NVIDIA(0):       HSyncEnd, HTotal : 1960, 2240
(II) NVIDIA(0):       VRes, VSyncStart : 1050, 1053
(II) NVIDIA(0):       VSyncEnd, VTotal : 1059, 1089
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Unable to use mode "1680x1050" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "840x525":
(II) NVIDIA(0):     840 x 525 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 73.12 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  840,  892
(II) NVIDIA(0):       HSyncEnd, HTotal :  980, 1120
(II) NVIDIA(0):       VRes, VSyncStart :  525,  526
(II) NVIDIA(0):       VSyncEnd, VTotal :  529,  544
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Unable to use mode "840x525" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1680x1050":
(II) NVIDIA(0):     1680 x 1050 @ 70 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 174.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1680, 1800
(II) NVIDIA(0):       HSyncEnd, HTotal : 1976, 2272
(II) NVIDIA(0):       VRes, VSyncStart : 1050, 1053
(II) NVIDIA(0):       VSyncEnd, VTotal : 1059, 1096
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Unable to use mode "1680x1050" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "840x525":
(II) NVIDIA(0):     840 x 525 @ 70 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 87.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  840,  900
(II) NVIDIA(0):       HSyncEnd, HTotal :  988, 1136
(II) NVIDIA(0):       VRes, VSyncStart :  525,  526
(II) NVIDIA(0):       VSyncEnd, VTotal :  529,  548
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Unable to use mode "840x525" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1680x1050":
(II) NVIDIA(0):     1680 x 1050 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 187.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1680, 1800
(II) NVIDIA(0):       HSyncEnd, HTotal : 1976, 2272
(II) NVIDIA(0):       VRes, VSyncStart : 1050, 1053
(II) NVIDIA(0):       VSyncEnd, VTotal : 1059, 1099
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Unable to use mode "1680x1050" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "840x525":
(II) NVIDIA(0):     840 x 525 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 93.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  840,  900
(II) NVIDIA(0):       HSyncEnd, HTotal :  988, 1136
(II) NVIDIA(0):       VRes, VSyncStart :  525,  526
(II) NVIDIA(0):       VSyncEnd, VTotal :  529,  549
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Unable to use mode "840x525" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1680x1050":
(II) NVIDIA(0):     1680 x 1050 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 214.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1680, 1808
(II) NVIDIA(0):       HSyncEnd, HTotal : 1984, 2288
(II) NVIDIA(0):       VRes, VSyncStart : 1050, 1053
(II) NVIDIA(0):       VSyncEnd, VTotal : 1059, 1105
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (93.9 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "840x525":
(II) NVIDIA(0):     840 x 525 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 107.38 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  840,  904
(II) NVIDIA(0):       HSyncEnd, HTotal :  992, 1144
(II) NVIDIA(0):       VRes, VSyncStart :  525,  526
(II) NVIDIA(0):       VSyncEnd, VTotal :  529,  552
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (93.9 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1920x1080":
(II) NVIDIA(0):     1920 x 1080 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 138.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1920, 1968
(II) NVIDIA(0):       HSyncEnd, HTotal : 2000, 2080
(II) NVIDIA(0):       VRes, VSyncStart : 1080, 1083
(II) NVIDIA(0):       VSyncEnd, VTotal : 1088, 1111
(II) NVIDIA(0):       H/V Polarity     : +/-
(WW) NVIDIA(0):     Unable to use mode "1920x1080" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "960x540":
(II) NVIDIA(0):     960 x 540 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 69.25 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  960,  984
(II) NVIDIA(0):       HSyncEnd, HTotal : 1000, 1040
(II) NVIDIA(0):       VRes, VSyncStart :  540,  541
(II) NVIDIA(0):       VSyncEnd, VTotal :  544,  555
(II) NVIDIA(0):       H/V Polarity     : +/-
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Unable to use mode "960x540" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1920x1200":
(II) NVIDIA(0):     1920 x 1200 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 154.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1920, 1968
(II) NVIDIA(0):       HSyncEnd, HTotal : 2000, 2080
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1203
(II) NVIDIA(0):       VSyncEnd, VTotal : 1209, 1235
(II) NVIDIA(0):       H/V Polarity     : +/-
(WW) NVIDIA(0):     Unable to use mode "1920x1200" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "960x600":
(II) NVIDIA(0):     960 x 600 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 77.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  960,  984
(II) NVIDIA(0):       HSyncEnd, HTotal : 1000, 1040
(II) NVIDIA(0):       VRes, VSyncStart :  600,  601
(II) NVIDIA(0):       VSyncEnd, VTotal :  604,  617
(II) NVIDIA(0):       H/V Polarity     : +/-
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Unable to use mode "960x600" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1920x1440":
(II) NVIDIA(0):     1920 x 1440 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 341.35 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1920, 2072
(II) NVIDIA(0):       HSyncEnd, HTotal : 2288, 2656
(II) NVIDIA(0):       VRes, VSyncStart : 1440, 1441
(II) NVIDIA(0):       VSyncEnd, VTotal : 1444, 1512
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (341.4 MHz) too high for
(WW) NVIDIA(0):     Display Device (Max: 330.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "960x720":
(II) NVIDIA(0):     960 x 720 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 170.68 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  960, 1036
(II) NVIDIA(0):       HSyncEnd, HTotal : 1144, 1328
(II) NVIDIA(0):       VRes, VSyncStart :  720,  720
(II) NVIDIA(0):       VSyncEnd, VTotal :  722,  756
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (128.5 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "2048x1536":
(II) NVIDIA(0):     2048 x 1536 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 266.95 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 2048, 2200
(II) NVIDIA(0):       HSyncEnd, HTotal : 2424, 2800
(II) NVIDIA(0):       VRes, VSyncStart : 1536, 1537
(II) NVIDIA(0):       VSyncEnd, VTotal : 1540, 1589
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (95.3 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 133.47 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1100
(II) NVIDIA(0):       HSyncEnd, HTotal : 1212, 1400
(II) NVIDIA(0):       VRes, VSyncStart :  768,  768
(II) NVIDIA(0):       VSyncEnd, VTotal :  770,  794
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (95.3 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "2048x1536":
(II) NVIDIA(0):     2048 x 1536 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 340.48 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 2048, 2216
(II) NVIDIA(0):       HSyncEnd, HTotal : 2440, 2832
(II) NVIDIA(0):       VRes, VSyncStart : 1536, 1537
(II) NVIDIA(0):       VSyncEnd, VTotal : 1540, 1603
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (340.5 MHz) too high for
(WW) NVIDIA(0):     Display Device (Max: 330.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 170.24 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1108
(II) NVIDIA(0):       HSyncEnd, HTotal : 1220, 1416
(II) NVIDIA(0):       VRes, VSyncStart :  768,  768
(II) NVIDIA(0):       VSyncEnd, VTotal :  770,  801
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (120.2 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "2048x1536":
(II) NVIDIA(0):     2048 x 1536 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 388.04 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 2048, 2216
(II) NVIDIA(0):       HSyncEnd, HTotal : 2440, 2832
(II) NVIDIA(0):       VRes, VSyncStart : 1536, 1537
(II) NVIDIA(0):       VSyncEnd, VTotal : 1540, 1612
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (388.0 MHz) too high for
(WW) NVIDIA(0):     Display Device (Max: 330.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 194.02 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1108
(II) NVIDIA(0):       HSyncEnd, HTotal : 1220, 1416
(II) NVIDIA(0):       VRes, VSyncStart :  768,  768
(II) NVIDIA(0):       VSyncEnd, VTotal :  770,  806
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (137.0 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x350":
(II) NVIDIA(0):     640 x 350 @ 85 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  672
(II) NVIDIA(0):       HSyncEnd, HTotal :  736,  832
(II) NVIDIA(0):       VRes, VSyncStart :  350,  382
(II) NVIDIA(0):       VSyncEnd, VTotal :  385,  445
(II) NVIDIA(0):       H/V Polarity     : +/-
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.1 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x400":
(II) NVIDIA(0):     640 x 400 @ 85 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  672
(II) NVIDIA(0):       HSyncEnd, HTotal :  736,  832
(II) NVIDIA(0):       VRes, VSyncStart :  400,  401
(II) NVIDIA(0):       VSyncEnd, VTotal :  404,  445
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.1 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "720x400":
(II) NVIDIA(0):     720 x 400 @ 85 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 35.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  720,  756
(II) NVIDIA(0):       HSyncEnd, HTotal :  828,  936
(II) NVIDIA(0):       VRes, VSyncStart :  400,  401
(II) NVIDIA(0):       VSyncEnd, VTotal :  404,  446
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.0 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 60 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 25.18 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  656
(II) NVIDIA(0):       HSyncEnd, HTotal :  752,  800
(II) NVIDIA(0):       VRes, VSyncStart :  480,  490
(II) NVIDIA(0):       VSyncEnd, VTotal :  492,  525
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     BestFit Backend for "640x480": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 73 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  664
(II) NVIDIA(0):       HSyncEnd, HTotal :  704,  832
(II) NVIDIA(0):       VRes, VSyncStart :  480,  489
(II) NVIDIA(0):       VSyncEnd, VTotal :  492,  520
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     BestFit Backend for "640x480": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 75 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  656
(II) NVIDIA(0):       HSyncEnd, HTotal :  720,  840
(II) NVIDIA(0):       VRes, VSyncStart :  480,  481
(II) NVIDIA(0):       VSyncEnd, VTotal :  484,  500
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     BestFit Backend for "640x480": 640x480
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 85 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 36.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  696
(II) NVIDIA(0):       HSyncEnd, HTotal :  752,  832
(II) NVIDIA(0):       VRes, VSyncStart :  480,  481
(II) NVIDIA(0):       VSyncEnd, VTotal :  484,  509
(II) NVIDIA(0):       H/V Polarity     : -/-
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.0 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 56 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 36.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  824
(II) NVIDIA(0):       HSyncEnd, HTotal :  896, 1024
(II) NVIDIA(0):       VRes, VSyncStart :  600,  601
(II) NVIDIA(0):       VSyncEnd, VTotal :  603,  625
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Unable to use mode "800x600" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 60 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 40.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  840
(II) NVIDIA(0):       HSyncEnd, HTotal :  968, 1056
(II) NVIDIA(0):       VRes, VSyncStart :  600,  601
(II) NVIDIA(0):       VSyncEnd, VTotal :  605,  628
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Unable to use mode "800x600" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 72 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 50.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  856
(II) NVIDIA(0):       HSyncEnd, HTotal :  976, 1040
(II) NVIDIA(0):       VRes, VSyncStart :  600,  637
(II) NVIDIA(0):       VSyncEnd, VTotal :  643,  666
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Unable to use mode "800x600" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 75 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 49.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  816
(II) NVIDIA(0):       HSyncEnd, HTotal :  896, 1056
(II) NVIDIA(0):       VRes, VSyncStart :  600,  601
(II) NVIDIA(0):       VSyncEnd, VTotal :  604,  625
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Unable to use mode "800x600" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 85 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 56.30 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  832
(II) NVIDIA(0):       HSyncEnd, HTotal :  896, 1048
(II) NVIDIA(0):       VRes, VSyncStart :  600,  601
(II) NVIDIA(0):       VSyncEnd, VTotal :  604,  631
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.1 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 87 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 44.90 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1032
(II) NVIDIA(0):       HSyncEnd, HTotal : 1208, 1264
(II) NVIDIA(0):       VRes, VSyncStart :  768,  768
(II) NVIDIA(0):       VSyncEnd, VTotal :  776,  817
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : Interlace
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (87.0 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 60 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 65.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1048
(II) NVIDIA(0):       HSyncEnd, HTotal : 1184, 1344
(II) NVIDIA(0):       VRes, VSyncStart :  768,  771
(II) NVIDIA(0):       VSyncEnd, VTotal :  777,  806
(II) NVIDIA(0):       H/V Polarity     : -/-
(WW) NVIDIA(0):     Unable to use mode "1024x768" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 70 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 75.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1048
(II) NVIDIA(0):       HSyncEnd, HTotal : 1184, 1328
(II) NVIDIA(0):       VRes, VSyncStart :  768,  771
(II) NVIDIA(0):       VSyncEnd, VTotal :  777,  806
(II) NVIDIA(0):       H/V Polarity     : -/-
(WW) NVIDIA(0):     Unable to use mode "1024x768" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 75 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 78.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1040
(II) NVIDIA(0):       HSyncEnd, HTotal : 1136, 1312
(II) NVIDIA(0):       VRes, VSyncStart :  768,  769
(II) NVIDIA(0):       VSyncEnd, VTotal :  772,  800
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Unable to use mode "1024x768" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 85 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 94.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1072
(II) NVIDIA(0):       HSyncEnd, HTotal : 1168, 1376
(II) NVIDIA(0):       VRes, VSyncStart :  768,  769
(II) NVIDIA(0):       VSyncEnd, VTotal :  772,  808
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.0 Hz) out of range
(WW) NVIDIA(0):     (50.000-75.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1152x864":
(II) NVIDIA(0):     1152 x 864 @ 75 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 108.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1152, 1216
(II) NVIDIA(0):       HSyncEnd, HTotal : 1344, 1600
(II) NVIDIA(0):       VRes, VSyncStart :  864,  865
(II) NVIDIA(0):       VSyncEnd, VTotal :  868,  900
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Unable to use mode "1152x864" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x960":
(II) NVIDIA(0):     1280 x 960 @ 60 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 108.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1376
(II) NVIDIA(0):       HSyncEnd, HTotal : 1488, 1800
(II) NVIDIA(0):       VRes, VSyncStart :  960,  961
(II) NVIDIA(0):       VSyncEnd, VTotal :  964, 1000
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Unable to use mode "1280x960" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x960":
(II) NVIDIA(0):     1280 x 960 @ 85 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 148.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1344
(II) NVIDIA(0):       HSyncEnd, HTotal : 1504, 1728
(II) NVIDIA(0):       VRes, VSyncStart :  960,  961
(II) NVIDIA(0):       VSyncEnd, VTotal :  964, 1011
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (85.9 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x1024":
(II) NVIDIA(0):     1280 x 1024 @ 60 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 108.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1328
(II) NVIDIA(0):       HSyncEnd, HTotal : 1440, 1688
(II) NVIDIA(0):       VRes, VSyncStart : 1024, 1025
(II) NVIDIA(0):       VSyncEnd, VTotal : 1028, 1066
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Unable to use mode "1280x1024" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x1024":
(II) NVIDIA(0):     1280 x 1024 @ 75 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 135.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1296
(II) NVIDIA(0):       HSyncEnd, HTotal : 1440, 1688
(II) NVIDIA(0):       VRes, VSyncStart : 1024, 1025
(II) NVIDIA(0):       VSyncEnd, VTotal : 1028, 1066
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Unable to use mode "1280x1024" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x1024":
(II) NVIDIA(0):     1280 x 1024 @ 85 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 157.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1344
(II) NVIDIA(0):       HSyncEnd, HTotal : 1504, 1728
(II) NVIDIA(0):       VRes, VSyncStart : 1024, 1025
(II) NVIDIA(0):       VSyncEnd, VTotal : 1028, 1072
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (91.1 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1200":
(II) NVIDIA(0):     1600 x 1200 @ 60 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 162.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
(II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
(II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Unable to use mode "1600x1200" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1200":
(II) NVIDIA(0):     1600 x 1200 @ 65 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 175.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
(II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
(II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Unable to use mode "1600x1200" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1200":
(II) NVIDIA(0):     1600 x 1200 @ 70 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 189.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
(II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
(II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (87.5 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1200":
(II) NVIDIA(0):     1600 x 1200 @ 75 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 202.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
(II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
(II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (93.8 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1200":
(II) NVIDIA(0):     1600 x 1200 @ 85 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 229.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
(II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
(II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (106.2 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1792x1344":
(II) NVIDIA(0):     1792 x 1344 @ 60 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 204.80 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1792, 1920
(II) NVIDIA(0):       HSyncEnd, HTotal : 2120, 2448
(II) NVIDIA(0):       VRes, VSyncStart : 1344, 1345
(II) NVIDIA(0):       VSyncEnd, VTotal : 1348, 1394
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (83.7 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1792x1344":
(II) NVIDIA(0):     1792 x 1344 @ 75 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 261.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1792, 1888
(II) NVIDIA(0):       HSyncEnd, HTotal : 2104, 2456
(II) NVIDIA(0):       VRes, VSyncStart : 1344, 1345
(II) NVIDIA(0):       VSyncEnd, VTotal : 1348, 1417
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (106.3 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1856x1392":
(II) NVIDIA(0):     1856 x 1392 @ 60 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 218.30 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1856, 1952
(II) NVIDIA(0):       HSyncEnd, HTotal : 2176, 2528
(II) NVIDIA(0):       VRes, VSyncStart : 1392, 1393
(II) NVIDIA(0):       VSyncEnd, VTotal : 1396, 1439
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (86.4 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1856x1392":
(II) NVIDIA(0):     1856 x 1392 @ 75 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 288.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1856, 1984
(II) NVIDIA(0):       HSyncEnd, HTotal : 2208, 2560
(II) NVIDIA(0):       VRes, VSyncStart : 1392, 1393
(II) NVIDIA(0):       VSyncEnd, VTotal : 1396, 1500
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (112.5 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1920x1440":
(II) NVIDIA(0):     1920 x 1440 @ 60 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 234.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1920, 2048
(II) NVIDIA(0):       HSyncEnd, HTotal : 2256, 2600
(II) NVIDIA(0):       VRes, VSyncStart : 1440, 1441
(II) NVIDIA(0):       VSyncEnd, VTotal : 1444, 1500
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (90.0 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1920x1440":
(II) NVIDIA(0):     1920 x 1440 @ 75 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 297.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1920, 2064
(II) NVIDIA(0):       HSyncEnd, HTotal : 2288, 2640
(II) NVIDIA(0):       VRes, VSyncStart : 1440, 1441
(II) NVIDIA(0):       VSyncEnd, VTotal : 1444, 1500
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (112.5 kHz) out of range
(WW) NVIDIA(0):     (24.000-82.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0): --- Done building ModePool for DFP-0 ---
(II) NVIDIA(0): 
(II) NVIDIA(0): 
(II) NVIDIA(0): --- Modes in ModePool for DFP-0 ---
(II) NVIDIA(0): "nvidia-auto-select" :  640 x  480 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "640x480"            :  640 x  480 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "640x480d60"         :  640 x  480 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "640x480_75"         :  640 x  480 @  75.0 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "640x480_73"         :  640 x  480 @  72.8 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "640x480_60"         :  640 x  480 @  59.9 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "576x432"            :  576 x  432 @  75.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "576x432d75"         :  576 x  432 @  75.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "576x432d75_0"       :  576 x  432 @  75.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "576x432d70"         :  576 x  432 @  70.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "576x432d60"         :  576 x  432 @  60.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "512x384"            :  512 x  384 @  75.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "512x384d75"         :  512 x  384 @  75.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "512x384d70"         :  512 x  384 @  70.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "512x384d60"         :  512 x  384 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "416x312"            :  416 x  312 @  74.7 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "416x312d75"         :  416 x  312 @  74.7 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "400x300"            :  400 x  300 @  75.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "400x300d75"         :  400 x  300 @  75.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "400x300d72"         :  400 x  300 @  72.2 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "400x300d60"         :  400 x  300 @  60.3 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "400x300d56"         :  400 x  300 @  56.3 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "320x240"            :  320 x  240 @  75.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "320x240d75"         :  320 x  240 @  75.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "320x240d73"         :  320 x  240 @  72.8 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "320x240d60"         :  320 x  240 @  60.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): --- End of ModePool for DFP-0: ---
(II) NVIDIA(0): 
(II) NVIDIA(0): Assigned Display Device: DFP-0
(WW) NVIDIA(0): No valid modes for "1680x1050"; removing.
(WW) NVIDIA(0): 
(WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(0):     "nvidia-auto-select".
(WW) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0): Virtual screen size determined to be 640 x 480
(II) NVIDIA(0): 
(II) NVIDIA(0): Implicitly adding the following modes to X Screen 0 (these
(II) NVIDIA(0):     will be available via XRandR and XF86VidMode):
(II) NVIDIA(0): 
(II) NVIDIA(0): "640x480_75"   :  640 x  480 @  75.0 Hz 
(II) NVIDIA(0): "640x480_73"   :  640 x  480 @  72.8 Hz 
(II) NVIDIA(0): "640x480_60"   :  640 x  480 @  59.9 Hz 
(II) NVIDIA(0): "576x432"      :  576 x  432 @  75.0 Hz DoubleScan 
(II) NVIDIA(0): "576x432d75_0" :  576 x  432 @  75.0 Hz DoubleScan 
(II) NVIDIA(0): "576x432d70"   :  576 x  432 @  70.0 Hz DoubleScan 
(II) NVIDIA(0): "576x432d60"   :  576 x  432 @  60.1 Hz DoubleScan 
(II) NVIDIA(0): "512x384"      :  512 x  384 @  75.0 Hz DoubleScan 
(II) NVIDIA(0): "512x384d70"   :  512 x  384 @  70.1 Hz DoubleScan 
(II) NVIDIA(0): "512x384d60"   :  512 x  384 @  60.0 Hz DoubleScan 
(II) NVIDIA(0): "416x312"      :  416 x  312 @  74.7 Hz DoubleScan 
(II) NVIDIA(0): "400x300"      :  400 x  300 @  75.1 Hz DoubleScan 
(II) NVIDIA(0): "400x300d72"   :  400 x  300 @  72.2 Hz DoubleScan 
(II) NVIDIA(0): "400x300d60"   :  400 x  300 @  60.3 Hz DoubleScan 
(II) NVIDIA(0): "400x300d56"   :  400 x  300 @  56.3 Hz DoubleScan 
(II) NVIDIA(0): "320x240"      :  320 x  240 @  75.0 Hz DoubleScan 
(II) NVIDIA(0): "320x240d73"   :  320 x  240 @  72.8 Hz DoubleScan 
(II) NVIDIA(0): "320x240d60"   :  320 x  240 @  60.1 Hz DoubleScan 
(II) NVIDIA(0): 
(WW) NVIDIA(0): Unable to get display device DFP-0's EDID; cannot compute DPI
(WW) NVIDIA(0):     from DFP-0's EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) NVIDIA(0): Built-in logo is bigger than the screen.
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing extension GLX
(II) config/hal: Adding input device Macintosh mouse button emulation
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) config/hal: Adding input device Microsoft Comfort Curve Keyboard 2000
(**) Microsoft Comfort Curve Keyboard 2000: always reports core events
(**) Microsoft Comfort Curve Keyboard 2000: Device: "/dev/input/event4"
(II) Microsoft Comfort Curve Keyboard 2000: Found keys
(II) Microsoft Comfort Curve Keyboard 2000: Configuring as keyboard
(II) XINPUT: Adding extended input device "Microsoft Comfort Curve Keyboard 2000" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Microsoft Comfort Curve Keyboard 2000: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Microsoft Comfort Curve Keyboard 2000: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Microsoft Comfort Curve Keyboard 2000: xkb_layout: "us"
(II) config/hal: Adding input device Microsoft Comfort Curve Keyboard 2000
(**) Microsoft Comfort Curve Keyboard 2000: always reports core events
(**) Microsoft Comfort Curve Keyboard 2000: Device: "/dev/input/event5"
(II) Microsoft Comfort Curve Keyboard 2000: Found 1 mouse buttons
(II) Microsoft Comfort Curve Keyboard 2000: Found keys
(II) Microsoft Comfort Curve Keyboard 2000: Configuring as keyboard
(**) Microsoft Comfort Curve Keyboard 2000: YAxisMapping: buttons 4 and 5
(**) Microsoft Comfort Curve Keyboard 2000: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Microsoft Comfort Curve Keyboard 2000" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Microsoft Comfort Curve Keyboard 2000: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Microsoft Comfort Curve Keyboard 2000: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Microsoft Comfort Curve Keyboard 2000: xkb_layout: "us"
(II) config/hal: Adding input device Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): always reports core events
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Device: "/dev/input/event6"
(II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found 3 mouse buttons
(II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found x and y relative axes
(II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Configuring as mouse
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): YAxisMapping: buttons 4 and 5
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)" (type: MOUSE)
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): (accel) keeping acceleration scheme 1
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): (accel) filter chain progression: 2.00
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): (accel) filter stage 0: 20.00 ms
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): (accel) set acceleration profile 0
```

Is it possible that the subsection "Display" isn't being properly reference by another section of the file?

---

### Post by CatKiller on 2009-09-06
Hmm.

```

(WW) NVIDIA(0):     Unable to use mode "1680x1050" for DFP-0; cannot compute
(WW) NVIDIA(0):         backend DFP timings (mode is larger than native
(WW) NVIDIA(0):         backend 640 x 480).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.

```I was hoping that  NoDFPNativeResolutionCheck would tell the nvidia driver not to check against this condition.

I still have no idea why the nvidia driver thinks that 640×480 is the native resolution for your monitor. If we could convince it otherwise, all would be fine. Heck, if your monitor could actually display 640×480, it might make some kind of sense, but it can't. That's why you get the out-of-range message with 

 ```
(II) NVIDIA(0): "nvidia-auto-select" :  640 x  480 @  60.0 Hz DoubleScan  (from: X Server) 
```OK. some other things to try; add in NoVirtualSizeCheck, NoTotalSizeCheck and NoDualLinkDVICheck arguments to the ModeValidation option, so that it says

```
    Option          "ModeValidation"     "NoDFPNativeResolutionCheck, NoVirtualSizeCheck, NoTotalSizeCheck, NoDualLinkDVICheck"
```And if that doesn't work, there's the sledgehammer approach; adding

```
    Option     "ExactModeTimingsDVI"     "True"
``` to the Device section and 

```
    ModeLine     "1680x1050@60"        154.20  1680 1712 2296 2328   1050 1071 1081 1103
``` in the Monitors section, with the Mode in the Screen section changed to "1680x1050@60".

In principle, this should tell the nvidia driver not to do any checks at all, but to just use these timings for the video signal.

On the whole, it would be much easier if your monitor's EDID worked properly, and if the source code to the nvidia driver were available to control for these arbitrary decisions that it makes.

EDIT:
> **tsali said:**
> Is it possible that the subsection "Display" isn't being properly reference by another section of the file?

It's being picked up, but the nvidia driver has decided that because that mode is bigger than 640×480 the mode is invalid, so the X Server helpfully throws it away.

```
(WW) NVIDIA(0): No valid modes for "1680x1050"; removing.
```

---

### Post by tsali on 2009-09-06
I tired adding the additional arguments to the ModeValidation option to no avail.

I added the ""ExactModeTimingsDVI" option and the modeline you specified.

Now, I get a display, but it has a tremendous amount of snow.

I tried another modeline that a guy on newegg had posted and it seems better, but I still have a good bit of "snow" at 1680x1050

new modeline: "1680x1050" 144.55 1680 1800 1984 2240 1050 1051 1054 1086

I also tired generating a modeline with an internet tool, but it gives me the same thing you posted.

We're getting closer.

What do we tweek to remove the snow?

---

### Post by CatKiller on 2009-09-06
> **tsali said:**
>  I also tired generating a modeline with an internet tool, but it gives me the same thing you posted.

You probably used the same one I did, then :)

>  What do we tweek to remove the snow?

You could try adding ```
+HSync +VSync
``` to the end of your modeline. This defines the polarity of the sync signals. According to the Windows driver for that monitor, that's the appropriate polarity.

You should probably make sure that the cable's seated properly.

Otherwise, I'm currently out of ideas.

---

### Post by tsali on 2009-09-07
Thanks for all your help. I'll try the polarity adjustment.

If that doesn't work, it looks like I just have a machine that's not suited for Ubuntu.

They can't all be.

---

### Post by P4man on 2009-09-07
> **tsali said:**
> Thanks for all your help. I'll try the polarity adjustment.

If that doesn't work, it looks like I just have a machine that's not suited for Ubuntu.

They can't all be.

While I wouldnt expect too much from it, perhaps its worth contacting nvidia support and point them to this thread as you and catkiller did a lot of detective work already, and if nothing else, it might help others at some point in the future if nvidia fixes it.

---

### Post by CatKiller on 2009-09-07
> **P4man said:**
> While I wouldnt expect too much from it, perhaps its worth contacting nvidia support and point them to this thread as you and catkiller did a lot of detective work already, and if nothing else, it might help others at some point in the future if nvidia fixes it.

That's not a bad plan. It's their secret test that's causing the problem (modulo the monitor not providing EDID, anyway). They seem to be happy to do weird non-spec stuff to, as they see it, overcome the deficiencies of how everything else works. See, for example, the crazy refresh rate stuff that they do to get unique mode names for TwinView. Unfortunately, this has the side-effect of having to know both the way nVidia does things as well as the way everybody else does.

While being able to modify the source code would be ideal, just being able to configure how the driver works without it doing random things would be a reasonable proxy for being able to get real-world hardware working.

EDIT:

From scanning the nvnews forum, it's possible that just having the  ```
    Option     "ExactModeTimingsDVI"     "True"
``` without specifying a modeline at all might work. Seems weird to me, but that's what people have reported.

---

