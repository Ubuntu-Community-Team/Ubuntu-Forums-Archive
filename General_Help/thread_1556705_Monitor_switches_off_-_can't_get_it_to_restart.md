---
title: "Monitor switches off - can't get it to restart"
date: 2010-08-19
forum: General Help
---

### Post by static_void on 2010-08-19
I'm running ubuntu 10.04 on a new pc I just bought. Every so often the monitor will just shut down and display a message: "no signal input".

I'm sure the computer is still running though because the fan is still running and all lights etc. are still on.

I've tried switching the monitor on and off and there is still no input signal, the only solution is to reboot the entire computer.

???

---

### Post by happyhamster on 2010-08-19
What type of videocard are you using? And which driver? To identify the hardware, you can use the command:
```

lspci | grep vga -i

```
in a terminal (Applications-->Accessories-->Terminal).

---

### Post by static_void on 2010-08-20
02:00.0 VGA compatible controller: nVidia Corporation GT216 [GeForce GT 220] (rev a2)

---

### Post by happyhamster on 2010-08-21
@static_void: bumping this thread on your behalf. The symptoms you're seeing are the same as I'm seeing on my Maverick install, but in my case it's an ATI (radeon) kernel mode problem. Forcing UMS fixed all problems for me (so far). The Nvidia driver doesn't have that option IIRC. 

Anyway, you'll probably just have to wait until some Nvidia users decide to chime in to provide some meaningful answers.

---

### Post by static_void on 2010-08-23
I've realized its not just the monitor that suddenly switches off but all hardware devices (keyboard, mouse, speaker etc.).  When this happens I need to turn off the computer and leave it for a little while before turning it back on again. If I turn it on too soon none of the hardware devices get recognized.

Any other reason this could be happening?


Also... sometimes the computer will just freeze, I can't move the cursor or type in anything on the keyboard so I just resort to turning the computer on and off again. I'm sure this is the same problem as above although somehow the screens back buffer doesn't get cleared.

---

### Post by happyhamster on 2010-08-23
> **static_void said:**
> I've realized its not just the monitor that suddenly switches off but all hardware devices (keyboard, mouse, speaker etc.).  When this happens I need to turn off the computer and leave it for a little while before turning it back on again. If I turn it on too soon none of the hardware devices get recognized.
When the computer appears frozen, does it still respond to the sequence:

alt + SysRq + r
alt + SysRq + e
alt + SysRq + i
alt + SysRq + s
alt + SysRq + u
alt + SysRq + b

(This will reboot the system in a gentler way, minimizing the chance of filesystem damage. See: [http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key))

> Any other reason this could be happening?
Perhaps because of hardware? Do you have another operating system on the machine (e.g. windows). If so, does that installation run well? One thing you could try: boot from a live-cd, and run memtest for a few hours (when booting a live-cd, just press a key when the first welcome-screen appears; this will bring up a menu from which you can run the memory test.)

> 
Also... sometimes the computer will just freeze, I can't move the cursor or type in anything on the keyboard so I just resort to turning the computer on and off again. I'm sure this is the same problem as above although somehow the screens back buffer doesn't get cleared.
Which nvidia driver are you using? If you installed one using System-->Administration-->Hardware Drivers, then you're using the proprietary nvidia driver. If you didn't install anything, you're using nouveau (open source driver).

Could you perhaps show the terminal output(Applications-->Accessories-->Terminal) of:
```
cat /var/log/Xorg.0.log
```
When pasting this (huge) log on this forum, make sure to put the text between [noparse]```
   
```[/noparse] tags, as it will be much friendlier on the layout of the page. Thanks.

---

### Post by static_void on 2010-08-23
I don't have any other operating system installed on the computer.

The nvidia driver automatically installed itself a few minutes after I booted the computer for the first time. (It is the proprietary driver)

The computer hasn't shut down so far so I can't tell you if the Alt-SysRq keycodes work or not.

here is the log:

```

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux craig-desktop 2.6.32-24-generic-pae #41-Ubuntu SMP Thu Aug 19 02:43:57 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic-pae root=UUID=429e05fe-cd36-4a4d-810c-b56a3fe10959 ro quiet splash
Build Date: 21 July 2010  12:47:34PM
xorg-server 2:1.7.6-2ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Aug 23 15:08:14 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No device specified for screen "Default Screen".
    Using the first device section listed.
(**) |   |-->Device "Default Device"
(==) No monitor specified for screen "Default Screen".
    Using a default monitor configuration.
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
(II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x81f0e80
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:2:0:0) 10de:0a20:0000:0000 nVidia Corporation GT216 [GeForce GT 220] rev 162, Mem @ 0xfd000000/16777216, 0xd0000000/268435456, 0xce000000/33554432, I/O @ 0x0000ec00/128, BIOS @ 0x????????/524288
(II) Open ACPI successful (/var/run/acpid.socket)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/extra-modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  195.36.24  Thu Apr 22 10:38:29 PDT 2010
(II) Loading extension GLX
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
(II) Primary Device is: PCI 02@00:00:0
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
(II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) Aug 23 15:08:15 NVIDIA(0): Enabling RENDER acceleration
(II) Aug 23 15:08:15 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Aug 23 15:08:15 NVIDIA(0):     enabled.
(II) Aug 23 15:08:16 NVIDIA(0): NVIDIA GPU GeForce GT 220 (GT216) at PCI:2:0:0 (GPU-0)
(--) Aug 23 15:08:16 NVIDIA(0): Memory: 1048576 kBytes
(--) Aug 23 15:08:16 NVIDIA(0): VideoBIOS: 70.16.50.00.00
(II) Aug 23 15:08:16 NVIDIA(0): Detected PCI Express Link width: 16X
(--) Aug 23 15:08:16 NVIDIA(0): Interlaced video modes are supported on this GPU
(--) Aug 23 15:08:16 NVIDIA(0): Connected display device(s) on GeForce GT 220 at PCI:2:0:0:
(--) Aug 23 15:08:16 NVIDIA(0):     Bit 3 LE1940 (CRT-1)
(--) Aug 23 15:08:16 NVIDIA(0): Bit 3 LE1940 (CRT-1): 400.0 MHz maximum pixel clock
(II) Aug 23 15:08:16 NVIDIA(0): Assigned Display Device: CRT-1
(==) Aug 23 15:08:16 NVIDIA(0): 
(==) Aug 23 15:08:16 NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) Aug 23 15:08:16 NVIDIA(0):     will be used as the requested mode.
(==) Aug 23 15:08:16 NVIDIA(0): 
(II) Aug 23 15:08:16 NVIDIA(0): Validated modes:
(II) Aug 23 15:08:16 NVIDIA(0):     "nvidia-auto-select"
(II) Aug 23 15:08:16 NVIDIA(0): Virtual screen size determined to be 1440 x 900
(--) Aug 23 15:08:16 NVIDIA(0): DPI set to (89, 87); computed from "UseEdidDpi" X config
(--) Aug 23 15:08:16 NVIDIA(0):     option
(==) Aug 23 15:08:16 NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) Aug 23 15:08:16 NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
(II) Aug 23 15:08:16 NVIDIA(0): Initialized GPU GART.
(II) Aug 23 15:08:16 NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) Aug 23 15:08:17 NVIDIA(0): Initialized OpenGL Acceleration
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) Aug 23 15:08:17 NVIDIA(0): Initialized X Rendering Acceleration
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
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(II) XKB: reuse xkmfile /var/lib/xkb/server-C1F82522E3F958F13C2D6D2C62551E135092F235.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event5)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/event4)
(**) ImPS/2 Generic Wheel Mouse: Applying InputClass "evdev pointer catchall"
(**) ImPS/2 Generic Wheel Mouse: always reports core events
(**) ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event4"
(II) ImPS/2 Generic Wheel Mouse: Found 3 mouse buttons
(II) ImPS/2 Generic Wheel Mouse: Found scroll wheel(s)
(II) ImPS/2 Generic Wheel Mouse: Found relative axes
(II) ImPS/2 Generic Wheel Mouse: Found x and y relative axes
(II) ImPS/2 Generic Wheel Mouse: Configuring as mouse
(**) ImPS/2 Generic Wheel Mouse: YAxisMapping: buttons 4 and 5
(**) ImPS/2 Generic Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE)
(II) ImPS/2 Generic Wheel Mouse: initialized for relative axes.
(II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/mouse1)
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
(II) Aug 23 15:14:31 NVIDIA(0): Setting mode "1280x800"
(II) Aug 23 16:08:06 NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Aug 23 16:49:45 NVIDIA(0): Setting mode "1280x800"
(II) Aug 23 17:26:47 NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Aug 23 19:38:45 NVIDIA(0): Setting mode "1280x800"
(II) Aug 23 21:01:04 NVIDIA(0): Setting mode "nvidia-auto-select"


```


Thanks for the help.

---

### Post by happyhamster on 2010-08-23
Doesn't look like there's something wrong there, but again, I'm not an nvidia user myself, so don't take my word for it. Other things you could test: disable compiz (System-->Appearance-->Visual Effects-->none), or running the nouveau driver instead of the proprietary one.
And on the hardware side of things, apart from running memtest, you could also take a look at overheating issues (fan's not working, or not making proper contact with whatever they should cool, etc.) Good luck.

---

### Post by static_void on 2010-08-27
I hasn't switched off for a few days now. Ever since I done 'sudo apt-get update' it seems to be working fine.

---

### Post by static_void on 2010-09-06
The computer started to play up again so I installed windows vista and about 5 minutes into it my computer just automatically switched off again. Could this be simply overheating or a more serious problem?
 
(I just recently bought the computer aswell)

---

### Post by happyhamster on 2010-09-08
Apologies for replying late (haven't visited the forums for some time), but yes: if you're having problems with both linux and windows, then it's almost certainly a hardware problem. Again I must ask, have you actually run memtest? It's a small program that will test the computer's memory (the hardware). Run it for several hours: if it finds even 1 error it will mean your RAM is bad (in much rarer cases it indicates a motherboard or even a cpu malfunction).

You're in a tough position, because a hardware problem like this is hard to diagnose without having access to spare parts. If you have spare RAM, power units, fans, etc., you can just swap those and test. If you can't, then in the end your only reliable option is to RMA the entire computer I think. 

Good luck.

---

