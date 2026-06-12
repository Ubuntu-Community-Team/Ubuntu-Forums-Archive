---
title: "Login problem on ubuntu 10.10"
date: 2010-11-04
forum: General Help
---

### Post by ElroyJ on 2010-11-04
I have installed ubuntu 10.10 on my pc and whenever i login to the desktop it shows the gnome panels,icons,wallpaper and then immediately goes back to the login screen.If i try to login again,it does the same thing all over again but sometimes it works.Is there any way to fix this?

---

### Post by NightwishFan on 2010-11-04
This might mean X is crashing. Post the contents of the file /var/log/Xorg.0.log here (surrounded by code '#' tags).

---

### Post by candtalan on 2010-11-06
> **NightwishFan said:**
> This might mean X is crashing. Post the contents of the file /var/log/Xorg.0.log here (surrounded by code '#' tags).

I get the same problem. 

This is an old PIII machine with 500MB ram.
I am using a fresh install of 10.10 now. 

A comment: I previously tried 10.04 and had problems (with panels not showing up) -  With a fresh install of Ubuntu 10.04  the gnome panels usually did not appear after booting.

I am now running it after having chosen gnome failsafe session at login.

Below, I paste the content of file
Xorg.0.log.old
which I guess is the failed session I have previously experienced after fresh install. I notice there is a segmentation fault near the end of it. Would this be when the session crashed?

