---
title: "Logs out automatically"
date: 2012-07-14
forum: General Help
---

### Post by EnteRCup on 2012-07-14
Hi!
Sometimes I just surf the web and my computer freezes and Ubuntu logs out automatically and then I need to log in again...
Why does it does that?
BTW If it matters, I'm using Ubuntu 12.04 LTS 32bit with GNOME 3.
Thanks.

---

### Post by Rexilion on 2012-07-14
Could be that something makes Xorg unhappy. When you log out and log back in, please provide:

/var/log/Xorg.0.log.old

---

### Post by EnteRCup on 2012-07-14
> **Rexilion said:**
> Could be that something makes Xorg unhappy. When you log out and log back in, please provide:

/var/log/Xorg.0.log.old
Actually, it happens when I watch YouTube videos...
If it'll happen again, I'll prove that log file. Thanks.

**UPDATE:  **It just logged out again, here's the file you asked:
> 
[  1192.752] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[  1192.752] X Protocol Version 11, Revision 0
[  1192.752] Build Operating System: Linux 2.6.42-23-generic i686 Ubuntu
[  1192.752] Current Operating System: Linux orel-MS-7522 3.2.0-26-generic-pae #41-Ubuntu SMP Thu Jun 14 16:45:14 UTC 2012 i686
[  1192.752] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-26-generic-pae root=UUID=ea00d08f-7b3f-4dc7-913a-dd8e46798211 ro quiet splash vt.handoff=7
[  1192.752] Build Date: 09 July 2012  11:32:18PM
[  1192.752] xorg-server 2:1.11.4-0ubuntu10.5 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[  1192.752] Current version of pixman: 0.24.4
[  1192.752]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[  1192.752] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  1192.752] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Jul 14 13:15:14 2012
[  1192.753] (==) Using config file: "/etc/X11/xorg.conf"
[  1192.753] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  1192.753] (==) No Layout section.  Using the first Screen section.
[  1192.753] (==) No screen section available. Using defaults.
[  1192.753] (**) |-->Screen "Default Screen Section" (0)
[  1192.753] (**) |   |-->Monitor "<default monitor>"
[  1192.753] (==) No device specified for screen "Default Screen Section".
    Using the first device section listed.
