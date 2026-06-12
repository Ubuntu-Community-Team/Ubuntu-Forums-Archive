---
title: "Update killed xorg,Nvidia"
date: 2010-07-27
forum: General Help
---

### Post by Dark Horse on 2010-07-27
I just did an update through update manager and it killed Xorg here is the boot log file :

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux ubuntustudio1 2.6.32-24-preempt #38-Ubuntu SMP PREEMPT Mon Jul 5 11:38:11 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-preempt root=UUID=5d286a64-8de2-4677-84d2-f157a801217b ro quiet splash
Build Date: 16 June 2010  09:34:29AM
xorg-server 2:1.7.6-2ubuntu7.2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.16.4
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.4.log", Time: Tue Jul 27 15:42:27 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "Layout0"
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
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(--) using VT number 8

(--) PCI:*(0:0:13:0) 10de:03d0:1458:d000 nVidia Corporation C61 [GeForce 6150SE nForce 430] rev 162, Mem @ 0xfb000000/16777216, 0xd0000000/268435456, 0xfc000000/16777216, BIOS @ 0x????????/131072
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
(II) NVIDIA GLX Module  195.36.24  Thu Apr 22 19:52:00 PDT 2010
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
(EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
(EE) NVIDIA:     system's kernel log for additional error messages.
(II) UnloadModule: "nvidia"
(II) Unloading /usr/lib/xorg/extra-modules/nvidia_drv.so
(EE) Failed to load module "nvidia" (module-specific error, 0)
(EE) No drivers available.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.4.log" for additional information.

 ddxSigGiveUp: Closing log




[COLOR="Blue"]Here is a copy of a boot log from before the update that does work:
[/COLOR]
X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux ubuntustudio1 2.6.32-23-preempt #37-Ubuntu SMP PREEMPT Fri Jun 11 10:19:07 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-23-preempt root=UUID=5d286a64-8de2-4677-84d2-f157a801217b ro quiet splash
Build Date: 16 June 2010  09:34:29AM
xorg-server 2:1.7.6-2ubuntu7.2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.16.4
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Jul 27 16:00:02 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "Layout0"
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
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:0:13:0) 10de:03d0:1458:d000 nVidia Corporation C61 [GeForce 6150SE nForce 430] rev 162, Mem @ 0xfb000000/16777216, 0xd0000000/268435456, 0xfc000000/16777216, BIOS @ 0x????????/131072
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
(II) NVIDIA GLX Module  195.36.24  Thu Apr 22 19:52:00 PDT 2010
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
(II) NVIDIA dlloader X Driver  195.36.24  Thu Apr 22 19:18:54 PDT 2010
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 00@00:0d:0
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
(**) NVIDIA(0): Option "MetaModes" "1600x1200 +0+0; nvidia-auto-select +0+0"
(**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "CRT-0"
(**) Jul 27 16:00:02 NVIDIA(0): Enabling RENDER acceleration
(II) Jul 27 16:00:02 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Jul 27 16:00:02 NVIDIA(0):     enabled.
(WW) Jul 27 16:00:03 NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
(II) Jul 27 16:00:03 NVIDIA(0): NVIDIA GPU GeForce 6150SE nForce 430 (C61) at PCI:0:13:0
(II) Jul 27 16:00:03 NVIDIA(0):     (GPU-0)
(--) Jul 27 16:00:03 NVIDIA(0): Memory: 262144 kBytes
(--) Jul 27 16:00:03 NVIDIA(0): VideoBIOS: 05.61.32.19.04
(--) Jul 27 16:00:03 NVIDIA(0): Interlaced video modes are supported on this GPU
(--) Jul 27 16:00:03 NVIDIA(0): Connected display device(s) on GeForce 6150SE nForce 430 at
(--) Jul 27 16:00:03 NVIDIA(0):     PCI:0:13:0:
(--) Jul 27 16:00:03 NVIDIA(0):     CRT-0
(--) Jul 27 16:00:03 NVIDIA(0): CRT-0: 350.0 MHz maximum pixel clock
(II) Jul 27 16:00:03 NVIDIA(0): Assigned Display Device: CRT-0
(II) Jul 27 16:00:03 NVIDIA(0): Validated modes:
(II) Jul 27 16:00:03 NVIDIA(0):     "1600x1200+0+0"
(II) Jul 27 16:00:03 NVIDIA(0):     "nvidia-auto-select+0+0"
(II) Jul 27 16:00:03 NVIDIA(0): Virtual screen size determined to be 1600 x 1200
(WW) Jul 27 16:00:03 NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
(WW) Jul 27 16:00:03 NVIDIA(0):     from CRT-0's EDID.
(==) Jul 27 16:00:03 NVIDIA(0): DPI set to (75, 75); computed from built-in default
(==) Jul 27 16:00:03 NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) Jul 27 16:00:03 NVIDIA(0): Initialized GPU GART.
(II) Jul 27 16:00:03 NVIDIA(0): Setting mode "1600x1200+0+0"
(II) Loading extension NV-GLX
(II) Jul 27 16:00:03 NVIDIA(0): Initialized OpenGL Acceleration
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) Jul 27 16:00:03 NVIDIA(0): Initialized X Rendering Acceleration
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
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
(II) config/udev: Adding input device Ideazon Zboard (/dev/input/event4)
(**) Ideazon Zboard: Applying InputClass "evdev keyboard catchall"
(**) Ideazon Zboard: always reports core events
(**) Ideazon Zboard: Device: "/dev/input/event4"
(II) Ideazon Zboard: Found keys
(II) Ideazon Zboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Ideazon Zboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) config/udev: Adding input device Microsoft Microsoft Trackball Optical® (/dev/input/event3)
(**) Microsoft Microsoft Trackball Optical®: Applying InputClass "evdev pointer catchall"
(**) Microsoft Microsoft Trackball Optical®: always reports core events
(**) Microsoft Microsoft Trackball Optical®: Device: "/dev/input/event3"
(II) Microsoft Microsoft Trackball Optical®: Found 9 mouse buttons
(II) Microsoft Microsoft Trackball Optical®: Found scroll wheel(s)
(II) Microsoft Microsoft Trackball Optical®: Found relative axes
(II) Microsoft Microsoft Trackball Optical®: Found x and y relative axes
(II) Microsoft Microsoft Trackball Optical®: Configuring as mouse
(**) Microsoft Microsoft Trackball Optical®: YAxisMapping: buttons 4 and 5
(**) Microsoft Microsoft Trackball Optical®: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Microsoft Microsoft Trackball Optical®" (type: MOUSE)
(II) Microsoft Microsoft Trackball Optical®: initialized for relative axes.
(II) config/udev: Adding input device Microsoft Microsoft Trackball Optical® (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event5)
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


