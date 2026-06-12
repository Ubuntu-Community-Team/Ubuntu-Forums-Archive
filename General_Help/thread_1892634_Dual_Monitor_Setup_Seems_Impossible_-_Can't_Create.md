---
title: "Dual Monitor Setup Seems Impossible - Can't Create xorg.conf"
date: 2011-12-08
forum: General Help
---

### Post by hypertyper on 2011-12-08
I've read the threads I could find but I seem to have a different problem. I've tried using xrandr and putting a script into .xinitrc & .xprofile or into the startup applications. I have a shell script which changes the settings to what I want but I currently have to run it manually.

I can't create a xorg.conf file because I get an error message saying "Number of created screens does not match number of detected devices".

None of my google searches have been a help. I've been going at this for the last 8 hours. I'd appreciate any tips.

I'm using the onboard graphics of my i3-530 Intel processor.

My goal is to use two monitors. That's all. I'm surprised that it would be this hard.

Thanks

Here is the log for my attempt at creating an xorg.conf
```
[  2160.037] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[  2160.037] X Protocol Version 11, Revision 0
[  2160.037] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[  2160.037] Current Operating System: Linux SebXubuntu 3.0.0-13-generic-pae #22-Ubuntu SMP Wed Nov 2 15:17:35 UTC 2011 i686
[  2160.037] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-13-generic-pae root=UUID=4d9cc74f-f80a-4fa6-9a79-985ea0b48979 ro quiet splash vt.handoff=7
[  2160.037] Build Date: 19 October 2011  05:09:41AM
[  2160.037] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[  2160.037] Current version of pixman: 0.22.2
[  2160.037] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[  2160.037] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  2160.037] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Dec  8 17:06:32 2011
[  2160.038] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  2160.038] (==) No Layout section.  Using the first Screen section.
[  2160.038] (==) No screen section available. Using defaults.
[  2160.038] (**) |-->Screen "Default Screen Section" (0)
[  2160.038] (**) |   |-->Monitor "<default monitor>"
[  2160.038] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[  2160.038] (==) Automatically adding devices
[  2160.038] (==) Automatically enabling devices
[  2160.038] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  2160.038] 	Entry deleted from font path.
[  2160.038] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[  2160.038] 	Entry deleted from font path.
[  2160.038] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[  2160.038] 	Entry deleted from font path.
[  2160.038] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[  2160.038] 	Entry deleted from font path.
[  2160.038] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[  2160.038] 	Entry deleted from font path.
[  2160.038] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[  2160.038] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  2160.038] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[  2160.038] (II) Loader magic: 0x823ada0
[  2160.038] (II) Module ABI versions:
[  2160.038] 	X.Org ANSI C Emulation: 0.4
[  2160.038] 	X.Org Video Driver: 10.0
[  2160.038] 	X.Org XInput driver : 12.3
[  2160.038] 	X.Org Server Extension : 5.0
[  2160.039] (--) PCI:*(0:0:2:0) 8086:0042:1458:d000 rev 18, Mem @ 0xfb800000/4194304, 0xe0000000/268435456, I/O @ 0x0000ff00/8
[  2160.039] (II) Open ACPI successful (/var/run/acpid.socket)
[  2160.039] (II) LoadModule: "extmod"
[  2160.039] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[  2160.039] (II) Module extmod: vendor="X.Org Foundation"
[  2160.039] 	compiled for 1.10.4, module version = 1.0.0
[  2160.039] 	Module class: X.Org Server Extension
[  2160.039] 	ABI class: X.Org Server Extension, version 5.0
[  2160.039] (II) Loading extension MIT-SCREEN-SAVER
[  2160.039] (II) Loading extension XFree86-VidModeExtension
[  2160.039] (II) Loading extension XFree86-DGA
[  2160.039] (II) Loading extension DPMS
[  2160.039] (II) Loading extension XVideo
[  2160.039] (II) Loading extension XVideo-MotionCompensation
[  2160.039] (II) Loading extension X-Resource
[  2160.039] (II) LoadModule: "dbe"
[  2160.040] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[  2160.040] (II) Module dbe: vendor="X.Org Foundation"
[  2160.040] 	compiled for 1.10.4, module version = 1.0.0
[  2160.040] 	Module class: X.Org Server Extension
[  2160.040] 	ABI class: X.Org Server Extension, version 5.0
[  2160.040] (II) Loading extension DOUBLE-BUFFER
[  2160.040] (II) LoadModule: "glx"
[  2160.040] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[  2160.040] (II) Module glx: vendor="X.Org Foundation"
[  2160.040] 	compiled for 1.10.4, module version = 1.0.0
[  2160.040] 	ABI class: X.Org Server Extension, version 5.0
[  2160.040] (==) AIGLX enabled
[  2160.040] (II) Loading extension GLX
[  2160.040] (II) LoadModule: "record"
[  2160.040] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[  2160.040] (II) Module record: vendor="X.Org Foundation"
[  2160.040] 	compiled for 1.10.4, module version = 1.13.0
[  2160.040] 	Module class: X.Org Server Extension
[  2160.040] 	ABI class: X.Org Server Extension, version 5.0
[  2160.040] (II) Loading extension RECORD
[  2160.040] (II) LoadModule: "dri"
[  2160.040] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[  2160.040] (II) Module dri: vendor="X.Org Foundation"
[  2160.040] 	compiled for 1.10.4, module version = 1.0.0
[  2160.040] 	ABI class: X.Org Server Extension, version 5.0
[  2160.040] (II) Loading extension XFree86-DRI
[  2160.040] (II) LoadModule: "dri2"
[  2160.041] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[  2160.041] (II) Module dri2: vendor="X.Org Foundation"
[  2160.041] 	compiled for 1.10.4, module version = 1.2.0
[  2160.041] 	ABI class: X.Org Server Extension, version 5.0
[  2160.041] (II) Loading extension DRI2
[  2160.041] (==) Matched intel as autoconfigured driver 0
[  2160.041] (==) Matched vesa as autoconfigured driver 1
[  2160.041] (==) Matched fbdev as autoconfigured driver 2
[  2160.041] (==) Assigned the driver to the xf86ConfigLayout
[  2160.041] (II) LoadModule: "intel"
[  2160.041] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[  2160.041] (II) Module intel: vendor="X.Org Foundation"
[  2160.041] 	compiled for 1.10.4, module version = 2.15.901
[  2160.041] 	Module class: X.Org Video Driver
[  2160.041] 	ABI class: X.Org Video Driver, version 10.0
[  2160.041] (II) LoadModule: "vesa"
[  2160.041] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  2160.041] (II) Module vesa: vendor="X.Org Foundation"
[  2160.041] 	compiled for 1.10.2, module version = 2.3.0
[  2160.041] 	Module class: X.Org Video Driver
[  2160.041] 	ABI class: X.Org Video Driver, version 10.0
[  2160.041] (II) LoadModule: "fbdev"
[  2160.042] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  2160.042] (II) Module fbdev: vendor="X.Org Foundation"
[  2160.042] 	compiled for 1.10.0, module version = 0.4.2
[  2160.042] 	ABI class: X.Org Video Driver, version 10.0
[  2160.042] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
	Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
	Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
	Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
	Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[  2160.042] (II) VESA: driver for VESA chipsets: vesa
[  2160.042] (II) FBDEV: driver for framebuffer: fbdev
[  2160.042] (++) using VT number 7

[  2160.043] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[  2160.043] (WW) Falling back to old probe method for vesa
[  2160.043] (WW) Falling back to old probe method for fbdev
[  2160.043] (II) Loading sub module "fbdevhw"
[  2160.043] (II) LoadModule: "fbdevhw"
[  2160.044] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[  2160.044] (II) Module fbdevhw: vendor="X.Org Foundation"
[  2160.044] 	compiled for 1.10.4, module version = 0.0.2
[  2160.044] 	ABI class: X.Org Video Driver, version 10.0
[  2160.044] drmOpenDevice: node name is /dev/dri/card0
[  2160.044] drmOpenDevice: open result is 12, (OK)
[  2160.044] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[  2160.044] drmOpenDevice: node name is /dev/dri/card0
[  2160.044] drmOpenDevice: open result is 12, (OK)
[  2160.044] drmOpenByBusid: drmOpenMinor returns 12
[  2160.044] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[  2160.044] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[  2160.044] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[  2160.044] (==) intel(0): RGB weight 888
[  2160.044] (==) intel(0): Default visual is TrueColor
[  2160.044] (II) intel(0): Integrated Graphics Chipset: Intel(R) Clarkdale
[  2160.044] (--) intel(0): Chipset: "Clarkdale"
[  2160.044] (**) intel(0): Relaxed fencing enabled
[  2160.044] (**) intel(0): Wait on SwapBuffers? enabled
[  2160.044] (**) intel(0): Triple buffering? enabled
[  2160.044] (**) intel(0): Framebuffer tiled
[  2160.044] (**) intel(0): Pixmaps tiled
[  2160.044] (**) intel(0): 3D buffers tiled
[  2160.044] (**) intel(0): SwapBuffers wait enabled
[  2160.044] (==) intel(0): video overlay key set to 0x101fe
[  2160.101] (II) intel(0): Output VGA1 has no monitor section
[  2160.121] (II) intel(0): Output HDMI1 has no monitor section
[  2160.168] (II) intel(0): Output DP1 has no monitor section
[  2160.280] (II) intel(0): Output HDMI2 has no monitor section
[  2160.300] (II) intel(0): Output HDMI3 has no monitor section
[  2160.348] (II) intel(0): Output DP2 has no monitor section
[  2160.396] (II) intel(0): Output DP3 has no monitor section
[  2160.452] (II) intel(0): EDID for output VGA1
[  2160.452] (II) intel(0): Manufacturer: GSM  Model: 56f3  Serial#: 417073
[  2160.452] (II) intel(0): Year: 2009  Week: 4
[  2160.452] (II) intel(0): EDID Version: 1.3
[  2160.452] (II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[  2160.452] (II) intel(0): Sync:  Separate  SyncOnGreen
[  2160.452] (II) intel(0): Max Image Size [cm]: horiz.: 53  vert.: 30
[  2160.452] (II) intel(0): Gamma: 2.20
[  2160.452] (II) intel(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[  2160.452] (II) intel(0): First detailed timing is preferred mode
[  2160.452] (II) intel(0): redX: 0.635 redY: 0.342   greenX: 0.292 greenY: 0.611
[  2160.452] (II) intel(0): blueX: 0.147 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
[  2160.452] (II) intel(0): Supported established timings:
[  2160.452] (II) intel(0): 720x400@70Hz
[  2160.452] (II) intel(0): 640x480@60Hz
[  2160.452] (II) intel(0): 640x480@75Hz
[  2160.452] (II) intel(0): 800x600@56Hz
[  2160.452] (II) intel(0): 800x600@60Hz
[  2160.452] (II) intel(0): 800x600@75Hz
[  2160.452] (II) intel(0): 832x624@75Hz
[  2160.452] (II) intel(0): 1024x768@60Hz
[  2160.452] (II) intel(0): 1024x768@75Hz
[  2160.452] (II) intel(0): 1280x1024@75Hz
[  2160.452] (II) intel(0): 1152x864@75Hz
[  2160.452] (II) intel(0): Manufacturer's mask: 0
[  2160.452] (II) intel(0): Supported standard timings:
[  2160.452] (II) intel(0): #0: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[  2160.452] (II) intel(0): #1: hsize: 1280  vsize 800  refresh: 60  vid: 129
[  2160.452] (II) intel(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[  2160.452] (II) intel(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[  2160.452] (II) intel(0): Supported detailed timing:
[  2160.452] (II) intel(0): clock: 148.5 MHz   Image Size:  531 x 299 mm
[  2160.452] (II) intel(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[  2160.452] (II) intel(0): v_active: 1080  v_sync: 1083  v_sync_end 1088 v_blanking: 1125 v_border: 0
[  2160.452] (II) intel(0): Supported detailed timing:
[  2160.452] (II) intel(0): clock: 146.2 MHz   Image Size:  531 x 299 mm
[  2160.452] (II) intel(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
[  2160.452] (II) intel(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
[  2160.452] (II) intel(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 155 MHz
[  2160.452] (II) intel(0): Monitor name: W2453
[  2160.452] (II) intel(0): EDID (in hex):
[  2160.452] (II) intel(0): 	00ffffffffffff001e6df356315d0600
[  2160.453] (II) intel(0): 	041301036a351e78eaaec5a2574a9c25
[  2160.453] (II) intel(0): 	125054a76b80b30081008140714f0101
[  2160.453] (II) intel(0): 	010101010101023a801871382d40582c
[  2160.453] (II) intel(0): 	3500132b2100001e21399030621a2740
[  2160.453] (II) intel(0): 	68b03600132b2100001c000000fd0038
[  2160.453] (II) intel(0): 	4b1e530f000a202020202020000000fc
[  2160.453] (II) intel(0): 	0057323435330a20202020202020002d
[  2160.453] (II) intel(0): EDID vendor "GSM", prod id 22259
[  2160.453] (II) intel(0): Using EDID range info for horizontal sync
[  2160.453] (II) intel(0): Using EDID range info for vertical refresh
[  2160.453] (II) intel(0): Printing DDC gathered Modelines:
[  2160.453] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1083 1088 1125 +hsync +vsync (67.5 kHz)
[  2160.453] (II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[  2160.453] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  2160.453] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[  2160.453] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  2160.453] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  2160.453] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  2160.453] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[  2160.453] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  2160.453] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  2160.453] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[  2160.453] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  2160.453] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[  2160.453] (II) intel(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
[  2160.453] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[  2160.453] (II) intel(0): Printing probed modes for output VGA1
[  2160.453] (II) intel(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1083 1088 1125 +hsync +vsync (67.5 kHz)
[  2160.453] (II) intel(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[  2160.453] (II) intel(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[  2160.453] (II) intel(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[  2160.453] (II) intel(0): Modeline "1280x800"x59.8   83.50  1280 1352 1480 1680  800 803 809 831 +hsync -vsync (49.7 kHz)
[  2160.453] (II) intel(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[  2160.453] (II) intel(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
[  2160.453] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  2160.453] (II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[  2160.453] (II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  2160.453] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  2160.453] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[  2160.453] (II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  2160.453] (II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  2160.453] (II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  2160.474] (II) intel(0): EDID for output HDMI1
[  2160.520] (II) intel(0): EDID for output DP1
[  2160.632] (II) intel(0): EDID for output HDMI2
[  2160.632] (II) intel(0): Manufacturer: BNQ  Model: 7705  Serial#: 6931
[  2160.632] (II) intel(0): Year: 2007  Week: 7
[  2160.632] (II) intel(0): EDID Version: 1.3
[  2160.632] (II) intel(0): Digital Display Input
[  2160.632] (II) intel(0): Max Image Size [cm]: horiz.: 38  vert.: 30
[  2160.632] (II) intel(0): Gamma: 2.20
[  2160.632] (II) intel(0): DPMS capabilities: StandBy Suspend Off
[  2160.632] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[  2160.632] (II) intel(0): First detailed timing is preferred mode
[  2160.632] (II) intel(0): redX: 0.640 redY: 0.340   greenX: 0.290 greenY: 0.610
[  2160.632] (II) intel(0): blueX: 0.140 blueY: 0.070   whiteX: 0.310 whiteY: 0.330
[  2160.632] (II) intel(0): Supported established timings:
[  2160.632] (II) intel(0): 720x400@70Hz
[  2160.632] (II) intel(0): 640x480@60Hz
[  2160.632] (II) intel(0): 640x480@67Hz
[  2160.632] (II) intel(0): 640x480@72Hz
[  2160.632] (II) intel(0): 640x480@75Hz
[  2160.632] (II) intel(0): 800x600@60Hz
[  2160.632] (II) intel(0): 800x600@72Hz
[  2160.632] (II) intel(0): 800x600@75Hz
[  2160.632] (II) intel(0): 832x624@75Hz
[  2160.632] (II) intel(0): 1024x768@60Hz
[  2160.632] (II) intel(0): 1024x768@70Hz
[  2160.632] (II) intel(0): 1024x768@75Hz
[  2160.632] (II) intel(0): 1280x1024@75Hz
[  2160.632] (II) intel(0): 1152x864@75Hz
[  2160.632] (II) intel(0): Manufacturer's mask: 0
[  2160.632] (II) intel(0): Supported standard timings:
[  2160.632] (II) intel(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[  2160.632] (II) intel(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[  2160.632] (II) intel(0): #2: hsize: 1280  vsize 1024  refresh: 72  vid: 35969
[  2160.632] (II) intel(0): Supported detailed timing:
[  2160.632] (II) intel(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
[  2160.632] (II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[  2160.632] (II) intel(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[  2160.632] (II) intel(0): Supported detailed timing:
[  2160.632] (II) intel(0): clock: 25.2 MHz   Image Size:  376 x 301 mm
[  2160.632] (II) intel(0): h_active: 640  h_sync: 656  h_sync_end 752 h_blank_end 800 h_border: 0
[  2160.632] (II) intel(0): v_active: 350  v_sync: 387  v_sync_end 389 v_blanking: 449 v_border: 0
[  2160.632] (II) intel(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 83 kHz, PixClock max 145 MHz
[  2160.632] (II) intel(0): Monitor name: BenQ FP93GX+
[  2160.632] (II) intel(0): EDID (in hex):
[  2160.632] (II) intel(0): 	00ffffffffffff0009d10577131b0000
[  2160.632] (II) intel(0): 	0711010380261e78eac5c6a3574a9c23
[  2160.632] (II) intel(0): 	124f54bdef80714f8180818c01010101
[  2160.632] (II) intel(0): 	010101010101302a009851002a403070
[  2160.632] (II) intel(0): 	1300782d1100001ed50980a0205e6310
[  2160.632] (II) intel(0): 	10605208782d1100001a000000fd0038
[  2160.633] (II) intel(0): 	4c1f530e000a202020202020000000fc
[  2160.633] (II) intel(0): 	0042656e51204650393347582b0a0019
[  2160.633] (II) intel(0): Printing probed modes for output HDMI2
[  2160.633] (II) intel(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  2160.633] (II) intel(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[  2160.633] (II) intel(0): Modeline "1280x1024"x72.0  132.84  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.9 kHz)
[  2160.633] (II) intel(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[  2160.633] (II) intel(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
[  2160.633] (II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[  2160.633] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  2160.633] (II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[  2160.633] (II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[  2160.633] (II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  2160.633] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  2160.633] (II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
[  2160.633] (II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  2160.633] (II) intel(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[  2160.633] (II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  2160.633] (II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  2160.633] (II) intel(0): Modeline "640x350"x70.1   25.17  640 656 752 800  350 357 359 449 +hsync -vsync (31.5 kHz)
[  2160.654] (II) intel(0): EDID for output HDMI3
[  2160.700] (II) intel(0): EDID for output DP2
[  2160.748] (II) intel(0): EDID for output DP3
[  2160.748] (II) intel(0): Output VGA1 connected
[  2160.748] (II) intel(0): Output HDMI1 disconnected
[  2160.748] (II) intel(0): Output DP1 disconnected
[  2160.748] (II) intel(0): Output HDMI2 connected
[  2160.748] (II) intel(0): Output HDMI3 disconnected
[  2160.748] (II) intel(0): Output DP2 disconnected
[  2160.748] (II) intel(0): Output DP3 disconnected
[  2160.748] (II) intel(0): Using exact sizes for initial modes
[  2160.748] (II) intel(0): Output VGA1 using initial mode 1280x1024
[  2160.748] (II) intel(0): Output HDMI2 using initial mode 1280x1024
[  2160.748] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[  2160.748] (II) intel(0): Kernel page flipping support detected, enabling
[  2160.748] (**) intel(0): Display dimensions: (530, 300) mm
[  2160.748] (**) intel(0): DPI set to (61, 86)
[  2160.748] (II) Loading sub module "fb"
[  2160.748] (II) LoadModule: "fb"
[  2160.748] (II) Loading /usr/lib/xorg/modules/libfb.so
[  2160.748] (II) Module fb: vendor="X.Org Foundation"
[  2160.748] 	compiled for 1.10.4, module version = 1.0.0
[  2160.748] 	ABI class: X.Org ANSI C Emulation, version 0.4
[  2160.748] (II) Loading sub module "dri2"
[  2160.748] (II) LoadModule: "dri2"
[  2160.749] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[  2160.749] (II) Module dri2: vendor="X.Org Foundation"
[  2160.749] 	compiled for 1.10.4, module version = 1.2.0
[  2160.749] 	ABI class: X.Org Server Extension, version 5.0
[  2160.749] (II) UnloadModule: "vesa"
[  2160.749] (II) Unloading vesa
[  2160.749] (II) UnloadModule: "fbdev"
[  2160.749] (II) Unloading fbdev
[  2160.749] (II) UnloadModule: "fbdevhw"
[  2160.749] (II) Unloading fbdevhw
[  2160.749] (==) Depth 24 pixmap format is 32 bpp
[  2160.749] (II) intel(0): [DRI2] Setup complete
[  2160.749] (II) intel(0): [DRI2]   DRI driver: i965
[  2160.749] (II) intel(0): Allocated new frame buffer 1280x1024 stride 5120, tiled
[  2160.758] (II) UXA(0): Driver registered support for the following operations:
[  2160.758] (II)         solid
[  2160.758] (II)         copy
[  2160.758] (II)         composite (RENDER acceleration)
[  2160.758] (II)         put_image
[  2160.758] (II)         get_image
[  2160.758] (==) intel(0): Backing store disabled
[  2160.758] (==) intel(0): Silken mouse enabled
[  2160.758] (II) intel(0): Initializing HW Cursor
[  2161.136] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[  2161.136] (==) intel(0): DPMS enabled
[  2161.136] (==) intel(0): Intel XvMC decoder enabled
[  2161.136] (II) intel(0): Set up textured video
[  2161.136] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[  2161.136] (II) intel(0): direct rendering: DRI2 Enabled
[  2161.136] (==) intel(0): hotplug detection: "enabled"
[  2161.136] (--) RandR disabled
[  2161.136] (II) Initializing built-in extension Generic Event Extension
[  2161.136] (II) Initializing built-in extension SHAPE
[  2161.136] (II) Initializing built-in extension MIT-SHM
[  2161.136] (II) Initializing built-in extension XInputExtension
[  2161.136] (II) Initializing built-in extension XTEST
[  2161.136] (II) Initializing built-in extension BIG-REQUESTS
[  2161.136] (II) Initializing built-in extension SYNC
[  2161.136] (II) Initializing built-in extension XKEYBOARD
[  2161.136] (II) Initializing built-in extension XC-MISC
[  2161.136] (II) Initializing built-in extension SECURITY
[  2161.136] (II) Initializing built-in extension XINERAMA
[  2161.136] (II) Initializing built-in extension XFIXES
[  2161.137] (II) Initializing built-in extension RENDER
[  2161.137] (II) Initializing built-in extension RANDR
[  2161.137] (II) Initializing built-in extension COMPOSITE
[  2161.137] (II) Initializing built-in extension DAMAGE
[  2161.137] (II) Initializing built-in extension GESTURE
[  2161.153] (II) AIGLX: Trying DRI driver /usr/lib/i386-linux-gnu/dri/i965_dri.so
[  2161.156] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[  2161.156] (II) AIGLX: enabled GLX_INTEL_swap_event
[  2161.156] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[  2161.156] (II) AIGLX: enabled GLX_SGI_make_current_read
[  2161.156] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[  2161.156] (II) AIGLX: Loaded and initialized i965
[  2161.156] (II) GLX: Initialized DRI2 GL provider for screen 0
[  2161.156] (II) intel(0): Setting screen physical size to 338 x 270
[  2161.162] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  2161.168] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[  2161.169] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  2161.169] (II) LoadModule: "evdev"
[  2161.169] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  2161.169] (II) Module evdev: vendor="X.Org Foundation"
[  2161.169] 	compiled for 1.10.2, module version = 2.6.0
[  2161.169] 	Module class: X.Org XInput Driver
[  2161.169] 	ABI class: X.Org XInput driver, version 12.3
[  2161.169] (II) Using input driver 'evdev' for 'Power Button'
[  2161.169] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  2161.169] (**) Power Button: always reports core events
[  2161.169] (**) Power Button: Device: "/dev/input/event1"
[  2161.169] (--) Power Button: Found keys
[  2161.169] (II) Power Button: Configuring as keyboard
[  2161.169] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[  2161.169] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[  2161.169] (**) Option "xkb_rules" "evdev"
[  2161.169] (**) Option "xkb_model" "pc105"
[  2161.169] (**) Option "xkb_layout" "gb"
[  2161.171] (II) XKB: reuse xkmfile /var/lib/xkb/server-2B4266AA55228AE7D9557A18F1965DBA19850816.xkm
[  2161.173] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[  2161.173] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  2161.173] (II) Using input driver 'evdev' for 'Power Button'
[  2161.173] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  2161.173] (**) Power Button: always reports core events
[  2161.173] (**) Power Button: Device: "/dev/input/event0"
[  2161.173] (--) Power Button: Found keys
[  2161.173] (II) Power Button: Configuring as keyboard
[  2161.173] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[  2161.173] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[  2161.173] (**) Option "xkb_rules" "evdev"
[  2161.173] (**) Option "xkb_model" "pc105"
[  2161.173] (**) Option "xkb_layout" "gb"
[  2161.176] (II) config/udev: Adding input device sonixj (/dev/input/event4)
[  2161.176] (**) sonixj: Applying InputClass "evdev keyboard catchall"
[  2161.176] (II) Using input driver 'evdev' for 'sonixj'
[  2161.176] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  2161.176] (**) sonixj: always reports core events
[  2161.176] (**) sonixj: Device: "/dev/input/event4"
[  2161.176] (--) sonixj: Found keys
[  2161.176] (II) sonixj: Configuring as keyboard
[  2161.176] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.1/usb4/4-1/input/input4/event4"
[  2161.176] (II) XINPUT: Adding extended input device "sonixj" (type: KEYBOARD)
[  2161.176] (**) Option "xkb_rules" "evdev"
[  2161.176] (**) Option "xkb_model" "pc105"
[  2161.176] (**) Option "xkb_layout" "gb"
[  2161.176] (II) config/udev: Adding input device NOVATEK USB Keyboard (/dev/input/event2)
[  2161.176] (**) NOVATEK USB Keyboard: Applying InputClass "evdev keyboard catchall"
[  2161.176] (II) Using input driver 'evdev' for 'NOVATEK USB Keyboard'
[  2161.176] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  2161.176] (**) NOVATEK USB Keyboard: always reports core events
[  2161.176] (**) NOVATEK USB Keyboard: Device: "/dev/input/event2"
[  2161.176] (--) NOVATEK USB Keyboard: Found keys
[  2161.176] (II) NOVATEK USB Keyboard: Configuring as keyboard
[  2161.176] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.1/usb4/4-2/4-2:1.0/input/input2/event2"
[  2161.176] (II) XINPUT: Adding extended input device "NOVATEK USB Keyboard" (type: KEYBOARD)
[  2161.176] (**) Option "xkb_rules" "evdev"
[  2161.176] (**) Option "xkb_model" "pc105"
[  2161.177] (**) Option "xkb_layout" "gb"
[  2161.177] (II) config/udev: Adding input device NOVATEK USB Keyboard (/dev/input/event3)
[  2161.177] (**) NOVATEK USB Keyboard: Applying InputClass "evdev keyboard catchall"
[  2161.177] (II) Using input driver 'evdev' for 'NOVATEK USB Keyboard'
[  2161.177] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  2161.177] (**) NOVATEK USB Keyboard: always reports core events
[  2161.177] (**) NOVATEK USB Keyboard: Device: "/dev/input/event3"
[  2161.177] (--) NOVATEK USB Keyboard: Found 20 mouse buttons
[  2161.177] (--) NOVATEK USB Keyboard: Found keys
[  2161.177] (II) NOVATEK USB Keyboard: Configuring as mouse
[  2161.177] (II) NOVATEK USB Keyboard: Configuring as keyboard
[  2161.177] (**) NOVATEK USB Keyboard: YAxisMapping: buttons 4 and 5
[  2161.177] (**) NOVATEK USB Keyboard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  2161.177] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.1/usb4/4-2/4-2:1.1/input/input3/event3"
[  2161.177] (II) XINPUT: Adding extended input device "NOVATEK USB Keyboard" (type: KEYBOARD)
[  2161.177] (**) Option "xkb_rules" "evdev"
[  2161.177] (**) Option "xkb_model" "pc105"
[  2161.177] (**) Option "xkb_layout" "gb"
[  2161.178] (II) config/udev: Adding input device HDA Intel HDMI/DP,pcm=3 (/dev/input/event7)
[  2161.178] (II) No input driver/identifier specified (ignoring)
[  2161.179] (II) config/udev: Adding input device ROCCAT ROCCAT Kone (/dev/input/event5)
[  2161.179] (**) ROCCAT ROCCAT Kone: Applying InputClass "evdev pointer catchall"
[  2161.180] (II) Using input driver 'evdev' for 'ROCCAT ROCCAT Kone'
[  2161.180] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  2161.180] (**) ROCCAT ROCCAT Kone: always reports core events
[  2161.180] (**) ROCCAT ROCCAT Kone: Device: "/dev/input/event5"
[  2161.180] (--) ROCCAT ROCCAT Kone: Found 9 mouse buttons
[  2161.180] (--) ROCCAT ROCCAT Kone: Found scroll wheel(s)
[  2161.180] (--) ROCCAT ROCCAT Kone: Found relative axes
[  2161.180] (--) ROCCAT ROCCAT Kone: Found x and y relative axes
[  2161.180] (II) ROCCAT ROCCAT Kone: Configuring as mouse
[  2161.180] (II) ROCCAT ROCCAT Kone: Adding scrollwheel support
[  2161.180] (**) ROCCAT ROCCAT Kone: YAxisMapping: buttons 4 and 5
[  2161.180] (**) ROCCAT ROCCAT Kone: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  2161.180] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1:1.0/input/input5/event5"
[  2161.180] (II) XINPUT: Adding extended input device "ROCCAT ROCCAT Kone" (type: MOUSE)
[  2161.180] (II) ROCCAT ROCCAT Kone: initialized for relative axes.
[  2161.180] (**) ROCCAT ROCCAT Kone: (accel) keeping acceleration scheme 1
[  2161.180] (**) ROCCAT ROCCAT Kone: (accel) acceleration profile 0
[  2161.180] (**) ROCCAT ROCCAT Kone: (accel) acceleration factor: 2.000
[  2161.180] (**) ROCCAT ROCCAT Kone: (accel) acceleration threshold: 4
[  2161.180] (II) config/udev: Adding input device ROCCAT ROCCAT Kone (/dev/input/mouse0)
[  2161.180] (II) No input driver/identifier specified (ignoring)
[  2161.180] (II) config/udev: Adding input device ROCCAT ROCCAT Kone (/dev/input/event6)
[  2161.180] (**) ROCCAT ROCCAT Kone: Applying InputClass "evdev keyboard catchall"
[  2161.180] (II) Using input driver 'evdev' for 'ROCCAT ROCCAT Kone'
[  2161.180] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  2161.180] (**) ROCCAT ROCCAT Kone: always reports core events
[  2161.180] (**) ROCCAT ROCCAT Kone: Device: "/dev/input/event6"
[  2161.180] (--) ROCCAT ROCCAT Kone: Found keys
[  2161.180] (II) ROCCAT ROCCAT Kone: Configuring as keyboard
[  2161.180] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1:1.1/input/input6/event6"
[  2161.180] (II) XINPUT: Adding extended input device "ROCCAT ROCCAT Kone" (type: KEYBOARD)
[  2161.180] (**) Option "xkb_rules" "evdev"
[  2161.181] (**) Option "xkb_model" "pc105"
[  2161.181] (**) Option "xkb_layout" "gb"
[  2167.312] (II) XKB: reuse xkmfile /var/lib/xkb/server-7996F6726817F73651B9DE0FDA11E35FC4524568.xkm
[  2167.694] (II) intel(0): EDID vendor "BNQ", prod id 30469
[  2167.694] (II) intel(0): Using hsync ranges from config file
[  2167.694] (II) intel(0): Using vrefresh ranges from config file
[  2167.694] (II) intel(0): Printing DDC gathered Modelines:
[  2167.694] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  2167.694] (II) intel(0): Modeline "640x350"x0.0   25.17  640 656 752 800  350 387 389 449 +hsync -vsync (31.5 kHz)
[  2167.694] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  2167.694] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  2167.694] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[  2167.694] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[  2167.694] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  2167.694] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  2167.694] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[  2167.694] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  2167.694] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[  2167.694] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  2167.694] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[  2167.694] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  2167.694] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[  2167.694] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[  2167.694] (II) intel(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz)
[  2168.051] (II) intel(0): EDID vendor "BNQ", prod id 30469
[  2168.052] (II) intel(0): Using hsync ranges from config file
[  2168.052] (II) intel(0): Using vrefresh ranges from config file
[  2168.052] (II) intel(0): Printing DDC gathered Modelines:
[  2168.052] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  2168.052] (II) intel(0): Modeline "640x350"x0.0   25.17  640 656 752 800  350 387 389 449 +hsync -vsync (31.5 kHz)
[  2168.052] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  2168.052] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  2168.052] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[  2168.052] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[  2168.052] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  2168.052] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  2168.052] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[  2168.052] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  2168.052] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[  2168.052] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  2168.052] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[  2168.052] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  2168.052] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[  2168.052] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[  2168.052] (II) intel(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz)
[  2168.416] (II) intel(0): EDID vendor "BNQ", prod id 30469
[  2168.416] (II) intel(0): Using hsync ranges from config file
[  2168.416] (II) intel(0): Using vrefresh ranges from config file
[  2168.416] (II) intel(0): Printing DDC gathered Modelines:
[  2168.416] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  2168.416] (II) intel(0): Modeline "640x350"x0.0   25.17  640 656 752 800  350 387 389 449 +hsync -vsync (31.5 kHz)
[  2168.416] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  2168.416] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  2168.416] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[  2168.417] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[  2168.417] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  2168.417] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  2168.417] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[  2168.417] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  2168.417] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[  2168.417] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  2168.417] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[  2168.417] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  2168.417] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[  2168.417] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[  2168.417] (II) intel(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz)
[  2168.552] (II) intel(0): Allocated new frame buffer 3200x1080 stride 12800, tiled
[  2169.247] (II) intel(0): EDID vendor "BNQ", prod id 30469
[  2169.247] (II) intel(0): Using hsync ranges from config file
[  2169.247] (II) intel(0): Using vrefresh ranges from config file
[  2169.247] (II) intel(0): Printing DDC gathered Modelines:
[  2169.247] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  2169.247] (II) intel(0): Modeline "640x350"x0.0   25.17  640 656 752 800  350 387 389 449 +hsync -vsync (31.5 kHz)
[  2169.247] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  2169.247] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  2169.247] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[  2169.247] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[  2169.247] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  2169.247] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  2169.247] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[  2169.247] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  2169.247] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[  2169.247] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  2169.247] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[  2169.247] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  2169.247] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[  2169.247] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[  2169.247] (II) intel(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz)
[  2169.612] (II) intel(0): EDID vendor "BNQ", prod id 30469
[  2169.612] (II) intel(0): Using hsync ranges from config file
[  2169.612] (II) intel(0): Using vrefresh ranges from config file
[  2169.612] (II) intel(0): Printing DDC gathered Modelines:
[  2169.612] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  2169.612] (II) intel(0): Modeline "640x350"x0.0   25.17  640 656 752 800  350 387 389 449 +hsync -vsync (31.5 kHz)
[  2169.612] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  2169.612] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  2169.612] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[  2169.612] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[  2169.612] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  2169.612] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  2169.612] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[  2169.612] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  2169.612] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[  2169.612] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  2169.612] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[  2169.612] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  2169.612] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[  2169.612] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[  2169.612] (II) intel(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz)
[  2169.983] (II) intel(0): EDID vendor "BNQ", prod id 30469
[  2169.983] (II) intel(0): Using hsync ranges from config file
[  2169.983] (II) intel(0): Using vrefresh ranges from config file
[  2169.983] (II) intel(0): Printing DDC gathered Modelines:
[  2169.983] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  2169.983] (II) intel(0): Modeline "640x350"x0.0   25.17  640 656 752 800  350 387 389 449 +hsync -vsync (31.5 kHz)
[  2169.983] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  2169.983] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  2169.983] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[  2169.983] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[  2169.983] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  2169.983] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  2169.983] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[  2169.983] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  2169.983] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[  2169.983] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  2169.983] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[  2169.983] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  2169.983] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[  2169.983] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[  2169.983] (II) intel(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz)
[  2170.490] (II) intel(0): EDID vendor "BNQ", prod id 30469
[  2170.490] (II) intel(0): Using hsync ranges from config file
[  2170.490] (II) intel(0): Using vrefresh ranges from config file
[  2170.490] (II) intel(0): Printing DDC gathered Modelines:
[  2170.490] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  2170.490] (II) intel(0): Modeline "640x350"x0.0   25.17  640 656 752 800  350 387 389 449 +hsync -vsync (31.5 kHz)
[  2170.490] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  2170.490] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  2170.490] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[  2170.490] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[  2170.490] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  2170.490] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  2170.490] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[  2170.490] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  2170.490] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[  2170.490] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  2170.490] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[  2170.490] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  2170.490] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[  2170.490] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[  2170.490] (II) intel(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz)
[  2170.627] (II) XKB: reuse xkmfile /var/lib/xkb/server-7996F6726817F73651B9DE0FDA11E35FC4524568.xkm
[  2170.898] (II) intel(0): EDID vendor "BNQ", prod id 30469
[  2170.898] (II) intel(0): Using hsync ranges from config file
[  2170.898] (II) intel(0): Using vrefresh ranges from config file
[  2170.898] (II) intel(0): Printing DDC gathered Modelines:
[  2170.898] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  2170.898] (II) intel(0): Modeline "640x350"x0.0   25.17  640 656 752 800  350 387 389 449 +hsync -vsync (31.5 kHz)
[  2170.898] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  2170.898] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  2170.898] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[  2170.898] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[  2170.898] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  2170.898] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  2170.898] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[  2170.898] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  2170.898] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[  2170.898] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  2170.898] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[  2170.898] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  2170.898] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[  2170.899] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[  2170.899] (II) intel(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz)
[  2171.332] (II) intel(0): Allocated new frame buffer 1280x1024 stride 5120, tiled
[  2171.730] (II) intel(0): EDID vendor "BNQ", prod id 30469
[  2171.730] (II) intel(0): Using hsync ranges from config file
[  2171.730] (II) intel(0): Using vrefresh ranges from config file
[  2171.730] (II) intel(0): Printing DDC gathered Modelines:
[  2171.730] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  2171.730] (II) intel(0): Modeline "640x350"x0.0   25.17  640 656 752 800  350 387 389 449 +hsync -vsync (31.5 kHz)
[  2171.730] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  2171.730] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  2171.731] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[  2171.731] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[  2171.731] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  2171.731] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  2171.731] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[  2171.731] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  2171.731] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[  2171.731] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  2171.731] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[  2171.731] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  2171.731] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[  2171.731] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[  2171.731] (II) intel(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz)
[  2172.091] (II) intel(0): EDID vendor "BNQ", prod id 30469
[  2172.091] (II) intel(0): Using hsync ranges from config file
[  2172.091] (II) intel(0): Using vrefresh ranges from config file
[  2172.091] (II) intel(0): Printing DDC gathered Modelines:
[  2172.091] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  2172.091] (II) intel(0): Modeline "640x350"x0.0   25.17  640 656 752 800  350 387 389 449 +hsync -vsync (31.5 kHz)
[  2172.091] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  2172.091] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  2172.091] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[  2172.091] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[  2172.091] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  2172.091] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  2172.091] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[  2172.091] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  2172.091] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[  2172.091] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  2172.091] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[  2172.091] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  2172.091] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[  2172.091] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[  2172.091] (II) intel(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz)
[  2172.463] (II) intel(0): EDID vendor "BNQ", prod id 30469
[  2172.463] (II) intel(0): Using hsync ranges from config file
[  2172.463] (II) intel(0): Using vrefresh ranges from config file
[  2172.463] (II) intel(0): Printing DDC gathered Modelines:
[  2172.463] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  2172.463] (II) intel(0): Modeline "640x350"x0.0   25.17  640 656 752 800  350 387 389 449 +hsync -vsync (31.5 kHz)
[  2172.463] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  2172.464] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  2172.464] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[  2172.464] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[  2172.464] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  2172.464] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  2172.464] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[  2172.464] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  2172.464] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[  2172.464] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  2172.464] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[  2172.464] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  2172.464] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[  2172.464] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[  2172.464] (II) intel(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz)
[  2172.814] (II) intel(0): EDID vendor "BNQ", prod id 30469
[  2172.814] (II) intel(0): Using hsync ranges from config file
[  2172.814] (II) intel(0): Using vrefresh ranges from config file
[  2172.814] (II) intel(0): Printing DDC gathered Modelines:
[  2172.814] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  2172.814] (II) intel(0): Modeline "640x350"x0.0   25.17  640 656 752 800  350 387 389 449 +hsync -vsync (31.5 kHz)
[  2172.814] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  2172.814] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  2172.814] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[  2172.814] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[  2172.814] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  2172.814] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  2172.814] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[  2172.814] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  2172.814] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[  2172.814] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  2172.814] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[  2172.814] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  2172.814] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[  2172.814] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[  2172.814] (II) intel(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz)
[  2204.616] (II) intel(0): EDID vendor "BNQ", prod id 30469
[  2204.616] (II) intel(0): Using hsync ranges from config file
[  2204.616] (II) intel(0): Using vrefresh ranges from config file
[  2204.616] (II) intel(0): Printing DDC gathered Modelines:
[  2204.616] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  2204.616] (II) intel(0): Modeline "640x350"x0.0   25.17  640 656 752 800  350 387 389 449 +hsync -vsync (31.5 kHz)
[  2204.616] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  2204.616] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  2204.616] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[  2204.616] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[  2204.616] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  2204.616] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  2204.616] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[  2204.616] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  2204.616] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[  2204.616] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  2204.616] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[  2204.616] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  2204.616] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[  2204.616] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[  2204.616] (II) intel(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz)
[  2204.800] (II) intel(0): Allocated new frame buffer 3200x1080 stride 12800, tiled
[  2205.571] (II) intel(0): EDID vendor "BNQ", prod id 30469
[  2205.571] (II) intel(0): Using hsync ranges from config file
[  2205.571] (II) intel(0): Using vrefresh ranges from config file
[  2205.571] (II) intel(0): Printing DDC gathered Modelines:
[  2205.571] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  2205.571] (II) intel(0): Modeline "640x350"x0.0   25.17  640 656 752 800  350 387 389 449 +hsync -vsync (31.5 kHz)
[  2205.571] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  2205.571] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  2205.571] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[  2205.571] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[  2205.571] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  2205.571] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  2205.571] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[  2205.571] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  2205.571] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[  2205.571] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  2205.571] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[  2205.571] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  2205.571] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[  2205.571] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[  2205.571] (II) intel(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz)
[  2205.948] (II) intel(0): EDID vendor "BNQ", prod id 30469
[  2205.948] (II) intel(0): Using hsync ranges from config file
[  2205.948] (II) intel(0): Using vrefresh ranges from config file
[  2205.948] (II) intel(0): Printing DDC gathered Modelines:
[  2205.948] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  2205.948] (II) intel(0): Modeline "640x350"x0.0   25.17  640 656 752 800  350 387 389 449 +hsync -vsync (31.5 kHz)
[  2205.948] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  2205.948] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  2205.948] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[  2205.948] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[  2205.948] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  2205.948] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  2205.948] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[  2205.948] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  2205.948] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[  2205.948] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  2205.948] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[  2205.948] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  2205.948] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[  2205.948] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[  2205.948] (II) intel(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz)
[  2206.307] (II) intel(0): EDID vendor "BNQ", prod id 30469
[  2206.307] (II) intel(0): Using hsync ranges from config file
[  2206.307] (II) intel(0): Using vrefresh ranges from config file
[  2206.307] (II) intel(0): Printing DDC gathered Modelines:
[  2206.307] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  2206.307] (II) intel(0): Modeline "640x350"x0.0   25.17  640 656 752 800  350 387 389 449 +hsync -vsync (31.5 kHz)
[  2206.307] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  2206.307] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  2206.307] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[  2206.307] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[  2206.307] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  2206.307] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  2206.307] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[  2206.307] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  2206.307] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[  2206.307] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  2206.307] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[  2206.307] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  2206.307] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[  2206.307] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[  2206.307] (II) intel(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz)
[  2206.660] (II) intel(0): EDID vendor "BNQ", prod id 30469
[  2206.660] (II) intel(0): Using hsync ranges from config file
[  2206.660] (II) intel(0): Using vrefresh ranges from config file
[  2206.660] (II) intel(0): Printing DDC gathered Modelines:
[  2206.660] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  2206.660] (II) intel(0): Modeline "640x350"x0.0   25.17  640 656 752 800  350 387 389 449 +hsync -vsync (31.5 kHz)
[  2206.660] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  2206.660] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  2206.660] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[  2206.660] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[  2206.660] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  2206.660] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  2206.660] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[  2206.660] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  2206.660] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[  2206.660] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  2206.660] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[  2206.660] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  2206.660] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[  2206.660] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[  2206.660] (II) intel(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz)
[  2206.799] (II) XKB: reuse xkmfile /var/lib/xkb/server-7996F6726817F73651B9DE0FDA11E35FC4524568.xkm
[  2243.128] (II) AIGLX: Suspending AIGLX clients for VT switch
[  2277.032] (II) Open ACPI successful (/var/run/acpid.socket)
[  2277.032] (II) AIGLX: Resuming AIGLX clients after VT switch
[  2277.384] (II) intel(0): EDID vendor "BNQ", prod id 30469
[  2277.384] (II) intel(0): Using hsync ranges from config file
[  2277.384] (II) intel(0): Using vrefresh ranges from config file
[  2277.384] (II) intel(0): Printing DDC gathered Modelines:
[  2277.384] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  2277.384] (II) intel(0): Modeline "640x350"x0.0   25.17  640 656 752 800  350 387 389 449 +hsync -vsync (31.5 kHz)
[  2277.384] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  2277.384] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  2277.384] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[  2277.384] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[  2277.384] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  2277.384] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  2277.384] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[  2277.384] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  2277.384] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[  2277.384] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  2277.384] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[  2277.384] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  2277.384] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[  2277.385] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[  2277.385] (II) intel(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz)

```

