---
title: "X restarts spontaneously"
date: 2012-02-01
forum: General Help
---

### Post by lordjj on 2012-02-01
Hello. I'm using Ubuntu 11.04 with gnome 2. My graphics card is:
```
VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
```
I've had X restart and close my session spontaneously a few times now. Last time it happened I was trying to open a directory with Gnome Mplayer (but previous times it just happened spontaneously without me even doing anything).
Here's what I have in /var/log/Xorg.0.log:
```
[ 19709.681] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[ 19709.682] X Protocol Version 11, Revision 0
[ 19709.682] Build Operating System: Linux 2.6.24-28-server i686 Ubuntu
[ 19709.682] Current Operating System: Linux probook 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686
[ 19709.682] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=846c2273-e3f1-4e5d-b501-6ea7513a99b1 ro vga=792
[ 19709.682] Build Date: 13 October 2011  05:38:22PM
[ 19709.682] xorg-server 2:1.10.1-1ubuntu1.3 (For technical support please see http://www.ubuntu.com/support) 
[ 19709.682] Current version of pixman: 0.20.2
[ 19709.682] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[ 19709.682] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[ 19709.682] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Feb  1 22:24:32 2012
[ 19709.682] (==) Using config file: "/etc/X11/xorg.conf"
[ 19709.682] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[ 19709.811] (==) ServerLayout "X.org Configured"
[ 19709.811] (**) |-->Screen "Screen0" (0)
[ 19709.811] (**) |   |-->Monitor "Monitor0"
[ 19709.811] (**) |   |-->Device "Card0"
[ 19709.811] (**) |-->Screen "Screen1" (1)
[ 19709.811] (**) |   |-->Monitor "Monitor1"
[ 19709.811] (**) |   |-->Device "Card1"
[ 19709.811] (**) |-->Screen "Screen2" (2)
[ 19709.811] (**) |   |-->Monitor "Monitor2"
[ 19709.812] (**) |   |-->Device "Card2"
[ 19709.812] (**) |-->Input Device "Mouse0"
[ 19709.812] (**) |-->Input Device "Keyboard0"
[ 19709.812] (==) Automatically adding devices
[ 19709.812] (==) Automatically enabling devices
[ 19709.812] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[ 19709.812] 	Entry deleted from font path.
[ 19709.812] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[ 19709.812] 	Entry deleted from font path.
[ 19709.812] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[ 19709.812] 	Entry deleted from font path.
[ 19709.812] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[ 19709.812] 	Entry deleted from font path.
[ 19709.812] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[ 19709.812] 	Entry deleted from font path.
[ 19709.812] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[ 19709.812] 	Entry deleted from font path.
[ 19709.813] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[ 19709.813] 	Entry deleted from font path.
[ 19709.813] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[ 19709.813] 	Entry deleted from font path.
[ 19709.813] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[ 19709.813] 	Entry deleted from font path.
[ 19709.813] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[ 19709.813] 	Entry deleted from font path.
[ 19709.813] (**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[ 19709.813] (**) ModulePath set to "/usr/lib/xorg/modules"
[ 19709.813] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[ 19709.813] (WW) Disabling Mouse0
[ 19709.813] (WW) Disabling Keyboard0
[ 19709.813] (II) Loader magic: 0x8200ac0
[ 19709.813] (II) Module ABI versions:
[ 19709.813] 	X.Org ANSI C Emulation: 0.4
[ 19709.813] 	X.Org Video Driver: 10.0
[ 19709.813] 	X.Org XInput driver : 12.3
[ 19709.813] 	X.Org Server Extension : 5.0
[ 19709.814] (--) PCI:*(0:0:2:0) 8086:2a42:103c:3072 rev 7, Mem @ 0x90000000/4194304, 0x80000000/268435456, I/O @ 0x00007120/8
[ 19709.814] (--) PCI: (0:0:2:1) 8086:2a43:103c:3072 rev 7, Mem @ 0x90400000/1048576
[ 19709.814] (II) Open ACPI successful (/var/run/acpid.socket)
[ 19709.814] (II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
[ 19709.814] (II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
[ 19709.814] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[ 19709.814] (II) "record" will be loaded. This was enabled by default and also specified in the config file.
[ 19709.814] (II) "dri" will be loaded. This was enabled by default and also specified in the config file.
[ 19709.814] (II) "dri2" will be loaded. This was enabled by default and also specified in the config file.
[ 19709.814] (II) LoadModule: "dri2"
[ 19709.815] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[ 19709.872] (II) Module dri2: vendor="X.Org Foundation"
[ 19709.872] 	compiled for 1.10.1, module version = 1.2.0
[ 19709.872] 	ABI class: X.Org Server Extension, version 5.0
[ 19709.872] (II) Loading extension DRI2
[ 19709.872] (II) LoadModule: "record"
[ 19709.872] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[ 19709.882] (II) Module record: vendor="X.Org Foundation"
[ 19709.882] 	compiled for 1.10.1, module version = 1.13.0
[ 19709.882] 	Module class: X.Org Server Extension
[ 19709.882] 	ABI class: X.Org Server Extension, version 5.0
[ 19709.882] (II) Loading extension RECORD
[ 19709.882] (II) LoadModule: "glx"
[ 19709.882] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[ 19709.895] (II) Module glx: vendor="X.Org Foundation"
[ 19709.895] 	compiled for 1.10.1, module version = 1.0.0
[ 19709.895] 	ABI class: X.Org Server Extension, version 5.0
[ 19709.895] (==) AIGLX enabled
[ 19709.895] (II) Loading extension GLX
[ 19709.896] (II) LoadModule: "dri"
[ 19709.896] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[ 19709.902] (II) Module dri: vendor="X.Org Foundation"
[ 19709.902] 	compiled for 1.10.1, module version = 1.0.0
[ 19709.902] 	ABI class: X.Org Server Extension, version 5.0
[ 19709.902] (II) Loading extension XFree86-DRI
[ 19709.902] (II) LoadModule: "dbe"
[ 19709.902] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[ 19709.902] (II) Module dbe: vendor="X.Org Foundation"
[ 19709.902] 	compiled for 1.10.1, module version = 1.0.0
[ 19709.902] 	Module class: X.Org Server Extension
[ 19709.902] 	ABI class: X.Org Server Extension, version 5.0
[ 19709.902] (II) Loading extension DOUBLE-BUFFER
[ 19709.902] (II) LoadModule: "extmod"
[ 19709.903] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[ 19709.907] (II) Module extmod: vendor="X.Org Foundation"
[ 19709.907] 	compiled for 1.10.1, module version = 1.0.0
[ 19709.908] 	Module class: X.Org Server Extension
[ 19709.908] 	ABI class: X.Org Server Extension, version 5.0
[ 19709.908] (II) Loading extension MIT-SCREEN-SAVER
[ 19709.908] (II) Loading extension XFree86-VidModeExtension
[ 19709.908] (II) Loading extension XFree86-DGA
[ 19709.908] (II) Loading extension DPMS
[ 19709.908] (II) Loading extension XVideo
[ 19709.908] (II) Loading extension XVideo-MotionCompensation
[ 19709.908] (II) Loading extension X-Resource
[ 19709.908] (II) LoadModule: "intel"
[ 19709.908] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[ 19709.940] (II) Module intel: vendor="X.Org Foundation"
[ 19709.940] 	compiled for 1.10.1, module version = 2.14.0
[ 19709.940] 	Module class: X.Org Video Driver
[ 19709.940] 	ABI class: X.Org Video Driver, version 10.0
[ 19709.940] (II) LoadModule: "fbdev"
[ 19709.940] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[ 19709.960] (II) Module fbdev: vendor="X.Org Foundation"
[ 19709.960] 	compiled for 1.10.0, module version = 0.4.2
[ 19709.960] 	ABI class: X.Org Video Driver, version 10.0
[ 19709.960] (II) LoadModule: "vesa"
[ 19709.960] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[ 19709.968] (II) Module vesa: vendor="X.Org Foundation"
[ 19709.968] 	compiled for 1.10.0, module version = 2.3.0
[ 19709.968] 	Module class: X.Org Video Driver
[ 19709.968] 	ABI class: X.Org Video Driver, version 10.0
[ 19709.968] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
	Sandybridge, Sandybridge
[ 19709.969] (II) FBDEV: driver for framebuffer: fbdev
[ 19709.969] (II) VESA: driver for VESA chipsets: vesa
[ 19709.969] (--) using VT number 8

[ 19710.047] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[ 19710.047] (WW) Falling back to old probe method for fbdev
[ 19710.047] (II) Loading sub module "fbdevhw"
[ 19710.047] (II) LoadModule: "fbdevhw"
[ 19710.048] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[ 19710.057] (II) Module fbdevhw: vendor="X.Org Foundation"
[ 19710.057] 	compiled for 1.10.1, module version = 0.0.2
[ 19710.057] 	ABI class: X.Org Video Driver, version 10.0
[ 19710.057] (WW) Falling back to old probe method for vesa
[ 19710.057] drmOpenDevice: node name is /dev/dri/card0
[ 19710.057] drmOpenDevice: open result is 9, (OK)
[ 19710.057] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[ 19710.058] drmOpenDevice: node name is /dev/dri/card0
[ 19710.058] drmOpenDevice: open result is 9, (OK)
[ 19710.058] drmOpenByBusid: drmOpenMinor returns 9
[ 19710.058] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[ 19710.058] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[ 19710.058] (==) intel(0): RGB weight 888
[ 19710.058] (==) intel(0): Default visual is TrueColor
[ 19710.058] (II) intel(0): Integrated Graphics Chipset: Intel(R) GM45
[ 19710.058] (--) intel(0): Chipset: "GM45"
[ 19710.058] (**) intel(0): Relaxed fencing enabled
[ 19710.058] (**) intel(0): Tiling enabled
[ 19710.058] (**) intel(0): SwapBuffers wait enabled
[ 19710.058] (==) intel(0): video overlay key set to 0x101fe
[ 19710.058] (II) intel(0): Output LVDS1 using monitor section Monitor0
[ 19710.058] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
[ 19710.080] (II) intel(0): Output VGA1 has no monitor section
[ 19710.084] (II) intel(0): Output HDMI1 has no monitor section
[ 19710.084] (II) intel(0): Output DP1 has no monitor section
[ 19710.085] (II) intel(0): Output DP2 has no monitor section
[ 19710.312] (II) intel(0): Output TV1 has no monitor section
[ 19710.312] (II) intel(0): EDID for output LVDS1
[ 19710.312] (II) intel(0): Manufacturer: CMO  Model: 1571  Serial#: 0
[ 19710.312] (II) intel(0): Year: 2008  Week: 36
[ 19710.312] (II) intel(0): EDID Version: 1.3
[ 19710.312] (II) intel(0): Digital Display Input
[ 19710.312] (II) intel(0): Max Image Size [cm]: horiz.: 35  vert.: 19
[ 19710.312] (II) intel(0): Gamma: 2.20
[ 19710.312] (II) intel(0): No DPMS capabilities specified
[ 19710.312] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[ 19710.312] (II) intel(0): First detailed timing is preferred mode
[ 19710.312] (II) intel(0): redX: 0.602 redY: 0.340   greenX: 0.306 greenY: 0.530
[ 19710.312] (II) intel(0): blueX: 0.151 blueY: 0.120   whiteX: 0.313 whiteY: 0.329
[ 19710.312] (II) intel(0): Manufacturer's mask: 0
[ 19710.312] (II) intel(0): Supported detailed timing:
[ 19710.312] (II) intel(0): clock: 69.3 MHz   Image Size:  344 x 193 mm
[ 19710.313] (II) intel(0): h_active: 1366  h_sync: 1382  h_sync_end 1416 h_blank_end 1466 h_border: 0
[ 19710.313] (II) intel(0): v_active: 768  v_sync: 770  v_sync_end 776 v_blanking: 788 v_border: 0
[ 19710.313] (II) intel(0):  N156B6-L04
[ 19710.313] (II) intel(0):  CMO
[ 19710.313] (II) intel(0):  N156B6-L04
[ 19710.313] (II) intel(0): EDID (in hex):
[ 19710.313] (II) intel(0): 	00ffffffffffff000daf711500000000
[ 19710.313] (II) intel(0): 	24120103802313780a07f59a574e8726
[ 19710.313] (II) intel(0): 	1e505400000001010101010101010101
[ 19710.313] (II) intel(0): 	010101010101121b5664500014301022
[ 19710.313] (II) intel(0): 	260058c110000018000000fe004e3135
[ 19710.313] (II) intel(0): 	3642362d4c30340a2020000000fe0043
[ 19710.313] (II) intel(0): 	4d4f0a202020202020202020000000fe
[ 19710.313] (II) intel(0): 	004e31353642362d4c30340a2020006f
[ 19710.313] (II) intel(0): EDID vendor "CMO", prod id 5489
[ 19710.313] (II) intel(0): Printing DDC gathered Modelines:
[ 19710.313] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1382 1416 1466  768 770 776 788 -hsync -vsync (47.3 kHz)
[ 19710.313] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[ 19710.313] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[ 19710.313] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[ 19710.313] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[ 19710.313] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[ 19710.313] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[ 19710.313] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[ 19710.314] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[ 19710.314] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[ 19710.314] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[ 19710.314] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[ 19710.314] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[ 19710.314] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[ 19710.314] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[ 19710.314] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[ 19710.314] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[ 19710.314] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[ 19710.314] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[ 19710.314] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[ 19710.314] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[ 19710.314] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[ 19710.314] (II) intel(0): Printing probed modes for output LVDS1
[ 19710.314] (II) intel(0): Modeline "1366x768"x60.0   69.30  1366 1382 1416 1466  768 770 776 788 -hsync -vsync (47.3 kHz)
[ 19710.314] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[ 19710.314] (II) intel(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz)
[ 19710.314] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[ 19710.314] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[ 19710.314] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[ 19710.314] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[ 19710.336] (II) intel(0): EDID for output VGA1
[ 19710.340] (II) intel(0): EDID for output HDMI1
[ 19710.340] (II) intel(0): EDID for output DP1
[ 19710.341] (II) intel(0): EDID for output DP2
[ 19710.488] (II) intel(0): EDID for output TV1
[ 19710.488] (II) intel(0): Output LVDS1 connected
[ 19710.488] (II) intel(0): Output VGA1 disconnected
[ 19710.488] (II) intel(0): Output HDMI1 disconnected
[ 19710.488] (II) intel(0): Output DP1 disconnected
[ 19710.488] (II) intel(0): Output DP2 disconnected
[ 19710.488] (II) intel(0): Output TV1 disconnected
[ 19710.488] (II) intel(0): Using exact sizes for initial modes
[ 19710.488] (II) intel(0): Output LVDS1 using initial mode 1366x768
[ 19710.488] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[ 19710.488] (II) intel(0): Kernel page flipping support detected, enabling
[ 19710.488] (**) intel(0): Display dimensions: (350, 190) mm
[ 19710.488] (**) intel(0): DPI set to (99, 102)
[ 19710.488] (II) Loading sub module "fb"
[ 19710.488] (II) LoadModule: "fb"
[ 19710.488] (II) Loading /usr/lib/xorg/modules/libfb.so
[ 19710.602] (II) Module fb: vendor="X.Org Foundation"
[ 19710.602] 	compiled for 1.10.1, module version = 1.0.0
[ 19710.602] 	ABI class: X.Org ANSI C Emulation, version 0.4
[ 19710.602] (II) UnloadModule: "fbdev"
[ 19710.602] (II) Unloading fbdev
[ 19710.602] (II) UnloadModule: "fbdevhw"
[ 19710.602] (II) Unloading fbdevhw
[ 19710.602] (II) UnloadModule: "vesa"
[ 19710.602] (II) Unloading vesa
[ 19710.602] (==) Depth 24 pixmap format is 32 bpp
[ 19710.602] (==) intel(0): VideoRam: 262144 KB
[ 19710.602] (II) intel(0): [DRI2] Setup complete
[ 19710.602] (II) intel(0): [DRI2]   DRI driver: i965
[ 19710.602] (II) intel(0): Allocated new frame buffer 1408x768 stride 5632, tiled
[ 19710.617] (II) UXA(0): Driver registered support for the following operations:
[ 19710.617] (II)         solid
[ 19710.617] (II)         copy
[ 19710.617] (II)         composite (RENDER acceleration)
[ 19710.617] (II)         put_image
[ 19710.617] (II)         get_image
[ 19710.617] (==) intel(0): Backing store disabled
[ 19710.617] (==) intel(0): Silken mouse enabled
[ 19710.617] (II) intel(0): Initializing HW Cursor
[ 19710.644] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[ 19710.645] (==) intel(0): DPMS enabled
[ 19710.645] (==) intel(0): Intel XvMC decoder enabled
[ 19710.645] (II) intel(0): Set up textured video
[ 19710.645] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[ 19710.645] (II) intel(0): direct rendering: DRI2 Enabled
[ 19710.645] (WW) intel(0): Option "ForceEnablePipeA" is not used
[ 19710.645] (WW) intel(0): Option "monitor-TV" is not used
[ 19710.645] (==) intel(0): hotplug detection: "enabled"
[ 19710.645] (--) RandR disabled
[ 19710.645] (II) Initializing built-in extension Generic Event Extension
[ 19710.645] (II) Initializing built-in extension SHAPE
[ 19710.645] (II) Initializing built-in extension MIT-SHM
[ 19710.645] (II) Initializing built-in extension XInputExtension
[ 19710.645] (II) Initializing built-in extension XTEST
[ 19710.645] (II) Initializing built-in extension BIG-REQUESTS
[ 19710.645] (II) Initializing built-in extension SYNC
[ 19710.645] (II) Initializing built-in extension XKEYBOARD
[ 19710.645] (II) Initializing built-in extension XC-MISC
[ 19710.645] (II) Initializing built-in extension SECURITY
[ 19710.645] (II) Initializing built-in extension XINERAMA
[ 19710.645] (II) Initializing built-in extension XFIXES
[ 19710.645] (II) Initializing built-in extension RENDER
[ 19710.645] (II) Initializing built-in extension RANDR
[ 19710.645] (II) Initializing built-in extension COMPOSITE
[ 19710.645] (II) Initializing built-in extension DAMAGE
[ 19710.645] (II) Initializing built-in extension GESTURE
[ 19710.662] (II) AIGLX: Trying DRI driver /usr/lib/dri/i965_dri.so
[ 19710.692] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[ 19710.692] (II) AIGLX: enabled GLX_INTEL_swap_event
[ 19710.692] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[ 19710.692] (II) AIGLX: enabled GLX_SGI_make_current_read
[ 19710.692] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[ 19710.692] (II) AIGLX: Loaded and initialized i965
[ 19710.692] (II) GLX: Initialized DRI2 GL provider for screen 0
[ 19710.693] (II) intel(0): Setting screen physical size to 361 x 203
[ 19710.771] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[ 19710.802] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[ 19710.802] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[ 19710.802] (II) LoadModule: "evdev"
[ 19710.803] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 19710.851] (II) Module evdev: vendor="X.Org Foundation"
[ 19710.851] 	compiled for 1.10.0.902, module version = 2.6.0
[ 19710.851] 	Module class: X.Org XInput Driver
[ 19710.851] 	ABI class: X.Org XInput driver, version 12.3
[ 19710.851] (II) Using input driver 'evdev' for 'Power Button'
[ 19710.851] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 19710.851] (**) Power Button: always reports core events
[ 19710.851] (**) Power Button: Device: "/dev/input/event2"
[ 19710.851] (--) Power Button: Found keys
[ 19710.851] (II) Power Button: Configuring as keyboard
[ 19710.851] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[ 19710.851] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[ 19710.851] (**) Option "xkb_rules" "evdev"
[ 19710.851] (**) Option "xkb_model" "pc105"
[ 19710.851] (**) Option "xkb_layout" "us"
[ 19710.853] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[ 19710.853] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[ 19710.853] (II) Using input driver 'evdev' for 'Video Bus'
[ 19710.853] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 19710.853] (**) Video Bus: always reports core events
[ 19710.853] (**) Video Bus: Device: "/dev/input/event5"
[ 19710.856] (--) Video Bus: Found keys
[ 19710.856] (II) Video Bus: Configuring as keyboard
[ 19710.856] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input5/event5"
[ 19710.856] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[ 19710.856] (**) Option "xkb_rules" "evdev"
[ 19710.856] (**) Option "xkb_model" "pc105"
[ 19710.856] (**) Option "xkb_layout" "us"
[ 19710.865] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[ 19710.865] (II) No input driver/identifier specified (ignoring)
[ 19710.865] (II) config/udev: Adding input device Sleep Button (/dev/input/event0)
[ 19710.865] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[ 19710.865] (II) Using input driver 'evdev' for 'Sleep Button'
[ 19710.865] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 19710.865] (**) Sleep Button: always reports core events
[ 19710.865] (**) Sleep Button: Device: "/dev/input/event0"
[ 19710.865] (--) Sleep Button: Found keys
[ 19710.865] (II) Sleep Button: Configuring as keyboard
[ 19710.865] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input0/event0"
[ 19710.866] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[ 19710.866] (**) Option "xkb_rules" "evdev"
[ 19710.866] (**) Option "xkb_model" "pc105"
[ 19710.866] (**) Option "xkb_layout" "us"
[ 19710.872] (II) config/udev: Adding input device USB LaserStream(TM) Mouse (/dev/input/event4)
[ 19710.872] (**) USB LaserStream(TM) Mouse: Applying InputClass "evdev pointer catchall"
[ 19710.872] (II) Using input driver 'evdev' for 'USB LaserStream(TM) Mouse'
[ 19710.872] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 19710.872] (**) USB LaserStream(TM) Mouse: always reports core events
[ 19710.872] (**) USB LaserStream(TM) Mouse: Device: "/dev/input/event4"
[ 19710.873] (--) USB LaserStream(TM) Mouse: Found 9 mouse buttons
[ 19710.873] (--) USB LaserStream(TM) Mouse: Found scroll wheel(s)
[ 19710.873] (--) USB LaserStream(TM) Mouse: Found relative axes
[ 19710.873] (--) USB LaserStream(TM) Mouse: Found x and y relative axes
[ 19710.873] (II) USB LaserStream(TM) Mouse: Configuring as mouse
[ 19710.873] (II) USB LaserStream(TM) Mouse: Adding scrollwheel support
[ 19710.873] (**) USB LaserStream(TM) Mouse: YAxisMapping: buttons 4 and 5
[ 19710.873] (**) USB LaserStream(TM) Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[ 19710.873] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1:1.0/input/input9/event4"
[ 19710.873] (II) XINPUT: Adding extended input device "USB LaserStream(TM) Mouse" (type: MOUSE)
[ 19710.873] (II) USB LaserStream(TM) Mouse: initialized for relative axes.
[ 19710.873] (**) USB LaserStream(TM) Mouse: (accel) keeping acceleration scheme 1
[ 19710.873] (**) USB LaserStream(TM) Mouse: (accel) acceleration profile 0
[ 19710.873] (**) USB LaserStream(TM) Mouse: (accel) acceleration factor: 2.000
[ 19710.873] (**) USB LaserStream(TM) Mouse: (accel) acceleration threshold: 4
[ 19710.873] (II) config/udev: Adding input device USB LaserStream(TM) Mouse (/dev/input/mouse0)
[ 19710.873] (II) No input driver/identifier specified (ignoring)
[ 19710.890] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[ 19710.890] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[ 19710.891] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[ 19710.891] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 19710.891] (**) AT Translated Set 2 keyboard: always reports core events
[ 19710.891] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[ 19710.892] (--) AT Translated Set 2 keyboard: Found keys
[ 19710.892] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[ 19710.892] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[ 19710.892] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[ 19710.892] (**) Option "xkb_rules" "evdev"
[ 19710.892] (**) Option "xkb_model" "pc105"
[ 19710.892] (**) Option "xkb_layout" "us"
[ 19710.893] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event8)
[ 19710.893] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[ 19710.893] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[ 19710.893] (II) LoadModule: "synaptics"
[ 19710.893] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[ 19710.905] (II) Module synaptics: vendor="X.Org Foundation"
[ 19710.905] 	compiled for 1.10.1, module version = 1.3.99
[ 19710.905] 	Module class: X.Org XInput Driver
[ 19710.905] 	ABI class: X.Org XInput driver, version 12.3
[ 19710.905] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[ 19710.905] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[ 19710.905] (**) SynPS/2 Synaptics TouchPad: always reports core events
[ 19710.905] (**) Option "Device" "/dev/input/event8"
[ 19710.912] (--) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5692
[ 19710.912] (--) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4680
[ 19710.912] (--) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[ 19710.912] (--) SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[ 19710.912] (--) SynPS/2 Synaptics TouchPad: buttons: left right double triple
[ 19710.924] (--) SynPS/2 Synaptics TouchPad: touchpad found
[ 19710.924] (**) SynPS/2 Synaptics TouchPad: always reports core events
[ 19710.928] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio4/input/input8/event8"
[ 19710.928] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[ 19710.928] (**) SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[ 19710.928] (**) SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[ 19710.928] (**) SynPS/2 Synaptics TouchPad: AccelFactor is now 0.037
[ 19710.928] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[ 19710.928] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[ 19710.928] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[ 19710.928] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[ 19710.937] (--) SynPS/2 Synaptics TouchPad: touchpad found
[ 19710.938] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[ 19710.938] (II) No input driver/identifier specified (ignoring)
[ 19710.938] (II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/event6)
[ 19710.939] (II) No input driver/identifier specified (ignoring)
[ 19710.939] (II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/js0)
[ 19710.939] (II) No input driver/identifier specified (ignoring)
[ 19710.950] (II) config/udev: Adding input device HP WMI hotkeys (/dev/input/event7)
[ 19710.950] (**) HP WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[ 19710.950] (II) Using input driver 'evdev' for 'HP WMI hotkeys'
[ 19710.950] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 19710.950] (**) HP WMI hotkeys: always reports core events
[ 19710.950] (**) HP WMI hotkeys: Device: "/dev/input/event7"
[ 19710.950] (--) HP WMI hotkeys: Found keys
[ 19710.950] (II) HP WMI hotkeys: Configuring as keyboard
[ 19710.950] (**) Option "config_info" "udev:/sys/devices/virtual/input/input7/event7"
[ 19710.950] (II) XINPUT: Adding extended input device "HP WMI hotkeys" (type: KEYBOARD)
[ 19710.950] (**) Option "xkb_rules" "evdev"
[ 19710.950] (**) Option "xkb_model" "pc105"
[ 19710.950] (**) Option "xkb_layout" "us"
[ 19711.684] (II) intel(0): EDID vendor "CMO", prod id 5489
[ 19711.684] (II) intel(0): Printing DDC gathered Modelines:
[ 19711.684] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1382 1416 1466  768 770 776 788 -hsync -vsync (47.3 kHz)
[ 19711.871] (II) intel(0): EDID vendor "CMO", prod id 5489
[ 19711.871] (II) intel(0): Printing DDC gathered Modelines:
[ 19711.871] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1382 1416 1466  768 770 776 788 -hsync -vsync (47.3 kHz)
[ 19712.051] (II) intel(0): EDID vendor "CMO", prod id 5489
[ 19712.051] (II) intel(0): Printing DDC gathered Modelines:
[ 19712.051] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1382 1416 1466  768 770 776 788 -hsync -vsync (47.3 kHz)
[ 19712.230] (II) intel(0): EDID vendor "CMO", prod id 5489
[ 19712.230] (II) intel(0): Printing DDC gathered Modelines:
[ 19712.230] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1382 1416 1466  768 770 776 788 -hsync -vsync (47.3 kHz)
[ 19721.120] (II) AIGLX: Suspending AIGLX clients for VT switch
[ 19722.261] (II) Open ACPI successful (/var/run/acpid.socket)
[ 19722.262] (II) AIGLX: Resuming AIGLX clients after VT switch
[ 19722.280] (II) intel(0): EDID vendor "CMO", prod id 5489
[ 19722.280] (II) intel(0): Printing DDC gathered Modelines:
[ 19722.280] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1382 1416 1466  768 770 776 788 -hsync -vsync (47.3 kHz)
[ 19722.484] (--) SynPS/2 Synaptics TouchPad: touchpad found
[ 19731.333] (II) intel(0): EDID vendor "CMO", prod id 5489
[ 19731.334] (II) intel(0): Printing DDC gathered Modelines:
[ 19731.334] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1382 1416 1466  768 770 776 788 -hsync -vsync (47.3 kHz)
[ 19731.595] (II) intel(0): EDID vendor "CMO", prod id 5489
[ 19731.595] (II) intel(0): Printing DDC gathered Modelines:
[ 19731.595] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1382 1416 1466  768 770 776 788 -hsync -vsync (47.3 kHz)
[ 19731.850] (II) intel(0): EDID vendor "CMO", prod id 5489
[ 19731.850] (II) intel(0): Printing DDC gathered Modelines:
[ 19731.850] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1382 1416 1466  768 770 776 788 -hsync -vsync (47.3 kHz)
[ 19731.981] (II) intel(0): EDID vendor "CMO", prod id 5489
[ 19731.981] (II) intel(0): Printing DDC gathered Modelines:
[ 19731.981] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1382 1416 1466  768 770 776 788 -hsync -vsync (47.3 kHz)
[ 19741.595] (II) intel(0): EDID vendor "CMO", prod id 5489
[ 19741.595] (II) intel(0): Printing DDC gathered Modelines:
[ 19741.595] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1382 1416 1466  768 770 776 788 -hsync -vsync (47.3 kHz)
[ 19741.781] (II) intel(0): EDID vendor "CMO", prod id 5489
[ 19741.781] (II) intel(0): Printing DDC gathered Modelines:
[ 19741.781] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1382 1416 1466  768 770 776 788 -hsync -vsync (47.3 kHz)
[ 19945.168] (II) AIGLX: Suspending AIGLX clients for VT switch
[ 19960.775] (II) Open ACPI successful (/var/run/acpid.socket)
[ 19960.775] (II) AIGLX: Resuming AIGLX clients after VT switch
[ 19960.792] (II) intel(0): EDID vendor "CMO", prod id 5489
[ 19960.792] (II) intel(0): Printing DDC gathered Modelines:
[ 19960.792] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1382 1416 1466  768 770 776 788 -hsync -vsync (47.3 kHz)
[ 19961.001] (--) SynPS/2 Synaptics TouchPad: touchpad found
```

