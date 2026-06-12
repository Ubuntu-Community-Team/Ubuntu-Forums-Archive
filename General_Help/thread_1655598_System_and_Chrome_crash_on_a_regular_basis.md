---
title: "System and Chrome crash on a regular basis"
date: 2010-12-29
forum: General Help
---

### Post by pr0grammer1 on 2010-12-29
[Edit] The issue turned out to be a bad stick of RAM. I should have checked that first ;)

I switched back from Windows a few weeks ago, and ever since, my computer's been crashing (everything freezes up and doesn't respond to any input at all) at least once every 1-3 days. In addition to that, Chrome crashes anywhere from 5 to 30 times per day, and I have an individual tab crash every 5-15 minutes.

Am I correct in assuming that this isn't normal? Which logs should I look at to find the cause of the crashes?

Edit: I've tried the stable, beta and dev builds of Chrome, and all of them crash with approximately the same frequency.

---

### Post by cariboo on 2010-12-29
Check /var/log/Xorg.0.log, it sounds like a video driver problem.

---

### Post by pr0grammer1 on 2010-12-29
Here's the contents of that log:
```
[    49.629] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    49.629] X Protocol Version 11, Revision 0
[    49.629] Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
[    49.629] Current Operating System: Linux alex-desktop 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 02:41:37 UTC 2010 x86_64
[    49.629] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-24-generic root=UUID=e079b1a2-da66-4ef2-af74-27d32a8a5048 ro quiet splash
[    49.629] Build Date: 16 September 2010  06:18:41PM
[    49.629] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    49.629] Current version of pixman: 0.18.4
[    49.629] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    49.629] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    49.629] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Dec 29 17:36:02 2010
[    49.629] (==) Using config file: "/etc/X11/xorg.conf"
[    49.629] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    49.629] (==) ServerLayout "Layout0"
[    49.629] (**) |-->Screen "Screen0" (0)
[    49.629] (**) |   |-->Monitor "Monitor0"
[    49.630] (**) |   |-->Device "Device0"
[    49.630] (**) |-->Input Device "Keyboard0"
[    49.630] (**) |-->Input Device "Mouse0"
[    49.630] (**) Option "Xinerama" "0"
[    49.630] (==) Automatically adding devices
[    49.630] (==) Automatically enabling devices
[    49.630] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    49.630] 	Entry deleted from font path.
[    49.630] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    49.630] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    49.630] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    49.630] (WW) Disabling Keyboard0
[    49.630] (WW) Disabling Mouse0
[    49.630] (II) Loader magic: 0x7d0200
[    49.630] (II) Module ABI versions:
[    49.630] 	X.Org ANSI C Emulation: 0.4
[    49.630] 	X.Org Video Driver: 8.0
[    49.630] 	X.Org XInput driver : 11.0
[    49.630] 	X.Org Server Extension : 4.0
[    49.631] (--) PCI:*(0:1:0:0) 10de:0611:0000:0000 rev 162, Mem @ 0xcc000000/16777216, 0xb0000000/268435456, 0xca000000/33554432, I/O @ 0x00009c00/128, BIOS @ 0x????????/131072
[    49.631] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    49.631] (II) LoadModule: "extmod"
[    49.650] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    49.651] (II) Module extmod: vendor="X.Org Foundation"
[    49.651] 	compiled for 1.9.0, module version = 1.0.0
[    49.651] 	Module class: X.Org Server Extension
[    49.651] 	ABI class: X.Org Server Extension, version 4.0
[    49.651] (II) Loading extension MIT-SCREEN-SAVER
[    49.651] (II) Loading extension XFree86-VidModeExtension
[    49.651] (II) Loading extension XFree86-DGA
[    49.651] (II) Loading extension DPMS
[    49.651] (II) Loading extension XVideo
[    49.651] (II) Loading extension XVideo-MotionCompensation
[    49.651] (II) Loading extension X-Resource
[    49.651] (II) LoadModule: "dbe"
[    49.651] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    49.651] (II) Module dbe: vendor="X.Org Foundation"
[    49.651] 	compiled for 1.9.0, module version = 1.0.0
[    49.651] 	Module class: X.Org Server Extension
[    49.651] 	ABI class: X.Org Server Extension, version 4.0
[    49.651] (II) Loading extension DOUBLE-BUFFER
[    49.651] (II) LoadModule: "glx"
[    49.651] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    49.661] (II) Module glx: vendor="NVIDIA Corporation"
[    49.661] 	compiled for 4.0.2, module version = 1.0.0
[    49.661] 	Module class: X.Org Server Extension
[    49.661] (II) NVIDIA GLX Module  260.19.06  Mon Sep 13 04:54:41 PDT 2010
[    49.661] (II) Loading extension GLX
[    49.661] (II) LoadModule: "record"
[    49.661] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    49.661] (II) Module record: vendor="X.Org Foundation"
[    49.661] 	compiled for 1.9.0, module version = 1.13.0
[    49.661] 	Module class: X.Org Server Extension
[    49.661] 	ABI class: X.Org Server Extension, version 4.0
[    49.661] (II) Loading extension RECORD
[    49.661] (II) LoadModule: "dri"
[    49.662] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    49.662] (II) Module dri: vendor="X.Org Foundation"
[    49.662] 	compiled for 1.9.0, module version = 1.0.0
[    49.662] 	ABI class: X.Org Server Extension, version 4.0
[    49.662] (II) Loading extension XFree86-DRI
[    49.662] (II) LoadModule: "dri2"
[    49.662] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    49.662] (II) Module dri2: vendor="X.Org Foundation"
[    49.662] 	compiled for 1.9.0, module version = 1.2.0
[    49.662] 	ABI class: X.Org Server Extension, version 4.0
[    49.662] (II) Loading extension DRI2
[    49.662] (II) LoadModule: "nvidia"
[    49.662] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    49.663] (II) Module nvidia: vendor="NVIDIA Corporation"
[    49.663] 	compiled for 4.0.2, module version = 1.0.0
[    49.663] 	Module class: X.Org Video Driver
[    49.663] (II) NVIDIA dlloader X Driver  260.19.06  Mon Sep 13 04:31:43 PDT 2010
[    49.663] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    49.663] (++) using VT number 7

[    49.664] (II) Loading sub module "fb"
[    49.664] (II) LoadModule: "fb"
[    49.664] (II) Loading /usr/lib/xorg/modules/libfb.so
[    49.664] (II) Module fb: vendor="X.Org Foundation"
[    49.664] 	compiled for 1.9.0, module version = 1.0.0
[    49.664] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    49.664] (II) Loading sub module "wfb"
[    49.664] (II) LoadModule: "wfb"
[    49.665] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    49.665] (II) Module wfb: vendor="X.Org Foundation"
[    49.665] 	compiled for 1.9.0, module version = 1.0.0
[    49.665] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    49.665] (II) Loading sub module "ramdac"
[    49.665] (II) LoadModule: "ramdac"
[    49.665] (II) Module "ramdac" already built-in
[    49.665] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    49.665] (==) NVIDIA(0): RGB weight 888
[    49.665] (==) NVIDIA(0): Default visual is TrueColor
[    49.665] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    49.665] (**) NVIDIA(0): Option "TwinView" "1"
[    49.665] (**) NVIDIA(0): Option "MetaModes" "DFP-0: nvidia-auto-select +1920+0, DFP-1: nvidia-auto-select +0+0"
[    49.665] (**) NVIDIA(0): Enabling RENDER acceleration
[    49.665] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[    49.665] (II) NVIDIA(0):     enabled.
[    50.801] (II) NVIDIA(0): NVIDIA GPU GeForce 8800 GT (G92) at PCI:1:0:0 (GPU-0)
[    50.801] (--) NVIDIA(0): Memory: 1048576 kBytes
[    50.801] (--) NVIDIA(0): VideoBIOS: 62.92.16.00.04
[    50.801] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    50.801] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    50.801] (--) NVIDIA(0): Connected display device(s) on GeForce 8800 GT at PCI:1:0:0
[    50.801] (--) NVIDIA(0):     Acer H233H (DFP-0)
[    50.801] (--) NVIDIA(0):     Acer H233H (DFP-1)
[    50.801] (--) NVIDIA(0): Acer H233H (DFP-0): 330.0 MHz maximum pixel clock
[    50.801] (--) NVIDIA(0): Acer H233H (DFP-0): Internal Dual Link TMDS
[    50.801] (--) NVIDIA(0): Acer H233H (DFP-1): 330.0 MHz maximum pixel clock
[    50.801] (--) NVIDIA(0): Acer H233H (DFP-1): Internal Dual Link TMDS
[    50.805] (**) NVIDIA(0): TwinView enabled
[    50.806] (II) NVIDIA(0): Display Devices found referenced in MetaMode: DFP-0, DFP-1
[    50.884] (II) NVIDIA(0): Assigned Display Devices: DFP-0, DFP-1
[    50.885] (II) NVIDIA(0): Validated modes:
[    50.885] (II) NVIDIA(0):    
[    50.885] (II) NVIDIA(0):     "DFP-0:nvidia-auto-select+1920+0,DFP-1:nvidia-auto-select+0+0"
[    50.885] (II) NVIDIA(0): Virtual screen size determined to be 3840 x 1080
[    50.913] (--) NVIDIA(0): DPI set to (95, 94); computed from "UseEdidDpi" X config
[    50.913] (--) NVIDIA(0):     option
[    50.913] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[    50.913] (--) Depth 24 pixmap format is 32 bpp
[    50.913] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    50.915] (II) NVIDIA(0): Initialized GPU GART.
[    50.922] (II) NVIDIA(0): Setting mode
[    50.923] (II) NVIDIA(0):     "DFP-0:nvidia-auto-select+1920+0,DFP-1:nvidia-auto-select+0+0"
[    51.013] (II) Loading extension NV-GLX
[    51.077] (II) NVIDIA(0): Initialized OpenGL Acceleration
[    51.077] (==) NVIDIA(0): Disabling shared memory pixmaps
[    51.077] (II) NVIDIA(0): Initialized X Rendering Acceleration
[    51.078] (==) NVIDIA(0): Backing store disabled
[    51.078] (==) NVIDIA(0): Silken mouse enabled
[    51.095] (**) NVIDIA(0): DPMS enabled
[    51.095] (II) Loading extension NV-CONTROL
[    51.095] (II) Loading extension XINERAMA
[    51.095] (II) Loading sub module "dri2"
[    51.095] (II) LoadModule: "dri2"
[    51.096] (II) Reloading /usr/lib/xorg/modules/extensions/libdri2.so
[    51.096] (II) NVIDIA(0): [DRI2] Setup complete
[    51.096] (==) RandR enabled
[    51.096] (II) Initializing built-in extension Generic Event Extension
[    51.096] (II) Initializing built-in extension SHAPE
[    51.096] (II) Initializing built-in extension MIT-SHM
[    51.096] (II) Initializing built-in extension XInputExtension
[    51.096] (II) Initializing built-in extension XTEST
[    51.096] (II) Initializing built-in extension BIG-REQUESTS
[    51.096] (II) Initializing built-in extension SYNC
[    51.096] (II) Initializing built-in extension XKEYBOARD
[    51.096] (II) Initializing built-in extension XC-MISC
[    51.096] (II) Initializing built-in extension SECURITY
[    51.096] (II) Initializing built-in extension XINERAMA
[    51.096] (II) Initializing built-in extension XFIXES
[    51.096] (II) Initializing built-in extension RENDER
[    51.096] (II) Initializing built-in extension RANDR
[    51.096] (II) Initializing built-in extension COMPOSITE
[    51.096] (II) Initializing built-in extension DAMAGE
[    51.096] (II) Initializing built-in extension GESTURE
[    51.097] (II) Initializing extension GLX
[    51.122] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    51.129] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    51.129] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    51.129] (II) LoadModule: "evdev"
[    51.130] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    51.130] (II) Module evdev: vendor="X.Org Foundation"
[    51.130] 	compiled for 1.9.0, module version = 2.3.2
[    51.130] 	Module class: X.Org XInput Driver
[    51.130] 	ABI class: X.Org XInput driver, version 11.0
[    51.130] (**) Power Button: always reports core events
[    51.130] (**) Power Button: Device: "/dev/input/event1"
[    51.210] (II) Power Button: Found keys
[    51.210] (II) Power Button: Configuring as keyboard
[    51.210] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    51.210] (**) Option "xkb_rules" "evdev"
[    51.210] (**) Option "xkb_model" "pc105"
[    51.210] (**) Option "xkb_layout" "us"
[    51.212] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    51.212] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    51.212] (**) Power Button: always reports core events
[    51.212] (**) Power Button: Device: "/dev/input/event0"
[    51.260] (II) Power Button: Found keys
[    51.260] (II) Power Button: Configuring as keyboard
[    51.260] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    51.260] (**) Option "xkb_rules" "evdev"
[    51.260] (**) Option "xkb_model" "pc105"
[    51.260] (**) Option "xkb_layout" "us"
[    51.261] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event2)
[    51.261] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    51.261] (**) Logitech USB Receiver: always reports core events
[    51.261] (**) Logitech USB Receiver: Device: "/dev/input/event2"
[    51.322] (II) Logitech USB Receiver: Found keys
[    51.322] (II) Logitech USB Receiver: Configuring as keyboard
[    51.322] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    51.322] (**) Option "xkb_rules" "evdev"
[    51.322] (**) Option "xkb_model" "pc105"
[    51.322] (**) Option "xkb_layout" "us"
[    51.323] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event3)
[    51.323] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[    51.323] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    51.323] (**) Logitech USB Receiver: always reports core events
[    51.323] (**) Logitech USB Receiver: Device: "/dev/input/event3"
[    51.350] (II) Logitech USB Receiver: Found 20 mouse buttons
[    51.350] (II) Logitech USB Receiver: Found scroll wheel(s)
[    51.350] (II) Logitech USB Receiver: Found relative axes
[    51.350] (II) Logitech USB Receiver: Found x and y relative axes
[    51.350] (II) Logitech USB Receiver: Found absolute axes
[    51.350] (II) evdev-grail: failed to open grail, no gesture support
[    51.350] (II) Logitech USB Receiver: Found keys
[    51.350] (II) Logitech USB Receiver: Configuring as mouse
[    51.350] (II) Logitech USB Receiver: Configuring as keyboard
[    51.350] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    51.350] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    51.350] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    51.350] (**) Option "xkb_rules" "evdev"
[    51.350] (**) Option "xkb_model" "pc105"
[    51.350] (**) Option "xkb_layout" "us"
[    51.350] (II) Logitech USB Receiver: initialized for relative axes.
[    51.350] (WW) Logitech USB Receiver: ignoring absolute axes.
[    51.350] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse0)
[    51.350] (II) No input driver/identifier specified (ignoring)
```

