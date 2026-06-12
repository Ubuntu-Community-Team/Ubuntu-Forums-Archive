---
title: "USB controller appearing as a mouse"
date: 2010-04-06
forum: General Help
---

### Post by steamedhams on 2010-04-06
Hi, I'm having a bit of a tussle with X at the moment, seeing my Logitech Cordless Rumblepad 2 as a mouse. The pad still functions as a pad, except that the left analogue stick also moves the pointer around, which is ridiculously annoying.

Below is the Xorg.0.log, if it will help any.

```

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.33-pf2 i686 
Current Operating System: Linux ussrtop 2.6.33-pf2 #1 SMP PREEMPT Sun Apr 4 20:53:57 EST 2010 i686
Kernel command line: root=/dev/sda1 vga=792 irqpoll
Build Date: 06 April 2010  02:26:17PM
 
Current version of pixman: 0.16.6
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Apr  7 03:43:13 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/lib/X11/fonts/OTF" does not exist.
    Entry deleted from font path.
(WW) The directory "/usr/lib/X11/fonts/Type1/" does not exist.
    Entry deleted from font path.
(**) FontPath set to:
    /usr/lib/X11/fonts/misc/:unscaled,
    /usr/lib/X11/fonts/100dpi/:unscaled,
    /usr/lib/X11/fonts/75dpi/:unscaled,
    /usr/lib/X11/fonts/misc/,
    /usr/lib/X11/fonts/Speedo/,
    /usr/lib/X11/fonts/100dpi/,
    /usr/lib/X11/fonts/75dpi/,
    /usr/lib/X11/fonts/cyrillic/,
    /usr/lib/X11/fonts/TTF/,
    /usr/lib/X11/fonts/misc/,
    /usr/lib/X11/fonts/TTF/,
    /usr/lib/X11/fonts/100dpi/,
    /usr/lib/X11/fonts/75dpi/
(==) ModulePath set to "/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x81f0740
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(--) using VT number 7

(--) PCI:*(0:1:0:0) 10de:0a28:103c:3659 rev 162, Mem @ 0xd2000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x00006000/128, BIOS @ 0x????????/524288
(II) Open ACPI successful (/var/run/acpid.socket)
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
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  195.36.15  Thu Mar 11 23:39:48 PST 2010
(II) Loading extension GLX
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
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  195.36.15  Thu Mar 11 22:01:49 PST 2010
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules/libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) Apr 07 03:43:13 NVIDIA(0): Enabling RENDER acceleration
(II) Apr 07 03:43:13 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Apr 07 03:43:13 NVIDIA(0):     enabled.
(II) Apr 07 03:43:14 NVIDIA(0): NVIDIA GPU GeForce GT 230M (GT216) at PCI:1:0:0 (GPU-0)
(--) Apr 07 03:43:14 NVIDIA(0): Memory: 1048576 kBytes
(--) Apr 07 03:43:14 NVIDIA(0): VideoBIOS: 70.16.25.00.24
(II) Apr 07 03:43:14 NVIDIA(0): Detected PCI Express Link width: 16X
(--) Apr 07 03:43:14 NVIDIA(0): Interlaced video modes are supported on this GPU
(--) Apr 07 03:43:14 NVIDIA(0): Connected display device(s) on GeForce GT 230M at PCI:1:0:0:
(--) Apr 07 03:43:14 NVIDIA(0):     LGD LP156WH2-TLQ1 (DFP-0)
(--) Apr 07 03:43:14 NVIDIA(0): LGD LP156WH2-TLQ1 (DFP-0): 330.0 MHz maximum pixel clock
(--) Apr 07 03:43:14 NVIDIA(0): LGD LP156WH2-TLQ1 (DFP-0): Internal Dual Link LVDS
(II) Apr 07 03:43:14 NVIDIA(0): Assigned Display Device: DFP-0
(==) Apr 07 03:43:14 NVIDIA(0): 
(==) Apr 07 03:43:14 NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) Apr 07 03:43:14 NVIDIA(0):     will be used as the requested mode.
(==) Apr 07 03:43:14 NVIDIA(0): 
(II) Apr 07 03:43:14 NVIDIA(0): Validated modes:
(II) Apr 07 03:43:14 NVIDIA(0):     "nvidia-auto-select"
(II) Apr 07 03:43:14 NVIDIA(0): Virtual screen size determined to be 1366 x 768
(--) Apr 07 03:43:15 NVIDIA(0): DPI set to (102, 102); computed from "UseEdidDpi" X config
(--) Apr 07 03:43:15 NVIDIA(0):     option
(==) Apr 07 03:43:15 NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) Apr 07 03:43:15 NVIDIA: Using 768.00 MB of virtual memory for indirect framebuffer
(II) Apr 07 03:43:15 NVIDIA:     access.
(II) Apr 07 03:43:15 NVIDIA(0): Initialized GPU GART.
(II) Apr 07 03:43:15 NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) Apr 07 03:43:15 NVIDIA(0): Initialized OpenGL Acceleration
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) Apr 07 03:43:15 NVIDIA(0): Initialized X Rendering Acceleration
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
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
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing extension GLX
(II) config/hal: Adding input device Logitech Logitech Cordless RumblePad 2
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) Logitech Logitech Cordless RumblePad 2: always reports core events
(**) Logitech Logitech Cordless RumblePad 2: Device: "/dev/input/event6"
(II) Logitech Logitech Cordless RumblePad 2: Found absolute axes
(II) Logitech Logitech Cordless RumblePad 2: Found x and y absolute axes
(II) Logitech Logitech Cordless RumblePad 2: Configuring as mouse
(II) XINPUT: Adding extended input device "Logitech Logitech Cordless RumblePad 2" (type: MOUSE)
(**) Logitech Logitech Cordless RumblePad 2: (accel) keeping acceleration scheme 1
(**) Logitech Logitech Cordless RumblePad 2: (accel) acceleration profile 0
(II) Logitech Logitech Cordless RumblePad 2: initialized for absolute axes.
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device HID 04d9:0499
(**) HID 04d9:0499: always reports core events
(**) HID 04d9:0499: Device: "/dev/input/event5"
(II) HID 04d9:0499: Found 3 mouse buttons
(II) HID 04d9:0499: Found scroll wheel(s)
(II) HID 04d9:0499: Found relative axes
(II) HID 04d9:0499: Found x and y relative axes
(II) HID 04d9:0499: Configuring as mouse
(**) HID 04d9:0499: YAxisMapping: buttons 4 and 5
(**) HID 04d9:0499: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "HID 04d9:0499" (type: MOUSE)
(**) HID 04d9:0499: (accel) keeping acceleration scheme 1
(**) HID 04d9:0499: (accel) acceleration profile 0
(II) HID 04d9:0499: initialized for relative axes.
```

---

