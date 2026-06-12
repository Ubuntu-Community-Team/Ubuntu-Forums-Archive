---
title: "Nvidia 260.19.26 drivers and kernel 2.6.35-23 = blank screen"
date: 2010-12-02
forum: General Help
---

### Post by drewsus on 2010-12-02
Hello, 
I am using Ubuntu 10.10 with a 1GB Nvidia GeForce 9800 GT card. I used the [x-swat ppa]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates") to get the up to date proprietary drivers. I have installed Ubuntu on a few computers with different cards using the same PPA without any problems and didn't have any until Update Manager updated my kernel to 2.6.35-23. On reboot, my computer now boots to a blank/black screen. 
I can get too tty1+ from here, and I have run 'sudo nvidia-xconfig' and rebooted, but nothing. 
In safe mode I tried resetting to the open drivers, but its the exact same issue. 
I don't know how to fix that. X-Swat updated drivers within the last day but nothing has changed. 
Any help please?! 
Furthermore, my netbook is still at 2.6.35-22. Why would it stay at that, but my desktop would go to 2.6.35-23? They are set up with the same PPAs, etc. 

Drew

---

### Post by nutznboltz on 2010-12-03
Can you post your Xorg.0.log?

You might want to do that via pastbin or gist

---

### Post by nutznboltz on 2010-12-03
Please also post /var/log/messages

---

### Post by drewsus on 2010-12-05
I used pastebin and the code tags so pick your fancy!

Okay, so here is [Xorg.0.log]("http://pastebin.com/XdBm27W3"):
```
[    17.192] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    17.192] X Protocol Version 11, Revision 0
[    17.192] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    17.192] Current Operating System: Linux drewtopia-home 2.6.35-23-generic #41-Ubuntu SMP Wed Nov 24 10:18:49 UTC 2010 i686
[    17.192] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-23-generic root=UUID=d92d1433-775f-4fdd-91a4-d74f164768da ro quiet splash nomodeset video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap
[    17.192] Build Date: 16 September 2010  05:39:22PM
[    17.192] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
[    17.192] Current version of pixman: 0.18.4
[    17.192] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    17.192] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    17.192] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Dec  5 19:53:51 2010
[    17.192] (==) Using config file: "/etc/X11/xorg.conf"
[    17.192] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    17.193] (==) ServerLayout "Layout0"
[    17.193] (**) |-->Screen "Screen0" (0)
[    17.193] (**) |   |-->Monitor "Monitor0"
[    17.193] (**) |   |-->Device "Device0"
[    17.193] (**) |-->Input Device "Keyboard0"
[    17.193] (**) |-->Input Device "Mouse0"
[    17.193] (==) Automatically adding devices
[    17.193] (==) Automatically enabling devices
[    17.193] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    17.193] 	Entry deleted from font path.
[    17.193] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    17.193] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    17.193] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    17.193] (WW) Disabling Keyboard0
[    17.193] (WW) Disabling Mouse0
[    17.193] (II) Loader magic: 0x81f8e00
[    17.193] (II) Module ABI versions:
[    17.193] 	X.Org ANSI C Emulation: 0.4
[    17.193] 	X.Org Video Driver: 8.0
[    17.193] 	X.Org XInput driver : 11.0
[    17.193] 	X.Org Server Extension : 4.0
[    17.194] (--) PCI:*(0:1:0:0) 10de:0640:3842:c959 rev 161, Mem @ 0xfd000000/16777216, 0xd0000000/268435456, 0xfa000000/33554432, I/O @ 0x0000cc00/128, BIOS @ 0x????????/524288
[    17.194] (II) Open ACPI successful (/var/run/acpid.socket)
[    17.194] (II) LoadModule: "extmod"
[    17.200] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    17.200] (II) Module extmod: vendor="X.Org Foundation"
[    17.200] 	compiled for 1.9.0, module version = 1.0.0
[    17.200] 	Module class: X.Org Server Extension
[    17.200] 	ABI class: X.Org Server Extension, version 4.0
[    17.200] (II) Loading extension MIT-SCREEN-SAVER
[    17.200] (II) Loading extension XFree86-VidModeExtension
[    17.200] (II) Loading extension XFree86-DGA
[    17.200] (II) Loading extension DPMS
[    17.200] (II) Loading extension XVideo
[    17.200] (II) Loading extension XVideo-MotionCompensation
[    17.200] (II) Loading extension X-Resource
[    17.200] (II) LoadModule: "dbe"
[    17.200] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    17.200] (II) Module dbe: vendor="X.Org Foundation"
[    17.200] 	compiled for 1.9.0, module version = 1.0.0
[    17.200] 	Module class: X.Org Server Extension
[    17.200] 	ABI class: X.Org Server Extension, version 4.0
[    17.200] (II) Loading extension DOUBLE-BUFFER
[    17.200] (II) LoadModule: "glx"
[    17.200] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    17.220] (II) Module glx: vendor="NVIDIA Corporation"
[    17.220] 	compiled for 4.0.2, module version = 1.0.0
[    17.220] 	Module class: X.Org Server Extension
[    17.220] (II) NVIDIA GLX Module  260.19.26  Sun Nov 28 22:55:54 PST 2010
[    17.220] (II) Loading extension GLX
[    17.220] (II) LoadModule: "record"
[    17.220] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    17.220] (II) Module record: vendor="X.Org Foundation"
[    17.220] 	compiled for 1.9.0, module version = 1.13.0
[    17.220] 	Module class: X.Org Server Extension
[    17.220] 	ABI class: X.Org Server Extension, version 4.0
[    17.220] (II) Loading extension RECORD
[    17.220] (II) LoadModule: "dri"
[    17.220] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    17.221] (II) Module dri: vendor="X.Org Foundation"
[    17.221] 	compiled for 1.9.0, module version = 1.0.0
[    17.221] 	ABI class: X.Org Server Extension, version 4.0
[    17.221] (II) Loading extension XFree86-DRI
[    17.221] (II) LoadModule: "dri2"
[    17.221] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    17.221] (II) Module dri2: vendor="X.Org Foundation"
[    17.221] 	compiled for 1.9.0, module version = 1.2.0
[    17.221] 	ABI class: X.Org Server Extension, version 4.0
[    17.221] (II) Loading extension DRI2
[    17.221] (II) LoadModule: "nvidia"
[    17.221] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    17.221] (II) Module nvidia: vendor="NVIDIA Corporation"
[    17.221] 	compiled for 4.0.2, module version = 1.0.0
[    17.221] 	Module class: X.Org Video Driver
[    17.221] (II) NVIDIA dlloader X Driver  260.19.26  Sun Nov 28 22:39:42 PST 2010
[    17.221] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    17.221] (++) using VT number 7

[    17.222] (II) Loading sub module "fb"
[    17.222] (II) LoadModule: "fb"
[    17.222] (II) Loading /usr/lib/xorg/modules/libfb.so
[    17.222] (II) Module fb: vendor="X.Org Foundation"
[    17.222] 	compiled for 1.9.0, module version = 1.0.0
[    17.222] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    17.222] (II) Loading sub module "wfb"
[    17.222] (II) LoadModule: "wfb"
[    17.223] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    17.223] (II) Module wfb: vendor="X.Org Foundation"
[    17.223] 	compiled for 1.9.0, module version = 1.0.0
[    17.223] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    17.223] (II) Loading sub module "ramdac"
[    17.223] (II) LoadModule: "ramdac"
[    17.223] (II) Module "ramdac" already built-in
[    17.223] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    17.223] (==) NVIDIA(0): RGB weight 888
[    17.223] (==) NVIDIA(0): Default visual is TrueColor
[    17.223] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    17.223] (**) NVIDIA(0): Enabling RENDER acceleration
[    17.223] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[    17.223] (II) NVIDIA(0):     enabled.
[    20.433] (II) NVIDIA(0): NVIDIA GPU GeForce 9500 GT (G96) at PCI:1:0:0 (GPU-0)
[    20.473] (--) NVIDIA(0): Memory: 1048576 kBytes
[    20.473] (--) NVIDIA(0): VideoBIOS: 62.94.73.00.50
[    20.473] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    20.473] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    20.473] (--) NVIDIA(0): Connected display device(s) on GeForce 9500 GT at PCI:1:0:0
[    20.473] (--) NVIDIA(0):     STN S/T 76V (CRT-0)
[    20.473] (--) NVIDIA(0): STN S/T 76V (CRT-0): 400.0 MHz maximum pixel clock
[    20.547] (II) NVIDIA(0): Assigned Display Device: CRT-0
[    20.547] (==) NVIDIA(0): 
[    20.547] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    20.547] (==) NVIDIA(0):     will be used as the requested mode.
[    20.547] (==) NVIDIA(0): 
[    20.547] (II) NVIDIA(0): Validated modes:
[    20.547] (II) NVIDIA(0):     "nvidia-auto-select"
[    20.547] (II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
[    20.571] (--) NVIDIA(0): DPI set to (81, 81); computed from "UseEdidDpi" X config
[    20.571] (--) NVIDIA(0):     option
[    20.571] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[    20.571] (--) Depth 24 pixmap format is 32 bpp
[    20.571] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    20.573] (II) NVIDIA(0): Initialized GPU GART.
[    20.580] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    20.610] (II) Loading extension NV-GLX
[    20.631] (II) NVIDIA(0): Initialized OpenGL Acceleration
[    20.635] (==) NVIDIA(0): Disabling shared memory pixmaps
[    20.635] (II) NVIDIA(0): Initialized X Rendering Acceleration
[    20.635] (==) NVIDIA(0): Backing store disabled
[    20.635] (==) NVIDIA(0): Silken mouse enabled
[    20.641] (**) NVIDIA(0): DPMS enabled
[    20.641] (II) Loading extension NV-CONTROL
[    20.641] (II) Loading extension XINERAMA
[    20.641] (II) Loading sub module "dri2"
[    20.641] (II) LoadModule: "dri2"
[    20.641] (II) Reloading /usr/lib/xorg/modules/extensions/libdri2.so
[    20.641] (II) NVIDIA(0): [DRI2] Setup complete
[    20.641] (==) RandR enabled
[    20.641] (II) Initializing built-in extension Generic Event Extension
[    20.641] (II) Initializing built-in extension SHAPE
[    20.641] (II) Initializing built-in extension MIT-SHM
[    20.642] (II) Initializing built-in extension XInputExtension
[    20.642] (II) Initializing built-in extension XTEST
[    20.642] (II) Initializing built-in extension BIG-REQUESTS
[    20.642] (II) Initializing built-in extension SYNC
[    20.642] (II) Initializing built-in extension XKEYBOARD
[    20.642] (II) Initializing built-in extension XC-MISC
[    20.642] (II) Initializing built-in extension SECURITY
[    20.642] (II) Initializing built-in extension XINERAMA
[    20.642] (II) Initializing built-in extension XFIXES
[    20.642] (II) Initializing built-in extension RENDER
[    20.642] (II) Initializing built-in extension RANDR
[    20.642] (II) Initializing built-in extension COMPOSITE
[    20.642] (II) Initializing built-in extension DAMAGE
[    20.642] (II) Initializing built-in extension GESTURE
[    20.644] (II) Initializing extension GLX
[    20.674] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    20.683] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    20.683] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    20.683] (II) LoadModule: "evdev"
[    20.683] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.683] (II) Module evdev: vendor="X.Org Foundation"
[    20.683] 	compiled for 1.9.0, module version = 2.3.2
[    20.683] 	Module class: X.Org XInput Driver
[    20.683] 	ABI class: X.Org XInput driver, version 11.0
[    20.683] (**) Power Button: always reports core events
[    20.683] (**) Power Button: Device: "/dev/input/event1"
[    20.692] (II) Power Button: Found keys
[    20.692] (II) Power Button: Configuring as keyboard
[    20.692] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    20.692] (**) Option "xkb_rules" "evdev"
[    20.692] (**) Option "xkb_model" "pc105"
[    20.692] (**) Option "xkb_layout" "us"
[    20.694] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    20.694] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    20.694] (**) Power Button: always reports core events
[    20.694] (**) Power Button: Device: "/dev/input/event0"
[    20.708] (II) Power Button: Found keys
[    20.708] (II) Power Button: Configuring as keyboard
[    20.708] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    20.708] (**) Option "xkb_rules" "evdev"
[    20.708] (**) Option "xkb_model" "pc105"
[    20.708] (**) Option "xkb_layout" "us"
[    20.709] (II) config/udev: Adding input device STV06xx (/dev/input/event7)
[    20.709] (**) STV06xx: Applying InputClass "evdev keyboard catchall"
[    20.709] (**) STV06xx: always reports core events
[    20.709] (**) STV06xx: Device: "/dev/input/event7"
[    20.724] (II) STV06xx: Found keys
[    20.724] (II) STV06xx: Configuring as keyboard
[    20.724] (II) XINPUT: Adding extended input device "STV06xx" (type: KEYBOARD)
[    20.724] (**) Option "xkb_rules" "evdev"
[    20.724] (**) Option "xkb_model" "pc105"
[    20.724] (**) Option "xkb_layout" "us"
[    20.725] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event2)
[    20.725] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    20.725] (**) Logitech USB Receiver: always reports core events
[    20.725] (**) Logitech USB Receiver: Device: "/dev/input/event2"
[    20.740] (II) Logitech USB Receiver: Found keys
[    20.740] (II) Logitech USB Receiver: Configuring as keyboard
[    20.740] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    20.740] (**) Option "xkb_rules" "evdev"
[    20.740] (**) Option "xkb_model" "pc105"
[    20.740] (**) Option "xkb_layout" "us"
[    20.741] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event3)
[    20.741] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[    20.741] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    20.741] (**) Logitech USB Receiver: always reports core events
[    20.741] (**) Logitech USB Receiver: Device: "/dev/input/event3"
[    20.756] (II) Logitech USB Receiver: Found 20 mouse buttons
[    20.756] (II) Logitech USB Receiver: Found scroll wheel(s)
[    20.756] (II) Logitech USB Receiver: Found relative axes
[    20.756] (II) Logitech USB Receiver: Found x and y relative axes
[    20.756] (II) Logitech USB Receiver: Found keys
[    20.756] (II) Logitech USB Receiver: Configuring as mouse
[    20.756] (II) Logitech USB Receiver: Configuring as keyboard
[    20.756] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    20.756] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    20.756] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    20.756] (**) Option "xkb_rules" "evdev"
[    20.756] (**) Option "xkb_model" "pc105"
[    20.756] (**) Option "xkb_layout" "us"
[    20.756] (II) Logitech USB Receiver: initialized for relative axes.
[    20.757] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse0)
[    20.757] (II) No input driver/identifier specified (ignoring)
[    20.760] (II) config/udev: Adding input device Microsoft Microsoft® Nano Transceiver v1.0 (/dev/input/event4)
[    20.760] (**) Microsoft Microsoft® Nano Transceiver v1.0: Applying InputClass "evdev keyboard catchall"
[    20.760] (**) Microsoft Microsoft® Nano Transceiver v1.0: always reports core events
[    20.760] (**) Microsoft Microsoft® Nano Transceiver v1.0: Device: "/dev/input/event4"
[    20.772] (II) Microsoft Microsoft® Nano Transceiver v1.0: Found keys
[    20.773] (II) Microsoft Microsoft® Nano Transceiver v1.0: Configuring as keyboard
[    20.773] (II) XINPUT: Adding extended input device "Microsoft Microsoft® Nano Transceiver v1.0" (type: KEYBOARD)
[    20.773] (**) Option "xkb_rules" "evdev"
[    20.773] (**) Option "xkb_model" "pc105"
[    20.773] (**) Option "xkb_layout" "us"
[    20.774] (II) config/udev: Adding input device Microsoft Microsoft® Nano Transceiver v1.0 (/dev/input/event5)
[    20.774] (**) Microsoft Microsoft® Nano Transceiver v1.0: Applying InputClass "evdev pointer catchall"
[    20.774] (**) Microsoft Microsoft® Nano Transceiver v1.0: Applying InputClass "evdev keyboard catchall"
[    20.774] (**) Microsoft Microsoft® Nano Transceiver v1.0: always reports core events
[    20.774] (**) Microsoft Microsoft® Nano Transceiver v1.0: Device: "/dev/input/event5"
[    20.792] (II) Microsoft Microsoft® Nano Transceiver v1.0: Found 9 mouse buttons
[    20.792] (II) Microsoft Microsoft® Nano Transceiver v1.0: Found scroll wheel(s)
[    20.792] (II) Microsoft Microsoft® Nano Transceiver v1.0: Found relative axes
[    20.792] (II) Microsoft Microsoft® Nano Transceiver v1.0: Found x and y relative axes
[    20.792] (II) Microsoft Microsoft® Nano Transceiver v1.0: Found absolute axes
[    20.792] (II) evdev-grail: failed to open grail, no gesture support
[    20.792] (II) Microsoft Microsoft® Nano Transceiver v1.0: Found keys
[    20.792] (II) Microsoft Microsoft® Nano Transceiver v1.0: Configuring as mouse
[    20.792] (II) Microsoft Microsoft® Nano Transceiver v1.0: Configuring as keyboard
[    20.792] (**) Microsoft Microsoft® Nano Transceiver v1.0: YAxisMapping: buttons 4 and 5
[    20.792] (**) Microsoft Microsoft® Nano Transceiver v1.0: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    20.792] (II) XINPUT: Adding extended input device "Microsoft Microsoft® Nano Transceiver v1.0" (type: KEYBOARD)
[    20.792] (**) Option "xkb_rules" "evdev"
[    20.792] (**) Option "xkb_model" "pc105"
[    20.792] (**) Option "xkb_layout" "us"
[    20.792] (II) Microsoft Microsoft® Nano Transceiver v1.0: initialized for relative axes.
[    20.792] (WW) Microsoft Microsoft® Nano Transceiver v1.0: ignoring absolute axes.
[    20.792] (II) config/udev: Adding input device Microsoft Microsoft® Nano Transceiver v1.0 (/dev/input/mouse1)
[    20.792] (II) No input driver/identifier specified (ignoring)
[    20.793] (II) config/udev: Adding input device Microsoft Microsoft® Nano Transceiver v1.0 (/dev/input/event6)
[    20.793] (**) Microsoft Microsoft® Nano Transceiver v1.0: Applying InputClass "evdev keyboard catchall"
[    20.793] (**) Microsoft Microsoft® Nano Transceiver v1.0: always reports core events
[    20.793] (**) Microsoft Microsoft® Nano Transceiver v1.0: Device: "/dev/input/event6"
[    20.812] (II) Microsoft Microsoft® Nano Transceiver v1.0: Found 1 mouse buttons
[    20.812] (II) Microsoft Microsoft® Nano Transceiver v1.0: Found scroll wheel(s)
[    20.812] (II) Microsoft Microsoft® Nano Transceiver v1.0: Found relative axes
[    20.812] (II) Microsoft Microsoft® Nano Transceiver v1.0: Found absolute axes
[    20.812] (II) Microsoft Microsoft® Nano Transceiver v1.0: Found x and y absolute axes
[    20.812] (II) Microsoft Microsoft® Nano Transceiver v1.0: Found keys
[    20.812] (II) Microsoft Microsoft® Nano Transceiver v1.0: Configuring as mouse
[    20.812] (II) Microsoft Microsoft® Nano Transceiver v1.0: Configuring as keyboard
[    20.812] (**) Microsoft Microsoft® Nano Transceiver v1.0: YAxisMapping: buttons 4 and 5
[    20.812] (**) Microsoft Microsoft® Nano Transceiver v1.0: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    20.812] (II) XINPUT: Adding extended input device "Microsoft Microsoft® Nano Transceiver v1.0" (type: KEYBOARD)
[    20.812] (**) Option "xkb_rules" "evdev"
[    20.812] (**) Option "xkb_model" "pc105"
[    20.812] (**) Option "xkb_layout" "us"
[    20.812] (EE) Microsoft Microsoft® Nano Transceiver v1.0: failed to initialize for relative axes.
[    20.812] (WW) Device 'Microsoft Microsoft® Nano Transceiver v1.0' has 37 axes, only using first 36.
[    20.812] (II) Microsoft Microsoft® Nano Transceiver v1.0: initialized for absolute axes.
[    20.812] (II) config/udev: Adding input device Microsoft Microsoft® Nano Transceiver v1.0 (/dev/input/js0)
[    20.812] (II) No input driver/identifier specified (ignoring)
```

