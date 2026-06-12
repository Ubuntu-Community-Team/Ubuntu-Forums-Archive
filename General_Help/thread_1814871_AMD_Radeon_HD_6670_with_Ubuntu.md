---
title: "AMD Radeon HD 6670 with Ubuntu"
date: 2011-07-30
forum: General Help
---

### Post by waqas300 on 2011-07-30
Hi guys, 
    please help me configuring my AMD radeon 6670 with ubuntu. how do i use this card with ubuntu?:o

---

### Post by Vaphell on 2011-07-30
you can install drivers manually (available at amd.com) or add PPA to your software sources
[http://www.ubuntuupdates.org/ppas/27](http://www.ubuntuupdates.org/ppas/27)
fglrx is the package you want (fglrx-amdcccle to get catalyst control panel). In case you have fglrx driver installed, replace last command from the article with 
```
sudo apt-get upgrade
```

---

### Post by .... on 2011-07-30
[http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Installing_the_drivers_manually)

---

### Post by waqas300 on 2011-08-12
having problems with installing Radeon drivers :-( when i start ubuntu in normal mode black screens comes up and stays.

---

### Post by .... on 2011-08-12
Maybe you need to blacklist the radeon driver?  Post your /var/log/Xorg.0.log

---

### Post by linuxman94 on 2011-08-12
Make sure you installed the fglrx driver.  The two packages installed should be fglrx and fglrx-amdcccle.  If you already have both installed, then reinstall them and run this command in the terminal:

```
sudo aticonfig --initial
```

---

### Post by waqas300 on 2011-08-15
> **.... said:**
> Maybe you need to blacklist the radeon driver?  Post your /var/log/Xorg.0.log

here it is

[    21.577] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    21.577] X Protocol Version 11, Revision 0
[    21.577] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    21.577] Current Operating System: Linux ubuntu 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686
[    21.577] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=08114BE14EF585E9 loop=/ubuntu/disks/root.disk ro quiet splash
[    21.577] Build Date: 21 May 2011  11:38:35AM
[    21.577] xorg-server 2:1.10.1-1ubuntu1.1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    21.577] Current version of pixman: 0.20.2
[    21.577] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    21.577] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    21.578] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Aug 15 19:59:31 2011
[    21.578] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    21.578] (==) No Layout section.  Using the first Screen section.
[    21.579] (==) No screen section available. Using defaults.
[    21.579] (**) |-->Screen "Default Screen Section" (0)
[    21.579] (**) |   |-->Monitor "<default monitor>"
[    21.579] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    21.579] (==) Automatically adding devices
[    21.579] (==) Automatically enabling devices
[    21.579] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    21.579] 	Entry deleted from font path.
[    21.579] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    21.579] 	Entry deleted from font path.
[    21.579] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    21.579] 	Entry deleted from font path.
[    21.579] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    21.579] 	Entry deleted from font path.
[    21.579] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    21.579] 	Entry deleted from font path.
[    21.579] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    21.579] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    21.579] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    21.579] (II) Loader magic: 0x81ffde0
[    21.579] (II) Module ABI versions:
[    21.579] 	X.Org ANSI C Emulation: 0.4
[    21.579] 	X.Org Video Driver: 10.0
[    21.579] 	X.Org XInput driver : 12.3
[    21.579] 	X.Org Server Extension : 5.0
[    21.581] (--) PCI:*(0:1:0:0) 1002:6758:1682:3181 rev 0, Mem @ 0x80000000/268435456, 0x90100000/131072, I/O @ 0x00002000/256, BIOS @ 0x????????/131072
[    21.581] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    21.581] (II) LoadModule: "extmod"
[    21.636] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    21.636] (II) Module extmod: vendor="X.Org Foundation"
[    21.637] 	compiled for 1.10.1, module version = 1.0.0
[    21.637] 	Module class: X.Org Server Extension
[    21.637] 	ABI class: X.Org Server Extension, version 5.0
[    21.637] (II) Loading extension MIT-SCREEN-SAVER
[    21.637] (II) Loading extension XFree86-VidModeExtension
[    21.637] (II) Loading extension XFree86-DGA
[    21.637] (II) Loading extension DPMS
[    21.637] (II) Loading extension XVideo
[    21.637] (II) Loading extension XVideo-MotionCompensation
[    21.637] (II) Loading extension X-Resource
[    21.637] (II) LoadModule: "dbe"
[    21.637] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    21.637] (II) Module dbe: vendor="X.Org Foundation"
[    21.637] 	compiled for 1.10.1, module version = 1.0.0
[    21.637] 	Module class: X.Org Server Extension
[    21.637] 	ABI class: X.Org Server Extension, version 5.0
[    21.637] (II) Loading extension DOUBLE-BUFFER
[    21.637] (II) LoadModule: "glx"
[    21.637] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    21.637] (II) Module glx: vendor="X.Org Foundation"
[    21.637] 	compiled for 1.10.1, module version = 1.0.0
[    21.637] 	ABI class: X.Org Server Extension, version 5.0
[    21.637] (==) AIGLX enabled
[    21.637] (II) Loading extension GLX
[    21.637] (II) LoadModule: "record"
[    21.638] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    21.638] (II) Module record: vendor="X.Org Foundation"
[    21.638] 	compiled for 1.10.1, module version = 1.13.0
[    21.638] 	Module class: X.Org Server Extension
[    21.638] 	ABI class: X.Org Server Extension, version 5.0
[    21.638] (II) Loading extension RECORD
[    21.638] (II) LoadModule: "dri"
[    21.638] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    21.638] (II) Module dri: vendor="X.Org Foundation"
[    21.638] 	compiled for 1.10.1, module version = 1.0.0
[    21.638] 	ABI class: X.Org Server Extension, version 5.0
[    21.638] (II) Loading extension XFree86-DRI
[    21.638] (II) LoadModule: "dri2"
[    21.638] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    21.638] (II) Module dri2: vendor="X.Org Foundation"
[    21.638] 	compiled for 1.10.1, module version = 1.2.0
[    21.638] 	ABI class: X.Org Server Extension, version 5.0
[    21.638] (II) Loading extension DRI2
[    21.639] (==) Matched fglrx as autoconfigured driver 0
[    21.639] (==) Matched ati as autoconfigured driver 1
[    21.639] (==) Matched vesa as autoconfigured driver 2
[    21.639] (==) Matched fbdev as autoconfigured driver 3
[    21.639] (==) Assigned the driver to the xf86ConfigLayout
[    21.639] (II) LoadModule: "fglrx"
[    21.660] (WW) Warning, couldn't open module fglrx
[    21.660] (II) UnloadModule: "fglrx"
[    21.660] (II) Unloading fglrx
[    21.660] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    21.660] (II) LoadModule: "ati"
[    21.660] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    21.660] (II) Module ati: vendor="X.Org Foundation"
[    21.660] 	compiled for 1.10.1, module version = 6.14.0
[    21.660] 	Module class: X.Org Video Driver
[    21.660] 	ABI class: X.Org Video Driver, version 10.0
[    21.660] (II) LoadModule: "radeon"
[    21.661] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    21.661] (II) Module radeon: vendor="X.Org Foundation"
[    21.661] 	compiled for 1.10.1, module version = 6.14.0
[    21.661] 	Module class: X.Org Video Driver
[    21.661] 	ABI class: X.Org Video Driver, version 10.0
[    21.661] (II) LoadModule: "vesa"
[    21.661] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    21.662] (II) Module vesa: vendor="X.Org Foundation"
[    21.662] 	compiled for 1.10.0, module version = 2.3.0
[    21.662] 	Module class: X.Org Video Driver
[    21.662] 	ABI class: X.Org Video Driver, version 10.0
[    21.662] (II) LoadModule: "fbdev"
[    21.662] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    21.662] (II) Module fbdev: vendor="X.Org Foundation"
[    21.662] 	compiled for 1.10.0, module version = 0.4.2
[    21.662] 	ABI class: X.Org Video Driver, version 10.0
[    21.662] (II) RADEON: Driver for ATI Radeon chipsets:
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
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon IGP320M (U1) 4336,
	ATI Radeon IGP330M/340M/350M (U2) 4337,
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
	ATI Radeon HD 4290, ATI Radeon HD 4250, AMD Radeon HD 6310 Graphics,
	AMD Radeon HD 6310 Graphics, AMD Radeon HD 6250 Graphics,
	AMD Radeon HD 6250 Graphics, CYPRESS,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
	AMD Firestream 9350, ATI Radeon HD 5800 Series,
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
	ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon Graphics,
	ATI Mobility Radeon Graphics, CEDAR,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI FirePro 2270, CEDAR,
	ATI Radeon HD 5450, CEDAR, AMD Radeon HD 6900M Series,
	Mobility Radeon HD 6000 Series, BARTS, BARTS,
	Mobility Radeon HD 6000 Series, Mobility Radeon HD 6000 Series,
	BARTS, BARTS, BARTS, BARTS, AMD Radeon HD 6800 Series,
	AMD Radeon HD 6800 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, CAICOS, CAICOS,
	CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
	CAICOS