```

[    83.517] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    83.517] X Protocol Version 11, Revision 0
[    83.517] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    83.517] Current Operating System: Linux davidputt-MS-6178 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:36:48 UTC 2010 i686
[    83.517] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=910e9a36-0367-4a7d-9d2d-29b60ad06811 ro quiet splash
[    83.518] Build Date: 16 September 2010  05:39:22PM
[    83.518] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
[    83.518] Current version of pixman: 0.18.4
[    83.518] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    83.518] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    83.519] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Nov  6 07:28:25 2010
[    83.520] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    83.526] (==) No Layout section.  Using the first Screen section.
[    83.526] (==) No screen section available. Using defaults.
[    83.526] (**) |-->Screen "Default Screen Section" (0)
[    83.526] (**) |   |-->Monitor "<default monitor>"
[    83.527] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    83.527] (==) Automatically adding devices
[    83.527] (==) Automatically enabling devices
[    83.532] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    83.532] 	Entry deleted from font path.
[    83.533] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    83.533] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    83.533] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    83.533] (II) Loader magic: 0x81f8e00
[    83.533] (II) Module ABI versions:
[    83.533] 	X.Org ANSI C Emulation: 0.4
[    83.533] 	X.Org Video Driver: 8.0
[    83.533] 	X.Org XInput driver : 11.0
[    83.533] 	X.Org Server Extension : 4.0
[    83.535] (--) PCI:*(0:0:1:0) 8086:7121:8086:0200 rev 3, Mem @ 0xe8000000/67108864, 0xeff80000/524288
[    83.537] (II) Open ACPI successful (/var/run/acpid.socket)
[    83.537] (II) LoadModule: "extmod"
[    83.538] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    83.539] (II) Module extmod: vendor="X.Org Foundation"
[    83.539] 	compiled for 1.9.0, module version = 1.0.0
[    83.539] 	Module class: X.Org Server Extension
[    83.539] 	ABI class: X.Org Server Extension, version 4.0
[    83.539] (II) Loading extension MIT-SCREEN-SAVER
[    83.539] (II) Loading extension XFree86-VidModeExtension
[    83.540] (II) Loading extension XFree86-DGA
[    83.540] (II) Loading extension DPMS
[    83.540] (II) Loading extension XVideo
[    83.540] (II) Loading extension XVideo-MotionCompensation
[    83.540] (II) Loading extension X-Resource
[    83.540] (II) LoadModule: "dbe"
[    83.545] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    83.545] (II) Module dbe: vendor="X.Org Foundation"
[    83.546] 	compiled for 1.9.0, module version = 1.0.0
[    83.546] 	Module class: X.Org Server Extension
[    83.546] 	ABI class: X.Org Server Extension, version 4.0
[    83.546] (II) Loading extension DOUBLE-BUFFER
[    83.546] (II) LoadModule: "glx"
[    83.547] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    83.547] (II) Module glx: vendor="X.Org Foundation"
[    83.547] 	compiled for 1.9.0, module version = 1.0.0
[    83.548] 	ABI class: X.Org Server Extension, version 4.0
[    83.548] (==) AIGLX enabled
[    83.548] (II) Loading extension GLX
[    83.548] (II) LoadModule: "record"
[    83.553] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    83.554] (II) Module record: vendor="X.Org Foundation"
[    83.554] 	compiled for 1.9.0, module version = 1.13.0
[    83.554] 	Module class: X.Org Server Extension
[    83.554] 	ABI class: X.Org Server Extension, version 4.0
[    83.554] (II) Loading extension RECORD
[    83.554] (II) LoadModule: "dri"
[    83.555] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    83.556] (II) Module dri: vendor="X.Org Foundation"
[    83.556] 	compiled for 1.9.0, module version = 1.0.0
[    83.556] 	ABI class: X.Org Server Extension, version 4.0
[    83.564] (II) Loading extension XFree86-DRI
[    83.564] (II) LoadModule: "dri2"
[    83.565] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    83.565] (II) Module dri2: vendor="X.Org Foundation"
[    83.565] 	compiled for 1.9.0, module version = 1.2.0
[    83.565] 	ABI class: X.Org Server Extension, version 4.0
[    83.566] (II) Loading extension DRI2
[    83.566] (==) Matched intel as autoconfigured driver 0
[    83.566] (==) Matched vesa as autoconfigured driver 1
[    83.566] (==) Matched fbdev as autoconfigured driver 2
[    83.566] (==) Assigned the driver to the xf86ConfigLayout
[    83.566] (II) LoadModule: "intel"
[    83.568] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    83.569] (II) Module intel: vendor="X.Org Foundation"
[    83.569] 	compiled for 1.9.0, module version = 2.12.0
[    83.569] 	Module class: X.Org Video Driver
[    83.569] 	ABI class: X.Org Video Driver, version 8.0
[    83.569] (II) LoadModule: "vesa"
[    83.570] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    83.571] (II) Module vesa: vendor="X.Org Foundation"
[    83.571] 	compiled for 1.8.99.905, module version = 2.3.0
[    83.571] 	Module class: X.Org Video Driver
[    83.571] 	ABI class: X.Org Video Driver, version 8.0
[    83.571] (II) LoadModule: "fbdev"
[    83.573] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    83.573] (II) Module fbdev: vendor="X.Org Foundation"
[    83.573] 	compiled for 1.8.99.905, module version = 0.4.2
[    83.573] 	ABI class: X.Org Video Driver, version 8.0
[    83.573] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
	Sandybridge, Sandybridge
[    83.577] (II) VESA: driver for VESA chipsets: vesa
[    83.577] (II) FBDEV: driver for framebuffer: fbdev
[    83.578] (--) using VT number 8

[    83.593] (WW) Falling back to old probe method for vesa
[    83.594] (WW) Falling back to old probe method for fbdev
[    83.594] (II) Loading sub module "fbdevhw"
[    83.594] (II) LoadModule: "fbdevhw"
[    83.596] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    83.597] (II) Module fbdevhw: vendor="X.Org Foundation"
[    83.597] 	compiled for 1.9.0, module version = 0.0.2
[    83.597] 	ABI class: X.Org Video Driver, version 8.0
[    83.597] (EE) open /dev/fb0: No such file or directory
[    83.597] (II) Loading sub module "vgahw"
[    83.597] (II) LoadModule: "vgahw"
[    83.598] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    83.598] (II) Module vgahw: vendor="X.Org Foundation"
[    83.598] 	compiled for 1.9.0, module version = 0.1.0
[    83.598] 	ABI class: X.Org Video Driver, version 8.0
[    83.599] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 16/16
[    83.599] (==) intel(0): Depth 16, (==) framebuffer bpp 16
[    83.599] (==) intel(0): RGB weight 565
[    83.599] (==) intel(0): Default visual is TrueColor
[    83.599] (II) Loading sub module "xaa"
[    83.599] (II) LoadModule: "xaa"
[    83.600] (II) Loading /usr/lib/xorg/modules/libxaa.so
[    83.601] (II) Module xaa: vendor="X.Org Foundation"
[    83.601] 	compiled for 1.9.0, module version = 1.2.1
[    83.601] 	ABI class: X.Org Video Driver, version 8.0
[    83.601] (II) Loading sub module "vbe"
[    83.601] (II) LoadModule: "vbe"
[    83.602] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    83.602] (II) Module vbe: vendor="X.Org Foundation"
[    83.602] 	compiled for 1.9.0, module version = 1.1.0
[    83.602] 	ABI class: X.Org Video Driver, version 8.0
[    83.602] (II) Loading sub module "int10"
[    83.602] (II) LoadModule: "int10"
[    83.603] (II) Loading /usr/lib/xorg/modules/libint10.so
[    83.604] (II) Module int10: vendor="X.Org Foundation"
[    83.604] 	compiled for 1.9.0, module version = 1.0.0
[    83.604] 	ABI class: X.Org Video Driver, version 8.0
[    83.604] (II) intel(0): initializing int10
[    83.612] (II) intel(0): Primary V_BIOS segment is: 0xc000
[    83.614] (II) intel(0): VESA BIOS detected
[    83.614] (II) intel(0): VESA VBE Version 2.0
[    83.614] (II) intel(0): VESA VBE Total Mem: 1024 kB
[    83.614] (II) intel(0): VESA VBE OEM: Intel810(TM) Graphics Chip Accelerated VGA BIOS
[    83.614] (II) intel(0): VESA VBE OEM Software Rev: 3.1
[    83.614] (II) intel(0): VESA VBE OEM Vendor: Intel Corporation
[    83.614] (II) intel(0): VESA VBE OEM Product: i810 Graphics Controller
[    83.614] (II) intel(0): VESA VBE OEM Product Rev: Hardware Version 0.0
[    83.615] (II) Loading sub module "ddc"
[    83.615] (II) LoadModule: "ddc"
[    83.615] (II) Module "ddc" already built-in
[    83.677] (II) intel(0): VESA VBE DDC supported
[    83.677] (II) intel(0): VESA VBE DDC Level 2
[    83.677] (II) intel(0): VESA VBE DDC transfer in appr. 1 sec.
[    85.102] (II) intel(0): VESA VBE DDC read successfully
[    85.102] (II) intel(0): Manufacturer: DEL  Model: 4274  Serial#: 811029078
[    85.102] (II) intel(0): Year: 1995  Week: 47
[    85.102] (II) intel(0): EDID Version: 1.0
[    85.102] (II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[    85.102] (II) intel(0): Sync:  Separate
[    85.102] (II) intel(0): Max Image Size [cm]: horiz.: 28  vert.: 20
[    85.103] (II) intel(0): Gamma: 1.01
[    85.103] (II) intel(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    85.103] (II) intel(0): redX: 0.004 redY: 0.004   greenX: 0.004 greenY: 0.005
[    85.103] (II) intel(0): blueX: 0.004 blueY: 0.004   whiteX: 0.004 whiteY: 0.005
[    85.103] (II) intel(0): Supported established timings:
[    85.103] (II) intel(0): 720x400@70Hz
[    85.103] (II) intel(0): 640x480@60Hz
[    85.103] (II) intel(0): 640x480@72Hz
[    85.103] (II) intel(0): 640x480@75Hz
[    85.103] (II) intel(0): 800x600@60Hz
[    85.103] (II) intel(0): 800x600@72Hz
[    85.103] (II) intel(0): 800x600@75Hz
[    85.104] (II) intel(0): 1024x768@60Hz
[    85.104] (II) intel(0): 1024x768@70Hz
[    85.104] (II) intel(0): 1024x768@75Hz
[    85.104] (II) intel(0): Manufacturer's mask: 0
[    85.104] (II) intel(0): Supported detailed timing:
[    85.104] (II) intel(0): clock: 110.0 MHz   Image Size:  262 x 196 mm
[    85.104] (II) intel(0): h_active: 1280  h_sync: 1358  h_sync_end 1470 h_blank_end 1720 h_border: 0
[    85.104] (II) intel(0): v_active: 1024  v_sync: 1025  v_sync_end 1030 v_blanking: 1067 v_border: 0
[    85.104] (II) intel(0): EDID (in hex):
[    85.104] (II) intel(0): 	00ffffffffffff0010ac744256525730
[    85.104] (II) intel(0): 	2f050100081c1401e801010101010101
[    85.104] (II) intel(0): 	010101adce0001010101010101010101
[    85.105] (II) intel(0): 	010101010101f82a00b851002b404e70
[    85.105] (II) intel(0): 	150006c4100000180101010101010101
[    85.105] (II) intel(0): 	01010101010101010101010101010101
[    85.105] (II) intel(0): 	01010101010101010101010101010101
[    85.105] (II) intel(0): 	010101010101010101010101010100e9
[    85.105] (II) intel(0): EDID vendor "DEL", prod id 17012
[    85.105] (II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
[    85.105] (II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
[    85.105] (II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
[    85.105] (II) intel(0): Printing DDC gathered Modelines:
[    85.106] (II) intel(0): Modeline "1280x1024"x0.0  110.00  1280 1358 1470 1720  1024 1025 1030 1067 -hsync -vsync (64.0 kHz)
[    85.106] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    85.106] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    85.106] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    85.106] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    85.106] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    85.106] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    85.106] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    85.106] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    85.106] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    85.106] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    85.107] (--) intel(0): Chipset: "i810"
[    85.107] (--) intel(0): Linear framebuffer at 0xE8000000
[    85.107] (--) intel(0): IO registers at addr 0xEFF80000
[    85.107] (II) intel(0): Kernel reported 106752 total, 1 used
[    85.108] (II) intel(0): I810CheckAvailableMemory: 427004k available
[    85.108] (==) intel(0): Will alloc AGP framebuffer: 24576 kByte
[    85.108] (==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
[    85.108] (II) intel(0): <default monitor>: Using hsync range of 31.47-63.95 kHz
[    85.108] (II) intel(0): <default monitor>: Using vrefresh range of 59.94-75.03 Hz
[    85.108] (II) intel(0): Estimated virtual size for aspect ratio 1.4000 is 1024x768
[    85.108] (II) intel(0): Clock range:   9.50 to 163.00 MHz
[    85.108] (II) intel(0): Not using default mode "640x350" (vrefresh out of range)
[    85.108] (II) intel(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
[    85.108] (II) intel(0): Not using default mode "640x400" (vrefresh out of range)
[    85.109] (II) intel(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
[    85.109] (II) intel(0): Not using default mode "720x400" (vrefresh out of range)
[    85.109] (II) intel(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
[    85.109] (II) intel(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[    85.109] (II) intel(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[    85.109] (II) intel(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[    85.109] (II) intel(0): Not using default mode "640x480" (vrefresh out of range)
[    85.109] (II) intel(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[    85.109] (II) intel(0): Not using default mode "800x600" (vrefresh out of range)
[    85.109] (II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[    85.109] (II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[    85.109] (II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[    85.109] (II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[    85.109] (II) intel(0): Not using default mode "800x600" (vrefresh out of range)
[    85.109] (II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[    85.110] (II) intel(0): Not using default mode "1024x768i" (unknown reason)
[    85.110] (II) intel(0): Not using default mode "512x384i" (bad mode clock/interlace/doublescan)
[    85.110] (II) intel(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
[    85.110] (II) intel(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
[    85.110] (II) intel(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
[    85.110] (II) intel(0): Not using default mode "1024x768" (hsync out of range)
[    85.110] (II) intel(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
[    85.110] (II) intel(0): Not using default mode "1152x864" (width too large for virtual size)
[    85.110] (II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[    85.110] (II) intel(0): Not using default mode "1280x960" (width too large for virtual size)
[    85.110] (II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
[    85.110] (II) intel(0): Not using default mode "1280x960" (width too large for virtual size)
[    85.110] (II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
[    85.110] (II) intel(0): Not using default mode "1280x1024" (width too large for virtual size)
[    85.111] (II) intel(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
[    85.111] (II) intel(0): Not using default mode "1280x1024" (width too large for virtual size)
[    85.111] (II) intel(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
[    85.111] (II) intel(0): Not using default mode "1280x1024" (width too large for virtual size)
[    85.111] (II) intel(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
[    85.111] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[    85.111] (II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[    85.111] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[    85.111] (II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[    85.111] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[    85.111] (II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[    85.111] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[    85.111] (II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[    85.111] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[    85.112] (II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[    85.112] (II) intel(0): Not using default mode "1792x1344" (width too large for virtual size)
[    85.112] (II) intel(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
[    85.112] (II) intel(0): Not using default mode "1792x1344" (width too large for virtual size)
[    85.112] (II) intel(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
[    85.112] (II) intel(0): Not using default mode "1856x1392" (width too large for virtual size)
[    85.112] (II) intel(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
[    85.112] (II) intel(0): Not using default mode "1856x1392" (width too large for virtual size)
[    85.112] (II) intel(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
[    85.112] (II) intel(0): Not using default mode "1920x1440" (width too large for virtual size)
[    85.112] (II) intel(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
[    85.112] (II) intel(0): Not using default mode "1920x1440" (width too large for virtual size)
[    85.112] (II) intel(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
[    85.112] (II) intel(0): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
[    85.113] (II) intel(0): Not using default mode "1152x864" (width too large for virtual size)
[    85.113] (II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[    85.113] (II) intel(0): Not using default mode "1152x864" (width too large for virtual size)
[    85.113] (II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[    85.113] (II) intel(0): Not using default mode "1152x864" (width too large for virtual size)
[    85.113] (II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[    85.113] (II) intel(0): Not using default mode "1152x864" (width too large for virtual size)
[    85.113] (II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[    85.113] (II) intel(0): Not using default mode "1152x864" (width too large for virtual size)
[    85.113] (II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[    85.113] (II) intel(0): Not using default mode "1152x864" (width too large for virtual size)
[    85.113] (II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[    85.113] (II) intel(0): Not using default mode "1360x768" (width too large for virtual size)
[    85.113] (II) intel(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
[    85.114] (II) intel(0): Not using default mode "1360x768" (width too large for virtual size)
[    85.114] (II) intel(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
[    85.114] (II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
[    85.114] (II) intel(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
[    85.114] (II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
[    85.114] (II) intel(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
[    85.114] (II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
[    85.114] (II) intel(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
[    85.114] (II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
[    85.114] (II) intel(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
[    85.114] (II) intel(0): Not using default mode "1440x900" (width too large for virtual size)
[    85.114] (II) intel(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
[    85.114] (II) intel(0): Not using default mode "1600x1024" (width too large for virtual size)
[    85.114] (II) intel(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
[    85.114] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[    85.115] (II) intel(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[    85.115] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[    85.115] (II) intel(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[    85.115] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[    85.115] (II) intel(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[    85.115] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[    85.115] (II) intel(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[    85.115] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[    85.115] (II) intel(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[    85.115] (II) intel(0): Not using default mode "1920x1080" (width too large for virtual size)
[    85.115] (II) intel(0): Not using default mode "960x540" (bad mode clock/interlace/doublescan)
[    85.115] (II) intel(0): Not using default mode "1920x1200" (width too large for virtual size)
[    85.115] (II) intel(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
[    85.115] (II) intel(0): Not using default mode "1920x1440" (width too large for virtual size)
[    85.116] (II) intel(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
[    85.116] (II) intel(0): Not using default mode "2048x1536" (width too large for virtual size)
[    85.116] (II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
[    85.116] (II) intel(0): Not using default mode "2048x1536" (width too large for virtual size)
[    85.116] (II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
[    85.116] (II) intel(0): Not using default mode "2048x1536" (width too large for virtual size)
[    85.116] (II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
[    85.116] (II) intel(0): Not using driver mode "1280x1024" (width too large for virtual size)
[    85.116] (--) intel(0): Virtual size is 1024x768 (pitch 1024)
[    85.116] (**) intel(0): *Driver mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
[    85.116] (II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    85.117] (**) intel(0): *Driver mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
[    85.117] (II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    85.117] (**) intel(0): *Driver mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
[    85.117] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    85.117] (**) intel(0): *Default mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
[    85.117] (II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    85.117] (**) intel(0): *Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
[    85.117] (II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    85.117] (**) intel(0): *Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
[    85.117] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    85.117] (**) intel(0): *Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
[    85.118] (II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    85.118] (**) intel(0): *Driver mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
[    85.118] (II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    85.118] (**) intel(0): *Driver mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
[    85.118] (II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    85.118] (**) intel(0): *Driver mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
[    85.118] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    85.118] (**) intel(0): *Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
[    85.118] (II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    85.118] (**) intel(0): *Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
[    85.118] (II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    85.118] (**) intel(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
[    85.119] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    85.119] (**) intel(0): *Driver mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
[    85.119] (II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    85.119] (**) intel(0): *Driver mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
[    85.119] (II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    85.119] (**) intel(0): *Driver mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
[    85.119] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    85.119] (**) intel(0): *Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
[    85.119] (II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    85.119] (**) intel(0): *Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
[    85.119] (II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    85.120] (**) intel(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
[    85.120] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    85.120] (**) intel(0): *Driver mode "720x400": 28.3 MHz, 31.5 kHz, 70.1 Hz
[    85.120] (II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    85.120] (**) intel(0): Display dimensions: (280, 200) mm
[    85.120] (**) intel(0): DPI set to (92, 97)
[    85.120] (II) Loading sub module "fb"
[    85.120] (II) LoadModule: "fb"
[    85.122] (II) Loading /usr/lib/xorg/modules/libfb.so
[    85.123] (II) Module fb: vendor="X.Org Foundation"
[    85.123] 	compiled for 1.9.0, module version = 1.0.0
[    85.123] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    85.123] (II) Loading sub module "ramdac"
[    85.123] (II) LoadModule: "ramdac"
[    85.123] (II) Module "ramdac" already built-in
[    85.123] (**) intel(0): page flipping disabled
[    85.123] (II) intel(0): XvMC is Disabled: use XvMCSurfaces config option to enable.
[    85.123] (II) UnloadModule: "vesa"
[    85.123] (II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    85.123] (II) UnloadModule: "fbdev"
[    85.124] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    85.124] (II) UnloadModule: "fbdevhw"
[    85.124] (II) Unloading /usr/lib/xorg/modules/libfbdevhw.so
[    85.125] drmOpenDevice: node name is /dev/dri/card0
[    85.126] drmOpenDevice: open result is 12, (OK)
[    85.126] drmOpenDevice: node name is /dev/dri/card0
[    85.126] drmOpenDevice: open result is 12, (OK)
[    85.126] drmOpenByBusid: Searching for BusID pci:0000:00:01.0
[    85.126] drmOpenDevice: node name is /dev/dri/card0
[    85.126] drmOpenDevice: open result is 12, (OK)
[    85.126] drmOpenByBusid: drmOpenMinor returns 12
[    85.126] drmOpenByBusid: drmGetBusid reports pci:0000:00:01.0
[    85.126] (II) [drm] DRM interface version 1.3
[    85.127] (II) [drm] DRM open master succeeded.
[    85.127] (II) intel(0): [drm] Using the DRM lock SAREA also for drawables.
[    85.127] (II) intel(0): [drm] framebuffer handle = 0xe8000000
[    85.127] (II) intel(0): [drm] added 1 reserved context for kernel
[    85.127] (II) intel(0): X context handle = 0x1
[    85.127] (II) intel(0): [drm] installed DRM signal handler
[    85.128] (II) intel(0): [drm] Registers = 0xeff80000
[    85.128] (II) intel(0): [agp] dcacheHandle : 0x0
[    85.128] (II) intel(0): [agp] GART: no dcache memory found
[    85.140] (II) intel(0): [agp] Bound backbuffer memory
[    85.151] (II) intel(0): [agp] Bound depthbuffer memory
[    85.316] (II) intel(0): [agp] Bound System Texture Memory
[    85.316] (II) intel(0): [agp] GART: Allocated 4K for mouse cursor image
[    85.317] (II) intel(0): [agp] GART: Allocated 16K for ARGB mouse cursor image
[    85.317] (II) intel(0): Adding 768 scanlines for pixmap caching
[    85.317] (II) intel(0): Allocated Scratch Memory
[    85.317] (II) intel(0): [dri] Buffer map : 13fb000
[    85.318] (II) intel(0): [drm] added 256 4096 byte DMA buffers
[    85.318] (II) intel(0): [drm] Init v1.4 interface.
[    85.323] (II) intel(0): [drm] dma control initialized, using IRQ -22
[    85.323] (II) intel(0): [dri] visual configs initialized.
[    85.342] (II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
[    85.343] (II) intel(0): Setting dot clock to 78.7 MHz [ 0x50 0x17 0x20 ] [ 82 25 2 ]
[    85.343] (II) intel(0): chose watermark 0x2210e000: (tab.freq 78.8)
[    85.401] (II) intel(0): Using XFree86 Acceleration Architecture (XAA)
[    85.402] 	Screen to screen bit blits
[    85.402] 	Solid filled rectangles
[    85.402] 	8x8 mono pattern filled rectangles
[    85.402] 	Indirect CPU to Screen color expansion
[    85.402] 	Solid Horizontal and Vertical Lines
[    85.402] 	Setting up tile and stipple cache:
[    85.402] 		24 128x128 slots
[    85.402] 		6 256x256 slots
[    85.402] (==) intel(0): Backing store disabled
[    85.402] (==) intel(0): Silken mouse enabled
[    85.403] (==) intel(0): DPMS enabled
[    85.403] (II) intel(0): [DRI] installation complete
[    85.403] (II) intel(0): Direct rendering enabled
[    85.404] (==) RandR enabled
[    85.404] (II) Initializing built-in extension Generic Event Extension
[    85.404] (II) Initializing built-in extension SHAPE
[    85.404] (II) Initializing built-in extension MIT-SHM
[    85.404] (II) Initializing built-in extension XInputExtension
[    85.404] (II) Initializing built-in extension XTEST
[    85.404] (II) Initializing built-in extension BIG-REQUESTS
[    85.404] (II) Initializing built-in extension SYNC
[    85.404] (II) Initializing built-in extension XKEYBOARD
[    85.404] (II) Initializing built-in extension XC-MISC
[    85.404] (II) Initializing built-in extension SECURITY
[    85.404] (II) Initializing built-in extension XINERAMA
[    85.404] (II) Initializing built-in extension XFIXES
[    85.404] (II) Initializing built-in extension RENDER
[    85.404] (II) Initializing built-in extension RANDR
[    85.404] (II) Initializing built-in extension COMPOSITE
[    85.404] (II) Initializing built-in extension DAMAGE
[    85.404] (II) Initializing built-in extension GESTURE
[    85.465] (II) AIGLX: Screen 0 is not DRI2 capable
[    85.465] drmOpenDevice: node name is /dev/dri/card0
[    85.465] drmOpenDevice: open result is 13, (OK)
[    88.464] drmOpenByBusid: Searching for BusID pci:0000:00:01.0
[    88.464] drmOpenDevice: node name is /dev/dri/card0
[    88.464] drmOpenDevice: open result is 13, (OK)
[    88.464] drmOpenByBusid: drmOpenMinor returns 13
[    88.464] drmOpenByBusid: drmGetBusid reports pci:0000:00:01.0
[    88.482] (II) AIGLX: Loaded and initialized /usr/lib/dri/i810_dri.so
[    88.482] (II) GLX: Initialized DRI GL provider for screen 0
[    88.585] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    88.623] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event0)
[    88.623] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    88.623] (II) LoadModule: "evdev"
[    88.625] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    88.626] (II) Module evdev: vendor="X.Org Foundation"
[    88.626] 	compiled for 1.9.0, module version = 2.3.2
[    88.626] 	Module class: X.Org XInput Driver
[    88.626] 	ABI class: X.Org XInput driver, version 11.0
[    88.627] (**) AT Translated Set 2 keyboard: always reports core events
[    88.627] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event0"
[    88.627] (II) AT Translated Set 2 keyboard: Found keys
[    88.627] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    88.627] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    88.627] (**) Option "xkb_rules" "evdev"
[    88.627] (**) Option "xkb_model" "evdev"
[    88.627] (**) Option "xkb_layout" "gb"
[    88.640] (II) XKB: reuse xkmfile /var/lib/xkb/server-C1F82522E3F958F13C2D6D2C62551E135092F235.xkm
[    88.644] (II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/event1)
[    88.644] (**) PS/2 Generic Mouse: Applying InputClass "evdev pointer catchall"
[    88.644] (**) PS/2 Generic Mouse: always reports core events
[    88.644] (**) PS/2 Generic Mouse: Device: "/dev/input/event1"
[    88.645] (II) PS/2 Generic Mouse: Found 3 mouse buttons
[    88.645] (II) PS/2 Generic Mouse: Found relative axes
[    88.645] (II) PS/2 Generic Mouse: Found x and y relative axes
[    88.645] (II) PS/2 Generic Mouse: Configuring as mouse
[    88.645] (**) PS/2 Generic Mouse: YAxisMapping: buttons 4 and 5
[    88.645] (**) PS/2 Generic Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    88.645] (II) XINPUT: Adding extended input device "PS/2 Generic Mouse" (type: MOUSE)
[    88.645] (II) PS/2 Generic Mouse: initialized for relative axes.
[    88.647] (II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/mouse0)
[    88.647] (II) No input driver/identifier specified (ignoring)
[   160.640] 
Backtrace:
[   160.645] 0: /usr/bin/X (xorg_backtrace+0x3b) [0x80e82fb]
[   160.645] 1: /usr/bin/X (0x8048000+0x5da8d) [0x80a5a8d]
[   160.645] 2: (vdso) (__kernel_rt_sigreturn+0x0) [0xa9a40c]
[   160.645] 3: /usr/bin/X (FreeClientResources+0xed) [0x808f04d]
[   160.645] 4: /usr/bin/X (CloseDownClient+0x69) [0x8069109]
[   160.645] 5: /usr/bin/X (0x8048000+0x260a5) [0x806e0a5]
[   160.646] 6: /usr/bin/X (0x8048000+0x1a5ba) [0x80625ba]
[   160.646] 7: /lib/libc.so.6 (__libc_start_main+0xe7) [0xddbce7]
[   160.646] 8: /usr/bin/X (0x8048000+0x1a191) [0x8062191]
[   160.646] Segmentation fault at address 0xb5c9c00c
[   160.646] 
Caught signal 11 (Segmentation fault). Server aborting
[   160.647] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[   160.647] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[   160.647] 
[   160.652] (II) AT Translated Set 2 keyboard: Close
[   160.653] (II) UnloadModule: "evdev"
[   160.654] (II) PS/2 Generic Mouse: Close
[   160.654] (II) UnloadModule: "evdev"
[   160.654] (II) AIGLX: Suspending AIGLX clients for VT switch

```



