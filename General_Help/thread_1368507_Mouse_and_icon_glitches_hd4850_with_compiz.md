---
title: "Mouse and icon glitches hd4850 with compiz"
date: 2009-12-30
forum: General Help
---

### Post by krikke on 2009-12-30
Hi,

After having some serious difficulties with the proprietary ati drivers, resulting in extreme slowness and fullscreen problems, I installed the opensource drivers by using the xorg edgers source.

With the proprietary ati drivers, everything was slow but there were no glitches. With this drivers my mouse is completely broken (unless I use openoffice), and my icons are having weird glitches also as you can see on the picture:

[[IMG]http://img85.imageshack.us/img85/2530/screenshotdl.png[/IMG]]("http://img691.imageshack.us/img691/1558/screenshotqek.png")

I'm using the newest xorg server 1.6.5, ubuntu 9.10, and kernel 2.6.32. Is this a common problem? I've included the xorg log:

```

X.Org X Server 1.6.5
Release Date: 2009-10-11
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-25-xen i686 Ubuntu
Current Operating System: Linux christophe-desktop 2.6.32-020632-generic #020632 SMP Thu Dec 3 10:58:45 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-020632-generic root=UUID=cb775073-5e68-4b8b-bebd-d28881c5ed1a ro quiet splash
Build Date: 07 November 2009  04:37:35PM
xorg-server 2:1.6.5+git20091107+server-1.6-branch.2dbcb06a-0ubuntu0sarvatt~karmic (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Dec 30 17:26:33 2009
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(--) using VT number 7

(--) PCI:*(0:1:0:0) 1002:9442:1002:0502 ATI Technologies Inc RV770 [Radeon HD 4850] rev 0, Mem @ 0xe0000000/268435456, 0xf0100000/65536, I/O @ 0x00004000/256, BIOS @ 0x????????/131072
(==) Using default built-in configuration (30 lines)
(==) --- Start of built-in configuration ---
	Section "Device"
		Identifier	"Builtin Default ati Device 0"
		Driver	"ati"
	EndSection
	Section "Screen"
		Identifier	"Builtin Default ati Screen 0"
		Device	"Builtin Default ati Device 0"
	EndSection
	Section "Device"
		Identifier	"Builtin Default vesa Device 0"
		Driver	"vesa"
	EndSection
	Section "Screen"
		Identifier	"Builtin Default vesa Screen 0"
		Device	"Builtin Default vesa Device 0"
	EndSection
	Section "Device"
		Identifier	"Builtin Default fbdev Device 0"
		Driver	"fbdev"
	EndSection
	Section "Screen"
		Identifier	"Builtin Default fbdev Screen 0"
		Device	"Builtin Default fbdev Device 0"
	EndSection
	Section "ServerLayout"
		Identifier	"Builtin Default Layout"
		Screen	"Builtin Default ati Screen 0"
		Screen	"Builtin Default vesa Screen 0"
		Screen	"Builtin Default fbdev Screen 0"
	EndSection
(==) --- End of built-in configuration ---
(==) ServerLayout "Builtin Default Layout"
(**) |-->Screen "Builtin Default ati Screen 0" (0)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default ati Device 0"
(==) No monitor specified for screen "Builtin Default ati Screen 0".
	Using a default monitor configuration.
(**) |-->Screen "Builtin Default vesa Screen 0" (1)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default vesa Device 0"
(==) No monitor specified for screen "Builtin Default vesa Screen 0".
	Using a default monitor configuration.
(**) |-->Screen "Builtin Default fbdev Screen 0" (2)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default fbdev Device 0"
(==) No monitor specified for screen "Builtin Default fbdev Screen 0".
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
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.5, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.5, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.6.5, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.5, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.5, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.5, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 1.6.5, module version = 6.12.99
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.6.5, module version = 6.12.99
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 2.2.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers//fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.4.0
	ABI class: X.Org Video Driver, version 5.0
(II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
	ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
	ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
	ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
	ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon 8500 AIW BC (AGP),
	ATI Radeon IGP320M (U1) 4336, ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
	ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
	ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
	ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
	ATI Radeon 9800XT NJ (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
	ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
	ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835,
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE),
	ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE),
	ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
	ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
	ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
	ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
	ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
	ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
	ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
	ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
	ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
	ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
	ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
	ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
	ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
	ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
	ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
	ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
	ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
	ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
	ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
	ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
	ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
	ATI Mobility Radeon X1700, ATI Radeon X2300HD,
	ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
	ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
	ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
	ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
	ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
	ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
	ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
	ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
	ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
	ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
	ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
	ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
	ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
	ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
	ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
	AMD FireStream 9250, ATI FirePro V8700 (FireGL),
	ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
	ATI Radeon 4800 Series, ATI Radeon 4800 Series, ATI FirePro M7750,
	ATI M98, ATI M98, ATI M98, ATI Mobility Radeon HD 4650,
	ATI Radeon RV730 (AGP), ATI Mobility Radeon HD 4670,
	ATI FirePro M5750, ATI Radeon RV730 (AGP),
	ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
	ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
	ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
	ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
	ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
	ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
	ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
	ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
	ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
	ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
	ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
	ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
	ATI Mobility Radeon HD 3850 X2, ATI RV670,
	ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
	ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
	ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
	ATI Radeon RV710, ATI Radeon RV710, ATI Radeon HD 4350,
	ATI Mobility Radeon 4300 Series, ATI Mobility Radeon 4500 Series,
	ATI Mobility Radeon 4500 Series, ATI FirePro RG220, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI Radeon HD 2600 LE,
	ATI Mobility FireGL Graphics Processor, ATI Radeon RV710,
	ATI Radeon HD 3470, ATI Mobility Radeon HD 3430,
	ATI Mobility Radeon HD 3400 Series, ATI Radeon HD 3450,
	ATI Radeon HD 3450, ATI Radeon HD 3430, ATI Radeon HD 3450,
	ATI FirePro V3700, ATI FireMV 2450, ATI FireMV 2260, ATI FireMV 2260,
	ATI Radeon HD 3600 Series, ATI Radeon HD 3650 AGP,
	ATI Radeon HD 3600 PRO, ATI Radeon HD 3600 XT,
	ATI Radeon HD 3600 PRO, ATI Mobility Radeon HD 3650,
	ATI Mobility Radeon HD 3670, ATI Mobility FireGL V5700,
	ATI Mobility FireGL V5725, ATI Radeon HD 3200 Graphics,
	ATI Radeon 3100 Graphics, ATI Radeon HD 3200 Graphics,
	ATI Radeon 3100 Graphics, ATI Radeon HD 3300 Graphics,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3000 Graphics,
	ATI Radeon HD 4200, ATI Radeon 4100, ATI Mobility Radeon HD 4200,
	ATI Mobility Radeon 4100, ATI RS880
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 01@00:00:0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) [KMS] drm report modesetting isn't supported.
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux//libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 1.6.5, module version = 0.0.2
	ABI class: X.Org Video Driver, version 5.0
(EE) open /dev/fb0: No such file or directory
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) RADEON(0): Built from git commit 9d0f3af7278dc939fd4e6f3ea69d9f488a9fbed7
(II) RADEON(0): TOTO SAYS 00000000f0100000
(II) RADEON(0): MMIO registers at 0x00000000f0100000: size 64KB
(II) RADEON(0): PCI bus 1 card 0 func 0
(II) RADEON(0): Creating default Display subsection in Screen section
	"Builtin Default ati Screen 0" for depth/fbbpp 24/32
(==) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.6.5, module version = 0.1.0
	ABI class: X.Org Video Driver, version 5.0
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(--) RADEON(0): Chipset: "ATI Radeon 4800 Series" (ChipID = 0x9442)
(--) RADEON(0): Linear framebuffer at 0x00000000e0000000
(II) RADEON(0): PCIE card detected
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.6.5, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(II) RADEON(0): ATOM BIOS detected
(II) RADEON(0): ATOM BIOS Rom: 
	SubsystemVendorID: 0x1002 SubsystemID: 0x0502
	IOBaseAddress: 0x4000
	Filename: B3B50102.103
	BIOS Bootup Message: 

Wekiva RV770 B50102 Board                                                   


(II) RADEON(0): Framebuffer space used by Firmware (kb): 20
(II) RADEON(0): Start of VRAM area used by Firmware: 0x7ffec
(II) RADEON(0): AtomBIOS requests 20kB of VRAM scratch space
(II) RADEON(0): AtomBIOS VRAM scratch base: 0x7ffec
(II) RADEON(0): Cannot get VRAM scratch space. Allocating in main memory instead
(II) RADEON(0): Default Engine Clock: 625000
(II) RADEON(0): Default Memory Clock: 993000
(II) RADEON(0): Maximum Pixel ClockPLL Frequency Output: 1200000
(II) RADEON(0): Minimum Pixel ClockPLL Frequency Output: 0
(II) RADEON(0): Maximum Pixel ClockPLL Frequency Input: 16000
(II) RADEON(0): Minimum Pixel ClockPLL Frequency Input: 6000
(II) RADEON(0): Maximum Pixel Clock: 400000
(II) RADEON(0): Reference Clock: 100000
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) RADEON(0): [dri] Found DRI library version 1.3.0 and kernel module version 1.31.0
(==) RADEON(0): Page Flipping disabled on r5xx and newer chips.

(II) RADEON(0): Will try to use DMA for Xv image transfers
(II) RADEON(0): Detected total video RAM=524288K, accessible=262144K (PCI BAR=262144K)
(--) RADEON(0): Mapped VideoRAM: 262144 kByte (128 bit DDR SDRAM)
(II) RADEON(0): Color tiling disabled
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) RADEON(0): PLL parameters: rf=10000 rd=12 min=60000 max=120000; xclk=40000
(II) RADEON(0): Output DVI-1 has no monitor section
(II) RADEON(0): I2C bus "DVI-1" initialized.
(II) RADEON(0): Output DVI-0 has no monitor section
(II) RADEON(0): I2C bus "DVI-0" initialized.
(II) RADEON(0): Port0:
  XRANDR name: DVI-1
  Connector: DVI-I
  CRT2: INTERNAL_KLDSCP_DAC2
  DFP1: INTERNAL_UNIPHY
  DDC reg: 0x7e60
(II) RADEON(0): Port1:
  XRANDR name: DVI-0
  Connector: DVI-I
  CRT1: INTERNAL_KLDSCP_DAC1
  DFP2: INTERNAL_KLDSCP_LVTMA
  DDC reg: 0x7e20
(II) RADEON(0): I2C device "DVI-1:E-EDID segment register" registered at address 0x60.
(II) RADEON(0): I2C device "DVI-1:ddc2" registered at address 0xA0.
Dac detection success
(II) RADEON(0): Output: DVI-1, Detected Monitor Type: 0
Unhandled monitor type 0
finished output detect: 0
(II) RADEON(0): I2C device "DVI-0:E-EDID segment register" registered at address 0x60.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: 4035  Serial#: 808990284
(II) RADEON(0): Year: 2009  Week: 33
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 65  vert.: 41
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.678 redY: 0.309   greenX: 0.210 greenY: 0.692
(II) RADEON(0): blueX: 0.146 blueY: 0.055   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #1: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEON(0): #2: hsize: 1920  vsize 1200  refresh: 60  vid: 209
(II) RADEON(0): #3: hsize: 1920  vsize 1440  refresh: 60  vid: 16593
(II) RADEON(0): #4: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #5: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) RADEON(0): #6: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 268.0 MHz   Image Size:  641 x 400 mm
(II) RADEON(0): h_active: 2560  h_sync: 2608  h_sync_end 2640 h_blank_end 2720 h_border: 0
(II) RADEON(0): v_active: 1600  v_sync: 1603  v_sync_end 1609 v_blanking: 1646 v_border: 0
(II) RADEON(0): Serial No: G501H98C086L
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 154.0 MHz   Image Size:  641 x 401 mm
(II) RADEON(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1203  v_sync_end 1209 v_blanking: 1235 v_border: 0
(II) RADEON(0): Ranges: V min: 49 V max: 86 Hz, H min: 29 H max: 113 kHz, PixClock max 280 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010ac35404c363830
(II) RADEON(0): 	2113010380412978ea8d85ad4f35b125
(II) RADEON(0): 	0e5054a54b008180a940d100d140714f
(II) RADEON(0): 	8100b3000101b06800a0a0402e603020
(II) RADEON(0): 	360081902100001e000000ff00473530
(II) RADEON(0): 	31483938433038364c0a283c80a070b0
(II) RADEON(0): 	23403020360081912100001c000000fd
(II) RADEON(0): 	0031561d711c000a202020202020004e
finished output detect: 1
finished all detect
before xf86InitialConfiguration
Dac detection success
(II) RADEON(0): Output: DVI-1, Detected Monitor Type: 0
Unhandled monitor type 0
(II) RADEON(0): EDID for output DVI-1
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Manufacturer: DEL  Model: 4035  Serial#: 808990284
(II) RADEON(0): Year: 2009  Week: 33
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 65  vert.: 41
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.678 redY: 0.309   greenX: 0.210 greenY: 0.692
(II) RADEON(0): blueX: 0.146 blueY: 0.055   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #1: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEON(0): #2: hsize: 1920  vsize 1200  refresh: 60  vid: 209
(II) RADEON(0): #3: hsize: 1920  vsize 1440  refresh: 60  vid: 16593
(II) RADEON(0): #4: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #5: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) RADEON(0): #6: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 268.0 MHz   Image Size:  641 x 400 mm
(II) RADEON(0): h_active: 2560  h_sync: 2608  h_sync_end 2640 h_blank_end 2720 h_border: 0
(II) RADEON(0): v_active: 1600  v_sync: 1603  v_sync_end 1609 v_blanking: 1646 v_border: 0
(II) RADEON(0): Serial No: G501H98C086L
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 154.0 MHz   Image Size:  641 x 401 mm
(II) RADEON(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1203  v_sync_end 1209 v_blanking: 1235 v_border: 0
(II) RADEON(0): Ranges: V min: 49 V max: 86 Hz, H min: 29 H max: 113 kHz, PixClock max 280 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010ac35404c363830
(II) RADEON(0): 	2113010380412978ea8d85ad4f35b125
(II) RADEON(0): 	0e5054a54b008180a940d100d140714f
(II) RADEON(0): 	8100b3000101b06800a0a0402e603020
(II) RADEON(0): 	360081902100001e000000ff00473530
(II) RADEON(0): 	31483938433038364c0a283c80a070b0
(II) RADEON(0): 	23403020360081912100001c000000fd
(II) RADEON(0): 	0031561d711c000a202020202020004e
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: 4035  Serial#: 808990284
(II) RADEON(0): Year: 2009  Week: 33
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 65  vert.: 41
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.678 redY: 0.309   greenX: 0.210 greenY: 0.692
(II) RADEON(0): blueX: 0.146 blueY: 0.055   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #1: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEON(0): #2: hsize: 1920  vsize 1200  refresh: 60  vid: 209
(II) RADEON(0): #3: hsize: 1920  vsize 1440  refresh: 60  vid: 16593
(II) RADEON(0): #4: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #5: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) RADEON(0): #6: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 268.0 MHz   Image Size:  641 x 400 mm
(II) RADEON(0): h_active: 2560  h_sync: 2608  h_sync_end 2640 h_blank_end 2720 h_border: 0
(II) RADEON(0): v_active: 1600  v_sync: 1603  v_sync_end 1609 v_blanking: 1646 v_border: 0
(II) RADEON(0): Serial No: G501H98C086L
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 154.0 MHz   Image Size:  641 x 401 mm
(II) RADEON(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1203  v_sync_end 1209 v_blanking: 1235 v_border: 0
(II) RADEON(0): Ranges: V min: 49 V max: 86 Hz, H min: 29 H max: 113 kHz, PixClock max 280 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010ac35404c363830
(II) RADEON(0): 	2113010380412978ea8d85ad4f35b125
(II) RADEON(0): 	0e5054a54b008180a940d100d140714f
(II) RADEON(0): 	8100b3000101b06800a0a0402e603020
(II) RADEON(0): 	360081902100001e000000ff00473530
(II) RADEON(0): 	31483938433038364c0a283c80a070b0
(II) RADEON(0): 	23403020360081912100001c000000fd
(II) RADEON(0): 	0031561d711c000a202020202020004e
(II) RADEON(0): Panel infos found from DDC detailed: 2560x1600
(II) RADEON(0): EDID vendor "DEL", prod id 16437
(II) RADEON(0): Printing probed modes for output DVI-0
(II) RADEON(0): Modeline "2560x1600"x59.9  268.00  2560 2608 2640 2720  1600 1603 1609 1646 +hsync +vsync (98.5 kHz)
(II) RADEON(0): Modeline "1920x1440"x60.0  234.00  1920 2048 2256 2600  1440 1441 1444 1500 -hsync +vsync (90.0 kHz)
(II) RADEON(0): Modeline "1920x1200"x60.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 -hsync +vsync (74.0 kHz)
(II) RADEON(0): Modeline "1920x1200"x60.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
(II) RADEON(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) RADEON(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
(II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Output DVI-1 disconnected
(II) RADEON(0): Output DVI-0 connected
(II) RADEON(0): Using exact sizes for initial modes
(II) RADEON(0): Output DVI-0 using initial mode 2560x1600
(==) RADEON(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.5, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(==) RADEON(0): Will attempt to use R6xx/R7xx EXA support if DRI is enabled.
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
	compiled for 1.6.5, module version = 2.4.0
	ABI class: X.Org Video Driver, version 5.0
(!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
(II) UnloadModule: "vesa"
(II) Unloading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers//fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux//libfbdevhw.so
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) RADEON(0): RADEONScreenInit e0000000 0 0
(II) RADEON(0): DIG0 transmitter: Coherent Mode enabled
Output DIG0 transmitter setup success
Blank CRTC 0 success
Disable CRTC memreq 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC memreq 1 success
Disable CRTC 1 success
(II) RADEON(0): Dynamic Power Management Disabled
(==) RADEON(0): Using 24 bit depth buffer
mc fb loc is 00ff00e0
(II) RADEON(0): RADEONInitMemoryMap() : 
(II) RADEON(0):   mem_size         : 0x20000000
(II) RADEON(0):   MC_FB_LOCATION   : 0x00ff00e0
(II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
(II) RADEON(0): Depth moves disabled by default
(II) RADEON(0): Allocating from a screen of 262080 kb
(II) RADEON(0): Will use 32 kb for hardware cursor 0 at offset 0x01900000
(II) RADEON(0): Will use 32 kb for hardware cursor 1 at offset 0x01904000
(II) RADEON(0): Will use 25600 kb for front buffer at offset 0x00000000
(II) RADEON(0): Will use 64 kb for PCI GART at offset 0x0fff0000
(II) RADEON(0): Will use 25600 kb for back buffer at offset 0x01908000
(II) RADEON(0): Will use 25600 kb for depth buffer at offset 0x03208000
(II) RADEON(0): Will use 92160 kb for textures at offset 0x04b08000
(II) RADEON(0): Will use 93088 kb for X Server offscreen at offset 0x0a508000
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) RADEON(0): [drm] Using the DRM lock SAREA also for drawables.
(II) RADEON(0): [drm] framebuffer handle = 0xe0000000
(II) RADEON(0): [drm] added 1 reserved context for kernel
(II) RADEON(0): X context handle = 0x1
(II) RADEON(0): [drm] installed DRM signal handler
(II) RADEON(0): [pci] 32768 kB allocated with handle 0xf8bc8000
(II) RADEON(0): [pci] ring handle = 0xf8bc8000
(II) RADEON(0): [pci] Ring mapped at 0xb71c2000
(II) RADEON(0): [pci] Ring contents 0x00000000
(II) RADEON(0): [pci] ring read ptr handle = 0xf8cc9000
(II) RADEON(0): [pci] Ring read ptr mapped at 0xb71c1000
(II) RADEON(0): [pci] Ring read ptr contents 0x00000000
(II) RADEON(0): [pci] vertex/indirect buffers handle = 0xf8cca000
(II) RADEON(0): [pci] Vertex/indirect buffers mapped at 0xa6f23000
(II) RADEON(0): [pci] Vertex/indirect buffers contents 0x00000000
(II) RADEON(0): [pci] GART texture map handle = 0xf8eca000
(II) RADEON(0): [pci] GART Texture map mapped at 0xa52a3000
(II) RADEON(0): [drm] register handle = 0x2e020000
(II) RADEON(0): [dri] Visual configs initialized
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x00ff00e0 0x001f0000
(II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
(==) RADEON(0): Backing store disabled
(II) RADEON(0): [DRI] installation complete
(II) RADEON(0): [drm] Added 32 65536 byte vertex/indirect buffers
(II) RADEON(0): [drm] Mapped 32 vertex/indirect buffers
(II) RADEON(0): [drm] dma control initialized, using IRQ 16
(II) RADEON(0): [drm] Initialized kernel GART heap manager, 29884416
(WW) RADEON(0): DRI init changed memory map, adjusting ...
(WW) RADEON(0):   MC_FB_LOCATION  was: 0x00ff00e0 is: 0x00ff00e0
(WW) RADEON(0):   MC_AGP_LOCATION was: 0x003f0000 is: 0x00030000
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x00ff00e0 0x00ff00e0
(II) RADEON(0):   MC_AGP_LOCATION  : 0x00030000
(II) RADEON(0): Direct rendering enabled
(II) RADEON(0): Setting EXA maxPitchBytes
(II) EXA(0): Offscreen pixmap area of 95322112 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(II)         UploadToScreen
(II)         DownloadFromScreen
(II) RADEON(0): Acceleration enabled
(II) RADEON(0): DPMS enabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Set up textured video
(II) RADEON(0): DIG0 transmitter: Coherent Mode enabled
Output DIG0 transmitter setup success
Blank CRTC 0 success
Disable CRTC memreq 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC memreq 1 success
Disable CRTC 1 success
(II) RADEON(0): DIG0 transmitter: Coherent Mode enabled
Output DIG0 transmitter setup success
Blank CRTC 0 success
Disable CRTC memreq 0 success
Disable CRTC 0 success
Mode 2560x1600 - 2720 1646 5
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x00ff00e0 0x00ff00e0
(II) RADEON(0):   MC_AGP_LOCATION  : 0x00030000
before 26800
after 26800
ffreq: 268000.000000
best_freq: 268000
best_feedback_div: 75.0
best_ref_div: 7
best_post_div: 4
(II) RADEON(0): crtc(0) Clock: mode 268000, PLL 268000
(II) RADEON(0): crtc(0) PLL  : refdiv 7, fbdiv 0x4B(75), fracfbdiv 0, pdiv 4
Set CRTC 0 PLL success
Set CRTC Timing success
Set CRTC 0 Overscan success
Not using RMX
scaler 0 setup success
Set CRTC 0 Source success
crtc 0 YUV disable setup success
(II) RADEON(0): DIG0 transmitter: Coherent Mode enabled
Output DIG0 transmitter setup success
Output DIG2 encoder setup success
Output DIG2 encoder setup success
(II) RADEON(0): DIG0 transmitter: Coherent Mode enabled
Output DIG0 transmitter setup success
(II) RADEON(0): DIG0 transmitter: Coherent Mode enabled
Output DIG0 transmitter setup success
(II) RADEON(0): DIG0 transmitter: Coherent Mode enabled
Output DIG0 transmitter setup success
(II) RADEON(0): DIG0 transmitter: Coherent Mode enabled
Output DIG0 transmitter setup success
Enable CRTC 0 success
Enable CRTC memreq 0 success
Unblank CRTC 0 success
Blank CRTC 1 success
Disable CRTC memreq 1 success
Disable CRTC 1 success
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) RADEON(0): DIG0 transmitter: Coherent Mode enabled
Output DIG0 transmitter setup success
Blank CRTC 0 success
Disable CRTC memreq 0 success
Disable CRTC 0 success
Mode 2560x1600 - 2720 1646 5
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x00ff00e0 0x00ff00e0
(II) RADEON(0):   MC_AGP_LOCATION  : 0x00030000
before 26800
after 26800
ffreq: 268000.000000
best_freq: 268000
best_feedback_div: 75.0
best_ref_div: 7
best_post_div: 4
(II) RADEON(0): crtc(0) Clock: mode 268000, PLL 268000
(II) RADEON(0): crtc(0) PLL  : refdiv 7, fbdiv 0x4B(75), fracfbdiv 0, pdiv 4
Set CRTC 0 PLL success
Set CRTC Timing success
Set CRTC 0 Overscan success
Not using RMX
scaler 0 setup success
Set CRTC 0 Source success
crtc 0 YUV disable setup success
(II) RADEON(0): DIG0 transmitter: Coherent Mode enabled
Output DIG0 transmitter setup success
Output DIG2 encoder setup success
Output DIG2 encoder setup success
(II) RADEON(0): DIG0 transmitter: Coherent Mode enabled
Output DIG0 transmitter setup success
(II) RADEON(0): DIG0 transmitter: Coherent Mode enabled
Output DIG0 transmitter setup success
(II) RADEON(0): DIG0 transmitter: Coherent Mode enabled
Output DIG0 transmitter setup success
(II) RADEON(0): DIG0 transmitter: Coherent Mode enabled
Output DIG0 transmitter setup success
Enable CRTC 0 success
Enable CRTC memreq 0 success
Unblank CRTC 0 success
(--) RandR disabled
(II) Setting vga for screen 0.
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
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_make_current_read
(II) AIGLX: enabled GLX_texture_from_pixmap with driver support
(II) AIGLX: Loaded and initialized /usr/lib/dri/r600_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) RADEON(0): Setting screen physical size to 641 x 400
(II) config/hal: Adding input device HID 1267:0103
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.5, module version = 2.3.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) HID 1267:0103: always reports core events
(**) HID 1267:0103: Device: "/dev/input/event4"
(II) HID 1267:0103: Found 1 mouse buttons
(II) HID 1267:0103: Found scroll wheel(s)
(II) HID 1267:0103: Found relative axes
(II) HID 1267:0103: Found absolute axes
(II) HID 1267:0103: Found keys
(II) HID 1267:0103: Configuring as mouse
(II) HID 1267:0103: Configuring as keyboard
(**) HID 1267:0103: YAxisMapping: buttons 4 and 5
(**) HID 1267:0103: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "HID 1267:0103" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "be"
(EE) HID 1267:0103: failed to initialize for relative axes.
(**) HID 1267:0103: (accel) keeping acceleration scheme 1
(**) HID 1267:0103: (accel) filter chain progression: 2.00
(**) HID 1267:0103: (accel) filter stage 0: 20.00 ms
(**) HID 1267:0103: (accel) set acceleration profile 0
(II) HID 1267:0103: initialized for absolute axes.
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "be"
(II) config/hal: Adding input device Logitech USB Receiver
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event6"
(II) Logitech USB Receiver: Found 1 mouse buttons
(II) Logitech USB Receiver: Found scroll wheel(s)
(II) Logitech USB Receiver: Found relative axes
(II) Logitech USB Receiver: Found absolute axes
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as mouse
(II) Logitech USB Receiver: Configuring as keyboard
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "be"
(EE) Logitech USB Receiver: failed to initialize for relative axes.
(**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
(**) Logitech USB Receiver: (accel) filter chain progression: 2.00
(**) Logitech USB Receiver: (accel) filter stage 0: 20.00 ms
(**) Logitech USB Receiver: (accel) set acceleration profile 0
(II) Logitech USB Receiver: initialized for absolute axes.
(II) config/hal: Adding input device HID 1267:0103
(**) HID 1267:0103: always reports core events
(**) HID 1267:0103: Device: "/dev/input/event3"
(II) HID 1267:0103: Found keys
(II) HID 1267:0103: Configuring as keyboard
(II) XINPUT: Adding extended input device "HID 1267:0103" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "be"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "be"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/hal: Adding input device Logitech USB Receiver
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event5"
(II) Logitech USB Receiver: Found 20 mouse buttons
(II) Logitech USB Receiver: Found scroll wheel(s)
(II) Logitech USB Receiver: Found relative axes
(II) Logitech USB Receiver: Found x and y relative axes
(II) Logitech USB Receiver: Configuring as mouse
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: MOUSE)
(**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
(**) Logitech USB Receiver: (accel) filter chain progression: 2.00
(**) Logitech USB Receiver: (accel) filter stage 0: 20.00 ms
(**) Logitech USB Receiver: (accel) set acceleration profile 0
(II) Logitech USB Receiver: initialized for relative axes.
Dac detection success
(II) RADEON(0): Output: DVI-1, Detected Monitor Type: 0
Unhandled monitor type 0
(II) RADEON(0): EDID for output DVI-1
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Manufacturer: DEL  Model: 4035  Serial#: 808990284
(II) RADEON(0): Year: 2009  Week: 33
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 65  vert.: 41
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.678 redY: 0.309   greenX: 0.210 greenY: 0.692
(II) RADEON(0): blueX: 0.146 blueY: 0.055   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #1: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEON(0): #2: hsize: 1920  vsize 1200  refresh: 60  vid: 209
(II) RADEON(0): #3: hsize: 1920  vsize 1440  refresh: 60  vid: 16593
(II) RADEON(0): #4: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #5: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) RADEON(0): #6: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 268.0 MHz   Image Size:  641 x 400 mm
(II) RADEON(0): h_active: 2560  h_sync: 2608  h_sync_end 2640 h_blank_end 2720 h_border: 0
(II) RADEON(0): v_active: 1600  v_sync: 1603  v_sync_end 1609 v_blanking: 1646 v_border: 0
(II) RADEON(0): Serial No: G501H98C086L
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 154.0 MHz   Image Size:  641 x 401 mm
(II) RADEON(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1203  v_sync_end 1209 v_blanking: 1235 v_border: 0
(II) RADEON(0): Ranges: V min: 49 V max: 86 Hz, H min: 29 H max: 113 kHz, PixClock max 280 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010ac35404c363830
(II) RADEON(0): 	2113010380412978ea8d85ad4f35b125
(II) RADEON(0): 	0e5054a54b008180a940d100d140714f
(II) RADEON(0): 	8100b3000101b06800a0a0402e603020
(II) RADEON(0): 	360081902100001e000000ff00473530
(II) RADEON(0): 	31483938433038364c0a283c80a070b0
(II) RADEON(0): 	23403020360081912100001c000000fd
(II) RADEON(0): 	0031561d711c000a202020202020004e
(II) RADEON(0): EDID vendor "DEL", prod id 16437
(II) RADEON(0): Using EDID range info for horizontal sync
(II) RADEON(0): Using EDID range info for vertical refresh
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "2560x1600"x0.0  268.00  2560 2608 2640 2720  1600 1603 1609 1646 +hsync +vsync (98.5 kHz)
(II) RADEON(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 -hsync +vsync (74.0 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) RADEON(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
(II) RADEON(0): Modeline "1920x1440"x0.0  234.00  1920 2048 2256 2600  1440 1441 1444 1500 -hsync +vsync (90.0 kHz)
(II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
(II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: 4035  Serial#: 808990284
(II) RADEON(0): Year: 2009  Week: 33
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 65  vert.: 41
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.678 redY: 0.309   greenX: 0.210 greenY: 0.692
(II) RADEON(0): blueX: 0.146 blueY: 0.055   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #1: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEON(0): #2: hsize: 1920  vsize 1200  refresh: 60  vid: 209
(II) RADEON(0): #3: hsize: 1920  vsize 1440  refresh: 60  vid: 16593
(II) RADEON(0): #4: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #5: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) RADEON(0): #6: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 268.0 MHz   Image Size:  641 x 400 mm
(II) RADEON(0): h_active: 2560  h_sync: 2608  h_sync_end 2640 h_blank_end 2720 h_border: 0
(II) RADEON(0): v_active: 1600  v_sync: 1603  v_sync_end 1609 v_blanking: 1646 v_border: 0
(II) RADEON(0): Serial No: G501H98C086L
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 154.0 MHz   Image Size:  641 x 401 mm
(II) RADEON(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1203  v_sync_end 1209 v_blanking: 1235 v_border: 0
(II) RADEON(0): Ranges: V min: 49 V max: 86 Hz, H min: 29 H max: 113 kHz, PixClock max 280 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010ac35404c363830
(II) RADEON(0): 	2113010380412978ea8d85ad4f35b125
(II) RADEON(0): 	0e5054a54b008180a940d100d140714f
(II) RADEON(0): 	8100b3000101b06800a0a0402e603020
(II) RADEON(0): 	360081902100001e000000ff00473530
(II) RADEON(0): 	31483938433038364c0a283c80a070b0
(II) RADEON(0): 	23403020360081912100001c000000fd
(II) RADEON(0): 	0031561d711c000a202020202020004e
(II) RADEON(0): EDID vendor "DEL", prod id 16437
(II) RADEON(0): Printing probed modes for output DVI-0
(II) RADEON(0): Modeline "2560x1600"x59.9  268.00  2560 2608 2640 2720  1600 1603 1609 1646 +hsync +vsync (98.5 kHz)
(II) RADEON(0): Modeline "1920x1440"x60.0  234.00  1920 2048 2256 2600  1440 1441 1444 1500 -hsync +vsync (90.0 kHz)
(II) RADEON(0): Modeline "1920x1200"x60.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 -hsync +vsync (74.0 kHz)
(II) RADEON(0): Modeline "1920x1200"x60.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
(II) RADEON(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) RADEON(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
(II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
Dac detection success
(II) RADEON(0): Output: DVI-1, Detected Monitor Type: 0
Unhandled monitor type 0
(II) RADEON(0): EDID for output DVI-1
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Manufacturer: DEL  Model: 4035  Serial#: 808990284
(II) RADEON(0): Year: 2009  Week: 33
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 65  vert.: 41
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.678 redY: 0.309   greenX: 0.210 greenY: 0.692
(II) RADEON(0): blueX: 0.146 blueY: 0.055   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #1: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEON(0): #2: hsize: 1920  vsize 1200  refresh: 60  vid: 209
(II) RADEON(0): #3: hsize: 1920  vsize 1440  refresh: 60  vid: 16593
(II) RADEON(0): #4: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #5: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) RADEON(0): #6: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 268.0 MHz   Image Size:  641 x 400 mm
(II) RADEON(0): h_active: 2560  h_sync: 2608  h_sync_end 2640 h_blank_end 2720 h_border: 0
(II) RADEON(0): v_active: 1600  v_sync: 1603  v_sync_end 1609 v_blanking: 1646 v_border: 0
(II) RADEON(0): Serial No: G501H98C086L
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 154.0 MHz   Image Size:  641 x 401 mm
(II) RADEON(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1203  v_sync_end 1209 v_blanking: 1235 v_border: 0
(II) RADEON(0): Ranges: V min: 49 V max: 86 Hz, H min: 29 H max: 113 kHz, PixClock max 280 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010ac35404c363830
(II) RADEON(0): 	2113010380412978ea8d85ad4f35b125
(II) RADEON(0): 	0e5054a54b008180a940d100d140714f
(II) RADEON(0): 	8100b3000101b06800a0a0402e603020
(II) RADEON(0): 	360081902100001e000000ff00473530
(II) RADEON(0): 	31483938433038364c0a283c80a070b0
(II) RADEON(0): 	23403020360081912100001c000000fd
(II) RADEON(0): 	0031561d711c000a202020202020004e
(II) RADEON(0): EDID vendor "DEL", prod id 16437
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "2560x1600"x0.0  268.00  2560 2608 2640 2720  1600 1603 1609 1646 +hsync +vsync (98.5 kHz)
(II) RADEON(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 -hsync +vsync (74.0 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) RADEON(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
(II) RADEON(0): Modeline "1920x1440"x0.0  234.00  1920 2048 2256 2600  1440 1441 1444 1500 -hsync +vsync (90.0 kHz)
(II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
(II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: 4035  Serial#: 808990284
(II) RADEON(0): Year: 2009  Week: 33
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 65  vert.: 41
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.678 redY: 0.309   greenX: 0.210 greenY: 0.692
(II) RADEON(0): blueX: 0.146 blueY: 0.055   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #1: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEON(0): #2: hsize: 1920  vsize 1200  refresh: 60  vid: 209
(II) RADEON(0): #3: hsize: 1920  vsize 1440  refresh: 60  vid: 16593
(II) RADEON(0): #4: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #5: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) RADEON(0): #6: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 268.0 MHz   Image Size:  641 x 400 mm
(II) RADEON(0): h_active: 2560  h_sync: 2608  h_sync_end 2640 h_blank_end 2720 h_border: 0
(II) RADEON(0): v_active: 1600  v_sync: 1603  v_sync_end 1609 v_blanking: 1646 v_border: 0
(II) RADEON(0): Serial No: G501H98C086L
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 154.0 MHz   Image Size:  641 x 401 mm
(II) RADEON(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1203  v_sync_end 1209 v_blanking: 1235 v_border: 0
(II) RADEON(0): Ranges: V min: 49 V max: 86 Hz, H min: 29 H max: 113 kHz, PixClock max 280 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010ac35404c363830
(II) RADEON(0): 	2113010380412978ea8d85ad4f35b125
(II) RADEON(0): 	0e5054a54b008180a940d100d140714f
(II) RADEON(0): 	8100b3000101b06800a0a0402e603020
(II) RADEON(0): 	360081902100001e000000ff00473530
(II) RADEON(0): 	31483938433038364c0a283c80a070b0
(II) RADEON(0): 	23403020360081912100001c000000fd
(II) RADEON(0): 	0031561d711c000a202020202020004e
(II) RADEON(0): EDID vendor "DEL", prod id 16437
(II) RADEON(0): Printing probed modes for output DVI-0
(II) RADEON(0): Modeline "2560x1600"x59.9  268.00  2560 2608 2640 2720  1600 1603 1609 1646 +hsync +vsync (98.5 kHz)
(II) RADEON(0): Modeline "1920x1440"x60.0  234.00  1920 2048 2256 2600  1440 1441 1444 1500 -hsync +vsync (90.0 kHz)
(II) RADEON(0): Modeline "1920x1200"x60.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 -hsync +vsync (74.0 kHz)
(II) RADEON(0): Modeline "1920x1200"x60.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
(II) RADEON(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) RADEON(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
(II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
Dac detection success
(II) RADEON(0): Output: DVI-1, Detected Monitor Type: 0
Unhandled monitor type 0
(II) RADEON(0): EDID for output DVI-1
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Manufacturer: DEL  Model: 4035  Serial#: 808990284
(II) RADEON(0): Year: 2009  Week: 33
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 65  vert.: 41
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.678 redY: 0.309   greenX: 0.210 greenY: 0.692
(II) RADEON(0): blueX: 0.146 blueY: 0.055   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #1: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEON(0): #2: hsize: 1920  vsize 1200  refresh: 60  vid: 209
(II) RADEON(0): #3: hsize: 1920  vsize 1440  refresh: 60  vid: 16593
(II) RADEON(0): #4: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #5: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) RADEON(0): #6: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 268.0 MHz   Image Size:  641 x 400 mm
(II) RADEON(0): h_active: 2560  h_sync: 2608  h_sync_end 2640 h_blank_end 2720 h_border: 0
(II) RADEON(0): v_active: 1600  v_sync: 1603  v_sync_end 1609 v_blanking: 1646 v_border: 0
(II) RADEON(0): Serial No: G501H98C086L
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 154.0 MHz   Image Size:  641 x 401 mm
(II) RADEON(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1203  v_sync_end 1209 v_blanking: 1235 v_border: 0
(II) RADEON(0): Ranges: V min: 49 V max: 86 Hz, H min: 29 H max: 113 kHz, PixClock max 280 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010ac35404c363830
(II) RADEON(0): 	2113010380412978ea8d85ad4f35b125
(II) RADEON(0): 	0e5054a54b008180a940d100d140714f
(II) RADEON(0): 	8100b3000101b06800a0a0402e603020
(II) RADEON(0): 	360081902100001e000000ff00473530
(II) RADEON(0): 	31483938433038364c0a283c80a070b0
(II) RADEON(0): 	23403020360081912100001c000000fd
(II) RADEON(0): 	0031561d711c000a202020202020004e
(II) RADEON(0): EDID vendor "DEL", prod id 16437
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "2560x1600"x0.0  268.00  2560 2608 2640 2720  1600 1603 1609 1646 +hsync +vsync (98.5 kHz)
(II) RADEON(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 -hsync +vsync (74.0 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) RADEON(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
(II) RADEON(0): Modeline "1920x1440"x0.0  234.00  1920 2048 2256 2600  1440 1441 1444 1500 -hsync +vsync (90.0 kHz)
(II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
(II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: 4035  Serial#: 808990284
(II) RADEON(0): Year: 2009  Week: 33
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 65  vert.: 41
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.678 redY: 0.309   greenX: 0.210 greenY: 0.692
(II) RADEON(0): blueX: 0.146 blueY: 0.055   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #1: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEON(0): #2: hsize: 1920  vsize 1200  refresh: 60  vid: 209
(II) RADEON(0): #3: hsize: 1920  vsize 1440  refresh: 60  vid: 16593
(II) RADEON(0): #4: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #5: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) RADEON(0): #6: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 268.0 MHz   Image Size:  641 x 400 mm
(II) RADEON(0): h_active: 2560  h_sync: 2608  h_sync_end 2640 h_blank_end 2720 h_border: 0
(II) RADEON(0): v_active: 1600  v_sync: 1603  v_sync_end 1609 v_blanking: 1646 v_border: 0
(II) RADEON(0): Serial No: G501H98C086L
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 154.0 MHz   Image Size:  641 x 401 mm
(II) RADEON(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1203  v_sync_end 1209 v_blanking: 1235 v_border: 0
(II) RADEON(0): Ranges: V min: 49 V max: 86 Hz, H min: 29 H max: 113 kHz, PixClock max 280 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010ac35404c363830
(II) RADEON(0): 	2113010380412978ea8d85ad4f35b125
(II) RADEON(0): 	0e5054a54b008180a940d100d140714f
(II) RADEON(0): 	8100b3000101b06800a0a0402e603020
(II) RADEON(0): 	360081902100001e000000ff00473530
(II) RADEON(0): 	31483938433038364c0a283c80a070b0
(II) RADEON(0): 	23403020360081912100001c000000fd
(II) RADEON(0): 	0031561d711c000a202020202020004e
(II) RADEON(0): EDID vendor "DEL", prod id 16437
(II) RADEON(0): Printing probed modes for output DVI-0
(II) RADEON(0): Modeline "2560x1600"x59.9  268.00  2560 2608 2640 2720  1600 1603 1609 1646 +hsync +vsync (98.5 kHz)
(II) RADEON(0): Modeline "1920x1440"x60.0  234.00  1920 2048 2256 2600  1440 1441 1444 1500 -hsync +vsync (90.0 kHz)
(II) RADEON(0): Modeline "1920x1200"x60.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 -hsync +vsync (74.0 kHz)
(II) RADEON(0): Modeline "1920x1200"x60.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
(II) RADEON(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) RADEON(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
(II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
Dac detection success
(II) RADEON(0): Output: DVI-1, Detected Monitor Type: 0
Unhandled monitor type 0
(II) RADEON(0): EDID for output DVI-1
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Manufacturer: DEL  Model: 4035  Serial#: 808990284
(II) RADEON(0): Year: 2009  Week: 33
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 65  vert.: 41
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.678 redY: 0.309   greenX: 0.210 greenY: 0.692
(II) RADEON(0): blueX: 0.146 blueY: 0.055   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #1: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEON(0): #2: hsize: 1920  vsize 1200  refresh: 60  vid: 209
(II) RADEON(0): #3: hsize: 1920  vsize 1440  refresh: 60  vid: 16593
(II) RADEON(0): #4: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #5: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) RADEON(0): #6: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 268.0 MHz   Image Size:  641 x 400 mm
(II) RADEON(0): h_active: 2560  h_sync: 2608  h_sync_end 2640 h_blank_end 2720 h_border: 0
(II) RADEON(0): v_active: 1600  v_sync: 1603  v_sync_end 1609 v_blanking: 1646 v_border: 0
(II) RADEON(0): Serial No: G501H98C086L
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 154.0 MHz   Image Size:  641 x 401 mm
(II) RADEON(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1203  v_sync_end 1209 v_blanking: 1235 v_border: 0
(II) RADEON(0): Ranges: V min: 49 V max: 86 Hz, H min: 29 H max: 113 kHz, PixClock max 280 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010ac35404c363830
(II) RADEON(0): 	2113010380412978ea8d85ad4f35b125
(II) RADEON(0): 	0e5054a54b008180a940d100d140714f
(II) RADEON(0): 	8100b3000101b06800a0a0402e603020
(II) RADEON(0): 	360081902100001e000000ff00473530
(II) RADEON(0): 	31483938433038364c0a283c80a070b0
(II) RADEON(0): 	23403020360081912100001c000000fd
(II) RADEON(0): 	0031561d711c000a202020202020004e
(II) RADEON(0): EDID vendor "DEL", prod id 16437
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "2560x1600"x0.0  268.00  2560 2608 2640 2720  1600 1603 1609 1646 +hsync +vsync (98.5 kHz)
(II) RADEON(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 -hsync +vsync (74.0 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) RADEON(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
(II) RADEON(0): Modeline "1920x1440"x0.0  234.00  1920 2048 2256 2600  1440 1441 1444 1500 -hsync +vsync (90.0 kHz)
(II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
(II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: 4035  Serial#: 808990284
(II) RADEON(0): Year: 2009  Week: 33
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 65  vert.: 41
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.678 redY: 0.309   greenX: 0.210 greenY: 0.692
(II) RADEON(0): blueX: 0.146 blueY: 0.055   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #1: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEON(0): #2: hsize: 1920  vsize 1200  refresh: 60  vid: 209
(II) RADEON(0): #3: hsize: 1920  vsize 1440  refresh: 60  vid: 16593
(II) RADEON(0): #4: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #5: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) RADEON(0): #6: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 268.0 MHz   Image Size:  641 x 400 mm
(II) RADEON(0): h_active: 2560  h_sync: 2608  h_sync_end 2640 h_blank_end 2720 h_border: 0
(II) RADEON(0): v_active: 1600  v_sync: 1603  v_sync_end 1609 v_blanking: 1646 v_border: 0
(II) RADEON(0): Serial No: G501H98C086L
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 154.0 MHz   Image Size:  641 x 401 mm
(II) RADEON(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1203  v_sync_end 1209 v_blanking: 1235 v_border: 0
(II) RADEON(0): Ranges: V min: 49 V max: 86 Hz, H min: 29 H max: 113 kHz, PixClock max 280 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010ac35404c363830
(II) RADEON(0): 	2113010380412978ea8d85ad4f35b125
(II) RADEON(0): 	0e5054a54b008180a940d100d140714f
(II) RADEON(0): 	8100b3000101b06800a0a0402e603020
(II) RADEON(0): 	360081902100001e000000ff00473530
(II) RADEON(0): 	31483938433038364c0a283c80a070b0
(II) RADEON(0): 	23403020360081912100001c000000fd
(II) RADEON(0): 	0031561d711c000a202020202020004e
(II) RADEON(0): EDID vendor "DEL", prod id 16437
(II) RADEON(0): Printing probed modes for output DVI-0
(II) RADEON(0): Modeline "2560x1600"x59.9  268.00  2560 2608 2640 2720  1600 1603 1609 1646 +hsync +vsync (98.5 kHz)
(II) RADEON(0): Modeline "1920x1440"x60.0  234.00  1920 2048 2256 2600  1440 1441 1444 1500 -hsync +vsync (90.0 kHz)
(II) RADEON(0): Modeline "1920x1200"x60.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 -hsync +vsync (74.0 kHz)
(II) RADEON(0): Modeline "1920x1200"x60.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
(II) RADEON(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) RADEON(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
(II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
Dac detection success
(II) RADEON(0): Output: DVI-1, Detected Monitor Type: 0
Unhandled monitor type 0
(II) RADEON(0): EDID for output DVI-1
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Manufacturer: DEL  Model: 4035  Serial#: 808990284
(II) RADEON(0): Year: 2009  Week: 33
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 65  vert.: 41
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.678 redY: 0.309   greenX: 0.210 greenY: 0.692
(II) RADEON(0): blueX: 0.146 blueY: 0.055   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #1: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEON(0): #2: hsize: 1920  vsize 1200  refresh: 60  vid: 209
(II) RADEON(0): #3: hsize: 1920  vsize 1440  refresh: 60  vid: 16593
(II) RADEON(0): #4: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #5: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) RADEON(0): #6: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 268.0 MHz   Image Size:  641 x 400 mm
(II) RADEON(0): h_active: 2560  h_sync: 2608  h_sync_end 2640 h_blank_end 2720 h_border: 0
(II) RADEON(0): v_active: 1600  v_sync: 1603  v_sync_end 1609 v_blanking: 1646 v_border: 0
(II) RADEON(0): Serial No: G501H98C086L
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 154.0 MHz   Image Size:  641 x 401 mm
(II) RADEON(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1203  v_sync_end 1209 v_blanking: 1235 v_border: 0
(II) RADEON(0): Ranges: V min: 49 V max: 86 Hz, H min: 29 H max: 113 kHz, PixClock max 280 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010ac35404c363830
(II) RADEON(0): 	2113010380412978ea8d85ad4f35b125
(II) RADEON(0): 	0e5054a54b008180a940d100d140714f
(II) RADEON(0): 	8100b3000101b06800a0a0402e603020
(II) RADEON(0): 	360081902100001e000000ff00473530
(II) RADEON(0): 	31483938433038364c0a283c80a070b0
(II) RADEON(0): 	23403020360081912100001c000000fd
(II) RADEON(0): 	0031561d711c000a202020202020004e
(II) RADEON(0): EDID vendor "DEL", prod id 16437
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "2560x1600"x0.0  268.00  2560 2608 2640 2720  1600 1603 1609 1646 +hsync +vsync (98.5 kHz)
(II) RADEON(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 -hsync +vsync (74.0 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) RADEON(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
(II) RADEON(0): Modeline "1920x1440"x0.0  234.00  1920 2048 2256 2600  1440 1441 1444 1500 -hsync +vsync (90.0 kHz)
(II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
(II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: 4035  Serial#: 808990284
(II) RADEON(0): Year: 2009  Week: 33
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 65  vert.: 41
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.678 redY: 0.309   greenX: 0.210 greenY: 0.692
(II) RADEON(0): blueX: 0.146 blueY: 0.055   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #1: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEON(0): #2: hsize: 1920  vsize 1200  refresh: 60  vid: 209
(II) RADEON(0): #3: hsize: 1920  vsize 1440  refresh: 60  vid: 16593
(II) RADEON(0): #4: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #5: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) RADEON(0): #6: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 268.0 MHz   Image Size:  641 x 400 mm
(II) RADEON(0): h_active: 2560  h_sync: 2608  h_sync_end 2640 h_blank_end 2720 h_border: 0
(II) RADEON(0): v_active: 1600  v_sync: 1603  v_sync_end 1609 v_blanking: 1646 v_border: 0
(II) RADEON(0): Serial No: G501H98C086L
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 154.0 MHz   Image Size:  641 x 401 mm
(II) RADEON(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1203  v_sync_end 1209 v_blanking: 1235 v_border: 0
(II) RADEON(0): Ranges: V min: 49 V max: 86 Hz, H min: 29 H max: 113 kHz, PixClock max 280 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010ac35404c363830
(II) RADEON(0): 	2113010380412978ea8d85ad4f35b125
(II) RADEON(0): 	0e5054a54b008180a940d100d140714f
(II) RADEON(0): 	8100b3000101b06800a0a0402e603020
(II) RADEON(0): 	360081902100001e000000ff00473530
(II) RADEON(0): 	31483938433038364c0a283c80a070b0
(II) RADEON(0): 	23403020360081912100001c000000fd
(II) RADEON(0): 	0031561d711c000a202020202020004e
(II) RADEON(0): EDID vendor "DEL", prod id 16437
(II) RADEON(0): Printing probed modes for output DVI-0
(II) RADEON(0): Modeline "2560x1600"x59.9  268.00  2560 2608 2640 2720  1600 1603 1609 1646 +hsync +vsync (98.5 kHz)
(II) RADEON(0): Modeline "1920x1440"x60.0  234.00  1920 2048 2256 2600  1440 1441 1444 1500 -hsync +vsync (90.0 kHz)
(II) RADEON(0): Modeline "1920x1200"x60.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 -hsync +vsync (74.0 kHz)
(II) RADEON(0): Modeline "1920x1200"x60.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
(II) RADEON(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) RADEON(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
(II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
Dac detection success
(II) RADEON(0): Output: DVI-1, Detected Monitor Type: 0
Unhandled monitor type 0
(II) RADEON(0): EDID for output DVI-1
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Manufacturer: DEL  Model: 4035  Serial#: 808990284
(II) RADEON(0): Year: 2009  Week: 33
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 65  vert.: 41
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.678 redY: 0.309   greenX: 0.210 greenY: 0.692
(II) RADEON(0): blueX: 0.146 blueY: 0.055   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #1: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEON(0): #2: hsize: 1920  vsize 1200  refresh: 60  vid: 209
(II) RADEON(0): #3: hsize: 1920  vsize 1440  refresh: 60  vid: 16593
(II) RADEON(0): #4: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #5: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) RADEON(0): #6: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 268.0 MHz   Image Size:  641 x 400 mm
(II) RADEON(0): h_active: 2560  h_sync: 2608  h_sync_end 2640 h_blank_end 2720 h_border: 0
(II) RADEON(0): v_active: 1600  v_sync: 1603  v_sync_end 1609 v_blanking: 1646 v_border: 0
(II) RADEON(0): Serial No: G501H98C086L
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 154.0 MHz   Image Size:  641 x 401 mm
(II) RADEON(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1203  v_sync_end 1209 v_blanking: 1235 v_border: 0
(II) RADEON(0): Ranges: V min: 49 V max: 86 Hz, H min: 29 H max: 113 kHz, PixClock max 280 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010ac35404c363830
(II) RADEON(0): 	2113010380412978ea8d85ad4f35b125
(II) RADEON(0): 	0e5054a54b008180a940d100d140714f
(II) RADEON(0): 	8100b3000101b06800a0a0402e603020
(II) RADEON(0): 	360081902100001e000000ff00473530
(II) RADEON(0): 	31483938433038364c0a283c80a070b0
(II) RADEON(0): 	23403020360081912100001c000000fd
(II) RADEON(0): 	0031561d711c000a202020202020004e
(II) RADEON(0): EDID vendor "DEL", prod id 16437
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "2560x1600"x0.0  268.00  2560 2608 2640 2720  1600 1603 1609 1646 +hsync +vsync (98.5 kHz)
(II) RADEON(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 -hsync +vsync (74.0 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) RADEON(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
(II) RADEON(0): Modeline "1920x1440"x0.0  234.00  1920 2048 2256 2600  1440 1441 1444 1500 -hsync +vsync (90.0 kHz)
(II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
(II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: 4035  Serial#: 808990284
(II) RADEON(0): Year: 2009  Week: 33
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 65  vert.: 41
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.678 redY: 0.309   greenX: 0.210 greenY: 0.692
(II) RADEON(0): blueX: 0.146 blueY: 0.055   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #1: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEON(0): #2: hsize: 1920  vsize 1200  refresh: 60  vid: 209
(II) RADEON(0): #3: hsize: 1920  vsize 1440  refresh: 60  vid: 16593
(II) RADEON(0): #4: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #5: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) RADEON(0): #6: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 268.0 MHz   Image Size:  641 x 400 mm
(II) RADEON(0): h_active: 2560  h_sync: 2608  h_sync_end 2640 h_blank_end 2720 h_border: 0
(II) RADEON(0): v_active: 1600  v_sync: 1603  v_sync_end 1609 v_blanking: 1646 v_border: 0
(II) RADEON(0): Serial No: G501H98C086L
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 154.0 MHz   Image Size:  641 x 401 mm
(II) RADEON(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1203  v_sync_end 1209 v_blanking: 1235 v_border: 0
(II) RADEON(0): Ranges: V min: 49 V max: 86 Hz, H min: 29 H max: 113 kHz, PixClock max 280 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010ac35404c363830
(II) RADEON(0): 	2113010380412978ea8d85ad4f35b125
(II) RADEON(0): 	0e5054a54b008180a940d100d140714f
(II) RADEON(0): 	8100b3000101b06800a0a0402e603020
(II) RADEON(0): 	360081902100001e000000ff00473530
(II) RADEON(0): 	31483938433038364c0a283c80a070b0
(II) RADEON(0): 	23403020360081912100001c000000fd
(II) RADEON(0): 	0031561d711c000a202020202020004e
(II) RADEON(0): EDID vendor "DEL", prod id 16437
(II) RADEON(0): Printing probed modes for output DVI-0
(II) RADEON(0): Modeline "2560x1600"x59.9  268.00  2560 2608 2640 2720  1600 1603 1609 1646 +hsync +vsync (98.5 kHz)
(II) RADEON(0): Modeline "1920x1440"x60.0  234.00  1920 2048 2256 2600  1440 1441 1444 1500 -hsync +vsync (90.0 kHz)
(II) RADEON(0): Modeline "1920x1200"x60.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 -hsync +vsync (74.0 kHz)
(II) RADEON(0): Modeline "1920x1200"x60.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
(II) RADEON(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) RADEON(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
(II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
Dac detection success
(II) RADEON(0): Output: DVI-1, Detected Monitor Type: 0
Unhandled monitor type 0
(II) RADEON(0): EDID for output DVI-1
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Manufacturer: DEL  Model: 4035  Serial#: 808990284
(II) RADEON(0): Year: 2009  Week: 33
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 65  vert.: 41
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.678 redY: 0.309   greenX: 0.210 greenY: 0.692
(II) RADEON(0): blueX: 0.146 blueY: 0.055   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #1: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEON(0): #2: hsize: 1920  vsize 1200  refresh: 60  vid: 209
(II) RADEON(0): #3: hsize: 1920  vsize 1440  refresh: 60  vid: 16593
(II) RADEON(0): #4: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #5: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) RADEON(0): #6: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 268.0 MHz   Image Size:  641 x 400 mm
(II) RADEON(0): h_active: 2560  h_sync: 2608  h_sync_end 2640 h_blank_end 2720 h_border: 0
(II) RADEON(0): v_active: 1600  v_sync: 1603  v_sync_end 1609 v_blanking: 1646 v_border: 0
(II) RADEON(0): Serial No: G501H98C086L
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 154.0 MHz   Image Size:  641 x 401 mm
(II) RADEON(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1203  v_sync_end 1209 v_blanking: 1235 v_border: 0
(II) RADEON(0): Ranges: V min: 49 V max: 86 Hz, H min: 29 H max: 113 kHz, PixClock max 280 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010ac35404c363830
(II) RADEON(0): 	2113010380412978ea8d85ad4f35b125
(II) RADEON(0): 	0e5054a54b008180a940d100d140714f
(II) RADEON(0): 	8100b3000101b06800a0a0402e603020
(II) RADEON(0): 	360081902100001e000000ff00473530
(II) RADEON(0): 	31483938433038364c0a283c80a070b0
(II) RADEON(0): 	23403020360081912100001c000000fd
(II) RADEON(0): 	0031561d711c000a202020202020004e
(II) RADEON(0): EDID vendor "DEL", prod id 16437
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "2560x1600"x0.0  268.00  2560 2608 2640 2720  1600 1603 1609 1646 +hsync +vsync (98.5 kHz)
(II) RADEON(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 -hsync +vsync (74.0 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) RADEON(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
(II) RADEON(0): Modeline "1920x1440"x0.0  234.00  1920 2048 2256 2600  1440 1441 1444 1500 -hsync +vsync (90.0 kHz)
(II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
(II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: 4035  Serial#: 808990284
(II) RADEON(0): Year: 2009  Week: 33
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 65  vert.: 41
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.678 redY: 0.309   greenX: 0.210 greenY: 0.692
(II) RADEON(0): blueX: 0.146 blueY: 0.055   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #1: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEON(0): #2: hsize: 1920  vsize 1200  refresh: 60  vid: 209
(II) RADEON(0): #3: hsize: 1920  vsize 1440  refresh: 60  vid: 16593
(II) RADEON(0): #4: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #5: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) RADEON(0): #6: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 268.0 MHz   Image Size:  641 x 400 mm
(II) RADEON(0): h_active: 2560  h_sync: 2608  h_sync_end 2640 h_blank_end 2720 h_border: 0
(II) RADEON(0): v_active: 1600  v_sync: 1603  v_sync_end 1609 v_blanking: 1646 v_border: 0
(II) RADEON(0): Serial No: G501H98C086L
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 154.0 MHz   Image Size:  641 x 401 mm
(II) RADEON(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1203  v_sync_end 1209 v_blanking: 1235 v_border: 0
(II) RADEON(0): Ranges: V min: 49 V max: 86 Hz, H min: 29 H max: 113 kHz, PixClock max 280 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010ac35404c363830
(II) RADEON(0): 	2113010380412978ea8d85ad4f35b125
(II) RADEON(0): 	0e5054a54b008180a940d100d140714f
(II) RADEON(0): 	8100b3000101b06800a0a0402e603020
(II) RADEON(0): 	360081902100001e000000ff00473530
(II) RADEON(0): 	31483938433038364c0a283c80a070b0
(II) RADEON(0): 	23403020360081912100001c000000fd
(II) RADEON(0): 	0031561d711c000a202020202020004e
(II) RADEON(0): EDID vendor "DEL", prod id 16437
(II) RADEON(0): Printing probed modes for output DVI-0
(II) RADEON(0): Modeline "2560x1600"x59.9  268.00  2560 2608 2640 2720  1600 1603 1609 1646 +hsync +vsync (98.5 kHz)
(II) RADEON(0): Modeline "1920x1440"x60.0  234.00  1920 2048 2256 2600  1440 1441 1444 1500 -hsync +vsync (90.0 kHz)
(II) RADEON(0): Modeline "1920x1200"x60.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 -hsync +vsync (74.0 kHz)
(II) RADEON(0): Modeline "1920x1200"x60.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
(II) RADEON(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) RADEON(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
(II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): DIG0 transmitter: Coherent Mode enabled
Output DIG0 transmitter setup success
Blank CRTC 0 success
Disable CRTC memreq 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC memreq 1 success
Disable CRTC 1 success
(II) RADEON(0): DIG0 transmitter: Coherent Mode enabled
Output DIG0 transmitter setup success
Blank CRTC 0 success
Disable CRTC memreq 0 success
Disable CRTC 0 success
Enable CRTC 0 success
Enable CRTC memreq 0 success
Unblank CRTC 0 success
(II) RADEON(0): DIG0 transmitter: Coherent Mode enabled
Output DIG0 transmitter setup success
```

---

### Post by krikke on 2010-01-01
Bump

---