I also tried running Chrome from the terminal. I've highlighted lines coinciding with a crash with ###. The first two crashes were tab crashes, the third was Flash crashing.
```
alex@alex-desktop:~$ google-chrome
[2811:2811:905547901:ERROR:base/native_library_linux.cc(32)] dlopen failed when trying to open libGLESv2.so: libGLESv2.so: cannot open shared object file: No such file or directory
[2712:2727:908282934:ERROR:net/disk_cache/backend_impl.cc(1172)] Critical error found -8
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
###[2712:2729:1166438310:ERROR:chrome/browser/crash_handler_host_linux.cc(290)] Failed to write crash dump for pid 2849
###Parent failed to complete crash dump.
###Cannot upload crash dump: cannot alloc
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
###[2712:2729:1605421259:ERROR:chrome/browser/crash_handler_host_linux.cc(290)] Failed to write ###crash dump for pid 2870
###Parent failed to complete crash dump.
Cannot upload crash dump: cannot alloc
###*** NSPlugin Viewer  *** ERROR: NPN_InvalidateRect() invoke: Connection reset by peer
###*** NSPlugin Viewer  *** WARNING:(/build/buildd/nspluginwrapper-1.2.2/src/npw-viewer.c:1017):invoke_NPN_InvalidateRect: assertion failed: (rpc_method_invoke_possible(g_rpc_connection))
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()

```

