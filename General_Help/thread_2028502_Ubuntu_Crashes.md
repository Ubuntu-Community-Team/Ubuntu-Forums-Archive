---
title: "Ubuntu Crashes"
date: 2012-07-18
forum: General Help
---

### Post by hunter.allen on 2012-07-18
For some reason, Ubuntu 12.04 (running with GNome desktop) decides to log me out while I am working. As a programmer, this is quite frustrating. Anything you can do to help me prevent losing any more work? Just let me know what logs you need to see. 

thanks in advance, 
-Hunter a.

---

### Post by matt_symes on 2012-07-18
Hi

If it is taking you back out to the login screen then it sounds like X is crashing.

Have a look in /var/log/ for the X.org.* log files.

If the last time it happened is your current session and you have not rebooted then post the output of (double check to see if it contains information about a crash)...

```
cat /var/log/Xorg.0.log.old
```

If not look through those logs and post back the ones containing information about the crash.

If you cannot find a log that contains crash info then post this information back to.

Kind regards

---

### Post by sgage on 2012-07-18
Are you running Ubuntu One? It has caused that exact symptom for me - bang, right to the login window. I don't use it, so I disabled it and have not had any problems since.

---

### Post by hunter.allen on 2012-07-18
```
allenh1@muri-pc7:~$ cat /var/log/Xorg.0.log.old
[433488.129] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[433488.129] X Protocol Version 11, Revision 0
[433488.129] Build Operating System: Linux 2.6.42-26-generic i686 Ubuntu
[433488.129] Current Operating System: Linux muri-pc7 3.2.0-27-generic-pae #43-Ubuntu SMP Fri Jul 6 15:06:05 UTC 2012 i686
[433488.129] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-27-generic-pae root=UUID=1d851126-0583-476a-840a-cff38607708e ro quiet splash vt.handoff=7
[433488.130] Build Date: 16 July 2012  08:06:34PM
[433488.130] xorg-server 2:1.11.4-0ubuntu10.6 (For technical support please see http://www.ubuntu.com/support) 
[433488.130] Current version of pixman: 0.24.4
[433488.130] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[433488.130] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[433488.130] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Jul 17 15:26:00 2012
[433488.130] (==) Using config file: "/etc/X11/xorg.conf"
[433488.130] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[433488.131] (==) ServerLayout "Layout0"
[433488.131] (**) |-->Screen "Screen0" (0)
[433488.131] (**) |   |-->Monitor "Monitor0"
[433488.131] (**) |   |-->Device "Device0"
[433488.131] (**) |-->Input Device "Keyboard0"
[433488.131] (**) |-->Input Device "Mouse0"
[433488.131] (**) Option "Xinerama" "0"
[433488.131] (==) Automatically adding devices
[433488.131] (==) Automatically enabling devices
[433488.131] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[433488.131] 	Entry deleted from font path.
[433488.131] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[433488.131] 	Entry deleted from font path.
[433488.131] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[433488.131] 	Entry deleted from font path.
[433488.131] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[433488.131] 	Entry deleted from font path.
[433488.131] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[433488.131] 	Entry deleted from font path.
[433488.131] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[433488.131] 	Entry deleted from font path.
[433488.131] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[433488.132] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[433488.132] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[433488.132] (WW) Disabling Keyboard0
[433488.132] (WW) Disabling Mouse0
[433488.132] (II) Loader magic: 0xb77685a0
[433488.132] (II) Module ABI versions:
[433488.132] 	X.Org ANSI C Emulation: 0.4
[433488.132] 	X.Org Video Driver: 11.0
[433488.132] 	X.Org XInput driver : 16.0
[433488.132] 	X.Org Server Extension : 6.0
[433488.133] (--) PCI:*(0:1:0:0) 10de:0607:10de:0736 rev 162, Mem @ 0xfa000000/16777216, 0xd0000000/268435456, 0xf8000000/33554432, I/O @ 0x0000ec00/128, BIOS @ 0x????????/131072
[433488.133] (II) Open ACPI successful (/var/run/acpid.socket)
[433488.133] (II) LoadModule: "extmod"
[433488.133] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[433488.134] (II) Module extmod: vendor="X.Org Foundation"
[433488.134] 	compiled for 1.11.3, module version = 1.0.0
[433488.134] 	Module class: X.Org Server Extension
[433488.134] 	ABI class: X.Org Server Extension, version 6.0
[433488.134] (II) Loading extension MIT-SCREEN-SAVER
[433488.134] (II) Loading extension XFree86-VidModeExtension
[433488.134] (II) Loading extension XFree86-DGA
[433488.134] (II) Loading extension DPMS
[433488.134] (II) Loading extension XVideo
[433488.134] (II) Loading extension XVideo-MotionCompensation
[433488.134] (II) Loading extension X-Resource
[433488.134] (II) LoadModule: "dbe"
[433488.134] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[433488.134] (II) Module dbe: vendor="X.Org Foundation"
[433488.134] 	compiled for 1.11.3, module version = 1.0.0
[433488.134] 	Module class: X.Org Server Extension
[433488.134] 	ABI class: X.Org Server Extension, version 6.0
[433488.134] (II) Loading extension DOUBLE-BUFFER
[433488.134] (II) LoadModule: "glx"
[433488.134] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/libglx.so
[433488.155] (II) Module glx: vendor="NVIDIA Corporation"
[433488.155] 	compiled for 4.0.2, module version = 1.0.0
[433488.155] 	Module class: X.Org Server Extension
[433488.155] (II) NVIDIA GLX Module  295.40  Thu Apr  5 21:49:54 PDT 2012
[433488.155] (II) Loading extension GLX
[433488.155] (II) LoadModule: "record"
[433488.156] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[433488.156] (II) Module record: vendor="X.Org Foundation"
[433488.156] 	compiled for 1.11.3, module version = 1.13.0
[433488.156] 	Module class: X.Org Server Extension
[433488.156] 	ABI class: X.Org Server Extension, version 6.0
[433488.156] (II) Loading extension RECORD
[433488.156] (II) LoadModule: "dri"
[433488.156] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[433488.156] (II) Module dri: vendor="X.Org Foundation"
[433488.156] 	compiled for 1.11.3, module version = 1.0.0
[433488.156] 	ABI class: X.Org Server Extension, version 6.0
[433488.156] (II) Loading extension XFree86-DRI
[433488.156] (II) LoadModule: "dri2"
[433488.156] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[433488.156] (II) Module dri2: vendor="X.Org Foundation"
[433488.156] 	compiled for 1.11.3, module version = 1.2.0
[433488.156] 	ABI class: X.Org Server Extension, version 6.0
[433488.156] (II) Loading extension DRI2
[433488.156] (II) LoadModule: "nvidia"
[433488.156] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[433488.156] (II) Module nvidia: vendor="NVIDIA Corporation"
[433488.156] 	compiled for 4.0.2, module version = 1.0.0
[433488.156] 	Module class: X.Org Video Driver
[433488.157] (II) NVIDIA dlloader X Driver  295.40  Thu Apr  5 21:29:50 PDT 2012
[433488.157] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[433488.157] (++) using VT number 7

[433488.157] (II) Loading sub module "fb"
[433488.157] (II) LoadModule: "fb"
[433488.157] (II) Loading /usr/lib/xorg/modules/libfb.so
[433488.157] (II) Module fb: vendor="X.Org Foundation"
[433488.157] 	compiled for 1.11.3, module version = 1.0.0
[433488.157] 	ABI class: X.Org ANSI C Emulation, version 0.4
[433488.157] (II) Loading sub module "wfb"
[433488.157] (II) LoadModule: "wfb"
[433488.157] (II) Loading /usr/lib/xorg/modules/libwfb.so
[433488.157] (II) Module wfb: vendor="X.Org Foundation"
[433488.157] 	compiled for 1.11.3, module version = 1.0.0
[433488.157] 	ABI class: X.Org ANSI C Emulation, version 0.4
[433488.157] (II) Loading sub module "ramdac"
[433488.157] (II) LoadModule: "ramdac"
[433488.157] (II) Module "ramdac" already built-in
[433488.157] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[433488.157] (II) Loading /usr/lib/xorg/modules/libwfb.so
[433488.157] (II) Loading /usr/lib/xorg/modules/libfb.so
[433488.157] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[433488.157] (==) NVIDIA(0): RGB weight 888
[433488.157] (==) NVIDIA(0): Default visual is TrueColor
[433488.157] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[433488.157] (**) NVIDIA(0): Option "TwinView" "0"
[433488.157] (**) NVIDIA(0): Option "MetaModes" "1920x1080_60_0 +0+0; nvidia-auto-select +0+0"
[433488.157] (**) NVIDIA(0): Enabling 2D acceleration
[433488.277] (II) NVIDIA(GPU-0): Display (DELL E2211H (DFP-0)) does not support NVIDIA 3D
[433488.278] (II) NVIDIA(GPU-0):     Vision stereo.
[433488.281] (II) NVIDIA(0): NVIDIA GPU GeForce GTS 240 (G92) at PCI:1:0:0 (GPU-0)
[433488.281] (--) NVIDIA(0): Memory: 1048576 kBytes
[433488.281] (--) NVIDIA(0): VideoBIOS: 62.92.93.00.08
[433488.281] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[433488.281] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[433488.291] (--) NVIDIA(0): Connected display device(s) on GeForce GTS 240 at PCI:1:0:0
[433488.291] (--) NVIDIA(0):     DELL E2211H (DFP-0)
[433488.291] (--) NVIDIA(0): DELL E2211H (DFP-0): 330.0 MHz maximum pixel clock
[433488.291] (--) NVIDIA(0): DELL E2211H (DFP-0): Internal Dual Link TMDS
[433488.408] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[433488.408] (**) NVIDIA(0):     device DELL E2211H (DFP-0) (Using EDID frequencies has
[433488.408] (**) NVIDIA(0):     been enabled on all display devices.)
[433488.447] (II) NVIDIA(0): Assigned Display Device: DFP-0
[433488.447] (II) NVIDIA(0): Validated modes:
[433488.447] (II) NVIDIA(0):     "1920x1080_60_0+0+0"
[433488.447] (II) NVIDIA(0):     "nvidia-auto-select+0+0"
[433488.447] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[433488.459] (--) NVIDIA(0): DPI set to (101, 101); computed from "UseEdidDpi" X config
[433488.459] (--) NVIDIA(0):     option
[433488.459] (--) Depth 24 pixmap format is 32 bpp
[433488.459] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[433488.472] (II) NVIDIA(0): Setting mode "1920x1080_60_0+0+0"
[433488.508] (II) Loading extension NV-GLX
[433488.556] (==) NVIDIA(0): Disabling shared memory pixmaps
[433488.556] (==) NVIDIA(0): Backing store disabled
[433488.556] (==) NVIDIA(0): Silken mouse enabled
[433488.556] (**) NVIDIA(0): DPMS enabled
[433488.556] (II) Loading extension NV-CONTROL
[433488.556] (II) Loading extension XINERAMA
[433488.556] (II) Loading sub module "dri2"
[433488.556] (II) LoadModule: "dri2"
[433488.556] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[433488.556] (II) Module dri2: vendor="X.Org Foundation"
[433488.556] 	compiled for 1.11.3, module version = 1.2.0
[433488.556] 	ABI class: X.Org Server Extension, version 6.0
[433488.556] (II) NVIDIA(0): [DRI2] Setup complete
[433488.556] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[433488.556] (==) RandR enabled
[433488.556] (II) Initializing built-in extension Generic Event Extension
[433488.556] (II) Initializing built-in extension SHAPE
[433488.556] (II) Initializing built-in extension MIT-SHM
[433488.556] (II) Initializing built-in extension XInputExtension
[433488.556] (II) Initializing built-in extension XTEST
[433488.556] (II) Initializing built-in extension BIG-REQUESTS
[433488.556] (II) Initializing built-in extension SYNC
[433488.556] (II) Initializing built-in extension XKEYBOARD
[433488.556] (II) Initializing built-in extension XC-MISC
[433488.556] (II) Initializing built-in extension SECURITY
[433488.556] (II) Initializing built-in extension XINERAMA
[433488.556] (II) Initializing built-in extension XFIXES
[433488.556] (II) Initializing built-in extension RENDER
[433488.556] (II) Initializing built-in extension RANDR
[433488.557] (II) Initializing built-in extension COMPOSITE
[433488.557] (II) Initializing built-in extension DAMAGE
[433488.558] (II) Initializing extension GLX
[433488.576] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[433488.578] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[433488.578] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[433488.578] (II) LoadModule: "evdev"
[433488.578] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[433488.578] (II) Module evdev: vendor="X.Org Foundation"
[433488.578] 	compiled for 1.11.3, module version = 2.7.0
[433488.578] 	Module class: X.Org XInput Driver
[433488.578] 	ABI class: X.Org XInput driver, version 16.0
[433488.578] (II) Using input driver 'evdev' for 'Power Button'
[433488.578] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[433488.578] (**) Power Button: always reports core events
[433488.578] (**) evdev: Power Button: Device: "/dev/input/event1"
[433488.578] (--) evdev: Power Button: Vendor 0 Product 0x1
[433488.578] (--) evdev: Power Button: Found keys
[433488.578] (II) evdev: Power Button: Configuring as keyboard
[433488.578] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[433488.578] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[433488.578] (**) Option "xkb_rules" "evdev"
[433488.578] (**) Option "xkb_model" "pc105"
[433488.578] (**) Option "xkb_layout" "us"
[433488.579] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[433488.579] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[433488.579] (II) Using input driver 'evdev' for 'Power Button'
[433488.579] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[433488.579] (**) Power Button: always reports core events
[433488.579] (**) evdev: Power Button: Device: "/dev/input/event0"
[433488.579] (--) evdev: Power Button: Vendor 0 Product 0x1
[433488.579] (--) evdev: Power Button: Found keys
[433488.579] (II) evdev: Power Button: Configuring as keyboard
[433488.579] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[433488.579] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[433488.579] (**) Option "xkb_rules" "evdev"
[433488.579] (**) Option "xkb_model" "pc105"
[433488.579] (**) Option "xkb_layout" "us"
[433488.579] (II) config/udev: Adding input device HDA Intel Line (/dev/input/event4)
[433488.579] (II) No input driver specified, ignoring this device.
[433488.579] (II) This device may have been added with another device file.
[433488.579] (II) config/udev: Adding input device HDA Intel Front Mic (/dev/input/event5)
[433488.580] (II) No input driver specified, ignoring this device.
[433488.580] (II) This device may have been added with another device file.
[433488.580] (II) config/udev: Adding input device HDA Intel Rear Mic (/dev/input/event6)
[433488.580] (II) No input driver specified, ignoring this device.
[433488.580] (II) This device may have been added with another device file.
[433488.580] (II) config/udev: Adding input device HDA Intel Front Headphone (/dev/input/event7)
[433488.580] (II) No input driver specified, ignoring this device.
[433488.580] (II) This device may have been added with another device file.
[433488.580] (II) config/udev: Adding input device HDA Intel Line-Out (/dev/input/event8)
[433488.580] (II) No input driver specified, ignoring this device.
[433488.580] (II) This device may have been added with another device file.
[433488.580] (II) config/udev: Adding input device Dell Dell QuietKey Keyboard (/dev/input/event2)
[433488.580] (**) Dell Dell QuietKey Keyboard: Applying InputClass "evdev keyboard catchall"
[433488.580] (II) Using input driver 'evdev' for 'Dell Dell QuietKey Keyboard'
[433488.580] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[433488.580] (**) Dell Dell QuietKey Keyboard: always reports core events
[433488.580] (**) evdev: Dell Dell QuietKey Keyboard: Device: "/dev/input/event2"
[433488.580] (--) evdev: Dell Dell QuietKey Keyboard: Vendor 0x413c Product 0x2106
[433488.580] (--) evdev: Dell Dell QuietKey Keyboard: Found keys
[433488.580] (II) evdev: Dell Dell QuietKey Keyboard: Configuring as keyboard
[433488.580] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.0/input/input2/event2"
[433488.580] (II) XINPUT: Adding extended input device "Dell Dell QuietKey Keyboard" (type: KEYBOARD, id 8)
[433488.580] (**) Option "xkb_rules" "evdev"
[433488.580] (**) Option "xkb_model" "pc105"
[433488.580] (**) Option "xkb_layout" "us"
[433488.581] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/event3)
[433488.581] (**) USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[433488.581] (II) Using input driver 'evdev' for 'USB Optical Mouse'
[433488.581] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[433488.581] (**) USB Optical Mouse: always reports core events
[433488.581] (**) evdev: USB Optical Mouse: Device: "/dev/input/event3"
[433488.581] (--) evdev: USB Optical Mouse: Vendor 0x461 Product 0x4d22
[433488.581] (--) evdev: USB Optical Mouse: Found 3 mouse buttons
[433488.581] (--) evdev: USB Optical Mouse: Found scroll wheel(s)
[433488.581] (--) evdev: USB Optical Mouse: Found relative axes
[433488.581] (--) evdev: USB Optical Mouse: Found x and y relative axes
[433488.581] (II) evdev: USB Optical Mouse: Configuring as mouse
[433488.581] (II) evdev: USB Optical Mouse: Adding scrollwheel support
[433488.581] (**) evdev: USB Optical Mouse: YAxisMapping: buttons 4 and 5
[433488.581] (**) evdev: USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[433488.581] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.0/input/input3/event3"
[433488.581] (II) XINPUT: Adding extended input device "USB Optical Mouse" (type: MOUSE, id 9)
[433488.581] (II) evdev: USB Optical Mouse: initialized for relative axes.
[433488.581] (**) USB Optical Mouse: (accel) keeping acceleration scheme 1
[433488.581] (**) USB Optical Mouse: (accel) acceleration profile 0
[433488.581] (**) USB Optical Mouse: (accel) acceleration factor: 2.000
[433488.581] (**) USB Optical Mouse: (accel) acceleration threshold: 4
[433488.581] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/mouse0)
[433488.581] (II) No input driver specified, ignoring this device.
[433488.581] (II) This device may have been added with another device file.
[433488.924] (II) NVIDIA(0): Setting mode "nvidia-auto-select+0+0"
[433553.000] 
Backtrace:
[433553.000] 0: /usr/bin/X (xorg_backtrace+0x37) [0xb76fb607]
[433553.000] 1: /usr/bin/X (0xb7573000+0x18c38a) [0xb76ff38a]
[433553.000] 2: (vdso) (__kernel_rt_sigreturn+0x0) [0xb755040c]
[433553.000] 3: /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so (0xb47ca000+0xd472a) [0xb489e72a]
[433553.000] Segmentation fault at address 0xb4f4f000
[433553.000] 
Caught signal 11 (Segmentation fault). Server aborting
[433553.000] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[433553.000] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[433553.000] 
[433553.001] (II) evdev: Power Button: Close
[433553.002] (II) UnloadModule: "evdev"
[433553.002] (II) Unloading evdev
[433553.002] (II) evdev: Power Button: Close
[433553.002] (II) UnloadModule: "evdev"
[433553.002] (II) Unloading evdev
[433553.012] (II) evdev: Dell Dell QuietKey Keyboard: Close
[433553.012] (II) UnloadModule: "evdev"
[433553.012] (II) Unloading evdev
[433553.016] (II) evdev: USB Optical Mouse: Close
[433553.017] (II) UnloadModule: "evdev"
[433553.017] (II) Unloading evdev

```

