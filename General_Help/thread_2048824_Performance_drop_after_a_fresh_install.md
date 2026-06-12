---
title: "Performance drop after a fresh install"
date: 2012-08-27
forum: General Help
---

### Post by Tornikee on 2012-08-27
Hello, I've been running 12.04 since its release and never experienced any issues w/ performance, although, after a fresh install yesterday, the overall performance has dropped, and this is especially apparent w/ multimedia apps like gThumb and Rhythmbox - some of their operations (like going from single picture view to browse view in gThumb), as well as switching windows to/from them takes much longer (like 3-4 seconds) than it used to. This has been happening w/ both Unity and GNOME Classic (with no effects) sessions.

This is all happening w/ Ubuntu 12.04 64-bit.

---

### Post by Rexilion on 2012-08-27
You had a recent kernel update? Also check the terminal program 'top' for processes hogging the CPU.

---

### Post by Tornikee on 2012-08-27
Thanks for the reply.

Don't think I had any kernel updates recently. And this is what the 'top' program shows regarding CPU usage:

[img]https://lh6.googleusercontent.com/-bSLOBKXI3io/UDuZrfSFLII/AAAAAAAAfto/3BZmu_44hWI/s0/Screenshot%2520from%25202012-08-27%252019%253A59%253A07.png[/img]

---

