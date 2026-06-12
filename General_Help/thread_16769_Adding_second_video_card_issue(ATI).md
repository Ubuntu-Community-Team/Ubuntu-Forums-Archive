---
title: "Adding second video card issue(ATI)"
date: 2005-02-23
forum: General Help
---

### Post by quan on 2005-02-23
Hi,
I was using two monitors through the Radeon 9800 Pro (AGP) fine using Hoary and X.Org and the fglrx driver (all latest versions). I am adding two more monitors through a Radeon 9200 (PCI version). Basically, I am getting unresolved symbols when I added the second video card to xorg.conf. Here is what my xorg.conf looks like:

```
Section "Device"
	Identifier	"RV350Right"
	Driver		"fglrx"
	BusID		"PCI:3:0:0"
	Option 		"UseInternalAGPGART" "no"
	Screen 0
EndSection

Section "Device"
	Identifier	"RV350Left"
	Driver 		"fglrx"
	BusID		"PCI:3:0:0"
	Screen 1
EndSection

Section "Device"
	Identifier	"RV280Left"
	Driver 		"fglrx"
	BusID		"PCI:1:8:0"
	Option  	"UseInternalAGPGART" "no"
	Screen 0
EndSection

Section "Device"
	Identifier	"RV280Right"
	Driver 		"fglrx"
	BusID		"PCI:1:8:0"
	Screen 1
EndSection

Section "Monitor"
	Identifier	"Monitor0"
	HorizSync	28-80
	VertRefresh	48-75
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"Monitor1"
	HorizSync	30-85
	VertRefresh	42-120
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"Monitor2"
	HorizSync	30-85
	VertRefresh	42-120
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"Monitor3"
	HorizSync	30-85
	VertRefresh	42-120
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"RV350Right"
	Monitor		"Monitor0"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Screen1"
	Device		"RV350Left"
	Monitor		"Monitor1"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Screen2"
	Device		"RV280Left"
	Monitor		"Monitor2"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Screen3"
	Device		"RV280Right"
	Monitor		"Monitor3"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Screen0"
	Screen		"Screen1" LeftOf "Screen0"
	Screen		"Screen2" LeftOf "Screen1"
	Screen		"Screen3" LeftOf "Screen2"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection
```

And here is the error log:

```
(II) Primary Device is: PCI 03:00:0
(WW) fglrx: No matching Device section for instance (BusID PCI:1:8:1) found
(WW) fglrx: No matching Device section for instance (BusID PCI:3:0:1) found
(--) Chipset RADEON 9200 SE (RV280 5964) found
(--) Chipset RADEON 9800 PRO (R350 4E48) found
(--) Chipset RADEON 9800 PRO (R350 4E48) found
(--) Chipset RADEON 9200 SE (RV280 5964) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xdd000000 - 0xdd00007f (0x80) MX[B]
	[6] -1	0	0xe1025000 - 0xe10251ff (0x200) MX[B]
	[7] -1	0	0xe1020000 - 0xe1023fff (0x4000) MX[B]
	[8] -1	0	0xe1024000 - 0xe10247ff (0x800) MX[B]
	[9] -1	0	0xe2002000 - 0xe2002fff (0x1000) MX[B]
	[10] -1	0	0xe2001000 - 0xe20010ff (0x100) MX[B]
	[11] -1	0	0xe2000000 - 0xe2000fff (0x1000) MX[B]
	[12] -1	0	0xe2003000 - 0xe2003fff (0x1000) MX[B]
	[13] -1	0	0xd8000000 - 0xd7ffffff (0x0) MX[B]O
	[14] -1	0	0xdf000000 - 0xdf00ffff (0x10000) MX[B](B)
	[15] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[16] -1	0	0xc0000000 - 0xc3ffffff (0x4000000) MX[B](B)
	[17] -1	0	0xdf010000 - 0xdf01ffff (0x10000) MX[B](B)
	[18] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[19] -1	0	0xe1010000 - 0xe101ffff (0x10000) MX[B](B)
	[20] -1	0	0xb8000000 - 0xbfffffff (0x8000000) MX[B](B)
	[21] -1	0	0xe1000000 - 0xe100ffff (0x10000) MX[B](B)
	[22] -1	0	0xb0000000 - 0xb7ffffff (0x8000000) MX[B](B)
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[25] -1	0	0x0000c000 - 0x0000c07f (0x80) IX[B]
	[26] -1	0	0x0000bc00 - 0x0000bc0f (0x10) IX[B]
	[27] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[28] -1	0	0x0000b400 - 0x0000b407 (0x8) IX[B]
	[29] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[30] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[31] -1	0	0x0000a800 - 0x0000a807 (0x8) IX[B]
	[32] -1	0	0x0000a400 - 0x0000a43f (0x40) IX[B]
	[33] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[34] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[35] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[36] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B](B)
	[37] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x820e740
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xdd000000 - 0xdd00007f (0x80) MX[B]
	[6] -1	0	0xe1025000 - 0xe10251ff (0x200) MX[B]
	[7] -1	0	0xe1020000 - 0xe1023fff (0x4000) MX[B]
	[8] -1	0	0xe1024000 - 0xe10247ff (0x800) MX[B]
	[9] -1	0	0xe2002000 - 0xe2002fff (0x1000) MX[B]
	[10] -1	0	0xe2001000 - 0xe20010ff (0x100) MX[B]
	[11] -1	0	0xe2000000 - 0xe2000fff (0x1000) MX[B]
	[12] -1	0	0xe2003000 - 0xe2003fff (0x1000) MX[B]
	[13] -1	0	0xd8000000 - 0xd7ffffff (0x0) MX[B]O
	[14] -1	0	0xdf000000 - 0xdf00ffff (0x10000) MX[B](B)
	[15] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[16] -1	0	0xc0000000 - 0xc3ffffff (0x4000000) MX[B](B)
	[17] -1	0	0xdf010000 - 0xdf01ffff (0x10000) MX[B](B)
	[18] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[19] -1	0	0xe1010000 - 0xe101ffff (0x10000) MX[B](B)
	[20] -1	0	0xb8000000 - 0xbfffffff (0x8000000) MX[B](B)
	[21] -1	0	0xe1000000 - 0xe100ffff (0x10000) MX[B](B)
	[22] -1	0	0xb0000000 - 0xb7ffffff (0x8000000) MX[B](B)
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[25] -1	0	0x0000c000 - 0x0000c07f (0x80) IX[B]
	[26] -1	0	0x0000bc00 - 0x0000bc0f (0x10) IX[B]
	[27] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[28] -1	0	0x0000b400 - 0x0000b407 (0x8) IX[B]
	[29] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[30] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[31] -1	0	0x0000a800 - 0x0000a807 (0x8) IX[B]
	[32] -1	0	0x0000a400 - 0x0000a43f (0x40) IX[B]
	[33] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[34] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[35] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[36] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B](B)
	[37] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
Symbol firegl_PM4Alloc from module /usr/X11R6/lib/modules/drivers/fglrx_drv.o is unresolved!
Symbol firegl_PM4Alloc from module /usr/X11R6/lib/modules/drivers/fglrx_drv.o is unresolved!
Symbol fbGetWinPrivateIndex from module /usr/X11R6/lib/modules/drivers/fglrx_drv.o is unresolved!
Symbol firegl_PM4Alloc from module /usr/X11R6/lib/modules/drivers/fglrx_drv.o is unresolved!
Symbol firegl_PM4Alloc from module /usr/X11R6/lib/modules/drivers/fglrx_drv.o is unresolved!
Symbol XAACheckTileReducibility from module /usr/X11R6/lib/modules/drivers/fglrx_drv.o is unresolved!
.
.
.
.
.
.
.
.
Symbol firegl_PM4Alloc from module /usr/X11R6/lib/modules/drivers/fglrx_drv.o is unresolved!
Symbol firegl_PM4Alloc from module /usr/X11R6/lib/modules/drivers/fglrx_drv.o is unresolved!

   *** If unresolved symbols were reported above, they might not
   *** be the reason for the server aborting.

Fatal server error:
Caught signal 11.  Server aborting
```

I have no idea why this is happening. Keep in mind that X worked fine without the second video card, ie. when I commented out the two lines:
#Screen		"Screen2" LeftOf "Screen1"
#Screen		"Screen3" LeftOf "Screen2"

Any help is appreciated,

Quan

---

### Post by Gbillou on 2005-03-26
i have exactly the same problem, but i'm using only one graphic card lol, a mobility X700...

---

