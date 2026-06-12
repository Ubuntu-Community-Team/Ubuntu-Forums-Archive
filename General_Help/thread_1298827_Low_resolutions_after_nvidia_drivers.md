---
title: "Low resolutions after nvidia drivers"
date: 2009-10-23
forum: General Help
---

### Post by cel13 on 2009-10-23
Hello, just installed Kubuntu, so I'm new to Linux.
I'm using nVidia Geforce 8600GTS so I downloaded and installed latest driver. Install was successful but now only resolutions I can choose are 640x480 and 320x240. I have tried many tutorials but I can't get it fixed.

Thank you

---

### Post by Giblet5 on 2009-10-23
> **cel13 said:**
> Hello, just installed Kubuntu, so I'm new to Linux.
I'm using nVidia Geforce 8600GTS so I downloaded and installed latest driver. Install was successful but now only resolutions I can choose are 640x480 and 320x240. I have tried many tutorials but I can't get it fixed.

Thank you

Click System->Administration->NVIDIA X Server Settings

Try changing the resolution from there.

---

### Post by cel13 on 2009-10-23
I'm using kubuntu, but I tried typing nvidia-settings in Terminal and I control panel opened - is this the same thing ? If it is then  I can't change it from there either.

---

### Post by Giblet5 on 2009-10-23
> **cel13 said:**
> I'm using kubuntu, but I tried typing nvidia-settings in Terminal and I control panel opened - is this the same thing ? If it is then  I can't change it from there either.


Good sleuth work!

Can you post the contents of your /var/log/Xorg.0.log file?

Maybe there are clues there.

Worst case scenario is that you look up the horizontal and vertical timing of your monitor and we create a custom-tailored xorg.conf file.

---

### Post by DeMus on 2009-10-23
> **cel13 said:**
> Hello, just installed Kubuntu, so I'm new to Linux.
I'm using nVidia Geforce 8600GTS so I downloaded and installed latest driver. Install was successful but now only resolutions I can choose are 640x480 and 320x240. I have tried many tutorials but I can't get it fixed.

Thank you

How did you install the driver and which version is it?

---

### Post by cel13 on 2009-10-23
Thanks for helping

```

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux Ordi 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Oct 23 14:56:22 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(**) Option "DontZap" "True"
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

(--) PCI:*(0@1:0:0) nVidia Corporation GeForce 8600 GTS rev 161, Mem @ 0xfd000000/16777216, 0xc0000000/268435456, 0xfa000000/33554432, I/O @ 0x0000bc00/128, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
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
(II) NVIDIA GLX Module  185.18.36  Fri Aug 14 17:50:12 PDT 2009
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
(II) NVIDIA dlloader X Driver  185.18.36  Fri Aug 14 17:24:40 PDT 2009
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
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
(II) NVIDIA(0): NVIDIA GPU GeForce 8600 GTS (G84) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 60.84.18.00.08
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 8600 GTS at PCI:1:0:0:
(--) NVIDIA(0):     CRT-0
(--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(==) NVIDIA(0): 
(==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) NVIDIA(0):     will be used as the requested mode.
(==) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 640 x 480
(WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
(WW) NVIDIA(0):     from CRT-0's EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) NVIDIA(0): Built-in logo is bigger than the screen.
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
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
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "ee"
(**) AT Translated Set 2 keyboard: xkb_layout: "ee"
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
(II) config/hal: Adding input device ImPS/2 Logitech Wheel Mouse
(**) ImPS/2 Logitech Wheel Mouse: always reports core events
(**) ImPS/2 Logitech Wheel Mouse: Device: "/dev/input/event5"
(II) ImPS/2 Logitech Wheel Mouse: Found 3 mouse buttons
(II) ImPS/2 Logitech Wheel Mouse: Found x and y relative axes
(II) ImPS/2 Logitech Wheel Mouse: Configuring as mouse
(**) ImPS/2 Logitech Wheel Mouse: YAxisMapping: buttons 4 and 5
(**) ImPS/2 Logitech Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "ImPS/2 Logitech Wheel Mouse" (type: MOUSE)
(**) ImPS/2 Logitech Wheel Mouse: (accel) keeping acceleration scheme 1
(**) ImPS/2 Logitech Wheel Mouse: (accel) filter chain progression: 2.00
(**) ImPS/2 Logitech Wheel Mouse: (accel) filter stage 0: 20.00 ms
(**) ImPS/2 Logitech Wheel Mouse: (accel) set acceleration profile 0
(II) NVIDIA(0): Setting mode "CRT-0:nvidia-auto-select@1440x900+0+0"
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) NVIDIA(0): Setting mode "CRT-0:nvidia-auto-select@1440x900+0+0"
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) NVIDIA(0): Setting mode "CRT-0:nvidia-auto-select@1440x900+0+0"
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) NVIDIA(0): Setting mode "CRT-0:nvidia-auto-select@1440x900+0+0"
(II) NVIDIA(0): Setting mode "nvidia-auto-select"

```

