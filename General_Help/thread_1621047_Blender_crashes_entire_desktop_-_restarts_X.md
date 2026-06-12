---
title: "Blender crashes entire desktop - restarts X"
date: 2010-11-13
forum: General Help
---

### Post by Shootfast on 2010-11-13
Hi,

I'm having a problem where whenever I start the 3d modelling app Blender, my entire desktop session crashes and I'm left at the login prompt.

I tried the version of blender in the repository, as well as the latest from blender.org.

The file /var/log/gdm/:0.log.1 has the following:
```

X.Org X Server 1.9.0
Release Date: 2010-08-20
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux Mark-PC 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:45:36 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=1a24061a-b25c-4bb1-b0e9-10a7a7dc82e1 ro quiet splash
Build Date: 16 September 2010  06:18:41PM
xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.18.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Nov 14 10:03:17 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Screen "Screen1" (1)
(**) |   |-->Monitor "Monitor1"
(**) |   |-->Device "Device1"
(**) |-->Screen "Screen2" (2)
(**) |   |-->Monitor "Monitor2"
(**) |   |-->Device "Device2"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(==) Automatically adding devices
(==) Automatically enabling devices
(**) Xinerama: enabled
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
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(--) PCI: (0:4:0:0) 10de:05eb:10de:0705 rev 161, Mem @ 0xdc000000/16777216, 0xb0000000/268435456, 0xda000000/33554432, I/O @ 0x0000df00/128, BIOS @ 0x????????/524288
(--) PCI:*(0:5:0:0) 10de:05eb:10de:0705 rev 161, Mem @ 0xd8000000/16777216, 0xa0000000/268435456, 0xd6000000/33554432, I/O @ 0x0000cf00/128, BIOS @ 0x????????/524288
(--) PCI: (0:7:0:0) 10de:06e4:1043:82b2 rev 161, Mem @ 0xf8000000/16777216, 0xc0000000/268435456, 0xf6000000/33554432, I/O @ 0x0000ef00/128, BIOS @ 0x????????/131072
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.9.0, module version = 1.0.0
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.9.0, module version = 1.0.0
(II) Loading /usr/lib/xorg/extra-modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
(II) NVIDIA GLX Module  260.19.06  Mon Sep 13 04:54:41 PDT 2010
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.9.0, module version = 1.13.0
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.9.0, module version = 1.0.0
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.9.0, module version = 1.2.0
(II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
(II) NVIDIA dlloader X Driver  260.19.06  Mon Sep 13 04:31:43 PDT 2010
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(--) using VT number 8

(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.9.0, module version = 1.0.0
(II) Loading /usr/lib/xorg/modules/libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.9.0, module version = 1.0.0
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 8400 GS (G98) at PCI:7:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 62.98.2c.00.00
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 8400 GS at PCI:7:0:0
(--) NVIDIA(0):     BenQ G2411HD (DFP-0)
(--) NVIDIA(0): BenQ G2411HD (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): BenQ G2411HD (DFP-0): Internal Dual Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select+0+0"
(II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
(--) NVIDIA(0): DPI set to (92, 91); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(WW) NVIDIA(0): 32-bit ARGB GLX visuals are not currently supported with the
(WW) NVIDIA(0):     Xinerama extension.
(WW) NVIDIA(0): Disabling 32-bit ARGB GLX visuals.
(**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(1): RGB weight 888
(==) NVIDIA(1): Default visual is TrueColor
(==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(1): Enabling RENDER acceleration
(II) NVIDIA(1): NVIDIA GPU GeForce GTX 295 (GT200) at PCI:5:0:0 (GPU-1)
(--) NVIDIA(1): Memory: 917504 kBytes
(--) NVIDIA(1): VideoBIOS: 62.00.6c.00.01
(II) NVIDIA(1): Detected PCI Express Link width: 16X
(--) NVIDIA(1): Interlaced video modes are supported on this GPU
(--) NVIDIA(1): Connected display device(s) on GeForce GTX 295 at PCI:5:0:0
(--) NVIDIA(1):     BenQ G2411HD (DFP-0)
(--) NVIDIA(1):     BenQ G2411HD (DFP-1)
(--) NVIDIA(1): BenQ G2411HD (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(1): BenQ G2411HD (DFP-0): Internal Dual Link TMDS
(--) NVIDIA(1): BenQ G2411HD (DFP-1): 330.0 MHz maximum pixel clock
(--) NVIDIA(1): BenQ G2411HD (DFP-1): Internal Dual Link TMDS
(II) NVIDIA(1): Display Device found referenced in MetaMode: DFP-0
(II) NVIDIA(1): Assigned Display Device: DFP-0
(II) NVIDIA(1): Validated modes:
(II) NVIDIA(1):     "DFP-0:nvidia-auto-select+0+0"
(II) NVIDIA(1): Virtual screen size determined to be 1920 x 1080
(--) NVIDIA(1): DPI set to (92, 91); computed from "UseEdidDpi" X config
(--) NVIDIA(1):     option
(WW) NVIDIA(1): 32-bit ARGB GLX visuals are not currently supported with the
(WW) NVIDIA(1):     Xinerama extension.
(WW) NVIDIA(1): Disabling 32-bit ARGB GLX visuals.
(**) NVIDIA(2): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(2): RGB weight 888
(==) NVIDIA(2): Default visual is TrueColor
(==) NVIDIA(2): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(2): Enabling RENDER acceleration
(II) NVIDIA(2): NVIDIA GPU GeForce GTX 295 (GT200) at PCI:5:0:0 (GPU-1)
(--) NVIDIA(2): Memory: 917504 kBytes
(--) NVIDIA(2): VideoBIOS: 62.00.6c.00.01
(II) NVIDIA(2): Detected PCI Express Link width: 16X
(--) NVIDIA(2): Interlaced video modes are supported on this GPU
(--) NVIDIA(2): Connected display device(s) on GeForce GTX 295 at PCI:5:0:0
(--) NVIDIA(2):     BenQ G2411HD (DFP-0)
(--) NVIDIA(2):     BenQ G2411HD (DFP-1)
(--) NVIDIA(2): BenQ G2411HD (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(2): BenQ G2411HD (DFP-0): Internal Dual Link TMDS
(--) NVIDIA(2): BenQ G2411HD (DFP-1): 330.0 MHz maximum pixel clock
(--) NVIDIA(2): BenQ G2411HD (DFP-1): Internal Dual Link TMDS
(II) NVIDIA(2): Display Device found referenced in MetaMode: DFP-1
(II) NVIDIA(2): Assigned Display Device: DFP-1
(II) NVIDIA(2): Validated modes:
(II) NVIDIA(2):     "DFP-1:nvidia-auto-select+0+0"
(II) NVIDIA(2): Virtual screen size determined to be 1920 x 1080
(--) NVIDIA(2): DPI set to (92, 91); computed from "UseEdidDpi" X config
(--) NVIDIA(2):     option
(WW) NVIDIA(2): 32-bit ARGB GLX visuals are not currently supported with the
(WW) NVIDIA(2):     Xinerama extension.
(WW) NVIDIA(2): Disabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
(WW) NVIDIA(0): Failed to enable display hotplug notification
(II) NVIDIA(GPU-2): NVIDIA GPU GeForce GTX 295 (GT200) at PCI:4:0:0 (GPU-2)
(--) NVIDIA(GPU-2): Memory: 917504 kBytes
(--) NVIDIA(GPU-2): VideoBIOS: 62.00.6c.00.02
(II) NVIDIA(GPU-2): Detected PCI Express Link width: 16X
(--) NVIDIA(GPU-2): Interlaced video modes are supported on this GPU
(--) NVIDIA(GPU-2): Connected display device(s) on GeForce GTX 295 at PCI:4:0:0
(--) NVIDIA(GPU-2):     none
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Setting mode "nvidia-auto-select+0+0"
(II) NVIDIA(0): Initialized OpenGL Acceleration
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) NVIDIA(0): Initialized X Rendering Acceleration
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) NVIDIA(0): DPMS enabled
(II) NVIDIA(0): [DRI2] Setup complete
(==) RandR enabled
(II) NVIDIA(1): Initialized GPU GART.
(II) NVIDIA(1): Setting mode "DFP-0:nvidia-auto-select+0+0"
(II) NVIDIA(1): Initialized OpenGL Acceleration
(==) NVIDIA(1): Disabling shared memory pixmaps
(II) NVIDIA(1): Initialized X Rendering Acceleration
(==) NVIDIA(1): Backing store disabled
(==) NVIDIA(1): Silken mouse enabled
(==) NVIDIA(1): DPMS enabled
(II) NVIDIA(1): [DRI2] Setup complete
(==) RandR enabled
(II) NVIDIA(2): Initialized GPU GART.
(II) NVIDIA(2): Setting mode "DFP-1:nvidia-auto-select+0+0"
(II) NVIDIA(2): Initialized OpenGL Acceleration
(==) NVIDIA(2): Disabling shared memory pixmaps
(II) NVIDIA(2): Initialized X Rendering Acceleration
(==) NVIDIA(2): Backing store disabled
(==) NVIDIA(2): Silken mouse enabled
(==) NVIDIA(2): DPMS enabled
(II) NVIDIA(2): [DRI2] Setup complete
(==) RandR enabled
(II) Initializing extension GLX
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.9.0, module version = 2.3.2
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(II) config/udev: Adding input device Logitech Logitech BT Mini-Receiver (/dev/input/event2)
(**) Logitech Logitech BT Mini-Receiver: Applying InputClass "evdev keyboard catchall"
(**) Logitech Logitech BT Mini-Receiver: always reports core events
(**) Logitech Logitech BT Mini-Receiver: Device: "/dev/input/event2"
(II) Logitech Logitech BT Mini-Receiver: Found keys
(II) Logitech Logitech BT Mini-Receiver: Configuring as keyboard
(II) XINPUT: Adding extended input device "Logitech Logitech BT Mini-Receiver" (type: KEYBOARD)
(II) config/udev: Adding input device Logitech Logitech BT Mini-Receiver (/dev/input/event3)
(**) Logitech Logitech BT Mini-Receiver: Applying InputClass "evdev pointer catchall"
(**) Logitech Logitech BT Mini-Receiver: Applying InputClass "evdev keyboard catchall"
(**) Logitech Logitech BT Mini-Receiver: always reports core events
(**) Logitech Logitech BT Mini-Receiver: Device: "/dev/input/event3"
(II) Logitech Logitech BT Mini-Receiver: Found 16 mouse buttons
(II) Logitech Logitech BT Mini-Receiver: Found scroll wheel(s)
(II) Logitech Logitech BT Mini-Receiver: Found relative axes
(II) Logitech Logitech BT Mini-Receiver: Found x and y relative axes
(II) Logitech Logitech BT Mini-Receiver: Found absolute axes
(II) evdev-grail: failed to open grail, no gesture support
(II) Logitech Logitech BT Mini-Receiver: Found keys
(II) Logitech Logitech BT Mini-Receiver: Configuring as mouse
(II) Logitech Logitech BT Mini-Receiver: Configuring as keyboard
(**) Logitech Logitech BT Mini-Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech Logitech BT Mini-Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech Logitech BT Mini-Receiver" (type: KEYBOARD)
(II) Logitech Logitech BT Mini-Receiver: initialized for relative axes.
(WW) Logitech Logitech BT Mini-Receiver: ignoring absolute axes.
(II) config/udev: Adding input device Logitech Logitech BT Mini-Receiver (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)

Backtrace:
0: /usr/bin/X (xorg_backtrace+0x28) [0x4a0fa8]
1: /usr/bin/X (0x400000+0x60fcd) [0x460fcd]
2: /lib/libpthread.so.0 (0x7ff4a5d98000+0xfb40) [0x7ff4a5da7b40]
3: /usr/bin/X (0x400000+0xbb22f) [0x4bb22f]
4: /usr/bin/X (0x400000+0x2c2d9) [0x42c2d9]
5: /usr/bin/X (0x400000+0x2184b) [0x42184b]
6: /lib/libc.so.6 (__libc_start_main+0xfe) [0x7ff4a4d03d8e]
7: /usr/bin/X (0x400000+0x213d9) [0x4213d9]
Segmentation fault at address 0x4

Caught signal 11 (Segmentation fault). Server aborting

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

(II) Power Button: Close
(II) Power Button: Close
(II) Logitech Logitech BT Mini-Receiver: Close
(II) Logitech Logitech BT Mini-Receiver: Close
(WW) xf86CloseConsole: VT_WAITACTIVE failed: Interrupted system call
 ddxSigGiveUp: Closing log


```

The Xorg.0.log file shows no errors (as it looks like a clean restart ox X)

Any ideas? I have an Nvidia GTX 295 and Nvidia 8400 GS powering 3 screens using Xinerama.

Thanks

---