---

### Post by pr0grammer1 on 2010-12-29
Chrome just crashed. Here's what went on in the terminal:

```
--2010-12-29 18:21:14--  https://clients2.google.com/cr/report
Resolving clients2.google.com... 74.125.127.100, 74.125.127.138, 74.125.127.139, ...
Connecting to clients2.google.com|74.125.127.100|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `/dev/fd/3'

    [<=>                                                                                                              ] 0           --.-K/s              
fc1a64c4348bcb6b    [ <=>                                                                                                             ] 16          --.-K/s   in 0s      


2010-12-29 18:21:15 (1.54 MB/s) - `/dev/fd/3' saved [16]

Segmentation fault
alex@alex-desktop:~$
```

---

### Post by pr0grammer1 on 2010-12-29
Update - I got this in the Chrome terminal:

```
[3458:3473:2924153814:ERROR:chrome/browser/browser_main_gtk.cc(39)] X Error detected: serial 339, error_code 3 (BadWindow (invalid Window parameter)), request code 15 minor_code 0 (X_QueryTree)
```

-Transcribed from a low-quality photo, so a couple numbers may be off.

Around the time that appeared, pretty much everything on the system crashed. Icons didn't show mouseover effects (although they were still clickable), and applications would stay "opening" forever. I could scroll through Chrome windows and enter text, but couldn't navigate to other pages or open new pages (new tabs would open but not load anything). I could select text in the terminal and open new terminals, but couldn't type anything into them. I could switch between workspaces, but after about two minutes things slowed down and then the whole system froze after about thirty seconds more.



