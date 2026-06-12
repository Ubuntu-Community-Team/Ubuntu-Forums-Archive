---
title: "Nvidia 195.36.15 - No GLX"
date: 2010-05-03
forum: General Help
---

### Post by adaptive on 2010-05-03
I haven't had any nvidia problems for a while, and I don't know how long it has been since I have not had GLX. 

But...I recently performed an upgrade from Karmic to Lucid, and so far most everything has been working fine. The GLX is the only think broken that I have noticed. 

Here is what is weird: I have a laptop at work, also nvidia, also did the upgrade, and its GLX has worked fine. I am not sure what the problem is. When I compare the nvidia packages that have been installed, they look comparable. So I don't understand why one works and the other doesn't.

When I check the hardware drivers menu, it says I am using the recommended and current nvidia driver. When I check it on nvidia-settings, it says I am using 195.36.15. Under OpenGL/GLX information, I get the following error: Fail to query the GLX server vendor. 

When I try and run GLX gears, I get the following: Error: couldn't get an RGB, Double-buffered visual.

My xorg.conf appears to be set up correctly [and in a similar manner to my laptop], with a load "GLX" module and the right "nvidia" driver. 

Can someone tell me what information I need to post to get this to work correctly? I would rather use the repository driver, and I would rather keep using the current driver [for some CUDA work]. I know it will work with the repository driver as it works on my laptop.


If it matters my desktop [not working GLX] card is a GeForce GTX 260; my laptop [the one that works] is a Quadro FX 770M. Thanks in advance.

---

### Post by GSF1200S on 2010-05-03
> **adaptive said:**
> I haven't had any nvidia problems for a while, and I don't know how long it has been since I have not had GLX. 

But...I recently performed an upgrade from Karmic to Lucid, and so far most everything has been working fine. The GLX is the only think broken that I have noticed. 

Here is what is weird: I have a laptop at work, also nvidia, also did the upgrade, and its GLX has worked fine. I am not sure what the problem is. When I compare the nvidia packages that have been installed, they look comparable. So I don't understand why one works and the other doesn't.

When I check the hardware drivers menu, it says I am using the recommended and current nvidia driver. When I check it on nvidia-settings, it says I am using 195.36.15. Under OpenGL/GLX information, I get the following error: Fail to query the GLX server vendor. 

When I try and run GLX gears, I get the following: Error: couldn't get an RGB, Double-buffered visual.

My xorg.conf appears to be set up correctly [and in a similar manner to my laptop], with a load "GLX" module and the right "nvidia" driver. 

Can someone tell me what information I need to post to get this to work correctly? I would rather use the repository driver, and I would rather keep using the current driver [for some CUDA work]. I know it will work with the repository driver as it works on my laptop.


If it matters my desktop [not working GLX] card is a GeForce GTX 260; my laptop [the one that works] is a Quadro FX 770M. Thanks in advance.