I definitely see a seg fault there... Any fix? Also, I do have UbuntuOne insalled; however, I use it... Any way to fix it so I can use it still?

Edit: 
So it's an NVIDIA problem. How fix?

---

### Post by Killminusnine on 2012-07-18
I'm getting the same thing here. I tried to force one older version of xserver-xorg-input-evdev (from 2.7.0-ubuntu1 to 2.7.0-ubuntu1.2) since it seemed to be related to this package, and only started some time ago (so may have been update related). No luck; the first day after this I had more stability, and now it seems to segfault constantly again. This usually seems to happen when I'm typing in some text field (often in chrome, but I believe that's incidental).

Using a lenovo laptop here, with intel graphics driver if that's helpful at all.

---

### Post by matt_symes on 2012-07-18
Hi

> So it's an NVIDIA problem. How fix?I'ts the nvidia driver that went bang and is causing X to crash dropping you back to LightDM login screen.

You're not the only person with this problem in 12.04 (search on launchpad) and i believe there was a problem with the nvidia drivers.

Boot into Unity2D (fallback). Does it still crash ?

Is there any reason why you have to use the nvidia drivers ? 

Are the nvidia drivers at the most up to date version ?

Kind regards

---

### Post by hunter.allen on 2012-07-18
I don't necessarily need it. How do I remove it without destroying my x-server?

---

### Post by matt_symes on 2012-07-19
Hi

> **hunter.allen said:**
> I don't necessarily need it. How do I remove it without destroying my x-server?

You should be able to to it from the "additional drivers" dialog. Type "additional drivers" into the dash and deactivate the nvidia driver.

You can also do it from the command line using jockey-text.

To list the drivers...

```
jockey-text -l
```and to disable them

```
jockey-text -d <driver_name>
```I use ATI cards but i think yours should be something like...

```
jockey-text -d xorg:nvidia_current
```Check the driver name using the command above though to be sure.

Reeboot after doing this to be sure.

Kind regards

---

### Post by markbl on 2012-07-19
You are probably experiencing [bug 972096](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/973096) like a heap of us. It is a bug in all nvidia drivers since about v295.33 and still occurs in the latest v304.22. Try the nouveau driver, it works well for me.

---

### Post by ashegray on 2012-08-05
I have a lenovo t420, 3000 HD graphics card, and am running into the same problem where I receive a systems error message every single time I login. The details read /usr/bin/xorg, internal error.  

also, I'm a complete neophyte when it comes to ubuntu or any coding business whatsoever, so if anyone could provide some assistance, I would be extremely grateful.

I attached my log ( don't know how to insert a textbox here so it isn't rendered in an incomprehensible mess here)

---

