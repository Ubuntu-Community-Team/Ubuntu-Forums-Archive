---
title: "Blank Screen"
date: 2006-06-14
forum: General Help
---

### Post by ajcoll5 on 2006-06-14
I have a nVidia Geforce 4 MX440 and when I go to run/install it loads then a dash blinks at the top left then it goes blank, then my monitor says no signal but I can hear the welcome song. I have tryed to mess with the display settings at the bottom and no luck. I even checked the disk. I have the latest version version of Ubuntu. All the older versions of Ubuntu worked.

---

### Post by ajcoll5 on 2006-06-14
Changed the wording a little. Please Help!

---

### Post by mlind on 2006-06-14
You should be able to access text console using Ctrl+Alt+F1

Once you've logged in, reconfigure your xserver
```

sudo dpkg-reconfigure xserver-xorg

```

You should install nvidia's proprietary driver too, you can find numerous threads
how to do it by searching or use guide on [https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia)

If problem persists, please post your /var/log/Xorg.0.log after reconfiguring.

---

### Post by axcairns on 2006-06-21
I have the same problem as the original poster (screen blank with mx440). I installed Ubuntu Server then sudo apt-get install ubuntu-desktop. After reboot it tries to start X and the monitor switches off but I can still hear the bongoes that herald the display of the GDM login screen.

I tried sudo dpkg-reconfigure xserver-xorg and answered the questions as best I could. When I rebooted X threw an error.

Here is my Xorg.0.log -