And /var/log/Xorg.1.log:
```
[  4446.683] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[  4446.683] X Protocol Version 11, Revision 0
[  4446.683] Build Operating System: Linux 2.6.24-28-server i686 Ubuntu
[  4446.683] Current Operating System: Linux probook 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686
[  4446.683] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=846c2273-e3f1-4e5d-b501-6ea7513a99b1 ro vga=792 splash quiet splash vt.handoff=7
[  4446.683] Build Date: 13 October 2011  05:38:22PM
[  4446.683] xorg-server 2:1.10.1-1ubuntu1.3 (For technical support please see http://www.ubuntu.com/support) 
[  4446.683] Current version of pixman: 0.20.2
[  4446.683] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[  4446.683] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  4446.683] (==) Log file: "/var/log/Xorg.1.log", Time: Wed Nov 16 11:14:21 2011
[  4446.683] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  4446.684] (==) No Layout section.  Using the first Screen section.
[  4446.684] (==) No screen section available. Using defaults.
[  4446.684] (**) |-->Screen "Default Screen Section" (0)
[  4446.684] (**) |   |-->Monitor "<default monitor>"
[  4446.684] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[  4446.684] (==) Automatically adding devices
[  4446.684] (==) Automatically enabling devices
[  4446.684] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  4446.684] 	Entry deleted from font path.
[  4446.684] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[  4446.684] 	Entry deleted from font path.
[  4446.684] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[  4446.684] 	Entry deleted from font path.
[  4446.684] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[  4446.684] 	Entry deleted from font path.
[  4446.684] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[  4446.684] 	Entry deleted from font path.
[  4446.685] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[  4446.685] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  4446.685] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[  4446.685] (II) Loader magic: 0x8200ac0
[  4446.685] (II) Module ABI versions:
[  4446.685] 	X.Org ANSI C Emulation: 0.4
[  4446.685] 	X.Org Video Driver: 10.0
[  4446.685] 	X.Org XInput driver : 12.3
[  4446.685] 	X.Org Server Extension : 5.0
[  4446.686] (--) PCI:*(0:0:2:0) 8086:2a42:103c:3072 rev 7, Mem @ 0x90000000/4194304, 0x80000000/268435456, I/O @ 0x00007120/8
[  4446.686] (--) PCI: (0:0:2:1) 8086:2a43:103c:3072 rev 7, Mem @ 0x90400000/1048576
[  4446.686] (II) Open ACPI successful (/var/run/acpid.socket)
[  4446.686] (II) LoadModule: "extmod"
[  4446.686] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[  4446.686] (II) Module extmod: vendor="X.Org Foundation"
[  4446.686] 	compiled for 1.10.1, module version = 1.0.0
[  4446.686] 	Module class: X.Org Server Extension
[  4446.686] 	ABI class: X.Org Server Extension, version 5.0
[  4446.686] (II) Loading extension MIT-SCREEN-SAVER
[  4446.686] (II) Loading extension XFree86-VidModeExtension
[  4446.687] (II) Loading extension XFree86-DGA
[  4446.687] (II) Loading extension DPMS
[  4446.687] (II) Loading extension XVideo
[  4446.687] (II) Loading extension XVideo-MotionCompensation
[  4446.687] (II) Loading extension X-Resource
[  4446.687] (II) LoadModule: "dbe"
[  4446.687] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[  4446.687] (II) Module dbe: vendor="X.Org Foundation"
[  4446.687] 	compiled for 1.10.1, module version = 1.0.0
[  4446.687] 	Module class: X.Org Server Extension
[  4446.687] 	ABI class: X.Org Server Extension, version 5.0
[  4446.687] (II) Loading extension DOUBLE-BUFFER
[  4446.687] (II) LoadModule: "glx"
[  4446.687] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[  4446.687] (II) Module glx: vendor="X.Org Foundation"
[  4446.687] 	compiled for 1.10.1, module version = 1.0.0
[  4446.687] 	ABI class: X.Org Server Extension, version 5.0
[  4446.687] (==) AIGLX enabled
[  4446.687] (II) Loading extension GLX
[  4446.687] (II) LoadModule: "record"
[  4446.687] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[  4446.687] (II) Module record: vendor="X.Org Foundation"
[  4446.687] 	compiled for 1.10.1, module version = 1.13.0
[  4446.688] 	Module class: X.Org Server Extension
[  4446.688] 	ABI class: X.Org Server Extension, version 5.0
[  4446.688] (II) Loading extension RECORD
[  4446.688] (II) LoadModule: "dri"
[  4446.688] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[  4446.688] (II) Module dri: vendor="X.Org Foundation"
[  4446.688] 	compiled for 1.10.1, module version = 1.0.0
[  4446.688] 	ABI class: X.Org Server Extension, version 5.0
[  4446.688] (II) Loading extension XFree86-DRI
[  4446.688] (II) LoadModule: "dri2"
[  4446.688] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[  4446.688] (II) Module dri2: vendor="X.Org Foundation"
[  4446.688] 	compiled for 1.10.1, module version = 1.2.0
[  4446.688] 	ABI class: X.Org Server Extension, version 5.0
[  4446.688] (II) Loading extension DRI2
[  4446.688] (==) Matched intel as autoconfigured driver 0
[  4446.688] (==) Matched vesa as autoconfigured driver 1
[  4446.688] (==) Matched fbdev as autoconfigured driver 2
[  4446.688] (==) Assigned the driver to the xf86ConfigLayout
[  4446.688] (II) LoadModule: "intel"
[  4446.689] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[  4446.689] (II) Module intel: vendor="X.Org Foundation"
[  4446.689] 	compiled for 1.10.1, module version = 2.14.0
[  4446.689] 	Module class: X.Org Video Driver
[  4446.689] 	ABI class: X.Org Video Driver, version 10.0
[  4446.689] (II) LoadModule: "vesa"
[  4446.689] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  4446.690] (II) Module vesa: vendor="X.Org Foundation"
[  4446.690] 	compiled for 1.10.0, module version = 2.3.0
[  4446.690] 	Module class: X.Org Video Driver
[  4446.690] 	ABI class: X.Org Video Driver, version 10.0
[  4446.690] (II) LoadModule: "fbdev"
[  4446.690] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  4446.690] (II) Module fbdev: vendor="X.Org Foundation"
[  4446.690] 	compiled for 1.10.0, module version = 0.4.2
[  4446.690] 	ABI class: X.Org Video Driver, version 10.0
[  4446.690] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
	Sandybridge, Sandybridge
[  4446.691] (II) VESA: driver for VESA chipsets: vesa
[  4446.691] (II) FBDEV: driver for framebuffer: fbdev
[  4446.691] (--) using VT number 8

[  4446.844] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[  4446.844] (WW) Falling back to old probe method for vesa
[  4446.844] (WW) Falling back to old probe method for fbdev
[  4446.844] (II) Loading sub module "fbdevhw"
[  4446.844] (II) LoadModule: "fbdevhw"
[  4446.845] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[  4446.845] (II) Module fbdevhw: vendor="X.Org Foundation"
[  4446.845] 	compiled for 1.10.1, module version = 0.0.2
[  4446.845] 	ABI class: X.Org Video Driver, version 10.0
[  4446.845] drmOpenDevice: node name is /dev/dri/card0
[  4446.845] drmOpenDevice: open result is 9, (OK)
[  4446.845] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[  4446.845] drmOpenDevice: node name is /dev/dri/card0
[  4446.845] drmOpenDevice: open result is 9, (OK)
[  4446.845] drmOpenByBusid: drmOpenMinor returns 9
[  4446.845] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[  4446.845] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[  4446.845] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[  4446.845] (==) intel(0): RGB weight 888
[  4446.845] (==) intel(0): Default visual is TrueColor
[  4446.845] (II) intel(0): Integrated Graphics Chipset: Intel(R) GM45
[  4446.845] (--) intel(0): Chipset: "GM45"
[  4446.845] (**) intel(0): Relaxed fencing enabled
[  4446.845] (**) intel(0): Tiling enabled
[  4446.845] (**) intel(0): SwapBuffers wait enabled
[  4446.845] (==) intel(0): video overlay key set to 0x101fe
[  4446.846] (II) intel(0): Output LVDS1 has no monitor section
[  4446.846] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
[  4446.868] (II) intel(0): Output VGA1 has no monitor section
[  4446.874] (II) intel(0): Output HDMI1 has no monitor section
[  4446.874] (II) intel(0): Output DP1 has no monitor section
[  4446.875] (II) intel(0): Output DP2 has no monitor section
[  4446.992] (II) intel(0): Output TV1 has no monitor section
[  4446.992] (II) intel(0): EDID for output LVDS1
[  4446.992] (II) intel(0): Manufacturer: CMO  Model: 1571  Serial#: 0
[  4446.992] (II) intel(0): Year: 2008  Week: 36
[  4446.992] (II) intel(0): EDID Version: 1.3
[  4446.992] (II) intel(0): Digital Display Input
[  4446.992] (II) intel(0): Max Image Size [cm]: horiz.: 35  vert.: 19
[  4446.992] (II) intel(0): Gamma: 2.20
[  4446.992] (II) intel(0): No DPMS capabilities specified
[  4446.992] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[  4446.992] (II) intel(0): First detailed timing is preferred mode
[  4446.992] (II) intel(0): redX: 0.602 redY: 0.340   greenX: 0.306 greenY: 0.530
[  4446.992] (II) intel(0): blueX: 0.151 blueY: 0.120   whiteX: 0.313 whiteY: 0.329
[  4446.992] (II) intel(0): Manufacturer's mask: 0
[  4446.992] (II) intel(0): Supported detailed timing:
[  4446.992] (II) intel(0): clock: 69.3 MHz   Image Size:  344 x 193 mm
[  4446.992] (II) intel(0): h_active: 1366  h_sync: 1382  h_sync_end 1416 h_blank_end 1466 h_border: 0
[  4446.992] (II) intel(0): v_active: 768  v_sync: 770  v_sync_end 776 v_blanking: 788 v_border: 0
[  4446.992] (II) intel(0):  N156B6-L04
[  4446.992] (II) intel(0):  CMO
[  4446.992] (II) intel(0):  N156B6-L04
[  4446.992] (II) intel(0): EDID (in hex):
[  4446.992] (II) intel(0): 	00ffffffffffff000daf711500000000
[  4446.992] (II) intel(0): 	24120103802313780a07f59a574e8726
[  4446.992] (II) intel(0): 	1e505400000001010101010101010101
[  4446.992] (II) intel(0): 	010101010101121b5664500014301022
[  4446.992] (II) intel(0): 	260058c110000018000000fe004e3135
[  4446.992] (II) intel(0): 	3642362d4c30340a2020000000fe0043
[  4446.992] (II) intel(0): 	4d4f0a202020202020202020000000fe
[  4446.992] (II) intel(0): 	004e31353642362d4c30340a2020006f
[  4446.992] (II) intel(0): EDID vendor "CMO", prod id 5489
[  4446.992] (II) intel(0): Printing DDC gathered Modelines:
[  4446.992] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1382 1416 1466  768 770 776 788 -hsync -vsync (47.3 kHz)
[  4446.993] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[  4446.993] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[  4446.993] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[  4446.993] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[  4446.993] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[  4446.993] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[  4446.993] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[  4446.993] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[  4446.993] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[  4446.993] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[  4446.993] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[  4446.993] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[  4446.993] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[  4446.993] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[  4446.993] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[  4446.993] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[  4446.993] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[  4446.993] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[  4446.993] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[  4446.993] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[  4446.993] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[  4446.993] (II) intel(0): Printing probed modes for output LVDS1
[  4446.993] (II) intel(0): Modeline "1366x768"x60.0   69.30  1366 1382 1416 1466  768 770 776 788 -hsync -vsync (47.3 kHz)
[  4446.993] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[  4446.993] (II) intel(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz)
[  4446.993] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  4446.993] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  4446.993] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[  4446.993] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  4447.016] (II) intel(0): EDID for output VGA1
[  4447.020] (II) intel(0): EDID for output HDMI1
[  4447.020] (II) intel(0): EDID for output DP1
[  4447.021] (II) intel(0): EDID for output DP2
[  4447.164] (II) intel(0): EDID for output TV1
[  4447.164] (II) intel(0): Printing probed modes for output TV1
[  4447.164] (II) intel(0): Modeline "848x480"x30.0   14.51  848 849 912 944  480 481 512 513 (15.4 kHz)
[  4447.164] (II) intel(0): Modeline "640x480"x30.0   11.31  640 641 704 736  480 481 512 513 (15.4 kHz)
[  4447.164] (II) intel(0): Modeline "1024x768"x30.0   26.89  1024 1025 1088 1120  768 769 800 801 (24.0 kHz)
[  4447.164] (II) intel(0): Modeline "800x600"x30.0   17.00  800 801 864 896  600 601 632 633 (19.0 kHz)
[  4447.164] (II) intel(0): Output LVDS1 connected
[  4447.164] (II) intel(0): Output VGA1 disconnected
[  4447.164] (II) intel(0): Output HDMI1 disconnected
[  4447.164] (II) intel(0): Output DP1 disconnected
[  4447.164] (II) intel(0): Output DP2 disconnected
[  4447.164] (II) intel(0): Output TV1 connected
[  4447.164] (II) intel(0): Using fuzzy aspect match for initial modes
[  4447.164] (II) intel(0): Output LVDS1 using initial mode 1024x768
[  4447.164] (II) intel(0): Output TV1 using initial mode 1024x768
[  4447.164] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[  4447.164] (II) intel(0): Kernel page flipping support detected, enabling
[  4447.164] (**) intel(0): Display dimensions: (350, 190) mm
[  4447.165] (**) intel(0): DPI set to (74, 102)
[  4447.165] (II) Loading sub module "fb"
[  4447.165] (II) LoadModule: "fb"
[  4447.165] (II) Loading /usr/lib/xorg/modules/libfb.so
[  4447.165] (II) Module fb: vendor="X.Org Foundation"
[  4447.165] 	compiled for 1.10.1, module version = 1.0.0
[  4447.165] 	ABI class: X.Org ANSI C Emulation, version 0.4
[  4447.165] (II) UnloadModule: "vesa"
[  4447.165] (II) Unloading vesa
[  4447.165] (II) UnloadModule: "fbdev"
[  4447.166] (II) Unloading fbdev
[  4447.166] (II) UnloadModule: "fbdevhw"
[  4447.166] (II) Unloading fbdevhw
[  4447.166] (==) Depth 24 pixmap format is 32 bpp
[  4447.166] (==) intel(0): VideoRam: 262144 KB
[  4447.166] (II) intel(0): [DRI2] Setup complete
[  4447.166] (II) intel(0): [DRI2]   DRI driver: i965
[  4447.166] (II) intel(0): Allocated new frame buffer 1024x768 stride 4096, tiled
[  4447.187] (II) UXA(0): Driver registered support for the following operations:
[  4447.187] (II)         solid
[  4447.187] (II)         copy
[  4447.187] (II)         composite (RENDER acceleration)
[  4447.187] (II)         put_image
[  4447.187] (II)         get_image
[  4447.187] (==) intel(0): Backing store disabled
[  4447.188] (==) intel(0): Silken mouse enabled
[  4447.188] (II) intel(0): Initializing HW Cursor
[  4447.580] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[  4447.581] (==) intel(0): DPMS enabled
[  4447.581] (==) intel(0): Intel XvMC decoder enabled
[  4447.581] (II) intel(0): Set up textured video
[  4447.581] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[  4447.581] (II) intel(0): direct rendering: DRI2 Enabled
[  4447.581] (==) intel(0): hotplug detection: "enabled"
[  4447.581] (--) RandR disabled
[  4447.581] (II) Initializing built-in extension Generic Event Extension
[  4447.581] (II) Initializing built-in extension SHAPE
[  4447.581] (II) Initializing built-in extension MIT-SHM
[  4447.581] (II) Initializing built-in extension XInputExtension
[  4447.581] (II) Initializing built-in extension XTEST
[  4447.581] (II) Initializing built-in extension BIG-REQUESTS
[  4447.581] (II) Initializing built-in extension SYNC
[  4447.581] (II) Initializing built-in extension XKEYBOARD
[  4447.581] (II) Initializing built-in extension XC-MISC
[  4447.581] (II) Initializing built-in extension SECURITY
[  4447.581] (II) Initializing built-in extension XINERAMA
[  4447.581] (II) Initializing built-in extension XFIXES
[  4447.581] (II) Initializing built-in extension RENDER
[  4447.581] (II) Initializing built-in extension RANDR
[  4447.581] (II) Initializing built-in extension COMPOSITE
[  4447.581] (II) Initializing built-in extension DAMAGE
[  4447.581] (II) Initializing built-in extension GESTURE
[  4447.593] (II) AIGLX: Trying DRI driver /usr/lib/dri/i965_dri.so
[  4447.596] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[  4447.596] (II) AIGLX: enabled GLX_INTEL_swap_event
[  4447.596] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[  4447.596] (II) AIGLX: enabled GLX_SGI_make_current_read
[  4447.596] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[  4447.596] (II) AIGLX: Loaded and initialized i965
[  4447.596] (II) GLX: Initialized DRI2 GL provider for screen 0
[  4447.597] (II) intel(0): Setting screen physical size to 270 x 203
[  4447.613] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  4447.628] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[  4447.628] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  4447.628] (II) LoadModule: "evdev"
[  4447.628] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  4447.629] (II) Module evdev: vendor="X.Org Foundation"
[  4447.629] 	compiled for 1.10.0.902, module version = 2.6.0
[  4447.629] 	Module class: X.Org XInput Driver
[  4447.629] 	ABI class: X.Org XInput driver, version 12.3
[  4447.629] (II) Using input driver 'evdev' for 'Power Button'
[  4447.629] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  4447.629] (**) Power Button: always reports core events
[  4447.629] (**) Power Button: Device: "/dev/input/event2"
[  4447.629] (--) Power Button: Found keys
[  4447.629] (II) Power Button: Configuring as keyboard
[  4447.629] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[  4447.629] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[  4447.629] (**) Option "xkb_rules" "evdev"
[  4447.629] (**) Option "xkb_model" "pc105"
[  4447.629] (**) Option "xkb_layout" "us"
[  4447.630] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[  4447.631] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[  4447.631] (II) Using input driver 'evdev' for 'Video Bus'
[  4447.631] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  4447.631] (**) Video Bus: always reports core events
[  4447.631] (**) Video Bus: Device: "/dev/input/event4"
[  4447.636] (--) Video Bus: Found keys
[  4447.636] (II) Video Bus: Configuring as keyboard
[  4447.636] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input4/event4"
[  4447.636] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[  4447.636] (**) Option "xkb_rules" "evdev"
[  4447.636] (**) Option "xkb_model" "pc105"
[  4447.636] (**) Option "xkb_layout" "us"
[  4447.642] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[  4447.642] (II) No input driver/identifier specified (ignoring)
[  4447.643] (II) config/udev: Adding input device Sleep Button (/dev/input/event0)
[  4447.643] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[  4447.643] (II) Using input driver 'evdev' for 'Sleep Button'
[  4447.643] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  4447.643] (**) Sleep Button: always reports core events
[  4447.643] (**) Sleep Button: Device: "/dev/input/event0"
[  4447.643] (--) Sleep Button: Found keys
[  4447.643] (II) Sleep Button: Configuring as keyboard
[  4447.643] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input0/event0"
[  4447.643] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[  4447.643] (**) Option "xkb_rules" "evdev"
[  4447.643] (**) Option "xkb_model" "pc105"
[  4447.643] (**) Option "xkb_layout" "us"
[  4447.648] (II) config/udev: Adding input device HP Webcam [2 MP Fixed] (/dev/input/event6)
[  4447.648] (**) HP Webcam [2 MP Fixed]: Applying InputClass "evdev keyboard catchall"
[  4447.648] (II) Using input driver 'evdev' for 'HP Webcam [2 MP Fixed]'
[  4447.648] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  4447.648] (**) HP Webcam [2 MP Fixed]: always reports core events
[  4447.648] (**) HP Webcam [2 MP Fixed]: Device: "/dev/input/event6"
[  4447.648] (--) HP Webcam [2 MP Fixed]: Found keys
[  4447.648] (II) HP Webcam [2 MP Fixed]: Configuring as keyboard
[  4447.648] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-5/1-5:1.0/input/input6/event6"
[  4447.648] (II) XINPUT: Adding extended input device "HP Webcam [2 MP Fixed]" (type: KEYBOARD)
[  4447.648] (**) Option "xkb_rules" "evdev"
[  4447.648] (**) Option "xkb_model" "pc105"
[  4447.648] (**) Option "xkb_layout" "us"
[  4447.657] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[  4447.657] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[  4447.657] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[  4447.657] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  4447.657] (**) AT Translated Set 2 keyboard: always reports core events
[  4447.657] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[  4447.657] (--) AT Translated Set 2 keyboard: Found keys
[  4447.657] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[  4447.657] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[  4447.657] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[  4447.657] (**) Option "xkb_rules" "evdev"
[  4447.657] (**) Option "xkb_model" "pc105"
[  4447.658] (**) Option "xkb_layout" "us"
[  4447.658] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event8)
[  4447.658] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[  4447.658] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[  4447.658] (II) LoadModule: "synaptics"
[  4447.659] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[  4447.659] (II) Module synaptics: vendor="X.Org Foundation"
[  4447.659] 	compiled for 1.10.0.902, module version = 1.3.99
[  4447.659] 	Module class: X.Org XInput Driver
[  4447.659] 	ABI class: X.Org XInput driver, version 12.3
[  4447.659] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[  4447.659] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[  4447.659] (**) SynPS/2 Synaptics TouchPad: always reports core events
[  4447.659] (**) Option "Device" "/dev/input/event8"
[  4447.683] (--) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5692
[  4447.683] (--) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4680
[  4447.683] (--) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[  4447.683] (--) SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[  4447.683] (--) SynPS/2 Synaptics TouchPad: buttons: left right double triple
[  4447.688] (--) SynPS/2 Synaptics TouchPad: touchpad found
[  4447.688] (**) SynPS/2 Synaptics TouchPad: always reports core events
[  4447.695] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio4/input/input8/event8"
[  4447.695] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[  4447.695] (**) SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[  4447.695] (**) SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[  4447.695] (**) SynPS/2 Synaptics TouchPad: AccelFactor is now 0.037
[  4447.695] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[  4447.695] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[  4447.696] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[  4447.696] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[  4447.701] (--) SynPS/2 Synaptics TouchPad: touchpad found
[  4447.702] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[  4447.702] (II) No input driver/identifier specified (ignoring)
[  4447.702] (II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/event5)
[  4447.702] (II) No input driver/identifier specified (ignoring)
[  4447.703] (II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/js0)
[  4447.703] (II) No input driver/identifier specified (ignoring)
[  4447.718] (II) config/udev: Adding input device HP WMI hotkeys (/dev/input/event7)
[  4447.718] (**) HP WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[  4447.718] (II) Using input driver 'evdev' for 'HP WMI hotkeys'
[  4447.718] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  4447.718] (**) HP WMI hotkeys: always reports core events
[  4447.718] (**) HP WMI hotkeys: Device: "/dev/input/event7"
[  4447.732] (--) HP WMI hotkeys: Found keys
[  4447.732] (II) HP WMI hotkeys: Configuring as keyboard
[  4447.732] (**) Option "config_info" "udev:/sys/devices/virtual/input/input7/event7"
[  4447.732] (II) XINPUT: Adding extended input device "HP WMI hotkeys" (type: KEYBOARD)
[  4447.732] (**) Option "xkb_rules" "evdev"
[  4447.732] (**) Option "xkb_model" "pc105"
[  4447.732] (**) Option "xkb_layout" "us"
[  4448.039] (II) intel(0): EDID vendor "CMO", prod id 5489
[  4448.039] (II) intel(0): Printing DDC gathered Modelines:
[  4448.039] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1382 1416 1466  768 770 776 788 -hsync -vsync (47.3 kHz)
[  4448.125] (II) intel(0): EDID vendor "CMO", prod id 5489
[  4448.125] (II) intel(0): Printing DDC gathered Modelines:
[  4448.125] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1382 1416 1466  768 770 776 788 -hsync -vsync (47.3 kHz)
[  4448.205] (II) intel(0): EDID vendor "CMO", prod id 5489
[  4448.205] (II) intel(0): Printing DDC gathered Modelines:
[  4448.205] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1382 1416 1466  768 770 776 788 -hsync -vsync (47.3 kHz)
[  4448.268] (II) intel(0): EDID vendor "CMO", prod id 5489
[  4448.268] (II) intel(0): Printing DDC gathered Modelines:
[  4448.268] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1382 1416 1466  768 770 776 788 -hsync -vsync (47.3 kHz)
[  4448.354] (II) intel(0): EDID vendor "CMO", prod id 5489
[  4448.354] (II) intel(0): Printing DDC gathered Modelines:
[  4448.354] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1382 1416 1466  768 770 776 788 -hsync -vsync (47.3 kHz)
[  4448.424] (II) intel(0): Allocated new frame buffer 1408x768 stride 5632, tiled
[  4661.332] (II) AIGLX: Suspending AIGLX clients for VT switch
[  5238.017] (II) HP WMI hotkeys: Close
[  5238.017] (II) UnloadModule: "evdev"
[  5238.017] (II) Unloading evdev
[  5238.018] (II) UnloadModule: "synaptics"
[  5238.018] (II) Unloading synaptics
[  5238.018] (II) AT Translated Set 2 keyboard: Close
[  5238.018] (II) UnloadModule: "evdev"
[  5238.018] (II) Unloading evdev
[  5238.018] (II) HP Webcam [2 MP Fixed]: Close
[  5238.018] (II) UnloadModule: "evdev"
[  5238.018] (II) Unloading evdev
[  5238.018] (II) Sleep Button: Close
[  5238.018] (II) UnloadModule: "evdev"
[  5238.018] (II) Unloading evdev
[  5238.018] (II) Video Bus: Close
[  5238.018] (II) UnloadModule: "evdev"
[  5238.018] (II) Unloading evdev
[  5238.018] (II) Power Button: Close
[  5238.018] (II) UnloadModule: "evdev"
[  5238.018] (II) Unloading evdev
[  5238.047]  ddxSigGiveUp: Closing log
```