I don't know if this qualifies as a bug but it is a problem when an update breaks the system I have reverted to the earlier install for now 
but if it is happening to me it is probably happening to others I haven't the fainest idea what the real problem is.
If you need othere info let me know what & where to look for it and I will try to post it
Mark

---

### Post by linux18 on 2010-07-27
not really a fix, but a temporary workaround to get you into your desktop environment: 

these steps will boot any non-bricked ubuntu:

STEP 1:
-choose recovery mode at grub

STEP 2:
-drop to a root prompt

STEP 3:
-type: 
```

telinit 3

```
 and login

STEP 4:
-then type:
```

 xinit

```

STEP 5:
-when xinit starts type:
```

metacity &

```
- for ubuntu OR:
```

compiz &

```
- if you have it OR flux/openbox & - if you have it OR:
```

fvwm4 & 

```
- for xubuntu

STEP 6:
-then type:
```

 gnome panel & 

```
-for ubuntu OR:
```

 xfce4-panel & 

```
-for xubuntu

STEP 7:
-lastly type:
```
 
nm-applet & 

```
-for networking

---

### Post by Dark Horse on 2010-09-01
Thanks for the reply I have tried your suggestion several times i can not make it work I am still using the earlier version preempt 2.6.32-23 Instead of the newest preempt2.6.32-24. It dies with the following errors:

(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
compiled for 4.0.2, module version = 1.0.0
Module class: X.Org Video Driver
(EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
(EE) NVIDIA: system's kernel log for additional error messages.
(II) UnloadModule: "nvidia"
(II) Unloading /usr/lib/xorg/extra-modules/nvidia_drv.so
(EE) Failed to load module "nvidia" (module-specific error, 0)
(EE) No drivers available.

Fatal server error:
no screens found
 it appears to not be loading the nvidia kernel module where do I look to fix this?? or at least find out why?
Mark :confused:  :rolleyes::rolleyes:

---

### Post by R3N3GAD3 on 2010-09-09
This happens to me every time there is an update to the xserver. I use the most recent nvidia development drivers for OpenCL/Cuda, and instead of going through the process describe above, I simply reinstall the driver, which is a very easy task, and remains in my download directory.

When the X crash screen comes up after you have rebooted sometime in the future after an update (I rarely ever restart my box, so I always get an annoying surprise when I reboot and forgot there was an update): 

(1) type "ctrl+alt+f1"

(2) login 

(3) /etc/init.d/gdm stop

(4) cd /home/userName/Downloads

(5)* sudo sh nvidiaDriverFileName.bin

*Make sure to restore xorg configuration wehn it prompts

I have tried numerous other efforts to restore my xorg configuration after this constant annoyance, but they failed so I stick to this simple method.

If someone has a better method, I would really love to hear it. I don't have time for fixing this kind of s**t. I'll get at it some day soon, but for now, I only update when it is completely necessary.

---

### Post by Dark Horse on 2010-09-29
> **R3N3GAD3 said:**
> This happens to me every time there is an update to the xserver. I use the most recent nvidia development drivers for OpenCL/Cuda, and instead of going through the process describe above, I simply reinstall the driver, which is a very easy task, and remains in my download directory.

When the X crash screen comes up after you have rebooted sometime in the future after an update (I rarely ever restart my box, so I always get an annoying surprise when I reboot and forgot there was an update): 

(1) type "ctrl+alt+f1"

(2) login 

(3) /etc/init.d/gdm stop

(4) cd /home/userName/Downloads

(5)* sudo sh nvidiaDriverFileName.bin

*Make sure to restore xorg configuration wehn it prompts

I have tried numerous other efforts to restore my xorg configuration after this constant annoyance, but they failed so I stick to this simple method.

If someone has a better method, I would really love to hear it. I don't have time for fixing this kind of s**t. I'll get at it some day soon, but for now, I only update when it is completely necessary.

Thanks for your answer it did not work either My original nvidia was installed through synaptic so I down loaded the version from Nvidia's site But so far I have not been able to get it to work for me. Tonight the update manager downloaded 2.6.32-25-preempt and still xorg is dead apparently there is no nvidia in the new kernel? it leaves me at a command line log on but I have not been able to get xorg to work. I am still looking for an answer that works mean while I am still using 2.6.32-23-preempt. until I find a better answer.

Mark :)

---

### Post by rbm0307 on 2010-10-13
Have you found a fix for this situation.  I'm in exactly the same position for exactly the same reason -- upgrade from 8.04 to 10.04.  

Original X11 Error message:
```
X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux mythbe 2.6.32-25-server #44-Ubuntu SMP Fri Sep 17 21:13:39 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-25-server root=UUID=a571e0e4-8835-4a1f-9845-11d58fdc687c ro quiet splash
Build Date: 21 July 2010  01:03:39PM
xorg-server 2:1.7.6-2ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Oct  8 20:30:58 2010
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
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
        X.Org ANSI C Emulation: 0.4
        X.Org Video Driver: 6.0
        X.Org XInput driver : 7.0
        X.Org Server Extension : 2.0
(--) using VT number 7

(--) PCI:*(0:3:0:0) 10de:01d1:1682:2208 nVidia Corporation G72 [GeForce 7300 LE] rev 161, Mem @ 0xfa000000/16777216, 0xe0000000/268435456, 0xfb000000/16777216, BIOS @ 0x????????/131072
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
(II) NVIDIA GLX Module  195.36.24  Thu Apr 22 19:52:00 PDT 2010
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
(EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
(EE) NVIDIA:     system's kernel log for additional error messages.
(II) UnloadModule: "nvidia"
(II) Unloading /usr/lib/xorg/extra-modules/nvidia_drv.so
(EE) Failed to load module "nvidia" (module-specific error, 0)
(EE) No drivers available.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
         at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
```

I've purged all Nvidia drivers using apt-get and reinstalled.  So, the nvidia software purge results:
```
root@mythbe:/var/log# sudo apt-get --purge remove nvidia-glx* nvidia-kernel-common nvidia-settings
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting nvidia-glx-96-dev for regex 'nvidia-glx*'
Note, selecting nvidia-glx-dev for regex 'nvidia-glx*'
Note, selecting nvidia-glx-ia32 for regex 'nvidia-glx*'
Note, selecting nvidia-glx-new for regex 'nvidia-glx*'
Note, selecting nvidia-glx-173-dev for regex 'nvidia-glx*'
Note, selecting nvidia-glx-src for regex 'nvidia-glx*'
Note, selecting nvidia-glx-185-dev for regex 'nvidia-glx*'
Note, selecting nvidia-glx-173 for regex 'nvidia-glx*'
Note, selecting nvidia-glx-180 for regex 'nvidia-glx*'
Note, selecting nvidia-glx-185 for regex 'nvidia-glx*'
Note, selecting nvidia-glx-legacy for regex 'nvidia-glx*'
Note, selecting nvidia-glx-96 for regex 'nvidia-glx*'
Note, selecting nvidia-glx for regex 'nvidia-glx*'
Note, selecting nvidia-glx-180-dev for regex 'nvidia-glx*'
The following packages will be REMOVED:
  linux-restricted-modules-2.6.24-19-generic* linux-restricted-modules-2.6.24-21-generic* linux-restricted-modules-2.6.24-22-generic*
  linux-restricted-modules-2.6.24-23-generic* linux-restricted-modules-2.6.24-24-generic* linux-restricted-modules-2.6.24-25-generic*
  linux-restricted-modules-2.6.24-26-generic* linux-restricted-modules-2.6.24-27-generic* nvidia-glx-173* nvidia-glx-180* nvidia-glx-185* nvidia-glx-96*
  nvidia-kernel-common* nvidia-settings*
0 upgraded, 0 newly installed, 14 to remove and 8 not upgraded.
After this operation, 449MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 313134 files and directories currently installed.)
Removing linux-restricted-modules-2.6.24-19-generic ...
Purging configuration files for linux-restricted-modules-2.6.24-19-generic ...
Removing linux-restricted-modules-2.6.24-21-generic ...
Purging configuration files for linux-restricted-modules-2.6.24-21-generic ...
Removing linux-restricted-modules-2.6.24-22-generic ...
Purging configuration files for linux-restricted-modules-2.6.24-22-generic ...
Removing linux-restricted-modules-2.6.24-23-generic ...
Purging configuration files for linux-restricted-modules-2.6.24-23-generic ...
Removing linux-restricted-modules-2.6.24-24-generic ...
Purging configuration files for linux-restricted-modules-2.6.24-24-generic ...
Removing linux-restricted-modules-2.6.24-25-generic ...
Purging configuration files for linux-restricted-modules-2.6.24-25-generic ...
Removing linux-restricted-modules-2.6.24-26-generic ...
Purging configuration files for linux-restricted-modules-2.6.24-26-generic ...
Removing linux-restricted-modules-2.6.24-27-generic ...
Purging configuration files for linux-restricted-modules-2.6.24-27-generic ...
Removing nvidia-glx-173 ...
Removing nvidia-glx-180 ...
Removing nvidia-glx-185 ...
Removing nvidia-glx-96 ...
Removing nvidia-kernel-common ...
Purging configuration files for nvidia-kernel-common ...
Removing nvidia-settings ...
Processing triggers for readahead-fedora ...
Processing triggers for man-db ...
root@mythbe:/var/log# 
root@mythbe:/var/log# sudo update-rc.d nvidia-kernel remove
 Removing any system startup links for /etc/init.d/nvidia-kernel ...
root@mythbe:/var/log#
```

And the Nvidia driver reload:
```
root@mythbe:/var/log# apt-get install nvidia-glx-185 nvidia-kernel-common nvidia-settings 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  nvidia-glx-185 nvidia-kernel-common nvidia-settings
0 upgraded, 3 newly installed, 0 to remove and 8 not upgraded.
Need to get 5,526B/851kB of archives.
After this operation, 2,109kB of additional disk space will be used.
Get:1 http://ca.archive.ubuntu.com/ubuntu/ lucid/restricted nvidia-kernel-common 20080825+1ubuntu2 [5,526B]
Fetched 5,526B in 0s (13.3kB/s)               
Selecting previously deselected package nvidia-glx-185.
(Reading database ... 311547 files and directories currently installed.)
Unpacking nvidia-glx-185 (from .../nvidia-glx-185_195.36.24-0ubuntu1~10.04_amd64.deb) ...
Selecting previously deselected package nvidia-kernel-common.
Unpacking nvidia-kernel-common (from .../nvidia-kernel-common_20080825+1ubuntu2_all.deb) ...
Selecting previously deselected package nvidia-settings.
Unpacking nvidia-settings (from .../nvidia-settings_195.36.08-0ubuntu2_amd64.deb) ...
Processing triggers for readahead-fedora ...
Processing triggers for man-db ...
Setting up nvidia-glx-185 (195.36.24-0ubuntu1~10.04) ...
Setting up nvidia-kernel-common (20080825+1ubuntu2) ...
update-rc.d: warning: nvidia-kernel stop runlevel arguments (1) do not match LSB Default-Stop values (none)

Setting up nvidia-settings (195.36.08-0ubuntu2) ...


```

Prior to all this I tried reinstalling GDM and X11 to make sure that they hadn't been clobbered by the update:
```
apt-get --reinstall install x11-xserver-utils gnome-core  
apt-get install gdm
dpkg-reconfigure gdm
depmod

```

Still no joy.  I want to avoid a complete reinstall of Ubuntu 10.04 if possible.  TIA.

---

### Post by Dark Horse on 2010-11-30
Sorry so far I have not found a fix that works I am still booting 2.6.32-23 
the latest update from the update manager Down loaded and installed about 10 minuets ago still does not boot xorg or Nvidia.
Here is my log file from the most recent attempt to update the kernal to
2.6.32-26

 
X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux ubuntustudio1 2.6.32-26-preempt #48-Ubuntu SMP PREEMPT Wed Nov 24 10:43:13 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-26-preempt root=UUID=5d286a64-8de2-4677-84d2-f157a801217b ro quiet splash
Build Date: 10 November 2010  11:25:53AM
xorg-server 2:1.7.6-2ubuntu7.4 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.16.4
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.5.log", Time: Tue Nov 30 10:02:57 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "Layout0"
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
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(--) using VT number 8

(--) PCI:*(0:0:13:0) 10de:03d0:1458:d000 nVidia Corporation C61 [GeForce 6150SE nForce 430] rev 162, Mem @ 0xfb000000/16777216, 0xd0000000/268435456, 0xfc000000/16777216, BIOS @ 0x????????/131072
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
(II) NVIDIA GLX Module  195.36.24  Thu Apr 22 19:52:00 PDT 2010
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
(EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
(EE) NVIDIA:     system's kernel log for additional error messages.
(II) UnloadModule: "nvidia"
(II) Unloading /usr/lib/xorg/extra-modules/nvidia_drv.so
(EE) Failed to load module "nvidia" (module-specific error, 0)
(EE) No drivers available.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.5.log" for additional information.

 ddxSigGiveUp: Closing log


I hope somebody can find an answer that works none of the suggested solutions have worked for me.

also if it matters my install was a clean install and not an upgrade from an earlier version. If there is some other info that would help solve this problem let me know where to look for it and I will try to get it posted.
Mark

---

### Post by rbm0307 on 2010-12-01
> **Dark Horse said:**
> I hope somebody can find an answer that works none of the suggested solutions have worked for me.

Mark

My Xorg prblems stemmed from the lrm-video script using the incorrect modprobe options for Nvidia, bug #482549.  I followed the advice in this web page, [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/482549]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/482549"), which cured my Xorg startup problems.  Maybe it will work for you as well (if you haven't already tried).

---

### Post by Dark Horse on 2010-12-01
> My Xorg prblems stemmed from the lrm-video script using the incorrect modprobe options for Nvidia, bug #482549. I followed the advice in this web page, [https://bugs.launchpad.net/ubuntu/+s...es/+bug/482549](https://bugs.launchpad.net/ubuntu/+s...es/+bug/482549), which cured my Xorg startup problems. Maybe it will work for you as well (if you haven't already tried). 

I checked that post and he appears to be modifying a file that doesn't seem to exist on my computer but thanks for the suggestion at least it was a new Idea.
Mark 

PPS. his error message is a little different than mine
Mark

---

