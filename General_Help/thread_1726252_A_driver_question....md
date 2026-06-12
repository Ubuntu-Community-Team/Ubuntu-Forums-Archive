---
title: "A driver question...???"
date: 2011-04-10
forum: General Help
---

### Post by robertcoulson on 2011-04-10
Hi...I thought I had lost my Intel@  HD Graphic driver(s) during a routine use of “Update manager”....I could not play any games or use  “Visual effects”.

So yesterday I ran Ubuntu under “Virtualbox”, and I could play games...???

BIG QUESTION....Is there a way to replace my Ubuntu driver(s)...??? (without reinstalling)
Robert

---

### Post by Yellow Pasque on 2011-04-10
Post your /var/log/Xorg.0.log

---

### Post by robertcoulson on 2011-04-10
Would not let me...see attachment
Robert

---

### Post by sam123 on 2011-04-10
Try
cat /var/log/Xorg.0.log

---

### Post by robertcoulson on 2011-04-10
```
robert@Robert-aspire-5742:~$ cat /var/log/Xorg.0.log
[    26.059] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    26.059] X Protocol Version 11, Revision 0
[    26.059] Build Operating System: Linux 2.6.24-28-server x86_64 Ubuntu
[    26.059] Current Operating System: Linux Robert-aspire-5742 2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:39:03 UTC 2011 x86_64
[    26.059] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-28-generic root=UUID=5cc311f9-ee13-4624-ae51-0e976caa8d87 ro quiet splash
[    26.059] Build Date: 09 January 2011  12:14:27PM
[    26.059] xorg-server 2:1.9.0-0ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
[    26.059] Current version of pixman: 0.18.4
[    26.059] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    26.059] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    26.059] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Apr 10 22:24:04 2011
[    26.138] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    26.139] (==) No Layout section.  Using the first Screen section.
[    26.139] (==) No screen section available. Using defaults.
[    26.139] (**) |-->Screen "Default Screen Section" (0)
[    26.139] (**) |   |-->Monitor "<default monitor>"
[    26.139] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    26.139] (==) Automatically adding devices
[    26.139] (==) Automatically enabling devices
[    26.139] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    26.139] 	Entry deleted from font path.
[    26.139] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    26.139] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    26.139] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    26.139] (II) Loader magic: 0x7d17a0
[    26.139] (II) Module ABI versions:
[    26.139] 	X.Org ANSI C Emulation: 0.4
[    26.139] 	X.Org Video Driver: 8.0
[    26.139] 	X.Org XInput driver : 11.0
[    26.139] 	X.Org Server Extension : 4.0
[    26.140] (--) PCI:*(0:0:2:0) 8086:0046:1025:0487 rev 2, Mem @ 0xb0000000/4194304, 0xa0000000/268435456, I/O @ 0x00003050/8
[    26.140] (II) Open ACPI successful (/var/run/acpid.socket)
[    26.140] (II) LoadModule: "extmod"
[    26.140] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    26.140] (II) Module extmod: vendor="X.Org Foundation"
[    26.140] 	compiled for 1.9.0, module version = 1.0.0
[    26.140] 	Module class: X.Org Server Extension
[    26.140] 	ABI class: X.Org Server Extension, version 4.0
[    26.140] (II) Loading extension MIT-SCREEN-SAVER
[    26.140] (II) Loading extension XFree86-VidModeExtension
[    26.140] (II) Loading extension XFree86-DGA
[    26.140] (II) Loading extension DPMS
[    26.140] (II) Loading extension XVideo
[    26.140] (II) Loading extension XVideo-MotionCompensation
[    26.140] (II) Loading extension X-Resource
[    26.140] (II) LoadModule: "dbe"
[    26.141] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    26.141] (II) Module dbe: vendor="X.Org Foundation"
[    26.141] 	compiled for 1.9.0, module version = 1.0.0
[    26.141] 	Module class: X.Org Server Extension
[    26.141] 	ABI class: X.Org Server Extension, version 4.0
[    26.141] (II) Loading extension DOUBLE-BUFFER
[    26.141] (II) LoadModule: "glx"
[    26.141] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    26.145] (II) Module glx: vendor="NVIDIA Corporation"
[    26.145] 	compiled for 4.0.2, module version = 1.0.0
[    26.145] 	Module class: X.Org Server Extension
[    26.145] (II) NVIDIA GLX Module  173.14.28  Wed Sep 29 10:19:01 PDT 2010
[    26.145] (II) Loading extension GLX
[    26.145] (II) LoadModule: "record"
[    26.145] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    26.145] (II) Module record: vendor="X.Org Foundation"
[    26.145] 	compiled for 1.9.0, module version = 1.13.0
[    26.145] 	Module class: X.Org Server Extension
[    26.145] 	ABI class: X.Org Server Extension, version 4.0
[    26.145] (II) Loading extension RECORD
[    26.145] (II) LoadModule: "dri"
[    26.145] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    26.145] (II) Module dri: vendor="X.Org Foundation"
[    26.145] 	compiled for 1.9.0, module version = 1.0.0
[    26.145] 	ABI class: X.Org Server Extension, version 4.0
[    26.145] (II) Loading extension XFree86-DRI
[    26.145] (II) LoadModule: "dri2"
[    26.145] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    26.145] (II) Module dri2: vendor="X.Org Foundation"
[    26.145] 	compiled for 1.9.0, module version = 1.2.0
[    26.145] 	ABI class: X.Org Server Extension, version 4.0
[    26.145] (II) Loading extension DRI2
[    26.145] (==) Matched intel as autoconfigured driver 0
[    26.145] (==) Matched vesa as autoconfigured driver 1
[    26.145] (==) Matched fbdev as autoconfigured driver 2
[    26.146] (==) Assigned the driver to the xf86ConfigLayout
[    26.146] (II) LoadModule: "intel"
[    26.270] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    26.302] (II) Module intel: vendor="X.Org Foundation"
[    26.302] 	compiled for 1.9.0, module version = 2.14.902
[    26.302] 	Module class: X.Org Video Driver
[    26.302] 	ABI class: X.Org Video Driver, version 8.0
[    26.302] (II) LoadModule: "vesa"
[    26.303] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    26.303] (II) Module vesa: vendor="X.Org Foundation"
[    26.303] 	compiled for 1.8.99.905, module version = 2.3.0
[    26.303] 	Module class: X.Org Video Driver
[    26.303] 	ABI class: X.Org Video Driver, version 8.0
[    26.303] (II) LoadModule: "fbdev"
[    26.303] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    26.303] (II) Module fbdev: vendor="X.Org Foundation"
[    26.303] 	compiled for 1.8.99.905, module version = 0.4.2
[    26.303] 	ABI class: X.Org Video Driver, version 8.0
[    26.303] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
	Sandybridge, Sandybridge
[    26.304] (II) VESA: driver for VESA chipsets: vesa
[    26.304] (II) FBDEV: driver for framebuffer: fbdev
[    26.304] (++) using VT number 7

[    26.305] (WW) Falling back to old probe method for vesa
[    26.305] (WW) Falling back to old probe method for fbdev
[    26.305] (II) Loading sub module "fbdevhw"
[    26.305] (II) LoadModule: "fbdevhw"
[    26.305] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    26.306] (II) Module fbdevhw: vendor="X.Org Foundation"
[    26.306] 	compiled for 1.9.0, module version = 0.0.2
[    26.306] 	ABI class: X.Org Video Driver, version 8.0
[    26.306] drmOpenDevice: node name is /dev/dri/card0
[    26.306] drmOpenDevice: open result is 9, (OK)
[    26.306] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    26.306] drmOpenDevice: node name is /dev/dri/card0
[    26.306] drmOpenDevice: open result is 9, (OK)
[    26.306] drmOpenByBusid: drmOpenMinor returns 9
[    26.306] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[    26.306] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    26.306] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    26.306] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    26.306] (==) intel(0): RGB weight 888
[    26.306] (==) intel(0): Default visual is TrueColor
[    26.306] (II) intel(0): Integrated Graphics Chipset: Intel(R) Arrandale
[    26.306] (--) intel(0): Chipset: "Arrandale"
[    26.306] (**) intel(0): Framebuffer tiled
[    26.306] (**) intel(0): Pixmaps tiled
[    26.306] (**) intel(0): 3D buffers tiled
[    26.306] (**) intel(0): SwapBuffers wait enabled
[    26.306] (==) intel(0): video overlay key set to 0x101fe
[    26.323] (II) intel(0): Output VGA1 has no monitor section
[    26.323] (II) intel(0): Output LVDS1 has no monitor section
[    26.430] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
[    26.439] (II) intel(0): Output HDMI1 has no monitor section
[    26.440] (II) intel(0): Output DP1 has no monitor section
[    26.457] (II) intel(0): EDID for output VGA1
[    26.457] (II) intel(0): EDID for output LVDS1
[    26.457] (II) intel(0): Manufacturer: AUO  Model: 22ec  Serial#: 0
[    26.457] (II) intel(0): Year: 2009  Week: 1
[    26.457] (II) intel(0): EDID Version: 1.3
[    26.457] (II) intel(0): Digital Display Input
[    26.457] (II) intel(0): Max Image Size [cm]: horiz.: 34  vert.: 19
[    26.457] (II) intel(0): Gamma: 2.20
[    26.457] (II) intel(0): No DPMS capabilities specified
[    26.457] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    26.457] (II) intel(0): First detailed timing is preferred mode
[    26.457] (II) intel(0): redX: 0.620 redY: 0.340   greenX: 0.330 greenY: 0.570
[    26.457] (II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
[    26.457] (II) intel(0): Manufacturer's mask: 0
[    26.457] (II) intel(0): Supported detailed timing:
[    26.457] (II) intel(0): clock: 69.3 MHz   Image Size:  344 x 193 mm
[    26.457] (II) intel(0): h_active: 1366  h_sync: 1398  h_sync_end 1422 h_blank_end 1432 h_border: 0
[    26.457] (II) intel(0): v_active: 768  v_sync: 771  v_sync_end 775 v_blanking: 806 v_border: 0
[    26.457] (II) intel(0): Unknown vendor-specific block f
[    26.457] (II) intel(0):  AUO
[    26.457] (II) intel(0):  B156XW02 V2
[    26.457] (II) intel(0): EDID (in hex):
[    26.457] (II) intel(0): 	00ffffffffffff0006afec2200000000
[    26.457] (II) intel(0): 	01130103802213780ac8959e57549226
[    26.457] (II) intel(0): 	0f505400000001010101010101010101
[    26.457] (II) intel(0): 	010101010101121b5642500026302018
[    26.457] (II) intel(0): 	340058c1100000180000000f00000000
[    26.457] (II) intel(0): 	00000000000000000020000000fe0041
[    26.457] (II) intel(0): 	554f0a202020202020202020000000fe
[    26.457] (II) intel(0): 	004231353658573032205632200a00c0
[    26.457] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    26.457] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    26.458] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    26.458] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    26.458] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    26.458] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    26.458] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    26.458] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    26.458] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    26.458] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    26.458] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    26.458] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    26.458] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    26.458] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    26.458] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    26.458] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    26.458] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    26.458] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    26.458] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    26.458] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    26.458] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    26.458] (II) intel(0): Printing probed modes for output LVDS1
[    26.458] (II) intel(0): Modeline "1366x768"x60.0   69.30  1366 1398 1422 1432  768 771 775 806 -hsync -vsync (48.4 kHz)
[    26.458] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    26.458] (II) intel(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz)
[    26.458] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    26.458] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    26.458] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    26.458] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    26.467] (II) intel(0): EDID for output HDMI1
[    26.468] (II) intel(0): EDID for output DP1
[    26.468] (II) intel(0): Output VGA1 disconnected
[    26.468] (II) intel(0): Output LVDS1 connected
[    26.468] (II) intel(0): Output HDMI1 disconnected
[    26.468] (II) intel(0): Output DP1 disconnected
[    26.468] (II) intel(0): Using exact sizes for initial modes
[    26.468] (II) intel(0): Output LVDS1 using initial mode 1366x768
[    26.468] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    26.468] (II) intel(0): Kernel page flipping support detected, enabling
[    26.468] (==) intel(0): DPI set to (96, 96)
[    26.468] (II) Loading sub module "fb"
[    26.468] (II) LoadModule: "fb"
[    26.468] (II) Loading /usr/lib/xorg/modules/libfb.so
[    26.468] (II) Module fb: vendor="X.Org Foundation"
[    26.468] 	compiled for 1.9.0, module version = 1.0.0
[    26.468] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    26.468] (II) Loading sub module "dri2"
[    26.468] (II) LoadModule: "dri2"
[    26.469] (II) Reloading /usr/lib/xorg/modules/extensions/libdri2.so
[    26.469] (II) UnloadModule: "vesa"
[    26.469] (II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    26.469] (II) UnloadModule: "fbdev"
[    26.469] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    26.469] (II) UnloadModule: "fbdevhw"
[    26.469] (II) Unloading /usr/lib/xorg/modules/libfbdevhw.so
[    26.469] (==) Depth 24 pixmap format is 32 bpp
[    26.469] (II) intel(0): [DRI2] Setup complete
[    26.469] (II) intel(0): [DRI2]   DRI driver: i965
[    26.469] (II) intel(0): Allocated new frame buffer 1408x768 stride 5632, tiled
[    26.475] (II) UXA(0): Driver registered support for the following operations:
[    26.475] (II)         solid
[    26.475] (II)         copy
[    26.475] (II)         composite (RENDER acceleration)
[    26.475] (II)         put_image
[    26.475] (II)         get_image
[    26.475] (==) intel(0): Backing store disabled
[    26.475] (==) intel(0): Silken mouse enabled
[    26.475] (II) intel(0): Initializing HW Cursor
[    26.510] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    26.511] (==) intel(0): DPMS enabled
[    26.511] (==) intel(0): Intel XvMC decoder enabled
[    26.511] (II) intel(0): Set up textured video
[    26.511] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[    26.511] (II) intel(0): direct rendering: DRI2 Enabled
[    26.511] (==) intel(0): hotplug detection: "enabled"
[    26.511] (--) RandR disabled
[    26.511] (II) Initializing built-in extension Generic Event Extension
[    26.511] (II) Initializing built-in extension SHAPE
[    26.511] (II) Initializing built-in extension MIT-SHM
[    26.511] (II) Initializing built-in extension XInputExtension
[    26.511] (II) Initializing built-in extension XTEST
[    26.511] (II) Initializing built-in extension BIG-REQUESTS
[    26.511] (II) Initializing built-in extension SYNC
[    26.511] (II) Initializing built-in extension XKEYBOARD
[    26.511] (II) Initializing built-in extension XC-MISC
[    26.511] (II) Initializing built-in extension SECURITY
[    26.511] (II) Initializing built-in extension XINERAMA
[    26.511] (II) Initializing built-in extension XFIXES
[    26.511] (II) Initializing built-in extension RENDER
[    26.511] (II) Initializing built-in extension RANDR
[    26.511] (II) Initializing built-in extension COMPOSITE
[    26.511] (II) Initializing built-in extension DAMAGE
[    26.511] (II) Initializing built-in extension GESTURE
[    26.513] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
[    26.516] (II) intel(0): Setting screen physical size to 361 x 203
[    26.529] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    26.535] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    26.535] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    26.535] (II) LoadModule: "evdev"
[    26.535] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    26.535] (II) Module evdev: vendor="X.Org Foundation"
[    26.535] 	compiled for 1.9.0, module version = 2.3.2
[    26.535] 	Module class: X.Org XInput Driver
[    26.535] 	ABI class: X.Org XInput driver, version 11.0
[    26.535] (**) Power Button: always reports core events
[    26.535] (**) Power Button: Device: "/dev/input/event3"
[    26.571] (II) Power Button: Found keys
[    26.571] (II) Power Button: Configuring as keyboard
[    26.571] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    26.571] (**) Option "xkb_rules" "evdev"
[    26.571] (**) Option "xkb_model" "pc105"
[    26.571] (**) Option "xkb_layout" "ca"
[    26.571] (**) Option "xkb_variant" "eng"
[    26.573] (II) XKB: reuse xkmfile /var/lib/xkb/server-4BAE3EC55BAE54958C3D00FF1B2E21454ECF913F.xkm
[    26.573] (II) config/udev: Adding input device Video Bus (/dev/input/event7)
[    26.573] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    26.573] (**) Video Bus: always reports core events
[    26.573] (**) Video Bus: Device: "/dev/input/event7"
[    26.651] (II) Video Bus: Found keys
[    26.651] (II) Video Bus: Configuring as keyboard
[    26.652] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    26.652] (**) Option "xkb_rules" "evdev"
[    26.652] (**) Option "xkb_model" "pc105"
[    26.652] (**) Option "xkb_layout" "ca"
[    26.652] (**) Option "xkb_variant" "eng"
[    26.652] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    26.652] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    26.652] (**) Power Button: always reports core events
[    26.652] (**) Power Button: Device: "/dev/input/event0"
[    26.731] (II) Power Button: Found keys
[    26.731] (II) Power Button: Configuring as keyboard
[    26.732] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    26.732] (**) Option "xkb_rules" "evdev"
[    26.732] (**) Option "xkb_model" "pc105"
[    26.732] (**) Option "xkb_layout" "ca"
[    26.732] (**) Option "xkb_variant" "eng"
[    26.732] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[    26.732] (II) No input driver/identifier specified (ignoring)
[    26.732] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    26.732] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    26.732] (**) Sleep Button: always reports core events
[    26.732] (**) Sleep Button: Device: "/dev/input/event2"
[    26.801] (II) Sleep Button: Found keys
[    26.802] (II) Sleep Button: Configuring as keyboard
[    26.802] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    26.802] (**) Option "xkb_rules" "evdev"
[    26.802] (**) Option "xkb_model" "pc105"
[    26.802] (**) Option "xkb_layout" "ca"
[    26.802] (**) Option "xkb_variant" "eng"
[    26.803] (II) config/udev: Adding input device 1.3M WebCam (/dev/input/event6)
[    26.803] (**) 1.3M WebCam: Applying InputClass "evdev keyboard catchall"
[    26.803] (**) 1.3M WebCam: always reports core events
[    26.803] (**) 1.3M WebCam: Device: "/dev/input/event6"
[    26.831] (II) 1.3M WebCam: Found keys
[    26.832] (II) 1.3M WebCam: Configuring as keyboard
[    26.832] (II) XINPUT: Adding extended input device "1.3M WebCam" (type: KEYBOARD)
[    26.832] (**) Option "xkb_rules" "evdev"
[    26.832] (**) Option "xkb_model" "pc105"
[    26.832] (**) Option "xkb_layout" "ca"
[    26.832] (**) Option "xkb_variant" "eng"
[    26.833] (II) config/udev: Adding input device Logitech USB RECEIVER (/dev/input/event5)
[    26.833] (**) Logitech USB RECEIVER: Applying InputClass "evdev pointer catchall"
[    26.833] (**) Logitech USB RECEIVER: always reports core events
[    26.833] (**) Logitech USB RECEIVER: Device: "/dev/input/event5"
[    26.862] (II) Logitech USB RECEIVER: Found 20 mouse buttons
[    26.862] (II) Logitech USB RECEIVER: Found scroll wheel(s)
[    26.862] (II) Logitech USB RECEIVER: Found relative axes
[    26.862] (II) Logitech USB RECEIVER: Found x and y relative axes
[    26.862] (II) Logitech USB RECEIVER: Configuring as mouse
[    26.862] (**) Logitech USB RECEIVER: YAxisMapping: buttons 4 and 5
[    26.862] (**) Logitech USB RECEIVER: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    26.862] (II) XINPUT: Adding extended input device "Logitech USB RECEIVER" (type: MOUSE)
[    26.862] (II) Logitech USB RECEIVER: initialized for relative axes.
[    26.862] (II) config/udev: Adding input device Logitech USB RECEIVER (/dev/input/mouse0)
[    26.862] (II) No input driver/identifier specified (ignoring)
[    26.863] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    26.863] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    26.863] (**) AT Translated Set 2 keyboard: always reports core events
[    26.863] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    26.941] (II) AT Translated Set 2 keyboard: Found keys
[    26.942] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    26.942] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    26.942] (**) Option "xkb_rules" "evdev"
[    26.942] (**) Option "xkb_model" "pc105"
[    26.942] (**) Option "xkb_layout" "ca"
[    26.942] (**) Option "xkb_variant" "eng"
[    26.949] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/event8)
[    26.949] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchpad catchall"
[    26.949] (**) ETPS/2 Elantech Touchpad: Applying InputClass "touchpad catchall"
[    26.949] (II) LoadModule: "synaptics"
[    26.949] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    26.949] (II) Module synaptics: vendor="X.Org Foundation"
[    26.949] 	compiled for 1.9.0, module version = 1.2.2
[    26.949] 	Module class: X.Org XInput Driver
[    26.949] 	ABI class: X.Org XInput driver, version 11.0
[    26.949] (II) Synaptics touchpad driver version 1.2.2
[    26.949] (**) Option "Device" "/dev/input/event8"
[    27.271] (II) ETPS/2 Elantech Touchpad: x-axis range 8 - 1144
[    27.271] (II) ETPS/2 Elantech Touchpad: y-axis range 8 - 760
[    27.271] (II) ETPS/2 Elantech Touchpad: device does not report pressure, will use touch data.
[    27.271] (II) ETPS/2 Elantech Touchpad: finger width range 0 - 0
[    27.271] (II) ETPS/2 Elantech Touchpad: buttons: left right double triple
[    27.401] (--) ETPS/2 Elantech Touchpad: touchpad found
[    27.401] (**) ETPS/2 Elantech Touchpad: always reports core events
[    27.461] (II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD)
[    27.461] (**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
[    27.461] (**) ETPS/2 Elantech Touchpad: (accel) acceleration profile 0
[    27.461] (**) ETPS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
[    27.461] (**) ETPS/2 Elantech Touchpad: (accel) acceleration threshold: 4
[    27.571] (--) ETPS/2 Elantech Touchpad: touchpad found
[    27.571] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/mouse1)
[    27.571] (II) No input driver/identifier specified (ignoring)
[    28.736] (II) intel(0): EDID vendor "AUO", prod id 8940
[    28.736] (II) intel(0): Printing DDC gathered Modelines:
[    28.736] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1398 1422 1432  768 771 775 806 -hsync -vsync (48.4 kHz)
[    28.764] (II) intel(0): EDID vendor "AUO", prod id 8940
[    28.764] (II) intel(0): Printing DDC gathered Modelines:
[    28.764] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1398 1422 1432  768 771 775 806 -hsync -vsync (48.4 kHz)
[    28.792] (II) intel(0): EDID vendor "AUO", prod id 8940
[    28.792] (II) intel(0): Printing DDC gathered Modelines:
[    28.792] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1398 1422 1432  768 771 775 806 -hsync -vsync (48.4 kHz)
[    28.820] (II) intel(0): EDID vendor "AUO", prod id 8940
[    28.820] (II) intel(0): Printing DDC gathered Modelines:
[    28.820] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1398 1422 1432  768 771 775 806 -hsync -vsync (48.4 kHz)
[    34.536] (II) intel(0): EDID vendor "AUO", prod id 8940
[    34.536] (II) intel(0): Printing DDC gathered Modelines:
[    34.536] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1398 1422 1432  768 771 775 806 -hsync -vsync (48.4 kHz)
robert@Robert-aspire-5742:~$ 

```

---

### Post by Yellow Pasque on 2011-04-11
The nvidia proprietary driver somehow got installed and is interfering. I've seen a lot of this lately :\
```
sudo apt-get remove --purge nvidia*
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
```
Log out to restart X.

---

### Post by robertcoulson on 2011-04-11
Temüjin...YOU ARE THE MAN....It worked perfectly...Now I can play games but still can not access "extra visual effects"...That is ok, I can live with that...Thanks.
Robert

---