---

### Post by Toz on 2011-12-08
> **hypertyper said:**
> I've read the threads I could find but I seem to have a different problem. I've tried using xrandr and putting a script into .xinitrc & .xprofile or into the startup applications. I have a shell script which changes the settings to what I want but I currently have to run it manually.
Did you make ~/.xprofile executable? Can you share the contents of your script and ~/.xprofile?

> I can't create a xorg.conf file because I get an error message saying "Number of created screens does not match number of detected devices".

None of my google searches have been a help. I've been going at this for the last 8 hours. I'd appreciate any tips.

I'm using the onboard graphics of my i3-530 Intel processor.

My goal is to use two monitors. That's all. I'm surprised that it would be this hard.

Thanks

Here is the log for my attempt at creating an xorg.conf
According to your log file:
> [ 2160.038] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
...its not using the xorg.conf file. In which directory did you put your xorg.conf file.

If you're using 11.10 (lightdm), have a look at this link: [http://askubuntu.com/questions/63681/how-can-i-make-xrandr-customization-permanent]("http://askubuntu.com/questions/63681/how-can-i-make-xrandr-customization-permanent"). There is a reply there about modifying lightdm.conf to run your xrandr commands.

---

### Post by hypertyper on 2011-12-09
Thanks for helping me out Toz. I'll try to explain:

my .xprofile (it is set to executable)
```
#!/bin/sh
xrandr --output DP3 --off --output DP2 --off --output DP1 --off --output HDMI3 --off --output HDMI2 --mode 1280x1024 --pos 0x0 --rotate normal --output HDMI1 --off --output VGA1 --mode 1920x1080 --pos 1280x0 --rotate normal

```

I don't currently have an xorg.conf file. I'm on 11.10 so it's using the new structure with separate files (or so I've read). My systems hasn't written the sub file in charge of monitors, so I don't have anything to edit. That's why I'm trying to create a xorg.conf file.

I tried adding the resolution script to the lightdm.conf file like the link you posted instructed me and that didn't do anything either. I can run the script from console and it works, so that's not the problem.

There is another suggestion in your link about writing the relevant xorg.conf entries manually. I'll see if I can do that.

---

### Post by Toz on 2011-12-09
After you login, have a look at your ~/.xsession-errors file to see if there is anything in there about xrandr - maybe a clue as to why its not working when run through .xprofile.

EDIT: You might also want to try this content in your .xprofile file:
```
#!/bin/bash
bash -c "xrandr --output DP3 --off --output DP2 --off --output DP1 --off --output HDMI3 --off --output HDMI2 --mode 1280x1024 --pos 0x0 --rotate normal --output HDMI1 --off --output VGA1 --mode 1920x1080 --pos 1280x0 --rotate normal"
```

