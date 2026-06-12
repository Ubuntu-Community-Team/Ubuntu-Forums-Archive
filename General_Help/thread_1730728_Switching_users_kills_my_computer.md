---
title: "Switching users kills my computer"
date: 2011-04-16
forum: General Help
---

### Post by NertSkull on 2011-04-16
So if I log into my main account.  Then switch to another account, log out and come back to my main account, then my computer has serious issues.

It doesn't completely crash, but acts as though all resources are being used.  I think its mainly a video card issue (can't tell you why though).  Its like it will be frozen for 10 seconds, then have 1 second where things work, then 10 seconds frozen, etc.

But, if I log off the main account and log onto the second account and log off an back onto the main account I have no problems.  I.e. if I don't "switch users" but instead log off it works.  I can have to people logged in at the same time when I'm on the 2nd account. 

I just can't come back to the first account without having issues.

I don't know if I explained that well enough, but how do I fix this.  I'd like to be able to leave my main account logged in all the time.

---

### Post by NertSkull on 2011-04-19
Anyone?  Is there any more information that could be useful?

---

### Post by Buntumatic on 2011-04-19
You didn't tell us if you can see some runaway process in top. Checking Xorg log would be in order, too. And looking at system messages.

---

### Post by NertSkull on 2011-04-19
Ok, so when I switch back, it appears these are eating up my CPU

Xorg - about 33%
Compiz - about 24%
migration/2 - about 11%

Also, I haven't done a tone of testing, but its worse when I try and switch desktops, but thats not the only time it freezes.

Here is an xorg after a switch.