---

Xorg.1.log looks like it might have some more relevant info, especially at the bottom:

```
[   736.794] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[   736.794] X Protocol Version 11, Revision 0
[   736.794] Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
[   736.794] Current Operating System: Linux alex-desktop 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:32:27 UTC 2010 x86_64
[   736.794] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=e079b1a2-da66-4ef2-af74-27d32a8a5048 ro quiet splash
[   736.794] Build Date: 16 September 2010  06:18:41PM
[   736.794] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
[   736.794] Current version of pixman: 0.18.4
[   736.794] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[   736.794] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   736.794] (==) Log file: "/var/log/Xorg.1.log", Time: Wed Sep 22 19:23:34 2010
[   736.794] (==) Using config file: "/etc/X11/xorg.conf"
[   736.794] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   736.794] (==) ServerLayout "Layout0"
[   736.794] (**) |-->Screen "Screen0" (0)
[   736.794] (**) |   |-->Monitor "Monitor0"
[   736.795] (**) |   |-->Device "Device0"
[   736.795] (**) |-->Input Device "Keyboard0"
[   736.795] (**) |-->Input Device "Mouse0"
[   736.795] (**) Option "Xinerama" "0"
[   736.795] (==) Automatically adding devices
[   736.795] (==) Automatically enabling devices
[   736.795] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   736.795] 	Entry deleted from font path.
[   736.795] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[   736.795] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   736.795] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[   736.795] (WW) Disabling Keyboard0
[   736.795] (WW) Disabling Mouse0
[   736.795] (II) Loader magic: 0x7d0200
[   736.795] (II) Module ABI versions:
[   736.795] 	X.Org ANSI C Emulation: 0.4
[   736.795] 	X.Org Video Driver: 8.0
[   736.795] 	X.Org XInput driver : 11.0
[   736.795] 	X.Org Server Extension : 4.0
[   736.796] (--) PCI:*(0:1:0:0) 10de:0611:0000:0000 rev 162, Mem @ 0xcc000000/16777216, 0xb0000000/268435456, 0xca000000/33554432, I/O @ 0x00008c00/128, BIOS @ 0x????????/131072
[   736.796] (II) Open ACPI successful (/var/run/acpid.socket)
[   736.796] (II) LoadModule: "extmod"
[   736.796] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   736.796] (II) Module extmod: vendor="X.Org Foundation"
[   736.796] 	compiled for 1.9.0, module version = 1.0.0
[   736.796] 	Module class: X.Org Server Extension
[   736.796] 	ABI class: X.Org Server Extension, version 4.0
[   736.796] (II) Loading extension MIT-SCREEN-SAVER
[   736.796] (II) Loading extension XFree86-VidModeExtension
[   736.796] (II) Loading extension XFree86-DGA
[   736.796] (II) Loading extension DPMS
[   736.796] (II) Loading extension XVideo
[   736.796] (II) Loading extension XVideo-MotionCompensation
[   736.796] (II) Loading extension X-Resource
[   736.796] (II) LoadModule: "dbe"
[   736.797] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   736.797] (II) Module dbe: vendor="X.Org Foundation"
[   736.797] 	compiled for 1.9.0, module version = 1.0.0
[   736.797] 	Module class: X.Org Server Extension
[   736.797] 	ABI class: X.Org Server Extension, version 4.0
[   736.797] (II) Loading extension DOUBLE-BUFFER
[   736.797] (II) LoadModule: "glx"
[   736.797] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[   736.804] (II) Module glx: vendor="NVIDIA Corporation"
[   736.804] 	compiled for 4.0.2, module version = 1.0.0
[   736.804] 	Module class: X.Org Server Extension
[   736.804] (II) NVIDIA GLX Module  256.53  Fri Aug 27 20:50:26 PDT 2010
[   736.804] (II) Loading extension GLX
[   736.804] (II) LoadModule: "record"
[   736.805] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   736.805] (II) Module record: vendor="X.Org Foundation"
[   736.805] 	compiled for 1.9.0, module version = 1.13.0
[   736.805] 	Module class: X.Org Server Extension
[   736.805] 	ABI class: X.Org Server Extension, version 4.0
[   736.805] (II) Loading extension RECORD
[   736.805] (II) LoadModule: "dri"
[   736.805] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   736.805] (II) Module dri: vendor="X.Org Foundation"
[   736.805] 	compiled for 1.9.0, module version = 1.0.0
[   736.805] 	ABI class: X.Org Server Extension, version 4.0
[   736.805] (II) Loading extension XFree86-DRI
[   736.805] (II) LoadModule: "dri2"
[   736.805] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   736.805] (II) Module dri2: vendor="X.Org Foundation"
[   736.805] 	compiled for 1.9.0, module version = 1.2.0
[   736.805] 	ABI class: X.Org Server Extension, version 4.0
[   736.805] (II) Loading extension DRI2
[   736.805] (II) LoadModule: "nvidia"
[   736.805] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[   736.806] (II) Module nvidia: vendor="NVIDIA Corporation"
[   736.806] 	compiled for 4.0.2, module version = 1.0.0
[   736.806] 	Module class: X.Org Video Driver
[   736.806] (II) NVIDIA dlloader X Driver  256.53  Fri Aug 27 20:29:45 PDT 2010
[   736.806] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[   736.806] (--) using VT number 9

[   737.957] (II) Loading sub module "fb"
[   737.957] (II) LoadModule: "fb"
[   737.958] (II) Loading /usr/lib/xorg/modules/libfb.so
[   737.958] (II) Module fb: vendor="X.Org Foundation"
[   737.958] 	compiled for 1.9.0, module version = 1.0.0
[   737.958] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   737.958] (II) Loading sub module "wfb"
[   737.958] (II) LoadModule: "wfb"
[   737.959] (II) Loading /usr/lib/xorg/modules/libwfb.so
[   737.959] (II) Module wfb: vendor="X.Org Foundation"
[   737.959] 	compiled for 1.9.0, module version = 1.0.0
[   737.959] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   737.959] (II) Loading sub module "ramdac"
[   737.959] (II) LoadModule: "ramdac"
[   737.959] (II) Module "ramdac" already built-in
[   737.959] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[   737.959] (==) NVIDIA(0): RGB weight 888
[   737.959] (==) NVIDIA(0): Default visual is TrueColor
[   737.959] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[   737.959] (**) NVIDIA(0): Option "TwinView" "1"
[   737.959] (**) NVIDIA(0): Option "MetaModes" "DFP-0: nvidia-auto-select +1920+0, DFP-1: nvidia-auto-select +0+0"
[   737.959] (**) NVIDIA(0): Enabling RENDER acceleration
[   737.959] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[   737.959] (II) NVIDIA(0):     enabled.
[   738.140] (II) NVIDIA(0): NVIDIA GPU GeForce 8800 GT (G92) at PCI:1:0:0 (GPU-0)
[   738.140] (--) NVIDIA(0): Memory: 1048576 kBytes
[   738.140] (--) NVIDIA(0): VideoBIOS: 62.92.16.00.04
[   738.140] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[   738.140] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[   738.140] (--) NVIDIA(0): Connected display device(s) on GeForce 8800 GT at PCI:1:0:0:
[   738.140] (--) NVIDIA(0):     Acer H233H (DFP-0)
[   738.140] (--) NVIDIA(0):     Acer H233H (DFP-1)
[   738.140] (--) NVIDIA(0): Acer H233H (DFP-0): 330.0 MHz maximum pixel clock
[   738.140] (--) NVIDIA(0): Acer H233H (DFP-0): Internal Dual Link TMDS
[   738.140] (--) NVIDIA(0): Acer H233H (DFP-1): 330.0 MHz maximum pixel clock
[   738.140] (--) NVIDIA(0): Acer H233H (DFP-1): Internal Dual Link TMDS
[   738.143] (**) NVIDIA(0): TwinView enabled
[   738.143] (II) NVIDIA(0): Display Devices found referenced in MetaMode: DFP-0, DFP-1
[   738.215] (II) NVIDIA(0): Assigned Display Devices: DFP-0, DFP-1
[   738.215] (II) NVIDIA(0): Validated modes:
[   738.215] (II) NVIDIA(0):    
[   738.215] (II) NVIDIA(0):     "DFP-0:nvidia-auto-select+1920+0,DFP-1:nvidia-auto-select+0+0"
[   738.215] (II) NVIDIA(0): Virtual screen size determined to be 3840 x 1080
[   738.243] (--) NVIDIA(0): DPI set to (95, 94); computed from "UseEdidDpi" X config
[   738.243] (--) NVIDIA(0):     option
[   738.243] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[   738.243] (--) Depth 24 pixmap format is 32 bpp
[   738.243] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[   738.244] (II) NVIDIA(0): Initialized GPU GART.
[   738.250] (II) NVIDIA(0): Setting mode
[   738.250] (II) NVIDIA(0):     "DFP-0:nvidia-auto-select+1920+0,DFP-1:nvidia-auto-select+0+0"
[   738.350] (II) Loading extension NV-GLX
[   738.399] (II) NVIDIA(0): Initialized OpenGL Acceleration
[   738.400] (==) NVIDIA(0): Disabling shared memory pixmaps
[   738.400] (II) NVIDIA(0): Initialized X Rendering Acceleration
[   738.400] (==) NVIDIA(0): Backing store disabled
[   738.400] (==) NVIDIA(0): Silken mouse enabled
[   738.418] (**) NVIDIA(0): DPMS enabled
[   738.418] (II) Loading extension NV-CONTROL
[   738.418] (II) Loading extension XINERAMA
[   738.418] (II) Loading sub module "dri2"
[   738.418] (II) LoadModule: "dri2"
[   738.418] (II) Reloading /usr/lib/xorg/modules/extensions/libdri2.so
[   738.419] (II) NVIDIA(0): [DRI2] Setup complete
[   738.419] (==) RandR enabled
[   738.419] (II) Initializing built-in extension Generic Event Extension
[   738.419] (II) Initializing built-in extension SHAPE
[   738.419] (II) Initializing built-in extension MIT-SHM
[   738.419] (II) Initializing built-in extension XInputExtension
[   738.419] (II) Initializing built-in extension XTEST
[   738.419] (II) Initializing built-in extension BIG-REQUESTS
[   738.419] (II) Initializing built-in extension SYNC
[   738.419] (II) Initializing built-in extension XKEYBOARD
[   738.419] (II) Initializing built-in extension XC-MISC
[   738.419] (II) Initializing built-in extension SECURITY
[   738.419] (II) Initializing built-in extension XINERAMA
[   738.419] (II) Initializing built-in extension XFIXES
[   738.419] (II) Initializing built-in extension RENDER
[   738.419] (II) Initializing built-in extension RANDR
[   738.419] (II) Initializing built-in extension COMPOSITE
[   738.419] (II) Initializing built-in extension DAMAGE
[   738.419] (II) Initializing built-in extension GESTURE
[   738.420] (II) Initializing extension GLX
[   738.440] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   738.446] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[   738.446] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   738.446] (II) LoadModule: "evdev"
[   738.446] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   738.446] (II) Module evdev: vendor="X.Org Foundation"
[   738.446] 	compiled for 1.9.0, module version = 2.3.2
[   738.446] 	Module class: X.Org XInput Driver
[   738.446] 	ABI class: X.Org XInput driver, version 11.0
[   738.446] (**) Power Button: always reports core events
[   738.446] (**) Power Button: Device: "/dev/input/event1"
[   738.513] (II) Power Button: Found keys
[   738.513] (II) Power Button: Configuring as keyboard
[   738.513] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[   738.513] (**) Option "xkb_rules" "evdev"
[   738.513] (**) Option "xkb_model" "pc105"
[   738.513] (**) Option "xkb_layout" "us"
[   738.515] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[   738.515] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   738.515] (**) Power Button: always reports core events
[   738.515] (**) Power Button: Device: "/dev/input/event0"
[   738.562] (II) Power Button: Found keys
[   738.562] (II) Power Button: Configuring as keyboard
[   738.562] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[   738.562] (**) Option "xkb_rules" "evdev"
[   738.562] (**) Option "xkb_model" "pc105"
[   738.562] (**) Option "xkb_layout" "us"
[   738.563] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event2)
[   738.563] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[   738.563] (**) Logitech USB Receiver: always reports core events
[   738.563] (**) Logitech USB Receiver: Device: "/dev/input/event2"
[   738.673] (II) Logitech USB Receiver: Found keys
[   738.673] (II) Logitech USB Receiver: Configuring as keyboard
[   738.673] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[   738.673] (**) Option "xkb_rules" "evdev"
[   738.673] (**) Option "xkb_model" "pc105"
[   738.673] (**) Option "xkb_layout" "us"
[   738.674] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event3)
[   738.674] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[   738.674] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[   738.674] (**) Logitech USB Receiver: always reports core events
[   738.674] (**) Logitech USB Receiver: Device: "/dev/input/event3"
[   738.733] (II) Logitech USB Receiver: Found 20 mouse buttons
[   738.733] (II) Logitech USB Receiver: Found scroll wheel(s)
[   738.733] (II) Logitech USB Receiver: Found relative axes
[   738.733] (II) Logitech USB Receiver: Found x and y relative axes
[   738.733] (II) Logitech USB Receiver: Found absolute axes
[   738.733] (II) evdev-grail: failed to open grail, no gesture support
[   738.733] (II) Logitech USB Receiver: Found keys
[   738.733] (II) Logitech USB Receiver: Configuring as mouse
[   738.733] (II) Logitech USB Receiver: Configuring as keyboard
[   738.733] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[   738.733] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   738.733] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[   738.733] (**) Option "xkb_rules" "evdev"
[   738.733] (**) Option "xkb_model" "pc105"
[   738.733] (**) Option "xkb_layout" "us"
[   738.734] (II) Logitech USB Receiver: initialized for relative axes.
[   738.734] (WW) Logitech USB Receiver: ignoring absolute axes.
[   738.734] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse0)
[   738.734] (II) No input driver/identifier specified (ignoring)
[   760.089] (II) Open ACPI successful (/var/run/acpid.socket)
[   760.139] (II) NVIDIA(0): Setting mode
[   760.139] (II) NVIDIA(0):     "DFP-0:nvidia-auto-select+1920+0,DFP-1:nvidia-auto-select+0+0"
[   760.483] (II) Power Button: Device reopened after 1 attempts.
[   760.523] (II) Power Button: Device reopened after 1 attempts.
[   760.552] (II) Logitech USB Receiver: Device reopened after 1 attempts.
[   760.582] (II) Logitech USB Receiver: Device reopened after 1 attempts.
[145013.030] (II) Open ACPI successful (/var/run/acpid.socket)
[145013.289] (II) NVIDIA(0): Setting mode
[145013.290] (II) NVIDIA(0):     "DFP-0:nvidia-auto-select+1920+0,DFP-1:nvidia-auto-select+0+0"
[145014.221] (II) Power Button: Device reopened after 1 attempts.
[145014.241] (II) Power Button: Device reopened after 1 attempts.
[145014.261] (II) Logitech USB Receiver: Device reopened after 1 attempts.
[145014.281] (II) Logitech USB Receiver: Device reopened after 1 attempts.
[145019.815] (WW) Open ACPI failed (/var/run/acpid.socket) (Connection refused)
[145026.120] (II) Power Button: Close
[145027.124] (II) UnloadModule: "evdev"
[145030.951] (II) Power Button: Close
[145030.951] (II) UnloadModule: "evdev"
[145031.151] (II) Logitech USB Receiver: Close
[145031.151] (II) UnloadModule: "evdev"
[145031.240] (II) Logitech USB Receiver: Close
[145031.366] (II) UnloadModule: "evdev"
[145033.391] (WW) xf86CloseConsole: VT_WAITACTIVE failed: Interrupted system call
[145033.392]  ddxSigGiveUp: Closing log
```