And here's dmesg:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.38-8-generic (buildd@vernadsky) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 (Ubuntu 2.6.38-8.42-generic 2.6.38.2)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000ef000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000076b58000 (usable)
[    0.000000]  BIOS-e820: 0000000076b58000 - 0000000076b5a000 (reserved)
[    0.000000]  BIOS-e820: 0000000076b5a000 - 0000000077970000 (usable)
[    0.000000]  BIOS-e820: 0000000077970000 - 0000000077980000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000077980000 - 000000007a10a000 (usable)
[    0.000000]  BIOS-e820: 000000007a10a000 - 000000007a30a000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007a30a000 - 000000007ba92000 (usable)
[    0.000000]  BIOS-e820: 000000007ba92000 - 000000007ba9a000 (reserved)
[    0.000000]  BIOS-e820: 000000007ba9a000 - 000000007babf000 (usable)
[    0.000000]  BIOS-e820: 000000007babf000 - 000000007bacf000 (reserved)
[    0.000000]  BIOS-e820: 000000007bacf000 - 000000007bbcf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007bbcf000 - 000000007bbff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007bbff000 - 000000007bc00000 (usable)
[    0.000000]  BIOS-e820: 000000007bc00000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed14000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI 2.4 present.
[    0.000000] DMI: Hewlett-Packard HP ProBook 4510s/3072, BIOS 68PZI Ver. F.0F 10/20/2009
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x7bc00 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0FFE00000 mask FFFE00000 write-protect
[    0.000000]   1 base 000000000 mask F80000000 write-back
[    0.000000]   2 base 077970000 mask FFFFF0000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 35cb0000 - 36e50000
[    0.000000] ACPI: RSDP 000f6970 00024 (v02 HPQOEM)
[    0.000000] ACPI: XSDT 7bbfe120 00074 (v01 HPQOEM SLIC-MPC 0000000F      01000013)
[    0.000000] ACPI: FACP 7bbfc000 000F4 (v03 HPQOEM 3072     0000000F HP   00000001)
[    0.000000] ACPI: DSDT 7bbdb000 1B05A (v01 HPQOEM 3072     00000001 INTL 20060912)
[    0.000000] ACPI: FACS 7bbad000 00040
[    0.000000] ACPI: HPET 7bbfb000 00038 (v01 HPQOEM 3072     00000001 HP   00000001)
[    0.000000] ACPI: APIC 7bbfa000 00084 (v01 HPQOEM 3072     00000001 HP   00000001)
[    0.000000] ACPI: MCFG 7bbf9000 0003C (v01 HPQOEM 3072     00000001 HP   00000001)
[    0.000000] ACPI: ASF! 7bbf8000 000A0 (v32 HPQOEM 3072     00000001 HP   00000001)
[    0.000000] ACPI: SSDT 7bbda000 0064F (v01 HPQOEM  SataPri 00001000 INTL 20060912)
[    0.000000] ACPI: SSDT 7bbd9000 00692 (v01 HPQOEM  SataSec 00001000 INTL 20060912)
[    0.000000] ACPI: SSDT 7bbd6000 0066C (v01  PmRef    CpuPm 00003000 INTL 20060912)
[    0.000000] ACPI: SSDT 7bbd5000 00288 (v01  PmRef  Cpu0Tst 00003000 INTL 20060912)
[    0.000000] ACPI: SSDT 7bbd4000 00225 (v01  PmRef    ApTst 00003000 INTL 20060912)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1092MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007bc00
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[7] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x00076b58
[    0.000000]     0: 0x00076b5a -> 0x00077970
[    0.000000]     0: 0x00077980 -> 0x0007a10a
[    0.000000]     0: 0x0007a30a -> 0x0007ba92
[    0.000000]     0: 0x0007ba9a -> 0x0007babf
[    0.000000]     0: 0x0007bbff -> 0x0007bc00
[    0.000000] On node 0 totalpages: 505909
[    0.000000] free_area_init_node: node 0, pgdat c1784100, node_mem_map f4d38200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2185 pages used for memmap
[    0.000000]   HighMem zone: 276511 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000ef000
[    0.000000] PM: Registered nosave memory: 00000000000ef000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:60000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f7000000 s28800 r0 d24448 u1048576
[    0.000000] pcpu-alloc: s28800 r0 d24448 u1048576 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 501948
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=846c2273-e3f1-4e5d-b501-6ea7513a99b1 ro vga=792
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] allocated 10137280 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007bc00)
[    0.000000] Memory: 1969428k/2027520k available (5188k kernel code, 54208k reserved, 2540k data, 700k init, 1114784k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc178d000 - 0xc183c000   ( 700 kB)
[    0.000000]       .data : 0xc15112a1 - 0xc178c480   (2540 kB)
[    0.000000]       .text : 0xc1000000 - 0xc15112a1   (5188 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:712 16
[    0.000000] CPU 0 irqstacks, hard=f3c08000 soft=f3c0a000
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2095.182 MHz processor.
[    0.004003] Calibrating delay loop (skipped), value calculated using timer frequency.. 4190.36 BogoMIPS (lpj=8380728)
[    0.004012] pid_max: default: 32768 minimum: 301
[    0.004039] Security Framework initialized
[    0.004056] AppArmor: AppArmor initialized
[    0.004060] Yama: becoming mindful.
[    0.004119] Mount-cache hash table entries: 512
[    0.004258] Initializing cgroup subsys ns
[    0.004264] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
[    0.004271] Initializing cgroup subsys cpuacct
[    0.004278] Initializing cgroup subsys memory
[    0.004289] Initializing cgroup subsys devices
[    0.004294] Initializing cgroup subsys freezer
[    0.004298] Initializing cgroup subsys net_cls
[    0.004302] Initializing cgroup subsys blkio
[    0.004342] CPU: Physical Processor ID: 0
[    0.004347] CPU: Processor Core ID: 0
[    0.004351] mce: CPU supports 6 MCE banks
[    0.004361] CPU0: Thermal monitoring handled by SMI
[    0.004365] using mwait in idle threads.
[    0.010507] ACPI: Core revision 20110112
[    0.021747] ftrace: allocating 23640 entries in 47 pages
[    0.024055] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.024420] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.064834] CPU0: Intel(R) Core(TM)2 Duo CPU     T6570  @ 2.10GHz stepping 0a
[    0.068003] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.068003] ... version:                2
[    0.068003] ... bit width:              40
[    0.068003] ... generic registers:      2
[    0.068003] ... value mask:             000000ffffffffff
[    0.068003] ... max period:             000000007fffffff
[    0.068003] ... fixed-purpose events:   3
[    0.068003] ... event mask:             0000000700000003
[    0.068003] CPU 1 irqstacks, hard=f3cd2000 soft=f3cd4000
[    0.068003] Booting Node   0, Processors  #1
[    0.008000] Initializing CPU#1
[    0.008000] CPU1: Thermal monitoring handled by SMI
[    0.156026] Brought up 2 CPUs
[    0.156036] Total of 2 processors activated (8379.82 BogoMIPS).
[    0.156600] devtmpfs: initialized
[    0.157303] print_constraints: dummy: 
[    0.157340] Time: 16:56:02  Date: 02/01/12
[    0.157381] NET: Registered protocol family 16
[    0.157411] Trying to unpack rootfs image as initramfs...
[    0.157505] EISA bus registered
[    0.157514] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.157521] ACPI: bus type pci registered
[    0.157599] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.157607] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.157613] PCI: Using MMCONFIG for extended config space
[    0.157617] PCI: Using configuration type 1 for base access
[    0.172147] bio: create slab <bio-0> at 0
[    0.175001] ACPI: EC: Look up EC in DSDT
[    0.212110] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.290035] ACPI: SSDT 7bac6c18 00275 (v01  PmRef  Cpu0Ist 00003000 INTL 20060912)
[    0.290702] ACPI: Dynamic OEM Table Load:
[    0.290708] ACPI: SSDT   (null) 00275 (v01  PmRef  Cpu0Ist 00003000 INTL 20060912)
[    0.290873] ACPI: SSDT 7bac4618 0057B (v01  PmRef  Cpu0Cst 00003001 INTL 20060912)
[    0.291513] ACPI: Dynamic OEM Table Load:
[    0.291519] ACPI: SSDT   (null) 0057B (v01  PmRef  Cpu0Cst 00003001 INTL 20060912)
[    0.352379] ACPI: SSDT 7bac5e18 001D7 (v01  PmRef    ApIst 00003000 INTL 20060912)
[    0.353071] ACPI: Dynamic OEM Table Load:
[    0.353077] ACPI: SSDT   (null) 001D7 (v01  PmRef    ApIst 00003000 INTL 20060912)
[    0.364161] ACPI: SSDT 7bac6f18 0008D (v01  PmRef    ApCst 00003000 INTL 20060912)
[    0.364823] ACPI: Dynamic OEM Table Load:
[    0.364829] ACPI: SSDT   (null) 0008D (v01  PmRef    ApCst 00003000 INTL 20060912)
[    0.583229] Freeing initrd memory: 18048k freed
[    0.640150] ACPI: Interpreter enabled
[    0.640169] ACPI: (supports S0 S3 S4 S5)
[    0.640200] ACPI: Using IOAPIC for interrupt routing
[    0.645091] ACPI: Power Resource [APPR] (off)
[    0.674026] ACPI: Power Resource [PFN6] (off)
[    0.674107] ACPI: Power Resource [PFN7] (off)
[    0.674185] ACPI: Power Resource [PFN8] (off)
[    0.674262] ACPI: Power Resource [PFN9] (off)
[    0.674343] ACPI: Power Resource [PFNA] (off)
[    0.674423] ACPI: Power Resource [PFNB] (off)
[    0.674476] ACPI: Power Resource [PGF0] (off)
[    0.675277] ACPI: Power Resource [PFN0] (off)
[    0.675359] ACPI: Power Resource [PFN1] (off)
[    0.675437] ACPI: Power Resource [PFN2] (off)
[    0.675516] ACPI: Power Resource [PFN3] (off)
[    0.675598] ACPI: Power Resource [PFN4] (off)
[    0.675677] ACPI: Power Resource [PFN5] (off)
[    0.676756] ACPI: EC: GPE = 0x16, I/O: command/status = 0x66, data = 0x62
[    0.677072] ACPI: No dock devices found.
[    0.677077] HEST: Table not found.
[    0.677083] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.678132] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.678930] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.678937] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.678942] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.678950] pci_root PNP0A08:00: host bridge window [mem 0x80000000-0xdfffffff]
[    0.678956] pci_root PNP0A08:00: host bridge window [mem 0xf0000000-0xfedfffff]
[    0.678962] pci_root PNP0A08:00: host bridge window [mem 0xfee01000-0xffffffff]
[    0.678982] pci 0000:00:00.0: [8086:2a40] type 0 class 0x000600
[    0.679009] DMAR: Forcing write-buffer flush capability
[    0.679013] DMAR: Disabling IOMMU for graphics on this chipset
[    0.679040] pci 0000:00:02.0: [8086:2a42] type 0 class 0x000300
[    0.679055] pci 0000:00:02.0: reg 10: [mem 0x90000000-0x903fffff 64bit]
[    0.679065] pci 0000:00:02.0: reg 18: [mem 0x80000000-0x8fffffff 64bit pref]
[    0.679072] pci 0000:00:02.0: reg 20: [io  0x7120-0x7127]
[    0.679108] pci 0000:00:02.1: [8086:2a43] type 0 class 0x000380
[    0.679121] pci 0000:00:02.1: reg 10: [mem 0x90400000-0x904fffff 64bit]
[    0.679217] pci 0000:00:1a.0: [8086:2937] type 0 class 0x000c03
[    0.679280] pci 0000:00:1a.0: reg 20: [io  0x70a0-0x70bf]
[    0.679344] pci 0000:00:1a.1: [8086:2938] type 0 class 0x000c03
[    0.679407] pci 0000:00:1a.1: reg 20: [io  0x7080-0x709f]
[    0.679470] pci 0000:00:1a.2: [8086:2939] type 0 class 0x000c03
[    0.679533] pci 0000:00:1a.2: reg 20: [io  0x7060-0x707f]
[    0.679610] pci 0000:00:1a.7: [8086:293c] type 0 class 0x000c03
[    0.679640] pci 0000:00:1a.7: reg 10: [mem 0x98804400-0x988047ff]
[    0.679739] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.679745] pci 0000:00:1a.7: PME# disabled
[    0.679778] pci 0000:00:1b.0: [8086:293e] type 0 class 0x000403
[    0.679802] pci 0000:00:1b.0: reg 10: [mem 0x98800000-0x98803fff 64bit]
[    0.679888] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.679893] pci 0000:00:1b.0: PME# disabled
[    0.679922] pci 0000:00:1c.0: [8086:2940] type 1 class 0x000604
[    0.680011] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.680016] pci 0000:00:1c.0: PME# disabled
[    0.680062] pci 0000:00:1c.2: [8086:2944] type 1 class 0x000604
[    0.680152] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.680157] pci 0000:00:1c.2: PME# disabled
[    0.680191] pci 0000:00:1c.4: [8086:2948] type 1 class 0x000604
[    0.680279] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.680285] pci 0000:00:1c.4: PME# disabled
[    0.680317] pci 0000:00:1c.5: [8086:294a] type 1 class 0x000604
[    0.680406] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.680411] pci 0000:00:1c.5: PME# disabled
[    0.680447] pci 0000:00:1d.0: [8086:2934] type 0 class 0x000c03
[    0.680509] pci 0000:00:1d.0: reg 20: [io  0x7040-0x705f]
[    0.680573] pci 0000:00:1d.1: [8086:2935] type 0 class 0x000c03
[    0.680636] pci 0000:00:1d.1: reg 20: [io  0x7020-0x703f]
[    0.680700] pci 0000:00:1d.2: [8086:2936] type 0 class 0x000c03
[    0.680763] pci 0000:00:1d.2: reg 20: [io  0x7000-0x701f]
[    0.680840] pci 0000:00:1d.7: [8086:293a] type 0 class 0x000c03
[    0.680869] pci 0000:00:1d.7: reg 10: [mem 0x98804000-0x988043ff]
[    0.680967] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.680973] pci 0000:00:1d.7: PME# disabled
[    0.681000] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    0.681090] pci 0000:00:1f.0: [8086:2919] type 0 class 0x000601
[    0.681249] pci 0000:00:1f.2: [8086:2928] type 0 class 0x000101
[    0.681274] pci 0000:00:1f.2: reg 10: [io  0x7118-0x711f]
[    0.681286] pci 0000:00:1f.2: reg 14: [io  0x7134-0x7137]
[    0.681299] pci 0000:00:1f.2: reg 18: [io  0x7110-0x7117]
[    0.681312] pci 0000:00:1f.2: reg 1c: [io  0x7130-0x7133]
[    0.681324] pci 0000:00:1f.2: reg 20: [io  0x70f0-0x70ff]
[    0.681337] pci 0000:00:1f.2: reg 24: [io  0x70e0-0x70ef]
[    0.681408] pci 0000:00:1f.5: [8086:292d] type 0 class 0x000101
[    0.681433] pci 0000:00:1f.5: reg 10: [io  0x7108-0x710f]
[    0.681445] pci 0000:00:1f.5: reg 14: [io  0x712c-0x712f]
[    0.681458] pci 0000:00:1f.5: reg 18: [io  0x7100-0x7107]
[    0.681470] pci 0000:00:1f.5: reg 1c: [io  0x7128-0x712b]
[    0.681483] pci 0000:00:1f.5: reg 20: [io  0x70d0-0x70df]
[    0.681495] pci 0000:00:1f.5: reg 24: [io  0x70c0-0x70cf]
[    0.681611] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.681619] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.681625] pci 0000:00:1c.0:   bridge window [mem 0x98700000-0x987fffff]
[    0.681634] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.681698] pci 0000:00:1c.2: PCI bridge to [bus 02-42]
[    0.681706] pci 0000:00:1c.2:   bridge window [io  0x5000-0x6fff]
[    0.681711] pci 0000:00:1c.2:   bridge window [mem 0x94700000-0x986fffff]
[    0.681720] pci 0000:00:1c.2:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.681784] pci 0000:00:1c.4: PCI bridge to [bus 43-83]
[    0.681792] pci 0000:00:1c.4:   bridge window [io  0x3000-0x4fff]
[    0.681797] pci 0000:00:1c.4:   bridge window [mem 0x90700000-0x946fffff]
[    0.681805] pci 0000:00:1c.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.682066] pci 0000:84:00.0: [11ab:436c] type 0 class 0x000200
[    0.682239] pci 0000:84:00.0: reg 10: [mem 0x90600000-0x90603fff 64bit]
[    0.682339] pci 0000:84:00.0: reg 18: [io  0x2000-0x20ff]
[    0.682700] pci 0000:84:00.0: reg 30: [mem 0xfffe0000-0xffffffff pref]
[    0.683025] pci 0000:84:00.0: supports D1 D2
[    0.683027] pci 0000:84:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.683053] pci 0000:84:00.0: PME# disabled
[    0.683233] pci 0000:00:1c.5: PCI bridge to [bus 84-84]
[    0.683241] pci 0000:00:1c.5:   bridge window [io  0x2000-0x2fff]
[    0.683246] pci 0000:00:1c.5:   bridge window [mem 0x90600000-0x906fffff]
[    0.683255] pci 0000:00:1c.5:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.683356] pci 0000:00:1e.0: PCI bridge to [bus 85-85] (subtractive decode)
[    0.683364] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.683369] pci 0000:00:1e.0:   bridge window [mem 0x90500000-0x905fffff]
[    0.683378] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.683381] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.683384] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.683387] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.683389] pci 0000:00:1e.0:   bridge window [mem 0x80000000-0xdfffffff] (subtractive decode)
[    0.683392] pci 0000:00:1e.0:   bridge window [mem 0xf0000000-0xfedfffff] (subtractive decode)
[    0.683395] pci 0000:00:1e.0:   bridge window [mem 0xfee01000-0xffffffff] (subtractive decode)
[    0.683429] pci_bus 0000:00: on NUMA node 0
[    0.683432] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.683666] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.683726] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.683820] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[    0.683913] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    0.684008] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.694753] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.694817] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.694878] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.694939] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.695000] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.695061] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.695122] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.695183] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    0.695317] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.695336] vgaarb: loaded
[    0.695611] SCSI subsystem initialized
[    0.695626] libata version 3.00 loaded.
[    0.695626] usbcore: registered new interface driver usbfs
[    0.695626] usbcore: registered new interface driver hub
[    0.695626] usbcore: registered new device driver usb
[    0.696179] wmi: Mapper loaded
[    0.696184] PCI: Using ACPI for IRQ routing
[    0.696190] PCI: pci_cache_line_size set to 64 bytes
[    0.696291] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.696294] reserve RAM buffer: 0000000076b58000 - 0000000077ffffff 
[    0.696297] reserve RAM buffer: 0000000077970000 - 0000000077ffffff 
[    0.696299] reserve RAM buffer: 000000007a10a000 - 000000007bffffff 
[    0.696303] reserve RAM buffer: 000000007ba92000 - 000000007bffffff 
[    0.696307] reserve RAM buffer: 000000007babf000 - 000000007bffffff 
[    0.696310] reserve RAM buffer: 000000007bc00000 - 000000007bffffff 
[    0.696423] NetLabel: Initializing
[    0.696428] NetLabel:  domain hash size = 128
[    0.696431] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.696445] NetLabel:  unlabeled traffic allowed by default
[    0.696492] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.696503] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.696511] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.700061] Switching to clocksource hpet
[    0.703893] Switched to NOHz mode on CPU #0
[    0.703995] Switched to NOHz mode on CPU #1
[    0.708287] AppArmor: AppArmor Filesystem Enabled
[    0.708327] pnp: PnP ACPI init
[    0.708349] ACPI: bus type pnp registered
[    0.708794] pnp 00:00: [bus 00-ff]
[    0.708798] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.708800] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.708802] pnp 00:00: [io  0x0d00-0xffff window]
[    0.708805] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.708808] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.708810] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.708812] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.708815] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.708817] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.708820] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.708822] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.708825] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.708827] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.708832] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.708834] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.708837] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.708839] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    0.708842] pnp 00:00: [mem 0x80000000-0xdfffffff window]
[    0.708844] pnp 00:00: [mem 0xf0000000-0xfedfffff window]
[    0.708847] pnp 00:00: [mem 0xfee01000-0xffffffff window]
[    0.708984] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.709077] pnp 00:01: [mem 0xfed1c000-0xfed1ffff]
[    0.709080] pnp 00:01: [mem 0xfed10000-0xfed13fff]
[    0.709082] pnp 00:01: [mem 0xfed18000-0xfed18fff]
[    0.709084] pnp 00:01: [mem 0xfed19000-0xfed19fff]
[    0.709087] pnp 00:01: [mem 0xe0000000-0xefffffff]
[    0.709089] pnp 00:01: [mem 0xfec00000-0xfec00fff]
[    0.709091] pnp 00:01: [mem 0xfed20000-0xfed3ffff]
[    0.709094] pnp 00:01: [mem 0xfed45000-0xfed8ffff]
[    0.709160] system 00:01: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.709167] system 00:01: [mem 0xfed10000-0xfed13fff] has been reserved
[    0.709172] system 00:01: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.709178] system 00:01: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.709184] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.709189] system 00:01: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.709195] system 00:01: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.709201] system 00:01: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.709207] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.709677] pnp 00:02: [io  0x0000-0x001f]
[    0.709679] pnp 00:02: [io  0x0081-0x0091]
[    0.709682] pnp 00:02: [io  0x0093-0x009f]
[    0.709684] pnp 00:02: [io  0x00c0-0x00df]
[    0.709686] pnp 00:02: [dma 4]
[    0.709752] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.709762] pnp 00:03: [mem 0xff000000-0xffffffff]
[    0.709827] pnp 00:03: Plug and Play ACPI device, IDs INT0800 (active)
[    0.709862] pnp 00:04: [io  0xfe00-0xfe0f]
[    0.709865] pnp 00:04: [io  0xfe80-0xfe8f]
[    0.709867] pnp 00:04: [mem 0xfed40000-0xfed44fff]
[    0.709953] system 00:04: [io  0xfe00-0xfe0f] has been reserved
[    0.709959] system 00:04: [io  0xfe80-0xfe8f] has been reserved
[    0.709965] system 00:04: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.709971] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.710068] pnp 00:05: [mem 0xfed00000-0xfed003ff]
[    0.710157] system 00:05: [mem 0xfed00000-0xfed003ff] has been reserved
[    0.710164] system 00:05: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
[    0.710177] pnp 00:06: [io  0x00f0]
[    0.710191] pnp 00:06: [irq 13]
[    0.710259] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.710272] pnp 00:07: [io  0x002e-0x002f]
[    0.710275] pnp 00:07: [io  0x004e-0x004f]
[    0.710277] pnp 00:07: [io  0x0061]
[    0.710279] pnp 00:07: [io  0x0063]
[    0.710281] pnp 00:07: [io  0x0065]
[    0.710283] pnp 00:07: [io  0x0067]
[    0.710285] pnp 00:07: [io  0x0070]
[    0.710287] pnp 00:07: [io  0x0080]
[    0.710289] pnp 00:07: [io  0x0092]
[    0.710291] pnp 00:07: [io  0x00b2-0x00b3]
[    0.710293] pnp 00:07: [io  0x0200-0x027f]
[    0.710295] pnp 00:07: [io  0x1000-0x1003]
[    0.710297] pnp 00:07: [io  0x1010-0x101f]
[    0.710300] pnp 00:07: [io  0xffff]
[    0.710302] pnp 00:07: [io  0x0400-0x047f]
[    0.710304] pnp 00:07: [io  0x0500-0x057f]
[    0.710306] pnp 00:07: [io  0xef80-0xef9f]
[    0.710409] system 00:07: [io  0x0200-0x027f] has been reserved
[    0.710415] system 00:07: [io  0x1000-0x1003] has been reserved
[    0.710420] system 00:07: [io  0x1010-0x101f] has been reserved
[    0.710426] system 00:07: [io  0xffff] has been reserved
[    0.710431] system 00:07: [io  0x0400-0x047f] has been reserved
[    0.710436] system 00:07: [io  0x0500-0x057f] has been reserved
[    0.710441] system 00:07: [io  0xef80-0xef9f] has been reserved
[    0.710447] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.710458] pnp 00:08: [io  0x0070-0x0077]
[    0.710463] pnp 00:08: [irq 8]
[    0.710530] pnp 00:08: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.710689] pnp 00:09: [io  0x0060]
[    0.710692] pnp 00:09: [io  0x0064]
[    0.710697] pnp 00:09: [irq 1]
[    0.710766] pnp 00:09: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.710780] pnp 00:0a: [irq 12]
[    0.710852] pnp 00:0a: Plug and Play ACPI device, IDs SYN0149 SYN0100 SYN0002 PNP0f13 (active)
[    0.710900] pnp 00:0b: [irq 23]
[    0.710972] pnp 00:0b: Plug and Play ACPI device, IDs HPQ0004 (active)
[    0.711116] pnp: PnP ACPI: found 12 devices
[    0.711121] ACPI: ACPI bus type pnp unregistered
[    0.711128] PnPBIOS: Disabled by ACPI PNP
[    0.747836] pci 0000:84:00.0: no compatible bridge window for [mem 0xfffe0000-0xffffffff pref]
[    0.747901] pci 0000:00:1c.0: BAR 15: assigned [mem 0x98900000-0x98afffff 64bit pref]
[    0.747911] pci 0000:00:1c.2: BAR 15: assigned [mem 0x98b00000-0x98cfffff 64bit pref]
[    0.747920] pci 0000:00:1c.4: BAR 15: assigned [mem 0x98d00000-0x98efffff 64bit pref]
[    0.747928] pci 0000:00:1c.5: BAR 15: assigned [mem 0x98f00000-0x990fffff pref]
[    0.747936] pci 0000:00:1c.0: BAR 13: assigned [io  0x8000-0x8fff]
[    0.747941] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.747947] pci 0000:00:1c.0:   bridge window [io  0x8000-0x8fff]
[    0.747957] pci 0000:00:1c.0:   bridge window [mem 0x98700000-0x987fffff]
[    0.747965] pci 0000:00:1c.0:   bridge window [mem 0x98900000-0x98afffff 64bit pref]
[    0.747977] pci 0000:00:1c.2: PCI bridge to [bus 02-42]
[    0.747983] pci 0000:00:1c.2:   bridge window [io  0x5000-0x6fff]
[    0.747992] pci 0000:00:1c.2:   bridge window [mem 0x94700000-0x986fffff]
[    0.748015] pci 0000:00:1c.2:   bridge window [mem 0x98b00000-0x98cfffff 64bit pref]
[    0.748027] pci 0000:00:1c.4: PCI bridge to [bus 43-83]
[    0.748033] pci 0000:00:1c.4:   bridge window [io  0x3000-0x4fff]
[    0.748042] pci 0000:00:1c.4:   bridge window [mem 0x90700000-0x946fffff]
[    0.748050] pci 0000:00:1c.4:   bridge window [mem 0x98d00000-0x98efffff 64bit pref]
[    0.748063] pci 0000:84:00.0: BAR 6: assigned [mem 0x98f00000-0x98f1ffff pref]
[    0.748069] pci 0000:00:1c.5: PCI bridge to [bus 84-84]
[    0.748075] pci 0000:00:1c.5:   bridge window [io  0x2000-0x2fff]
[    0.748084] pci 0000:00:1c.5:   bridge window [mem 0x90600000-0x906fffff]
[    0.748092] pci 0000:00:1c.5:   bridge window [mem 0x98f00000-0x990fffff pref]
[    0.748104] pci 0000:00:1e.0: PCI bridge to [bus 85-85]
[    0.748108] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.748117] pci 0000:00:1e.0:   bridge window [mem 0x90500000-0x905fffff]
[    0.748124] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.748147] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.748157] pci 0000:00:1c.0: setting latency timer to 64
[    0.748168] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.748176] pci 0000:00:1c.2: setting latency timer to 64
[    0.748184] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.748192] pci 0000:00:1c.4: setting latency timer to 64
[    0.748203] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.748211] pci 0000:00:1c.5: setting latency timer to 64
[    0.748220] pci 0000:00:1e.0: setting latency timer to 64
[    0.748225] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.748227] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.748230] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.748232] pci_bus 0000:00: resource 7 [mem 0x80000000-0xdfffffff]
[    0.748235] pci_bus 0000:00: resource 8 [mem 0xf0000000-0xfedfffff]
[    0.748237] pci_bus 0000:00: resource 9 [mem 0xfee01000-0xffffffff]
[    0.748240] pci_bus 0000:01: resource 0 [io  0x8000-0x8fff]
[    0.748242] pci_bus 0000:01: resource 1 [mem 0x98700000-0x987fffff]
[    0.748245] pci_bus 0000:01: resource 2 [mem 0x98900000-0x98afffff 64bit pref]
[    0.748248] pci_bus 0000:02: resource 0 [io  0x5000-0x6fff]
[    0.748250] pci_bus 0000:02: resource 1 [mem 0x94700000-0x986fffff]
[    0.748253] pci_bus 0000:02: resource 2 [mem 0x98b00000-0x98cfffff 64bit pref]
[    0.748256] pci_bus 0000:43: resource 0 [io  0x3000-0x4fff]
[    0.748258] pci_bus 0000:43: resource 1 [mem 0x90700000-0x946fffff]
[    0.748261] pci_bus 0000:43: resource 2 [mem 0x98d00000-0x98efffff 64bit pref]
[    0.748263] pci_bus 0000:84: resource 0 [io  0x2000-0x2fff]
[    0.748266] pci_bus 0000:84: resource 1 [mem 0x90600000-0x906fffff]
[    0.748269] pci_bus 0000:84: resource 2 [mem 0x98f00000-0x990fffff pref]
[    0.748271] pci_bus 0000:85: resource 1 [mem 0x90500000-0x905fffff]
[    0.748274] pci_bus 0000:85: resource 4 [io  0x0000-0x0cf7]
[    0.748276] pci_bus 0000:85: resource 5 [io  0x0d00-0xffff]
[    0.748279] pci_bus 0000:85: resource 6 [mem 0x000a0000-0x000bffff]
[    0.748281] pci_bus 0000:85: resource 7 [mem 0x80000000-0xdfffffff]
[    0.748284] pci_bus 0000:85: resource 8 [mem 0xf0000000-0xfedfffff]
[    0.748286] pci_bus 0000:85: resource 9 [mem 0xfee01000-0xffffffff]
[    0.748322] NET: Registered protocol family 2
[    0.748400] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.748683] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.749160] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.749357] TCP: Hash tables configured (established 131072 bind 65536)
[    0.749362] TCP reno registered
[    0.749366] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.749376] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.749469] NET: Registered protocol family 1
[    0.749490] pci 0000:00:02.0: Boot video device
[    0.749768] PCI: CLS 64 bytes, default 64
[    0.750018] cpufreq-nforce2: No nForce2 chipset.
[    0.750178] audit: initializing netlink socket (disabled)
[    0.750190] type=2000 audit(1328115361.744:1): initialized
[    0.760093] highmem bounce pool size: 64 pages
[    0.760101] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.762113] VFS: Disk quotas dquot_6.5.2
[    0.762183] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.762915] fuse init (API version 7.16)
[    0.763028] msgmni has been set to 1704
[    0.763306] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.763340] io scheduler noop registered
[    0.763345] io scheduler deadline registered
[    0.763363] io scheduler cfq registered (default)
[    0.763495] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.763558] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.763646] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.763702] pcieport 0000:00:1c.2: irq 41 for MSI/MSI-X
[    0.763788] pcieport 0000:00:1c.4: setting latency timer to 64
[    0.763845] pcieport 0000:00:1c.4: irq 42 for MSI/MSI-X
[    0.763932] pcieport 0000:00:1c.5: setting latency timer to 64
[    0.763988] pcieport 0000:00:1c.5: irq 43 for MSI/MSI-X
[    0.764119] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.764155] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.764231] intel_idle: MWAIT substates: 0x3122220
[    0.764233] intel_idle: does not run on family 6 model 23
[    0.764413] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.764544] ACPI: AC Adapter [AC] (on-line)
[    0.764829] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input0
[    0.764839] ACPI: Sleep Button [SLPB]
[    0.764894] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    0.764946] ACPI: Lid Switch [LID]
[    0.765008] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.765015] ACPI: Power Button [PWRF]
[    0.765134] ACPI: Fan [FAN6] (off)
[    0.765203] ACPI: Fan [FAN7] (off)
[    0.765269] ACPI: Fan [FAN8] (off)
[    0.765339] ACPI: Fan [FAN9] (off)
[    0.765405] ACPI: Fan [FANA] (off)
[    0.765471] ACPI: Fan [FANB] (off)
[    0.765517] ACPI: Fan [FANG] (off)
[    0.765586] ACPI: Fan [FAN0] (off)
[    0.765653] ACPI: Fan [FAN1] (off)
[    0.765721] ACPI: Fan [FAN2] (off)
[    0.765790] ACPI: Fan [FAN3] (off)
[    0.765864] ACPI: Fan [FAN4] (off)
[    0.765933] ACPI: Fan [FAN5] (off)
[    0.766182] ACPI: acpi_idle registered with cpuidle
[    0.768787] Monitor-Mwait will be used to enter C-1 state
[    0.768817] Monitor-Mwait will be used to enter C-2 state
[    0.768824] Marking TSC unstable due to TSC halts in idle
[    1.308782] thermal LNXTHERM:00: registered as thermal_zone0
[    1.308789] ACPI: Thermal Zone [GFXZ] (16 C)
[    1.318208] thermal LNXTHERM:01: registered as thermal_zone1
[    1.318214] ACPI: Thermal Zone [DTSZ] (33 C)
[    1.323524] thermal LNXTHERM:02: registered as thermal_zone2
[    1.323530] ACPI: Thermal Zone [CPUZ] (34 C)
[    1.327027] thermal LNXTHERM:03: registered as thermal_zone3
[    1.327033] ACPI: Thermal Zone [SKNZ] (21 C)
[    1.337724] thermal LNXTHERM:04: registered as thermal_zone4
[    1.337730] ACPI: Thermal Zone [BATZ] (20 C)
[    1.341475] thermal LNXTHERM:05: registered as thermal_zone5
[    1.341481] ACPI: Thermal Zone [FDTZ] (34 C)
[    1.341517] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.341604] ERST: Table is not found!
[    1.341672] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.341814] isapnp: Scanning for PnP cards...
[    1.393864] ACPI: Battery Slot [BAT0] (battery present)
[    1.697184] isapnp: No Plug & Play device found
[    1.736609] Linux agpgart interface v0.103
[    1.736735] agpgart-intel 0000:00:00.0: Intel GM45 Chipset
[    1.736873] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    1.737900] agpgart-intel 0000:00:00.0: detected 65536K stolen memory
[    1.738034] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x80000000
[    1.739500] brd: module loaded
[    1.740227] loop: module loaded
[    1.740336] i2c-core: driver [adp5520] using legacy suspend method
[    1.740341] i2c-core: driver [adp5520] using legacy resume method
[    1.740463] ata_piix 0000:00:1f.2: version 2.13
[    1.740488] ata_piix 0000:00:1f.2: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    1.740498] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[    1.896036] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.896338] scsi0 : ata_piix
[    1.896444] scsi1 : ata_piix
[    1.897108] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x70f0 irq 14
[    1.897116] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x70f8 irq 15
[    1.897139] ata_piix 0000:00:1f.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.897150] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    2.052024] ata_piix 0000:00:1f.5: SCR access via SIDPR is available but doesn't work
[    2.052040] ata_piix 0000:00:1f.5: setting latency timer to 64
[    2.052320] scsi2 : ata_piix
[    2.052408] scsi3 : ata_piix
[    2.052462] ata3: SATA max UDMA/133 cmd 0x7108 ctl 0x712c bmdma 0x70d0 irq 18
[    2.052467] ata4: SATA max UDMA/133 cmd 0x7100 ctl 0x7128 bmdma 0x70d8 irq 18
[    2.052948] Fixed MDIO Bus: probed
[    2.053001] PPP generic driver version 2.4.2
[    2.053053] tun: Universal TUN/TAP device driver, 1.6
[    2.053057] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    2.053159] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.053184] ehci_hcd 0000:00:1a.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    2.053203] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    2.053207] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    2.053253] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    2.053382] ehci_hcd 0000:00:1a.7: debug port 1
[    2.057274] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
[    2.057290] ehci_hcd 0000:00:1a.7: irq 19, io mem 0x98804400
[    2.072017] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    2.072144] hub 1-0:1.0: USB hub found
[    2.072151] hub 1-0:1.0: 6 ports detected
[    2.072245] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 20 (level, low) -> IRQ 20
[    2.072261] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.072265] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.072311] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    2.072368] ehci_hcd 0000:00:1d.7: debug port 1
[    2.076256] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    2.076271] ehci_hcd 0000:00:1d.7: irq 20, io mem 0x98804000
[    2.092017] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    2.092152] hub 2-0:1.0: USB hub found
[    2.092159] hub 2-0:1.0: 6 ports detected
[    2.092249] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.092268] uhci_hcd: USB Universal Host Controller Interface driver
[    2.092297] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.092307] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    2.092310] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    2.092355] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    2.092414] uhci_hcd 0000:00:1a.0: irq 16, io base 0x000070a0
[    2.092545] hub 3-0:1.0: USB hub found
[    2.092552] hub 3-0:1.0: 2 ports detected
[    2.092631] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.092641] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    2.092645] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    2.092691] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    2.092750] uhci_hcd 0000:00:1a.1: irq 17, io base 0x00007080
[    2.092886] hub 4-0:1.0: USB hub found
[    2.092892] hub 4-0:1.0: 2 ports detected
[    2.092975] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.092987] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    2.092991] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    2.093037] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    2.096051] uhci_hcd 0000:00:1a.2: irq 18, io base 0x00007060
[    2.096181] hub 5-0:1.0: USB hub found
[    2.096187] hub 5-0:1.0: 2 ports detected
[    2.096268] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.096278] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.096281] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.096322] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    2.096370] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00007040
[    2.096506] hub 6-0:1.0: USB hub found
[    2.096512] hub 6-0:1.0: 2 ports detected
[    2.096592] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    2.096604] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.096608] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.096652] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    2.096711] uhci_hcd 0000:00:1d.1: irq 22, io base 0x00007020
[    2.096843] hub 7-0:1.0: USB hub found
[    2.096850] hub 7-0:1.0: 2 ports detected
[    2.096927] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.096937] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.096941] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.096981] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    2.097032] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00007000
[    2.097173] hub 8-0:1.0: USB hub found
[    2.097180] hub 8-0:1.0: 2 ports detected
[    2.097333] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.098988] i8042: Detected active multiplexing controller, rev 1.1
[    2.099751] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.099759] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    2.099796] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    2.099832] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    2.099864] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    2.100016] mousedev: PS/2 mouse device common for all mice
[    2.100207] rtc_cmos 00:08: RTC can wake from S4
[    2.100273] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    2.100309] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    2.100403] device-mapper: uevent: version 1.0.3
[    2.100488] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
[    2.100563] device-mapper: multipath: version 1.2.0 loaded
[    2.100569] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.100653] EISA: Probing bus 0 at eisa.0
[    2.100658] EISA: Cannot allocate resource for mainboard
[    2.100663] Cannot allocate resource for EISA slot 1
[    2.100667] Cannot allocate resource for EISA slot 2
[    2.100672] Cannot allocate resource for EISA slot 3
[    2.100676] Cannot allocate resource for EISA slot 4
[    2.100681] Cannot allocate resource for EISA slot 5
[    2.100685] Cannot allocate resource for EISA slot 6
[    2.100690] Cannot allocate resource for EISA slot 7
[    2.100694] Cannot allocate resource for EISA slot 8
[    2.100698] EISA: Detected 0 cards.
[    2.100821] cpuidle: using governor ladder
[    2.100905] cpuidle: using governor menu
[    2.101203] TCP cubic registered
[    2.101346] NET: Registered protocol family 10
[    2.101969] NET: Registered protocol family 17
[    2.101988] Registering the dns_resolver key type
[    2.103175] Using IPI No-Shortcut mode
[    2.103277] PM: Hibernation image not present or could not be loaded.
[    2.103289] registered taskstats version 1
[    2.103629]   Magic number: 0:636:943
[    2.103664] tty tty0: hash matches
[    2.103668] tty console: hash matches
[    2.103766] rtc_cmos 00:08: setting system clock to 2012-02-01 16:56:04 UTC (1328115364)
[    2.103782] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.103787] EDD information not available.
[    2.121982] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    2.372224] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.380342] ata1.00: ATA-8: WDC WD3200BEKT-60F3T1, 12.01A12, max UDMA/100
[    2.380354] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.388352] ata1.00: configured for UDMA/100
[    2.388532] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200BEKT-6 12.0 PQ: 0 ANSI: 5
[    2.388712] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.388715] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    2.388772] sd 0:0:0:0: [sda] Write Protect is off
[    2.388778] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.388834] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.499040]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 sda9 sda10 >
[    2.499798] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.572176] usb 2-6: new high speed USB device using ehci_hcd and address 4
[    2.924173] ata2: failed to resume link (SControl 0)
[    2.935272] ata2: SATA link down (SStatus 4 SControl 0)
[    2.935376] Freeing unused kernel memory: 700k freed
[    2.935645] Write protecting the kernel text: 5192k
[    2.935709] Write protecting the kernel read-only data: 2148k
[    2.960033] usb 6-1: new low speed USB device using uhci_hcd and address 2
[    2.962508] <30>udev[78]: starting version 167
[    3.102672] [drm] Initialized drm 1.1.0 20060810
[    3.109905] sky2: driver version 1.28
[    3.109952] sky2 0000:84:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.109970] sky2 0000:84:00.0: setting latency timer to 64
[    3.110003] sky2 0000:84:00.0: Yukon-2 Extreme chip revision 2
[    3.110140] sky2 0000:84:00.0: irq 44 for MSI/MSI-X
[    3.115378] sky2 0000:84:00.0: eth0: addr 18:a9:05:d2:cc:1c
[    3.141002] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.141015] i915 0000:00:02.0: setting latency timer to 64
[    3.176343] i915 0000:00:02.0: irq 45 for MSI/MSI-X
[    3.176350] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    3.176357] [drm] Driver supports precise vblank timestamp query.
[    3.195927] input: USB LaserStream(TM) Mouse as /devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1:1.0/input/input4
[    3.196089] generic-usb 0003:192F:0716.0001: input,hidraw0: USB HID v1.11 Mouse [USB LaserStream(TM) Mouse] on usb-0000:00:1d.0-1/input0
[    3.196116] usbcore: registered new interface driver usbhid
[    3.196120] usbhid: USB HID core driver
[    3.263543] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    3.376020] usb 6-2: new full speed USB device using uhci_hcd and address 3
[    3.556461] hub 6-2:1.0: USB hub found
[    3.558416] hub 6-2:1.0: 4 ports detected
[    3.732098] Console: switching to colour frame buffer device 170x48
[    3.736048] fb0: inteldrmfb frame buffer device
[    3.736100] drm: registered panic notifier
[    3.752751] acpi device:09: registered as cooling_device15
[    3.753204] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input5
[    3.753358] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    3.753749] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    3.783292] vesafb: framebuffer at 0x80000000, mapped to 0xf9000000, using 3072k, total 3072k
[    3.783354] vesafb: mode is 1024x768x32, linelength=4096, pages=0
[    3.783393] vesafb: scrolling: redraw
[    3.783420] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    3.783531] fb1: VESA VGA frame buffer device
[    4.155931] Btrfs loaded
[    4.162905] xor: automatically using best checksumming function: pIII_sse
[    4.180010]    pIII_sse  :  8328.000 MB/sec
[    4.180044] xor: using function: pIII_sse (8328.000 MB/sec)
[    4.182726] device-mapper: dm-raid45: initialized v0.2594b
[    4.466718] EXT4-fs (sda9): mounted filesystem with ordered data mode. Opts: (null)
[   18.657798] <30>udev[385]: starting version 167
[   18.678911] lp: driver loaded but no devices found
[   18.849899] hp_accel: laptop model unknown, using default axes configuration
[   18.850539] lis3lv02d: 8 bits sensor found
[   18.924154] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input6
[   18.924329] Registered led device: hp::hddprotect
[   18.924356] hp_accel: driver loaded
[   18.946311] EXT4-fs (sda9): re-mounted. Opts: errors=remount-ro
[   19.260653] EXT4-fs (sda8): mounted filesystem with ordered data mode. Opts: (null)
[   19.492208] input: HP WMI hotkeys as /devices/virtual/input/input7
[   19.554530] cfg80211: Calling CRDA to update world regulatory domain
[   19.590795] cfg80211: World regulatory domain updated:
[   19.590800] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   19.590803] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.590805] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   19.590809] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   19.590811] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.590814] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.612382] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   19.612386] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   19.612388] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   19.612391] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   19.612393] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   19.612396] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   19.612398] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   19.612401] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   19.612403] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   19.612406] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   19.612408] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   19.612411] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   19.612413] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   19.612416] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   19.612418] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   19.612421] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   19.612423] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   19.612426] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   19.612429] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   19.612431] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   19.612434] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   19.612436] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   19.612439] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   19.612441] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[   19.612444] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   19.612446] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[   19.612449] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   19.612451] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[   19.618380] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   19.619138] Registered led device: rt2800usb-phy0::radio
[   19.619170] Registered led device: rt2800usb-phy0::assoc
[   19.619196] Registered led device: rt2800usb-phy0::quality
[   19.619487] usbcore: registered new interface driver rt2800usb
[   19.620448] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   19.626317] rtusb init --->
[   19.626403] usbcore: registered new interface driver rt2870
[   19.672584] <30>udev[394]: renamed network interface wlan0 to wlan1
[   19.704735] sky2 0000:84:00.0: eth0: enabling interface
[   19.705003] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.836116] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04733/0xa40000/0xa0000
[   19.876500] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8
[   20.091415] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[   20.091426] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[   20.091437] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   20.091528] HDA Intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   20.091561] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   20.102842] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   21.106747] cfg80211: Found new beacon on frequency: 2467 MHz (Ch 12) on phy0
[   21.342148] ppdev: user-space parallel port driver
[   21.412529] HP WMI: Unknown event_id - 0 - 0x0
[   21.696363] Intel AES-NI instructions are not detected.
[   21.710084] padlock_aes: VIA PadLock not detected.
[   21.733776] padlock_sha: VIA PadLock Hash Engine not detected.
[   22.478607] Adding 4586520k swap on /dev/mapper/cryptswap1.  Priority:-1 extents:1 across:4586520k 
[   23.715398] vboxdrv: Found 2 processor cores.
[   23.715523] vboxdrv: fAsync=0 offMin=0x1ae offMax=0x1684
[   23.715603] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   23.715606] vboxdrv: Successfully loaded version 4.0.6 (interface 0x00180000).
[   27.002714] EXT4-fs (sda9): re-mounted. Opts: errors=remount-ro,commit=0
[   27.007536] EXT4-fs (sda8): re-mounted. Opts: commit=0
[   27.044638] ata2: exception Emask 0x10 SAct 0x0 SErr 0x4050000 action 0xf
[   27.044644] ata2: SError: { PHYRdyChg CommWake DevExch }
[   27.044657] ata2: hard resetting link
[   28.072041] ata2: failed to resume link (SControl 0)
[   28.083055] ata2: SATA link down (SStatus 4 SControl 0)
[   28.083083] ata2: EH complete
[  983.385666] usb 2-6: USB disconnect, address 4
[  985.636268] usb 2-6: new high speed USB device using ehci_hcd and address 5
[  985.803605] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  985.803613] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  985.803617] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  985.803622] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  985.803627] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  985.803631] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  985.803636] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  985.803640] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  985.803645] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  985.803649] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  985.803653] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  985.803658] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  985.803662] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  985.803667] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  985.803671] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  985.803676] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  985.803680] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  985.803685] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  985.803689] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  985.803694] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  985.803698] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  985.803703] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  985.803707] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  985.803711] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[  985.803716] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  985.803720] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[  985.803725] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[  985.803729] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[  985.803909] ieee80211 phy1: Selected rate control algorithm 'minstrel_ht'
[  985.806068] Registered led device: rt2800usb-phy1::radio
[  985.806118] Registered led device: rt2800usb-phy1::assoc
[  985.806167] Registered led device: rt2800usb-phy1::quality
[  985.869371] <30>udev[555]: renamed network interface wlan0 to wlan1
[  986.303879] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 1101.380214] ecryptfs_parse_options: eCryptfs: unrecognized option [ecryptfs_check_dev_ruid]
[ 1110.279102] Valid eCryptfs headers not found in file header region or xattr region
[ 1110.279108] Either the lower file is not in a valid eCryptfs format, or the key could not be retrieved. Plaintext passthrough mode is not enabled; returning -EIO
[ 1120.374715] usb 2-6: USB disconnect, address 5
[ 1120.700037] usb 2-6: new high speed USB device using ehci_hcd and address 6
[ 1120.866350] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 1120.866355] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1120.866358] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 1120.866360] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1120.866363] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 1120.866366] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1120.866368] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 1120.866371] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1120.866373] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 1120.866376] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1120.866378] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 1120.866381] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1120.866384] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 1120.866386] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1120.866389] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 1120.866391] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1120.866394] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 1120.866396] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1120.866399] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 1120.866402] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1120.866404] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 1120.866407] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1120.866409] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[ 1120.866412] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1120.866414] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[ 1120.866417] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1120.866419] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[ 1120.866422] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1120.866541] ieee80211 phy2: Selected rate control algorithm 'minstrel_ht'
[ 1120.867352] Registered led device: rt2800usb-phy2::radio
[ 1120.867386] Registered led device: rt2800usb-phy2::assoc
[ 1120.867413] Registered led device: rt2800usb-phy2::quality
[ 1120.908911] <30>udev[3002]: renamed network interface wlan0 to wlan1
[ 1121.243857] usb 2-6: USB disconnect, address 6
[ 1121.572040] usb 2-6: new high speed USB device using ehci_hcd and address 7
[ 1121.741100] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 1121.741104] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1121.741107] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 1121.741110] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1121.741112] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 1121.741115] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1121.741117] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 1121.741120] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1121.741122] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 1121.741125] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1121.741127] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 1121.741130] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1121.741132] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 1121.741135] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1121.741138] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 1121.741140] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1121.741143] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 1121.741145] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1121.741148] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 1121.741151] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1121.741153] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 1121.741156] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1121.741158] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[ 1121.741161] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1121.741163] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[ 1121.741166] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1121.741168] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[ 1121.741171] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1121.741290] ieee80211 phy3: Selected rate control algorithm 'minstrel_ht'
[ 1121.742055] Registered led device: rt2800usb-phy3::radio
[ 1121.742085] Registered led device: rt2800usb-phy3::assoc
[ 1121.742113] Registered led device: rt2800usb-phy3::quality
[ 1121.792814] <30>udev[3002]: renamed network interface wlan0 to wlan1
[ 1122.083388] usb 2-6: USB disconnect, address 7
[ 1125.688285] usb 2-6: new high speed USB device using ehci_hcd and address 8
[ 1125.869478] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 1125.869484] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1125.869486] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 1125.869489] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1125.869491] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 1125.869494] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1125.869496] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 1125.869499] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1125.869502] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 1125.869504] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1125.869507] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 1125.869509] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1125.869512] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 1125.869514] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1125.869517] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 1125.869519] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1125.869522] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 1125.869524] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1125.869527] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 1125.869529] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1125.869532] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 1125.869535] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1125.869537] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[ 1125.869540] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1125.869542] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[ 1125.869545] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1125.869547] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[ 1125.869550] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1125.869681] ieee80211 phy4: Selected rate control algorithm 'minstrel_ht'
[ 1125.870574] Registered led device: rt2800usb-phy4::radio
[ 1125.870604] Registered led device: rt2800usb-phy4::assoc
[ 1125.870631] Registered led device: rt2800usb-phy4::quality
[ 1125.915741] usb 2-6: USB disconnect, address 8
[ 1125.921053] <30>udev[3538]: renamed network interface wlan0 to wlan1
[ 1126.240271] usb 2-6: new high speed USB device using ehci_hcd and address 9
[ 1126.407509] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 1126.407516] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1126.407520] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 1126.407525] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1126.407529] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 1126.407535] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1126.407539] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 1126.407544] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1126.407548] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 1126.407553] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1126.407557] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 1126.407562] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1126.407566] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 1126.407570] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1126.407575] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 1126.407579] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1126.407583] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 1126.407588] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1126.407592] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 1126.407597] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1126.407601] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 1126.407606] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1126.407610] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[ 1126.407615] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1126.407619] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[ 1126.407623] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1126.407628] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[ 1126.407632] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1126.407843] ieee80211 phy5: Selected rate control algorithm 'minstrel_ht'
[ 1126.409502] Registered led device: rt2800usb-phy5::radio
[ 1126.409551] Registered led device: rt2800usb-phy5::assoc
[ 1126.409600] Registered led device: rt2800usb-phy5::quality
[ 1126.473690] <30>udev[3538]: renamed network interface wlan0 to wlan1
[ 1126.895769] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 1131.297101] hub 2-0:1.0: port 6 disabled by hub (EMI?), re-enabling...
[ 1131.297108] usb 2-6: USB disconnect, address 9
[ 1131.664068] usb 2-6: new high speed USB device using ehci_hcd and address 10
[ 1131.836626] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 1131.836633] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1131.836637] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 1131.836642] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1131.836646] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 1131.836651] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1131.836655] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 1131.836660] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1131.836664] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 1131.836669] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1131.836673] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 1131.836677] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1131.836682] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 1131.836686] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1131.836690] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 1131.836695] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1131.836699] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 1131.836704] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1131.836708] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 1131.836713] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1131.836717] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 1131.836722] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1131.836726] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[ 1131.836731] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1131.836735] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[ 1131.836739] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1131.836744] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[ 1131.836748] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1131.837065] ieee80211 phy6: Selected rate control algorithm 'minstrel_ht'
[ 1131.839466] Registered led device: rt2800usb-phy6::radio
[ 1131.839513] Registered led device: rt2800usb-phy6::assoc
[ 1131.839557] Registered led device: rt2800usb-phy6::quality
[ 1131.897126] <30>udev[3538]: renamed network interface wlan0 to wlan1
[ 1132.413491] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 1138.829000] ecryptfs_parse_options: eCryptfs: unrecognized option [ecryptfs_check_dev_ruid]
[ 1141.213168] Valid eCryptfs headers not found in file header region or xattr region
[ 1141.213172] Either the lower file is not in a valid eCryptfs format, or the key could not be retrieved. Plaintext passthrough mode is not enabled; returning -EIO
[ 1157.965203] wlan1: authenticate with 00:1e:58:34:5b:b3 (try 1)
[ 1157.966696] wlan1: authenticated
[ 1157.966730] wlan1: associate with 00:1e:58:34:5b:b3 (try 1)
[ 1157.970339] wlan1: RX AssocResp from 00:1e:58:34:5b:b3 (capab=0x431 status=0 aid=1)
[ 1157.970344] wlan1: associated
[ 1157.981856] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[ 1157.983333] cfg80211: Calling CRDA for country: NA
[ 1168.176010] wlan1: no IPv6 routers present
[ 1206.586851] exe (4803): /proc/4803/oom_adj is deprecated, please use /proc/4803/oom_score_adj instead.
[ 2353.806515] usb 2-6: USB disconnect, address 10
[ 2353.820756] wlan1: deauthenticating from 00:1e:58:34:5b:b3 by local choice (reason=3)
[ 2353.844236] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 2353.844244] cfg80211: Restoring regulatory settings
[ 2353.844252] cfg80211: Calling CRDA to update world regulatory domain
[ 2353.851043] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 2353.851050] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 2353.851055] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 2353.851060] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 2353.851064] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 2353.851069] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 2353.851073] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 2353.851078] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 2353.851082] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 2353.851086] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 2353.851090] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 2353.851095] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 2353.851099] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 2353.851104] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 2353.851108] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 2353.851112] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 2353.851117] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 2353.851121] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 2353.851125] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 2353.851130] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 2353.851134] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 2353.851138] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 2353.851143] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[ 2353.851147] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 2353.851151] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[ 2353.851156] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 2353.851160] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[ 2353.851165] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 2353.851170] cfg80211: World regulatory domain updated:
[ 2353.851173] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2353.851178] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2353.851183] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2353.851187] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2353.851192] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2353.851196] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2354.180098] usb 2-6: new high speed USB device using ehci_hcd and address 11
[ 2354.354311] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 2354.354315] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 2354.354317] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 2354.354320] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 2354.354322] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 2354.354325] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 2354.354328] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 2354.354330] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 2354.354333] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 2354.354335] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 2354.354338] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 2354.354340] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 2354.354343] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 2354.354345] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 2354.354348] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 2354.354351] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 2354.354353] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 2354.354356] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 2354.354358] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 2354.354361] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 2354.354363] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 2354.354366] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 2354.354368] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[ 2354.354371] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 2354.354373] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[ 2354.354376] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 2354.354378] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[ 2354.354381] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 2354.354523] ieee80211 phy7: Selected rate control algorithm 'minstrel_ht'
[ 2354.355470] Registered led device: rt2800usb-phy7::radio
[ 2354.355503] Registered led device: rt2800usb-phy7::assoc
[ 2354.355533] Registered led device: rt2800usb-phy7::quality
[ 2354.405078] <30>udev[3799]: renamed network interface wlan0 to wlan1
[ 2354.845974] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 2358.446881] usb 2-6: USB disconnect, address 11
[ 2360.236261] sky2 0000:84:00.0: eth0: disabling interface
[ 2360.245977] sky2 0000:84:00.0: eth0: enabling interface
[ 2360.246358] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2360.428046] usb 2-6: new high speed USB device using ehci_hcd and address 12
[ 2360.605340] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 2360.605347] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 2360.605351] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 2360.605357] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 2360.605361] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 2360.605365] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 2360.605370] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 2360.605375] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 2360.605379] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 2360.605383] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 2360.605388] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 2360.605392] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 2360.605396] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 2360.605401] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 2360.605405] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 2360.605410] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 2360.605414] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 2360.605419] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 2360.605423] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 2360.605428] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 2360.605432] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 2360.605436] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 2360.605441] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[ 2360.605445] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 2360.605450] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[ 2360.605454] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 2360.605459] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[ 2360.605463] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 2360.605640] ieee80211 phy8: Selected rate control algorithm 'minstrel_ht'
[ 2360.607448] Registered led device: rt2800usb-phy8::radio
[ 2360.607505] Registered led device: rt2800usb-phy8::assoc
[ 2360.607559] Registered led device: rt2800usb-phy8::quality
[ 2360.657082] <30>udev[6767]: renamed network interface wlan0 to wlan1
[ 2361.214585] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 2376.631255] wlan1: authenticate with 00:1e:58:34:5b:b3 (try 1)
[ 2376.632779] wlan1: authenticated
[ 2378.243014] wlan1: associate with 00:1e:58:34:5b:b3 (try 1)
[ 2378.245291] wlan1: RX AssocResp from 00:1e:58:34:5b:b3 (capab=0x431 status=0 aid=1)
[ 2378.245297] wlan1: associated
[ 2378.257484] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[ 2378.258725] cfg80211: Calling CRDA for country: NA
[ 2389.072253] wlan1: no IPv6 routers present
[ 2534.735188] cfg80211: Found new beacon on frequency: 2467 MHz (Ch 12) on phy8
[ 2534.735214] cfg80211: Pending regulatory request, waiting for it to be processed...
[16031.391421] ardour-2.8.11[24087]: segfault at b73bccf8 ip 006546f0 sp bff88dd0 error 4 in libpthread-2.13.so[649000+15000]
[16075.481726] render error detected, EIR: 0x00000010
[16075.481733]   IPEIR: 0x00000000
[16075.481737]   IPEHR: 0x00000000
[16075.481741]   INSTDONE: 0xfffffffe
[16075.481744]   INSTPS: 0x0001e000
[16075.481747]   INSTDONE1: 0xffffffff
[16075.481750]   ACTHD: 0x72e0d840
[16075.481753] page table error
[16075.481756]   PGTBL_ER: 0x00000001
[16075.481761] [drm:i915_report_and_clear_eir] *ERROR* EIR stuck: 0x00000010, masking
[16239.485516] ardour-2.8.11[25015]: segfault at b1369cf8 ip 00b096f0 sp bff21f50 error 4 in libpthread-2.13.so[afe000+15000]
[18492.784080] usb 6-1: USB disconnect, address 2
[18507.468109] usb 6-1: new low speed USB device using uhci_hcd and address 4
[18507.662085] input: USB LaserStream(TM) Mouse as /devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1:1.0/input/input9
[18507.662340] generic-usb 0003:192F:0716.0002: input,hidraw0: USB HID v1.11 Mouse [USB LaserStream(TM) Mouse] on usb-0000:00:1d.0-1/input0
[19708.822326] wlan1: deauthenticating from 00:1e:58:34:5b:b3 by local choice (reason=3)
[19710.458332] cfg80211: All devices are disconnected, going to restore regulatory settings
[19710.458340] cfg80211: Restoring regulatory settings
[19710.458350] cfg80211: Calling CRDA to update world regulatory domain
[19710.558359] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[19710.558363] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[19710.558365] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[19710.558368] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[19710.558371] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[19710.558373] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[19710.558376] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[19710.558378] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[19710.558381] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[19710.558383] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[19710.558386] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[19710.558388] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[19710.558391] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[19710.558393] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[19710.558396] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[19710.558398] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[19710.558401] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[19710.558403] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[19710.558406] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[19710.558408] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[19710.558411] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[19710.558413] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[19710.558416] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[19710.558418] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[19710.558421] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[19710.558423] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[19710.558426] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[19710.558428] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[19710.558431] cfg80211: World regulatory domain updated:
[19710.558433] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[19710.558436] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[19710.558439] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[19710.558442] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[19710.558444] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[19710.558447] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[19711.610417] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[19711.820292] sky2 0000:84:00.0: eth0: disabling interface
[19711.829448] sky2 0000:84:00.0: eth0: enabling interface
[19711.829823] ADDRCONF(NETDEV_UP): eth0: link is not ready
[19729.425250] ecryptfs_parse_options: eCryptfs: unrecognized option [ecryptfs_check_dev_ruid]
[19739.388254] Valid eCryptfs headers not found in file header region or xattr region
[19739.388258] Either the lower file is not in a valid eCryptfs format, or the key could not be retrieved. Plaintext passthrough mode is not enabled; returning -EIO
[19761.313207] wlan1: authenticate with 00:1e:58:34:5b:b3 (try 1)
[19761.314594] wlan1: authenticated
[19762.923458] wlan1: associate with 00:1e:58:34:5b:b3 (try 1)
[19762.925964] wlan1: RX AssocResp from 00:1e:58:34:5b:b3 (capab=0x431 status=0 aid=1)
[19762.925968] wlan1: associated
[19762.934151] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[19762.935239] cfg80211: Calling CRDA for country: NA
[19773.704047] wlan1: no IPv6 routers present
```

Just wondering if there's anything clearly wrong here so that I can try to avoid this in the future. Thank you.

---

### Post by lordjj on 2012-02-04
This seems to be happening more frequently now. It's already happened 3 times today. Every time I was launching some application (something different each time). It's very annoying, I don't know what could be causing it.

Here's today's Xorg.0.log
```
[ 13487.442] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[ 13487.442] X Protocol Version 11, Revision 0
[ 13487.442] Build Operating System: Linux 2.6.24-28-server i686 Ubuntu
[ 13487.442] Current Operating System: Linux probook 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686
[ 13487.442] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=846c2273-e3f1-4e5d-b501-6ea7513a99b1 ro vga=792
[ 13487.442] Build Date: 13 October 2011  05:38:22PM
[ 13487.442] xorg-server 2:1.10.1-1ubuntu1.3 (For technical support please see http://www.ubuntu.com/support) 
[ 13487.442] Current version of pixman: 0.20.2
[ 13487.442] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[ 13487.442] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[ 13487.443] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Feb  4 16:02:00 2012
[ 13487.443] (==) Using config file: "/etc/X11/xorg.conf"
[ 13487.443] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[ 13487.443] (==) ServerLayout "X.org Configured"
[ 13487.443] (**) |-->Screen "Screen0" (0)
[ 13487.443] (**) |   |-->Monitor "Monitor0"
[ 13487.443] (**) |   |-->Device "Card0"
[ 13487.443] (**) |-->Screen "Screen1" (1)
[ 13487.443] (**) |   |-->Monitor "Monitor1"
[ 13487.449] (**) |   |-->Device "Card1"
[ 13487.449] (**) |-->Screen "Screen2" (2)
[ 13487.449] (**) |   |-->Monitor "Monitor2"
[ 13487.449] (**) |   |-->Device "Card2"
[ 13487.449] (**) |-->Input Device "Mouse0"
[ 13487.449] (**) |-->Input Device "Keyboard0"
[ 13487.449] (==) Automatically adding devices
[ 13487.449] (==) Automatically enabling devices
[ 13487.450] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[ 13487.450] 	Entry deleted from font path.
[ 13487.450] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[ 13487.450] 	Entry deleted from font path.
[ 13487.450] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[ 13487.450] 	Entry deleted from font path.
[ 13487.450] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[ 13487.450] 	Entry deleted from font path.
[ 13487.450] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[ 13487.450] 	Entry deleted from font path.
[ 13487.450] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[ 13487.450] 	Entry deleted from font path.
[ 13487.450] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[ 13487.450] 	Entry deleted from font path.
[ 13487.450] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[ 13487.450] 	Entry deleted from font path.
[ 13487.450] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[ 13487.450] 	Entry deleted from font path.
[ 13487.450] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[ 13487.450] 	Entry deleted from font path.
[ 13487.450] (**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[ 13487.450] (**) ModulePath set to "/usr/lib/xorg/modules"
[ 13487.450] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[ 13487.450] (WW) Disabling Mouse0
[ 13487.450] (WW) Disabling Keyboard0
[ 13487.450] (II) Loader magic: 0x8200ac0
[ 13487.450] (II) Module ABI versions:
[ 13487.450] 	X.Org ANSI C Emulation: 0.4
[ 13487.450] 	X.Org Video Driver: 10.0
[ 13487.450] 	X.Org XInput driver : 12.3
[ 13487.450] 	X.Org Server Extension : 5.0
[ 13487.452] (--) PCI:*(0:0:2:0) 8086:2a42:103c:3072 rev 7, Mem @ 0x90000000/4194304, 0x80000000/268435456, I/O @ 0x00007120/8
[ 13487.452] (--) PCI: (0:0:2:1) 8086:2a43:103c:3072 rev 7, Mem @ 0x90400000/1048576
[ 13487.452] (II) Open ACPI successful (/var/run/acpid.socket)
[ 13487.452] (II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
[ 13487.452] (II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
[ 13487.452] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[ 13487.452] (II) "record" will be loaded. This was enabled by default and also specified in the config file.
[ 13487.452] (II) "dri" will be loaded. This was enabled by default and also specified in the config file.
[ 13487.452] (II) "dri2" will be loaded. This was enabled by default and also specified in the config file.
[ 13487.452] (II) LoadModule: "dri2"
[ 13487.452] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[ 13487.453] (II) Module dri2: vendor="X.Org Foundation"
[ 13487.453] 	compiled for 1.10.1, module version = 1.2.0
[ 13487.453] 	ABI class: X.Org Server Extension, version 5.0
[ 13487.453] (II) Loading extension DRI2
[ 13487.453] (II) LoadModule: "record"
[ 13487.453] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[ 13487.453] (II) Module record: vendor="X.Org Foundation"
[ 13487.453] 	compiled for 1.10.1, module version = 1.13.0
[ 13487.453] 	Module class: X.Org Server Extension
[ 13487.453] 	ABI class: X.Org Server Extension, version 5.0
[ 13487.453] (II) Loading extension RECORD
[ 13487.453] (II) LoadModule: "glx"
[ 13487.453] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[ 13487.453] (II) Module glx: vendor="X.Org Foundation"
[ 13487.453] 	compiled for 1.10.1, module version = 1.0.0
[ 13487.453] 	ABI class: X.Org Server Extension, version 5.0
[ 13487.453] (==) AIGLX enabled
[ 13487.453] (II) Loading extension GLX
[ 13487.453] (II) LoadModule: "dri"
[ 13487.453] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[ 13487.453] (II) Module dri: vendor="X.Org Foundation"
[ 13487.453] 	compiled for 1.10.1, module version = 1.0.0
[ 13487.453] 	ABI class: X.Org Server Extension, version 5.0
[ 13487.453] (II) Loading extension XFree86-DRI
[ 13487.453] (II) LoadModule: "dbe"
[ 13487.454] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[ 13487.454] (II) Module dbe: vendor="X.Org Foundation"
[ 13487.454] 	compiled for 1.10.1, module version = 1.0.0
[ 13487.454] 	Module class: X.Org Server Extension
[ 13487.454] 	ABI class: X.Org Server Extension, version 5.0
[ 13487.454] (II) Loading extension DOUBLE-BUFFER
[ 13487.454] (II) LoadModule: "extmod"
[ 13487.454] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[ 13487.454] (II) Module extmod: vendor="X.Org Foundation"
[ 13487.454] 	compiled for 1.10.1, module version = 1.0.0
[ 13487.454] 	Module class: X.Org Server Extension
[ 13487.454] 	ABI class: X.Org Server Extension, version 5.0
[ 13487.454] (II) Loading extension MIT-SCREEN-SAVER
[ 13487.454] (II) Loading extension XFree86-VidModeExtension
[ 13487.454] (II) Loading extension XFree86-DGA
[ 13487.454] (II) Loading extension DPMS
[ 13487.454] (II) Loading extension XVideo
[ 13487.454] (II) Loading extension XVideo-MotionCompensation
[ 13487.454] (II) Loading extension X-Resource
[ 13487.454] (II) LoadModule: "intel"
[ 13487.454] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[ 13487.455] (II) Module intel: vendor="X.Org Foundation"
[ 13487.455] 	compiled for 1.10.1, module version = 2.14.0
[ 13487.455] 	Module class: X.Org Video Driver
[ 13487.455] 	ABI class: X.Org Video Driver, version 10.0
[ 13487.455] (II) LoadModule: "fbdev"
[ 13487.455] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[ 13487.455] (II) Module fbdev: vendor="X.Org Foundation"
[ 13487.455] 	compiled for 1.10.0, module version = 0.4.2
[ 13487.455] 	ABI class: X.Org Video Driver, version 10.0
[ 13487.455] (II) LoadModule: "vesa"
[ 13487.455] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[ 13487.455] (II) Module vesa: vendor="X.Org Foundation"
[ 13487.455] 	compiled for 1.10.0, module version = 2.3.0
[ 13487.455] 	Module class: X.Org Video Driver
[ 13487.455] 	ABI class: X.Org Video Driver, version 10.0
[ 13487.455] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
	Sandybridge, Sandybridge
[ 13487.456] (II) FBDEV: driver for framebuffer: fbdev
[ 13487.456] (II) VESA: driver for VESA chipsets: vesa
[ 13487.456] (--) using VT number 8

[ 13487.463] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[ 13487.463] (WW) Falling back to old probe method for fbdev
[ 13487.463] (II) Loading sub module "fbdevhw"
[ 13487.463] (II) LoadModule: "fbdevhw"
[ 13487.463] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[ 13487.463] (II) Module fbdevhw: vendor="X.Org Foundation"
[ 13487.464] 	compiled for 1.10.1, module version = 0.0.2
[ 13487.464] 	ABI class: X.Org Video Driver, version 10.0
[ 13487.464] (WW) Falling back to old probe method for vesa
[ 13487.464] drmOpenDevice: node name is /dev/dri/card0
[ 13487.464] drmOpenDevice: open result is 9, (OK)
[ 13487.464] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[ 13487.464] drmOpenDevice: node name is /dev/dri/card0
[ 13487.464] drmOpenDevice: open result is 9, (OK)
[ 13487.464] drmOpenByBusid: drmOpenMinor returns 9
[ 13487.464] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[ 13487.464] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[ 13487.464] (==) intel(0): RGB weight 888
[ 13487.464] (==) intel(0): Default visual is TrueColor
[ 13487.464] (II) intel(0): Integrated Graphics Chipset: Intel(R) GM45
[ 13487.464] (--) intel(0): Chipset: "GM45"
[ 13487.464] (**) intel(0): Relaxed fencing enabled
[ 13487.464] (**) intel(0): Tiling enabled
[ 13487.464] (**) intel(0): SwapBuffers wait enabled
[ 13487.464] (==) intel(0): video overlay key set to 0x101fe
[ 13487.464] (II) intel(0): Output LVDS1 using monitor section Monitor0
[ 13487.464] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
[ 13487.480] (II) intel(0): Output VGA1 has no monitor section
[ 13487.484] (II) intel(0): Output HDMI1 has no monitor section
[ 13487.484] (II) intel(0): Output DP1 has no monitor section
[ 13487.485] (II) intel(0): Output DP2 has no monitor section
[ 13487.632] (II) intel(0): Output TV1 has no monitor section
[ 13487.632] (II) intel(0): EDID for output LVDS1
[ 13487.632] (II) intel(0): Manufacturer: CMO  Model: 1571  Serial#: 0
[ 13487.632] (II) intel(0): Year: 2008  Week: 36
[ 13487.632] (II) intel(0): EDID Version: 1.3
[ 13487.632] (II) intel(0): Digital Display Input
[ 13487.632] (II) intel(0): Max Image Size [cm]: horiz.: 35  vert.: 19
[ 13487.632] (II) intel(0): Gamma: 2.20
[ 13487.632] (II) intel(0): No DPMS capabilities specified
[ 13487.632] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[ 13487.632] (II) intel(0): First detailed timing is preferred mode
[ 13487.632] (II) intel(0): redX: 0.602 redY: 0.340   greenX: 0.306 greenY: 0.530
[ 13487.632] (II) intel(0): blueX: 0.151 blueY: 0.120   whiteX: 0.313 whiteY: 0.329
[ 13487.632] (II) intel(0): Manufacturer's mask: 0
[ 13487.632] (II) intel(0): Supported detailed timing:
[ 13487.632] (II) intel(0): clock: 69.3 MHz   Image Size:  344 x 193 mm
[ 13487.632] (II) intel(0): h_active: 1366  h_sync: 1382  h_sync_end 1416 h_blank_end 1466 h_border: 0
[ 13487.632] (II) intel(0): v_active: 768  v_sync: 770  v_sync_end 776 v_blanking: 788 v_border: 0
[ 13487.632] (II) intel(0):  N156B6-L04
[ 13487.632] (II) intel(0):  CMO
[ 13487.632] (II) intel(0):  N156B6-L04
[ 13487.632] (II) intel(0): EDID (in hex):
[ 13487.632] (II) intel(0): 	00ffffffffffff000daf711500000000
[ 13487.632] (II) intel(0): 	24120103802313780a07f59a574e8726
[ 13487.632] (II) intel(0): 	1e505400000001010101010101010101
[ 13487.632] (II) intel(0): 	010101010101121b5664500014301022
[ 13487.632] (II) intel(0): 	260058c110000018000000fe004e3135
[ 13487.632] (II) intel(0): 	3642362d4c30340a2020000000fe0043
[ 13487.632] (II) intel(0): 	4d4f0a202020202020202020000000fe
[ 13487.632] (II) intel(0): 	004e31353642362d4c30340a2020006f
[ 13487.632] (II) intel(0): EDID vendor "CMO", prod id 5489
[ 13487.632] (II) intel(0): Printing DDC gathered Modelines:
[ 13487.632] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1382 1416 1466  768 770 776 788 -hsync -vsync (47.3 kHz)
[ 13487.632] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[ 13487.632] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[ 13487.633] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[ 13487.633] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[ 13487.633] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[ 13487.633] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[ 13487.633] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[ 13487.633] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[ 13487.633] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[ 13487.633] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[ 13487.633] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[ 13487.633] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[ 13487.633] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[ 13487.633] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[ 13487.633] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[ 13487.633] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[ 13487.633] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[ 13487.633] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[ 13487.633] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[ 13487.633] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[ 13487.633] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[ 13487.633] (II) intel(0): Printing probed modes for output LVDS1
[ 13487.633] (II) intel(0): Modeline "1366x768"x60.0   69.30  1366 1382 1416 1466  768 770 776 788 -hsync -vsync (47.3 kHz)
[ 13487.633] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[ 13487.633] (II) intel(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz)
[ 13487.633] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[ 13487.633] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[ 13487.633] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[ 13487.633] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[ 13487.648] (II) intel(0): EDID for output VGA1
[ 13487.652] (II) intel(0): EDID for output HDMI1
[ 13487.652] (II) intel(0): EDID for output DP1
[ 13487.653] (II) intel(0): EDID for output DP2
[ 13487.812] (II) intel(0): EDID for output TV1
[ 13487.812] (II) intel(0): Output LVDS1 connected
[ 13487.812] (II) intel(0): Output VGA1 disconnected
[ 13487.812] (II) intel(0): Output HDMI1 disconnected
[ 13487.812] (II) intel(0): Output DP1 disconnected
[ 13487.812] (II) intel(0): Output DP2 disconnected
[ 13487.812] (II) intel(0): Output TV1 disconnected
[ 13487.812] (II) intel(0): Using exact sizes for initial modes
[ 13487.812] (II) intel(0): Output LVDS1 using initial mode 1366x768
[ 13487.812] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[ 13487.812] (II) intel(0): Kernel page flipping support detected, enabling
[ 13487.812] (**) intel(0): Display dimensions: (350, 190) mm
[ 13487.812] (**) intel(0): DPI set to (99, 102)
[ 13487.812] (II) Loading sub module "fb"
[ 13487.812] (II) LoadModule: "fb"
[ 13487.812] (II) Loading /usr/lib/xorg/modules/libfb.so
[ 13487.813] (II) Module fb: vendor="X.Org Foundation"
[ 13487.813] 	compiled for 1.10.1, module version = 1.0.0
[ 13487.813] 	ABI class: X.Org ANSI C Emulation, version 0.4
[ 13487.813] (II) UnloadModule: "fbdev"
[ 13487.813] (II) Unloading fbdev
[ 13487.813] (II) UnloadModule: "fbdevhw"
[ 13487.813] (II) Unloading fbdevhw
[ 13487.813] (II) UnloadModule: "vesa"
[ 13487.813] (II) Unloading vesa
[ 13487.813] (==) Depth 24 pixmap format is 32 bpp
[ 13487.813] (==) intel(0): VideoRam: 262144 KB
[ 13487.813] (II) intel(0): [DRI2] Setup complete
[ 13487.813] (II) intel(0): [DRI2]   DRI driver: i965
[ 13487.813] (II) intel(0): Allocated new frame buffer 1408x768 stride 5632, tiled
[ 13487.830] (II) UXA(0): Driver registered support for the following operations:
[ 13487.830] (II)         solid
[ 13487.830] (II)         copy
[ 13487.830] (II)         composite (RENDER acceleration)
[ 13487.830] (II)         put_image
[ 13487.830] (II)         get_image
[ 13487.830] (==) intel(0): Backing store disabled
[ 13487.830] (==) intel(0): Silken mouse enabled
[ 13487.830] (II) intel(0): Initializing HW Cursor
[ 13487.856] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[ 13487.858] (==) intel(0): DPMS enabled
[ 13487.858] (==) intel(0): Intel XvMC decoder enabled
[ 13487.858] (II) intel(0): Set up textured video
[ 13487.858] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[ 13487.858] (II) intel(0): direct rendering: DRI2 Enabled
[ 13487.858] (WW) intel(0): Option "ForceEnablePipeA" is not used
[ 13487.858] (WW) intel(0): Option "monitor-TV" is not used
[ 13487.858] (==) intel(0): hotplug detection: "enabled"
[ 13487.858] (--) RandR disabled
[ 13487.858] (II) Initializing built-in extension Generic Event Extension
[ 13487.858] (II) Initializing built-in extension SHAPE
[ 13487.858] (II) Initializing built-in extension MIT-SHM
[ 13487.858] (II) Initializing built-in extension XInputExtension
[ 13487.858] (II) Initializing built-in extension XTEST
[ 13487.858] (II) Initializing built-in extension BIG-REQUESTS
[ 13487.858] (II) Initializing built-in extension SYNC
[ 13487.858] (II) Initializing built-in extension XKEYBOARD
[ 13487.858] (II) Initializing built-in extension XC-MISC
[ 13487.858] (II) Initializing built-in extension SECURITY
[ 13487.858] (II) Initializing built-in extension XINERAMA
[ 13487.859] (II) Initializing built-in extension XFIXES
[ 13487.859] (II) Initializing built-in extension RENDER
[ 13487.859] (II) Initializing built-in extension RANDR
[ 13487.859] (II) Initializing built-in extension COMPOSITE
[ 13487.859] (II) Initializing built-in extension DAMAGE
[ 13487.859] (II) Initializing built-in extension GESTURE
[ 13487.870] (II) AIGLX: Trying DRI driver /usr/lib/dri/i965_dri.so
[ 13487.874] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[ 13487.874] (II) AIGLX: enabled GLX_INTEL_swap_event
[ 13487.874] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[ 13487.874] (II) AIGLX: enabled GLX_SGI_make_current_read
[ 13487.874] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[ 13487.874] (II) AIGLX: Loaded and initialized i965
[ 13487.874] (II) GLX: Initialized DRI2 GL provider for screen 0
[ 13487.875] (II) intel(0): Setting screen physical size to 361 x 203
[ 13487.897] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[ 13487.911] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[ 13487.911] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[ 13487.911] (II) LoadModule: "evdev"
[ 13487.911] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 13487.912] (II) Module evdev: vendor="X.Org Foundation"
[ 13487.912] 	compiled for 1.10.0.902, module version = 2.6.0
[ 13487.912] 	Module class: X.Org XInput Driver
[ 13487.912] 	ABI class: X.Org XInput driver, version 12.3
[ 13487.912] (II) Using input driver 'evdev' for 'Power Button'
[ 13487.912] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 13487.912] (**) Power Button: always reports core events
[ 13487.912] (**) Power Button: Device: "/dev/input/event2"
[ 13487.924] (--) Power Button: Found keys
[ 13487.924] (II) Power Button: Configuring as keyboard
[ 13487.924] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[ 13487.924] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[ 13487.924] (**) Option "xkb_rules" "evdev"
[ 13487.924] (**) Option "xkb_model" "pc105"
[ 13487.924] (**) Option "xkb_layout" "us"
[ 13487.925] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[ 13487.925] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[ 13487.925] (II) Using input driver 'evdev' for 'Video Bus'
[ 13487.925] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 13487.925] (**) Video Bus: always reports core events
[ 13487.925] (**) Video Bus: Device: "/dev/input/event5"
[ 13487.936] (--) Video Bus: Found keys
[ 13487.936] (II) Video Bus: Configuring as keyboard
[ 13487.936] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input5/event5"
[ 13487.936] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[ 13487.936] (**) Option "xkb_rules" "evdev"
[ 13487.936] (**) Option "xkb_model" "pc105"
[ 13487.936] (**) Option "xkb_layout" "us"
[ 13487.942] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[ 13487.942] (II) No input driver/identifier specified (ignoring)
[ 13487.942] (II) config/udev: Adding input device Sleep Button (/dev/input/event0)
[ 13487.942] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[ 13487.942] (II) Using input driver 'evdev' for 'Sleep Button'
[ 13487.943] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 13487.943] (**) Sleep Button: always reports core events
[ 13487.943] (**) Sleep Button: Device: "/dev/input/event0"
[ 13487.956] (--) Sleep Button: Found keys
[ 13487.956] (II) Sleep Button: Configuring as keyboard
[ 13487.956] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input0/event0"
[ 13487.956] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[ 13487.956] (**) Option "xkb_rules" "evdev"
[ 13487.956] (**) Option "xkb_model" "pc105"
[ 13487.956] (**) Option "xkb_layout" "us"
[ 13487.966] (II) config/udev: Adding input device USB LaserStream(TM) Mouse (/dev/input/event4)
[ 13487.966] (**) USB LaserStream(TM) Mouse: Applying InputClass "evdev pointer catchall"
[ 13487.966] (II) Using input driver 'evdev' for 'USB LaserStream(TM) Mouse'
[ 13487.966] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 13487.966] (**) USB LaserStream(TM) Mouse: always reports core events
[ 13487.966] (**) USB LaserStream(TM) Mouse: Device: "/dev/input/event4"
[ 13487.966] (--) USB LaserStream(TM) Mouse: Found 9 mouse buttons
[ 13487.966] (--) USB LaserStream(TM) Mouse: Found scroll wheel(s)
[ 13487.966] (--) USB LaserStream(TM) Mouse: Found relative axes
[ 13487.966] (--) USB LaserStream(TM) Mouse: Found x and y relative axes
[ 13487.966] (II) USB LaserStream(TM) Mouse: Configuring as mouse
[ 13487.966] (II) USB LaserStream(TM) Mouse: Adding scrollwheel support
[ 13487.966] (**) USB LaserStream(TM) Mouse: YAxisMapping: buttons 4 and 5
[ 13487.966] (**) USB LaserStream(TM) Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[ 13487.966] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1:1.0/input/input4/event4"
[ 13487.967] (II) XINPUT: Adding extended input device "USB LaserStream(TM) Mouse" (type: MOUSE)
[ 13487.967] (II) USB LaserStream(TM) Mouse: initialized for relative axes.
[ 13487.967] (**) USB LaserStream(TM) Mouse: (accel) keeping acceleration scheme 1
[ 13487.967] (**) USB LaserStream(TM) Mouse: (accel) acceleration profile 0
[ 13487.967] (**) USB LaserStream(TM) Mouse: (accel) acceleration factor: 2.000
[ 13487.967] (**) USB LaserStream(TM) Mouse: (accel) acceleration threshold: 4
[ 13487.967] (II) config/udev: Adding input device USB LaserStream(TM) Mouse (/dev/input/mouse0)
[ 13487.967] (II) No input driver/identifier specified (ignoring)
[ 13487.973] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[ 13487.973] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[ 13487.973] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[ 13487.973] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 13487.973] (**) AT Translated Set 2 keyboard: always reports core events
[ 13487.973] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[ 13487.973] (--) AT Translated Set 2 keyboard: Found keys
[ 13487.973] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[ 13487.973] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[ 13487.973] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[ 13487.973] (**) Option "xkb_rules" "evdev"
[ 13487.973] (**) Option "xkb_model" "pc105"
[ 13487.973] (**) Option "xkb_layout" "us"
[ 13487.974] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event8)
[ 13487.974] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[ 13487.974] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[ 13487.974] (II) LoadModule: "synaptics"
[ 13487.974] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[ 13487.974] (II) Module synaptics: vendor="X.Org Foundation"
[ 13487.974] 	compiled for 1.10.1, module version = 1.3.99
[ 13487.974] 	Module class: X.Org XInput Driver
[ 13487.974] 	ABI class: X.Org XInput driver, version 12.3
[ 13487.974] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[ 13487.974] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[ 13487.974] (**) SynPS/2 Synaptics TouchPad: always reports core events
[ 13487.974] (**) Option "Device" "/dev/input/event8"
[ 13488.008] (--) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5692
[ 13488.008] (--) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4680
[ 13488.008] (--) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[ 13488.008] (--) SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[ 13488.008] (--) SynPS/2 Synaptics TouchPad: buttons: left right double triple
[ 13488.064] (--) SynPS/2 Synaptics TouchPad: touchpad found
[ 13488.064] (**) SynPS/2 Synaptics TouchPad: always reports core events
[ 13488.116] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio4/input/input8/event8"
[ 13488.116] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[ 13488.116] (**) SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[ 13488.116] (**) SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[ 13488.116] (**) SynPS/2 Synaptics TouchPad: AccelFactor is now 0.037
[ 13488.116] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[ 13488.116] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[ 13488.116] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[ 13488.116] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[ 13488.164] (--) SynPS/2 Synaptics TouchPad: touchpad found
[ 13488.165] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[ 13488.165] (II) No input driver/identifier specified (ignoring)
[ 13488.165] (II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/event6)
[ 13488.165] (II) No input driver/identifier specified (ignoring)
[ 13488.165] (II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/js0)
[ 13488.165] (II) No input driver/identifier specified (ignoring)
[ 13488.172] (II) config/udev: Adding input device HP WMI hotkeys (/dev/input/event7)
[ 13488.173] (**) HP WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[ 13488.173] (II) Using input driver 'evdev' for 'HP WMI hotkeys'
[ 13488.173] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 13488.173] (**) HP WMI hotkeys: always reports core events
[ 13488.173] (**) HP WMI hotkeys: Device: "/dev/input/event7"
[ 13488.188] (--) HP WMI hotkeys: Found keys
[ 13488.189] (II) HP WMI hotkeys: Configuring as keyboard
[ 13488.189] (**) Option "config_info" "udev:/sys/devices/virtual/input/input7/event7"
[ 13488.189] (II) XINPUT: Adding extended input device "HP WMI hotkeys" (type: KEYBOARD)
[ 13488.189] (**) Option "xkb_rules" "evdev"
[ 13488.189] (**) Option "xkb_model" "pc105"
[ 13488.189] (**) Option "xkb_layout" "us"
[ 13488.437] (II) intel(0): EDID vendor "CMO", prod id 5489
[ 13488.437] (II) intel(0): Printing DDC gathered Modelines:
[ 13488.437] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1382 1416 1466  768 770 776 788 -hsync -vsync (47.3 kHz)
[ 13488.626] (II) intel(0): EDID vendor "CMO", prod id 5489
[ 13488.626] (II) intel(0): Printing DDC gathered Modelines:
[ 13488.626] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1382 1416 1466  768 770 776 788 -hsync -vsync (47.3 kHz)
[ 13488.830] (II) intel(0): EDID vendor "CMO", prod id 5489
[ 13488.830] (II) intel(0): Printing DDC gathered Modelines:
[ 13488.830] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1382 1416 1466  768 770 776 788 -hsync -vsync (47.3 kHz)
[ 13489.018] (II) intel(0): EDID vendor "CMO", prod id 5489
[ 13489.018] (II) intel(0): Printing DDC gathered Modelines:
[ 13489.018] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1382 1416 1466  768 770 776 788 -hsync -vsync (47.3 kHz)
[ 13499.298] (II) intel(0): EDID vendor "CMO", prod id 5489
[ 13499.298] (II) intel(0): Printing DDC gathered Modelines:
[ 13499.298] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1382 1416 1466  768 770 776 788 -hsync -vsync (47.3 kHz)
[ 13499.795] (II) intel(0): EDID vendor "CMO", prod id 5489
[ 13499.796] (II) intel(0): Printing DDC gathered Modelines:
[ 13499.796] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1382 1416 1466  768 770 776 788 -hsync -vsync (47.3 kHz)
[ 13500.261] (II) intel(0): EDID vendor "CMO", prod id 5489
[ 13500.261] (II) intel(0): Printing DDC gathered Modelines:
[ 13500.261] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1382 1416 1466  768 770 776 788 -hsync -vsync (47.3 kHz)
[ 13506.578] (II) intel(0): EDID vendor "CMO", prod id 5489
[ 13506.578] (II) intel(0): Printing DDC gathered Modelines:
[ 13506.578] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1382 1416 1466  768 770 776 788 -hsync -vsync (47.3 kHz)
[ 13507.445] (II) intel(0): EDID vendor "CMO", prod id 5489
[ 13507.445] (II) intel(0): Printing DDC gathered Modelines:
[ 13507.445] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1382 1416 1466  768 770 776 788 -hsync -vsync (47.3 kHz)
```

And Xorg.1.log
```
[  4446.683] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[  4446.683] X Protocol Version 11, Revision 0
[  4446.683] Build Operating System: Linux 2.6.24-28-server i686 Ubuntu
[  4446.683] Current Operating System: Linux probook 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686
[  4446.683] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=846c2273-e3f1-4e5d-b501-6ea7513a99b1 ro vga=792 splash quiet splash vt.handoff=7
[  4446.683] Build Date: 13 October 2011  05:38:22PM
[  4446.683] xorg-server 2:1.10.1-1ubuntu1.3 (For technical support please see http://www.ubuntu.com/support) 
[  4446.683] Current version of pixman: 0.20.2
[  4446.683] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[  4446.683] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  4446.683] (==) Log file: "/var/log/Xorg.1.log", Time: Wed Nov 16 11:14:21 2011
[  4446.683] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  4446.684] (==) No Layout section.  Using the first Screen section.
[  4446.684] (==) No screen section available. Using defaults.
[  4446.684] (**) |-->Screen "Default Screen Section" (0)
[  4446.684] (**) |   |-->Monitor "<default monitor>"
[  4446.684] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[  4446.684] (==) Automatically adding devices
[  4446.684] (==) Automatically enabling devices
[  4446.684] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  4446.684] 	Entry deleted from font path.
[  4446.684] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[  4446.684] 	Entry deleted from font path.
[  4446.684] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[  4446.684] 	Entry deleted from font path.
[  4446.684] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[  4446.684] 	Entry deleted from font path.
[  4446.684] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[  4446.684] 	Entry deleted from font path.
[  4446.685] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[  4446.685] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  4446.685] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[  4446.685] (II) Loader magic: 0x8200ac0
[  4446.685] (II) Module ABI versions:
[  4446.685] 	X.Org ANSI C Emulation: 0.4
[  4446.685] 	X.Org Video Driver: 10.0
[  4446.685] 	X.Org XInput driver : 12.3
[  4446.685] 	X.Org Server Extension : 5.0
[  4446.686] (--) PCI:*(0:0:2:0) 8086:2a42:103c:3072 rev 7, Mem @ 0x90000000/4194304, 0x80000000/268435456, I/O @ 0x00007120/8
[  4446.686] (--) PCI: (0:0:2:1) 8086:2a43:103c:3072 rev 7, Mem @ 0x90400000/1048576
[  4446.686] (II) Open ACPI successful (/var/run/acpid.socket)
[  4446.686] (II) LoadModule: "extmod"
[  4446.686] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[  4446.686] (II) Module extmod: vendor="X.Org Foundation"
[  4446.686] 	compiled for 1.10.1, module version = 1.0.0
[  4446.686] 	Module class: X.Org Server Extension
[  4446.686] 	ABI class: X.Org Server Extension, version 5.0
[  4446.686] (II) Loading extension MIT-SCREEN-SAVER
[  4446.686] (II) Loading extension XFree86-VidModeExtension
[  4446.687] (II) Loading extension XFree86-DGA
[  4446.687] (II) Loading extension DPMS
[  4446.687] (II) Loading extension XVideo
[  4446.687] (II) Loading extension XVideo-MotionCompensation
[  4446.687] (II) Loading extension X-Resource
[  4446.687] (II) LoadModule: "dbe"
[  4446.687] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[  4446.687] (II) Module dbe: vendor="X.Org Foundation"
[  4446.687] 	compiled for 1.10.1, module version = 1.0.0
[  4446.687] 	Module class: X.Org Server Extension
[  4446.687] 	ABI class: X.Org Server Extension, version 5.0
[  4446.687] (II) Loading extension DOUBLE-BUFFER
[  4446.687] (II) LoadModule: "glx"
[  4446.687] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[  4446.687] (II) Module glx: vendor="X.Org Foundation"
[  4446.687] 	compiled for 1.10.1, module version = 1.0.0
[  4446.687] 	ABI class: X.Org Server Extension, version 5.0
[  4446.687] (==) AIGLX enabled
[  4446.687] (II) Loading extension GLX
[  4446.687] (II) LoadModule: "record"
[  4446.687] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[  4446.687] (II) Module record: vendor="X.Org Foundation"
[  4446.687] 	compiled for 1.10.1, module version = 1.13.0
[  4446.688] 	Module class: X.Org Server Extension
[  4446.688] 	ABI class: X.Org Server Extension, version 5.0
[  4446.688] (II) Loading extension RECORD
[  4446.688] (II) LoadModule: "dri"
[  4446.688] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[  4446.688] (II) Module dri: vendor="X.Org Foundation"
[  4446.688] 	compiled for 1.10.1, module version = 1.0.0
[  4446.688] 	ABI class: X.Org Server Extension, version 5.0
[  4446.688] (II) Loading extension XFree86-DRI
[  4446.688] (II) LoadModule: "dri2"
[  4446.688] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[  4446.688] (II) Module dri2: vendor="X.Org Foundation"
[  4446.688] 	compiled for 1.10.1, module version = 1.2.0
[  4446.688] 	ABI class: X.Org Server Extension, version 5.0
[  4446.688] (II) Loading extension DRI2
[  4446.688] (==) Matched intel as autoconfigured driver 0
[  4446.688] (==) Matched vesa as autoconfigured driver 1
[  4446.688] (==) Matched fbdev as autoconfigured driver 2
[  4446.688] (==) Assigned the driver to the xf86ConfigLayout
[  4446.688] (II) LoadModule: "intel"
[  4446.689] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[  4446.689] (II) Module intel: vendor="X.Org Foundation"
[  4446.689] 	compiled for 1.10.1, module version = 2.14.0
[  4446.689] 	Module class: X.Org Video Driver
[  4446.689] 	ABI class: X.Org Video Driver, version 10.0
[  4446.689] (II) LoadModule: "vesa"
[  4446.689] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  4446.690] (II) Module vesa: vendor="X.Org Foundation"
[  4446.690] 	compiled for 1.10.0, module version = 2.3.0
[  4446.690] 	Module class: X.Org Video Driver
[  4446.690] 	ABI class: X.Org Video Driver, version 10.0
[  4446.690] (II) LoadModule: "fbdev"
[  4446.690] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  4446.690] (II) Module fbdev: vendor="X.Org Foundation"
[  4446.690] 	compiled for 1.10.0, module version = 0.4.2
[  4446.690] 	ABI class: X.Org Video Driver, version 10.0
[  4446.690] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
	Sandybridge, Sandybridge