---

### Post by cel13 on 2009-10-23
> **DeMus said:**
> How did you install the driver and which version is it?

version is: 185.18.36
I logged off, opened console, then I used "sudo/etc/init.d/kdm stop" and then I installed like this "sudo sh driverfile.run" and I just followed instructions there.

Oh I'm sorry I just double posted :(

---

### Post by Giblet5 on 2009-10-23
> **cel13 said:**
> Thanks for helping

```
(WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
(WW) NVIDIA(0):     from CRT-0's EDID.
```

There it is.

The card can't get an ID of the monitor so it can't determine "safe" resolutions and timings.

Probably a D-15 style "VGA" connector? Those don't pass DDC data sometimes.

What vendor/model monitor are you using?

Do you have the max horizontal and vertical frequencies handy?

---

### Post by cel13 on 2009-10-23
> **Giblet5 said:**
> There it is.

The card can't get an ID of the monitor so it can't determine "safe" resolutions and timings.

Probably a D-15 style "VGA" connector? Those don't pass DDC data sometimes.

What vendor/model monitor are you using?

Do you have the max horizontal and vertical frequencies handy?

I tried searching info, but I'm not sure if it's what you asked, VGA (HD-15) - is this connector ? I'm sorry I don't really know what are horizontal and vertical frequencies.
By the way it's Grundig Vision 2

Thank you

---

### Post by manoriax on 2009-10-23
Any technical data sheet within the monitor's manual?

---

### Post by Giblet5 on 2009-10-23
Found it: Grundig Vision II 26" LCD with 1280x760 (720p) native resolution. Is that right?

I'll create a rough xorg.conf as soon as I track down its timing numbers.

---

### Post by P4man on 2009-10-23
sorry to throw this rant in here which isnt going to help anyone, but this seems to happen frequently with the nvidia drivers (or should we blame the cards?). I really wish nvidia added an option to override everything and have  a "Stop wining, ignore EDID because I know what Im doing and I want x by y resolution at z Hz " button. 

/end rant

---

### Post by Giblet5 on 2009-10-23
> **P4man said:**
> sorry to throw this rant in here which isnt going to help anyone, but this seems to happen frequently with the nvidia drivers (or should we blame the cards?). I really wish nvidia added an option to override everything and have  a "Stop wining, ignore EDID because I know what Im doing and I want x by y resolution at z Hz " button. 

/end rant

No, this is a limitation of using D15 vga connectors/cables.

The cable can't accurately transfer data about the monitor back to the video card.

The reason you hear about this more with nvidia cards is because there are a LOT more nvidia cards in use with older VGA connectors.

ATI cards are really good, but only in the past two years have they been worth actual money... Most <= 2yo systems use DVI or dual-DVI connectors and this isn't a problem.

---

### Post by cel13 on 2009-10-23
> **Giblet5 said:**
> Found it: Grundig Vision II 26" LCD with 1280x760 (720p) native resolution. Is that right?

I'll create a rough xorg.conf as soon as I track down its timing numbers.

Grundig vision 2 19-2801, actually it is 1440x900

---

### Post by Giblet5 on 2009-10-23
> **cel13 said:**
> Grundig vision 2 19-2801, actually it is 1440x900

Grundig doesn't publish their sync timings...

You have two choices:

A) Get a DVI cable and connect the monitor to the PC using that. This is the best solution as a digital signal will be clearer than the analog signal you'll use with a VGA cable.

****** OR *******

B) Contact Grundig's customer support and tell them you need:
"Horizontal Sync Frequency range, in hertz"
"Vertical Sync Frequency rangs, in hertz"

Those will be in a range, like 30.0Khz - 75.0Khz, but yours WILL be different. Getting it wrong can make the display unreadable or can actually damage the monitor.

Plug those in to this xorg.conf, in the "Monitor" section. Then, make a copy of your old xorg.conf, and move the new one to /etc/X11/xorg.conf.