and here is [messages]("http://pastebin.com/53egjdUy"):
```
Dec  5 07:20:37 drewtopia-home pulseaudio[1812]: ratelimit.c: 70518 events suppressed
Dec  5 12:39:45 drewtopia-home &#65279;<30>AptDaemon: INFO: InstallFile() was called: /home/drewsus/Downloads/frostwire-4.21.1.i586.deb
Dec  5 12:39:52 drewtopia-home &#65279;<30>AptDaemon.Worker: INFO: Installing local package file: /home/drewsus/Downloads/frostwire-4.21.1.i586.deb
Dec  5 13:23:25 drewtopia-home kernel: [263859.635105] lo: Disabled Privacy Extensions
Dec  5 13:27:05 drewtopia-home kernel: [264079.502107] lo: Disabled Privacy Extensions
Dec  5 14:05:54 drewtopia-home kernel: [266408.467826] ptrace of non-child pid 2675 was attempted by: firefox-bin (pid 2674)
Dec  5 14:05:54 drewtopia-home kernel: [266408.467830] ptrace of non-child pid 2676 was attempted by: firefox-bin (pid 2674)
Dec  5 14:05:54 drewtopia-home kernel: [266408.467833] ptrace of non-child pid 6340 was attempted by: firefox-bin (pid 2674)
Dec  5 14:05:54 drewtopia-home kernel: [266408.467836] ptrace of non-child pid 6341 was attempted by: firefox-bin (pid 2674)
Dec  5 14:06:16 drewtopia-home kernel: [266430.414724] ptrace of non-child pid 15841 was attempted by: firefox-bin (pid 2674)
Dec  5 14:06:16 drewtopia-home kernel: [266430.414727] ptrace of non-child pid 15842 was attempted by: firefox-bin (pid 2674)
Dec  5 14:06:16 drewtopia-home kernel: [266430.414730] ptrace of non-child pid 15864 was attempted by: firefox-bin (pid 2674)
Dec  5 14:06:16 drewtopia-home kernel: [266430.414732] ptrace of non-child pid 15865 was attempted by: firefox-bin (pid 2674)
Dec  5 14:06:54 drewtopia-home kernel: [266469.009024] ptrace of non-child pid 15928 was attempted by: firefox-bin (pid 2674)
Dec  5 14:06:54 drewtopia-home kernel: [266469.009027] ptrace of non-child pid 15929 was attempted by: firefox-bin (pid 2674)
Dec  5 14:06:54 drewtopia-home kernel: [266469.009030] ptrace of non-child pid 15933 was attempted by: firefox-bin (pid 2674)
Dec  5 14:06:54 drewtopia-home kernel: [266469.009033] ptrace of non-child pid 15934 was attempted by: firefox-bin (pid 2674)
Dec  5 14:08:05 drewtopia-home kernel: [266539.177170] ptrace of non-child pid 16039 was attempted by: firefox-bin (pid 2674)
Dec  5 14:08:05 drewtopia-home kernel: [266539.177174] ptrace of non-child pid 16040 was attempted by: firefox-bin (pid 2674)
Dec  5 14:08:05 drewtopia-home kernel: [266539.177177] ptrace of non-child pid 16044 was attempted by: firefox-bin (pid 2674)
Dec  5 14:08:05 drewtopia-home kernel: [266539.177179] ptrace of non-child pid 16045 was attempted by: firefox-bin (pid 2674)
Dec  5 14:08:07 drewtopia-home kernel: [266541.849368] ptrace of non-child pid 16054 was attempted by: firefox-bin (pid 2674)
Dec  5 14:08:07 drewtopia-home kernel: [266541.849372] ptrace of non-child pid 16055 was attempted by: firefox-bin (pid 2674)
Dec  5 14:08:07 drewtopia-home kernel: [266541.849374] ptrace of non-child pid 16059 was attempted by: firefox-bin (pid 2674)
Dec  5 14:08:07 drewtopia-home kernel: [266541.849377] ptrace of non-child pid 16060 was attempted by: firefox-bin (pid 2674)
Dec  5 15:03:59 drewtopia-home kernel: [269893.677183] lo: Disabled Privacy Extensions
Dec  5 15:04:01 drewtopia-home kernel: [269895.383565] lo: Disabled Privacy Extensions
Dec  5 16:03:16 drewtopia-home kernel: [273450.664020] usb 8-1: new full speed USB device using uhci_hcd and address 6
Dec  5 16:03:16 drewtopia-home kernel: [273450.803615] usb 8-1: config 1 has an invalid interface number: 3 but max is 2
Dec  5 16:03:16 drewtopia-home kernel: [273450.803619] usb 8-1: config 1 has 4 interfaces, different from the descriptor's value: 3
Dec  5 16:03:16 drewtopia-home kernel: [273450.816681] cdc_acm 8-1:1.0: ttyACM0: USB ACM device
Dec  5 16:03:16 drewtopia-home kernel: [273450.821690] qcaux 8-1:1.2: qcaux converter detected
Dec  5 16:03:16 drewtopia-home kernel: [273450.821743] usb 8-1: qcaux converter now attached to ttyUSB0
Dec  5 16:03:16 drewtopia-home kernel: [273450.821795] qcaux 8-1:1.3: qcaux converter detected
Dec  5 16:03:16 drewtopia-home kernel: [273450.821843] usb 8-1: qcaux converter now attached to ttyUSB1
Dec  5 16:26:28 drewtopia-home kernel: [274842.453119] ptrace of non-child pid 16094 was attempted by: firefox-bin (pid 2674)
Dec  5 16:26:28 drewtopia-home kernel: [274842.453122] ptrace of non-child pid 16095 was attempted by: firefox-bin (pid 2674)
Dec  5 16:26:28 drewtopia-home kernel: [274842.453125] ptrace of non-child pid 23641 was attempted by: firefox-bin (pid 2674)
Dec  5 16:26:28 drewtopia-home kernel: [274842.453128] ptrace of non-child pid 23642 was attempted by: firefox-bin (pid 2674)
Dec  5 16:26:28 drewtopia-home kernel: [274842.453131] ptrace of non-child pid 26656 was attempted by: firefox-bin (pid 2674)
Dec  5 16:26:28 drewtopia-home kernel: [274842.453134] ptrace of non-child pid 26664 was attempted by: firefox-bin (pid 2674)
Dec  5 16:26:28 drewtopia-home kernel: [274842.453137] ptrace of non-child pid 26665 was attempted by: firefox-bin (pid 2674)
Dec  5 16:26:28 drewtopia-home kernel: [274842.453140] ptrace of non-child pid 26666 was attempted by: firefox-bin (pid 2674)
Dec  5 16:26:28 drewtopia-home kernel: [274842.453142] ptrace of non-child pid 26670 was attempted by: firefox-bin (pid 2674)
Dec  5 16:26:28 drewtopia-home kernel: [274842.453145] ptrace of non-child pid 26677 was attempted by: firefox-bin (pid 2674)
Dec  5 16:26:51 drewtopia-home kernel: [274865.556710] yama_ptrace_access_check: 4 callbacks suppressed
Dec  5 16:26:51 drewtopia-home kernel: [274865.556714] ptrace of non-child pid 555 was attempted by: firefox-bin (pid 2674)
Dec  5 16:26:51 drewtopia-home kernel: [274865.556717] ptrace of non-child pid 556 was attempted by: firefox-bin (pid 2674)
Dec  5 16:26:51 drewtopia-home kernel: [274865.556720] ptrace of non-child pid 560 was attempted by: firefox-bin (pid 2674)
Dec  5 16:26:51 drewtopia-home kernel: [274865.556723] ptrace of non-child pid 561 was attempted by: firefox-bin (pid 2674)
Dec  5 16:26:51 drewtopia-home kernel: [274865.556726] ptrace of non-child pid 564 was attempted by: firefox-bin (pid 2674)
Dec  5 16:26:51 drewtopia-home kernel: [274865.556728] ptrace of non-child pid 568 was attempted by: firefox-bin (pid 2674)
Dec  5 16:26:51 drewtopia-home kernel: [274865.556731] ptrace of non-child pid 569 was attempted by: firefox-bin (pid 2674)
Dec  5 16:26:51 drewtopia-home kernel: [274865.556734] ptrace of non-child pid 587 was attempted by: firefox-bin (pid 2674)
Dec  5 16:26:51 drewtopia-home kernel: [274865.556736] ptrace of non-child pid 588 was attempted by: firefox-bin (pid 2674)
Dec  5 16:26:51 drewtopia-home kernel: [274865.556739] ptrace of non-child pid 590 was attempted by: firefox-bin (pid 2674)
Dec  5 19:52:56 drewtopia-home kernel: [287230.442993] show_signal_msg: 18 callbacks suppressed
Dec  5 19:52:56 drewtopia-home kernel: [287230.442997] indicator-appli[2096]: segfault at 1 ip 0804b8bc sp bff8f560 error 4 in indicator-application-service[8048000+7000]
Dec  5 19:53:47 drewtopia-home kernel: imklog 4.2.0, log source = /proc/kmsg started.
Dec  5 19:53:47 drewtopia-home rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="1260" x-info="http://www.rsyslog.com"] (re)start
Dec  5 19:53:47 drewtopia-home rsyslogd: rsyslogd's groupid changed to 103
Dec  5 19:53:47 drewtopia-home rsyslogd: rsyslogd's userid changed to 101
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] Initializing cgroup subsys cpuset
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] Initializing cgroup subsys cpu
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] Linux version 2.6.35-23-generic (buildd@roseapple) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #41-Ubuntu SMP Wed Nov 24 10:18:49 UTC 2010 (Ubuntu 2.6.35-23.41-generic 2.6.35.7)
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] BIOS-provided physical RAM map:
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007ff80000 (usable)
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]  BIOS-e820: 000000007ff80000 - 000000007ff8e000 (ACPI data)
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]  BIOS-e820: 000000007ff8e000 - 000000007ffe0000 (ACPI NVS)
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]  BIOS-e820: 000000007ffe0000 - 0000000080000000 (reserved)
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] Notice: NX (Execute Disable) protection cannot be enabled: non-PAE kernel!
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] DMI 2.4 present.
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] last_pfn = 0x7ff80 max_arch_pfn = 0x100000
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] Scanning 0 areas for low memory corruption
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] modified physical RAM map:
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]  modified: 0000000000100000 - 000000007ff80000 (usable)
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]  modified: 000000007ff80000 - 000000007ff8e000 (ACPI data)
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]  modified: 000000007ff8e000 - 000000007ffe0000 (ACPI NVS)
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]  modified: 000000007ffe0000 - 0000000080000000 (reserved)
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] found SMP MP-table at [c00ff780] ff780
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] RAMDISK: 37160000 - 37ff0000
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] Allocated new RAMDISK: 009a5000 - 01834594
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] Move RAMDISK from 0000000037160000 - 0000000037fef593 to 009a5000 - 01834593
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] ACPI: RSDP 000fbcd0 00014 (v00 ACPIAM)
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] ACPI: RSDT 7ff80000 0003C (v01 A_M_I_ OEMRSDT  12000724 MSFT 00000097)
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] ACPI: FACP 7ff80200 00084 (v02 A_M_I_ OEMFACP  12000724 MSFT 00000097)
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] ACPI: DSDT 7ff805c0 090A1 (v01  A0751 A0751067 00000067 INTL 20060113)
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] ACPI: FACS 7ff8e000 00040
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] ACPI: APIC 7ff80390 0006C (v01 A_M_I_ OEMAPIC  12000724 MSFT 00000097)
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] ACPI: MCFG 7ff80400 0003C (v01 A_M_I_ OEMMCFG  12000724 MSFT 00000097)
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] ACPI: OEMB 7ff8e040 00081 (v01 A_M_I_ AMI_OEM  12000724 MSFT 00000097)
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] ACPI: HPET 7ff89670 00038 (v01 A_M_I_ OEMHPET  12000724 MSFT 00000097)
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] ACPI: OSFR 7ff896b0 000B0 (v01 A_M_I_ OEMOSFR  12000724 MSFT 00000097)
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] 1159MB HIGHMEM available.
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] 887MB LOWMEM available.
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]   low ram: 0 - 377fe000
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] Zone PFN ranges:
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]   HighMem  0x000377fe -> 0x0007ff80
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] Movable zone start PFN for each node
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] early_node_map[2] active PFN ranges
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]     0: 0x00000100 -> 0x0007ff80
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] Using APIC driver default
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] ACPI: HPET id: 0xffffffff base: 0xfed00000
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:7ee00000)
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @c2c00000 s36416 r0 d20928 u1048576
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] pcpu-alloc: s36416 r0 d20928 u1048576 alloc=1*4194304
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519951
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-23-generic root=UUID=d92d1433-775f-4fdd-91a4-d74f164768da ro quiet splash nomodeset video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] Enabling fast FPU save and restore... done.
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] Initializing CPU#0
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] allocated 10482880 bytes of page_cgroup
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] Subtract (50 early reservations)
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]   #2 [0000100000 - 00009a0adc]   TEXT DATA BSS
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]   #3 [00009a1000 - 00009a420c]             BRK
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]   #4 [00000ff790 - 0000100000]   BIOS reserved
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]   #5 [00000ff780 - 00000ff790]    MP-table mpf
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]   #6 [000009fc00 - 00000f1530]   BIOS reserved
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]   #7 [00000f16a4 - 00000ff780]   BIOS reserved
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]   #8 [00000f1530 - 00000f16a4]    MP-table mpc
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]   #9 [0000010000 - 0000011000]      TRAMPOLINE
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]   #10 [0000011000 - 0000015000]     ACPI WAKEUP
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]   #11 [0000015000 - 0000016000]         PGTABLE
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]   #12 [00009a5000 - 0001835000]     NEW RAMDISK
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]   #13 [0001835000 - 0001836000]         BOOTMEM
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]   #14 [0001836000 - 0002836000]         BOOTMEM
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]   #15 [0002836000 - 0002836004]         BOOTMEM
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]   #16 [0002836040 - 0002836100]         BOOTMEM
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]   #17 [0002836100 - 0002836154]         BOOTMEM
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]   #18 [0002836180 - 0002839180]         BOOTMEM
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]   #19 [0002839180 - 00028391f0]         BOOTMEM
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]   #20 [0002839200 - 000283f200]         BOOTMEM
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]   #21 [000283f200 - 000283f225]         BOOTMEM
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]   #22 [000283f240 - 000283f267]         BOOTMEM
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]   #23 [000283f280 - 000283f398]         BOOTMEM
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]   #24 [000283f3c0 - 000283f400]         BOOTMEM
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]   #25 [000283f400 - 000283f440]         BOOTMEM
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]   #26 [000283f440 - 000283f480]         BOOTMEM
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]   #27 [000283f480 - 000283f4c0]         BOOTMEM
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]   #28 [000283f4c0 - 000283f500]         BOOTMEM
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]   #29 [000283f500 - 000283f540]         BOOTMEM
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]   #30 [000283f540 - 000283f580]         BOOTMEM
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]   #31 [000283f580 - 000283f5c0]         BOOTMEM
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]   #32 [000283f5c0 - 000283f600]         BOOTMEM
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]   #33 [000283f600 - 000283f610]         BOOTMEM
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]   #34 [000283f640 - 000283f6ef]         BOOTMEM
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]   #35 [000283f700 - 000283f7af]         BOOTMEM
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]   #36 [0002c00000 - 0002c0e000]         BOOTMEM
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]   #37 [0002d00000 - 0002d0e000]         BOOTMEM
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]   #38 [0002e00000 - 0002e0e000]         BOOTMEM
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]   #39 [0002f00000 - 0002f0e000]         BOOTMEM
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]   #40 [00028417c0 - 00028417c4]         BOOTMEM
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]   #41 [0002841800 - 0002841804]         BOOTMEM
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]   #42 [0002841840 - 0002841850]         BOOTMEM
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]   #43 [0002841880 - 0002841890]         BOOTMEM
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]   #44 [00028418c0 - 0002841960]         BOOTMEM
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]   #45 [0002841980 - 00028419c8]         BOOTMEM
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]   #46 [0002841a00 - 0002845a00]         BOOTMEM
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]   #47 [0002845a00 - 00028c5a00]         BOOTMEM
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]   #48 [00028c5a00 - 0002905a00]         BOOTMEM
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]   #49 [0002f0e000 - 000390d4c0]         BOOTMEM
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:0007ff80)
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] Memory: 2044720k/2096640k available (4930k kernel code, 51468k reserved, 2334k data, 684k init, 1187336k highmem)
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] virtual kernel memory layout:
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]       .init : 0xc0819000 - 0xc08c4000   ( 684 kB)
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]       .data : 0xc05d0bee - 0xc0818628   (2334 kB)
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000]       .text : 0xc0100000 - 0xc05d0bee   (4930 kB)
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] Hierarchical RCU implementation.
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] 	RCU-based detection of stalled CPUs is disabled.
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] 	Verbose stalled-CPUs detection is disabled.
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] NR_IRQS:2304 nr_irqs:712
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] Console: colour VGA+ 80x25
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] console [tty0] enabled
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] Fast TSC calibration using PIT
Dec  5 19:53:47 drewtopia-home kernel: [    0.000000] Detected 2666.679 MHz processor.
Dec  5 19:53:47 drewtopia-home kernel: [    0.004005] Calibrating delay loop (skipped), value calculated using timer frequency.. 5333.35 BogoMIPS (lpj=10666716)
Dec  5 19:53:47 drewtopia-home kernel: [    0.004009] pid_max: default: 32768 minimum: 301
Dec  5 19:53:47 drewtopia-home kernel: [    0.004025] Security Framework initialized
Dec  5 19:53:47 drewtopia-home kernel: [    0.004039] AppArmor: AppArmor initialized
Dec  5 19:53:47 drewtopia-home kernel: [    0.004040] Yama: becoming mindful.
Dec  5 19:53:47 drewtopia-home kernel: [    0.004085] Mount-cache hash table entries: 512
Dec  5 19:53:47 drewtopia-home kernel: [    0.004193] Initializing cgroup subsys ns
Dec  5 19:53:47 drewtopia-home kernel: [    0.004197] Initializing cgroup subsys cpuacct
Dec  5 19:53:47 drewtopia-home kernel: [    0.004201] Initializing cgroup subsys memory
Dec  5 19:53:47 drewtopia-home kernel: [    0.004208] Initializing cgroup subsys devices
Dec  5 19:53:47 drewtopia-home kernel: [    0.004209] Initializing cgroup subsys freezer
Dec  5 19:53:47 drewtopia-home kernel: [    0.004211] Initializing cgroup subsys net_cls
Dec  5 19:53:47 drewtopia-home kernel: [    0.004235] CPU: Physical Processor ID: 0
Dec  5 19:53:47 drewtopia-home kernel: [    0.004236] CPU: Processor Core ID: 0
Dec  5 19:53:47 drewtopia-home kernel: [    0.004238] mce: CPU supports 6 MCE banks
Dec  5 19:53:47 drewtopia-home kernel: [    0.004245] CPU0: Thermal monitoring enabled (TM2)
Dec  5 19:53:47 drewtopia-home kernel: [    0.004248] using mwait in idle threads.
Dec  5 19:53:47 drewtopia-home kernel: [    0.004254] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
Dec  5 19:53:47 drewtopia-home kernel: [    0.004262] ... version:                2
Dec  5 19:53:47 drewtopia-home kernel: [    0.004263] ... bit width:              40
Dec  5 19:53:47 drewtopia-home kernel: [    0.004265] ... generic registers:      2
Dec  5 19:53:47 drewtopia-home kernel: [    0.004266] ... value mask:             000000ffffffffff
Dec  5 19:53:47 drewtopia-home kernel: [    0.004268] ... max period:             000000007fffffff
Dec  5 19:53:47 drewtopia-home kernel: [    0.004269] ... fixed-purpose events:   3
Dec  5 19:53:47 drewtopia-home kernel: [    0.004271] ... event mask:             0000000700000003
Dec  5 19:53:47 drewtopia-home kernel: [    0.009067] ACPI: Core revision 20100428
Dec  5 19:53:47 drewtopia-home kernel: [    0.020007] ftrace: converting mcount calls to 0f 1f 44 00 00
Dec  5 19:53:47 drewtopia-home kernel: [    0.020011] ftrace: allocating 21766 entries in 43 pages
Dec  5 19:53:47 drewtopia-home kernel: [    0.024034] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Dec  5 19:53:47 drewtopia-home kernel: [    0.024332] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Dec  5 19:53:47 drewtopia-home kernel: [    0.066029] CPU0: Intel(R) Core(TM)2 Duo CPU     E8200  @ 2.66GHz stepping 06
Dec  5 19:53:47 drewtopia-home kernel: [    0.068000] Booting Node   0, Processors  #1
Dec  5 19:53:47 drewtopia-home kernel: [    0.008000] Initializing CPU#1
Dec  5 19:53:47 drewtopia-home kernel: [    0.156013] Brought up 2 CPUs
Dec  5 19:53:47 drewtopia-home kernel: [    0.156016] Total of 2 processors activated (10666.51 BogoMIPS).
Dec  5 19:53:47 drewtopia-home kernel: [    0.156905] devtmpfs: initialized
Dec  5 19:53:47 drewtopia-home kernel: [    0.156905] regulator: core version 0.5
Dec  5 19:53:47 drewtopia-home kernel: [    0.156905] Time: 19:53:34  Date: 12/05/10
Dec  5 19:53:47 drewtopia-home kernel: [    0.156905] NET: Registered protocol family 16
Dec  5 19:53:47 drewtopia-home kernel: [    0.156905] Trying to unpack rootfs image as initramfs...
Dec  5 19:53:47 drewtopia-home kernel: [    0.156942] EISA bus registered
Dec  5 19:53:47 drewtopia-home kernel: [    0.156949] ACPI: bus type pci registered
Dec  5 19:53:47 drewtopia-home kernel: [    0.157010] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Dec  5 19:53:47 drewtopia-home kernel: [    0.157013] PCI: not using MMCONFIG
Dec  5 19:53:47 drewtopia-home kernel: [    0.157166] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=5
Dec  5 19:53:47 drewtopia-home kernel: [    0.157168] PCI: Using configuration type 1 for base access
Dec  5 19:53:47 drewtopia-home kernel: [    0.164130] bio: create slab <bio-0> at 0
Dec  5 19:53:47 drewtopia-home kernel: [    0.166632] ACPI: Executed 1 blocks of module-level executable AML code
Dec  5 19:53:47 drewtopia-home kernel: [    0.176076] ACPI: SSDT 7ff8e0d0 001D2 (v01    AMI   CPU1PM 00000001 INTL 20060113)
Dec  5 19:53:47 drewtopia-home kernel: [    0.176412] ACPI: Dynamic OEM Table Load:
Dec  5 19:53:47 drewtopia-home kernel: [    0.176415] ACPI: SSDT (null) 001D2 (v01    AMI   CPU1PM 00000001 INTL 20060113)
Dec  5 19:53:47 drewtopia-home kernel: [    0.176720] ACPI: SSDT 7ff8e2b0 00143 (v01    AMI   CPU2PM 00000001 INTL 20060113)
Dec  5 19:53:47 drewtopia-home kernel: [    0.177050] ACPI: Dynamic OEM Table Load:
Dec  5 19:53:47 drewtopia-home kernel: [    0.177053] ACPI: SSDT (null) 00143 (v01    AMI   CPU2PM 00000001 INTL 20060113)
Dec  5 19:53:47 drewtopia-home kernel: [    0.177121] ACPI: Interpreter enabled
Dec  5 19:53:47 drewtopia-home kernel: [    0.177124] ACPI: (supports S0 S1 S3 S4 S5)
Dec  5 19:53:47 drewtopia-home kernel: [    0.177145] ACPI: Using IOAPIC for interrupt routing
Dec  5 19:53:47 drewtopia-home kernel: [    0.177189] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Dec  5 19:53:47 drewtopia-home kernel: [    0.178142] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
Dec  5 19:53:47 drewtopia-home kernel: [    0.178144] PCI: Using MMCONFIG for extended config space
Dec  5 19:53:47 drewtopia-home kernel: [    0.186618] ACPI: No dock devices found.
Dec  5 19:53:47 drewtopia-home kernel: [    0.186622] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
Dec  5 19:53:47 drewtopia-home kernel: [    0.186725] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Dec  5 19:53:47 drewtopia-home kernel: [    0.187882] pci 0000:00:1f.0: quirk: [io  0x0800-0x087f] claimed by ICH6 ACPI/GPIO/TCO
Dec  5 19:53:47 drewtopia-home kernel: [    0.187885] pci 0000:00:1f.0: quirk: [io  0x0480-0x04bf] claimed by ICH6 GPIO
Dec  5 19:53:47 drewtopia-home kernel: [    0.187889] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0294 (mask 0003)
Dec  5 19:53:47 drewtopia-home kernel: [    0.188202] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Dec  5 19:53:47 drewtopia-home kernel: [    0.188245] pci 0000:00:1c.0: PCI bridge to [bus 04-04]
Dec  5 19:53:47 drewtopia-home kernel: [    0.188530] pci 0000:03:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
Dec  5 19:53:47 drewtopia-home kernel: [    0.188542] pci 0000:00:1c.4: PCI bridge to [bus 03-03]
Dec  5 19:53:47 drewtopia-home kernel: [    0.188699] pci 0000:02:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
Dec  5 19:53:47 drewtopia-home kernel: [    0.188707] pci 0000:00:1c.5: PCI bridge to [bus 02-02]
Dec  5 19:53:47 drewtopia-home kernel: [    0.188919] pci 0000:00:1e.0: PCI bridge to [bus 05-05] (subtractive decode)
Dec  5 19:53:47 drewtopia-home kernel: [    0.204545] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Dec  5 19:53:47 drewtopia-home kernel: [    0.204642] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
Dec  5 19:53:47 drewtopia-home kernel: [    0.204736] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Dec  5 19:53:47 drewtopia-home kernel: [    0.204832] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 12 *14 15)
Dec  5 19:53:47 drewtopia-home kernel: [    0.204926] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Dec  5 19:53:47 drewtopia-home kernel: [    0.205022] ACPI: PCI Interrupt Link [LNKF] (IRQs *3 4 5 6 7 10 11 12 14 15)
Dec  5 19:53:47 drewtopia-home kernel: [    0.205117] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 *15)
Dec  5 19:53:47 drewtopia-home kernel: [    0.205210] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 10 11 12 14 15)
Dec  5 19:53:47 drewtopia-home kernel: [    0.205252] HEST: Table is not found!
Dec  5 19:53:47 drewtopia-home kernel: [    0.205329] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Dec  5 19:53:47 drewtopia-home kernel: [    0.205334] vgaarb: loaded
Dec  5 19:53:47 drewtopia-home kernel: [    0.205468] SCSI subsystem initialized
Dec  5 19:53:47 drewtopia-home kernel: [    0.205577] usbcore: registered new interface driver usbfs
Dec  5 19:53:47 drewtopia-home kernel: [    0.205587] usbcore: registered new interface driver hub
Dec  5 19:53:47 drewtopia-home kernel: [    0.205606] usbcore: registered new device driver usb
Dec  5 19:53:47 drewtopia-home kernel: [    0.205706] ACPI: WMI: Mapper loaded
Dec  5 19:53:47 drewtopia-home kernel: [    0.205708] PCI: Using ACPI for IRQ routing
Dec  5 19:53:47 drewtopia-home kernel: [    0.205878] NetLabel: Initializing
Dec  5 19:53:47 drewtopia-home kernel: [    0.205879] NetLabel:  domain hash size = 128
Dec  5 19:53:47 drewtopia-home kernel: [    0.205880] NetLabel:  protocols = UNLABELED CIPSOv4
Dec  5 19:53:47 drewtopia-home kernel: [    0.205890] NetLabel:  unlabeled traffic allowed by default
Dec  5 19:53:47 drewtopia-home kernel: [    0.205914] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
Dec  5 19:53:47 drewtopia-home kernel: [    0.205919] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Dec  5 19:53:47 drewtopia-home kernel: [    0.205923] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
Dec  5 19:53:47 drewtopia-home kernel: [    0.216103] Switching to clocksource tsc
Dec  5 19:53:47 drewtopia-home kernel: [    0.224730] AppArmor: AppArmor Filesystem Enabled
Dec  5 19:53:47 drewtopia-home kernel: [    0.224743] pnp: PnP ACPI init
Dec  5 19:53:47 drewtopia-home kernel: [    0.224760] ACPI: bus type pnp registered
Dec  5 19:53:47 drewtopia-home kernel: [    0.227530] pnp: PnP ACPI: found 15 devices
Dec  5 19:53:47 drewtopia-home kernel: [    0.227532] ACPI: ACPI bus type pnp unregistered
Dec  5 19:53:47 drewtopia-home kernel: [    0.227536] PnPBIOS: Disabled by ACPI PNP
Dec  5 19:53:47 drewtopia-home kernel: [    0.227546] system 00:01: [mem 0xfed14000-0xfed19fff] has been reserved
Dec  5 19:53:47 drewtopia-home kernel: [    0.227553] system 00:07: [io  0x0290-0x0297] has been reserved
Dec  5 19:53:47 drewtopia-home kernel: [    0.227557] system 00:08: [io  0x04d0-0x04d1] has been reserved
Dec  5 19:53:47 drewtopia-home kernel: [    0.227559] system 00:08: [io  0x0800-0x087f] has been reserved
Dec  5 19:53:47 drewtopia-home kernel: [    0.227561] system 00:08: [io  0x0480-0x04bf] has been reserved
Dec  5 19:53:47 drewtopia-home kernel: [    0.227564] system 00:08: [mem 0xfed1c000-0xfed1ffff] has been reserved
Dec  5 19:53:47 drewtopia-home kernel: [    0.227566] system 00:08: [mem 0xfed20000-0xfed3ffff] has been reserved
Dec  5 19:53:47 drewtopia-home kernel: [    0.227568] system 00:08: [mem 0xfed50000-0xfed8ffff] has been reserved
Dec  5 19:53:47 drewtopia-home kernel: [    0.227571] system 00:08: [mem 0xffa00000-0xffafffff] has been reserved
Dec  5 19:53:47 drewtopia-home kernel: [    0.227573] system 00:08: [mem 0xffb00000-0xffbfffff] has been reserved
Dec  5 19:53:47 drewtopia-home kernel: [    0.227575] system 00:08: [mem 0xffe00000-0xffefffff] has been reserved
Dec  5 19:53:47 drewtopia-home kernel: [    0.227577] system 00:08: [mem 0xfff00000-0xfffffffe] has been reserved
Dec  5 19:53:47 drewtopia-home kernel: [    0.227582] system 00:0b: [mem 0xfec00000-0xfec00fff] could not be reserved
Dec  5 19:53:47 drewtopia-home kernel: [    0.227584] system 00:0b: [mem 0xfee00000-0xfee00fff] has been reserved
Dec  5 19:53:47 drewtopia-home kernel: [    0.227589] system 00:0d: [mem 0xe0000000-0xefffffff] has been reserved
Dec  5 19:53:47 drewtopia-home kernel: [    0.227594] system 00:0e: [mem 0x00000000-0x0009ffff] could not be reserved
Dec  5 19:53:47 drewtopia-home kernel: [    0.227596] system 00:0e: [mem 0x000c0000-0x000cffff] could not be reserved
Dec  5 19:53:47 drewtopia-home kernel: [    0.227598] system 00:0e: [mem 0x000e0000-0x000fffff] could not be reserved
Dec  5 19:53:47 drewtopia-home kernel: [    0.227600] system 00:0e: [mem 0x00100000-0x7fffffff] could not be reserved
Dec  5 19:53:47 drewtopia-home kernel: [    0.263329] pci 0000:00:1c.0: BAR 14: assigned [mem 0x80000000-0x803fffff]
Dec  5 19:53:47 drewtopia-home kernel: [    0.263333] pci 0000:00:1c.4: BAR 15: assigned [mem 0x80400000-0x805fffff 64bit pref]
Dec  5 19:53:47 drewtopia-home kernel: [    0.263336] pci 0000:00:1c.5: BAR 15: assigned [mem 0x80600000-0x807fffff 64bit pref]
Dec  5 19:53:47 drewtopia-home kernel: [    0.263339] pci 0000:00:1c.0: BAR 13: assigned [io  0x1000-0x1fff]
Dec  5 19:53:47 drewtopia-home kernel: [    0.263341] pci 0000:00:1c.5: BAR 13: assigned [io  0x2000-0x2fff]
Dec  5 19:53:47 drewtopia-home kernel: [    0.263344] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Dec  5 19:53:47 drewtopia-home kernel: [    0.263346] pci 0000:00:01.0:   bridge window [io  0xc000-0xcfff]
Dec  5 19:53:47 drewtopia-home kernel: [    0.263349] pci 0000:00:01.0:   bridge window [mem 0xfa000000-0xfe8fffff]
Dec  5 19:53:47 drewtopia-home kernel: [    0.263352] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
Dec  5 19:53:47 drewtopia-home kernel: [    0.263356] pci 0000:00:1c.0: PCI bridge to [bus 04-04]
Dec  5 19:53:47 drewtopia-home kernel: [    0.263358] pci 0000:00:1c.0:   bridge window [io  0x1000-0x1fff]
Dec  5 19:53:47 drewtopia-home kernel: [    0.263362] pci 0000:00:1c.0:   bridge window [mem 0x80000000-0x803fffff]
Dec  5 19:53:47 drewtopia-home kernel: [    0.263366] pci 0000:00:1c.0:   bridge window [mem 0xf8f00000-0xf8ffffff 64bit pref]
Dec  5 19:53:47 drewtopia-home kernel: [    0.263371] pci 0000:00:1c.4: PCI bridge to [bus 03-03]
Dec  5 19:53:47 drewtopia-home kernel: [    0.263373] pci 0000:00:1c.4:   bridge window [io  0xd000-0xdfff]
Dec  5 19:53:47 drewtopia-home kernel: [    0.263377] pci 0000:00:1c.4:   bridge window [mem 0xfea00000-0xfeafffff]
Dec  5 19:53:47 drewtopia-home kernel: [    0.263381] pci 0000:00:1c.4:   bridge window [mem 0x80400000-0x805fffff 64bit pref]
Dec  5 19:53:47 drewtopia-home kernel: [    0.263386] pci 0000:00:1c.5: PCI bridge to [bus 02-02]
Dec  5 19:53:47 drewtopia-home kernel: [    0.263388] pci 0000:00:1c.5:   bridge window [io  0x2000-0x2fff]
Dec  5 19:53:47 drewtopia-home kernel: [    0.263392] pci 0000:00:1c.5:   bridge window [mem 0xfe900000-0xfe9fffff]
Dec  5 19:53:47 drewtopia-home kernel: [    0.263395] pci 0000:00:1c.5:   bridge window [mem 0x80600000-0x807fffff 64bit pref]
Dec  5 19:53:47 drewtopia-home kernel: [    0.263400] pci 0000:00:1e.0: PCI bridge to [bus 05-05]
Dec  5 19:53:47 drewtopia-home kernel: [    0.263403] pci 0000:00:1e.0:   bridge window [io  0xe000-0xefff]
Dec  5 19:53:47 drewtopia-home kernel: [    0.263407] pci 0000:00:1e.0:   bridge window [mem 0xfeb00000-0xfebfffff]
Dec  5 19:53:47 drewtopia-home kernel: [    0.263410] pci 0000:00:1e.0:   bridge window [mem pref disabled]
Dec  5 19:53:47 drewtopia-home kernel: [    0.263432] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec  5 19:53:47 drewtopia-home kernel: [    0.263443] pci 0000:00:1c.0: enabling device (0106 -> 0107)
Dec  5 19:53:47 drewtopia-home kernel: [    0.263451] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Dec  5 19:53:47 drewtopia-home kernel: [    0.263462] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Dec  5 19:53:47 drewtopia-home kernel: [    0.263473] pci 0000:00:1c.5: enabling device (0106 -> 0107)
Dec  5 19:53:47 drewtopia-home kernel: [    0.263477] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
Dec  5 19:53:47 drewtopia-home kernel: [    0.263573] NET: Registered protocol family 2
Dec  5 19:53:47 drewtopia-home kernel: [    0.263638] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Dec  5 19:53:47 drewtopia-home kernel: [    0.263847] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Dec  5 19:53:47 drewtopia-home kernel: [    0.264271] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Dec  5 19:53:47 drewtopia-home kernel: [    0.264489] TCP: Hash tables configured (established 131072 bind 65536)
Dec  5 19:53:47 drewtopia-home kernel: [    0.264491] TCP reno registered
Dec  5 19:53:47 drewtopia-home kernel: [    0.264493] UDP hash table entries: 512 (order: 2, 16384 bytes)
Dec  5 19:53:47 drewtopia-home kernel: [    0.264501] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
Dec  5 19:53:47 drewtopia-home kernel: [    0.264562] NET: Registered protocol family 1
Dec  5 19:53:47 drewtopia-home kernel: [    0.264870] cpufreq-nforce2: No nForce2 chipset.
Dec  5 19:53:47 drewtopia-home kernel: [    0.264893] Scanning for low memory corruption every 60 seconds
Dec  5 19:53:47 drewtopia-home kernel: [    0.264978] audit: initializing netlink socket (disabled)
Dec  5 19:53:47 drewtopia-home kernel: [    0.264985] type=2000 audit(1291578813.260:1): initialized
Dec  5 19:53:47 drewtopia-home kernel: [    0.273403] highmem bounce pool size: 64 pages
Dec  5 19:53:47 drewtopia-home kernel: [    0.273408] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Dec  5 19:53:47 drewtopia-home kernel: [    0.274818] VFS: Disk quotas dquot_6.5.2
Dec  5 19:53:47 drewtopia-home kernel: [    0.274872] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Dec  5 19:53:47 drewtopia-home kernel: [    0.275343] fuse init (API version 7.14)
Dec  5 19:53:47 drewtopia-home kernel: [    0.275414] msgmni has been set to 1674
Dec  5 19:53:47 drewtopia-home kernel: [    0.275643] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Dec  5 19:53:47 drewtopia-home kernel: [    0.275645] io scheduler noop registered
Dec  5 19:53:47 drewtopia-home kernel: [    0.275647] io scheduler deadline registered
Dec  5 19:53:47 drewtopia-home kernel: [    0.275657] io scheduler cfq registered (default)
Dec  5 19:53:47 drewtopia-home kernel: [    0.276144] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Dec  5 19:53:47 drewtopia-home kernel: [    0.276223] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Dec  5 19:53:47 drewtopia-home kernel: [    0.276386] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Dec  5 19:53:47 drewtopia-home kernel: [    0.276392] ACPI: Power Button [PWRB]
Dec  5 19:53:47 drewtopia-home kernel: [    0.276430] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Dec  5 19:53:47 drewtopia-home kernel: [    0.276433] ACPI: Power Button [PWRF]
Dec  5 19:53:47 drewtopia-home kernel: [    0.278990] ERST: Table is not found!
Dec  5 19:53:47 drewtopia-home kernel: [    0.279157] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Dec  5 19:53:47 drewtopia-home kernel: [    0.279245] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Dec  5 19:53:47 drewtopia-home kernel: [    0.279601] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Dec  5 19:53:47 drewtopia-home kernel: [    0.280591] brd: module loaded
Dec  5 19:53:47 drewtopia-home kernel: [    0.281035] loop: module loaded
Dec  5 19:53:47 drewtopia-home kernel: [    0.281180] ata_piix 0000:00:1f.2: PCI INT B -> GSI 22 (level, low) -> IRQ 22
Dec  5 19:53:47 drewtopia-home kernel: [    0.281184] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
Dec  5 19:53:47 drewtopia-home kernel: [    0.281272] isapnp: Scanning for PnP cards...
Dec  5 19:53:47 drewtopia-home kernel: [    0.286732] scsi0 : ata_piix
Dec  5 19:53:47 drewtopia-home kernel: [    0.286787] scsi1 : ata_piix
Dec  5 19:53:47 drewtopia-home kernel: [    0.288216] ata1: SATA max UDMA/133 cmd 0xa000 ctl 0x9c00 bmdma 0x9480 irq 22
Dec  5 19:53:47 drewtopia-home kernel: [    0.288220] ata2: SATA max UDMA/133 cmd 0x9880 ctl 0x9800 bmdma 0x9488 irq 22
Dec  5 19:53:47 drewtopia-home kernel: [    0.288236] ata_piix 0000:00:1f.5: PCI INT B -> GSI 22 (level, low) -> IRQ 22
Dec  5 19:53:47 drewtopia-home kernel: [    0.288239] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
Dec  5 19:53:47 drewtopia-home kernel: [    0.331727] scsi2 : ata_piix
Dec  5 19:53:47 drewtopia-home kernel: [    0.331824] scsi3 : ata_piix
Dec  5 19:53:47 drewtopia-home kernel: [    0.333150] ata3: SATA max UDMA/133 cmd 0xb000 ctl 0xac00 bmdma 0xa480 irq 22
Dec  5 19:53:47 drewtopia-home kernel: [    0.333154] ata4: SATA max UDMA/133 cmd 0xa880 ctl 0xa800 bmdma 0xa488 irq 22
Dec  5 19:53:47 drewtopia-home kernel: [    0.333213] pata_acpi 0000:03:00.1: enabling device (0000 -> 0001)
Dec  5 19:53:47 drewtopia-home kernel: [    0.333220] pata_acpi 0000:03:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Dec  5 19:53:47 drewtopia-home kernel: [    0.333265] pata_acpi 0000:03:00.1: PCI INT B disabled
Dec  5 19:53:47 drewtopia-home kernel: [    0.333508] Fixed MDIO Bus: probed
Dec  5 19:53:47 drewtopia-home kernel: [    0.333537] PPP generic driver version 2.4.2
Dec  5 19:53:47 drewtopia-home kernel: [    0.333593] tun: Universal TUN/TAP device driver, 1.6
Dec  5 19:53:47 drewtopia-home kernel: [    0.333595] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Dec  5 19:53:47 drewtopia-home kernel: [    0.333668] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Dec  5 19:53:47 drewtopia-home kernel: [    0.333692] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Dec  5 19:53:47 drewtopia-home kernel: [    0.333711] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Dec  5 19:53:47 drewtopia-home kernel: [    0.333738] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
Dec  5 19:53:47 drewtopia-home kernel: [    0.333760] ehci_hcd 0000:00:1a.7: debug port 1
Dec  5 19:53:47 drewtopia-home kernel: [    0.337667] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf9fffc00
Dec  5 19:53:47 drewtopia-home kernel: [    0.385030] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
Dec  5 19:53:47 drewtopia-home kernel: [    0.385164] hub 1-0:1.0: USB hub found
Dec  5 19:53:47 drewtopia-home kernel: [    0.385169] hub 1-0:1.0: 6 ports detected
Dec  5 19:53:47 drewtopia-home kernel: [    0.385252] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Dec  5 19:53:47 drewtopia-home kernel: [    0.385276] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Dec  5 19:53:47 drewtopia-home kernel: [    0.385310] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
Dec  5 19:53:47 drewtopia-home kernel: [    0.385331] ehci_hcd 0000:00:1d.7: debug port 1
Dec  5 19:53:47 drewtopia-home kernel: [    0.389242] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf9fff800
Dec  5 19:53:47 drewtopia-home kernel: [    0.436583] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Dec  5 19:53:47 drewtopia-home kernel: [    0.436724] hub 2-0:1.0: USB hub found
Dec  5 19:53:47 drewtopia-home kernel: [    0.436729] hub 2-0:1.0: 6 ports detected
Dec  5 19:53:47 drewtopia-home kernel: [    0.436804] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Dec  5 19:53:47 drewtopia-home kernel: [    0.436819] uhci_hcd: USB Universal Host Controller Interface driver
Dec  5 19:53:47 drewtopia-home kernel: [    0.436858] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec  5 19:53:47 drewtopia-home kernel: [    0.436869] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Dec  5 19:53:47 drewtopia-home kernel: [    0.436902] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
Dec  5 19:53:47 drewtopia-home kernel: [    0.436935] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000b800
Dec  5 19:53:47 drewtopia-home kernel: [    0.437035] hub 3-0:1.0: USB hub found
Dec  5 19:53:47 drewtopia-home kernel: [    0.437038] hub 3-0:1.0: 2 ports detected
Dec  5 19:53:47 drewtopia-home kernel: [    0.437095] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Dec  5 19:53:47 drewtopia-home kernel: [    0.437103] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Dec  5 19:53:47 drewtopia-home kernel: [    0.437128] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
Dec  5 19:53:47 drewtopia-home kernel: [    0.437155] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000b880
Dec  5 19:53:47 drewtopia-home kernel: [    0.437242] hub 4-0:1.0: USB hub found
Dec  5 19:53:47 drewtopia-home kernel: [    0.437245] hub 4-0:1.0: 2 ports detected
Dec  5 19:53:47 drewtopia-home kernel: [    0.437300] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Dec  5 19:53:47 drewtopia-home kernel: [    0.437307] uhci_hcd 0000:00:1a.2: UHCI Host Controller
Dec  5 19:53:47 drewtopia-home kernel: [    0.437336] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
Dec  5 19:53:47 drewtopia-home kernel: [    0.437356] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000bc00
Dec  5 19:53:47 drewtopia-home kernel: [    0.437447] hub 5-0:1.0: USB hub found
Dec  5 19:53:47 drewtopia-home kernel: [    0.437450] hub 5-0:1.0: 2 ports detected
Dec  5 19:53:47 drewtopia-home kernel: [    0.437499] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Dec  5 19:53:47 drewtopia-home kernel: [    0.437506] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Dec  5 19:53:47 drewtopia-home kernel: [    0.437535] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
Dec  5 19:53:47 drewtopia-home kernel: [    0.437554] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000b080
Dec  5 19:53:47 drewtopia-home kernel: [    0.437644] hub 6-0:1.0: USB hub found
Dec  5 19:53:47 drewtopia-home kernel: [    0.437647] hub 6-0:1.0: 2 ports detected
Dec  5 19:53:47 drewtopia-home kernel: [    0.437699] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Dec  5 19:53:47 drewtopia-home kernel: [    0.437706] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Dec  5 19:53:47 drewtopia-home kernel: [    0.437733] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
Dec  5 19:53:47 drewtopia-home kernel: [    0.437759] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000b400
Dec  5 19:53:47 drewtopia-home kernel: [    0.437845] hub 7-0:1.0: USB hub found
Dec  5 19:53:47 drewtopia-home kernel: [    0.437848] hub 7-0:1.0: 2 ports detected
Dec  5 19:53:47 drewtopia-home kernel: [    0.437900] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Dec  5 19:53:47 drewtopia-home kernel: [    0.437907] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Dec  5 19:53:47 drewtopia-home kernel: [    0.437931] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
Dec  5 19:53:47 drewtopia-home kernel: [    0.437950] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000b480
Dec  5 19:53:47 drewtopia-home kernel: [    0.438038] hub 8-0:1.0: USB hub found
Dec  5 19:53:47 drewtopia-home kernel: [    0.438041] hub 8-0:1.0: 2 ports detected
Dec  5 19:53:47 drewtopia-home kernel: [    0.438148] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
Dec  5 19:53:47 drewtopia-home kernel: [    0.438150] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
Dec  5 19:53:47 drewtopia-home kernel: [    0.438899] serio: i8042 KBD port at 0x60,0x64 irq 1
Dec  5 19:53:47 drewtopia-home kernel: [    0.438958] mice: PS/2 mouse device common for all mice
Dec  5 19:53:47 drewtopia-home kernel: [    0.439045] rtc_cmos 00:03: RTC can wake from S4
Dec  5 19:53:47 drewtopia-home kernel: [    0.439086] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
Dec  5 19:53:47 drewtopia-home kernel: [    0.439107] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
Dec  5 19:53:47 drewtopia-home kernel: [    0.439230] device-mapper: uevent: version 1.0.3
Dec  5 19:53:47 drewtopia-home kernel: [    0.449124] Freeing initrd memory: 14912k freed
Dec  5 19:53:47 drewtopia-home kernel: [    0.453870] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
Dec  5 19:53:47 drewtopia-home kernel: [    0.453947] device-mapper: multipath: version 1.1.1 loaded
Dec  5 19:53:47 drewtopia-home kernel: [    0.453950] device-mapper: multipath round-robin: version 1.0.0 loaded
Dec  5 19:53:47 drewtopia-home kernel: [    0.454065] EISA: Probing bus 0 at eisa.0
Dec  5 19:53:47 drewtopia-home kernel: [    0.454072] Cannot allocate resource for EISA slot 1
Dec  5 19:53:47 drewtopia-home kernel: [    0.454074] Cannot allocate resource for EISA slot 2
Dec  5 19:53:47 drewtopia-home kernel: [    0.454089] EISA: Detected 0 cards.
Dec  5 19:53:47 drewtopia-home kernel: [    0.454147] cpuidle: using governor ladder
Dec  5 19:53:47 drewtopia-home kernel: [    0.454149] cpuidle: using governor menu
Dec  5 19:53:47 drewtopia-home kernel: [    0.454412] TCP cubic registered
Dec  5 19:53:47 drewtopia-home kernel: [    0.454523] NET: Registered protocol family 10
Dec  5 19:53:47 drewtopia-home kernel: [    0.454842] lo: Disabled Privacy Extensions
Dec  5 19:53:47 drewtopia-home kernel: [    0.455031] NET: Registered protocol family 17
Dec  5 19:53:47 drewtopia-home kernel: [    0.455447] Using IPI No-Shortcut mode
Dec  5 19:53:47 drewtopia-home kernel: [    0.455529] registered taskstats version 1
Dec  5 19:53:47 drewtopia-home kernel: [    0.455834]   Magic number: 6:766:899
Dec  5 19:53:47 drewtopia-home kernel: [    0.455924] rtc_cmos 00:03: setting system clock to 2010-12-05 19:53:34 UTC (1291578814)
Dec  5 19:53:47 drewtopia-home kernel: [    0.455926] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Dec  5 19:53:47 drewtopia-home kernel: [    0.455928] EDD information not available.
Dec  5 19:53:47 drewtopia-home kernel: [    0.656352] isapnp: No Plug & Play device found
Dec  5 19:53:47 drewtopia-home kernel: [    0.714007] ata3: SATA link down (SStatus 0 SControl 300)
Dec  5 19:53:47 drewtopia-home kernel: [    0.811522] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Dec  5 19:53:47 drewtopia-home kernel: [    0.820535] ata1.00: ATA-8: WDC WD5000AAKS-00A7B0, 01.03B01, max UDMA/133
Dec  5 19:53:47 drewtopia-home kernel: [    0.820538] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Dec  5 19:53:47 drewtopia-home kernel: [    0.836604] ata1.00: configured for UDMA/133
Dec  5 19:53:47 drewtopia-home kernel: [    0.836723] scsi 0:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-0 01.0 PQ: 0 ANSI: 5
Dec  5 19:53:47 drewtopia-home kernel: [    0.836824] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Dec  5 19:53:47 drewtopia-home kernel: [    0.836836] sd 0:0:0:0: Attached scsi generic sg0 type 0
Dec  5 19:53:47 drewtopia-home kernel: [    0.836865] sd 0:0:0:0: [sda] Write Protect is off
Dec  5 19:53:47 drewtopia-home kernel: [    0.836888] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec  5 19:53:47 drewtopia-home kernel: [    0.837009]  sda: sda1 sda2 <
Dec  5 19:53:47 drewtopia-home kernel: [    0.855523] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Dec  5 19:53:47 drewtopia-home kernel: [    0.857611]  sda5 sda6
Dec  5 19:53:47 drewtopia-home kernel: [    0.894460] ata2.00: ATA-7: MAXTOR STM3500630AS, 3.AAE, max UDMA/133
Dec  5 19:53:47 drewtopia-home kernel: [    0.894464] ata2.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Dec  5 19:53:47 drewtopia-home kernel: [    0.902118]  sda7 >
Dec  5 19:53:47 drewtopia-home kernel: [    0.902398] sd 0:0:0:0: [sda] Attached SCSI disk
Dec  5 19:53:47 drewtopia-home kernel: [    0.931681] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Dec  5 19:53:47 drewtopia-home kernel: [    0.955775] ata4.00: ATA-8: Hitachi HDT721010SLA360, ST6OA31B, max UDMA/133
Dec  5 19:53:47 drewtopia-home kernel: [    0.955778] ata4.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Dec  5 19:53:47 drewtopia-home kernel: [    0.969440] ata2.00: configured for UDMA/133
Dec  5 19:53:47 drewtopia-home kernel: [    0.969523] scsi 1:0:0:0: Direct-Access     ATA      MAXTOR STM350063 3.AA PQ: 0 ANSI: 5
Dec  5 19:53:47 drewtopia-home kernel: [    0.969597] sd 1:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Dec  5 19:53:47 drewtopia-home kernel: [    0.969612] sd 1:0:0:0: Attached scsi generic sg1 type 0
Dec  5 19:53:47 drewtopia-home kernel: [    0.969646] sd 1:0:0:0: [sdb] Write Protect is off
Dec  5 19:53:47 drewtopia-home kernel: [    0.969671] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec  5 19:53:47 drewtopia-home kernel: [    0.969781]  sdb:
Dec  5 19:53:47 drewtopia-home kernel: [    0.971934] ata4.00: configured for UDMA/133
Dec  5 19:53:47 drewtopia-home kernel: [    0.972013] scsi 3:0:0:0: Direct-Access     ATA      Hitachi HDT72101 ST6O PQ: 0 ANSI: 5
Dec  5 19:53:47 drewtopia-home kernel: [    0.972104] sd 3:0:0:0: [sdc] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Dec  5 19:53:47 drewtopia-home kernel: [    0.972123] sd 3:0:0:0: Attached scsi generic sg2 type 0
Dec  5 19:53:47 drewtopia-home kernel: [    0.972145] sd 3:0:0:0: [sdc] Write Protect is off
Dec  5 19:53:47 drewtopia-home kernel: [    0.972169] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec  5 19:53:47 drewtopia-home kernel: [    0.972279]  sdc: sdc1
Dec  5 19:53:47 drewtopia-home kernel: [    0.986959] sd 3:0:0:0: [sdc] Attached SCSI disk
Dec  5 19:53:47 drewtopia-home kernel: [    1.009072]  sdb1
Dec  5 19:53:47 drewtopia-home kernel: [    1.009255] sd 1:0:0:0: [sdb] Attached SCSI disk
Dec  5 19:53:47 drewtopia-home kernel: [    1.009268] Freeing unused kernel memory: 684k freed
Dec  5 19:53:47 drewtopia-home kernel: [    1.009575] Write protecting the kernel text: 4932k
Dec  5 19:53:47 drewtopia-home kernel: [    1.009608] Write protecting the kernel read-only data: 1976k
Dec  5 19:53:47 drewtopia-home kernel: [    1.023396] udev[85]: starting version 163
Dec  5 19:53:47 drewtopia-home kernel: [    1.087108] pata_jmicron 0000:03:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Dec  5 19:53:47 drewtopia-home kernel: [    1.090717] atl1 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Dec  5 19:53:47 drewtopia-home kernel: [    1.090766] atl1 0000:02:00.0: version 2.1.3
Dec  5 19:53:47 drewtopia-home kernel: [    1.095288] Linux agpgart interface v0.103
Dec  5 19:53:47 drewtopia-home kernel: [    1.099543] firewire_ohci 0000:05:03.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec  5 19:53:47 drewtopia-home kernel: [    1.112402] scsi4 : pata_jmicron
Dec  5 19:53:47 drewtopia-home kernel: [    1.123712] Floppy drive(s): fd0 is 1.44M
Dec  5 19:53:47 drewtopia-home kernel: [    1.130647] scsi5 : pata_jmicron
Dec  5 19:53:47 drewtopia-home kernel: [    1.131369] ata5: PATA max UDMA/100 cmd 0xdc00 ctl 0xd880 bmdma 0xd400 irq 17
Dec  5 19:53:47 drewtopia-home kernel: [    1.131372] ata6: PATA max UDMA/100 cmd 0xd800 ctl 0xd480 bmdma 0xd408 irq 17
Dec  5 19:53:47 drewtopia-home kernel: [    1.131684] ahci 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec  5 19:53:47 drewtopia-home kernel: [    1.143668] FDC 0 is a post-1991 82077
Dec  5 19:53:47 drewtopia-home kernel: [    1.144099] ahci 0000:03:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
Dec  5 19:53:47 drewtopia-home kernel: [    1.144103] ahci 0000:03:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
Dec  5 19:53:47 drewtopia-home kernel: [    1.144534] scsi6 : ahci
Dec  5 19:53:47 drewtopia-home kernel: [    1.144770] scsi7 : ahci
Dec  5 19:53:47 drewtopia-home kernel: [    1.144856] ata7: SATA max UDMA/133 abar m8192@0xfeafe000 port 0xfeafe100 irq 16
Dec  5 19:53:47 drewtopia-home kernel: [    1.144860] ata8: SATA max UDMA/133 abar m8192@0xfeafe000 port 0xfeafe180 irq 16
Dec  5 19:53:47 drewtopia-home kernel: [    1.200015] firewire_ohci: Added fw-ohci device 0000:05:03.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x1
Dec  5 19:53:47 drewtopia-home kernel: [    1.216521] usb 3-2: new full speed USB device using uhci_hcd and address 2
Dec  5 19:53:47 drewtopia-home kernel: [    1.292501] ata5.01: ATAPI: HL-DT-ST DVDRAM GSA-4167B, DL13, max UDMA/33
Dec  5 19:53:47 drewtopia-home kernel: [    1.309016] ata5.01: configured for UDMA/33
Dec  5 19:53:47 drewtopia-home kernel: [    1.317788] scsi 4:0:1:0: CD-ROM            HL-DT-ST DVDRAM GSA-4167B DL13 PQ: 0 ANSI: 5
Dec  5 19:53:47 drewtopia-home kernel: [    1.330575] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Dec  5 19:53:47 drewtopia-home kernel: [    1.330578] Uniform CD-ROM driver Revision: 3.20
Dec  5 19:53:47 drewtopia-home kernel: [    1.330732] sr 4:0:1:0: Attached scsi generic sg3 type 5
Dec  5 19:53:47 drewtopia-home kernel: [    1.464524] ata7: SATA link down (SStatus 0 SControl 300)
Dec  5 19:53:47 drewtopia-home kernel: [    1.464553] ata8: SATA link down (SStatus 0 SControl 300)
Dec  5 19:53:47 drewtopia-home kernel: [    1.644006] usb 5-2: new low speed USB device using uhci_hcd and address 2
Dec  5 19:53:47 drewtopia-home kernel: [    1.647066] uvesafb: NVIDIA Corporation, G96 Board - 09730003, Chip Rev   , OEM: NVIDIA, VBE v3.0
Dec  5 19:53:47 drewtopia-home kernel: [    1.657290] uvesafb: protected mode interface info at c000:c440
Dec  5 19:53:47 drewtopia-home kernel: [    1.657292] uvesafb: pmi: set display start = c00cc4a3, set palette = c00cc4fe
Dec  5 19:53:47 drewtopia-home kernel: [    1.657294] uvesafb: pmi: ports = 3b4 3b5 3ba 3c0 3c1 3c4 3c5 3c6 3c7 3c8 3c9 3cc 3ce 3cf 3d0 3d1 3d2 3d3 3d4 3d5 3da 
Dec  5 19:53:47 drewtopia-home kernel: [    1.692555] firewire_core: created device fw0: GUID 0011d800017e30d0, S400
Dec  5 19:53:47 drewtopia-home kernel: [    1.721046] uvesafb: VBIOS/hardware supports DDC2 transfers
Dec  5 19:53:47 drewtopia-home kernel: [    1.783913]       Display is GTF capable
Dec  5 19:53:47 drewtopia-home kernel: [    1.783921] uvesafb: monitor limits: vf = 160 Hz, hf = 70 kHz, clk = 110 MHz
Dec  5 19:53:47 drewtopia-home kernel: [    1.784032] uvesafb: scrolling: ywrap using protected mode interface, yres_virtual=2867
Dec  5 19:53:47 drewtopia-home kernel: [    1.837954] usbcore: registered new interface driver hiddev
Dec  5 19:53:47 drewtopia-home kernel: [    1.851751] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.0/input/input2
Dec  5 19:53:47 drewtopia-home kernel: [    1.851851] generic-usb 0003:046D:C505.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1a.2-2/input0
Dec  5 19:53:47 drewtopia-home kernel: [    1.884423] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.1/input/input3
Dec  5 19:53:47 drewtopia-home kernel: [    1.884733] generic-usb 0003:046D:C505.0002: input,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1a.2-2/input1
Dec  5 19:53:47 drewtopia-home kernel: [    1.884836] usbcore: registered new interface driver usbhid
Dec  5 19:53:47 drewtopia-home kernel: [    1.884837] usbhid: USB HID core driver
Dec  5 19:53:47 drewtopia-home kernel: [    2.068005] usb 8-1: new full speed USB device using uhci_hcd and address 2
Dec  5 19:53:47 drewtopia-home kernel: [    2.127865] Console: switching to colour frame buffer device 160x64
Dec  5 19:53:47 drewtopia-home kernel: [    2.131561] uvesafb: framebuffer at 0xfb000000, mapped to 0xf8200000, using 14336k, total 14336k
Dec  5 19:53:47 drewtopia-home kernel: [    2.131562] fb0: VESA VGA frame buffer device
Dec  5 19:53:47 drewtopia-home kernel: [    2.220945] usb 8-1: config 1 has an invalid interface number: 3 but max is 2
Dec  5 19:53:47 drewtopia-home kernel: [    2.220949] usb 8-1: config 1 has 4 interfaces, different from the descriptor's value: 3
Dec  5 19:53:47 drewtopia-home kernel: [    2.258174] EXT4-fs (sda5): INFO: recovery required on readonly filesystem
Dec  5 19:53:47 drewtopia-home kernel: [    2.258179] EXT4-fs (sda5): write access will be enabled during recovery
Dec  5 19:53:47 drewtopia-home kernel: [    2.480011] usb 8-2: new full speed USB device using uhci_hcd and address 3
Dec  5 19:53:47 drewtopia-home kernel: [    2.657340] input: Microsoft Microsoft® Nano Transceiver v1.0 as /devices/pci0000:00/0000:00:1d.2/usb8/8-2/8-2:1.0/input/input4
Dec  5 19:53:47 drewtopia-home kernel: [    2.657396] generic-usb 0003:045E:0745.0003: input,hidraw2: USB HID v1.11 Keyboard [Microsoft Microsoft® Nano Transceiver v1.0] on usb-0000:00:1d.2-2/input0
Dec  5 19:53:47 drewtopia-home kernel: [    2.665316] input: Microsoft Microsoft® Nano Transceiver v1.0 as /devices/pci0000:00/0000:00:1d.2/usb8/8-2/8-2:1.1/input/input5
Dec  5 19:53:47 drewtopia-home kernel: [    2.665386] generic-usb 0003:045E:0745.0004: input,hidraw3: USB HID v1.11 Mouse [Microsoft Microsoft® Nano Transceiver v1.0] on usb-0000:00:1d.2-2/input1
Dec  5 19:53:47 drewtopia-home kernel: [    2.690121] input: Microsoft Microsoft® Nano Transceiver v1.0 as /devices/pci0000:00/0000:00:1d.2/usb8/8-2/8-2:1.2/input/input6
Dec  5 19:53:47 drewtopia-home kernel: [    2.690211] generic-usb 0003:045E:0745.0005: input,hiddev96,hidraw4: USB HID v1.11 Device [Microsoft Microsoft® Nano Transceiver v1.0] on usb-0000:00:1d.2-2/input2
Dec  5 19:53:47 drewtopia-home kernel: [    4.269311] EXT4-fs (sda5): recovery complete
Dec  5 19:53:47 drewtopia-home kernel: [    4.269700] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
Dec  5 19:53:47 drewtopia-home kernel: [   10.734975] udev[455]: starting version 163
Dec  5 19:53:47 drewtopia-home kernel: [   10.840630] lp: driver loaded but no devices found
Dec  5 19:53:47 drewtopia-home kernel: [   10.869262] Adding 3998716k swap on /dev/sda6.  Priority:-1 extents:1 across:3998716k 
Dec  5 19:53:47 drewtopia-home kernel: [   10.939900] Linux video capture interface: v2.00
Dec  5 19:53:47 drewtopia-home kernel: [   10.942191] gspca: main v2.9.0 registered
Dec  5 19:53:47 drewtopia-home kernel: [   10.943135] STV06xx: Probing for a stv06xx device
Dec  5 19:53:47 drewtopia-home kernel: [   10.943137] gspca: probing 046d:08f0
Dec  5 19:53:47 drewtopia-home kernel: [   10.943139] STV06xx: Configuring camera
Dec  5 19:53:47 drewtopia-home kernel: [   10.943140] STV06xx: st6422 sensor detected
Dec  5 19:53:47 drewtopia-home kernel: [   10.943144] STV06xx: Initializing camera
Dec  5 19:53:47 drewtopia-home kernel: [   11.025185] cfg80211: Calling CRDA to update world regulatory domain
Dec  5 19:53:47 drewtopia-home kernel: [   11.054045] type=1400 audit(1291596825.093:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=768 comm="apparmor_parser"
Dec  5 19:53:47 drewtopia-home kernel: [   11.054583] type=1400 audit(1291596825.093:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=768 comm="apparmor_parser"
Dec  5 19:53:47 drewtopia-home kernel: [   11.054877] type=1400 audit(1291596825.093:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=768 comm="apparmor_parser"
Dec  5 19:53:47 drewtopia-home kernel: [   11.065688] type=1400 audit(1291596825.105:5): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=807 comm="apparmor_parser"
Dec  5 19:53:47 drewtopia-home kernel: [   11.075085] rtl8180 0000:05:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Dec  5 19:53:47 drewtopia-home kernel: [   11.082455] cfg80211: World regulatory domain updated:
Dec  5 19:53:47 drewtopia-home kernel: [   11.082458]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Dec  5 19:53:47 drewtopia-home kernel: [   11.082460]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec  5 19:53:47 drewtopia-home kernel: [   11.082462]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Dec  5 19:53:47 drewtopia-home kernel: [   11.082464]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Dec  5 19:53:47 drewtopia-home kernel: [   11.082466]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec  5 19:53:47 drewtopia-home kernel: [   11.082468]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec  5 19:53:47 drewtopia-home kernel: [   11.084951] nvidia: module license 'NVIDIA' taints kernel.
Dec  5 19:53:47 drewtopia-home kernel: [   11.084954] Disabling lock debugging due to kernel taint
Dec  5 19:53:47 drewtopia-home kernel: [   11.125437] cdc_acm 8-1:1.0: ttyACM0: USB ACM device
Dec  5 19:53:47 drewtopia-home kernel: [   11.130807] usbcore: registered new interface driver cdc_acm
Dec  5 19:53:47 drewtopia-home kernel: [   11.130809] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
Dec  5 19:53:47 drewtopia-home kernel: [   11.158002] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Dec  5 19:53:47 drewtopia-home kernel: [   11.203630] phy0: hwaddr 00:17:3f:31:ad:c4, RTL8185vD + rtl8225z2
Dec  5 19:53:47 drewtopia-home kernel: [   11.214336] usbcore: registered new interface driver usbserial
Dec  5 19:53:47 drewtopia-home kernel: [   11.214368] USB Serial support registered for generic
Dec  5 19:53:47 drewtopia-home kernel: [   11.222871] hda_codec: ALC883: BIOS auto-probing.
Dec  5 19:53:47 drewtopia-home kernel: [   11.259761] input: STV06xx as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/input/input7
Dec  5 19:53:47 drewtopia-home kernel: [   11.259829] gspca: video0 created
Dec  5 19:53:47 drewtopia-home kernel: [   11.259832] gspca: found int in endpoint: 0x82, buffer_len=1, interval=16
Dec  5 19:53:47 drewtopia-home kernel: [   11.259848] STV06xx: Probing for a stv06xx device
Dec  5 19:53:47 drewtopia-home kernel: [   11.259849] gspca: probing 046d:08f0
Dec  5 19:53:47 drewtopia-home kernel: [   11.259855] STV06xx: Probing for a stv06xx device
Dec  5 19:53:47 drewtopia-home kernel: [   11.259856] gspca: probing 046d:08f0
Dec  5 19:53:47 drewtopia-home kernel: [   11.259876] usbcore: registered new interface driver STV06xx
Dec  5 19:53:47 drewtopia-home kernel: [   11.259878] STV06xx: registered
Dec  5 19:53:47 drewtopia-home kernel: [   11.263224] quickcam_messenger: v0.01:Logitech Quickcam Messenger USB
Dec  5 19:53:47 drewtopia-home kernel: [   11.263253] usbcore: registered new interface driver QCM
Dec  5 19:53:47 drewtopia-home kernel: [   11.263685] usbcore: registered new interface driver usbserial_generic
Dec  5 19:53:47 drewtopia-home kernel: [   11.263688] usbserial: USB Serial Driver core
Dec  5 19:53:47 drewtopia-home kernel: [   11.302837] usbcore: registered new interface driver snd-usb-audio
Dec  5 19:53:47 drewtopia-home kernel: [   11.946180] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec  5 19:53:47 drewtopia-home kernel: [   11.946192] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
Dec  5 19:53:47 drewtopia-home kernel: [   11.946335] NVRM: loading NVIDIA UNIX x86 Kernel Module  260.19.26  Sun Nov 28 22:38:24 PST 2010
Dec  5 19:53:47 drewtopia-home kernel: [   12.003153] USB Serial support registered for qcaux
Dec  5 19:53:47 drewtopia-home kernel: [   12.003178] qcaux 8-1:1.2: qcaux converter detected
Dec  5 19:53:47 drewtopia-home kernel: [   12.003249] usb 8-1: qcaux converter now attached to ttyUSB0
Dec  5 19:53:47 drewtopia-home kernel: [   12.003256] qcaux 8-1:1.3: qcaux converter detected
Dec  5 19:53:47 drewtopia-home kernel: [   12.003296] usb 8-1: qcaux converter now attached to ttyUSB1
Dec  5 19:53:47 drewtopia-home kernel: [   12.003307] usbcore: registered new interface driver qcaux
Dec  5 19:53:47 drewtopia-home kernel: [   13.020324] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
Dec  5 19:53:47 drewtopia-home kernel: [   13.830590] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
Dec  5 19:53:48 drewtopia-home kernel: [   13.977040] atl1 0000:02:00.0: eth0 link is up 100 Mbps full duplex
Dec  5 19:53:48 drewtopia-home kernel: [   13.982942] ppdev: user-space parallel port driver
Dec  5 19:53:48 drewtopia-home kernel: [   14.007427] type=1400 audit(1291596828.045:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=1375 comm="apparmor_parser"
Dec  5 19:53:48 drewtopia-home kernel: [   14.007970] type=1400 audit(1291596828.045:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1375 comm="apparmor_parser"
Dec  5 19:53:48 drewtopia-home kernel: [   14.008269] type=1400 audit(1291596828.049:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1375 comm="apparmor_parser"
Dec  5 19:53:48 drewtopia-home kernel: [   14.012860] type=1400 audit(1291596828.053:9): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1374 comm="apparmor_parser"
Dec  5 19:53:48 drewtopia-home kernel: [   14.035392] type=1400 audit(1291596828.073:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1377 comm="apparmor_parser"
Dec  5 19:53:48 drewtopia-home kernel: [   14.046728] type=1400 audit(1291596828.085:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=1377 comm="apparmor_parser"
Dec  5 19:53:48 drewtopia-home kernel: [   14.581069] vboxdrv: fAsync=0 offMin=0x198 offMax=0x690
Dec  5 19:53:48 drewtopia-home kernel: [   14.581493] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Dec  5 19:53:54 drewtopia-home kernel: [   19.740662] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Dec  5 19:53:55 drewtopia-home kernel: [   21.091418] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
Dec  5 19:53:55 drewtopia-home kernel: [   21.159120] EXT4-fs (sda7): re-mounted. Opts: commit=0
Dec  5 19:53:55 drewtopia-home pulseaudio[1875]: lock-autospawn.c: Cannot access autospawn lock.
```