The current log file is below, this is my current gnome failsafe session:
filename Xorg.0.log

```


[   161.334] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[   161.334] X Protocol Version 11, Revision 0
[   161.334] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[   161.334] Current Operating System: Linux davidputt-MS-6178 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:36:48 UTC 2010 i686
[   161.334] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=910e9a36-0367-4a7d-9d2d-29b60ad06811 ro quiet splash
[   161.335] Build Date: 16 September 2010  05:39:22PM
[   161.335] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
[   161.335] Current version of pixman: 0.18.4
[   161.335] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[   161.335] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   161.336] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Nov  6 07:29:43 2010
[   161.336] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   161.338] (==) No Layout section.  Using the first Screen section.
[   161.338] (==) No screen section available. Using defaults.
[   161.338] (**) |-->Screen "Default Screen Section" (0)
[   161.338] (**) |   |-->Monitor "<default monitor>"
[   161.339] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[   161.339] (==) Automatically adding devices
[   161.339] (==) Automatically enabling devices
[   161.340] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   161.340] 	Entry deleted from font path.
[   161.340] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[   161.340] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   161.340] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[   161.340] (II) Loader magic: 0x81f8e00
[   161.340] (II) Module ABI versions:
[   161.340] 	X.Org ANSI C Emulation: 0.4
[   161.340] 	X.Org Video Driver: 8.0
[   161.340] 	X.Org XInput driver : 11.0
[   161.341] 	X.Org Server Extension : 4.0
[   161.342] (--) PCI:*(0:0:1:0) 8086:7121:8086:0200 rev 3, Mem @ 0xe8000000/67108864, 0xeff80000/524288
[   161.344] (II) Open ACPI successful (/var/run/acpid.socket)
[   161.344] (II) LoadModule: "extmod"
[   161.346] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   161.347] (II) Module extmod: vendor="X.Org Foundation"
[   161.347] 	compiled for 1.9.0, module version = 1.0.0
[   161.347] 	Module class: X.Org Server Extension
[   161.347] 	ABI class: X.Org Server Extension, version 4.0
[   161.347] (II) Loading extension MIT-SCREEN-SAVER
[   161.347] (II) Loading extension XFree86-VidModeExtension
[   161.347] (II) Loading extension XFree86-DGA
[   161.347] (II) Loading extension DPMS
[   161.347] (II) Loading extension XVideo
[   161.347] (II) Loading extension XVideo-MotionCompensation
[   161.347] (II) Loading extension X-Resource
[   161.347] (II) LoadModule: "dbe"
[   161.348] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   161.348] (II) Module dbe: vendor="X.Org Foundation"
[   161.349] 	compiled for 1.9.0, module version = 1.0.0
[   161.349] 	Module class: X.Org Server Extension
[   161.349] 	ABI class: X.Org Server Extension, version 4.0
[   161.349] (II) Loading extension DOUBLE-BUFFER
[   161.349] (II) LoadModule: "glx"
[   161.349] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   161.350] (II) Module glx: vendor="X.Org Foundation"
[   161.350] 	compiled for 1.9.0, module version = 1.0.0
[   161.350] 	ABI class: X.Org Server Extension, version 4.0
[   161.350] (==) AIGLX enabled
[   161.351] (II) Loading extension GLX
[   161.351] (II) LoadModule: "record"
[   161.351] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   161.352] (II) Module record: vendor="X.Org Foundation"
[   161.352] 	compiled for 1.9.0, module version = 1.13.0
[   161.352] 	Module class: X.Org Server Extension
[   161.352] 	ABI class: X.Org Server Extension, version 4.0
[   161.352] (II) Loading extension RECORD
[   161.352] (II) LoadModule: "dri"
[   161.353] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   161.354] (II) Module dri: vendor="X.Org Foundation"
[   161.354] 	compiled for 1.9.0, module version = 1.0.0
[   161.354] 	ABI class: X.Org Server Extension, version 4.0
[   161.354] (II) Loading extension XFree86-DRI
[   161.354] (II) LoadModule: "dri2"
[   161.355] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   161.356] (II) Module dri2: vendor="X.Org Foundation"
[   161.356] 	compiled for 1.9.0, module version = 1.2.0
[   161.356] 	ABI class: X.Org Server Extension, version 4.0
[   161.356] (II) Loading extension DRI2
[   161.356] (==) Matched intel as autoconfigured driver 0
[   161.356] (==) Matched vesa as autoconfigured driver 1
[   161.356] (==) Matched fbdev as autoconfigured driver 2
[   161.356] (==) Assigned the driver to the xf86ConfigLayout
[   161.356] (II) LoadModule: "intel"
[   161.358] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[   161.359] (II) Module intel: vendor="X.Org Foundation"
[   161.359] 	compiled for 1.9.0, module version = 2.12.0
[   161.359] 	Module class: X.Org Video Driver
[   161.359] 	ABI class: X.Org Video Driver, version 8.0
[   161.359] (II) LoadModule: "vesa"
[   161.361] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   161.361] (II) Module vesa: vendor="X.Org Foundation"
[   161.361] 	compiled for 1.8.99.905, module version = 2.3.0
[   161.361] 	Module class: X.Org Video Driver
[   161.361] 	ABI class: X.Org Video Driver, version 8.0
[   161.361] (II) LoadModule: "fbdev"
[   161.363] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   161.363] (II) Module fbdev: vendor="X.Org Foundation"
[   161.363] 	compiled for 1.8.99.905, module version = 0.4.2
[   161.363] 	ABI class: X.Org Video Driver, version 8.0
[   161.363] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
	Sandybridge, Sandybridge
[   161.367] (II) VESA: driver for VESA chipsets: vesa
[   161.367] (II) FBDEV: driver for framebuffer: fbdev
[   161.368] (--) using VT number 9

[   161.383] (WW) Falling back to old probe method for vesa
[   161.383] (WW) Falling back to old probe method for fbdev
[   161.383] (II) Loading sub module "fbdevhw"
[   161.383] (II) LoadModule: "fbdevhw"
[   161.385] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   161.386] (II) Module fbdevhw: vendor="X.Org Foundation"
[   161.386] 	compiled for 1.9.0, module version = 0.0.2
[   161.386] 	ABI class: X.Org Video Driver, version 8.0
[   161.386] (EE) open /dev/fb0: No such file or directory
[   161.386] (II) Loading sub module "vgahw"
[   161.386] (II) LoadModule: "vgahw"
[   161.387] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[   161.387] (II) Module vgahw: vendor="X.Org Foundation"
[   161.388] 	compiled for 1.9.0, module version = 0.1.0
[   161.388] 	ABI class: X.Org Video Driver, version 8.0
[   161.388] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 16/16
[   161.388] (==) intel(0): Depth 16, (==) framebuffer bpp 16
[   161.388] (==) intel(0): RGB weight 565
[   161.388] (==) intel(0): Default visual is TrueColor
[   161.388] (II) Loading sub module "xaa"
[   161.388] (II) LoadModule: "xaa"
[   161.389] (II) Loading /usr/lib/xorg/modules/libxaa.so
[   161.390] (II) Module xaa: vendor="X.Org Foundation"
[   161.390] 	compiled for 1.9.0, module version = 1.2.1
[   161.390] 	ABI class: X.Org Video Driver, version 8.0
[   161.390] (II) Loading sub module "vbe"
[   161.390] (II) LoadModule: "vbe"
[   161.391] (II) Loading /usr/lib/xorg/modules/libvbe.so
[   161.391] (II) Module vbe: vendor="X.Org Foundation"
[   161.391] 	compiled for 1.9.0, module version = 1.1.0
[   161.392] 	ABI class: X.Org Video Driver, version 8.0
[   161.392] (II) Loading sub module "int10"
[   161.392] (II) LoadModule: "int10"
[   161.393] (II) Loading /usr/lib/xorg/modules/libint10.so
[   161.393] (II) Module int10: vendor="X.Org Foundation"
[   161.393] 	compiled for 1.9.0, module version = 1.0.0
[   161.393] 	ABI class: X.Org Video Driver, version 8.0
[   161.393] (II) intel(0): initializing int10
[   161.401] (II) intel(0): Primary V_BIOS segment is: 0xc000
[   161.403] (II) intel(0): VESA BIOS detected
[   161.403] (II) intel(0): VESA VBE Version 2.0
[   161.403] (II) intel(0): VESA VBE Total Mem: 1024 kB
[   161.404] (II) intel(0): VESA VBE OEM: Intel810(TM) Graphics Chip Accelerated VGA BIOS
[   161.404] (II) intel(0): VESA VBE OEM Software Rev: 3.1
[   161.404] (II) intel(0): VESA VBE OEM Vendor: Intel Corporation
[   161.404] (II) intel(0): VESA VBE OEM Product: i810 Graphics Controller
[   161.404] (II) intel(0): VESA VBE OEM Product Rev: Hardware Version 0.0
[   161.404] (II) Loading sub module "ddc"
[   161.404] (II) LoadModule: "ddc"
[   161.404] (II) Module "ddc" already built-in
[   161.462] (II) intel(0): VESA VBE DDC supported
[   161.462] (II) intel(0): VESA VBE DDC Level 2
[   161.462] (II) intel(0): VESA VBE DDC transfer in appr. 1 sec.
[   162.836] (II) intel(0): VESA VBE DDC read successfully
[   162.837] (II) intel(0): Manufacturer: DEL  Model: 4274  Serial#: 811029078
[   162.837] (II) intel(0): Year: 1995  Week: 47
[   162.837] (II) intel(0): EDID Version: 1.0
[   162.837] (II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[   162.837] (II) intel(0): Sync:  Separate
[   162.837] (II) intel(0): Max Image Size [cm]: horiz.: 28  vert.: 20
[   162.837] (II) intel(0): Gamma: 1.01
[   162.837] (II) intel(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[   162.837] (II) intel(0): redX: 0.004 redY: 0.004   greenX: 0.004 greenY: 0.005
[   162.838] (II) intel(0): blueX: 0.004 blueY: 0.004   whiteX: 0.004 whiteY: 0.005
[   162.838] (II) intel(0): Supported established timings:
[   162.838] (II) intel(0): 720x400@70Hz
[   162.838] (II) intel(0): 640x480@60Hz
[   162.838] (II) intel(0): 640x480@72Hz
[   162.838] (II) intel(0): 640x480@75Hz
[   162.838] (II) intel(0): 800x600@60Hz
[   162.838] (II) intel(0): 800x600@72Hz
[   162.838] (II) intel(0): 800x600@75Hz
[   162.838] (II) intel(0): 1024x768@60Hz
[   162.838] (II) intel(0): 1024x768@70Hz
[   162.838] (II) intel(0): 1024x768@75Hz
[   162.838] (II) intel(0): Manufacturer's mask: 0
[   162.838] (II) intel(0): Supported detailed timing:
[   162.839] (II) intel(0): clock: 110.0 MHz   Image Size:  262 x 196 mm
[   162.839] (II) intel(0): h_active: 1280  h_sync: 1358  h_sync_end 1470 h_blank_end 1720 h_border: 0
[   162.839] (II) intel(0): v_active: 1024  v_sync: 1025  v_sync_end 1030 v_blanking: 1067 v_border: 0
[   162.839] (II) intel(0): EDID (in hex):
[   162.839] (II) intel(0): 	00ffffffffffff0010ac744256525730
[   162.839] (II) intel(0): 	2f050100081c1401e801010101010101
[   162.839] (II) intel(0): 	010101adce0001010101010101010101
[   162.839] (II) intel(0): 	010101010101f82a00b851002b404e70
[   162.839] (II) intel(0): 	150006c4100000180101010101010101
[   162.839] (II) intel(0): 	01010101010101010101010101010101
[   162.839] (II) intel(0): 	01010101010101010101010101010101
[   162.840] (II) intel(0): 	010101010101010101010101010100e9
[   162.840] (II) intel(0): EDID vendor "DEL", prod id 17012
[   162.840] (II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
[   162.840] (II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
[   162.840] (II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
[   162.840] (II) intel(0): Printing DDC gathered Modelines:
[   162.840] (II) intel(0): Modeline "1280x1024"x0.0  110.00  1280 1358 1470 1720  1024 1025 1030 1067 -hsync -vsync (64.0 kHz)
[   162.840] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   162.840] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   162.840] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[   162.841] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   162.841] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   162.841] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   162.841] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   162.841] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   162.841] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   162.841] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   162.842] (--) intel(0): Chipset: "i810"
[   162.842] (--) intel(0): Linear framebuffer at 0xE8000000
[   162.842] (--) intel(0): IO registers at addr 0xEFF80000
[   162.842] (II) intel(0): Kernel reported 106752 total, 1 used
[   162.842] (II) intel(0): I810CheckAvailableMemory: 427004k available
[   162.842] (==) intel(0): Will alloc AGP framebuffer: 24576 kByte
[   162.842] (==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
[   162.842] (II) intel(0): <default monitor>: Using hsync range of 31.47-63.95 kHz
[   162.843] (II) intel(0): <default monitor>: Using vrefresh range of 59.94-75.03 Hz
[   162.843] (II) intel(0): Estimated virtual size for aspect ratio 1.4000 is 1024x768
[   162.843] (II) intel(0): Clock range:   9.50 to 163.00 MHz
[   162.843] (II) intel(0): Not using default mode "640x350" (vrefresh out of range)
[   162.843] (II) intel(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
[   162.843] (II) intel(0): Not using default mode "640x400" (vrefresh out of range)
[   162.843] (II) intel(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
[   162.843] (II) intel(0): Not using default mode "720x400" (vrefresh out of range)
[   162.843] (II) intel(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
[   162.843] (II) intel(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[   162.843] (II) intel(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[   162.843] (II) intel(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[   162.843] (II) intel(0): Not using default mode "640x480" (vrefresh out of range)
[   162.844] (II) intel(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[   162.844] (II) intel(0): Not using default mode "800x600" (vrefresh out of range)
[   162.844] (II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[   162.844] (II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[   162.844] (II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[   162.844] (II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[   162.844] (II) intel(0): Not using default mode "800x600" (vrefresh out of range)
[   162.844] (II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[   162.844] (II) intel(0): Not using default mode "1024x768i" (unknown reason)
[   162.844] (II) intel(0): Not using default mode "512x384i" (bad mode clock/interlace/doublescan)
[   162.844] (II) intel(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
[   162.844] (II) intel(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
[   162.845] (II) intel(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
[   162.845] (II) intel(0): Not using default mode "1024x768" (hsync out of range)
[   162.845] (II) intel(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
[   162.845] (II) intel(0): Not using default mode "1152x864" (width too large for virtual size)
[   162.845] (II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[   162.845] (II) intel(0): Not using default mode "1280x960" (width too large for virtual size)
[   162.845] (II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
[   162.845] (II) intel(0): Not using default mode "1280x960" (width too large for virtual size)
[   162.845] (II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
[   162.845] (II) intel(0): Not using default mode "1280x1024" (width too large for virtual size)
[   162.845] (II) intel(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
[   162.845] (II) intel(0): Not using default mode "1280x1024" (width too large for virtual size)
[   162.845] (II) intel(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
[   162.845] (II) intel(0): Not using default mode "1280x1024" (width too large for virtual size)
[   162.845] (II) intel(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
[   162.846] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[   162.846] (II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[   162.846] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[   162.846] (II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[   162.846] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[   162.846] (II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[   162.846] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[   162.846] (II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[   162.846] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[   162.846] (II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[   162.846] (II) intel(0): Not using default mode "1792x1344" (width too large for virtual size)
[   162.846] (II) intel(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
[   162.846] (II) intel(0): Not using default mode "1792x1344" (width too large for virtual size)
[   162.846] (II) intel(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
[   162.847] (II) intel(0): Not using default mode "1856x1392" (width too large for virtual size)
[   162.847] (II) intel(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
[   162.847] (II) intel(0): Not using default mode "1856x1392" (width too large for virtual size)
[   162.847] (II) intel(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
[   162.847] (II) intel(0): Not using default mode "1920x1440" (width too large for virtual size)
[   162.847] (II) intel(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
[   162.847] (II) intel(0): Not using default mode "1920x1440" (width too large for virtual size)
[   162.847] (II) intel(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
[   162.847] (II) intel(0): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
[   162.847] (II) intel(0): Not using default mode "1152x864" (width too large for virtual size)
[   162.847] (II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[   162.847] (II) intel(0): Not using default mode "1152x864" (width too large for virtual size)
[   162.847] (II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[   162.847] (II) intel(0): Not using default mode "1152x864" (width too large for virtual size)
[   162.848] (II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[   162.848] (II) intel(0): Not using default mode "1152x864" (width too large for virtual size)
[   162.848] (II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[   162.848] (II) intel(0): Not using default mode "1152x864" (width too large for virtual size)
[   162.848] (II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[   162.848] (II) intel(0): Not using default mode "1152x864" (width too large for virtual size)
[   162.848] (II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[   162.848] (II) intel(0): Not using default mode "1360x768" (width too large for virtual size)
[   162.848] (II) intel(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
[   162.848] (II) intel(0): Not using default mode "1360x768" (width too large for virtual size)
[   162.848] (II) intel(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
[   162.848] (II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
[   162.848] (II) intel(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
[   162.848] (II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
[   162.849] (II) intel(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
[   162.849] (II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
[   162.849] (II) intel(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
[   162.849] (II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
[   162.849] (II) intel(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
[   162.849] (II) intel(0): Not using default mode "1440x900" (width too large for virtual size)
[   162.849] (II) intel(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
[   162.849] (II) intel(0): Not using default mode "1600x1024" (width too large for virtual size)
[   162.849] (II) intel(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
[   162.849] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[   162.849] (II) intel(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[   162.849] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[   162.849] (II) intel(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[   162.849] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[   162.850] (II) intel(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[   162.850] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[   162.850] (II) intel(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[   162.850] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[   162.850] (II) intel(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[   162.850] (II) intel(0): Not using default mode "1920x1080" (width too large for virtual size)
[   162.850] (II) intel(0): Not using default mode "960x540" (bad mode clock/interlace/doublescan)
[   162.850] (II) intel(0): Not using default mode "1920x1200" (width too large for virtual size)
[   162.850] (II) intel(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
[   162.850] (II) intel(0): Not using default mode "1920x1440" (width too large for virtual size)
[   162.850] (II) intel(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
[   162.850] (II) intel(0): Not using default mode "2048x1536" (width too large for virtual size)
[   162.850] (II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
[   162.850] (II) intel(0): Not using default mode "2048x1536" (width too large for virtual size)
[   162.851] (II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
[   162.851] (II) intel(0): Not using default mode "2048x1536" (width too large for virtual size)
[   162.851] (II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
[   162.851] (II) intel(0): Not using driver mode "1280x1024" (width too large for virtual size)
[   162.851] (--) intel(0): Virtual size is 1024x768 (pitch 1024)
[   162.851] (**) intel(0): *Driver mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
[   162.851] (II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   162.851] (**) intel(0): *Driver mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
[   162.851] (II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   162.851] (**) intel(0): *Driver mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
[   162.851] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   162.852] (**) intel(0): *Default mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
[   162.852] (II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   162.852] (**) intel(0): *Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
[   162.852] (II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   162.852] (**) intel(0): *Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
[   162.852] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   162.852] (**) intel(0): *Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
[   162.852] (II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   162.852] (**) intel(0): *Driver mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
[   162.852] (II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   162.853] (**) intel(0): *Driver mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
[   162.853] (II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   162.853] (**) intel(0): *Driver mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
[   162.853] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   162.853] (**) intel(0): *Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
[   162.853] (II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   162.853] (**) intel(0): *Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
[   162.853] (II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   162.853] (**) intel(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
[   162.853] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   162.853] (**) intel(0): *Driver mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
[   162.854] (II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   162.854] (**) intel(0): *Driver mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
[   162.854] (II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[   162.854] (**) intel(0): *Driver mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
[   162.854] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   162.854] (**) intel(0): *Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
[   162.854] (II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   162.854] (**) intel(0): *Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
[   162.854] (II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[   162.854] (**) intel(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
[   162.854] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   162.855] (**) intel(0): *Driver mode "720x400": 28.3 MHz, 31.5 kHz, 70.1 Hz
[   162.855] (II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   162.855] (**) intel(0): Display dimensions: (280, 200) mm
[   162.855] (**) intel(0): DPI set to (92, 97)
[   162.855] (II) Loading sub module "fb"
[   162.855] (II) LoadModule: "fb"
[   162.857] (II) Loading /usr/lib/xorg/modules/libfb.so
[   162.857] (II) Module fb: vendor="X.Org Foundation"
[   162.858] 	compiled for 1.9.0, module version = 1.0.0
[   162.858] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   162.858] (II) Loading sub module "ramdac"
[   162.858] (II) LoadModule: "ramdac"
[   162.858] (II) Module "ramdac" already built-in
[   162.858] (**) intel(0): page flipping disabled
[   162.858] (II) intel(0): XvMC is Disabled: use XvMCSurfaces config option to enable.
[   162.858] (II) UnloadModule: "vesa"
[   162.858] (II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   162.858] (II) UnloadModule: "fbdev"
[   162.858] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   162.858] (II) UnloadModule: "fbdevhw"
[   162.858] (II) Unloading /usr/lib/xorg/modules/libfbdevhw.so
[   162.859] drmOpenDevice: node name is /dev/dri/card0
[   162.859] drmOpenDevice: open result is 12, (OK)
[   162.859] drmOpenDevice: node name is /dev/dri/card0
[   162.859] drmOpenDevice: open result is 12, (OK)
[   162.859] drmOpenByBusid: Searching for BusID pci:0000:00:01.0
[   162.859] drmOpenDevice: node name is /dev/dri/card0
[   162.860] drmOpenDevice: open result is 12, (OK)
[   162.860] drmOpenByBusid: drmOpenMinor returns 12
[   162.860] drmOpenByBusid: drmGetBusid reports pci:0000:00:01.0
[   162.860] (II) [drm] DRM interface version 1.3
[   162.860] (II) [drm] DRM open master succeeded.
[   162.860] (II) intel(0): [drm] Using the DRM lock SAREA also for drawables.
[   162.860] (II) intel(0): [drm] framebuffer handle = 0xe8000000
[   162.860] (II) intel(0): [drm] added 1 reserved context for kernel
[   162.861] (II) intel(0): X context handle = 0x1
[   162.861] (II) intel(0): [drm] installed DRM signal handler
[   162.861] (II) intel(0): [drm] Registers = 0xeff80000
[   162.861] (II) intel(0): [agp] dcacheHandle : 0x0
[   162.861] (II) intel(0): [agp] GART: no dcache memory found
[   162.873] (II) intel(0): [agp] Bound backbuffer memory
[   162.884] (II) intel(0): [agp] Bound depthbuffer memory
[   163.037] (II) intel(0): [agp] Bound System Texture Memory
[   163.038] (II) intel(0): [agp] GART: Allocated 4K for mouse cursor image
[   163.039] (II) intel(0): [agp] GART: Allocated 16K for ARGB mouse cursor image
[   163.039] (II) intel(0): Adding 768 scanlines for pixmap caching
[   163.039] (II) intel(0): Allocated Scratch Memory
[   163.039] (II) intel(0): [dri] Buffer map : 13fb000
[   163.039] (II) intel(0): [drm] added 256 4096 byte DMA buffers
[   163.039] (II) intel(0): [drm] Init v1.4 interface.
[   163.044] (II) intel(0): [drm] dma control initialized, using IRQ -22
[   163.045] (II) intel(0): [dri] visual configs initialized.
[   163.063] (II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
[   163.065] (II) intel(0): Setting dot clock to 78.7 MHz [ 0x50 0x17 0x20 ] [ 82 25 2 ]
[   163.065] (II) intel(0): chose watermark 0x2210e000: (tab.freq 78.8)
[   163.125] (II) intel(0): Using XFree86 Acceleration Architecture (XAA)
[   163.125] 	Screen to screen bit blits
[   163.126] 	Solid filled rectangles
[   163.126] 	8x8 mono pattern filled rectangles
[   163.126] 	Indirect CPU to Screen color expansion
[   163.126] 	Solid Horizontal and Vertical Lines
[   163.126] 	Setting up tile and stipple cache:
[   163.126] 		24 128x128 slots
[   163.126] 		6 256x256 slots
[   163.126] (==) intel(0): Backing store disabled
[   163.126] (==) intel(0): Silken mouse enabled
[   163.127] (==) intel(0): DPMS enabled
[   163.127] (II) intel(0): [DRI] installation complete
[   163.127] (II) intel(0): Direct rendering enabled
[   163.127] (==) RandR enabled
[   163.127] (II) Initializing built-in extension Generic Event Extension
[   163.128] (II) Initializing built-in extension SHAPE
[   163.128] (II) Initializing built-in extension MIT-SHM
[   163.128] (II) Initializing built-in extension XInputExtension
[   163.128] (II) Initializing built-in extension XTEST
[   163.128] (II) Initializing built-in extension BIG-REQUESTS
[   163.128] (II) Initializing built-in extension SYNC
[   163.128] (II) Initializing built-in extension XKEYBOARD
[   163.128] (II) Initializing built-in extension XC-MISC
[   163.128] (II) Initializing built-in extension SECURITY
[   163.128] (II) Initializing built-in extension XINERAMA
[   163.128] (II) Initializing built-in extension XFIXES
[   163.128] (II) Initializing built-in extension RENDER
[   163.128] (II) Initializing built-in extension RANDR
[   163.128] (II) Initializing built-in extension COMPOSITE
[   163.128] (II) Initializing built-in extension DAMAGE
[   163.128] (II) Initializing built-in extension GESTURE
[   163.178] (II) AIGLX: Screen 0 is not DRI2 capable
[   163.179] drmOpenDevice: node name is /dev/dri/card0
[   163.179] drmOpenDevice: open result is 13, (OK)
[   166.176] drmOpenByBusid: Searching for BusID pci:0000:00:01.0
[   166.177] drmOpenDevice: node name is /dev/dri/card0
[   166.177] drmOpenDevice: open result is 13, (OK)
[   166.177] drmOpenByBusid: drmOpenMinor returns 13
[   166.177] drmOpenByBusid: drmGetBusid reports pci:0000:00:01.0
[   166.195] (II) AIGLX: Loaded and initialized /usr/lib/dri/i810_dri.so
[   166.196] (II) GLX: Initialized DRI GL provider for screen 0
[   166.299] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   166.341] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event0)
[   166.342] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[   166.342] (II) LoadModule: "evdev"
[   166.343] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   166.345] (II) Module evdev: vendor="X.Org Foundation"
[   166.345] 	compiled for 1.9.0, module version = 2.3.2
[   166.345] 	Module class: X.Org XInput Driver
[   166.345] 	ABI class: X.Org XInput driver, version 11.0
[   166.345] (**) AT Translated Set 2 keyboard: always reports core events
[   166.346] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event0"
[   166.346] (II) AT Translated Set 2 keyboard: Found keys
[   166.346] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[   166.346] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[   166.346] (**) Option "xkb_rules" "evdev"
[   166.346] (**) Option "xkb_model" "evdev"
[   166.346] (**) Option "xkb_layout" "gb"
[   166.359] (II) XKB: reuse xkmfile /var/lib/xkb/server-C1F82522E3F958F13C2D6D2C62551E135092F235.xkm
[   166.363] (II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/event1)
[   166.363] (**) PS/2 Generic Mouse: Applying InputClass "evdev pointer catchall"
[   166.364] (**) PS/2 Generic Mouse: always reports core events
[   166.364] (**) PS/2 Generic Mouse: Device: "/dev/input/event1"
[   166.364] (II) PS/2 Generic Mouse: Found 3 mouse buttons
[   166.364] (II) PS/2 Generic Mouse: Found relative axes
[   166.364] (II) PS/2 Generic Mouse: Found x and y relative axes
[   166.364] (II) PS/2 Generic Mouse: Configuring as mouse
[   166.364] (**) PS/2 Generic Mouse: YAxisMapping: buttons 4 and 5
[   166.364] (**) PS/2 Generic Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   166.364] (II) XINPUT: Adding extended input device "PS/2 Generic Mouse" (type: MOUSE)
[   166.365] (II) PS/2 Generic Mouse: initialized for relative axes.
[   166.366] (II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/mouse0)
[   166.366] (II) No input driver/identifier specified (ignoring)

```

