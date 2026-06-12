---
title: "Having a horrible time getting linux to recognize my monitor model/settings"
date: 2010-12-19
forum: General Help
---

### Post by switchrodeo720 on 2010-12-19
I've been an Ubuntu user since 8.04. I haven't ever had any issues with setting up display drivers or setting proper resolution, until this week that is.

I have a 22' LCD monitor with a full resolution of 1680x1050. It's Westinghouse brand and have used this same model for years. 

I have a GeForce 8500GT video card and have the current drivers installed. 

Previous to having these issues, I was using Kubuntu 10.10, but before I had Ubuntu 10.04 installed with no issues what so ever.

I decided I liked the Gnome desktop better than KDE, so I wanted to install Ubuntu 10.10. When I did, this is when my resolution difficulties began. I couldn't get anything decent, and after I installed the nvidia drivers it was even worse. I read that there is an incompatibility issue between the new xorg version and the nvidia drivers required for my GeForce 8500 GT. So I thought, no biggy, I'll just go back to 10.04 and be a happy camper. Wrong! After going back to 10.04 I still cannot get full 1680x1050 resolution even though I had it before.

I struggled and struggled trying to figure out why this is happening. I even installed Ubuntu 9.10, Debian 5 and now Fedora 14 trying to see if it was a distro specific issue, but it certainly doesn't seem to be.

At this point I'm thinking that there has to be some sort of problem with my monitor. I'm completely stumped. 

The one clue that seems strange to me is that in 'nvidia-settings' it's detecting my monitor as 'CRT0' rather than displaying my monitor model number like it used to. Is it possible that my monitor isn't providing needed feedback to the drivers, and therefor the drivers don't know that it can handle higher resolution?

Again, I'm stumped so I'm just throwing hail-marys hoping I get lucky.

If anyone has any ideas for me I'd be greatly appreciative. 

Thanks in advance.

---

### Post by switchrodeo720 on 2010-12-20
Any help? Anyone?

Is there more information I should provide?

---

### Post by gordintoronto on 2010-12-20
Did you read the release notes for Ubuntu 10.10: "the new Xorg 1.9 available in Maverick is not compatible with nVidia based chipsets that use the (nvidia-96) and (nvidia-173) drivers."

Exactly what video driver are you using? I saw this elsewhere, but I am unable to test it myself:

"You can update your system with unsupported packages from this untrusted PPA by adding ppa:dajhorn/nvidia-96 to your system's Software Sources." The 96.43.19 driver is reported to work well with Maverick."

---

### Post by switchrodeo720 on 2010-12-21
> **gordintoronto said:**
> Did you read the release notes for Ubuntu 10.10: "the new Xorg 1.9 available in Maverick is not compatible with nVidia based chipsets that use the (nvidia-96) and (nvidia-173) drivers."

Exactly what video driver are you using? I saw this elsewhere, but I am unable to test it myself:

"You can update your system with unsupported packages from this untrusted PPA by adding ppa:dajhorn/nvidia-96 to your system's Software Sources." The 96.43.19 driver is reported to work well with Maverick."

Thanks for the reply. I saw this after the fact, which certainly seemed to be the issue with Ubuntu 10.10. With the current nvidia drivers installed I was only able to get resolution up to about 640x4*. So, when I saw that the nvidia drivers didn't like the new version of xorg, I switched back to Ubuntu 10.04 which I had successfully used before. 

At this point I was still having issues. With the proprietary drivers installed I was able to get higher resolution, but not the full 1680x1050. This was the same when I installed Debian and Fedora 14. 

So, one thing I noticed while trying all these different OSs and researching like mad is that in nvidia-settings the option to save/store my display's EDID was no longer there. I'm interpreting this to mean that for some reason my monitor isn't sending it anymore. Could this be the reason why I cannot get it to work on older versions of xorg?

If so, is there anything I can do to get full resolution?

---

### Post by stoneage on 2010-12-21
> **switchrodeo720 said:**
> I'm interpreting this to mean that for some reason my monitor isn't sending it anymore. 

It is possible it isn't being detected. If you upgraded rather then reinstalled, that might explain why the settings persisted.

---

### Post by switchrodeo720 on 2010-12-21
> **stoneage said:**
> It is possible it isn't being detected. If you upgraded rather then reinstalled, that might explain why the settings persisted.

This was my path, each time reformatting the entire drive. 

Kubuntu 10.10 64 bit (full resolution)
to
Ubuntu 10.10 32 bit (poor resolution)
to 
Ubuntu 10.04 32 bit (poor resolution)
to
Debian 5 32 bit (poor resolution)
to
Fedora 14 32 bit (poor resolution)

and at each re-install I installed the current nvidia drivers.

I think tonight I am going to hook up the monitor to my wife's Windows 7 box and see it it's detected. I'm not sure what else to try at this point.

---

### Post by bobcollard on 2010-12-21
Same basic problem here except I am using a laptop as a desktop with a 21.5" Samsung screen.  The best solution I found was to use XFCE Xubuntu in my current configuration of 10.04.  I tried 10.10 and it worked but it has no advantages over 10.04 which is LTS.  Some people don't like XFCE, so I'm not pushing it off on you.  Just a suggestion.

---

### Post by Stainesy on 2010-12-21
With the switch to KMS (Kernel Mode Setting) since 10.04 and its automatic detection of graphics many users seem to be having a similar issue with various monitors not detected correctly, and/or Hsync and VertRefresh ranges being incorrect. These issues often cause KMS to default to Vesa drivers which provide the user with poorer resolution options. For example I run a Nvidia GeForce GT240 graphics card hooked up to a Samsung SyncMaster 2333 monitor (1920x1080) and neither Ubuntu 10.10 nor LinuxMint 10 could correctly detect the monitor and its settings when using the default Nouveau driver. The issues were reported in the Xorg.log. So I purged Nouveau and installed a Nvida driver and now both OS' run as normal. Answers should be found in your Xorg.log

---

### Post by bobcollard on 2010-12-21
Sorry, no fancy graphics board in here, just a common Intel Mobile 4 chipset.  but, that's my problem.

---

### Post by stoneage on 2010-12-21
I'm one of the victims of this too. I had to generate a modeline and create an xorg.conf. Irony....?

I think mine broke when HAL was introduced. Still broke on 10.04.

---