---

### Post by WakkiTabakki on 2010-12-07
Hi

Just in case you didn't already know...

For me this workaround gets X up and running: 
switch to a tty and run 
```
sudo service gdm restart
```

I've had this same problem since 10.04, and still do (did a dist-upgrade from 10.04 to 10.10). I'm not sure exactly when the problem started. It might have been when experimenting with some nvidia beta-driver; but, again, not sure...

I've since tried a whole bunch of different nvidia driver version to no avail...

All the best
/N

---

### Post by drewsus on 2010-12-07
Okay, well, "sudo service gdm restart" definitely allowed me to boot up sans safe mode. Thank you. 
However, thats not a very user friendly way to start the computer. I think I tracked it down to a plymouth theme I installed. I reverted to a different one and the issue seems to have gone away. That particular theme must not have been compatible with the new kernel. 
Thank you fellows.

---

### Post by WakkiTabakki on 2010-12-08
Brilliant, drewsus! That was it!

I had been trying for quite a while to figure out why it booted into a black screen. As I had been fiddling with a bunch of nVidia beta drivers, I just figured that some old residue of those were messing with X... Turned out is was indeed a dodgy plymouth-theme; I reverted to default theme and it started up fine! Sweet!

How to revert plymouth-theme:
```

sudo update-alternatives --config default.plymouth
sudo update-initramfs -u

```
The first command should present a number of choices; choose "auto mode" (should be option 0).

And, you're of course right; my previous post was certainly not a solution, but rather a workaround to get the desktop up and running. But, thanks for finding the real cause of the problem!

Could you mark the thread as "solved"?

Cheers
N

---

### Post by drewsus on 2010-12-08
Ha, wicked, I'm really glad that I could in turn help you out WakkiTabakki! 
Sorry I didn't post the "how to fix-it" in my previous post. Thats normally not like me. I'm usually far too verbose!
Marked as solved (I passed out before doing that last post - finals time!)
Drew

**edit**
and for the record, the offending plymouth theme was Spinfinity although I cannot seem to find where I downloaded it to tell them. I think I may have downloaded it directly in a plymouth manager program. 

**edit 2: return of the editor**
yes, the package was 'plymouth-theme-spinfinity' installed from within 'plymouth-manager'

---

