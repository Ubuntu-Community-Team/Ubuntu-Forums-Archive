---
title: "Unwanted logout - help!!"
date: 2011-01-06
forum: General Help
---

### Post by lloydsmart on 2011-01-06
Hello all, I have a question regarding a rather strange behaviour that my system has recently started showing.

Basically, it's completely logging me off and dumping me back to the login screen (having terminated all my active processes) without me asking it to!

It happens whenever I use two of my favorite and most frequently used programs, which of course is quite annoying, and it didn't start happening when I updated them or anything like that.

The programs in question are [MakeMKV]("http://makemkv.com/") and [tsMuxeR]("http://www.smlabs.net/tsmuxer_en.html"), both of which I use quite a lot. It happens at very specific points, too. In MakeMKV it happens when I try to click a check-box or an expansion-traingle-thingy (like you get for folders in file list views), and in tsMuxeR it happens when I try to open a file.

Can anyone help or at least offer some explanation for this? I'm tempted to think it's something related to the nvidia drivers, but that's just a hunch.

I'm running Maverick 64-bit on an ASUS M3N78 Pro (which means I have an Nvidia GeForce 8300), and an AMD Phenom 2 quad-core. This problem has only started happening in the last few days, so maybe it's related to some system update that's been released recently?

If you think some log file or other would help diagnose this problem I'd be happy to provide them if you tell me where to look.

Thanks in advance for any help you can provide - this is driving me nuts!

---

### Post by lloydsmart on 2011-01-08
*bump*

Tl;dr? Basically I get logged out when I use these two applications. It's very annoying.

Thanks!

---

### Post by lloydsmart on 2011-01-09
Anyone? I hate to bump a thread this much but I really can't fix this problem by myself.

If you need more information I'll be happy to provide it. Where should I start troubleshooting something like this?

---

### Post by lloydsmart on 2011-01-10
*bump*

---

