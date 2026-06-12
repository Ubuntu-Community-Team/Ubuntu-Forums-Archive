---
title: "hard xorg problem"
date: 2010-10-14
forum: General Help
---

### Post by night_fox on 2010-10-14
My Xorg has failed. On startup, ubuntu tells me this, and tries to boot in low graphics mode. This also fails. At first I find no /etc/X11/xorg.conf. When I drop to the command line and run the command

> sudo dpkg-reconfigure -phigh xserver-xorg

then do startx, X works but when I reboot it fails again.

Here are two of my Xorg.logs:

Xorg.1.log

> X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux john-laptop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686
Kernel command line: root=UUID=00b193ba-eed8-49e2-a9dc-0369b710212b ro quiet splash
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Tue Dec  8 16:42:42 2009
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
        X.Org ANSI C Emulation: 0.4
        X.Org Video Driver: 5.0
        X.Org XInput driver : 4.0
        X.Org Server Extension : 2.0
(II) Loader running on linux
(--) using VT number 7

(--) PCI:*(0:0:2:0) 8086:27a2:1028:01bd Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller rev 3, Mem @ 0xeff00000/524288, 0xd0000000/268435456, 0xefec0000/262144, I/O @ 0x0000eff8/8
(==) Using default built-in configuration (39 lines)
(==) --- Start of built-in configuration ---
        Section "Device"
                Identifier      "Builtin Default intel Device 0"
                Driver  "intel"
        EndSection
        Section "Screen"
                Identifier      "Builtin Default intel Screen 0"
                Device  "Builtin Default intel Device 0"
        EndSection
        Section "Device"
                Identifier      "Builtin Default i810 Device 0"
                Driver  "i810"
        EndSection
        Section "Screen"
                Identifier      "Builtin Default i810 Screen 0"
                Device  "Builtin Default i810 Device 0"
        EndSection
        Section "Device"
                Identifier      "Builtin Default vesa Device 0"
                Driver  "vesa"
        EndSection
        Section "Screen"
                Identifier      "Builtin Default vesa Screen 0"
                Device  "Builtin Default vesa Device 0"
        EndSection
        Section "Device"
                Identifier      "Builtin Default fbdev Device 0"
                Driver  "fbdev"
        EndSection
        Section "Screen"
                Identifier      "Builtin Default fbdev Screen 0"
                Device  "Builtin Default fbdev Device 0"
        EndSection
        Section "ServerLayout"
                Identifier      "Builtin Default Layout"
                Screen  "Builtin Default intel Screen 0"
                Screen  "Builtin Default i810 Screen 0"
                Screen  "Builtin Default vesa Screen 0"
                Screen  "Builtin Default fbdev Screen 0"
        EndSection
(==) --- End of built-in configuration ---
(==) ServerLayout "Builtin Default Layout"
(**) |-->Screen "Builtin Default intel Screen 0" (0)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default intel Device 0"
(==) No monitor specified for screen "Builtin Default intel Screen 0".
        Using a default monitor configuration.
(**) |-->Screen "Builtin Default i810 Screen 0" (1)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default i810 Device 0"
(==) No monitor specified for screen "Builtin Default i810 Screen 0".
        Using a default monitor configuration.
(**) |-->Screen "Builtin Default vesa Screen 0" (2)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default vesa Device 0"
(==) No monitor specified for screen "Builtin Default vesa Screen 0".
        Using a default monitor configuration.
(**) |-->Screen "Builtin Default fbdev Screen 0" (3)
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
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x00000000 (0x1) IX[B]
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
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
        compiled for 1.6.4, module version = 2.9.0
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "i810"
(WW) Warning, couldn't open module i810
(II) UnloadModule: "i810"
(EE) Failed to load module "i810" (module does not exist, 0)
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
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
        i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
        E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
        965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
        4 Series, G45/G43, Q45/Q43, G41, B43, Clarkdale, Arrandale
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 00@00:02:0
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux//libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
        compiled for 1.6.4, module version = 0.0.2
        ABI class: X.Org Video Driver, version 5.0
(II) resource ranges after probing:
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x00000000 (0x1) IX[B]
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) intel(0): Creating default Display subsection in Screen section
        "Builtin Default intel Screen 0" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 945GM
