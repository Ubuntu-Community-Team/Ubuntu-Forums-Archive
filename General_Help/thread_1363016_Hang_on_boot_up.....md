---
title: "Hang on boot up...."
date: 2009-12-23
forum: General Help
---

### Post by Lambchopper on 2009-12-23
I'm hoping someone one can help me with an odd problem I'm having....

I'm running Ubuntu 9.10 on a Dell Inspiron 1505 and it was running great.  After some updates, I found that now Ubuntu will every so often hang on a Text based login even though my run level is to login via graphical interface.

If I login via the text based login (which it will let me) software like Firefox won't run right and eventually it kicks me to a graphical login.  If I leave the text based login up, it'll take about 5 minutes and then the Graphical interface will start.

One problem, it doesn't happen on every boot.  It's intermittent  and I can't seem to figure out what causes it to happen...

I suspect this is a Gnome problem, but I'm not sure where to begin to troubleshoot.  

Could someone please help?  Below is a copy of my most recent Xorg.log file.  The issue happened during the boot the generated this log.

Thanks in advance!

> 
X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux dave-laptop 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-16-generic root=UUID=7a7bb886-890a-4b6f-b566-ba6da09aeae7 ro quiet splash
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Dec 23 20:53:22 2009
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0:1:5:0) 1002:5975:1028:01f5 ATI Technologies Inc RS482 [Radeon Xpress 200M] rev 0, Mem @ 0xc8000000/134217728, 0xc0100000/65536, I/O @ 0x00009000/256, BIOS @ 0x????????/131072
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
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[24] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[25] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[26] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[27] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[28] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[29] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
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
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 6.12.99
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 6.12.99
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
(II) Primary Device is: PCI 01@00:05:0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[24] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[25] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[26] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[27] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[28] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[29] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) [KMS] drm report modesetting isn't supported.
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux//libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 0.0.2
	ABI class: X.Org Video Driver, version 5.0
(EE) open /dev/fb0: No such file or directory
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[21] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[22] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[25] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[26] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[27] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[28] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[29] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[30] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[31] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[32] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[33] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[34] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) RADEON(0): Built from git commit 7968e1fb89f6b59d1654df48249bf4b81990c008
(II) RADEON(0): TOTO SAYS 00000000c0100000
(II) RADEON(0): MMIO registers at 0x00000000c0100000: size 64KB
(II) RADEON(0): PCI bus 1 card 5 func 0
(II) RADEON(0): Creating default Display subsection in Screen section
	"Builtin Default ati Screen 0" for depth/fbbpp 24/32
(==) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 0.1.0
	ABI class: X.Org Video Driver, version 5.0
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(--) RADEON(0): Chipset: "ATI Radeon XPRESS 200M 5975 (PCIE)" (ChipID = 0x5975)
(--) RADEON(0): Linear framebuffer at 0x00000000c8000000
(II) RADEON(0): PCI card detected
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(II) RADEON(0): Legacy BIOS detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:05.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
(II) RADEON(0): [dri] Found DRI library version 1.3.0 and kernel module version 1.31.0
(II) RADEON(0): Direct rendering experimental on RS400/Xpress 200 enabled
(==) RADEON(0): Page Flipping disabled
(II) RADEON(0): Will try to use DMA for Xv image transfers
(II) RADEON(0): Detected total video RAM=131072K, accessible=131072K (PCI BAR=131072K)
(--) RADEON(0): Mapped VideoRAM: 131072 kByte (128 bit DDR SDRAM)
(II) RADEON(0): Color tiling enabled by default
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) RADEON(0): ref_freq: 1432, min_out_pll: 20000, max_out_pll: 40000, min_in_pll: 100, max_in_pll: 1350, xclk: 20000, sclk: 400.000000, mclk: 200.000000
(II) RADEON(0): PLL parameters: rf=1432 rd=6 min=20000 max=40000; xclk=20000
(II) RADEON(0): Panel ID string: AUO                     
(II) RADEON(0): Panel Size from BIOS: 1280x800
(II) RADEON(0): BIOS provided dividers will be used.
(WW) RADEON(0): LVDS Info:
XRes: 1280, YRes: 800, DotClock: 71110
HBlank: 160, HOverPlus: 16, HSyncWidth: 32
VBlank: 23, VOverPlus: 4, VSyncWidth: 4
(WW) RADEON(0): LCD DDC Info Table found!
(II) RADEON(0): Output VGA-0 has no monitor section
(II) RADEON(0): I2C bus "VGA-0" initialized.
(II) RADEON(0): Output LVDS has no monitor section
(II) RADEON(0): I2C bus "LVDS" initialized.
(II) RADEON(0): Port0:
  XRANDR name: VGA-0
  Connector: VGA
  CRT1: INTERNAL_DAC2
  DDC reg: 0x68
(II) RADEON(0): Port1:
  XRANDR name: LVDS
  Connector: LVDS
  LCD1: INTERNAL_LVDS
  DDC reg: 0x1a0
