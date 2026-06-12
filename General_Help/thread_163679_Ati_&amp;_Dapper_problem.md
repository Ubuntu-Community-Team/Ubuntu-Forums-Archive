---
title: "Ati &amp; Dapper problem"
date: 2006-04-21
forum: General Help
---

### Post by putte30 on 2006-04-21
Hi all

Did a dist-upgrade today from breezy to dapper. Everything went well until i tried to start Enemy territory. In breezy I went with the standard ATI-driver in xorg, which work quite well, but in dapper Enemy territory complains something about the mesa driver. I have tried to follow the wiki guide to install the ATI driver without success, I have ATI Radeon 8500 card. Any ideas?

---

### Post by bollix47 on 2006-04-21
Did you try the steps outlined at:

[http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide)

---

### Post by putte30 on 2006-04-21
yes :-k

---

### Post by bollix47 on 2006-04-21
Just so I'm clear on what you did, you ran the following 3 steps?

sudo apt-get install xorg-driver-fglrx
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo dpkg-reconfigure xserver-xorg

---

### Post by putte30 on 2006-04-21
I followed both methods without success...

---

### Post by putte30 on 2006-04-21
Damn ATI drivers... You have to be a rocket sciencer to install proper drivers....

---

### Post by bollix47 on 2006-04-21
The only thing I've had to do to get my ATI Radeon 9200 to work was run the 3 steps mentioned earlier on both breezy and dapper.

After running I did a startx or a reboot and everything just worked afterwards.

What output do you get from:

fglrxinfo

Also, what is showing in the output from:

cat /var/log/Xorg.0.log

You may find some useful info at:

