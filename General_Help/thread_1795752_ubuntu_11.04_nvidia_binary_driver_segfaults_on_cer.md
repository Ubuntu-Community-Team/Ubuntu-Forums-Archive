---
title: "ubuntu 11.04 nvidia binary driver segfaults on certain applications"
date: 2011-07-03
forum: General Help
---

### Post by membuntu on 2011-07-03
Most applications starts fine, but specific applications:

* xcalc
* Eterm
* some perl/tk apps

cause instant segfaults but only if I am using the proprietary nvidia driver. I require the driver for vdpau accelerated video playback.

I have tried all combinations of (each time purging the old before testing the new:
* latest nvidia binaries from nvidia
* ubuntu's packaged drivers from the vanilla repo
*the latest via ppa.

All have the same result.

I also tried xorg edgers and repeated trying the nvidia drivers again, with the same results.

Help please :confused:

Dump of relevant info below:

xorg log:
```
[ 41976.903] 
X.Org X Server 1.10.2.901 (1.10.3 RC 1)
Release Date: 2011-06-17
[ 41976.903] X Protocol Version 11, Revision 0
[ 41976.903] Build Operating System: Linux 2.6.24-29-xen i686 Ubuntu
[ 41976.903] Current Operating System: Linux drbl1101 2.6.38-10-generic-pae #46-Ubuntu SMP Tue Jun 28 16:54:49 UTC 2011 i686
[ 41976.903] Kernel command line: initrd=initrd-pxe.img devfs=nomount drblthincli=off selinux=0 edd=on vmalloc=192MB BOOT_IMAGE=vmlinuz-pxe 
[ 41976.904] Build Date: 01 July 2011  10:45:53AM
[ 41976.904] xorg-server 2:1.10.2.901+git20110702+server-1.10-branch.79ef102c-0ubuntu0sarvatt~natty (For technical support please see http://www.ubuntu.com/support) 
[ 41976.904] Current version of pixman: 0.21.8
[ 41976.904] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[ 41976.904] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[ 41976.905] (==) Log file: "/var/log/Xorg.2.log", Time: Sun Jul  3 17:05:34 2011
[ 41976.908] (==) Using config file: "/etc/X11/xorg.conf"
[ 41976.908] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[ 41976.908] (==) ServerLayout "Layout0"
[ 41976.908] (**) |-->Screen "Screen0" (0)
[ 41976.908] (**) |   |-->Monitor "Monitor0"
[ 41976.908] (**) |   |-->Device "Device0"
[ 41976.908] (**) |-->Input Device "Keyboard0"
[ 41976.908] (**) |-->Input Device "Mouse0"
[ 41976.908] (==) Automatically adding devices
[ 41976.908] (==) Automatically enabling devices
[ 41976.910] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[ 41976.910] 	Entry deleted from font path.
[ 41976.914] (**) FontPath set to:
	unix/:7100,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[ 41976.914] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[ 41976.914] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[ 41976.914] (WW) Disabling Keyboard0
[ 41976.914] (WW) Disabling Mouse0
[ 41976.914] (II) Loader magic: 0x8201ae0
[ 41976.914] (II) Module ABI versions:
[ 41976.914] 	X.Org ANSI C Emulation: 0.4
[ 41976.914] 	X.Org Video Driver: 10.0
[ 41976.914] 	X.Org XInput driver : 12.3
[ 41976.914] 	X.Org Server Extension : 5.0
[ 41976.914] (--) PCI:*(0:1:0:0) 10de:0605:1043:829c rev 162, Mem @ 0xfa000000/16777216, 0xd0000000/268435456, 0xf8000000/33554432, I/O @ 0x0000cc00/128, BIOS @ 0x????????/131072
[ 41976.915] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[ 41976.915] (II) LoadModule: "extmod"
[ 41976.920] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[ 41976.921] (II) Module extmod: vendor="X.Org Foundation"
[ 41976.921] 	compiled for 1.10.2.901, module version = 1.0.0
[ 41976.921] 	Module class: X.Org Server Extension
[ 41976.921] 	ABI class: X.Org Server Extension, version 5.0
[ 41976.921] (II) Loading extension MIT-SCREEN-SAVER
[ 41976.921] (II) Loading extension XFree86-VidModeExtension
[ 41976.921] (II) Loading extension XFree86-DGA
[ 41976.921] (II) Loading extension DPMS
[ 41976.921] (II) Loading extension XVideo
[ 41976.921] (II) Loading extension XVideo-MotionCompensation
[ 41976.921] (II) Loading extension X-Resource
[ 41976.921] (II) LoadModule: "dbe"
[ 41976.923] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[ 41976.923] (II) Module dbe: vendor="X.Org Foundation"
[ 41976.923] 	compiled for 1.10.2.901, module version = 1.0.0
[ 41976.923] 	Module class: X.Org Server Extension
[ 41976.923] 	ABI class: X.Org Server Extension, version 5.0
[ 41976.923] (II) Loading extension DOUBLE-BUFFER
[ 41976.923] (II) LoadModule: "glx"
[ 41976.924] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[ 41976.941] (II) Module glx: vendor="NVIDIA Corporation"
[ 41976.941] 	compiled for 4.0.2, module version = 1.0.0
[ 41976.941] 	Module class: X.Org Server Extension
[ 41976.941] (II) NVIDIA GLX Module  270.41.06  Mon Apr 18 15:11:28 PDT 2011
[ 41976.941] (II) Loading extension GLX
[ 41976.941] (II) LoadModule: "record"
[ 41976.943] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[ 41976.944] (II) Module record: vendor="X.Org Foundation"
[ 41976.944] 	compiled for 1.10.2.901, module version = 1.13.0
[ 41976.944] 	Module class: X.Org Server Extension
[ 41976.944] 	ABI class: X.Org Server Extension, version 5.0
[ 41976.944] (II) Loading extension RECORD
[ 41976.944] (II) LoadModule: "dri"
[ 41976.946] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[ 41976.947] (II) Module dri: vendor="X.Org Foundation"
[ 41976.947] 	compiled for 1.10.2.901, module version = 1.0.0
[ 41976.947] 	ABI class: X.Org Server Extension, version 5.0
[ 41976.947] (II) Loading extension XFree86-DRI
[ 41976.947] (II) LoadModule: "dri2"
[ 41976.949] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[ 41976.950] (II) Module dri2: vendor="X.Org Foundation"
[ 41976.950] 	compiled for 1.10.2.901, module version = 1.2.0
[ 41976.950] 	ABI class: X.Org Server Extension, version 5.0
[ 41976.950] (II) Loading extension DRI2
[ 41976.950] (II) LoadModule: "nvidia"
[ 41976.950] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[ 41976.951] (II) Module nvidia: vendor="NVIDIA Corporation"
[ 41976.951] 	compiled for 4.0.2, module version = 1.0.0
[ 41976.951] 	Module class: X.Org Video Driver
[ 41976.951] (II) NVIDIA dlloader X Driver  270.41.06  Mon Apr 18 14:55:51 PDT 2011
[ 41976.951] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[ 41976.951] (--) using VT number 8

[ 41976.959] (II) Loading sub module "fb"
[ 41976.959] (II) LoadModule: "fb"
[ 41976.962] (II) Loading /usr/lib/xorg/modules/libfb.so
[ 41976.963] (II) Module fb: vendor="X.Org Foundation"
[ 41976.963] 	compiled for 1.10.2.901, module version = 1.0.0
[ 41976.963] 	ABI class: X.Org ANSI C Emulation, version 0.4
[ 41976.963] (II) Loading sub module "wfb"
[ 41976.963] (II) LoadModule: "wfb"
[ 41976.965] (II) Loading /usr/lib/xorg/modules/libwfb.so
[ 41976.966] (II) Module wfb: vendor="X.Org Foundation"
[ 41976.966] 	compiled for 1.10.2.901, module version = 1.0.0
[ 41976.966] 	ABI class: X.Org ANSI C Emulation, version 0.4
[ 41976.966] (II) Loading sub module "ramdac"
[ 41976.966] (II) LoadModule: "ramdac"
[ 41976.966] (II) Module "ramdac" already built-in
[ 41976.966] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[ 41976.966] (II) Loading /usr/lib/xorg/modules/libwfb.so
[ 41976.966] (II) Loading /usr/lib/xorg/modules/libfb.so
[ 41976.966] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[ 41976.966] (==) NVIDIA(0): RGB weight 888
[ 41976.966] (==) NVIDIA(0): Default visual is TrueColor
[ 41976.966] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[ 41976.966] (**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
[ 41977.142] (II) NVIDIA(GPU-0): Display (SHARP HDMI (DFP-1)) does not support NVIDIA 3D Vision
[ 41977.142] (II) NVIDIA(GPU-0):     stereo.
[ 41977.144] (II) NVIDIA(0): NVIDIA GPU GeForce 9800 GT (G92) at PCI:1:0:0 (GPU-0)
[ 41977.144] (--) NVIDIA(0): Memory: 524288 kBytes
[ 41977.144] (--) NVIDIA(0): VideoBIOS: 62.92.3b.00.00
[ 41977.144] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[ 41977.144] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[ 41977.144] (--) NVIDIA(0): Connected display device(s) on GeForce 9800 GT at PCI:1:0:0
[ 41977.144] (--) NVIDIA(0):     SHARP HDMI (DFP-1)
[ 41977.144] (--) NVIDIA(0): SHARP HDMI (DFP-1): 330.0 MHz maximum pixel clock
[ 41977.144] (--) NVIDIA(0): SHARP HDMI (DFP-1): Internal Dual Link TMDS
[ 41977.258] (II) NVIDIA(0): Assigned Display Device: DFP-1
[ 41977.258] (==) NVIDIA(0): 
[ 41977.258] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[ 41977.258] (==) NVIDIA(0):     will be used as the requested mode.
[ 41977.258] (==) NVIDIA(0): 
[ 41977.258] (II) NVIDIA(0): Validated modes:
[ 41977.258] (II) NVIDIA(0):     "nvidia-auto-select"
[ 41977.258] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[ 41977.306] (--) NVIDIA(0): DPI set to (59, 59); computed from "UseEdidDpi" X config
[ 41977.306] (--) NVIDIA(0):     option
[ 41977.306] (**) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[ 41977.306] (--) Depth 24 pixmap format is 32 bpp
[ 41977.306] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[ 41977.309] (II) NVIDIA(0): ACPI: failed to connect to the ACPI event daemon; the daemon
[ 41977.309] (II) NVIDIA(0):     may not be running or the "AcpidSocketPath" X
[ 41977.309] (II) NVIDIA(0):     configuration option may not be set correctly.  When the
[ 41977.309] (II) NVIDIA(0):     ACPI event daemon is available, the NVIDIA X driver will
[ 41977.309] (II) NVIDIA(0):     try to use it to receive ACPI event notifications.  For
[ 41977.309] (II) NVIDIA(0):     details, please see the "ConnectToAcpid" and
[ 41977.309] (II) NVIDIA(0):     "AcpidSocketPath" X configuration options in Appendix B: X
[ 41977.309] (II) NVIDIA(0):     Config Options in the README.
[ 41977.314] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[ 41977.390] (II) Loading extension NV-GLX
[ 41977.436] (==) NVIDIA(0): Disabling shared memory pixmaps
[ 41977.436] (==) NVIDIA(0): Backing store disabled
[ 41977.436] (==) NVIDIA(0): Silken mouse enabled
[ 41977.437] (**) NVIDIA(0): DPMS enabled
[ 41977.437] (II) Loading extension NV-CONTROL
[ 41977.437] (II) Loading extension XINERAMA
[ 41977.437] (II) Loading sub module "dri2"
[ 41977.437] (II) LoadModule: "dri2"
[ 41977.439] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[ 41977.439] (II) Module dri2: vendor="X.Org Foundation"
[ 41977.439] 	compiled for 1.10.2.901, module version = 1.2.0
[ 41977.439] 	ABI class: X.Org Server Extension, version 5.0
[ 41977.439] (II) NVIDIA(0): [DRI2] Setup complete
[ 41977.439] (==) RandR enabled
[ 41977.439] (II) Initializing built-in extension Generic Event Extension
[ 41977.439] (II) Initializing built-in extension SHAPE
[ 41977.439] (II) Initializing built-in extension MIT-SHM
[ 41977.439] (II) Initializing built-in extension XInputExtension
[ 41977.439] (II) Initializing built-in extension XTEST
[ 41977.439] (II) Initializing built-in extension BIG-REQUESTS
[ 41977.439] (II) Initializing built-in extension SYNC
[ 41977.439] (II) Initializing built-in extension XKEYBOARD
[ 41977.439] (II) Initializing built-in extension XC-MISC
[ 41977.439] (II) Initializing built-in extension SECURITY
[ 41977.439] (II) Initializing built-in extension XINERAMA
[ 41977.439] (II) Initializing built-in extension XFIXES
[ 41977.439] (II) Initializing built-in extension RENDER
[ 41977.439] (II) Initializing built-in extension RANDR
[ 41977.439] (II) Initializing built-in extension COMPOSITE
[ 41977.439] (II) Initializing built-in extension DAMAGE
[ 41977.439] (II) Initializing built-in extension GESTURE
[ 41977.441] (II) Initializing extension GLX
[ 41977.483] (II) XKB: reuse xkmfile /tmp/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[ 41977.489] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[ 41977.489] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[ 41977.489] (II) LoadModule: "evdev"
[ 41977.491] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 41977.491] (II) Module evdev: vendor="X.Org Foundation"
[ 41977.491] 	compiled for 1.10.0, module version = 2.6.0
[ 41977.491] 	Module class: X.Org XInput Driver
[ 41977.491] 	ABI class: X.Org XInput driver, version 12.3
[ 41977.491] (II) Using input driver 'evdev' for 'Power Button'
[ 41977.491] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 41977.491] (**) Power Button: always reports core events
[ 41977.491] (**) evdev: Power Button: Device: "/dev/input/event1"
[ 41977.520] (--) evdev: Power Button: Found keys
[ 41977.520] (II) evdev: Power Button: Configuring as keyboard
[ 41977.520] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[ 41977.520] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[ 41977.520] (**) Option "xkb_rules" "evdev"
[ 41977.520] (**) Option "xkb_model" "pc105"
[ 41977.520] (**) Option "xkb_layout" "us"
[ 41977.521] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[ 41977.521] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[ 41977.521] (II) Using input driver 'evdev' for 'Power Button'
[ 41977.521] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 41977.521] (**) Power Button: always reports core events
[ 41977.521] (**) evdev: Power Button: Device: "/dev/input/event0"
[ 41977.552] (--) evdev: Power Button: Found keys
[ 41977.552] (II) evdev: Power Button: Configuring as keyboard
[ 41977.552] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[ 41977.552] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[ 41977.552] (**) Option "xkb_rules" "evdev"
[ 41977.552] (**) Option "xkb_model" "pc105"
[ 41977.552] (**) Option "xkb_layout" "us"
[ 41977.554] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/event3)
[ 41977.554] (**) Logitech USB-PS/2 Optical Mouse: Applying InputClass "evdev pointer catchall"
[ 41977.554] (II) Using input driver 'evdev' for 'Logitech USB-PS/2 Optical Mouse'
[ 41977.554] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 41977.554] (**) Logitech USB-PS/2 Optical Mouse: always reports core events
[ 41977.554] (**) evdev: Logitech USB-PS/2 Optical Mouse: Device: "/dev/input/event3"
[ 41977.600] (--) evdev: Logitech USB-PS/2 Optical Mouse: Found 12 mouse buttons
[ 41977.600] (--) evdev: Logitech USB-PS/2 Optical Mouse: Found scroll wheel(s)
[ 41977.600] (--) evdev: Logitech USB-PS/2 Optical Mouse: Found relative axes
[ 41977.600] (--) evdev: Logitech USB-PS/2 Optical Mouse: Found x and y relative axes
[ 41977.600] (II) evdev: Logitech USB-PS/2 Optical Mouse: Configuring as mouse
[ 41977.600] (II) evdev: Logitech USB-PS/2 Optical Mouse: Adding scrollwheel support
[ 41977.600] (**) evdev: Logitech USB-PS/2 Optical Mouse: YAxisMapping: buttons 4 and 5
[ 41977.600] (**) evdev: Logitech USB-PS/2 Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[ 41977.600] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb3/3-1/3-1:1.0/input/input3/event3"
[ 41977.600] (II) XINPUT: Adding extended input device "Logitech USB-PS/2 Optical Mouse" (type: MOUSE)
[ 41977.600] (II) evdev: Logitech USB-PS/2 Optical Mouse: initialized for relative axes.
[ 41977.600] (**) Logitech USB-PS/2 Optical Mouse: (accel) keeping acceleration scheme 1
[ 41977.600] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration profile 0
[ 41977.600] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration factor: 2.000
[ 41977.600] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration threshold: 4
[ 41977.600] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/mouse0)
[ 41977.600] (II) No input driver/identifier specified (ignoring)
[ 41977.600] (II) config/udev: Adding input device UC-100KMA (/dev/input/event4)
[ 41977.600] (**) UC-100KMA: Applying InputClass "evdev keyboard catchall"
[ 41977.600] (II) Using input driver 'evdev' for 'UC-100KMA'
[ 41977.600] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 41977.600] (**) UC-100KMA: always reports core events
[ 41977.600] (**) evdev: UC-100KMA: Device: "/dev/input/event4"
[ 41977.620] (--) evdev: UC-100KMA: Found keys
[ 41977.620] (II) evdev: UC-100KMA: Configuring as keyboard
[ 41977.620] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb3/3-3/3-3:1.0/input/input4/event4"
[ 41977.620] (II) XINPUT: Adding extended input device "UC-100KMA" (type: KEYBOARD)
[ 41977.620] (**) Option "xkb_rules" "evdev"
[ 41977.620] (**) Option "xkb_model" "pc105"
[ 41977.620] (**) Option "xkb_layout" "us"
[ 41977.620] (II) config/udev: Adding input device UC-100KMA (/dev/input/event5)
[ 41977.620] (**) UC-100KMA: Applying InputClass "evdev pointer catchall"
[ 41977.620] (II) Using input driver 'evdev' for 'UC-100KMA'
[ 41977.620] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 41977.620] (**) UC-100KMA: always reports core events
[ 41977.620] (**) evdev: UC-100KMA: Device: "/dev/input/event5"
[ 41977.668] (--) evdev: UC-100KMA: Found 9 mouse buttons
[ 41977.668] (--) evdev: UC-100KMA: Found scroll wheel(s)
[ 41977.668] (--) evdev: UC-100KMA: Found relative axes
[ 41977.668] (--) evdev: UC-100KMA: Found x and y relative axes
[ 41977.668] (II) evdev: UC-100KMA: Configuring as mouse
[ 41977.668] (II) evdev: UC-100KMA: Adding scrollwheel support
[ 41977.668] (**) evdev: UC-100KMA: YAxisMapping: buttons 4 and 5
[ 41977.668] (**) evdev: UC-100KMA: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[ 41977.668] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb3/3-3/3-3:1.1/input/input5/event5"
[ 41977.668] (II) XINPUT: Adding extended input device "UC-100KMA" (type: MOUSE)
[ 41977.668] (II) evdev: UC-100KMA: initialized for relative axes.
[ 41977.668] (**) UC-100KMA: (accel) keeping acceleration scheme 1
[ 41977.668] (**) UC-100KMA: (accel) acceleration profile 0
[ 41977.668] (**) UC-100KMA: (accel) acceleration factor: 2.000
[ 41977.668] (**) UC-100KMA: (accel) acceleration threshold: 4
[ 41977.668] (II) config/udev: Adding input device UC-100KMA (/dev/input/mouse1)
[ 41977.668] (II) No input driver/identifier specified (ignoring)
[ 41977.670] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[ 41977.670] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[ 41977.670] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[ 41977.670] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 41977.670] (**) AT Translated Set 2 keyboard: always reports core events
[ 41977.670] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[ 41977.700] (--) evdev: AT Translated Set 2 keyboard: Found keys
[ 41977.700] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[ 41977.700] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[ 41977.700] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[ 41977.700] (**) Option "xkb_rules" "evdev"
[ 41977.700] (**) Option "xkb_model" "pc105"
[ 41977.700] (**) Option "xkb_layout" "us"
[ 41977.741] 
Backtrace:
[ 41977.741] 0: X (xorg_backtrace+0x3b) [0x80af49b]
[ 41977.741] 1: X (0x8048000+0x640c8) [0x80ac0c8]
[ 41977.741] 2: (vdso) (__kernel_rt_sigreturn+0x0) [0xb78bf40c]
[ 41977.741] 3: X (ProcessWorkQueue+0x30) [0x806d460]
[ 41977.741] 4: X (WaitForSomething+0x60) [0x80acb50]
[ 41977.741] 5: X (0x8048000+0x4ca3e) [0x8094a3e]
[ 41977.741] 6: X (0x8048000+0x1a87c) [0x806287c]
[ 41977.741] 7: /lib/i386-linux-gnu/libc.so.6 (__libc_start_main+0xe7) [0xb75c3e37]
[ 41977.741] 8: X (0x8048000+0x1a471) [0x8062471]
[ 41977.741] Segmentation fault at address (nil)
[ 41977.741] 
Caught signal 11 (Segmentation fault). Server aborting
[ 41977.741] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[ 41977.741] Please also check the log file at "/var/log/Xorg.2.log" for additional information.
[ 41977.741] 
[ 41977.792] (II) evdev: Power Button: Close
[ 41977.792] (II) UnloadModule: "evdev"
[ 41977.792] (II) Unloading evdev
[ 41977.864] (II) evdev: Power Button: Close
[ 41977.864] (II) UnloadModule: "evdev"
[ 41977.864] (II) Unloading evdev
[ 41977.928] (II) evdev: Logitech USB-PS/2 Optical Mouse: Close
[ 41977.928] (II) UnloadModule: "evdev"
[ 41977.928] (II) Unloading evdev
[ 41977.992] (II) evdev: UC-100KMA: Close
[ 41977.992] (II) UnloadModule: "evdev"
[ 41977.992] (II) Unloading evdev
[ 41978.020] (II) evdev: UC-100KMA: Close
[ 41978.020] (II) UnloadModule: "evdev"
[ 41978.020] (II) Unloading evdev
[ 41978.024] (II) evdev: AT Translated Set 2 keyboard: Close
[ 41978.024] (II) UnloadModule: "evdev"
[ 41978.024] (II) Unloading evdev
[ 41978.380]  ddxSigGiveUp: Closing log

```

lspci
```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB7x0/SB8x0/SB9x0 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 9800 GT] (rev a2)
02:00.0 Ethernet controller: Atheros Communications AR8121/AR8113/AR8114 Gigabit or Fast Ethernet (rev b0)
03:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6315 Series Firewire Controller

```

current package versions
```
ii  nvidia-cg-toolkit 3.0.0007-0ubuntu1  Cg Toolkit - GPU Shader Authoring Language
ii  nvidia-common     0.2.30             Find obsolete NVIDIA drivers
ii  nvidia-current    270.41.06-0ubuntu1 NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-settings   270.29-0ubuntu1    Tool of configuring the NVIDIA graphics driver
ii  xserver-xorg                          1:7.6+4ubuntu3.1                                                          
ii  xserver-xorg-core                     2:1.10.2.901+git20110702+server-1.10-branch.79ef102c-0ubuntu0sarvatt~natty

```

---

