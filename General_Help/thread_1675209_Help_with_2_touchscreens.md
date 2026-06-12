---
title: "Help with 2 touchscreens"
date: 2011-01-25
forum: General Help
---

### Post by ideacoratex on 2011-01-25
hello can someone help me im trying to put 2 touchscreens working in the same pc im usin the evtouch driver but my second touchscreen doesnt work here is my xorg.conf and my xorg log.

Section "ServerLayout"
    Identifier     "seat1"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" Above "Screen0"
    InputDevice    "touchscreen1" "CorePointer"
    InputDevice    "Mouse0" 
    InputDevice    "Keyboard0" "CoreKeyboard"
    Option         "Xinerama" "0"
EndSection

Section "ServerLayout"
    Identifier     "seat2"
    Screen      0  "Screen2" 0 0
    Screen      1  "Screen3" Above "Screen2"
    InputDevice    "touchscreen0" "CorePointer"
    InputDevice    "Mouse1"
    InputDevice    "Keyboard1" "CoreKeyboard"
    Option         "Xinerama" "0"
EndSection

Section "Files"
    ModulePath      "/usr/lib/xorg/modules"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath        "built-ins"
EndSection

Section "Module"
    Load           "record"
    Load           "dri2"
    Load           "extmod"
    Load           "glx"
    Load           "dbe"
EndSection

Section "ServerFlags"
    Option         "AutoAddDevices" "off"
     #Option "AllowEmptyInput" "true"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "evdev"
    Option         "Device" "/dev/input/by-path/pci-0000:00:1d.0-usb-0:1.5:1.0-event-kbd"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "evdev"
    Option         "Device" "/dev/input/by-path/pci-0000:00:1d.0-usb-0:1.8:1.0-event-mouse"
EndSection

Section "InputDevice"
    Identifier     "Keyboard1"
    Driver         "evdev"
    Option         "Device" "/dev/input/by-path/pci-0000:00:1d.0-usb-0:1.6:1.0-event-kbd"
EndSection

Section "InputDevice"
    Identifier     "Mouse1"
    Driver         "evdev"
    Option         "Device" "/dev/input/by-path/pci-0000:00:1d.0-usb-0:1.7:1.0-event-mouse"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "CRT-1"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Monitor"
    Identifier     "Monitor2"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Monitor"
    Identifier     "Monitor3"
    VendorName     "Unknown"
    ModelName      "CRT-1"
    HorizSync       28.0 - 55.0
    VertRefresh     43.0 - 72.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 220"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 220"
    Option         "RandRRotation" "true"
#    Option         "Rotate" "right"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Device"
    Identifier     "Device2"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 220"
    BusID          "PCI:24:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device3"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 220"
    Option         "RandRRotation" "true"
#    Option         "Rotate" "right"
    BusID          "PCI:24:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: 1360x768"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT:"
    SubSection     "Display"
        Depth       24
    Modes        "1360x768"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen2"
    Device         "Device2"
    Monitor        "Monitor2"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: 1360x768"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen3"
    Device         "Device3"
    Monitor        "Monitor3"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT: "
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


Section "InputDevice"
   Identifier "touchscreen0"
   Driver "evtouch"
   Option "Device" "/dev/input/by-path/pci-0000:00:1a.0-usb-0:1.2:1.0-event"
   Option "DeviceName" "touchscreen"
   Option "MinX" "5011"
   Option "MinY" "1960"
   Option "MaxX" "1094"
   Option "MaxY" "4080"
   Option "ReportingMode" "Raw"
   Option "SendCoreEvents" "On"
EndSection


Section "InputDevice"
   Identifier "touchscreen1"
   Driver "evtouch"
   Option "Device" "/dev/input/by-path/pci-0000:00:1a.0-usb-0:1.1:1.0-event"
   Option "DeviceName" "touchscreen"
   Option "MinX" "5011"
   Option "MinY" "1960"
   Option "MaxX" "1094"
   Option "MaxY" "4080"
   Option "ReportingMode" "Raw"
   Option "SendCoreEvents" "On"