---

### Post by hypertyper on 2011-12-09
I tried following the archlinux guide on setting up dual monitors but it doesn't mention how I find out what things are called in terms of drivers, devices, monitors etc.

If I could get my machine to write a xorg.conf I'd have something to edit. But noooo

I tried your .xprofile and it didn't work. I think he tries to set it, the screen goes blank for a second which doesn't otherwise happen, but then I still end up with the old crap setup.

There is no mention of xrandr in the xsessions-errors log. Here it is anyway:

```
Running X session wrapper
Loading profile from /etc/profile
Loading profile from /home/seb/.profile
Loading profile from /home/seb/.xprofile
Loading resource: /etc/X11/Xresources/x11-common
Loading X session script /etc/X11/Xsession.d/20x11-common_process-args
Loading X session script /etc/X11/Xsession.d/30x11-common_xresources
Loading X session script /etc/X11/Xsession.d/40x11-common_xsessionrc
Loading X session script /etc/X11/Xsession.d/50x11-common_determine-startup
Loading X session script /etc/X11/Xsession.d/52libcanberra-gtk3-module_add-to-gtk-modules
Loading X session script /etc/X11/Xsession.d/52libcanberra-gtk-module_add-to-gtk-modules
Loading X session script /etc/X11/Xsession.d/60x11-common_localhost
Loading X session script /etc/X11/Xsession.d/60x11-common_xdg_path
Loading X session script /etc/X11/Xsession.d/60xdg-user-dirs-update
Loading X session script /etc/X11/Xsession.d/70gconfd_path-on-session
Loading X session script /etc/X11/Xsession.d/75dbus_dbus-launch
Loading X session script /etc/X11/Xsession.d/80im-switch
Setting IM through im-switch for locale=en_GB.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
Loading X session script /etc/X11/Xsession.d/90consolekit
Loading X session script /etc/X11/Xsession.d/90x11-common_ssh-agent
Loading X session script /etc/X11/Xsession.d/99x11-common_start
/usr/bin/startxfce4: X server already running on display :0
xrdb:  "Xft.hinting" on line 13 overrides entry on line 6
xrdb:  "Xft.hintstyle" on line 14 overrides entry on line 7
ssh-agent is already running
GNOME_KEYRING_CONTROL=/tmp/keyring-8J7GHJ
SSH_AUTH_SOCK=/tmp/keyring-8J7GHJ/ssh
GPG_AGENT_INFO=/tmp/keyring-8J7GHJ/gpg:0:1
GNOME_KEYRING_CONTROL=/tmp/keyring-8J7GHJ
SSH_AUTH_SOCK=/tmp/keyring-8J7GHJ/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-8J7GHJ
SSH_AUTH_SOCK=/tmp/keyring-8J7GHJ/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-8J7GHJ
SSH_AUTH_SOCK=/tmp/keyring-8J7GHJ/ssh
GPG_AGENT_INFO=/tmp/keyring-8J7GHJ/gpg:0:1
xfdesktop[4264]: starting up

** (synapse:4268): WARNING **: desktop-file-service.vala:267: Desktop session type is not recognized, assuming GNOME.

(polkit-gnome-authentication-agent-1:4301): polkit-gnome-1-WARNING **: Failed to register client: The name org.gnome.SessionManager was not provided by any .service files
(synapse:4268): GtkHotkey-DEBUG: Listener Type: GtkHotkeyX11Listener
** Message: applet now removed from the notification area
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/blueman/plugins/BasePlugin.py", line 65, in _load
    self.on_load(parent)
  File "/usr/lib/python2.7/dist-packages/blueman/plugins/applet/PulseAudio.py", line 173, in on_load
    raise Exception("PulseAudio too old, required 0.9.15 or higher")
Exception: PulseAudio too old, required 0.9.15 or higher

(xfce4-indicator-plugin:4380): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GtkWidget'

(xfce4-indicator-plugin:4380): Gtk-CRITICAL **: IA__gtk_widget_set_name: assertion `GTK_IS_WIDGET (widget)' failed
(xfce4-indicator-plugin:4380): xfce4-indicator-plugin-DEBUG: Looking at Module: libsoundmenu.so
(xfce4-indicator-plugin:4380): xfce4-indicator-plugin-DEBUG: Loading Module: libsoundmenu.so