### Post by switchrodeo720 on 2010-12-21
Well, I appreciate the continued interest in this thread.

I've copied my latest Xorg.log file below. 

One thing I found in the code (that I know to be bad) is the line that says "The EDID read for display device CRT-0 is invalid". I'm not sure how this has all the sudden become invalid.

```
[    28.005] 
X.Org X Server 1.9.1
Release Date: 2010-10-22
[    28.005] X Protocol Version 11, Revision 0
[    28.005] Build Operating System: x86-13 2.6.32-72.el6.bz634452.x86_64 
[    28.005] Current Operating System: Linux diablo 2.6.35.9-64.fc14.i686 #1 SMP Fri Dec 3 12:35:42 UTC 2010 i686
[    28.005] Kernel command line: ro root=/dev/mapper/vg_diablo-lv_root rd_LVM_LV=vg_diablo/lv_root rd_LVM_LV=vg_diablo/lv_swap rd_NO_LUKS rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us noiswmd rhgb quiet nouveau.modeset=0 rdblacklist=nouveau
[    28.005] Build Date: 09 November 2010  08:15:10PM
[    28.006] Build ID: xorg-x11-server 1.9.1-3.fc14 
[    28.006] Current version of pixman: 0.18.4
[    28.006] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    28.006] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    28.006] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Dec 21 21:38:30 2010
[    28.007] (==) Using config file: "/etc/X11/xorg.conf"
[    28.007] (==) Using config directory: "/etc/X11/xorg.conf.d"
[    28.007] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    28.008] (==) ServerLayout "Layout0"
[    28.008] (**) |-->Screen "Screen0" (0)
[    28.008] (**) |   |-->Monitor "Monitor0"
[    28.008] (**) |   |-->Device "Device0"
[    28.008] (**) |-->Input Device "Keyboard0"
[    28.008] (**) |-->Input Device "Mouse0"
[    28.008] (**) Option "Xinerama" "0"
[    28.008] (==) Automatically adding devices
[    28.008] (==) Automatically enabling devices
[    28.009] (**) FontPath set to:
	/usr/share/fonts/default/Type1,
	catalogue:/etc/X11/fontpath.d,
	built-ins
[    28.009] (==) ModulePath set to "/usr/lib/xorg/modules"
[    28.009] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    28.009] (WW) Disabling Keyboard0
[    28.009] (WW) Disabling Mouse0
[    28.010] (II) Loader magic: 0x81fac2c
[    28.010] (II) Module ABI versions:
[    28.010] 	X.Org ANSI C Emulation: 0.4
[    28.010] 	X.Org Video Driver: 8.0
[    28.010] 	X.Org XInput driver : 11.0
[    28.010] 	X.Org Server Extension : 4.0
[    28.011] (--) PCI:*(0:1:0:0) 10de:0421:0000:0000 rev 161, Mem @ 0xfa000000/16777216, 0xd0000000/268435456, 0xf8000000/33554432, I/O @ 0x0000df00/128, BIOS @ 0x????????/131072
[    28.012] (II) LoadModule: "extmod"
[    28.013] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    28.013] (II) Module extmod: vendor="X.Org Foundation"
[    28.013] 	compiled for 1.9.1, module version = 1.0.0
[    28.014] 	Module class: X.Org Server Extension
[    28.014] 	ABI class: X.Org Server Extension, version 4.0
[    28.014] (II) Loading extension SELinux
[    28.014] (II) Loading extension MIT-SCREEN-SAVER
[    28.014] (II) Loading extension XFree86-VidModeExtension
[    28.014] (II) Loading extension XFree86-DGA
[    28.014] (II) Loading extension DPMS
[    28.014] (II) Loading extension XVideo
[    28.014] (II) Loading extension XVideo-MotionCompensation
[    28.014] (II) Loading extension X-Resource
[    28.014] (II) LoadModule: "dbe"
[    28.014] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    28.014] (II) Module dbe: vendor="X.Org Foundation"
[    28.014] 	compiled for 1.9.1, module version = 1.0.0
[    28.014] 	Module class: X.Org Server Extension
[    28.014] 	ABI class: X.Org Server Extension, version 4.0
[    28.015] (II) Loading extension DOUBLE-BUFFER
[    28.015] (II) LoadModule: "glx"
[    28.015] (II) Loading /usr/lib/xorg/modules/extensions/nvidia/libglx.so
[    28.744] (II) Module glx: vendor="NVIDIA Corporation"
[    28.744] 	compiled for 4.0.2, module version = 1.0.0
[    28.744] 	Module class: X.Org Server Extension
[    28.744] (II) NVIDIA GLX Module  260.19.21  Thu Nov  4 20:52:05 PDT 2010
[    28.744] (II) Loading extension GLX
[    28.744] (II) LoadModule: "record"
[    28.745] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    28.745] (II) Module record: vendor="X.Org Foundation"
[    28.745] 	compiled for 1.9.1, module version = 1.13.0
[    28.745] 	Module class: X.Org Server Extension
[    28.745] 	ABI class: X.Org Server Extension, version 4.0
[    28.745] (II) Loading extension RECORD
[    28.745] (II) LoadModule: "dri"
[    28.746] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    28.746] (II) Module dri: vendor="X.Org Foundation"
[    28.746] 	compiled for 1.9.1, module version = 1.0.0
[    28.746] 	ABI class: X.Org Server Extension, version 4.0
[    28.746] (II) Loading extension XFree86-DRI
[    28.746] (II) LoadModule: "dri2"
[    28.747] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    28.747] (II) Module dri2: vendor="X.Org Foundation"
[    28.747] 	compiled for 1.9.1, module version = 1.2.0
[    28.747] 	ABI class: X.Org Server Extension, version 4.0
[    28.747] (II) Loading extension DRI2
[    28.747] (II) LoadModule: "nvidia"
[    28.758] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    28.760] (II) Module nvidia: vendor="NVIDIA Corporation"
[    28.760] 	compiled for 4.0.2, module version = 1.0.0
[    28.760] 	Module class: X.Org Video Driver
[    28.760] (II) NVIDIA dlloader X Driver  260.19.21  Thu Nov  4 20:26:43 PDT 2010
[    28.760] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    28.760] (++) using VT number 1

[    28.766] (II) Loading sub module "fb"
[    28.766] (II) LoadModule: "fb"
[    28.766] (II) Loading /usr/lib/xorg/modules/libfb.so
[    28.767] (II) Module fb: vendor="X.Org Foundation"
[    28.767] 	compiled for 1.9.1, module version = 1.0.0
[    28.767] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    28.767] (II) Loading sub module "wfb"
[    28.767] (II) LoadModule: "wfb"
[    28.768] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    28.768] (II) Module wfb: vendor="X.Org Foundation"
[    28.768] 	compiled for 1.9.1, module version = 1.0.0
[    28.768] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    28.768] (II) Loading sub module "ramdac"
[    28.768] (II) LoadModule: "ramdac"
[    28.768] (II) Module "ramdac" already built-in
[    28.769] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    28.769] (==) NVIDIA(0): RGB weight 888
[    28.769] (==) NVIDIA(0): Default visual is TrueColor
[    28.769] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    28.769] (**) NVIDIA(0): Option "TwinView" "0"
[    28.769] (**) NVIDIA(0): Option "MetaModes" "1680x1050 +0+0"
[    28.769] (**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "CRT-0"
[    28.769] (**) NVIDIA(0): Enabling RENDER acceleration
[    28.770] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[    28.770] (II) NVIDIA(0):     enabled.
[    30.024] (WW) NVIDIA(GPU-0): The EDID read for display device CRT-0 is invalid: the
[    30.024] (WW) NVIDIA(GPU-0):     checksum for EDID version 1 is invalid.
[    30.024] (--) NVIDIA(GPU-0): 
[    30.024] (--) NVIDIA(GPU-0): Raw EDID bytes:
[    30.024] (--) NVIDIA(GPU-0): 
[    30.024] (--) NVIDIA(GPU-0):   00 ff ff ff ff ff ff 00  5c 85 03 22 01 01 01 01
[    30.024] (--) NVIDIA(GPU-0):   0f 11 01 03 68 2f 1e 78  2e c5 85 a4 59 49 9a 24
[    30.024] (--) NVIDIA(GPU-0):   12 50 54 bf ef 00 81 80  81 40 71 4f 95 00 95 0f
[    30.024] (--) NVIDIA(GPU-0):   b3 00 81 c0 81 00 21 39  90 30 62 1a 27 40 68 b0
[    30.024] (--) NVIDIA(GPU-0):   36 00 d9 28 11 00 00 1c  00 00 00 fd 00 38 4c 1e
[    30.024] (--) NVIDIA(GPU-0):   52 10 00 0a 20 20 20 20  20 20 00 00 00 ff 00 30
[    30.024] (--) NVIDIA(GPU-0):   0a 20 20 20 20 20 20 20  20 20 20 20 00 00 b1 fc
[    30.024] (--) NVIDIA(GPU-0):   00 4c 43 4d 2d 32 32 b0  33 0a 20 20 20 20 00 21
[    30.024] (--) NVIDIA(GPU-0): 
[    30.030] (II) NVIDIA(0): NVIDIA GPU GeForce 8500 GT (G86) at PCI:1:0:0 (GPU-0)
[    30.030] (--) NVIDIA(0): Memory: 524288 kBytes
[    30.030] (--) NVIDIA(0): VideoBIOS: 60.86.41.00.00
[    30.030] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    30.030] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    30.030] (--) NVIDIA(0): Connected display device(s) on GeForce 8500 GT at PCI:1:0:0
[    30.030] (--) NVIDIA(0):     CRT-0
[    30.030] (--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
[    30.143] (II) NVIDIA(0): Assigned Display Device: CRT-0
[    30.143] (WW) NVIDIA(0): No valid modes for "1680x1050+0+0"; removing.
[    30.143] (WW) NVIDIA(0): 
[    30.143] (WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
[    30.143] (WW) NVIDIA(0):     "nvidia-auto-select".
[    30.143] (WW) NVIDIA(0): 
[    30.143] (II) NVIDIA(0): Validated modes:
[    30.143] (II) NVIDIA(0):     "nvidia-auto-select"
[    30.143] (II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
[    30.165] (WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
[    30.165] (WW) NVIDIA(0):     from CRT-0's EDID.
[    30.165] (==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
[    30.165] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[    30.165] (--) Depth 24 pixmap format is 32 bpp
[    30.165] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    30.167] (II) NVIDIA(0): Initialized GPU GART.
[    30.172] (II) NVIDIA(0): ACPI: failed to connect to the ACPI event daemon; the daemon
[    30.172] (II) NVIDIA(0):     may not be running or the "AcpidSocketPath" X
[    30.172] (II) NVIDIA(0):     configuration option may not be set correctly.  When the
[    30.172] (II) NVIDIA(0):     ACPI event daemon is available, the NVIDIA X driver will
[    30.172] (II) NVIDIA(0):     try to use it to receive ACPI event notifications.  For
[    30.172] (II) NVIDIA(0):     details, please see the "ConnectToAcpid" and
[    30.172] (II) NVIDIA(0):     "AcpidSocketPath" X configuration options in Appendix B: X
[    30.172] (II) NVIDIA(0):     Config Options in the README.
[    30.175] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    30.219] (II) Loading extension NV-GLX
[    30.253] (II) NVIDIA(0): Initialized OpenGL Acceleration
[    30.258] (==) NVIDIA(0): Disabling shared memory pixmaps
[    30.258] (II) NVIDIA(0): Initialized X Rendering Acceleration
[    30.258] (==) NVIDIA(0): Backing store disabled
[    30.258] (==) NVIDIA(0): Silken mouse enabled
[    30.261] (**) NVIDIA(0): DPMS enabled
[    30.261] (II) Loading extension NV-CONTROL
[    30.262] (II) Loading extension XINERAMA
[    30.262] (II) Loading sub module "dri2"
[    30.262] (II) LoadModule: "dri2"
[    30.262] (II) Reloading /usr/lib/xorg/modules/extensions/libdri2.so
[    30.262] (II) NVIDIA(0): [DRI2] Setup complete
[    30.262] (==) RandR enabled
[    30.262] (II) Initializing built-in extension Generic Event Extension
[    30.262] (II) Initializing built-in extension SHAPE
[    30.263] (II) Initializing built-in extension MIT-SHM
[    30.263] (II) Initializing built-in extension XInputExtension
[    30.263] (II) Initializing built-in extension XTEST
[    30.263] (II) Initializing built-in extension BIG-REQUESTS
[    30.263] (II) Initializing built-in extension SYNC
[    30.263] (II) Initializing built-in extension XKEYBOARD
[    30.263] (II) Initializing built-in extension XC-MISC
[    30.263] (II) Initializing built-in extension XINERAMA
[    30.263] (II) Initializing built-in extension XFIXES
[    30.263] (II) Initializing built-in extension RENDER
[    30.263] (II) Initializing built-in extension RANDR
[    30.263] (II) Initializing built-in extension COMPOSITE
[    30.263] (II) Initializing built-in extension DAMAGE
[    30.263] (II) SELinux: Disabled on system
[    30.266] (II) Initializing extension GLX
[    30.396] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    30.396] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    30.396] (**) Power Button: Applying InputClass "system-setup-keyboard"
[    30.396] (II) LoadModule: "evdev"
[    30.397] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    30.397] (II) Module evdev: vendor="X.Org Foundation"
[    30.397] 	compiled for 1.8.99.905, module version = 2.5.0
[    30.397] 	Module class: X.Org XInput Driver
[    30.397] 	ABI class: X.Org XInput driver, version 11.0
[    30.397] (**) Power Button: always reports core events
[    30.397] (**) Power Button: Device: "/dev/input/event1"
[    30.399] (--) Power Button: Found keys
[    30.399] (II) Power Button: Configuring as keyboard
[    30.399] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    30.399] (**) Option "xkb_rules" "evdev"
[    30.399] (**) Option "xkb_model" "pc105+inet"
[    30.399] (**) Option "xkb_layout" "us"
[    30.399] (**) Option "xkb_options" "terminate:ctrl_alt_bksp,"
[    30.435] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    30.436] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    30.436] (**) Power Button: Applying InputClass "system-setup-keyboard"
[    30.436] (**) Power Button: always reports core events
[    30.436] (**) Power Button: Device: "/dev/input/event0"
[    30.439] (--) Power Button: Found keys
[    30.439] (II) Power Button: Configuring as keyboard
[    30.439] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    30.439] (**) Option "xkb_rules" "evdev"
[    30.439] (**) Option "xkb_model" "pc105+inet"
[    30.439] (**) Option "xkb_layout" "us"
[    30.439] (**) Option "xkb_options" "terminate:ctrl_alt_bksp,"
[    30.442] (II) config/udev: Adding input device Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) (/dev/input/event3)
[    30.442] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Applying InputClass "evdev pointer catchall"
[    30.442] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): always reports core events
[    30.442] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Device: "/dev/input/event3"
[    30.443] (--) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found 3 mouse buttons
[    30.443] (--) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found scroll wheel(s)
[    30.443] (--) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found relative axes
[    30.443] (--) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found x and y relative axes
[    30.443] (II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Configuring as mouse
[    30.443] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): YAxisMapping: buttons 4 and 5
[    30.443] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    30.443] (II) XINPUT: Adding extended input device "Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)" (type: MOUSE)
[    30.443] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): (accel) keeping acceleration scheme 1
[    30.443] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): (accel) acceleration profile 0
[    30.443] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): (accel) acceleration factor: 2.000
[    30.443] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): (accel) acceleration threshold: 4
[    30.443] (II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): initialized for relative axes.
[    30.443] (II) config/udev: Adding input device Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) (/dev/input/mouse0)
[    30.444] (II) No input driver/identifier specified (ignoring)
[    30.444] (II) config/udev: Adding input device Media Center Ed. eHome Infrared Remote Transceiver (1784:0008) (/dev/input/event4)
[    30.444] (**) Media Center Ed. eHome Infrared Remote Transceiver (1784:0008): Applying InputClass "evdev keyboard catchall"
[    30.444] (**) Media Center Ed. eHome Infrared Remote Transceiver (1784:0008): Applying InputClass "system-setup-keyboard"
[    30.444] (**) Media Center Ed. eHome Infrared Remote Transceiver (1784:0008): always reports core events
[    30.444] (**) Media Center Ed. eHome Infrared Remote Transceiver (1784:0008): Device: "/dev/input/event4"
[    30.444] (--) Media Center Ed. eHome Infrared Remote Transceiver (1784:0008): Found keys
[    30.444] (II) Media Center Ed. eHome Infrared Remote Transceiver (1784:0008): Configuring as keyboard
[    30.445] (II) XINPUT: Adding extended input device "Media Center Ed. eHome Infrared Remote Transceiver (1784:0008)" (type: KEYBOARD)
[    30.445] (**) Option "xkb_rules" "evdev"
[    30.445] (**) Option "xkb_model" "pc105+inet"
[    30.445] (**) Option "xkb_layout" "us"
[    30.445] (**) Option "xkb_options" "terminate:ctrl_alt_bksp,"
[    30.450] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    30.450] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    30.450] (**) AT Translated Set 2 keyboard: Applying InputClass "system-setup-keyboard"
[    30.450] (**) AT Translated Set 2 keyboard: always reports core events
[    30.450] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    30.450] (--) AT Translated Set 2 keyboard: Found keys
[    30.450] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    30.450] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    30.450] (**) Option "xkb_rules" "evdev"
[    30.450] (**) Option "xkb_model" "pc105+inet"
[    30.450] (**) Option "xkb_layout" "us"
[    30.450] (**) Option "xkb_options" "terminate:ctrl_alt_bksp,"
```

