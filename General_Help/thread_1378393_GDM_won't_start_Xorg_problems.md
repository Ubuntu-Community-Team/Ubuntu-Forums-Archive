---
title: "GDM won't start Xorg problems"
date: 2010-01-11
forum: General Help
---

### Post by jammersplace on 2010-01-11
Xorg.0.log File
```

X.Org X Server 1.4.2
Release Date: 11 June 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux Debian (xorg-server 2:1.4.2-10.lenny2)
Current Operating System: Linux tablet 2.6.26-2-686 #1 SMP Wed Aug 19 06:06:52 UTC 2009 i686
Build Date: 08 June 2009  09:12:57AM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Jan 11 06:06:27 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(==) No device specified for screen "Default Screen".
	Using the first device section listed.
(**) |   |-->Device "Configured Video Device"
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
	Using the first mouse device.
(==) The core keyboard device wasn't specified explicitly in the layout.
	Using the first keyboard device.
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81e38c0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 2.0
	X.Org XInput driver : 2.0
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.4.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,3575 card 10cf,113b rev 04 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 8086,3577 card 10cf,113c rev 04 class 03,00,00 hdr 80
(II) PCI: 00:02:1: chip 8086,3577 card 10cf,113c rev 00 class 03,80,00 hdr 80
(II) PCI: 00:1d:0: chip 8086,2482 card 10cf,113d rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2484 card 10cf,113d rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,2487 card 10cf,113d rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev 42 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,248c card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,248a card 10cf,113d rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,2483 card 10cf,113d rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,2485 card 10cf,1177 rev 02 class 04,01,00 hdr 00
(II) PCI: 00:1f:6: chip 8086,2486 card 10cf,10d1 rev 02 class 07,03,00 hdr 00
(II) PCI: 01:09:0: chip 10ec,8139 card 10cf,111c rev 10 class 02,00,00 hdr 00
(II) PCI: 01:0a:0: chip 104c,ac50 card 3400,0000 rev 01 class 06,07,00 hdr 02
(II) PCI: 01:0c:0: chip 1033,00e7 card 10cf,11a0 rev 01 class 0c,00,10 hdr 00
(II) PCI: 01:0d:0: chip 1260,3873 card 10cf,1169 rev 01 class 02,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:30:0), (0,1,5), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[1] -1	0	0x00003400 - 0x000034ff (0x100) IX[B]
	[2] -1	0	0x00003800 - 0x000038ff (0x100) IX[B]
	[3] -1	0	0x00003c00 - 0x00003cff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xe0200000 - 0xe02fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe0500000 - 0xe05fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 2: bridge is at (1:10:0), (1,2,5), BCTRL: 0x05c0 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00003400 - 0x000034ff (0x100) IX[B]
	[1] -1	0	0x00003800 - 0x000038ff (0x100) IX[B]
(--) PCI:*(0:2:0) Intel Corporation 82830 CGC [Chipset Graphics Controller] rev 4, Mem @ 0xe8000000/27, 0xe0000000/19
(--) PCI: (0:2:1) Intel Corporation 82830 CGC [Chipset Graphics Controller] rev 0, Mem @ 0xf0000000/27, 0xe0080000/19
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
(II) Active PCI resource ranges:
	[0] -1	0	0xe0500000 - 0xe0500fff (0x1000) MX[B]
	[1] -1	0	0xe0200000 - 0xe0200fff (0x1000) MX[B]
	[2] -1	0	0xe0201000 - 0xe02010ff (0x100) MX[B]
	[3] -1	0	0xe0100000 - 0xe01003ff (0x400) MX[B]
	[4] -1	0	0xe0080000 - 0xe00fffff (0x80000) MX[B](B)
	[5] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[6] -1	0	0xe0000000 - 0xe007ffff (0x80000) MX[B](B)
	[7] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[8] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[9] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[10] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[11] -1	0	0x000018c0 - 0x000018ff (0x40) IX[B]
	[12] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[13] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[14] -1	0	0x00001860 - 0x0000186f (0x10) IX[B]
	[15] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[16] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[17] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[20] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[21] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xe0500000 - 0xe0500fff (0x1000) MX[B]
	[1] -1	0	0xe0200000 - 0xe0200fff (0x1000) MX[B]
	[2] -1	0	0xe0201000 - 0xe02010ff (0x100) MX[B]
	[3] -1	0	0xe0100000 - 0xe01003ff (0x400) MX[B]
	[4] -1	0	0xe0080000 - 0xe00fffff (0x80000) MX[B](B)
	[5] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[6] -1	0	0xe0000000 - 0xe007ffff (0x80000) MX[B](B)
	[7] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[8] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[9] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[10] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[11] -1	0	0x000018c0 - 0x000018ff (0x40) IX[B]
	[12] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[13] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[14] -1	0	0x00001860 - 0x0000186f (0x10) IX[B]
	[15] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[16] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[17] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[20] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[21] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
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
	[4] -1	0	0xe0500000 - 0xe0500fff (0x1000) MX[B]
	[5] -1	0	0xe0200000 - 0xe0200fff (0x1000) MX[B]
	[6] -1	0	0xe0201000 - 0xe02010ff (0x100) MX[B]
	[7] -1	0	0xe0100000 - 0xe01003ff (0x400) MX[B]
	[8] -1	0	0xe0080000 - 0xe00fffff (0x80000) MX[B](B)
	[9] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[10] -1	0	0xe0000000 - 0xe007ffff (0x80000) MX[B](B)
	[11] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[15] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[16] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[17] -1	0	0x000018c0 - 0x000018ff (0x40) IX[B]
	[18] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[19] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[20] -1	0	0x00001860 - 0x0000186f (0x10) IX[B]
	[21] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[22] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[23] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[26] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[27] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.4.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
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
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.4.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.2, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) Matched intel from file name intel.ids in autoconfig
(==) Matched intel for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.4.2, module version = 2.3.2
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.3.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.3.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
	965GM, 965GME/GLE, G33, Q35, Q33,
	Mobile IntelÂ® GM45 Express Chipset,
	Intel Integrated Graphics Device, G45/G43, Q45/Q43, G41
(II) Primary Device is: PCI 00:02:0
(--) Assigning device section with no busID to primary device
(--) Chipset i830M found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe0500000 - 0xe0500fff (0x1000) MX[B]
	[5] -1	0	0xe0200000 - 0xe0200fff (0x1000) MX[B]
	[6] -1	0	0xe0201000 - 0xe02010ff (0x100) MX[B]
	[7] -1	0	0xe0100000 - 0xe01003ff (0x400) MX[B]
	[8] -1	0	0xe0080000 - 0xe00fffff (0x80000) MX[B](B)
	[9] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[10] -1	0	0xe0000000 - 0xe007ffff (0x80000) MX[B](B)
	[11] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[15] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[16] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[17] -1	0	0x000018c0 - 0x000018ff (0x40) IX[B]
	[18] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[19] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[20] -1	0	0x00001860 - 0x0000186f (0x10) IX[B]
	[21] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[22] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[23] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[26] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[27] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe0500000 - 0xe0500fff (0x1000) MX[B]
	[5] -1	0	0xe0200000 - 0xe0200fff (0x1000) MX[B]
	[6] -1	0	0xe0201000 - 0xe02010ff (0x100) MX[B]
	[7] -1	0	0xe0100000 - 0xe01003ff (0x400) MX[B]
	[8] -1	0	0xe0080000 - 0xe00fffff (0x80000) MX[B](B)
	[9] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[10] -1	0	0xe0000000 - 0xe007ffff (0x80000) MX[B](B)
	[11] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[12] 1	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[13] 1	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[14] 1	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[18] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[19] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[20] -1	0	0x000018c0 - 0x000018ff (0x40) IX[B]
	[21] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[22] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[23] -1	0	0x00001860 - 0x0000186f (0x10) IX[B]
	[24] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[25] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[26] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[29] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[30] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[31] 1	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[32] 1	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.4.2, module version = 1.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(**) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(**) intel(0): Option "AccelMethod" "uxa"
(**) intel(0): Option "Tiling" "true"
(II) intel(0): Integrated Graphics Chipset: Intel(R) 830M
(--) intel(0): Chipset: "i830"
(--) intel(0): Linear framebuffer at 0xE8000000
(--) intel(0): IO registers at addr 0xE0000000
(II) intel(0): 2 display pipes available.
(==) intel(0): Using EXA for acceleration
(==) intel(0): Enabling EXA render acceleration
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(II) intel(0): Output VGA using monitor section Configured Monitor
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "DVODDC_D" initialized.
(II) Loading sub module "sil164"
(II) LoadModule: "sil164"
(II) Loading /usr/lib/xorg/modules/drivers//sil164.so
(II) Module sil164: vendor="X.Org Foundation"
	compiled for 1.4.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) intel(0): I2C bus "DVOI2C_E" initialized.
(EE) intel(0): sil164 not detected got 5: from DVOI2C_E Slave 112.
(II) Loading sub module "ch7xxx"
(II) LoadModule: "ch7xxx"
(II) Loading /usr/lib/xorg/modules/drivers//ch7xxx.so
(II) Module ch7xxx: vendor="X.Org Foundation"
	compiled for 1.4.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) intel(0): I2C bus "DVOI2C_E" removed.
(II) intel(0): I2C bus "DVOI2C_E" initialized.
(II) Loading sub module "ivch"
(II) LoadModule: "ivch"
(II) Loading /usr/lib/xorg/modules/drivers//ivch.so
(II) Module ivch: vendor="X.Org Foundation"
	compiled for 1.4.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) intel(0): I2C bus "DVOI2C_E" removed.
(II) intel(0): I2C bus "DVOI2C_B" initialized.
(II) Loading sub module "tfp410"
(II) LoadModule: "tfp410"
(II) Loading /usr/lib/xorg/modules/drivers//tfp410.so
(II) Module tfp410: vendor="X.Org Foundation"
	compiled for 1.4.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) intel(0): I2C bus "DVOI2C_B" removed.
(II) intel(0): I2C bus "DVOI2C_E" initialized.
(EE) intel(0): tfp410 not detected got VID 1305: from DVOI2C_E Slave 112.
(II) Loading sub module "ch7017"
(II) LoadModule: "ch7017"
(II) Loading /usr/lib/xorg/modules/drivers//ch7017.so
(II) Module ch7017: vendor="X.Org Foundation"
	compiled for 1.4.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) intel(0): I2C bus "DVOI2C_E" removed.
(II) intel(0): I2C bus "DVOI2C_E" initialized.
(II) intel(0): I2C bus "DVOI2C_E" removed.
(II) intel(0): I2C bus "DVODDC_D" removed.
(II) intel(0): Output VGA disconnected
(EE) intel(0): No valid modes.
(II) UnloadModule: "intel"
(II) UnloadModule: "ch7017"
(II) Unloading /usr/lib/xorg/modules/drivers//ch7017.so
(II) UnloadModule: "tfp410"
(II) Unloading /usr/lib/xorg/modules/drivers//tfp410.so
(II) UnloadModule: "ivch"
(II) Unloading /usr/lib/xorg/modules/drivers//ivch.so
(II) UnloadModule: "ch7xxx"
(II) Unloading /usr/lib/xorg/modules/drivers//ch7xxx.so
(II) UnloadModule: "sil164"
(II) Unloading /usr/lib/xorg/modules/drivers//sil164.so
(II) UnloadModule: "vgahw"
(II) Unloading /usr/lib/xorg/modules//libvgahw.so
(II) UnloadModule: "vbe"
(II) Unloading /usr/lib/xorg/modules//libvbe.so
(II) UnloadModule: "int10"
(II) Unloading /usr/lib/xorg/modules//libint10.so
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
[COLOR="Red"]no screens found[/COLOR]

```
xorg.conf
```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection

#Section "Device"
#	Identifier	"Configured Video Device"
#EndSection

Section "Device"
	Identifier 	"Configured Video Device"
	Option		"AccelMethod"	"uxa"
	Option		"EXAOptimizeMigration"	"true"
	Option		"MigrationHeuristic"	"greedy"
	Option		"Tiling"	"true"
EndSection	

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes	"640x480"
	EndSubSection
EndSection

```

So I couldn't get ubuntu to install right for some reason but debian did install got it all running wireless works all that good stuff the pc is a Fujitsu Stylistic ST4120 has a intel 82830 for grafix if anyone could help me fix this problem because GDM won't start because of this problem. Since Ubuntu is sooo close to Debian I figured someone could help here.

---

### Post by jammersplace on 2010-01-11
bump

---

### Post by Favux on 2010-01-12
Hi jammersplace,

I think you need a "ServerLayout".  Something like:
```
Section "ServerLayout"
  Identifier    "Default Layout"
  Screen        "Default Screen"
EndSection

```

---