tia

---

### Post by NightwishFan on 2010-11-06
Yes there the segmentation fault means the session crashed. Can you post what  your display device is? Run:
```
sudo lshw -C display
```

Nothing stands out in the log for me. If I know your chip I might know more.

---

### Post by candtalan on 2010-11-07
> **NightwishFan said:**
> Yes there the segmentation fault means the session crashed. Can you post what  your display device is? Run:
```
sudo lshw -C display
```

Nothing stands out in the log for me. If I know your chip I might know more.
Thanks.
Incidentally, I then installed xubuntu-desktop in the hope that different (window managers?) software might do something, but then in both sessions, normal gnome and normal xubuntu sessions the same crash seemed to happen. The only way to login and run stuff is by choosing safe mode ('ubuntu desktop edition safe mode'), running now to post this.

```

 sudo lshw -C display
[sudo] password for user1: 
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: 82810 (CGC) Chipset Graphics Controller
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 03
       width: 32 bits
       clock: 66MHz
       capabilities: pm vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:e8000000-ebffffff memory:eff80000-efffffff



```

---

### Post by NightwishFan on 2010-11-07
Ok, try this on for size.

Press alt+f2 in gnome and type (and press enter after, the X in X11 is caps): gksudo gedit /etc/X11/xorg.conf