** (synapse:4268): WARNING **: desktop-file-service.vala:91: Unity is not understood

(synapse:4268): Gdk-CRITICAL **: IA__gdk_window_thaw_toplevel_updates_libgtk_only: assertion `private->update_and_descendants_freeze_count > 0' failed

(xfce4-indicator-plugin:4380): libindicator-WARNING **: IndicatorObject class does not have an accessible description.
(xfce4-indicator-plugin:4380): xfce4-indicator-plugin-DEBUG: Looking at Module: libmessaging.so
(xfce4-indicator-plugin:4380): xfce4-indicator-plugin-DEBUG: Loading Module: libmessaging.so

(xfce4-indicator-plugin:4380): libindicator-WARNING **: IndicatorObject class does not have an accessible description.
(xfce4-indicator-plugin:4380): xfce4-indicator-plugin-DEBUG: Looking at Module: libapplication.so
(xfce4-indicator-plugin:4380): xfce4-indicator-plugin-DEBUG: Loading Module: libapplication.so

(xfce4-indicator-plugin:4380): libxfce4panel-CRITICAL **: IA__xfce_panel_plugin_add_action_widget: assertion `GTK_IS_WIDGET (widget)' failed
** Message: using fallback from indicator to GtkStatusIcon
** Message: applet now embedded in the notification area
(xfce4-indicator-plugin:4380): Indicator-Sound-DEBUG: indicator-sound: new_volume_slider_widget
** Message: moving back from GtkStatusIcon to indicator
** Message: applet now removed from the notification area
(xfce4-indicator-plugin:4380): Indicator-Sound-DEBUG: indicator-sound: new_voip_slider_widget
(xfce4-indicator-plugin:4380): Indicator-Sound-DEBUG: indicator-sound: new_metadata_widget
(xfce4-indicator-plugin:4380): Indicator-Sound-DEBUG: new_metadata_widget ("gmusicbrowser")
(xfce4-indicator-plugin:4380): Indicator-Sound-DEBUG: indicator-sound: new_transport_bar() called 

