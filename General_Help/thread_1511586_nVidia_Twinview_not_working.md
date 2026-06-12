---
title: "nVidia Twinview not working"
date: 2010-06-17
forum: General Help
---

### Post by noremac3000 on 2010-06-17
I have no idea what to do to get Twinview to work. I had found a bit of code to paste into the xorg.conf file but after I pasted it in and restarted my computer, but it wouldn't boot up. Whenever I open up the "Monitors" dialog under System>Preferences, it doesn't even see that the second monitor is there! It doesn't matter if I go to the default tool or if I go to nVidia's tool. On the nVidia tool, under X "Server Display Configuration", there is a button "Configure...", when I press it, it asks "How should this display be configured?". The options "Twinview" and "Disabled" are both unselectable and the only one that I can select is "Separate X Screen". It's almost like my computer doesn't know that I have a second monitor plug.

I am running Ubuntu 10.04.

My xorg.conf:
```

Section "Device" 
    Identifier     "nVidia Corporation NV34 [GeForce FX 5200]" 
    Driver         "nvidia" 
    Option         "NvAGP"     "1"
    Option "AddARGBVisuals" "True"
    Option "AddARGBGLXVisuals" "True"
EndSection

```
[SIZE=1](Isn't this supposed to be longer?)[/SIZE]

I'm kind of a beginner on Ubuntu so please be patient with me ;D

---

### Post by jocko on 2010-06-17
I'm not sure, but if that's all you have in your xorg.conf maybe that's the problem.
Try this:
First back up your current xorg.conf by running this in a terminal:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```Then have nvidia-xconfig generate a new xorg.conf by running this in a terminal:
```
sudo nvidia-xconfig --force-generate
```Then restart x (Alt+SysRq+K) or reboot.
If you by some reason really need those options you had in your original xorg.conf:
```
sudo nvidia-xconfig --force-generate --nvagp=1 --add-argb-glx-visuals
```but I would at least try without the nvagp option first as I think that will be better in most cases.
And if things does not work at all and you want to get back to using your original xorg.conf:
```
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```

If you still can't get twinview working after this, post your /var/log/Xorg.0.log here. It may give some clues.

---

### Post by noremac3000 on 2010-06-17
Ok, I tried generating a new xorg.conf like you said. I have no idea why but it seriously messed it up so I changed it back and tried regenerating it with the second command:```

sudo nvidia-xconfig --force-generate --nvagp=1 --add-argb-glx-visuals

```This time it went back to normal, but the second monitor is STILL not working :confused:.

Xorg.0.log:
```


X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux cameron-computer 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=83b23f4c-fa21-411f-a6e2-32dcc72126b4 ro quiet splash
Build Date: 09 June 2010  10:55:28AM
xorg-server 2:1.7.6-2ubuntu7.1 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Jun 17 01:57:55 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
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
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x81f0e80
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(--) using VT number 7

(--) PCI:*(0:1:0:0) 10de:0172:1043:03b3 nVidia Corporation NV17 [GeForce4 MX 420] rev 163, Mem @ 0xec000000/16777216, 0xe4000000/67108864, 0xe8000000/524288, BIOS @ 0x????????/131072
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
(II) NVIDIA GLX Module  96.43.17  Thu Apr 15 05:52:20 PDT 2010
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
(II) NVIDIA dlloader X Driver  96.43.17  Thu Apr 15 05:35:23 PDT 2010
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NvAGP" "1"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): Use of NVIDIA internal AGP requested
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce4 MX 420 at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 65536 kBytes
(--) NVIDIA(0): VideoBIOS: 04.17.00.44.27
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce4 MX 420 at PCI:1:0:0:
(--) NVIDIA(0):     hp f70 (CRT-0)
(--) NVIDIA(0): hp f70 (CRT-0): 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(WW) NVIDIA(0): No valid modes for "1600x1200"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(--) NVIDIA(0): DPI set to (95, 96); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(--) Depth 24 pixmap format is 32 bpp
(WW) NVIDIA(0): No useable GART found.
(II) NVIDIA(0): Setting mode "1280x1024"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
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
(II) config/udev: Adding input device HID 0461:4d03 (/dev/input/event4)
(**) HID 0461:4d03: Applying InputClass "evdev pointer catchall"
(**) HID 0461:4d03: always reports core events
(**) HID 0461:4d03: Device: "/dev/input/event4"
(II) HID 0461:4d03: Found 3 mouse buttons
(II) HID 0461:4d03: Found scroll wheel(s)
(II) HID 0461:4d03: Found relative axes
(II) HID 0461:4d03: Found x and y relative axes
(II) HID 0461:4d03: Configuring as mouse
(**) HID 0461:4d03: YAxisMapping: buttons 4 and 5
(**) HID 0461:4d03: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "HID 0461:4d03" (type: MOUSE)
(II) HID 0461:4d03: initialized for relative axes.
(II) config/udev: Adding input device HID 0461:4d03 (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
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

### Post by wojox on 2010-06-17
Open it as root and set it up

```
sudo nvidia-xconfig
```

```
gksudo nvidia-settings
```


When you apply it, you will see one big desktop. The panels will stretch the entire length of the monitors. Just reboot and it will fix that. I've done this before. :p

---

### Post by noremac3000 on 2010-06-17
Nope, second monitor still not working. I even tried another monitor, it didn't work either.

---

### Post by wojox on 2010-06-17
Try clicking on the on monitor screen in the nvidia-settings and see if you can move it. The second one maybe hidden behind it.

---

### Post by noremac3000 on 2010-06-17
Nope, it's not dragging around.

---

### Post by wojox on 2010-06-17
It's a little old but may still work [Dual Monitor With nVidia TwinView HowTo]("http://ubuntuforums.org/showthread.php?p=1773584")

---

### Post by noremac3000 on 2010-06-17
That didn't work either...

---

### Post by noremac3000 on 2010-06-19
Anyone else want to help?

---

### Post by skewray on 2010-07-20
I just re-installed lucid on a machine that worked fine with twinview before, and twinview ceased working.  "NVIDIA X Server Settings" from the menu in KDE failed to work, even though there were no errors in the X11 log file.  I tried "sudo nvidia-xconfig" from above and that fixed the problem.

Thanks, wojox!

Brian

---

### Post by zissshh on 2010-07-23
i have a extra monitor connected to the tv tuner and a extra vga cable running form the tuner to the main system where the dvi splitter vga is attached,,,,now when i watch cctv relay from my classroom i have to switch on the monitor and tv tuner,but if i turn off the tv tuner then it mirrors the screen of my pc ,,,i
   i have down loaded nvidia  x server and hardware and  when i detect monitors it doesnt show the other one but displays what ever is going on the main monitor
     now what do i do should i connect the second monitor directly to system with vga dvi splitter so that it recognises the second monitor if i do so will my cctv  work

---

