---
title: "Failed boot kernel 2.6.38.2"
date: 2011-02-06
forum: General Help
---

### Post by randiroo76073 on 2011-02-06
Running ubuntu 10.10 maverick x64
Hi all, just updated my kernel to latest in repos: 2.6.38.2 and can't get gui to load, boots fine in kernel 2.6.37.12 . Have tried dpkg-reconfigure, no luck. here's my /var/log/xorg.0.log:
```

[   253.018] 
X.Org X Server 1.9.2.901 (1.9.3 RC 1)
Release Date: 2010-11-13
[   253.018] X Protocol Version 11, Revision 0
[   253.019] Build Operating System: Linux 2.6.24-28-xen x86_64 Ubuntu
[   253.019] Current Operating System: Linux Roo1 2.6.38-2-generic #29-Ubuntu SMP Fri Feb 4 14:25:38 UTC 2011 x86_64
[   253.019] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-2-generic root=UUID=4520688a-7006-49f0-bef3-4e9d306465a3 ro quiet splash
[   253.019] Build Date: 29 November 2010  03:31:56PM
[   253.019] xorg-server 2:1.9.2.901+git20101129+server-1.9-branch.65f2ab20-0ubuntu0sarvatt2~maverick (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[   253.019] Current version of pixman: 0.21.4
[   253.020] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[   253.020] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   253.021] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Feb  6 04:53:31 2011
[   253.021] (==) Using config file: "/etc/X11/xorg.conf"
[   253.022] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   253.022] (==) No Layout section.  Using the first Screen section.
[   253.022] (**) |-->Screen "Default Screen" (0)
[   253.022] (**) |   |-->Monitor "<default monitor>"
[   253.023] (==) No device specified for screen "Default Screen".
	Using the first device section listed.
[   253.023] (**) |   |-->Device "Default Device"
[   253.023] (==) No monitor specified for screen "Default Screen".
	Using a default monitor configuration.
[   253.023] (==) Automatically adding devices
[   253.023] (==) Automatically enabling devices
[   253.023] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   253.023] 	Entry deleted from font path.
[   253.023] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[   253.023] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   253.023] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[   253.023] (II) Loader magic: 0x7d1d00
[   253.023] (II) Module ABI versions:
[   253.023] 	X.Org ANSI C Emulation: 0.4
[   253.023] 	X.Org Video Driver: 8.0
[   253.023] 	X.Org XInput driver : 11.0
[   253.023] 	X.Org Server Extension : 4.0
[   253.025] (--) PCI:*(0:1:0:0) 1002:9498:174b:e109 rev 0, Mem @ 0xd0000000/268435456, 0xfdce0000/65536, I/O @ 0x0000de00/256, BIOS @ 0x????????/131072
[   253.025] (II) Open ACPI successful (/var/run/acpid.socket)
[   253.025] (II) "extmod" will be loaded by default.
[   253.025] (II) "dbe" will be loaded by default.
[   253.025] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[   253.025] (II) "record" will be loaded by default.
[   253.025] (II) "dri" will be loaded by default.
[   253.025] (II) "dri2" will be loaded by default.
[   253.025] (II) LoadModule: "glx"
[   253.026] (II) Loading /usr/lib/xorg/extra-modules/modules/extensions/libglx.so
[   253.027] (II) Module glx: vendor="FireGL - ATI Technologies Inc."
[   253.027] 	compiled for 7.6.0, module version = 1.0.0
[   253.027] (II) Loading extension GLX
[   253.027] (II) LoadModule: "extmod"
[   253.028] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   253.028] (II) Module extmod: vendor="X.Org Foundation"
[   253.028] 	compiled for 1.9.2.901, module version = 1.0.0
[   253.028] 	Module class: X.Org Server Extension
[   253.028] 	ABI class: X.Org Server Extension, version 4.0
[   253.028] (II) Loading extension MIT-SCREEN-SAVER
[   253.028] (II) Loading extension XFree86-VidModeExtension
[   253.028] (II) Loading extension XFree86-DGA
[   253.028] (II) Loading extension DPMS
[   253.028] (II) Loading extension XVideo
[   253.028] (II) Loading extension XVideo-MotionCompensation
[   253.028] (II) Loading extension X-Resource
[   253.028] (II) LoadModule: "dbe"
[   253.029] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   253.029] (II) Module dbe: vendor="X.Org Foundation"
[   253.029] 	compiled for 1.9.2.901, module version = 1.0.0
[   253.029] 	Module class: X.Org Server Extension
[   253.029] 	ABI class: X.Org Server Extension, version 4.0
[   253.029] (II) Loading extension DOUBLE-BUFFER
[   253.029] (II) LoadModule: "record"
[   253.030] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   253.030] (II) Module record: vendor="X.Org Foundation"
[   253.030] 	compiled for 1.9.2.901, module version = 1.13.0
[   253.030] 	Module class: X.Org Server Extension
[   253.030] 	ABI class: X.Org Server Extension, version 4.0
[   253.030] (II) Loading extension RECORD
[   253.030] (II) LoadModule: "dri"
[   253.031] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   253.031] (II) Module dri: vendor="X.Org Foundation"
[   253.031] 	compiled for 1.9.2.901, module version = 1.0.0
[   253.031] 	ABI class: X.Org Server Extension, version 4.0
[   253.031] (II) Loading extension XFree86-DRI
[   253.031] (II) LoadModule: "dri2"
[   253.032] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   253.032] (II) Module dri2: vendor="X.Org Foundation"
[   253.032] 	compiled for 1.9.2.901, module version = 1.2.0
[   253.032] 	ABI class: X.Org Server Extension, version 4.0
[   253.032] (II) Loading extension DRI2
[   253.032] (II) LoadModule: "fglrx"
[   253.033] (II) Loading /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so
[   253.074] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[   253.074] 	compiled for 1.4.99.906, module version = 8.80.5
[   253.074] 	Module class: X.Org Video Driver
[   253.074] (II) Loading sub module "fglrxdrm"
[   253.074] (II) LoadModule: "fglrxdrm"
[   253.075] (II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[   253.075] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[   253.075] 	compiled for 1.4.99.906, module version = 8.80.5
[   253.075] (II) ATI Proprietary Linux Driver Version Identifier:8.80.5
[   253.075] (II) ATI Proprietary Linux Driver Release Identifier: 8.801                                
[   253.075] (II) ATI Proprietary Linux Driver Build Date: Nov 25 2010 21:36:26
[   253.075] (--) using VT number 8

[   253.084] (WW) Falling back to old probe method for fglrx
[   253.097] (II) Loading PCS database from /etc/ati/amdpcsdb
[   253.099] (--) Assigning device section with no busID to primary device
[   253.099] (--) Chipset Supported AMD Graphics Processor (0x9498) found
[   253.099] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:0:0) found
[   253.099] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:2:0) found
[   253.099] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:7:0) found
[   253.099] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:0) found
[   253.099] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:0) found
[   253.099] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:1) found
[   253.099] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:2) found
[   253.099] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:3) found
[   253.099] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:4) found
[   253.099] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:5) found
[   253.099] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:0) found
[   253.099] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:1) found
[   253.099] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:2) found
[   253.099] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:3) found
[   253.099] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:4) found
[   253.100] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
[   253.100] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[   253.100] (II) AMD Video driver is signed
[   253.100] (II) fglrx(0): pEnt->device->identifier=0x1ff1eb0
[   253.100] (II) fglrx(0): === [xdl_x760_atiddxPreInit] === begin
[   253.101] (II) Loading sub module "vgahw"
[   253.101] (II) LoadModule: "vgahw"
[   253.102] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[   253.102] (II) Module vgahw: vendor="X.Org Foundation"
[   253.102] 	compiled for 1.9.2.901, module version = 0.1.0
[   253.102] 	ABI class: X.Org Video Driver, version 8.0
[   253.102] (II) fglrx(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
[   253.102] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[   253.102] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[   253.102] (==) fglrx(0): Default visual is TrueColor
[   253.102] (==) fglrx(0): RGB weight 888
[   253.102] (II) fglrx(0): Using 8 bits per RGB 
[   253.103] (==) fglrx(0): Buffer Tiling is ON
[   253.103] (II) Loading sub module "fglrxdrm"
[   253.103] (II) LoadModule: "fglrxdrm"
[   253.103] (II) Reloading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[   253.107] ukiDynamicMajor: failed to open /proc/ati/major
[   253.107] ukiDynamicMajor: failed to open /proc/ati/major
[   253.108] (==) fglrx(0): NoAccel = NO
[   253.108] (==) fglrx(0): ATI 2D Acceleration Architecture enabled
[   253.108] (--) fglrx(0): Chipset: "ATI Radeon HD 4600 Series " (Chipset = 0x9498)
[   253.108] (--) fglrx(0): (PciSubVendor = 0x174b, PciSubDevice = 0xe109)
[   253.108] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
[   253.108] (--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
[   253.108] (--) fglrx(0): MMIO registers at 0xfdce0000
[   253.108] (--) fglrx(0): I/O port at 0x0000de00
[   253.108] (==) fglrx(0): ROM-BIOS at 0x000c0000
[   253.118] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
[   253.118] (EE) fglrx(0): ACPI: DRM connection failed
[   253.232] (II) Loading sub module "vbe"
[   253.232] (II) LoadModule: "vbe"
[   253.233] (II) Loading /usr/lib/xorg/modules/libvbe.so
[   253.233] (II) Module vbe: vendor="X.Org Foundation"
[   253.233] 	compiled for 1.9.2.901, module version = 1.1.0
[   253.234] 	ABI class: X.Org Video Driver, version 8.0
[   253.234] (II) fglrx(0): VESA BIOS detected
[   253.234] (II) fglrx(0): VESA VBE Version 3.0
[   253.234] (II) fglrx(0): VESA VBE Total Mem: 16384 kB
[   253.234] (II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
[   253.234] (II) fglrx(0): VESA VBE OEM Software Rev: 11.22
[   253.234] (II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
[   253.234] (II) fglrx(0): VESA VBE OEM Product: RV730
[   253.234] (II) fglrx(0): VESA VBE OEM Product Rev: 01.00
[   253.278] (II) fglrx(0): ATI Video BIOS revision 9 or later detected
[   253.278] (--) fglrx(0): Video RAM: 524288 kByte, Type: DDR2
[   253.278] (II) fglrx(0): PCIE card detected
[   253.278] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[   253.278] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[   253.278] (EE) fglrx(0): ACPI: DRM connection failed
[   253.278] (WW) fglrx(0): Hasn't establisted DRM connection
[   253.278] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x20000000)
[   253.278] (WW) fglrx(0): No DRM connection for driver fglrx.
[   253.278] (II) fglrx(0): RandR 1.2 support is enabled!
[   253.278] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[   253.278] (==) fglrx(0): Center Mode is disabled 
[   253.278] (II) Loading sub module "fb"
[   253.278] (II) LoadModule: "fb"
[   253.279] (II) Loading /usr/lib/xorg/modules/libfb.so
[   253.279] (II) Module fb: vendor="X.Org Foundation"
[   253.279] 	compiled for 1.9.2.901, module version = 1.0.0
[   253.279] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   253.280] (II) Loading sub module "ddc"
[   253.280] (II) LoadModule: "ddc"
[   253.280] (II) Module "ddc" already built-in
[   253.674] (II) fglrx(0): Output DFP1 has no monitor section
[   253.674] (II) fglrx(0): Output DFP2 has no monitor section
[   253.674] (II) fglrx(0): Output CRT1 has no monitor section
[   253.674] (II) fglrx(0): Output CRT2 has no monitor section
[   253.674] (II) Loading sub module "ddc"
[   253.674] (II) LoadModule: "ddc"
[   253.674] (II) Module "ddc" already built-in
[   253.674] (II) fglrx(0): Connected Display0: DFP1
[   253.674] (II) fglrx(0): Display0 EDID data ---------------------------
[   253.674] (II) fglrx(0): Manufacturer: BNQ  Model: 76c3  Serial#: 9997
[   253.674] (II) fglrx(0): Year: 2007  Week: 20
[   253.674] (II) fglrx(0): EDID Version: 1.3
[   253.674] (II) fglrx(0): Digital Display Input
[   253.674] (II) fglrx(0): Max Image Size [cm]: horiz.: 43  vert.: 27
[   253.674] (II) fglrx(0): Gamma: 2.20
[   253.674] (II) fglrx(0): DPMS capabilities: StandBy Suspend Off
[   253.674] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[   253.674] (II) fglrx(0): Default color space is primary color space
[   253.674] (II) fglrx(0): First detailed timing is preferred mode
[   253.674] (II) fglrx(0): redX: 0.640 redY: 0.332   greenX: 0.288 greenY: 0.601
[   253.674] (II) fglrx(0): blueX: 0.146 blueY: 0.065   whiteX: 0.313 whiteY: 0.329
[   253.674] (II) fglrx(0): Supported established timings:
[   253.674] (II) fglrx(0): 720x400@70Hz
[   253.674] (II) fglrx(0): 640x480@60Hz
[   253.674] (II) fglrx(0): 640x480@75Hz
[   253.674] (II) fglrx(0): 800x600@60Hz
[   253.674] (II) fglrx(0): 800x600@75Hz
[   253.674] (II) fglrx(0): 832x624@75Hz
[   253.674] (II) fglrx(0): 1024x768@60Hz
[   253.674] (II) fglrx(0): 1024x768@70Hz
[   253.674] (II) fglrx(0): 1024x768@75Hz
[   253.674] (II) fglrx(0): 1280x1024@75Hz
[   253.674] (II) fglrx(0): 1152x864@75Hz
[   253.674] (II) fglrx(0): Manufacturer's mask: 0
[   253.674] (II) fglrx(0): Supported standard timings:
[   253.674] (II) fglrx(0): #0: hsize: 800  vsize 600  refresh: 75  vid: 20293
[   253.674] (II) fglrx(0): #1: hsize: 1024  vsize 768  refresh: 75  vid: 20321
[   253.674] (II) fglrx(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[   253.674] (II) fglrx(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[   253.674] (II) fglrx(0): #4: hsize: 1280  vsize 1024  refresh: 75  vid: 36737
[   253.674] (II) fglrx(0): #5: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[   253.674] (II) fglrx(0): #6: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[   253.674] (II) fglrx(0): Supported detailed timing:
[   253.674] (II) fglrx(0): clock: 119.0 MHz   Image Size:  433 x 271 mm
[   253.674] (II) fglrx(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
[   253.674] (II) fglrx(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
[   253.674] (II) fglrx(0): Supported detailed timing:
[   253.674] (II) fglrx(0): clock: 25.2 MHz   Image Size:  376 x 301 mm
[   253.674] (II) fglrx(0): h_active: 640  h_sync: 656  h_sync_end 752 h_blank_end 800 h_border: 0
[   253.674] (II) fglrx(0): v_active: 350  v_sync: 387  v_sync_end 389 v_blanking: 449 v_border: 0
[   253.674] (II) fglrx(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 84 kHz, PixClock max 175 MHz
[   253.674] (II) fglrx(0): Monitor name: BenQ FP202W
[   253.674] (II) fglrx(0): EDID (in hex):
[   253.674] (II) fglrx(0): 	00ffffffffffff0009d1c3760d270000
[   253.674] (II) fglrx(0): 	14110103802b1b78eecfb5a355499925
[   253.674] (II) fglrx(0): 	105054a56f80454f614f81408180818f
[   253.674] (II) fglrx(0): 	714fb30001017c2e90a0601a1e403020
[   253.674] (II) fglrx(0): 	3600b10f1100001ad50980a0205e6310
[   253.674] (II) fglrx(0): 	10605208782d1100001a000000fd0038
[   253.674] (II) fglrx(0): 	4c1e5411000a202020202020000000fc
[   253.674] (II) fglrx(0): 	0042656e51204650323032570a20006d
[   253.675] (II) fglrx(0): End of Display0 EDID data --------------------
[   253.733] (II) fglrx(0): EDID for output DFP1
[   253.733] (II) fglrx(0): Manufacturer: BNQ  Model: 76c3  Serial#: 9997
[   253.733] (II) fglrx(0): Year: 2007  Week: 20
[   253.733] (II) fglrx(0): EDID Version: 1.3
[   253.733] (II) fglrx(0): Digital Display Input
[   253.733] (II) fglrx(0): Max Image Size [cm]: horiz.: 43  vert.: 27
[   253.733] (II) fglrx(0): Gamma: 2.20
[   253.733] (II) fglrx(0): DPMS capabilities: StandBy Suspend Off
[   253.733] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[   253.733] (II) fglrx(0): Default color space is primary color space
[   253.733] (II) fglrx(0): First detailed timing is preferred mode
[   253.733] (II) fglrx(0): redX: 0.640 redY: 0.332   greenX: 0.288 greenY: 0.601
[   253.733] (II) fglrx(0): blueX: 0.146 blueY: 0.065   whiteX: 0.313 whiteY: 0.329
[   253.733] (II) fglrx(0): Supported established timings:
[   253.733] (II) fglrx(0): 720x400@70Hz
[   253.733] (II) fglrx(0): 640x480@60Hz
[   253.733] (II) fglrx(0): 640x480@75Hz
[   253.733] (II) fglrx(0): 800x600@60Hz
[   253.733] (II) fglrx(0): 800x600@75Hz
[   253.734] (II) fglrx(0): 832x624@75Hz
[   253.734] (II) fglrx(0): 1024x768@60Hz
[   253.734] (II) fglrx(0): 1024x768@70Hz
[   253.734] (II) fglrx(0): 1024x768@75Hz
[   253.734] (II) fglrx(0): 1280x1024@75Hz
[   253.734] (II) fglrx(0): 1152x864@75Hz
[   253.734] (II) fglrx(0): Manufacturer's mask: 0
[   253.734] (II) fglrx(0): Supported standard timings:
[   253.734] (II) fglrx(0): #0: hsize: 800  vsize 600  refresh: 75  vid: 20293
[   253.734] (II) fglrx(0): #1: hsize: 1024  vsize 768  refresh: 75  vid: 20321
[   253.734] (II) fglrx(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[   253.734] (II) fglrx(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[   253.734] (II) fglrx(0): #4: hsize: 1280  vsize 1024  refresh: 75  vid: 36737
[   253.734] (II) fglrx(0): #5: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[   253.734] (II) fglrx(0): #6: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[   253.734] (II) fglrx(0): Supported detailed timing:
[   253.734] (II) fglrx(0): clock: 119.0 MHz   Image Size:  433 x 271 mm
[   253.734] (II) fglrx(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
[   253.734] (II) fglrx(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
[   253.734] (II) fglrx(0): Supported detailed timing:
[   253.734] (II) fglrx(0): clock: 25.2 MHz   Image Size:  376 x 301 mm
[   253.734] (II) fglrx(0): h_active: 640  h_sync: 656  h_sync_end 752 h_blank_end 800 h_border: 0
[   253.734] (II) fglrx(0): v_active: 350  v_sync: 387  v_sync_end 389 v_blanking: 449 v_border: 0
[   253.734] (II) fglrx(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 84 kHz, PixClock max 175 MHz
[   253.734] (II) fglrx(0): Monitor name: BenQ FP202W
[   253.734] (II) fglrx(0): EDID (in hex):
[   253.734] (II) fglrx(0): 	00000000000000003a202325693a2068
[   253.734] (II) fglrx(0): 	73697a653a20256920207673697a6520
[   253.734] (II) fglrx(0): 	25692020726566726573683a20256920
[   253.734] (II) fglrx(0): 	207669643a2025690a00601a1e403020
[   253.734] (II) fglrx(0): 	3600b10f1100001a6100000000000000
[   253.734] (II) fglrx(0): 	00000000000000003a2052616e676573
[   253.734] (II) fglrx(0): 	3a2056206d696e3a2025692056206d61
[   253.734] (II) fglrx(0): 	783a20256920487a2c2048206d696e3a
[   253.734] (II) fglrx(0): EDID vendor "BNQ", prod id 30403
[   253.734] (II) fglrx(0): Using EDID range info for horizontal sync
[   253.734] (II) fglrx(0): Using EDID range info for vertical refresh
[   253.734] (II) fglrx(0): Printing DDC gathered Modelines:
[   253.734] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[   253.734] (II) fglrx(0): Modeline "640x350"x0.0   25.17  640 656 752 800  350 387 389 449 +hsync -vsync (31.5 kHz)
[   253.734] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   253.734] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   253.734] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   253.734] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   253.734] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   253.734] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   253.734] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   253.734] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   253.734] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   253.734] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   253.734] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   253.734] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[   253.734] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   253.734] (II) fglrx(0): Printing probed modes for output DFP1
[   253.734] (II) fglrx(0): Modeline "1680x1050"x60.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 -hsync +vsync (64.7 kHz)
[   253.734] (II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 +hsync -vsync (65.3 kHz)
[   253.734] (II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 +hsync -vsync (55.9 kHz)
[   253.734] (II) fglrx(0): Modeline "1280x800"x60.0   83.46  1280 1344 1480 1680  800 801 804 828 +hsync -vsync (49.7 kHz)
[   253.734] (II) fglrx(0): Modeline "1152x648"x60.0   59.90  1152 1200 1320 1488  648 649 652 671 +hsync -vsync (40.3 kHz)
[   253.734] (II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 -hsync -vsync (80.0 kHz)
[   253.734] (II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 -hsync -vsync (64.0 kHz)
[   253.734] (II) fglrx(0): Modeline "1280x960"x75.0  129.86  1280 1368 1504 1728  960 961 964 1002 +hsync -vsync (75.2 kHz)
[   253.734] (II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 -hsync -vsync (60.0 kHz)
[   253.734] (II) fglrx(0): Modeline "1280x800"x75.0  107.21  1280 1360 1496 1712  800 801 804 835 +hsync -vsync (62.6 kHz)
[   253.734] (II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 -hsync -vsync (67.5 kHz)
[   253.734] (II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 +hsync -vsync (53.7 kHz)
[   253.734] (II) fglrx(0): Modeline "1280x768"x75.0  102.25  1280 1360 1488 1696  768 771 778 805 +hsync -vsync (60.3 kHz)
[   253.734] (II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 +hsync -vsync (47.8 kHz)
[   253.734] (II) fglrx(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 -hsync -vsync (45.0 kHz)
[   253.734] (II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 -hsync -vsync (60.0 kHz)
[   253.734] (II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync (56.5 kHz)
[   253.734] (II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync (48.4 kHz)
[   253.734] (II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 -hsync -vsync (46.9 kHz)
[   253.734] (II) fglrx(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 +hsync -vsync (43.8 kHz)
[   253.734] (II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 -hsync -vsync (37.9 kHz)
[   253.734] (II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 +hsync -vsync (29.8 kHz)
[   253.734] (II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 +hsync +vsync (37.5 kHz)
[   253.734] (II) fglrx(0): Modeline "640x480"x60.0   25.18  640 648 744 800  480 482 484 525 +hsync +vsync (31.5 kHz)
[   253.734] (II) fglrx(0): EDID for output DFP2
[   253.734] (II) fglrx(0): EDID for output CRT1
[   253.734] (II) fglrx(0): EDID for output CRT2
[   253.734] (II) fglrx(0): Output DFP1 connected
[   253.734] (II) fglrx(0): Output DFP2 disconnected
[   253.735] (II) fglrx(0): Output CRT1 disconnected
[   253.735] (II) fglrx(0): Output CRT2 disconnected
[   253.735] (II) fglrx(0): Using exact sizes for initial modes
[   253.735] (II) fglrx(0): Output DFP1 using initial mode 1680x1050
[   253.735] (II) fglrx(0): Display dimensions: (430, 270) mm
[   253.735] (II) fglrx(0): DPI set to (99, 99)
[   253.735] (II) fglrx(0): Adapter ATI Radeon HD 4600 Series  has 2 configurable heads and 1 displays connected.
[   253.735] (==) fglrx(0):  PseudoColor visuals disabled
[   253.735] (II) Loading sub module "ramdac"
[   253.735] (II) LoadModule: "ramdac"
[   253.735] (II) Module "ramdac" already built-in
[   253.735] (==) fglrx(0): NoDRI = NO
[   253.735] (==) fglrx(0): Capabilities: 0x00000000
[   253.735] (==) fglrx(0): CapabilitiesEx: 0x00000000
[   253.735] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[   253.735] (==) fglrx(0): UseFastTLS=0
[   253.735] (==) fglrx(0): BlockSignalsOnLock=1
[   253.735] (--) Depth 24 pixmap format is 32 bpp
[   253.735] (EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
[   253.735] (WW) fglrx(0): ***********************************************************
[   253.735] (WW) fglrx(0): * DRI initialization failed                               *
[   253.735] (WW) fglrx(0): * kernel module (fglrx.ko) may be missing or incompatible *
[   253.735] (WW) fglrx(0): * 2D and 3D acceleration disabled                         *
[   253.735] (WW) fglrx(0): ***********************************************************
[   253.735] (II) fglrx(0): FBADPhys: 0xf00000000 FBMappedSize: 0x10000000
[   253.756] (II) fglrx(0): FBMM initialized for area (0,0)-(1728,8191)
[   253.756] (II) fglrx(0): FBMM auto alloc for area (0,0)-(1728,1680) (front color buffer - assumption)
[   253.756] (II) fglrx(0): Largest offscreen area available: 1728 x 6511
[   253.756] (==) fglrx(0): Backing store disabled
[   253.756] (II) Loading extension FGLRXEXTENSION
[   253.756] (==) fglrx(0): DPMS enabled
[   253.756] (II) fglrx(0): Initialized in-driver Xinerama extension
[   253.756] (WW) fglrx(0): Textured Video not supported without DRI enabled.
[   253.756] (II) LoadModule: "glesx"
[   253.756] (II) Loading /usr/lib/xorg/extra-modules/modules/glesx.so
[   253.757] (II) Module glesx: vendor="X.Org Foundation"
[   253.757] 	compiled for 1.4.99.906, module version = 1.0.0
[   253.757] (II) Loading extension GLESX
[   253.757] (II) fglrx(0): GLESX enableFlags = 512
[   253.757] (II) fglrx(0): Acceleration enabled
[   253.757] (II) LoadModule: "amdxmm"
[   253.757] (II) Loading /usr/lib/xorg/extra-modules/modules/amdxmm.so
[   253.757] (II) Module amdxmm: vendor="X.Org Foundation"
[   253.757] 	compiled for 1.8.99.905, module version = 1.0.0
[   253.757] (EE) fglrx(0): XMM failed to open CMMQS connection.
[   253.757] (EE) fglrx(0): XMM failed to initialize
[   253.757] (WW) fglrx(0): No XV video playback available
[   253.757] (II) fglrx(0): Enable composite support successfully
[   253.757] (==) fglrx(0): Silken mouse enabled
[   253.758] (==) fglrx(0): Using HW cursor of display infrastructure!
[   253.758] (II) fglrx(0): Disabling in-server RandR and enabling in-driver RandR 1.2.
[   253.833] (--) RandR disabled
[   253.833] (II) Initializing built-in extension Generic Event Extension
[   253.833] (II) Initializing built-in extension SHAPE
[   253.833] (II) Initializing built-in extension MIT-SHM
[   253.833] (II) Initializing built-in extension XInputExtension
[   253.833] (II) Initializing built-in extension XTEST
[   253.833] (II) Initializing built-in extension BIG-REQUESTS
[   253.833] (II) Initializing built-in extension SYNC
[   253.833] (II) Initializing built-in extension XKEYBOARD
[   253.833] (II) Initializing built-in extension XC-MISC
[   253.833] (II) Initializing built-in extension SECURITY
[   253.833] (II) Initializing built-in extension XINERAMA
[   253.833] (II) Initializing built-in extension XFIXES
[   253.833] (II) Initializing built-in extension RENDER
[   253.833] (II) Initializing built-in extension RANDR
[   253.833] (II) Initializing built-in extension COMPOSITE
[   253.833] (II) Initializing built-in extension DAMAGE
[   253.833] (II) Initializing built-in extension GESTURE
[   253.836] [glesx] __glESXExtensionInit: No GL ES2.0 capable screen found!
[   253.840] 
Backtrace:
[   253.841] 0: /usr/bin/X (xorg_backtrace+0x28) [0x467908]
[   253.841] 1: /usr/bin/X (0x400000+0x6784d) [0x46784d]
[   253.841] 2: /lib/libpthread.so.0 (0x7f8a6ebde000+0xfb40) [0x7f8a6ebedb40]
[   253.841] 3: /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so (xdl_x760_swlDriOpenConnection+0x3a) [0x7f8a6b71b46a]
[   253.841] 4: /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so (swlDriOpenConnection+0xd) [0x7f8a6b651ecd]
[   253.841] 5: /usr/lib/xorg/extra-modules/modules/extensions/libglx.so (0x7f8a6cc56000+0x1ad04) [0x7f8a6cc70d04]
[   253.841] 6: /usr/lib/xorg/extra-modules/modules/extensions/libglx.so (0x7f8a6cc56000+0x1d005) [0x7f8a6cc73005]
[   253.841] 7: /usr/bin/X (InitExtensions+0x89) [0x48fc99]
[   253.841] 8: /usr/bin/X (0x400000+0x21735) [0x421735]
[   253.841] 9: /lib/libc.so.6 (__libc_start_main+0xfe) [0x7f8a6db37d8e]
[   253.841] 10: /usr/bin/X (0x400000+0x21469) [0x421469]
[   253.841] Segmentation fault at address 0xa0
[   253.841] 
Caught signal 11 (Segmentation fault). Server aborting
[   253.841] 
Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[   253.841] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[   253.841] 
[   254.041] (EE) fglrx(0): firegl_SetSuspendResumeState FAILED -9.
[   254.048]  ddxSigGiveUp: Closing log

```

Can anyone see the problem why my gui is not loading, tried startx & gdm start, nether one brings up desktop.
Thanks for any help.

---

### Post by criticalsmile on 2011-02-19
I recompiled my kernel 2.6.37 and 2.6.38.x on Maverick 10.10 and I get the same results. My ATI video is the 3200. Seems like ATI isn't taking Linux too serious. Next time I buy a laptop or desktop system, I'm going to switch to nVidia. I hope that ATI is hearing the warnings. ;-)

Does anybody have a solution for this? I've tried to recompile the kernel after ticking and unticking all of the things I felt might be related to the ATI problem and I get no where with it. :-(

---

### Post by Bucky Ball on 2011-02-19
These newest kernels don't yet play with ATI as far as I know. You can't download the drivers. It refuses. That would be your problem if you are using ATI. I know it's mine when trying to run the latest kernels. I can get in low resolution but when I try to install the driver from Additional Drivers no go. ;(

You could try booting into the recovery kernel and when you get to the options choose 'Failsafe X'. That will get you to a desktop at least and you might try a fix from there.

---