(--) intel(0): Chipset: "945GM"
(II) intel(0): Output VGA1 has no monitor section
(II) intel(0): Output LVDS1 has no monitor section
(II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
(II) intel(0): Output TV1 has no monitor section
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: SEC  Model: 0  Serial#: 0
(II) intel(0): Year: 2006  Week: 0
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) intel(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 71.1 MHz   Image Size:  331 x 207 mm
(II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) intel(0): v_active: 800  v_sync: 802  v_sync_end 808 v_blanking: 823 v_border: 0
(WW) intel(0): Unknown vendor-specific block f
(II) intel(0):  DD282^D154X3
(II) intel(0):  '@PZ<81><B0><D9><FF>^A^A
(II) intel(0): EDID (in hex):
(II) intel(0):  00ffffffffffff004ca3000000000000
(II) intel(0):  00100103802115780a87f594574f8c27
(II) intel(0):  27505400000001010101010101010101
(II) intel(0):  010101010101c71b00a0502017303020
(II) intel(0):  26004bcf100000190000000f00000000
(II) intel(0):  00000000002387026400000000fe0044
(II) intel(0):  443238320431353458330a20000000fe
(II) intel(0):  002740505a81b0d9ff01010a2020009d
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1360x768" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1440x900" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1280x800"x60.0   71.11  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (49.4 kHz)
(II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) intel(0): EDID for output TV1
(II) intel(0): Output VGA1 disconnected
(II) intel(0): Output LVDS1 connected
(II) intel(0): Output TV1 disconnected
(II) intel(0): Using exact sizes for initial modes
(II) intel(0): Output LVDS1 using initial mode 1280x800
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(==) intel(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
        compiled for 1.6.4, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.4
(II) UnloadModule: "vesa"
(II) Unloading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers//fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux//libfbdevhw.so
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x00000000 (0x1) IX[B]
(II) intel(0): [DRI2] Setup complete
(**) intel(0): Kernel mode setting active, disabling FBC.
(**) intel(0): Framebuffer compression disabled
(**) intel(0): Tiling enabled
(**) intel(0): SwapBuffers wait enabled
(==) intel(0): VideoRam: 262144 KB
(II) intel(0): Attempting memory allocation with tiled buffers.
(II) intel(0): Tiled allocation successful.
(II) UXA(0): Driver registered support for the following operations:
(II)         solid
(II)         copy
(II)         composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): No memory allocations
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) intel(0): DPMS enabled
(==) intel(0): Intel XvMC decoder disabled
(II) intel(0): Set up textured video
(II) intel(0): direct rendering: DRI2 Enabled
(--) RandR disabled
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
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
(II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
(II) GLX: Initialized DRI2 GL provider for screen 0
(II) intel(0): Setting screen physical size to 331 x 207
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
(**) Option "xkb_layout" "gb"
(II) config/hal: Adding input device Video Bus
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event5"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "gb"
(II) config/hal: Adding input device Sleep Button
(**) Sleep Button: always reports core events
(**) Sleep Button: Device: "/dev/input/event2"
(II) Sleep Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "gb"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "gb"
(II) config/hal: Adding input device Video Bus
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event6"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "gb"
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "gb"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
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
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: SEC  Model: 0  Serial#: 0
(II) intel(0): Year: 2006  Week: 0
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) intel(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 71.1 MHz   Image Size:  331 x 207 mm
(II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) intel(0): v_active: 800  v_sync: 802  v_sync_end 808 v_blanking: 823 v_border: 0
(WW) intel(0): Unknown vendor-specific block f
(II) intel(0):  DD282^D154X3
(II) intel(0):  '@PZ<81><B0><D9><FF>^A^A


And it repeats......
There are some random characters in there which gedit dislikes.

Here is Xorg.failsafe.log:


> X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux john-laptop 2.6.32-25-generic #44-Ubuntu SMP Fri Sep 17 20:26:08 UTC 2010 i686
Kernel command line: root=UUID=00b193ba-eed8-49e2-a9dc-0369b710212b ro quiet splash  crashkernel=384M-2G:64M,2G-:128M
Build Date: 21 July 2010  12:47:34PM
xorg-server 2:1.7.6-2ubuntu7.3 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.16.4
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(++) Log file: "/var/log/Xorg.failsafe.log", Time: Thu Oct 14 23:13:02 2010
(++) Using config file: "/etc/X11/xorg.conf.failsafe"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
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
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x81f0e80
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(--) using VT number 1

(--) PCI:*(0:0:2:0) 8086:27a2:1028:01bd Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller rev 3, Mem @ 0xeff00000/524288, 0xd0000000/268435456, 0xefec0000/262144, I/O @ 0x0000eff8/8
(--) PCI: (0:0:2:1) 8086:27a6:1028:01bd Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller rev 3, Mem @ 0xeff80000/524288
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.4.1
	ABI class: X.Org Video Driver, version 6.0
(II) FBDEV: driver for framebuffer: fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.0.2
	ABI class: X.Org Video Driver, version 6.0
(**) FBDEV(0): claimed PCI slot 0@0:2:0
(II) FBDEV(0): using default device
(II) FBDEV(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
(==) FBDEV(0): RGB weight 888
(==) FBDEV(0): Default visual is TrueColor
(==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) FBDEV(0): hardware: inteldrmfb (video memory: 4000kB)
(II) FBDEV(0): checking modes against framebuffer device...
(II) FBDEV(0): checking modes against monitor...
(--) FBDEV(0): Virtual size is 1280x800 (pitch 1280)
(**) FBDEV(0):  Built-in mode "current"
(==) FBDEV(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(**) FBDEV(0): using shadow framebuffer
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules/libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(==) Depth 24 pixmap format is 32 bpp
(==) FBDEV(0): Backing store disabled
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
....
....
.... loads of these errors
....
....
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(==) FBDEV(0): DPMS enabled
(==) RandR enabled
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
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Video Bus (/dev/input/event5)
(**) Video Bus: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event5"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "gb"
(II) XKB: reuse xkmfile /var/lib/xkb/server-2B4266AA55228AE7D9557A18F1965DBA19850816.xkm
(II) config/udev: Adding input device Video Bus (/dev/input/event6)
(**) Video Bus: Applying InputClass "evdev keyboard catchall"
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event6"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "gb"
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "gb"
(II) config/udev: Adding input device Lid Switch (/dev/input/event0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Sleep Button (/dev/input/event2)
(**) Sleep Button: Applying InputClass "evdev keyboard catchall"
(**) Sleep Button: always reports core events
(**) Sleep Button: Device: "/dev/input/event2"
(II) Sleep Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "gb"
(II) config/udev: Adding input device HDA Intel HP Out at Ext Right Jack (/dev/input/event10)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Intel Mic at Ext Right Jack (/dev/input/event9)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "gb"
(II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event7)
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(II) Synaptics touchpad driver version 1.2.2
(**) Option "Device" "/dev/input/event7"
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
(II) SynPS/2 Synaptics TouchPad: buttons: left right middle double triple
(--) SynPS/2 Synaptics TouchPad: touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
(--) SynPS/2 Synaptics TouchPad: touchpad found
(II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event3)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event8)
(**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
(**) Dell WMI hotkeys: always reports core events
(**) Dell WMI hotkeys: Device: "/dev/input/event8"
(II) Dell WMI hotkeys: Found keys
(II) Dell WMI hotkeys: Configuring as keyboard
(II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "gb"
(II) Dell WMI hotkeys: Close
(II) UnloadModule: "evdev"
(II) Macintosh mouse button emulation: Close
(II) UnloadModule: "evdev"
(II) UnloadModule: "synaptics"
(II) AT Translated Set 2 keyboard: Close
(II) UnloadModule: "evdev"
(II) Sleep Button: Close
(II) UnloadModule: "evdev"
(II) Power Button: Close
(II) UnloadModule: "evdev"
(II) Video Bus: Close
(II) UnloadModule: "evdev"
(II) Video Bus: Close
(II) UnloadModule: "evdev"
 ddxSigGiveUp: Closing log

Can someone please help me understand what's going on and fix it? Please?
:confused:

---

### Post by night_fox on 2010-10-15
Bump

---

### Post by night_fox on 2010-10-15
It wouldn't let me put edit this into the previous post, so apologies for bumping again.

I'm trying everything it says on here:

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1484137](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1484137)

---

### Post by night_fox on 2010-10-15
None of that worked. I'm upgrading to Maverick

---

### Post by night_fox on 2010-10-15
After upgrading to Maverick, my xserver is still broken. Please could someone help me fix this?

---

### Post by Toz on 2010-10-15
From your first log file, there is:

(EE) Failed to load module "i810" (module does not exist, 0)

When I search the repositories for i810, I get:

i810switch - Enables/disables video output to CRT/LCD on i810 video hardware
xserver-xorg-video-intel-dbg - X.Org X server -- Intel i8xx, i9xx display driver (debug symbols)
xserver-xorg-video-intel - X.Org X server -- Intel i8xx, i9xx display driver

So the easy question is, do you have xserver-xorg-video-intel installed? You can check quickly by opening a terminal window and typing in:

apt-cache policy xserver-xorg-video-intel

---

### Post by AlphaLexman on 2010-10-15
Take a look at:
```
man dexconf
```

---

### Post by night_fox on 2010-10-15
Thanks very much, Toz and AlphaLexman, for replying to my post.

Amazingly, I didn't have xserver-xorg-video-intel installed, but now I do. Installing that didn't fix my problem.

I tried using dexconf. It didn't generate a new xorg.conf as it said in the man page, nor did it output anything when I used the -o option. I found a file xorg.conf.new in /

Here is it's contents:
> Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "glx"
	Load  "extmod"
	Load  "record"
	Load  "dri2"
	Load  "dbe"
	Load  "dri"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "ColorKey"           	# <i>
        #Option     "CacheLines"         	# <i>
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "DRI"                	# [<bool>]
        #Option     "NoDDC"              	# [<bool>]
        #Option     "ShowCache"          	# [<bool>]
        #Option     "XvMCSurfaces"       	# <i>
        #Option     "PageFlip"           	# [<bool>]
	Identifier  "Card0"
	Driver      "intel"
	VendorName  "Intel Corporation"
	BoardName   "Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
	BusID       "PCI:0:2:0"
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

Using that as xorg.conf didn't fix the problem either.

I can't see that any of my Xorg.log.x have changed.

Any other ideas would be more than welcome. This is just sooooooo annoying

---

### Post by Ayuthia on 2010-10-15
Does the i810 error message still appear?  If not, can you post an updated copy of your Xorg.0.log?

---

### Post by Ayuthia on 2010-10-15
You might check this [link]("https://bugs.launchpad.net/ubuntu/maverick/+source/xserver-xorg-video-intel/+bug/633593") also.  It suggests i915.modeset=1 in the kernel parameters.  You might also move your xorg.conf file somewhere else to test also.  Maverick should not need an xorg.conf file.  See post #6 in that link to add it to grub.

---

### Post by night_fox on 2010-10-15
> X.Org X Server 1.9.0
Release Date: 2010-08-20
[   226.893] X Protocol Version 11, Revision 0
[   226.895] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[   226.896] Current Operating System: Linux john-laptop 2.6.35-22-generic #34-Ubuntu SMP Sun Oct 10 09:24:00 UTC 2010 i686
[   226.897] Kernel command line: root=UUID=00b193ba-eed8-49e2-a9dc-0369b710212b ro quiet splash  crashkernel=384M-2G:64M,2G-:128M
[   226.899] Build Date: 16 September 2010  05:39:22PM
[   226.900] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[   226.902] Current version of pixman: 0.18.4
[   226.903]    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
[   226.906] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   226.911] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Oct 15 17:46:10 2010
[   226.913] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   226.915] (==) No Layout section.  Using the first Screen section.
[   226.915] (==) No screen section available. Using defaults.
[   226.915] (**) |-->Screen "Default Screen Section" (0)
[   226.915] (**) |   |-->Monitor "<default monitor>"
[   226.915] (==) No monitor specified for screen "Default Screen Section".
        Using a default monitor configuration.
[   226.915] (==) Automatically adding devices
[   226.915] (==) Automatically enabling devices
[   226.916] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   226.916]    Entry deleted from font path.
[   226.916] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/100dpi/:unscaled,
        /usr/share/fonts/X11/75dpi/:unscaled,
        /usr/share/fonts/X11/Type1,
        /usr/share/fonts/X11/100dpi,
        /usr/share/fonts/X11/75dpi,
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
        built-ins
[   226.916] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   226.916] (II) The server relies on udev to provide the list of input devices.
        If no devices become available, reconfigure udev or disable AutoAddDevices.
