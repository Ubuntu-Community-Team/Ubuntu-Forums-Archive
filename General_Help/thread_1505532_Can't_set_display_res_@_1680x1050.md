---
title: "Can't set display res @ 1680x1050?"
date: 2010-06-09
forum: General Help
---

### Post by BMT22033 on 2010-06-09
I'm running 10.04 desktop on a Dell PowerEdge T710 connected to a Dell 22" LCD (E2210).  The T710 uses a Matrox G200eW chipset.  For some reason, I can't set the display resolution to the native res of my monitor (1680x1050).  For what it's worth, here are the contents of /var/log/Xorg.0.log:



X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux map-renderer-1 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=95546d53-2465-4192-84e4-ed7d2a6a8491 ro quiet splash
Build Date: 23 April 2010  05:11:46PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>) 
Current version of pixman: 0.16.4
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Jun  8 11:58:00 2010
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
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:6:3:0) 102b:0532:1028:029b Matrox Graphics, Inc. MGA G200eW WPCM450 rev 10, Mem @ 0xd5000000/8388608, 0xde7fc000/16384, 0xde800000/8388608, BIOS @ 0x????????/65536
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
(==) Matched mga as autoconfigured driver 0
(==) Matched vesa as autoconfigured driver 1
(==) Matched fbdev as autoconfigured driver 2
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "mga"
(II) Loading /usr/lib/xorg/modules/drivers/mga_drv.so
(II) Module mga: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.4.11
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
(II) MGA: driver for Matrox chipsets: mga2064w, mga1064sg, mga2164w,
	mga2164w AGP, mgag100, mgag100 PCI, mgag200, mgag200 PCI,
	mgag200 SE A PCI, mgag200 SE B PCI, mgag200 EV Maxim,
	mgag200 eW Nuvoton, mgag200eH, mgag400, mgag550
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 06@00:03:0
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.0.2
	ABI class: X.Org Video Driver, version 6.0
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.1.0
	ABI class: X.Org Video Driver, version 6.0