[  4446.691] (II) VESA: driver for VESA chipsets: vesa
[  4446.691] (II) FBDEV: driver for framebuffer: fbdev
[  4446.691] (--) using VT number 8

[  4446.844] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[  4446.844] (WW) Falling back to old probe method for vesa
[  4446.844] (WW) Falling back to old probe method for fbdev
[  4446.844] (II) Loading sub module "fbdevhw"
[  4446.844] (II) LoadModule: "fbdevhw"
[  4446.845] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[  4446.845] (II) Module fbdevhw: vendor="X.Org Foundation"
[  4446.845] 	compiled for 1.10.1, module version = 0.0.2
[  4446.845] 	ABI class: X.Org Video Driver, version 10.0
[  4446.845] drmOpenDevice: node name is /dev/dri/card0
[  4446.845] drmOpenDevice: open result is 9, (OK)
[  4446.845] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[  4446.845] drmOpenDevice: node name is /dev/dri/card0
[  4446.845] drmOpenDevice: open result is 9, (OK)
[  4446.845] drmOpenByBusid: drmOpenMinor returns 9
[  4446.845] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[  4446.845] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[  4446.845] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[  4446.845] (==) intel(0): RGB weight 888
[  4446.845] (==) intel(0): Default visual is TrueColor
[  4446.845] (II) intel(0): Integrated Graphics Chipset: Intel(R) GM45
[  4446.845] (--) intel(0): Chipset: "GM45"
[  4446.845] (**) intel(0): Relaxed fencing enabled
[  4446.845] (**) intel(0): Tiling enabled
[  4446.845] (**) intel(0): SwapBuffers wait enabled
[  4446.845] (==) intel(0): video overlay key set to 0x101fe
[  4446.846] (II) intel(0): Output LVDS1 has no monitor section
[  4446.846] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
[  4446.868] (II) intel(0): Output VGA1 has no monitor section
[  4446.874] (II) intel(0): Output HDMI1 has no monitor section
[  4446.874] (II) intel(0): Output DP1 has no monitor section
[  4446.875] (II) intel(0): Output DP2 has no monitor section
[  4446.992] (II) intel(0): Output TV1 has no monitor section
[  4446.992] (II) intel(0): EDID for output LVDS1
[  4446.992] (II) intel(0): Manufacturer: CMO  Model: 1571  Serial#: 0
[  4446.992] (II) intel(0): Year: 2008  Week: 36
[  4446.992] (II) intel(0): EDID Version: 1.3
[  4446.992] (II) intel(0): Digital Display Input
[  4446.992] (II) intel(0): Max Image Size [cm]: horiz.: 35  vert.: 19
[  4446.992] (II) intel(0): Gamma: 2.20
[  4446.992] (II) intel(0): No DPMS capabilities specified
[  4446.992] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[  4446.992] (II) intel(0): First detailed timing is preferred mode
[  4446.992] (II) intel(0): redX: 0.602 redY: 0.340   greenX: 0.306 greenY: 0.530
[  4446.992] (II) intel(0): blueX: 0.151 blueY: 0.120   whiteX: 0.313 whiteY: 0.329
[  4446.992] (II) intel(0): Manufacturer's mask: 0
[  4446.992] (II) intel(0): Supported detailed timing:
[  4446.992] (II) intel(0): clock: 69.3 MHz   Image Size:  344 x 193 mm
[  4446.992] (II) intel(0): h_active: 1366  h_sync: 1382  h_sync_end 1416 h_blank_end 1466 h_border: 0
[  4446.992] (II) intel(0): v_active: 768  v_sync: 770  v_sync_end 776 v_blanking: 788 v_border: 0
[  4446.992] (II) intel(0):  N156B6-L04
[  4446.992] (II) intel(0):  CMO
[  4446.992] (II) intel(0):  N156B6-L04
[  4446.992] (II) intel(0): EDID (in hex):
[  4446.992] (II) intel(0): 	00ffffffffffff000daf711500000000
[  4446.992] (II) intel(0): 	24120103802313780a07f59a574e8726
[  4446.992] (II) intel(0): 	1e505400000001010101010101010101
[  4446.992] (II) intel(0): 	010101010101121b5664500014301022
[  4446.992] (II) intel(0): 	260058c110000018000000fe004e3135
[  4446.992] (II) intel(0): 	3642362d4c30340a2020000000fe0043
[  4446.992] (II) intel(0): 	4d4f0a202020202020202020000000fe
[  4446.992] (II) intel(0): 	004e31353642362d4c30340a2020006f
[  4446.992] (II) intel(0): EDID vendor "CMO", prod id 5489
[  4446.992] (II) intel(0): Printing DDC gathered Modelines:
[  4446.992] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1382 1416 1466  768 770 776 788 -hsync -vsync (47.3 kHz)
[  4446.993] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[  4446.993] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[  4446.993] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[  4446.993] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[  4446.993] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[  4446.993] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[  4446.993] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[  4446.993] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[  4446.993] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[  4446.993] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[  4446.993] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[  4446.993] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[  4446.993] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[  4446.993] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[  4446.993] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[  4446.993] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[  4446.993] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[  4446.993] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[  4446.993] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[  4446.993] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[  4446.993] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[  4446.993] (II) intel(0): Printing probed modes for output LVDS1
[  4446.993] (II) intel(0): Modeline "1366x768"x60.0   69.30  1366 1382 1416 1466  768 770 776 788 -hsync -vsync (47.3 kHz)
[  4446.993] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[  4446.993] (II) intel(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz)
[  4446.993] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  4446.993] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  4446.993] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[  4446.993] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  4447.016] (II) intel(0): EDID for output VGA1
[  4447.020] (II) intel(0): EDID for output HDMI1
[  4447.020] (II) intel(0): EDID for output DP1
[  4447.021] (II) intel(0): EDID for output DP2
[  4447.164] (II) intel(0): EDID for output TV1
[  4447.164] (II) intel(0): Printing probed modes for output TV1
[  4447.164] (II) intel(0): Modeline "848x480"x30.0   14.51  848 849 912 944  480 481 512 513 (15.4 kHz)
[  4447.164] (II) intel(0): Modeline "640x480"x30.0   11.31  640 641 704 736  480 481 512 513 (15.4 kHz)
[  4447.164] (II) intel(0): Modeline "1024x768"x30.0   26.89  1024 1025 1088 1120  768 769 800 801 (24.0 kHz)
[  4447.164] (II) intel(0): Modeline "800x600"x30.0   17.00  800 801 864 896  600 601 632 633 (19.0 kHz)
[  4447.164] (II) intel(0): Output LVDS1 connected
[  4447.164] (II) intel(0): Output VGA1 disconnected
[  4447.164] (II) intel(0): Output HDMI1 disconnected
[  4447.164] (II) intel(0): Output DP1 disconnected
[  4447.164] (II) intel(0): Output DP2 disconnected
[  4447.164] (II) intel(0): Output TV1 connected
[  4447.164] (II) intel(0): Using fuzzy aspect match for initial modes
[  4447.164] (II) intel(0): Output LVDS1 using initial mode 1024x768
[  4447.164] (II) intel(0): Output TV1 using initial mode 1024x768
[  4447.164] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[  4447.164] (II) intel(0): Kernel page flipping support detected, enabling
[  4447.164] (**) intel(0): Display dimensions: (350, 190) mm
[  4447.165] (**) intel(0): DPI set to (74, 102)
[  4447.165] (II) Loading sub module "fb"
[  4447.165] (II) LoadModule: "fb"
[  4447.165] (II) Loading /usr/lib/xorg/modules/libfb.so
[  4447.165] (II) Module fb: vendor="X.Org Foundation"
[  4447.165] 	compiled for 1.10.1, module version = 1.0.0
[  4447.165] 	ABI class: X.Org ANSI C Emulation, version 0.4
[  4447.165] (II) UnloadModule: "vesa"
[  4447.165] (II) Unloading vesa
[  4447.165] (II) UnloadModule: "fbdev"
[  4447.166] (II) Unloading fbdev
[  4447.166] (II) UnloadModule: "fbdevhw"
[  4447.166] (II) Unloading fbdevhw
[  4447.166] (==) Depth 24 pixmap format is 32 bpp
[  4447.166] (==) intel(0): VideoRam: 262144 KB
[  4447.166] (II) intel(0): [DRI2] Setup complete
[  4447.166] (II) intel(0): [DRI2]   DRI driver: i965
[  4447.166] (II) intel(0): Allocated new frame buffer 1024x768 stride 4096, tiled
[  4447.187] (II) UXA(0): Driver registered support for the following operations:
[  4447.187] (II)         solid
[  4447.187] (II)         copy
[  4447.187] (II)         composite (RENDER acceleration)
[  4447.187] (II)         put_image
[  4447.187] (II)         get_image
[  4447.187] (==) intel(0): Backing store disabled
[  4447.188] (==) intel(0): Silken mouse enabled
[  4447.188] (II) intel(0): Initializing HW Cursor
[  4447.580] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[  4447.581] (==) intel(0): DPMS enabled
[  4447.581] (==) intel(0): Intel XvMC decoder enabled
[  4447.581] (II) intel(0): Set up textured video
[  4447.581] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[  4447.581] (II) intel(0): direct rendering: DRI2 Enabled
[  4447.581] (==) intel(0): hotplug detection: "enabled"
[  4447.581] (--) RandR disabled
[  4447.581] (II) Initializing built-in extension Generic Event Extension
[  4447.581] (II) Initializing built-in extension SHAPE
[  4447.581] (II) Initializing built-in extension MIT-SHM
[  4447.581] (II) Initializing built-in extension XInputExtension
[  4447.581] (II) Initializing built-in extension XTEST
[  4447.581] (II) Initializing built-in extension BIG-REQUESTS
[  4447.581] (II) Initializing built-in extension SYNC
[  4447.581] (II) Initializing built-in extension XKEYBOARD
[  4447.581] (II) Initializing built-in extension XC-MISC
[  4447.581] (II) Initializing built-in extension SECURITY
[  4447.581] (II) Initializing built-in extension XINERAMA
[  4447.581] (II) Initializing built-in extension XFIXES
[  4447.581] (II) Initializing built-in extension RENDER
[  4447.581] (II) Initializing built-in extension RANDR
[  4447.581] (II) Initializing built-in extension COMPOSITE
[  4447.581] (II) Initializing built-in extension DAMAGE
[  4447.581] (II) Initializing built-in extension GESTURE
[  4447.593] (II) AIGLX: Trying DRI driver /usr/lib/dri/i965_dri.so
[  4447.596] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[  4447.596] (II) AIGLX: enabled GLX_INTEL_swap_event
[  4447.596] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[  4447.596] (II) AIGLX: enabled GLX_SGI_make_current_read
[  4447.596] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[  4447.596] (II) AIGLX: Loaded and initialized i965
[  4447.596] (II) GLX: Initialized DRI2 GL provider for screen 0
[  4447.597] (II) intel(0): Setting screen physical size to 270 x 203
[  4447.613] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  4447.628] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[  4447.628] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  4447.628] (II) LoadModule: "evdev"
[  4447.628] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  4447.629] (II) Module evdev: vendor="X.Org Foundation"
[  4447.629] 	compiled for 1.10.0.902, module version = 2.6.0
[  4447.629] 	Module class: X.Org XInput Driver
[  4447.629] 	ABI class: X.Org XInput driver, version 12.3
[  4447.629] (II) Using input driver 'evdev' for 'Power Button'
[  4447.629] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  4447.629] (**) Power Button: always reports core events
[  4447.629] (**) Power Button: Device: "/dev/input/event2"
[  4447.629] (--) Power Button: Found keys
[  4447.629] (II) Power Button: Configuring as keyboard
[  4447.629] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[  4447.629] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[  4447.629] (**) Option "xkb_rules" "evdev"
[  4447.629] (**) Option "xkb_model" "pc105"
[  4447.629] (**) Option "xkb_layout" "us"
[  4447.630] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[  4447.631] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[  4447.631] (II) Using input driver 'evdev' for 'Video Bus'
[  4447.631] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  4447.631] (**) Video Bus: always reports core events
[  4447.631] (**) Video Bus: Device: "/dev/input/event4"
[  4447.636] (--) Video Bus: Found keys
[  4447.636] (II) Video Bus: Configuring as keyboard
[  4447.636] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input4/event4"
[  4447.636] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[  4447.636] (**) Option "xkb_rules" "evdev"
[  4447.636] (**) Option "xkb_model" "pc105"
[  4447.636] (**) Option "xkb_layout" "us"
[  4447.642] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[  4447.642] (II) No input driver/identifier specified (ignoring)
[  4447.643] (II) config/udev: Adding input device Sleep Button (/dev/input/event0)
[  4447.643] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[  4447.643] (II) Using input driver 'evdev' for 'Sleep Button'
[  4447.643] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  4447.643] (**) Sleep Button: always reports core events
[  4447.643] (**) Sleep Button: Device: "/dev/input/event0"
[  4447.643] (--) Sleep Button: Found keys
[  4447.643] (II) Sleep Button: Configuring as keyboard
[  4447.643] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input0/event0"
[  4447.643] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[  4447.643] (**) Option "xkb_rules" "evdev"
[  4447.643] (**) Option "xkb_model" "pc105"
[  4447.643] (**) Option "xkb_layout" "us"
[  4447.648] (II) config/udev: Adding input device HP Webcam [2 MP Fixed] (/dev/input/event6)
[  4447.648] (**) HP Webcam [2 MP Fixed]: Applying InputClass "evdev keyboard catchall"
[  4447.648] (II) Using input driver 'evdev' for 'HP Webcam [2 MP Fixed]'
[  4447.648] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  4447.648] (**) HP Webcam [2 MP Fixed]: always reports core events
[  4447.648] (**) HP Webcam [2 MP Fixed]: Device: "/dev/input/event6"
[  4447.648] (--) HP Webcam [2 MP Fixed]: Found keys
[  4447.648] (II) HP Webcam [2 MP Fixed]: Configuring as keyboard
[  4447.648] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-5/1-5:1.0/input/input6/event6"
[  4447.648] (II) XINPUT: Adding extended input device "HP Webcam [2 MP Fixed]" (type: KEYBOARD)
[  4447.648] (**) Option "xkb_rules" "evdev"
[  4447.648] (**) Option "xkb_model" "pc105"
[  4447.648] (**) Option "xkb_layout" "us"
[  4447.657] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[  4447.657] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[  4447.657] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[  4447.657] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  4447.657] (**) AT Translated Set 2 keyboard: always reports core events
[  4447.657] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[  4447.657] (--) AT Translated Set 2 keyboard: Found keys
[  4447.657] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[  4447.657] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[  4447.657] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[  4447.657] (**) Option "xkb_rules" "evdev"
[  4447.657] (**) Option "xkb_model" "pc105"
[  4447.658] (**) Option "xkb_layout" "us"
[  4447.658] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event8)
[  4447.658] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[  4447.658] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[  4447.658] (II) LoadModule: "synaptics"
[  4447.659] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[  4447.659] (II) Module synaptics: vendor="X.Org Foundation"
[  4447.659] 	compiled for 1.10.0.902, module version = 1.3.99
[  4447.659] 	Module class: X.Org XInput Driver
[  4447.659] 	ABI class: X.Org XInput driver, version 12.3
[  4447.659] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[  4447.659] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[  4447.659] (**) SynPS/2 Synaptics TouchPad: always reports core events
[  4447.659] (**) Option "Device" "/dev/input/event8"
[  4447.683] (--) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5692
[  4447.683] (--) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4680
[  4447.683] (--) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[  4447.683] (--) SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[  4447.683] (--) SynPS/2 Synaptics TouchPad: buttons: left right double triple
[  4447.688] (--) SynPS/2 Synaptics TouchPad: touchpad found
[  4447.688] (**) SynPS/2 Synaptics TouchPad: always reports core events
[  4447.695] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio4/input/input8/event8"
[  4447.695] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[  4447.695] (**) SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[  4447.695] (**) SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[  4447.695] (**) SynPS/2 Synaptics TouchPad: AccelFactor is now 0.037
[  4447.695] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[  4447.695] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[  4447.696] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[  4447.696] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[  4447.701] (--) SynPS/2 Synaptics TouchPad: touchpad found
[  4447.702] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[  4447.702] (II) No input driver/identifier specified (ignoring)
[  4447.702] (II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/event5)
[  4447.702] (II) No input driver/identifier specified (ignoring)
[  4447.703] (II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/js0)
[  4447.703] (II) No input driver/identifier specified (ignoring)
[  4447.718] (II) config/udev: Adding input device HP WMI hotkeys (/dev/input/event7)
[  4447.718] (**) HP WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[  4447.718] (II) Using input driver 'evdev' for 'HP WMI hotkeys'
[  4447.718] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  4447.718] (**) HP WMI hotkeys: always reports core events
[  4447.718] (**) HP WMI hotkeys: Device: "/dev/input/event7"
[  4447.732] (--) HP WMI hotkeys: Found keys
[  4447.732] (II) HP WMI hotkeys: Configuring as keyboard
[  4447.732] (**) Option "config_info" "udev:/sys/devices/virtual/input/input7/event7"
[  4447.732] (II) XINPUT: Adding extended input device "HP WMI hotkeys" (type: KEYBOARD)
[  4447.732] (**) Option "xkb_rules" "evdev"
[  4447.732] (**) Option "xkb_model" "pc105"
[  4447.732] (**) Option "xkb_layout" "us"
[  4448.039] (II) intel(0): EDID vendor "CMO", prod id 5489
[  4448.039] (II) intel(0): Printing DDC gathered Modelines:
[  4448.039] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1382 1416 1466  768 770 776 788 -hsync -vsync (47.3 kHz)
[  4448.125] (II) intel(0): EDID vendor "CMO", prod id 5489
[  4448.125] (II) intel(0): Printing DDC gathered Modelines:
[  4448.125] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1382 1416 1466  768 770 776 788 -hsync -vsync (47.3 kHz)
[  4448.205] (II) intel(0): EDID vendor "CMO", prod id 5489
[  4448.205] (II) intel(0): Printing DDC gathered Modelines:
[  4448.205] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1382 1416 1466  768 770 776 788 -hsync -vsync (47.3 kHz)
[  4448.268] (II) intel(0): EDID vendor "CMO", prod id 5489
[  4448.268] (II) intel(0): Printing DDC gathered Modelines:
[  4448.268] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1382 1416 1466  768 770 776 788 -hsync -vsync (47.3 kHz)
[  4448.354] (II) intel(0): EDID vendor "CMO", prod id 5489
[  4448.354] (II) intel(0): Printing DDC gathered Modelines:
[  4448.354] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1382 1416 1466  768 770 776 788 -hsync -vsync (47.3 kHz)
[  4448.424] (II) intel(0): Allocated new frame buffer 1408x768 stride 5632, tiled
[  4661.332] (II) AIGLX: Suspending AIGLX clients for VT switch
[  5238.017] (II) HP WMI hotkeys: Close
[  5238.017] (II) UnloadModule: "evdev"
[  5238.017] (II) Unloading evdev
[  5238.018] (II) UnloadModule: "synaptics"
[  5238.018] (II) Unloading synaptics
[  5238.018] (II) AT Translated Set 2 keyboard: Close
[  5238.018] (II) UnloadModule: "evdev"
[  5238.018] (II) Unloading evdev
[  5238.018] (II) HP Webcam [2 MP Fixed]: Close
[  5238.018] (II) UnloadModule: "evdev"
[  5238.018] (II) Unloading evdev
[  5238.018] (II) Sleep Button: Close
[  5238.018] (II) UnloadModule: "evdev"
[  5238.018] (II) Unloading evdev
[  5238.018] (II) Video Bus: Close
[  5238.018] (II) UnloadModule: "evdev"
[  5238.018] (II) Unloading evdev
[  5238.018] (II) Power Button: Close
[  5238.018] (II) UnloadModule: "evdev"
[  5238.018] (II) Unloading evdev
[  5238.047]  ddxSigGiveUp: Closing log
```

and dmesg:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.38-8-generic (buildd@vernadsky) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 (Ubuntu 2.6.38-8.42-generic 2.6.38.2)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000ef000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000076b58000 (usable)
[    0.000000]  BIOS-e820: 0000000076b58000 - 0000000076b5a000 (reserved)
[    0.000000]  BIOS-e820: 0000000076b5a000 - 0000000077970000 (usable)
[    0.000000]  BIOS-e820: 0000000077970000 - 0000000077980000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000077980000 - 000000007a10a000 (usable)
[    0.000000]  BIOS-e820: 000000007a10a000 - 000000007a30a000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007a30a000 - 000000007ba92000 (usable)
[    0.000000]  BIOS-e820: 000000007ba92000 - 000000007ba9a000 (reserved)
[    0.000000]  BIOS-e820: 000000007ba9a000 - 000000007babf000 (usable)
[    0.000000]  BIOS-e820: 000000007babf000 - 000000007bacf000 (reserved)
[    0.000000]  BIOS-e820: 000000007bacf000 - 000000007bbcf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007bbcf000 - 000000007bbff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007bbff000 - 000000007bc00000 (usable)
[    0.000000]  BIOS-e820: 000000007bc00000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed14000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI 2.4 present.
[    0.000000] DMI: Hewlett-Packard HP ProBook 4510s/3072, BIOS 68PZI Ver. F.0F 10/20/2009
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x7bc00 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0FFE00000 mask FFFE00000 write-protect
[    0.000000]   1 base 000000000 mask F80000000 write-back
[    0.000000]   2 base 077970000 mask FFFFF0000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 35cb0000 - 36e50000
[    0.000000] ACPI: RSDP 000f6970 00024 (v02 HPQOEM)
[    0.000000] ACPI: XSDT 7bbfe120 00074 (v01 HPQOEM SLIC-MPC 0000000F      01000013)
[    0.000000] ACPI: FACP 7bbfc000 000F4 (v03 HPQOEM 3072     0000000F HP   00000001)
[    0.000000] ACPI: DSDT 7bbdb000 1B05A (v01 HPQOEM 3072     00000001 INTL 20060912)
[    0.000000] ACPI: FACS 7bbad000 00040
[    0.000000] ACPI: HPET 7bbfb000 00038 (v01 HPQOEM 3072     00000001 HP   00000001)
[    0.000000] ACPI: APIC 7bbfa000 00084 (v01 HPQOEM 3072     00000001 HP   00000001)
[    0.000000] ACPI: MCFG 7bbf9000 0003C (v01 HPQOEM 3072     00000001 HP   00000001)
[    0.000000] ACPI: ASF! 7bbf8000 000A0 (v32 HPQOEM 3072     00000001 HP   00000001)
[    0.000000] ACPI: SSDT 7bbda000 0064F (v01 HPQOEM  SataPri 00001000 INTL 20060912)
[    0.000000] ACPI: SSDT 7bbd9000 00692 (v01 HPQOEM  SataSec 00001000 INTL 20060912)
[    0.000000] ACPI: SSDT 7bbd6000 0066C (v01  PmRef    CpuPm 00003000 INTL 20060912)
[    0.000000] ACPI: SSDT 7bbd5000 00288 (v01  PmRef  Cpu0Tst 00003000 INTL 20060912)
[    0.000000] ACPI: SSDT 7bbd4000 00225 (v01  PmRef    ApTst 00003000 INTL 20060912)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1092MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007bc00
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[7] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x00076b58
[    0.000000]     0: 0x00076b5a -> 0x00077970
[    0.000000]     0: 0x00077980 -> 0x0007a10a
[    0.000000]     0: 0x0007a30a -> 0x0007ba92
[    0.000000]     0: 0x0007ba9a -> 0x0007babf
[    0.000000]     0: 0x0007bbff -> 0x0007bc00
[    0.000000] On node 0 totalpages: 505909
[    0.000000] free_area_init_node: node 0, pgdat c1784100, node_mem_map f4d38200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2185 pages used for memmap
[    0.000000]   HighMem zone: 276511 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000ef000
[    0.000000] PM: Registered nosave memory: 00000000000ef000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:60000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f7000000 s28800 r0 d24448 u1048576
[    0.000000] pcpu-alloc: s28800 r0 d24448 u1048576 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 501948
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=846c2273-e3f1-4e5d-b501-6ea7513a99b1 ro vga=792
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] allocated 10137280 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007bc00)
[    0.000000] Memory: 1969428k/2027520k available (5188k kernel code, 54208k reserved, 2540k data, 700k init, 1114784k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc178d000 - 0xc183c000   ( 700 kB)
[    0.000000]       .data : 0xc15112a1 - 0xc178c480   (2540 kB)
[    0.000000]       .text : 0xc1000000 - 0xc15112a1   (5188 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:712 16
[    0.000000] CPU 0 irqstacks, hard=f3c08000 soft=f3c0a000
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2094.759 MHz processor.
[    0.004003] Calibrating delay loop (skipped), value calculated using timer frequency.. 4189.51 BogoMIPS (lpj=8379036)
[    0.004013] pid_max: default: 32768 minimum: 301
[    0.004039] Security Framework initialized
[    0.004056] AppArmor: AppArmor initialized
[    0.004060] Yama: becoming mindful.
[    0.004120] Mount-cache hash table entries: 512
[    0.004262] Initializing cgroup subsys ns
[    0.004269] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
[    0.004275] Initializing cgroup subsys cpuacct
[    0.004282] Initializing cgroup subsys memory
[    0.004295] Initializing cgroup subsys devices
[    0.004299] Initializing cgroup subsys freezer
[    0.004303] Initializing cgroup subsys net_cls
[    0.004307] Initializing cgroup subsys blkio
[    0.004347] CPU: Physical Processor ID: 0
[    0.004350] CPU: Processor Core ID: 0
[    0.004355] mce: CPU supports 6 MCE banks
[    0.004364] CPU0: Thermal monitoring handled by SMI
[    0.004368] using mwait in idle threads.
[    0.010504] ACPI: Core revision 20110112
[    0.021749] ftrace: allocating 23640 entries in 47 pages
[    0.024055] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.024417] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.064825] CPU0: Intel(R) Core(TM)2 Duo CPU     T6570  @ 2.10GHz stepping 0a
[    0.068003] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.068003] ... version:                2
[    0.068003] ... bit width:              40
[    0.068003] ... generic registers:      2
[    0.068003] ... value mask:             000000ffffffffff
[    0.068003] ... max period:             000000007fffffff
[    0.068003] ... fixed-purpose events:   3
[    0.068003] ... event mask:             0000000700000003
[    0.068003] CPU 1 irqstacks, hard=f3cd2000 soft=f3cd4000
[    0.068003] Booting Node   0, Processors  #1
[    0.008000] Initializing CPU#1
[    0.008000] CPU1: Thermal monitoring handled by SMI
[    0.156025] Brought up 2 CPUs
[    0.156035] Total of 2 processors activated (8378.98 BogoMIPS).
[    0.156600] devtmpfs: initialized
[    0.157308] print_constraints: dummy: 
[    0.157346] Time: 12:17:12  Date: 02/04/12
[    0.157387] NET: Registered protocol family 16
[    0.157415] Trying to unpack rootfs image as initramfs...
[    0.157512] EISA bus registered
[    0.157522] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.157528] ACPI: bus type pci registered
[    0.157606] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.157614] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.157619] PCI: Using MMCONFIG for extended config space
[    0.157623] PCI: Using configuration type 1 for base access
[    0.172114] bio: create slab <bio-0> at 0
[    0.175016] ACPI: EC: Look up EC in DSDT
[    0.212110] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.290040] ACPI: SSDT 7bac6c18 00275 (v01  PmRef  Cpu0Ist 00003000 INTL 20060912)
[    0.290708] ACPI: Dynamic OEM Table Load:
[    0.290714] ACPI: SSDT   (null) 00275 (v01  PmRef  Cpu0Ist 00003000 INTL 20060912)
[    0.290879] ACPI: SSDT 7bac4618 0057B (v01  PmRef  Cpu0Cst 00003001 INTL 20060912)
[    0.291518] ACPI: Dynamic OEM Table Load:
[    0.291524] ACPI: SSDT   (null) 0057B (v01  PmRef  Cpu0Cst 00003001 INTL 20060912)
[    0.352381] ACPI: SSDT 7bac5e18 001D7 (v01  PmRef    ApIst 00003000 INTL 20060912)
[    0.353074] ACPI: Dynamic OEM Table Load:
[    0.353080] ACPI: SSDT   (null) 001D7 (v01  PmRef    ApIst 00003000 INTL 20060912)
[    0.364160] ACPI: SSDT 7bac6f18 0008D (v01  PmRef    ApCst 00003000 INTL 20060912)
[    0.364823] ACPI: Dynamic OEM Table Load:
[    0.364829] ACPI: SSDT   (null) 0008D (v01  PmRef    ApCst 00003000 INTL 20060912)
[    0.583218] Freeing initrd memory: 18048k freed
[    0.640149] ACPI: Interpreter enabled
[    0.640168] ACPI: (supports S0 S3 S4 S5)
[    0.640197] ACPI: Using IOAPIC for interrupt routing
[    0.641748] ACPI: Power Resource [APPR] (off)
[    0.673964] ACPI: Power Resource [PFN6] (off)
[    0.674046] ACPI: Power Resource [PFN7] (off)
[    0.674124] ACPI: Power Resource [PFN8] (off)
[    0.674199] ACPI: Power Resource [PFN9] (off)
[    0.674275] ACPI: Power Resource [PFNA] (off)
[    0.674353] ACPI: Power Resource [PFNB] (off)
[    0.674403] ACPI: Power Resource [PGF0] (off)
[    0.675174] ACPI: Power Resource [PFN0] (off)
[    0.675254] ACPI: Power Resource [PFN1] (off)
[    0.675333] ACPI: Power Resource [PFN2] (off)
[    0.675409] ACPI: Power Resource [PFN3] (off)
[    0.675490] ACPI: Power Resource [PFN4] (off)
[    0.675567] ACPI: Power Resource [PFN5] (off)
[    0.676612] ACPI: EC: GPE = 0x16, I/O: command/status = 0x66, data = 0x62
[    0.676928] ACPI: No dock devices found.
[    0.676932] HEST: Table not found.
[    0.676938] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.677987] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.678786] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.678792] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.678798] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.678805] pci_root PNP0A08:00: host bridge window [mem 0x80000000-0xdfffffff]
[    0.678812] pci_root PNP0A08:00: host bridge window [mem 0xf0000000-0xfedfffff]
[    0.678818] pci_root PNP0A08:00: host bridge window [mem 0xfee01000-0xffffffff]
[    0.678838] pci 0000:00:00.0: [8086:2a40] type 0 class 0x000600
[    0.678865] DMAR: Forcing write-buffer flush capability
[    0.678869] DMAR: Disabling IOMMU for graphics on this chipset
[    0.678897] pci 0000:00:02.0: [8086:2a42] type 0 class 0x000300
[    0.678912] pci 0000:00:02.0: reg 10: [mem 0x90000000-0x903fffff 64bit]
[    0.678922] pci 0000:00:02.0: reg 18: [mem 0x80000000-0x8fffffff 64bit pref]
[    0.678929] pci 0000:00:02.0: reg 20: [io  0x7120-0x7127]
[    0.678964] pci 0000:00:02.1: [8086:2a43] type 0 class 0x000380
[    0.678977] pci 0000:00:02.1: reg 10: [mem 0x90400000-0x904fffff 64bit]
[    0.679073] pci 0000:00:1a.0: [8086:2937] type 0 class 0x000c03
[    0.679136] pci 0000:00:1a.0: reg 20: [io  0x70a0-0x70bf]
[    0.679199] pci 0000:00:1a.1: [8086:2938] type 0 class 0x000c03
[    0.679263] pci 0000:00:1a.1: reg 20: [io  0x7080-0x709f]
[    0.679326] pci 0000:00:1a.2: [8086:2939] type 0 class 0x000c03
[    0.679389] pci 0000:00:1a.2: reg 20: [io  0x7060-0x707f]
[    0.679465] pci 0000:00:1a.7: [8086:293c] type 0 class 0x000c03
[    0.679493] pci 0000:00:1a.7: reg 10: [mem 0x98804400-0x988047ff]
[    0.679592] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.679598] pci 0000:00:1a.7: PME# disabled
[    0.679631] pci 0000:00:1b.0: [8086:293e] type 0 class 0x000403
[    0.679655] pci 0000:00:1b.0: reg 10: [mem 0x98800000-0x98803fff 64bit]
[    0.679741] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.679746] pci 0000:00:1b.0: PME# disabled
[    0.679775] pci 0000:00:1c.0: [8086:2940] type 1 class 0x000604
[    0.679865] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.679870] pci 0000:00:1c.0: PME# disabled
[    0.679904] pci 0000:00:1c.2: [8086:2944] type 1 class 0x000604
[    0.679993] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.679998] pci 0000:00:1c.2: PME# disabled
[    0.680032] pci 0000:00:1c.4: [8086:2948] type 1 class 0x000604
[    0.680131] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.680136] pci 0000:00:1c.4: PME# disabled
[    0.680169] pci 0000:00:1c.5: [8086:294a] type 1 class 0x000604
[    0.680258] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.680264] pci 0000:00:1c.5: PME# disabled
[    0.680301] pci 0000:00:1d.0: [8086:2934] type 0 class 0x000c03
[    0.680364] pci 0000:00:1d.0: reg 20: [io  0x7040-0x705f]
[    0.680427] pci 0000:00:1d.1: [8086:2935] type 0 class 0x000c03
[    0.680490] pci 0000:00:1d.1: reg 20: [io  0x7020-0x703f]
[    0.680554] pci 0000:00:1d.2: [8086:2936] type 0 class 0x000c03
[    0.680616] pci 0000:00:1d.2: reg 20: [io  0x7000-0x701f]
[    0.680692] pci 0000:00:1d.7: [8086:293a] type 0 class 0x000c03
[    0.680720] pci 0000:00:1d.7: reg 10: [mem 0x98804000-0x988043ff]
[    0.680819] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.680825] pci 0000:00:1d.7: PME# disabled
[    0.680852] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    0.680941] pci 0000:00:1f.0: [8086:2919] type 0 class 0x000601
[    0.681101] pci 0000:00:1f.2: [8086:2928] type 0 class 0x000101
[    0.681126] pci 0000:00:1f.2: reg 10: [io  0x7118-0x711f]
[    0.681139] pci 0000:00:1f.2: reg 14: [io  0x7134-0x7137]
[    0.681151] pci 0000:00:1f.2: reg 18: [io  0x7110-0x7117]
[    0.681164] pci 0000:00:1f.2: reg 1c: [io  0x7130-0x7133]
[    0.681177] pci 0000:00:1f.2: reg 20: [io  0x70f0-0x70ff]
[    0.681189] pci 0000:00:1f.2: reg 24: [io  0x70e0-0x70ef]
[    0.681260] pci 0000:00:1f.5: [8086:292d] type 0 class 0x000101
[    0.681285] pci 0000:00:1f.5: reg 10: [io  0x7108-0x710f]
[    0.681298] pci 0000:00:1f.5: reg 14: [io  0x712c-0x712f]
[    0.681310] pci 0000:00:1f.5: reg 18: [io  0x7100-0x7107]
[    0.681323] pci 0000:00:1f.5: reg 1c: [io  0x7128-0x712b]
[    0.681336] pci 0000:00:1f.5: reg 20: [io  0x70d0-0x70df]
[    0.681348] pci 0000:00:1f.5: reg 24: [io  0x70c0-0x70cf]
[    0.681464] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.681472] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.681478] pci 0000:00:1c.0:   bridge window [mem 0x98700000-0x987fffff]
[    0.681487] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.681551] pci 0000:00:1c.2: PCI bridge to [bus 02-42]
[    0.681558] pci 0000:00:1c.2:   bridge window [io  0x5000-0x6fff]
[    0.681564] pci 0000:00:1c.2:   bridge window [mem 0x94700000-0x986fffff]
[    0.681572] pci 0000:00:1c.2:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.681636] pci 0000:00:1c.4: PCI bridge to [bus 43-83]
[    0.681644] pci 0000:00:1c.4:   bridge window [io  0x3000-0x4fff]
[    0.681649] pci 0000:00:1c.4:   bridge window [mem 0x90700000-0x946fffff]
[    0.681657] pci 0000:00:1c.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.681914] pci 0000:84:00.0: [11ab:436c] type 0 class 0x000200
[    0.682086] pci 0000:84:00.0: reg 10: [mem 0x90600000-0x90603fff 64bit]
[    0.682185] pci 0000:84:00.0: reg 18: [io  0x2000-0x20ff]
[    0.682547] pci 0000:84:00.0: reg 30: [mem 0xfffe0000-0xffffffff pref]
[    0.682867] pci 0000:84:00.0: supports D1 D2
[    0.682869] pci 0000:84:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.682895] pci 0000:84:00.0: PME# disabled
[    0.683070] pci 0000:00:1c.5: PCI bridge to [bus 84-84]
[    0.683078] pci 0000:00:1c.5:   bridge window [io  0x2000-0x2fff]
[    0.683083] pci 0000:00:1c.5:   bridge window [mem 0x90600000-0x906fffff]
[    0.683092] pci 0000:00:1c.5:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.683192] pci 0000:00:1e.0: PCI bridge to [bus 85-85] (subtractive decode)
[    0.683201] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.683206] pci 0000:00:1e.0:   bridge window [mem 0x90500000-0x905fffff]
[    0.683215] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.683218] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.683221] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.683223] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.683226] pci 0000:00:1e.0:   bridge window [mem 0x80000000-0xdfffffff] (subtractive decode)
[    0.683229] pci 0000:00:1e.0:   bridge window [mem 0xf0000000-0xfedfffff] (subtractive decode)
[    0.683232] pci 0000:00:1e.0:   bridge window [mem 0xfee01000-0xffffffff] (subtractive decode)
[    0.683266] pci_bus 0000:00: on NUMA node 0
[    0.683270] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.683505] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.683564] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.683657] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[    0.683750] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    0.683844] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.694480] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.694544] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.694604] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.694664] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.694724] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.694784] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.694845] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.694904] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    0.695037] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.695056] vgaarb: loaded
[    0.695293] SCSI subsystem initialized
[    0.695307] libata version 3.00 loaded.
[    0.695307] usbcore: registered new interface driver usbfs
[    0.695307] usbcore: registered new interface driver hub
[    0.695307] usbcore: registered new device driver usb
[    0.696094] wmi: Mapper loaded
[    0.696098] PCI: Using ACPI for IRQ routing
[    0.696103] PCI: pci_cache_line_size set to 64 bytes
[    0.696205] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.696208] reserve RAM buffer: 0000000076b58000 - 0000000077ffffff 
[    0.696211] reserve RAM buffer: 0000000077970000 - 0000000077ffffff 
[    0.696213] reserve RAM buffer: 000000007a10a000 - 000000007bffffff 
[    0.696217] reserve RAM buffer: 000000007ba92000 - 000000007bffffff 
[    0.696220] reserve RAM buffer: 000000007babf000 - 000000007bffffff 
[    0.696224] reserve RAM buffer: 000000007bc00000 - 000000007bffffff 
[    0.696349] NetLabel: Initializing
[    0.696353] NetLabel:  domain hash size = 128
[    0.696357] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.696371] NetLabel:  unlabeled traffic allowed by default
[    0.696416] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.696427] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.696435] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.700061] Switching to clocksource hpet
[    0.703918] Switched to NOHz mode on CPU #0
[    0.703994] Switched to NOHz mode on CPU #1
[    0.708319] AppArmor: AppArmor Filesystem Enabled
[    0.708360] pnp: PnP ACPI init
[    0.708382] ACPI: bus type pnp registered
[    0.708824] pnp 00:00: [bus 00-ff]
[    0.708827] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.708830] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.708832] pnp 00:00: [io  0x0d00-0xffff window]
[    0.708835] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.708837] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.708840] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.708842] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.708845] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.708847] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.708849] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.708852] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.708854] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.708857] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.708859] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.708862] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.708864] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.708867] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    0.708869] pnp 00:00: [mem 0x80000000-0xdfffffff window]
[    0.708871] pnp 00:00: [mem 0xf0000000-0xfedfffff window]
[    0.708874] pnp 00:00: [mem 0xfee01000-0xffffffff window]
[    0.709012] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.709105] pnp 00:01: [mem 0xfed1c000-0xfed1ffff]
[    0.709108] pnp 00:01: [mem 0xfed10000-0xfed13fff]
[    0.709110] pnp 00:01: [mem 0xfed18000-0xfed18fff]
[    0.709112] pnp 00:01: [mem 0xfed19000-0xfed19fff]
[    0.709114] pnp 00:01: [mem 0xe0000000-0xefffffff]
[    0.709117] pnp 00:01: [mem 0xfec00000-0xfec00fff]
[    0.709119] pnp 00:01: [mem 0xfed20000-0xfed3ffff]
[    0.709121] pnp 00:01: [mem 0xfed45000-0xfed8ffff]
[    0.709188] system 00:01: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.709194] system 00:01: [mem 0xfed10000-0xfed13fff] has been reserved
[    0.709200] system 00:01: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.709206] system 00:01: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.709212] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.709217] system 00:01: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.709223] system 00:01: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.709229] system 00:01: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.709235] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.709704] pnp 00:02: [io  0x0000-0x001f]
[    0.709707] pnp 00:02: [io  0x0081-0x0091]
[    0.709709] pnp 00:02: [io  0x0093-0x009f]
[    0.709711] pnp 00:02: [io  0x00c0-0x00df]
[    0.709714] pnp 00:02: [dma 4]
[    0.709780] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.709790] pnp 00:03: [mem 0xff000000-0xffffffff]
[    0.709855] pnp 00:03: Plug and Play ACPI device, IDs INT0800 (active)
[    0.709896] pnp 00:04: [io  0xfe00-0xfe0f]
[    0.709898] pnp 00:04: [io  0xfe80-0xfe8f]
[    0.709900] pnp 00:04: [mem 0xfed40000-0xfed44fff]
[    0.709989] system 00:04: [io  0xfe00-0xfe0f] has been reserved
[    0.709995] system 00:04: [io  0xfe80-0xfe8f] has been reserved
[    0.710001] system 00:04: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.710007] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.710105] pnp 00:05: [mem 0xfed00000-0xfed003ff]
[    0.710192] system 00:05: [mem 0xfed00000-0xfed003ff] has been reserved
[    0.710199] system 00:05: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
[    0.710212] pnp 00:06: [io  0x00f0]
[    0.710225] pnp 00:06: [irq 13]
[    0.710291] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.710305] pnp 00:07: [io  0x002e-0x002f]
[    0.710307] pnp 00:07: [io  0x004e-0x004f]
[    0.710309] pnp 00:07: [io  0x0061]
[    0.710311] pnp 00:07: [io  0x0063]
[    0.710313] pnp 00:07: [io  0x0065]
[    0.710315] pnp 00:07: [io  0x0067]
[    0.710317] pnp 00:07: [io  0x0070]
[    0.710319] pnp 00:07: [io  0x0080]
[    0.710321] pnp 00:07: [io  0x0092]
[    0.710323] pnp 00:07: [io  0x00b2-0x00b3]
[    0.710325] pnp 00:07: [io  0x0200-0x027f]
[    0.710328] pnp 00:07: [io  0x1000-0x1003]
[    0.710330] pnp 00:07: [io  0x1010-0x101f]
[    0.710332] pnp 00:07: [io  0xffff]
[    0.710334] pnp 00:07: [io  0x0400-0x047f]
[    0.710336] pnp 00:07: [io  0x0500-0x057f]
[    0.710338] pnp 00:07: [io  0xef80-0xef9f]
[    0.710445] system 00:07: [io  0x0200-0x027f] has been reserved
[    0.710451] system 00:07: [io  0x1000-0x1003] has been reserved
[    0.710456] system 00:07: [io  0x1010-0x101f] has been reserved
[    0.710462] system 00:07: [io  0xffff] has been reserved
[    0.710467] system 00:07: [io  0x0400-0x047f] has been reserved
[    0.710472] system 00:07: [io  0x0500-0x057f] has been reserved
[    0.710477] system 00:07: [io  0xef80-0xef9f] has been reserved
[    0.710483] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.710494] pnp 00:08: [io  0x0070-0x0077]
[    0.710500] pnp 00:08: [irq 8]
[    0.710566] pnp 00:08: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.710725] pnp 00:09: [io  0x0060]
[    0.710730] pnp 00:09: [io  0x0064]
[    0.710735] pnp 00:09: [irq 1]
[    0.710804] pnp 00:09: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.710818] pnp 00:0a: [irq 12]
[    0.710890] pnp 00:0a: Plug and Play ACPI device, IDs SYN0149 SYN0100 SYN0002 PNP0f13 (active)
[    0.710940] pnp 00:0b: [irq 23]
[    0.711012] pnp 00:0b: Plug and Play ACPI device, IDs HPQ0004 (active)
[    0.711152] pnp: PnP ACPI: found 12 devices
[    0.711157] ACPI: ACPI bus type pnp unregistered
[    0.711163] PnPBIOS: Disabled by ACPI PNP
[    0.747875] pci 0000:84:00.0: no compatible bridge window for [mem 0xfffe0000-0xffffffff pref]
[    0.747940] pci 0000:00:1c.0: BAR 15: assigned [mem 0x98900000-0x98afffff 64bit pref]
[    0.747950] pci 0000:00:1c.2: BAR 15: assigned [mem 0x98b00000-0x98cfffff 64bit pref]
[    0.747959] pci 0000:00:1c.4: BAR 15: assigned [mem 0x98d00000-0x98efffff 64bit pref]
[    0.747967] pci 0000:00:1c.5: BAR 15: assigned [mem 0x98f00000-0x990fffff pref]
[    0.747975] pci 0000:00:1c.0: BAR 13: assigned [io  0x8000-0x8fff]
[    0.747980] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.747988] pci 0000:00:1c.0:   bridge window [io  0x8000-0x8fff]
[    0.748012] pci 0000:00:1c.0:   bridge window [mem 0x98700000-0x987fffff]
[    0.748020] pci 0000:00:1c.0:   bridge window [mem 0x98900000-0x98afffff 64bit pref]
[    0.748032] pci 0000:00:1c.2: PCI bridge to [bus 02-42]
[    0.748038] pci 0000:00:1c.2:   bridge window [io  0x5000-0x6fff]
[    0.748047] pci 0000:00:1c.2:   bridge window [mem 0x94700000-0x986fffff]
[    0.748055] pci 0000:00:1c.2:   bridge window [mem 0x98b00000-0x98cfffff 64bit pref]
[    0.748067] pci 0000:00:1c.4: PCI bridge to [bus 43-83]
[    0.748073] pci 0000:00:1c.4:   bridge window [io  0x3000-0x4fff]
[    0.748082] pci 0000:00:1c.4:   bridge window [mem 0x90700000-0x946fffff]
[    0.748090] pci 0000:00:1c.4:   bridge window [mem 0x98d00000-0x98efffff 64bit pref]
[    0.748103] pci 0000:84:00.0: BAR 6: assigned [mem 0x98f00000-0x98f1ffff pref]
[    0.748110] pci 0000:00:1c.5: PCI bridge to [bus 84-84]
[    0.748116] pci 0000:00:1c.5:   bridge window [io  0x2000-0x2fff]
[    0.748125] pci 0000:00:1c.5:   bridge window [mem 0x90600000-0x906fffff]
[    0.748133] pci 0000:00:1c.5:   bridge window [mem 0x98f00000-0x990fffff pref]
[    0.748144] pci 0000:00:1e.0: PCI bridge to [bus 85-85]
[    0.748149] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.748158] pci 0000:00:1e.0:   bridge window [mem 0x90500000-0x905fffff]
[    0.748165] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.748188] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.748197] pci 0000:00:1c.0: setting latency timer to 64
[    0.748208] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.748216] pci 0000:00:1c.2: setting latency timer to 64
[    0.748224] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.748232] pci 0000:00:1c.4: setting latency timer to 64
[    0.748243] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.748251] pci 0000:00:1c.5: setting latency timer to 64
[    0.748261] pci 0000:00:1e.0: setting latency timer to 64
[    0.748265] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.748268] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.748270] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.748273] pci_bus 0000:00: resource 7 [mem 0x80000000-0xdfffffff]
[    0.748275] pci_bus 0000:00: resource 8 [mem 0xf0000000-0xfedfffff]
[    0.748278] pci_bus 0000:00: resource 9 [mem 0xfee01000-0xffffffff]
[    0.748280] pci_bus 0000:01: resource 0 [io  0x8000-0x8fff]
[    0.748283] pci_bus 0000:01: resource 1 [mem 0x98700000-0x987fffff]
[    0.748285] pci_bus 0000:01: resource 2 [mem 0x98900000-0x98afffff 64bit pref]
[    0.748288] pci_bus 0000:02: resource 0 [io  0x5000-0x6fff]
[    0.748291] pci_bus 0000:02: resource 1 [mem 0x94700000-0x986fffff]
[    0.748293] pci_bus 0000:02: resource 2 [mem 0x98b00000-0x98cfffff 64bit pref]
[    0.748296] pci_bus 0000:43: resource 0 [io  0x3000-0x4fff]
[    0.748298] pci_bus 0000:43: resource 1 [mem 0x90700000-0x946fffff]
[    0.748301] pci_bus 0000:43: resource 2 [mem 0x98d00000-0x98efffff 64bit pref]
[    0.748304] pci_bus 0000:84: resource 0 [io  0x2000-0x2fff]
[    0.748306] pci_bus 0000:84: resource 1 [mem 0x90600000-0x906fffff]
[    0.748309] pci_bus 0000:84: resource 2 [mem 0x98f00000-0x990fffff pref]
[    0.748312] pci_bus 0000:85: resource 1 [mem 0x90500000-0x905fffff]
[    0.748314] pci_bus 0000:85: resource 4 [io  0x0000-0x0cf7]
[    0.748317] pci_bus 0000:85: resource 5 [io  0x0d00-0xffff]
[    0.748319] pci_bus 0000:85: resource 6 [mem 0x000a0000-0x000bffff]
[    0.748322] pci_bus 0000:85: resource 7 [mem 0x80000000-0xdfffffff]
[    0.748324] pci_bus 0000:85: resource 8 [mem 0xf0000000-0xfedfffff]
[    0.748327] pci_bus 0000:85: resource 9 [mem 0xfee01000-0xffffffff]
[    0.748362] NET: Registered protocol family 2
[    0.748442] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.748721] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.749200] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.749399] TCP: Hash tables configured (established 131072 bind 65536)
[    0.749405] TCP reno registered
[    0.749409] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.749420] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.749509] NET: Registered protocol family 1
[    0.749528] pci 0000:00:02.0: Boot video device
[    0.749810] PCI: CLS 64 bytes, default 64
[    0.750064] cpufreq-nforce2: No nForce2 chipset.
[    0.750219] audit: initializing netlink socket (disabled)
[    0.750231] type=2000 audit(1328357832.744:1): initialized
[    0.760138] highmem bounce pool size: 64 pages
[    0.760147] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.762155] VFS: Disk quotas dquot_6.5.2
[    0.762225] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.762962] fuse init (API version 7.16)
[    0.763073] msgmni has been set to 1704
[    0.763361] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.763396] io scheduler noop registered
[    0.763401] io scheduler deadline registered
[    0.763419] io scheduler cfq registered (default)
[    0.763542] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.763606] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.763694] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.763750] pcieport 0000:00:1c.2: irq 41 for MSI/MSI-X
[    0.763833] pcieport 0000:00:1c.4: setting latency timer to 64
[    0.763890] pcieport 0000:00:1c.4: irq 42 for MSI/MSI-X
[    0.763976] pcieport 0000:00:1c.5: setting latency timer to 64
[    0.764044] pcieport 0000:00:1c.5: irq 43 for MSI/MSI-X
[    0.764155] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.764185] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.764256] intel_idle: MWAIT substates: 0x3122220
[    0.764258] intel_idle: does not run on family 6 model 23
[    0.764429] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.764560] ACPI: AC Adapter [AC] (on-line)
[    0.764840] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input0
[    0.764850] ACPI: Sleep Button [SLPB]
[    0.764900] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    0.764953] ACPI: Lid Switch [LID]
[    0.765012] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.765019] ACPI: Power Button [PWRF]
[    0.765129] ACPI: Fan [FAN6] (off)
[    0.765196] ACPI: Fan [FAN7] (off)
[    0.765261] ACPI: Fan [FAN8] (off)
[    0.765325] ACPI: Fan [FAN9] (off)
[    0.765391] ACPI: Fan [FANA] (off)
[    0.765455] ACPI: Fan [FANB] (off)
[    0.765496] ACPI: Fan [FANG] (off)
[    0.765563] ACPI: Fan [FAN0] (off)
[    0.765630] ACPI: Fan [FAN1] (off)
[    0.765695] ACPI: Fan [FAN2] (off)
[    0.765760] ACPI: Fan [FAN3] (off)
[    0.765836] ACPI: Fan [FAN4] (off)
[    0.765900] ACPI: Fan [FAN5] (off)
[    0.766148] ACPI: acpi_idle registered with cpuidle
[    0.768747] Monitor-Mwait will be used to enter C-1 state
[    0.768777] Monitor-Mwait will be used to enter C-2 state
[    0.768784] Marking TSC unstable due to TSC halts in idle
[    1.306324] thermal LNXTHERM:00: registered as thermal_zone0
[    1.306330] ACPI: Thermal Zone [GFXZ] (16 C)
[    1.316070] thermal LNXTHERM:01: registered as thermal_zone1
[    1.316076] ACPI: Thermal Zone [DTSZ] (31 C)
[    1.321654] thermal LNXTHERM:02: registered as thermal_zone2
[    1.321660] ACPI: Thermal Zone [CPUZ] (34 C)
[    1.325163] thermal LNXTHERM:03: registered as thermal_zone3
[    1.325169] ACPI: Thermal Zone [SKNZ] (20 C)
[    1.336606] thermal LNXTHERM:04: registered as thermal_zone4
[    1.336612] ACPI: Thermal Zone [BATZ] (20 C)
[    1.340358] thermal LNXTHERM:05: registered as thermal_zone5
[    1.340363] ACPI: Thermal Zone [FDTZ] (35 C)
[    1.340401] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.340491] ERST: Table is not found!
[    1.340569] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.340696] isapnp: Scanning for PnP cards...
[    1.392748] ACPI: Battery Slot [BAT0] (battery present)
[    1.695717] isapnp: No Plug & Play device found
[    1.756481] Linux agpgart interface v0.103
[    1.756602] agpgart-intel 0000:00:00.0: Intel GM45 Chipset
[    1.756740] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    1.757769] agpgart-intel 0000:00:00.0: detected 65536K stolen memory
[    1.757898] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x80000000
[    1.759290] brd: module loaded
[    1.759945] loop: module loaded
[    1.760071] i2c-core: driver [adp5520] using legacy suspend method
[    1.760076] i2c-core: driver [adp5520] using legacy resume method
[    1.760188] ata_piix 0000:00:1f.2: version 2.13
[    1.760212] ata_piix 0000:00:1f.2: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    1.760223] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[    1.916041] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.916330] scsi0 : ata_piix
[    1.916436] scsi1 : ata_piix
[    1.917089] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x70f0 irq 14
[    1.917097] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x70f8 irq 15
[    1.917121] ata_piix 0000:00:1f.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.917132] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    2.072024] ata_piix 0000:00:1f.5: SCR access via SIDPR is available but doesn't work
[    2.072040] ata_piix 0000:00:1f.5: setting latency timer to 64
[    2.072305] scsi2 : ata_piix
[    2.072393] scsi3 : ata_piix
[    2.072445] ata3: SATA max UDMA/133 cmd 0x7108 ctl 0x712c bmdma 0x70d0 irq 18
[    2.072451] ata4: SATA max UDMA/133 cmd 0x7100 ctl 0x7128 bmdma 0x70d8 irq 18
[    2.072854] Fixed MDIO Bus: probed
[    2.072898] PPP generic driver version 2.4.2
[    2.072945] tun: Universal TUN/TAP device driver, 1.6
[    2.072950] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    2.073049] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.073075] ehci_hcd 0000:00:1a.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    2.073098] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    2.073102] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    2.073144] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    2.073273] ehci_hcd 0000:00:1a.7: debug port 1
[    2.077159] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
[    2.077175] ehci_hcd 0000:00:1a.7: irq 19, io mem 0x98804400
[    2.092017] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    2.092146] hub 1-0:1.0: USB hub found
[    2.092153] hub 1-0:1.0: 6 ports detected
[    2.092250] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 20 (level, low) -> IRQ 20
[    2.092267] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.092271] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.092320] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    2.092377] ehci_hcd 0000:00:1d.7: debug port 1
[    2.096265] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    2.096282] ehci_hcd 0000:00:1d.7: irq 20, io mem 0x98804000
[    2.112017] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    2.112132] hub 2-0:1.0: USB hub found
[    2.112138] hub 2-0:1.0: 6 ports detected
[    2.112226] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.112244] uhci_hcd: USB Universal Host Controller Interface driver
[    2.112272] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.112283] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    2.112286] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    2.112330] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    2.112391] uhci_hcd 0000:00:1a.0: irq 16, io base 0x000070a0
[    2.112536] hub 3-0:1.0: USB hub found
[    2.112544] hub 3-0:1.0: 2 ports detected
[    2.112625] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.112636] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    2.112640] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    2.112683] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    2.112743] uhci_hcd 0000:00:1a.1: irq 17, io base 0x00007080
[    2.112875] hub 4-0:1.0: USB hub found
[    2.112882] hub 4-0:1.0: 2 ports detected
[    2.112963] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.112973] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    2.112976] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    2.113021] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    2.116050] uhci_hcd 0000:00:1a.2: irq 18, io base 0x00007060
[    2.116188] hub 5-0:1.0: USB hub found
[    2.116195] hub 5-0:1.0: 2 ports detected
[    2.116274] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.116284] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.116288] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.116331] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    2.116379] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00007040
[    2.116509] hub 6-0:1.0: USB hub found
[    2.116515] hub 6-0:1.0: 2 ports detected
[    2.116596] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    2.116606] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.116610] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.116650] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    2.116707] uhci_hcd 0000:00:1d.1: irq 22, io base 0x00007020
[    2.116845] hub 7-0:1.0: USB hub found
[    2.116852] hub 7-0:1.0: 2 ports detected
[    2.116927] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.116937] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.116941] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.116985] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    2.117034] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00007000
[    2.117164] hub 8-0:1.0: USB hub found
[    2.117170] hub 8-0:1.0: 2 ports detected
[    2.117313] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.118968] i8042: Detected active multiplexing controller, rev 1.1
[    2.119731] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.119739] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    2.119777] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    2.119810] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    2.119841] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    2.119972] mousedev: PS/2 mouse device common for all mice
[    2.120168] rtc_cmos 00:08: RTC can wake from S4
[    2.120235] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    2.120270] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    2.120365] device-mapper: uevent: version 1.0.3
[    2.120456] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
[    2.120528] device-mapper: multipath: version 1.2.0 loaded
[    2.120534] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.120617] EISA: Probing bus 0 at eisa.0
[    2.120634] EISA: Cannot allocate resource for mainboard
[    2.120639] Cannot allocate resource for EISA slot 1
[    2.120643] Cannot allocate resource for EISA slot 2
[    2.120647] Cannot allocate resource for EISA slot 3
[    2.120651] Cannot allocate resource for EISA slot 4
[    2.120655] Cannot allocate resource for EISA slot 5
[    2.120659] Cannot allocate resource for EISA slot 6
[    2.120663] Cannot allocate resource for EISA slot 7
[    2.120667] Cannot allocate resource for EISA slot 8
[    2.120671] EISA: Detected 0 cards.
[    2.120796] cpuidle: using governor ladder
[    2.120902] cpuidle: using governor menu
[    2.121205] TCP cubic registered
[    2.121351] NET: Registered protocol family 10
[    2.121983] NET: Registered protocol family 17
[    2.122003] Registering the dns_resolver key type
[    2.123124] Using IPI No-Shortcut mode
[    2.123233] PM: Hibernation image not present or could not be loaded.
[    2.123243] registered taskstats version 1
[    2.123583]   Magic number: 0:266:278
[    2.123617] tty tty15: hash matches
[    2.123710] rtc_cmos 00:08: setting system clock to 2012-02-04 12:17:14 UTC (1328357834)
[    2.123717] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.123721] EDD information not available.
[    2.141921] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    2.392199] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.400323] ata1.00: ATA-8: WDC WD3200BEKT-60F3T1, 12.01A12, max UDMA/100
[    2.400335] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.408318] ata1.00: configured for UDMA/100
[    2.408506] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200BEKT-6 12.0 PQ: 0 ANSI: 5
[    2.408689] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.408692] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    2.408746] sd 0:0:0:0: [sda] Write Protect is off
[    2.408752] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.408801] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.514721]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 sda9 sda10 >
[    2.515489] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.592150] usb 2-5: new high speed USB device using ehci_hcd and address 4
[    2.944144] ata2: failed to resume link (SControl 0)
[    2.955226] ata2: SATA link down (SStatus 4 SControl 0)
[    2.955322] Freeing unused kernel memory: 700k freed
[    2.955629] Write protecting the kernel text: 5192k
[    2.955693] Write protecting the kernel read-only data: 2148k
[    2.980033] usb 6-1: new low speed USB device using uhci_hcd and address 2
[    2.982438] <30>udev[78]: starting version 167
[    3.063737] sky2: driver version 1.28
[    3.063784] sky2 0000:84:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.063802] sky2 0000:84:00.0: setting latency timer to 64
[    3.063836] sky2 0000:84:00.0: Yukon-2 Extreme chip revision 2
[    3.063976] sky2 0000:84:00.0: irq 44 for MSI/MSI-X
[    3.086522] sky2 0000:84:00.0: eth0: addr 18:a9:05:d2:cc:1c
[    3.136617] [drm] Initialized drm 1.1.0 20060810
[    3.190462] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.190474] i915 0000:00:02.0: setting latency timer to 64
[    3.213009] input: USB LaserStream(TM) Mouse as /devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1:1.0/input/input4
[    3.213234] generic-usb 0003:192F:0716.0001: input,hidraw0: USB HID v1.11 Mouse [USB LaserStream(TM) Mouse] on usb-0000:00:1d.0-1/input0
[    3.213426] usbcore: registered new interface driver usbhid
[    3.213431] usbhid: USB HID core driver
[    3.224496] i915 0000:00:02.0: irq 45 for MSI/MSI-X
[    3.224503] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    3.224510] [drm] Driver supports precise vblank timestamp query.
[    3.310010] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    3.400050] usb 6-2: new full speed USB device using uhci_hcd and address 3
[    3.582469] hub 6-2:1.0: USB hub found
[    3.584421] hub 6-2:1.0: 4 ports detected
[    3.748258] Console: switching to colour frame buffer device 170x48
[    3.752093] fb0: inteldrmfb frame buffer device
[    3.752124] drm: registered panic notifier
[    3.760737] acpi device:09: registered as cooling_device15
[    3.761203] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input5
[    3.761327] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    3.761716] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    3.813709] vesafb: framebuffer at 0x80000000, mapped to 0xf9000000, using 3072k, total 3072k
[    3.813766] vesafb: mode is 1024x768x32, linelength=4096, pages=0
[    3.813805] vesafb: scrolling: redraw
[    3.813830] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    3.813951] fb1: VESA VGA frame buffer device
[    4.172371] Btrfs loaded
[    4.179156] xor: automatically using best checksumming function: pIII_sse
[    4.196030]    pIII_sse  :  8349.000 MB/sec
[    4.196057] xor: using function: pIII_sse (8349.000 MB/sec)
[    4.198762] device-mapper: dm-raid45: initialized v0.2594b
[    4.482400] EXT4-fs (sda9): mounted filesystem with ordered data mode. Opts: (null)
[   18.686546] <30>udev[375]: starting version 167
[   18.705125] lp: driver loaded but no devices found
[   18.921491] hp_accel: laptop model unknown, using default axes configuration
[   18.922135] lis3lv02d: 8 bits sensor found
[   18.968115] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input6
[   18.968295] Registered led device: hp::hddprotect
[   18.968325] hp_accel: driver loaded
[   19.017880] EXT4-fs (sda9): re-mounted. Opts: errors=remount-ro
[   19.169850] EXT4-fs (sda8): mounted filesystem with ordered data mode. Opts: (null)
[   19.444135] cfg80211: Calling CRDA to update world regulatory domain
[   19.472319] input: HP WMI hotkeys as /devices/virtual/input/input7
[   19.547393] cfg80211: World regulatory domain updated:
[   19.547399] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   19.547403] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.547406] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   19.547409] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   19.547411] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.547414] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.553976] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   19.553980] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   19.553983] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   19.553986] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   19.553988] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   19.553990] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   19.553993] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   19.553995] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   19.553998] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   19.554000] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   19.554002] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   19.554005] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   19.554007] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   19.554010] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   19.554012] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   19.554015] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   19.554017] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   19.554020] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   19.554023] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   19.554025] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   19.554028] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   19.554030] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   19.554033] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   19.554035] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[   19.554038] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   19.554040] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[   19.554043] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   19.554046] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[   19.584675] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[   19.584685] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[   19.584695] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   19.584770] HDA Intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   19.584807] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   19.589610] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   19.592460] Registered led device: rt2800usb-phy0::radio
[   19.592554] Registered led device: rt2800usb-phy0::assoc
[   19.592633] Registered led device: rt2800usb-phy0::quality
[   19.593647] usbcore: registered new interface driver rt2800usb
[   19.594585] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   19.616288] rtusb init --->
[   19.617160] usbcore: registered new interface driver rt2870
[   19.668608] <30>udev[384]: renamed network interface wlan0 to wlan1
[   19.737523] sky2 0000:84:00.0: eth0: enabling interface
[   19.739324] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.856747] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04733/0xa40000/0xa0000
[   19.902975] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8
[   20.162348] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   20.919609] ppdev: user-space parallel port driver
[   21.054827] Intel AES-NI instructions are not detected.
[   21.065181] padlock_aes: VIA PadLock not detected.
[   21.092625] padlock_sha: VIA PadLock Hash Engine not detected.
[   21.100950] cfg80211: Found new beacon on frequency: 2467 MHz (Ch 12) on phy0
[   21.877300] Adding 4586520k swap on /dev/mapper/cryptswap1.  Priority:-1 extents:1 across:4586520k 
[   22.812280] vboxdrv: Found 2 processor cores.
[   22.813002] vboxdrv: fAsync=0 offMin=0x165 offMax=0x8bc
[   22.813682] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   22.813685] vboxdrv: Successfully loaded version 4.0.6 (interface 0x00180000).
[   26.713936] EXT4-fs (sda9): re-mounted. Opts: errors=remount-ro,commit=0
[   26.717118] EXT4-fs (sda8): re-mounted. Opts: commit=0
[   26.752806] ata2: exception Emask 0x10 SAct 0x0 SErr 0x4050000 action 0xf
[   26.752812] ata2: SError: { PHYRdyChg CommWake DevExch }
[   26.752824] ata2: hard resetting link
[   27.784051] ata2: failed to resume link (SControl 0)
[   27.795116] ata2: SATA link down (SStatus 4 SControl 0)
[   27.795141] ata2: EH complete
[   32.983932] ecryptfs_parse_options: eCryptfs: unrecognized option [ecryptfs_check_dev_ruid]
[   39.180638] Valid eCryptfs headers not found in file header region or xattr region
[   39.180643] Either the lower file is not in a valid eCryptfs format, or the key could not be retrieved. Plaintext passthrough mode is not enabled; returning -EIO
[   76.111975] wlan1: authenticate with 00:1e:58:34:5b:b3 (try 1)
[   76.113364] wlan1: authenticated
[   77.716973] wlan1: associate with 00:1e:58:34:5b:b3 (try 1)
[   77.722984] wlan1: RX AssocResp from 00:1e:58:34:5b:b3 (capab=0x431 status=0 aid=1)
[   77.722995] wlan1: associated
[   77.731305] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[   77.732156] cfg80211: Calling CRDA for country: NA
[   88.216047] wlan1: no IPv6 routers present
[   99.234293] exe (2535): /proc/2535/oom_adj is deprecated, please use /proc/2535/oom_score_adj instead.
[  612.023196] watwat[3477]: segfault at c361c1f0 ip 08048589 sp bfa14210 error 5 in watwat[8048000+1000]
[  624.159212] watwat[3495]: segfault at c11864c0 ip 08048589 sp bf9ce4e0 error 5 in watwat[8048000+1000]
[  678.569989] watwat[3591]: segfault at c0750480 ip 08048589 sp bfbf84a0 error 7 in watwat[8048000+1000]
[  703.639301] watwat[3632]: segfault at c09408bc ip 08048589 sp bff8c8d0 error 7 in watwat[8048000+1000]
[ 1128.958870] watwat[4630]: segfault at c2c700dc ip 08048589 sp bffe80f0 error 7 in watwat[8048000+1000]
[10895.384250] wlan1: deauthenticating from 00:1e:58:34:5b:b3 by local choice (reason=3)
[10896.002111] cfg80211: All devices are disconnected, going to restore regulatory settings
[10896.002117] cfg80211: Restoring regulatory settings
[10896.002124] cfg80211: Calling CRDA to update world regulatory domain
[10896.533217] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[10896.533221] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[10896.533224] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[10896.533226] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[10896.533229] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[10896.533232] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[10896.533234] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[10896.533237] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[10896.533239] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[10896.533242] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[10896.533244] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[10896.533247] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[10896.533249] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[10896.533252] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[10896.533254] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[10896.533257] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[10896.533259] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[10896.533262] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[10896.533264] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[10896.533267] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[10896.533269] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[10896.533272] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[10896.533274] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[10896.533277] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[10896.533279] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[10896.533282] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[10896.533284] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[10896.533287] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[10896.533290] cfg80211: World regulatory domain updated:
[10896.533292] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[10896.533295] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[10896.533297] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[10896.533300] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[10896.533303] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[10896.533305] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[10899.398795] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[10899.806617] render error detected, EIR: 0x00000010
[10899.806622]   IPEIR: 0x00000000
[10899.806624]   IPEHR: 0x00000000
[10899.806626]   INSTDONE: 0xfffffffe
[10899.806628]   INSTPS: 0x0001e000
[10899.806629]   INSTDONE1: 0xffffffff
[10899.806631]   ACTHD: 0x7e806450
[10899.806633] page table error
[10899.806635]   PGTBL_ER: 0x00000001
[10899.806638] [drm:i915_report_and_clear_eir] *ERROR* EIR stuck: 0x00000010, masking
[10900.240084] sky2 0000:84:00.0: eth0: disabling interface
[10900.247538] sky2 0000:84:00.0: eth0: enabling interface
[10900.248403] ADDRCONF(NETDEV_UP): eth0: link is not ready
[10927.329141] Valid eCryptfs headers not found in file header region or xattr region
[10927.329146] Either the lower file is not in a valid eCryptfs format, or the key could not be retrieved. Plaintext passthrough mode is not enabled; returning -EIO
[10967.585872] Valid eCryptfs headers not found in file header region or xattr region
[10967.585877] Either the lower file is not in a valid eCryptfs format, or the key could not be retrieved. Plaintext passthrough mode is not enabled; returning -EIO
[11230.477043] wlan1: authenticate with 00:1e:58:34:5b:b3 (try 1)
[11230.478427] wlan1: authenticated
[11232.086440] wlan1: associate with 00:1e:58:34:5b:b3 (try 1)
[11232.089081] wlan1: RX AssocResp from 00:1e:58:34:5b:b3 (capab=0x431 status=0 aid=1)
[11232.089086] wlan1: associated
[11232.097834] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[11232.099070] cfg80211: Calling CRDA for country: NA
[11242.744021] wlan1: no IPv6 routers present
[12857.085483] wlan1: deauthenticating from 00:1e:58:34:5b:b3 by local choice (reason=3)
[12858.738137] cfg80211: All devices are disconnected, going to restore regulatory settings
[12858.738144] cfg80211: Restoring regulatory settings
[12858.738154] cfg80211: Calling CRDA to update world regulatory domain
[12858.742640] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[12858.742644] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[12858.742647] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[12858.742650] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[12858.742652] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[12858.742655] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[12858.742657] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[12858.742660] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[12858.742662] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[12858.742665] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[12858.742667] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[12858.742670] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[12858.742672] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[12858.742675] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[12858.742677] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[12858.742680] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[12858.742683] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[12858.742685] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[12858.742688] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[12858.742690] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[12858.742693] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[12858.742695] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[12858.742698] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[12858.742700] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[12858.742703] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[12858.742705] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[12858.742708] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[12858.742711] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[12858.742714] cfg80211: World regulatory domain updated:
[12858.742715] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[12858.742718] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[12858.742721] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[12858.742723] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[12858.742726] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[12858.742729] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[12859.428583] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[12859.564092] sky2 0000:84:00.0: eth0: disabling interface
[12859.571250] sky2 0000:84:00.0: eth0: enabling interface
[12859.571666] ADDRCONF(NETDEV_UP): eth0: link is not ready
[12884.571323] Valid eCryptfs headers not found in file header region or xattr region
[12884.571328] Either the lower file is not in a valid eCryptfs format, or the key could not be retrieved. Plaintext passthrough mode is not enabled; returning -EIO
[12909.814746] wlan1: authenticate with 00:1e:58:34:5b:b3 (try 1)
[12909.816132] wlan1: authenticated
[12911.429998] wlan1: associate with 00:1e:58:34:5b:b3 (try 1)
[12911.432652] wlan1: RX AssocResp from 00:1e:58:34:5b:b3 (capab=0x431 status=0 aid=1)
[12911.432659] wlan1: associated
[12911.443497] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[12911.444774] cfg80211: Calling CRDA for country: NA
[12922.352245] wlan1: no IPv6 routers present
[13487.557677] wlan1: deauthenticating from 00:1e:58:34:5b:b3 by local choice (reason=3)
[13488.014051] cfg80211: All devices are disconnected, going to restore regulatory settings
[13488.014059] cfg80211: Restoring regulatory settings
[13488.014065] cfg80211: Calling CRDA to update world regulatory domain
[13488.018789] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[13488.018794] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[13488.018796] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[13488.018799] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[13488.018802] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[13488.018804] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[13488.018807] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[13488.018810] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[13488.018812] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[13488.018814] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[13488.018817] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[13488.018819] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[13488.018822] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[13488.018824] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[13488.018827] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[13488.018829] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[13488.018832] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[13488.018834] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[13488.018837] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[13488.018839] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[13488.018841] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[13488.018844] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[13488.018846] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[13488.018849] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[13488.018851] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[13488.018854] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[13488.018856] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[13488.018859] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[13488.018862] cfg80211: World regulatory domain updated:
[13488.018863] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[13488.018866] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[13488.018869] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[13488.018871] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[13488.018874] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[13488.018877] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[13490.630910] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[13490.760348] sky2 0000:84:00.0: eth0: disabling interface
[13490.770381] sky2 0000:84:00.0: eth0: enabling interface
[13490.770754] ADDRCONF(NETDEV_UP): eth0: link is not ready
[13502.268235] Valid eCryptfs headers not found in file header region or xattr region
[13502.268240] Either the lower file is not in a valid eCryptfs format, or the key could not be retrieved. Plaintext passthrough mode is not enabled; returning -EIO
```

---