[   226.916] (II) Loader magic: 0x81f8e00
[   226.916] (II) Module ABI versions:
[   226.916]    X.Org ANSI C Emulation: 0.4
[   226.916]    X.Org Video Driver: 8.0
[   226.916]    X.Org XInput driver : 11.0
[   226.916]    X.Org Server Extension : 4.0
[   226.917] (--) PCI:*(0:0:2:0) 8086:27a2:1028:01bd rev 3, Mem @ 0xeff00000/524288, 0xd0000000/268435456, 0xefec0000/262144, I/O @ 0x0000eff8/8
[   226.917] (--) PCI: (0:0:2:1) 8086:27a6:1028:01bd rev 3, Mem @ 0xeff80000/524288
[   226.917] (II) Open ACPI successful (/var/run/acpid.socket)
[   226.917] (II) LoadModule: "extmod"
[   226.918] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   226.918] (II) Module extmod: vendor="X.Org Foundation"
[   226.918]    compiled for 1.9.0, module version = 1.0.0
[   226.918]    Module class: X.Org Server Extension
[   226.918]    ABI class: X.Org Server Extension, version 4.0
[   226.918] (II) Loading extension MIT-SCREEN-SAVER
[   226.918] (II) Loading extension XFree86-VidModeExtension
[   226.918] (II) Loading extension XFree86-DGA
[   226.918] (II) Loading extension DPMS
[   226.918] (II) Loading extension XVideo
[   226.918] (II) Loading extension XVideo-MotionCompensation
[   226.918] (II) Loading extension X-Resource
[   226.918] (II) LoadModule: "dbe"
[   226.919] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   226.919] (II) Module dbe: vendor="X.Org Foundation"
[   226.919]    compiled for 1.9.0, module version = 1.0.0
[   226.919]    Module class: X.Org Server Extension
[   226.919]    ABI class: X.Org Server Extension, version 4.0
[   226.919] (II) Loading extension DOUBLE-BUFFER
[   226.919] (II) LoadModule: "glx"
[   226.920] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   226.920] (II) Module glx: vendor="X.Org Foundation"
[   226.920]    compiled for 1.9.0, module version = 1.0.0
[   226.920]    ABI class: X.Org Server Extension, version 4.0
[   226.920] (==) AIGLX enabled
[   226.920] (II) Loading extension GLX
[   226.920] (II) LoadModule: "record"
[   226.920] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   226.920] (II) Module record: vendor="X.Org Foundation"
[   226.920]    compiled for 1.9.0, module version = 1.13.0
[   226.920]    Module class: X.Org Server Extension
[   226.920]    ABI class: X.Org Server Extension, version 4.0
[   226.921] (II) Loading extension RECORD
[   226.921] (II) LoadModule: "dri"
[   226.921] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   226.921] (II) Module dri: vendor="X.Org Foundation"
[   226.921]    compiled for 1.9.0, module version = 1.0.0
[   226.921]    ABI class: X.Org Server Extension, version 4.0
[   226.921] (II) Loading extension XFree86-DRI
[   226.921] (II) LoadModule: "dri2"
[   226.922] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   226.922] (II) Module dri2: vendor="X.Org Foundation"
[   226.922]    compiled for 1.9.0, module version = 1.2.0
[   226.922]    ABI class: X.Org Server Extension, version 4.0
[   226.922] (II) Loading extension DRI2
[   226.922] (==) Matched intel as autoconfigured driver 0
[   226.922] (==) Matched vesa as autoconfigured driver 1
[   226.922] (==) Matched fbdev as autoconfigured driver 2
[   226.922] (==) Assigned the driver to the xf86ConfigLayout
[   226.922] (II) LoadModule: "intel"
[   226.922] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[   226.976] (II) Module intel: vendor="X.Org Foundation"
[   226.976]    compiled for 1.9.0, module version = 2.12.0
[   226.976]    Module class: X.Org Video Driver
[   226.976]    ABI class: X.Org Video Driver, version 8.0
[   226.976] (II) LoadModule: "vesa"
[   226.977] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   226.992] (II) Module vesa: vendor="X.Org Foundation"
[   226.992]    compiled for 1.8.99.905, module version = 2.3.0
[   226.992]    Module class: X.Org Video Driver
[   226.992]    ABI class: X.Org Video Driver, version 8.0
[   226.992] (II) LoadModule: "fbdev"
[   226.992] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   226.993] (II) Module fbdev: vendor="X.Org Foundation"
[   226.993]    compiled for 1.8.99.905, module version = 0.4.2
[   226.993]    ABI class: X.Org Video Driver, version 8.0
[   226.993] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
        i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
        E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
        965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
        4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
        Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
        Sandybridge, Sandybridge
