---
title: "xf86-vidoe-intel"
date: 2011-09-16
forum: General Help
---

### Post by nos09 on 2011-09-16
i been having a problem installing running compiz on my ubuntu since last couple of releases (9.04 worked just fine !) so just now i thought i might try installing arch linux and to my surprise in arch with xf86-video-intel drivers everything is working fine !!! 

so i m just wondering what drivers ubuntu uses now ?!?! how do i remove them ? and how to install the xf86 intel drivers ?! the arch repo have this driver in there would it work for me, i m guessing they are tar balls so it should work..

and here is my xorg.0.log file's output :

```
[    19.777] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    19.777] X Protocol Version 11, Revision 0
[    19.777] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    19.777] Current Operating System: Linux olympians 3.0.0-0300-generic #201107220917 SMP Fri Jul 22 10:10:37 UTC 2011 i686
[    19.777] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-0300-generic root=UUID=077b811a-33ac-4cb9-8913-46a3e1949f6a ro quiet splash vt.handoff=7
[    19.777] Build Date: 11 August 2011  03:47:56PM
[    19.777] xorg-server 2:1.10.1-1ubuntu1.2 (For technical support please see http://www.ubuntu.com/support) 
[    19.792] Current version of pixman: 0.20.2
[    19.792] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    19.792] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    19.793] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Sep 16 21:32:13 2011
[    19.837] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    19.886] (==) No Layout section.  Using the first Screen section.
[    19.886] (==) No screen section available. Using defaults.
[    19.886] (**) |-->Screen "Default Screen Section" (0)
[    19.886] (**) |   |-->Monitor "<default monitor>"
[    19.887] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    19.887] (==) Automatically adding devices
[    19.887] (==) Automatically enabling devices
[    19.912] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    19.912] 	Entry deleted from font path.
[    19.912] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    19.912] 	Entry deleted from font path.
[    19.912] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    19.912] 	Entry deleted from font path.
[    19.925] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    19.925] 	Entry deleted from font path.
[    19.925] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    19.925] 	Entry deleted from font path.
[    19.960] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    19.960] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    19.960] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    19.960] (II) Loader magic: 0x81ffde0
[    19.960] (II) Module ABI versions:
[    19.960] 	X.Org ANSI C Emulation: 0.4
[    19.960] 	X.Org Video Driver: 10.0
[    19.960] 	X.Org XInput driver : 12.3
[    19.960] 	X.Org Server Extension : 5.0
[    19.961] (--) PCI:*(0:0:2:0) 8086:2772:1019:2624 rev 2, Mem @ 0xfea80000/524288, 0xd0000000/268435456, 0xfea40000/262144, I/O @ 0x0000dc00/8
[    19.961] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    19.961] (II) LoadModule: "extmod"
[    20.019] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    20.027] (II) Module extmod: vendor="X.Org Foundation"
[    20.027] 	compiled for 1.10.1, module version = 1.0.0
[    20.027] 	Module class: X.Org Server Extension
[    20.027] 	ABI class: X.Org Server Extension, version 5.0
[    20.027] (II) Loading extension MIT-SCREEN-SAVER
[    20.027] (II) Loading extension XFree86-VidModeExtension
[    20.027] (II) Loading extension XFree86-DGA
[    20.027] (II) Loading extension DPMS
[    20.027] (II) Loading extension XVideo
[    20.027] (II) Loading extension XVideo-MotionCompensation
[    20.027] (II) Loading extension X-Resource
[    20.027] (II) LoadModule: "dbe"
[    20.027] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    20.036] (II) Module dbe: vendor="X.Org Foundation"
[    20.036] 	compiled for 1.10.1, module version = 1.0.0
[    20.036] 	Module class: X.Org Server Extension
[    20.036] 	ABI class: X.Org Server Extension, version 5.0
[    20.036] (II) Loading extension DOUBLE-BUFFER
[    20.036] (II) LoadModule: "glx"
[    20.036] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    21.020] (II) Module glx: vendor="NVIDIA Corporation"
[    21.020] 	compiled for 4.0.2, module version = 1.0.0
[    21.020] 	Module class: X.Org Server Extension
[    21.020] (II) NVIDIA GLX Module  270.41.06  Mon Apr 18 15:11:28 PDT 2011
[    21.020] (II) Loading extension GLX
[    21.020] (II) LoadModule: "record"
[    21.021] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    21.028] (II) Module record: vendor="X.Org Foundation"
[    21.028] 	compiled for 1.10.1, module version = 1.13.0
[    21.028] 	Module class: X.Org Server Extension
[    21.028] 	ABI class: X.Org Server Extension, version 5.0
[    21.028] (II) Loading extension RECORD
[    21.028] (II) LoadModule: "dri"
[    21.028] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    21.049] (II) Module dri: vendor="X.Org Foundation"
[    21.049] 	compiled for 1.10.1, module version = 1.0.0
[    21.049] 	ABI class: X.Org Server Extension, version 5.0
[    21.049] (II) Loading extension XFree86-DRI
[    21.049] (II) LoadModule: "dri2"
[    21.049] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    21.062] (II) Module dri2: vendor="X.Org Foundation"
[    21.062] 	compiled for 1.10.1, module version = 1.2.0
[    21.062] 	ABI class: X.Org Server Extension, version 5.0
[    21.062] (II) Loading extension DRI2
[    21.062] (==) Matched intel as autoconfigured driver 0
[    21.062] (==) Matched vesa as autoconfigured driver 1
[    21.062] (==) Matched fbdev as autoconfigured driver 2
[    21.062] (==) Assigned the driver to the xf86ConfigLayout
[    21.062] (II) LoadModule: "intel"
[    21.091] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    21.114] (II) Module intel: vendor="X.Org Foundation"
[    21.114] 	compiled for 1.10.1, module version = 2.14.0
[    21.114] 	Module class: X.Org Video Driver
[    21.114] 	ABI class: X.Org Video Driver, version 10.0
[    21.114] (II) LoadModule: "vesa"
[    21.115] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    21.127] (II) Module vesa: vendor="X.Org Foundation"
[    21.127] 	compiled for 1.10.0, module version = 2.3.0
[    21.127] 	Module class: X.Org Video Driver
[    21.127] 	ABI class: X.Org Video Driver, version 10.0
[    21.127] (II) LoadModule: "fbdev"
[    21.128] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    21.130] (II) Module fbdev: vendor="X.Org Foundation"
[    21.130] 	compiled for 1.10.0, module version = 0.4.2
[    21.130] 	ABI class: X.Org Video Driver, version 10.0
[    21.130] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
	Sandybridge, Sandybridge
[    21.131] (II) VESA: driver for VESA chipsets: vesa
[    21.131] (II) FBDEV: driver for framebuffer: fbdev
[    21.131] (++) using VT number 7

[    21.134] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    21.134] (WW) Falling back to old probe method for vesa
[    21.134] (WW) Falling back to old probe method for fbdev
[    21.134] (II) Loading sub module "fbdevhw"
[    21.134] (II) LoadModule: "fbdevhw"
[    21.134] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    21.146] (II) Module fbdevhw: vendor="X.Org Foundation"
[    21.146] 	compiled for 1.10.1, module version = 0.0.2
[    21.146] 	ABI class: X.Org Video Driver, version 10.0
[    21.146] drmOpenDevice: node name is /dev/dri/card0
[    21.146] drmOpenDevice: open result is 8, (OK)
[    21.146] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    21.146] drmOpenDevice: node name is /dev/dri/card0
[    21.146] drmOpenDevice: open result is 8, (OK)
[    21.146] drmOpenByBusid: drmOpenMinor returns 8
[    21.146] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    21.146] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    21.146] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    21.146] (==) intel(0): RGB weight 888
[    21.146] (==) intel(0): Default visual is TrueColor
[    21.146] (II) intel(0): Integrated Graphics Chipset: Intel(R) 945G
[    21.146] (--) intel(0): Chipset: "945G"
[    21.146] (**) intel(0): Relaxed fencing disabled
[    21.146] (**) intel(0): Tiling enabled
[    21.146] (**) intel(0): SwapBuffers wait enabled
[    21.146] (==) intel(0): video overlay key set to 0x101fe
[    21.229] (II) intel(0): Output VGA1 has no monitor section
[    21.291] (II) intel(0): EDID for output VGA1
[    21.291] (II) intel(0): Manufacturer: GSM  Model: 4432  Serial#: 2905
[    21.291] (II) intel(0): Year: 2007  Week: 27
[    21.291] (II) intel(0): EDID Version: 1.1
[    21.291] (II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    21.291] (II) intel(0): Sync:  Separate  Composite  SyncOnGreen
[    21.291] (II) intel(0): Max Image Size [cm]: horiz.: 34  vert.: 27
[    21.291] (II) intel(0): Gamma: 2.20
[    21.291] (II) intel(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    21.291] (II) intel(0): First detailed timing is preferred mode
[    21.291] (II) intel(0): redX: 0.641 redY: 0.342   greenX: 0.292 greenY: 0.611
[    21.291] (II) intel(0): blueX: 0.147 blueY: 0.068   whiteX: 0.313 whiteY: 0.329
[    21.291] (II) intel(0): Supported established timings:
[    21.291] (II) intel(0): 720x400@70Hz
[    21.291] (II) intel(0): 640x480@60Hz
[    21.291] (II) intel(0): 640x480@75Hz
[    21.291] (II) intel(0): 800x600@60Hz
[    21.291] (II) intel(0): 800x600@75Hz
[    21.291] (II) intel(0): 832x624@75Hz
[    21.291] (II) intel(0): 1024x768@60Hz
[    21.291] (II) intel(0): 1024x768@75Hz
[    21.291] (II) intel(0): 1280x1024@75Hz
[    21.291] (II) intel(0): 1152x864@75Hz
[    21.291] (II) intel(0): Manufacturer's mask: 0
[    21.291] (II) intel(0): Supported standard timings:
[    21.291] (II) intel(0): #0: hsize: 640  vsize 480  refresh: 75  vid: 20273
[    21.291] (II) intel(0): #1: hsize: 800  vsize 600  refresh: 75  vid: 20293
[    21.291] (II) intel(0): #2: hsize: 1024  vsize 768  refresh: 75  vid: 20321
[    21.291] (II) intel(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    21.291] (II) intel(0): Supported detailed timing:
[    21.291] (II) intel(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
[    21.291] (II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[    21.291] (II) intel(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[    21.291] (II) intel(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 145 MHz
[    21.291] (II) intel(0): Monitor name: L1752S
[    21.291] (II) intel(0): Monitor name: 
[    21.291] (II) intel(0): EDID (in hex):
[    21.291] (II) intel(0): 	00ffffffffffff001e6d3244590b0000
[    21.291] (II) intel(0): 	1b1101016e221b78ea2ee5a4574a9c25
[    21.291] (II) intel(0): 	115054a56b80314f454f614f81800101
[    21.291] (II) intel(0): 	010101010101302a009851002a403070
[    21.291] (II) intel(0): 	1300520e1100001e000000fd00384b1e
[    21.291] (II) intel(0): 	530e000a202020202020000000fc004c
[    21.291] (II) intel(0): 	31373532530a202020202020000000fc
[    21.291] (II) intel(0): 	00200a202020202020202020202000c9
[    21.291] (II) intel(0): EDID vendor "GSM", prod id 17458
[    21.291] (II) intel(0): Using EDID range info for horizontal sync
[    21.291] (II) intel(0): Using EDID range info for vertical refresh
[    21.291] (II) intel(0): Printing DDC gathered Modelines:
[    21.292] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    21.292] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    21.292] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    21.292] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    21.292] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    21.292] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    21.292] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    21.292] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    21.292] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    21.292] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    21.292] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    21.292] (II) intel(0): Printing probed modes for output VGA1
[    21.292] (II) intel(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    21.292] (II) intel(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    21.292] (II) intel(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    21.292] (II) intel(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
[    21.292] (II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    21.292] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    21.292] (II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    21.292] (II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    21.292] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    21.292] (II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    21.292] (II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    21.292] (II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    21.292] (II) intel(0): Output VGA1 connected
[    21.292] (II) intel(0): Using exact sizes for initial modes
[    21.292] (II) intel(0): Output VGA1 using initial mode 1280x1024
[    21.292] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    21.292] (II) intel(0): Kernel page flipping support detected, enabling
[    21.292] (**) intel(0): Display dimensions: (340, 270) mm
[    21.292] (**) intel(0): DPI set to (95, 96)
[    21.292] (II) Loading sub module "fb"
[    21.292] (II) LoadModule: "fb"
[    21.293] (II) Loading /usr/lib/xorg/modules/libfb.so
[    21.302] (II) Module fb: vendor="X.Org Foundation"
[    21.302] 	compiled for 1.10.1, module version = 1.0.0
[    21.302] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    21.302] (II) UnloadModule: "vesa"
[    21.302] (II) Unloading vesa
[    21.302] (II) UnloadModule: "fbdev"
[    21.302] (II) Unloading fbdev
[    21.302] (II) UnloadModule: "fbdevhw"
[    21.302] (II) Unloading fbdevhw
[    21.302] (==) Depth 24 pixmap format is 32 bpp
[    21.302] (==) intel(0): VideoRam: 262144 KB
[    21.302] (II) intel(0): [DRI2] Setup complete
[    21.302] (II) intel(0): [DRI2]   DRI driver: i915
[    21.303] (II) intel(0): Allocated new frame buffer 1280x1024 stride 8192, tiled
[    21.319] (II) UXA(0): Driver registered support for the following operations:
[    21.319] (II)         solid
[    21.319] (II)         copy
[    21.319] (II)         composite (RENDER acceleration)
[    21.319] (II)         put_image
[    21.319] (II)         get_image
[    21.319] (==) intel(0): Backing store disabled
[    21.319] (==) intel(0): Silken mouse enabled
[    21.320] (II) intel(0): Initializing HW Cursor
[    21.352] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    21.352] (==) intel(0): DPMS enabled
[    21.352] (==) intel(0): Intel XvMC decoder disabled
[    21.352] (II) intel(0): Set up textured video
[    21.352] (II) intel(0): Set up overlay video
[    21.352] (II) intel(0): direct rendering: DRI2 Enabled
[    21.352] (==) intel(0): hotplug detection: "enabled"
[    21.352] (--) RandR disabled
[    21.352] (II) Initializing built-in extension Generic Event Extension
[    21.352] (II) Initializing built-in extension SHAPE
[    21.352] (II) Initializing built-in extension MIT-SHM
[    21.352] (II) Initializing built-in extension XInputExtension
[    21.352] (II) Initializing built-in extension XTEST
[    21.352] (II) Initializing built-in extension BIG-REQUESTS
[    21.352] (II) Initializing built-in extension SYNC
[    21.352] (II) Initializing built-in extension XKEYBOARD
[    21.352] (II) Initializing built-in extension XC-MISC
[    21.352] (II) Initializing built-in extension SECURITY
[    21.352] (II) Initializing built-in extension XINERAMA
[    21.352] (II) Initializing built-in extension XFIXES
[    21.352] (II) Initializing built-in extension RENDER
[    21.352] (II) Initializing built-in extension RANDR
[    21.352] (II) Initializing built-in extension COMPOSITE
[    21.352] (II) Initializing built-in extension DAMAGE
[    21.352] (II) Initializing built-in extension GESTURE
[    21.365] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
[    21.375] (II) intel(0): Setting screen physical size to 338 x 270
[    21.463] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    21.476] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    21.476] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    21.476] (II) LoadModule: "evdev"
[    21.476] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.503] (II) Module evdev: vendor="X.Org Foundation"
[    21.503] 	compiled for 1.10.0.902, module version = 2.6.0
[    21.503] 	Module class: X.Org XInput Driver
[    21.503] 	ABI class: X.Org XInput driver, version 12.3
[    21.503] (II) Using input driver 'evdev' for 'Power Button'
[    21.503] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.503] (**) Power Button: always reports core events
[    21.503] (**) Power Button: Device: "/dev/input/event1"
[    21.503] (--) Power Button: Found keys
[    21.503] (II) Power Button: Configuring as keyboard
[    21.503] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    21.503] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    21.503] (**) Option "xkb_rules" "evdev"
[    21.503] (**) Option "xkb_model" "pc105"
[    21.503] (**) Option "xkb_layout" "us"
[    21.506] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    21.506] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    21.506] (II) Using input driver 'evdev' for 'Power Button'
[    21.506] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.506] (**) Power Button: always reports core events
[    21.506] (**) Power Button: Device: "/dev/input/event0"
[    21.506] (--) Power Button: Found keys
[    21.506] (II) Power Button: Configuring as keyboard
[    21.506] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    21.506] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    21.506] (**) Option "xkb_rules" "evdev"
[    21.506] (**) Option "xkb_model" "pc105"
[    21.506] (**) Option "xkb_layout" "us"
[    21.509] (II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event4)
[    21.509] (II) No input driver/identifier specified (ignoring)
[    21.510] (II) config/udev: Adding input device SIGMACHIP Usb Mouse (/dev/input/event3)
[    21.510] (**) SIGMACHIP Usb Mouse: Applying InputClass "evdev pointer catchall"
[    21.511] (II) Using input driver 'evdev' for 'SIGMACHIP Usb Mouse'
[    21.511] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.511] (**) SIGMACHIP Usb Mouse: always reports core events
[    21.511] (**) SIGMACHIP Usb Mouse: Device: "/dev/input/event3"
[    21.511] (--) SIGMACHIP Usb Mouse: Found 3 mouse buttons
[    21.511] (--) SIGMACHIP Usb Mouse: Found scroll wheel(s)
[    21.511] (--) SIGMACHIP Usb Mouse: Found relative axes
[    21.511] (--) SIGMACHIP Usb Mouse: Found x and y relative axes
[    21.511] (II) SIGMACHIP Usb Mouse: Configuring as mouse
[    21.511] (II) SIGMACHIP Usb Mouse: Adding scrollwheel support
[    21.511] (**) SIGMACHIP Usb Mouse: YAxisMapping: buttons 4 and 5
[    21.511] (**) SIGMACHIP Usb Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    21.511] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/input/input5/event3"
[    21.511] (II) XINPUT: Adding extended input device "SIGMACHIP Usb Mouse" (type: MOUSE)
[    21.511] (II) SIGMACHIP Usb Mouse: initialized for relative axes.
[    21.511] (**) SIGMACHIP Usb Mouse: (accel) keeping acceleration scheme 1
[    21.511] (**) SIGMACHIP Usb Mouse: (accel) acceleration profile 0
[    21.511] (**) SIGMACHIP Usb Mouse: (accel) acceleration factor: 2.000
[    21.511] (**) SIGMACHIP Usb Mouse: (accel) acceleration threshold: 4
[    21.511] (II) config/udev: Adding input device SIGMACHIP Usb Mouse (/dev/input/mouse0)
[    21.511] (II) No input driver/identifier specified (ignoring)
[    21.519] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    21.519] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    21.519] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    21.519] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.519] (**) AT Translated Set 2 keyboard: always reports core events
[    21.519] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    21.519] (--) AT Translated Set 2 keyboard: Found keys
[    21.519] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    21.519] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    21.519] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    21.519] (**) Option "xkb_rules" "evdev"
[    21.519] (**) Option "xkb_model" "pc105"
[    21.519] (**) Option "xkb_layout" "us"
[    24.019] (II) intel(0): EDID vendor "GSM", prod id 17458
[    24.019] (II) intel(0): Using hsync ranges from config file
[    24.019] (II) intel(0): Using vrefresh ranges from config file
[    24.019] (II) intel(0): Printing DDC gathered Modelines:
[    24.019] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    24.019] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    24.019] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    24.019] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    24.019] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    24.019] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    24.019] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    24.019] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    24.019] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    24.019] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    24.019] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    24.087] (II) intel(0): EDID vendor "GSM", prod id 17458
[    24.087] (II) intel(0): Using hsync ranges from config file
[    24.087] (II) intel(0): Using vrefresh ranges from config file
[    24.087] (II) intel(0): Printing DDC gathered Modelines:
[    24.087] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    24.087] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    24.087] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    24.087] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    24.087] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    24.087] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    24.087] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    24.087] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    24.087] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    24.087] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    24.087] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    24.187] (II) intel(0): EDID vendor "GSM", prod id 17458
[    24.188] (II) intel(0): Using hsync ranges from config file
[    24.188] (II) intel(0): Using vrefresh ranges from config file
[    24.188] (II) intel(0): Printing DDC gathered Modelines:
[    24.188] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    24.188] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    24.188] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    24.188] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    24.188] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    24.188] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    24.188] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    24.188] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    24.188] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    24.188] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    24.188] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    24.251] (II) intel(0): EDID vendor "GSM", prod id 17458
[    24.251] (II) intel(0): Using hsync ranges from config file
[    24.251] (II) intel(0): Using vrefresh ranges from config file
[    24.251] (II) intel(0): Printing DDC gathered Modelines:
[    24.251] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    24.251] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    24.251] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    24.251] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    24.251] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    24.251] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    24.251] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    24.251] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    24.251] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    24.251] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    24.252] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    43.611] (II) intel(0): EDID vendor "GSM", prod id 17458
[    43.611] (II) intel(0): Using hsync ranges from config file
[    43.611] (II) intel(0): Using vrefresh ranges from config file
[    43.611] (II) intel(0): Printing DDC gathered Modelines:
[    43.611] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    43.611] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    43.611] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    43.611] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    43.611] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    43.611] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    43.611] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    43.611] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    43.611] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    43.611] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    43.611] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    43.679] (II) intel(0): EDID vendor "GSM", prod id 17458
[    43.679] (II) intel(0): Using hsync ranges from config file
[    43.679] (II) intel(0): Using vrefresh ranges from config file
[    43.679] (II) intel(0): Printing DDC gathered Modelines:
[    43.679] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    43.679] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    43.679] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    43.679] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    43.679] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    43.679] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    43.679] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    43.679] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    43.679] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    43.679] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    43.679] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    43.747] (II) intel(0): EDID vendor "GSM", prod id 17458
[    43.747] (II) intel(0): Using hsync ranges from config file
[    43.747] (II) intel(0): Using vrefresh ranges from config file
[    43.747] (II) intel(0): Printing DDC gathered Modelines:
[    43.747] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    43.747] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    43.747] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    43.747] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    43.747] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    43.747] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    43.747] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    43.747] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    43.747] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    43.747] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    43.747] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    43.815] (II) intel(0): EDID vendor "GSM", prod id 17458
[    43.815] (II) intel(0): Using hsync ranges from config file
[    43.815] (II) intel(0): Using vrefresh ranges from config file
[    43.815] (II) intel(0): Printing DDC gathered Modelines:
[    43.815] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    43.815] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    43.815] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    43.815] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    43.815] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    43.815] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    43.815] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    43.815] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    43.815] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    43.815] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    43.815] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    52.911] (II) intel(0): EDID vendor "GSM", prod id 17458
[    52.911] (II) intel(0): Using hsync ranges from config file
[    52.911] (II) intel(0): Using vrefresh ranges from config file
[    52.911] (II) intel(0): Printing DDC gathered Modelines:
[    52.911] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    52.911] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    52.911] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    52.911] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    52.911] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    52.911] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    52.911] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    52.911] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    52.911] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    52.911] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    52.911] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   514.927] (II) intel(0): EDID vendor "GSM", prod id 17458
[   514.927] (II) intel(0): Using hsync ranges from config file
[   514.927] (II) intel(0): Using vrefresh ranges from config file
[   514.927] (II) intel(0): Printing DDC gathered Modelines:
[   514.927] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   514.928] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   514.928] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   514.928] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   514.928] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   514.928] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   514.928] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   514.928] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   514.928] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   514.928] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   514.928] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   965.011] (II) intel(0): EDID vendor "GSM", prod id 17458
[   965.011] (II) intel(0): Using hsync ranges from config file
[   965.011] (II) intel(0): Using vrefresh ranges from config file
[   965.011] (II) intel(0): Printing DDC gathered Modelines:
[   965.011] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   965.012] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   965.012] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   965.012] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   965.012] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   965.012] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   965.012] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   965.012] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   965.012] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   965.012] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   965.012] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[  1927.171] (II) intel(0): EDID vendor "GSM", prod id 17458
[  1927.172] (II) intel(0): Using hsync ranges from config file
[  1927.172] (II) intel(0): Using vrefresh ranges from config file
[  1927.172] (II) intel(0): Printing DDC gathered Modelines:
[  1927.172] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  1927.172] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  1927.172] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  1927.172] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  1927.172] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  1927.172] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[  1927.172] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  1927.172] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  1927.172] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[  1927.172] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  1927.172] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
```

---