[  1192.753] (**) |   |-->Device "Default Device"
[  1192.753] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[  1192.753] (==) Automatically adding devices
[  1192.753] (==) Automatically enabling devices
[  1192.754] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  1192.754]     Entry deleted from font path.
[  1192.754] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[  1192.754]     Entry deleted from font path.
[  1192.754] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[  1192.754]     Entry deleted from font path.
[  1192.754] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[  1192.754]     Entry deleted from font path.
[  1192.754] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[  1192.754]     Entry deleted from font path.
[  1192.754] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[  1192.754]     Entry deleted from font path.
[  1192.754] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[  1192.754] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  1192.754] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[  1192.754] (II) Loader magic: 0xb77795a0
[  1192.754] (II) Module ABI versions:
[  1192.754]     X.Org ANSI C Emulation: 0.4
[  1192.754]     X.Org Video Driver: 11.0
[  1192.754]     X.Org XInput driver : 16.0
[  1192.754]     X.Org Server Extension : 6.0
[  1192.755] (--) PCI:*(0:2:0:0) 10de:0614:1acc:902b rev 162, Mem @ 0xfa000000/16777216, 0xd0000000/268435456, 0xf8000000/33554432, I/O @ 0x0000cc00/128, BIOS @ 0x????????/131072
[  1192.755] (II) Open ACPI successful (/var/run/acpid.socket)
[  1192.755] (II) LoadModule: "extmod"
[  1192.756] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[  1192.756] (II) Module extmod: vendor="X.Org Foundation"
[  1192.756]     compiled for 1.11.3, module version = 1.0.0
[  1192.756]     Module class: X.Org Server Extension
[  1192.756]     ABI class: X.Org Server Extension, version 6.0
[  1192.756] (II) Loading extension MIT-SCREEN-SAVER
[  1192.756] (II) Loading extension XFree86-VidModeExtension
[  1192.756] (II) Loading extension XFree86-DGA
[  1192.756] (II) Loading extension DPMS
[  1192.756] (II) Loading extension XVideo
[  1192.756] (II) Loading extension XVideo-MotionCompensation
[  1192.756] (II) Loading extension X-Resource
[  1192.756] (II) LoadModule: "dbe"
[  1192.756] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[  1192.756] (II) Module dbe: vendor="X.Org Foundation"
[  1192.756]     compiled for 1.11.3, module version = 1.0.0
[  1192.756]     Module class: X.Org Server Extension
[  1192.756]     ABI class: X.Org Server Extension, version 6.0
[  1192.756] (II) Loading extension DOUBLE-BUFFER
[  1192.756] (II) LoadModule: "glx"
[  1192.756] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/libglx.so
[  1192.772] (II) Module glx: vendor="NVIDIA Corporation"
[  1192.772]     compiled for 4.0.2, module version = 1.0.0
[  1192.772]     Module class: X.Org Server Extension
[  1192.772] (II) NVIDIA GLX Module  295.40  Thu Apr  5 21:49:54 PDT 2012
[  1192.772] (II) Loading extension GLX
[  1192.772] (II) LoadModule: "record"
[  1192.772] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[  1192.772] (II) Module record: vendor="X.Org Foundation"
[  1192.772]     compiled for 1.11.3, module version = 1.13.0
[  1192.772]     Module class: X.Org Server Extension
[  1192.772]     ABI class: X.Org Server Extension, version 6.0
[  1192.772] (II) Loading extension RECORD
[  1192.772] (II) LoadModule: "dri"
[  1192.772] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[  1192.773] (II) Module dri: vendor="X.Org Foundation"
[  1192.773]     compiled for 1.11.3, module version = 1.0.0
[  1192.773]     ABI class: X.Org Server Extension, version 6.0
[  1192.773] (II) Loading extension XFree86-DRI
[  1192.773] (II) LoadModule: "dri2"
[  1192.773] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[  1192.773] (II) Module dri2: vendor="X.Org Foundation"
[  1192.773]     compiled for 1.11.3, module version = 1.2.0
[  1192.773]     ABI class: X.Org Server Extension, version 6.0
[  1192.773] (II) Loading extension DRI2
[  1192.773] (==) Matched nvidia as autoconfigured driver 0
[  1192.773] (==) Matched nouveau as autoconfigured driver 1
[  1192.773] (==) Matched nv as autoconfigured driver 2
[  1192.773] (==) Matched vesa as autoconfigured driver 3
[  1192.773] (==) Matched fbdev as autoconfigured driver 4
[  1192.773] (==) Assigned the driver to the xf86ConfigLayout
[  1192.773] (II) LoadModule: "nvidia"
[  1192.773] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[  1192.773] (II) Module nvidia: vendor="NVIDIA Corporation"
[  1192.773]     compiled for 4.0.2, module version = 1.0.0
[  1192.773]     Module class: X.Org Video Driver
[  1192.773] (II) LoadModule: "nouveau"
[  1192.774] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[  1192.774] (II) Module nouveau: vendor="X.Org Foundation"
[  1192.774]     compiled for 1.11.3, module version = 0.0.16
[  1192.774]     Module class: X.Org Video Driver
[  1192.774]     ABI class: X.Org Video Driver, version 11.0
[  1192.774] (II) LoadModule: "nv"
[  1192.774] (WW) Warning, couldn't open module nv
[  1192.774] (II) UnloadModule: "nv"
[  1192.774] (II) Unloading nv
[  1192.774] (EE) Failed to load module "nv" (module does not exist, 0)
[  1192.774] (II) LoadModule: "vesa"
[  1192.774] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  1192.774] (II) Module vesa: vendor="X.Org Foundation"
[  1192.774]     compiled for 1.11.3, module version = 2.3.0
[  1192.774]     Module class: X.Org Video Driver
[  1192.774]     ABI class: X.Org Video Driver, version 11.0
[  1192.774] (II) LoadModule: "fbdev"
[  1192.775] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  1192.775] (II) Module fbdev: vendor="X.Org Foundation"
[  1192.775]     compiled for 1.11.3, module version = 0.4.2
[  1192.775]     ABI class: X.Org Video Driver, version 11.0
[  1192.775] (==) Matched nvidia as autoconfigured driver 0
[  1192.775] (==) Matched nouveau as autoconfigured driver 1
[  1192.775] (==) Matched nv as autoconfigured driver 2
[  1192.775] (==) Matched vesa as autoconfigured driver 3
[  1192.775] (==) Matched fbdev as autoconfigured driver 4
[  1192.775] (==) Assigned the driver to the xf86ConfigLayout
[  1192.775] (II) LoadModule: "nvidia"
[  1192.775] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[  1192.775] (II) Module nvidia: vendor="NVIDIA Corporation"
[  1192.775]     compiled for 4.0.2, module version = 1.0.0
[  1192.775]     Module class: X.Org Video Driver
[  1192.775] (II) UnloadModule: "nvidia"
[  1192.775] (II) Unloading nvidia
[  1192.775] (II) Failed to load module "nvidia" (already loaded, -1217135973)
[  1192.775] (II) LoadModule: "nouveau"
[  1192.775] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[  1192.775] (II) Module nouveau: vendor="X.Org Foundation"
[  1192.775]     compiled for 1.11.3, module version = 0.0.16
[  1192.775]     Module class: X.Org Video Driver
[  1192.775]     ABI class: X.Org Video Driver, version 11.0
[  1192.775] (II) UnloadModule: "nouveau"
[  1192.775] (II) Unloading nouveau
[  1192.775] (II) Failed to load module "nouveau" (already loaded, -1217135973)
[  1192.775] (II) LoadModule: "nv"
[  1192.775] (WW) Warning, couldn't open module nv
[  1192.775] (II) UnloadModule: "nv"
[  1192.775] (II) Unloading nv
[  1192.775] (EE) Failed to load module "nv" (module does not exist, 0)
[  1192.775] (II) LoadModule: "vesa"
[  1192.776] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  1192.776] (II) Module vesa: vendor="X.Org Foundation"
[  1192.776]     compiled for 1.11.3, module version = 2.3.0
[  1192.776]     Module class: X.Org Video Driver
[  1192.776]     ABI class: X.Org Video Driver, version 11.0
[  1192.776] (II) UnloadModule: "vesa"
[  1192.776] (II) Unloading vesa
[  1192.776] (II) Failed to load module "vesa" (already loaded, 0)
[  1192.776] (II) LoadModule: "fbdev"
[  1192.776] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  1192.776] (II) Module fbdev: vendor="X.Org Foundation"
[  1192.776]     compiled for 1.11.3, module version = 0.4.2
[  1192.776]     ABI class: X.Org Video Driver, version 11.0
[  1192.776] (II) UnloadModule: "fbdev"
[  1192.776] (II) Unloading fbdev
[  1192.776] (II) Failed to load module "fbdev" (already loaded, 0)
[  1192.776] (II) NVIDIA dlloader X Driver  295.40  Thu Apr  5 21:29:50 PDT 2012
[  1192.776] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[  1192.776] (II) NOUVEAU driver Date:   Wed Nov 30 18:56:54 2011 +0100
[  1192.776] (II) NOUVEAU driver for NVIDIA chipset families :
[  1192.776]     RIVA TNT        (NV04)
[  1192.776]     RIVA TNT2       (NV05)
[  1192.776]     GeForce 256     (NV10)
[  1192.776]     GeForce 2       (NV11, NV15)
[  1192.776]     GeForce 4MX     (NV17, NV18)
[  1192.776]     GeForce 3       (NV20)
[  1192.776]     GeForce 4Ti     (NV25, NV28)
[  1192.776]     GeForce FX      (NV3x)
[  1192.776]     GeForce 6       (NV4x)
[  1192.776]     GeForce 7       (G7x)
[  1192.776]     GeForce 8       (G8x)
[  1192.776]     GeForce GTX 200 (NVA0)
[  1192.776]     GeForce GTX 400 (NVC0)
[  1192.776] (II) VESA: driver for VESA chipsets: vesa
[  1192.776] (II) FBDEV: driver for framebuffer: fbdev
[  1192.776] (++) using VT number 7