```

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.12 i686
Current Operating System: Linux htpc 2.6.15-23-server #1 SMP Tue May 23 15:10:35 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Jun 21 22:23:20 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "IBM G74"
(**) |   |-->Device "Nvidia Geforce 4 MX440"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.8
	X.Org XInput driver : 0.5
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1106,3205 card 1106,3205 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,b198 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:09:0: chip 14f1,8800 card 18ac,db10 rev 05 class 04,00,00 hdr 80
(II) PCI: 00:09:2: chip 14f1,8802 card 18ac,db10 rev 05 class 04,80,00 hdr 80
(II) PCI: 00:10:0: chip 1106,3038 card 1106,3038 rev 80 class 0c,03,00 hdr 80
(II) PCI: 00:10:1: chip 1106,3038 card 1106,3038 rev 80 class 0c,03,00 hdr 80
(II) PCI: 00:10:2: chip 1106,3038 card 1106,3038 rev 80 class 0c,03,00 hdr 80
(II) PCI: 00:10:3: chip 1106,3104 card 1106,3104 rev 82 class 0c,03,20 hdr 00
(II) PCI: 00:11:0: chip 1106,3177 card 1106,3177 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:11:1: chip 1106,0571 card 1106,0571 rev 06 class 01,01,8a hdr 00
(II) PCI: 00:11:5: chip 1106,3059 card 1695,3005 rev 50 class 04,01,00 hdr 00
(II) PCI: 00:12:0: chip 1106,3065 card 1695,3005 rev 74 class 02,00,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0181 card 0000,0000 rev a4 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xe8000000 - 0xe9ffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI: (0:9:0) unknown vendor (0x14f1) unknown chipset (0x8800) rev 5, Mem @ 0xea000000/24
(--) PCI:*(1:0:0) nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] rev 164, Mem @ 0xe8000000/24, 0xe0000000/27
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xd8000000 from 0xdfffffff to 0xd7ffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xec001000 - 0xec0010ff (0x100) MX[B]
	[1] -1	0	0xec000000 - 0xec0000ff (0x100) MX[B]
	[2] -1	0	0xeb000000 - 0xebffffff (0x1000000) MX[B]
	[3] -1	0	0xd8000000 - 0xd7ffffff (0x0) MX[B]O
	[4] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[5] -1	0	0xe8000000 - 0xe8ffffff (0x1000000) MX[B](B)
	[6] -1	0	0xea000000 - 0xeaffffff (0x1000000) MX[B](B)
	[7] -1	0	0x0000e500 - 0x0000e5ff (0x100) IX[B]
	[8] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[9] -1	0	0x0000e300 - 0x0000e30f (0x10) IX[B]
	[10] -1	0	0x0000e200 - 0x0000e21f (0x20) IX[B]
	[11] -1	0	0x0000e100 - 0x0000e11f (0x20) IX[B]
	[12] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xec001000 - 0xec0010ff (0x100) MX[B]
	[1] -1	0	0xec000000 - 0xec0000ff (0x100) MX[B]
	[2] -1	0	0xeb000000 - 0xebffffff (0x1000000) MX[B]
	[3] -1	0	0xd8000000 - 0xd7ffffff (0x0) MX[B]O
	[4] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[5] -1	0	0xe8000000 - 0xe8ffffff (0x1000000) MX[B](B)
	[6] -1	0	0xea000000 - 0xeaffffff (0x1000000) MX[B](B)
	[7] -1	0	0x0000e500 - 0x0000e5ff (0x100) IX[B]
	[8] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[9] -1	0	0x0000e300 - 0x0000e30f (0x10) IX[B]
	[10] -1	0	0x0000e200 - 0x0000e21f (0x20) IX[B]
	[11] -1	0	0x0000e100 - 0x0000e11f (0x20) IX[B]
	[12] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xec001000 - 0xec0010ff (0x100) MX[B]
	[5] -1	0	0xec000000 - 0xec0000ff (0x100) MX[B]
	[6] -1	0	0xeb000000 - 0xebffffff (0x1000000) MX[B]
	[7] -1	0	0xd8000000 - 0xd7ffffff (0x0) MX[B]O
	[8] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0xe8000000 - 0xe8ffffff (0x1000000) MX[B](B)
	[10] -1	0	0xea000000 - 0xeaffffff (0x1000000) MX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x0000e500 - 0x0000e5ff (0x100) IX[B]
	[14] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[15] -1	0	0x0000e300 - 0x0000e30f (0x10) IX[B]
	[16] -1	0	0x0000e200 - 0x0000e21f (0x20) IX[B]
	[17] -1	0	0x0000e100 - 0x0000e11f (0x20) IX[B]
	[18] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.0.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions/libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "nv"
(II) Loading /usr/lib/xorg/modules/drivers/nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 6.99.99.904, module version = 1.0.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) Wacom driver level: 47-0.7.2 $
(II) NV: driver for NVIDIA chipsets: RIVA 128, RIVA TNT, RIVA TNT2,
	Unknown TNT2, Vanta, RIVA TNT2 Ultra, RIVA TNT2 Model 64,
	Aladdin TNT2, GeForce 256, GeForce DDR, Quadro, GeForce2 MX/MX 400,
	GeForce2 MX 100/200, GeForce2 Go, Quadro2 MXR/EX/Go,
	GeForce2 Integrated GPU, GeForce2 GTS, GeForce2 Ti, GeForce2 Ultra,
	Quadro2 Pro, GeForce4 MX 460, GeForce4 MX 440, GeForce4 MX 420,
	GeForce4 MX 440-SE, GeForce4 440 Go, GeForce4 420 Go,
	GeForce4 420 Go 32M, GeForce4 460 Go, Quadro4 550 XGL,
	GeForce4 440 Go 64M, Quadro NVS, Quadro4 500 GoGL,
	GeForce4 410 Go 16M, GeForce4 MX 440 with AGP8X,
	GeForce4 MX 440SE with AGP8X, GeForce4 MX 420 with AGP8X,
	GeForce4 MX 4000, GeForce4 448 Go, GeForce4 488 Go, Quadro4 580 XGL,
	Quadro4 NVS 280 SD, Quadro4 380 XGL, Quadro NVS 50 PCI,
	GeForce4 448 Go, GeForce4 MX Integrated GPU, GeForce3,
	GeForce3 Ti 200, GeForce3 Ti 500, Quadro DCC, GeForce4 Ti 4600,
	GeForce4 Ti 4400, GeForce4 Ti 4200, Quadro4 900 XGL, Quadro4 750 XGL,
	Quadro4 700 XGL, GeForce4 Ti 4800, GeForce4 Ti 4200 with AGP8X,
	GeForce4 Ti 4800 SE, GeForce4 4200 Go, Quadro4 700 GoGL,
	Quadro4 980 XGL, Quadro4 780 XGL, GeForce FX 5800 Ultra,
	GeForce FX 5800, Quadro FX 2000, Quadro FX 1000,
	GeForce FX 5600 Ultra, GeForce FX 5600, GeForce FX 5600XT,
	GeForce FX Go5600, GeForce FX Go5650, Quadro FX Go700,
	GeForce FX 5200, GeForce FX 5200 Ultra, GeForce FX 5200,
	GeForce FX 5200LE, GeForce FX Go5200, GeForce FX Go5250,
	GeForce FX 5500, GeForce FX 5100, GeForce FX Go5200 32M/64M,
	Quadro NVS 55/280 PCI, Quadro FX 500/600 PCI,
	GeForce FX Go53xx Series, GeForce FX Go5100, GeForce FX 5900 Ultra,
	GeForce FX 5900, GeForce FX 5900XT, GeForce FX 5950 Ultra,
	GeForce FX 5900ZT, Quadro FX 3000, Quadro FX 700,
	GeForce FX 5700 Ultra, GeForce FX 5700, GeForce FX 5700LE,
	GeForce FX 5700VE, GeForce FX Go5700, GeForce FX Go5700,
	Quadro FX Go1000, Quadro FX 1100, GeForce 6800 Ultra, GeForce 6800,
	GeForce 6800 LE, GeForce 6800 XE, GeForce 6800 GT, GeForce 6800 GT,
	GeForce 6800 GS, GeForce 6800 XT, Quadro FX 4000, GeForce 6800 GS,
	GeForce 6800, GeForce 6800 LE, GeForce 6800 XT, GeForce Go 6800,
	GeForce Go 6800 Ultra, Quadro FX Go1400, Quadro FX 3450/4000 SDI,
	Quadro FX 1400, GeForce 6600 GT, GeForce 6600, GeForce 6600 LE,
	GeForce 6600 VE, GeForce Go 6600, GeForce 6610 XL,
	GeForce Go 6600 TE/6200 TE, GeForce 6700 XL, GeForce Go 6600,
	GeForce Go 6600 GT, Quadro FX 540, GeForce 6200, GeForce 6500,
	GeForce 6200 TurboCache(TM), GeForce 6200SE TurboCache(TM),
	GeForce 6200 LE, GeForce Go 6200, Quadro NVS 285, GeForce Go 6400,
	GeForce Go 6200, GeForce Go 6400, GeForce 6250, GeForce 6800,
	GeForce 6800 LE, GeForce 6800 GT, GeForce 6800 XT, GeForce 6200,
	GeForce 7800 GTX, GeForce 7800 GTX, GeForce 7800 GT, GeForce 7800 GS,
	GeForce 7800 SLI, GeForce Go 7800, GeForce Go 7800 GTX,
	Quadro FX 4500, GeForce 7300 LE, GeForce Go 7200, GeForce Go 7300,
	GeForce Go 7400, Quadro NVS 110M, Quadro NVS 120M, Quadro FX 350M,
	Quadro FX 350, GeForce 7300 GS, GeForce Go 7600, GeForce Go 7600 GT,
	Quadro NVS 300M, Quadro FX 550M, GeForce Go 7900 GS,
	GeForce Go 7900 GTX, Quadro FX 2500M, Quadro FX 1500M, GeForce 6150,
	GeForce 6150 LE, GeForce 6100, GeForce Go 6150, GeForce Go 6100
(II) Primary Device is: PCI 01:00:0
(--) Chipset GeForce4 MX 440 with AGP8X found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xec001000 - 0xec0010ff (0x100) MX[B]
	[5] -1	0	0xec000000 - 0xec0000ff (0x100) MX[B]
	[6] -1	0	0xeb000000 - 0xebffffff (0x1000000) MX[B]
	[7] -1	0	0xd8000000 - 0xd7ffffff (0x0) MX[B]O
	[8] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0xe8000000 - 0xe8ffffff (0x1000000) MX[B](B)
	[10] -1	0	0xea000000 - 0xeaffffff (0x1000000) MX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x0000e500 - 0x0000e5ff (0x100) IX[B]
	[14] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[15] -1	0	0x0000e300 - 0x0000e30f (0x10) IX[B]
	[16] -1	0	0x0000e200 - 0x0000e21f (0x20) IX[B]
	[17] -1	0	0x0000e100 - 0x0000e11f (0x20) IX[B]
	[18] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xec001000 - 0xec0010ff (0x100) MX[B]
	[5] -1	0	0xec000000 - 0xec0000ff (0x100) MX[B]
	[6] -1	0	0xeb000000 - 0xebffffff (0x1000000) MX[B]
	[7] -1	0	0xd8000000 - 0xd7ffffff (0x0) MX[B]O
	[8] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0xe8000000 - 0xe8ffffff (0x1000000) MX[B](B)
	[10] -1	0	0xea000000 - 0xeaffffff (0x1000000) MX[B](B)
	[11] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[12] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[13] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000e500 - 0x0000e5ff (0x100) IX[B]
	[17] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[18] -1	0	0x0000e300 - 0x0000e30f (0x10) IX[B]
	[19] -1	0	0x0000e200 - 0x0000e21f (0x20) IX[B]
	[20] -1	0	0x0000e100 - 0x0000e11f (0x20) IX[B]
	[21] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[22] 0	0	0xe90003b0 - 0xe90003bb (0xc) IS[B]
	[23] 0	0	0xe90003c0 - 0xe90003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) NV(0): Initializing int10
(II) NV(0): Primary V_BIOS segment is: 0xc000
(--) NV(0): Chipset: "GeForce4 MX 440 with AGP8X"
(**) NV(0): Depth 24, (--) framebuffer bpp 32
(==) NV(0): RGB weight 888
(==) NV(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.8
(**) NV(0): Option "UseFBDev" "true"
(==) NV(0): Using HW cursor
(**) NV(0): Using framebuffer device
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 0.0.2
	ABI class: X.Org Video Driver, version 0.8
(WW) open /dev/fb1: No such file or directory
(WW) open /dev/fb2: No such file or directory
(WW) open /dev/fb3: No such file or directory
(WW) open /dev/fb4: No such file or directory
(WW) open /dev/fb5: No such file or directory
(WW) open /dev/fb6: No such file or directory
(WW) open /dev/fb7: No such file or directory
(EE) Unable to find a valid framebuffer device
(EE) NV(0): Failed to open framebuffer device, consult warnings and/or errors above for possible reasons
	(you may have to look at the server log to see warnings)
(II) UnloadModule: "nv"
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) UnloadModule: "vgahw"
(II) Unloading /usr/lib/xorg/modules/libvgahw.so
(II) UnloadModule: "int10"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

```