Paste this into the file:
```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "intel"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```

Save, then log out and try to log back in as a normal session.

---

### Post by candtalan on 2010-11-07
Some more details about the hardware in case it can be useful for someone:
The PC is from the 'Tiny' Computers range (UK) model 810L. PIII, I am using on (main) board graphics. I have just looked closely at the inscriptions and chips on the Mboard and the large Intel chip is marked as 

Intel FW82801AA 
F005IB86
SL3MA
INTEL (M) (C) '98
KOREA

I note with interest that the software reported itself as
82810
(not 82801 as marked on the outside of the chip) which seems a bit odd to me, but maybe  it is normal practice?

The mainboasd is marked with a barcode sticker:
M/B
0010046100400

The white MB screen print includes a large apparent board ID:
MS6178 VER:1.1

(Just seen your recent response - will  look at that thanks)

---

### Post by NightwishFan on 2010-11-07
If that does not work, try rebooting, and if you still have issues as a temporary workaround you can try this. Do the same but add this to the file instead:
```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```

Then reboot. You will not have 3d accleration if you do this though, but perhaps it will suit until you find some answers.

---

### Post by candtalan on 2010-11-07
> **NightwishFan said:**
> Ok, try this on for size.

Press alt+f2 in gnome and type (and press enter after, the X in X11 is caps): gksudo gedit /etc/X11/xorg.conf