Can you please post the contents of:
```
sudo gedit /var/log/Xorg.0.log
```
in a reply here? We need to figure out why GLX isnt initializing. Remember to wrap the results in code tags so it makes it easier to read (the # at the top of your post window)

---

### Post by adaptive on 2010-05-04
If there is something you just want me to grep out of here, please let me know...
```
X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux AdaptiveMesh.info 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.32-21-generic root=UUID=979d5991-8730-423c-aedb-31095dfc8f9b ro quiet splash nomodeset video=uvesafb:mode_option=1680x1050-24,mtrr=3,scroll=ywrap
Build Date: 23 April 2010  05:11:46PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon May  3 22:59:10 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
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

(--) PCI:*(0:1:0:0) 10de:05e2:1462:1771 nVidia Corporation GT200 [GeForce GTX 260] rev 161, Mem @ 0xf8000000/16777216, 0xe0000000/268435456, 0xf6000000/33554432, I/O @ 0x0000cf00/128, BIOS @ 0x????????/524288
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
(II) NVIDIA GLX Module  195.36.15  Fri Mar 12 01:17:05 PST 2010
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
(II) NVIDIA dlloader X Driver  195.36.15  Fri Mar 12 00:38:50 PST 2010
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
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
(**) NVIDIA(0): Option "MetaModes" "nvidia-auto-select +0+0"
(**) May 03 22:59:10 NVIDIA(0): Enabling RENDER acceleration
(II) May 03 22:59:10 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) May 03 22:59:10 NVIDIA(0):     enabled.
(II) May 03 22:59:12 NVIDIA(0): NVIDIA GPU GeForce GTX 260 (GT200) at PCI:1:0:0 (GPU-0)
(--) May 03 22:59:12 NVIDIA(0): Memory: 917504 kBytes
(--) May 03 22:59:12 NVIDIA(0): VideoBIOS: 62.00.4c.00.01
(II) May 03 22:59:12 NVIDIA(0): Detected PCI Express Link width: 16X
(--) May 03 22:59:12 NVIDIA(0): Interlaced video modes are supported on this GPU
(--) May 03 22:59:12 NVIDIA(0): Connected display device(s) on GeForce GTX 260 at PCI:1:0:0:
(--) May 03 22:59:12 NVIDIA(0):     DELL E228WFP (DFP-1)
(--) May 03 22:59:12 NVIDIA(0): DELL E228WFP (DFP-1): 330.0 MHz maximum pixel clock
(--) May 03 22:59:12 NVIDIA(0): DELL E228WFP (DFP-1): Internal Dual Link TMDS
(II) May 03 22:59:12 NVIDIA(0): Assigned Display Device: DFP-1
(II) May 03 22:59:12 NVIDIA(0): Validated modes:
(II) May 03 22:59:12 NVIDIA(0):     "nvidia-auto-select+0+0"
(II) May 03 22:59:12 NVIDIA(0): Virtual screen size determined to be 1680 x 1050
(--) May 03 22:59:12 NVIDIA(0): DPI set to (90, 88); computed from "UseEdidDpi" X config
(--) May 03 22:59:12 NVIDIA(0):     option
(==) May 03 22:59:12 NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) May 03 22:59:12 NVIDIA: Using 768.00 MB of virtual memory for indirect framebuffer
(II) May 03 22:59:12 NVIDIA:     access.
(II) May 03 22:59:12 NVIDIA(0): Initialized GPU GART.
(II) May 03 22:59:12 NVIDIA(0): Setting mode "nvidia-auto-select+0+0"
(II) Loading extension NV-GLX
(II) May 03 22:59:12 NVIDIA(0): Initialized OpenGL Acceleration
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) May 03 22:59:12 NVIDIA(0): Initialized X Rendering Acceleration
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
(II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/event3)
(**) Logitech USB-PS/2 Optical Mouse: Applying InputClass "evdev pointer catchall"
(**) Logitech USB-PS/2 Optical Mouse: always reports core events
(**) Logitech USB-PS/2 Optical Mouse: Device: "/dev/input/event3"
(II) Logitech USB-PS/2 Optical Mouse: Found 12 mouse buttons
(II) Logitech USB-PS/2 Optical Mouse: Found scroll wheel(s)
(II) Logitech USB-PS/2 Optical Mouse: Found relative axes
(II) Logitech USB-PS/2 Optical Mouse: Found x and y relative axes
(II) Logitech USB-PS/2 Optical Mouse: Configuring as mouse
(**) Logitech USB-PS/2 Optical Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech USB-PS/2 Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB-PS/2 Optical Mouse" (type: MOUSE)
(II) Logitech USB-PS/2 Optical Mouse: initialized for relative axes.
(II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device   USB Keyboard (/dev/input/event4)
(**)   USB Keyboard: Applying InputClass "evdev keyboard catchall"
(**)   USB Keyboard: always reports core events
(**)   USB Keyboard: Device: "/dev/input/event4"
(II)   USB Keyboard: Found keys
(II)   USB Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "  USB Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device   USB Keyboard (/dev/input/event5)
(**)   USB Keyboard: Applying InputClass "evdev keyboard catchall"
(**)   USB Keyboard: always reports core events
(**)   USB Keyboard: Device: "/dev/input/event5"
(II)   USB Keyboard: Found keys
(II)   USB Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "  USB Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event6)
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
```

---

### Post by adaptive on 2010-05-04
I tried to use the utility to uninstall [then reinstall] the nvidia driver. When I uninstalled the nvidia driver, and just used the nv driver - GLX worked. Then I reinstalled nvidia's proprietary driver, restarted, and it broke again. 

Does this tell you anything?

---

### Post by GSF1200S on 2010-05-04
> **adaptive said:**
> I tried to use the utility to uninstall [then reinstall] the nvidia driver. When I uninstalled the nvidia driver, and just used the nv driver - GLX worked. Then I reinstalled nvidia's proprietary driver, restarted, and it broke again. 

Does this tell you anything?

Everything looks fine to me in Xorg.0.log- it seems like GLX is initializing. Perhaps someone else will come along who can help. The only thing further I can suggest is to grab the Nvidia driver from Nvidias site and try to install it. It requires you killing X and working from the command line (3 or 4 commands) and then restarting X. If you get that to work, I would reason that GLX should work just fine. If you do this, I would delete (but backup) your xorg.conf and start from scratch. The only disadvantage to this method is that you will need to reinstall the driver when a new kernel comes out. Thats not too often though..

If you have an old kernel lying around, you could try booting that.. Good luck man- seems some people are having a tough start with 10.04 (works great for me and others though) so hang in there.

---

### Post by adaptive on 2010-05-04
Thanks for the reassurance. 

Can you help me figure out one thing? Why would it work for my laptop and not for my desktop? Could it be because of different graphics cards? 

If no one chimes in with the end-all solution, I will go ahead and reinstall the binary from nvidia's site. 

Thanks.

---

