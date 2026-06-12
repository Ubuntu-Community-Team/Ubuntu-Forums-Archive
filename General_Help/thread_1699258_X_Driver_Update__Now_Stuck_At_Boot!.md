---
title: "X Driver Update | Now Stuck At Boot!"
date: 2011-03-03
forum: General Help
---

### Post by Jonher937 on 2011-03-03
Hi!

I updated my server via SSH from another computer.
I'm running Ubuntu 10.10 on my old laptop.

I updated it at the 1/3. But now i experience problems!
Since the update there where Radeon driver updates which made Ubuntu not to load X.

[http://wiki.x.org/wiki/RecentChanges](http://wiki.x.org/wiki/RecentChanges)

You can see the update @ 1/3.

The computer is a HP 6715s.
As I can remember there is a Radeon X1250 in the computer.

How can I get the old version working again without reinstalling?

**Xorg.log**

```

[    24.793] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    24.793] X Protocol Version 11, Revision 0
[    24.793] Build Operating System: Linux 2.6.24-28-server i686 Ubuntu
[    24.793] Current Operating System: Linux jonte-port 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:48 UTC 2011 i686
[    24.793] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-25-generic root=UUID=aac9d1be-54b8-4865-9f7f-c8e1da590065 ro quiet splash
[    24.793] Build Date: 09 January 2011  12:14:58PM
[    24.793] xorg-server 2:1.9.0-0ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
[    24.793] Current version of pixman: 0.18.4
[    24.793] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    24.793] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    24.793] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Mar  1 21:18:26 2011
[    24.843] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    24.852] (==) No Layout section.  Using the first Screen section.
[    24.852] (==) No screen section available. Using defaults.
[    24.852] (**) |-->Screen "Default Screen Section" (0)
[    24.852] (**) |   |-->Monitor "<default monitor>"
[    24.852] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    24.852] (==) Automatically adding devices
[    24.852] (==) Automatically enabling devices
[    24.852] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    24.852] 	Entry deleted from font path.
[    24.852] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    24.852] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    24.852] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    24.852] (II) Loader magic: 0x81f9b00
[    24.852] (II) Module ABI versions:
[    24.852] 	X.Org ANSI C Emulation: 0.4
[    24.852] 	X.Org Video Driver: 8.0
[    24.852] 	X.Org XInput driver : 11.0
[    24.852] 	X.Org Server Extension : 4.0
[    24.853] (--) PCI:*(0:1:5:0) 1002:791f:103c:30c2 rev 0, Mem @ 0xc0000000/134217728, 0xd0200000/65536, 0xd0300000/1048576, I/O @ 0x00004000/256
[    24.854] (II) Open ACPI successful (/var/run/acpid.socket)
[    24.854] (II) LoadModule: "extmod"
[    24.894] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    24.895] (II) Module extmod: vendor="X.Org Foundation"
[    24.895] 	compiled for 1.9.0, module version = 1.0.0
[    24.895] 	Module class: X.Org Server Extension
[    24.895] 	ABI class: X.Org Server Extension, version 4.0
[    24.895] (II) Loading extension MIT-SCREEN-SAVER
[    24.895] (II) Loading extension XFree86-VidModeExtension
[    24.895] (II) Loading extension XFree86-DGA
[    24.895] (II) Loading extension DPMS
[    24.895] (II) Loading extension XVideo
[    24.895] (II) Loading extension XVideo-MotionCompensation
[    24.895] (II) Loading extension X-Resource
[    24.895] (II) LoadModule: "dbe"
[    24.895] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    24.895] (II) Module dbe: vendor="X.Org Foundation"
[    24.895] 	compiled for 1.9.0, module version = 1.0.0
[    24.895] 	Module class: X.Org Server Extension
[    24.895] 	ABI class: X.Org Server Extension, version 4.0
[    24.895] (II) Loading extension DOUBLE-BUFFER
[    24.895] (II) LoadModule: "glx"
[    24.895] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    24.895] (II) Module glx: vendor="X.Org Foundation"
[    24.895] 	compiled for 1.9.0, module version = 1.0.0
[    24.895] 	ABI class: X.Org Server Extension, version 4.0
[    24.896] (==) AIGLX enabled
[    24.896] (II) Loading extension GLX
[    24.896] (II) LoadModule: "record"
[    24.896] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    24.896] (II) Module record: vendor="X.Org Foundation"
[    24.896] 	compiled for 1.9.0, module version = 1.13.0
[    24.896] 	Module class: X.Org Server Extension
[    24.896] 	ABI class: X.Org Server Extension, version 4.0
[    24.896] (II) Loading extension RECORD
[    24.896] (II) LoadModule: "dri"
[    24.896] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    24.896] (II) Module dri: vendor="X.Org Foundation"
[    24.896] 	compiled for 1.9.0, module version = 1.0.0
[    24.896] 	ABI class: X.Org Server Extension, version 4.0
[    24.896] (II) Loading extension XFree86-DRI
[    24.896] (II) LoadModule: "dri2"
[    24.897] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    24.897] (II) Module dri2: vendor="X.Org Foundation"
[    24.897] 	compiled for 1.9.0, module version = 1.2.0
[    24.897] 	ABI class: X.Org Server Extension, version 4.0
[    24.897] (II) Loading extension DRI2
[    24.897] (==) Matched ati as autoconfigured driver 0
[    24.897] (==) Matched vesa as autoconfigured driver 1
[    24.897] (==) Matched fbdev as autoconfigured driver 2
[    24.897] (==) Assigned the driver to the xf86ConfigLayout
[    24.897] (II) LoadModule: "ati"
[    24.897] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    24.897] (II) Module ati: vendor="X.Org Foundation"
[    24.897] 	compiled for 1.9.0, module version = 6.13.1
[    24.897] 	Module class: X.Org Video Driver
[    24.897] 	ABI class: X.Org Video Driver, version 8.0
[    24.897] (II) LoadModule: "radeon"
[    24.898] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    24.898] (II) Module radeon: vendor="X.Org Foundation"
[    24.898] 	compiled for 1.9.0, module version = 6.13.1
[    24.898] 	Module class: X.Org Video Driver
[    24.898] 	ABI class: X.Org Video Driver, version 8.0
[    24.898] (II) LoadModule: "vesa"
[    24.898] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    24.899] (II) Module vesa: vendor="X.Org Foundation"
[    24.899] 	compiled for 1.8.99.905, module version = 2.3.0
[    24.899] 	Module class: X.Org Video Driver
[    24.899] 	ABI class: X.Org Video Driver, version 8.0
[    24.899] (II) LoadModule: "fbdev"
[    24.899] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    24.899] (II) Module fbdev: vendor="X.Org Foundation"
[    24.899] 	compiled for 1.8.99.905, module version = 0.4.2
[    24.899] 	ABI class: X.Org Video Driver, version 8.0
[    24.899] (II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI FireMV 2400 3155 (PCI),
	ATI Radeon X600 (RV380) 3E50 (PCIE),
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
	ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
	ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
	ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
	ATI Mobility Radeon HD 4670, ATI FirePro M5750,
	ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
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
	ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
	ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
	ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
	ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI Radeon HD 2600 LE,
	ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
	ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
	ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
	ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
	ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
	ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
	ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
	ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
	ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
	ATI Radeon 3000 Graphics, ATI Radeon HD 4200, ATI Radeon 4100,
	ATI Mobility Radeon HD 4200, ATI Mobility Radeon 4100,
	ATI Radeon HD 4290, ATI Radeon HD 4290, CYPRESS,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5900 Series, ATI Radeon HD 5900 Series,
	ATI Mobility Radeon HD 5800 Series,
	ATI Mobility Radeon HD 5800 Series,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
	ATI Radeon HD 5700 Series, ATI Radeon HD 5700 Series,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
	ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, CEDAR, CEDAR, CEDAR,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, CEDAR, ATI Radeon HD 5450,
	CEDAR
[    24.924] (II) VESA: driver for VESA chipsets: vesa
[    24.924] (II) FBDEV: driver for framebuffer: fbdev
[    24.924] (++) using VT number 7

[    24.925] (II) [KMS] Kernel modesetting enabled.
[    24.925] (WW) Falling back to old probe method for vesa
[    24.925] (WW) Falling back to old probe method for fbdev
[    24.925] (II) Loading sub module "fbdevhw"
[    24.925] (II) LoadModule: "fbdevhw"
[    24.925] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    24.925] (II) Module fbdevhw: vendor="X.Org Foundation"
[    24.925] 	compiled for 1.9.0, module version = 0.0.2
[    24.925] 	ABI class: X.Org Video Driver, version 8.0
[    24.925] (II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    24.925] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    24.925] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    24.925] (==) RADEON(0): Default visual is TrueColor
[    24.925] (==) RADEON(0): RGB weight 888
[    24.925] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    24.925] (--) RADEON(0): Chipset: "ATI Radeon X1200" (ChipID = 0x791f)
[    24.925] (II) RADEON(0): PCI card detected
[    24.925] (II) RADEON(0): KMS Color Tiling: enabled
[    24.925] drmOpenDevice: node name is /dev/dri/card0
[    24.925] drmOpenDevice: open result is 9, (OK)
[    24.925] drmOpenByBusid: Searching for BusID pci:0000:01:05.0
[    24.925] drmOpenDevice: node name is /dev/dri/card0
[    24.925] drmOpenDevice: open result is 9, (OK)
[    24.925] drmOpenByBusid: drmOpenMinor returns 9
[    24.925] drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
[    25.072] (II) RADEON(0): Output VGA-0 has no monitor section
[    25.072] (II) RADEON(0): Output LVDS has no monitor section
[    25.216] (II) RADEON(0): Output S-video has no monitor section
[    25.360] (II) RADEON(0): EDID for output VGA-0
[    25.360] (II) RADEON(0): EDID for output LVDS
[    25.360] (II) RADEON(0): Manufacturer: LPL  Model: db00  Serial#: 0
[    25.360] (II) RADEON(0): Year: 2006  Week: 0
[    25.360] (II) RADEON(0): EDID Version: 1.3
[    25.360] (II) RADEON(0): Digital Display Input
[    25.360] (II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
[    25.360] (II) RADEON(0): Gamma: 2.20
[    25.360] (II) RADEON(0): No DPMS capabilities specified
[    25.360] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    25.360] (II) RADEON(0): First detailed timing is preferred mode
[    25.360] (II) RADEON(0): redX: 0.600 redY: 0.351   greenX: 0.324 greenY: 0.554
[    25.360] (II) RADEON(0): blueX: 0.153 blueY: 0.145   whiteX: 0.312 whiteY: 0.328
[    25.360] (II) RADEON(0): Manufacturer's mask: 0
[    25.360] (II) RADEON(0): Supported detailed timing:
[    25.360] (II) RADEON(0): clock: 71.0 MHz   Image Size:  331 x 207 mm
[    25.360] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
[    25.360] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
[    25.360] (II) RADEON(0):  LGPhilipsLCD
[    25.360] (II) RADEON(0):  LP154WX4-TLC1
[    25.360] (II) RADEON(0): EDID (in hex):
[    25.360] (II) RADEON(0): 	00ffffffffffff00320c00db00000000
[    25.360] (II) RADEON(0): 	00100103802115780ab3409959538d27
[    25.360] (II) RADEON(0): 	25505400000001010101010101010101
[    25.360] (II) RADEON(0): 	010101010101bc1b00a0502017303020
[    25.360] (II) RADEON(0): 	36004bcf100000190000000000000000
[    25.360] (II) RADEON(0): 	00000000000000000000000000fe004c
[    25.360] (II) RADEON(0): 	475068696c6970734c43440a000000fe
[    25.360] (II) RADEON(0): 	004c503135345758342d544c43310046
[    25.360] (II) RADEON(0): Printing probed modes for output LVDS
[    25.360] (II) RADEON(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[    25.360] (II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
[    25.360] (II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
[    25.360] (II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
[    25.360] (II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[    25.360] (II) RADEON(0): Modeline "848x480"x59.7   31.50  848 872 952 1056  480 483 493 500 -hsync +vsync (29.8 kHz)
[    25.360] (II) RADEON(0): Modeline "720x480"x59.7   26.75  720 744 808 896  480 483 493 500 -hsync +vsync (29.9 kHz)
[    25.360] (II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[    25.504] (II) RADEON(0): EDID for output S-video
[    25.504] (II) RADEON(0): Output VGA-0 disconnected
[    25.504] (II) RADEON(0): Output LVDS connected
[    25.504] (II) RADEON(0): Output S-video disconnected
[    25.504] (II) RADEON(0): Using exact sizes for initial modes
[    25.504] (II) RADEON(0): Output LVDS using initial mode 1280x800
[    25.504] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    25.504] (II) RADEON(0): mem size init: gart size :1fdff000 vram size: s:8000000 visible:7bd8000
[    25.504] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[    25.504] (==) RADEON(0): DPI set to (96, 96)
[    25.504] (II) Loading sub module "fb"
[    25.504] (II) LoadModule: "fb"
[    25.504] (II) Loading /usr/lib/xorg/modules/libfb.so
[    25.504] (II) Module fb: vendor="X.Org Foundation"
[    25.504] 	compiled for 1.9.0, module version = 1.0.0
[    25.504] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    25.504] (II) Loading sub module "ramdac"
[    25.504] (II) LoadModule: "ramdac"
[    25.504] (II) Module "ramdac" already built-in
[    25.504] (II) Loading sub module "exa"
[    25.504] (II) LoadModule: "exa"
[    25.504] (II) Loading /usr/lib/xorg/modules/libexa.so
[    25.505] (II) Module exa: vendor="X.Org Foundation"
[    25.505] 	compiled for 1.9.0, module version = 2.5.0
[    25.505] 	ABI class: X.Org Video Driver, version 8.0
[    25.505] (II) UnloadModule: "vesa"
[    25.505] (II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    25.505] (II) UnloadModule: "fbdev"
[    25.505] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    25.505] (II) UnloadModule: "fbdevhw"
[    25.505] (II) Unloading /usr/lib/xorg/modules/libfbdevhw.so
[    25.505] (--) Depth 24 pixmap format is 32 bpp
[    25.505] (II) RADEON(0): [DRI2] Setup complete
[    25.505] (II) RADEON(0): [DRI2]   DRI driver: r300
[    25.505] (II) RADEON(0): Front buffer size: 4000K
[    25.505] (II) RADEON(0): VRAM usage limit set to 110534K
[    25.505] (==) RADEON(0): Backing store disabled
[    25.505] (II) RADEON(0): Direct rendering enabled
[    25.505] (II) RADEON(0): Render acceleration enabled for R300/R400/R500 type cards.
[    25.505] (II) RADEON(0): Setting EXA maxPitchBytes
[    25.505] (II) EXA(0): Driver allocated offscreen pixmaps
[    25.505] (II) EXA(0): Driver registered support for the following operations:
[    25.505] (II)         Solid
[    25.505] (II)         Copy
[    25.505] (II)         Composite (RENDER acceleration)
[    25.505] (II)         UploadToScreen
[    25.505] (II)         DownloadFromScreen
[    25.505] (II) RADEON(0): Acceleration enabled
[    25.505] (==) RADEON(0): DPMS enabled
[    25.505] (==) RADEON(0): Silken mouse enabled
[    25.505] (II) RADEON(0): Set up textured video
[    25.505] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    25.506] (--) RandR disabled
[    25.506] (II) Initializing built-in extension Generic Event Extension
[    25.506] (II) Initializing built-in extension SHAPE
[    25.506] (II) Initializing built-in extension MIT-SHM
[    25.506] (II) Initializing built-in extension XInputExtension
[    25.506] (II) Initializing built-in extension XTEST
[    25.506] (II) Initializing built-in extension BIG-REQUESTS
[    25.506] (II) Initializing built-in extension SYNC
[    25.506] (II) Initializing built-in extension XKEYBOARD
[    25.506] (II) Initializing built-in extension XC-MISC
[    25.506] (II) Initializing built-in extension SECURITY
[    25.506] (II) Initializing built-in extension XINERAMA
[    25.506] (II) Initializing built-in extension XFIXES
[    25.506] (II) Initializing built-in extension RENDER
[    25.506] (II) Initializing built-in extension RANDR
[    25.506] (II) Initializing built-in extension COMPOSITE
[    25.506] (II) Initializing built-in extension DAMAGE
[    25.506] (II) Initializing built-in extension GESTURE
[    25.521] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    25.521] (II) AIGLX: enabled GLX_INTEL_swap_event
[    25.521] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    25.521] (II) AIGLX: enabled GLX_SGI_make_current_read
[    25.521] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    25.521] (II) AIGLX: Loaded and initialized /usr/lib/dri/r300_dri.so
[    25.521] (II) GLX: Initialized DRI2 GL provider for screen 0
[    25.522] (II) RADEON(0): Setting screen physical size to 338 x 211
[    25.546] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    25.556] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    25.556] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    25.556] (II) LoadModule: "evdev"
[    25.556] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.556] (II) Module evdev: vendor="X.Org Foundation"
[    25.556] 	compiled for 1.9.0, module version = 2.3.2
[    25.556] 	Module class: X.Org XInput Driver
[    25.556] 	ABI class: X.Org XInput driver, version 11.0
[    25.556] (**) Power Button: always reports core events
[    25.556] (**) Power Button: Device: "/dev/input/event2"
[    25.556] (II) Power Button: Found keys
[    25.556] (II) Power Button: Configuring as keyboard
[    25.556] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    25.556] (**) Option "xkb_rules" "evdev"
[    25.557] (**) Option "xkb_model" "evdev"
[    25.557] (**) Option "xkb_layout" "se"
[    25.559] (II) XKB: reuse xkmfile /var/lib/xkb/server-0AF9E7D16D4BD54DD200670A82421D73A1D8FAED.xkm
[    25.561] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    25.561] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    25.561] (**) Video Bus: always reports core events
[    25.561] (**) Video Bus: Device: "/dev/input/event4"
[    25.561] (II) Video Bus: Found keys
[    25.561] (II) Video Bus: Configuring as keyboard
[    25.561] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    25.561] (**) Option "xkb_rules" "evdev"
[    25.561] (**) Option "xkb_model" "evdev"
[    25.561] (**) Option "xkb_layout" "se"
[    25.563] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[    25.563] (II) No input driver/identifier specified (ignoring)
[    25.563] (II) config/udev: Adding input device Sleep Button (/dev/input/event0)
[    25.563] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    25.564] (**) Sleep Button: always reports core events
[    25.564] (**) Sleep Button: Device: "/dev/input/event0"
[    25.564] (II) Sleep Button: Found keys
[    25.564] (II) Sleep Button: Configuring as keyboard
[    25.564] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    25.564] (**) Option "xkb_rules" "evdev"
[    25.564] (**) Option "xkb_model" "evdev"
[    25.564] (**) Option "xkb_layout" "se"
[    25.569] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    25.569] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    25.569] (**) AT Translated Set 2 keyboard: always reports core events
[    25.569] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    25.569] (II) AT Translated Set 2 keyboard: Found keys
[    25.569] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    25.569] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    25.569] (**) Option "xkb_rules" "evdev"
[    25.569] (**) Option "xkb_model" "evdev"
[    25.569] (**) Option "xkb_layout" "se"
[    25.570] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event6)
[    25.570] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    25.570] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    25.570] (II) LoadModule: "synaptics"
[    25.570] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    25.590] (II) Module synaptics: vendor="X.Org Foundation"
[    25.590] 	compiled for 1.9.0, module version = 1.2.2
[    25.590] 	Module class: X.Org XInput Driver
[    25.590] 	ABI class: X.Org XInput driver, version 11.0
[    25.590] (II) Synaptics touchpad driver version 1.2.2
[    25.590] (**) Option "Device" "/dev/input/event6"
[    25.590] (II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[    25.590] (II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[    25.590] (II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    25.590] (II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
[    25.590] (II) SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    25.590] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    25.590] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    25.590] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    25.590] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    25.590] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
[    25.590] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    25.590] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    25.591] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    25.591] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    25.591] (II) No input driver/identifier specified (ignoring)
[    25.594] (II) config/udev: Adding input device HP WMI hotkeys (/dev/input/event5)
[    25.594] (**) HP WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    25.594] (**) HP WMI hotkeys: always reports core events
[    25.594] (**) HP WMI hotkeys: Device: "/dev/input/event5"
[    25.594] (II) HP WMI hotkeys: Found keys
[    25.594] (II) HP WMI hotkeys: Configuring as keyboard
[    25.594] (II) XINPUT: Adding extended input device "HP WMI hotkeys" (type: KEYBOARD)
[    25.594] (**) Option "xkb_rules" "evdev"
[    25.594] (**) Option "xkb_model" "evdev"
[    25.594] (**) Option "xkb_layout" "se"
[    26.496] (II) RADEON(0): EDID vendor "LPL", prod id 56064
[    26.505] (II) RADEON(0): Printing DDC gathered Modelines:
[    26.505] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[    26.792] (II) RADEON(0): EDID vendor "LPL", prod id 56064
[    26.792] (II) RADEON(0): Printing DDC gathered Modelines:
[    26.792] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[    27.080] (II) RADEON(0): EDID vendor "LPL", prod id 56064
[    27.080] (II) RADEON(0): Printing DDC gathered Modelines:
[    27.080] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[    27.376] (II) RADEON(0): EDID vendor "LPL", prod id 56064
[    27.376] (II) RADEON(0): Printing DDC gathered Modelines:
[    27.376] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[    29.272] (II) RADEON(0): EDID vendor "LPL", prod id 56064
[    29.272] (II) RADEON(0): Printing DDC gathered Modelines:
[    29.272] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[    29.584] (II) RADEON(0): EDID vendor "LPL", prod id 56064
[    29.584] (II) RADEON(0): Printing DDC gathered Modelines:
[    29.584] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[    30.312] (II) RADEON(0): EDID vendor "LPL", prod id 56064
[    30.312] (II) RADEON(0): Printing DDC gathered Modelines:
[    30.312] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[    30.736] (II) RADEON(0): EDID vendor "LPL", prod id 56064
[    30.736] (II) RADEON(0): Printing DDC gathered Modelines:
[    30.736] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[    32.212] (II) RADEON(0): EDID vendor "LPL", prod id 56064
[    32.212] (II) RADEON(0): Printing DDC gathered Modelines:
[    32.212] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[    32.672] (II) RADEON(0): EDID vendor "LPL", prod id 56064
[    32.672] (II) RADEON(0): Printing DDC gathered Modelines:
[    32.672] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[    33.612] (II) RADEON(0): EDID vendor "LPL", prod id 56064
[    33.612] (II) RADEON(0): Printing DDC gathered Modelines:
[    33.612] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[    34.440] (II) RADEON(0): EDID vendor "LPL", prod id 56064
[    34.440] (II) RADEON(0): Printing DDC gathered Modelines:
[    34.440] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[    43.484] (II) RADEON(0): EDID vendor "LPL", prod id 56064
[    43.484] (II) RADEON(0): Printing DDC gathered Modelines:
[    43.484] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[    51.940] (II) RADEON(0): EDID vendor "LPL", prod id 56064
[    51.940] (II) RADEON(0): Printing DDC gathered Modelines:
[    51.940] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)

```

Need anymore? Just ask.

/ Jonher937

---

### Post by Jonher937 on 2011-03-03
Bump

---

### Post by Jonher937 on 2011-03-13
Anyone?

---