Not sure if this is relevant but there is onboard video on the motherboard but this is disabled in the bios.

Help!

Allan

---

### Post by jjf on 2006-07-05
I'm no pro, but I have similar trouble with my older Nvidia graphics cards.  Try this:

boot into recovery mode
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
(makes a backup of your xorg configuration file)
sudo nano /etc/X11/xorg.conf

Your xorg.conf file opens in a text editor.  Scroll down to find where it's calling the driver "nv".  Change that to "nvidia".  CTRL+O to save.  CTRL+X (I think, maybe Q) to exit.  Reboot.

---

### Post by dbw on 2006-07-11
I also have this problem in Dapper.  I have tried both Xubuntu and Ubuntu live cds, neither of which are able to boot to a graphical session.  I was able to install a Ubuntu-server, and then I added:
```
 apt-get install xubuntu-desktop gdm linux-image-686
```
I can now boot to a blank screen.  Just before I would expect the gdm, I see the basic xorg mouse crosshairs, which I am able to move before the system blanks.

Note that I had been running Breezy, with no problems.  I blanked the root partition, and now Dapper is giving me issues.  All other hardware seems aok, and my xorg.conf even lists the correct model of monitor that I am using!  My video card is a Nvidia Riva tnt2, and I have installed the nvidia-legacy drivers.  I have tried dpkg-reconfigure xserver.org, and I get the following message:
>  package 'xserver.org' is not installed and no info is available

