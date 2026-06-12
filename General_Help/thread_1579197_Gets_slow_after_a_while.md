---
title: "Gets slow after a while"
date: 2010-09-21
forum: General Help
---

### Post by XPeter on 2010-09-21
When my computer have runned for some time (10-20 minutes maybe, not sure) it gets very sluggish and slow. It's like everything gets much slower to render. The fading effect when clicking Quit is like 2-3x slower. If I restart, everything gets as fast as it should but gets slow after a while like I told. It is not that it gets slower and slower. It is either normal or slow.

The problem started a few days ago and I don't think I have done anything special except automatic updates. I am using Ubuntu 8.04 (64bit).

I noticed now that all programs that uses OpenGL crashes. glxgears just shows an empty window for some seconds and then close with the text "Aborted". I don't really know what's causing the problem but I guess it has something to do with graphics stuff.

---

### Post by Soul-Sing on 2010-09-21
problem with X? videocard/graph. card too hot?
you could monitor your Xorg log, and event. copy/paste it here (on the forum)

---

### Post by XPeter on 2010-09-21
I add my Xorg log below (/var/log/Xorg.0.log)

This is what I did before I put the log here. I restarted the computer everything was fine. Turned off Compiz as I always do after startup and that have worked for years. I went out a couple of hours and now when I'm back, it's slow and here is the log:

```

This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at [http://bugs.freedesktop.org/](http://bugs.freedesktop.org/).
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See [http://wiki.x.org/wiki/GitPage](http://wiki.x.org/wiki/GitPage) for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.3)
Current Operating System: Linux peter-desktop 2.6.24-28-generic #1 SMP Thu Sep 16 14:18:43 UTC 2010 x86_64
Build Date: 07 May 2010  06:58:38AM
 
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Sep 21 21:04:48 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
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
(II) Loader magic: 0x7bd660
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
(II) PCI: 00:00:0: chip 1106,3188 card 1043,80a3 rev 01 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,b188 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:07:0: chip 1106,3044 card 1043,808a rev 80 class 0c,00,10 hdr 00
(II) PCI: 00:08:0: chip 105a,3373 card 1043,80f5 rev 02 class 01,04,00 hdr 00
(II) PCI: 00:0a:0: chip 11ab,4320 card 1043,811a rev 13 class 02,00,00 hdr 00
(II) PCI: 00:0d:0: chip 1814,0302 card 1186,3c09 rev 00 class 02,80,00 hdr 00
(II) PCI: 00:0f:0: chip 1106,3149 card 1043,80ed rev 80 class 01,04,00 hdr 80
(II) PCI: 00:0f:1: chip 1106,0571 card 1043,80ed rev 06 class 01,01,8a hdr 00
(II) PCI: 00:10:0: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:1: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:2: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:3: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:4: chip 1106,3104 card 1043,80ed rev 86 class 0c,03,20 hdr 80
(II) PCI: 00:11:0: chip 1106,3227 card 1043,80ed rev 00 class 06,01,00 hdr 80
(II) PCI: 00:11:5: chip 1106,3059 card 1043,80b0 rev 60 class 04,01,00 hdr 00
(II) PCI: 00:11:6: chip 1106,3068 card 0000,0000 rev 80 class 07,80,00 hdr 00
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 10de,0332 card 0000,0000 rev a1 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
    [0] -1    0    0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
    [0] -1    0    0xf4f00000 - 0xf70fffff (0x2200000) MX[B]
(II) Bus 1 prefetchable memory range:
    [0] -1    0    0xe4e00000 - 0xf4dfffff (0x10000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV35 [GeForce FX 5900XT] rev 161, Mem @ 0xf6000000/24, 0xe8000000/27, BIOS @ 0xf7000000/17
(II) Addressable bus resource ranges are
    [0] -1    0    0x00000000 - 0xffffffff (0x100000000) MX[B]
    [1] -1    0    0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xf8000000 from 0xf8000000 to 0xf7ffffff
(II) Active PCI resource ranges:
    [0] -1    0    0xf7f00000 - 0xf7f000ff (0x100) MX[B]
    [1] -1    0    0xf7e00000 - 0xf7e07fff (0x8000) MX[B]
    [2] -1    0    0xf7d00000 - 0xf7d03fff (0x4000) MX[B]
    [3] -1    0    0xf7a00000 - 0xf7a1ffff (0x20000) MX[B]
    [4] -1    0    0xf7b00000 - 0xf7b00fff (0x1000) MX[B]
    [5] -1    0    0xf7900000 - 0xf79007ff (0x800) MX[B]
    [6] -1    0    0xf8000000 - 0xf7ffffff (0x0) MX[B]O
    [7] -1    0    0xf7000000 - 0xf701ffff (0x20000) MX[B](B)
    [8] -1    0    0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
    [9] -1    0    0xf6000000 - 0xf6ffffff (0x1000000) MX[B](B)
    [10] -1    0    0x00001000 - 0x000010ff (0x100) IX[B]
    [11] -1    0    0x0000c800 - 0x0000c8ff (0x100) IX[B]
    [12] -1    0    0x0000c400 - 0x0000c41f (0x20) IX[B]
    [13] -1    0    0x0000c000 - 0x0000c01f (0x20) IX[B]
    [14] -1    0    0x0000b800 - 0x0000b81f (0x20) IX[B]
    [15] -1    0    0x0000b400 - 0x0000b41f (0x20) IX[B]
    [16] -1    0    0x0000fc00 - 0x0000fc0f (0x10) IX[B]
    [17] -1    0    0x0000d000 - 0x0000d0ff (0x100) IX[B]
    [18] -1    0    0x0000d400 - 0x0000d40f (0x10) IX[B]
    [19] -1    0    0x0000d800 - 0x0000d803 (0x4) IX[B]
    [20] -1    0    0x0000e000 - 0x0000e007 (0x8) IX[B]
    [21] -1    0    0x0000e400 - 0x0000e403 (0x4) IX[B]
    [22] -1    0    0x0000e800 - 0x0000e807 (0x8) IX[B]
    [23] -1    0    0x0000b000 - 0x0000b0ff (0x100) IX[B]
    [24] -1    0    0x0000cc00 - 0x0000cc7f (0x80) IX[B]
    [25] -1    0    0x0000dc00 - 0x0000dc0f (0x10) IX[B]
    [26] -1    0    0x0000ec00 - 0x0000ec3f (0x40) IX[B]
    [27] -1    0    0x0000bc00 - 0x0000bc7f (0x80) IX[B]
(II) Active PCI resource ranges after removing overlaps:
    [0] -1    0    0xf7f00000 - 0xf7f000ff (0x100) MX[B]
    [1] -1    0    0xf7e00000 - 0xf7e07fff (0x8000) MX[B]
    [2] -1    0    0xf7d00000 - 0xf7d03fff (0x4000) MX[B]
    [3] -1    0    0xf7a00000 - 0xf7a1ffff (0x20000) MX[B]
    [4] -1    0    0xf7b00000 - 0xf7b00fff (0x1000) MX[B]
    [5] -1    0    0xf7900000 - 0xf79007ff (0x800) MX[B]
    [6] -1    0    0xf8000000 - 0xf7ffffff (0x0) MX[B]O
    [7] -1    0    0xf7000000 - 0xf701ffff (0x20000) MX[B](B)
    [8] -1    0    0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
    [9] -1    0    0xf6000000 - 0xf6ffffff (0x1000000) MX[B](B)
    [10] -1    0    0x00001000 - 0x000010ff (0x100) IX[B]
    [11] -1    0    0x0000c800 - 0x0000c8ff (0x100) IX[B]
    [12] -1    0    0x0000c400 - 0x0000c41f (0x20) IX[B]
    [13] -1    0    0x0000c000 - 0x0000c01f (0x20) IX[B]
    [14] -1    0    0x0000b800 - 0x0000b81f (0x20) IX[B]
    [15] -1    0    0x0000b400 - 0x0000b41f (0x20) IX[B]
    [16] -1    0    0x0000fc00 - 0x0000fc0f (0x10) IX[B]
    [17] -1    0    0x0000d000 - 0x0000d0ff (0x100) IX[B]
    [18] -1    0    0x0000d400 - 0x0000d40f (0x10) IX[B]
    [19] -1    0    0x0000d800 - 0x0000d803 (0x4) IX[B]
    [20] -1    0    0x0000e000 - 0x0000e007 (0x8) IX[B]
    [21] -1    0    0x0000e400 - 0x0000e403 (0x4) IX[B]
    [22] -1    0    0x0000e800 - 0x0000e807 (0x8) IX[B]
    [23] -1    0    0x0000b000 - 0x0000b0ff (0x100) IX[B]
    [24] -1    0    0x0000cc00 - 0x0000cc7f (0x80) IX[B]
    [25] -1    0    0x0000dc00 - 0x0000dc0f (0x10) IX[B]
    [26] -1    0    0x0000ec00 - 0x0000ec3f (0x40) IX[B]
    [27] -1    0    0x0000bc00 - 0x0000bc7f (0x80) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0xf7f00000 - 0xf7f000ff (0x100) MX[B]
    [5] -1    0    0xf7e00000 - 0xf7e07fff (0x8000) MX[B]
    [6] -1    0    0xf7d00000 - 0xf7d03fff (0x4000) MX[B]
    [7] -1    0    0xf7a00000 - 0xf7a1ffff (0x20000) MX[B]
    [8] -1    0    0xf7b00000 - 0xf7b00fff (0x1000) MX[B]
    [9] -1    0    0xf7900000 - 0xf79007ff (0x800) MX[B]
    [10] -1    0    0xf8000000 - 0xf7ffffff (0x0) MX[B]O
    [11] -1    0    0xf7000000 - 0xf701ffff (0x20000) MX[B](B)
    [12] -1    0    0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
    [13] -1    0    0xf6000000 - 0xf6ffffff (0x1000000) MX[B](B)
    [14] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [15] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
    [16] -1    0    0x00001000 - 0x000010ff (0x100) IX[B]
    [17] -1    0    0x0000c800 - 0x0000c8ff (0x100) IX[B]
    [18] -1    0    0x0000c400 - 0x0000c41f (0x20) IX[B]
    [19] -1    0    0x0000c000 - 0x0000c01f (0x20) IX[B]
    [20] -1    0    0x0000b800 - 0x0000b81f (0x20) IX[B]
    [21] -1    0    0x0000b400 - 0x0000b41f (0x20) IX[B]
    [22] -1    0    0x0000fc00 - 0x0000fc0f (0x10) IX[B]
    [23] -1    0    0x0000d000 - 0x0000d0ff (0x100) IX[B]
    [24] -1    0    0x0000d400 - 0x0000d40f (0x10) IX[B]
    [25] -1    0    0x0000d800 - 0x0000d803 (0x4) IX[B]
    [26] -1    0    0x0000e000 - 0x0000e007 (0x8) IX[B]
    [27] -1    0    0x0000e400 - 0x0000e403 (0x4) IX[B]
    [28] -1    0    0x0000e800 - 0x0000e807 (0x8) IX[B]
    [29] -1    0    0x0000b000 - 0x0000b0ff (0x100) IX[B]
    [30] -1    0    0x0000cc00 - 0x0000cc7f (0x80) IX[B]
    [31] -1    0    0x0000dc00 - 0x0000dc0f (0x10) IX[B]
    [32] -1    0    0x0000ec00 - 0x0000ec3f (0x40) IX[B]
    [33] -1    0    0x0000bc00 - 0x0000bc7f (0x80) IX[B]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  169.12  Thu Feb 14 18:34:02 PST 2008
(II) Loading extension GLX
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
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
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
(II) NVIDIA dlloader X Driver  169.12  Thu Feb 14 17:53:48 PST 2008
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) resource ranges after xf86ClaimFixedResources() call:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0xf7f00000 - 0xf7f000ff (0x100) MX[B]
    [5] -1    0    0xf7e00000 - 0xf7e07fff (0x8000) MX[B]
    [6] -1    0    0xf7d00000 - 0xf7d03fff (0x4000) MX[B]
    [7] -1    0    0xf7a00000 - 0xf7a1ffff (0x20000) MX[B]
    [8] -1    0    0xf7b00000 - 0xf7b00fff (0x1000) MX[B]
    [9] -1    0    0xf7900000 - 0xf79007ff (0x800) MX[B]
    [10] -1    0    0xf8000000 - 0xf7ffffff (0x0) MX[B]O
    [11] -1    0    0xf7000000 - 0xf701ffff (0x20000) MX[B](B)
    [12] -1    0    0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
    [13] -1    0    0xf6000000 - 0xf6ffffff (0x1000000) MX[B](B)
    [14] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [15] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
    [16] -1    0    0x00001000 - 0x000010ff (0x100) IX[B]
    [17] -1    0    0x0000c800 - 0x0000c8ff (0x100) IX[B]
    [18] -1    0    0x0000c400 - 0x0000c41f (0x20) IX[B]
    [19] -1    0    0x0000c000 - 0x0000c01f (0x20) IX[B]
    [20] -1    0    0x0000b800 - 0x0000b81f (0x20) IX[B]
    [21] -1    0    0x0000b400 - 0x0000b41f (0x20) IX[B]
    [22] -1    0    0x0000fc00 - 0x0000fc0f (0x10) IX[B]
    [23] -1    0    0x0000d000 - 0x0000d0ff (0x100) IX[B]
    [24] -1    0    0x0000d400 - 0x0000d40f (0x10) IX[B]
    [25] -1    0    0x0000d800 - 0x0000d803 (0x4) IX[B]
    [26] -1    0    0x0000e000 - 0x0000e007 (0x8) IX[B]
    [27] -1    0    0x0000e400 - 0x0000e403 (0x4) IX[B]
    [28] -1    0    0x0000e800 - 0x0000e807 (0x8) IX[B]
    [29] -1    0    0x0000b000 - 0x0000b0ff (0x100) IX[B]
    [30] -1    0    0x0000cc00 - 0x0000cc7f (0x80) IX[B]
    [31] -1    0    0x0000dc00 - 0x0000dc0f (0x10) IX[B]
    [32] -1    0    0x0000ec00 - 0x0000ec3f (0x40) IX[B]
    [33] -1    0    0x0000bc00 - 0x0000bc7f (0x80) IX[B]
(II) resource ranges after probing:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0xf7f00000 - 0xf7f000ff (0x100) MX[B]
    [5] -1    0    0xf7e00000 - 0xf7e07fff (0x8000) MX[B]
    [6] -1    0    0xf7d00000 - 0xf7d03fff (0x4000) MX[B]
    [7] -1    0    0xf7a00000 - 0xf7a1ffff (0x20000) MX[B]
    [8] -1    0    0xf7b00000 - 0xf7b00fff (0x1000) MX[B]
    [9] -1    0    0xf7900000 - 0xf79007ff (0x800) MX[B]
    [10] -1    0    0xf8000000 - 0xf7ffffff (0x0) MX[B]O
    [11] -1    0    0xf7000000 - 0xf701ffff (0x20000) MX[B](B)
    [12] -1    0    0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
    [13] -1    0    0xf6000000 - 0xf6ffffff (0x1000000) MX[B](B)
    [14] 0    0    0x000a0000 - 0x000affff (0x10000) MS[B]
    [15] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[B]
    [16] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[B]
    [17] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [18] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
    [19] -1    0    0x00001000 - 0x000010ff (0x100) IX[B]
    [20] -1    0    0x0000c800 - 0x0000c8ff (0x100) IX[B]
    [21] -1    0    0x0000c400 - 0x0000c41f (0x20) IX[B]
    [22] -1    0    0x0000c000 - 0x0000c01f (0x20) IX[B]
    [23] -1    0    0x0000b800 - 0x0000b81f (0x20) IX[B]
    [24] -1    0    0x0000b400 - 0x0000b41f (0x20) IX[B]
    [25] -1    0    0x0000fc00 - 0x0000fc0f (0x10) IX[B]
    [26] -1    0    0x0000d000 - 0x0000d0ff (0x100) IX[B]
    [27] -1    0    0x0000d400 - 0x0000d40f (0x10) IX[B]
    [28] -1    0    0x0000d800 - 0x0000d803 (0x4) IX[B]
    [29] -1    0    0x0000e000 - 0x0000e007 (0x8) IX[B]
    [30] -1    0    0x0000e400 - 0x0000e403 (0x4) IX[B]
    [31] -1    0    0x0000e800 - 0x0000e807 (0x8) IX[B]
    [32] -1    0    0x0000b000 - 0x0000b0ff (0x100) IX[B]
    [33] -1    0    0x0000cc00 - 0x0000cc7f (0x80) IX[B]
    [34] -1    0    0x0000dc00 - 0x0000dc0f (0x10) IX[B]
    [35] -1    0    0x0000ec00 - 0x0000ec3f (0x40) IX[B]
    [36] -1    0    0x0000bc00 - 0x0000bc7f (0x80) IX[B]
    [37] 0    0    0x000003b0 - 0x000003bb (0xc) IS[B]
    [38] 0    0    0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce FX 5900XT (NV35) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 04.35.20.32.00
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce FX 5900XT at
(--) NVIDIA(0):     PCI:1:0:0:
(--) NVIDIA(0):     STN SAMTRON (CRT-0)
(--) NVIDIA(0): STN SAMTRON (CRT-0): 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(==) NVIDIA(0): 
(==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) NVIDIA(0):     will be used as the requested mode.
(==) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(--) NVIDIA(0): DPI set to (92, 100); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0xf7f00000 - 0xf7f000ff (0x100) MX[B]
    [5] -1    0    0xf7e00000 - 0xf7e07fff (0x8000) MX[B]
    [6] -1    0    0xf7d00000 - 0xf7d03fff (0x4000) MX[B]
    [7] -1    0    0xf7a00000 - 0xf7a1ffff (0x20000) MX[B]
    [8] -1    0    0xf7b00000 - 0xf7b00fff (0x1000) MX[B]
    [9] -1    0    0xf7900000 - 0xf79007ff (0x800) MX[B]
    [10] -1    0    0xf8000000 - 0xf7ffffff (0x0) MX[B]O
    [11] -1    0    0xf7000000 - 0xf701ffff (0x20000) MX[B](B)
    [12] -1    0    0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
    [13] -1    0    0xf6000000 - 0xf6ffffff (0x1000000) MX[B](B)
    [14] 0    0    0x000a0000 - 0x000affff (0x10000) MS[B]
    [15] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[B]
    [16] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[B]
    [17] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [18] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
    [19] -1    0    0x00001000 - 0x000010ff (0x100) IX[B]
    [20] -1    0    0x0000c800 - 0x0000c8ff (0x100) IX[B]
    [21] -1    0    0x0000c400 - 0x0000c41f (0x20) IX[B]
    [22] -1    0    0x0000c000 - 0x0000c01f (0x20) IX[B]
    [23] -1    0    0x0000b800 - 0x0000b81f (0x20) IX[B]
    [24] -1    0    0x0000b400 - 0x0000b41f (0x20) IX[B]
    [25] -1    0    0x0000fc00 - 0x0000fc0f (0x10) IX[B]
    [26] -1    0    0x0000d000 - 0x0000d0ff (0x100) IX[B]
    [27] -1    0    0x0000d400 - 0x0000d40f (0x10) IX[B]
    [28] -1    0    0x0000d800 - 0x0000d803 (0x4) IX[B]
    [29] -1    0    0x0000e000 - 0x0000e007 (0x8) IX[B]
    [30] -1    0    0x0000e400 - 0x0000e403 (0x4) IX[B]
    [31] -1    0    0x0000e800 - 0x0000e807 (0x8) IX[B]
    [32] -1    0    0x0000b000 - 0x0000b0ff (0x100) IX[B]
    [33] -1    0    0x0000cc00 - 0x0000cc7f (0x80) IX[B]
    [34] -1    0    0x0000dc00 - 0x0000dc0f (0x10) IX[B]
    [35] -1    0    0x0000ec00 - 0x0000ec3f (0x40) IX[B]
    [36] -1    0    0x0000bc00 - 0x0000bc7f (0x80) IX[B]
    [37] 0    0    0x000003b0 - 0x000003bb (0xc) IS[B]
    [38] 0    0    0x000003c0 - 0x000003df (0x20) IS[B]
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Setting vga for screen 0.
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
(II) Initializing extension GLX
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
(**) Option "XkbLayout" "se"
(**) Generic Keyboard: XkbLayout: "se"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
SetClientVersion: 0 9
SetGrabKeysState - disabled
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Initialized AGP GART.
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Initialized AGP GART.
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
SetGrabKeysState - enabled
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Initialized AGP GART.
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Initialized AGP GART.
(WW) NVIDIA(0): The NVIDIA X driver has encountered too many errors.  Falling
(WW) NVIDIA(0):     back to legacy PCI mode.
(II) NVIDIA(0): Initialized AGP GART.
```

---

### Post by Soul-Sing on 2010-09-22
thx, the  > The NVIDIA X driver has encountered too many errors.  Falling
(WW) NVIDIA(0):     back to legacy PCI mode.
says it all, but I don't know whats going wrong here
An idea is to try another nvidia driver....(but i do not expect a miracle)

---

### Post by XPeter on 2010-10-01
Today I opened up my computer and cleaned inside. After removing some stuff from the graphics card I found a lot of dust around the fan. It must have been impossible for the air to pass that thick layer of dust. So I guess it could have been the problem (like leoquant mentioned). I haven't used the computer much after this so I don't know yet if the problem is gone but I am optimistic :)

---

### Post by Soul-Sing on 2010-10-01
Dust is THE hardware killer...

---