(--) MGA(0): Chipset: "mgag200 eW Nuvoton"
(--) MGA(0): Linear framebuffer at 0xD5000000
(--) MGA(0): MMIO registers at 0xDE7FC000
(--) MGA(0): Pseudo-DMA transfer window at 0xDE800000
(II) MGA(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
(==) MGA(0): Depth 24, (--) framebuffer bpp 32
(==) MGA(0): RGB weight 888
(**) MGA(0): Enabling KVM
(==) MGA(0): Using AGP 1x mode
(==) MGA(0): Using HW cursor
(==) MGA(0): Using XAA acceleration
(--) MGA(0): Video BIOS info block at offset 0x07D40
(==) MGA(0): VideoRAM: 8128 kByte
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) MGA(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) MGA(0): I2C bus "DDC P1" initialized.
(II) MGA(0): I2C device "DDC P1:ddc2" registered at address 0xA0.
(II) MGA(0): I2C device "DDC P1:EDID EEPROM interface" registered at address 0x62.
(II) MGA(0): I2C monitor info
(II) MGA(0): Manufacturer: DEL  Model: d036  Serial#: 808470092
(II) MGA(0): Year: 2010  Week: 18
(II) MGA(0): EDID Version: 1.3
(II) MGA(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) MGA(0): Sync:  Separate  Composite  SyncOnGreen
(II) MGA(0): Max Image Size [cm]: horiz.: 47  vert.: 30
(II) MGA(0): Gamma: 2.20
(II) MGA(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) MGA(0): Default color space is primary color space
(II) MGA(0): First detailed timing is preferred mode
(II) MGA(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) MGA(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
(II) MGA(0): Supported established timings:
(II) MGA(0): 720x400@70Hz
(II) MGA(0): 640x480@60Hz
(II) MGA(0): 640x480@75Hz
(II) MGA(0): 800x600@60Hz
(II) MGA(0): 800x600@75Hz
(II) MGA(0): 1024x768@60Hz
(II) MGA(0): 1024x768@75Hz
(II) MGA(0): 1280x1024@75Hz
(II) MGA(0): Manufacturer's mask: 0
(II) MGA(0): Supported standard timings:
(II) MGA(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) MGA(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) MGA(0): #2: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) MGA(0): Supported detailed timing:
(II) MGA(0): clock: 146.2 MHz   Image Size:  473 x 296 mm
(II) MGA(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) MGA(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) MGA(0): Serial No: T776R04P00FL
(II) MGA(0): Monitor name: DELL E2210
(II) MGA(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 160 MHz
(II) MGA(0): EDID (in hex):
(II) MGA(0): 	00ffffffffffff0010ac36d04c463030
(II) MGA(0): 	121401030e2f1e78eeee95a3544c9926
(II) MGA(0): 	0f5054a54b00714f8180b30001010101
(II) MGA(0): 	01010101010121399030621a274068b0
(II) MGA(0): 	3600d9281100001c000000ff00543737
(II) MGA(0): 	36523034503030464c0a000000fc0044
(II) MGA(0): 	454c4c2045323231300a2020000000fd
(II) MGA(0): 	00384b1e5310000a20202020202000f3
(II) MGA(0): end of monitor info
(II) MGA(0): EDID vendor "DEL", prod id 53302
(II) MGA(0): Using EDID range info for horizontal sync
(II) MGA(0): Using EDID range info for vertical refresh
(II) MGA(0): Printing DDC gathered Modelines:
(II) MGA(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) MGA(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) MGA(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) MGA(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) MGA(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) MGA(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) MGA(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) MGA(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) MGA(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) MGA(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) MGA(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(==) MGA(0): Using gamma correction (1.0, 1.0, 1.0)
(==) MGA(0): Min pixel clock is 18 MHz
(--) MGA(0): Max pixel clock is 203 MHz
(II) MGA(0): <default monitor>: Using hsync range of 30.00-83.00 kHz
(II) MGA(0): <default monitor>: Using vrefresh range of 56.00-75.00 Hz
(II) MGA(0): <default monitor>: Using maximum pixel clock of 160.00 MHz
(II) MGA(0): Estimated virtual size for aspect ratio 1.5667 is 1680x1050
(II) MGA(0): Clock range:  18.75 to 203.40 MHz
(II) MGA(0): Not using default mode "640x350" (vrefresh out of range)
(II) MGA(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) MGA(0): Not using default mode "640x400" (vrefresh out of range)
(II) MGA(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) MGA(0): Not using default mode "720x400" (vrefresh out of range)
(II) MGA(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) MGA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) MGA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) MGA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) MGA(0): Not using default mode "640x480" (vrefresh out of range)
(II) MGA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) MGA(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) MGA(0): Not using default mode "400x300" (doublescan mode not supported)
(II) MGA(0): Not using default mode "400x300" (doublescan mode not supported)
(II) MGA(0): Not using default mode "400x300" (doublescan mode not supported)
(II) MGA(0): Not using default mode "800x600" (vrefresh out of range)
(II) MGA(0): Not using default mode "400x300" (doublescan mode not supported)
(II) MGA(0): Not using default mode "1024x768" (vrefresh out of range)
(II) MGA(0): Not using default mode "512x384" (doublescan mode not supported)
(II) MGA(0): Not using default mode "512x384" (doublescan mode not supported)
(II) MGA(0): Not using default mode "512x384" (doublescan mode not supported)
(II) MGA(0): Not using default mode "512x384" (doublescan mode not supported)
(II) MGA(0): Not using default mode "1024x768" (vrefresh out of range)
(II) MGA(0): Not using default mode "512x384" (doublescan mode not supported)
(II) MGA(0): Not using default mode "576x432" (doublescan mode not supported)
(II) MGA(0): Not using default mode "640x480" (doublescan mode not supported)
(II) MGA(0): Not using default mode "1280x960" (mode requires too much memory bandwidth)
(II) MGA(0): Not using default mode "640x480" (doublescan mode not supported)
(II) MGA(0): Not using default mode "640x512" (doublescan mode not supported)
(II) MGA(0): Not using default mode "1280x1024" (mode requires too much memory bandwidth)
(II) MGA(0): Not using default mode "640x512" (doublescan mode not supported)
(II) MGA(0): Not using default mode "1280x1024" (mode requires too much memory bandwidth)
(II) MGA(0): Not using default mode "640x512" (doublescan mode not supported)
(II) MGA(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) MGA(0): Not using default mode "800x600" (doublescan mode not supported)
(II) MGA(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) MGA(0): Not using default mode "800x600" (doublescan mode not supported)
(II) MGA(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) MGA(0): Not using default mode "800x600" (doublescan mode not supported)
(II) MGA(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) MGA(0): Not using default mode "800x600" (doublescan mode not supported)
(II) MGA(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) MGA(0): Not using default mode "800x600" (doublescan mode not supported)
(II) MGA(0): Not using default mode "1792x1344" (insufficient memory for mode)
(II) MGA(0): Not using default mode "896x672" (doublescan mode not supported)
(II) MGA(0): Not using default mode "1792x1344" (insufficient memory for mode)
(II) MGA(0): Not using default mode "896x672" (doublescan mode not supported)
(II) MGA(0): Not using default mode "1856x1392" (insufficient memory for mode)
(II) MGA(0): Not using default mode "928x696" (doublescan mode not supported)
(II) MGA(0): Not using default mode "1856x1392" (insufficient memory for mode)
(II) MGA(0): Not using default mode "928x696" (doublescan mode not supported)
(II) MGA(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) MGA(0): Not using default mode "960x720" (doublescan mode not supported)
(II) MGA(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) MGA(0): Not using default mode "960x720" (doublescan mode not supported)
(II) MGA(0): Not using default mode "416x312" (doublescan mode not supported)
(II) MGA(0): Not using default mode "576x432" (doublescan mode not supported)
(II) MGA(0): Not using default mode "576x432" (doublescan mode not supported)
(II) MGA(0): Not using default mode "576x432" (doublescan mode not supported)
(II) MGA(0): Not using default mode "1152x864" (mode requires too much memory bandwidth)
(II) MGA(0): Not using default mode "576x432" (doublescan mode not supported)
(II) MGA(0): Not using default mode "1152x864" (mode requires too much memory bandwidth)
(II) MGA(0): Not using default mode "576x432" (doublescan mode not supported)
(II) MGA(0): Not using default mode "1152x864" (mode requires too much memory bandwidth)
(II) MGA(0): Not using default mode "576x432" (doublescan mode not supported)
(II) MGA(0): Not using default mode "1360x768" (width too large for virtual size)
(II) MGA(0): Not using default mode "680x384" (doublescan mode not supported)
(II) MGA(0): Not using default mode "1360x768" (width too large for virtual size)
(II) MGA(0): Not using default mode "680x384" (doublescan mode not supported)
(II) MGA(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) MGA(0): Not using default mode "700x525" (doublescan mode not supported)
(II) MGA(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) MGA(0): Not using default mode "700x525" (doublescan mode not supported)
(II) MGA(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) MGA(0): Not using default mode "700x525" (doublescan mode not supported)
(II) MGA(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) MGA(0): Not using default mode "700x525" (doublescan mode not supported)
(II) MGA(0): Not using default mode "1440x900" (width too large for virtual size)
(II) MGA(0): Not using default mode "720x450" (doublescan mode not supported)
(II) MGA(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) MGA(0): Not using default mode "800x512" (doublescan mode not supported)
(II) MGA(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) MGA(0): Not using default mode "840x525" (doublescan mode not supported)
(II) MGA(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) MGA(0): Not using default mode "840x525" (doublescan mode not supported)
(II) MGA(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) MGA(0): Not using default mode "840x525" (doublescan mode not supported)
(II) MGA(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) MGA(0): Not using default mode "840x525" (doublescan mode not supported)
(II) MGA(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) MGA(0): Not using default mode "840x525" (doublescan mode not supported)
(II) MGA(0): Not using default mode "1920x1080" (width too large for virtual size)
(II) MGA(0): Not using default mode "960x540" (doublescan mode not supported)
(II) MGA(0): Not using default mode "1920x1200" (insufficient memory for mode)
(II) MGA(0): Not using default mode "960x600" (doublescan mode not supported)
(II) MGA(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) MGA(0): Not using default mode "960x720" (doublescan mode not supported)
(II) MGA(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) MGA(0): Not using default mode "1024x768" (doublescan mode not supported)
(II) MGA(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) MGA(0): Not using default mode "1024x768" (doublescan mode not supported)
(II) MGA(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) MGA(0): Not using default mode "1024x768" (doublescan mode not supported)
(II) MGA(0): Not using driver mode "1680x1050" (width too large for virtual size)
(II) MGA(0): Not using driver mode "1280x1024" (mode requires too much memory bandwidth)
(WW) MGA(0): Shrinking virtual size estimate from 1680x1050 to 1280x1024
(--) MGA(0): Has SDRAM
(--) MGA(0): Virtual size is 1280x1024 (pitch 1280)
(**) MGA(0): *Driver mode "1280x1024": 108.0 MHz, 64.0 kHz, 60.0 Hz
(II) MGA(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(**) MGA(0): *Default mode "1280x1024": 108.0 MHz, 64.0 kHz, 60.0 Hz
(II) MGA(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(**) MGA(0): *Default mode "1280x960": 108.0 MHz, 60.0 kHz, 60.0 Hz
(II) MGA(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(**) MGA(0): *Driver mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
(II) MGA(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(**) MGA(0): *Default mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
(II) MGA(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(**) MGA(0): *Default mode "1152x864": 105.0 MHz, 67.6 kHz, 75.0 Hz
(II) MGA(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.6 kHz)
(**) MGA(0): *Default mode "1152x864": 96.8 MHz, 63.0 kHz, 70.0 Hz
(II) MGA(0): Modeline "1152x864"x70.0   96.77  1152 1224 1344 1536  864 865 868 900 -hsync +vsync (63.0 kHz)
(**) MGA(0): *Default mode "1152x864": 81.6 MHz, 53.7 kHz, 60.0 Hz
(II) MGA(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(**) MGA(0): *Driver mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
(II) MGA(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(**) MGA(0): *Driver mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) MGA(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) MGA(0): *Default mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
(II) MGA(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(**) MGA(0): *Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) MGA(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(**) MGA(0): *Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) MGA(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) MGA(0): *Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) MGA(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(**) MGA(0): *Driver mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) MGA(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) MGA(0): *Driver mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) MGA(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) MGA(0): *Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) MGA(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) MGA(0): *Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) MGA(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(**) MGA(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) MGA(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) MGA(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) MGA(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) MGA(0): *Driver mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) MGA(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) MGA(0): *Driver mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) MGA(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) MGA(0): *Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) MGA(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) MGA(0): *Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) MGA(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(**) MGA(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) MGA(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) MGA(0): *Driver mode "720x400": 28.3 MHz, 31.5 kHz, 70.1 Hz
(II) MGA(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(**) MGA(0): Display dimensions: (470, 300) mm
(**) MGA(0): DPI set to (69, 86)
(II) MGA(0): YDstOrg is set to 0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.2.1
	ABI class: X.Org Video Driver, version 6.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) UnloadModule: "vesa"
(II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(--) Depth 24 pixmap format is 32 bpp
(II) MGA(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(--) MGA(0): 64 DWORD fifo
(==) MGA(0): Default visual is TrueColor
(EE) MGA(0): Static buffer allocation failed, not initializing the DRI
(EE) MGA(0): Need at least 15360 kB video memory at this resolution, bit depth
(II) MGA(0): Using 601 lines for offscreen memory.
(II) MGA(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid filled trapezoids
	8x8 mono pattern filled rectangles
	8x8 mono pattern filled trapezoids
	Indirect CPU to Screen color expansion
	Screen to Screen color expansion
	Solid Lines
	Dashed Lines
	Scanline Image Writes
	Setting up tile and stipple cache:
		20 128x128 slots
		5 256x256 slots
(==) MGA(0): Backing store disabled
(==) MGA(0): Silken mouse enabled
(==) MGA(0): DPMS enabled
(WW) MGA(0): Direct rendering disabled
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
(II) AIGLX: Screen 0 is not DRI2 capable
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Dell Dell USB Optical Mouse (/dev/input/event2)
(**) Dell Dell USB Optical Mouse: Applying InputClass "evdev pointer catchall"
(**) Dell Dell USB Optical Mouse: always reports core events
(**) Dell Dell USB Optical Mouse: Device: "/dev/input/event2"
(II) Dell Dell USB Optical Mouse: Found 3 mouse buttons
(II) Dell Dell USB Optical Mouse: Found scroll wheel(s)
(II) Dell Dell USB Optical Mouse: Found relative axes
(II) Dell Dell USB Optical Mouse: Found x and y relative axes
(II) Dell Dell USB Optical Mouse: Configuring as mouse
(**) Dell Dell USB Optical Mouse: YAxisMapping: buttons 4 and 5
(**) Dell Dell USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Dell Dell USB Optical Mouse" (type: MOUSE)
(II) Dell Dell USB Optical Mouse: initialized for relative axes.
(II) config/udev: Adding input device Dell Dell USB Optical Mouse (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Dell Dell USB Keyboard (/dev/input/event3)
(**) Dell Dell USB Keyboard: Applying InputClass "evdev keyboard catchall"
(**) Dell Dell USB Keyboard: always reports core events
(**) Dell Dell USB Keyboard: Device: "/dev/input/event3"
(II) Dell Dell USB Keyboard: Found keys
(II) Dell Dell USB Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Dell Dell USB Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event1)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event1"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)

---

### Post by dino99 on 2010-06-09
check into : system admin hardware driver that mga driver is activated

if you have a xorg.conf file, rename or delete it

sudo rm -f /etc/X11/xorg.conf

from synaptic, you need : matroxset, mga-vid-source and xserver-xorg-video-mga installed

sudo dpkg-reconfigure xserver-xorg-video-mga

sudo apt-get install -f

---

### Post by BMT22033 on 2010-06-09
> **dino99 said:**
> check into : system admin hardware driver that mga driver is activated

That pops up a dialog window that says "Searching for available drivers..." and after several seconds, the Hardware Drivers window appears and states "No proprietary drivers are in use on this system."  So the mga driver isn't installed?  Doh!

> **dino99 said:**
> if you have a xorg.conf file, rename or delete it

I don't have a xorg.conf file.

> **dino99 said:**
> from synaptic, you need : matroxset, mga-vid-source and xserver-xorg-video-mga installed

xserver-xorg-video-mga was already installed but matroxset and mga-vid-source were not so I added them.

> **dino99 said:**
> sudo dpkg-reconfigure xserver-xorg-video-mga

I did this and then rebooted.  Unfortunately, it doesn't seem to have changed anything.  :-(  I REALLY appreciate your help, though!  Thank you!

---

### Post by dino99 on 2010-06-09
the next step is to look at the different logs:

- into /home: .xsession-errors (its a hidden file, ctrl+h to see it)

- into system admin logviewer: mainly xorg.log, system.log, user.log and messages.log

you might find some errors and/or warnings about X/mga/video, to be able to google around them

note: resolutions depend on graphic and display capabilities, and are limited by the poorest one

---

### Post by BMT22033 on 2010-06-09
Thanks for your quick response and additional suggestions.  I re-ran System -> Administration -> Hardware Drivers again and it still says "No proprietary drivers are in use on this system".  Should the mga driver be listed here if it's installed and working correctly?

---

### Post by dino99 on 2010-06-09
> **BMT22033 said:**
> Thanks for your quick response and additional suggestions.  I re-ran System -> Administration -> Hardware Drivers again and it still says "No proprietary drivers are in use on this system".  Should the mga driver be listed here if it's installed and working correctly? [COLOR="Blue"]yes[/COLOR]

goto synaptic and install: xserver-xorg-video-nouveau, maybe it'll give better graphics, but remember that your chipset is an oldish one and not designed for our today wide screens

---

### Post by BMT22033 on 2010-06-09
> **dino99 said:**
> [COLOR="Blue"]yes[/COLOR]

goto synaptic and install: xserver-xorg-video-nouveau, maybe it'll give better graphics, but remember that your chipset is an oldish one and not designed for our today wide screens

I looked at xserver-xorg-video-nouveau but it appears that it's just for some Nvidia chipsets?  Oh, well.  I'm out of time to fix this issue so I'll have to live with 1024x768 on a 22" display.  :-(  Thank you again for your help!

---

### Post by giorgio.v on 2010-07-31
Same monitor, same chipset, same problem!
I can't understand (also reeding many forums and post) if it's a  problem of the driver or if it is the video card not supporting wide  screen!
Same report from X log.

Can we try asking dell support?
Did you?

Giorgio

---