EndSection


Log


X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-25-server i686 Ubuntu
Current Operating System: Linux insight-1-desktop 2.6.34-020634-generic #020634 SMP Mon May 17 20:34:55 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.34-020634-generic root=UUID=a3fc1fca-2f37-4f57-8514-9cd0723ebc44 ro quiet splash
Build Date: 23 April 2010  05:11:50PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>) 
Current version of pixman: 0.16.4
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Jan 24 19:33:26 2011
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(++) ServerLayout "seat2"
(**) |-->Screen "Screen2" (0)
(**) |   |-->Monitor "Monitor2"
(**) |   |-->Device "Device2"
(**) |-->Screen "Screen3" (1)
(**) |   |-->Monitor "Monitor3"
(**) |   |-->Device "Device3"
(**) |-->Input Device "touchscreen0"
(**) |-->Input Device "dummy"
(**) |-->Input Device "Mouse1"
(**) |-->Input Device "Keyboard1"
(**) Option "Xinerama" "0"
(**) Option "AutoAddDevices" "off"
(**) Not automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(**) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins,
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(**) ModulePath set to "/usr/lib/xorg/modules"
(II) Loader magic: 0x81f0e80
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:1:0:0) 10de:0a20:1043:830f nVidia Corporation GT216 [GeForce GT 220] rev 162, Mem @ 0xf8000000/16777216, 0xd0000000/268435456, 0xce000000/33554432, I/O @ 0x00002100/128, BIOS @ 0x????????/524288
(--) PCI: (0:24:0:0) 10de:0a20:1043:8311 nVidia Corporation GT216 [GeForce GT 220] rev 162, Mem @ 0xf2000000/16777216, 0xe0000000/268435456, 0xf0000000/33554432, I/O @ 0x00001100/128, BIOS @ 0x????????/524288
(II) Open ACPI successful (/var/run/acpid.socket)
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded. This was enabled by default and also specified in the config file.
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
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
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) LoadModule: "evtouch"
(II) Loading /usr/lib/xorg/modules/input/evtouch_drv.so
(II) Module evtouch: vendor="Kenan Esau"
    compiled for 1.7.6, module version = 0.8.8
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(II) LoadModule: "void"
(WW) Warning, couldn't open module void
(II) UnloadModule: "void"
(EE) Failed to load module "void" (module does not exist, 0)
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(II) NVIDIA dlloader X Driver  195.36.24  Thu Apr 22 09:34:29 PDT 2010
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
(**) NVIDIA(0): Option "TwinView" "0"
(**) NVIDIA(0): Option "MetaModes" "DFP: 1360x768"
(**) Jan 24 19:33:27 NVIDIA(0): Enabling RENDER acceleration
(EE) Jan 24 19:33:27 NVIDIA(0): Failed to initialize the GLX module; please check in your X
(EE) Jan 24 19:33:27 NVIDIA(0):     log file that the GLX module has been loaded in your X
(EE) Jan 24 19:33:27 NVIDIA(0):     server, and that the module is the NVIDIA GLX module.  If
(EE) Jan 24 19:33:27 NVIDIA(0):     you continue to encounter problems, Please try
(EE) Jan 24 19:33:27 NVIDIA(0):     reinstalling the NVIDIA driver.
(II) Jan 24 19:33:32 NVIDIA(0): NVIDIA GPU GeForce GT 220 (GT216) at PCI:24:0:0 (GPU-0)
(--) Jan 24 19:33:32 NVIDIA(0): Memory: 1048576 kBytes
(--) Jan 24 19:33:32 NVIDIA(0): VideoBIOS: 70.16.2e.00.0d
(II) Jan 24 19:33:32 NVIDIA(0): Detected PCI Express Link width: 4X
(--) Jan 24 19:33:32 NVIDIA(0): Interlaced video modes are supported on this GPU
(--) Jan 24 19:33:32 NVIDIA(0): Connected display device(s) on GeForce GT 220 at PCI:24:0:0:
(--) Jan 24 19:33:32 NVIDIA(0):     Samsung SyncMaster (CRT-0)
(--) Jan 24 19:33:32 NVIDIA(0): Samsung SyncMaster (CRT-0): 400.0 MHz maximum pixel clock
(II) Jan 24 19:33:32 NVIDIA(0): Assigned Display Device: CRT-0
(II) Jan 24 19:33:32 NVIDIA(0): Validated modes:
(II) Jan 24 19:33:32 NVIDIA(0):     "DFP:1360x768"
(II) Jan 24 19:33:32 NVIDIA(0): Virtual screen size determined to be 1360 x 768
(--) Jan 24 19:33:32 NVIDIA(0): DPI set to (38, 39); computed from "UseEdidDpi" X config
(--) Jan 24 19:33:32 NVIDIA(0):     option
(==) Jan 24 19:33:32 NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(1): RGB weight 888
(==) NVIDIA(1): Default visual is TrueColor
(==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(1): Option "TwinView" "0"
(**) NVIDIA(1): Option "MetaModes" "CRT: "
(**) NVIDIA(1): Option "RandRRotation" "true"
(**) Jan 24 19:33:32 NVIDIA(1): Enabling RENDER acceleration
(II) Jan 24 19:33:32 NVIDIA(1): NVIDIA GPU GeForce GT 220 (GT216) at PCI:24:0:0 (GPU-0)
(--) Jan 24 19:33:32 NVIDIA(1): Memory: 1048576 kBytes
(--) Jan 24 19:33:32 NVIDIA(1): VideoBIOS: 70.16.2e.00.0d
(II) Jan 24 19:33:32 NVIDIA(1): Detected PCI Express Link width: 4X
(--) Jan 24 19:33:32 NVIDIA(1): Interlaced video modes are supported on this GPU
(--) Jan 24 19:33:32 NVIDIA(1): Connected display device(s) on GeForce GT 220 at PCI:24:0:0:
(--) Jan 24 19:33:32 NVIDIA(1):     Samsung SyncMaster (CRT-0)
(--) Jan 24 19:33:32 NVIDIA(1): Samsung SyncMaster (CRT-0): 400.0 MHz maximum pixel clock
(EE) Jan 24 19:33:32 NVIDIA(1): Unable to find available Display Devices for screen 1.
(EE) Jan 24 19:33:32 NVIDIA(1): No display devices found for this X screen.
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(--) Depth 24 pixmap format is 32 bpp
(II) Jan 24 19:33:32 NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
(II) Jan 24 19:33:33 NVIDIA(GPU-1): NVIDIA GPU GeForce GT 220 (GT216) at PCI:1:0:0 (GPU-1)
(--) Jan 24 19:33:33 NVIDIA(GPU-1): Memory: 1048576 kBytes
(--) Jan 24 19:33:33 NVIDIA(GPU-1): VideoBIOS: 70.16.68.00.00
(II) Jan 24 19:33:33 NVIDIA(GPU-1): Detected PCI Express Link width: 16X
(--) Jan 24 19:33:33 NVIDIA(GPU-1): Interlaced video modes are supported on this GPU
(--) Jan 24 19:33:33 NVIDIA(GPU-1): Connected display device(s) on GeForce GT 220 at PCI:1:0:0:
(--) Jan 24 19:33:33 NVIDIA(GPU-1):     Samsung SyncMaster (CRT-0)
(--) Jan 24 19:33:33 NVIDIA(GPU-1): Samsung SyncMaster (CRT-0): 400.0 MHz maximum pixel clock
(II) Jan 24 19:33:33 NVIDIA(0): Initialized GPU GART.
(II) Jan 24 19:33:33 NVIDIA(0): Setting mode "DFP:1360x768"
(II) Loading extension NV-GLX
(II) Jan 24 19:33:33 NVIDIA(0): Initialized OpenGL Acceleration
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) Jan 24 19:33:33 NVIDIA(0): Initialized X Rendering Acceleration
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(==) NVIDIA(0): DPMS enabled
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
(II) XKB: reuse xkmfile /var/lib/xkb/server-02D8252E59564A234380F1E5417646A9DB3B7452.xkm
State: S_UNTOUCHED    Action: No Action        Button: 0
State: S_TOUCHED    Action: No Action        Button: 0
State: S_LONGTOUCHED    Action: down        Button: 1
State: S_MOVING    Action: No Action        Button: 0
State: S_MAYBETAPPED    Action: click        Button: 1
State: S_ONEANDAHALFTAP    Action: down        Button: 3
(**) Option "MinX" "5011"
(**) Option "MaxX" "1094"
(**) Option "MinY" "1960"
(**) Option "MaxY" "4080"
(**) Option "DeviceName" "touchscreen"
(**) Option "SendCoreEvents" "On"
(**) Option "CorePointer"
(**) touchscreen: always reports core events
(II) XINPUT: Adding extended input device "touchscreen" (type: TOUCHSCREEN)
[COLOR=RoyalBlue](**) Option "Device" "/dev/input/by-path/pci-0000:00:1a.0-usb-0:1.2:1.0-event"
(EE) xf86OpenSerial: Cannot open device /dev/input/by-path/pci-0000:00:1a.0-usb-0:1.2:1.0-event
    No such file or directory.