I have tried to create custom modelines also, but to be honest I have no idea what I'm doing. I cannot seem to find a tutorial that has step a-z on manually building a proper xorg.conf file. I imagine that is because they're all somewhat unique.

If anyone has any pointers I'm definitely up for trying just about anything at this point. 

```
The best solution I found was to use XFCE Xubuntu in my current configuration of 10.04
```

I guess I don't understand why xfce would be different. If it truly is, I'm down for giving it a go.

---

### Post by bobcollard on 2010-12-22
Xubuntu uses a different xrandr, the applet that changes your resolution, and a different Power Manager.

---

### Post by samstreet101 on 2010-12-22
Have you tried using xrandr to add a new modeline to start up in a specified resolution? I find that often helps when I have resolution issues. Though if it is a deeper chipset problem it may not help, I had that happen with one particular machine.

---

### Post by realzippy on 2010-12-22
@ switchrodeo

> **switchrodeo720 said:**
> Well, I appreciate the continued interest in this thread.

I've copied my latest Xorg.log file below. 

One thing I found in the code (that I know to be bad) is the line that says "The EDID read for display device CRT-0 is invalid". I'm not sure how this has all the sudden become invalid.

```
[    28.005] 
X.Org X Server 1.9.1
Release Date: 2010-10-22
[    28.005] X Protocol Version 11, Revision 0
[    28.005] Build Operating System: x86-13 2.6.32-72.el6.bz634452.x86_64 
[    28.005] Current Operating System: Linux diablo 2.6.35.9-64.fc14.i686 #1 SMP Fri Dec 3 12:35:42 UTC 2010 i686
[    28.005] Kernel command line: ro root=/dev/mapper/vg_diablo-lv_root rd_LVM_LV=vg_diablo/lv_root rd_LVM_LV=vg_diablo/lv_swap rd_NO_LUKS rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us noiswmd rhgb quiet nouveau.modeset=0 rdblacklist=nouveau
[    28.005] Build Date: 09 November 2010  08:15:10PM
[    28.006] Build ID: xorg-x11-server 1.9.1-3.fc14 
[    28.006] Current version of pixman: 0.18.4
[    28.006] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    28.006] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    28.006] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Dec 21 21:38:30 2010
[    28.007] (==) Using config file: "/etc/X11/xorg.conf"
[    28.007] (==) Using config directory: "/etc/X11/xorg.conf.d"
[    28.007] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    28.008] (==) ServerLayout "Layout0"
[    28.008] (**) |-->Screen "Screen0" (0)
[    28.008] (**) |   |-->Monitor "Monitor0"
[    28.008] (**) |   |-->Device "Device0"
[    28.008] (**) |-->Input Device "Keyboard0"
[    28.008] (**) |-->Input Device "Mouse0"
[    28.008] (**) Option "Xinerama" "0"
[    28.008] (==) Automatically adding devices
[    28.008] (==) Automatically enabling devices
[    28.009] (**) FontPath set to:
	/usr/share/fonts/default/Type1,
	catalogue:/etc/X11/fontpath.d,
	built-ins
[    28.009] (==) ModulePath set to "/usr/lib/xorg/modules"
[    28.009] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    28.009] (WW) Disabling Keyboard0
[    28.009] (WW) Disabling Mouse0
[    28.010] (II) Loader magic: 0x81fac2c
[    28.010] (II) Module ABI versions:
[    28.010] 	X.Org ANSI C Emulation: 0.4
[    28.010] 	X.Org Video Driver: 8.0
[    28.010] 	X.Org XInput driver : 11.0
[    28.010] 	X.Org Server Extension : 4.0
[    28.011] (--) PCI:*(0:1:0:0) 10de:0421:0000:0000 rev 161, Mem @ 0xfa000000/16777216, 0xd0000000/268435456, 0xf8000000/33554432, I/O @ 0x0000df00/128, BIOS @ 0x????????/131072
[    28.012] (II) LoadModule: "extmod"
[    28.013] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    28.013] (II) Module extmod: vendor="X.Org Foundation"
[    28.013] 	compiled for 1.9.1, module version = 1.0.0
[    28.014] 	Module class: X.Org Server Extension
[    28.014] 	ABI class: X.Org Server Extension, version 4.0
[    28.014] (II) Loading extension SELinux
[    28.014] (II) Loading extension MIT-SCREEN-SAVER
[    28.014] (II) Loading extension XFree86-VidModeExtension
[    28.014] (II) Loading extension XFree86-DGA
[    28.014] (II) Loading extension DPMS
[    28.014] (II) Loading extension XVideo
[    28.014] (II) Loading extension XVideo-MotionCompensation
[    28.014] (II) Loading extension X-Resource
[    28.014] (II) LoadModule: "dbe"
[    28.014] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    28.014] (II) Module dbe: vendor="X.Org Foundation"
[    28.014] 	compiled for 1.9.1, module version = 1.0.0
[    28.014] 	Module class: X.Org Server Extension
[    28.014] 	ABI class: X.Org Server Extension, version 4.0
[    28.015] (II) Loading extension DOUBLE-BUFFER
[    28.015] (II) LoadModule: "glx"
[    28.015] (II) Loading /usr/lib/xorg/modules/extensions/nvidia/libglx.so
[    28.744] (II) Module glx: vendor="NVIDIA Corporation"
[    28.744] 	compiled for 4.0.2, module version = 1.0.0
[    28.744] 	Module class: X.Org Server Extension
[    28.744] (II) NVIDIA GLX Module  260.19.21  Thu Nov  4 20:52:05 PDT 2010
[    28.744] (II) Loading extension GLX
[    28.744] (II) LoadModule: "record"
[    28.745] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    28.745] (II) Module record: vendor="X.Org Foundation"
[    28.745] 	compiled for 1.9.1, module version = 1.13.0
[    28.745] 	Module class: X.Org Server Extension
[    28.745] 	ABI class: X.Org Server Extension, version 4.0
[    28.745] (II) Loading extension RECORD
[    28.745] (II) LoadModule: "dri"
[    28.746] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    28.746] (II) Module dri: vendor="X.Org Foundation"
[    28.746] 	compiled for 1.9.1, module version = 1.0.0
[    28.746] 	ABI class: X.Org Server Extension, version 4.0
[    28.746] (II) Loading extension XFree86-DRI
[    28.746] (II) LoadModule: "dri2"
[    28.747] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    28.747] (II) Module dri2: vendor="X.Org Foundation"
[    28.747] 	compiled for 1.9.1, module version = 1.2.0
[    28.747] 	ABI class: X.Org Server Extension, version 4.0
[    28.747] (II) Loading extension DRI2
[    28.747] (II) LoadModule: "nvidia"
[    28.758] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    28.760] (II) Module nvidia: vendor="NVIDIA Corporation"
[    28.760] 	compiled for 4.0.2, module version = 1.0.0
[    28.760] 	Module class: X.Org Video Driver
[    28.760] (II) NVIDIA dlloader X Driver  260.19.21  Thu Nov  4 20:26:43 PDT 2010
[    28.760] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    28.760] (++) using VT number 1

[    28.766] (II) Loading sub module "fb"
[    28.766] (II) LoadModule: "fb"
[    28.766] (II) Loading /usr/lib/xorg/modules/libfb.so
[    28.767] (II) Module fb: vendor="X.Org Foundation"
[    28.767] 	compiled for 1.9.1, module version = 1.0.0
[    28.767] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    28.767] (II) Loading sub module "wfb"
[    28.767] (II) LoadModule: "wfb"
[    28.768] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    28.768] (II) Module wfb: vendor="X.Org Foundation"
[    28.768] 	compiled for 1.9.1, module version = 1.0.0
[    28.768] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    28.768] (II) Loading sub module "ramdac"
[    28.768] (II) LoadModule: "ramdac"
[    28.768] (II) Module "ramdac" already built-in
[    28.769] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    28.769] (==) NVIDIA(0): RGB weight 888
[    28.769] (==) NVIDIA(0): Default visual is TrueColor
[    28.769] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    28.769] (**) NVIDIA(0): Option "TwinView" "0"
[    28.769] (**) NVIDIA(0): Option "MetaModes" "1680x1050 +0+0"
[    28.769] (**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "CRT-0"
[    28.769] (**) NVIDIA(0): Enabling RENDER acceleration
[    28.770] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[    28.770] (II) NVIDIA(0):     enabled.
[    30.024] (WW) NVIDIA(GPU-0): The EDID read for display device CRT-0 is invalid: the
[    30.024] (WW) NVIDIA(GPU-0):     checksum for EDID version 1 is invalid.
[    30.024] (--) NVIDIA(GPU-0): 
[    30.024] (--) NVIDIA(GPU-0): Raw EDID bytes:
[    30.024] (--) NVIDIA(GPU-0): 
[    30.024] (--) NVIDIA(GPU-0):   00 ff ff ff ff ff ff 00  5c 85 03 22 01 01 01 01
[    30.024] (--) NVIDIA(GPU-0):   0f 11 01 03 68 2f 1e 78  2e c5 85 a4 59 49 9a 24
[    30.024] (--) NVIDIA(GPU-0):   12 50 54 bf ef 00 81 80  81 40 71 4f 95 00 95 0f
[    30.024] (--) NVIDIA(GPU-0):   b3 00 81 c0 81 00 21 39  90 30 62 1a 27 40 68 b0
[    30.024] (--) NVIDIA(GPU-0):   36 00 d9 28 11 00 00 1c  00 00 00 fd 00 38 4c 1e
[    30.024] (--) NVIDIA(GPU-0):   52 10 00 0a 20 20 20 20  20 20 00 00 00 ff 00 30
[    30.024] (--) NVIDIA(GPU-0):   0a 20 20 20 20 20 20 20  20 20 20 20 00 00 b1 fc
[    30.024] (--) NVIDIA(GPU-0):   00 4c 43 4d 2d 32 32 b0  33 0a 20 20 20 20 00 21
[    30.024] (--) NVIDIA(GPU-0): 
[    30.030] (II) NVIDIA(0): NVIDIA GPU GeForce 8500 GT (G86) at PCI:1:0:0 (GPU-0)
[    30.030] (--) NVIDIA(0): Memory: 524288 kBytes
[    30.030] (--) NVIDIA(0): VideoBIOS: 60.86.41.00.00
[    30.030] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    30.030] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    30.030] (--) NVIDIA(0): Connected display device(s) on GeForce 8500 GT at PCI:1:0:0
[    30.030] (--) NVIDIA(0):     CRT-0
[    30.030] (--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
[    30.143] (II) NVIDIA(0): Assigned Display Device: CRT-0
[    30.143] (WW) NVIDIA(0): No valid modes for "1680x1050+0+0"; removing.
[    30.143] (WW) NVIDIA(0): 
[    30.143] (WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
[    30.143] (WW) NVIDIA(0):     "nvidia-auto-select".
[    30.143] (WW) NVIDIA(0): 
[    30.143] (II) NVIDIA(0): Validated modes:
[    30.143] (II) NVIDIA(0):     "nvidia-auto-select"
[    30.143] (II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
[    30.165] (WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
[    30.165] (WW) NVIDIA(0):     from CRT-0's EDID.
[    30.165] (==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
[    30.165] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[    30.165] (--) Depth 24 pixmap format is 32 bpp
[    30.165] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    30.167] (II) NVIDIA(0): Initialized GPU GART.
[    30.172] (II) NVIDIA(0): ACPI: failed to connect to the ACPI event daemon; the daemon
[    30.172] (II) NVIDIA(0):     may not be running or the "AcpidSocketPath" X
[    30.172] (II) NVIDIA(0):     configuration option may not be set correctly.  When the
[    30.172] (II) NVIDIA(0):     ACPI event daemon is available, the NVIDIA X driver will
[    30.172] (II) NVIDIA(0):     try to use it to receive ACPI event notifications.  For
[    30.172] (II) NVIDIA(0):     details, please see the "ConnectToAcpid" and
[    30.172] (II) NVIDIA(0):     "AcpidSocketPath" X configuration options in Appendix B: X
[    30.172] (II) NVIDIA(0):     Config Options in the README.
[    30.175] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    30.219] (II) Loading extension NV-GLX
[    30.253] (II) NVIDIA(0): Initialized OpenGL Acceleration
[    30.258] (==) NVIDIA(0): Disabling shared memory pixmaps
[    30.258] (II) NVIDIA(0): Initialized X Rendering Acceleration
[    30.258] (==) NVIDIA(0): Backing store disabled
[    30.258] (==) NVIDIA(0): Silken mouse enabled
[    30.261] (**) NVIDIA(0): DPMS enabled
[    30.261] (II) Loading extension NV-CONTROL
[    30.262] (II) Loading extension XINERAMA
[    30.262] (II) Loading sub module "dri2"
[    30.262] (II) LoadModule: "dri2"
[    30.262] (II) Reloading /usr/lib/xorg/modules/extensions/libdri2.so
[    30.262] (II) NVIDIA(0): [DRI2] Setup complete
[    30.262] (==) RandR enabled
[    30.262] (II) Initializing built-in extension Generic Event Extension
[    30.262] (II) Initializing built-in extension SHAPE
[    30.263] (II) Initializing built-in extension MIT-SHM
[    30.263] (II) Initializing built-in extension XInputExtension
[    30.263] (II) Initializing built-in extension XTEST
[    30.263] (II) Initializing built-in extension BIG-REQUESTS
[    30.263] (II) Initializing built-in extension SYNC
[    30.263] (II) Initializing built-in extension XKEYBOARD
[    30.263] (II) Initializing built-in extension XC-MISC
[    30.263] (II) Initializing built-in extension XINERAMA
[    30.263] (II) Initializing built-in extension XFIXES
[    30.263] (II) Initializing built-in extension RENDER
[    30.263] (II) Initializing built-in extension RANDR
[    30.263] (II) Initializing built-in extension COMPOSITE
[    30.263] (II) Initializing built-in extension DAMAGE
[    30.263] (II) SELinux: Disabled on system
[    30.266] (II) Initializing extension GLX
[    30.396] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    30.396] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    30.396] (**) Power Button: Applying InputClass "system-setup-keyboard"
[    30.396] (II) LoadModule: "evdev"
[    30.397] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    30.397] (II) Module evdev: vendor="X.Org Foundation"
[    30.397] 	compiled for 1.8.99.905, module version = 2.5.0
[    30.397] 	Module class: X.Org XInput Driver
[    30.397] 	ABI class: X.Org XInput driver, version 11.0
[    30.397] (**) Power Button: always reports core events
[    30.397] (**) Power Button: Device: "/dev/input/event1"
[    30.399] (--) Power Button: Found keys
[    30.399] (II) Power Button: Configuring as keyboard
[    30.399] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    30.399] (**) Option "xkb_rules" "evdev"
[    30.399] (**) Option "xkb_model" "pc105+inet"
[    30.399] (**) Option "xkb_layout" "us"
[    30.399] (**) Option "xkb_options" "terminate:ctrl_alt_bksp,"
[    30.435] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    30.436] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    30.436] (**) Power Button: Applying InputClass "system-setup-keyboard"
[    30.436] (**) Power Button: always reports core events
[    30.436] (**) Power Button: Device: "/dev/input/event0"
[    30.439] (--) Power Button: Found keys
[    30.439] (II) Power Button: Configuring as keyboard
[    30.439] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    30.439] (**) Option "xkb_rules" "evdev"
[    30.439] (**) Option "xkb_model" "pc105+inet"
[    30.439] (**) Option "xkb_layout" "us"
[    30.439] (**) Option "xkb_options" "terminate:ctrl_alt_bksp,"
[    30.442] (II) config/udev: Adding input device Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) (/dev/input/event3)
[    30.442] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Applying InputClass "evdev pointer catchall"
[    30.442] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): always reports core events
[    30.442] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Device: "/dev/input/event3"
[    30.443] (--) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found 3 mouse buttons
[    30.443] (--) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found scroll wheel(s)
[    30.443] (--) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found relative axes
[    30.443] (--) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found x and y relative axes
[    30.443] (II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Configuring as mouse
[    30.443] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): YAxisMapping: buttons 4 and 5
[    30.443] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    30.443] (II) XINPUT: Adding extended input device "Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)" (type: MOUSE)
[    30.443] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): (accel) keeping acceleration scheme 1
[    30.443] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): (accel) acceleration profile 0
[    30.443] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): (accel) acceleration factor: 2.000
[    30.443] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): (accel) acceleration threshold: 4
[    30.443] (II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): initialized for relative axes.
[    30.443] (II) config/udev: Adding input device Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) (/dev/input/mouse0)
[    30.444] (II) No input driver/identifier specified (ignoring)
[    30.444] (II) config/udev: Adding input device Media Center Ed. eHome Infrared Remote Transceiver (1784:0008) (/dev/input/event4)
[    30.444] (**) Media Center Ed. eHome Infrared Remote Transceiver (1784:0008): Applying InputClass "evdev keyboard catchall"
[    30.444] (**) Media Center Ed. eHome Infrared Remote Transceiver (1784:0008): Applying InputClass "system-setup-keyboard"
[    30.444] (**) Media Center Ed. eHome Infrared Remote Transceiver (1784:0008): always reports core events
[    30.444] (**) Media Center Ed. eHome Infrared Remote Transceiver (1784:0008): Device: "/dev/input/event4"
[    30.444] (--) Media Center Ed. eHome Infrared Remote Transceiver (1784:0008): Found keys
[    30.444] (II) Media Center Ed. eHome Infrared Remote Transceiver (1784:0008): Configuring as keyboard
[    30.445] (II) XINPUT: Adding extended input device "Media Center Ed. eHome Infrared Remote Transceiver (1784:0008)" (type: KEYBOARD)
[    30.445] (**) Option "xkb_rules" "evdev"
[    30.445] (**) Option "xkb_model" "pc105+inet"
[    30.445] (**) Option "xkb_layout" "us"
[    30.445] (**) Option "xkb_options" "terminate:ctrl_alt_bksp,"
[    30.450] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    30.450] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    30.450] (**) AT Translated Set 2 keyboard: Applying InputClass "system-setup-keyboard"
[    30.450] (**) AT Translated Set 2 keyboard: always reports core events
[    30.450] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    30.450] (--) AT Translated Set 2 keyboard: Found keys
[    30.450] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    30.450] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    30.450] (**) Option "xkb_rules" "evdev"
[    30.450] (**) Option "xkb_model" "pc105+inet"
[    30.450] (**) Option "xkb_layout" "us"
[    30.450] (**) Option "xkb_options" "terminate:ctrl_alt_bksp,"
```

