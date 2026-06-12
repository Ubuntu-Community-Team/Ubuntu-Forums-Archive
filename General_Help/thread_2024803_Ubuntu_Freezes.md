---
title: "Ubuntu Freezes"
date: 2012-07-14
forum: General Help
---

### Post by EnteRCup on 2012-07-14
Hi guys.
I just surf the web using Firefox, and sometimes (pretty often) Ubuntu just freezes.
I'm using Ubuntu 12.04 LTS 32bit and GNOME 3.
Here's the /var/log/Xorg.0.log:
```

[    16.512] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    16.512] X Protocol Version 11, Revision 0
[    16.512] Build Operating System: Linux 2.6.42-23-generic i686 Ubuntu
[    16.512] Current Operating System: Linux orel-MS-7522 3.2.0-26-generic-pae #41-Ubuntu SMP Thu Jun 14 16:45:14 UTC 2012 i686
[    16.512] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-26-generic-pae root=UUID=ea00d08f-7b3f-4dc7-913a-dd8e46798211 ro quiet splash vt.handoff=7
[    16.512] Build Date: 09 July 2012  11:32:18PM
[    16.512] xorg-server 2:1.11.4-0ubuntu10.5 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    16.512] Current version of pixman: 0.24.4
[    16.512]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    16.512] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    16.512] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Jul 14 12:55:38 2012
[    16.535] (==) Using config file: "/etc/X11/xorg.conf"
[    16.535] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    16.595] (==) No Layout section.  Using the first Screen section.
[    16.595] (==) No screen section available. Using defaults.
[    16.595] (**) |-->Screen "Default Screen Section" (0)
[    16.595] (**) |   |-->Monitor "<default monitor>"
[    16.627] (==) No device specified for screen "Default Screen Section".
    Using the first device section listed.
[    16.627] (**) |   |-->Device "Default Device"
[    16.627] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    16.627] (==) Automatically adding devices
[    16.627] (==) Automatically enabling devices
[    16.647] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    16.647]     Entry deleted from font path.
[    16.647] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    16.647]     Entry deleted from font path.
[    16.647] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    16.647]     Entry deleted from font path.
[    16.647] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    16.647]     Entry deleted from font path.
[    16.647] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    16.647]     Entry deleted from font path.
[    16.647] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    16.647]     Entry deleted from font path.
[    16.647] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    16.647] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    16.647] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    16.648] (II) Loader magic: 0xb77835a0
[    16.648] (II) Module ABI versions:
[    16.648]     X.Org ANSI C Emulation: 0.4
[    16.648]     X.Org Video Driver: 11.0
[    16.648]     X.Org XInput driver : 16.0
[    16.648]     X.Org Server Extension : 6.0
[    16.649] (--) PCI:*(0:2:0:0) 10de:0614:1acc:902b rev 162, Mem @ 0xfa000000/16777216, 0xd0000000/268435456, 0xf8000000/33554432, I/O @ 0x0000cc00/128, BIOS @ 0x????????/131072
[    16.649] (II) Open ACPI successful (/var/run/acpid.socket)
[    16.649] (II) LoadModule: "extmod"
[    16.680] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    16.696] (II) Module extmod: vendor="X.Org Foundation"
[    16.696]     compiled for 1.11.3, module version = 1.0.0
[    16.696]     Module class: X.Org Server Extension
[    16.696]     ABI class: X.Org Server Extension, version 6.0
[    16.696] (II) Loading extension MIT-SCREEN-SAVER
[    16.696] (II) Loading extension XFree86-VidModeExtension
[    16.696] (II) Loading extension XFree86-DGA
[    16.728] (II) Loading extension DPMS
[    16.728] (II) Loading extension XVideo
[    16.728] (II) Loading extension XVideo-MotionCompensation
[    16.728] (II) Loading extension X-Resource
[    16.728] (II) LoadModule: "dbe"
[    16.728] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    16.749] (II) Module dbe: vendor="X.Org Foundation"
[    16.749]     compiled for 1.11.3, module version = 1.0.0
[    16.749]     Module class: X.Org Server Extension
[    16.749]     ABI class: X.Org Server Extension, version 6.0
[    16.749] (II) Loading extension DOUBLE-BUFFER
[    16.749] (II) LoadModule: "glx"
[    16.749] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/libglx.so
[    17.479] (II) Module glx: vendor="NVIDIA Corporation"
[    17.479]     compiled for 4.0.2, module version = 1.0.0
[    17.479]     Module class: X.Org Server Extension
[    17.479] (II) NVIDIA GLX Module  295.40  Thu Apr  5 21:49:54 PDT 2012
[    17.479] (II) Loading extension GLX
[    17.479] (II) LoadModule: "record"
[    17.479] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    17.499] (II) Module record: vendor="X.Org Foundation"
[    17.499]     compiled for 1.11.3, module version = 1.13.0
[    17.499]     Module class: X.Org Server Extension
[    17.499]     ABI class: X.Org Server Extension, version 6.0
[    17.499] (II) Loading extension RECORD
[    17.499] (II) LoadModule: "dri"
[    17.499] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    17.500] (II) Module dri: vendor="X.Org Foundation"
[    17.500]     compiled for 1.11.3, module version = 1.0.0
[    17.500]     ABI class: X.Org Server Extension, version 6.0
[    17.500] (II) Loading extension XFree86-DRI
[    17.500] (II) LoadModule: "dri2"
[    17.501] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    17.501] (II) Module dri2: vendor="X.Org Foundation"
[    17.501]     compiled for 1.11.3, module version = 1.2.0
[    17.501]     ABI class: X.Org Server Extension, version 6.0
[    17.501] (II) Loading extension DRI2
[    17.501] (==) Matched nvidia as autoconfigured driver 0
[    17.501] (==) Matched nouveau as autoconfigured driver 1
[    17.501] (==) Matched nv as autoconfigured driver 2
[    17.501] (==) Matched vesa as autoconfigured driver 3
[    17.501] (==) Matched fbdev as autoconfigured driver 4
[    17.501] (==) Assigned the driver to the xf86ConfigLayout
[    17.501] (II) LoadModule: "nvidia"
[    17.501] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    17.555] (II) Module nvidia: vendor="NVIDIA Corporation"
[    17.555]     compiled for 4.0.2, module version = 1.0.0
[    17.555]     Module class: X.Org Video Driver
[    17.567] (II) LoadModule: "nouveau"
[    17.567] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    17.589] (II) Module nouveau: vendor="X.Org Foundation"
[    17.589]     compiled for 1.11.3, module version = 0.0.16
[    17.589]     Module class: X.Org Video Driver
[    17.589]     ABI class: X.Org Video Driver, version 11.0
[    17.589] (II) LoadModule: "nv"
[    17.590] (WW) Warning, couldn't open module nv
[    17.590] (II) UnloadModule: "nv"
[    17.590] (II) Unloading nv
[    17.590] (EE) Failed to load module "nv" (module does not exist, 0)
[    17.590] (II) LoadModule: "vesa"
[    17.590] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    17.598] (II) Module vesa: vendor="X.Org Foundation"
[    17.598]     compiled for 1.11.3, module version = 2.3.0
[    17.598]     Module class: X.Org Video Driver
[    17.598]     ABI class: X.Org Video Driver, version 11.0
[    17.598] (II) LoadModule: "fbdev"
[    17.598] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    17.602] (II) Module fbdev: vendor="X.Org Foundation"
[    17.602]     compiled for 1.11.3, module version = 0.4.2
[    17.602]     ABI class: X.Org Video Driver, version 11.0
[    17.602] (==) Matched nvidia as autoconfigured driver 0
[    17.602] (==) Matched nouveau as autoconfigured driver 1
[    17.602] (==) Matched nv as autoconfigured driver 2
[    17.602] (==) Matched vesa as autoconfigured driver 3
[    17.602] (==) Matched fbdev as autoconfigured driver 4
[    17.602] (==) Assigned the driver to the xf86ConfigLayout
[    17.602] (II) LoadModule: "nvidia"
[    17.602] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    17.602] (II) Module nvidia: vendor="NVIDIA Corporation"
[    17.602]     compiled for 4.0.2, module version = 1.0.0
[    17.602]     Module class: X.Org Video Driver
[    17.602] (II) UnloadModule: "nvidia"
[    17.603] (II) Unloading nvidia
[    17.603] (II) Failed to load module "nvidia" (already loaded, -1217095013)
[    17.603] (II) LoadModule: "nouveau"
[    17.603] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    17.603] (II) Module nouveau: vendor="X.Org Foundation"
[    17.603]     compiled for 1.11.3, module version = 0.0.16
[    17.603]     Module class: X.Org Video Driver
[    17.603]     ABI class: X.Org Video Driver, version 11.0
[    17.603] (II) UnloadModule: "nouveau"
[    17.603] (II) Unloading nouveau
[    17.603] (II) Failed to load module "nouveau" (already loaded, -1217095013)
[    17.603] (II) LoadModule: "nv"
[    17.603] (WW) Warning, couldn't open module nv
[    17.603] (II) UnloadModule: "nv"
[    17.603] (II) Unloading nv
[    17.603] (EE) Failed to load module "nv" (module does not exist, 0)
[    17.603] (II) LoadModule: "vesa"
[    17.603] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    17.603] (II) Module vesa: vendor="X.Org Foundation"
[    17.603]     compiled for 1.11.3, module version = 2.3.0
[    17.603]     Module class: X.Org Video Driver
[    17.603]     ABI class: X.Org Video Driver, version 11.0
[    17.603] (II) UnloadModule: "vesa"
[    17.603] (II) Unloading vesa
[    17.603] (II) Failed to load module "vesa" (already loaded, 0)
[    17.603] (II) LoadModule: "fbdev"
[    17.603] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    17.603] (II) Module fbdev: vendor="X.Org Foundation"
[    17.603]     compiled for 1.11.3, module version = 0.4.2
[    17.603]     ABI class: X.Org Video Driver, version 11.0
[    17.603] (II) UnloadModule: "fbdev"
[    17.603] (II) Unloading fbdev
[    17.603] (II) Failed to load module "fbdev" (already loaded, 0)
[    17.604] (II) NVIDIA dlloader X Driver  295.40  Thu Apr  5 21:29:50 PDT 2012
[    17.604] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    17.625] (II) NOUVEAU driver Date:   Wed Nov 30 18:56:54 2011 +0100
[    17.625] (II) NOUVEAU driver for NVIDIA chipset families :
[    17.625]     RIVA TNT        (NV04)
[    17.625]     RIVA TNT2       (NV05)
[    17.625]     GeForce 256     (NV10)
[    17.625]     GeForce 2       (NV11, NV15)
[    17.625]     GeForce 4MX     (NV17, NV18)
[    17.625]     GeForce 3       (NV20)
[    17.625]     GeForce 4Ti     (NV25, NV28)
[    17.625]     GeForce FX      (NV3x)
[    17.625]     GeForce 6       (NV4x)
[    17.625]     GeForce 7       (G7x)
[    17.625]     GeForce 8       (G8x)
[    17.625]     GeForce GTX 200 (NVA0)
[    17.625]     GeForce GTX 400 (NVC0)
[    17.625] (II) VESA: driver for VESA chipsets: vesa
[    17.625] (II) FBDEV: driver for framebuffer: fbdev
[    17.625] (++) using VT number 7

[    17.626] (II) Loading sub module "fb"
[    17.626] (II) LoadModule: "fb"
[    17.626] (II) Loading /usr/lib/xorg/modules/libfb.so
[    17.635] (II) Module fb: vendor="X.Org Foundation"
[    17.635]     compiled for 1.11.3, module version = 1.0.0
[    17.635]     ABI class: X.Org ANSI C Emulation, version 0.4
[    17.635] (II) Loading sub module "wfb"
[    17.635] (II) LoadModule: "wfb"
[    17.635] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    17.640] (II) Module wfb: vendor="X.Org Foundation"
[    17.640]     compiled for 1.11.3, module version = 1.0.0
[    17.640]     ABI class: X.Org ANSI C Emulation, version 0.4
[    17.640] (II) Loading sub module "ramdac"
[    17.640] (II) LoadModule: "ramdac"
[    17.640] (II) Module "ramdac" already built-in
[    17.641] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    17.641] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    17.641] (II) Loading /usr/lib/xorg/modules/libfb.so
[    17.653] (WW) Falling back to old probe method for vesa
[    17.653] (WW) Falling back to old probe method for fbdev
[    17.653] (II) Loading sub module "fbdevhw"
[    17.653] (II) LoadModule: "fbdevhw"
[    17.653] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    17.674] (II) Module fbdevhw: vendor="X.Org Foundation"
[    17.674]     compiled for 1.11.3, module version = 0.0.2
[    17.674]     ABI class: X.Org Video Driver, version 11.0
[    17.674] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    17.674] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    17.674] (==) NVIDIA(0): RGB weight 888
[    17.674] (==) NVIDIA(0): Default visual is TrueColor
[    17.674] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    17.675] (**) NVIDIA(0): Option "NoLogo" "True"
[    17.675] (**) NVIDIA(0): Enabling 2D acceleration
[    19.212] (II) NVIDIA(GPU-0): Display (HKC (CRT-1)) does not support NVIDIA 3D Vision
[    19.212] (II) NVIDIA(GPU-0):     stereo.
[    19.223] (II) NVIDIA(0): NVIDIA GPU GeForce 9800 GT (G92) at PCI:2:0:0 (GPU-0)
[    19.223] (--) NVIDIA(0): Memory: 524288 kBytes
[    19.223] (--) NVIDIA(0): VideoBIOS: 62.92.56.00.1a
[    19.223] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    19.223] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    19.234] (--) NVIDIA(0): Connected display device(s) on GeForce 9800 GT at PCI:2:0:0
[    19.234] (--) NVIDIA(0):     HKC (CRT-1)
[    19.234] (--) NVIDIA(0): HKC (CRT-1): 400.0 MHz maximum pixel clock
[    19.271] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    19.271] (**) NVIDIA(0):     device HKC (CRT-1) (Using EDID frequencies has been
[    19.271] (**) NVIDIA(0):     enabled on all display devices.)
[    19.284] (II) NVIDIA(0): Assigned Display Device: CRT-1
[    19.284] (==) NVIDIA(0): 
[    19.284] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    19.284] (==) NVIDIA(0):     will be used as the requested mode.
[    19.284] (==) NVIDIA(0): 
[    19.284] (II) NVIDIA(0): Validated modes:
[    19.284] (II) NVIDIA(0):     "nvidia-auto-select"
[    19.284] (II) NVIDIA(0): Virtual screen size determined to be 1680 x 1050
[    19.314] (--) NVIDIA(0): DPI set to (99, 98); computed from "UseEdidDpi" X config
[    19.314] (--) NVIDIA(0):     option
[    19.314] (II) UnloadModule: "nouveau"
[    19.314] (II) Unloading nouveau
[    19.314] (II) UnloadModule: "vesa"
[    19.314] (II) Unloading vesa
[    19.314] (II) UnloadModule: "fbdev"
[    19.314] (II) Unloading fbdev
[    19.314] (II) UnloadModule: "fbdevhw"
[    19.314] (II) Unloading fbdevhw
[    19.314] (--) Depth 24 pixmap format is 32 bpp
[    19.314] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    19.332] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    19.355] (II) Loading extension NV-GLX
[    19.397] (==) NVIDIA(0): Disabling shared memory pixmaps
[    19.397] (==) NVIDIA(0): Backing store disabled
[    19.397] (==) NVIDIA(0): Silken mouse enabled
[    19.398] (==) NVIDIA(0): DPMS enabled
[    19.398] (II) Loading extension NV-CONTROL
[    19.398] (II) Loading extension XINERAMA
[    19.398] (II) Loading sub module "dri2"
[    19.398] (II) LoadModule: "dri2"
[    19.398] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    19.398] (II) Module dri2: vendor="X.Org Foundation"
[    19.398]     compiled for 1.11.3, module version = 1.2.0
[    19.398]     ABI class: X.Org Server Extension, version 6.0
[    19.398] (II) NVIDIA(0): [DRI2] Setup complete
[    19.398] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    19.398] (==) RandR enabled
[    19.398] (II) Initializing built-in extension Generic Event Extension
[    19.398] (II) Initializing built-in extension SHAPE
[    19.398] (II) Initializing built-in extension MIT-SHM
[    19.398] (II) Initializing built-in extension XInputExtension
[    19.398] (II) Initializing built-in extension XTEST
[    19.398] (II) Initializing built-in extension BIG-REQUESTS
[    19.398] (II) Initializing built-in extension SYNC
[    19.398] (II) Initializing built-in extension XKEYBOARD
[    19.398] (II) Initializing built-in extension XC-MISC
[    19.398] (II) Initializing built-in extension SECURITY
[    19.398] (II) Initializing built-in extension XINERAMA
[    19.398] (II) Initializing built-in extension XFIXES
[    19.398] (II) Initializing built-in extension RENDER
[    19.398] (II) Initializing built-in extension RANDR
[    19.398] (II) Initializing built-in extension COMPOSITE
[    19.398] (II) Initializing built-in extension DAMAGE
[    19.400] (II) Initializing extension GLX
[    19.489] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    19.496] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    19.496] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    19.496] (II) LoadModule: "evdev"
[    19.496] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.521] (II) Module evdev: vendor="X.Org Foundation"
[    19.521]     compiled for 1.11.3, module version = 2.7.0
[    19.521]     Module class: X.Org XInput Driver
[    19.521]     ABI class: X.Org XInput driver, version 16.0
[    19.521] (II) Using input driver 'evdev' for 'Power Button'
[    19.521] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.521] (**) Power Button: always reports core events
[    19.521] (**) evdev: Power Button: Device: "/dev/input/event1"
[    19.521] (--) evdev: Power Button: Vendor 0 Product 0x1
[    19.521] (--) evdev: Power Button: Found keys
[    19.521] (II) evdev: Power Button: Configuring as keyboard
[    19.521] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    19.521] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    19.521] (**) Option "xkb_rules" "evdev"
[    19.521] (**) Option "xkb_model" "pc105"
[    19.521] (**) Option "xkb_layout" "us,il"
[    19.521] (**) Option "xkb_variant" ","
[    19.521] (**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
[    19.523] (II) XKB: reuse xkmfile /var/lib/xkb/server-2CE46D2F8CCFAB6C1A4B498F695121C1147485D7.xkm
[    19.537] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    19.537] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    19.537] (II) Using input driver 'evdev' for 'Power Button'
[    19.537] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.537] (**) Power Button: always reports core events
[    19.537] (**) evdev: Power Button: Device: "/dev/input/event0"
[    19.537] (--) evdev: Power Button: Vendor 0 Product 0x1
[    19.537] (--) evdev: Power Button: Found keys
[    19.537] (II) evdev: Power Button: Configuring as keyboard
[    19.537] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    19.537] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    19.537] (**) Option "xkb_rules" "evdev"
[    19.537] (**) Option "xkb_model" "pc105"
[    19.537] (**) Option "xkb_layout" "us,il"
[    19.537] (**) Option "xkb_variant" ","
[    19.537] (**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
[    19.537] (II) config/udev: Adding input device Logitech USB Gaming Mouse (/dev/input/event2)
[    19.537] (**) Logitech USB Gaming Mouse: Applying InputClass "evdev pointer catchall"
[    19.537] (II) Using input driver 'evdev' for 'Logitech USB Gaming Mouse'
[    19.537] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.537] (**) Logitech USB Gaming Mouse: always reports core events
[    19.537] (**) evdev: Logitech USB Gaming Mouse: Device: "/dev/input/event2"
[    19.537] (--) evdev: Logitech USB Gaming Mouse: Vendor 0x46d Product 0xc041
[    19.537] (--) evdev: Logitech USB Gaming Mouse: Found 20 mouse buttons
[    19.537] (--) evdev: Logitech USB Gaming Mouse: Found scroll wheel(s)
[    19.537] (--) evdev: Logitech USB Gaming Mouse: Found relative axes
[    19.537] (--) evdev: Logitech USB Gaming Mouse: Found x and y relative axes
[    19.537] (II) evdev: Logitech USB Gaming Mouse: Configuring as mouse
[    19.537] (II) evdev: Logitech USB Gaming Mouse: Adding scrollwheel support
[    19.537] (**) evdev: Logitech USB Gaming Mouse: YAxisMapping: buttons 4 and 5
[    19.537] (**) evdev: Logitech USB Gaming Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    19.537] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0/input/input2/event2"
[    19.537] (II) XINPUT: Adding extended input device "Logitech USB Gaming Mouse" (type: MOUSE, id 8)
[    19.537] (II) evdev: Logitech USB Gaming Mouse: initialized for relative axes.
[    19.538] (**) Logitech USB Gaming Mouse: (accel) keeping acceleration scheme 1
[    19.538] (**) Logitech USB Gaming Mouse: (accel) acceleration profile 0
[    19.538] (**) Logitech USB Gaming Mouse: (accel) acceleration factor: 2.000
[    19.538] (**) Logitech USB Gaming Mouse: (accel) acceleration threshold: 4
[    19.538] (II) config/udev: Adding input device Logitech USB Gaming Mouse (/dev/input/mouse0)
[    19.538] (II) No input driver specified, ignoring this device.
[    19.538] (II) This device may have been added with another device file.
[    19.538] (II) config/udev: Adding input device Razer Razer BlackWidow (/dev/input/event3)
[    19.538] (**) Razer Razer BlackWidow: Applying InputClass "evdev keyboard catchall"
[    19.538] (II) Using input driver 'evdev' for 'Razer Razer BlackWidow'
[    19.538] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.538] (**) Razer Razer BlackWidow: always reports core events
[    19.538] (**) evdev: Razer Razer BlackWidow: Device: "/dev/input/event3"
[    19.538] (--) evdev: Razer Razer BlackWidow: Vendor 0x1532 Product 0x10e
[    19.538] (--) evdev: Razer Razer BlackWidow: Found keys
[    19.538] (II) evdev: Razer Razer BlackWidow: Configuring as keyboard
[    19.538] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.0/input/input3/event3"
[    19.538] (II) XINPUT: Adding extended input device "Razer Razer BlackWidow" (type: KEYBOARD, id 9)
[    19.538] (**) Option "xkb_rules" "evdev"
[    19.538] (**) Option "xkb_model" "pc105"
[    19.538] (**) Option "xkb_layout" "us,il"
[    19.538] (**) Option "xkb_variant" ","
[    19.538] (**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
[    19.539] (II) config/udev: Adding input device Razer Razer BlackWidow (/dev/input/event4)
[    19.539] (**) Razer Razer BlackWidow: Applying InputClass "evdev keyboard catchall"
[    19.539] (II) Using input driver 'evdev' for 'Razer Razer BlackWidow'
[    19.539] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.539] (**) Razer Razer BlackWidow: always reports core events
[    19.539] (**) evdev: Razer Razer BlackWidow: Device: "/dev/input/event4"
[    19.539] (--) evdev: Razer Razer BlackWidow: Vendor 0x1532 Product 0x10e
[    19.539] (--) evdev: Razer Razer BlackWidow: Found 1 mouse buttons
[    19.539] (--) evdev: Razer Razer BlackWidow: Found scroll wheel(s)
[    19.539] (--) evdev: Razer Razer BlackWidow: Found relative axes
[    19.539] (II) evdev: Razer Razer BlackWidow: Forcing relative x/y axes to exist.
[    19.539] (--) evdev: Razer Razer BlackWidow: Found absolute axes
[    19.539] (II) evdev: Razer Razer BlackWidow: Forcing absolute x/y axes to exist.
[    19.539] (--) evdev: Razer Razer BlackWidow: Found keys
[    19.539] (II) evdev: Razer Razer BlackWidow: Configuring as mouse
[    19.539] (II) evdev: Razer Razer BlackWidow: Configuring as keyboard
[    19.539] (II) evdev: Razer Razer BlackWidow: Adding scrollwheel support
[    19.539] (**) evdev: Razer Razer BlackWidow: YAxisMapping: buttons 4 and 5
[    19.539] (**) evdev: Razer Razer BlackWidow: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    19.539] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.1/input/input4/event4"
[    19.539] (II) XINPUT: Adding extended input device "Razer Razer BlackWidow" (type: KEYBOARD, id 10)
[    19.539] (**) Option "xkb_rules" "evdev"
[    19.539] (**) Option "xkb_model" "pc105"
[    19.539] (**) Option "xkb_layout" "us,il"
[    19.539] (**) Option "xkb_variant" ","
[    19.539] (**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
[    19.539] (II) evdev: Razer Razer BlackWidow: initialized for relative axes.
[    19.539] (WW) evdev: Razer Razer BlackWidow: ignoring absolute axes.
[    19.539] (**) Razer Razer BlackWidow: (accel) keeping acceleration scheme 1
[    19.539] (**) Razer Razer BlackWidow: (accel) acceleration profile 0
[    19.539] (**) Razer Razer BlackWidow: (accel) acceleration factor: 2.000
[    19.539] (**) Razer Razer BlackWidow: (accel) acceleration threshold: 4
[    19.540] (II) config/udev: Adding input device Razer Razer BlackWidow (/dev/input/event5)
[    19.540] (**) Razer Razer BlackWidow: Applying InputClass "evdev pointer catchall"
[    19.540] (II) Using input driver 'evdev' for 'Razer Razer BlackWidow'
[    19.540] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.540] (**) Razer Razer BlackWidow: always reports core events
[    19.540] (**) evdev: Razer Razer BlackWidow: Device: "/dev/input/event5"
[    19.540] (--) evdev: Razer Razer BlackWidow: Vendor 0x1532 Product 0x10e
[    19.540] (--) evdev: Razer Razer BlackWidow: Found 3 mouse buttons
[    19.540] (--) evdev: Razer Razer BlackWidow: Found scroll wheel(s)
[    19.540] (--) evdev: Razer Razer BlackWidow: Found relative axes
[    19.540] (--) evdev: Razer Razer BlackWidow: Found x and y relative axes
[    19.540] (II) evdev: Razer Razer BlackWidow: Configuring as mouse
[    19.540] (II) evdev: Razer Razer BlackWidow: Adding scrollwheel support
[    19.540] (**) evdev: Razer Razer BlackWidow: YAxisMapping: buttons 4 and 5
[    19.540] (**) evdev: Razer Razer BlackWidow: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    19.540] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.2/input/input5/event5"
[    19.540] (II) XINPUT: Adding extended input device "Razer Razer BlackWidow" (type: MOUSE, id 11)
[    19.540] (II) evdev: Razer Razer BlackWidow: initialized for relative axes.
[    19.540] (**) Razer Razer BlackWidow: (accel) keeping acceleration scheme 1
[    19.540] (**) Razer Razer BlackWidow: (accel) acceleration profile 0
[    19.540] (**) Razer Razer BlackWidow: (accel) acceleration factor: 2.000
[    19.540] (**) Razer Razer BlackWidow: (accel) acceleration threshold: 4
[    19.540] (II) config/udev: Adding input device Razer Razer BlackWidow (/dev/input/mouse1)
[    19.540] (II) No input driver specified, ignoring this device.
[    19.540] (II) This device may have been added with another device file.
[    19.541] (II) config/udev: Adding input device HDA Intel Line-Out Side (/dev/input/event10)
[    19.541] (II) No input driver specified, ignoring this device.
[    19.541] (II) This device may have been added with another device file.
[    19.541] (II) config/udev: Adding input device HDA Intel Line-Out CLFE (/dev/input/event11)
[    19.541] (II) No input driver specified, ignoring this device.
[    19.541] (II) This device may have been added with another device file.
[    19.541] (II) config/udev: Adding input device HDA Intel Line-Out Surround (/dev/input/event12)
[    19.541] (II) No input driver specified, ignoring this device.
[    19.541] (II) This device may have been added with another device file.
[    19.541] (II) config/udev: Adding input device HDA Intel Line-Out Front (/dev/input/event13)
[    19.541] (II) No input driver specified, ignoring this device.
[    19.541] (II) This device may have been added with another device file.
[    19.541] (II) config/udev: Adding input device HDA Intel Line (/dev/input/event6)
[    19.541] (II) No input driver specified, ignoring this device.
[    19.541] (II) This device may have been added with another device file.
[    19.542] (II) config/udev: Adding input device HDA Intel Front Mic (/dev/input/event7)
[    19.542] (II) No input driver specified, ignoring this device.
[    19.542] (II) This device may have been added with another device file.
[    19.542] (II) config/udev: Adding input device HDA Intel Rear Mic (/dev/input/event8)
[    19.542] (II) No input driver specified, ignoring this device.
[    19.542] (II) This device may have been added with another device file.
[    19.542] (II) config/udev: Adding input device HDA Intel Front Headphone (/dev/input/event9)
[    19.542] (II) No input driver specified, ignoring this device.
[    19.542] (II) This device may have been added with another device file.
[    33.961] (II) XKB: reuse xkmfile /var/lib/xkb/server-2DB0F716AAD6C7AD88AAAC376D12645FCDC3680E.xkm

```

Thanks!

---

### Post by Rexilion on 2012-07-14
I don't see anything that stands out. But I have some questions suggestions below.

I see you also have nouveau installed. Maybe delete the xorg driver and make sure that the nouveau kernel modules never get loaded?

Why is Xorg adding sound card 'ports' as input devices? :shock: Do you have some xorg.conf defined (somehwhere)?

---

### Post by Rexilion on 2012-07-14
Oops, double post...

---