[   226.995] (II) VESA: driver for VESA chipsets: vesa
[   226.995] (II) FBDEV: driver for framebuffer: fbdev
[   226.995] (--) using VT number 8

[   227.007] (WW) Falling back to old probe method for vesa
[   227.007] (WW) Falling back to old probe method for fbdev
[   227.007] (II) Loading sub module "fbdevhw"
[   227.007] (II) LoadModule: "fbdevhw"
[   227.007] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   227.008] (II) Module fbdevhw: vendor="X.Org Foundation"
[   227.008]    compiled for 1.9.0, module version = 0.0.2
[   227.008]    ABI class: X.Org Video Driver, version 8.0
[   227.010] drmOpenDevice: node name is /dev/dri/card0
[   227.010] drmOpenDevice: open result is 9, (OK)
[   227.036] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[   227.036] drmOpenDevice: node name is /dev/dri/card0
[   227.036] drmOpenDevice: open result is 9, (OK)
[   227.036] drmOpenByBusid: drmOpenMinor returns 9
[   227.036] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[   227.036] (II) intel(0): Creating default Display subsection in Screen section
        "Default Screen Section" for depth/fbbpp 24/32
[   227.036] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[   227.036] (==) intel(0): RGB weight 888
[   227.036] (==) intel(0): Default visual is TrueColor
[   227.036] (II) intel(0): Integrated Graphics Chipset: Intel(R) 945GM
[   227.036] (--) intel(0): Chipset: "945GM"
[   227.036] (==) intel(0): video overlay key set to 0x101fe
[   227.064] (II) intel(0): Output VGA1 has no monitor section
[   227.064] (II) intel(0): Output LVDS1 has no monitor section
[   227.064] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
[   227.400] (II) intel(0): Output TV1 has no monitor section
[   227.432] (II) intel(0): EDID for output VGA1
[   227.432] (II) intel(0): EDID for output LVDS1
[   227.432] (II) intel(0): Manufacturer: SEC  Model: 0  Serial#: 0
[   227.432] (II) intel(0): Year: 2006  Week: 0
[   227.432] (II) intel(0): EDID Version: 1.3
[   227.432] (II) intel(0): Digital Display Input
[   227.432] (II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 21
[   227.432] (II) intel(0): Gamma: 2.20
[   227.432] (II) intel(0): No DPMS capabilities specified
[   227.432] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[   227.432] (II) intel(0): First detailed timing is preferred mode
[   227.433] (II) intel(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
[   227.433] (II) intel(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
[   227.433] (II) intel(0): Manufacturer's mask: 0
[   227.433] (II) intel(0): Supported detailed timing:
[   227.433] (II) intel(0): clock: 71.1 MHz   Image Size:  331 x 207 mm
[   227.433] (II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
[   227.433] (II) intel(0): v_active: 800  v_sync: 802  v_sync_end 808 v_blanking: 823 v_border: 0
[   227.433] (II) intel(0): Unknown vendor-specific block f
[   227.433] (II) intel(0):  DD282^D154X3
[   227.433] (II) intel(0):  '@PZ<81><B0><D9><FF>^A^A
[   227.433] (II) intel(0): EDID (in hex):
[   227.433] (II) intel(0):     00ffffffffffff004ca3000000000000
[   227.433] (II) intel(0):     00100103802115780a87f594574f8c27
[   227.433] (II) intel(0):     27505400000001010101010101010101
[   227.433] (II) intel(0):     010101010101c71b00a0502017303020
[   227.433] (II) intel(0):     26004bcf100000190000000f00000000
[   227.433] (II) intel(0):     00000000002387026400000000fe0044
[   227.433] (II) intel(0):     443238320431353458330a20000000fe
[   227.433] (II) intel(0):     002740505a81b0d9ff01010a2020009d
[   227.434] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[   227.434] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[   227.434] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[   227.434] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[   227.434] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[   227.434] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[   227.434] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[   227.434] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[   227.434] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[   227.434] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[   227.434] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[   227.434] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[   227.435] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[   227.435] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[   227.435] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[   227.435] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[   227.435] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[   227.435] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[   227.435] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[   227.435] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[   227.435] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[   227.435] (II) intel(0): Printing probed modes for output LVDS1
[   227.435] (II) intel(0): Modeline "1280x800"x60.0   71.11  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (49.4 kHz)
[   227.435] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   227.435] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   227.435] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   227.435] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   227.768] (II) intel(0): EDID for output TV1
[   227.768] (II) intel(0): Output VGA1 disconnected
[   227.768] (II) intel(0): Output LVDS1 connected
[   227.768] (II) intel(0): Output TV1 disconnected
[   227.768] (II) intel(0): Using exact sizes for initial modes
[   227.768] (II) intel(0): Output LVDS1 using initial mode 1280x800
[   227.768] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[   227.768] (II) intel(0): Kernel page flipping support detected, but forcibly disabled.
[   227.768] (==) intel(0): DPI set to (96, 96)
[   227.768] (II) Loading sub module "fb"
[   227.768] (II) LoadModule: "fb"
[   227.770] (II) Loading /usr/lib/xorg/modules/libfb.so
[   227.770] (II) Module fb: vendor="X.Org Foundation"
[   227.770]    compiled for 1.9.0, module version = 1.0.0
[   227.770]    ABI class: X.Org ANSI C Emulation, version 0.4
[   227.770] (II) UnloadModule: "vesa"
[   227.770] (II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   227.770] (II) UnloadModule: "fbdev"
[   227.770] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   227.770] (II) UnloadModule: "fbdevhw"
[   227.770] (II) Unloading /usr/lib/xorg/modules/libfbdevhw.so
[   227.770] (==) Depth 24 pixmap format is 32 bpp
[   227.771] (II) intel(0): [DRI2] Setup complete
[   227.771] (II) intel(0): [DRI2]   DRI driver: i915
[   227.771] (**) intel(0): Tiling enabled
[   227.771] (**) intel(0): SwapBuffers wait enabled
[   227.771] (==) intel(0): VideoRam: 262144 KB
[   227.771] (II) intel(0): Allocated new frame buffer 1280x800 stride 8192, tiled
[   227.771] (II) UXA(0): Driver registered support for the following operations:
[   227.771] (II)         solid
[   227.771] (II)         copy
[   227.771] (II)         composite (RENDER acceleration)
[   227.771] (II)         put_image
[   227.771] (II)         get_image
[   227.771] (==) intel(0): Backing store disabled
[   227.771] (==) intel(0): Silken mouse enabled
[   227.771] (II) intel(0): Initializing HW Cursor
[   227.812] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[   227.819] (==) intel(0): DPMS enabled
[   227.819] (==) intel(0): Intel XvMC decoder disabled
[   227.819] (II) intel(0): Set up textured video
[   227.819] (II) intel(0): Set up overlay video
[   227.819] (II) intel(0): direct rendering: DRI2 Enabled
[   227.819] (--) RandR disabled
[   227.819] (II) Initializing built-in extension Generic Event Extension
[   227.819] (II) Initializing built-in extension SHAPE
[   227.819] (II) Initializing built-in extension MIT-SHM
[   227.819] (II) Initializing built-in extension XInputExtension
[   227.819] (II) Initializing built-in extension XTEST
[   227.819] (II) Initializing built-in extension BIG-REQUESTS
[   227.819] (II) Initializing built-in extension SYNC
[   227.819] (II) Initializing built-in extension XKEYBOARD
[   227.819] (II) Initializing built-in extension XC-MISC
[   227.819] (II) Initializing built-in extension SECURITY
[   227.819] (II) Initializing built-in extension XINERAMA
[   227.820] (II) Initializing built-in extension XFIXES
[   227.820] (II) Initializing built-in extension RENDER
[   227.820] (II) Initializing built-in extension RANDR
[   227.820] (II) Initializing built-in extension COMPOSITE
[   227.820] (II) Initializing built-in extension DAMAGE
[   227.820] (II) Initializing built-in extension GESTURE
[   228.006] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[   228.006] (II) AIGLX: enabled GLX_INTEL_swap_event
[   228.006] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[   228.006] (II) AIGLX: enabled GLX_SGI_make_current_read
[   228.006] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[   228.006] (II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
[   228.006] (II) GLX: Initialized DRI2 GL provider for screen 0
[   228.008] (II) intel(0): Setting screen physical size to 338 x 211
[   228.040] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   228.052] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[   228.053] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[   228.053] (II) LoadModule: "evdev"
[   228.053] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   228.053] (II) Module evdev: vendor="X.Org Foundation"
[   228.053]    compiled for 1.9.0, module version = 2.3.2
[   228.053]    Module class: X.Org XInput Driver
[   228.053]    ABI class: X.Org XInput driver, version 11.0
[   228.053] (**) Video Bus: always reports core events
[   228.053] (**) Video Bus: Device: "/dev/input/event4"
[   228.072] (II) Video Bus: Found keys
[   228.072] (II) Video Bus: Configuring as keyboard
[   228.072] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[   228.072] (**) Option "xkb_rules" "evdev"
[   228.072] (**) Option "xkb_model" "pc105"
[   228.072] (**) Option "xkb_layout" "gb"
[   228.079] (II) XKB: reuse xkmfile /var/lib/xkb/server-2B4266AA55228AE7D9557A18F1965DBA19850816.xkm
[   228.086] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[   228.087] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   228.087] (**) Power Button: always reports core events
[   228.087] (**) Power Button: Device: "/dev/input/event1"
[   228.104] (II) Power Button: Found keys
[   228.104] (II) Power Button: Configuring as keyboard
[   228.104] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[   228.104] (**) Option "xkb_rules" "evdev"
[   228.104] (**) Option "xkb_model" "pc105"
[   228.104] (**) Option "xkb_layout" "gb"
[   228.105] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[   228.105] (II) No input driver/identifier specified (ignoring)
[   228.106] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[   228.106] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[   228.106] (**) Sleep Button: always reports core events
[   228.106] (**) Sleep Button: Device: "/dev/input/event2"
[   228.124] (II) Sleep Button: Found keys
[   228.124] (II) Sleep Button: Configuring as keyboard
[   228.124] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[   228.124] (**) Option "xkb_rules" "evdev"
[   228.124] (**) Option "xkb_model" "pc105"
[   228.124] (**) Option "xkb_layout" "gb"
[   228.127] (II) config/udev: Adding input device HDA Intel Mic at Ext Right Jack (/dev/input/event7)
[   228.127] (II) No input driver/identifier specified (ignoring)
[   228.128] (II) config/udev: Adding input device HDA Intel HP Out at Ext Right Jack (/dev/input/event8)
[   228.128] (II) No input driver/identifier specified (ignoring)
[   228.141] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[   228.141] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[   228.141] (**) AT Translated Set 2 keyboard: always reports core events
[   228.141] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[   228.160] (II) AT Translated Set 2 keyboard: Found keys
[   228.160] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[   228.160] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[   228.160] (**) Option "xkb_rules" "evdev"
[   228.160] (**) Option "xkb_model" "pc105"
[   228.160] (**) Option "xkb_layout" "gb"
[   228.161] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event6)
[   228.161] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[   228.162] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[   228.162] (II) LoadModule: "synaptics"
[   228.162] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[   228.162] (II) Module synaptics: vendor="X.Org Foundation"
[   228.162]    compiled for 1.9.0, module version = 1.2.2
[   228.162]    Module class: X.Org XInput Driver
[   228.162]    ABI class: X.Org XInput driver, version 11.0
[   228.163] (II) Synaptics touchpad driver version 1.2.2
[   228.163] (**) Option "Device" "/dev/input/event6"
[   228.212] (II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[   228.212] (II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[   228.212] (II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[   228.212] (II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
[   228.212] (II) SynPS/2 Synaptics TouchPad: buttons: left right double triple
[   228.244] (--) SynPS/2 Synaptics TouchPad: touchpad found
[   228.244] (**) SynPS/2 Synaptics TouchPad: always reports core events
[   228.260] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[   228.260] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[   228.260] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
[   228.260] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[   228.260] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[   228.292] (--) SynPS/2 Synaptics TouchPad: touchpad found
[   228.292] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[   228.292] (II) No input driver/identifier specified (ignoring)
[   228.301] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event5)
[   228.301] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[   228.301] (**) Dell WMI hotkeys: always reports core events
[   228.301] (**) Dell WMI hotkeys: Device: "/dev/input/event5"
[   228.316] (II) Dell WMI hotkeys: Found keys
[   228.316] (II) Dell WMI hotkeys: Configuring as keyboard
[   228.316] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD)
[   228.316] (**) Option "xkb_rules" "evdev"
[   228.316] (**) Option "xkb_model" "pc105"
[   228.316] (**) Option "xkb_layout" "gb"
[   231.464] (II) intel(0): EDID vendor "SEC", prod id 0
[   231.464] (II) intel(0): Printing DDC gathered Modelines:
[   231.464] (II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (49.4 kHz)
[   231.832] (II) intel(0): EDID vendor "SEC", prod id 0
[   231.832] (II) intel(0): Printing DDC gathered Modelines:
[   231.832] (II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (49.4 kHz)
[   232.196] (II) intel(0): EDID vendor "SEC", prod id 0
[   232.196] (II) intel(0): Printing DDC gathered Modelines:
[   232.196] (II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (49.4 kHz)
[   232.568] (II) intel(0): EDID vendor "SEC", prod id 0
[   232.568] (II) intel(0): Printing DDC gathered Modelines:
[   232.568] (II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (49.4 kHz)
[   240.109] (II) intel(0): EDID vendor "SEC", prod id 0
[   240.109] (II) intel(0): Printing DDC gathered Modelines:
[   240.109] (II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (49.4 kHz)

Thanks Ayuthia.

It ends there. The i810 message doesnt appear, but it still doesn't work I'm going to try the modeset thing.

---

### Post by night_fox on 2010-10-15
i915.modeset=1 and i915.modeset=0 both don't work. i915.modeset=0 makes the splash screen look really strange

---

### Post by Ayuthia on 2010-10-15
If that is the case, then it looks like i915 is on by default.  You mentioned that startx works.  Have you checked the difference between that log and the one when you start up?

EDIT:
Have you also tried:
```

sudo service gdm restart

```
or
```

sudo service gdm start

```
You might also check /var/log/gdm/:0.log and /var/log/gdm/:0-greeter.log to see if there are any additional error messages.

---

### Post by night_fox on 2010-10-26
Sorry, I got bored and reinstalled Maverick from the cd.

---

