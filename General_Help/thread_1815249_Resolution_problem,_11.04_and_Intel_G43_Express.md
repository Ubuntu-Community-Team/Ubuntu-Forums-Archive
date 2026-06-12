---
title: "Resolution problem, 11.04 and Intel G43 Express"
date: 2011-07-30
forum: General Help
---

### Post by DocForbin on 2011-07-30
I just installed 64 bit Ubuntu 11.04 Desktop on a new Gateway SX-2803. The screen resolution is off, I can't see the left or bottom of the screen. 

It has a Intel® G43 Express chipset. I have it connected to a Samsung DLP via HDMI.

When I run the Monitor app it shows 1280x720, and the only other options are 720x480 and 640x480. There is no xorg.conf file in /etc/X11 or /usr/share/Xll.

Can someone point me in the right direction? I'll post output of the xorg log and lspci if it helps.

---

### Post by DocForbin on 2011-07-30
```
$ lspci
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:19.0 Ethernet controller: Intel Corporation 82567V-2 Gigabit Network Connection
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIB (ICH10) LPC Interface Controller
00:1f.2 SATA controller: Intel Corporation 82801JI (ICH10 Family) SATA AHCI Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
01:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6315 Series Firewire Controller (rev 01)

```

---

### Post by DocForbin on 2011-07-30
```
[    12.349] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    12.349] X Protocol Version 11, Revision 0
[    12.349] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[    12.349] Current Operating System: Linux muddy 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:07:17 UTC 2011 x86_64
[    12.349] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-10-generic root=UUID=88d30ba4-30a3-443a-a4e5-bdde6bad9c3d ro quiet splash vt.handoff=7
[    12.349] Build Date: 21 May 2011  11:48:41AM
[    12.349] xorg-server 2:1.10.1-1ubuntu1.1 (For technical support please see http://www.ubuntu.com/support) 
[    12.349] Current version of pixman: 0.20.2
[    12.349] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    12.349] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    12.349] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Jul 30 22:33:20 2011
[    12.498] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    12.498] (==) No Layout section.  Using the first Screen section.
[    12.498] (==) No screen section available. Using defaults.
[    12.498] (**) |-->Screen "Default Screen Section" (0)
[    12.498] (**) |   |-->Monitor "<default monitor>"
[    12.499] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    12.499] (==) Automatically adding devices
[    12.499] (==) Automatically enabling devices
[    12.499] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    12.499] 	Entry deleted from font path.
[    12.499] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    12.499] 	Entry deleted from font path.
[    12.499] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    12.499] 	Entry deleted from font path.
[    12.499] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    12.499] 	Entry deleted from font path.
[    12.499] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    12.499] 	Entry deleted from font path.
[    12.499] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    12.499] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    12.499] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    12.499] (II) Loader magic: 0x7e0280
[    12.499] (II) Module ABI versions:
[    12.499] 	X.Org ANSI C Emulation: 0.4
[    12.499] 	X.Org Video Driver: 10.0
[    12.499] 	X.Org XInput driver : 12.3
[    12.499] 	X.Org Server Extension : 5.0
[    12.499] (--) PCI:*(0:0:2:0) 8086:2e22:1025:0251 rev 3, Mem @ 0xfe400000/4194304, 0xd0000000/268435456, I/O @ 0x0000dc00/8
[    12.499] (--) PCI: (0:0:2:1) 8086:2e23:1025:0251 rev 3, Mem @ 0xfe900000/1048576
[    12.499] (II) Open ACPI successful (/var/run/acpid.socket)
[    12.499] (II) LoadModule: "extmod"
[    12.559] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    12.670] (II) Module extmod: vendor="X.Org Foundation"
[    12.671] 	compiled for 1.10.1, module version = 1.0.0
[    12.671] 	Module class: X.Org Server Extension
[    12.671] 	ABI class: X.Org Server Extension, version 5.0
[    12.671] (II) Loading extension MIT-SCREEN-SAVER
[    12.671] (II) Loading extension XFree86-VidModeExtension
[    12.671] (II) Loading extension XFree86-DGA
[    12.671] (II) Loading extension DPMS
[    12.671] (II) Loading extension XVideo
[    12.671] (II) Loading extension XVideo-MotionCompensation
[    12.671] (II) Loading extension X-Resource
[    12.671] (II) LoadModule: "dbe"
[    12.671] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    12.671] (II) Module dbe: vendor="X.Org Foundation"
[    12.671] 	compiled for 1.10.1, module version = 1.0.0
[    12.671] 	Module class: X.Org Server Extension
[    12.671] 	ABI class: X.Org Server Extension, version 5.0
[    12.671] (II) Loading extension DOUBLE-BUFFER
[    12.671] (II) LoadModule: "glx"
[    12.671] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    12.671] (II) Module glx: vendor="X.Org Foundation"
[    12.671] 	compiled for 1.10.1, module version = 1.0.0
[    12.671] 	ABI class: X.Org Server Extension, version 5.0
[    12.671] (==) AIGLX enabled
[    12.671] (II) Loading extension GLX
[    12.671] (II) LoadModule: "record"
[    12.671] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    12.672] (II) Module record: vendor="X.Org Foundation"
[    12.672] 	compiled for 1.10.1, module version = 1.13.0
[    12.672] 	Module class: X.Org Server Extension
[    12.672] 	ABI class: X.Org Server Extension, version 5.0
[    12.672] (II) Loading extension RECORD
[    12.672] (II) LoadModule: "dri"
[    12.672] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    12.672] (II) Module dri: vendor="X.Org Foundation"
[    12.672] 	compiled for 1.10.1, module version = 1.0.0
[    12.672] 	ABI class: X.Org Server Extension, version 5.0
[    12.672] (II) Loading extension XFree86-DRI
[    12.672] (II) LoadModule: "dri2"
[    12.672] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    12.672] (II) Module dri2: vendor="X.Org Foundation"
[    12.672] 	compiled for 1.10.1, module version = 1.2.0
[    12.672] 	ABI class: X.Org Server Extension, version 5.0
[    12.672] (II) Loading extension DRI2
[    12.672] (==) Matched intel as autoconfigured driver 0
[    12.672] (==) Matched vesa as autoconfigured driver 1
[    12.672] (==) Matched fbdev as autoconfigured driver 2
[    12.672] (==) Assigned the driver to the xf86ConfigLayout
[    12.672] (II) LoadModule: "intel"
[    12.672] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    12.673] (II) Module intel: vendor="X.Org Foundation"
[    12.673] 	compiled for 1.10.1, module version = 2.14.0
[    12.673] 	Module class: X.Org Video Driver
[    12.673] 	ABI class: X.Org Video Driver, version 10.0
[    12.673] (II) LoadModule: "vesa"
[    12.673] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    12.673] (II) Module vesa: vendor="X.Org Foundation"
[    12.673] 	compiled for 1.10.0, module version = 2.3.0
[    12.673] 	Module class: X.Org Video Driver
[    12.673] 	ABI class: X.Org Video Driver, version 10.0
[    12.673] (II) LoadModule: "fbdev"
[    12.673] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    12.673] (II) Module fbdev: vendor="X.Org Foundation"
[    12.673] 	compiled for 1.10.0, module version = 0.4.2
[    12.673] 	ABI class: X.Org Video Driver, version 10.0
[    12.673] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
	Sandybridge, Sandybridge
[    12.673] (II) VESA: driver for VESA chipsets: vesa
[    12.673] (II) FBDEV: driver for framebuffer: fbdev
[    12.673] (++) using VT number 7

[    12.675] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    12.675] (WW) Falling back to old probe method for vesa
[    12.675] (WW) Falling back to old probe method for fbdev
[    12.675] (II) Loading sub module "fbdevhw"
[    12.675] (II) LoadModule: "fbdevhw"
[    12.675] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    12.675] (II) Module fbdevhw: vendor="X.Org Foundation"
[    12.675] 	compiled for 1.10.1, module version = 0.0.2
[    12.675] 	ABI class: X.Org Video Driver, version 10.0
[    12.675] drmOpenDevice: node name is /dev/dri/card0
[    12.675] drmOpenDevice: open result is 9, (OK)
[    12.675] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    12.675] drmOpenDevice: node name is /dev/dri/card0
[    12.675] drmOpenDevice: open result is 9, (OK)
[    12.675] drmOpenByBusid: drmOpenMinor returns 9
[    12.675] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    12.675] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    12.675] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    12.675] (==) intel(0): RGB weight 888
[    12.675] (==) intel(0): Default visual is TrueColor
[    12.675] (II) intel(0): Integrated Graphics Chipset: Intel(R) G45/G43
[    12.675] (--) intel(0): Chipset: "G45/G43"
[    12.675] (**) intel(0): Relaxed fencing enabled
[    12.675] (**) intel(0): Tiling enabled
[    12.675] (**) intel(0): SwapBuffers wait enabled
[    12.675] (==) intel(0): video overlay key set to 0x101fe
[    12.750] (II) intel(0): Output VGA1 has no monitor section
[    12.954] (II) intel(0): Output HDMI1 has no monitor section
[    12.955] (II) intel(0): Output DP1 has no monitor section
[    13.030] (II) intel(0): EDID for output VGA1
[    13.234] (II) intel(0): EDID for output HDMI1
[    13.234] (II) intel(0): Manufacturer: SAM  Model: 137  Serial#: 0
[    13.234] (II) intel(0): Year: 2004  Week: 19
[    13.234] (II) intel(0): EDID Version: 1.3
[    13.234] (II) intel(0): Digital Display Input
[    13.234] (II) intel(0): Max Image Size [cm]: horiz.: 110  vert.: 62
[    13.234] (II) intel(0): Gamma: 2.20
[    13.234] (II) intel(0): No DPMS capabilities specified
[    13.234] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    13.234] (II) intel(0): First detailed timing is preferred mode
[    13.234] (II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
[    13.234] (II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
[    13.234] (II) intel(0): Supported established timings:
[    13.234] (II) intel(0): 640x480@60Hz
[    13.234] (II) intel(0): Manufacturer's mask: 0
[    13.234] (II) intel(0): Supported detailed timing:
[    13.234] (II) intel(0): clock: 74.2 MHz   Image Size:  1107 x 623 mm
[    13.234] (II) intel(0): h_active: 1280  h_sync: 1390  h_sync_end 1430 h_blank_end 1650 h_border: 0
[    13.234] (II) intel(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[    13.234] (II) intel(0): Supported detailed timing:
[    13.234] (II) intel(0): clock: 74.2 MHz   Image Size:  1107 x 623 mm
[    13.234] (II) intel(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    13.234] (II) intel(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
[    13.234] (II) intel(0): Monitor name: SAMSUNG DLP
[    13.235] (II) intel(0): Ranges: V min: 59 V max: 61 Hz, H min: 15 H max: 46 kHz, PixClock max 85 MHz
[    13.235] (II) intel(0): Supported detailed timing:
[    13.235] (II) intel(0): clock: 27.0 MHz   Image Size:  1107 x 623 mm
[    13.235] (II) intel(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
[    13.235] (II) intel(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
[    13.235] (II) intel(0): Number of EDID sections to follow: 1
[    13.235] (II) intel(0): EDID (in hex):
[    13.235] (II) intel(0): 	00ffffffffffff004c2d370100000000
[    13.235] (II) intel(0): 	130e0103806e3e780aee91a3544c9926
[    13.235] (II) intel(0): 	0f505420000001010101010101010101
[    13.235] (II) intel(0): 	010101010101011d007251d01e206e28
[    13.235] (II) intel(0): 	5500536f4200001e011d8018711c1620
[    13.235] (II) intel(0): 	582c2500536f4200009e000000fc0053
[    13.235] (II) intel(0): 	414d53554e4720444c500a20000000fd
[    13.235] (II) intel(0): 	003b3d0f2e08000a2020202020200195
[    13.235] (II) intel(0): 	02031673438405032309070783010000
[    13.235] (II) intel(0): 	65030c0010008c0ad08a20e02d10103e
[    13.235] (II) intel(0): 	9600536f420000180000000000000000
[    13.235] (II) intel(0): 	00000000000000000000000000000000
[    13.235] (II) intel(0): 	00000000000000000000000000000000
[    13.235] (II) intel(0): 	00000000000000000000000000000000
[    13.235] (II) intel(0): 	00000000000000000000000000000000
[    13.235] (II) intel(0): 	00000000000000000000000000000034
[    13.235] (II) intel(0): Printing probed modes for output HDMI1
[    13.235] (II) intel(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    13.235] (II) intel(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    13.235] (II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    13.236] (II) intel(0): EDID for output DP1
[    13.236] (II) intel(0): Output VGA1 disconnected
[    13.236] (II) intel(0): Output HDMI1 connected
[    13.236] (II) intel(0): Output DP1 disconnected
[    13.236] (II) intel(0): Using exact sizes for initial modes
[    13.236] (II) intel(0): Output HDMI1 using initial mode 1280x720
[    13.236] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    13.236] (II) intel(0): Kernel page flipping support detected, enabling
[    13.236] (==) intel(0): DPI set to (96, 96)
[    13.236] (II) Loading sub module "fb"
[    13.236] (II) LoadModule: "fb"
[    13.236] (II) Loading /usr/lib/xorg/modules/libfb.so
[    13.236] (II) Module fb: vendor="X.Org Foundation"
[    13.236] 	compiled for 1.10.1, module version = 1.0.0
[    13.236] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    13.236] (II) UnloadModule: "vesa"
[    13.236] (II) Unloading vesa
[    13.236] (II) UnloadModule: "fbdev"
[    13.236] (II) Unloading fbdev
[    13.236] (II) UnloadModule: "fbdevhw"
[    13.236] (II) Unloading fbdevhw
[    13.236] (==) Depth 24 pixmap format is 32 bpp
[    13.236] (==) intel(0): VideoRam: 262144 KB
[    13.236] (II) intel(0): [DRI2] Setup complete
[    13.236] (II) intel(0): [DRI2]   DRI driver: i965
[    13.236] (II) intel(0): Allocated new frame buffer 1280x720 stride 5120, tiled
[    13.246] (II) UXA(0): Driver registered support for the following operations:
[    13.246] (II)         solid
[    13.246] (II)         copy
[    13.246] (II)         composite (RENDER acceleration)
[    13.246] (II)         put_image
[    13.246] (II)         get_image
[    13.246] (==) intel(0): Backing store disabled
[    13.246] (==) intel(0): Silken mouse enabled
[    13.246] (II) intel(0): Initializing HW Cursor
[    13.270] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    13.270] (==) intel(0): DPMS enabled
[    13.270] (==) intel(0): Intel XvMC decoder enabled
[    13.270] (II) intel(0): Set up textured video
[    13.270] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[    13.270] (II) intel(0): direct rendering: DRI2 Enabled
[    13.270] (==) intel(0): hotplug detection: "enabled"
[    13.270] (--) RandR disabled
[    13.270] (II) Initializing built-in extension Generic Event Extension
[    13.270] (II) Initializing built-in extension SHAPE
[    13.270] (II) Initializing built-in extension MIT-SHM
[    13.270] (II) Initializing built-in extension XInputExtension
[    13.270] (II) Initializing built-in extension XTEST
[    13.270] (II) Initializing built-in extension BIG-REQUESTS
[    13.270] (II) Initializing built-in extension SYNC
[    13.270] (II) Initializing built-in extension XKEYBOARD
[    13.270] (II) Initializing built-in extension XC-MISC
[    13.270] (II) Initializing built-in extension SECURITY
[    13.270] (II) Initializing built-in extension XINERAMA
[    13.270] (II) Initializing built-in extension XFIXES
[    13.270] (II) Initializing built-in extension RENDER
[    13.270] (II) Initializing built-in extension RANDR
[    13.270] (II) Initializing built-in extension COMPOSITE
[    13.270] (II) Initializing built-in extension DAMAGE
[    13.270] (II) Initializing built-in extension GESTURE
[    13.274] (II) AIGLX: Trying DRI driver /usr/lib/dri/i965_dri.so
[    13.301] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    13.301] (II) AIGLX: enabled GLX_INTEL_swap_event
[    13.301] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    13.301] (II) AIGLX: enabled GLX_SGI_make_current_read
[    13.301] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    13.301] (II) AIGLX: Loaded and initialized i965
[    13.301] (II) GLX: Initialized DRI2 GL provider for screen 0
[    13.302] (II) intel(0): Setting screen physical size to 338 x 190
[    13.307] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    13.314] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    13.314] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    13.314] (II) LoadModule: "evdev"
[    13.314] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.315] (II) Module evdev: vendor="X.Org Foundation"
[    13.315] 	compiled for 1.10.0.902, module version = 2.6.0
[    13.315] 	Module class: X.Org XInput Driver
[    13.315] 	ABI class: X.Org XInput driver, version 12.3
[    13.315] (II) Using input driver 'evdev' for 'Power Button'
[    13.315] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.315] (**) Power Button: always reports core events
[    13.315] (**) Power Button: Device: "/dev/input/event1"
[    13.340] (--) Power Button: Found keys
[    13.340] (II) Power Button: Configuring as keyboard
[    13.340] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    13.340] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    13.340] (**) Option "xkb_rules" "evdev"
[    13.340] (**) Option "xkb_model" "pc105"
[    13.340] (**) Option "xkb_layout" "us"
[    13.342] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    13.342] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    13.342] (II) Using input driver 'evdev' for 'Power Button'
[    13.342] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.342] (**) Power Button: always reports core events
[    13.342] (**) Power Button: Device: "/dev/input/event0"
[    13.342] (--) Power Button: Found keys
[    13.342] (II) Power Button: Configuring as keyboard
[    13.342] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    13.342] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    13.342] (**) Option "xkb_rules" "evdev"
[    13.342] (**) Option "xkb_model" "pc105"
[    13.342] (**) Option "xkb_layout" "us"
[    13.344] (II) config/udev: Adding input device Microsoft Microsoft® Nano Transceiver v2.0 (/dev/input/event2)
[    13.344] (**) Microsoft Microsoft® Nano Transceiver v2.0: Applying InputClass "evdev keyboard catchall"
[    13.344] (II) Using input driver 'evdev' for 'Microsoft Microsoft® Nano Transceiver v2.0'
[    13.344] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.344] (**) Microsoft Microsoft® Nano Transceiver v2.0: always reports core events
[    13.344] (**) Microsoft Microsoft® Nano Transceiver v2.0: Device: "/dev/input/event2"
[    13.350] (--) Microsoft Microsoft® Nano Transceiver v2.0: Found keys
[    13.350] (II) Microsoft Microsoft® Nano Transceiver v2.0: Configuring as keyboard
[    13.350] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.0/input/input2/event2"
[    13.350] (II) XINPUT: Adding extended input device "Microsoft Microsoft® Nano Transceiver v2.0" (type: KEYBOARD)
[    13.350] (**) Option "xkb_rules" "evdev"
[    13.350] (**) Option "xkb_model" "pc105"
[    13.350] (**) Option "xkb_layout" "us"
[    13.350] (II) config/udev: Adding input device Microsoft Microsoft® Nano Transceiver v2.0 (/dev/input/event3)
[    13.350] (**) Microsoft Microsoft® Nano Transceiver v2.0: Applying InputClass "evdev pointer catchall"
[    13.350] (**) Microsoft Microsoft® Nano Transceiver v2.0: Applying InputClass "evdev keyboard catchall"
[    13.350] (II) Using input driver 'evdev' for 'Microsoft Microsoft® Nano Transceiver v2.0'
[    13.350] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.350] (**) Microsoft Microsoft® Nano Transceiver v2.0: always reports core events
[    13.350] (**) Microsoft Microsoft® Nano Transceiver v2.0: Device: "/dev/input/event3"
[    13.350] (--) Microsoft Microsoft® Nano Transceiver v2.0: Found 9 mouse buttons
[    13.350] (--) Microsoft Microsoft® Nano Transceiver v2.0: Found scroll wheel(s)
[    13.350] (--) Microsoft Microsoft® Nano Transceiver v2.0: Found relative axes
[    13.350] (--) Microsoft Microsoft® Nano Transceiver v2.0: Found x and y relative axes
[    13.350] (--) Microsoft Microsoft® Nano Transceiver v2.0: Found absolute axes
[    13.350] (II) evdev-grail: failed to open grail, no gesture support
[    13.350] (--) Microsoft Microsoft® Nano Transceiver v2.0: Found keys
[    13.350] (II) Microsoft Microsoft® Nano Transceiver v2.0: Configuring as mouse
[    13.350] (II) Microsoft Microsoft® Nano Transceiver v2.0: Configuring as keyboard
[    13.350] (II) Microsoft Microsoft® Nano Transceiver v2.0: Adding scrollwheel support
[    13.350] (**) Microsoft Microsoft® Nano Transceiver v2.0: YAxisMapping: buttons 4 and 5
[    13.350] (**) Microsoft Microsoft® Nano Transceiver v2.0: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    13.350] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.1/input/input3/event3"
[    13.350] (II) XINPUT: Adding extended input device "Microsoft Microsoft® Nano Transceiver v2.0" (type: KEYBOARD)
[    13.350] (**) Option "xkb_rules" "evdev"
[    13.351] (**) Option "xkb_model" "pc105"
[    13.351] (**) Option "xkb_layout" "us"
[    13.351] (II) Microsoft Microsoft® Nano Transceiver v2.0: initialized for relative axes.
[    13.351] (WW) Microsoft Microsoft® Nano Transceiver v2.0: ignoring absolute axes.
[    13.351] (**) Microsoft Microsoft® Nano Transceiver v2.0: (accel) keeping acceleration scheme 1
[    13.351] (**) Microsoft Microsoft® Nano Transceiver v2.0: (accel) acceleration profile 0
[    13.351] (**) Microsoft Microsoft® Nano Transceiver v2.0: (accel) acceleration factor: 2.000
[    13.351] (**) Microsoft Microsoft® Nano Transceiver v2.0: (accel) acceleration threshold: 4
[    13.351] (II) config/udev: Adding input device Microsoft Microsoft® Nano Transceiver v2.0 (/dev/input/mouse0)
[    13.351] (II) No input driver/identifier specified (ignoring)
[    13.351] (II) config/udev: Adding input device Microsoft Microsoft® Nano Transceiver v2.0 (/dev/input/event4)
[    13.351] (**) Microsoft Microsoft® Nano Transceiver v2.0: Applying InputClass "evdev keyboard catchall"
[    13.351] (II) Using input driver 'evdev' for 'Microsoft Microsoft® Nano Transceiver v2.0'
[    13.351] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.351] (**) Microsoft Microsoft® Nano Transceiver v2.0: always reports core events
[    13.351] (**) Microsoft Microsoft® Nano Transceiver v2.0: Device: "/dev/input/event4"
[    13.380] (--) Microsoft Microsoft® Nano Transceiver v2.0: Found 1 mouse buttons
[    13.380] (--) Microsoft Microsoft® Nano Transceiver v2.0: Found scroll wheel(s)
[    13.380] (--) Microsoft Microsoft® Nano Transceiver v2.0: Found relative axes
[    13.380] (--) Microsoft Microsoft® Nano Transceiver v2.0: Found absolute axes
[    13.380] (--) Microsoft Microsoft® Nano Transceiver v2.0: Found x and y absolute axes
[    13.380] (--) Microsoft Microsoft® Nano Transceiver v2.0: Found keys
[    13.380] (II) Microsoft Microsoft® Nano Transceiver v2.0: Configuring as mouse
[    13.380] (II) Microsoft Microsoft® Nano Transceiver v2.0: Configuring as keyboard
[    13.380] (II) Microsoft Microsoft® Nano Transceiver v2.0: Adding scrollwheel support
[    13.380] (**) Microsoft Microsoft® Nano Transceiver v2.0: YAxisMapping: buttons 4 and 5
[    13.380] (**) Microsoft Microsoft® Nano Transceiver v2.0: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    13.380] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.2/input/input4/event4"
[    13.380] (II) XINPUT: Adding extended input device "Microsoft Microsoft® Nano Transceiver v2.0" (type: KEYBOARD)
[    13.380] (**) Option "xkb_rules" "evdev"
[    13.380] (**) Option "xkb_model" "pc105"
[    13.380] (**) Option "xkb_layout" "us"
[    13.380] (EE) Microsoft Microsoft® Nano Transceiver v2.0: failed to initialize for relative axes.
[    13.382] (WW) Touch X valuator does not match pointer X valuator, pointer emulation may be incorrect
[    13.382] (WW) Touch Y valuator does not match pointer Y valuator, pointer emulation may be incorrect
[    13.382] (II) Microsoft Microsoft® Nano Transceiver v2.0: initialized for absolute axes.
[    13.382] (**) Microsoft Microsoft® Nano Transceiver v2.0: (accel) keeping acceleration scheme 1
[    13.382] (**) Microsoft Microsoft® Nano Transceiver v2.0: (accel) acceleration profile 0
[    13.382] (**) Microsoft Microsoft® Nano Transceiver v2.0: (accel) acceleration factor: 2.000
[    13.382] (**) Microsoft Microsoft® Nano Transceiver v2.0: (accel) acceleration threshold: 4
[    13.383] (II) config/udev: Adding input device Microsoft Microsoft® Nano Transceiver v2.0 (/dev/input/js0)
[    13.383] (II) No input driver/identifier specified (ignoring)
[    13.384] (II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event8)
[    13.384] (II) No input driver/identifier specified (ignoring)
[    13.385] (II) config/udev: Adding input device Microsoft Microsoft® Nano Transceiver v2.0 (/dev/input/event5)
[    13.385] (**) Microsoft Microsoft® Nano Transceiver v2.0: Applying InputClass "evdev keyboard catchall"
[    13.385] (II) Using input driver 'evdev' for 'Microsoft Microsoft® Nano Transceiver v2.0'
[    13.385] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.385] (**) Microsoft Microsoft® Nano Transceiver v2.0: always reports core events
[    13.385] (**) Microsoft Microsoft® Nano Transceiver v2.0: Device: "/dev/input/event5"
[    13.420] (--) Microsoft Microsoft® Nano Transceiver v2.0: Found keys
[    13.420] (II) Microsoft Microsoft® Nano Transceiver v2.0: Configuring as keyboard
[    13.420] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.0/input/input5/event5"
[    13.420] (II) XINPUT: Adding extended input device "Microsoft Microsoft® Nano Transceiver v2.0" (type: KEYBOARD)
[    13.420] (**) Option "xkb_rules" "evdev"
[    13.420] (**) Option "xkb_model" "pc105"
[    13.420] (**) Option "xkb_layout" "us"
[    13.420] (II) config/udev: Adding input device Microsoft Microsoft® Nano Transceiver v2.0 (/dev/input/event6)
[    13.420] (**) Microsoft Microsoft® Nano Transceiver v2.0: Applying InputClass "evdev pointer catchall"
[    13.420] (**) Microsoft Microsoft® Nano Transceiver v2.0: Applying InputClass "evdev keyboard catchall"
[    13.420] (II) Using input driver 'evdev' for 'Microsoft Microsoft® Nano Transceiver v2.0'
[    13.420] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.420] (**) Microsoft Microsoft® Nano Transceiver v2.0: always reports core events
[    13.420] (**) Microsoft Microsoft® Nano Transceiver v2.0: Device: "/dev/input/event6"
[    13.420] (--) Microsoft Microsoft® Nano Transceiver v2.0: Found 9 mouse buttons
[    13.420] (--) Microsoft Microsoft® Nano Transceiver v2.0: Found scroll wheel(s)
[    13.420] (--) Microsoft Microsoft® Nano Transceiver v2.0: Found relative axes
[    13.420] (--) Microsoft Microsoft® Nano Transceiver v2.0: Found x and y relative axes
[    13.421] (--) Microsoft Microsoft® Nano Transceiver v2.0: Found absolute axes
[    13.421] (II) evdev-grail: failed to open grail, no gesture support
[    13.421] (--) Microsoft Microsoft® Nano Transceiver v2.0: Found keys
[    13.421] (II) Microsoft Microsoft® Nano Transceiver v2.0: Configuring as mouse
[    13.421] (II) Microsoft Microsoft® Nano Transceiver v2.0: Configuring as keyboard
[    13.421] (II) Microsoft Microsoft® Nano Transceiver v2.0: Adding scrollwheel support
[    13.421] (**) Microsoft Microsoft® Nano Transceiver v2.0: YAxisMapping: buttons 4 and 5
[    13.421] (**) Microsoft Microsoft® Nano Transceiver v2.0: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    13.421] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.1/input/input6/event6"
[    13.421] (II) XINPUT: Adding extended input device "Microsoft Microsoft® Nano Transceiver v2.0" (type: KEYBOARD)
[    13.421] (**) Option "xkb_rules" "evdev"
[    13.421] (**) Option "xkb_model" "pc105"
[    13.421] (**) Option "xkb_layout" "us"
[    13.421] (II) Microsoft Microsoft® Nano Transceiver v2.0: initialized for relative axes.
[    13.421] (WW) Microsoft Microsoft® Nano Transceiver v2.0: ignoring absolute axes.
[    13.421] (**) Microsoft Microsoft® Nano Transceiver v2.0: (accel) keeping acceleration scheme 1
[    13.421] (**) Microsoft Microsoft® Nano Transceiver v2.0: (accel) acceleration profile 0
[    13.421] (**) Microsoft Microsoft® Nano Transceiver v2.0: (accel) acceleration factor: 2.000
[    13.421] (**) Microsoft Microsoft® Nano Transceiver v2.0: (accel) acceleration threshold: 4
[    13.421] (II) config/udev: Adding input device Microsoft Microsoft® Nano Transceiver v2.0 (/dev/input/mouse1)
[    13.421] (II) No input driver/identifier specified (ignoring)
[    13.421] (II) config/udev: Adding input device Microsoft Microsoft® Nano Transceiver v2.0 (/dev/input/event7)
[    13.421] (**) Microsoft Microsoft® Nano Transceiver v2.0: Applying InputClass "evdev keyboard catchall"
[    13.421] (II) Using input driver 'evdev' for 'Microsoft Microsoft® Nano Transceiver v2.0'
[    13.421] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.421] (**) Microsoft Microsoft® Nano Transceiver v2.0: always reports core events
[    13.421] (**) Microsoft Microsoft® Nano Transceiver v2.0: Device: "/dev/input/event7"
[    13.422] (--) Microsoft Microsoft® Nano Transceiver v2.0: Found 1 mouse buttons
[    13.422] (--) Microsoft Microsoft® Nano Transceiver v2.0: Found scroll wheel(s)
[    13.422] (--) Microsoft Microsoft® Nano Transceiver v2.0: Found relative axes
[    13.422] (--) Microsoft Microsoft® Nano Transceiver v2.0: Found absolute axes
[    13.422] (--) Microsoft Microsoft® Nano Transceiver v2.0: Found x and y absolute axes
[    13.422] (--) Microsoft Microsoft® Nano Transceiver v2.0: Found keys
[    13.422] (II) Microsoft Microsoft® Nano Transceiver v2.0: Configuring as mouse
[    13.422] (II) Microsoft Microsoft® Nano Transceiver v2.0: Configuring as keyboard
[    13.422] (II) Microsoft Microsoft® Nano Transceiver v2.0: Adding scrollwheel support
[    13.422] (**) Microsoft Microsoft® Nano Transceiver v2.0: YAxisMapping: buttons 4 and 5
[    13.422] (**) Microsoft Microsoft® Nano Transceiver v2.0: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    13.422] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.2/input/input7/event7"
[    13.422] (II) XINPUT: Adding extended input device "Microsoft Microsoft® Nano Transceiver v2.0" (type: KEYBOARD)
[    13.422] (**) Option "xkb_rules" "evdev"
[    13.422] (**) Option "xkb_model" "pc105"
[    13.422] (**) Option "xkb_layout" "us"
[    13.422] (EE) Microsoft Microsoft® Nano Transceiver v2.0: failed to initialize for relative axes.
[    13.424] (WW) Touch X valuator does not match pointer X valuator, pointer emulation may be incorrect
[    13.424] (WW) Touch Y valuator does not match pointer Y valuator, pointer emulation may be incorrect
[    13.424] (II) Microsoft Microsoft® Nano Transceiver v2.0: initialized for absolute axes.
[    13.424] (**) Microsoft Microsoft® Nano Transceiver v2.0: (accel) keeping acceleration scheme 1
[    13.424] (**) Microsoft Microsoft® Nano Transceiver v2.0: (accel) acceleration profile 0
[    13.424] (**) Microsoft Microsoft® Nano Transceiver v2.0: (accel) acceleration factor: 2.000
[    13.424] (**) Microsoft Microsoft® Nano Transceiver v2.0: (accel) acceleration threshold: 4
[    13.425] (II) config/udev: Adding input device Microsoft Microsoft® Nano Transceiver v2.0 (/dev/input/js1)
[    13.425] (II) No input driver/identifier specified (ignoring)
[    14.364] (II) intel(0): EDID vendor "SAM", prod id 311
[    14.365] (II) intel(0): Using EDID range info for horizontal sync
[    14.365] (II) intel(0): Using EDID range info for vertical refresh
[    14.365] (II) intel(0): Printing DDC gathered Modelines:
[    14.365] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    14.365] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    14.365] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    14.365] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    14.365] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    14.646] (II) intel(0): EDID vendor "SAM", prod id 311
[    14.646] (II) intel(0): Using hsync ranges from config file
[    14.646] (II) intel(0): Using vrefresh ranges from config file
[    14.646] (II) intel(0): Printing DDC gathered Modelines:
[    14.646] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    14.646] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    14.646] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    14.646] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    14.646] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    14.923] (II) intel(0): EDID vendor "SAM", prod id 311
[    14.924] (II) intel(0): Using hsync ranges from config file
[    14.924] (II) intel(0): Using vrefresh ranges from config file
[    14.924] (II) intel(0): Printing DDC gathered Modelines:
[    14.924] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    14.924] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    14.924] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    14.924] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    14.924] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    14.925] (II) intel(0): Allocated new frame buffer 640x480 stride 2560, tiled
[    15.333] (II) intel(0): EDID vendor "SAM", prod id 311
[    15.334] (II) intel(0): Using hsync ranges from config file
[    15.334] (II) intel(0): Using vrefresh ranges from config file
[    15.334] (II) intel(0): Printing DDC gathered Modelines:
[    15.334] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    15.334] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    15.334] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    15.334] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    15.334] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    20.523] (II) intel(0): EDID vendor "SAM", prod id 311
[    20.524] (II) intel(0): Using hsync ranges from config file
[    20.524] (II) intel(0): Using vrefresh ranges from config file
[    20.524] (II) intel(0): Printing DDC gathered Modelines:
[    20.524] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    20.524] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    20.524] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    20.524] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    20.524] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    97.341] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.341] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.341] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.341] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.341] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.341] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.341] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.341] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.341] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.341] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.341] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.341] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.341] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.341] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.341] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.341] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.341] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.341] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.341] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.341] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.341] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.342] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.342] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.342] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.357] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.357] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.357] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.357] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.357] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.357] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.357] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.357] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.663] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.663] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.663] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.663] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.663] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.663] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.663] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.663] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.670] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.670] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.670] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.670] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.670] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.670] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.670] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.670] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.670] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.670] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.670] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.670] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.670] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.670] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.670] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.670] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.670] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.670] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.670] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.670] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.670] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.670] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.670] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.670] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.670] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.670] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.671] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.671] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.671] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.671] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.671] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
[    97.671] Microsoft Microsoft® Nano Transceiver v2.0: dropping event due to full queue!
```

---