[http://www.ubuntuforums.org/showthread.php?p=739758](http://www.ubuntuforums.org/showthread.php?p=739758)

---

### Post by bollix47 on 2006-04-22
Another link you could look at:

[http://www.ubuntuforums.org/showthread.php?t=143283](http://www.ubuntuforums.org/showthread.php?t=143283)

---

### Post by putte30 on 2006-04-22
Thanks mate.

---

### Post by putte30 on 2006-04-22
Going insane ](*,) .. It just dont wanna work....


X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.12 i686
Current Operating System: Linux c83-249-114-135 2.6.15-20-686 #1 SMP PREEMPT Tue Apr 4 18:37:00 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Apr 22 20:47:41 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "aticonfig Screen 0" (0)
(**) |   |-->Monitor "aticonfig Monitor 0"
(**) |   |-->Device "ATI Graphics Adapter 0"
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
(II) PCI: 00:00:0: chip 1106,3099 card 1106,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,b099 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:07:0: chip 109e,036e card 107d,6609 rev 11 class 04,00,00 hdr 80
(II) PCI: 00:07:1: chip 109e,0878 card 107d,6609 rev 11 class 04,80,00 hdr 80
(II) PCI: 00:0b:0: chip 10ec,8029 card 10ec,8029 rev 00 class 02,00,00 hdr 00
(II) PCI: 00:10:0: chip 1106,3038 card 1462,7120 rev 80 class 0c,03,00 hdr 80
(II) PCI: 00:10:1: chip 1106,3038 card 1462,7120 rev 80 class 0c,03,00 hdr 80
(II) PCI: 00:10:3: chip 1106,3104 card 1462,7120 rev 82 class 0c,03,20 hdr 00
(II) PCI: 00:11:0: chip 1106,3177 card 1106,0000 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:11:1: chip 1106,0571 card 1462,7120 rev 06 class 01,01,8a hdr 00
(II) PCI: 00:11:5: chip 1106,3059 card 1462,7120 rev 50 class 04,01,00 hdr 00
(II) PCI: 00:12:0: chip 1106,3065 card 1462,7120 rev 74 class 02,00,00 hdr 00
(II) PCI: 01:00:0: chip 1002,514c card 1002,013a rev 80 class 03,00,00 hdr 00
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
(II) Bus 1 I/O range:
	[0] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[1] -1	0	0x0000c400 - 0x0000c4ff (0x100) IX[B]
	[2] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[3] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xdfe00000 - 0xdfefffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xcfd00000 - 0xdfcfffff (0x10000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI: (0:7:0) Brooktree Corporation Bt878 Video Capture rev 17, Mem @ 0xdfdfe000/12
(--) PCI:*(1:0:0) ATI Technologies Inc Radeon R200 QL [Radeon 8500 LE] rev 128, Mem @ 0xd0000000/27, 0xdfef0000/16, I/O @ 0xc800/8, BIOS @ 0xdfec0000/17
(
(II) Module shadowfb: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) RADEON(0): Page flipping disabled
(II) RADEON(0): Will try to use DMA for Xv image transfers
(WW) RADEON(0): [dri] limiting video memory to one aperture of 65536K
(WW) RADEON(0): [dri] detected radeon kernel module version 1.19 but 1.23 or newer is required for full memory mapping.
(II) RADEON(0): Detected total video RAM=65536K, accessible=65536K (PCI BAR=131072K)
(--) RADEON(0): Mapped VideoRAM: 65536 kByte (128 bit DDR SDRAM)
(II) RADEON(0): Color tiling enabled by default
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules/libddc.so
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.8
(II) RADEON(0): I2C bus "DDC" initialized.
(II) RADEON(0): Legacy BIOS detected
(II) RADEON(0): Connector0: DDCType-2, DACType-1, TMDSType-0, ConnectorType-3
(II) RADEON(0): Connector1: DDCType-3, DACType-0, TMDSType--1, ConnectorType-2
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 2, Detected Type: 0
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 3, Detected Type: 1
(II) RADEON(0): EDID data from the display on port 2-----------------------
(II) RADEON(0): Manufacturer: NEC  Model: 43c6  Serial#: 16843009
(II) RADEON(0): Year: 1998  Week: 4
(II) RADEON(0): EDID Version: 1.1
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 32  vert.: 24
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): redX: 0.635 redY: 0.330   greenX: 0.297 greenY: 0.605
(II) RADEON(0): blueX: 0.150 blueY: 0.065   whiteX: 0.281 whiteY: 0.311
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 720x400@88Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@87Hz (interlaced)
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 108.5 MHz   Image Size:  306 x 230 mm
(II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1472 h_blank_end 1696 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Ranges: V min: 55  V max: 120 Hz, H min: 31  H max: 69 kHz, PixClock max 120 MHz
(II) RADEON(0): Monitor name: NEC M700
(II) RADEON(0): Serial No: 8104860TA
(II) RADEON(0): 
(II) RADEON(0): Primary:
 Monitor   -- CRT
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- NONE
 DDC Type  -- VGA_DDC
(II) RADEON(0): Secondary:
 Monitor   -- NONE
 Connector -- DVI-I
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- Internal
 DDC Type  -- DVI_DDC

(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.8
(==) RADEON(0): Using XAA acceleration architecture
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.8
(II) RADEON(0): No MM_TABLE found - assuming CARD is not TV-in capable.
(!!) RADEON(0): For information on using the multimedia capabilities
	of this adapter, please see [http://gatos.sf.net](http://gatos.sf.net).
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xdfef0000 - 0xdfefffff (0x10000) MX[B]
	[1] 0	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B]
	[2] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xdffefe00 - 0xdffefeff (0x100) MX[B]
	[8] -1	0	0xdffeff00 - 0xdffeffff (0x100) MX[B]
	[9] -1	0	0xdfdff000 - 0xdfdfffff (0x1000) MX[B]
	[10] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[11] -1	0	0xdfec0000 - 0xdfedffff (0x20000) MX[B](B)
	[12] -1	0	0xdfef0000 - 0xdfefffff (0x10000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[14] -1	0	0xdfdfe000 - 0xdfdfefff (0x1000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[18] 0	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[22] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[23] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[24] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[25] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[26] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[27] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B](B)
	[28] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[29] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(**) RADEON(0): RADEONScreenInit d0000000 0
(**) RADEON(0): Map: 0xd0000000, 0x04000000
(**) RADEON(0): RADEONSave
(**) RADEON(0): RADEONSaveMode(0x81fea90)
(**) RADEON(0): Read: 0x0000000c 0x00030065 0x00000000
(**) RADEON(0): Read: rd=12, fd=101, pd=3
(**) RADEON(0): RADEONSaveMode returns 0x81fea90
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenByBusid: drmOpenMinor returns 6
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) RADEON(0): [drm] DRM interface version 1.2
(II) RADEON(0): [drm] created "radeon" driver at busid "pci:0000:01:00.0"
(II) RADEON(0): [drm] added 8192 byte SAREA at 0xe0d08000
(II) RADEON(0): [drm] mapped SAREA 0xe0d08000 to 0xb790e000
(II) RADEON(0): [drm] framebuffer handle = 0xd0000000
(II) RADEON(0): [drm] added 1 reserved context for kernel
(II) RADEON(0): [agp] Mode 0x1f000201 [AGP 0x1106/0x3099; Card 0x1002/0x514c]
(II) RADEON(0): [agp] 8192 kB allocated with handle 0x00000001
(II) RADEON(0): [agp] ring handle = 0xe0000000
(II) RADEON(0): [agp] Ring mapped at 0xb36ea000
(II) RADEON(0): [agp] ring read ptr handle = 0xe0101000
(II) RADEON(0): [agp] Ring read ptr mapped at 0xb36e9000
(II) RADEON(0): [agp] vertex/indirect buffers handle = 0xe0102000
(II) RADEON(0): [agp] Vertex/indirect buffers mapped at 0xb34e9000
(II) RADEON(0): [agp] GART texture map handle = 0xe0302000
(II) RADEON(0): [agp] GART Texture map mapped at 0xb3009000
(II) RADEON(0): [drm] register handle = 0xdfef0000
(II) RADEON(0): [dri] Visual configs initialized
(**) RADEON(0): RADEONInitMemoryMap() : 
(**) RADEON(0):   mem_size         : 0x04000000
(**) RADEON(0):   agp_size         : 0x081fe968
(**) RADEON(0):   agp_base         : 0x081fe968
(**) RADEON(0):   MC_FB_LOCATION   : 0xd3ffd000
(**) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(**) RADEON(0): RADEONModeInit()
1680x1050     147.14  1680 1784 1968 2256  1050 1051 1054 1087 (24,32)
1680x1050     147.14  1680 1784 1968 2256  1050 1051 1054 1087 (24,32)
(**) RADEON(0): Pitch = 14155992 bytes (virtualX = 1680, displayWidth = 1728)
(**) RADEON(0): dc=14713, of=29426, fd=131, pd=2
(**) RADEON(0): RADEONInit returns 0x81ff440
(**) RADEON(0): RADEONRestoreMode()
(**) RADEON(0): RADEONRestoreMode(0x81ff440)
(**) RADEON(0): RADEONRestoreMemMapRegisters() : 
(**) RADEON(0):   MC_FB_LOCATION   : 0xd3ffd000
(**) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(**) RADEON(0):   Map Changed ! Applying ...
(**) RADEON(0):   Map applied, resetting engine ...
(**) RADEON(0): Updating display base addresses...
(**) RADEON(0): Memory map updated.
(**) RADEON(0): Programming CRTC1, offset: 0x00000000
(**) RADEON(0): Wrote: 0x0000000c 0x00010083 0x00000000 (0x0000a400)
(**) RADEON(0): Wrote: rd=12, fd=131, pd=1
(**) RADEON(0): GRPH_BUFFER_CNTL from 20207c7c to 20127c7c
(**) RADEON(0): RADEONSaveScreen(0)
(II) RADEON(0): Depth moves disabled by default
(**) RADEON(0): Setting up initial surfaces
(**) RADEON(0): Initializing fb layer
(**) RADEON(0): Setting up accel memmap
(II) RADEON(0): CP in BM mode
(II) RADEON(0): Using 8 MB GART aperture
(II) RADEON(0): Using 1 MB for the ring buffer
(II) RADEON(0): Using 2 MB for vertex/indirect buffers
(II) RADEON(0): Using 5 MB for GART textures
(II) RADEON(0): Memory manager initialized to (0,0) (1728,8191)
(II) RADEON(0): Reserved area from (0,1050) to (1728,1058)
(II) RADEON(0): Largest offscreen area available: 1728 x 7133
(II) RADEON(0): Will use back buffer at offset 0xe07000
(II) RADEON(0): Will use depth buffer at offset 0x14fd000
(II) RADEON(0): Will use 36864 kb for textures at offset 0x1bf3000
(**) RADEON(0): Initializing backing store
(==) RADEON(0): Backing store disabled
(**) RADEON(0): DRI Finishing init !
(II) RADEON(0): X context handle = 0x1
(II) RADEON(0): [drm] installed DRM signal handler
(II) RADEON(0): [DRI] installation complete
(**) RADEON(0): EngineRestore (32/32)
(II) RADEON(0): [drm] Added 32 65536 byte vertex/indirect buffers
(II) RADEON(0): [drm] Mapped 32 vertex/indirect buffers
(II) RADEON(0): [drm] dma control initialized, using IRQ 201
(II) RADEON(0): [drm] Initialized kernel GART heap manager, 5111808
(WW) RADEON(0): DRI init changed memory map, adjusting ...
(WW) RADEON(0):   MC_FB_LOCATION  was: 0xd3ffd000 is: 0xd3ffd000
(WW) RADEON(0):   MC_AGP_LOCATION was: 0xffffffc0 is: 0xd47fd400
(**) RADEON(0): GRPH_BUFFER_CNTL from 20207c7c to 20127c7c
(II) RADEON(0): Direct rendering enabled
(**) RADEON(0): Setting up final surfaces
(**) RADEON(0): Initializing Acceleration
(II) RADEON(0): Render acceleration enabled
(**) RADEON(0): EngineInit (32/32)
(**) RADEON(0): Pitch for acceleration = 216
(**) RADEON(0): EngineRestore (32/32)
(II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) RADEON(0): Acceleration enabled
(**) RADEON(0): Initializing DPMS
(**) RADEON(0): Initializing Cursor
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Using hardware cursor (scanline 1058)
(II) RADEON(0): Largest offscreen area available: 1728 x 7130
(**) RADEON(0): Initializing color map
(**) RADEON(0): Initializing DGA
(**) RADEON(0): Initializing Xv
(II) RADEON(0): No video input capabilities detected and no information is provided - disabling multimedia i2c
(II) Loading sub module "theatre_detect"
(II) LoadModule: "theatre_detect"
(II) Loading /usr/lib/xorg/modules/multimedia/theatre_detect_drv.so
(II) Module theatre_detect: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) RADEON(0): no multimedia table present, disabling Rage Theatre.
(WW) RADEON(0): Option "(null)" is not used
(WW) RADEON(0): Option "VideoOverlay" is not used
(WW) RADEON(0): Option "OpenGLOverlay" is not used
(**) RADEON(0): RADEONScreenInit finished
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "se"
(**) Generic Keyboard: XkbLayout: "se"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(**) RADEON(0): RADEONSaveScreen(2)
(**) RADEON(0): EngineRestore (32/32)
(**) RADEON(0): RADEONSwitchMode() !n(**) RADEON(0): RADEONModeInit()
1024x768       94.50  1024 1072 1168 1376   768  769  772  808 (24,32) +H +V
1024x768       94.50  1024 1072 1168 1376   768  769  772  808 (24,32) +H +V
(**) RADEON(0): Pitch = 14155992 bytes (virtualX = 1024, displayWidth = 1728)
(**) RADEON(0): dc=9450, of=28350, fd=126, pd=3
(**) RADEON(0): RADEONInit returns 0x81ff440
(**) RADEON(0): RADEONRestoreMode()
(**) RADEON(0): RADEONRestoreMode(0x81ff440)
(**) RADEON(0): RADEONRestoreMemMapRegisters() : 
(**) RADEON(0):   MC_FB_LOCATION   : 0xd3ffd000
(**) RADEON(0):   MC_AGP_LOCATION  : 0xd47fd400
(**) RADEON(0): Updating display base addresses...
(**) RADEON(0): Memory map updated.
(**) RADEON(0): Programming CRTC1, offset: 0x00000000
(**) RADEON(0): Wrote: 0x0000000c 0x0004007e 0x00000000 (0x0000a400)
(**) RADEON(0): Wrote: rd=12, fd=126, pd=4
(**) RADEON(0): GRPH_BUFFER_CNTL from 20207c7c to 200c7c7c
(**) RADEON(0): EngineRestore (32/32)
(**) RADEON(0): EngineRestore (32/32)
(**) RADEON(0): RADEONSwitchMode() !n(**) RADEON(0): RADEONModeInit()
800x600        56.30   800  832  896 1048   600  601  604  631 (24,32) +H +V
800x600        56.30   800  832  896 1048   600  601  604  631 (24,32) +H +V
(**) RADEON(0): Pitch = 14155992 bytes (virtualX = 1024, displayWidth = 1728)
(**) RADEON(0): dc=5629, of=22516, fd=100, pd=4
(**) RADEON(0): RADEONInit returns 0x81ff440
(**) RADEON(0): RADEONRestoreMode()
(**) RADEON(0): RADEONRestoreMode(0x81ff440)
(**) RADEON(0): RADEONRestoreMemMapRegisters() : 
(**) RADEON(0):   MC_FB_LOCATION   : 0xd3ffd000
(**) RADEON(0):   MC_AGP_LOCATION  : 0xd47fd400
(**) RADEON(0): Updating display base addresses...
(**) RADEON(0): Memory map updated.
(**) RADEON(0): Programming CRTC1, offset: 0x00000000
(**) RADEON(0): Wrote: 0x0000000c 0x00020064 0x00000000 (0x0000a400)
(**) RADEON(0): Wrote: rd=12, fd=100, pd=2
(**) RADEON(0): GRPH_BUFFER_CNTL from 20207c7c to 20077c7c
(**) RADEON(0): EngineRestore (32/32)
(**) RADEON(0): EngineRestore (32/32)
(**) RADEON(0): RADEONSwitchMode() !n(**) RADEON(0): RADEONModeInit()
832x624        57.28   832  864  928 1152   624  625  628  667 (24,32) -H -V
832x624        57.28   832  864  928 1152   624  625  628  667 (24,32) -H -V
(**) RADEON(0): Pitch = 14155992 bytes (virtualX = 1024, displayWidth = 1728)
(**) RADEON(0): dc=5728, of=22912, fd=102, pd=4
(**) RADEON(0): RADEONInit returns 0x81ff440
(**) RADEON(0): RADEONRestoreMode()
(**) RADEON(0): RADEONRestoreMode(0x81ff440)
(**) RADEON(0): RADEONRestoreMemMapRegisters() : 
(**) RADEON(0):   MC_FB_LOCATION   : 0xd3ffd000
(**) RADEON(0):   MC_AGP_LOCATION  : 0xd47fd400
(**) RADEON(0): Updating display base addresses...
(**) RADEON(0): Memory map updated.
(**) RADEON(0): Programming CRTC1, offset: 0x00000000
(**) RADEON(0): Wrote: 0x0000000c 0x00020066 0x00000000 (0x0000a400)
(**) RADEON(0): Wrote: rd=12, fd=102, pd=2
(**) RADEON(0): GRPH_BUFFER_CNTL from 20207c7c to 20077c7c
(**) RADEON(0): EngineRestore (32/32)
(**) RADEON(0): EngineRestore (32/32)
(**) RADEON(0): RADEONSwitchMode() !n(**) RADEON(0): RADEONModeInit()
1024x768       44.90  1024 1032 1208 1264   768  768  776  817 (24,32) I +H +V
1024x768       44.90  1024 1032 1208 1264   768  768  776  817 (24,32) I +H +V
(**) RADEON(0): Pitch = 14155992 bytes (virtualX = 1024, displayWidth = 1728)
(**) RADEON(0): dc=4489, of=26934, fd=120, pd=6
(**) RADEON(0): RADEONInit returns 0x81ff440
(**) RADEON(0): RADEONRestoreMode()
(**) RADEON(0): RADEONRestoreMode(0x81ff440)
(**) RADEON(0): RADEONRestoreMemMapRegisters() : 
(**) RADEON(0):   MC_FB_LOCATION   : 0xd3ffd000
(**) RADEON(0):   MC_AGP_LOCATION  : 0xd47fd400
(**) RADEON(0): Updating display base addresses...
(**) RADEON(0): Memory map updated.
(**) RADEON(0): Programming CRTC1, offset: 0x00000000
(**) RADEON(0): Wrote: 0x0000000c 0x00060078 0x00000000 (0x0000a400)
(**) RADEON(0): Wrote: rd=12, fd=120, pd=6
(**) RADEON(0): GRPH_BUFFER_CNTL from 20207c7c to 20067c7c
(EE) RADEON(0): drm: could not allocate surface for front buffer!
(**) RADEON(0): EngineRestore (32/32)
(**) RADEON(0): EngineRestore (32/32)
(**) RADEON(0): RADEONSwitchMode() !n(**) RADEON(0): RADEONModeInit()
1024x768       65.00  1024 1048 1184 1344   768  771  777  806 (24,32) -H -V
1024x768       65.00  1024 1048 1184 1344   768  771  777  806 (24,32) -H -V
(**) RADEON(0): Pitch = 14155992 bytes (virtualX = 1024, displayWidth = 1728)
(**) RADEON(0): dc=6500, of=26000, fd=116, pd=4
(**) RADEON(0): RADEONInit returns 0x81ff440
(**) RADEON(0): RADEONRestoreMode()
(**) RADEON(0): RADEONRestoreMode(0x81ff440)
(**) RADEON(0): RADEONRestoreMemMapRegisters() : 
(**) RADEON(0):   MC_FB_LOCATION   : 0xd3ffd000
(**) RADEON(0):   MC_AGP_LOCATION  : 0xd47fd400
(**) RADEON(0): Updating display base addresses...
(**) RADEON(0): Memory map updated.
(**) RADEON(0): Programming CRTC1, offset: 0x00000000
(**) RADEON(0): Wrote: 0x0000000c 0x00020074 0x00000000 (0x0000a400)
(**) RADEON(0): Wrote: rd=12, fd=116, pd=2
(**) RADEON(0): GRPH_BUFFER_CNTL from 20207c7c to 20087c7c
(**) RADEON(0): EngineRestore (32/32)
(**) RADEON(0): EngineRestore (32/32)
(**) RADEON(0): RADEONSwitchMode() !n(**) RADEON(0): RADEONModeInit()
1024x768       75.00  1024 1048 1184 1328   768  771  777  806 (24,32) -H -V
1024x768       75.00  1024 1048 1184 1328   768  771  777  806 (24,32) -H -V
(**) RADEON(0): Pitch = 14155992 bytes (virtualX = 1024, displayWidth = 1728)
(**) RADEON(0): dc=7500, of=30000, fd=133, pd=4
(**) RADEON(0): RADEONInit returns 0x81ff440
(**) RADEON(0): RADEONRestoreMode()
(**) RADEON(0): RADEONRestoreMode(0x81ff440)
(**) RADEON(0): RADEONRestoreMemMapRegisters() : 
(**) RADEON(0):   MC_FB_LOCATION   : 0xd3ffd000
(**) RADEON(0):   MC_AGP_LOCATION  : 0xd47fd400
(**) RADEON(0): Updating display base addresses...
(**) RADEON(0): Memory map updated.
(**) RADEON(0): Programming CRTC1, offset: 0x00000000
(**) RADEON(0): Wrote: 0x0000000c 0x00020085 0x00000000 (0x0000a400)
(**) RADEON(0): Wrote: rd=12, fd=133, pd=2
(**) RADEON(0): GRPH_BUFFER_CNTL from 20207c7c to 20097c7c
(**) RADEON(0): EngineRestore (32/32)
(**) RADEON(0): EngineRestore (32/32)
(**) RADEON(0): RADEONSwitchMode() !n(**) RADEON(0): RADEONModeInit()
1024x768       78.80  1024 1040 1136 1312   768  769  772  800 (24,32) +H +V
1024x768       78.80  1024 1040 1136 1312   768  769  772  800 (24,32) +H +V
(**) RADEON(0): Pitch = 14155992 bytes (virtualX = 1024, displayWidth = 1728)
(**) RADEON(0): dc=7879, of=31516, fd=140, pd=4
(**) RADEON(0): RADEONInit returns 0x81ff440
(**) RADEON(0): RADEONRestoreMode()
(**) RADEON(0): RADEONRestoreMode(0x81ff440)
(**) RADEON(0): RADEONRestoreMemMapRegisters() : 
(**) RADEON(0):   MC_FB_LOCATION   : 0xd3ffd000
(**) RADEON(0):   MC_AGP_LOCATION  : 0xd47fd400
(**) RADEON(0): Updating display base addresses...
(**) RADEON(0): Memory map updated.
(**) RADEON(0): Programming CRTC1, offset: 0x00000000
(**) RADEON(0): Wrote: 0x0000000c 0x0002008c 0x00000000 (0x0000a400)
(**) RADEON(0): Wrote: rd=12, fd=140, pd=2
(**) RADEON(0): GRPH_BUFFER_CNTL from 20207c7c to 200a7c7c
(**) RADEON(0): EngineRestore (32/32)

---