```
[ 67941.261] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[ 67941.261] X Protocol Version 11, Revision 0
[ 67941.261] Build Operating System: Linux 2.6.24-28-server x86_64 Ubuntu
[ 67941.261] Current Operating System: Linux Main 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 18:42:20 UTC 2011 x86_64
[ 67941.261] Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.35-28-generic root=/dev/mapper/Main_encrypted-Main_OS ro quiet splash
[ 67941.262] Build Date: 09 January 2011  12:14:27PM
[ 67941.262] xorg-server 2:1.9.0-0ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
[ 67941.262] Current version of pixman: 0.18.4
[ 67941.262] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[ 67941.262] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[ 67941.262] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Apr 18 07:30:12 2011
[ 67941.262] (==) Using config file: "/etc/X11/xorg.conf"
[ 67941.262] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[ 67941.262] (==) ServerLayout "Layout0"
[ 67941.262] (**) |-->Screen "Screen0" (0)
[ 67941.262] (**) |   |-->Monitor "Monitor0"
[ 67941.262] (**) |   |-->Device "Device0"
[ 67941.262] (**) |-->Input Device "Keyboard0"
[ 67941.262] (**) |-->Input Device "Mouse0"
[ 67941.262] (**) Option "Xinerama" "0"
[ 67941.262] (==) Automatically adding devices
[ 67941.262] (==) Automatically enabling devices
[ 67941.262] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[ 67941.262] 	Entry deleted from font path.
[ 67941.262] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[ 67941.262] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[ 67941.262] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[ 67941.262] (WW) Disabling Keyboard0
[ 67941.262] (WW) Disabling Mouse0
[ 67941.262] (II) Loader magic: 0x7d17a0
[ 67941.262] (II) Module ABI versions:
[ 67941.262] 	X.Org ANSI C Emulation: 0.4
[ 67941.262] 	X.Org Video Driver: 8.0
[ 67941.262] 	X.Org XInput driver : 11.0
[ 67941.262] 	X.Org Server Extension : 4.0
[ 67941.263] (--) PCI:*(0:6:0:0) 10de:0e22:3842:1371 rev 161, Mem @ 0xfc000000/33554432, 0xd8000000/134217728, 0xd4000000/67108864, I/O @ 0x0000ec00/128, BIOS @ 0x????????/524288
[ 67941.263] (II) Open ACPI successful (/var/run/acpid.socket)
[ 67941.263] (II) LoadModule: "extmod"
[ 67941.263] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[ 67941.274] (II) Module extmod: vendor="X.Org Foundation"
[ 67941.274] 	compiled for 1.9.0, module version = 1.0.0
[ 67941.274] 	Module class: X.Org Server Extension
[ 67941.274] 	ABI class: X.Org Server Extension, version 4.0
[ 67941.274] (II) Loading extension MIT-SCREEN-SAVER
[ 67941.274] (II) Loading extension XFree86-VidModeExtension
[ 67941.274] (II) Loading extension XFree86-DGA
[ 67941.274] (II) Loading extension DPMS
[ 67941.274] (II) Loading extension XVideo
[ 67941.274] (II) Loading extension XVideo-MotionCompensation
[ 67941.274] (II) Loading extension X-Resource
[ 67941.274] (II) LoadModule: "dbe"
[ 67941.274] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[ 67941.279] (II) Module dbe: vendor="X.Org Foundation"
[ 67941.279] 	compiled for 1.9.0, module version = 1.0.0
[ 67941.279] 	Module class: X.Org Server Extension
[ 67941.279] 	ABI class: X.Org Server Extension, version 4.0
[ 67941.279] (II) Loading extension DOUBLE-BUFFER
[ 67941.279] (II) LoadModule: "glx"
[ 67941.279] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[ 67941.320] (II) Module glx: vendor="NVIDIA Corporation"
[ 67941.320] 	compiled for 4.0.2, module version = 1.0.0
[ 67941.320] 	Module class: X.Org Server Extension
[ 67941.320] (II) NVIDIA GLX Module  260.19.06  Mon Sep 13 04:54:41 PDT 2010
[ 67941.320] (II) Loading extension GLX
[ 67941.320] (II) LoadModule: "record"
[ 67941.320] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[ 67941.327] (II) Module record: vendor="X.Org Foundation"
[ 67941.327] 	compiled for 1.9.0, module version = 1.13.0
[ 67941.327] 	Module class: X.Org Server Extension
[ 67941.327] 	ABI class: X.Org Server Extension, version 4.0
[ 67941.327] (II) Loading extension RECORD
[ 67941.327] (II) LoadModule: "dri"
[ 67941.327] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[ 67941.345] (II) Module dri: vendor="X.Org Foundation"
[ 67941.345] 	compiled for 1.9.0, module version = 1.0.0
[ 67941.345] 	ABI class: X.Org Server Extension, version 4.0
[ 67941.345] (II) Loading extension XFree86-DRI
[ 67941.345] (II) LoadModule: "dri2"
[ 67941.345] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[ 67941.351] (II) Module dri2: vendor="X.Org Foundation"
[ 67941.351] 	compiled for 1.9.0, module version = 1.2.0
[ 67941.351] 	ABI class: X.Org Server Extension, version 4.0
[ 67941.351] (II) Loading extension DRI2
[ 67941.351] (II) LoadModule: "nvidia"
[ 67941.351] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[ 67941.370] (II) Module nvidia: vendor="NVIDIA Corporation"
[ 67941.370] 	compiled for 4.0.2, module version = 1.0.0
[ 67941.370] 	Module class: X.Org Video Driver
[ 67941.370] (II) NVIDIA dlloader X Driver  260.19.06  Mon Sep 13 04:31:43 PDT 2010
[ 67941.370] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[ 67941.370] (--) using VT number 8

[ 67941.389] (II) Loading sub module "fb"
[ 67941.389] (II) LoadModule: "fb"
[ 67941.389] (II) Loading /usr/lib/xorg/modules/libfb.so
[ 67941.402] (II) Module fb: vendor="X.Org Foundation"
[ 67941.402] 	compiled for 1.9.0, module version = 1.0.0
[ 67941.402] 	ABI class: X.Org ANSI C Emulation, version 0.4
[ 67941.402] (II) Loading sub module "wfb"
[ 67941.402] (II) LoadModule: "wfb"
[ 67941.403] (II) Loading /usr/lib/xorg/modules/libwfb.so
[ 67941.411] (II) Module wfb: vendor="X.Org Foundation"
[ 67941.411] 	compiled for 1.9.0, module version = 1.0.0
[ 67941.411] 	ABI class: X.Org ANSI C Emulation, version 0.4
[ 67941.411] (II) Loading sub module "ramdac"
[ 67941.411] (II) LoadModule: "ramdac"
[ 67941.411] (II) Module "ramdac" already built-in
[ 67941.411] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[ 67941.411] (==) NVIDIA(0): RGB weight 888
[ 67941.411] (==) NVIDIA(0): Default visual is TrueColor
[ 67941.411] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[ 67941.411] (**) NVIDIA(0): Option "TwinView" "1"
[ 67941.411] (**) NVIDIA(0): Option "MetaModes" "DFP-0: nvidia-auto-select +0+0, DFP-2: nvidia-auto-select +1680+0"
[ 67941.411] (**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "DFP-0"
[ 67941.411] (**) NVIDIA(0): Enabling RENDER acceleration
[ 67941.411] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[ 67941.411] (II) NVIDIA(0):     enabled.
[ 67941.927] (II) NVIDIA(0): NVIDIA GPU GeForce GTX 460 (GF104) at PCI:6:0:0 (GPU-0)
[ 67941.927] (--) NVIDIA(0): Memory: 1048576 kBytes
[ 67941.927] (--) NVIDIA(0): VideoBIOS: 70.04.1b.00.70
[ 67941.927] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[ 67941.927] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[ 67941.927] (--) NVIDIA(0): Connected display device(s) on GeForce GTX 460 at PCI:6:0:0
[ 67941.927] (--) NVIDIA(0):     Acer AL2216W (DFP-0)
[ 67941.927] (--) NVIDIA(0):     VIZ VT420M (DFP-1)
[ 67941.927] (--) NVIDIA(0):     Samsung SyncMaster (DFP-2)
[ 67941.927] (--) NVIDIA(0): Acer AL2216W (DFP-0): 330.0 MHz maximum pixel clock
[ 67941.927] (--) NVIDIA(0): Acer AL2216W (DFP-0): Internal Dual Link TMDS
[ 67941.927] (--) NVIDIA(0): VIZ VT420M (DFP-1): 165.0 MHz maximum pixel clock
[ 67941.927] (--) NVIDIA(0): VIZ VT420M (DFP-1): Internal Single Link TMDS
[ 67941.927] (--) NVIDIA(0): Samsung SyncMaster (DFP-2): 330.0 MHz maximum pixel clock
[ 67941.927] (--) NVIDIA(0): Samsung SyncMaster (DFP-2): Internal Dual Link TMDS
[ 67941.929] (**) NVIDIA(0): TwinView enabled
[ 67941.929] (II) NVIDIA(0): Display Devices found referenced in MetaMode: DFP-0, DFP-2
[ 67941.929] (WW) NVIDIA(0): The EDID for Acer AL2216W (DFP-0) contradicts itself: mode
[ 67941.929] (WW) NVIDIA(0):     "640x480" is specified in the EDID; however, the EDID's
[ 67941.929] (WW) NVIDIA(0):     valid HorizSync range (47.000-84.000 kHz) would exclude
[ 67941.929] (WW) NVIDIA(0):     this mode's HorizSync (31.5 kHz); ignoring HorizSync check
[ 67941.929] (WW) NVIDIA(0):     for mode "640x480".
[ 67941.929] (WW) NVIDIA(0): The EDID for Acer AL2216W (DFP-0) contradicts itself: mode
[ 67941.929] (WW) NVIDIA(0):     "640x480" is specified in the EDID; however, the EDID's
[ 67941.929] (WW) NVIDIA(0):     valid HorizSync range (47.000-84.000 kHz) would exclude
[ 67941.929] (WW) NVIDIA(0):     this mode's HorizSync (37.9 kHz); ignoring HorizSync check
[ 67941.929] (WW) NVIDIA(0):     for mode "640x480".
[ 67941.929] (WW) NVIDIA(0): The EDID for Acer AL2216W (DFP-0) contradicts itself: mode
[ 67941.929] (WW) NVIDIA(0):     "640x480" is specified in the EDID; however, the EDID's
[ 67941.929] (WW) NVIDIA(0):     valid HorizSync range (47.000-84.000 kHz) would exclude
[ 67941.929] (WW) NVIDIA(0):     this mode's HorizSync (37.5 kHz); ignoring HorizSync check
[ 67941.929] (WW) NVIDIA(0):     for mode "640x480".
[ 67941.929] (WW) NVIDIA(0): The EDID for Acer AL2216W (DFP-0) contradicts itself: mode
[ 67941.929] (WW) NVIDIA(0):     "800x600" is specified in the EDID; however, the EDID's
[ 67941.929] (WW) NVIDIA(0):     valid HorizSync range (47.000-84.000 kHz) would exclude
[ 67941.929] (WW) NVIDIA(0):     this mode's HorizSync (35.2 kHz); ignoring HorizSync check
[ 67941.929] (WW) NVIDIA(0):     for mode "800x600".
[ 67941.929] (WW) NVIDIA(0): The EDID for Acer AL2216W (DFP-0) contradicts itself: mode
[ 67941.929] (WW) NVIDIA(0):     "800x600" is specified in the EDID; however, the EDID's
[ 67941.929] (WW) NVIDIA(0):     valid HorizSync range (47.000-84.000 kHz) would exclude
[ 67941.929] (WW) NVIDIA(0):     this mode's HorizSync (37.9 kHz); ignoring HorizSync check
[ 67941.929] (WW) NVIDIA(0):     for mode "800x600".
[ 67941.930] (WW) NVIDIA(0): The EDID for Acer AL2216W (DFP-0) contradicts itself: mode
[ 67941.930] (WW) NVIDIA(0):     "640x480" is specified in the EDID; however, the EDID's
[ 67941.930] (WW) NVIDIA(0):     valid HorizSync range (47.000-84.000 kHz) would exclude
[ 67941.930] (WW) NVIDIA(0):     this mode's HorizSync (31.5 kHz); ignoring HorizSync check
[ 67941.930] (WW) NVIDIA(0):     for mode "640x480".
[ 67941.930] (WW) NVIDIA(0): The EDID for Acer AL2216W (DFP-0) contradicts itself: mode
[ 67941.930] (WW) NVIDIA(0):     "640x480" is specified in the EDID; however, the EDID's
[ 67941.930] (WW) NVIDIA(0):     valid HorizSync range (47.000-84.000 kHz) would exclude
[ 67941.930] (WW) NVIDIA(0):     this mode's HorizSync (37.9 kHz); ignoring HorizSync check
[ 67941.930] (WW) NVIDIA(0):     for mode "640x480".
[ 67941.931] (WW) NVIDIA(0): The EDID for Acer AL2216W (DFP-0) contradicts itself: mode
[ 67941.931] (WW) NVIDIA(0):     "640x480" is specified in the EDID; however, the EDID's
[ 67941.931] (WW) NVIDIA(0):     valid HorizSync range (47.000-84.000 kHz) would exclude
[ 67941.931] (WW) NVIDIA(0):     this mode's HorizSync (37.5 kHz); ignoring HorizSync check
[ 67941.931] (WW) NVIDIA(0):     for mode "640x480".
[ 67941.931] (WW) NVIDIA(0): The EDID for Acer AL2216W (DFP-0) contradicts itself: mode
[ 67941.931] (WW) NVIDIA(0):     "800x600" is specified in the EDID; however, the EDID's
[ 67941.931] (WW) NVIDIA(0):     valid HorizSync range (47.000-84.000 kHz) would exclude
[ 67941.931] (WW) NVIDIA(0):     this mode's HorizSync (35.2 kHz); ignoring HorizSync check
[ 67941.931] (WW) NVIDIA(0):     for mode "800x600".
[ 67941.931] (WW) NVIDIA(0): The EDID for Acer AL2216W (DFP-0) contradicts itself: mode
[ 67941.931] (WW) NVIDIA(0):     "800x600" is specified in the EDID; however, the EDID's
[ 67941.931] (WW) NVIDIA(0):     valid HorizSync range (47.000-84.000 kHz) would exclude
[ 67941.931] (WW) NVIDIA(0):     this mode's HorizSync (37.9 kHz); ignoring HorizSync check
[ 67941.931] (WW) NVIDIA(0):     for mode "800x600".
[ 67941.973] (II) NVIDIA(0): Assigned Display Devices: DFP-0, DFP-2
[ 67941.973] (II) NVIDIA(0): Validated modes:
[ 67941.973] (II) NVIDIA(0):    
[ 67941.973] (II) NVIDIA(0):     "DFP-0:nvidia-auto-select+0+0,DFP-2:nvidia-auto-select+1680+0"
[ 67941.973] (II) NVIDIA(0): Virtual screen size determined to be 2960 x 1050
[ 67941.996] (--) NVIDIA(0): DPI set to (90, 88); computed from "UseEdidDpi" X config
[ 67941.996] (--) NVIDIA(0):     option
[ 67941.996] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[ 67941.996] (--) Depth 24 pixmap format is 32 bpp
[ 67941.996] (II) NVIDIA: Using 3069.00 MB of virtual memory for indirect memory
[ 67941.996] (II) NVIDIA:     access.
[ 67941.997] (II) NVIDIA(0): Initialized GPU GART.
[ 67942.003] (II) NVIDIA(0): Setting mode
[ 67942.003] (II) NVIDIA(0):     "DFP-0:nvidia-auto-select+0+0,DFP-2:nvidia-auto-select+1680+0"
[ 67942.039] (II) Loading extension NV-GLX
[ 67942.134] (II) NVIDIA(0): Initialized OpenGL Acceleration
[ 67942.135] (==) NVIDIA(0): Disabling shared memory pixmaps
[ 67942.135] (II) NVIDIA(0): Initialized X Rendering Acceleration
[ 67942.135] (==) NVIDIA(0): Backing store disabled
[ 67942.135] (==) NVIDIA(0): Silken mouse enabled
[ 67942.159] (**) NVIDIA(0): DPMS enabled
[ 67942.159] (II) Loading extension NV-CONTROL
[ 67942.159] (II) Loading extension XINERAMA
[ 67942.159] (II) Loading sub module "dri2"
[ 67942.159] (II) LoadModule: "dri2"
[ 67942.159] (II) Reloading /usr/lib/xorg/modules/extensions/libdri2.so
[ 67942.159] (II) NVIDIA(0): [DRI2] Setup complete
[ 67942.159] (==) RandR enabled
[ 67942.159] (II) Initializing built-in extension Generic Event Extension
[ 67942.159] (II) Initializing built-in extension SHAPE
[ 67942.159] (II) Initializing built-in extension MIT-SHM
[ 67942.159] (II) Initializing built-in extension XInputExtension
[ 67942.159] (II) Initializing built-in extension XTEST
[ 67942.159] (II) Initializing built-in extension BIG-REQUESTS
[ 67942.159] (II) Initializing built-in extension SYNC
[ 67942.159] (II) Initializing built-in extension XKEYBOARD
[ 67942.159] (II) Initializing built-in extension XC-MISC
[ 67942.159] (II) Initializing built-in extension SECURITY
[ 67942.159] (II) Initializing built-in extension XINERAMA
[ 67942.159] (II) Initializing built-in extension XFIXES
[ 67942.159] (II) Initializing built-in extension RENDER
[ 67942.159] (II) Initializing built-in extension RANDR
[ 67942.159] (II) Initializing built-in extension COMPOSITE
[ 67942.159] (II) Initializing built-in extension DAMAGE
[ 67942.159] (II) Initializing built-in extension GESTURE
[ 67942.161] (II) Initializing extension GLX
[ 67942.202] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[ 67942.208] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[ 67942.208] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[ 67942.208] (II) LoadModule: "evdev"
[ 67942.208] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 67942.240] (II) Module evdev: vendor="X.Org Foundation"
[ 67942.240] 	compiled for 1.9.0, module version = 2.3.2
[ 67942.240] 	Module class: X.Org XInput Driver
[ 67942.240] 	ABI class: X.Org XInput driver, version 11.0
[ 67942.240] (**) Power Button: always reports core events
[ 67942.240] (**) Power Button: Device: "/dev/input/event1"
[ 67942.311] (II) Power Button: Found keys
[ 67942.311] (II) Power Button: Configuring as keyboard
[ 67942.311] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[ 67942.311] (**) Option "xkb_rules" "evdev"
[ 67942.311] (**) Option "xkb_model" "pc105"
[ 67942.311] (**) Option "xkb_layout" "us"
[ 67942.311] (**) Option "xkb_options" "lv3:ralt_switch"
[ 67942.312] (II) XKB: reuse xkmfile /var/lib/xkb/server-0C76CA335E924C2441A31FBFED02D59A89874CA6.xkm
[ 67942.337] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[ 67942.337] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[ 67942.337] (**) Power Button: always reports core events
[ 67942.337] (**) Power Button: Device: "/dev/input/event0"
[ 67942.411] (II) Power Button: Found keys
[ 67942.411] (II) Power Button: Configuring as keyboard
[ 67942.411] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[ 67942.411] (**) Option "xkb_rules" "evdev"
[ 67942.411] (**) Option "xkb_model" "pc105"
[ 67942.411] (**) Option "xkb_layout" "us"
[ 67942.411] (**) Option "xkb_options" "lv3:ralt_switch"
[ 67942.414] (II) config/udev: Adding input device Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) (/dev/input/event2)
[ 67942.414] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Applying InputClass "evdev pointer catchall"
[ 67942.414] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): always reports core events
[ 67942.414] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Device: "/dev/input/event2"
[ 67942.491] (II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found 3 mouse buttons
[ 67942.491] (II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found scroll wheel(s)
[ 67942.491] (II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found relative axes
[ 67942.491] (II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found x and y relative axes
[ 67942.491] (II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Configuring as mouse
[ 67942.491] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): YAxisMapping: buttons 4 and 5
[ 67942.491] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[ 67942.491] (II) XINPUT: Adding extended input device "Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)" (type: MOUSE)
[ 67942.491] (II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): initialized for relative axes.
[ 67942.492] (II) config/udev: Adding input device Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) (/dev/input/mouse0)
[ 67942.492] (II) No input driver/identifier specified (ignoring)
[ 67942.492] (II) config/udev: Adding input device Logitech USB Keyboard (/dev/input/event3)
[ 67942.492] (**) Logitech USB Keyboard: Applying InputClass "evdev keyboard catchall"
[ 67942.492] (**) Logitech USB Keyboard: always reports core events
[ 67942.492] (**) Logitech USB Keyboard: Device: "/dev/input/event3"
[ 67942.492] (II) Logitech USB Keyboard: Found keys
[ 67942.492] (II) Logitech USB Keyboard: Configuring as keyboard
[ 67942.492] (II) XINPUT: Adding extended input device "Logitech USB Keyboard" (type: KEYBOARD)
[ 67942.492] (**) Option "xkb_rules" "evdev"
[ 67942.492] (**) Option "xkb_model" "pc105"
[ 67942.492] (**) Option "xkb_layout" "us"
[ 67942.492] (**) Option "xkb_options" "lv3:ralt_switch"
[ 67942.492] (II) config/udev: Adding input device Logitech USB Keyboard (/dev/input/event4)
[ 67942.492] (**) Logitech USB Keyboard: Applying InputClass "evdev keyboard catchall"
[ 67942.492] (**) Logitech USB Keyboard: always reports core events
[ 67942.492] (**) Logitech USB Keyboard: Device: "/dev/input/event4"
[ 67942.570] (II) Logitech USB Keyboard: Found absolute axes
[ 67942.570] (II) evdev-grail: failed to open grail, no gesture support
[ 67942.570] (II) Logitech USB Keyboard: Found keys
[ 67942.570] (II) Logitech USB Keyboard: Configuring as mouse
[ 67942.570] (II) Logitech USB Keyboard: Configuring as keyboard
[ 67942.570] (II) XINPUT: Adding extended input device "Logitech USB Keyboard" (type: KEYBOARD)
[ 67942.570] (**) Option "xkb_rules" "evdev"
[ 67942.570] (**) Option "xkb_model" "pc105"
[ 67942.570] (**) Option "xkb_layout" "us"
[ 67942.570] (**) Option "xkb_options" "lv3:ralt_switch"
[ 67942.571] (II) Logitech USB Keyboard: initialized for absolute axes.
[ 67942.571] (II) config/udev: Adding input device Logitech Logitech BT Mini-Receiver (/dev/input/event5)
[ 67942.571] (**) Logitech Logitech BT Mini-Receiver: Applying InputClass "evdev keyboard catchall"
[ 67942.571] (**) Logitech Logitech BT Mini-Receiver: always reports core events
[ 67942.571] (**) Logitech Logitech BT Mini-Receiver: Device: "/dev/input/event5"
[ 67942.650] (II) Logitech Logitech BT Mini-Receiver: Found keys
[ 67942.650] (II) Logitech Logitech BT Mini-Receiver: Configuring as keyboard
[ 67942.650] (II) XINPUT: Adding extended input device "Logitech Logitech BT Mini-Receiver" (type: KEYBOARD)
[ 67942.650] (**) Option "xkb_rules" "evdev"
[ 67942.650] (**) Option "xkb_model" "pc105"
[ 67942.650] (**) Option "xkb_layout" "us"
[ 67942.650] (**) Option "xkb_options" "lv3:ralt_switch"
[ 67942.651] (II) config/udev: Adding input device Logitech Logitech BT Mini-Receiver (/dev/input/event6)
[ 67942.651] (**) Logitech Logitech BT Mini-Receiver: Applying InputClass "evdev pointer catchall"
[ 67942.651] (**) Logitech Logitech BT Mini-Receiver: Applying InputClass "evdev keyboard catchall"
[ 67942.651] (**) Logitech Logitech BT Mini-Receiver: always reports core events
[ 67942.651] (**) Logitech Logitech BT Mini-Receiver: Device: "/dev/input/event6"
[ 67942.730] (II) Logitech Logitech BT Mini-Receiver: Found 16 mouse buttons
[ 67942.730] (II) Logitech Logitech BT Mini-Receiver: Found scroll wheel(s)
[ 67942.730] (II) Logitech Logitech BT Mini-Receiver: Found relative axes
[ 67942.730] (II) Logitech Logitech BT Mini-Receiver: Found x and y relative axes
[ 67942.730] (II) Logitech Logitech BT Mini-Receiver: Found absolute axes
[ 67942.730] (II) evdev-grail: failed to open grail, no gesture support
[ 67942.730] (II) Logitech Logitech BT Mini-Receiver: Found keys
[ 67942.730] (II) Logitech Logitech BT Mini-Receiver: Configuring as mouse
[ 67942.730] (II) Logitech Logitech BT Mini-Receiver: Configuring as keyboard
[ 67942.730] (**) Logitech Logitech BT Mini-Receiver: YAxisMapping: buttons 4 and 5
[ 67942.730] (**) Logitech Logitech BT Mini-Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[ 67942.730] (II) XINPUT: Adding extended input device "Logitech Logitech BT Mini-Receiver" (type: KEYBOARD)
[ 67942.730] (**) Option "xkb_rules" "evdev"
[ 67942.730] (**) Option "xkb_model" "pc105"
[ 67942.730] (**) Option "xkb_layout" "us"
[ 67942.730] (**) Option "xkb_options" "lv3:ralt_switch"
[ 67942.731] (II) Logitech Logitech BT Mini-Receiver: initialized for relative axes.
[ 67942.731] (WW) Logitech Logitech BT Mini-Receiver: ignoring absolute axes.
[ 67942.731] (II) config/udev: Adding input device Logitech Logitech BT Mini-Receiver (/dev/input/mouse1)
[ 67942.731] (II) No input driver/identifier specified (ignoring)
[ 76139.212] (II) XKB: reuse xkmfile /var/lib/xkb/server-5C7F4EEEBFF6E9635AC166DF7A844D8F8C403543.xkm
[ 80664.102] (II) XKB: reuse xkmfile /var/lib/xkb/server-5C7F4EEEBFF6E9635AC166DF7A844D8F8C403543.xkm
[ 81679.327] (II) XKB: reuse xkmfile /var/lib/xkb/server-5C7F4EEEBFF6E9635AC166DF7A844D8F8C403543.xkm
[110951.533] (II) XKB: reuse xkmfile /var/lib/xkb/server-5C7F4EEEBFF6E9635AC166DF7A844D8F8C403543.xkm
[164960.491] (II) XKB: reuse xkmfile /var/lib/xkb/server-5C7F4EEEBFF6E9635AC166DF7A844D8F8C403543.xkm
[165094.236] (II) XKB: reuse xkmfile /var/lib/xkb/server-5C7F4EEEBFF6E9635AC166DF7A844D8F8C403543.xkm
[170874.968] (II) XKB: reuse xkmfile /var/lib/xkb/server-5C7F4EEEBFF6E9635AC166DF7A844D8F8C403543.xkm
[170883.573] (II) XKB: reuse xkmfile /var/lib/xkb/server-5C7F4EEEBFF6E9635AC166DF7A844D8F8C403543.xkm
[171592.479] (II) Open ACPI successful (/var/run/acpid.socket)
[171596.494] (II) NVIDIA(0): Setting mode
[171596.494] (II) NVIDIA(0):     "DFP-0:nvidia-auto-select+0+0,DFP-2:nvidia-auto-select+1680+0"
[171597.374] (II) Power Button: Device reopened after 1 attempts.
[171597.421] (II) Power Button: Device reopened after 1 attempts.
[171597.451] (II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Device reopened after 1 attempts.
[171597.471] (II) Logitech USB Keyboard: Device reopened after 1 attempts.
[171597.521] (II) Logitech USB Keyboard: Device reopened after 1 attempts.
[171597.541] (II) Logitech Logitech BT Mini-Receiver: Device reopened after 1 attempts.
[171597.561] (II) Logitech Logitech BT Mini-Receiver: Device reopened after 1 attempts.
[171608.588] (II) XKB: reuse xkmfile /var/lib/xkb/server-5C7F4EEEBFF6E9635AC166DF7A844D8F8C403543.xkm
```