(WW) touchscreen: cannot open input device
[dix] couldn't enable device 6[/COLOR]
(EE) Couldn't init device "touchscreen0"
(II) UnloadModule: "evtouch"
(II) LoadModule: "void"
(WW) Warning, couldn't open module void
(II) UnloadModule: "void"
(EE) Failed to load module "void" (module does not exist, 0)
(EE) No input driver matching `void'
(**) Mouse1: always reports core events
(**) Mouse1: Device: "/dev/input/by-path/pci-0000:00:1d.0-usb-0:1.7:1.0-event-mouse"
(EE) Unable to open evdev device "/dev/input/by-path/pci-0000:00:1d.0-usb-0:1.7:1.0-event-mouse".
(II) UnloadModule: "evdev"
(EE) PreInit returned NULL for "Mouse1"
(**) Option "CoreKeyboard"
(**) Keyboard1: always reports core events
(**) Keyboard1: Device: "/dev/input/by-path/pci-0000:00:1d.0-usb-0:1.6:1.0-event-kbd"
(EE) Unable to open evdev device "/dev/input/by-path/pci-0000:00:1d.0-usb-0:1.6:1.0-event-kbd".
(II) UnloadModule: "evdev"
(EE) PreInit returned NULL for "Keyboard1"
(EE) xf86OpenSerial: Cannot open device /dev/input/by-path/pci-0000:00:1a.0-usb-0:1.2:1.0-event
    No such file or directory.
(WW) touchscreen: cannot open input device
[dix] couldn't enable device 6
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(II) AutoAddDevices is off - not adding device.
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(II) AutoAddDevices is off - not adding device.
(II) config/udev: Adding input device USB Touchscreen 0dfc:0001 (/dev/input/event3)
(II) AutoAddDevices is off - not adding device.
(II) config/udev: Adding input device USB Touchscreen 0dfc:0001 (/dev/input/mouse0)
(II) AutoAddDevices is off - not adding device.
(II) config/udev: Adding input device HP WMI hotkeys (/dev/input/event2)
(II) AutoAddDevices is off - not adding device.
(II) config/udev: Adding input device USB Touchscreen 0dfc:0001 (/dev/input/mouse1)
(II) AutoAddDevices is off - not adding device.
(II) config/udev: Adding input device USB Touchscreen 0dfc:0001 (/dev/input/event4)
(II) AutoAddDevices is off - not adding device.


Can someone help me tanks in advance

---

### Post by ideacoratex on 2011-01-26
i have discovered that if i restart gdm all work fine can someone help me and tell me how to make a restart of gdm automatic when ubuntu starts .

tanks

---