---

### Post by mlind on 2006-07-11
> **dbw said:**
> I also have this problem in Dapper.  I have tried both Xubuntu and Ubuntu live cds, neither of which are able to boot to a graphical session.  I was able to install a Ubuntu-server, and then I added:
```
 apt-get install xubuntu-desktop gdm linux-image-686
```
I can now boot to a blank screen.  Just before I would expect the gdm, I see the basic xorg mouse crosshairs, which I am able to move before the system blanks.

Note that I had been running Breezy, with no problems.  I blanked the root partition, and now Dapper is giving me issues.  All other hardware seems aok, and my xorg.conf even lists the correct model of monitor that I am using!  My video card is a Nvidia Riva tnt2, and I have installed the nvidia-legacy drivers.  I have tried dpkg-reconfigure xserver.org, and I get the following message:

It's xserver**-xorg**

---

### Post by dbw on 2006-07-12
sorry, yeah, I tried reconfigure xserver-xorg, to no avail.  It turns out that Dapper Drake ( every version ) believes, by default, that my setup includes a Wacom tablet.  I do not have one, so X freaks out and fails when it learns this.  I was able to fix the problem by commenting a couple of lines that had appeared in my xorg.conf about the tablet business.  thanks for your help, as usual.

---

### Post by mlind on 2006-07-12
> **dbw said:**
> sorry, yeah, I tried reconfigure xserver-xorg, to no avail.  It turns out that Dapper Drake ( every version ) believes, by default, that my setup includes a Wacom tablet.  I do not have one, so X freaks out and fails when it learns this.  I was able to fix the problem by commenting a couple of lines that had appeared in my xorg.conf about the tablet business.  thanks for your help, as usual.