Paste this into the file:
```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "intel"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```

Save, then log out and try to log back in as a normal session.

Did this, noted the file was initially empty, then logged out and tried log in normally but unfortunately same problem.

fwiw contents currently following te failed attempt and now in safe mode:
/var/log/Xorg.0.log


```

[  4356.713] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[  4356.713] X Protocol Version 11, Revision 0
[  4356.714] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[  4356.714] Current Operating System: Linux davidputt-MS-6178 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:36:48 UTC 2010 i686
[  4356.714] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=910e9a36-0367-4a7d-9d2d-29b60ad06811 ro quiet splash
[  4356.714] Build Date: 16 September 2010  05:39:22PM
[  4356.714] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
[  4356.714] Current version of pixman: 0.18.4
[  4356.714] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[  4356.714] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  4356.715] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Nov  7 12:54:23 2010
[  4356.716] (==) Using config file: "/etc/X11/xorg.conf"
[  4356.716] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  4356.717] (==) No Layout section.  Using the first Screen section.
[  4356.717] (**) |-->Screen "Default Screen" (0)
[  4356.717] (**) |   |-->Monitor "Configured Monitor"
[  4356.718] (**) |   |-->Device "Configured Video Device"
[  4356.719] (==) Automatically adding devices
[  4356.719] (==) Automatically enabling devices
[  4356.719] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  4356.719] 	Entry deleted from font path.
[  4356.719] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[  4356.719] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  4356.720] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[  4356.720] (II) Loader magic: 0x81f8e00
[  4356.720] (II) Module ABI versions:
[  4356.720] 	X.Org ANSI C Emulation: 0.4
[  4356.720] 	X.Org Video Driver: 8.0
[  4356.720] 	X.Org XInput driver : 11.0
[  4356.720] 	X.Org Server Extension : 4.0
[  4356.722] (--) PCI:*(0:0:1:0) 8086:7121:8086:0200 rev 3, Mem @ 0xe8000000/67108864, 0xeff80000/524288
[  4356.724] (II) Open ACPI successful (/var/run/acpid.socket)
[  4356.724] (II) LoadModule: "extmod"
[  4356.725] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[  4356.726] (II) Module extmod: vendor="X.Org Foundation"
[  4356.726] 	compiled for 1.9.0, module version = 1.0.0
[  4356.726] 	Module class: X.Org Server Extension
[  4356.726] 	ABI class: X.Org Server Extension, version 4.0
[  4356.726] (II) Loading extension MIT-SCREEN-SAVER
[  4356.726] (II) Loading extension XFree86-VidModeExtension
[  4356.726] (II) Loading extension XFree86-DGA
[  4356.726] (II) Loading extension DPMS
[  4356.727] (II) Loading extension XVideo
[  4356.727] (II) Loading extension XVideo-MotionCompensation
[  4356.727] (II) Loading extension X-Resource
[  4356.727] (II) LoadModule: "dbe"
[  4356.727] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[  4356.728] (II) Module dbe: vendor="X.Org Foundation"
[  4356.728] 	compiled for 1.9.0, module version = 1.0.0
[  4356.728] 	Module class: X.Org Server Extension
[  4356.728] 	ABI class: X.Org Server Extension, version 4.0
[  4356.728] (II) Loading extension DOUBLE-BUFFER
[  4356.728] (II) LoadModule: "glx"
[  4356.729] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[  4356.730] (II) Module glx: vendor="X.Org Foundation"
[  4356.730] 	compiled for 1.9.0, module version = 1.0.0
[  4356.730] 	ABI class: X.Org Server Extension, version 4.0
[  4356.730] (==) AIGLX enabled
[  4356.730] (II) Loading extension GLX
[  4356.730] (II) LoadModule: "record"
[  4356.731] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[  4356.731] (II) Module record: vendor="X.Org Foundation"
[  4356.732] 	compiled for 1.9.0, module version = 1.13.0
[  4356.732] 	Module class: X.Org Server Extension
[  4356.732] 	ABI class: X.Org Server Extension, version 4.0
[  4356.732] (II) Loading extension RECORD
[  4356.732] (II) LoadModule: "dri"
[  4356.733] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[  4356.734] (II) Module dri: vendor="X.Org Foundation"
[  4356.734] 	compiled for 1.9.0, module version = 1.0.0
[  4356.734] 	ABI class: X.Org Server Extension, version 4.0
[  4356.734] (II) Loading extension XFree86-DRI
[  4356.734] (II) LoadModule: "dri2"
[  4356.735] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[  4356.735] (II) Module dri2: vendor="X.Org Foundation"
[  4356.735] 	compiled for 1.9.0, module version = 1.2.0
[  4356.735] 	ABI class: X.Org Server Extension, version 4.0
[  4356.735] (II) Loading extension DRI2
[  4356.735] (II) LoadModule: "intel"
[  4356.737] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[  4356.738] (II) Module intel: vendor="X.Org Foundation"
[  4356.738] 	compiled for 1.9.0, module version = 2.12.0
[  4356.738] 	Module class: X.Org Video Driver
[  4356.738] 	ABI class: X.Org Video Driver, version 8.0
[  4356.738] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
	Sandybridge, Sandybridge
[  4356.742] (--) using VT number 9

[  4356.759] (II) Loading sub module "vgahw"
[  4356.759] (II) LoadModule: "vgahw"
[  4356.760] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[  4356.761] (II) Module vgahw: vendor="X.Org Foundation"
[  4356.761] 	compiled for 1.9.0, module version = 0.1.0
[  4356.761] 	ABI class: X.Org Video Driver, version 8.0
[  4356.761] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 16/16
[  4356.761] (==) intel(0): Depth 16, (==) framebuffer bpp 16
[  4356.761] (==) intel(0): RGB weight 565
[  4356.761] (==) intel(0): Default visual is TrueColor
[  4356.761] (II) Loading sub module "xaa"
[  4356.761] (II) LoadModule: "xaa"
[  4356.762] (II) Loading /usr/lib/xorg/modules/libxaa.so
[  4356.763] (II) Module xaa: vendor="X.Org Foundation"
[  4356.763] 	compiled for 1.9.0, module version = 1.2.1
[  4356.763] 	ABI class: X.Org Video Driver, version 8.0
[  4356.763] (II) Loading sub module "vbe"
[  4356.763] (II) LoadModule: "vbe"
[  4356.764] (II) Loading /usr/lib/xorg/modules/libvbe.so
[  4356.764] (II) Module vbe: vendor="X.Org Foundation"
[  4356.765] 	compiled for 1.9.0, module version = 1.1.0
[  4356.765] 	ABI class: X.Org Video Driver, version 8.0
[  4356.765] (II) Loading sub module "int10"
[  4356.765] (II) LoadModule: "int10"
[  4356.766] (II) Loading /usr/lib/xorg/modules/libint10.so
[  4356.766] (II) Module int10: vendor="X.Org Foundation"
[  4356.766] 	compiled for 1.9.0, module version = 1.0.0
[  4356.766] 	ABI class: X.Org Video Driver, version 8.0
[  4356.767] (II) intel(0): initializing int10
[  4356.775] (II) intel(0): Primary V_BIOS segment is: 0xc000
[  4356.777] (II) intel(0): VESA BIOS detected
[  4356.777] (II) intel(0): VESA VBE Version 2.0
[  4356.777] (II) intel(0): VESA VBE Total Mem: 1024 kB
[  4356.777] (II) intel(0): VESA VBE OEM: Intel810(TM) Graphics Chip Accelerated VGA BIOS
[  4356.777] (II) intel(0): VESA VBE OEM Software Rev: 3.1
[  4356.777] (II) intel(0): VESA VBE OEM Vendor: Intel Corporation
[  4356.777] (II) intel(0): VESA VBE OEM Product: i810 Graphics Controller
[  4356.777] (II) intel(0): VESA VBE OEM Product Rev: Hardware Version 0.0
[  4356.777] (II) Loading sub module "ddc"
[  4356.777] (II) LoadModule: "ddc"
[  4356.777] (II) Module "ddc" already built-in
[  4356.835] (II) intel(0): VESA VBE DDC supported
[  4356.835] (II) intel(0): VESA VBE DDC Level 2
[  4356.835] (II) intel(0): VESA VBE DDC transfer in appr. 1 sec.
[  4358.213] (II) intel(0): VESA VBE DDC read successfully
[  4358.213] (II) intel(0): Manufacturer: DEL  Model: 4274  Serial#: 811029078
[  4358.213] (II) intel(0): Year: 1995  Week: 47
[  4358.213] (II) intel(0): EDID Version: 1.0
[  4358.213] (II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[  4358.214] (II) intel(0): Sync:  Separate
[  4358.214] (II) intel(0): Max Image Size [cm]: horiz.: 28  vert.: 20
[  4358.214] (II) intel(0): Gamma: 1.01
[  4358.214] (II) intel(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[  4358.214] (II) intel(0): redX: 0.004 redY: 0.004   greenX: 0.004 greenY: 0.005
[  4358.214] (II) intel(0): blueX: 0.004 blueY: 0.004   whiteX: 0.004 whiteY: 0.005
[  4358.214] (II) intel(0): Supported established timings:
[  4358.214] (II) intel(0): 720x400@70Hz
[  4358.214] (II) intel(0): 640x480@60Hz
[  4358.215] (II) intel(0): 640x480@72Hz
[  4358.215] (II) intel(0): 640x480@75Hz
[  4358.215] (II) intel(0): 800x600@60Hz
[  4358.215] (II) intel(0): 800x600@72Hz
[  4358.215] (II) intel(0): 800x600@75Hz
[  4358.215] (II) intel(0): 1024x768@60Hz
[  4358.215] (II) intel(0): 1024x768@70Hz
[  4358.215] (II) intel(0): 1024x768@75Hz
[  4358.215] (II) intel(0): Manufacturer's mask: 0
[  4358.215] (II) intel(0): Supported detailed timing:
[  4358.215] (II) intel(0): clock: 110.0 MHz   Image Size:  262 x 196 mm
[  4358.215] (II) intel(0): h_active: 1280  h_sync: 1358  h_sync_end 1470 h_blank_end 1720 h_border: 0
[  4358.215] (II) intel(0): v_active: 1024  v_sync: 1025  v_sync_end 1030 v_blanking: 1067 v_border: 0
[  4358.216] (II) intel(0): EDID (in hex):
[  4358.216] (II) intel(0): 	00ffffffffffff0010ac744256525730
[  4358.216] (II) intel(0): 	2f050100081c1401e801010101010101
[  4358.216] (II) intel(0): 	010101adce0001010101010101010101
[  4358.216] (II) intel(0): 	010101010101f82a00b851002b404e70
[  4358.216] (II) intel(0): 	150006c4100000180101010101010101
[  4358.216] (II) intel(0): 	01010101010101010101010101010101
[  4358.216] (II) intel(0): 	01010101010101010101010101010101
[  4358.216] (II) intel(0): 	010101010101010101010101010100e9
[  4358.216] (II) intel(0): EDID vendor "DEL", prod id 17012
[  4358.216] (II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
[  4358.216] (II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
[  4358.217] (II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
[  4358.217] (II) intel(0): Printing DDC gathered Modelines:
[  4358.217] (II) intel(0): Modeline "1280x1024"x0.0  110.00  1280 1358 1470 1720  1024 1025 1030 1067 -hsync -vsync (64.0 kHz)
[  4358.217] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  4358.217] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  4358.217] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[  4358.217] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  4358.217] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  4358.217] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  4358.217] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[  4358.217] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  4358.218] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  4358.218] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[  4358.218] (--) intel(0): Chipset: "i810"
[  4358.218] (--) intel(0): Linear framebuffer at 0xE8000000
[  4358.218] (--) intel(0): IO registers at addr 0xEFF80000
[  4358.219] (II) intel(0): Kernel reported 106752 total, 1 used
[  4358.219] (II) intel(0): I810CheckAvailableMemory: 427004k available
[  4358.219] (==) intel(0): Will alloc AGP framebuffer: 24576 kByte
[  4358.219] (==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
[  4358.219] (II) intel(0): Configured Monitor: Using hsync range of 31.47-63.95 kHz
[  4358.219] (II) intel(0): Configured Monitor: Using vrefresh range of 59.94-75.03 Hz
[  4358.219] (II) intel(0): Estimated virtual size for aspect ratio 1.4000 is 1024x768
[  4358.219] (II) intel(0): Clock range:   9.50 to 163.00 MHz
[  4358.219] (II) intel(0): Not using default mode "640x350" (vrefresh out of range)
[  4358.220] (II) intel(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
[  4358.220] (II) intel(0): Not using default mode "640x400" (vrefresh out of range)
[  4358.220] (II) intel(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
[  4358.220] (II) intel(0): Not using default mode "720x400" (vrefresh out of range)
[  4358.220] (II) intel(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
[  4358.220] (II) intel(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[  4358.220] (II) intel(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[  4358.220] (II) intel(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[  4358.220] (II) intel(0): Not using default mode "640x480" (vrefresh out of range)
[  4358.220] (II) intel(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[  4358.220] (II) intel(0): Not using default mode "800x600" (vrefresh out of range)
[  4358.220] (II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[  4358.220] (II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[  4358.221] (II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[  4358.221] (II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[  4358.221] (II) intel(0): Not using default mode "800x600" (vrefresh out of range)
[  4358.221] (II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[  4358.221] (II) intel(0): Not using default mode "1024x768i" (unknown reason)
[  4358.221] (II) intel(0): Not using default mode "512x384i" (bad mode clock/interlace/doublescan)
[  4358.221] (II) intel(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
[  4358.221] (II) intel(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
[  4358.221] (II) intel(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
[  4358.221] (II) intel(0): Not using default mode "1024x768" (hsync out of range)
[  4358.221] (II) intel(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
[  4358.221] (II) intel(0): Not using default mode "1152x864" (width too large for virtual size)
[  4358.221] (II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[  4358.221] (II) intel(0): Not using default mode "1280x960" (width too large for virtual size)
[  4358.222] (II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
[  4358.222] (II) intel(0): Not using default mode "1280x960" (width too large for virtual size)
[  4358.222] (II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
[  4358.222] (II) intel(0): Not using default mode "1280x1024" (width too large for virtual size)
[  4358.222] (II) intel(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
[  4358.222] (II) intel(0): Not using default mode "1280x1024" (width too large for virtual size)
[  4358.222] (II) intel(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
[  4358.222] (II) intel(0): Not using default mode "1280x1024" (width too large for virtual size)
[  4358.222] (II) intel(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
[  4358.222] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[  4358.222] (II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[  4358.222] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[  4358.222] (II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[  4358.222] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[  4358.223] (II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[  4358.223] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[  4358.223] (II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[  4358.223] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[  4358.223] (II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[  4358.223] (II) intel(0): Not using default mode "1792x1344" (width too large for virtual size)
[  4358.223] (II) intel(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
[  4358.223] (II) intel(0): Not using default mode "1792x1344" (width too large for virtual size)
[  4358.223] (II) intel(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
[  4358.223] (II) intel(0): Not using default mode "1856x1392" (width too large for virtual size)
[  4358.223] (II) intel(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
[  4358.223] (II) intel(0): Not using default mode "1856x1392" (width too large for virtual size)
[  4358.223] (II) intel(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
[  4358.223] (II) intel(0): Not using default mode "1920x1440" (width too large for virtual size)
[  4358.224] (II) intel(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
[  4358.224] (II) intel(0): Not using default mode "1920x1440" (width too large for virtual size)
[  4358.224] (II) intel(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
[  4358.224] (II) intel(0): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
[  4358.224] (II) intel(0): Not using default mode "1152x864" (width too large for virtual size)
[  4358.224] (II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[  4358.224] (II) intel(0): Not using default mode "1152x864" (width too large for virtual size)
[  4358.224] (II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[  4358.224] (II) intel(0): Not using default mode "1152x864" (width too large for virtual size)
[  4358.224] (II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[  4358.224] (II) intel(0): Not using default mode "1152x864" (width too large for virtual size)
[  4358.224] (II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[  4358.224] (II) intel(0): Not using default mode "1152x864" (width too large for virtual size)
[  4358.224] (II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[  4358.225] (II) intel(0): Not using default mode "1152x864" (width too large for virtual size)
[  4358.225] (II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[  4358.225] (II) intel(0): Not using default mode "1360x768" (width too large for virtual size)
[  4358.225] (II) intel(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
[  4358.225] (II) intel(0): Not using default mode "1360x768" (width too large for virtual size)
[  4358.225] (II) intel(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
[  4358.225] (II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
[  4358.225] (II) intel(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
[  4358.225] (II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
[  4358.225] (II) intel(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
[  4358.225] (II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
[  4358.225] (II) intel(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
[  4358.225] (II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
[  4358.225] (II) intel(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
[  4358.226] (II) intel(0): Not using default mode "1440x900" (width too large for virtual size)
[  4358.226] (II) intel(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
[  4358.226] (II) intel(0): Not using default mode "1600x1024" (width too large for virtual size)
[  4358.226] (II) intel(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
[  4358.226] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[  4358.226] (II) intel(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[  4358.226] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[  4358.226] (II) intel(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[  4358.226] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[  4358.226] (II) intel(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[  4358.226] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[  4358.226] (II) intel(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[  4358.226] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[  4358.226] (II) intel(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[  4358.227] (II) intel(0): Not using default mode "1920x1080" (width too large for virtual size)
[  4358.227] (II) intel(0): Not using default mode "960x540" (bad mode clock/interlace/doublescan)
[  4358.227] (II) intel(0): Not using default mode "1920x1200" (width too large for virtual size)
[  4358.227] (II) intel(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
[  4358.227] (II) intel(0): Not using default mode "1920x1440" (width too large for virtual size)
[  4358.227] (II) intel(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
[  4358.227] (II) intel(0): Not using default mode "2048x1536" (width too large for virtual size)
[  4358.227] (II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
[  4358.227] (II) intel(0): Not using default mode "2048x1536" (width too large for virtual size)
[  4358.227] (II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
[  4358.227] (II) intel(0): Not using default mode "2048x1536" (width too large for virtual size)
[  4358.227] (II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
[  4358.227] (II) intel(0): Not using driver mode "1280x1024" (width too large for virtual size)
[  4358.228] (--) intel(0): Virtual size is 1024x768 (pitch 1024)
[  4358.228] (**) intel(0): *Driver mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
[  4358.228] (II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  4358.228] (**) intel(0): *Driver mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
[  4358.228] (II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[  4358.228] (**) intel(0): *Driver mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
[  4358.228] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  4358.228] (**) intel(0): *Default mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
[  4358.228] (II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  4358.228] (**) intel(0): *Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
[  4358.229] (II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[  4358.229] (**) intel(0): *Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
[  4358.229] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  4358.229] (**) intel(0): *Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
[  4358.229] (II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[  4358.229] (**) intel(0): *Driver mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
[  4358.229] (II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  4358.229] (**) intel(0): *Driver mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
[  4358.229] (II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[  4358.229] (**) intel(0): *Driver mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
[  4358.229] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  4358.230] (**) intel(0): *Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
[  4358.230] (II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  4358.230] (**) intel(0): *Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
[  4358.230] (II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[  4358.230] (**) intel(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
[  4358.230] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  4358.230] (**) intel(0): *Driver mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
[  4358.230] (II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  4358.230] (**) intel(0): *Driver mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
[  4358.230] (II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[  4358.230] (**) intel(0): *Driver mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
[  4358.231] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  4358.231] (**) intel(0): *Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
[  4358.231] (II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  4358.231] (**) intel(0): *Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
[  4358.231] (II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[  4358.231] (**) intel(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
[  4358.231] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  4358.231] (**) intel(0): *Driver mode "720x400": 28.3 MHz, 31.5 kHz, 70.1 Hz
[  4358.231] (II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  4358.231] (**) intel(0): Display dimensions: (280, 200) mm
[  4358.231] (**) intel(0): DPI set to (92, 97)
[  4358.232] (II) Loading sub module "fb"
[  4358.232] (II) LoadModule: "fb"
[  4358.233] (II) Loading /usr/lib/xorg/modules/libfb.so
[  4358.234] (II) Module fb: vendor="X.Org Foundation"
[  4358.234] 	compiled for 1.9.0, module version = 1.0.0
[  4358.234] 	ABI class: X.Org ANSI C Emulation, version 0.4
[  4358.234] (II) Loading sub module "ramdac"
[  4358.234] (II) LoadModule: "ramdac"
[  4358.235] (II) Module "ramdac" already built-in
[  4358.235] (**) intel(0): page flipping disabled
[  4358.235] (II) intel(0): XvMC is Disabled: use XvMCSurfaces config option to enable.
[  4358.235] drmOpenDevice: node name is /dev/dri/card0
[  4358.235] drmOpenDevice: open result is 12, (OK)
[  4358.236] drmOpenDevice: node name is /dev/dri/card0
[  4358.236] drmOpenDevice: open result is 12, (OK)
[  4358.236] drmOpenByBusid: Searching for BusID pci:0000:00:01.0
[  4358.236] drmOpenDevice: node name is /dev/dri/card0
[  4358.236] drmOpenDevice: open result is 12, (OK)
[  4358.236] drmOpenByBusid: drmOpenMinor returns 12
[  4358.236] drmOpenByBusid: drmGetBusid reports pci:0000:00:01.0
[  4358.236] (II) [drm] DRM interface version 1.3
[  4358.236] (II) [drm] DRM open master succeeded.
[  4358.237] (II) intel(0): [drm] Using the DRM lock SAREA also for drawables.
[  4358.237] (II) intel(0): [drm] framebuffer handle = 0xe8000000
[  4358.237] (II) intel(0): [drm] added 1 reserved context for kernel
[  4358.237] (II) intel(0): X context handle = 0x1
[  4358.237] (II) intel(0): [drm] installed DRM signal handler
[  4358.237] (II) intel(0): [drm] Registers = 0xeff80000
[  4358.238] (II) intel(0): [agp] dcacheHandle : 0x0
[  4358.238] (II) intel(0): [agp] GART: no dcache memory found
[  4358.250] (II) intel(0): [agp] Bound backbuffer memory
[  4358.261] (II) intel(0): [agp] Bound depthbuffer memory
[  4358.415] (II) intel(0): [agp] Bound System Texture Memory
[  4358.416] (II) intel(0): [agp] GART: Allocated 4K for mouse cursor image
[  4358.417] (II) intel(0): [agp] GART: Allocated 16K for ARGB mouse cursor image
[  4358.417] (II) intel(0): Adding 768 scanlines for pixmap caching
[  4358.417] (II) intel(0): Allocated Scratch Memory
[  4358.417] (II) intel(0): [dri] Buffer map : 13fb000
[  4358.417] (II) intel(0): [drm] added 256 4096 byte DMA buffers
[  4358.417] (II) intel(0): [drm] Init v1.4 interface.
[  4358.422] (II) intel(0): [drm] dma control initialized, using IRQ -22
[  4358.422] (II) intel(0): [dri] visual configs initialized.
[  4358.442] (II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
[  4358.443] (II) intel(0): Setting dot clock to 78.7 MHz [ 0x50 0x17 0x20 ] [ 82 25 2 ]
[  4358.443] (II) intel(0): chose watermark 0x2210e000: (tab.freq 78.8)
[  4358.501] (II) intel(0): Using XFree86 Acceleration Architecture (XAA)
[  4358.501] 	Screen to screen bit blits
[  4358.501] 	Solid filled rectangles
[  4358.502] 	8x8 mono pattern filled rectangles
[  4358.502] 	Indirect CPU to Screen color expansion
[  4358.502] 	Solid Horizontal and Vertical Lines
[  4358.502] 	Setting up tile and stipple cache:
[  4358.502] 		24 128x128 slots
[  4358.502] 		6 256x256 slots
[  4358.502] (==) intel(0): Backing store disabled
[  4358.502] (==) intel(0): Silken mouse enabled
[  4358.503] (==) intel(0): DPMS enabled
[  4358.503] (II) intel(0): [DRI] installation complete
[  4358.503] (II) intel(0): Direct rendering enabled
[  4358.503] (==) RandR enabled
[  4358.503] (II) Initializing built-in extension Generic Event Extension
[  4358.503] (II) Initializing built-in extension SHAPE
[  4358.503] (II) Initializing built-in extension MIT-SHM
[  4358.504] (II) Initializing built-in extension XInputExtension
[  4358.504] (II) Initializing built-in extension XTEST
[  4358.504] (II) Initializing built-in extension BIG-REQUESTS
[  4358.504] (II) Initializing built-in extension SYNC
[  4358.504] (II) Initializing built-in extension XKEYBOARD
[  4358.504] (II) Initializing built-in extension XC-MISC
[  4358.504] (II) Initializing built-in extension SECURITY
[  4358.504] (II) Initializing built-in extension XINERAMA
[  4358.504] (II) Initializing built-in extension XFIXES
[  4358.504] (II) Initializing built-in extension RENDER
[  4358.504] (II) Initializing built-in extension RANDR
[  4358.504] (II) Initializing built-in extension COMPOSITE
[  4358.504] (II) Initializing built-in extension DAMAGE
[  4358.504] (II) Initializing built-in extension GESTURE
[  4358.554] (II) AIGLX: Screen 0 is not DRI2 capable
[  4358.554] drmOpenDevice: node name is /dev/dri/card0
[  4358.555] drmOpenDevice: open result is 13, (OK)
[  4361.552] drmOpenByBusid: Searching for BusID pci:0000:00:01.0
[  4361.552] drmOpenDevice: node name is /dev/dri/card0
[  4361.552] drmOpenDevice: open result is 13, (OK)
[  4361.552] drmOpenByBusid: drmOpenMinor returns 13
[  4361.552] drmOpenByBusid: drmGetBusid reports pci:0000:00:01.0
[  4361.570] (II) AIGLX: Loaded and initialized /usr/lib/dri/i810_dri.so
[  4361.575] (II) GLX: Initialized DRI GL provider for screen 0
[  4361.680] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  4361.718] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event0)
[  4361.718] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[  4361.718] (II) LoadModule: "evdev"
[  4361.720] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  4361.721] (II) Module evdev: vendor="X.Org Foundation"
[  4361.721] 	compiled for 1.9.0, module version = 2.3.2
[  4361.721] 	Module class: X.Org XInput Driver
[  4361.721] 	ABI class: X.Org XInput driver, version 11.0
[  4361.722] (**) AT Translated Set 2 keyboard: always reports core events
[  4361.722] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event0"
[  4361.722] (II) AT Translated Set 2 keyboard: Found keys
[  4361.722] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[  4361.722] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[  4361.722] (**) Option "xkb_rules" "evdev"
[  4361.722] (**) Option "xkb_model" "evdev"
[  4361.722] (**) Option "xkb_layout" "gb"
[  4361.741] (II) XKB: reuse xkmfile /var/lib/xkb/server-C1F82522E3F958F13C2D6D2C62551E135092F235.xkm
[  4361.746] (II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/event1)
[  4361.747] (**) PS/2 Generic Mouse: Applying InputClass "evdev pointer catchall"
[  4361.747] (**) PS/2 Generic Mouse: always reports core events
[  4361.747] (**) PS/2 Generic Mouse: Device: "/dev/input/event1"
[  4361.747] (II) PS/2 Generic Mouse: Found 3 mouse buttons
[  4361.747] (II) PS/2 Generic Mouse: Found relative axes
[  4361.747] (II) PS/2 Generic Mouse: Found x and y relative axes
[  4361.748] (II) PS/2 Generic Mouse: Configuring as mouse
[  4361.748] (**) PS/2 Generic Mouse: YAxisMapping: buttons 4 and 5
[  4361.748] (**) PS/2 Generic Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  4361.748] (II) XINPUT: Adding extended input device "PS/2 Generic Mouse" (type: MOUSE)
[  4361.748] (II) PS/2 Generic Mouse: initialized for relative axes.
[  4361.750] (II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/mouse0)
[  4361.750] (II) No input driver/identifier specified (ignoring)


```

