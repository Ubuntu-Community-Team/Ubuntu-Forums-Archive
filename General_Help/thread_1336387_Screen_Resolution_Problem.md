---
title: "Screen Resolution Problem"
date: 2009-11-24
forum: General Help
---

### Post by Diaz214 on 2009-11-24
I am kinda new to Ubuntu and Linux, and I really like it. I am Currently Using Ubuntu 9.10, however there is a problem that really bothers me. My screen resolution changes everytime I turn on the computer. My current Resolution is 1280X1024, however when I end my cession and restart my computer, the resolution changes to 1024X768. So I was wondering, how can I keep my current screen resolution (1280X1024) from changing, once I log back in? Also, there is another problem. The new Human Login theme, was somehow disable, when I chose the option: Enhance contrast in colors. Is there a way to get it back?

If this helps, I am using:

GeForce2 MX 100/200
32 MB
DELL  E771p (CRT-0)

[I am sorry if I've posted this in the wrong place.

---

### Post by VastOne on 2009-11-24
In a terminal session, try:

```
gksudo nvidia-settings
```

Make your changes and save and you should be good to go

---

### Post by Diaz214 on 2009-11-24
> **VastOne said:**
> In a terminal session, try:
```
gksudo nvidia-settings
```Make your changes and save and you should be good to go


That is what I have been doing for the past Month, in order to change the screen Resolution to 1280X1024; however, it changes but once I turn the computer off and then I turn it back on to use it the screen resolution changes back to 1024X768. I also tried to save it to X configuration file, but it gives me this error: 

> Failed to parse existing X config file '/etc/X11/xorg.conf'!

What am I supposed to do?  :(

---

### Post by raffaele181188 on 2009-11-24
Please post yout /etc/X11/xorg.conf
I often see this error caused by wrong [H|V]sync parameters in that file.
Or maybe you are not running NVidia drivers due to that parsing error ...
Also /var/log/Xorg.0.log can be useful

---

### Post by Diaz214 on 2009-11-24
> **raffaele181188 said:**
> Please post yout /etc/X11/xorg.conf
I often see this error caused by wrong [H|V]sync parameters in that file.
Or maybe you are not running NVidia drivers due to that parsing error ...
Also /var/log/Xorg.0.log can be useful


Okay here is the xorg.conf:

> Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
    Option    "AddARGBGLXVisuals"    "True"
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection


and the Xorg.0.log

> 
X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux samuel-desktop 2.6.31-15-generic #50-Ubuntu SMP Tue Nov 10 14:54:29 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-15-generic root=UUID=d4301d66-a7a9-4156-a82a-f9ecf429e290 ro quiet splash
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Nov 24 14:29:16 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No device specified for screen "Default Screen".
    Using the first device section listed.
(**) |   |-->Device "Default Device"
(==) No monitor specified for screen "Default Screen".
    Using a default monitor configuration.
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

(--) PCI:*(0:1:0:0) 10de:0111:1545:002c nVidia Corporation NV11DDR [GeForce2 MX200] rev 178, Mem @ 0xfd000000/16777216, 0xe8000000/134217728, BIOS @ 0x????????/65536
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  96.43.13  Thu Jun 25 18:56:56 PDT 2009
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
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
    compiled for 1.6.4, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  96.43.13  Thu Jun 25 18:45:26 PDT 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce2 MX 100/200 at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 32768 kBytes
(--) NVIDIA(0): VideoBIOS: 03.11.01.30.65
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are not supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce2 MX 100/200 at
(--) NVIDIA(0):     PCI:1:0:0:
(--) NVIDIA(0):     DELL  E771p (CRT-0)
(--) NVIDIA(0): DELL  E771p (CRT-0): 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(WW) NVIDIA(0): 
(WW) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(WW) NVIDIA(0):     will be used as the requested mode.
(WW) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
(--) NVIDIA(0): DPI set to (86, 84); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
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
(II) config/hal: Adding input device ImPS/2 Logitech Wheel Mouse
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 2.2.5
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(**) ImPS/2 Logitech Wheel Mouse: always reports core events
(**) ImPS/2 Logitech Wheel Mouse: Device: "/dev/input/event4"
(II) ImPS/2 Logitech Wheel Mouse: Found 3 mouse buttons
(II) ImPS/2 Logitech Wheel Mouse: Found x and y relative axes
(II) ImPS/2 Logitech Wheel Mouse: Found scroll wheel(s)
(II) ImPS/2 Logitech Wheel Mouse: Configuring as mouse
(**) ImPS/2 Logitech Wheel Mouse: YAxisMapping: buttons 4 and 5
(**) ImPS/2 Logitech Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "ImPS/2 Logitech Wheel Mouse" (type: MOUSE)
(**) ImPS/2 Logitech Wheel Mouse: (accel) keeping acceleration scheme 1
(**) ImPS/2 Logitech Wheel Mouse: (accel) filter chain progression: 2.00
(**) ImPS/2 Logitech Wheel Mouse: (accel) filter stage 0: 20.00 ms
(**) ImPS/2 Logitech Wheel Mouse: (accel) set acceleration profile 0
(II) ImPS/2 Logitech Wheel Mouse: initialized for relative axes.
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
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
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) NVIDIA(0): Setting mode "CRT-0:1280x1024@1280x1024+0+0"

---

### Post by Diaz214 on 2009-11-25
Sorry for the double post, but this thread appeared lost already. And help is really appreciated. Well I found some stuff on the web, but they are explained like if it was to an expert when I am barely a newbie.

---

### Post by raffaele181188 on 2009-11-25
How did you install NVidia drivers? Did you let them create your xorg.conf or did you copy it from any source?

---

### Post by Arup on 2009-11-25
gksudo nvidia-settings, select your resolution and click on save to x configuration file.

---

### Post by Diaz214 on 2009-11-25
> How did you install NVidia drivers? Did you let them create your xorg.conf or did you copy it from any source? 	

I installed the drivers from the Hardware drivers tool in ubuntu. System>administration>hardware drivers

> **Arup said:**
> gksudo nvidia-settings, select your resolution and click on save to x configuration file.

If you read my previous two post you'll know that I been trying to do that but I get the error message.

>  			 				Failed to parse existing X config file '/etc/X11/xorg.conf'! 			 		

---

### Post by Arup on 2009-11-25
> **Diaz214 said:**
> I installed the drivers from the Hardware drivers tool in ubuntu. System>administration>hardware drivers



If you read my previous two post you'll know that I been trying to do that but I get the error message.

Thats an issue with the built in drivers, do a gksudo nvidia-xconfig, this will then create the xconfig file, then do a gksudo nvidia-settings and select your rez and save to X.

---

### Post by Diaz214 on 2009-11-25
> **Arup said:**
> Thats an issue with the built in drivers, do a gksudo nvidia-xconfig, this will then create the xconfig file, then do a gksudo nvidia-settings and select your rez and save to X.

See, you should had told me that step first!:P Thanks for explaining this to a newbie. *lol*
Well as for the other issue in my first post... Is there anyway of getting the Human login theme back to normal, or is this just a bug of 9.10?

---

### Post by Arup on 2009-11-25
> **Diaz214 said:**
> See, you should had told me that step first!:P Thanks for explaining this to a newbie. *lol*
Well as for the other issue in my first post... Is there anyway of getting the Human login theme back to normal, or is this just a bug of 9.10?

My oversight, I didnt notice that you were using the built-in drivers. Since Ubuntu Karmic uses Grub 2 by default, there is some tweaking needed to make other GDM themes work. Its no bug here, the new login is part of Karmic.

---

### Post by Diaz214 on 2009-11-25
> **Arup said:**
> My oversight, I didnt notice that you were using the built-in drivers. Since Ubuntu Karmic uses Grub 2 by default, there is some tweaking needed to make other GDM themes work. Its no bug here, the new login is part of Karmic.

Oh, I dont know if I made my self clear on my second issue. Well here is whats going on.
You see this is what the normal login looks like in ubuntu 9.10 like you said:
[http://dl.maximumpc.com/galleries/ubuntu910/karmic-rc-login_sm.png](http://dl.maximumpc.com/galleries/ubuntu910/karmic-rc-login_sm.png)
Aren't I correct? Well heres the problem. From the options menu on the login screen I chose "enhanced colors contrast" and then the theme somehow change into this:
[http://i196.photobucket.com/albums/aa150/Diaz-soul/ubuntu_login1.png](http://i196.photobucket.com/albums/aa150/Diaz-soul/ubuntu_login1.png)

Well I unchecked the option "enhanced colors contrast" to try to get the theme back, however it stayed the same. Now, is there away to get the theme back to normal? I know that I cant choose other GDM themes, like in prevous ubunutu versions, but I dont want to change the login theme. I just want to get it back to normal. By the way, thanks to all of you for the help.

---

### Post by Arup on 2009-11-25
Open Synaptic, find gdm and then select mark for reinstall.

---

### Post by Diaz214 on 2009-11-25
> **Arup said:**
> Open Synaptic, find gdm and then select mark for reinstall.
 
Thank you so much for your help! Well I did as you said. I opened synaptic, searched for gdm and mark anything dealing with gdm, for reinstall. Well it worked! I got the login back to normal, however, once I Logged into my account, the top bar disappeared on the window. Heres a screenshot:

[http://i196.photobucket.com/albums/aa150/Diaz-soul/Screenshot-3.png](http://i196.photobucket.com/albums/aa150/Diaz-soul/Screenshot-3.png)

As you can see from the screenshot, the title bars are gone, and that big white box is what happened to the terminal... I've looked if it was a compizConfig setting that was causing it, but everything looks normal. I disabled visual effects to see if that was the problem, but it appears not. So a little help on this issue would be nice.

---

### Post by Diaz214 on 2009-11-25
Ah thanks for everyones help! I've solve my problem. I wen to Synaptic Manager again and I selected everything dealing with GDM for reinstallation. I then Uninstall CompizConfig manager and reinstalled it again. I restarted the computer and wala! Everything is cool!
Here's screenshot: [http://i196.photobucket.com/albums/aa150/Diaz-soul/Screenshot-4.png](http://i196.photobucket.com/albums/aa150/Diaz-soul/Screenshot-4.png)

Thanks for everyones help!

---

### Post by cebif on 2009-12-19
> **Arup said:**
> Thats an issue with the built in drivers, do a gksudo nvidia-xconfig, this will then create the xconfig file, then do a gksudo nvidia-settings and select your rez and save to X.
I had the same problem enabling the recommended driver (version 185) in System, Administration, Hardware drivers.
I solved it by disabling the driver and after a restart selecting version 173 then another restart and it was fixed.
My video card is a GeForce 7950 GT and lcd monitor is Sony MFM-HT75W. The native resolution for this monitor is: 1280x768.

---