I have tried to create custom modelines also, but to be honest I have no idea what I'm doing. I cannot seem to find a tutorial that has step a-z on manually building a proper xorg.conf file. I imagine that is because they're all somewhat unique.

If anyone has any pointers I'm definitely up for trying just about anything at this point. 

```
The best solution I found was to use XFCE Xubuntu in my current configuration of 10.04
```

I guess I don't understand why xfce would be different. If it truly is, I'm down for giving it a go.

...could you post your xorg.conf also?
Which Westinghouse monitor is it exactly?

---

### Post by bobcollard on 2010-12-22
realzippy, if you are asking me, file not found in etc/x11, see screenshot:

---

### Post by stoneage on 2010-12-22
10.04 doesn't use an xorg.conf.

Maybe these links are of some use:-

[http://ubuntuforums.org/showthread.php?t=1437980](http://ubuntuforums.org/showthread.php?t=1437980)
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by bobcollard on 2010-12-22
> **stoneage said:**
> 10.04 doesn't use an xorg.conf.

Maybe these links are of some use:-

[http://ubuntuforums.org/showthread.php?t=1437980](http://ubuntuforums.org/showthread.php?t=1437980)
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)
Thanks, but, I'd rather let sleeping dogs lie.  (If it works, don't fix it.)  I'll keep it in mind though.

