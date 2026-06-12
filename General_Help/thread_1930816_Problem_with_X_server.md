---
title: "Problem with X server"
date: 2012-02-24
forum: General Help
---

### Post by inconnu259 on 2012-02-24
Hello!
 I don't know what I'm doing, but now when I launch a program (such as digikam, cmake, meshlab, antidote and perhaps others), the X server stops and restarts.

The Xorg.0.log.old :

```
[  5482.383] (II) XKB: reuse xkmfile /var/lib/xkb/server-0CF70113BD0CF0830F6D9334ADBCCCCFD25B9871.xkm [  6513.045]  Backtrace: [  6513.045] 0: /usr/bin/X (xorg_backtrace+0x26) [0x460566] [  6513.045] 1: /usr/bin/X (0x400000+0x64b7a) [0x464b7a] [  6513.045] 2: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7fb2161db000+0x10060) [0x7fb2161eb060] [  6513.045] 3: /usr/lib/libXfont.so.1 (FontFileListNextFontWithInfo+0x29) [0x7fb215d37c89] [  6513.045] 4: /usr/bin/X (doListFontsWithInfo+0x16d) [0x43061d] [  6513.045] 5: /usr/bin/X (ProcessWorkQueue+0x21) [0x433d51] [  6513.045] 6: /usr/bin/X (WaitForSomething+0x65) [0x45dec5] [  6513.045] 7: /usr/bin/X (0x400000+0x2f912) [0x42f912] [  6513.045] 8: /usr/bin/X (0x400000+0x232fe) [0x4232fe] [  6513.045] 9: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xed) [0x7fb21511730d] [  6513.045] 10: /usr/bin/X (0x400000+0x235ed) [0x4235ed] [  6513.045] Segmentation fault at address (nil) [  6513.045]  Caught signal 11 (Segmentation fault). Server aborting [  6513.045]  Please consult the The X.Org Foundation support       at http://wiki.x.org  for help.  [  6513.045] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
                      


```   And the error output of a program (here it's meshlab)



```
meshlab: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
```If anybody have an idea. I think there are a mistake in library like libc but I'm not sure and I don't know how I can fix it.

Edit : I have a 64 bits.
NVIDIA quadro FX 2700 M
the last official driver 295.20

---

### Post by roelforg on 2012-02-24
Try installing nvidia-common

Also, please post the entire Xorg.0.log.old after a crash and try to fix the enters (it's really hard to read this way)

---

### Post by inconnu259 on 2012-02-24
I've already nvidia-common

Xorg.0.log.old :

```

[  3127.967] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[  3127.967] X Protocol Version 11, Revision 0
[  3127.967] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[  3127.967] Current Operating System: Linux inconnu259-laptop 3.0.0-16-generic #29-Ubuntu SMP Tue Feb 14 12:48:51 UTC 2012 x86_64
[  3127.967] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-16-generic root=UUID=7a807624-5c0d-4dff-8509-7182df0f7add ro quiet splash vt.handoff=7
[  3127.967] Build Date: 19 October 2011  05:21:26AM
[  3127.967] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see http://www.ubuntu.com/support) 
[  3127.967] Current version of pixman: 0.22.2
[  3127.967]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[  3127.967] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  3127.967] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Feb 24 09:57:28 2012
[  3127.967] (==) Using config file: "/etc/X11/xorg.conf"
[  3127.967] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  3127.967] (==) ServerLayout "Layout0"
[  3127.967] (**) |-->Screen "Screen0" (0)
[  3127.967] (**) |   |-->Monitor "Monitor0"
[  3127.968] (**) |   |-->Device "Device0"
[  3127.968] (**) |-->Input Device "Keyboard0"
[  3127.968] (**) |-->Input Device "Mouse0"
[  3127.968] (==) Automatically adding devices
[  3127.968] (==) Automatically enabling devices
[  3127.968] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  3127.968]     Entry deleted from font path.
[  3127.968] (**) FontPath set to:
    unix/:7100,
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[  3127.968] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  3127.968] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[  3127.968] (WW) Disabling Keyboard0
[  3127.968] (WW) Disabling Mouse0
[  3127.968] (II) Loader magic: 0x7e0220
[  3127.968] (II) Module ABI versions:
[  3127.968]     X.Org ANSI C Emulation: 0.4
[  3127.968]     X.Org Video Driver: 10.0
[  3127.968]     X.Org XInput driver : 12.3
[  3127.968]     X.Org Server Extension : 5.0
[  3127.969] (--) PCI:*(0:1:0:0) 10de:063a:103c:30ec rev 161, Mem @ 0xd2000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x00007000/128
[  3127.969] (II) Open ACPI successful (/var/run/acpid.socket)
[  3127.969] (II) LoadModule: "extmod"
[  3127.970] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[  3127.970] (II) Module extmod: vendor="X.Org Foundation"
[  3127.970]     compiled for 1.10.4, module version = 1.0.0
[  3127.970]     Module class: X.Org Server Extension
[  3127.970]     ABI class: X.Org Server Extension, version 5.0
[  3127.970] (II) Loading extension MIT-SCREEN-SAVER
[  3127.970] (II) Loading extension XFree86-VidModeExtension
[  3127.970] (II) Loading extension XFree86-DGA
[  3127.970] (II) Loading extension DPMS
[  3127.970] (II) Loading extension XVideo
[  3127.970] (II) Loading extension XVideo-MotionCompensation
[  3127.970] (II) Loading extension X-Resource
[  3127.970] (II) LoadModule: "dbe"
[  3127.971] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[  3127.971] (II) Module dbe: vendor="X.Org Foundation"
[  3127.971]     compiled for 1.10.4, module version = 1.0.0
[  3127.971]     Module class: X.Org Server Extension
[  3127.971]     ABI class: X.Org Server Extension, version 5.0
[  3127.971] (II) Loading extension DOUBLE-BUFFER
[  3127.971] (II) LoadModule: "glx"
[  3127.971] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[  3127.990] (II) Module glx: vendor="NVIDIA Corporation"
[  3127.990]     compiled for 4.0.2, module version = 1.0.0
[  3127.990]     Module class: X.Org Server Extension
[  3127.991] (II) NVIDIA GLX Module  295.20  Mon Feb  6 21:28:16 PST 2012
[  3127.991] (II) Loading extension GLX
[  3127.991] (II) LoadModule: "record"
[  3127.991] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[  3127.991] (II) Module record: vendor="X.Org Foundation"
[  3127.991]     compiled for 1.10.4, module version = 1.13.0
[  3127.991]     Module class: X.Org Server Extension
[  3127.991]     ABI class: X.Org Server Extension, version 5.0
[  3127.991] (II) Loading extension RECORD
[  3127.991] (II) LoadModule: "dri"
[  3127.991] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[  3127.992] (II) Module dri: vendor="X.Org Foundation"
[  3127.992]     compiled for 1.10.4, module version = 1.0.0
[  3127.992]     ABI class: X.Org Server Extension, version 5.0
[  3127.992] (II) Loading extension XFree86-DRI
[  3127.992] (II) LoadModule: "dri2"
[  3127.992] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[  3127.992] (II) Module dri2: vendor="X.Org Foundation"
[  3127.992]     compiled for 1.10.4, module version = 1.2.0
[  3127.992]     ABI class: X.Org Server Extension, version 5.0
[  3127.992] (II) Loading extension DRI2
[  3127.992] (II) LoadModule: "nvidia"
[  3127.992] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[  3127.993] (II) Module nvidia: vendor="NVIDIA Corporation"
[  3127.993]     compiled for 4.0.2, module version = 1.0.0
[  3127.993]     Module class: X.Org Video Driver
[  3127.993] (II) NVIDIA dlloader X Driver  295.20  Mon Feb  6 21:09:10 PST 2012
[  3127.993] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[  3127.993] (++) using VT number 7

[  3127.994] (II) Loading sub module "fb"
[  3127.994] (II) LoadModule: "fb"
[  3127.994] (II) Loading /usr/lib/xorg/modules/libfb.so
[  3127.994] (II) Module fb: vendor="X.Org Foundation"
[  3127.994]     compiled for 1.10.4, module version = 1.0.0
[  3127.994]     ABI class: X.Org ANSI C Emulation, version 0.4
[  3127.994] (II) Loading sub module "wfb"
[  3127.994] (II) LoadModule: "wfb"
[  3127.994] (II) Loading /usr/lib/xorg/modules/libwfb.so
[  3127.994] (II) Module wfb: vendor="X.Org Foundation"
[  3127.994]     compiled for 1.10.4, module version = 1.0.0
[  3127.994]     ABI class: X.Org ANSI C Emulation, version 0.4
[  3127.994] (II) Loading sub module "ramdac"
[  3127.995] (II) LoadModule: "ramdac"
[  3127.995] (II) Module "ramdac" already built-in
[  3127.995] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[  3127.995] (II) Loading /usr/lib/xorg/modules/libwfb.so
[  3127.995] (II) Loading /usr/lib/xorg/modules/libfb.so
[  3127.995] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[  3127.995] (==) NVIDIA(0): RGB weight 888
[  3127.995] (==) NVIDIA(0): Default visual is TrueColor
[  3127.995] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[  3127.995] (**) NVIDIA(0): Enabling 2D acceleration
[  3128.001] (II) NVIDIA(GPU-0): Display (Seiko/Epson (DFP-0)) does not support NVIDIA 3D
[  3128.001] (II) NVIDIA(GPU-0):     Vision stereo.
[  3128.004] (II) NVIDIA(0): NVIDIA GPU Quadro FX 2700M (G94GL) at PCI:1:0:0 (GPU-0)
[  3128.004] (--) NVIDIA(0): Memory: 524288 kBytes
[  3128.004] (--) NVIDIA(0): VideoBIOS: 62.94.42.00.05
[  3128.004] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[  3128.004] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[  3128.004] (--) NVIDIA(0): Connected display device(s) on Quadro FX 2700M at PCI:1:0:0
[  3128.004] (--) NVIDIA(0):     Seiko/Epson (DFP-0)
[  3128.004] (--) NVIDIA(0): Seiko/Epson (DFP-0): 330.0 MHz maximum pixel clock
[  3128.004] (--) NVIDIA(0): Seiko/Epson (DFP-0): Internal Dual Link LVDS
[  3128.007] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[  3128.007] (**) NVIDIA(0):     device Seiko/Epson (DFP-0) (Using EDID frequencies has
[  3128.007] (**) NVIDIA(0):     been enabled on all display devices.)
[  3128.132] (II) NVIDIA(0): Assigned Display Device: DFP-0
[  3128.132] (==) NVIDIA(0): 
[  3128.132] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[  3128.132] (==) NVIDIA(0):     will be used as the requested mode.
[  3128.132] (==) NVIDIA(0): 
[  3128.132] (II) NVIDIA(0): Validated modes:
[  3128.132] (II) NVIDIA(0):     "nvidia-auto-select"
[  3128.132] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1200
[  3129.210] (--) NVIDIA(0): DPI set to (131, 132); computed from "UseEdidDpi" X config
[  3129.210] (--) NVIDIA(0):     option
[  3129.210] (WW) NVIDIA(0): UBB is incompatible with the Composite extension.  Disabling
[  3129.210] (WW) NVIDIA(0):     UBB.
[  3129.210] (--) Depth 24 pixmap format is 32 bpp
[  3129.210] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[  3129.220] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[  3129.527] (II) Loading extension NV-GLX
[  3129.581] (==) NVIDIA(0): Disabling shared memory pixmaps
[  3129.581] (==) NVIDIA(0): Backing store disabled
[  3129.581] (==) NVIDIA(0): Silken mouse enabled
[  3129.582] (**) NVIDIA(0): DPMS enabled
[  3129.582] (II) Loading extension NV-CONTROL
[  3129.582] (II) Loading extension XINERAMA
[  3129.582] (II) Loading sub module "dri2"
[  3129.582] (II) LoadModule: "dri2"
[  3129.583] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[  3129.583] (II) Module dri2: vendor="X.Org Foundation"
[  3129.583]     compiled for 1.10.4, module version = 1.2.0
[  3129.583]     ABI class: X.Org Server Extension, version 5.0
[  3129.583] (II) NVIDIA(0): [DRI2] Setup complete
[  3129.583] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[  3129.583] (==) RandR enabled
[  3129.583] (II) Initializing built-in extension Generic Event Extension
[  3129.583] (II) Initializing built-in extension SHAPE
[  3129.583] (II) Initializing built-in extension MIT-SHM
[  3129.583] (II) Initializing built-in extension XInputExtension
[  3129.583] (II) Initializing built-in extension XTEST
[  3129.583] (II) Initializing built-in extension BIG-REQUESTS
[  3129.583] (II) Initializing built-in extension SYNC
[  3129.583] (II) Initializing built-in extension XKEYBOARD
[  3129.583] (II) Initializing built-in extension XC-MISC
[  3129.583] (II) Initializing built-in extension SECURITY
[  3129.583] (II) Initializing built-in extension XINERAMA
[  3129.583] (II) Initializing built-in extension XFIXES
[  3129.583] (II) Initializing built-in extension RENDER
[  3129.583] (II) Initializing built-in extension RANDR
[  3129.583] (II) Initializing built-in extension COMPOSITE
[  3129.583] (II) Initializing built-in extension DAMAGE
[  3129.583] (II) Initializing built-in extension GESTURE
[  3129.585] (II) Initializing extension GLX
[  3129.616] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  3129.627] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[  3129.627] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  3129.627] (II) LoadModule: "evdev"
[  3129.627] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  3129.628] (II) Module evdev: vendor="X.Org Foundation"
[  3129.628]     compiled for 1.10.2, module version = 2.6.0
[  3129.628]     Module class: X.Org XInput Driver
[  3129.628]     ABI class: X.Org XInput driver, version 12.3
[  3129.628] (II) Using input driver 'evdev' for 'Power Button'
[  3129.628] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  3129.628] (**) Power Button: always reports core events
[  3129.628] (**) Power Button: Device: "/dev/input/event2"
[  3129.628] (--) Power Button: Found keys
[  3129.628] (II) Power Button: Configuring as keyboard
[  3129.628] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[  3129.628] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[  3129.628] (**) Option "xkb_rules" "evdev"
[  3129.628] (**) Option "xkb_model" "pc105"
[  3129.628] (**) Option "xkb_layout" "fr"
[  3129.628] (**) Option "xkb_variant" "oss"
[  3129.630] (II) XKB: reuse xkmfile /var/lib/xkb/server-6CCE7350BC740BB33D520367F4A10E64192A358C.xkm
[  3129.631] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[  3129.631] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[  3129.631] (II) Using input driver 'evdev' for 'Video Bus'
[  3129.631] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  3129.631] (**) Video Bus: always reports core events
[  3129.631] (**) Video Bus: Device: "/dev/input/event4"
[  3129.631] (--) Video Bus: Found keys
[  3129.631] (II) Video Bus: Configuring as keyboard
[  3129.631] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/LNXVIDEO:00/input/input4/event4"
[  3129.631] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[  3129.631] (**) Option "xkb_rules" "evdev"
[  3129.631] (**) Option "xkb_model" "pc105"
[  3129.631] (**) Option "xkb_layout" "fr"
[  3129.631] (**) Option "xkb_variant" "oss"
[  3129.636] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[  3129.636] (II) No input driver/identifier specified (ignoring)
[  3129.636] (II) config/udev: Adding input device Sleep Button (/dev/input/event0)
[  3129.636] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[  3129.636] (II) Using input driver 'evdev' for 'Sleep Button'
[  3129.636] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  3129.636] (**) Sleep Button: always reports core events
[  3129.636] (**) Sleep Button: Device: "/dev/input/event0"
[  3129.636] (--) Sleep Button: Found keys
[  3129.636] (II) Sleep Button: Configuring as keyboard
[  3129.636] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input0/event0"
[  3129.636] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[  3129.636] (**) Option "xkb_rules" "evdev"
[  3129.636] (**) Option "xkb_model" "pc105"
[  3129.636] (**) Option "xkb_layout" "fr"
[  3129.636] (**) Option "xkb_variant" "oss"
[  3129.640] (II) config/udev: Adding input device CKA7216 (/dev/input/event6)
[  3129.640] (**) CKA7216: Applying InputClass "evdev keyboard catchall"
[  3129.640] (II) Using input driver 'evdev' for 'CKA7216'
[  3129.640] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  3129.640] (**) CKA7216: always reports core events
[  3129.640] (**) CKA7216: Device: "/dev/input/event6"
[  3129.640] (--) CKA7216: Found keys
[  3129.640] (II) CKA7216: Configuring as keyboard
[  3129.640] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-5/1-5:1.0/input/input6/event6"
[  3129.640] (II) XINPUT: Adding extended input device "CKA7216" (type: KEYBOARD)
[  3129.640] (**) Option "xkb_rules" "evdev"
[  3129.640] (**) Option "xkb_model" "pc105"
[  3129.640] (**) Option "xkb_layout" "fr"
[  3129.640] (**) Option "xkb_variant" "oss"
[  3129.647] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[  3129.647] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[  3129.647] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[  3129.647] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  3129.647] (**) AT Translated Set 2 keyboard: always reports core events
[  3129.647] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[  3129.647] (--) AT Translated Set 2 keyboard: Found keys
[  3129.647] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[  3129.647] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[  3129.647] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[  3129.647] (**) Option "xkb_rules" "evdev"
[  3129.647] (**) Option "xkb_model" "pc105"
[  3129.647] (**) Option "xkb_layout" "fr"
[  3129.647] (**) Option "xkb_variant" "oss"
[  3129.647] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event7)
[  3129.647] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[  3129.647] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[  3129.647] (II) LoadModule: "synaptics"
[  3129.648] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[  3129.648] (II) Module synaptics: vendor="X.Org Foundation"
[  3129.648]     compiled for 1.10.4, module version = 1.4.1
[  3129.648]     Module class: X.Org XInput Driver
[  3129.648]     ABI class: X.Org XInput driver, version 12.3
[  3129.648] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[  3129.648] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[  3129.648] (**) SynPS/2 Synaptics TouchPad: always reports core events
[  3129.648] (**) Option "Device" "/dev/input/event7"
[  3129.720] (--) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[  3129.720] (--) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[  3129.720] (--) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[  3129.720] (--) SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[  3129.720] (--) SynPS/2 Synaptics TouchPad: buttons: left right middle
[  3129.824] (--) SynPS/2 Synaptics TouchPad: touchpad found
[  3129.824] (**) SynPS/2 Synaptics TouchPad: always reports core events
[  3129.824] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio4/input/input7/event7"
[  3129.824] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[  3129.824] (**) SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[  3129.824] (**) SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[  3129.824] (**) SynPS/2 Synaptics TouchPad: AccelFactor is now 0.040
[  3129.824] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[  3129.824] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[  3129.824] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[  3129.824] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[  3129.824] (II) SynPS/2 Synaptics TouchPad: failed to open grail, no gesture support
[  3129.824] (--) SynPS/2 Synaptics TouchPad: touchpad found
[  3129.825] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[  3129.825] (II) No input driver/identifier specified (ignoring)
[  3129.825] (II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/event9)
[  3129.825] (**) PS/2 Generic Mouse: Applying InputClass "evdev pointer catchall"
[  3129.825] (II) Using input driver 'evdev' for 'PS/2 Generic Mouse'
[  3129.825] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  3129.825] (**) PS/2 Generic Mouse: always reports core events
[  3129.825] (**) PS/2 Generic Mouse: Device: "/dev/input/event9"
[  3129.825] (--) PS/2 Generic Mouse: Found 3 mouse buttons
[  3129.825] (--) PS/2 Generic Mouse: Found relative axes
[  3129.825] (--) PS/2 Generic Mouse: Found x and y relative axes
[  3129.825] (II) PS/2 Generic Mouse: Configuring as mouse
[  3129.825] (**) PS/2 Generic Mouse: YAxisMapping: buttons 4 and 5
[  3129.825] (**) PS/2 Generic Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  3129.825] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio4/serio5/input/input9/event9"
[  3129.825] (II) XINPUT: Adding extended input device "PS/2 Generic Mouse" (type: MOUSE)
[  3129.825] (II) PS/2 Generic Mouse: initialized for relative axes.
[  3129.826] (**) PS/2 Generic Mouse: (accel) keeping acceleration scheme 1
[  3129.826] (**) PS/2 Generic Mouse: (accel) acceleration profile 0
[  3129.826] (**) PS/2 Generic Mouse: (accel) acceleration factor: 2.000
[  3129.826] (**) PS/2 Generic Mouse: (accel) acceleration threshold: 4
[  3129.826] (II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/mouse1)
[  3129.826] (II) No input driver/identifier specified (ignoring)
[  3129.826] (II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/event5)
[  3129.826] (II) No input driver/identifier specified (ignoring)
[  3129.827] (II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/js0)
[  3129.827] (II) No input driver/identifier specified (ignoring)
[  3129.834] (II) config/udev: Adding input device HP WMI hotkeys (/dev/input/event8)
[  3129.834] (**) HP WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[  3129.834] (II) Using input driver 'evdev' for 'HP WMI hotkeys'
[  3129.834] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  3129.834] (**) HP WMI hotkeys: always reports core events
[  3129.834] (**) HP WMI hotkeys: Device: "/dev/input/event8"
[  3129.834] (--) HP WMI hotkeys: Found keys
[  3129.834] (II) HP WMI hotkeys: Configuring as keyboard
[  3129.834] (**) Option "config_info" "udev:/sys/devices/virtual/input/input8/event8"
[  3129.834] (II) XINPUT: Adding extended input device "HP WMI hotkeys" (type: KEYBOARD)
[  3129.834] (**) Option "xkb_rules" "evdev"
[  3129.834] (**) Option "xkb_model" "pc105"
[  3129.834] (**) Option "xkb_layout" "fr"
[  3129.834] (**) Option "xkb_variant" "oss"
[  3138.113] (II) XKB: reuse xkmfile /var/lib/xkb/server-0CF70113BD0CF0830F6D9334ADBCCCCFD25B9871.xkm
[  4456.608] (II) Open ACPI successful (/var/run/acpid.socket)
[  4456.780] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[  4458.219] (II) SynPS/2 Synaptics TouchPad: failed to open grail, no gesture support
[  4458.219] (--) SynPS/2 Synaptics TouchPad: touchpad found
[  6639.528] 
Backtrace:
[  6639.548] 0: /usr/bin/X (xorg_backtrace+0x26) [0x460566]
[  6639.548] 1: /usr/bin/X (0x400000+0x64b7a) [0x464b7a]
[  6639.548] 2: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7f16648d2000+0x10060) [0x7f16648e2060]
[  6639.548] 3: /usr/lib/libXfont.so.1 (FontFileListNextFontWithInfo+0x29) [0x7f166442ec89]
[  6639.548] 4: /usr/bin/X (doListFontsWithInfo+0x16d) [0x43061d]
[  6639.548] 5: /usr/bin/X (ProcessWorkQueue+0x21) [0x433d51]
[  6639.548] 6: /usr/bin/X (WaitForSomething+0x65) [0x45dec5]
[  6639.549] 7: /usr/bin/X (0x400000+0x2f912) [0x42f912]
[  6639.549] 8: /usr/bin/X (0x400000+0x232fe) [0x4232fe]
[  6639.549] 9: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xed) [0x7f166380e30d]
[  6639.549] 10: /usr/bin/X (0x400000+0x235ed) [0x4235ed]
[  6639.549] Segmentation fault at address (nil)
[  6639.549] 
Caught signal 11 (Segmentation fault). Server aborting
[  6639.549] 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[  6639.549] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[  6639.549] 
[  6639.600] (II) Power Button: Close
[  6639.600] (II) UnloadModule: "evdev"
[  6639.600] (II) Unloading evdev
[  6639.604] (II) Video Bus: Close
[  6639.604] (II) UnloadModule: "evdev"
[  6639.604] (II) Unloading evdev
[  6639.608] (II) Sleep Button: Close
[  6639.608] (II) UnloadModule: "evdev"
[  6639.608] (II) Unloading evdev
[  6639.612] (II) CKA7216: Close
[  6639.612] (II) UnloadModule: "evdev"
[  6639.612] (II) Unloading evdev
[  6639.616] (II) AT Translated Set 2 keyboard: Close
[  6639.616] (II) UnloadModule: "evdev"
[  6639.616] (II) Unloading evdev
[  6639.644] (II) UnloadModule: "synaptics"
[  6639.644] (II) Unloading synaptics
[  6639.646] (II) PS/2 Generic Mouse: Close
[  6639.646] (II) UnloadModule: "evdev"
[  6639.646] (II) Unloading evdev
[  6639.648] (II) HP WMI hotkeys: Close
[  6639.648] (II) UnloadModule: "evdev"
[  6639.648] (II) Unloading evdev
[  6642.265]  ddxSigGiveUp: Closing log

```

---

### Post by roelforg on 2012-02-24
try:
```

sudo apt-get install nvidia-common-updates

```

---

### Post by inconnu259 on 2012-02-24
I haven't nvidia-common-updates. Only nvidia-settings-updates and nvidia-current-updates.
I already reinstall all drivers. But nothing change.
I try to reinstall all library in the backtrace like this : libpthread, libXfont and libc but only libc have an error. I can't reinstall it with synaptic.

---

### Post by roelforg on 2012-02-24
> **inconnu259 said:**
> I haven't nvidia-common-updates. Only nvidia-settings-updates and nvidia-current-updates.
I already reinstall all drivers. But nothing change.
I try to reinstall all library in the backtrace like this : libpthread, libXfont and libc but only libc have an error. I can't reinstall it with synaptic.
Yeah.. That was a case of my fingers going faster then my brain, i meant nvidia-current-updates.
Try this:
```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by inconnu259 on 2012-02-24
Nothing change.
   I don't know if it's related or not. But before I noticed this problem, I uninstalled libjpeg62 .... And all its dependencies. Yes, I know it's stupid but I had read that it could correct a problem....
And after that, no unity, no lightdm, no graphical interface...
So I had to reinstall everything. And after that, when I connected, the X server crashed and rebooted....
I fixed it by deleted some configuratio file in home (or reinstall driver, I don't remember)....
And now... I have this problem... But maybe but is not related, because I have installed some library for programming...

---

### Post by roelforg on 2012-02-24
> **inconnu259 said:**
> Nothing change.
   I don't know if it's related or not. But before I noticed this problem, I uninstalled libjpeg62 .... And all its dependencies. Yes, I know it's stupid but I had read that it could correct a problem....
And after that, no unity, no lightdm, no graphical interface...
So I had to reinstall everything. And after that, when I connected, the X server crashed and rebooted....
I fixed it by deleted some configuratio file in home (or reinstall driver, I don't remember)....
And now... I have this problem... But maybe but is not related, because I have installed some library for programming...
Completely reinstall xorg. (look in the wiki for the instructions)

---

### Post by inconnu259 on 2012-02-24
It works !
You're a genius !!!!
Thank you !

---

### Post by roelforg on 2012-02-24
> **inconnu259 said:**
> It works !
You're a genius !!!!
Thank you !
Sometimes your Xorg is out of date. The reinstall will fix any config probs. and upgrade as well.

---