### Post by happyhamster on 2011-01-10
Could you show the output of dmesg after you have had to re-login? Make the automatic logout happen, login again, open a terminal (Applications-->Accessories-->Terminal) and run:
```

dmesg >dmesg.log

```
And then attach dmesg.log here. You can also post the contents of that file, but make sure to put it between [noparse]```
 
```[/noparse] tags (because it's a lot of text).

---

### Post by lloydsmart on 2011-01-10
Thanks for looking at this for me, here is the log.

---

### Post by happyhamster on 2011-01-10
The log did show a few segfaults related to flash. What you can test is: do a clean boot, don't start any other programs (especially firefox/flash) and see if you can trigger the logout using MakeMKV and tsMuxeR. It's possible that the segfaults caused some memory corruption (which can trigger errors in other applications). This is unlikely IMHO, because recent firefox builds shield the flash plugin to prevent errors like these, but it's nice to rule out nevertheless.

Can you also show the output of:
```

uname -a

```
(The exact ubuntu version), and (after having had to re-login):
```

cat /var/log/Xorg.0.log

```
It should show any graphical related errors. 

Also, concerning the tv-card you're using: does it work out-of-the-box, or did you have to compile its driver manually? If the latter, see if recompiling that driver fixes anything (perhaps there were some X or kernel updates that expect an updated tv-card driver).

Good luck.

---

### Post by lloydsmart on 2011-01-10
Hi. I did a clean boot and the problem still happens without launching any other applications first.

Here are the logs you requested:

```
$ uname -a
Linux lloydsmart-desktop 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 02:41:37 UTC 2010 x86_64 GNU/Linux
```

```
$ cat /var/log/Xorg.0.log
[   227.457] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[   227.458] X Protocol Version 11, Revision 0
[   227.458] Build Operating System: Linux 2.6.24-28-server x86_64 Ubuntu
[   227.458] Current Operating System: Linux lloydsmart-desktop 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 02:41:37 UTC 2010 x86_64
[   227.458] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-24-generic root=UUID=630ec411-dcab-4d70-a3bd-403d8b809479 ro quiet splash
[   227.458] Build Date: 23 November 2010  11:54:56PM
[   227.458] xorg-server 2:1.9.0-0ubuntu7.1 (For technical support please see http://www.ubuntu.com/support) 
[   227.458] Current version of pixman: 0.18.4
[   227.458] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[   227.458] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   227.458] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Jan 10 22:09:04 2011
[   227.458] (==) Using config file: "/etc/X11/xorg.conf"
[   227.458] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   227.459] (==) ServerLayout "Layout0"
[   227.459] (**) |-->Screen "Screen0" (0)
[   227.459] (**) |   |-->Monitor "Monitor0"
[   227.459] (**) |   |-->Device "Device0"
[   227.459] (**) |-->Input Device "Keyboard0"
[   227.459] (**) |-->Input Device "Mouse0"
[   227.460] (**) Option "Xinerama" "0"
[   227.460] (==) Automatically adding devices
[   227.460] (==) Automatically enabling devices
[   227.460] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   227.460] 	Entry deleted from font path.
[   227.460] (**) FontPath set to:
	unix/:7100,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[   227.460] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   227.460] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[   227.460] (WW) Disabling Keyboard0
[   227.460] (WW) Disabling Mouse0
[   227.460] (II) Loader magic: 0x7d17a0
[   227.460] (II) Module ABI versions:
[   227.460] 	X.Org ANSI C Emulation: 0.4
[   227.460] 	X.Org Video Driver: 8.0
[   227.460] 	X.Org XInput driver : 11.0
[   227.460] 	X.Org Server Extension : 4.0
[   227.462] (--) PCI: (0:1:11:0) 14f1:8800:0070:6902 rev 5, Mem @ 0xfb000000/16777216
[   227.462] (--) PCI:*(0:2:0:0) 10de:0848:1043:82e2 rev 162, Mem @ 0xf6000000/16777216, 0xe0000000/134217728, 0xee000000/33554432, I/O @ 0x0000bc00/128, BIOS @ 0x????????/131072
[   227.462] (II) Open ACPI successful (/var/run/acpid.socket)
[   227.462] (II) LoadModule: "extmod"
[   227.463] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   227.464] (II) Module extmod: vendor="X.Org Foundation"
[   227.464] 	compiled for 1.9.0, module version = 1.0.0
[   227.464] 	Module class: X.Org Server Extension
[   227.464] 	ABI class: X.Org Server Extension, version 4.0
[   227.464] (II) Loading extension MIT-SCREEN-SAVER
[   227.464] (II) Loading extension XFree86-VidModeExtension
[   227.464] (II) Loading extension XFree86-DGA
[   227.464] (II) Loading extension DPMS
[   227.464] (II) Loading extension XVideo
[   227.464] (II) Loading extension XVideo-MotionCompensation
[   227.464] (II) Loading extension X-Resource
[   227.464] (II) LoadModule: "dbe"
[   227.464] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   227.464] (II) Module dbe: vendor="X.Org Foundation"
[   227.464] 	compiled for 1.9.0, module version = 1.0.0
[   227.464] 	Module class: X.Org Server Extension
[   227.464] 	ABI class: X.Org Server Extension, version 4.0
[   227.464] (II) Loading extension DOUBLE-BUFFER
[   227.464] (II) LoadModule: "glx"
[   227.464] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[   227.476] (II) Module glx: vendor="NVIDIA Corporation"
[   227.476] 	compiled for 4.0.2, module version = 1.0.0
[   227.476] 	Module class: X.Org Server Extension
[   227.476] (II) NVIDIA GLX Module  260.19.06  Mon Sep 13 04:54:41 PDT 2010
[   227.476] (II) Loading extension GLX
[   227.476] (II) LoadModule: "record"
[   227.476] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   227.476] (II) Module record: vendor="X.Org Foundation"
[   227.476] 	compiled for 1.9.0, module version = 1.13.0
[   227.476] 	Module class: X.Org Server Extension
[   227.476] 	ABI class: X.Org Server Extension, version 4.0
[   227.476] (II) Loading extension RECORD
[   227.476] (II) LoadModule: "dri"
[   227.477] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   227.477] (II) Module dri: vendor="X.Org Foundation"
[   227.477] 	compiled for 1.9.0, module version = 1.0.0
[   227.477] 	ABI class: X.Org Server Extension, version 4.0
[   227.477] (II) Loading extension XFree86-DRI
[   227.477] (II) LoadModule: "dri2"
[   227.477] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   227.477] (II) Module dri2: vendor="X.Org Foundation"
[   227.477] 	compiled for 1.9.0, module version = 1.2.0
[   227.477] 	ABI class: X.Org Server Extension, version 4.0
[   227.477] (II) Loading extension DRI2
[   227.477] (II) LoadModule: "nvidia"
[   227.477] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[   227.478] (II) Module nvidia: vendor="NVIDIA Corporation"
[   227.478] 	compiled for 4.0.2, module version = 1.0.0
[   227.478] 	Module class: X.Org Video Driver
[   227.478] (II) NVIDIA dlloader X Driver  260.19.06  Mon Sep 13 04:31:43 PDT 2010
[   227.478] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[   227.478] (--) using VT number 8

[   227.488] (II) Loading sub module "fb"
[   227.488] (II) LoadModule: "fb"
[   227.489] (II) Loading /usr/lib/xorg/modules/libfb.so
[   227.489] (II) Module fb: vendor="X.Org Foundation"
[   227.489] 	compiled for 1.9.0, module version = 1.0.0
[   227.489] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   227.489] (II) Loading sub module "wfb"
[   227.489] (II) LoadModule: "wfb"
[   227.489] (II) Loading /usr/lib/xorg/modules/libwfb.so
[   227.489] (II) Module wfb: vendor="X.Org Foundation"
[   227.489] 	compiled for 1.9.0, module version = 1.0.0
[   227.489] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   227.489] (II) Loading sub module "ramdac"
[   227.489] (II) LoadModule: "ramdac"
[   227.490] (II) Module "ramdac" already built-in
[   227.497] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[   227.497] (==) NVIDIA(0): RGB weight 888
[   227.497] (==) NVIDIA(0): Default visual is TrueColor
[   227.497] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[   227.497] (**) NVIDIA(0): Option "TwinView" "0"
[   227.497] (**) NVIDIA(0): Option "MetaModes" "1920x1080_50 +0+0; nvidia-auto-select +0+0; 1680x1050 +0+0; 1920x1080 +0+0"
[   227.497] (**) NVIDIA(0): Enabling RENDER acceleration
[   227.497] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[   227.497] (II) NVIDIA(0):     enabled.
[   227.550] (II) NVIDIA(0): NVIDIA GPU GeForce 8300 (C77) at PCI:2:0:0 (GPU-0)
[   227.550] (--) NVIDIA(0): Memory: 524288 kBytes
[   227.550] (--) NVIDIA(0): VideoBIOS: 62.77.1e.00.05
[   227.550] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[   227.550] (--) NVIDIA(0): Connected display device(s) on GeForce 8300 at PCI:2:0:0
[   227.550] (--) NVIDIA(0):     ONK TX-SR705 (DFP-0)
[   227.550] (--) NVIDIA(0): ONK TX-SR705 (DFP-0): 165.0 MHz maximum pixel clock
[   227.550] (--) NVIDIA(0): ONK TX-SR705 (DFP-0): Internal Single Link TMDS
[   227.577] (II) NVIDIA(0): Assigned Display Device: DFP-0
[   227.577] (II) NVIDIA(0): Validated modes:
[   227.577] (II) NVIDIA(0):     "1920x1080_50+0+0"
[   227.577] (II) NVIDIA(0):     "nvidia-auto-select+0+0"
[   227.577] (II) NVIDIA(0):     "1680x1050+0+0"
[   227.577] (II) NVIDIA(0):     "1920x1080+0+0"
[   227.577] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[   227.614] (--) NVIDIA(0): DPI set to (304, 304); computed from "UseEdidDpi" X config
[   227.614] (--) NVIDIA(0):     option
[   227.614] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[   227.614] (--) Depth 24 pixmap format is 32 bpp
[   227.614] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[   227.616] (II) NVIDIA(0): Initialized GPU GART.
[   227.621] (II) NVIDIA(0): Setting mode "1920x1080_50+0+0"
[   227.757] (II) Loading extension NV-GLX
[   227.782] (II) NVIDIA(0): Initialized OpenGL Acceleration
[   227.792] (==) NVIDIA(0): Disabling shared memory pixmaps
[   227.792] (II) NVIDIA(0): Initialized X Rendering Acceleration
[   227.792] (==) NVIDIA(0): Backing store disabled
[   227.792] (==) NVIDIA(0): Silken mouse enabled
[   227.796] (**) NVIDIA(0): DPMS enabled
[   227.796] (II) Loading extension NV-CONTROL
[   227.796] (II) Loading extension XINERAMA
[   227.796] (II) Loading sub module "dri2"
[   227.796] (II) LoadModule: "dri2"
[   227.797] (II) Reloading /usr/lib/xorg/modules/extensions/libdri2.so
[   227.797] (II) NVIDIA(0): [DRI2] Setup complete
[   227.797] (==) RandR enabled
[   227.797] (II) Initializing built-in extension Generic Event Extension
[   227.797] (II) Initializing built-in extension SHAPE
[   227.797] (II) Initializing built-in extension MIT-SHM
[   227.797] (II) Initializing built-in extension XInputExtension
[   227.797] (II) Initializing built-in extension XTEST
[   227.797] (II) Initializing built-in extension BIG-REQUESTS
[   227.797] (II) Initializing built-in extension SYNC
[   227.797] (II) Initializing built-in extension XKEYBOARD
[   227.797] (II) Initializing built-in extension XC-MISC
[   227.797] (II) Initializing built-in extension SECURITY
[   227.797] (II) Initializing built-in extension XINERAMA
[   227.797] (II) Initializing built-in extension XFIXES
[   227.797] (II) Initializing built-in extension RENDER
[   227.797] (II) Initializing built-in extension RANDR
[   227.797] (II) Initializing built-in extension COMPOSITE
[   227.797] (II) Initializing built-in extension DAMAGE
[   227.797] (II) Initializing built-in extension GESTURE
[   227.799] (II) Initializing extension GLX
[   227.839] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   227.850] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[   227.850] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   227.850] (II) LoadModule: "evdev"
[   227.850] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   227.850] (II) Module evdev: vendor="X.Org Foundation"
[   227.850] 	compiled for 1.9.0, module version = 2.3.2
[   227.850] 	Module class: X.Org XInput Driver
[   227.850] 	ABI class: X.Org XInput driver, version 11.0
[   227.850] (**) Power Button: always reports core events
[   227.850] (**) Power Button: Device: "/dev/input/event1"
[   227.901] (II) Power Button: Found keys
[   227.901] (II) Power Button: Configuring as keyboard
[   227.901] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[   227.901] (**) Option "xkb_rules" "evdev"
[   227.901] (**) Option "xkb_model" "pc104"
[   227.901] (**) Option "xkb_layout" "us"
[   227.901] (**) Option "xkb_options" "grp:shift_caps_toggle"
[   227.905] (II) XKB: reuse xkmfile /var/lib/xkb/server-BE8ED50818B9CF35E1DE74AA972921E22E28A52B.xkm
[   227.911] (II) config/udev: Adding input device Video Bus (/dev/input/event7)
[   227.911] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[   227.911] (**) Video Bus: always reports core events
[   227.911] (**) Video Bus: Device: "/dev/input/event7"
[   228.011] (II) Video Bus: Found keys
[   228.011] (II) Video Bus: Configuring as keyboard
[   228.011] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[   228.011] (**) Option "xkb_rules" "evdev"
[   228.011] (**) Option "xkb_model" "pc104"
[   228.011] (**) Option "xkb_layout" "us"
[   228.011] (**) Option "xkb_options" "grp:shift_caps_toggle"
[   228.013] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[   228.013] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   228.014] (**) Power Button: always reports core events
[   228.014] (**) Power Button: Device: "/dev/input/event0"
[   228.091] (II) Power Button: Found keys
[   228.091] (II) Power Button: Configuring as keyboard
[   228.091] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[   228.091] (**) Option "xkb_rules" "evdev"
[   228.091] (**) Option "xkb_model" "pc104"
[   228.091] (**) Option "xkb_layout" "us"
[   228.091] (**) Option "xkb_options" "grp:shift_caps_toggle"
[   228.093] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event3)
[   228.093] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[   228.093] (**) Logitech USB Receiver: always reports core events
[   228.093] (**) Logitech USB Receiver: Device: "/dev/input/event3"
[   228.171] (II) Logitech USB Receiver: Found 20 mouse buttons
[   228.171] (II) Logitech USB Receiver: Found scroll wheel(s)
[   228.171] (II) Logitech USB Receiver: Found relative axes
[   228.171] (II) Logitech USB Receiver: Found x and y relative axes
[   228.171] (II) Logitech USB Receiver: Configuring as mouse
[   228.171] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[   228.171] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   228.171] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: MOUSE)
[   228.171] (II) Logitech USB Receiver: initialized for relative axes.
[   228.172] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse0)
[   228.172] (II) No input driver/identifier specified (ignoring)
[   228.173] (II) config/udev: Adding input device iMON Remote (15c2:0036) (/dev/input/event6)
[   228.173] (**) iMON Remote (15c2:0036): Applying InputClass "evdev pointer catchall"
[   228.173] (**) iMON Remote (15c2:0036): Applying InputClass "evdev keyboard catchall"
[   228.173] (**) iMON Remote (15c2:0036): always reports core events
[   228.173] (**) iMON Remote (15c2:0036): Device: "/dev/input/event6"
[   228.251] (II) iMON Remote (15c2:0036): Found 3 mouse buttons
[   228.251] (II) iMON Remote (15c2:0036): Found scroll wheel(s)
[   228.251] (II) iMON Remote (15c2:0036): Found relative axes
[   228.251] (II) iMON Remote (15c2:0036): Found x and y relative axes
[   228.251] (II) iMON Remote (15c2:0036): Found keys
[   228.251] (II) iMON Remote (15c2:0036): Configuring as mouse
[   228.251] (II) iMON Remote (15c2:0036): Configuring as keyboard
[   228.251] (**) iMON Remote (15c2:0036): YAxisMapping: buttons 4 and 5
[   228.251] (**) iMON Remote (15c2:0036): EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   228.251] (II) XINPUT: Adding extended input device "iMON Remote (15c2:0036)" (type: KEYBOARD)
[   228.251] (**) Option "xkb_rules" "evdev"
[   228.251] (**) Option "xkb_model" "pc104"
[   228.251] (**) Option "xkb_layout" "us"
[   228.251] (**) Option "xkb_options" "grp:shift_caps_toggle"
[   228.252] (II) iMON Remote (15c2:0036): initialized for relative axes.
[   228.253] (II) config/udev: Adding input device iMON Remote (15c2:0036) (/dev/input/mouse2)
[   228.253] (II) No input driver/identifier specified (ignoring)
[   228.258] (II) config/udev: Adding input device USB-compliant keyboard (/dev/input/event4)
[   228.258] (**) USB-compliant keyboard: Applying InputClass "evdev keyboard catchall"
[   228.258] (**) USB-compliant keyboard: always reports core events
[   228.258] (**) USB-compliant keyboard: Device: "/dev/input/event4"
[   228.331] (II) USB-compliant keyboard: Found keys
[   228.331] (II) USB-compliant keyboard: Configuring as keyboard
[   228.331] (II) XINPUT: Adding extended input device "USB-compliant keyboard" (type: KEYBOARD)
[   228.331] (**) Option "xkb_rules" "evdev"
[   228.331] (**) Option "xkb_model" "pc104"
[   228.331] (**) Option "xkb_layout" "us"
[   228.331] (**) Option "xkb_options" "grp:shift_caps_toggle"
[   228.332] (II) config/udev: Adding input device USB-compliant keyboard (/dev/input/event5)
[   228.332] (**) USB-compliant keyboard: Applying InputClass "evdev keyboard catchall"
[   228.333] (**) USB-compliant keyboard: always reports core events
[   228.333] (**) USB-compliant keyboard: Device: "/dev/input/event5"
[   228.411] (II) USB-compliant keyboard: Found 1 mouse buttons
[   228.411] (II) USB-compliant keyboard: Found scroll wheel(s)
[   228.411] (II) USB-compliant keyboard: Found relative axes
[   228.411] (II) USB-compliant keyboard: Found x and y relative axes
[   228.411] (II) USB-compliant keyboard: Found absolute axes
[   228.411] (II) evdev-grail: failed to open grail, no gesture support
[   228.411] (II) USB-compliant keyboard: Found keys
[   228.411] (II) USB-compliant keyboard: Configuring as mouse
[   228.411] (II) USB-compliant keyboard: Configuring as keyboard
[   228.411] (**) USB-compliant keyboard: YAxisMapping: buttons 4 and 5
[   228.411] (**) USB-compliant keyboard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   228.412] (II) XINPUT: Adding extended input device "USB-compliant keyboard" (type: KEYBOARD)
[   228.412] (**) Option "xkb_rules" "evdev"
[   228.412] (**) Option "xkb_model" "pc104"
[   228.412] (**) Option "xkb_layout" "us"
[   228.412] (**) Option "xkb_options" "grp:shift_caps_toggle"
[   228.412] (II) USB-compliant keyboard: initialized for relative axes.
[   228.412] (WW) USB-compliant keyboard: ignoring absolute axes.
[   228.413] (II) config/udev: Adding input device USB-compliant keyboard (/dev/input/mouse1)
[   228.413] (II) No input driver/identifier specified (ignoring)
[   228.418] (II) config/udev: Adding input device cx88 IR (Hauppauge WinTV-HVR400 (/dev/input/event8)
[   228.418] (**) cx88 IR (Hauppauge WinTV-HVR400: Applying InputClass "evdev keyboard catchall"
[   228.418] (**) cx88 IR (Hauppauge WinTV-HVR400: always reports core events
[   228.418] (**) cx88 IR (Hauppauge WinTV-HVR400: Device: "/dev/input/event8"
[   228.491] (II) cx88 IR (Hauppauge WinTV-HVR400: Found keys
[   228.491] (II) cx88 IR (Hauppauge WinTV-HVR400: Configuring as keyboard
[   228.491] (II) XINPUT: Adding extended input device "cx88 IR (Hauppauge WinTV-HVR400" (type: KEYBOARD)
[   228.491] (**) Option "xkb_rules" "evdev"
[   228.491] (**) Option "xkb_model" "pc104"
[   228.491] (**) Option "xkb_layout" "us"
[   228.491] (**) Option "xkb_options" "grp:shift_caps_toggle"
[   228.501] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[   228.501] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[   228.501] (**) AT Translated Set 2 keyboard: always reports core events
[   228.501] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[   228.572] (II) AT Translated Set 2 keyboard: Found keys
[   228.572] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[   228.572] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[   228.572] (**) Option "xkb_rules" "evdev"
[   228.572] (**) Option "xkb_model" "pc104"
[   228.572] (**) Option "xkb_layout" "us"
[   228.572] (**) Option "xkb_options" "grp:shift_caps_toggle"
[   235.182] (II) NVIDIA(0): Setting mode "1920x1080_50+0+0"
```

As for the tv card, it just worked out of the box. I haven't compiled any special drivers for it.

Thanks for your help!

---

### Post by happyhamster on 2011-01-10
Looks clean. Just to make sure: these logs are from *after* having forced a logout and logging in again? Can you also post the output of:
```

cat /var/log/syslog

```
It will show if any daemons/services are misbehaving.

And one other thing to try: when logged in, or at the login screen, press ctrl-alt-F3, this will drop you into a console. Login, and run:
```

sudo service gdm stop

```
This will stop gdm (the logon service amongst other things). Then run:
```

startx

```
This will start the graphical interface, but without gdm running. See if you can reproduce the logoff in that case (it's possible that you will get dumped into the console instead, and that error messages will show. Make a note in that case. Also, if you want to reboot from a console, run:
```

sudo reboot

```
Or, to restart gdm:
```

sudo service gdm start

```

Good luck.

---

### Post by lloydsmart on 2011-01-15
Hello. Just to confirm, yes, these logs were taken *after* the unexpected logout.

I've attached the output of "cat /var/log/syslog" both before and after the logout:

I tried stopping the gdm as you suggested, and reproduced the problem in the GUI. The exact same thing happened, except that this time, I got dumped back to the console instead of the login screen. I was also presented with the following error messages at the console:

```
Segmentation fault at address (nil)

Please consult the X.Org Foundation support at http://wiki.x.org for help.

Please also check the log file at "/var/log/Xorg.0.log" for additional information.

ddxSigGiveUp: Closing log
xinit: connection to X server lost.

waiting for X server to shut down
```

I checked the Xorg.0.log file again as it instructed. I've attached its contents.

Any more ideas? I'm completely stumped!

Thanks.

---

### Post by lloydsmart on 2011-01-16
Just noticed that the problem also happens when I launch "Oracle VM Virtualbox". I don't even have to click anything in that application, just launch it. Two seconds after the interface/wizard appears on the screen, I get logged out!

---

### Post by lloydsmart on 2011-01-16
Just noticed something. When I get logged out, the nvidia splash screen comes up for a second. Nothing unusual about that, except that it has "Beta version" written on it in red letters. Maybe that's the issue here? I've somehow ended up with beta nvidia drivers? If so, can anyone give me advice on how to remove them, and "downgrade" to the latest stable drivers?

Thanks!

---

### Post by JGJones on 2011-01-16
My first thought is that it's a problem with the graphics.

Regarding your NVidia drivers - did you add any extra repos for graphics such as the X Update (which come with a more up to date drivers)

Also can you go to Additional Drivers in the System menu (in the "Control Panel" area in main menu).

It should list all available drivers on your system.

If memory serve me correctly, it would list two drivers if using X Updates (version 185) - the updated version and the one provided by Ubuntu (Version 173).

Try switching to the Ubuntu provided driver.

If just the one listed - disable it (it'll fall back onto the open source nvidia driver instead with no 3D functions) and reboot. Then try your software.

If it works, then you can try reinstalling the driver again - if it fails and you don't have X Updates - I suggest adding this software source for a more updated driver

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

Hope that helps - please ask if any question to clear up if I'm not clear above.

---

### Post by lloydsmart on 2011-01-22
Well, I removed the nvidia driver, restarted, and it wouldn't even start the GUI at all. Just dumped me to a console. I assumed it would default to the nv driver (I even tried setting it to this in xorg.conf), but it didn't work. Running startx didn't work either.

I decided to give up on this and reformat. The installation is completely borked and it's not worth the effort when I can just reinstall ubuntu fresh.

Thanks for all your help anyway though guys - I *do* appreciate it.

:)

---

### Post by JGJones on 2011-01-24
Even so, sorry that you had to reformat - it's not the ideal answer but if it's a fresh installation with no loss of data fair enough.

---