---

### Post by NightwishFan on 2010-11-07
That is so strange the log seems quite normal. Did you try the second post? If that works then we know the problem is with the intel driver.

---

### Post by candtalan on 2010-11-07
> **candtalan said:**
> Did this, noted the file was initially empty, then logged out and tried log in normally but unfortunately same problem.

fwiw contents (snip)

After the unsuccessful log out/in attempt, I restarted the machine, and after a normal login I now do actually see a partial desktop with 10.10 default background, however this is not showing the top and bottom panels. A mouse right click offers the normal menu, eg create folder, which works.

I think I mentioned that this PC was one of a couple I had problems with panels not appearing (in ubuntu 10.04), I think a number of people had similar problems.

from the then relevant thread, I now tried the commands as follows using three separate uses of 
alt F2
```

gconftool-2 --shutdown

```
```

rm -rf ~/.gconf/apps/panel

```
```

pkill gnome-panel

```
and I now I see the panels appear. This is following an attempted 'normal' login.

=====================================================
I notice that there is a crash alert in the top panel, so I will go back to the problem PC and see if I can get any useful information.
=====================================================
sorry my bad, it is not a crash alert at all it is a red looking notification of a couple of updates which are now available.

---

### Post by NightwishFan on 2010-11-07
So after adding the "intel" related lines in xorg.conf and a reboot, and then retting gconf it works for you?

