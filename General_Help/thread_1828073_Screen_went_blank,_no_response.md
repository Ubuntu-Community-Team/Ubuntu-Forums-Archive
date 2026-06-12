---
title: "Screen went blank, no response"
date: 2011-08-18
forum: General Help
---

### Post by holadebob on 2011-08-18
[COLOR="rgb(0, 100, 0)"][COLOR="rgb(0, 100, 0)"][COLOR="DarkGreen"]I'm really over my head here. I don't understand what's going on and don't know where to even start to find this problem. I restarted my computer and everything seems fine. If it is important to know what the computer was doing before it crashed, it was converting a mkv movie to avi. 
I have the syslog info....[/COLOR][/COLOR][/COLOR]

Aug 18 11:58:05 clark-office kernel: [91336.404020] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
Aug 18 11:58:05 clark-office kernel: [91336.404033] render error detected, EIR: 0x00000000
Aug 18 11:58:05 clark-office kernel: [91336.404060] [drm:i915_do_wait_request] *ERROR* i915_do_wait_request returns -5 (awaiting 7368989 at 7368988)
Aug 18 11:58:05 clark-office NetworkManager: <info>  (eth0): device state change: 8 -> 3 (reason 38)
Aug 18 11:58:05 clark-office NetworkManager: <info>  (eth0): deactivating device (reason: 38).
Aug 18 11:58:05 clark-office NetworkManager: <WARN>  check_one_route(): (eth0) error -34 returned from rtnl_route_del(): Sucess#012
Aug 18 11:58:05 clark-office avahi-daemon[758]: Withdrawing address record for 190.2.227.131 on eth0.
Aug 18 11:58:05 clark-office avahi-daemon[758]: Leaving mDNS multicast group on interface eth0.IPv4 with address 190.2.227.131.
Aug 18 11:58:05 clark-office avahi-daemon[758]: Interface eth0.IPv4 no longer relevant for mDNS.
Aug 18 11:58:07 clark-office acpid: client 859[0:0] has disconnected
Aug 18 11:58:07 clark-office acpid: client connected from 6659[0:0]
Aug 18 11:58:07 clark-office acpid: 1 client rule loaded
Aug 18 11:58:07 clark-office gdm-binary[753]: WARNING: GdmDisplay: display lasted 1.447740 seconds
Aug 18 11:58:07 clark-office acpid: client 6659[0:0] has disconnected
Aug 18 11:58:07 clark-office acpid: client connected from 6666[0:0]
Aug 18 11:58:07 clark-office acpid: 1 client rule loaded
Aug 18 11:58:08 clark-office gdm-binary[753]: WARNING: GdmDisplay: display lasted 0.466434 seconds
Aug 18 11:58:08 clark-office acpid: client 6666[0:0] has disconnected
Aug 18 11:58:08 clark-office acpid: client connected from 6673[0:0]
Aug 18 11:58:08 clark-office acpid: 1 client rule loaded
Aug 18 11:58:08 clark-office gdm-binary[753]: WARNING: GdmDisplay: display lasted 0.379403 seconds
Aug 18 11:58:08 clark-office acpid: client 6673[0:0] has disconnected
Aug 18 11:58:08 clark-office acpid: client connected from 6680[0:0]
Aug 18 11:58:08 clark-office acpid: 1 client rule loaded
Aug 18 11:58:08 clark-office gdm-binary[753]: WARNING: GdmDisplay: display lasted 0.386619 seconds
Aug 18 11:58:09 clark-office acpid: client 6680[0:0] has disconnected
Aug 18 11:58:09 clark-office acpid: client connected from 6687[0:0]
Aug 18 11:58:09 clark-office acpid: 1 client rule loaded
Aug 18 11:58:09 clark-office gdm-binary[753]: WARNING: GdmDisplay: display lasted 0.399594 seconds
Aug 18 11:58:09 clark-office acpid: client 6687[0:0] has disconnected
Aug 18 11:58:09 clark-office acpid: client connected from 6694[0:0]
Aug 18 11:58:09 clark-office acpid: 1 client rule loaded
Aug 18 11:58:09 clark-office gdm-binary[753]: WARNING: GdmDisplay: display lasted 0.379245 seconds
Aug 18 11:58:09 clark-office gdm-binary[753]: WARNING: GdmLocalDisplayFactory: maximum number of X display failures reached: check X server log for errors
Aug 18 11:58:09 clark-office init: gdm main process (753) terminated with status 1
Aug 18 11:58:10 clark-office acpid: client 6694[0:0] has disconnected
Aug 18 11:58:10 clark-office acpid: client connected from 6715[0:0]
Aug 18 11:58:10 clark-office acpid: 1 client rule loaded