[    21.670] (II) VESA: driver for VESA chipsets: vesa
[    21.670] (II) FBDEV: driver for framebuffer: fbdev
[    21.670] (++) using VT number 7

[    21.670] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    21.670] (II) [KMS] Kernel modesetting enabled.
[    21.670] (WW) Falling back to old probe method for vesa
[    21.670] (WW) Falling back to old probe method for fbdev
[    21.670] (II) Loading sub module "fbdevhw"
[    21.670] (II) LoadModule: "fbdevhw"
[    21.670] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    21.670] (II) Module fbdevhw: vendor="X.Org Foundation"
[    21.670] 	compiled for 1.10.1, module version = 0.0.2
[    21.670] 	ABI class: X.Org Video Driver, version 10.0
[    21.670] (II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    21.670] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    21.670] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    21.670] (==) RADEON(0): Default visual is TrueColor
[    21.670] (==) RADEON(0): RGB weight 888
[    21.670] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    21.670] (--) RADEON(0): Chipset: "TURKS" (ChipID = 0x6758)
[    21.671] (II) RADEON(0): PCIE card detected
[    21.671] drmOpenDevice: node name is /dev/dri/card0
[    21.671] drmOpenDevice: open result is 8, (OK)
[    21.671] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[    21.671] drmOpenDevice: node name is /dev/dri/card0
[    21.671] drmOpenDevice: open result is 8, (OK)
[    21.671] drmOpenByBusid: drmOpenMinor returns 8
[    21.671] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[    21.671] (II) RADEON(0): KMS Color Tiling: disabled
[    21.671] (II) RADEON(0): KMS Pageflipping: enabled
[    21.671] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[    21.676] (II) RADEON(0): Output DisplayPort-0 has no monitor section
[    21.680] (II) RADEON(0): Output HDMI-0 has no monitor section
[    21.699] (II) RADEON(0): Output DVI-0 has no monitor section
[    21.704] (II) RADEON(0): EDID for output DisplayPort-0
[    21.708] (II) RADEON(0): EDID for output HDMI-0
[    21.718] (II) RADEON(0): EDID for output DVI-0
[    21.719] (II) RADEON(0): Printing probed modes for output DVI-0
[    21.719] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    21.719] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    21.719] (II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    21.719] (II) RADEON(0): Modeline "848x480"x60.0   33.75  848 864 976 1088  480 486 494 517 +hsync +vsync (31.0 kHz)
[    21.719] (II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 489 492 525 -hsync -vsync (31.5 kHz)
[    21.719] (II) RADEON(0): Output DisplayPort-0 disconnected
[    21.719] (II) RADEON(0): Output HDMI-0 disconnected
[    21.719] (II) RADEON(0): Output DVI-0 connected
[    21.719] (II) RADEON(0): Using fuzzy aspect match for initial modes
[    21.719] (II) RADEON(0): Output DVI-0 using initial mode 1024x768
[    21.719] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    21.719] (II) RADEON(0): mem size init: gart size :1fdff000 vram size: s:40000000 visible:fcc0000
[    21.719] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[    21.719] (==) RADEON(0): DPI set to (96, 96)
[    21.719] (II) Loading sub module "fb"
[    21.719] (II) LoadModule: "fb"
[    21.719] (II) Loading /usr/lib/xorg/modules/libfb.so
[    21.719] (II) Module fb: vendor="X.Org Foundation"
[    21.719] 	compiled for 1.10.1, module version = 1.0.0
[    21.719] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    21.719] (II) Loading sub module "ramdac"
[    21.719] (II) LoadModule: "ramdac"
[    21.719] (II) Module "ramdac" already built-in
[    21.719] (II) Loading sub module "exa"
[    21.719] (II) LoadModule: "exa"
[    21.719] (II) Loading /usr/lib/xorg/modules/libexa.so
[    21.719] (II) Module exa: vendor="X.Org Foundation"
[    21.719] 	compiled for 1.10.1, module version = 2.5.0
[    21.719] 	ABI class: X.Org Video Driver, version 10.0
[    21.719] (II) UnloadModule: "vesa"
[    21.719] (II) Unloading vesa
[    21.719] (II) UnloadModule: "fbdev"
[    21.719] (II) Unloading fbdev
[    21.719] (II) UnloadModule: "fbdevhw"
[    21.720] (II) Unloading fbdevhw
[    21.720] (--) Depth 24 pixmap format is 32 bpp
[    21.720] (II) RADEON(0): [DRI2] Setup complete
[    21.720] (II) RADEON(0): [DRI2]   DRI driver: r600
[    21.720] (II) RADEON(0): Front buffer size: 3072K
[    21.720] (II) RADEON(0): VRAM usage limit set to 230169K
[    21.720] (==) RADEON(0): Backing store disabled
[    21.720] (II) RADEON(0): Direct rendering enabled
[    21.720] (II) RADEON(0): Setting EXA maxPitchBytes
[    21.720] (II) EXA(0): Driver allocated offscreen pixmaps
[    21.720] (II) EXA(0): Driver registered support for the following operations:
[    21.720] (II)         Solid
[    21.720] (II)         Copy
[    21.720] (II)         Composite (RENDER acceleration)
[    21.720] (II)         UploadToScreen
[    21.720] (II)         DownloadFromScreen
[    21.720] (II) RADEON(0): Acceleration enabled
[    21.720] (==) RADEON(0): DPMS enabled
[    21.720] (==) RADEON(0): Silken mouse enabled
[    21.720] (II) RADEON(0): Set up textured video
[    21.720] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    21.721] (--) RandR disabled
[    21.721] (II) Initializing built-in extension Generic Event Extension
[    21.721] (II) Initializing built-in extension SHAPE
[    21.721] (II) Initializing built-in extension MIT-SHM
[    21.721] (II) Initializing built-in extension XInputExtension
[    21.721] (II) Initializing built-in extension XTEST
[    21.721] (II) Initializing built-in extension BIG-REQUESTS
[    21.721] (II) Initializing built-in extension SYNC
[    21.721] (II) Initializing built-in extension XKEYBOARD
[    21.721] (II) Initializing built-in extension XC-MISC
[    21.721] (II) Initializing built-in extension SECURITY
[    21.721] (II) Initializing built-in extension XINERAMA
[    21.721] (II) Initializing built-in extension XFIXES
[    21.721] (II) Initializing built-in extension RENDER
[    21.721] (II) Initializing built-in extension RANDR
[    21.721] (II) Initializing built-in extension COMPOSITE
[    21.721] (II) Initializing built-in extension DAMAGE
[    21.721] (II) Initializing built-in extension GESTURE
[    21.734] (II) AIGLX: Trying DRI driver /usr/lib/dri/r600_dri.so
[    21.738] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    21.738] (II) AIGLX: enabled GLX_INTEL_swap_event
[    21.738] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    21.738] (II) AIGLX: enabled GLX_SGI_make_current_read
[    21.738] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    21.739] (II) AIGLX: Loaded and initialized r600
[    21.739] (II) GLX: Initialized DRI2 GL provider for screen 0
[    21.739] (II) RADEON(0): Setting screen physical size to 270 x 203
[    21.752] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    21.763] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    21.763] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    21.763] (II) LoadModule: "evdev"
[    21.763] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.764] (II) Module evdev: vendor="X.Org Foundation"
[    21.764] 	compiled for 1.10.0.902, module version = 2.6.0
[    21.764] 	Module class: X.Org XInput Driver
[    21.764] 	ABI class: X.Org XInput driver, version 12.3
[    21.764] (II) Using input driver 'evdev' for 'Power Button'
[    21.764] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.764] (**) Power Button: always reports core events
[    21.764] (**) Power Button: Device: "/dev/input/event1"
[    21.780] (--) Power Button: Found keys
[    21.780] (II) Power Button: Configuring as keyboard
[    21.780] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    21.780] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    21.780] (**) Option "xkb_rules" "evdev"
[    21.780] (**) Option "xkb_model" "pc105"
[    21.780] (**) Option "xkb_layout" "us"
[    21.783] (II) config/udev: Adding input device Sleep Button (/dev/input/event0)
[    21.783] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    21.783] (II) Using input driver 'evdev' for 'Sleep Button'
[    21.783] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.783] (**) Sleep Button: always reports core events
[    21.783] (**) Sleep Button: Device: "/dev/input/event0"
[    21.796] (--) Sleep Button: Found keys
[    21.796] (II) Sleep Button: Configuring as keyboard
[    21.796] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input0/event0"
[    21.796] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    21.796] (**) Option "xkb_rules" "evdev"
[    21.796] (**) Option "xkb_model" "pc105"
[    21.796] (**) Option "xkb_layout" "us"
[    21.799] (II) config/udev: Adding input device Dell Dell USB Keyboard (/dev/input/event2)
[    21.799] (**) Dell Dell USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    21.799] (II) Using input driver 'evdev' for 'Dell Dell USB Keyboard'
[    21.799] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.799] (**) Dell Dell USB Keyboard: always reports core events
[    21.799] (**) Dell Dell USB Keyboard: Device: "/dev/input/event2"
[    21.816] (--) Dell Dell USB Keyboard: Found keys
[    21.816] (II) Dell Dell USB Keyboard: Configuring as keyboard
[    21.816] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.0/input/input2/event2"
[    21.816] (II) XINPUT: Adding extended input device "Dell Dell USB Keyboard" (type: KEYBOARD)
[    21.816] (**) Option "xkb_rules" "evdev"
[    21.816] (**) Option "xkb_model" "pc105"
[    21.816] (**) Option "xkb_layout" "us"
[    21.817] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/event3)
[    21.817] (**) USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    21.817] (II) Using input driver 'evdev' for 'USB Optical Mouse'
[    21.817] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.817] (**) USB Optical Mouse: always reports core events
[    21.817] (**) USB Optical Mouse: Device: "/dev/input/event3"
[    21.832] (--) USB Optical Mouse: Found 3 mouse buttons
[    21.832] (--) USB Optical Mouse: Found scroll wheel(s)
[    21.832] (--) USB Optical Mouse: Found relative axes
[    21.832] (--) USB Optical Mouse: Found x and y relative axes
[    21.832] (II) USB Optical Mouse: Configuring as mouse
[    21.832] (II) USB Optical Mouse: Adding scrollwheel support
[    21.832] (**) USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    21.832] (**) USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    21.832] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.1/usb4/4-2/4-2:1.0/input/input3/event3"
[    21.832] (II) XINPUT: Adding extended input device "USB Optical Mouse" (type: MOUSE)
[    21.832] (II) USB Optical Mouse: initialized for relative axes.
[    21.832] (**) USB Optical Mouse: (accel) keeping acceleration scheme 1
[    21.832] (**) USB Optical Mouse: (accel) acceleration profile 0
[    21.832] (**) USB Optical Mouse: (accel) acceleration factor: 2.000
[    21.832] (**) USB Optical Mouse: (accel) acceleration threshold: 4
[    21.832] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/mouse0)
[    21.832] (II) No input driver/identifier specified (ignoring)