(II) RADEON(0): I2C device "VGA-0:E-EDID segment register" registered at address 0x60.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
finished output detect: 0
(II) RADEON(0): I2C device "LVDS:E-EDID segment register" registered at address 0x60.
(II) RADEON(0): I2C device "LVDS:ddc2" registered at address 0xA0.
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: AUO  Model: 1c74  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 1
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.600 redY: 0.350   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.115   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 71.1 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1301  h_sync_end 1333 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 804  v_sync_end 808 v_blanking: 823 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 59.3 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1301  h_sync_end 1333 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 804  v_sync_end 808 v_blanking: 823 v_border: 0
(II) RADEON(0):  FF059
(II) RADEON(0):  0AMWx€Ìø
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006af741c00000000
(II) RADEON(0): 	010f0103802115780aa7e599594f8c27
(II) RADEON(0): 	1d505400000001010101010101010101
(II) RADEON(0): 	010101010101c71b00a0502017301520
(II) RADEON(0): 	44004bcf10000018261700a050201730
(II) RADEON(0): 	152044004bcf10000000000000fe0046
(II) RADEON(0): 	463035390042313534455731000000fe
(II) RADEON(0): 	0030414d5778a4ccf801010a202000e9
finished output detect: 1
finished all detect
before xf86InitialConfiguration
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): EDID for output LVDS
(II) RADEON(0): Manufacturer: AUO  Model: 1c74  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 1
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.600 redY: 0.350   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.115   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 71.1 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1301  h_sync_end 1333 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 804  v_sync_end 808 v_blanking: 823 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 59.3 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1301  h_sync_end 1333 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 804  v_sync_end 808 v_blanking: 823 v_border: 0
(II) RADEON(0):  FF059
(II) RADEON(0):  0AMWx€Ìø
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006af741c00000000
(II) RADEON(0): 	010f0103802115780aa7e599594f8c27
(II) RADEON(0): 	1d505400000001010101010101010101
(II) RADEON(0): 	010101010101c71b00a0502017301520
(II) RADEON(0): 	44004bcf10000018261700a050201730
(II) RADEON(0): 	152044004bcf10000000000000fe0046
(II) RADEON(0): 	463035390042313534455731000000fe
(II) RADEON(0): 	0030414d5778a4ccf801010a202000e9
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: AUO  Model: 1c74  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 1
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.600 redY: 0.350   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.115   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 71.1 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1301  h_sync_end 1333 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 804  v_sync_end 808 v_blanking: 823 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 59.3 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1301  h_sync_end 1333 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 804  v_sync_end 808 v_blanking: 823 v_border: 0
(II) RADEON(0):  FF059
(II) RADEON(0):  0AMWx€Ìø
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006af741c00000000
(II) RADEON(0): 	010f0103802115780aa7e599594f8c27
(II) RADEON(0): 	1d505400000001010101010101010101
(II) RADEON(0): 	010101010101c71b00a0502017301520
(II) RADEON(0): 	44004bcf10000018261700a050201730
(II) RADEON(0): 	152044004bcf10000000000000fe0046
(II) RADEON(0): 	463035390042313534455731000000fe
(II) RADEON(0): 	0030414d5778a4ccf801010a202000e9
(II) RADEON(0): EDID vendor "AUO", prod id 7284
(II) RADEON(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
(II) RADEON(0): Printing probed modes for output LVDS
(II) RADEON(0): Modeline "1280x800"x60.0   71.11  1280 1301 1333 1440  800 804 808 823 -hsync -vsync (49.4 kHz)
(II) RADEON(0): Modeline "1280x800"x50.0   59.26  1280 1301 1333 1440  800 804 808 823 -hsync -vsync (41.2 kHz)
(II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
(II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
(II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
(II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
(II) RADEON(0): Output VGA-0 disconnected
(II) RADEON(0): Output LVDS connected
(II) RADEON(0): Using exact sizes for initial modes
(II) RADEON(0): Output LVDS using initial mode 1280x800
(==) RADEON(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(==) RADEON(0): Using EXA acceleration architecture
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 2.4.0
	ABI class: X.Org Video Driver, version 5.0
(==) RADEON(0): Assuming overlay scaler buffer width is 1536
(II) RADEON(0): No MM_TABLE found - assuming CARD is not TV-in capable.
(!!) RADEON(0): For information on using the multimedia capabilities
	of this adapter, please see [http://gatos.sf.net](http://gatos.sf.net).
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
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[21] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[22] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[25] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[26] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[27] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[28] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[29] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[30] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[31] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[32] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[33] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[34] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) RADEON(0): RADEONScreenInit c8000000 0 0
Entering TV Save
Save TV timing tables
saveTimingTables: reading timing tables
TV Save done
disable LVDS
(II) RADEON(0): Dynamic Power Management Disabled
(==) RADEON(0): Using 24 bit depth buffer
(II) RADEON(0): RADEONInitMemoryMap() : 
(II) RADEON(0):   mem_size         : 0x08000000
(II) RADEON(0):   MC_FB_LOCATION   : 0x3fff3800
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(II) RADEON(0): Depth moves disabled by default
(II) RADEON(0): Allocating from a screen of 131072 kb
(II) RADEON(0): Will use 32 kb for hardware cursor 0 at offset 0x00640000
(II) RADEON(0): Will use 32 kb for hardware cursor 1 at offset 0x00644000
(II) RADEON(0): Will use 6400 kb for front buffer at offset 0x00000000
(II) RADEON(0): Will use 6400 kb for back buffer at offset 0x00648000
(II) RADEON(0): Will use 6400 kb for depth buffer at offset 0x00c88000
(II) RADEON(0): Will use 55808 kb for textures at offset 0x012c8000
(II) RADEON(0): Will use 56032 kb for X Server offscreen at offset 0x04948000
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:05.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) RADEON(0): [drm] Using the DRM lock SAREA also for drawables.
(II) RADEON(0): [drm] framebuffer handle = 0xc8000000
(II) RADEON(0): [drm] added 1 reserved context for kernel
(II) RADEON(0): X context handle = 0x1
(II) RADEON(0): [drm] installed DRM signal handler
(II) RADEON(0): [pci] 32768 kB allocated with handle 0xf884b000
(II) RADEON(0): [pci] ring handle = 0xf884b000
(II) RADEON(0): [pci] Ring mapped at 0xb769b000
(II) RADEON(0): [pci] Ring contents 0x00000000
(II) RADEON(0): [pci] ring read ptr handle = 0xf894c000
(II) RADEON(0): [pci] Ring read ptr mapped at 0xb769a000
(II) RADEON(0): [pci] Ring read ptr contents 0x00000000
(II) RADEON(0): [pci] vertex/indirect buffers handle = 0xf894d000
(II) RADEON(0): [pci] Vertex/indirect buffers mapped at 0xaf42c000
(II) RADEON(0): [pci] Vertex/indirect buffers contents 0x00000000
(II) RADEON(0): [pci] GART texture map handle = 0xf8b4d000
(II) RADEON(0): [pci] GART Texture map mapped at 0xad7ac000
(II) RADEON(0): [drm] register handle = 0x28020000
(II) RADEON(0): [dri] Visual configs initialized
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x3fff3800 0x3fff3800
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(==) RADEON(0): Backing store disabled
(II) RADEON(0): [DRI] installation complete
(II) RADEON(0): [drm] Added 32 65536 byte vertex/indirect buffers
(II) RADEON(0): [drm] Mapped 32 vertex/indirect buffers
(II) RADEON(0): [drm] dma control initialized, using IRQ 17
(II) RADEON(0): [drm] Initialized kernel GART heap manager, 29884416
(WW) RADEON(0): DRI init changed memory map, adjusting ...
(WW) RADEON(0):   MC_FB_LOCATION  was: 0x3fff3800 is: 0x3fff3800
(WW) RADEON(0):   MC_AGP_LOCATION was: 0xffffffc0 is: 0x41ff4000
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x3fff3800 0x3fff3800
(II) RADEON(0):   MC_AGP_LOCATION  : 0x41ff4000
(II) RADEON(0): Direct rendering enabled
(II) RADEON(0): Render acceleration enabled for R300/R400/R500 type cards.
(II) RADEON(0): Setting EXA maxPitchBytes
(II) RADEON(0): num quad-pipes is 3
(II) EXA(0): Offscreen pixmap area of 57376768 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(II)         UploadToScreen
(II)         DownloadFromScreen
(II) RADEON(0): Acceleration enabled
(II) RADEON(0): DPMS enabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): No video input capabilities detected and no information is provided - disabling multimedia i2c
(II) Loading sub module "theatre_detect"
(II) LoadModule: "theatre_detect"
(II) Loading /usr/lib/xorg/modules/multimedia//theatre_detect_drv.so
(II) Module theatre_detect: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(II) RADEON(0): no multimedia table present, disabling Rage Theatre.
(II) RADEON(0): Set up overlay video
(II) RADEON(0): Set up textured video
disable TVDAC
disable LVDS
disable LVDS
init memmap
init common
init crtc1
init pll1
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x3fff3800 0x3fff3800
(II) RADEON(0):   MC_AGP_LOCATION  : 0x41ff4000
restore common
restore crtc1
restore pll1
set RMX
set LVDS
enable LVDS
disable TVDAC
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
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
drmOpenByBusid: Searching for BusID pci:0000:01:05.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_make_current_read
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: enabled GLX_texture_from_pixmap with driver support
(II) AIGLX: Loaded and initialized /usr/lib/dri/r300_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) RADEON(0): Setting screen physical size to 331 x 207
(II) config/hal: Adding input device SynPS/2 Synaptics TouchPad
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.1.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) Synaptics touchpad driver version 1.1.2
(**) Option "Device" "/dev/input/event10"
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
(II) SynPS/2 Synaptics TouchPad: buttons: left right middle double triple
(--) SynPS/2 Synaptics TouchPad: touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) filter chain progression: 2.00
(**) SynPS/2 Synaptics TouchPad: (accel) filter stage 0: 20.00 ms
(**) SynPS/2 Synaptics TouchPad: (accel) set acceleration profile 0
(--) SynPS/2 Synaptics TouchPad: touchpad found
(II) config/hal: Adding input device Dell WMI hotkeys
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 2.2.5
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) Dell WMI hotkeys: always reports core events
(**) Dell WMI hotkeys: Device: "/dev/input/event7"
(II) Dell WMI hotkeys: Found keys
(II) Dell WMI hotkeys: Configuring as keyboard
(II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event5"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Video Bus
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event6"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event4"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
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
(II) config/hal: Adding input device Sleep Button
(**) Sleep Button: always reports core events
(**) Sleep Button: Device: "/dev/input/event2"
(II) Sleep Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): EDID for output LVDS
(II) RADEON(0): Manufacturer: AUO  Model: 1c74  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 1
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.600 redY: 0.350   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.115   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 71.1 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1301  h_sync_end 1333 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 804  v_sync_end 808 v_blanking: 823 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 59.3 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1301  h_sync_end 1333 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 804  v_sync_end 808 v_blanking: 823 v_border: 0
(II) RADEON(0):  FF059
(II) RADEON(0):  0AMWx€Ìø
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006af741c00000000
(II) RADEON(0): 	010f0103802115780aa7e599594f8c27
(II) RADEON(0): 	1d505400000001010101010101010101
(II) RADEON(0): 	010101010101c71b00a0502017301520
(II) RADEON(0): 	44004bcf10000018261700a050201730
(II) RADEON(0): 	152044004bcf10000000000000fe0046
(II) RADEON(0): 	463035390042313534455731000000fe
(II) RADEON(0): 	0030414d5778a4ccf801010a202000e9
(II) RADEON(0): EDID vendor "AUO", prod id 7284
(II) RADEON(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x800"x0.0   71.11  1280 1301 1333 1440  800 804 808 823 -hsync -vsync (49.4 kHz)
(II) RADEON(0): Modeline "1280x800"x0.0   59.26  1280 1301 1333 1440  800 804 808 823 -hsync -vsync (41.2 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: AUO  Model: 1c74  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 1
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.600 redY: 0.350   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.115   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 71.1 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1301  h_sync_end 1333 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 804  v_sync_end 808 v_blanking: 823 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 59.3 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1301  h_sync_end 1333 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 804  v_sync_end 808 v_blanking: 823 v_border: 0
(II) RADEON(0):  FF059
(II) RADEON(0):  0AMWx€Ìø
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006af741c00000000
(II) RADEON(0): 	010f0103802115780aa7e599594f8c27
(II) RADEON(0): 	1d505400000001010101010101010101
(II) RADEON(0): 	010101010101c71b00a0502017301520
(II) RADEON(0): 	44004bcf10000018261700a050201730
(II) RADEON(0): 	152044004bcf10000000000000fe0046
(II) RADEON(0): 	463035390042313534455731000000fe
(II) RADEON(0): 	0030414d5778a4ccf801010a202000e9
(II) RADEON(0): EDID vendor "AUO", prod id 7284
(II) RADEON(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
(II) RADEON(0): Printing probed modes for output LVDS
(II) RADEON(0): Modeline "1280x800"x60.0   71.11  1280 1301 1333 1440  800 804 808 823 -hsync -vsync (49.4 kHz)
(II) RADEON(0): Modeline "1280x800"x50.0   59.26  1280 1301 1333 1440  800 804 808 823 -hsync -vsync (41.2 kHz)
(II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
(II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
(II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
(II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): EDID for output LVDS
(II) RADEON(0): Manufacturer: AUO  Model: 1c74  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 1
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.600 redY: 0.350   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.115   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 71.1 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1301  h_sync_end 1333 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 804  v_sync_end 808 v_blanking: 823 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 59.3 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1301  h_sync_end 1333 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 804  v_sync_end 808 v_blanking: 823 v_border: 0
(II) RADEON(0):  FF059
(II) RADEON(0):  0AMWx€Ìø
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006af741c00000000
(II) RADEON(0): 	010f0103802115780aa7e599594f8c27
(II) RADEON(0): 	1d505400000001010101010101010101
(II) RADEON(0): 	010101010101c71b00a0502017301520
(II) RADEON(0): 	44004bcf10000018261700a050201730
(II) RADEON(0): 	152044004bcf10000000000000fe0046
(II) RADEON(0): 	463035390042313534455731000000fe
(II) RADEON(0): 	0030414d5778a4ccf801010a202000e9
(II) RADEON(0): EDID vendor "AUO", prod id 7284
(II) RADEON(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x800"x0.0   71.11  1280 1301 1333 1440  800 804 808 823 -hsync -vsync (49.4 kHz)
(II) RADEON(0): Modeline "1280x800"x0.0   59.26  1280 1301 1333 1440  800 804 808 823 -hsync -vsync (41.2 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: AUO  Model: 1c74  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 1
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.600 redY: 0.350   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.115   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 71.1 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1301  h_sync_end 1333 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 804  v_sync_end 808 v_blanking: 823 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 59.3 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1301  h_sync_end 1333 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 804  v_sync_end 808 v_blanking: 823 v_border: 0
(II) RADEON(0):  FF059
(II) RADEON(0):  0AMWx€Ìø
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006af741c00000000
(II) RADEON(0): 	010f0103802115780aa7e599594f8c27
(II) RADEON(0): 	1d505400000001010101010101010101
(II) RADEON(0): 	010101010101c71b00a0502017301520
(II) RADEON(0): 	44004bcf10000018261700a050201730
(II) RADEON(0): 	152044004bcf10000000000000fe0046
(II) RADEON(0): 	463035390042313534455731000000fe
(II) RADEON(0): 	0030414d5778a4ccf801010a202000e9
(II) RADEON(0): EDID vendor "AUO", prod id 7284
(II) RADEON(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
(II) RADEON(0): Printing probed modes for output LVDS
(II) RADEON(0): Modeline "1280x800"x60.0   71.11  1280 1301 1333 1440  800 804 808 823 -hsync -vsync (49.4 kHz)
(II) RADEON(0): Modeline "1280x800"x50.0   59.26  1280 1301 1333 1440  800 804 808 823 -hsync -vsync (41.2 kHz)
(II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
(II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
(II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
(II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): EDID for output LVDS
(II) RADEON(0): Manufacturer: AUO  Model: 1c74  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 1
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.600 redY: 0.350   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.115   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 71.1 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1301  h_sync_end 1333 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 804  v_sync_end 808 v_blanking: 823 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 59.3 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1301  h_sync_end 1333 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 804  v_sync_end 808 v_blanking: 823 v_border: 0
(II) RADEON(0):  FF059
(II) RADEON(0):  0AMWx€Ìø
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006af741c00000000
(II) RADEON(0): 	010f0103802115780aa7e599594f8c27
(II) RADEON(0): 	1d505400000001010101010101010101
(II) RADEON(0): 	010101010101c71b00a0502017301520
(II) RADEON(0): 	44004bcf10000018261700a050201730
(II) RADEON(0): 	152044004bcf10000000000000fe0046
(II) RADEON(0): 	463035390042313534455731000000fe
(II) RADEON(0): 	0030414d5778a4ccf801010a202000e9
(II) RADEON(0): EDID vendor "AUO", prod id 7284
(II) RADEON(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x800"x0.0   71.11  1280 1301 1333 1440  800 804 808 823 -hsync -vsync (49.4 kHz)
(II) RADEON(0): Modeline "1280x800"x0.0   59.26  1280 1301 1333 1440  800 804 808 823 -hsync -vsync (41.2 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: AUO  Model: 1c74  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 1
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.600 redY: 0.350   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.115   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 71.1 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1301  h_sync_end 1333 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 804  v_sync_end 808 v_blanking: 823 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 59.3 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1301  h_sync_end 1333 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 804  v_sync_end 808 v_blanking: 823 v_border: 0
(II) RADEON(0):  FF059
(II) RADEON(0):  0AMWx€Ìø
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006af741c00000000
(II) RADEON(0): 	010f0103802115780aa7e599594f8c27
(II) RADEON(0): 	1d505400000001010101010101010101
(II) RADEON(0): 	010101010101c71b00a0502017301520
(II) RADEON(0): 	44004bcf10000018261700a050201730
(II) RADEON(0): 	152044004bcf10000000000000fe0046
(II) RADEON(0): 	463035390042313534455731000000fe
(II) RADEON(0): 	0030414d5778a4ccf801010a202000e9
(II) RADEON(0): EDID vendor "AUO", prod id 7284
(II) RADEON(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
(II) RADEON(0): Printing probed modes for output LVDS
(II) RADEON(0): Modeline "1280x800"x60.0   71.11  1280 1301 1333 1440  800 804 808 823 -hsync -vsync (49.4 kHz)
(II) RADEON(0): Modeline "1280x800"x50.0   59.26  1280 1301 1333 1440  800 804 808 823 -hsync -vsync (41.2 kHz)
(II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
(II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
(II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
(II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): EDID for output LVDS
(II) RADEON(0): Manufacturer: AUO  Model: 1c74  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 1
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.600 redY: 0.350   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.115   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 71.1 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1301  h_sync_end 1333 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 804  v_sync_end 808 v_blanking: 823 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 59.3 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1301  h_sync_end 1333 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 804  v_sync_end 808 v_blanking: 823 v_border: 0
(II) RADEON(0):  FF059
(II) RADEON(0):  0AMWx€Ìø
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006af741c00000000
(II) RADEON(0): 	010f0103802115780aa7e599594f8c27
(II) RADEON(0): 	1d505400000001010101010101010101
(II) RADEON(0): 	010101010101c71b00a0502017301520
(II) RADEON(0): 	44004bcf10000018261700a050201730
(II) RADEON(0): 	152044004bcf10000000000000fe0046
(II) RADEON(0): 	463035390042313534455731000000fe
(II) RADEON(0): 	0030414d5778a4ccf801010a202000e9
(II) RADEON(0): EDID vendor "AUO", prod id 7284
(II) RADEON(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x800"x0.0   71.11  1280 1301 1333 1440  800 804 808 823 -hsync -vsync (49.4 kHz)
(II) RADEON(0): Modeline "1280x800"x0.0   59.26  1280 1301 1333 1440  800 804 808 823 -hsync -vsync (41.2 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: AUO  Model: 1c74  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 1
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.600 redY: 0.350   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.115   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 71.1 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1301  h_sync_end 1333 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 804  v_sync_end 808 v_blanking: 823 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 59.3 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1301  h_sync_end 1333 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 804  v_sync_end 808 v_blanking: 823 v_border: 0
(II) RADEON(0):  FF059
(II) RADEON(0):  0AMWx€Ìø
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006af741c00000000
(II) RADEON(0): 	010f0103802115780aa7e599594f8c27
(II) RADEON(0): 	1d505400000001010101010101010101
(II) RADEON(0): 	010101010101c71b00a0502017301520
(II) RADEON(0): 	44004bcf10000018261700a050201730
(II) RADEON(0): 	152044004bcf10000000000000fe0046
(II) RADEON(0): 	463035390042313534455731000000fe
(II) RADEON(0): 	0030414d5778a4ccf801010a202000e9
(II) RADEON(0): EDID vendor "AUO", prod id 7284
(II) RADEON(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
(II) RADEON(0): Printing probed modes for output LVDS
(II) RADEON(0): Modeline "1280x800"x60.0   71.11  1280 1301 1333 1440  800 804 808 823 -hsync -vsync (49.4 kHz)
(II) RADEON(0): Modeline "1280x800"x50.0   59.26  1280 1301 1333 1440  800 804 808 823 -hsync -vsync (41.2 kHz)
(II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
(II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
(II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
(II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): EDID for output LVDS
(II) RADEON(0): Manufacturer: AUO  Model: 1c74  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 1
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.600 redY: 0.350   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.115   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 71.1 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1301  h_sync_end 1333 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 804  v_sync_end 808 v_blanking: 823 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 59.3 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1301  h_sync_end 1333 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 804  v_sync_end 808 v_blanking: 823 v_border: 0
(II) RADEON(0):  FF059
(II) RADEON(0):  0AMWx€Ìø
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006af741c00000000
(II) RADEON(0): 	010f0103802115780aa7e599594f8c27
(II) RADEON(0): 	1d505400000001010101010101010101
(II) RADEON(0): 	010101010101c71b00a0502017301520
(II) RADEON(0): 	44004bcf10000018261700a050201730
(II) RADEON(0): 	152044004bcf10000000000000fe0046
(II) RADEON(0): 	463035390042313534455731000000fe
(II) RADEON(0): 	0030414d5778a4ccf801010a202000e9
(II) RADEON(0): EDID vendor "AUO", prod id 7284
(II) RADEON(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x800"x0.0   71.11  1280 1301 1333 1440  800 804 808 823 -hsync -vsync (49.4 kHz)
(II) RADEON(0): Modeline "1280x800"x0.0   59.26  1280 1301 1333 1440  800 804 808 823 -hsync -vsync (41.2 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: AUO  Model: 1c74  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 1
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.600 redY: 0.350   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.115   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 71.1 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1301  h_sync_end 1333 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 804  v_sync_end 808 v_blanking: 823 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 59.3 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1301  h_sync_end 1333 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 804  v_sync_end 808 v_blanking: 823 v_border: 0
(II) RADEON(0):  FF059
(II) RADEON(0):  0AMWx€Ìø
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006af741c00000000
(II) RADEON(0): 	010f0103802115780aa7e599594f8c27
(II) RADEON(0): 	1d505400000001010101010101010101
(II) RADEON(0): 	010101010101c71b00a0502017301520
(II) RADEON(0): 	44004bcf10000018261700a050201730
(II) RADEON(0): 	152044004bcf10000000000000fe0046
(II) RADEON(0): 	463035390042313534455731000000fe
(II) RADEON(0): 	0030414d5778a4ccf801010a202000e9
(II) RADEON(0): EDID vendor "AUO", prod id 7284
(II) RADEON(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
(II) RADEON(0): Printing probed modes for output LVDS
(II) RADEON(0): Modeline "1280x800"x60.0   71.11  1280 1301 1333 1440  800 804 808 823 -hsync -vsync (49.4 kHz)
(II) RADEON(0): Modeline "1280x800"x50.0   59.26  1280 1301 1333 1440  800 804 808 823 -hsync -vsync (41.2 kHz)
(II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
(II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
(II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
(II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): EDID for output LVDS
(II) RADEON(0): Manufacturer: AUO  Model: 1c74  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 1
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.600 redY: 0.350   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.115   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 71.1 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1301  h_sync_end 1333 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 804  v_sync_end 808 v_blanking: 823 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 59.3 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1301  h_sync_end 1333 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 804  v_sync_end 808 v_blanking: 823 v_border: 0
(II) RADEON(0):  FF059
(II) RADEON(0):  0AMWx€Ìø
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006af741c00000000
(II) RADEON(0): 	010f0103802115780aa7e599594f8c27
(II) RADEON(0): 	1d505400000001010101010101010101
(II) RADEON(0): 	010101010101c71b00a0502017301520
(II) RADEON(0): 	44004bcf10000018261700a050201730
(II) RADEON(0): 	152044004bcf10000000000000fe0046
(II) RADEON(0): 	463035390042313534455731000000fe
(II) RADEON(0): 	0030414d5778a4ccf801010a202000e9
(II) RADEON(0): EDID vendor "AUO", prod id 7284
(II) RADEON(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x800"x0.0   71.11  1280 1301 1333 1440  800 804 808 823 -hsync -vsync (49.4 kHz)
(II) RADEON(0): Modeline "1280x800"x0.0   59.26  1280 1301 1333 1440  800 804 808 823 -hsync -vsync (41.2 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: AUO  Model: 1c74  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 1
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.600 redY: 0.350   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.115   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 71.1 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1301  h_sync_end 1333 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 804  v_sync_end 808 v_blanking: 823 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 59.3 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1301  h_sync_end 1333 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 804  v_sync_end 808 v_blanking: 823 v_border: 0
(II) RADEON(0):  FF059
(II) RADEON(0):  0AMWx€Ìø
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006af741c00000000
(II) RADEON(0): 	010f0103802115780aa7e599594f8c27
(II) RADEON(0): 	1d505400000001010101010101010101
(II) RADEON(0): 	010101010101c71b00a0502017301520
(II) RADEON(0): 	44004bcf10000018261700a050201730
(II) RADEON(0): 	152044004bcf10000000000000fe0046
(II) RADEON(0): 	463035390042313534455731000000fe
(II) RADEON(0): 	0030414d5778a4ccf801010a202000e9
(II) RADEON(0): EDID vendor "AUO", prod id 7284
(II) RADEON(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
(II) RADEON(0): Printing probed modes for output LVDS
(II) RADEON(0): Modeline "1280x800"x60.0   71.11  1280 1301 1333 1440  800 804 808 823 -hsync -vsync (49.4 kHz)
(II) RADEON(0): Modeline "1280x800"x50.0   59.26  1280 1301 1333 1440  800 804 808 823 -hsync -vsync (41.2 kHz)
(II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
(II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
(II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
(II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): EDID for output LVDS
(II) RADEON(0): Manufacturer: AUO  Model: 1c74  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 1
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.600 redY: 0.350   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.115   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 71.1 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1301  h_sync_end 1333 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 804  v_sync_end 808 v_blanking: 823 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 59.3 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1301  h_sync_end 1333 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 804  v_sync_end 808 v_blanking: 823 v_border: 0
(II) RADEON(0):  FF059
(II) RADEON(0):  0AMWx€Ìø
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006af741c00000000
(II) RADEON(0): 	010f0103802115780aa7e599594f8c27
(II) RADEON(0): 	1d505400000001010101010101010101
(II) RADEON(0): 	010101010101c71b00a0502017301520
(II) RADEON(0): 	44004bcf10000018261700a050201730
(II) RADEON(0): 	152044004bcf10000000000000fe0046
(II) RADEON(0): 	463035390042313534455731000000fe
(II) RADEON(0): 	0030414d5778a4ccf801010a202000e9
(II) RADEON(0): EDID vendor "AUO", prod id 7284
(II) RADEON(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x800"x0.0   71.11  1280 1301 1333 1440  800 804 808 823 -hsync -vsync (49.4 kHz)
(II) RADEON(0): Modeline "1280x800"x0.0   59.26  1280 1301 1333 1440  800 804 808 823 -hsync -vsync (41.2 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: AUO  Model: 1c74  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 1
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.600 redY: 0.350   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.115   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 71.1 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1301  h_sync_end 1333 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 804  v_sync_end 808 v_blanking: 823 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 59.3 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1301  h_sync_end 1333 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 804  v_sync_end 808 v_blanking: 823 v_border: 0
(II) RADEON(0):  FF059
(II) RADEON(0):  0AMWx€Ìø
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006af741c00000000
(II) RADEON(0): 	010f0103802115780aa7e599594f8c27
(II) RADEON(0): 	1d505400000001010101010101010101
(II) RADEON(0): 	010101010101c71b00a0502017301520
(II) RADEON(0): 	44004bcf10000018261700a050201730
(II) RADEON(0): 	152044004bcf10000000000000fe0046
(II) RADEON(0): 	463035390042313534455731000000fe
(II) RADEON(0): 	0030414d5778a4ccf801010a202000e9
(II) RADEON(0): EDID vendor "AUO", prod id 7284
(II) RADEON(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
(II) RADEON(0): Printing probed modes for output LVDS
(II) RADEON(0): Modeline "1280x800"x60.0   71.11  1280 1301 1333 1440  800 804 808 823 -hsync -vsync (49.4 kHz)
(II) RADEON(0): Modeline "1280x800"x50.0   59.26  1280 1301 1333 1440  800 804 808 823 -hsync -vsync (41.2 kHz)
(II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
(II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
(II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
(II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)

---

### Post by spiderbatdad on 2009-12-23
lol

---

### Post by Lambchopper on 2009-12-23
> **spiderbatdad said:**
> lol

What's so funny?

---

### Post by ademey on 2009-12-26
I can confirm this isues for my dell vostro 1000

In my particular case, the issue is accompanied by a (wired) network failure. After reboot (or 2 reboots), login is normal (GUI) and network works fine.

The issue seems to happen more often, if not only, after using windows (I dual boot windows vista and ubuntu 9.10 x86_64)

integrated graphics: ATI Radeon xpress 1150

I reported this issue on other similar threads, but so far no response.. any ideas?

---

### Post by Lambchopper on 2010-01-05
I did some more testing and poking around on this last night.  I found a couple of ACPI messages and an unstable Clocking message in my Syslog.  I also found that this happens mostly when the computer is powered up from being shutdown completely.  Rebooting doesn't seem to be a problem.  I also found if I boot in to the BIOS and then exit and reboot from there, it's also not a problem.  My computer is a Dell Inspiron 1501.  

At this point I'm starting to suspect a conflict with the Kernel and my Hardware.  This wasn't a problem until a recent Kernel upgrade.  For what ever reason, I'm suspecting that some hardware isn't initializing fast enough and that hangs the system.

Here's what I've tried so far with no luck:
[LIST]
[*]Upgraded the BIOS to the most recent Dell version.
[*]Turned off the PowerNow feature in the BIOS.
[*]Changed the Clocking source to ACPI_PM
[/LIST]

Here's what I have yet to try:
[LIST]
[*]Revert back to the previous Kernel.
[*]Look in to all the Kernel ACPI settings and see if there are any that make sense to tweek.
[/LIST]

Any more ideas would be helpful.

---

### Post by Lambchopper on 2010-01-07
> **Lambchopper said:**
> I did some more testing and poking around on this last night.  I found a couple of ACPI messages and an unstable Clocking message in my Syslog.  I also found that this happens mostly when the computer is powered up from being shutdown completely.  Rebooting doesn't seem to be a problem.  I also found if I boot in to the BIOS and then exit and reboot from there, it's also not a problem.  My computer is a Dell Inspiron 1501.  

At this point I'm starting to suspect a conflict with the Kernel and my Hardware.  This wasn't a problem until a recent Kernel upgrade.  For what ever reason, I'm suspecting that some hardware isn't initializing fast enough and that hangs the system.

Here's what I've tried so far with no luck:
[LIST]
[*]Upgraded the BIOS to the most recent Dell version.
[*]Turned off the PowerNow feature in the BIOS.
[*]Changed the Clocking source to ACPI_PM
[/LIST]

Here's what I have yet to try:
[LIST]
[*]Revert back to the previous Kernel.
[*]Look in to all the Kernel ACPI settings and see if there are any that make sense to tweek.
[/LIST]

Any more ideas would be helpful.

Ok, so these last two items didn't work. I'm desperate, any ideas?

Thanks in advance...

---

### Post by HiImTye on 2010-01-07
are you using any sort of BIOS feature like a 'fast boot' or 'super boot'? one that saves the previous configuration and then applies it the next time it boots up? if so, try disabling that and see if it fixes it

---

### Post by Lambchopper on 2010-01-08
> **HiImTye said:**
> are you using any sort of BIOS feature like a 'fast boot' or 'super boot'? one that saves the previous configuration and then applies it the next time it boots up? if so, try disabling that and see if it fixes it

Thank you.  I did have a QuickBoot setting and I disabled it. But it didn't work.  I'm starting to think maybe it's a Gnome problem. The machine boots fine to a Text Based Login and then will sit there for about 3 minutes until I eventually get a GUI login screen.  While on the Text based login, I can actually login and do things, so it's not like the computer is hung, it's just taking forever to start X.  errr.....

---

### Post by Lambchopper on 2010-01-08
Ok, I'm really starting to think this is a X-Server problem.  I went back and looked at the xorg.log file and referenced AllowEmptyInput On causing an error with the kbd module.  I added:

Section "ServerFlags"
       Option "AllowEmptyInput" "off"
EndSection

That at least changed the response I was getting from the xorg.log file.  

Now I get an error:
(II) LoadModule: "kbd"
(WW) Warning, couldn't open module kbd
(II) UnloadModule: "kbd"
(EE) Failed to load module "kbd" (module does not exist, 0)
(EE) No input driver matching `kbd'

I'm starting to think the cause of my problem are these kbd module errors.  Since (correct me if I"m wrong, as I often am) I would think that the fact that the Gnome Login screen hangs up would indicate that the xserver is having a problem starting..

---

### Post by Lambchopper on 2010-01-08
Ok, so I installed:

sudo apt-get install xserver-xorg-input-kbd

and it totally screwed everything up.  I couldn't log in any-more.  When I typed a single character, I would get 3 characters.  I wasn't able to login via the Gnome login screen until I booted in to text mode and removed that package.

So I'm back where I started..

ERRR.....

---