---

### Post by pr0grammer1 on 2010-12-30
I found this in system.log after another crash, if it might help anything:

```
Dec 29 21:50:43 alex-desktop kernel: [11614.025445] chrome[2805]: segfault at 5b478a0 ip 0000000005b478a0 sp 00007fff22cfe878 error 15
```

---

### Post by pr0grammer1 on 2011-01-02
I managed to go a few days without a crash, but my screen just randomly blacked out, flashed the nVidia logo, and dumped me back to the login screen. After logging back in, the theme is now light grey (instead of black) and looks really old-style. Here's some relevant lines from Xorg.0.log.old:

```
[ 52945.983] (II) XKB: generating xkmfile /var/lib/xkb/server-DAEA4C886ED13CCB49EF0284D9D47E5611DB4ADA.xkm
[ 53841.444]
Backtrace:
[ 53841.444] 0: /usr/bin/X (xorg_backtrace+0x28) [0x4a0fa8]
[ 53841.444] 1: /usr/bin/X (0x400000+0x60fcd) [0x460fcd]
[ 53841.444] 2: /lib/libpthread.so.0 (0x7f592596b000+0xfb40) [0x7f592597ab40]
[ 53841.444] 3: /usr/bin/X (0x400000+0xb0a26) [0x4b0a26]
[ 53841.444] 4: /usr/bin/X (0x400000+0xb1c55) [0x4b1c55]
[ 53841.444] 5: /usr/bin/X (0x400000+0x2c2d9) [0x42c2d9]
[ 53841.444] 6: /usr/bin/X (0x400000+0x2184b) [0x42184b]
[ 53841.444] 7: /lib/libc.so.6 (__libc_start_main+0xfe) [0x7f59248d6d8e]
[ 53841.444] 8: /usr/bin/X (0x400000+0x213d9) [0x4213d9]
[ 53841.444] Segmentation fault at address 0x20
[ 53841.444]
Caught signal 11 (Segmentation fault). Server aborting
[ 53841.444]
Please consult the The X.Org Foundation support
         at http://wiki.x.org
 for help.
[ 53841.444] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[ 53841.444]
[ 53841.512] (II) Power Button: Close
[ 53841.512] (II) UnloadModule: "evdev"
[ 53841.592] (II) Power Button: Close
[ 53841.592] (II) UnloadModule: "evdev"
[ 53841.692] (II) Logitech USB Receiver: Close
[ 53841.692] (II) UnloadModule: "evdev"
[ 53841.752] (II) Logitech USB Receiver: Close
[ 53841.753] (II) UnloadModule: "evdev"
[ 53842.313]  ddxSigGiveUp: Closing log
```

Does this have anything to do with my situation, or is it just a random crash resulting from a bug? If so, where should I report it?

---

