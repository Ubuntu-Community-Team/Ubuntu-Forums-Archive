---
title: "Multi-seat making me mental"
date: 2010-12-23
forum: General Help
---

### Post by DarrenO on 2010-12-23
I am not an Ubuntu expert, but I have been using it for about 5 years and love it. Currently running 10.04.

Recently, we have changed our desk configuration and my significant other and I have a need for the Multiseat capabilities in Linux.

I have two Nvidia video cards, two USB mice and two USB keyboards. I can get both monitors running and working in twinview mode using the "nvidia" software.
I followed this:
[http://multiseatonlinux.blogspot.com/2010/06/part-1-setting-up-base.html](http://multiseatonlinux.blogspot.com/2010/06/part-1-setting-up-base.html)
and got an error saying "Microsoft Comfort Curve Keyboard 2000: failed to initialize for relative axes".

This stops X from starting. I tried changing from "evdev" to "kbd" and "mouse" drivers but get the same thing. There is nothing else that I notice in my error logs, but I am not sure I am looking in the right spots.

I tried using this guide, but I really don't understand how to piece it all together.
[http://linuxagora.com/vbforum/showthread.php?t=764](http://linuxagora.com/vbforum/showthread.php?t=764)

This is my xorg from the second attempt, but I am totally confused as to what to do with gdm.conf which does not exist on my system.

```
Section "ServerLayout"  
     Identifier "Seat0"  
     Screen 0 "Screen0" 0 0  
     InputDevice "Mouse0" "CorePointer"  
     InputDevice "Keyboard0" "CoreKeyboard" 
     Option "AutoAddDevices" "false"
     Option "AutoEnableDevices" "false"
     Option "Xinerama" "0"
EndSection

Section "ServerLayout"  
     Identifier "Seat1"  
     Screen 0 "Screen1" 0 0  
     InputDevice "Mouse1" "CorePointer"  
     InputDevice "Keyboard1" "CoreKeyboard" 
     Option "AutoAddDevices" "false"
     Option "AutoEnableDevices" "false"
     Option "Xinerama" "0"
EndSection

Section "InputDevice"  
     Identifier "Keyboard0"  
     Driver "evdev"  
     Option "Device" "/dev/input/by-path/pci-0000:00:12.1-usb-0:2:1.0-event-kbd"  
     Option "specialKeys" "true" 
EndSection

Section "InputDevice"  
     Identifier "Mouse0"  
     Driver "mouse"  
     Option "ZAxisMapping" "4 5"  
     Option "Device" "/dev/input/by-path/pci-0000:00:12.1-usb-0:3:1.1-event-mouse"
EndSection

Section "InputDevice"  
     Identifier "Keyboard1"  
     Driver "evdev"  
     Option "Device" "/dev/input/by-path/pci-0000:00:12.0-usb-0:3.1:1.0-event-kbd"  
     Option "specialKeys" "true" 
EndSection

Section "InputDevice"  
     Identifier "Mouse1"  
     Driver "mouse"  
     Option "ZAxisMapping" "4 5"  
     Option "Device" "/dev/input/by-path/pci-0000:00:12.0-usb-0:1:1.0-event-mouse"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL 1702FP"
    HorizSync       30.0 - 80.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "LG L226WTX"
    HorizSync       28.0 - 83.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400 GS"
    BusID          "PCI:4:0:0"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9500 GS"
    BusID          "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

Does anybody have any ideas or a sure fire way to make multi-seat work? I also tried the Userful software, but that does not work on my machine.

---

### Post by DarrenO on 2010-12-23
Does anybody have any ideas? I think this is the log file that documents the issue: Xorg.1.log

```
X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-28-server i686 Ubuntu
Current Operating System: Linux danger 2.6.32-26-generic #48-Ubuntu SMP Wed Nov 24 09:00:03 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-26-generic root=UUID=35390ab0-9489-45e9-a4f0-e7184c34d277 ro quiet splash
Build Date: 10 November 2010  11:25:26AM
xorg-server 2:1.7.6-2ubuntu7.4 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Thu Dec 23 08:09:33 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Screen "Screen1" (1)
(**) |   |-->Monitor "Monitor1"
(**) |   |-->Device "Device1"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(**) Option "Xinerama" "0"
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
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x81f1b20
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(--) using VT number 8

(--) PCI: (0:1:0:0) 10de:0644:174b:9600 nVidia Corporation G96 [GeForce 9500 GS] rev 161, Mem @ 0xf4000000/16777216, 0xc0000000/268435456, 0xf2000000/33554432, I/O @ 0x0000ef00/128, BIOS @ 0x????????/524288
(--) PCI:*(0:4:0:0) 10de:06e4:3842:b724 nVidia Corporation G98 [GeForce 8400 GS] rev 161, Mem @ 0xf8000000/16777216, 0xd0000000/268435456, 0xf6000000/33554432, I/O @ 0x0000cf00/128, BIOS @ 0x????????/131072
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
(II) Loading /usr/lib/xorg/extra-modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  195.36.24  Thu Apr 22 10:38:29 PDT 2010
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
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  195.36.24  Thu Apr 22 09:34:29 PDT 2010
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 04@00:00:0
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
(**) NVIDIA(0): Option "TwinView" "0"
(**) NVIDIA(0): Option "MetaModes" "nvidia-auto-select +0+0"
(**) Dec 23 08:09:34 NVIDIA(0): Enabling RENDER acceleration
(II) Dec 23 08:09:34 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Dec 23 08:09:34 NVIDIA(0):     enabled.
(II) Dec 23 08:09:34 NVIDIA(0): NVIDIA GPU GeForce 8400 GS (G98) at PCI:4:0:0 (GPU-0)
(--) Dec 23 08:09:34 NVIDIA(0): Memory: 524288 kBytes
(--) Dec 23 08:09:34 NVIDIA(0): VideoBIOS: 62.98.42.00.27
(II) Dec 23 08:09:34 NVIDIA(0): Detected PCI Express Link width: 1X
(--) Dec 23 08:09:34 NVIDIA(0): Interlaced video modes are supported on this GPU
(--) Dec 23 08:09:34 NVIDIA(0): Connected display device(s) on GeForce 8400 GS at PCI:4:0:0:
(--) Dec 23 08:09:34 NVIDIA(0):     DELL 1702FP (DFP-0)
(--) Dec 23 08:09:34 NVIDIA(0): DELL 1702FP (DFP-0): 330.0 MHz maximum pixel clock
(--) Dec 23 08:09:34 NVIDIA(0): DELL 1702FP (DFP-0): Internal Dual Link TMDS
(II) Dec 23 08:09:34 NVIDIA(0): Assigned Display Device: DFP-0
(II) Dec 23 08:09:34 NVIDIA(0): Validated modes:
(II) Dec 23 08:09:34 NVIDIA(0):     "nvidia-auto-select+0+0"
(II) Dec 23 08:09:34 NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(--) Dec 23 08:09:34 NVIDIA(0): DPI set to (95, 96); computed from "UseEdidDpi" X config
(--) Dec 23 08:09:34 NVIDIA(0):     option
(==) Dec 23 08:09:34 NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(1): RGB weight 888
(==) NVIDIA(1): Default visual is TrueColor
(==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(1): Option "TwinView" "0"
(**) NVIDIA(1): Option "MetaModes" "nvidia-auto-select +0+0"
(**) Dec 23 08:09:34 NVIDIA(1): Enabling RENDER acceleration
(II) Dec 23 08:09:34 NVIDIA(1): NVIDIA GPU GeForce 9500 GS (G96) at PCI:1:0:0 (GPU-1)
(--) Dec 23 08:09:34 NVIDIA(1): Memory: 524288 kBytes
(--) Dec 23 08:09:34 NVIDIA(1): VideoBIOS: 62.94.32.00.13
(II) Dec 23 08:09:34 NVIDIA(1): Detected PCI Express Link width: 16X
(--) Dec 23 08:09:34 NVIDIA(1): Interlaced video modes are supported on this GPU
(--) Dec 23 08:09:34 NVIDIA(1): Connected display device(s) on GeForce 9500 GS at PCI:1:0:0:
(--) Dec 23 08:09:34 NVIDIA(1):     LG L226WTX (DFP-0)
(--) Dec 23 08:09:34 NVIDIA(1): LG L226WTX (DFP-0): 330.0 MHz maximum pixel clock
(--) Dec 23 08:09:34 NVIDIA(1): LG L226WTX (DFP-0): Internal Dual Link TMDS
(II) Dec 23 08:09:34 NVIDIA(1): Assigned Display Device: DFP-0
(II) Dec 23 08:09:34 NVIDIA(1): Validated modes:
(II) Dec 23 08:09:34 NVIDIA(1):     "nvidia-auto-select+0+0"
(II) Dec 23 08:09:34 NVIDIA(1): Virtual screen size determined to be 1680 x 1050
(--) Dec 23 08:09:34 NVIDIA(1): DPI set to (90, 88); computed from "UseEdidDpi" X config
(--) Dec 23 08:09:34 NVIDIA(1):     option
(==) Dec 23 08:09:34 NVIDIA(1): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) Dec 23 08:09:34 NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
(II) Dec 23 08:09:34 NVIDIA(0): Initialized GPU GART.
(II) Dec 23 08:09:34 NVIDIA(0): Setting mode "nvidia-auto-select+0+0"
(II) Loading extension NV-GLX
(II) Dec 23 08:09:34 NVIDIA(0): Initialized OpenGL Acceleration
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) Dec 23 08:09:35 NVIDIA(0): Initialized X Rendering Acceleration
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
(II) Dec 23 08:09:35 NVIDIA(1): Initialized GPU GART.
(II) Dec 23 08:09:35 NVIDIA(1): Setting mode "nvidia-auto-select+0+0"
(II) Dec 23 08:09:35 NVIDIA(1): Initialized OpenGL Acceleration
(==) NVIDIA(1): Disabling shared memory pixmaps
(II) Dec 23 08:09:35 NVIDIA(1): Initialized X Rendering Acceleration
(==) NVIDIA(1): Backing store disabled
(==) NVIDIA(1): Silken mouse enabled
(==) NVIDIA(1): DPMS enabled
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
(II) Initializing extension GLX
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) XKB: reuse xkmfile /var/lib/xkb/server-0C76CA335E924C2441A31FBFED02D59A89874CA6.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) config/udev: Adding input device Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) (/dev/input/event3)
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Applying InputClass "evdev pointer catchall"
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): always reports core events
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Device: "/dev/input/event3"
(II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found 3 mouse buttons
(II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found scroll wheel(s)
(II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found relative axes
(II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found x and y relative axes
(II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Configuring as mouse
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): YAxisMapping: buttons 4 and 5
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)" (type: MOUSE)
(II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): initialized for relative axes.
(II) config/udev: Adding input device Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Dell Dell USB Keyboard (/dev/input/event8)
(**) Dell Dell USB Keyboard: Applying InputClass "evdev keyboard catchall"
(**) Dell Dell USB Keyboard: always reports core events
(**) Dell Dell USB Keyboard: Device: "/dev/input/event8"
(II) Dell Dell USB Keyboard: Found keys
(II) Dell Dell USB Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Dell Dell USB Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) config/udev: Adding input device Dell Dell USB Keyboard (/dev/input/event9)
(**) Dell Dell USB Keyboard: Applying InputClass "evdev keyboard catchall"
(**) Dell Dell USB Keyboard: always reports core events
(**) Dell Dell USB Keyboard: Device: "/dev/input/event9"
(II) Dell Dell USB Keyboard: Found absolute axes
(II) Dell Dell USB Keyboard: Found keys
(II) Dell Dell USB Keyboard: Configuring as mouse
(II) Dell Dell USB Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Dell Dell USB Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) Dell Dell USB Keyboard: initialized for absolute axes.
(II) config/udev: Adding input device Microsoft Comfort Curve Keyboard 2000 (/dev/input/event4)
(**) Microsoft Comfort Curve Keyboard 2000: Applying InputClass "evdev keyboard catchall"
(**) Microsoft Comfort Curve Keyboard 2000: always reports core events
(**) Microsoft Comfort Curve Keyboard 2000: Device: "/dev/input/event4"
(II) Microsoft Comfort Curve Keyboard 2000: Found keys
(II) Microsoft Comfort Curve Keyboard 2000: Configuring as keyboard
(II) XINPUT: Adding extended input device "Microsoft Comfort Curve Keyboard 2000" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) config/udev: Adding input device Microsoft Comfort Curve Keyboard 2000 (/dev/input/event5)
(**) Microsoft Comfort Curve Keyboard 2000: Applying InputClass "evdev keyboard catchall"
(**) Microsoft Comfort Curve Keyboard 2000: always reports core events
(**) Microsoft Comfort Curve Keyboard 2000: Device: "/dev/input/event5"
(II) Microsoft Comfort Curve Keyboard 2000: Found 1 mouse buttons
(II) Microsoft Comfort Curve Keyboard 2000: Found scroll wheel(s)
(II) Microsoft Comfort Curve Keyboard 2000: Found relative axes
(II) Microsoft Comfort Curve Keyboard 2000: Found absolute axes
(II) Microsoft Comfort Curve Keyboard 2000: Found keys
(II) Microsoft Comfort Curve Keyboard 2000: Configuring as mouse
(II) Microsoft Comfort Curve Keyboard 2000: Configuring as keyboard
(**) Microsoft Comfort Curve Keyboard 2000: YAxisMapping: buttons 4 and 5
(**) Microsoft Comfort Curve Keyboard 2000: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Microsoft Comfort Curve Keyboard 2000" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_options" "lv3:ralt_switch"
(EE) Microsoft Comfort Curve Keyboard 2000: failed to initialize for relative axes.
(II) Microsoft Comfort Curve Keyboard 2000: initialized for absolute axes.
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event6)
(**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event6"
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as keyboard
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event7)
(**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
(**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event7"
(II) Logitech USB Receiver: Found 20 mouse buttons
(II) Logitech USB Receiver: Found scroll wheel(s)
(II) Logitech USB Receiver: Found relative axes
(II) Logitech USB Receiver: Found x and y relative axes
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as mouse
(II) Logitech USB Receiver: Configuring as keyboard
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) Logitech USB Receiver: initialized for relative axes.
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event10)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event2)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
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
```

---

### Post by donjon7 on 2010-12-27
Hi DarrenO,

I see you are having problems but they are not related to the screens which is traditional :)

I note your last reference was posted in 2007 [I](I tried using this guide, but I really don't understand how to piece it all together.
[http://linuxagora.com/vbforum/showthread.php?t=764](http://linuxagora.com/vbforum/showthread.php?t=764))[/I]

Obviously, Ubuntu has changed a lot since then... the first reference was much better...

What I would suggest is setting up a single  configuration with one set of the keyboad+mouse... grab the setting from xorg.conf for that... then do the same with the other set of keyboard+mouse...

Then break them down into different seats.

Did you roll back gdm and consolekit? 

You need to either roll it back or apply the patches which will enable it within the distro (I haven't read anything good about the patches so I rolled back)

regards,
donjon

---

### Post by Jummel on 2011-01-31
Hi DarrenO,

I have set up a multiseat as well, it has issues, but at least one seat works. As it is not working properly, I won't post my configurations here, just give you a link to my thread (which has my configurations) where hopefully someone can help me fix it.
[http://ubuntuforums.org/showthread.php?t=1678708]("http://ubuntuforums.org/showthread.php?t=1678708")

---

### Post by HermanAB on 2011-01-31
Howdy,

If I were you, I would go to my local recycling centre and pick up another machine for $50 or so and use it as a terminal to connect to the better machine using ssh or nomachine, rather than trying to make a pernickety multi-seat system.

---

### Post by Jummel on 2011-02-03
Hi DarrenO
I just got my multiseat working! I'll attach may xorg.conf and kdmrc.
You need to:
remove "corepointer" from your devices in server layout
change your mouse driver to "evdev"
remove all references to Xinerama.

Cheers

Jummel

---