(xfce4-indicator-plugin:4380): Gtk-CRITICAL **: IA__gtk_widget_realize: assertion `GTK_WIDGET_ANCHORED (widget) || GTK_IS_INVISIBLE (widget)' failed
(xfce4-indicator-plugin:4380): Indicator-Application-DEBUG: Connected to Application Indicator Service.
(xfce4-indicator-plugin:4380): Indicator-Messages-DEBUG: new_application_item ("Pidgin Internet Messenger")
(xfce4-indicator-plugin:4380): Indicator-Messages-DEBUG: new_application_item ("Set Up Mail...")
(xfce4-indicator-plugin:4380): Indicator-Application-DEBUG: Request current apps
(xfce4-indicator-plugin:4380): Indicator-Application-DEBUG: Building new application entry: :1.36  with icon: synapse at position 0
(xfce4-indicator-plugin:4380): Indicator-Application-DEBUG: Building new application entry: :1.44  with icon: software-update-urgent at position 1
(xfce4-indicator-plugin:4380): Indicator-Application-DEBUG: Building new application entry: :1.48  with icon: nm-device-wired at position 2

(update-manager:4463): Gtk-WARNING **: Attempting to add a widget with type aptdaemon+gtk3widgets+AptProgressDialog to a GtkWindow, but as a GtkBin subclass a GtkWindow can only contain one widget at a time; it already contains a widget of type GtkVBox
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
** (process:4275): DEBUG: desktop-launch-listener.vala:118: ran with uri: file:///home/seb/.xsession-errors
** (process:4275): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events

```

