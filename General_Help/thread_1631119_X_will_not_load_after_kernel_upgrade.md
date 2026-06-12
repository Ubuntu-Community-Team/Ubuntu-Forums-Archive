---
title: "X will not load after kernel upgrade"
date: 2010-11-26
forum: General Help
---

### Post by logan85 on 2010-11-26
Hi, I have an ubuntu 10.10, with Ati HD4850 video card, and catalyst 10.10 installed, and everything was fine, until I upgraded the kernel to the newest one, and after that, instead of the login screen the screen had began to flicker 3-4 times, and after that switched to a terminal login, where I tried again to load X, but did not manage, it gave me a segmentation fault. I did ran sudo aticonfig --initial, but nothing happened.
And with the previous kernel works fine...

 Anticipated thanks for help, here is the Xorg log:

[    25.680] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    25.680] X Protocol Version 11, Revision 0
[    25.680] Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
[    25.680] Current Operating System: Linux logan-desktop 2.6.35-23-generic #40-Ubuntu SMP Wed Nov 17 22:14:33 UTC 2010 x86_64
[    25.680] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-23-generic root=UUID=eabcb5d9-d35f-4783-9842-f9a39be3b0f9 ro quiet splash
[    25.680] Build Date: 16 September 2010  06:18:41PM
[    25.680] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    25.680] Current version of pixman: 0.18.4
[    25.680] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    25.680] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    25.680] (==) Log file: "/var/log/Xorg.1.log", Time: Fri Nov 26 12:22:34 2010
[    25.680] (==) Using config file: "/etc/X11/xorg.conf"
[    25.680] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    25.681] (==) ServerLayout "aticonfig Layout"
[    25.681] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[    25.681] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[    25.681] (**) |   |-->Device "aticonfig-Device[0]-0"
[    25.681] (==) Automatically adding devices
[    25.681] (==) Automatically enabling devices
[    25.681] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    25.681] 	Entry deleted from font path.
[    25.681] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    25.681] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    25.681] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    25.681] (II) Loader magic: 0x7d0200
[    25.681] (II) Module ABI versions:
[    25.681] 	X.Org ANSI C Emulation: 0.4
[    25.681] 	X.Org Video Driver: 8.0
[    25.681] 	X.Org XInput driver : 11.0
[    25.681] 	X.Org Server Extension : 4.0
[    25.682] (--) PCI:*(0:1:0:0) 1002:9442:174b:e810 rev 0, Mem @ 0xd0000000/268435456, 0xfeaf0000/65536, I/O @ 0x0000e000/256, BIOS @ 0x????????/131072
[    25.682] (II) Open ACPI successful (/var/run/acpid.socket)
[    25.682] (II) "extmod" will be loaded by default.
[    25.682] (II) "dbe" will be loaded by default.
[    25.682] (II) "glx" will be loaded by default.
[    25.682] (II) "record" will be loaded by default.
[    25.682] (II) "dri" will be loaded by default.
[    25.682] (II) "dri2" will be loaded by default.
[    25.682] (II) LoadModule: "extmod"
[    25.682] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    25.683] (II) Module extmod: vendor="X.Org Foundation"
[    25.683] 	compiled for 1.9.0, module version = 1.0.0
[    25.683] 	Module class: X.Org Server Extension
[    25.683] 	ABI class: X.Org Server Extension, version 4.0
[    25.683] (II) Loading extension MIT-SCREEN-SAVER
[    25.683] (II) Loading extension XFree86-VidModeExtension
[    25.683] (II) Loading extension XFree86-DGA
[    25.683] (II) Loading extension DPMS
[    25.683] (II) Loading extension XVideo
[    25.683] (II) Loading extension XVideo-MotionCompensation
[    25.683] (II) Loading extension X-Resource
[    25.683] (II) LoadModule: "dbe"
[    25.683] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    25.683] (II) Module dbe: vendor="X.Org Foundation"
[    25.683] 	compiled for 1.9.0, module version = 1.0.0
[    25.683] 	Module class: X.Org Server Extension
[    25.683] 	ABI class: X.Org Server Extension, version 4.0
[    25.683] (II) Loading extension DOUBLE-BUFFER
[    25.683] (II) LoadModule: "glx"
[    25.683] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    25.683] (II) Module glx: vendor="FireGL - ATI Technologies Inc."
[    25.684] 	compiled for 7.6.0, module version = 1.0.0
[    25.684] (II) Loading extension GLX
[    25.684] (II) LoadModule: "record"
[    25.684] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    25.684] (II) Module record: vendor="X.Org Foundation"
[    25.684] 	compiled for 1.9.0, module version = 1.13.0
[    25.684] 	Module class: X.Org Server Extension
[    25.684] 	ABI class: X.Org Server Extension, version 4.0
[    25.684] (II) Loading extension RECORD
[    25.684] (II) LoadModule: "dri"
[    25.684] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    25.684] (II) Module dri: vendor="X.Org Foundation"
[    25.684] 	compiled for 1.9.0, module version = 1.0.0
[    25.684] 	ABI class: X.Org Server Extension, version 4.0
[    25.684] (II) Loading extension XFree86-DRI
[    25.684] (II) LoadModule: "dri2"
[    25.685] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    25.685] (II) Module dri2: vendor="X.Org Foundation"
[    25.685] 	compiled for 1.9.0, module version = 1.2.0
[    25.685] 	ABI class: X.Org Server Extension, version 4.0
[    25.685] (II) Loading extension DRI2
[    25.685] (II) LoadModule: "fglrx"
[    25.685] (II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
[    25.700] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[    25.700] 	compiled for 1.4.99.906, module version = 8.78.6
[    25.701] 	Module class: X.Org Video Driver
[    25.701] (II) Loading sub module "fglrxdrm"
[    25.701] (II) LoadModule: "fglrxdrm"
[    25.701] (II) Loading /usr/lib/xorg/modules/linux/libfglrxdrm.so
[    25.701] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    25.701] 	compiled for 1.8.99.905, module version = 8.78.6
[    25.701] (II) ATI Proprietary Linux Driver Version Identifier:8.78.6
[    25.701] (II) ATI Proprietary Linux Driver Release Identifier: 8.783                                
[    25.701] (II) ATI Proprietary Linux Driver Build Date: Oct  5 2010 21:22:57
[    25.701] (--) using VT number 7

