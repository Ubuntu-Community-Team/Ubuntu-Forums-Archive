---
title: "How to fix screen resolution"
date: 2011-04-16
forum: General Help
---

### Post by dmu on 2011-04-16
Ok,

I've really had enough of this screen resolution thing. Running KDE 4 I have a really low resolution on my 1920x1080 HD Acer 8930 Laptop I open firefox and it is filling 80% of the width of my screen and all of the height of my screen. (This is an 18.5 inch widescreen display!). I cant even get 2 firefox windows side by side. Ive got an Nvidia GeForce 9600m with the very latest driver downloaded today and running nvidia-settings I can select 1920x1080 but it doesnt make a difference.

Then I log into Gnome and get a slightly better resolution I can line up at least 2 firefox windows side by side and there is even a little bit of space between the firefox window and the bottom of the desktop but it wont go full 1920x1080 either.

Neither KDE or Gnome are running at full resolution. 

If I start windows and use the same windows Nvidia driver it is quite happy to display the full 1920x1080 res. 

After using nvidia-settings xrandr reports that im running at 1920x1080 which is obviously not the case? so whats is up??


```


$xrandr output

Screen 0: minimum 320 x 175, current 1920 x 1080, maximum 1920 x 1080
default connected 1920x1080+0+0 0mm x 0mm

   1920x1080     140.0     51.0*
   1680x1050      52.0
   1600x1024      53.0
   1440x900       54.0
   1400x1050      55.0
   1360x768       56.0     57.0
   1280x1024      58.0     59.0
   1280x960       60.0
   1152x864       61.0     62.0     63.0     64.0     65.0     66.0
   1024x768       67.0     68.0     69.0     70.0     71.0     72.0
   960x720        73.0
   960x600        74.0
   960x540        75.0
   928x696        76.0
   896x672        77.0     78.0
   840x525        79.0     80.0     81.0     82.0     83.0
   832x624        84.0
   800x600        85.0     86.0     87.0     88.0     89.0     90.0     91.0 92.0     93.0     94.0
   800x512        95.0
   720x450        96.0
   720x400        97.0
   700x525        98.0     99.0    100.0    101.0
   680x384       102.0    103.0
   640x512       104.0    105.0    106.0
   640x480       107.0    108.0    109.0    110.0    111.0    112.0
   640x400       113.0
   640x350       114.0
   576x432       115.0    116.0    117.0    118.0    119.0    120.0    121.0
   512x384       122.0    123.0    124.0    125.0    126.0
   416x312       127.0
   400x300       128.0    129.0    130.0    131.0    132.0
   360x200       133.0
   320x240       134.0    135.0    136.0    137.0
   320x200       138.0
   320x175       139.0


```and my xorg.conf