---

### Post by Toz on 2011-12-09
It looks like .xprofile is being processed before X is initialized. Try this. Create a script called something like **setup_xrandr** in your home directory with the following content:
```
#!/bin/bash
bash -c "xrandr --output DP3 --off --output DP2 --off --output DP1 --off --output HDMI3 --off --output HDMI2 --mode 1280x1024 --pos 0x0 --rotate normal --output HDMI1 --off --output VGA1 --mode 1920x1080 --pos 1280x0 --rotate normal"
```
...and make the file executable.

To make sure the script works, test it out by running (from a command line):
```
/home/seb/setup_xrandr
```

If it works, add the script to your startup files (Settings -> Settings Manager -> Session and startup -> Application Autostart).

EDIT: If that all works, and you want xrandr to run before the login screen, you can referencing the script to your /etc/lightdm/lightdm.conf file as shown in the: [http://askubuntu.com/questions/63681/how-can-i-make-xrandr-customization-permanent]("http://askubuntu.com/questions/63681/how-can-i-make-xrandr-customization-permanent") link. 

Specifically:

Copy the setup_randr file to /usr/local/bin (and make sure its still executable):
```
sudo cp /home/seb/setup_xrandr /usr/local/bin
sudo chmod +x /usr/local/bin/setup_xrandr
```
...edit the lightdm conf file
```
sudo leafpad /etc/lightdm/lightdm.conf
```
...with the following content:
```
[SeatDefaults]
user-session=xubuntu
greeter-session=lightdm-gtk-greeter
display-setup-script=/usr/local/bin/setup_xrandr
```
...and I guess reboot to test that it works.

---

### Post by hypertyper on 2011-12-10
I had performed this exact procedure before, same way you described, since that was suggested in your link but it doesn't make a difference. I did everything step by step a second time and it doesn't help. I got the spelling wrong in the lightdm.conf file which stopped it from starting. Then I corrected it so the machine boots but I still end up with a cloned screen and wrong resolution on the bigger one.

The script works, we know what. The conf file does get read, that's clear because it broke the whole thing when I got the name wrong.

My guess would be that something overrules the script at some point during the boot process? I thought that's why using the xorg.conf or 10-monitor.conf would be a good idea. I tried manufacturing one but that also doesn't affect where I end up after I boot.

:guitar:

---

### Post by Toz on 2011-12-10
Hmmm. Maybe xrandr can't find the display??? Try this script:
```
#!/bin/bash
export DISPLAY=:0
bash -c "xrandr --output DP3 --off --output DP2 --off --output DP1 --off --output HDMI3 --off --output HDMI2 --mode 1280x1024 --pos 0x0 --rotate normal --output HDMI1 --off --output VGA1 --mode 1920x1080 --pos 1280x0 --rotate normal"
```

Wherever you're running the script from, specify the script as:
```
/home/seb/setup_xrandr > /tmp/mylog 2>&1
```
...then after it runs look at **/tmp/mylog** to see if there is anything in there.

---

### Post by hypertyper on 2011-12-11
I'm confused. The script I'm using works when I simply execute it once I've logged in. Trying to use the same script via the lightdm.conf fails.

The last idea was executing the script once I'm logged in to see if it produces a log, correct? When I do that the log file stays empty.

Ubuntu has a tool which can simply take the screen settings and you apply them and it's done. Can I run that tool in Xubuntu? I know it has a lot of the ubuntu libraries so I thought I'd ask.

If I'm doing what you told me wrong please explain.

Side note: the file names you suggested for the scripts never ended in .sh but I always put mine as such. When I tried to use one without the .sh my machine refuses to boot. Just in case that's relevant.

Thanks for your time.

---

### Post by Toz on 2011-12-11
> **hypertyper said:**
> I'm confused. The script I'm using works when I simply execute it once I've logged in. Trying to use the same script via the lightdm.conf fails.
Thats odd. Because the same works for me when I run it from lightdm.conf.

> The last idea was executing the script once I'm logged in to see if it produces a log, correct? When I do that the log file stays empty.

Ubuntu has a tool which can simply take the screen settings and you apply them and it's done. Can I run that tool in Xubuntu? I know it has a lot of the ubuntu libraries so I thought I'd ask.
Which tool is this?

> If I'm doing what you told me wrong please explain.

Side note: the file names you suggested for the scripts never ended in .sh but I always put mine as such. When I tried to use one without the .sh my machine refuses to boot. Just in case that's relevant.
Doesn't matter as long as the script is executable.

> Thanks for your time.
Can you post back the contents of:
- /etc/lightdm/lightdm.conf
- /usr/local/bin/setup_xrandr
...and the results of:
```
ls -l /usr/local/bin/setup_xrandr
```

---

### Post by hypertyper on 2011-12-12
The monitor tool is included in ubuntu. I don't know the "proper" name for it. It's the default display configuration tool.

usr/local/bin/screen.sh
```
!/bin/bash
bash -c "xrandr --output DP3 --off --output DP2 --off --output DP1 --off --output HDMI3 --off --output HDMI2 --mode 1280x1024 --pos 0x0 --rotate normal --output HDMI1 --off --output VGA1 --mode 1920x1080 --pos 1280x0 --rotate normal"
```

lightdm.conf
```

[SeatDefaults]
autologin-guest=false
autologin-user=seb
autologin-user-timeout=0
autologin-session=lightdm-autologin
user-session=xubuntu
greeter-session=lightdm-gtk-greeter
display-setup-script=/usr/local/bin/screen.sh
#session-setup-script=/usr/local/bin/screen_setup.sh
#greeter-setup-script=/usr/local/bin/screen_setup.sh
```

ls -l
```
seb@sebXubuntu:~$ ls -l /usr/local/bin/screen.sh 
-rwxrwxrwx 1 seb seb 244 2011-12-11 21:01 /usr/local/bin/screen.sh

```

I'm using the onboard graphic via my i3 530 and the VGA and HDMI slot for one monitor each. Just throwing it out there. I tried booting into ubuntu 10.10, changed the monitors with the integrated tool and wrote a gconf.org but didn't get very far from there. It didn't seem to specify much about the monitor setup.

Thanks again for your time, I really appreciate it.

---

### Post by Toz on 2011-12-12
Try dropping the bash -c from your script (I don't actually use it it mine). When I suggested it I was thinking along a different set of lines. Change your screen.sh file to look like this:
```

#!/bin/bash
xrandr -q > /tmp/xrandr.log
xrandr --output DP3 --off --output DP2 --off --output DP1 --off --output HDMI3 --off --output HDMI2 --mode 1280x1024 --pos 0x0 --rotate normal --output HDMI1 --off --output VGA1 --mode 1920x1080 --pos 1280x0 --rotate normal
```
I also added in another line to dump the results of xrandr -q to a log file. If it still doesn't work, post back the contents of that log file. Lets see what its reporting.

EDIT: I just realized that the first line in your screen.sh was incorrect. You were missing the # mark. It should be:
```
#!/bin/bash
```

---

### Post by hypertyper on 2011-12-12
For reasons far beyond me, it is now working. I refuse to believe that it was simply the # that I was forgetting. I had tried several different versions of the script, mostly copy pasted and even tried executing them manually. It's the only reason that makes sense but I refuse to believe it.

The last version of your script didn't seem to produce a log so I've taken it out, since it's working now anyways.

I'm really happy it's working but annoyed that I don't know what I've been doing wrong. I refuse to believe it was the #.

Either way, thank you Toz for your persistence!

Edit: Clearly the universe is just fu**ing with me. I changed the lightdm.conf to this

```
[SeatDefaults]
autologin-guest=false
autologin-user=seb
autologin-user-timeout=0
autologin-session=lightdm-autologin
user-session=xubuntu
greeter-session=lightdm-gtk-greeter
#display-setup-script=/usr/local/bin/screen.sh
#session-setup-script=/usr/local/bin/screen.sh
#greeter-setup-script=/usr/local/bin/screen_setup.sh
```

and it still worked.

Then I renamed the screen.sh script and it's still working.  SERIOUSLY???

Unbelievably random behaviour from where I'm standing.

I double checked all the files I had messed with, there is no reason at all that it should be working, unless one of the scripts I've executed has a permanent effect somewhere.

---

### Post by Toz on 2011-12-12
I'm glad it worked. Can you please mark this thread as Solved from the Thread Tools link above?

---

### Post by hypertyper on 2011-12-13
I still have no idea why it's working. If I ever have to reinstall I'm screwed :|

I'll keep the methods you taught me in mind, if things brake I'll try those.

Cheers

---