[    25.710] (WW) Falling back to old probe method for fglrx
[    25.715] (II) Loading PCS database from /etc/ati/amdpcsdb
[    25.715] (--) Chipset Supported AMD Graphics Processor (0x9442) found
[    25.715] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:0:0) found
[    25.715] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:2:0) found
[    25.715] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:6:0) found
[    25.715] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:0) found
[    25.715] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:0) found
[    25.716] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:1) found
[    25.716] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:2) found
[    25.716] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:3) found
[    25.716] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:4) found
[    25.716] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:5) found
[    25.716] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:0) found
[    25.716] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:1) found
[    25.716] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:2) found
[    25.716] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:3) found
[    25.716] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:4) found
[    25.716] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
[    25.716] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[    25.716] (II) AMD Video driver is signed
[    25.716] (II) fglrx(0): pEnt->device->identifier=0x8e0580
[    25.716] (II) fglrx(0): === [xdl_x760_atiddxPreInit] === begin
[    25.716] (II) Loading sub module "vgahw"
[    25.716] (II) LoadModule: "vgahw"
[    25.716] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    25.717] (II) Module vgahw: vendor="X.Org Foundation"
[    25.717] 	compiled for 1.9.0, module version = 0.1.0
[    25.717] 	ABI class: X.Org Video Driver, version 8.0
[    25.717] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[    25.717] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    25.717] (==) fglrx(0): Default visual is TrueColor
[    25.717] (**) fglrx(0): Option "DPMS" "true"
[    25.717] (==) fglrx(0): RGB weight 888
[    25.717] (II) fglrx(0): Using 8 bits per RGB 
[    25.717] (==) fglrx(0): Buffer Tiling is ON
[    25.717] (II) Loading sub module "fglrxdrm"
[    25.717] (II) LoadModule: "fglrxdrm"
[    25.717] (II) Reloading /usr/lib/xorg/modules/linux/libfglrxdrm.so
[    25.719] ukiDynamicMajor: failed to open /proc/ati/major
[    25.719] ukiDynamicMajor: failed to open /proc/ati/major
[    25.719] (==) fglrx(0): NoAccel = NO
[    25.719] (==) fglrx(0): ATI 2D Acceleration Architecture enabled
[    25.719] (--) fglrx(0): Chipset: "ATI Radeon HD 4800 Series        " (Chipset = 0x9442)
[    25.719] (--) fglrx(0): (PciSubVendor = 0x174b, PciSubDevice = 0xe810)
[    25.719] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
[    25.719] (--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
[    25.719] (--) fglrx(0): MMIO registers at 0xfeaf0000
[    25.719] (--) fglrx(0): I/O port at 0x0000e000
[    25.719] (==) fglrx(0): ROM-BIOS at 0x000c0000
[    25.726] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
[    25.726] (EE) fglrx(0): ACPI: DRM connection failed
[    25.847] (II) Loading sub module "vbe"
[    25.847] (II) LoadModule: "vbe"
[    25.847] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    25.847] (II) Module vbe: vendor="X.Org Foundation"
[    25.847] 	compiled for 1.9.0, module version = 1.1.0
[    25.847] 	ABI class: X.Org Video Driver, version 8.0
[    25.847] (II) fglrx(0): VESA BIOS detected
[    25.847] (II) fglrx(0): VESA VBE Version 3.0
[    25.847] (II) fglrx(0): VESA VBE Total Mem: 16384 kB
[    25.847] (II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
[    25.847] (II) fglrx(0): VESA VBE OEM Software Rev: 11.4
[    25.847] (II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
[    25.847] (II) fglrx(0): VESA VBE OEM Product: 3
[    25.847] (II) fglrx(0): VESA VBE OEM Product Rev: 01.00
[    25.885] (II) fglrx(0): ATI Video BIOS revision 9 or later detected
[    25.885] (--) fglrx(0): Video RAM: 524288 kByte, Type: GDDR3
[    25.885] (II) fglrx(0): PCIE card detected
[    25.885] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[    25.885] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[    25.885] (EE) fglrx(0): ACPI: DRM connection failed
[    25.885] (WW) fglrx(0): Hasn't establisted DRM connection
[    25.885] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x20000000)
[    25.885] (WW) fglrx(0): No DRM connection for driver fglrx.
[    25.886] (II) fglrx(0): RandR 1.2 support is enabled!
[    25.886] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[    25.886] (==) fglrx(0): Center Mode is disabled 
[    25.886] (II) Loading sub module "fb"
[    25.886] (II) LoadModule: "fb"
[    25.886] (II) Loading /usr/lib/xorg/modules/libfb.so
[    25.886] (II) Module fb: vendor="X.Org Foundation"
[    25.886] 	compiled for 1.9.0, module version = 1.0.0
[    25.886] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    25.886] (==) fglrx(0): Active stereo disabled
[    25.886] (II) Loading sub module "ddc"
[    25.886] (II) LoadModule: "ddc"
[    25.886] (II) Module "ddc" already built-in
[    26.855] (II) fglrx(0): Output DFP1 using monitor section aticonfig-Monitor[0]-0
[    26.855] (II) fglrx(0): Output DFP2 has no monitor section
[    26.855] (II) fglrx(0): Output CRT1 has no monitor section
[    26.855] (II) fglrx(0): Output CRT2 has no monitor section
[    26.855] (II) fglrx(0): Output TV has no monitor section
[    26.855] (II) fglrx(0): Output CV has no monitor section
[    26.855] (II) Loading sub module "ddc"
[    26.855] (II) LoadModule: "ddc"
[    26.855] (II) Module "ddc" already built-in
[    26.855] (II) fglrx(0): Connected Display0: CRT1
[    26.855] (II) fglrx(0): Display0 EDID data ---------------------------
[    26.855] (II) fglrx(0): Manufacturer: FUS  Model: 7c7  Serial#: 1
[    26.855] (II) fglrx(0): Year: 2009  Week: 53
[    26.855] (II) fglrx(0): EDID Version: 1.3
[    26.855] (II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    26.855] (II) fglrx(0): Sync:  Separate
[    26.855] (II) fglrx(0): Max Image Size [cm]: horiz.: 47  vert.: 30
[    26.855] (II) fglrx(0): Gamma: 2.30
[    26.855] (II) fglrx(0): DPMS capabilities: Off; RGB/Color Display
[    26.855] (II) fglrx(0): First detailed timing is preferred mode
[    26.855] (II) fglrx(0): redX: 0.644 redY: 0.333   greenX: 0.286 greenY: 0.605
[    26.855] (II) fglrx(0): blueX: 0.152 blueY: 0.076   whiteX: 0.313 whiteY: 0.329
[    26.855] (II) fglrx(0): Supported established timings:
[    26.855] (II) fglrx(0): 720x400@70Hz
[    26.855] (II) fglrx(0): 640x480@60Hz
[    26.855] (II) fglrx(0): 640x480@75Hz
[    26.855] (II) fglrx(0): 800x600@60Hz
[    26.855] (II) fglrx(0): 800x600@75Hz
[    26.855] (II) fglrx(0): 1024x768@60Hz
[    26.855] (II) fglrx(0): 1024x768@75Hz
[    26.855] (II) fglrx(0): 1280x1024@75Hz
[    26.856] (II) fglrx(0): Manufacturer's mask: 0
[    26.856] (II) fglrx(0): Supported standard timings:
[    26.856] (II) fglrx(0): #0: hsize: 1440  vsize 900  refresh: 75  vid: 3989
[    26.856] (II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    26.856] (II) fglrx(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    26.856] (II) fglrx(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    26.856] (II) fglrx(0): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    26.856] (II) fglrx(0): #5: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    26.856] (II) fglrx(0): #6: hsize: 1280  vsize 720  refresh: 60  vid: 49281
[    26.856] (II) fglrx(0): Supported detailed timing:
[    26.856] (II) fglrx(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
[    26.856] (II) fglrx(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
[    26.856] (II) fglrx(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
[    26.856] (II) fglrx(0): Serial No: YV1U055361
[    26.856] (II) fglrx(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 155 MHz
[    26.856] (II) fglrx(0): Monitor name: SL3220W
[    26.856] (II) fglrx(0): EDID (in hex):
[    26.856] (II) fglrx(0): 	00ffffffffffff001ab3c70701000000
[    26.856] (II) fglrx(0): 	35130103682f1e822ad425a455499b27
[    26.856] (II) fglrx(0): 	135054a54b00950f81808140714f9500
[    26.856] (II) fglrx(0): 	b30081c0010121399030621a274068b0
[    26.856] (II) fglrx(0): 	3600da281100001c000000ff00595631
[    26.856] (II) fglrx(0): 	553035353336310a2020000000fd0038
[    26.856] (II) fglrx(0): 	4b1e530f000a202020202020000000fc
[    26.856] (II) fglrx(0): 	00534c33323230570a2020202020000f
[    26.856] (II) fglrx(0): End of Display0 EDID data --------------------
[    27.039] (II) fglrx(0): Output DFP1 disconnected
[    27.039] (II) fglrx(0): Output DFP2 disconnected
[    27.039] (II) fglrx(0): Output CRT1 connected
[    27.039] (II) fglrx(0): Output CRT2 disconnected
[    27.039] (II) fglrx(0): Output TV disconnected
[    27.039] (II) fglrx(0): Output CV disconnected
[    27.039] (II) fglrx(0): Using exact sizes for initial modes
[    27.039] (II) fglrx(0): Output CRT1 using initial mode 1680x1050
[    27.039] (II) fglrx(0): DPI set to (96, 96)
[    27.039] (II) fglrx(0): Adapter ATI Radeon HD 4800 Series         has 2 configurable heads and 1 displays connected.
[    27.039] (==) fglrx(0):  PseudoColor visuals disabled
[    27.039] (II) Loading sub module "ramdac"
[    27.039] (II) LoadModule: "ramdac"
[    27.039] (II) Module "ramdac" already built-in
[    27.039] (==) fglrx(0): NoDRI = NO
[    27.039] (==) fglrx(0): Capabilities: 0x00000000
[    27.040] (==) fglrx(0): CapabilitiesEx: 0x00000000
[    27.040] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[    27.040] (==) fglrx(0): UseFastTLS=0
[    27.040] (==) fglrx(0): BlockSignalsOnLock=1
[    27.040] (--) Depth 24 pixmap format is 32 bpp
[    27.040] (EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
[    27.040] (WW) fglrx(0): ***********************************************************
[    27.040] (WW) fglrx(0): * DRI initialization failed                               *
[    27.040] (WW) fglrx(0): * kernel module (fglrx.ko) may be missing or incompatible *
[    27.040] (WW) fglrx(0): * 2D and 3D acceleration disabled                         *
[    27.040] (WW) fglrx(0): ***********************************************************
[    27.040] (II) fglrx(0): FBADPhys: 0xf00000000 FBMappedSize: 0x10000000
[    27.064] (II) fglrx(0): FBMM initialized for area (0,0)-(1728,8191)
[    27.064] (II) fglrx(0): FBMM auto alloc for area (0,0)-(1728,1680) (front color buffer - assumption)
[    27.064] (II) fglrx(0): Largest offscreen area available: 1728 x 6511
[    27.065] (==) fglrx(0): Backing store disabled
[    27.065] (II) Loading extension FGLRXEXTENSION
[    27.065] (**) fglrx(0): DPMS enabled
[    27.065] (II) fglrx(0): Initialized in-driver Xinerama extension
[    27.065] (WW) fglrx(0): Textured Video not supported without DRI enabled.
[    27.065] (II) LoadModule: "glesx"
[    27.065] (II) Loading /usr/lib/xorg/modules/glesx.so
[    27.066] (II) Module glesx: vendor="X.Org Foundation"
[    27.066] 	compiled for 1.8.99.905, module version = 1.0.0
[    27.066] (II) Loading extension GLESX
[    27.066] (II) fglrx(0): GLESX enableFlags = 512
[    27.066] (II) fglrx(0): Acceleration enabled
[    27.066] (II) LoadModule: "amdxmm"
[    27.067] (II) Loading /usr/lib/xorg/modules/amdxmm.so
[    27.067] (II) Module amdxmm: vendor="X.Org Foundation"
[    27.067] 	compiled for 1.8.99.905, module version = 1.0.0
[    27.067] (EE) fglrx(0): XMM failed to open CMMQS connection.
[    27.067] (EE) fglrx(0): XMM failed to initialize
[    27.067] (WW) fglrx(0): No XV video playback available
[    27.067] (II) fglrx(0): Enable composite support successfully
[    27.067] (WW) fglrx(0): Option "VendorName" is not used
[    27.067] (WW) fglrx(0): Option "ModelName" is not used
[    27.067] (==) fglrx(0): Silken mouse enabled
[    27.067] (==) fglrx(0): Using HW cursor of display infrastructure!
[    27.067] (II) fglrx(0): Disabling in-server RandR and enabling in-driver RandR 1.2.
[    27.067] (II) fglrx(0): Cannot get TV Format. Set all TV geometry value to zero!
[    27.067] (II) fglrx(0): Cannot get TV Format for trying to adjust horizontal position after horizontal size changed. 
[    27.131] (--) RandR disabled
[    27.131] (II) Initializing built-in extension Generic Event Extension
[    27.131] (II) Initializing built-in extension SHAPE
[    27.131] (II) Initializing built-in extension MIT-SHM
[    27.131] (II) Initializing built-in extension XInputExtension
[    27.131] (II) Initializing built-in extension XTEST
[    27.131] (II) Initializing built-in extension BIG-REQUESTS
[    27.131] (II) Initializing built-in extension SYNC
[    27.131] (II) Initializing built-in extension XKEYBOARD
[    27.131] (II) Initializing built-in extension XC-MISC
[    27.131] (II) Initializing built-in extension SECURITY
[    27.131] (II) Initializing built-in extension XINERAMA
[    27.131] (II) Initializing built-in extension XFIXES
[    27.131] (II) Initializing built-in extension RENDER
[    27.131] (II) Initializing built-in extension RANDR
[    27.131] (II) Initializing built-in extension COMPOSITE
[    27.131] (II) Initializing built-in extension DAMAGE
[    27.131] (II) Initializing built-in extension GESTURE
[    27.133] 
Backtrace:
[    27.133] 0: /usr/bin/X (xorg_backtrace+0x28) [0x4a0fa8]
[    27.133] 1: /usr/bin/X (0x400000+0x60fcd) [0x460fcd]
[    27.133] 2: /lib/libpthread.so.0 (0x7fe062738000+0xfb40) [0x7fe062747b40]
[    27.133] 3: /usr/lib/xorg/modules/drivers/fglrx_drv.so (xdl_x760_swlDriOpenConnection+0x3a) [0x7fe05f2d5e2a]
[    27.134] 4: /usr/lib/xorg/modules/drivers/fglrx_drv.so (swlDriOpenConnection+0xd) [0x7fe05f20e00d]
[    27.134] 5: /usr/lib/xorg/modules/extensions/libglx.so (0x7fe0603a9000+0x1a163) [0x7fe0603c3163]
[    27.134] 6: /usr/lib/xorg/modules/extensions/libglx.so (0x7fe0603a9000+0x1c325) [0x7fe0603c5325]
[    27.134] 7: /usr/bin/X (InitExtensions+0x89) [0x487679]
[    27.134] 8: /usr/bin/X (0x400000+0x216a5) [0x4216a5]
[    27.134] 9: /lib/libc.so.6 (__libc_start_main+0xfe) [0x7fe0616a3d8e]
[    27.134] 10: /usr/bin/X (0x400000+0x213d9) [0x4213d9]
[    27.134] Segmentation fault at address 0xa0
[    27.134] 
Caught signal 11 (Segmentation fault). Server aborting
[    27.134] 
Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[    27.134] Please also check the log file at "/var/log/Xorg.1.log" for additional information.
[    27.134] 
[    27.439] (EE) fglrx(0): firegl_SetSuspendResumeState FAILED -9.
[    27.447]  ddxSigGiveUp: Closing log

---

### Post by jim_deadlock on 2010-11-26
If /etc/xorg.conf exists, try deleting it and reboot.

---

### Post by dino99 on 2010-11-26
[http://ubuntuforums.org/showpost.php?p=10164766&postcount=2](http://ubuntuforums.org/showpost.php?p=10164766&postcount=2)

---

### Post by logan85 on 2010-11-26
thanks, but doesn't exist...
rm: cannot remove `/etc/xorg.conf': No such file or directory

---

### Post by logan85 on 2010-11-26
I'm using an Ati videocard, should I reinstall it's driver?
FailsafeX it's working, and just deleting the /etc/X11/xorg.conf does not solve the problem...

Reinstalling the Ati driver worked...

---

### Post by bobyl573 on 2010-11-27
can you elaborate what fixed this problem? I have the same problem, and by deleting the xorg file I can boot in. But running glxgears or flgrxinfo gives me Segmentation Fault. It worked for kernel 2.6.35-22 but ever since I upgraded to 2.6.35-23, I've been having all these ati driver issues

---

### Post by logan85 on 2010-11-28
first, I deleted the /etc/X11/xorg.conf file, then run the uninstall script sudo sh /usr/share/ati/fglrx-uninstall.sh, download the catalyst 10.11 driver from Ati's homepage, reboot, navigate to the directory where the downloaded driver is, and run it with sudo sh ./ati*

I hope this will help you!

---

### Post by bobyl573 on 2010-11-28
> **logan85 said:**
> first, I deleted the /etc/X11/xorg.conf file, then run the uninstall script sudo sh /usr/share/ati/fglrx-uninstall.sh, download the catalyst 10.11 driver from Ati's homepage, reboot, navigate to the directory where the downloaded driver is, and run it with sudo sh ./ati*

I hope this will help you!

solved! thanks!

---

