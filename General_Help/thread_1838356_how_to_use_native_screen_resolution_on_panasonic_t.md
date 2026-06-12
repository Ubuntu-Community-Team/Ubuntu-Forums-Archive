---
title: "how to use native screen resolution on panasonic tc-L32x1"
date: 2011-09-03
forum: General Help
---

### Post by pdq2 on 2011-09-03
Hello guys and gals, I upgraded to 11.04 (64 bit) back when was 1st released and am loving unity so far.
Have no problems with detecting proper resolutions (ie: 1440 x 900) when hooked up to my usual monitor(s).

I do have a problem when connecting to my **panasonic tv tc-L32x1 **using vga connection, it should (and used to on 10.04/10.10) detect proper resolution of **1366 x 768**.

The highest resolution detected in 11.04 when connecting to my **panasonic tv tc-L32x1** is **1024 x 768**.

Not sure how to remedy this issue, so any help and guidance is much appreciated.
Even a hack/temp fix is good enough for me. :)

Here is my info:

**[~] lspci | grep VGA**
```

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12)
```**Xorg.0.log**
```

[    21.483] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    21.483] X Protocol Version 11, Revision 0
[    21.483] Build Operating System: Linux 2.6.24-28-server x86_64 Ubuntu
[    21.483] Current Operating System: Linux pdq-desktop 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:02:55 UTC 2011 x86_64
[    21.483] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-11-generic root=UUID=4dc01b4a-765d-4378-b9ba-63506205f644 ro quiet splash vt.handoff=7
[    21.483] Build Date: 11 August 2011  03:43:05PM
[    21.483] xorg-server 2:1.10.1-1ubuntu1.2 (For technical support please see http://www.ubuntu.com/support) 
[    21.483] Current version of pixman: 0.20.2
[    21.483]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    21.483] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    21.483] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Sep  3 11:05:45 2011
[    21.638] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    21.687] (==) No Layout section.  Using the first Screen section.
[    21.687] (==) No screen section available. Using defaults.
[    21.687] (**) |-->Screen "Default Screen Section" (0)
[    21.687] (**) |   |-->Monitor "<default monitor>"
[    21.706] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    21.706] (==) Automatically adding devices
[    21.707] (==) Automatically enabling devices
[    21.770] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    21.770]     Entry deleted from font path.
[    21.860] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    21.860] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    21.860] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    21.860] (II) Loader magic: 0x7e17e0
[    21.860] (II) Module ABI versions:
[    21.860]     X.Org ANSI C Emulation: 0.4
[    21.860]     X.Org Video Driver: 10.0
[    21.860]     X.Org XInput driver : 12.3
[    21.860]     X.Org Server Extension : 5.0
[    21.860] (--) PCI:*(0:0:2:0) 8086:0042:1849:0042 rev 18, Mem @ 0xfb800000/4194304, 0xd0000000/268435456, I/O @ 0x0000cc00/8
[    21.860] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    21.860] (II) LoadModule: "extmod"
[    21.946] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    21.987] (II) Module extmod: vendor="X.Org Foundation"
[    21.987]     compiled for 1.10.1, module version = 1.0.0
[    21.987]     Module class: X.Org Server Extension
[    21.987]     ABI class: X.Org Server Extension, version 5.0
[    21.987] (II) Loading extension MIT-SCREEN-SAVER
[    21.987] (II) Loading extension XFree86-VidModeExtension
[    21.987] (II) Loading extension XFree86-DGA
[    21.988] (II) Loading extension DPMS
[    21.988] (II) Loading extension XVideo
[    21.988] (II) Loading extension XVideo-MotionCompensation
[    21.988] (II) Loading extension X-Resource
[    21.988] (II) LoadModule: "dbe"
[    21.988] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    21.988] (II) Module dbe: vendor="X.Org Foundation"
[    21.988]     compiled for 1.10.1, module version = 1.0.0
[    21.988]     Module class: X.Org Server Extension
[    21.988]     ABI class: X.Org Server Extension, version 5.0
[    21.988] (II) Loading extension DOUBLE-BUFFER
[    21.988] (II) LoadModule: "glx"
[    21.988] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    22.026] (II) Module glx: vendor="X.Org Foundation"
[    22.026]     compiled for 1.10.1, module version = 1.0.0
[    22.026]     ABI class: X.Org Server Extension, version 5.0
[    22.026] (==) AIGLX enabled
[    22.026] (II) Loading extension GLX
[    22.026] (II) LoadModule: "record"
[    22.026] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    22.038] (II) Module record: vendor="X.Org Foundation"
[    22.038]     compiled for 1.10.1, module version = 1.13.0
[    22.038]     Module class: X.Org Server Extension
[    22.038]     ABI class: X.Org Server Extension, version 5.0
[    22.038] (II) Loading extension RECORD
[    22.038] (II) LoadModule: "dri"
[    22.038] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    22.050] (II) Module dri: vendor="X.Org Foundation"
[    22.050]     compiled for 1.10.1, module version = 1.0.0
[    22.050]     ABI class: X.Org Server Extension, version 5.0
[    22.050] (II) Loading extension XFree86-DRI
[    22.050] (II) LoadModule: "dri2"
[    22.050] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    22.063] (II) Module dri2: vendor="X.Org Foundation"
[    22.063]     compiled for 1.10.1, module version = 1.2.0
[    22.063]     ABI class: X.Org Server Extension, version 5.0
[    22.063] (II) Loading extension DRI2
[    22.063] (==) Matched intel as autoconfigured driver 0
[    22.063] (==) Matched vesa as autoconfigured driver 1
[    22.063] (==) Matched fbdev as autoconfigured driver 2
[    22.063] (==) Assigned the driver to the xf86ConfigLayout
[    22.063] (II) LoadModule: "intel"
[    22.092] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    22.122] (II) Module intel: vendor="X.Org Foundation"
[    22.122]     compiled for 1.10.1, module version = 2.14.0
[    22.122]     Module class: X.Org Video Driver
[    22.122]     ABI class: X.Org Video Driver, version 10.0
[    22.122] (II) LoadModule: "vesa"
[    22.122] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    22.129] (II) Module vesa: vendor="X.Org Foundation"
[    22.129]     compiled for 1.10.0, module version = 2.3.0
[    22.129]     Module class: X.Org Video Driver
[    22.129]     ABI class: X.Org Video Driver, version 10.0
[    22.129] (II) LoadModule: "fbdev"
[    22.129] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    22.138] (II) Module fbdev: vendor="X.Org Foundation"
[    22.138]     compiled for 1.10.0, module version = 0.4.2
[    22.138]     ABI class: X.Org Video Driver, version 10.0
[    22.138] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
    Sandybridge, Sandybridge
[    22.138] (II) VESA: driver for VESA chipsets: vesa
[    22.138] (II) FBDEV: driver for framebuffer: fbdev
[    22.138] (++) using VT number 7

[    22.140] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    22.140] (WW) Falling back to old probe method for vesa
[    22.140] (WW) Falling back to old probe method for fbdev
[    22.140] (II) Loading sub module "fbdevhw"
[    22.140] (II) LoadModule: "fbdevhw"
[    22.140] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    22.153] (II) Module fbdevhw: vendor="X.Org Foundation"
[    22.153]     compiled for 1.10.1, module version = 0.0.2
[    22.153]     ABI class: X.Org Video Driver, version 10.0
[    22.153] drmOpenDevice: node name is /dev/dri/card0
[    22.153] drmOpenDevice: open result is 8, (OK)
[    22.153] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    22.153] drmOpenDevice: node name is /dev/dri/card0
[    22.153] drmOpenDevice: open result is 8, (OK)
[    22.153] drmOpenByBusid: drmOpenMinor returns 8
[    22.153] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    22.153] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    22.153] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    22.153] (==) intel(0): RGB weight 888
[    22.153] (==) intel(0): Default visual is TrueColor
[    22.153] (II) intel(0): Integrated Graphics Chipset: Intel(R) Clarkdale
[    22.153] (--) intel(0): Chipset: "Clarkdale"
[    22.153] (**) intel(0): Relaxed fencing enabled
[    22.153] (**) intel(0): Tiling enabled
[    22.153] (**) intel(0): SwapBuffers wait enabled
[    22.153] (==) intel(0): video overlay key set to 0x101fe
[    22.155] (II) intel(0): Output VGA1 has no monitor section
[    22.159] (II) intel(0): Output HDMI1 has no monitor section
[    22.160] (II) intel(0): Output DP1 has no monitor section
[    22.165] (II) intel(0): Output HDMI2 has no monitor section
[    22.166] (II) intel(0): Output DP2 has no monitor section
[    22.168] (II) intel(0): EDID for output VGA1
[    22.168] (II) intel(0): Printing probed modes for output VGA1
[    22.168] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    22.168] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    22.168] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    22.168] (II) intel(0): Modeline "848x480"x60.0   33.75  848 864 976 1088  480 486 494 517 +hsync +vsync (31.0 kHz)
[    22.168] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 489 492 525 -hsync -vsync (31.5 kHz)
[    22.172] (II) intel(0): EDID for output HDMI1
[    22.173] (II) intel(0): EDID for output DP1
[    22.177] (II) intel(0): EDID for output HDMI2
[    22.178] (II) intel(0): EDID for output DP2
[    22.178] (II) intel(0): Output VGA1 connected
[    22.178] (II) intel(0): Output HDMI1 disconnected
[    22.178] (II) intel(0): Output DP1 disconnected
[    22.178] (II) intel(0): Output HDMI2 disconnected
[    22.178] (II) intel(0): Output DP2 disconnected
[    22.178] (II) intel(0): Using fuzzy aspect match for initial modes
[    22.178] (II) intel(0): Output VGA1 using initial mode 1024x768
[    22.178] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    22.178] (II) intel(0): Kernel page flipping support detected, enabling
[    22.178] (==) intel(0): DPI set to (96, 96)
[    22.178] (II) Loading sub module "fb"
[    22.178] (II) LoadModule: "fb"
[    22.179] (II) Loading /usr/lib/xorg/modules/libfb.so
[    22.280] (II) Module fb: vendor="X.Org Foundation"
[    22.280]     compiled for 1.10.1, module version = 1.0.0
[    22.280]     ABI class: X.Org ANSI C Emulation, version 0.4
[    22.280] (II) UnloadModule: "vesa"
[    22.280] (II) Unloading vesa
[    22.280] (II) UnloadModule: "fbdev"
[    22.280] (II) Unloading fbdev
[    22.280] (II) UnloadModule: "fbdevhw"
[    22.280] (II) Unloading fbdevhw
[    22.280] (==) Depth 24 pixmap format is 32 bpp
[    22.280] (==) intel(0): VideoRam: 262144 KB
[    22.280] (II) intel(0): [DRI2] Setup complete
[    22.280] (II) intel(0): [DRI2]   DRI driver: i965
[    22.280] (II) intel(0): Allocated new frame buffer 1024x768 stride 4096, tiled
[    22.375] (II) UXA(0): Driver registered support for the following operations:
[    22.375] (II)         solid
[    22.375] (II)         copy
[    22.375] (II)         composite (RENDER acceleration)
[    22.375] (II)         put_image
[    22.375] (II)         get_image
[    22.375] (==) intel(0): Backing store disabled
[    22.375] (==) intel(0): Silken mouse enabled
[    22.375] (II) intel(0): Initializing HW Cursor
[    22.450] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    22.450] (==) intel(0): DPMS enabled
[    22.450] (==) intel(0): Intel XvMC decoder enabled
[    22.450] (II) intel(0): Set up textured video
[    22.450] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[    22.450] (II) intel(0): direct rendering: DRI2 Enabled
[    22.450] (==) intel(0): hotplug detection: "enabled"
[    22.450] (--) RandR disabled
[    22.450] (II) Initializing built-in extension Generic Event Extension
[    22.450] (II) Initializing built-in extension SHAPE
[    22.450] (II) Initializing built-in extension MIT-SHM
[    22.450] (II) Initializing built-in extension XInputExtension
[    22.450] (II) Initializing built-in extension XTEST
[    22.450] (II) Initializing built-in extension BIG-REQUESTS
[    22.450] (II) Initializing built-in extension SYNC
[    22.450] (II) Initializing built-in extension XKEYBOARD
[    22.450] (II) Initializing built-in extension XC-MISC
[    22.450] (II) Initializing built-in extension SECURITY
[    22.450] (II) Initializing built-in extension XINERAMA
[    22.450] (II) Initializing built-in extension XFIXES
[    22.450] (II) Initializing built-in extension RENDER
[    22.450] (II) Initializing built-in extension RANDR
[    22.450] (II) Initializing built-in extension COMPOSITE
[    22.450] (II) Initializing built-in extension DAMAGE
[    22.450] (II) Initializing built-in extension GESTURE
[    22.454] (II) AIGLX: Trying DRI driver /usr/lib/dri/i965_dri.so
[    22.722] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    22.722] (II) AIGLX: enabled GLX_INTEL_swap_event
[    22.722] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    22.722] (II) AIGLX: enabled GLX_SGI_make_current_read
[    22.722] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    22.722] (II) AIGLX: Loaded and initialized i965
[    22.722] (II) GLX: Initialized DRI2 GL provider for screen 0
[    22.722] (II) intel(0): Setting screen physical size to 270 x 203
[    23.165] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    23.201] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    23.201] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    23.201] (II) LoadModule: "evdev"
[    23.201] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.287] (II) Module evdev: vendor="X.Org Foundation"
[    23.287]     compiled for 1.10.0.902, module version = 2.6.0
[    23.287]     Module class: X.Org XInput Driver
[    23.287]     ABI class: X.Org XInput driver, version 12.3
[    23.287] (II) Using input driver 'evdev' for 'Power Button'
[    23.287] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.287] (**) Power Button: always reports core events
[    23.287] (**) Power Button: Device: "/dev/input/event1"
[    23.340] (--) Power Button: Found keys
[    23.340] (II) Power Button: Configuring as keyboard
[    23.340] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    23.340] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    23.340] (**) Option "xkb_rules" "evdev"
[    23.340] (**) Option "xkb_model" "pc105"
[    23.340] (**) Option "xkb_layout" "us"
[    23.342] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    23.342] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    23.342] (II) Using input driver 'evdev' for 'Power Button'
[    23.342] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.342] (**) Power Button: always reports core events
[    23.342] (**) Power Button: Device: "/dev/input/event0"
[    23.410] (--) Power Button: Found keys
[    23.410] (II) Power Button: Configuring as keyboard
[    23.410] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    23.410] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    23.410] (**) Option "xkb_rules" "evdev"
[    23.410] (**) Option "xkb_model" "pc105"
[    23.410] (**) Option "xkb_layout" "us"
[    23.412] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event2)
[    23.412] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[    23.412] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[    23.412] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.412] (**) Logitech USB Receiver: always reports core events
[    23.412] (**) Logitech USB Receiver: Device: "/dev/input/event2"
[    23.470] (--) Logitech USB Receiver: Found 20 mouse buttons
[    23.470] (--) Logitech USB Receiver: Found scroll wheel(s)
[    23.470] (--) Logitech USB Receiver: Found relative axes
[    23.470] (--) Logitech USB Receiver: Found x and y relative axes
[    23.470] (II) Logitech USB Receiver: Configuring as mouse
[    23.470] (II) Logitech USB Receiver: Adding scrollwheel support
[    23.470] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    23.470] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    23.470] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input2/event2"
[    23.470] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: MOUSE)
[    23.470] (II) Logitech USB Receiver: initialized for relative axes.
[    23.470] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[    23.470] (**) Logitech USB Receiver: (accel) acceleration profile 0
[    23.470] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[    23.470] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[    23.470] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse0)
[    23.470] (II) No input driver/identifier specified (ignoring)
[    23.471] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event3)
[    23.471] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    23.471] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[    23.471] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.471] (**) Logitech USB Receiver: always reports core events
[    23.471] (**) Logitech USB Receiver: Device: "/dev/input/event3"
[    23.530] (--) Logitech USB Receiver: Found 1 mouse buttons
[    23.530] (--) Logitech USB Receiver: Found scroll wheel(s)
[    23.530] (--) Logitech USB Receiver: Found relative axes
[    23.530] (--) Logitech USB Receiver: Found absolute axes
[    23.530] (II) evdev-grail: failed to open grail, no gesture support
[    23.530] (--) Logitech USB Receiver: Found keys
[    23.530] (II) Logitech USB Receiver: Configuring as mouse
[    23.530] (II) Logitech USB Receiver: Configuring as keyboard
[    23.530] (II) Logitech USB Receiver: Adding scrollwheel support
[    23.530] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    23.530] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    23.530] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.1/input/input3/event3"
[    23.530] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    23.530] (**) Option "xkb_rules" "evdev"
[    23.530] (**) Option "xkb_model" "pc105"
[    23.530] (**) Option "xkb_layout" "us"
[    23.530] (EE) Logitech USB Receiver: failed to initialize for relative axes.
[    23.530] (II) Logitech USB Receiver: initialized for absolute axes.
[    23.530] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[    23.530] (**) Logitech USB Receiver: (accel) acceleration profile 0
[    23.530] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[    23.530] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[    23.531] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event4)
[    23.531] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    23.531] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[    23.531] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.531] (**) Logitech USB Receiver: always reports core events
[    23.531] (**) Logitech USB Receiver: Device: "/dev/input/event4"
[    23.580] (--) Logitech USB Receiver: Found keys
[    23.580] (II) Logitech USB Receiver: Configuring as keyboard
[    23.580] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input4/event4"
[    23.580] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    23.580] (**) Option "xkb_rules" "evdev"
[    23.580] (**) Option "xkb_model" "pc105"
[    23.580] (**) Option "xkb_layout" "us"
[    23.581] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event5)
[    23.581] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[    23.581] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    23.581] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[    23.581] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.581] (**) Logitech USB Receiver: always reports core events
[    23.581] (**) Logitech USB Receiver: Device: "/dev/input/event5"
[    23.640] (--) Logitech USB Receiver: Found 20 mouse buttons
[    23.640] (--) Logitech USB Receiver: Found scroll wheel(s)
[    23.640] (--) Logitech USB Receiver: Found relative axes
[    23.640] (--) Logitech USB Receiver: Found x and y relative axes
[    23.640] (--) Logitech USB Receiver: Found absolute axes
[    23.640] (II) evdev-grail: failed to open grail, no gesture support
[    23.640] (--) Logitech USB Receiver: Found keys
[    23.640] (II) Logitech USB Receiver: Configuring as mouse
[    23.640] (II) Logitech USB Receiver: Configuring as keyboard
[    23.640] (II) Logitech USB Receiver: Adding scrollwheel support
[    23.640] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    23.640] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    23.640] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.1/input/input5/event5"
[    23.640] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    23.640] (**) Option "xkb_rules" "evdev"
[    23.640] (**) Option "xkb_model" "pc105"
[    23.640] (**) Option "xkb_layout" "us"
[    23.640] (II) Logitech USB Receiver: initialized for relative axes.
[    23.640] (WW) Logitech USB Receiver: ignoring absolute axes.
[    23.640] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[    23.640] (**) Logitech USB Receiver: (accel) acceleration profile 0
[    23.640] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[    23.640] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[    23.641] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse1)
[    23.641] (II) No input driver/identifier specified (ignoring)

```[B][~] sudo get-edid | parse-edid
[/B]```

parse-edid: parse-edid version 2.0.0get-edid: get-edid version 2.0.0

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
    Function supported
    Call successful

    VBE version 300
    VBE string at 0x11100 "Intel(R)Ironlake Desktop Graphics Chipset Accelerated VGA BIOS"

VBE/DDC service about to be called
    Report DDC capabilities

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f15 bx=0x0 cx=0x0
    Function supported
    Call successful

    Monitor and video card combination does not support DDC1 transfers
    Monitor and video card combination does not support DDC2 transfers
    0 seconds per 128 byte EDID block transfer
    Screen is not blanked during DDC transfer

Reading next EDID block

VBE/DDC service about to be called
    Read EDID

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
    Function supported
    Call failed

The EDID data should not be trusted as the VBE call failed
Error: output block unchanged
parse-edid: IO error reading EDID
```**[~] locate xorg.conf**
```
/etc/X11/xorg.conf-backup-100727154458
/etc/X11/xorg.conf.failsafe
/usr/share/X11/xorg.conf.d
/usr/share/X11/xorg.conf.d/10-evdev.conf
/usr/share/X11/xorg.conf.d/11-evdev-quirks.conf
/usr/share/X11/xorg.conf.d/50-synaptics.conf
/usr/share/X11/xorg.conf.d/50-vmmouse.conf
/usr/share/X11/xorg.conf.d/50-wacom.conf
/usr/share/X11/xorg.conf.d/51-synaptics-quirks.conf
/usr/share/doc/xserver-xorg-video-nouveau/examples/xorg.conf
/usr/share/man/man5/xorg.conf.5.gz
/var/lib/x11/xorg.conf.md5sum
```I've read many, many threads here regarding similar issues but is very confusing and not sure much of it applied to my specific issue. Need help please.

:confused:

---

### Post by pdq2 on 2011-09-23
bumpity bump :)

---