```


Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0   
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"    
    Option         "Xinerama" "0"            
EndSection                                   

Section "Module"
    Load           "glx"
EndSection              

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "keyboard" 
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

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection                             

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown" 
    ModelName      "CMO"     
    HorizSync       30.0 - 83.0
    VertRefresh     55.0 - 75.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9600M GT"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

Section "Screen"

# Removed Option "metamodes" "DFP-0: nvidia-auto-select +0+0, DFP-1: nvidia-auto-select +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0, DFP-1: 1024x768+0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


```I used [http://www.x.org/wiki/FAQVideoModes#ObtainingmodelinesfromWindowsprogramPowerStrip](http://www.x.org/wiki/FAQVideoModes#ObtainingmodelinesfromWindowsprogramPowerStrip)
Powerstrip from my working windows setup to get a Linux Modeline and changed my "Monitor" to look like

```

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown" 
    ModelName      "CM0"     
    ModeLine       "1920x1080" 138.656 1920 1968 2000 2080 1080 1083 1088 1111 +hsync +vsync
EndSection

```and restarted which made no difference either...

Here is my Xorg.0.log

```


X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux muji 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Apr 16 12:47:37 2011
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
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
(==) ModulePath set to "/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 5.0
    X.Org XInput driver : 4.0
    X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@1:0:0) nVidia Corporation GeForce 9600M GT rev 161, Mem @ 0xd2000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x00005000/128
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  260.19.44  Sun Feb 27 21:47:21 PST 2011
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
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
    compiled for 1.6.0, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  260.19.44  Sun Feb 27 21:31:52 PST 2011
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "1"
(**) NVIDIA(0): Option "MetaModes" "DFP-0: nvidia-auto-select +0+0, DFP-1: 1024x768 +0+0"
(**) Apr 16 12:47:37 NVIDIA(0): Enabling RENDER acceleration
(II) Apr 16 12:47:37 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Apr 16 12:47:37 NVIDIA(0):     enabled.
(II) Apr 16 12:47:41 NVIDIA(0): NVIDIA GPU GeForce 9600M GT (G96) at PCI:1:0:0 (GPU-0)
(--) Apr 16 12:47:41 NVIDIA(0): Memory: 1048576 kBytes
(--) Apr 16 12:47:41 NVIDIA(0): VideoBIOS: 62.94.4a.00.23
(II) Apr 16 12:47:41 NVIDIA(0): Detected PCI Express Link width: 16X
(--) Apr 16 12:47:41 NVIDIA(0): Interlaced video modes are supported on this GPU
(--) Apr 16 12:47:41 NVIDIA(0): Connected display device(s) on GeForce 9600M GT at PCI:1:0:0
(--) Apr 16 12:47:41 NVIDIA(0):     Chi Mei Optoelectronics corp. (DFP-0)
(--) Apr 16 12:47:41 NVIDIA(0): Chi Mei Optoelectronics corp. (DFP-0): 330.0 MHz maximum pixel
(--) Apr 16 12:47:41 NVIDIA(0):     clock
(--) Apr 16 12:47:41 NVIDIA(0): Chi Mei Optoelectronics corp. (DFP-0): Internal Dual Link
(--) Apr 16 12:47:41 NVIDIA(0):     LVDS
(**) Apr 16 12:47:41 NVIDIA(0): TwinView enabled
(II) Apr 16 12:47:41 NVIDIA(0): Display Device found referenced in MetaMode: DFP-0
(WW) Apr 16 12:47:41 NVIDIA(0): TwinView requested, but only 1 display devices found.
(II) Apr 16 12:47:42 NVIDIA(0): Assigned Display Device: DFP-0
(WW) Apr 16 12:47:42 NVIDIA(0): Invalid display device in Mode Description
(WW) Apr 16 12:47:42 NVIDIA(0):     "DFP-1:1024x768+0+0"
(WW) Apr 16 12:47:42 NVIDIA(0): Not using mode description "DFP-1:1024x768+0+0"; unable to map
(WW) Apr 16 12:47:42 NVIDIA(0):     to display device
(II) Apr 16 12:47:42 NVIDIA(0): Validated modes:
(II) Apr 16 12:47:42 NVIDIA(0):     "DFP-0:nvidia-auto-select+0+0,DFP-1:1024x768+0+0"
(II) Apr 16 12:47:42 NVIDIA(0): Virtual screen size determined to be 1920 x 1080
(--) Apr 16 12:47:44 NVIDIA(0): DPI set to (118, 119); computed from "UseEdidDpi" X config
(--) Apr 16 12:47:44 NVIDIA(0):     option
(==) Apr 16 12:47:44 NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) Apr 16 12:47:44 NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
(II) Apr 16 12:47:44 NVIDIA(0): Initialized GPU GART.
(WW) Apr 16 12:47:44 NVIDIA(0): ACPI: Error: Unable to find the DOS (Enable/Disable output
(WW) Apr 16 12:47:44 NVIDIA(0):     switching) file path under /proc/acpi/video. The NVIDIA X
(WW) Apr 16 12:47:44 NVIDIA(0):     driver will not be able to respond to ACPI display change
(WW) Apr 16 12:47:44 NVIDIA(0):     hotkey events.
(WW) Apr 16 12:47:44 NVIDIA(0): ACPI: Error: Unable to find the brightness file path under
(WW) Apr 16 12:47:44 NVIDIA(0):     /proc/acpi/video. The NVIDIA X driver will not be able to
(WW) Apr 16 12:47:44 NVIDIA(0):     respond to ACPI brightness change hotkey events.
(II) Apr 16 12:47:44 NVIDIA(0): Setting mode
(II) Apr 16 12:47:44 NVIDIA(0):     "DFP-0:nvidia-auto-select+0+0,DFP-1:1024x768+0+0"
(II) Loading extension NV-GLX
(II) Apr 16 12:47:45 NVIDIA(0): Initialized OpenGL Acceleration
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) Apr 16 12:47:45 NVIDIA(0): Initialized X Rendering Acceleration
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
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
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 2.1.1
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event5"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "gb"
(**) AT Translated Set 2 keyboard: xkb_layout: "gb"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event4"
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
(II) config/hal: Adding input device SynPS/2 Synaptics TouchPad
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 0.99.3
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(II) Synaptics touchpad driver version 0.99.3
(**) Option "Device" "/dev/input/event9"
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
(II) SynPS/2 Synaptics TouchPad: buttons: left right middle double triple
(--) SynPS/2 Synaptics TouchPad touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) filter chain progression: 2.00
(**) SynPS/2 Synaptics TouchPad: (accel) filter stage 0: 20.00 ms
(**) SynPS/2 Synaptics TouchPad: (accel) set acceleration profile 0
(--) SynPS/2 Synaptics TouchPad touchpad found
(WW) AT Translated Set 2 keyboard: unable to handle keycode 435


```

---

### Post by dmu on 2011-04-18
bump
anyone?

---

