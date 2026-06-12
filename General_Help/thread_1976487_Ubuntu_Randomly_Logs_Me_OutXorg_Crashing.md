---
title: "Ubuntu Randomly Logs Me Out/Xorg Crashing"
date: 2012-05-08
forum: General Help
---

### Post by alsamman on 2012-05-08
Ubuntu 12.04 randomly logs me out and I am trying to figure out what the problem is. I think it has something to do with xorg and when I logged in today I got an error message that said something like "ubuntu has experienced an internal error" and it posted this:
[[IMG]http://img710.imageshack.us/img710/207/screenshotfrom201205081.th.png[/IMG]](http://imageshack.us/photo/my-images/710/screenshotfrom201205081.png/)
[[IMG]http://img845.imageshack.us/img845/207/screenshotfrom201205081.th.png[/IMG]](http://imageshack.us/photo/my-images/845/screenshotfrom201205081.png/)
[[IMG]http://img151.imageshack.us/img151/207/screenshotfrom201205081.th.png[/IMG]](http://imageshack.us/photo/my-images/151/screenshotfrom201205081.png/)
[[IMG]http://img190.imageshack.us/img190/207/screenshotfrom201205081.th.png[/IMG]](http://imageshack.us/photo/my-images/190/screenshotfrom201205081.png/)
[[IMG]http://img692.imageshack.us/img692/3186/screenshotfrom201205081dj.th.png[/IMG]](http://imageshack.us/photo/my-images/692/screenshotfrom201205081dj.png/)
Please help on how I can fix this.

Thanks

---

### Post by antirealm on 2012-05-11
I have the same problem, usually when I'm running Chromium and I go to youtube or open a pdf, but the thing is I can't reproduce the bug, it happens when I least expect it. GRRRR starting to regret the upgrade from 11.10 to 12.04 lts.

---

### Post by alsamman on 2012-05-11
> **antirealm said:**
> I have the same problem, usually when I'm running Chromium and I go to youtube or open a pdf, but the thing is I can't reproduce the bug, it happens when I least expect it. GRRRR starting to regret the upgrade from 11.10 to 12.04 lts.

yup thats exactly what happens to me.

anybody?

---

### Post by thatsfw on 2012-05-15
This started happening to me also after installing CCSM. (This install is only several days old, so I'm unsure if CCSM is the culprit, but it's a lead.) Generally, Chromium is open at crash time. OpenJdk 7 is installed. Flash is installed but still buggy (Youtube video hue). Apart from these and a dozen libs/codecs and a dozen pkgs for school (non-system i.e. Oregano or Octave) my Ubuntu is mostly unmodified from the standard 12.04 install, with latest (non-beta) updates.

The last part of my .xsession-errors reads:
```
** (zeitgeist-datahub:17874): WARNING **: zeitgeist-datahub.vala:227: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!

(exe:17844): Gdk-WARNING **: XID collision, trouble ahead

(exe:17844): Gdk-WARNING **: XID collision, trouble ahead

(exe:17844): Gdk-WARNING **: XID collision, trouble ahead

(exe:17844): Gdk-WARNING **: XID collision, trouble ahead

(exe:17844): Gdk-WARNING **: XID collision, trouble ahead
compiz (decor) - Warn: failed to bind pixmap to texture

```

... and then I'm kicked to the login screen. I just fixed the problem with Ubuntu Tweak where the login sound was making the startup hang and I had to switch to a text terminal and "sudo stop lightdm && sudo start lightdm" and turn the login sound back on.

---

### Post by roelforg on 2012-05-15
Some info:
You getting logged out DOES have to do with xorg.
Whenever you click logout, gnome shuts down and xorg will do so as well,
lightdm will then restart xorg and present you a login.
If it crashes, log back in and post the content of /var/log/Xorg.0.log.old
That should tell us what crashed.

---

### Post by alsamman on 2012-05-18
alright so it crashed again so heres the results:
```
[   249.670] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[   249.670] X Protocol Version 11, Revision 0
[   249.670] Build Operating System: Linux 2.6.42-23-generic i686 Ubuntu
[   249.670] Current Operating System: Linux kenan-desktop 3.2.0-24-generic-pae #37-Ubuntu SMP Wed Apr 25 10:47:59 UTC 2012 i686
[   249.670] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-24-generic-pae root=UUID=40b2eba4-1699-4051-81d3-d4af9e08fc05 ro quiet splash vt.handoff=7
[   249.670] Build Date: 20 April 2012  05:12:21AM
[   249.670] xorg-server 2:1.11.4-0ubuntu10.1 (For technical support please see http://www.ubuntu.com/support) 
[   249.670] Current version of pixman: 0.24.4
[   249.670] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[   249.670] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   249.670] (==) Log file: "/var/log/Xorg.0.log", Time: Fri May 18 20:21:27 2012
[   249.671] (==) Using config file: "/etc/X11/xorg.conf"
[   249.671] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   249.671] (==) No Layout section.  Using the first Screen section.
[   249.671] (==) No screen section available. Using defaults.
[   249.671] (**) |-->Screen "Default Screen Section" (0)
[   249.671] (**) |   |-->Monitor "<default monitor>"
[   249.671] (==) No device specified for screen "Default Screen Section".
	Using the first device section listed.
[   249.671] (**) |   |-->Device "Default Device"
[   249.671] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[   249.671] (==) Automatically adding devices
[   249.671] (==) Automatically enabling devices
[   249.671] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   249.671] 	Entry deleted from font path.
[   249.671] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   249.671] 	Entry deleted from font path.
[   249.671] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   249.671] 	Entry deleted from font path.
[   249.671] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   249.671] 	Entry deleted from font path.
[   249.673] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   249.673] 	Entry deleted from font path.
[   249.673] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[   249.673] 	Entry deleted from font path.
[   249.673] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[   249.673] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   249.673] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[   249.673] (II) Loader magic: 0xb774e5a0
[   249.673] (II) Module ABI versions:
[   249.673] 	X.Org ANSI C Emulation: 0.4
[   249.673] 	X.Org Video Driver: 11.0
[   249.673] 	X.Org XInput driver : 16.0
[   249.673] 	X.Org Server Extension : 6.0
[   249.673] (--) PCI:*(0:5:0:0) 10de:0421:1682:2305 rev 161, Mem @ 0xfa000000/16777216, 0xd0000000/268435456, 0xf8000000/33554432, I/O @ 0x00009c00/128, BIOS @ 0x????????/131072
[   249.674] (II) Open ACPI successful (/var/run/acpid.socket)
[   249.674] (II) LoadModule: "extmod"
[   249.674] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   249.674] (II) Module extmod: vendor="X.Org Foundation"
[   249.674] 	compiled for 1.11.3, module version = 1.0.0
[   249.674] 	Module class: X.Org Server Extension
[   249.674] 	ABI class: X.Org Server Extension, version 6.0
[   249.674] (II) Loading extension MIT-SCREEN-SAVER
[   249.674] (II) Loading extension XFree86-VidModeExtension
[   249.674] (II) Loading extension XFree86-DGA
[   249.674] (II) Loading extension DPMS
[   249.674] (II) Loading extension XVideo
[   249.674] (II) Loading extension XVideo-MotionCompensation
[   249.674] (II) Loading extension X-Resource
[   249.674] (II) LoadModule: "dbe"
[   249.675] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   249.675] (II) Module dbe: vendor="X.Org Foundation"
[   249.675] 	compiled for 1.11.3, module version = 1.0.0
[   249.675] 	Module class: X.Org Server Extension
[   249.675] 	ABI class: X.Org Server Extension, version 6.0
[   249.675] (II) Loading extension DOUBLE-BUFFER
[   249.675] (II) LoadModule: "glx"
[   249.675] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/libglx.so
[   249.717] (II) Module glx: vendor="NVIDIA Corporation"
[   249.717] 	compiled for 4.0.2, module version = 1.0.0
[   249.717] 	Module class: X.Org Server Extension
[   249.717] (II) NVIDIA GLX Module  295.40  Thu Apr  5 21:49:54 PDT 2012
[   249.717] (II) Loading extension GLX
[   249.717] (II) LoadModule: "record"
[   249.717] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   249.718] (II) Module record: vendor="X.Org Foundation"
[   249.718] 	compiled for 1.11.3, module version = 1.13.0
[   249.718] 	Module class: X.Org Server Extension
[   249.718] 	ABI class: X.Org Server Extension, version 6.0
[   249.718] (II) Loading extension RECORD
[   249.718] (II) LoadModule: "dri"
[   249.718] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   249.718] (II) Module dri: vendor="X.Org Foundation"
[   249.718] 	compiled for 1.11.3, module version = 1.0.0
[   249.718] 	ABI class: X.Org Server Extension, version 6.0
[   249.718] (II) Loading extension XFree86-DRI
[   249.718] (II) LoadModule: "dri2"
[   249.718] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   249.718] (II) Module dri2: vendor="X.Org Foundation"
[   249.718] 	compiled for 1.11.3, module version = 1.2.0
[   249.718] 	ABI class: X.Org Server Extension, version 6.0
[   249.718] (II) Loading extension DRI2
[   249.718] (==) Matched nvidia as autoconfigured driver 0
[   249.719] (==) Matched nouveau as autoconfigured driver 1
[   249.719] (==) Matched nv as autoconfigured driver 2
[   249.719] (==) Matched vesa as autoconfigured driver 3
[   249.719] (==) Matched fbdev as autoconfigured driver 4
[   249.719] (==) Assigned the driver to the xf86ConfigLayout
[   249.719] (II) LoadModule: "nvidia"
[   249.719] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[   249.719] (II) Module nvidia: vendor="NVIDIA Corporation"
[   249.719] 	compiled for 4.0.2, module version = 1.0.0
[   249.719] 	Module class: X.Org Video Driver
[   249.721] (II) LoadModule: "nouveau"
[   249.721] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[   249.722] (II) Module nouveau: vendor="X.Org Foundation"
[   249.722] 	compiled for 1.11.3, module version = 0.0.16
[   249.722] 	Module class: X.Org Video Driver
[   249.722] 	ABI class: X.Org Video Driver, version 11.0
[   249.722] (II) LoadModule: "nv"
[   249.722] (WW) Warning, couldn't open module nv
[   249.722] (II) UnloadModule: "nv"
[   249.722] (II) Unloading nv
[   249.722] (EE) Failed to load module "nv" (module does not exist, 0)
[   249.722] (II) LoadModule: "vesa"
[   249.723] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   249.723] (II) Module vesa: vendor="X.Org Foundation"
[   249.723] 	compiled for 1.11.3, module version = 2.3.0
[   249.723] 	Module class: X.Org Video Driver
[   249.723] 	ABI class: X.Org Video Driver, version 11.0
[   249.723] (II) LoadModule: "fbdev"
[   249.723] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   249.723] (II) Module fbdev: vendor="X.Org Foundation"
[   249.723] 	compiled for 1.11.3, module version = 0.4.2
[   249.723] 	ABI class: X.Org Video Driver, version 11.0
[   249.723] (==) Matched nvidia as autoconfigured driver 0
[   249.723] (==) Matched nouveau as autoconfigured driver 1
[   249.723] (==) Matched nv as autoconfigured driver 2
[   249.723] (==) Matched vesa as autoconfigured driver 3
[   249.723] (==) Matched fbdev as autoconfigured driver 4
[   249.723] (==) Assigned the driver to the xf86ConfigLayout
[   249.723] (II) LoadModule: "nvidia"
[   249.723] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[   249.724] (II) Module nvidia: vendor="NVIDIA Corporation"
[   249.724] 	compiled for 4.0.2, module version = 1.0.0
[   249.724] 	Module class: X.Org Video Driver
[   249.724] (II) UnloadModule: "nvidia"
[   249.724] (II) Unloading nvidia
[   249.724] (II) Failed to load module "nvidia" (already loaded, -1217312693)
[   249.724] (II) LoadModule: "nouveau"
[   249.724] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[   249.724] (II) Module nouveau: vendor="X.Org Foundation"
[   249.724] 	compiled for 1.11.3, module version = 0.0.16
[   249.724] 	Module class: X.Org Video Driver
[   249.724] 	ABI class: X.Org Video Driver, version 11.0
[   249.724] (II) UnloadModule: "nouveau"
[   249.724] (II) Unloading nouveau
[   249.724] (II) Failed to load module "nouveau" (already loaded, -1217312693)
[   249.724] (II) LoadModule: "nv"
[   249.725] (WW) Warning, couldn't open module nv
[   249.725] (II) UnloadModule: "nv"
[   249.725] (II) Unloading nv
[   249.725] (EE) Failed to load module "nv" (module does not exist, 0)
[   249.725] (II) LoadModule: "vesa"
[   249.725] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   249.725] (II) Module vesa: vendor="X.Org Foundation"
[   249.725] 	compiled for 1.11.3, module version = 2.3.0
[   249.725] 	Module class: X.Org Video Driver
[   249.725] 	ABI class: X.Org Video Driver, version 11.0
[   249.725] (II) UnloadModule: "vesa"
[   249.725] (II) Unloading vesa
[   249.725] (II) Failed to load module "vesa" (already loaded, 0)
[   249.725] (II) LoadModule: "fbdev"
[   249.725] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   249.725] (II) Module fbdev: vendor="X.Org Foundation"
[   249.725] 	compiled for 1.11.3, module version = 0.4.2
[   249.725] 	ABI class: X.Org Video Driver, version 11.0
[   249.725] (II) UnloadModule: "fbdev"
[   249.725] (II) Unloading fbdev
[   249.725] (II) Failed to load module "fbdev" (already loaded, 0)
[   249.725] (II) NVIDIA dlloader X Driver  295.40  Thu Apr  5 21:29:50 PDT 2012
[   249.725] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[   249.726] (II) NOUVEAU driver Date:   Wed Nov 30 18:56:54 2011 +0100
[   249.726] (II) NOUVEAU driver for NVIDIA chipset families :
[   249.726] 	RIVA TNT        (NV04)
[   249.726] 	RIVA TNT2       (NV05)
[   249.726] 	GeForce 256     (NV10)
[   249.726] 	GeForce 2       (NV11, NV15)
[   249.726] 	GeForce 4MX     (NV17, NV18)
[   249.726] 	GeForce 3       (NV20)
[   249.726] 	GeForce 4Ti     (NV25, NV28)
[   249.726] 	GeForce FX      (NV3x)
[   249.726] 	GeForce 6       (NV4x)
[   249.726] 	GeForce 7       (G7x)
[   249.726] 	GeForce 8       (G8x)
[   249.726] 	GeForce GTX 200 (NVA0)
[   249.726] 	GeForce GTX 400 (NVC0)
[   249.726] (II) VESA: driver for VESA chipsets: vesa
[   249.726] (II) FBDEV: driver for framebuffer: fbdev
[   249.726] (++) using VT number 7

[   249.726] (II) Loading sub module "fb"
[   249.726] (II) LoadModule: "fb"
[   249.727] (II) Loading /usr/lib/xorg/modules/libfb.so
[   249.727] (II) Module fb: vendor="X.Org Foundation"
[   249.727] 	compiled for 1.11.3, module version = 1.0.0
[   249.727] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   249.727] (II) Loading sub module "wfb"
[   249.727] (II) LoadModule: "wfb"
[   249.727] (II) Loading /usr/lib/xorg/modules/libwfb.so
[   249.727] (II) Module wfb: vendor="X.Org Foundation"
[   249.727] 	compiled for 1.11.3, module version = 1.0.0
[   249.727] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   249.727] (II) Loading sub module "ramdac"
[   249.727] (II) LoadModule: "ramdac"
[   249.727] (II) Module "ramdac" already built-in
[   249.727] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[   249.727] (II) Loading /usr/lib/xorg/modules/libwfb.so
[   249.727] (II) Loading /usr/lib/xorg/modules/libfb.so
[   249.728] (WW) Falling back to old probe method for vesa
[   249.728] (WW) Falling back to old probe method for fbdev
[   249.728] (II) Loading sub module "fbdevhw"
[   249.728] (II) LoadModule: "fbdevhw"
[   249.728] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   249.728] (II) Module fbdevhw: vendor="X.Org Foundation"
[   249.728] 	compiled for 1.11.3, module version = 0.0.2
[   249.728] 	ABI class: X.Org Video Driver, version 11.0
[   249.728] (II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[   249.728] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[   249.728] (==) NVIDIA(0): RGB weight 888
[   249.728] (==) NVIDIA(0): Default visual is TrueColor
[   249.728] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[   249.728] (**) NVIDIA(0): Option "NoLogo" "True"
[   249.729] (**) NVIDIA(0): Enabling 2D acceleration
[   249.837] (II) NVIDIA(GPU-0): Display (Samsung S24B300 (CRT-0)) does not support NVIDIA 3D
[   249.837] (II) NVIDIA(GPU-0):     Vision stereo.
[   249.841] (II) NVIDIA(0): NVIDIA GPU GeForce 8500 GT (G86) at PCI:5:0:0 (GPU-0)
[   249.841] (--) NVIDIA(0): Memory: 524288 kBytes
[   249.841] (--) NVIDIA(0): VideoBIOS: 60.86.34.00.81
[   249.841] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[   249.841] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[   249.843] (--) NVIDIA(0): Connected display device(s) on GeForce 8500 GT at PCI:5:0:0
[   249.843] (--) NVIDIA(0):     Samsung S24B300 (CRT-0)
[   249.843] (--) NVIDIA(0): Samsung S24B300 (CRT-0): 400.0 MHz maximum pixel clock
[   249.940] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   249.940] (**) NVIDIA(0):     device Samsung S24B300 (CRT-0) (Using EDID frequencies has
[   249.940] (**) NVIDIA(0):     been enabled on all display devices.)
[   249.974] (II) NVIDIA(0): Assigned Display Device: CRT-0
[   249.974] (==) NVIDIA(0): 
[   249.974] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[   249.974] (==) NVIDIA(0):     will be used as the requested mode.
[   249.974] (==) NVIDIA(0): 
[   249.974] (II) NVIDIA(0): Validated modes:
[   249.974] (II) NVIDIA(0):     "nvidia-auto-select"
[   249.974] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[   249.979] (--) NVIDIA(0): DPI set to (93, 94); computed from "UseEdidDpi" X config
[   249.979] (--) NVIDIA(0):     option
[   249.979] (II) UnloadModule: "nouveau"
[   249.979] (II) Unloading nouveau
[   249.979] (II) UnloadModule: "vesa"
[   249.979] (II) Unloading vesa
[   249.979] (II) UnloadModule: "fbdev"
[   249.979] (II) Unloading fbdev
[   249.979] (II) UnloadModule: "fbdevhw"
[   249.979] (II) Unloading fbdevhw
[   249.979] (--) Depth 24 pixmap format is 32 bpp
[   249.979] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[   249.987] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[   250.012] (II) Loading extension NV-GLX
[   250.060] (==) NVIDIA(0): Disabling shared memory pixmaps
[   250.060] (==) NVIDIA(0): Backing store disabled
[   250.060] (==) NVIDIA(0): Silken mouse enabled
[   250.060] (==) NVIDIA(0): DPMS enabled
[   250.060] (II) Loading extension NV-CONTROL
[   250.061] (II) Loading extension XINERAMA
[   250.061] (II) Loading sub module "dri2"
[   250.061] (II) LoadModule: "dri2"
[   250.061] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   250.061] (II) Module dri2: vendor="X.Org Foundation"
[   250.061] 	compiled for 1.11.3, module version = 1.2.0
[   250.061] 	ABI class: X.Org Server Extension, version 6.0
[   250.061] (II) NVIDIA(0): [DRI2] Setup complete
[   250.061] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[   250.061] (==) RandR enabled
[   250.061] (II) Initializing built-in extension Generic Event Extension
[   250.061] (II) Initializing built-in extension SHAPE
[   250.061] (II) Initializing built-in extension MIT-SHM
[   250.061] (II) Initializing built-in extension XInputExtension
[   250.061] (II) Initializing built-in extension XTEST
[   250.061] (II) Initializing built-in extension BIG-REQUESTS
[   250.061] (II) Initializing built-in extension SYNC
[   250.061] (II) Initializing built-in extension XKEYBOARD
[   250.061] (II) Initializing built-in extension XC-MISC
[   250.061] (II) Initializing built-in extension SECURITY
[   250.061] (II) Initializing built-in extension XINERAMA
[   250.061] (II) Initializing built-in extension XFIXES
[   250.061] (II) Initializing built-in extension RENDER
[   250.061] (II) Initializing built-in extension RANDR
[   250.061] (II) Initializing built-in extension COMPOSITE
[   250.061] (II) Initializing built-in extension DAMAGE
[   250.064] (II) Initializing extension GLX
[   250.092] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   250.096] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[   250.096] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   250.096] (II) LoadModule: "evdev"
[   250.096] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   250.096] (II) Module evdev: vendor="X.Org Foundation"
[   250.096] 	compiled for 1.11.3, module version = 2.7.0
[   250.096] 	Module class: X.Org XInput Driver
[   250.096] 	ABI class: X.Org XInput driver, version 16.0
[   250.096] (II) Using input driver 'evdev' for 'Power Button'
[   250.096] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   250.096] (**) Power Button: always reports core events
[   250.096] (**) evdev: Power Button: Device: "/dev/input/event1"
[   250.097] (--) evdev: Power Button: Vendor 0 Product 0x1
[   250.097] (--) evdev: Power Button: Found keys
[   250.097] (II) evdev: Power Button: Configuring as keyboard
[   250.097] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[   250.097] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[   250.097] (**) Option "xkb_rules" "evdev"
[   250.097] (**) Option "xkb_model" "pc105"
[   250.097] (**) Option "xkb_layout" "us"
[   250.098] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[   250.098] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   250.098] (II) Using input driver 'evdev' for 'Power Button'
[   250.098] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   250.098] (**) Power Button: always reports core events
[   250.098] (**) evdev: Power Button: Device: "/dev/input/event0"
[   250.098] (--) evdev: Power Button: Vendor 0 Product 0x1
[   250.098] (--) evdev: Power Button: Found keys
[   250.098] (II) evdev: Power Button: Configuring as keyboard
[   250.098] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[   250.098] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[   250.098] (**) Option "xkb_rules" "evdev"
[   250.098] (**) Option "xkb_model" "pc105"
[   250.098] (**) Option "xkb_layout" "us"
[   250.099] (II) config/udev: Adding input device Microsoft Comfort Mouse 6000 (/dev/input/event2)
[   250.099] (**) Microsoft Comfort Mouse 6000: Applying InputClass "evdev pointer catchall"
[   250.099] (**) Microsoft Comfort Mouse 6000: Applying InputClass "evdev keyboard catchall"
[   250.099] (II) Using input driver 'evdev' for 'Microsoft Comfort Mouse 6000'
[   250.099] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   250.099] (**) Microsoft Comfort Mouse 6000: always reports core events
[   250.099] (**) evdev: Microsoft Comfort Mouse 6000: Device: "/dev/input/event2"
[   250.099] (--) evdev: Microsoft Comfort Mouse 6000: Vendor 0x45e Product 0x77d
[   250.099] (--) evdev: Microsoft Comfort Mouse 6000: Found 9 mouse buttons
[   250.099] (--) evdev: Microsoft Comfort Mouse 6000: Found scroll wheel(s)
[   250.099] (--) evdev: Microsoft Comfort Mouse 6000: Found relative axes
[   250.099] (--) evdev: Microsoft Comfort Mouse 6000: Found x and y relative axes
[   250.099] (--) evdev: Microsoft Comfort Mouse 6000: Found absolute axes
[   250.099] (II) evdev: Microsoft Comfort Mouse 6000: Forcing absolute x/y axes to exist.
[   250.099] (--) evdev: Microsoft Comfort Mouse 6000: Found keys
[   250.099] (II) evdev: Microsoft Comfort Mouse 6000: Configuring as mouse
[   250.099] (II) evdev: Microsoft Comfort Mouse 6000: Configuring as keyboard
[   250.099] (II) evdev: Microsoft Comfort Mouse 6000: Adding scrollwheel support
[   250.099] (**) evdev: Microsoft Comfort Mouse 6000: YAxisMapping: buttons 4 and 5
[   250.099] (**) evdev: Microsoft Comfort Mouse 6000: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   250.099] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/usb2/2-1/2-1:1.0/input/input2/event2"
[   250.099] (II) XINPUT: Adding extended input device "Microsoft Comfort Mouse 6000" (type: KEYBOARD, id 8)
[   250.099] (**) Option "xkb_rules" "evdev"
[   250.099] (**) Option "xkb_model" "pc105"
[   250.099] (**) Option "xkb_layout" "us"
[   250.100] (II) evdev: Microsoft Comfort Mouse 6000: initialized for relative axes.
[   250.100] (WW) evdev: Microsoft Comfort Mouse 6000: ignoring absolute axes.
[   250.100] (**) Microsoft Comfort Mouse 6000: (accel) keeping acceleration scheme 1
[   250.100] (**) Microsoft Comfort Mouse 6000: (accel) acceleration profile 0
[   250.100] (**) Microsoft Comfort Mouse 6000: (accel) acceleration factor: 2.000
[   250.100] (**) Microsoft Comfort Mouse 6000: (accel) acceleration threshold: 4
[   250.100] (II) config/udev: Adding input device Microsoft Comfort Mouse 6000 (/dev/input/mouse0)
[   250.100] (II) No input driver specified, ignoring this device.
[   250.100] (II) This device may have been added with another device file.
[   250.101] (II) config/udev: Adding input device Razer Razer Arctosa (/dev/input/event3)
[   250.101] (**) Razer Razer Arctosa: Applying InputClass "evdev keyboard catchall"
[   250.101] (II) Using input driver 'evdev' for 'Razer Razer Arctosa'
[   250.101] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   250.101] (**) Razer Razer Arctosa: always reports core events
[   250.101] (**) evdev: Razer Razer Arctosa: Device: "/dev/input/event3"
[   250.101] (--) evdev: Razer Razer Arctosa: Vendor 0x1532 Product 0x10b
[   250.101] (--) evdev: Razer Razer Arctosa: Found keys
[   250.101] (II) evdev: Razer Razer Arctosa: Configuring as keyboard
[   250.101] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3:1.0/input/input3/event3"
[   250.101] (II) XINPUT: Adding extended input device "Razer Razer Arctosa" (type: KEYBOARD, id 9)
[   250.101] (**) Option "xkb_rules" "evdev"
[   250.101] (**) Option "xkb_model" "pc105"
[   250.101] (**) Option "xkb_layout" "us"
[   250.102] (II) config/udev: Adding input device Razer Razer Arctosa (/dev/input/event4)
[   250.102] (**) Razer Razer Arctosa: Applying InputClass "evdev keyboard catchall"
[   250.102] (II) Using input driver 'evdev' for 'Razer Razer Arctosa'
[   250.102] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   250.102] (**) Razer Razer Arctosa: always reports core events
[   250.102] (**) evdev: Razer Razer Arctosa: Device: "/dev/input/event4"
[   250.102] (--) evdev: Razer Razer Arctosa: Vendor 0x1532 Product 0x10b
[   250.102] (--) evdev: Razer Razer Arctosa: Found 1 mouse buttons
[   250.102] (--) evdev: Razer Razer Arctosa: Found scroll wheel(s)
[   250.102] (--) evdev: Razer Razer Arctosa: Found relative axes
[   250.102] (II) evdev: Razer Razer Arctosa: Forcing relative x/y axes to exist.
[   250.102] (--) evdev: Razer Razer Arctosa: Found absolute axes
[   250.102] (II) evdev: Razer Razer Arctosa: Forcing absolute x/y axes to exist.
[   250.102] (--) evdev: Razer Razer Arctosa: Found keys
[   250.102] (II) evdev: Razer Razer Arctosa: Configuring as mouse
[   250.102] (II) evdev: Razer Razer Arctosa: Configuring as keyboard
[   250.102] (II) evdev: Razer Razer Arctosa: Adding scrollwheel support
[   250.102] (**) evdev: Razer Razer Arctosa: YAxisMapping: buttons 4 and 5
[   250.102] (**) evdev: Razer Razer Arctosa: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   250.102] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3:1.1/input/input4/event4"
[   250.102] (II) XINPUT: Adding extended input device "Razer Razer Arctosa" (type: KEYBOARD, id 10)
[   250.102] (**) Option "xkb_rules" "evdev"
[   250.102] (**) Option "xkb_model" "pc105"
[   250.103] (**) Option "xkb_layout" "us"
[   250.103] (II) evdev: Razer Razer Arctosa: initialized for relative axes.
[   250.103] (WW) evdev: Razer Razer Arctosa: ignoring absolute axes.
[   250.103] (**) Razer Razer Arctosa: (accel) keeping acceleration scheme 1
[   250.103] (**) Razer Razer Arctosa: (accel) acceleration profile 0
[   250.103] (**) Razer Razer Arctosa: (accel) acceleration factor: 2.000
[   250.103] (**) Razer Razer Arctosa: (accel) acceleration threshold: 4
[   250.104] (II) config/udev: Adding input device UVC Camera (046d:08ca) (/dev/input/event5)
[   250.104] (**) UVC Camera (046d:08ca): Applying InputClass "evdev keyboard catchall"
[   250.104] (II) Using input driver 'evdev' for 'UVC Camera (046d:08ca)'
[   250.104] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   250.104] (**) UVC Camera (046d:08ca): always reports core events
[   250.104] (**) evdev: UVC Camera (046d:08ca): Device: "/dev/input/event5"
[   250.104] (--) evdev: UVC Camera (046d:08ca): Vendor 0x46d Product 0x8ca
[   250.104] (--) evdev: UVC Camera (046d:08ca): Found keys
[   250.104] (II) evdev: UVC Camera (046d:08ca): Configuring as keyboard
[   250.104] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.1/usb1/1-4/1-4:1.0/input/input5/event5"
[   250.104] (II) XINPUT: Adding extended input device "UVC Camera (046d:08ca)" (type: KEYBOARD, id 11)
[   250.104] (**) Option "xkb_rules" "evdev"
[   250.104] (**) Option "xkb_model" "pc105"
[   250.104] (**) Option "xkb_layout" "us"
[   250.656] (II) NVIDIA(0): Setting mode "1920x1080_60_0"
[   260.006] (II) XKB: reuse xkmfile /var/lib/xkb/server-03AF3717FF3AB439A4BAABA686CCB40771CDF520.xkm
[   490.388] (II) evdev: Power Button: Close
[   490.388] (II) UnloadModule: "evdev"
[   490.388] (II) Unloading evdev
[   490.416] (II) evdev: Power Button: Close
[   490.416] (II) UnloadModule: "evdev"
[   490.416] (II) Unloading evdev
[   490.444] (II) evdev: Microsoft Comfort Mouse 6000: Close
[   490.444] (II) UnloadModule: "evdev"
[   490.444] (II) Unloading evdev
[   490.480] (II) evdev: Razer Razer Arctosa: Close
[   490.480] (II) UnloadModule: "evdev"
[   490.480] (II) Unloading evdev
[   490.508] (II) evdev: Razer Razer Arctosa: Close
[   490.508] (II) UnloadModule: "evdev"
[   490.508] (II) Unloading evdev
[   490.548] (II) evdev: UVC Camera (046d:08ca): Close
[   490.548] (II) UnloadModule: "evdev"
[   490.548] (II) Unloading evdev
[   490.621]  ddxSigGiveUp: Closing log
[   490.621] Server terminated successfully (0). Closing log file.
```

---

### Post by alsamman on 2012-05-19
bump

---

### Post by alsamman on 2012-05-20
bump

---

### Post by roelforg on 2012-05-21
It's related to the xid error, no xorg crash (this rules out most hw issues).
And i've crashed compiz a lot (i like playing with settings ;)) but it never took gnome with it so i believe the compiz error doesn't have to do with it.

Did you recently install updates?
If you have some remaining ones, install them.
The xid error warns about an version mismatch between xorg and gdk (part of gtk and it's where gnome and most buildin apps rely on), and this can cause the crash.

EDIT:
I looked it up, it seems that using the oss drivers for both nvidia and ati/amd can cause this as well.
I've seen in the xorg log that you're using the oss drivers, so you could try closed source the nvidia ones.

---

### Post by woxuxow on 2012-05-21
I had the same problem as yours with 11.10 but now i have 12.04 and the problem is gone

---

### Post by alsamman on 2012-05-21
I reinstalled 12.04 and recently it crashed again but when I reported the problem it said this:

The problem cannot be reported:

You have some obsolete package versions installed. Please upgrade the following packages and check if the problem still occurs:

xserver-xorg-core, upstart, xserver-common


How exactly do I upgrade these packages???

---

### Post by woxuxow on 2012-05-22
> **alsamman said:**
> I reinstalled 12.04 and recently it crashed again but when I reported the problem it said this:

The problem cannot be reported:

You have some obsolete package versions installed. Please upgrade the following packages and check if the problem still occurs:

xserver-xorg-core, upstart, xserver-common


How exactly do I upgrade these packages???

sudo apt-get dist-upgrade

it is better to do the update before the upgrade by

sudo apt-get update

---

### Post by alsamman on 2012-06-02
bump. This issue is still going on and I don't know what to do.

---

### Post by stanislawe on 2012-07-16
Hi there,

I'm experiencing the same problem on my computer where my Ubuntu 12.04 is logging me out randomly. Here are the lines from the Xorg.0.log.old file which are explaining the problem:

```
Backtrace:
[ 13999.061] 0: /usr/bin/X (xorg_backtrace+0x37) [0xb76a2727]
[ 13999.061] 1: /usr/bin/X (0xb751a000+0x18c4aa) [0xb76a64aa]
[ 13999.061] 2: (vdso) (__kernel_rt_sigreturn+0x0) [0xb74f740c]
[ 13999.061] 3: /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so (0xb4704000+0xd6b76) [0xb47dab76]
[ 13999.061] Segmentation fault at address 0x80
[ 13999.062]
Caught signal 11 (Segmentation fault). Server aborting
[ 13999.062]
Please consult the The X.Org Foundation support
         at http://wiki.x.org
 for help.
[ 13999.062] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[ 13999.062]
[ 13999.129] (II) evdev: Power Button: Close
[ 13999.129] (II) UnloadModule: "evdev"
[ 13999.129] (II) Unloading evdev
[ 13999.136] (II) evdev: Video Bus: Close
[ 13999.136] (II) evdev: Video Bus: Close
[ 13999.136] (II) UnloadModule: "evdev"
[ 13999.136] (II) Unloading evdev
[ 13999.145] (II) evdev: Power Button: Close
[ 13999.145] (II) UnloadModule: "evdev"
[ 13999.145] (II) Unloading evdev
[ 13999.148] (II) evdev: Sleep Button: Close
[ 13999.148] (II) UnloadModule: "evdev"
[ 13999.148] (II) Unloading evdev
[ 13999.153] (II) evdev: AT Translated Set 2 keyboard: Close
[ 13999.153] (II) UnloadModule: "evdev"
[ 13999.153] (II) Unloading evdev
[ 13999.166] (II) UnloadModule: "synaptics"
[ 13999.167] (II) Unloading synaptics
[ 13999.167] (II) evdev: HP WMI hotkeys: Close
[ 13999.167] (II) UnloadModule: "evdev"
[ 13999.167] (II) Unloading evdev

```If I'm correct there is a problem with my nvidia drivers. Should I reinstall the drivers or would you be able to point me to a fix which can resolve this problem?
Any advices and different opinion will be more than welcome.

---

