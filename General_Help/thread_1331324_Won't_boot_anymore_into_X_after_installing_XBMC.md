---
title: "Won't boot anymore into X after installing XBMC"
date: 2009-11-19
forum: General Help
---

### Post by surfinmdq on 2009-11-19
Hi guys,

please help!!! grrrr
I'm writing this from the LiveCD because I can't boot in X.

The last thing I remember I did before getting system screwed up is installing XBMC -X-BOX Multimedia Center- which adds it's own user group aswell creates a separate user to log-in.

Ubuntu keeps booting to the console and I can't make the X server run. The menu driven options -which appears after X failing to start in the boot-up process- are of not use because I can't get back my configuration or set standar X config.

Any idea on how to make system boot again?
Thank you!

---

### Post by PmDematagoda on 2009-11-19
What is the hardware you use? Also, could you post the contents of:
```
/var/log/Xorg.0.log
```
in the malfunctioning Ubuntu install.

---

### Post by surfinmdq on 2009-11-19
Hi!

Thank you for your swift assistance!! Here it is:


X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server x86_64 Ubuntu
Current Operating System: Linux americandad 2.6.31-15-generic #50-Ubuntu SMP Tue Nov 10 14:53:52 UTC 2009 x86_64
Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.31-15-generic root=UUID=878887fe-1654-4843-b5f8-5cf51e40e075 ro splash vga=789 quiet splash
Build Date: 26 October 2009  05:19:56PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Nov 18 22:09:00 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
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
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0xb40
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 5.0
    X.Org XInput driver : 4.0
    X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0:1:0:0) 10de:0640:0000:0000 nVidia Corporation G96 [GeForce 9500 GT] rev 161, Mem @ 0xf2000000/16777216, 0xe0000000/268435456, 0xf0000000/33554432, I/O @ 0x0000c000/128, BIOS @ 0x????????/524288
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) No APM support in BIOS or kernel
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
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
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  190.42  Tue Oct 20 21:19:30 PDT 2009
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
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  190.42  Tue Oct 20 20:42:04 PDT 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) Nov 18 22:09:00 NVIDIA(0): Enabling RENDER acceleration
(II) Nov 18 22:09:00 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Nov 18 22:09:00 NVIDIA(0):     enabled.
(II) Nov 18 22:09:03 NVIDIA(0): NVIDIA GPU GeForce 9500 GT (G96) at PCI:1:0:0 (GPU-0)
(--) Nov 18 22:09:03 NVIDIA(0): Memory: 1048576 kBytes
(--) Nov 18 22:09:03 NVIDIA(0): VideoBIOS: 62.94.36.00.00
(II) Nov 18 22:09:03 NVIDIA(0): Detected PCI Express Link width: 16X
(--) Nov 18 22:09:03 NVIDIA(0): Interlaced video modes are supported on this GPU
(--) Nov 18 22:09:03 NVIDIA(0): Connected display device(s) on GeForce 9500 GT at PCI:1:0:0:
(--) Nov 18 22:09:03 NVIDIA(0):     LG 710E (CRT-1)
(--) Nov 18 22:09:03 NVIDIA(0): LG 710E (CRT-1): 400.0 MHz maximum pixel clock
(II) Nov 18 22:09:03 NVIDIA(0): Assigned Display Device: CRT-1
(==) Nov 18 22:09:03 NVIDIA(0): 
(==) Nov 18 22:09:03 NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) Nov 18 22:09:03 NVIDIA(0):     will be used as the requested mode.
(==) Nov 18 22:09:03 NVIDIA(0): 
(II) Nov 18 22:09:03 NVIDIA(0): Validated modes:
(II) Nov 18 22:09:03 NVIDIA(0):     "nvidia-auto-select"
(II) Nov 18 22:09:03 NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(--) Nov 18 22:09:03 NVIDIA(0): DPI set to (98, 104); computed from "UseEdidDpi" X config
(--) Nov 18 22:09:03 NVIDIA(0):     option
(==) Nov 18 22:09:03 NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
(II) Nov 18 22:09:03 NVIDIA(0): Initialized GPU GART.
(II) Nov 18 22:09:03 NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) Nov 18 22:09:03 NVIDIA(0): Initialized OpenGL Acceleration
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) Nov 18 22:09:03 NVIDIA(0): Initialized X Rendering Acceleration
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
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
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing extension GLX
(EE) config/hal: couldn't initialise context: unknown error (null)
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 2.2.5
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "es"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "es"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "es"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
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
(II) config/hal: Adding input device Genius 4D Scroll Mouse
(**) Genius 4D Scroll Mouse: always reports core events
(**) Genius 4D Scroll Mouse: Device: "/dev/input/event4"
(II) Genius 4D Scroll Mouse: Found 3 mouse buttons
(II) Genius 4D Scroll Mouse: Found x and y relative axes
(II) Genius 4D Scroll Mouse: Found scroll wheel(s)
(II) Genius 4D Scroll Mouse: Configuring as mouse
(**) Genius 4D Scroll Mouse: YAxisMapping: buttons 4 and 5
(**) Genius 4D Scroll Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Genius 4D Scroll Mouse" (type: MOUSE)
(**) Genius 4D Scroll Mouse: (accel) keeping acceleration scheme 1
(**) Genius 4D Scroll Mouse: (accel) filter chain progression: 2.00
(**) Genius 4D Scroll Mouse: (accel) filter stage 0: 20.00 ms
(**) Genius 4D Scroll Mouse: (accel) set acceleration profile 0
(II) Genius 4D Scroll Mouse: initialized for relative axes.
(II) AT Translated Set 2 keyboard: Close
(II) UnloadModule: "evdev"
(II) Power Button: Close
(II) UnloadModule: "evdev"
(II) Power Button: Close
(II) UnloadModule: "evdev"
(II) Macintosh mouse button emulation: Close
(II) UnloadModule: "evdev"
(II) Genius 4D Scroll Mouse: Close
(II) UnloadModule: "evdev"
 ddxSigGiveUp: Closing log