---

### Post by realzippy on 2010-12-22
> **bobcollard said:**
> realzippy, if you are asking me, file not found in etc/x11, see screenshot:

...sorry,asked OP (*switchrodeo720*).

@ *stoneage*

When running Nvidia/Ati prop. driver(as OP does),you have to have an xorg.conf file...

---

### Post by switchrodeo720 on 2010-12-23
I'm currently working on installing Xubuntu 10.04. I will post back my results. If it doesn't work we'll see where I have to go next.

As it stands right now I cannot tolerate using my computer with 1024x768 resolution on a 22" monitor...it drives me crazy, plus I hate being stumped.

---

### Post by realzippy on 2010-12-23
[I]If it doesn't work we'll see where I have to go next.
[/I]

..posting your xorg.conf (when using the nvidiadriver)

---

### Post by switchrodeo720 on 2010-12-23
> **switchrodeo720 said:**
> I'm currently working on installing Xubuntu 10.04. I will post back my results. If it doesn't work we'll see where I have to go next.

As it stands right now I cannot tolerate using my computer with 1024x768 resolution on a 22" monitor...it drives me crazy, plus I hate being stumped.

Ok, so I now have Xubuntu 10.04 installed. 

With the open source default drivers I could still only get 1024x768 resolution. I installed the current Nvidia driver and managed to get it up to 1152x864. This is something I was unable to do with the Nvidia drivers in Fedora, Ubuntu 10.04/10.10 or Debian 5. I'm not all the way there, but I feel that this is encouraging.