[  1192.776] (II) Loading sub module "fb"
[  1192.776] (II) LoadModule: "fb"
[  1192.776] (II) Loading /usr/lib/xorg/modules/libfb.so
[  1192.776] (II) Module fb: vendor="X.Org Foundation"
[  1192.776]     compiled for 1.11.3, module version = 1.0.0
[  1192.776]     ABI class: X.Org ANSI C Emulation, version 0.4
[  1192.776] (II) Loading sub module "wfb"
[  1192.776] (II) LoadModule: "wfb"
[  1192.777] (II) Loading /usr/lib/xorg/modules/libwfb.so
[  1192.777] (II) Module wfb: vendor="X.Org Foundation"
[  1192.777]     compiled for 1.11.3, module version = 1.0.0
[  1192.777]     ABI class: X.Org ANSI C Emulation, version 0.4
[  1192.777] (II) Loading sub module "ramdac"
[  1192.777] (II) LoadModule: "ramdac"
[  1192.777] (II) Module "ramdac" already built-in
[  1192.777] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[  1192.777] (II) Loading /usr/lib/xorg/modules/libwfb.so
[  1192.777] (II) Loading /usr/lib/xorg/modules/libfb.so
[  1192.777] (WW) Falling back to old probe method for vesa
[  1192.777] (WW) Falling back to old probe method for fbdev
[  1192.777] (II) Loading sub module "fbdevhw"
[  1192.777] (II) LoadModule: "fbdevhw"
[  1192.777] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[  1192.777] (II) Module fbdevhw: vendor="X.Org Foundation"
[  1192.777]     compiled for 1.11.3, module version = 0.0.2
[  1192.777]     ABI class: X.Org Video Driver, version 11.0
[  1192.777] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[  1192.777] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[  1192.777] (==) NVIDIA(0): RGB weight 888
[  1192.777] (==) NVIDIA(0): Default visual is TrueColor
[  1192.777] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[  1192.777] (**) NVIDIA(0): Option "NoLogo" "True"
[  1192.777] (**) NVIDIA(0): Enabling 2D acceleration
[  1193.855] (II) NVIDIA(GPU-0): Display (HKC (CRT-1)) does not support NVIDIA 3D Vision
[  1193.855] (II) NVIDIA(GPU-0):     stereo.
[  1193.858] (II) NVIDIA(0): NVIDIA GPU GeForce 9800 GT (G92) at PCI:2:0:0 (GPU-0)
[  1193.858] (--) NVIDIA(0): Memory: 524288 kBytes
[  1193.858] (--) NVIDIA(0): VideoBIOS: 62.92.56.00.1a
[  1193.858] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[  1193.858] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[  1193.868] (--) NVIDIA(0): Connected display device(s) on GeForce 9800 GT at PCI:2:0:0
[  1193.868] (--) NVIDIA(0):     HKC (CRT-1)
[  1193.868] (--) NVIDIA(0): HKC (CRT-1): 400.0 MHz maximum pixel clock
[  1193.937] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[  1193.937] (**) NVIDIA(0):     device HKC (CRT-1) (Using EDID frequencies has been
[  1193.937] (**) NVIDIA(0):     enabled on all display devices.)
[  1193.953] (II) NVIDIA(0): Assigned Display Device: CRT-1
[  1193.953] (==) NVIDIA(0): 
[  1193.953] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[  1193.953] (==) NVIDIA(0):     will be used as the requested mode.
[  1193.953] (==) NVIDIA(0): 
[  1193.953] (II) NVIDIA(0): Validated modes:
[  1193.953] (II) NVIDIA(0):     "nvidia-auto-select"
[  1193.953] (II) NVIDIA(0): Virtual screen size determined to be 1680 x 1050
[  1193.964] (--) NVIDIA(0): DPI set to (99, 98); computed from "UseEdidDpi" X config
[  1193.964] (--) NVIDIA(0):     option
[  1193.964] (II) UnloadModule: "nouveau"
[  1193.964] (II) Unloading nouveau
[  1193.964] (II) UnloadModule: "vesa"
[  1193.964] (II) Unloading vesa
[  1193.964] (II) UnloadModule: "fbdev"
[  1193.964] (II) Unloading fbdev
[  1193.964] (II) UnloadModule: "fbdevhw"
[  1193.964] (II) Unloading fbdevhw
[  1193.964] (--) Depth 24 pixmap format is 32 bpp
[  1193.964] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[  1193.980] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[  1194.002] (II) Loading extension NV-GLX
[  1194.035] (==) NVIDIA(0): Disabling shared memory pixmaps
[  1194.035] (==) NVIDIA(0): Backing store disabled
[  1194.035] (==) NVIDIA(0): Silken mouse enabled
[  1194.035] (==) NVIDIA(0): DPMS enabled
[  1194.035] (II) Loading extension NV-CONTROL
[  1194.036] (II) Loading extension XINERAMA
[  1194.036] (II) Loading sub module "dri2"
[  1194.036] (II) LoadModule: "dri2"
[  1194.036] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[  1194.036] (II) Module dri2: vendor="X.Org Foundation"
[  1194.036]     compiled for 1.11.3, module version = 1.2.0
[  1194.036]     ABI class: X.Org Server Extension, version 6.0
[  1194.036] (II) NVIDIA(0): [DRI2] Setup complete
[  1194.036] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[  1194.036] (==) RandR enabled
[  1194.036] (II) Initializing built-in extension Generic Event Extension
[  1194.036] (II) Initializing built-in extension SHAPE
[  1194.036] (II) Initializing built-in extension MIT-SHM
[  1194.036] (II) Initializing built-in extension XInputExtension
[  1194.036] (II) Initializing built-in extension XTEST
[  1194.036] (II) Initializing built-in extension BIG-REQUESTS
[  1194.036] (II) Initializing built-in extension SYNC
[  1194.036] (II) Initializing built-in extension XKEYBOARD
[  1194.036] (II) Initializing built-in extension XC-MISC
[  1194.036] (II) Initializing built-in extension SECURITY
[  1194.036] (II) Initializing built-in extension XINERAMA
[  1194.036] (II) Initializing built-in extension XFIXES
[  1194.036] (II) Initializing built-in extension RENDER
[  1194.036] (II) Initializing built-in extension RANDR
[  1194.036] (II) Initializing built-in extension COMPOSITE
[  1194.036] (II) Initializing built-in extension DAMAGE
[  1194.038] (II) Initializing extension GLX
[  1194.058] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  1194.060] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[  1194.060] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  1194.060] (II) LoadModule: "evdev"
[  1194.060] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1194.060] (II) Module evdev: vendor="X.Org Foundation"
[  1194.060]     compiled for 1.11.3, module version = 2.7.0
[  1194.060]     Module class: X.Org XInput Driver
[  1194.060]     ABI class: X.Org XInput driver, version 16.0
[  1194.060] (II) Using input driver 'evdev' for 'Power Button'
[  1194.060] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1194.061] (**) Power Button: always reports core events
[  1194.061] (**) evdev: Power Button: Device: "/dev/input/event1"
[  1194.061] (--) evdev: Power Button: Vendor 0 Product 0x1
[  1194.061] (--) evdev: Power Button: Found keys
[  1194.061] (II) evdev: Power Button: Configuring as keyboard
[  1194.061] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[  1194.061] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[  1194.061] (**) Option "xkb_rules" "evdev"
[  1194.061] (**) Option "xkb_model" "pc105"
[  1194.061] (**) Option "xkb_layout" "us,il"
[  1194.061] (**) Option "xkb_variant" ","
[  1194.061] (**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
[  1194.063] (II) XKB: reuse xkmfile /var/lib/xkb/server-2CE46D2F8CCFAB6C1A4B498F695121C1147485D7.xkm
[  1194.063] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[  1194.063] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  1194.063] (II) Using input driver 'evdev' for 'Power Button'
[  1194.063] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1194.063] (**) Power Button: always reports core events
[  1194.063] (**) evdev: Power Button: Device: "/dev/input/event0"
[  1194.063] (--) evdev: Power Button: Vendor 0 Product 0x1
[  1194.063] (--) evdev: Power Button: Found keys
[  1194.063] (II) evdev: Power Button: Configuring as keyboard
[  1194.063] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[  1194.063] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[  1194.063] (**) Option "xkb_rules" "evdev"
[  1194.063] (**) Option "xkb_model" "pc105"
[  1194.063] (**) Option "xkb_layout" "us,il"
[  1194.063] (**) Option "xkb_variant" ","
[  1194.063] (**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
[  1194.064] (II) config/udev: Adding input device Logitech USB Gaming Mouse (/dev/input/event2)
[  1194.064] (**) Logitech USB Gaming Mouse: Applying InputClass "evdev pointer catchall"
[  1194.064] (II) Using input driver 'evdev' for 'Logitech USB Gaming Mouse'
[  1194.064] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1194.064] (**) Logitech USB Gaming Mouse: always reports core events
[  1194.064] (**) evdev: Logitech USB Gaming Mouse: Device: "/dev/input/event2"
[  1194.064] (--) evdev: Logitech USB Gaming Mouse: Vendor 0x46d Product 0xc041
[  1194.064] (--) evdev: Logitech USB Gaming Mouse: Found 20 mouse buttons
[  1194.064] (--) evdev: Logitech USB Gaming Mouse: Found scroll wheel(s)
[  1194.064] (--) evdev: Logitech USB Gaming Mouse: Found relative axes
[  1194.064] (--) evdev: Logitech USB Gaming Mouse: Found x and y relative axes
[  1194.064] (II) evdev: Logitech USB Gaming Mouse: Configuring as mouse
[  1194.064] (II) evdev: Logitech USB Gaming Mouse: Adding scrollwheel support
[  1194.064] (**) evdev: Logitech USB Gaming Mouse: YAxisMapping: buttons 4 and 5
[  1194.064] (**) evdev: Logitech USB Gaming Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  1194.064] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0/input/input2/event2"
[  1194.064] (II) XINPUT: Adding extended input device "Logitech USB Gaming Mouse" (type: MOUSE, id 8)
[  1194.064] (II) evdev: Logitech USB Gaming Mouse: initialized for relative axes.
[  1194.064] (**) Logitech USB Gaming Mouse: (accel) keeping acceleration scheme 1
[  1194.064] (**) Logitech USB Gaming Mouse: (accel) acceleration profile 0
[  1194.064] (**) Logitech USB Gaming Mouse: (accel) acceleration factor: 2.000
[  1194.064] (**) Logitech USB Gaming Mouse: (accel) acceleration threshold: 4
[  1194.065] (II) config/udev: Adding input device Logitech USB Gaming Mouse (/dev/input/mouse0)
[  1194.065] (II) No input driver specified, ignoring this device.
[  1194.065] (II) This device may have been added with another device file.
[  1194.065] (II) config/udev: Adding input device Razer Razer BlackWidow (/dev/input/event3)
[  1194.065] (**) Razer Razer BlackWidow: Applying InputClass "evdev keyboard catchall"
[  1194.065] (II) Using input driver 'evdev' for 'Razer Razer BlackWidow'
[  1194.065] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1194.065] (**) Razer Razer BlackWidow: always reports core events
[  1194.065] (**) evdev: Razer Razer BlackWidow: Device: "/dev/input/event3"
[  1194.065] (--) evdev: Razer Razer BlackWidow: Vendor 0x1532 Product 0x10e
[  1194.065] (--) evdev: Razer Razer BlackWidow: Found keys
[  1194.065] (II) evdev: Razer Razer BlackWidow: Configuring as keyboard
[  1194.065] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.0/input/input3/event3"
[  1194.065] (II) XINPUT: Adding extended input device "Razer Razer BlackWidow" (type: KEYBOARD, id 9)
[  1194.065] (**) Option "xkb_rules" "evdev"
[  1194.065] (**) Option "xkb_model" "pc105"
[  1194.065] (**) Option "xkb_layout" "us,il"
[  1194.065] (**) Option "xkb_variant" ","
[  1194.065] (**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
[  1194.066] (II) config/udev: Adding input device Razer Razer BlackWidow (/dev/input/event4)
[  1194.066] (**) Razer Razer BlackWidow: Applying InputClass "evdev keyboard catchall"
[  1194.066] (II) Using input driver 'evdev' for 'Razer Razer BlackWidow'
[  1194.066] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1194.066] (**) Razer Razer BlackWidow: always reports core events
[  1194.066] (**) evdev: Razer Razer BlackWidow: Device: "/dev/input/event4"
[  1194.066] (--) evdev: Razer Razer BlackWidow: Vendor 0x1532 Product 0x10e
[  1194.066] (--) evdev: Razer Razer BlackWidow: Found 1 mouse buttons
[  1194.066] (--) evdev: Razer Razer BlackWidow: Found scroll wheel(s)
[  1194.066] (--) evdev: Razer Razer BlackWidow: Found relative axes
[  1194.066] (II) evdev: Razer Razer BlackWidow: Forcing relative x/y axes to exist.
[  1194.066] (--) evdev: Razer Razer BlackWidow: Found absolute axes
[  1194.066] (II) evdev: Razer Razer BlackWidow: Forcing absolute x/y axes to exist.
[  1194.066] (--) evdev: Razer Razer BlackWidow: Found keys
[  1194.066] (II) evdev: Razer Razer BlackWidow: Configuring as mouse
[  1194.066] (II) evdev: Razer Razer BlackWidow: Configuring as keyboard
[  1194.066] (II) evdev: Razer Razer BlackWidow: Adding scrollwheel support
[  1194.066] (**) evdev: Razer Razer BlackWidow: YAxisMapping: buttons 4 and 5
[  1194.066] (**) evdev: Razer Razer BlackWidow: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  1194.066] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.1/input/input4/event4"
[  1194.066] (II) XINPUT: Adding extended input device "Razer Razer BlackWidow" (type: KEYBOARD, id 10)
[  1194.066] (**) Option "xkb_rules" "evdev"
[  1194.066] (**) Option "xkb_model" "pc105"
[  1194.066] (**) Option "xkb_layout" "us,il"
[  1194.066] (**) Option "xkb_variant" ","
[  1194.066] (**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
[  1194.066] (II) evdev: Razer Razer BlackWidow: initialized for relative axes.
[  1194.066] (WW) evdev: Razer Razer BlackWidow: ignoring absolute axes.
[  1194.066] (**) Razer Razer BlackWidow: (accel) keeping acceleration scheme 1
[  1194.066] (**) Razer Razer BlackWidow: (accel) acceleration profile 0
[  1194.066] (**) Razer Razer BlackWidow: (accel) acceleration factor: 2.000
[  1194.066] (**) Razer Razer BlackWidow: (accel) acceleration threshold: 4
[  1194.067] (II) config/udev: Adding input device Razer Razer BlackWidow (/dev/input/event5)
[  1194.067] (**) Razer Razer BlackWidow: Applying InputClass "evdev pointer catchall"
[  1194.067] (II) Using input driver 'evdev' for 'Razer Razer BlackWidow'
[  1194.067] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1194.067] (**) Razer Razer BlackWidow: always reports core events
[  1194.067] (**) evdev: Razer Razer BlackWidow: Device: "/dev/input/event5"
[  1194.067] (--) evdev: Razer Razer BlackWidow: Vendor 0x1532 Product 0x10e
[  1194.067] (--) evdev: Razer Razer BlackWidow: Found 3 mouse buttons
[  1194.067] (--) evdev: Razer Razer BlackWidow: Found scroll wheel(s)
[  1194.067] (--) evdev: Razer Razer BlackWidow: Found relative axes
[  1194.067] (--) evdev: Razer Razer BlackWidow: Found x and y relative axes
[  1194.067] (II) evdev: Razer Razer BlackWidow: Configuring as mouse
[  1194.067] (II) evdev: Razer Razer BlackWidow: Adding scrollwheel support
[  1194.067] (**) evdev: Razer Razer BlackWidow: YAxisMapping: buttons 4 and 5
[  1194.067] (**) evdev: Razer Razer BlackWidow: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  1194.067] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.2/input/input5/event5"
[  1194.067] (II) XINPUT: Adding extended input device "Razer Razer BlackWidow" (type: MOUSE, id 11)
[  1194.067] (II) evdev: Razer Razer BlackWidow: initialized for relative axes.
[  1194.067] (**) Razer Razer BlackWidow: (accel) keeping acceleration scheme 1
[  1194.067] (**) Razer Razer BlackWidow: (accel) acceleration profile 0
[  1194.067] (**) Razer Razer BlackWidow: (accel) acceleration factor: 2.000
[  1194.067] (**) Razer Razer BlackWidow: (accel) acceleration threshold: 4
[  1194.067] (II) config/udev: Adding input device Razer Razer BlackWidow (/dev/input/mouse1)
[  1194.067] (II) No input driver specified, ignoring this device.
[  1194.067] (II) This device may have been added with another device file.
[  1194.067] (II) config/udev: Adding input device HDA Intel Line-Out Side (/dev/input/event10)
[  1194.067] (II) No input driver specified, ignoring this device.
[  1194.067] (II) This device may have been added with another device file.
[  1194.068] (II) config/udev: Adding input device HDA Intel Line-Out CLFE (/dev/input/event11)
[  1194.068] (II) No input driver specified, ignoring this device.
[  1194.068] (II) This device may have been added with another device file.
[  1194.068] (II) config/udev: Adding input device HDA Intel Line-Out Surround (/dev/input/event12)
[  1194.068] (II) No input driver specified, ignoring this device.
[  1194.068] (II) This device may have been added with another device file.
[  1194.068] (II) config/udev: Adding input device HDA Intel Line-Out Front (/dev/input/event13)
[  1194.068] (II) No input driver specified, ignoring this device.
[  1194.068] (II) This device may have been added with another device file.
[  1194.068] (II) config/udev: Adding input device HDA Intel Line (/dev/input/event6)
[  1194.068] (II) No input driver specified, ignoring this device.
[  1194.068] (II) This device may have been added with another device file.
[  1194.068] (II) config/udev: Adding input device HDA Intel Front Mic (/dev/input/event7)
[  1194.069] (II) No input driver specified, ignoring this device.
[  1194.069] (II) This device may have been added with another device file.
[  1194.069] (II) config/udev: Adding input device HDA Intel Rear Mic (/dev/input/event8)
[  1194.069] (II) No input driver specified, ignoring this device.
[  1194.069] (II) This device may have been added with another device file.
[  1194.069] (II) config/udev: Adding input device HDA Intel Front Headphone (/dev/input/event9)
[  1194.069] (II) No input driver specified, ignoring this device.
[  1194.069] (II) This device may have been added with another device file.
[  1375.998] (II) evdev: Razer Razer BlackWidow: Close
[  1375.998] (II) UnloadModule: "evdev"
[  1375.998] (II) Unloading evdev
[  1375.998] (II) evdev: Razer Razer BlackWidow: Close
[  1375.998] (II) UnloadModule: "evdev"
[  1375.998] (II) Unloading evdev
[  1375.998] (II) evdev: Razer Razer BlackWidow: Close
[  1375.998] (II) UnloadModule: "evdev"
[  1375.998] (II) Unloading evdev
[  1375.998] (II) evdev: Logitech USB Gaming Mouse: Close
[  1375.998] (II) UnloadModule: "evdev"
[  1375.998] (II) Unloading evdev
[  1375.998] (II) evdev: Power Button: Close
[  1375.998] (II) UnloadModule: "evdev"
[  1375.998] (II) Unloading evdev
[  1375.998] (II) evdev: Power Button: Close
[  1375.998] (II) UnloadModule: "evdev"
[  1375.998] (II) Unloading evdev
[  1376.070]  ddxSigGiveUp: Closing log
[  1376.070] Server terminated successfully (0). Closing log file.


---

### Post by Rexilion on 2012-08-25
Xorg shuts down cleanly which is good.

If it happens again, please provide your ~/.xsession-errors.

---

