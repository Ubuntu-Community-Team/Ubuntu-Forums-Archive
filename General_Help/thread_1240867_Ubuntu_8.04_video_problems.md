---
title: "Ubuntu 8.04 video problems"
date: 2009-08-15
forum: General Help
---

### Post by Alexmania on 2009-08-15
i'm new to ubuntu, i've heard so many good things about it, i decided to install it on my sister's old laptop to try it out, installed 8.04 because it was the only version that seemed to work properly on it, i followed some guides and got everything installed, for a week or so it worked great but after an update i started having problem with the video playback, about 80% of the times i open a video, a black screen appears and the only thing i can do is force the laptop to shutdown, it is really anoying.
i dont really know how to check the hardware configuration in ubuntu to post here :(
please, i need help to solve this problem.

---

### Post by coldReactive on 2009-08-15
What guides did you follow?

Also, did you make sure to...

```
gstreamer-properties
```

in terminal and set the video output to **X Window System (No Xv)**?

---

### Post by Yellow Pasque on 2009-08-15
What video chip and driver are we talking about here?

> i dont really know how to check the hardware configuration in ubuntu to post here
Some useful commands
```
lspci | grep VGA #this should tell you what video card you have
cat /var/log/Xorg.0.log #shows your X log
```

---

### Post by jerrrys on 2009-08-15
you should also install this

[https://help.ubuntu.com/community/RestrictedFormats#Playing%20Restricted%20Formats](https://help.ubuntu.com/community/RestrictedFormats#Playing%20Restricted%20Formats)

---

### Post by Alexmania on 2009-08-15
> **coldReactive said:**
> What guides did you follow?

Also, did you make sure to...

```
gstreamer-properties
```in terminal and set the video output to **X Window System (No Xv)**?

that makes all the videos run very slowly.
when i said guides i meant tutorials about getting ubuntu fully ready for use, istalling codecs, open office, etc.



this is the rusult of the commands that Temüjin said
```
$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
``````
$ cat /var/log/Xorg.0.log

This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux lucy-laptop 2.6.24-24-generic #1 SMP Fri Jul 24 22:46:06 UTC 2009 i686
Build Date: 13 June 2008  01:08:21AM
 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Aug 15 17:25:53 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(**) |-->Input Device "Synaptics Touchpad"
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
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
    Using the first core pointer device.
(==) The core keyboard device wasn't specified explicitly in the layout.
    Using the first keyboard device.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81dc500
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
    compiled for 1.4.0.90, module version = 1.0.0
    ABI class: X.Org Video Driver, version 2.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,3580 card 10cf,11d5 rev 02 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 8086,3584 card 10cf,11d5 rev 02 class 08,80,00 hdr 00
(II) PCI: 00:00:3: chip 8086,3585 card 10cf,11d5 rev 02 class 08,80,00 hdr 80
(II) PCI: 00:02:0: chip 8086,3582 card 10cf,120e rev 02 class 03,00,00 hdr 80
(II) PCI: 00:02:1: chip 8086,3582 card 10cf,120e rev 02 class 03,80,00 hdr 80
(II) PCI: 00:1d:0: chip 8086,24c2 card 10cf,11ab rev 03 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24c4 card 10cf,11ab rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24c7 card 10cf,11ab rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24cd card 10cf,11ab rev 03 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev 83 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24cc card 0000,0000 rev 03 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24ca card 10cf,11ab rev 03 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,24c3 card 10cf,11ab rev 03 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,24c5 card 10cf,11c3 rev 03 class 04,01,00 hdr 00
(II) PCI: 00:1f:6: chip 8086,24c6 card 10cf,10d1 rev 03 class 07,03,00 hdr 00
(II) PCI: 01:0a:0: chip 1217,6933 card 3401,0000 rev 20 class 06,07,00 hdr 82
(II) PCI: 01:0a:1: chip 1217,6933 card 3c01,0000 rev 20 class 06,07,00 hdr 82
(II) PCI: 01:0c:0: chip 10ec,8139 card 10cf,11bd rev 10 class 02,00,00 hdr 00
(II) PCI: 01:0d:0: chip 8086,1043 card 8086,2527 rev 04 class 02,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,3), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
    [0] -1    0    0x00000000 - 0x0000ffff (0x10000) IX[b]
(II) Bus 0 non-prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[b]
(II) Bus 0 prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[b]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:30:0), (0,1,6), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 1 I/O range:
    [0] -1    0    0x00003000 - 0x000030ff (0x100) IX[b]
    [1] -1    0    0x00003400 - 0x000034ff (0x100) IX[b]
    [2] -1    0    0x00003800 - 0x000038ff (0x100) IX[b]
    [3] -1    0    0x00003c00 - 0x00003cff (0x100) IX[b]
(II) Bus 1 non-prefetchable memory range:
    [0] -1    0    0xd0200000 - 0xd02fffff (0x100000) MX[b]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 2: bridge is at (1:10:0), (1,2,2), BCTRL: 0x0580 (VGA_EN is cleared)
(II) Bus 2 I/O range:
    [0] -1    0    0x00003400 - 0x000034ff (0x100) IX[b]
    [1] -1    0    0x00003800 - 0x000038ff (0x100) IX[b]
(II) PCI-to-CardBus bridge:
(II) Bus 3: bridge is at (1:10:1), (1,3,6), BCTRL: 0x0580 (VGA_EN is cleared)
(II) Bus 3 I/O range:
    [0] -1    0    0x00003c00 - 0x00003cff (0x100) IX[b]
(--) PCI:*(0:2:0) Intel Corporation 82852/855GM Integrated Graphics Device rev 2, Mem @ 0xd8000000/27, 0xd0000000/19, I/O @ 0x1800/3
(--) PCI: (0:2:1) Intel Corporation 82852/855GM Integrated Graphics Device rev 2, Mem @ 0xe0000000/27, 0xd0080000/19
(II) Addressable bus resource ranges are
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[b]
    [1] -1    0    0x00000000 - 0x0000ffff (0x10000) IX[b]
(II) OS-reported resource ranges:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
(II) Active PCI resource ranges:
    [0] -1    0    0xd0201000 - 0xd0201fff (0x1000) MX[b]
    [1] -1    0    0xd0200000 - 0xd02000ff (0x100) MX[b]
    [2] -1    0    0xd0100800 - 0xd01008ff (0x100) MX[b]
    [3] -1    0    0xd0100c00 - 0xd0100dff (0x200) MX[b]
    [4] -1    0    0x30000000 - 0x300003ff (0x400) MX[b]
    [5] -1    0    0xd0100000 - 0xd01003ff (0x400) MX[b]
    [6] -1    0    0xd0080000 - 0xd00fffff (0x80000) MX[b](B)
    [7] -1    0    0xe0000000 - 0xe7ffffff (0x8000000) MX[b](B)
    [8] -1    0    0xd0000000 - 0xd007ffff (0x80000) MX[b](B)
    [9] -1    0    0xd8000000 - 0xdfffffff (0x8000000) MX[b](B)
    [10] -1    0    0x00003000 - 0x000030ff (0x100) IX[b]
    [11] -1    0    0x00002000 - 0x0000207f (0x80) IX[b]
    [12] -1    0    0x00002400 - 0x000024ff (0x100) IX[b]
    [13] -1    0    0x000018c0 - 0x000018ff (0x40) IX[b]
    [14] -1    0    0x00001c00 - 0x00001cff (0x100) IX[b]
    [15] -1    0    0x00001880 - 0x0000189f (0x20) IX[b]
    [16] -1    0    0x00001810 - 0x0000181f (0x10) IX[b]
    [17] -1    0    0x000001f0 - 0x000001f0 (0x1) IX[b]
    [18] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[b]
    [19] -1    0    0x000001f0 - 0x000001f0 (0x1) IX[b]
    [20] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[b]
    [21] -1    0    0x00001860 - 0x0000187f (0x20) IX[b]
    [22] -1    0    0x00001840 - 0x0000185f (0x20) IX[b]
    [23] -1    0    0x00001820 - 0x0000183f (0x20) IX[b]
    [24] -1    0    0x00001800 - 0x00001807 (0x8) IX[b](B)
(II) Active PCI resource ranges after removing overlaps:
    [0] -1    0    0xd0201000 - 0xd0201fff (0x1000) MX[b]
    [1] -1    0    0xd0200000 - 0xd02000ff (0x100) MX[b]
    [2] -1    0    0xd0100800 - 0xd01008ff (0x100) MX[b]
    [3] -1    0    0xd0100c00 - 0xd0100dff (0x200) MX[b]
    [4] -1    0    0x30000000 - 0x300003ff (0x400) MX[b]
    [5] -1    0    0xd0100000 - 0xd01003ff (0x400) MX[b]
    [6] -1    0    0xd0080000 - 0xd00fffff (0x80000) MX[b](B)
    [7] -1    0    0xe0000000 - 0xe7ffffff (0x8000000) MX[b](B)
    [8] -1    0    0xd0000000 - 0xd007ffff (0x80000) MX[b](B)
    [9] -1    0    0xd8000000 - 0xdfffffff (0x8000000) MX[b](B)
    [10] -1    0    0x00003000 - 0x000030ff (0x100) IX[b]
    [11] -1    0    0x00002000 - 0x0000207f (0x80) IX[b]
    [12] -1    0    0x00002400 - 0x000024ff (0x100) IX[b]
    [13] -1    0    0x000018c0 - 0x000018ff (0x40) IX[b]
    [14] -1    0    0x00001c00 - 0x00001cff (0x100) IX[b]
    [15] -1    0    0x00001880 - 0x0000189f (0x20) IX[b]
    [16] -1    0    0x00001810 - 0x0000181f (0x10) IX[b]
    [17] -1    0    0x000001f0 - 0x000001f0 (0x1) IX[b]
    [18] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[b]
    [19] -1    0    0x000001f0 - 0x000001f0 (0x1) IX[b]
    [20] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[b]
    [21] -1    0    0x00001860 - 0x0000187f (0x20) IX[b]
    [22] -1    0    0x00001840 - 0x0000185f (0x20) IX[b]
    [23] -1    0    0x00001820 - 0x0000183f (0x20) IX[b]
    [24] -1    0    0x00001800 - 0x00001807 (0x8) IX[b](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
    [0] -1    0    0x00100000 - 0x2fffffff (0x2ff00000) MX[b]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
(II) All system resource ranges:
    [0] -1    0    0x00100000 - 0x2fffffff (0x2ff00000) MX[b]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xd0201000 - 0xd0201fff (0x1000) MX[b]
    [5] -1    0    0xd0200000 - 0xd02000ff (0x100) MX[b]
    [6] -1    0    0xd0100800 - 0xd01008ff (0x100) MX[b]
    [7] -1    0    0xd0100c00 - 0xd0100dff (0x200) MX[b]
    [8] -1    0    0x30000000 - 0x300003ff (0x400) MX[b]
    [9] -1    0    0xd0100000 - 0xd01003ff (0x400) MX[b]
    [10] -1    0    0xd0080000 - 0xd00fffff (0x80000) MX[b](B)
    [11] -1    0    0xe0000000 - 0xe7ffffff (0x8000000) MX[b](B)
    [12] -1    0    0xd0000000 - 0xd007ffff (0x80000) MX[b](B)
    [13] -1    0    0xd8000000 - 0xdfffffff (0x8000000) MX[b](B)
    [14] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [15] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
    [16] -1    0    0x00003000 - 0x000030ff (0x100) IX[b]
    [17] -1    0    0x00002000 - 0x0000207f (0x80) IX[b]
    [18] -1    0    0x00002400 - 0x000024ff (0x100) IX[b]
    [19] -1    0    0x000018c0 - 0x000018ff (0x40) IX[b]
    [20] -1    0    0x00001c00 - 0x00001cff (0x100) IX[b]
    [21] -1    0    0x00001880 - 0x0000189f (0x20) IX[b]
    [22] -1    0    0x00001810 - 0x0000181f (0x10) IX[b]
    [23] -1    0    0x000001f0 - 0x000001f0 (0x1) IX[b]
    [24] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[b]
    [25] -1    0    0x000001f0 - 0x000001f0 (0x1) IX[b]
    [26] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[b]
    [27] -1    0    0x00001860 - 0x0000187f (0x20) IX[b]
    [28] -1    0    0x00001840 - 0x0000185f (0x20) IX[b]
    [29] -1    0    0x00001820 - 0x0000183f (0x20) IX[b]
    [30] -1    0    0x00001800 - 0x00001807 (0x8) IX[b](B)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
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
    compiled for 1.4.0.90, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
    compiled for 1.4.0.90, module version = 2.1.0
    Module class: X.Org Font Renderer
    ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) Matched intel from file name intel.ids in autoconfig
(==) Matched intel for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 2.2.1
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
    compiled for 4.3.99.902, module version = 1.0.0
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
    compiled for 1.4.0, module version = 1.2.3
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
    compiled for 1.4.0, module version = 1.2.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 2.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
    965GM, 965GME/GLE, G33, Q35, Q33, Intel Integrated Graphics Device
(II) Primary Device is: PCI 00:02:0
(--) Assigning device section with no busID to primary device
(--) Chipset 852GM/855GM found
(II) resource ranges after xf86ClaimFixedResources() call:
    [0] -1    0    0x00100000 - 0x2fffffff (0x2ff00000) MX[b]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xd0201000 - 0xd0201fff (0x1000) MX[b]
    [5] -1    0    0xd0200000 - 0xd02000ff (0x100) MX[b]
    [6] -1    0    0xd0100800 - 0xd01008ff (0x100) MX[b]
    [7] -1    0    0xd0100c00 - 0xd0100dff (0x200) MX[b]
    [8] -1    0    0x30000000 - 0x300003ff (0x400) MX[b]
    [9] -1    0    0xd0100000 - 0xd01003ff (0x400) MX[b]
    [10] -1    0    0xd0080000 - 0xd00fffff (0x80000) MX[b](B)
    [11] -1    0    0xe0000000 - 0xe7ffffff (0x8000000) MX[b](B)
    [12] -1    0    0xd0000000 - 0xd007ffff (0x80000) MX[b](B)
    [13] -1    0    0xd8000000 - 0xdfffffff (0x8000000) MX[b](B)
    [14] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [15] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
    [16] -1    0    0x00003000 - 0x000030ff (0x100) IX[b]
    [17] -1    0    0x00002000 - 0x0000207f (0x80) IX[b]
    [18] -1    0    0x00002400 - 0x000024ff (0x100) IX[b]
    [19] -1    0    0x000018c0 - 0x000018ff (0x40) IX[b]
    [20] -1    0    0x00001c00 - 0x00001cff (0x100) IX[b]
    [21] -1    0    0x00001880 - 0x0000189f (0x20) IX[b]
    [22] -1    0    0x00001810 - 0x0000181f (0x10) IX[b]
    [23] -1    0    0x000001f0 - 0x000001f0 (0x1) IX[b]
    [24] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[b]
    [25] -1    0    0x000001f0 - 0x000001f0 (0x1) IX[b]
    [26] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[b]
    [27] -1    0    0x00001860 - 0x0000187f (0x20) IX[b]
    [28] -1    0    0x00001840 - 0x0000185f (0x20) IX[b]
    [29] -1    0    0x00001820 - 0x0000183f (0x20) IX[b]
    [30] -1    0    0x00001800 - 0x00001807 (0x8) IX[b](B)
(II) resource ranges after probing:
    [0] -1    0    0x00100000 - 0x2fffffff (0x2ff00000) MX[b]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xd0201000 - 0xd0201fff (0x1000) MX[b]
    [5] -1    0    0xd0200000 - 0xd02000ff (0x100) MX[b]
    [6] -1    0    0xd0100800 - 0xd01008ff (0x100) MX[b]
    [7] -1    0    0xd0100c00 - 0xd0100dff (0x200) MX[b]
    [8] -1    0    0x30000000 - 0x300003ff (0x400) MX[b]
    [9] -1    0    0xd0100000 - 0xd01003ff (0x400) MX[b]
    [10] -1    0    0xd0080000 - 0xd00fffff (0x80000) MX[b](B)
    [11] -1    0    0xe0000000 - 0xe7ffffff (0x8000000) MX[b](B)
    [12] -1    0    0xd0000000 - 0xd007ffff (0x80000) MX[b](B)
    [13] -1    0    0xd8000000 - 0xdfffffff (0x8000000) MX[b](B)
    [14] 1    0    0x000a0000 - 0x000affff (0x10000) MS[b]
    [15] 1    0    0x000b0000 - 0x000b7fff (0x8000) MS[b]
    [16] 1    0    0x000b8000 - 0x000bffff (0x8000) MS[b]
    [17] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [18] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
    [19] -1    0    0x00003000 - 0x000030ff (0x100) IX[b]
    [20] -1    0    0x00002000 - 0x0000207f (0x80) IX[b]
    [21] -1    0    0x00002400 - 0x000024ff (0x100) IX[b]
    [22] -1    0    0x000018c0 - 0x000018ff (0x40) IX[b]
    [23] -1    0    0x00001c00 - 0x00001cff (0x100) IX[b]
    [24] -1    0    0x00001880 - 0x0000189f (0x20) IX[b]
    [25] -1    0    0x00001810 - 0x0000181f (0x10) IX[b]
    [26] -1    0    0x000001f0 - 0x000001f0 (0x1) IX[b]
    [27] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[b]
    [28] -1    0    0x000001f0 - 0x000001f0 (0x1) IX[b]
    [29] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[b]
    [30] -1    0    0x00001860 - 0x0000187f (0x20) IX[b]
    [31] -1    0    0x00001840 - 0x0000185f (0x20) IX[b]
    [32] -1    0    0x00001820 - 0x0000183f (0x20) IX[b]
    [33] -1    0    0x00001800 - 0x00001807 (0x8) IX[b](B)
    [34] 1    0    0x000003b0 - 0x000003bb (0xc) IS[b]
    [35] 1    0    0x000003c0 - 0x000003df (0x20) IS[b]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.1.0
    ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 0.1.0
    ABI class: X.Org Video Driver, version 2.0
(II) intel(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (==) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 855GM
(--) intel(0): Chipset: "852GM/855GM"
(--) intel(0): Linear framebuffer at 0xD8000000
(--) intel(0): IO registers at addr 0xD0000000
(II) intel(0): 2 display pipes available.
(==) intel(0): Using EXA for acceleration
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(II) intel(0): Output VGA using monitor section Configured Monitor
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): Output LVDS has no monitor section
(II) intel(0): I2C bus "LVDSDDC_C" initialized.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) intel(0): initializing int10
(II) intel(0): Primary V_BIOS segment is: 0xc000
(II) intel(0): VESA BIOS detected
(II) intel(0): VESA VBE Version 3.0
(II) intel(0): VESA VBE Total Mem: 8000 kB
(II) intel(0): VESA VBE OEM: Intel(r)852MG/852MGE/855MG/855MGE Graphics Chip Accelerated VGA BIOS
(II) intel(0): VESA VBE OEM Software Rev: 1.0
(II) intel(0): VESA VBE OEM Vendor: Intel Corporation
(II) intel(0): VESA VBE OEM Product: Intel(r)852MG/852MGE/855MG/855MGE Graphics Controller
(II) intel(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) intel(0): I2C bus "DVODDC_D" initialized.
(II) Loading sub module "sil164"
(II) LoadModule: "sil164"
(II) Loading /usr/lib/xorg/modules/drivers//sil164.so
(II) Module sil164: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    ABI class: X.Org Video Driver, version 2.0
(II) intel(0): I2C bus "DVOI2C_E" initialized.
(II) Loading sub module "ch7xxx"
(II) LoadModule: "ch7xxx"
(II) Loading /usr/lib/xorg/modules/drivers//ch7xxx.so
(II) Module ch7xxx: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    ABI class: X.Org Video Driver, version 2.0
(II) intel(0): I2C bus "DVOI2C_E" removed.
(II) intel(0): I2C bus "DVOI2C_E" initialized.
(II) intel(0): Detected CH7009A chipset, vendor/device ID 0x84/0x17
(II) intel(0): I2C device "DVOI2C_E:CH7xxx TMDS Controller" registered at address 0xEC.
(II) intel(0): Output TMDS has no monitor section
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): Output VGA disconnected
(II) intel(0): Output LVDS connected
(II) intel(0): Output TMDS disconnected
(II) intel(0): Output LVDS using initial mode 1400x1050
(II) intel(0): Monitoring connected displays enabled
(II) intel(0): detected 128 kB GTT.
(II) intel(0): detected 8060 kB stolen memory.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Will not try to enable page flipping
(==) intel(0): Triple buffering disabled
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(==) intel(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 2.2.0
    ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) intel(0): Comparing regs from server start up to After PreInit
(WW) intel(0): Register 0x61200 (PP_STATUS) changed from 0xc0000008 to 0xd0000009
(WW) intel(0): PP_STATUS before: on, ready, sequencing idle
(WW) intel(0): PP_STATUS after: on, ready, sequencing on
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] 1    0    0xd0000000 - 0xd007ffff (0x80000) MS[b]
    [1] 1    0    0xd8000000 - 0xdfffffff (0x8000000) MS[b]
    [2] -1    0    0x00100000 - 0x2fffffff (0x2ff00000) MX[b]E(B)
    [3] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [4] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [5] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [6] -1    0    0xd0201000 - 0xd0201fff (0x1000) MX[b]
    [7] -1    0    0xd0200000 - 0xd02000ff (0x100) MX[b]
    [8] -1    0    0xd0100800 - 0xd01008ff (0x100) MX[b]
    [9] -1    0    0xd0100c00 - 0xd0100dff (0x200) MX[b]
    [10] -1    0    0x30000000 - 0x300003ff (0x400) MX[b]
    [11] -1    0    0xd0100000 - 0xd01003ff (0x400) MX[b]
    [12] -1    0    0xd0080000 - 0xd00fffff (0x80000) MX[b](B)
    [13] -1    0    0xe0000000 - 0xe7ffffff (0x8000000) MX[b](B)
    [14] -1    0    0xd0000000 - 0xd007ffff (0x80000) MX[b](B)
    [15] -1    0    0xd8000000 - 0xdfffffff (0x8000000) MX[b](B)
    [16] 1    0    0x000a0000 - 0x000affff (0x10000) MS[b](OprD)
    [17] 1    0    0x000b0000 - 0x000b7fff (0x8000) MS[b](OprD)
    [18] 1    0    0x000b8000 - 0x000bffff (0x8000) MS[b](OprD)
    [19] 1    0    0x00001800 - 0x00001807 (0x8) IS[b]
    [20] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [21] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
    [22] -1    0    0x00003000 - 0x000030ff (0x100) IX[b]
    [23] -1    0    0x00002000 - 0x0000207f (0x80) IX[b]
    [24] -1    0    0x00002400 - 0x000024ff (0x100) IX[b]
    [25] -1    0    0x000018c0 - 0x000018ff (0x40) IX[b]
    [26] -1    0    0x00001c00 - 0x00001cff (0x100) IX[b]
    [27] -1    0    0x00001880 - 0x0000189f (0x20) IX[b]
    [28] -1    0    0x00001810 - 0x0000181f (0x10) IX[b]
    [29] -1    0    0x000001f0 - 0x000001f0 (0x1) IX[b]
    [30] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[b]
    [31] -1    0    0x000001f0 - 0x000001f0 (0x1) IX[b]
    [32] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[b]
    [33] -1    0    0x00001860 - 0x0000187f (0x20) IX[b]
    [34] -1    0    0x00001840 - 0x0000185f (0x20) IX[b]
    [35] -1    0    0x00001820 - 0x0000183f (0x20) IX[b]
    [36] -1    0    0x00001800 - 0x00001807 (0x8) IX[b](B)
    [37] 1    0    0x000003b0 - 0x000003bb (0xc) IS[b](OprU)
    [38] 1    0    0x000003c0 - 0x000003df (0x20) IS[b](OprU)
(II) intel(0): Kernel reported 110080 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 440316 kB available
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) [drm] loaded kernel module for "i915" driver.
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) intel(0): [drm] Using the DRM lock SAREA also for drawables.
(II) intel(0): [drm] framebuffer mapped by ddx driver
(II) intel(0): [drm] added 1 reserved context for kernel
(II) intel(0): X context handle = 0x1
(II) intel(0): [drm] installed DRM signal handler
(==) intel(0): VideoRam: 131072 KB
(**) intel(0): Framebuffer compression enabled
(**) intel(0): Tiling enabled
(II) intel(0): Attempting memory allocation with tiled buffers.
(WW) intel(0): xf86AllocateGARTMemory: allocation of 1536 pages failed
    (Cannot allocate memory)
(WW) intel(0): Allocation error, framebuffer compression disabled
(WW) intel(0): xf86AllocateGARTMemory: allocation of 10 pages failed
    (Cannot allocate memory)
(WW) intel(0): Failed to allocate texture space.
(II) intel(0): Attempting memory allocation with untiled buffers.
(WW) intel(0): xf86AllocateGARTMemory: allocation of 10 pages failed
    (Cannot allocate memory)
(II) intel(0): Success.
(II) intel(0): [drm] Registers = 0xd0000000
(II) intel(0): [drm] ring buffer = 0xd8000000
(II) intel(0): [drm] mapped front buffer at 0xd8030000, handle = 0xd8030000
(II) intel(0): [drm] mapped back buffer at 0xd9e79000, handle = 0xd9e79000
(II) intel(0): [drm] mapped depth buffer at 0xda5fe000, handle = 0xda5fe000
(II) intel(0): [drm] mapped classic textures at 0xdad83000, handle = 0xdad83000
(II) intel(0): [drm] Initialized kernel agp heap manager, 33554432
(II) intel(0): [dri] visual configs initialized
(II) intel(0): Page Flipping disabled
(==) intel(0): Write-combining range (0xd8000000,0x8000000)
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(WW) intel(0): EXA greedy migration mode enabled.
(II) EXA(0): Forcing greedy migration option
(II) EXA(0): Offscreen pixmap area of 23654400 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): [DRI] installation complete
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x007df000 (pgoffset 2015)
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x007e0000 (pgoffset 2016)
(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x007e4000 (pgoffset 2020)
(II) intel(0): xf86BindGARTMemory: bind key 3 at 0x007e5000 (pgoffset 2021)
(II) intel(0): xf86BindGARTMemory: bind key 4 at 0x007e9000 (pgoffset 2025)
(II) intel(0): xf86BindGARTMemory: bind key 5 at 0x007ea000 (pgoffset 2026)
(II) intel(0): xf86BindGARTMemory: bind key 6 at 0x01e79000 (pgoffset 7801)
(II) intel(0): xf86BindGARTMemory: bind key 7 at 0x025fe000 (pgoffset 9726)
(II) intel(0): xf86BindGARTMemory: bind key 8 at 0x02d83000 (pgoffset 11651)
(II) intel(0): Fixed memory allocation layout:
(II) intel(0): 0x00000000-0x0001ffff: ring buffer (128 kB)
(II) intel(0): 0x00020000-0x00027fff: logical 3D context (32 kB)
(II) intel(0): 0x00030000-0x007b4fff: front buffer (7700 kB)
(II) intel(0): 0x007df000:            end of stolen memory
(II) intel(0): 0x007df000-0x007dffff: Core cursor (4 kB, 0x0000000010809000 physical
)
(II) intel(0): 0x007e0000-0x007e3fff: ARGB cursor (16 kB, 0x000000000ff68000 physical
)
(II) intel(0): 0x007e4000-0x007e4fff: Core cursor (4 kB, 0x000000000f809000 physical
)
(II) intel(0): 0x007e5000-0x007e8fff: ARGB cursor (16 kB, 0x000000001080c000 physical
)
(II) intel(0): 0x007e9000-0x007e9fff: overlay registers (4 kB, 0x000000000f802000 physical
)
(II) intel(0): 0x007ea000-0x01e78fff: exa offscreen (23100 kB)
(II) intel(0): 0x01e79000-0x025fdfff: back buffer (7700 kB)
(II) intel(0): 0x025fe000-0x02d82fff: depth buffer (7700 kB)
(II) intel(0): 0x02d83000-0x04d82fff: classic textures (32768 kB)
(II) intel(0): 0x08000000:            end of aperture
(WW) intel(0): Chosen PLL clock of 96.0 Mhz more than 2% away from desired 106.9 Mhz
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is off
(II) intel(0):   Display plane A is now disabled and connected to pipe A.
(II) intel(0):   Pipe B is on
(II) intel(0):   Display plane B is now enabled and connected to pipe B.
(II) intel(0):   Output VGA is connected to pipe none
(II) intel(0):   Output LVDS is connected to pipe B
(II) intel(0):   Output TMDS is connected to pipe none
(II) intel(0): [drm] dma control initialized, using IRQ 11
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) intel(0): DPMS enabled
(II) intel(0): Set up overlay video
(II) intel(0): direct rendering: Enabled
(--) RandR disabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) intel(0): Setting screen physical size to 370 x 277
Atom 4, CARD32 4, unsigned long 4
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event9
(**) Option "Device" "/dev/input/event9"
(**) Option "HorizEdgeScroll" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "pt"
(**) Generic Keyboard: XkbLayout: "pt"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) evaluating device (Synaptics Touchpad)
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event9
(**) Option "Device" "/dev/input/event9"
(--) Synaptics Touchpad touchpad found
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
SetClientVersion: 0 9
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) 3rd Button detected: disabling emulate3Button

```

---

### Post by Yellow Pasque on 2009-08-15
The warnings seem to be fixed in Jaunty, but I guess that doesn't help since you're running Hardy. Also, I'm not sure if those warnings are causing your problems.
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/304981](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/304981)

---