And here is from the syslog around the time I switched back

```
Apr 19 12:17:07 Main pulseaudio[5254]: alsa-util.c:   hw_ptr       : 1014210
Apr 19 12:17:07 Main pulseaudio[5254]: ratelimit.c: 10 events suppressed
Apr 19 12:17:12 Main CRON[5456]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 19 12:17:25 Main kernel: [171574.706120] [UFW BLOCK] IN=eth0 OUT= MAC=xx SRC=xx DST=xx LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=17499 DF PROTO=TCP SPT=722 DPT=33331 WINDOW=5840 RES=0x00 SYN URGP=0 
Apr 19 12:17:43 Main acpid: client 5068[0:0] has disconnected
Apr 19 12:17:43 Main acpid: client 5068[0:0] has disconnected
Apr 19 12:17:43 Main acpid: client connected from 7104[0:0]
Apr 19 12:17:43 Main acpid: 1 client rule loaded
Apr 19 12:17:45 Main kernel: [171594.404346] NVRM: os_schedule: Attempted to yield the CPU while in atomic or interrupt context
Apr 19 12:17:47 Main acpid: client connected from 7104[0:0]
Apr 19 12:17:47 Main acpid: 1 client rule loaded
Apr 19 12:18:04 Main kernel: [171613.410852] NVRM: Xid (0006:00): 53, CMDre 00000000 00000080 00000000 00000005 00000005
Apr 19 12:18:04 Main kernel: [171613.410873] NVRM: Xid (0006:00): 53, CMDre 00000000 00000080 00000000 00000005 00000005
Apr 19 12:18:04 Main kernel: [171613.413063] NVRM: Xid (0006:00): 53, CMDre 00000000 00000080 00000000 00000005 00000005
Apr 19 12:18:04 Main kernel: [171613.413091] NVRM: Xid (0006:00): 53, CMDre 00000000 00000080 00000000 00000005 00000005
Apr 19 12:18:04 Main kernel: [171613.413124] NVRM: Xid (0006:00): 53, CMDre 00000000 00000080 00000000 00000005 00000005
Apr 19 12:18:04 Main kernel: [171613.413158] NVRM: Xid (0006:00): 53, CMDre 00000000 00000080 00000000 00000005 00000005
Apr 19 12:18:04 Main kernel: [171613.488514] NVRM: Xid (0006:00): 53, CMDre 00000000 00000080 00000000 00000005 00000005
Apr 19 12:18:07 Main kernel: [171616.489661] NVRM: Xid (0006:00): 53, CMDre 00000001 00000080 00000000 00000005 0000000b
Apr 19 12:18:07 Main kernel: [171616.489666] NVRM: Xid (0006:00): 53, CMDre 00000002 00000080 00000000 00000005 0000000b
Apr 19 12:18:07 Main kernel: [171616.489675] NVRM: Xid (0006:00): 53, CMDre 00000001 00000080 00000000 00000005 0000000b
Apr 19 12:18:07 Main kernel: [171616.489679] NVRM: Xid (0006:00): 53, CMDre 00000002 00000080 00000000 00000005 0000000b
Apr 19 12:18:07 Main kernel: [171616.489843] NVRM: Xid (0006:00): 53, CMDre 00000000 00000080 00000000 00000005 00000005
Apr 19 12:18:20 Main kernel: [171629.563650] NVRM: Xid (0006:00): 53, CMDre 00000000 00000080 00000000 00000005 00000005
Apr 19 12:18:23 Main kernel: [171632.565031] NVRM: Xid (0006:00): 53, CMDre 00000000 00000080 00000000 00000005 00000005
Apr 19 12:18:35 Main kernel: [171644.897485] NVRM: Xid (0006:00): 53, CMDre 00000000 00000080 00000000 00000005 00000005
Apr 19 12:18:35 Main kernel: [171644.897522] NVRM: Xid (0006:00): 53, CMDre 00000000 00000080 00000000 00000005 00000005
Apr 19 12:21:17 Main nmbd[1770]: [2011/04/19 12:21:17.547732,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Apr 19 12:21:17 Main nmbd[1770]:   find_domain_master_name_query_fail:
Apr 19 12:21:17 Main nmbd[1770]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Apr 19 12:21:17 Main nmbd[1770]:   Unable to sync browse lists in this workgroup.
Apr 19 12:24:22 Main pulseaudio[2279]: ratelimit.c: 464 events suppressed
```

Hopefully that helps a bit more.  I feel like it has to be something with Xorg, compiz or my video card.  Thanks

---

### Post by NertSkull on 2011-04-19
Also, I don't actually have to restart the computer to fix it.

If I come back to my main account and it is freezing, I just need to log out and log back in and it works again.

---

### Post by Buntumatic on 2011-04-19
Compiz is probably the culprit.

---

### Post by NertSkull on 2011-04-19
Is there a way to restart compiz without logging on/off?

I mean yeah I'd like to fix it permanently, but until then is there a way to just send a command to restart it for that session?

Edit
It appears I can do "compiz --replace" to restart compiz, is that an acceptable way to do that?

---