Thanks again!


EDIT: I found this error above, the same it shows in the recovery window just after fail loading X.

(EE) config/hal: couldn't initialise context: unknown error (null)

Best

---

### Post by PmDematagoda on 2009-11-19
Can you post the contents of:-
```
cat /etc/X11/xorg.conf
```

---

### Post by surfinmdq on 2009-11-19
Here it is:

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder58)  Tue Oct 20 21:25:04 PDT 2009


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
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


=(

---

### Post by surfinmdq on 2009-11-19
You're from Sri Lanka!? Cool!! It's a pleasure to communicate with someone on the other side of the world! Best!!

---

### Post by surfinmdq on 2009-11-19
If you think it will be hard to diagnose my problem, just let me know how can I backup the menu layout (I mean the GNOME menu) because I customized it hard to fit my needs/taste and don't want to loose all that work.

I will install -again- a plain new copy of Ubuntu... grrrrrr.

---

### Post by PmDematagoda on 2009-11-21
Hey, sorry for the late reply. About your problem, can you try editing your xorg.conf file by adding this line:-
```
"AutoAddDevices" "off"
```
to the ServerLayout section to make it look like this:-
```
Section "ServerLayout"
Identifier "Layout0"
Screen 0 "Screen0" 0 0
"AutoAddDevices" "off"
InputDevice "Keyboard0" "CoreKeyboard"
InputDevice "Mouse0" "CorePointer"
EndSection
```

You can open the file for editing with:-
```
sudo nano /etc/X11/xorg.conf
```
after editing, you can exit by pressing Ctrl+X, make sure you save the changes. Then see if X works properly.

---

### Post by surfinmdq on 2009-11-28
Hi!

Well, thanks for your kind help but don't worry, actually I give up on that and installed a clean new Karmic, that was faster than keep troubleshooting the issue.

As a side benefit, I ended erasing all my config settings in ~ so now I have a clean and consistent new system working very good -but not so good the hibernation feature on my 64-bit box.

I learned this the hard way but in Linux systems things can be wrecked easyly, may be not as Window$ but still too easy. So, I download, install and try all the new soft in a virtual machine and later if there were no problem I run it on my everyday Ubuntu.

Thanks anyway for your great help!

---

