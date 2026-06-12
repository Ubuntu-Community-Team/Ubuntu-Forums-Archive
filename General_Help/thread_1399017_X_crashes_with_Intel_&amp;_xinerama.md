---
title: "X crashes with Intel &amp; xinerama"
date: 2010-02-05
forum: General Help
---

### Post by fackamato on 2010-02-05
Hi,

I tried to enable xinerama on a T400 laptop and an external usb card, but x crashes.

```
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
```

The log file from X:

```
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): No memory allocations
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.

Backtrace:
0: /usr/bin/X(xorg_backtrace+0x3b) [0x8133d6b]
1: /usr/bin/X(xf86SigHandler+0x55) [0x80c7d35]
2: [0xb7856400]
3: /usr/lib/xorg/modules/drivers//intel_drv.so [0xb73ab08a]
4: /usr/bin/X [0x80ced05]
5: /usr/bin/X [0x80cef85]
6: /usr/bin/X(xf86HandleColormaps+0x20d) [0x80cfeed]
7: /usr/lib/xorg/modules/drivers//intel_drv.so [0xb73afb36]
8: /usr/bin/X(AddScreen+0x198) [0x8071c38]
9: /usr/bin/X(InitOutput+0x72e) [0x80b07fe]
10: /usr/bin/X(main+0x1cb) [0x807234b]
11: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0xb7545b56]
12: /usr/bin/X [0x80719c1]
Saw signal 11.  Server aborting.
(II) Screen 0 shares mem & io resources
(II) Screen 1 shares mem & io resources
 ddxSigGiveUp: Closing log
```

What gives?

```

Section "Device"
	Identifier  "Card0"
	Driver      "intel"
	VendorName  "Intel Corporation"
	BoardName   "Mobile 4 Series Chipset Integrated Graphics Controller"
	BusID       "PCI:0:2:0"
EndSection

Section "Device"
	Identifier "SiS USB2VGA"
	VendorName "SiS" # Value does not matter
	BoardName "SiS" # Value does not matter
	Driver "sisusb"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
Section "Screen"
	Identifier "Screen1"
	Device     "SiS USB2VGA"
	Monitor    "Monitor1"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen	0	"Screen0"
	Screen	1	"Screen1" RightOf "Screen0"
	Option "Xinerama" "on"
EndSection

```

---