So, with the proprietary drivers installed, here is my xorg.conf file:

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@yellow)  Fri Apr  9 11:51:21 UTC 2010

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: builtin, VertRefresh source: builtin
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       28.0 - 55.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8500 GT"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1152x864 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


```

Any suggestions (of course) will be much appreciated.

---

### Post by switchrodeo720 on 2010-12-24
Ok -- I finally got full resolution. 

I wasn't able to get it using the Nvidia drivers. At one point I actually had to start from scratch and remove the Nvidia drivers and go back to the open source drivers, but I ended up figuring it out based on information found here: [https://wiki.ubuntu.com/X/Config/Resolution#Dynamically%20testing%20different%20resolutions](https://wiki.ubuntu.com/X/Config/Resolution#Dynamically%20testing%20different%20resolutions)

I had to create a new modeline and apply it.

---

### Post by realzippy on 2010-12-24
Using the nvidiadriver,I would have suggested to increase the
Hsync value (limiting resolution)in xorg.conf
from:

28.0 - 55.0
to
28.0 - 83.0

---

### Post by switchrodeo720 on 2010-12-25
> **realzippy said:**
> Using the nvidiadriver,I would have suggested to increase the
Hsync value (limiting resolution)in xorg.conf
from:

28.0 - 55.0
to
28.0 - 83.0

I guess I don't understand what that would do for me if I have to limit the resolution. Please explain.

---

### Post by realzippy on 2010-12-26
> **switchrodeo720 said:**
> I guess I don't understand what that would do for me if I have to limit the resolution. Please explain.

*Limit* resolution?
Thought your problem was not having enough available resolutions when running the nvidiadriver.

From [http://www.epanorama.net/faq/vga2rgb/basics.html#faq](http://www.epanorama.net/faq/vga2rgb/basics.html#faq) :

  31.5 - 31.5 kHz (Standard VGA monitor, 640x480 @ 60 Hz)
  31.5 - 35.1 kHz (Old SVGA monitor, 800x600 @ 56 Hz)
  31.5 - 35.5 kHz (Low-end SVGA, 8514, 1024x768 @ 43 Hz interlaced)
  31.5 - 37.9 kHz (SVGA monitor, 800x600 @ 60 Hz, 640x480 @ 72 Hz)
  31.5 - 48.3 kHz (SVGA non-interlaced, 800x600 @ 72 Hz, 1024x768 @ 60 Hz)
  31.5 - 56.0 kHz (high frequency, 1024x768 @ 70 Hz)
  31.5 - 57.6 kHz (1024x768 @ 72 Hz)
  31.5 - 64.3 kHz (1280x1024 @ 60 Hz)

Means,with *HorizSync 28.0 - [COLOR="Red"]55.0[/COLOR]* you will not get eg. 1280x1024...

---

### Post by switchrodeo720 on 2010-12-27
> **realzippy said:**
> *Limit* resolution?
Thought your problem was not having enough available resolutions when running the nvidiadriver.

Ahh, I understand now. I was confused and thought that you were suggesting that the changes would further limit the resolution.

I'll report back when I have more information.

Thanks again.

---

### Post by switchrodeo720 on 2010-12-27
> **realzippy said:**
> *Limit* resolution?
Thought your problem was not having enough available resolutions when running the nvidiadriver.

Ahh, I understand now. I was confused and thought that you were suggesting that the changes would further limit the resolution.

I'll report back when I have more information.

Thanks again.

---

### Post by needlpt on 2011-03-09
I too am having resolution troubles, but so far this has only baffleed me.

When I first installed Ubuntu 10.04LTS 64-bit, my monitor was working at its maximum resolution of 1920x1080.  At the time (with the computer in the basement on my workbench) I thought this was too hard to read, so I used the GUI to change it to 1360x768.  This was fine, but when I moved it up to my desk today, I wanted the native resolution back.  No such luck.  The maximum choice in the GUI is 1360x768.  Using xrandr also displays a max of 1360x768.

I know the monitor can work at 1920x1080, and can prove so by booting to Win7.  After the first change to the lower resolution, I have rebooted a couple of times, moved the machine upstairs, and played with some settings for a wireless card I have since took out.  One last thing I did was use a different VGA cable in my office, but that shouldn't cause the valid modes to change.

Please help! I want to switch to Ubuntu, but it seems that a lot things don't work!

---

### Post by realzippy on 2011-03-10
The different VGA cable indeed may be the reason;there was a change to the "edid" pins some years ago.Try again the other "working" cable,just to be sure it is no hardware issue.And welcome to the forum!

---