Yes, that "feature" somehow came along with late builds before the final version. I don't have a table PC either and still that stuff is on my xorg.conf after reconfigure. It should be harmless, but as you see it's not.

It's okay to remove that wacom stuff completely.

---

### Post by SteeL_x on 2006-09-21
I'm gona try wht "**jjf**" said.
I use nVidia Gforce FX5500 PCI 128mb
I get a Blank screen after windows xp pro welcome screen.

---

### Post by skwerl530 on 2006-09-25
I had the exact same problem and just got it fixed.  I am running dual 6600gt's in SLI mode.  WHen I installed Ubuntu it set up X to use the wrong card.  You can test this by moving the monitor cable to another head.  If it works then just change the /etc/X11.conf file to use the other card.  Find the pci bus ID of the cards by opening a terminal with ctrl+alt+F2.  type "lspci" and it will spit out a ton of stuff. You are looking for the "PCI BUS ID" of the 2 cards.  Mine was on "PCI:4:0:0" and "PCI:5:0:0".  Backup your file by typing "sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak". Next edit the xorg.conf file by typing "sudo nano /etc/X11/xorg.conf".  Scroll down to the "Device" section that names your vidoe card.  Change the PCI Bus ID to match the other card.  save with ctrl + "o" and exit with "ctrl + "x".  reboot and pray.

Good luck.

---