### Post by Rexilion on 2012-08-27
Why did you do the fresh install? Do you know what kernel the old install was running? (if the old install was fully updated then you don't have to know the answer).

Provide the output of

```
cat /var/log/Xorg.0.log
```

please.

---

### Post by Tornikee on 2012-08-28
> **Rexilion said:**
> Why did you do the fresh install?
I was having trouble w/ removing an app/plugin source. I couldn't even access Software Sources via Software Center, encountering error messages while trying to open the latter.
> **Rexilion said:**
> Do you know what kernel the old install was running? (if the old install was fully updated then you don't have to know the answer).
No idea. The install was full (=erased the OS and installed it from scratch), so probably the old install was updated fully?

> **Rexilion said:**
> Provide the output of

```
cat /var/log/Xorg.0.log
```

please.

```
tornike@TornikeLinux:~$ cat /var/log/Xorg.0.log
[    10.394] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    10.394] X Protocol Version 11, Revision 0
[    10.394] Build Operating System: Linux 2.6.42-26-generic x86_64 Ubuntu
[    10.394] Current Operating System: Linux TornikeLinux 3.2.0-29-generic #46-Ubuntu SMP Fri Jul 27 17:03:23 UTC 2012 x86_64
[    10.394] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-29-generic root=UUID=13154744-cc6e-4798-9db4-77ee87a8f163 ro quiet splash vt.handoff=7
[    10.394] Build Date: 04 August 2012  01:51:23AM
[    10.394] xorg-server 2:1.11.4-0ubuntu10.7 (For technical support please see http://www.ubuntu.com/support) 
[    10.394] Current version of pixman: 0.24.4
[    10.394] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    10.394] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    10.394] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Aug 28 11:44:49 2012
[    10.394] (==) Using config file: "/etc/X11/xorg.conf"
[    10.394] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    10.394] (==) No Layout section.  Using the first Screen section.
[    10.394] (==) No screen section available. Using defaults.
[    10.394] (**) |-->Screen "Default Screen Section" (0)
[    10.394] (**) |   |-->Monitor "<default monitor>"
[    10.395] (==) No device specified for screen "Default Screen Section".
	Using the first device section listed.
[    10.395] (**) |   |-->Device "Default Device"
[    10.395] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    10.395] (==) Automatically adding devices
[    10.395] (==) Automatically enabling devices
[    10.395] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    10.395] 	Entry deleted from font path.
[    10.395] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    10.395] 	Entry deleted from font path.
[    10.395] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    10.395] 	Entry deleted from font path.
[    10.395] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    10.395] 	Entry deleted from font path.
[    10.395] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    10.395] 	Entry deleted from font path.
[    10.395] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    10.395] 	Entry deleted from font path.
[    10.395] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    10.395] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    10.395] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    10.395] (II) Loader magic: 0x7f250b2b5b00
[    10.395] (II) Module ABI versions:
[    10.395] 	X.Org ANSI C Emulation: 0.4
[    10.395] 	X.Org Video Driver: 11.0
[    10.395] 	X.Org XInput driver : 16.0
[    10.395] 	X.Org Server Extension : 6.0
[    10.395] (--) PCI:*(0:1:0:0) 10de:0640:1043:829a rev 161, Mem @ 0xfd000000/16777216, 0xe0000000/268435456, 0xfa000000/33554432, I/O @ 0x0000dc00/128, BIOS @ 0x????????/524288
[    10.398] (II) Open ACPI successful (/var/run/acpid.socket)
[    10.398] (II) LoadModule: "extmod"
[    10.399] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    10.399] (II) Module extmod: vendor="X.Org Foundation"
[    10.399] 	compiled for 1.11.3, module version = 1.0.0
[    10.399] 	Module class: X.Org Server Extension
[    10.399] 	ABI class: X.Org Server Extension, version 6.0
[    10.399] (II) Loading extension MIT-SCREEN-SAVER
[    10.399] (II) Loading extension XFree86-VidModeExtension
[    10.399] (II) Loading extension XFree86-DGA
[    10.399] (II) Loading extension DPMS
[    10.399] (II) Loading extension XVideo
[    10.399] (II) Loading extension XVideo-MotionCompensation
[    10.399] (II) Loading extension X-Resource
[    10.399] (II) LoadModule: "dbe"
[    10.399] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    10.399] (II) Module dbe: vendor="X.Org Foundation"
[    10.399] 	compiled for 1.11.3, module version = 1.0.0
[    10.399] 	Module class: X.Org Server Extension
[    10.399] 	ABI class: X.Org Server Extension, version 6.0
[    10.399] (II) Loading extension DOUBLE-BUFFER
[    10.399] (II) LoadModule: "glx"
[    10.399] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    11.391] (II) Module glx: vendor="NVIDIA Corporation"
[    11.391] 	compiled for 4.0.2, module version = 1.0.0
[    11.391] 	Module class: X.Org Server Extension
[    11.391] (II) NVIDIA GLX Module  295.40  Thu Apr  5 21:57:38 PDT 2012
[    11.391] (II) Loading extension GLX
[    11.391] (II) LoadModule: "record"
[    11.391] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    11.392] (II) Module record: vendor="X.Org Foundation"
[    11.392] 	compiled for 1.11.3, module version = 1.13.0
[    11.392] 	Module class: X.Org Server Extension
[    11.392] 	ABI class: X.Org Server Extension, version 6.0
[    11.392] (II) Loading extension RECORD
[    11.392] (II) LoadModule: "dri"
[    11.392] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    11.392] (II) Module dri: vendor="X.Org Foundation"
[    11.392] 	compiled for 1.11.3, module version = 1.0.0
[    11.392] 	ABI class: X.Org Server Extension, version 6.0
[    11.392] (II) Loading extension XFree86-DRI
[    11.392] (II) LoadModule: "dri2"
[    11.392] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    11.392] (II) Module dri2: vendor="X.Org Foundation"
[    11.392] 	compiled for 1.11.3, module version = 1.2.0
[    11.392] 	ABI class: X.Org Server Extension, version 6.0
[    11.392] (II) Loading extension DRI2
[    11.392] (==) Matched nvidia as autoconfigured driver 0
[    11.392] (==) Matched nouveau as autoconfigured driver 1
[    11.392] (==) Matched nv as autoconfigured driver 2
[    11.392] (==) Matched vesa as autoconfigured driver 3
[    11.392] (==) Matched fbdev as autoconfigured driver 4
[    11.392] (==) Assigned the driver to the xf86ConfigLayout
[    11.392] (II) LoadModule: "nvidia"
[    11.392] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    11.441] (II) Module nvidia: vendor="NVIDIA Corporation"
[    11.441] 	compiled for 4.0.2, module version = 1.0.0
[    11.441] 	Module class: X.Org Video Driver
[    11.456] (II) LoadModule: "nouveau"
[    11.457] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    11.457] (II) Module nouveau: vendor="X.Org Foundation"
[    11.457] 	compiled for 1.11.3, module version = 0.0.16
[    11.457] 	Module class: X.Org Video Driver
[    11.457] 	ABI class: X.Org Video Driver, version 11.0
[    11.457] (II) LoadModule: "nv"
[    11.472] (WW) Warning, couldn't open module nv
[    11.472] (II) UnloadModule: "nv"
[    11.472] (II) Unloading nv
[    11.472] (EE) Failed to load module "nv" (module does not exist, 0)
[    11.472] (II) LoadModule: "vesa"
[    11.473] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    11.473] (II) Module vesa: vendor="X.Org Foundation"
[    11.473] 	compiled for 1.11.3, module version = 2.3.0
[    11.473] 	Module class: X.Org Video Driver
[    11.473] 	ABI class: X.Org Video Driver, version 11.0
[    11.473] (II) LoadModule: "fbdev"
[    11.473] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    11.473] (II) Module fbdev: vendor="X.Org Foundation"
[    11.473] 	compiled for 1.11.3, module version = 0.4.2
[    11.473] 	ABI class: X.Org Video Driver, version 11.0
[    11.473] (==) Matched nvidia as autoconfigured driver 0
[    11.473] (==) Matched nouveau as autoconfigured driver 1
[    11.473] (==) Matched nv as autoconfigured driver 2
[    11.473] (==) Matched vesa as autoconfigured driver 3
[    11.473] (==) Matched fbdev as autoconfigured driver 4
[    11.473] (==) Assigned the driver to the xf86ConfigLayout
[    11.473] (II) LoadModule: "nvidia"
[    11.473] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    11.473] (II) Module nvidia: vendor="NVIDIA Corporation"
[    11.473] 	compiled for 4.0.2, module version = 1.0.0
[    11.473] 	Module class: X.Org Video Driver
[    11.473] (II) UnloadModule: "nvidia"
[    11.473] (II) Unloading nvidia
[    11.473] (II) Failed to load module "nvidia" (already loaded, 32549)
[    11.473] (II) LoadModule: "nouveau"
[    11.473] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    11.473] (II) Module nouveau: vendor="X.Org Foundation"
[    11.473] 	compiled for 1.11.3, module version = 0.0.16
[    11.473] 	Module class: X.Org Video Driver
[    11.473] 	ABI class: X.Org Video Driver, version 11.0
[    11.473] (II) UnloadModule: "nouveau"
[    11.473] (II) Unloading nouveau
[    11.473] (II) Failed to load module "nouveau" (already loaded, 32549)
[    11.473] (II) LoadModule: "nv"
[    11.474] (WW) Warning, couldn't open module nv
[    11.474] (II) UnloadModule: "nv"
[    11.474] (II) Unloading nv
[    11.474] (EE) Failed to load module "nv" (module does not exist, 0)
[    11.474] (II) LoadModule: "vesa"
[    11.474] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    11.474] (II) Module vesa: vendor="X.Org Foundation"
[    11.474] 	compiled for 1.11.3, module version = 2.3.0
[    11.474] 	Module class: X.Org Video Driver
[    11.474] 	ABI class: X.Org Video Driver, version 11.0
[    11.474] (II) UnloadModule: "vesa"
[    11.474] (II) Unloading vesa
[    11.474] (II) Failed to load module "vesa" (already loaded, 0)
[    11.474] (II) LoadModule: "fbdev"
[    11.474] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    11.474] (II) Module fbdev: vendor="X.Org Foundation"
[    11.474] 	compiled for 1.11.3, module version = 0.4.2
[    11.474] 	ABI class: X.Org Video Driver, version 11.0
[    11.474] (II) UnloadModule: "fbdev"
[    11.474] (II) Unloading fbdev
[    11.474] (II) Failed to load module "fbdev" (already loaded, 0)
[    11.474] (II) NVIDIA dlloader X Driver  295.40  Thu Apr  5 21:38:35 PDT 2012
[    11.474] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    11.490] (II) NOUVEAU driver Date:   Wed Nov 30 18:56:54 2011 +0100
[    11.490] (II) NOUVEAU driver for NVIDIA chipset families :
[    11.490] 	RIVA TNT        (NV04)
[    11.490] 	RIVA TNT2       (NV05)
[    11.490] 	GeForce 256     (NV10)
[    11.490] 	GeForce 2       (NV11, NV15)
[    11.490] 	GeForce 4MX     (NV17, NV18)
[    11.490] 	GeForce 3       (NV20)
[    11.490] 	GeForce 4Ti     (NV25, NV28)
[    11.490] 	GeForce FX      (NV3x)
[    11.490] 	GeForce 6       (NV4x)
[    11.490] 	GeForce 7       (G7x)
[    11.490] 	GeForce 8       (G8x)
[    11.490] 	GeForce GTX 200 (NVA0)
[    11.490] 	GeForce GTX 400 (NVC0)
[    11.490] (II) VESA: driver for VESA chipsets: vesa
[    11.490] (II) FBDEV: driver for framebuffer: fbdev
[    11.490] (++) using VT number 7

[    11.491] (II) Loading sub module "fb"
[    11.491] (II) LoadModule: "fb"
[    11.491] (II) Loading /usr/lib/xorg/modules/libfb.so
[    11.491] (II) Module fb: vendor="X.Org Foundation"
[    11.491] 	compiled for 1.11.3, module version = 1.0.0
[    11.491] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    11.491] (II) Loading sub module "wfb"
[    11.491] (II) LoadModule: "wfb"
[    11.492] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    11.492] (II) Module wfb: vendor="X.Org Foundation"
[    11.492] 	compiled for 1.11.3, module version = 1.0.0
[    11.492] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    11.492] (II) Loading sub module "ramdac"
[    11.492] (II) LoadModule: "ramdac"
[    11.492] (II) Module "ramdac" already built-in
[    11.493] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    11.493] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    11.493] (II) Loading /usr/lib/xorg/modules/libfb.so
[    11.493] (WW) Falling back to old probe method for vesa
[    11.493] (WW) Falling back to old probe method for fbdev
[    11.493] (II) Loading sub module "fbdevhw"
[    11.493] (II) LoadModule: "fbdevhw"
[    11.493] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    11.493] (II) Module fbdevhw: vendor="X.Org Foundation"
[    11.493] 	compiled for 1.11.3, module version = 0.0.2
[    11.493] 	ABI class: X.Org Video Driver, version 11.0
[    11.493] (II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    11.493] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    11.493] (==) NVIDIA(0): RGB weight 888
[    11.493] (==) NVIDIA(0): Default visual is TrueColor
[    11.493] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    11.493] (**) NVIDIA(0): Option "NoLogo" "True"
[    11.493] (**) NVIDIA(0): Enabling 2D acceleration
[    13.160] (II) NVIDIA(GPU-0): Display (Samsung SyncMaster (CRT-1)) does not support NVIDIA
[    13.160] (II) NVIDIA(GPU-0):     3D Vision stereo.
[    13.161] (II) NVIDIA(0): NVIDIA GPU GeForce 9500 GT (G96) at PCI:1:0:0 (GPU-0)
[    13.161] (--) NVIDIA(0): Memory: 1048576 kBytes
[    13.161] (--) NVIDIA(0): VideoBIOS: 62.94.4b.00.00
[    13.161] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    13.161] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    13.163] (--) NVIDIA(0): Connected display device(s) on GeForce 9500 GT at PCI:1:0:0
[    13.164] (--) NVIDIA(0):     Samsung SyncMaster (CRT-1)
[    13.164] (--) NVIDIA(0): Samsung SyncMaster (CRT-1): 400.0 MHz maximum pixel clock
[    13.198] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    13.198] (**) NVIDIA(0):     device Samsung SyncMaster (CRT-1) (Using EDID frequencies
[    13.198] (**) NVIDIA(0):     has been enabled on all display devices.)
[    13.210] (II) NVIDIA(0): Assigned Display Device: CRT-1
[    13.210] (==) NVIDIA(0): 
[    13.210] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    13.210] (==) NVIDIA(0):     will be used as the requested mode.
[    13.210] (==) NVIDIA(0): 
[    13.210] (II) NVIDIA(0): Validated modes:
[    13.210] (II) NVIDIA(0):     "nvidia-auto-select"
[    13.210] (II) NVIDIA(0): Virtual screen size determined to be 1680 x 1050
[    13.237] (--) NVIDIA(0): DPI set to (99, 98); computed from "UseEdidDpi" X config
[    13.237] (--) NVIDIA(0):     option
[    13.237] (II) UnloadModule: "nouveau"
[    13.237] (II) Unloading nouveau
[    13.237] (II) UnloadModule: "vesa"
[    13.237] (II) Unloading vesa
[    13.237] (II) UnloadModule: "fbdev"
[    13.237] (II) Unloading fbdev
[    13.237] (II) UnloadModule: "fbdevhw"
[    13.237] (II) Unloading fbdevhw
[    13.237] (--) Depth 24 pixmap format is 32 bpp
[    13.237] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    13.242] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    13.265] (II) Loading extension NV-GLX
[    13.301] (==) NVIDIA(0): Disabling shared memory pixmaps
[    13.301] (==) NVIDIA(0): Backing store disabled
[    13.301] (==) NVIDIA(0): Silken mouse enabled
[    13.302] (==) NVIDIA(0): DPMS enabled
[    13.302] (II) Loading extension NV-CONTROL
[    13.302] (II) Loading extension XINERAMA
[    13.302] (II) Loading sub module "dri2"
[    13.302] (II) LoadModule: "dri2"
[    13.302] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    13.302] (II) Module dri2: vendor="X.Org Foundation"
[    13.302] 	compiled for 1.11.3, module version = 1.2.0
[    13.302] 	ABI class: X.Org Server Extension, version 6.0
[    13.302] (II) NVIDIA(0): [DRI2] Setup complete
[    13.302] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    13.302] (==) RandR enabled
[    13.302] (II) Initializing built-in extension Generic Event Extension
[    13.302] (II) Initializing built-in extension SHAPE
[    13.302] (II) Initializing built-in extension MIT-SHM
[    13.302] (II) Initializing built-in extension XInputExtension
[    13.302] (II) Initializing built-in extension XTEST
[    13.302] (II) Initializing built-in extension BIG-REQUESTS
[    13.302] (II) Initializing built-in extension SYNC
[    13.302] (II) Initializing built-in extension XKEYBOARD
[    13.302] (II) Initializing built-in extension XC-MISC
[    13.302] (II) Initializing built-in extension SECURITY
[    13.302] (II) Initializing built-in extension XINERAMA
[    13.302] (II) Initializing built-in extension XFIXES
[    13.302] (II) Initializing built-in extension RENDER
[    13.302] (II) Initializing built-in extension RANDR
[    13.302] (II) Initializing built-in extension COMPOSITE
[    13.302] (II) Initializing built-in extension DAMAGE
[    13.303] (II) Initializing extension GLX
[    13.402] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    13.404] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    13.404] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    13.404] (II) LoadModule: "evdev"
[    13.405] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.405] (II) Module evdev: vendor="X.Org Foundation"
[    13.405] 	compiled for 1.11.3, module version = 2.7.0
[    13.405] 	Module class: X.Org XInput Driver
[    13.405] 	ABI class: X.Org XInput driver, version 16.0
[    13.405] (II) Using input driver 'evdev' for 'Power Button'
[    13.405] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.405] (**) Power Button: always reports core events
[    13.405] (**) evdev: Power Button: Device: "/dev/input/event1"
[    13.405] (--) evdev: Power Button: Vendor 0 Product 0x1
[    13.405] (--) evdev: Power Button: Found keys
[    13.405] (II) evdev: Power Button: Configuring as keyboard
[    13.405] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    13.405] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    13.405] (**) Option "xkb_rules" "evdev"
[    13.405] (**) Option "xkb_model" "pc105"
[    13.405] (**) Option "xkb_layout" "us"
[    13.405] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    13.405] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    13.405] (II) Using input driver 'evdev' for 'Power Button'
[    13.405] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.406] (**) Power Button: always reports core events
[    13.406] (**) evdev: Power Button: Device: "/dev/input/event0"
[    13.406] (--) evdev: Power Button: Vendor 0 Product 0x1
[    13.406] (--) evdev: Power Button: Found keys
[    13.406] (II) evdev: Power Button: Configuring as keyboard
[    13.406] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    13.406] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    13.406] (**) Option "xkb_rules" "evdev"
[    13.406] (**) Option "xkb_model" "pc105"
[    13.406] (**) Option "xkb_layout" "us"
[    13.406] (II) config/udev: Adding input device HDA Intel Line-Out Surround (/dev/input/event10)
[    13.406] (II) No input driver specified, ignoring this device.
[    13.406] (II) This device may have been added with another device file.
[    13.406] (II) config/udev: Adding input device HDA Intel Line-Out Front (/dev/input/event11)
[    13.406] (II) No input driver specified, ignoring this device.
[    13.406] (II) This device may have been added with another device file.
[    13.406] (II) config/udev: Adding input device HDA Intel Line (/dev/input/event4)
[    13.406] (II) No input driver specified, ignoring this device.
[    13.406] (II) This device may have been added with another device file.
[    13.407] (II) config/udev: Adding input device HDA Intel Front Mic (/dev/input/event5)
[    13.407] (II) No input driver specified, ignoring this device.
[    13.407] (II) This device may have been added with another device file.
[    13.407] (II) config/udev: Adding input device HDA Intel Rear Mic (/dev/input/event6)
[    13.407] (II) No input driver specified, ignoring this device.
[    13.407] (II) This device may have been added with another device file.
[    13.407] (II) config/udev: Adding input device HDA Intel Front Headphone (/dev/input/event7)
[    13.407] (II) No input driver specified, ignoring this device.
[    13.407] (II) This device may have been added with another device file.
[    13.407] (II) config/udev: Adding input device HDA Intel Line-Out Side (/dev/input/event8)
[    13.407] (II) No input driver specified, ignoring this device.
[    13.407] (II) This device may have been added with another device file.
[    13.407] (II) config/udev: Adding input device HDA Intel Line-Out CLFE (/dev/input/event9)
[    13.407] (II) No input driver specified, ignoring this device.
[    13.407] (II) This device may have been added with another device file.
[    13.408] (II) config/udev: Adding input device Razer  Razer Abyssus (/dev/input/event3)
[    13.408] (**) Razer  Razer Abyssus: Applying InputClass "evdev pointer catchall"
[    13.408] (II) Using input driver 'evdev' for 'Razer  Razer Abyssus'
[    13.408] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.408] (**) Razer  Razer Abyssus: always reports core events
[    13.408] (**) evdev: Razer  Razer Abyssus: Device: "/dev/input/event3"
[    13.408] (--) evdev: Razer  Razer Abyssus: Vendor 0x1532 Product 0x1c
[    13.408] (--) evdev: Razer  Razer Abyssus: Found 11 mouse buttons
[    13.408] (--) evdev: Razer  Razer Abyssus: Found scroll wheel(s)
[    13.408] (--) evdev: Razer  Razer Abyssus: Found relative axes
[    13.408] (--) evdev: Razer  Razer Abyssus: Found x and y relative axes
[    13.408] (II) evdev: Razer  Razer Abyssus: Configuring as mouse
[    13.408] (II) evdev: Razer  Razer Abyssus: Adding scrollwheel support
[    13.408] (**) evdev: Razer  Razer Abyssus: YAxisMapping: buttons 4 and 5
[    13.408] (**) evdev: Razer  Razer Abyssus: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    13.408] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input3/event3"
[    13.408] (II) XINPUT: Adding extended input device "Razer  Razer Abyssus" (type: MOUSE, id 8)
[    13.408] (II) evdev: Razer  Razer Abyssus: initialized for relative axes.
[    13.408] (**) Razer  Razer Abyssus: (accel) keeping acceleration scheme 1
[    13.408] (**) Razer  Razer Abyssus: (accel) acceleration profile 0
[    13.408] (**) Razer  Razer Abyssus: (accel) acceleration factor: 2.000
[    13.408] (**) Razer  Razer Abyssus: (accel) acceleration threshold: 4
[    13.408] (II) config/udev: Adding input device Razer  Razer Abyssus (/dev/input/mouse0)
[    13.408] (II) No input driver specified, ignoring this device.
[    13.408] (II) This device may have been added with another device file.
[    13.409] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    13.409] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    13.409] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    13.409] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.409] (**) AT Translated Set 2 keyboard: always reports core events
[    13.409] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    13.409] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    13.409] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    13.409] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    13.409] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    13.409] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)
[    13.409] (**) Option "xkb_rules" "evdev"
[    13.409] (**) Option "xkb_model" "pc105"
[    13.409] (**) Option "xkb_layout" "us"
[    14.196] (II) NVIDIA(0): Setting mode "1680x1050_60_0"
[    20.350] (II) XKB: reuse xkmfile /var/lib/xkb/server-7F14526994F5FB82B7760356D55B746501573715.xkm
```

Here it is.

---

### Post by Tornikee on 2012-08-28
Surprisingly, the performance of both gThumb and Rhythmbox has improved to previous levels today. There were no system changes made by me from yesterday, so no idea why this happened.

---

### Post by Rexilion on 2012-08-29
Maybe you have dying hardware? Or is it only these specific applications?

---

### Post by Tornikee on 2012-08-29
I wouldn't suspect a hardware issue.
Not just these two apps, but performance in general was down.

---