---

### Post by .... on 2011-08-15
The log shows you using the open-source radeon driver (and doesn't show any errors). Is that the driver you're tryinf to use?

---

### Post by waqas300 on 2011-08-15
> **.... said:**
> The log shows you using the open-source radeon driver (and doesn't show any errors). Is that the driver you're tryinf to use?

i have downloaded the drivers from here

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English)

---

### Post by .... on 2011-08-17
[http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Installing_the_drivers_manually)

---

### Post by curmudgeon38 on 2012-03-08
Hey guys, I'm having the same problem.

So from what I gathered from above, what we should do is this:

1) Install fglrx and fglrx-amdcccle using instructions from this link:
[http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Updated_Open_Source_Driver_PPA.27s](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Updated_Open_Source_Driver_PPA.27s)

2)Run this line in the terminal:
sudo aticonfig --initial

3) Add PPA to software sources with these instructions:
[http://www.ubuntuupdates.org/ppa/ubuntu-x-swat](http://www.ubuntuupdates.org/ppa/ubuntu-x-swat)

But what about this driver?:
AMD Catalyst™ Proprietary Display Driver - Linux x86 & Linux x86_64 
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English)

And will it be working the next time I reboot?

Thanks

---

### Post by Wootyeah on 2012-04-08
I need some help with this too.  Anyone?

---

### Post by Zestypanda on 2012-10-11
I am having the exact same problem, I have posted multiple times yet I haven't found a fix, it is annoying, with steam coming to linux I am very excited and am fully eagar to switch all the way over to ubuntu. My Core 2 duo dual core 2.4ghz 4gb with asus branded 6670 is not wanting to cooperate with ubuntu.

---

### Post by earlgrey2 on 2013-08-22
I could get Xorg radeon driver working, but with poor performances comparing to AMD driver.  Currently most recent version of AMD drivers usable with RadeonHD6670 ( codename TURKS ) seems to be AMD Catalyst installer 13.1 ( See : [http://wiki.cchtml.com/index.php/Troubleshooting#.5BSOLVED.5D_RadeonHD6670_.26_Catalyst_13.4_:_X_server_crash_.28_segmentation_fault_after_driCreateNewScreen_in_fglrx_dri.so_.29_.2F_KMS_working](http://wiki.cchtml.com/index.php/Troubleshooting#.5BSOLVED.5D_RadeonHD6670_.26_Catalyst_13.4_:_X_server_crash_.28_segmentation_fault_after_driCreateNewScreen_in_fglrx_dri.so_.29_.2F_KMS_working) )

---