---

### Post by candtalan on 2010-11-07
> **NightwishFan said:**
> So after adding the "intel" related lines in xorg.conf and a reboot, and then retting gconf it works for you?

Yes, the desktop appeared without any panels (top or bottom), and the 'traditional' fix for missing panels worked. 

I did not (yet ) try the vesa  related edit (non intel). Would that be useful? [done]

I guess that means that the intel drive is ok and is not causing the crash?

Thanks

Edit:
I have now just also tried the vesa driver entry from your other post, and with this the desktop came up fast and complete with panels, whereas with the intel entry, there was a significant delay at the point before the (non-panels) desktop appeared. However, with the vesa entry the display is only 640x480


Edit2:
Having modified xorg.conf and presumably avoided an x crash, I find a second gotcha of no panels, as discussed above. I did in fact see 'no panels' early on with a clean install of Ubuntu 10.04
At the time, on the -same- machine an Ubuntu 10.04 which had online upgraded from 9.10 did not show the same no-panels problem.
[http://ubuntuforums.org/showthread.php?t=1479779](http://ubuntuforums.org/showthread.php?t=1479779)

The bug #542343 'gnome-panel will not autostart on lucid' seems to have been fixed, however, a possible issue of a race condition is commented on here:
[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/542343/comments/41](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/542343/comments/41)
It interested me because my problem is with older machines, and I am not aware of a bug filed relating to a possible race condition.

Edit3:
My machine here is a PIII 650MHz which is spot on for the race condition comment link above.

---

### Post by NightwishFan on 2010-11-07
If the intel version has delays but works correctly I advise you use that method. The vesa method will lack a lot of functionality.

---

### Post by candtalan on 2010-11-08
> **NightwishFan said:**
> If the intel version has delays but works correctly I advise you use that method. The vesa method will lack a lot of functionality.

Yes, OK, and thank you very much for your help with this.

However it does mean that with this old but working machine at present, it is not possible to make much use of Ubuntu 10.10 (or 10.04 LTS) - because of the missing panels at startup. I have a small charity awaiting a donation of such a machine (I have two in fact) and they will need it to start up normally.

If the missing panels problem is caused by the supposed race condition suggested in
[https://bugs.launchpad.net/ubuntu/+s...43/comments/41](https://bugs.launchpad.net/ubuntu/+s...43/comments/41)
 then I am not going to find a solution soon with Ubuntu and these old machines.

For the record - I did a clean install of Lubuntu 10.10 and it boots into its desktop normally, so that might be a way forward for me.

Incidentally, I then installed ubuntu-desktop into Lubuntu, and when starting into the then available Ubuntu session, the same missing panels occurs.

---

### Post by NightwishFan on 2010-11-08
Try using Xubuntu on the machines. I highly recommend it.

---

### Post by candtalan on 2010-11-08
> **NightwishFan said:**
> Try using Xubuntu on the machines. I highly recommend it.

I have just tried Xubuntu  and it works ok too. I think I will stay with Xubuntu because it has the familiar two panels, and the default browser is Firefox, which I need. (Although I was impressed by Lubuntu. I did not make measurements but it seemed a bit faster)

Thanks again.

---

### Post by candtalan on 2010-11-15
I have just been asked by a newcomer to linux  about what seems to be this same problem. A Shuttle PC was being used, and Ubuntu 10.10, and everything installed ok. However, after restart and then login, after login was completed the system almost immediately went back to login again, sounds like the x crash.

Another strange thing, maybe off topic, is that the person also complained that the Live CD was not useful because a password was always asked  before the session came up!

I have experienced this myself, I guess with my older machines here and ubuntu 10.10

---