[COLOR="DarkGreen"]Then I checked x.org.5.log and I got...[/COLOR]

(==) Log file: "/var/log/Xorg.5.log", Time: Thu Aug 18 11:58:09 2011
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(==) No screen section available. Using defaults.
(**) |-->Screen "Default Screen Section" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No monitor specified for screen "Default Screen Section".
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
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x81f1e80
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(--) using VT number 8

(--) PCI:*(0:0:2:0) 8086:2772:1458:d000 Intel Corporation 82945G/GZ Integrated Graphics Controller rev 2, Mem @ 0xe2000000/524288, 0xd0000000/268435456, 0xe2080000/262144, I/O @ 0x0000c000/8
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(==) Matched intel as autoconfigured driver 0
(==) Matched vesa as autoconfigured driver 1
(==) Matched fbdev as autoconfigured driver 2
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.9.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.4.1
	ABI class: X.Org Video Driver, version 6.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, Clarkdale, Arrandale
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 00@00:02:0
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.0.2
	ABI class: X.Org Video Driver, version 6.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 945G
(--) intel(0): Chipset: "945G"
(II) intel(0): Output VGA1 has no monitor section
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: GSM  Model: 448d  Serial#: 185932
(II) intel(0): Year: 2007  Week: 11
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) intel(0): Sync:  Separate  SyncOnGreen
(II) intel(0): Max Image Size [cm]: horiz.: 37  vert.: 23
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.609 redY: 0.339   greenX: 0.301 greenY: 0.594
(II) intel(0): blueX: 0.148 blueY: 0.089   whiteX: 0.312 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 720x400@70Hz
(II) intel(0): 640x480@60Hz
(II) intel(0): 640x480@75Hz
(II) intel(0): 800x600@56Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 800x600@75Hz
(II) intel(0): 832x624@75Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): 1024x768@70Hz
(II) intel(0): 1024x768@75Hz
(II) intel(0): 1280x1024@75Hz
(II) intel(0): 1152x864@75Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) intel(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) intel(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 106.5 MHz   Image Size:  370 x 232 mm
(II) intel(0): h_active: 1440  h_sync: 1520  h_sync_end 1672 h_blank_end 1904 h_border: 0
(II) intel(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 934 v_border: 0
(II) intel(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 140 MHz
(II) intel(0): Monitor name: L177WSB
(II) intel(0): Monitor name: 
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff001e6d8d444cd60200
(II) intel(0): 	0b1101036a251778ea30319c564d9826
(II) intel(0): 	165054a76f80950f81808140714f0101
(II) intel(0): 	0101010101019a29a0d0518422305098
(II) intel(0): 	360072e81000001c000000fd00384b1e
(II) intel(0): 	530e000a202020202020000000fc004c
(II) intel(0): 	3137375753420a2020202020000000fc
(II) intel(0): 	000a20202020202020202020202000b8
(II) intel(0): EDID vendor "GSM", prod id 17549
(II) intel(0): Using EDID range info for horizontal sync
(II) intel(0): Using EDID range info for vertical refresh
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1440x900"x75.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(II) intel(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Output VGA1 connected
(II) intel(0): Using exact sizes for initial modes
(II) intel(0): Output VGA1 using initial mode 1440x900
(II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
(==) intel(0): video overlay key set to 0x101fe
(**) intel(0): Display dimensions: (370, 230) mm
(**) intel(0): DPI set to (98, 99)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) UnloadModule: "vesa"
(II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(==) Depth 24 pixmap format is 32 bpp
(II) intel(0): [DRI2] Setup complete
(**) intel(0): Framebuffer compression disabled
(**) intel(0): Tiling enabled
(**) intel(0): SwapBuffers wait enabled
(==) intel(0): VideoRam: 262144 KB
(II) intel(0): Attempting memory allocation with tiled buffers.
(II) intel(0): Tiled allocation successful.
(II) UXA(0): Driver registered support for the following operations:
(II)         solid
(II)         copy
(II)         composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): No memory allocations

Fatal server error:
Failed to submit batchbuffer: Input/output error


[COLOR="DarkGreen"]Up until a couple of months ago when I started having the "running in low graphics mode, etc." problems, my 10.04 has been nothing but the epitomy of stable. I haven't changed any equipment in my system, so I can't understand what to do....

I have intel integrated 82945GC, using kernel i915.

The web search says it might be an x problem, but then after going to their recommended website x.org, I couldn't find anything to relate to this problem.

Thank you for any help thrown my way...[/COLOR]

---

### Post by holadebob on 2011-08-22
No help, so I decided to try Mint. A reinstall of 10.04 might have solved the problem, but I don't have the Low Graphic error problem on Mint either, so we'll see what happens. It seems to be working pretty smooth and fast. Green is ok. :)

---