```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Generic Mouse"
    Option         "BlankTime" "20"
    Option         "OffTime" "25"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "dbe"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "record"
    Load           "type1"
    Load           "vbe"
    Load           "v4l"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
        # Option        "Emulate3Buttons" "true"
    Option         "ZAxisMapping" "4 5"
    Option         "Buttons" "9"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "Monitor"
    Identifier     "Grundig Vision II"
    HorizSync       30.0 - 94.0
    VertRefresh     48.0 - 85.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA 8600GS"
    Driver         "nvidia"
    Option         "FlatPanelProperties" "Scaling=centered, Dithering=enabled"
    Option         "UseEDIDFreqs" "false"
    Option         "UseEDIDDpi" "false"
    Option         "AllowDDCCI" "false"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA 8600GS"
    Monitor        "Grundig Vision II"
    DefaultDepth    24
    Option         "UseEdidFreqs" "False"
    Option         "UseEdid" "False"
    Option         "AllowDDCCI" "False"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1440x900"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1440x900"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1440x900"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1440x900"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1440x900"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1440x900"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
    Option         "RENDER" "True"
    Option         "DAMAGE" "True"
EndSection
```

---

### Post by P4man on 2009-10-23
If it helps, my monitor has the same native resolution (1440x900) @60Hz (can do 75 apparently), and the relevant section of my xorg.conf is:

```
Section "Monitor"
  # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Acer AL1916W"
[B]    HorizSync       30.0 - 82.0
    VertRefresh     56.0 - 76.0[/B]
    Option         "DPMS"
EndSection
```

Id also like to add it works with this nvidia card and monitor with a plain 15 pin VGA cable, whereas most people reporting these issues seem to be using a DVI connection.

---

### Post by cel13 on 2009-10-23
> **Giblet5 said:**
> Grundig doesn't publish their sync timings...

You have two choices:

A) Get a DVI cable and connect the monitor to the PC using that. This is the best solution as a digital signal will be clearer than the analog signal you'll use with a VGA cable.

****** OR *******

B) Contact Grundig's customer support and tell them you need:
"Horizontal Sync Frequency range, in hertz"
"Vertical Sync Frequency rangs, in hertz"

Those will be in a range, like 30.0Khz - 75.0Khz, but yours WILL be different. Getting it wrong can make the display unreadable or can actually damage the monitor.

Plug those in to this xorg.conf, in the "Monitor" section. Then, make a copy of your old xorg.conf, and move the new one to /etc/X11/xorg.conf.

```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Generic Mouse"
    Option         "BlankTime" "20"
    Option         "OffTime" "25"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "dbe"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "record"
    Load           "type1"
    Load           "vbe"
    Load           "v4l"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
        # Option        "Emulate3Buttons" "true"
    Option         "ZAxisMapping" "4 5"
    Option         "Buttons" "9"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "Monitor"
    Identifier     "Grundig Vision II"
    HorizSync       30.0 - 94.0
    VertRefresh     48.0 - 85.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA 8600GS"
    Driver         "nvidia"
    Option         "FlatPanelProperties" "Scaling=centered, Dithering=enabled"
    Option         "UseEDIDFreqs" "false"
    Option         "UseEDIDDpi" "false"
    Option         "AllowDDCCI" "false"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA 8600GS"
    Monitor        "Grundig Vision II"
    DefaultDepth    24
    Option         "UseEdidFreqs" "False"
    Option         "UseEdid" "False"
    Option         "AllowDDCCI" "False"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1440x900"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1440x900"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1440x900"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1440x900"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1440x900"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1440x900"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
    Option         "RENDER" "True"
    Option         "DAMAGE" "True"
EndSection
```

Thanks a lot, I'll try to get this info from Grundig
Thanks P4man, is it safe for me to try it or could it do any damage ?

---

### Post by P4man on 2009-10-23
> **cel13 said:**
> Thanks a lot, I'll try to get this info from Grundig
Thanks P4man, is it safe for me to try it or could it do any damage ?

I dont think it could do any damage. Modern monitors will simply display "out of range" if they cant handle the signal (and its unlikely your monitor would not be able to handle the same frequencies as mine).

But if it will actually help that is something else.

---

### Post by Giblet5 on 2009-10-23
> **cel13 said:**
> Thanks a lot, I'll try to get this info from Grundig
Thanks P4man, is it safe for me to try it or could it do any damage ?

It should be reasonably close to your monitor.

If the display blanks, just flip to the console via CtrlAltF1, log in, move the backup xorg.conf back to /etc/X11/xorg.conf, and restart the session via ```
sudo /etc/init.d/gdm restart
```

---

### Post by cel13 on 2009-10-23
Okay, I used it, I got some new resolutions that are better but still no 1440x900.

Edit: I just opened up nVidia X Server settings and now I was able to choose 1440x900 from there :)

Thanks a lot everyone

---

