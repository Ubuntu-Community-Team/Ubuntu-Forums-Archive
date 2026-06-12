---
title: "Maverick takes too long to boot (1.5 minutes!!)"
date: 2011-01-25
forum: General Help
---

### Post by vickychijwani on 2011-01-25
It's been a while since this problem started. I have an Acer Aspire 4720z laptop with Ubuntu 10.10 installed. My laptop takes a whole damn 1.5 minutes to boot up and login (measured according to bootchart; I have auto-login enabled) (The majority of this 1.5 minutes is taken up *after* boot up, so it might indicate a problem with Xorg.)

I don't know whether this is relevant, but when I boot up, a message gets displayed: "ata4.01: failed to resume link (SControl 0)". Also, this problem started right around the time I upgraded from Lucid to Maverick, so it could be some problem with my upgrade. Please help me find the source of this issue.

ATTACHED: bootchart image from last login.

boot.log:
```
fsck from util-linux-ng 2.17.2
udevd[370]: can not read '/etc/udev/rules.d/z80_user.rules'


/dev/sda6: clean, 562775/1171456 files, 3256169/4678923 blocks
init: ureadahead-other main process (653) terminated with status 4

 * Starting AppArmor profiles       [160G Cache read/write disabled: /sys/kernel/security/apparmor/features interface file missing. (Kernel needs AppArmor 2.4 compatibility patch.)
Cache read/write disabled: /sys/kernel/security/apparmor/features interface file missing. (Kernel needs AppArmor 2.4 compatibility patch.)
Warning from /etc/apparmor.d/sbin.dhclient3 (/etc/apparmor.d/sbin.dhclient3 line 73): profile /sbin/dhclient3 network rules not enforced
Cache read/write disabled: /sys/kernel/security/apparmor/features interface file missing. (Kernel needs AppArmor 2.4 compatibility patch.)
Warning from /etc/apparmor.d/gdm-guest-session (/etc/apparmor.d/gdm-guest-session line 48): profile /usr/share/gdm/guest-session/Xsession network rules not enforced
Cache read/write disabled: /sys/kernel/security/apparmor/features interface file missing. (Kernel needs AppArmor 2.4 compatibility patch.)
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
Cache read/write disabled: /sys/kernel/security/apparmor/features interface file missing. (Kernel needs AppArmor 2.4 compatibility patch.)
Warning from /etc/apparmor.d/usr.sbin.cupsd (/etc/apparmor.d/usr.sbin.cupsd line 165): profile /usr/lib/cups/backend/cups-pdf network rules not enforced
Warning from /etc/apparmor.d/usr.sbin.cupsd (/etc/apparmor.d/usr.sbin.cupsd line 165): profile /usr/sbin/cupsd network rules not enforced
Cache read/write disabled: /sys/kernel/security/apparmor/features interface file missing. (Kernel needs AppArmor 2.4 compatibility patch.)
Warning from /etc/apparmor.d/usr.sbin.mysqld (/etc/apparmor.d/usr.sbin.mysqld line 44): profile /usr/sbin/mysqld network rules not enforced
Cache read/write disabled: /sys/kernel/security/apparmor/features interface file missing. (Kernel needs AppArmor 2.4 compatibility patch.)
Warning from /etc/apparmor.d/usr.sbin.mysqld-akonadi (/etc/apparmor.d/usr.sbin.mysqld-akonadi line 24): profile /usr/sbin/mysqld-akonadi network rules not enforced
Cache read/write disabled: /sys/kernel/security/apparmor/features interface file missing. (Kernel needs AppArmor 2.4 compatibility patch.)
Warning from /etc/apparmor.d/usr.sbin.tcpdump (/etc/apparmor.d/usr.sbin.tcpdump line 51): profile /usr/sbin/tcpdump network rules not enforced

```

Xorg.0.log:
```
[    24.838] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    24.838] X Protocol Version 11, Revision 0
[    24.838] Build Operating System: Linux 2.6.24-28-server i686 Ubuntu
[    24.838] Current Operating System: Linux vicky-laptop 2.6.36-020636-generic #201010210905 SMP Thu Oct 21 10:17:53 UTC 2010 i686
[    24.838] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.36-020636-generic root=UUID=848716f4-25e3-4e91-871e-e2a355f4116b ro quiet splash
[    24.838] Build Date: 09 January 2011  12:14:58PM
[    24.838] xorg-server 2:1.9.0-0ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
[    24.838] Current version of pixman: 0.18.4
[    24.838] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    24.838] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    24.838] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Jan 25 09:49:38 2011
[    24.870] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    24.896] (==) No Layout section.  Using the first Screen section.
[    24.896] (==) No screen section available. Using defaults.
[    24.896] (**) |-->Screen "Default Screen Section" (0)
[    24.896] (**) |   |-->Monitor "<default monitor>"
[    24.896] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    24.896] (==) Automatically adding devices
[    24.896] (==) Automatically enabling devices
[    24.930] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    24.930] 	Entry deleted from font path.
[    25.003] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    25.003] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    25.003] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    25.003] (II) Loader magic: 0x81f9b00
[    25.003] (II) Module ABI versions:
[    25.003] 	X.Org ANSI C Emulation: 0.4
[    25.003] 	X.Org Video Driver: 8.0
[    25.003] 	X.Org XInput driver : 11.0
[    25.003] 	X.Org Server Extension : 4.0
[    25.005] (--) PCI:*(0:0:2:0) 8086:2a02:1025:011d rev 3, Mem @ 0xf0000000/1048576, 0xd0000000/268435456, I/O @ 0x00001800/8
[    25.005] (--) PCI: (0:0:2:1) 8086:2a03:1025:011d rev 3, Mem @ 0xf0100000/1048576
[    25.005] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    25.005] (II) LoadModule: "extmod"
[    25.082] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    25.094] (II) Module extmod: vendor="X.Org Foundation"
[    25.094] 	compiled for 1.9.0, module version = 1.0.0
[    25.094] 	Module class: X.Org Server Extension
[    25.094] 	ABI class: X.Org Server Extension, version 4.0
[    25.094] (II) Loading extension MIT-SCREEN-SAVER
[    25.094] (II) Loading extension XFree86-VidModeExtension
[    25.094] (II) Loading extension XFree86-DGA
[    25.094] (II) Loading extension DPMS
[    25.094] (II) Loading extension XVideo
[    25.094] (II) Loading extension XVideo-MotionCompensation
[    25.094] (II) Loading extension X-Resource
[    25.094] (II) LoadModule: "dbe"
[    25.095] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    25.098] (II) Module dbe: vendor="X.Org Foundation"
[    25.098] 	compiled for 1.9.0, module version = 1.0.0
[    25.098] 	Module class: X.Org Server Extension
[    25.098] 	ABI class: X.Org Server Extension, version 4.0
[    25.098] (II) Loading extension DOUBLE-BUFFER
[    25.098] (II) LoadModule: "glx"
[    25.098] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    25.109] (II) Module glx: vendor="X.Org Foundation"
[    25.109] 	compiled for 1.9.0, module version = 1.0.0
[    25.109] 	ABI class: X.Org Server Extension, version 4.0
[    25.110] (==) AIGLX enabled
[    25.111] (II) Loading extension GLX
[    25.111] (II) LoadModule: "record"
[    25.111] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    25.112] (II) Module record: vendor="X.Org Foundation"
[    25.112] 	compiled for 1.9.0, module version = 1.13.0
[    25.112] 	Module class: X.Org Server Extension
[    25.112] 	ABI class: X.Org Server Extension, version 4.0
[    25.112] (II) Loading extension RECORD
[    25.112] (II) LoadModule: "dri"
[    25.112] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    25.113] (II) Module dri: vendor="X.Org Foundation"
[    25.113] 	compiled for 1.9.0, module version = 1.0.0
[    25.113] 	ABI class: X.Org Server Extension, version 4.0
[    25.113] (II) Loading extension XFree86-DRI
[    25.113] (II) LoadModule: "dri2"
[    25.113] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    25.114] (II) Module dri2: vendor="X.Org Foundation"
[    25.114] 	compiled for 1.9.0, module version = 1.2.0
[    25.114] 	ABI class: X.Org Server Extension, version 4.0
[    25.114] (II) Loading extension DRI2
[    25.114] (==) Matched intel as autoconfigured driver 0
[    25.114] (==) Matched vesa as autoconfigured driver 1
[    25.114] (==) Matched fbdev as autoconfigured driver 2
[    25.114] (==) Assigned the driver to the xf86ConfigLayout
[    25.114] (II) LoadModule: "intel"
[    25.117] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    25.169] (II) Module intel: vendor="X.Org Foundation"
[    25.169] 	compiled for 1.9.0, module version = 2.12.0
[    25.169] 	Module class: X.Org Video Driver
[    25.169] 	ABI class: X.Org Video Driver, version 8.0
[    25.169] (II) LoadModule: "vesa"
[    25.170] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    25.211] (II) Module vesa: vendor="X.Org Foundation"
[    25.211] 	compiled for 1.8.99.905, module version = 2.3.0
[    25.211] 	Module class: X.Org Video Driver
[    25.211] 	ABI class: X.Org Video Driver, version 8.0
[    25.211] (II) LoadModule: "fbdev"
[    25.211] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    25.224] (II) Module fbdev: vendor="X.Org Foundation"
[    25.224] 	compiled for 1.8.99.905, module version = 0.4.2
[    25.224] 	ABI class: X.Org Video Driver, version 8.0
[    25.224] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
	Sandybridge, Sandybridge
[    25.225] (II) VESA: driver for VESA chipsets: vesa
[    25.225] (II) FBDEV: driver for framebuffer: fbdev
[    25.225] (++) using VT number 7

[    25.225] (WW) Falling back to old probe method for vesa
[    25.225] (WW) Falling back to old probe method for fbdev
[    25.225] (II) Loading sub module "fbdevhw"
[    25.226] (II) LoadModule: "fbdevhw"
[    25.226] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    25.233] (II) Module fbdevhw: vendor="X.Org Foundation"
[    25.233] 	compiled for 1.9.0, module version = 0.0.2
[    25.233] 	ABI class: X.Org Video Driver, version 8.0
[    25.252] drmOpenDevice: node name is /dev/dri/card0
[    25.252] drmOpenDevice: open result is 8, (OK)
[    25.252] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    25.252] drmOpenDevice: node name is /dev/dri/card0
[    25.252] drmOpenDevice: open result is 8, (OK)
[    25.252] drmOpenByBusid: drmOpenMinor returns 8
[    25.252] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    25.252] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    25.252] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    25.252] (==) intel(0): RGB weight 888
[    25.252] (==) intel(0): Default visual is TrueColor
[    25.252] (II) intel(0): Integrated Graphics Chipset: Intel(R) 965GM
[    25.253] (--) intel(0): Chipset: "965GM"
[    25.253] (==) intel(0): video overlay key set to 0x101fe
[    25.358] (II) intel(0): Output LVDS1 has no monitor section
[    25.358] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video1
[    25.380] (II) intel(0): Output VGA1 has no monitor section
[    25.630] (II) intel(0): Output TV1 has no monitor section
[    25.735] (II) intel(0): EDID for output LVDS1
[    25.735] (II) intel(0): Manufacturer: SEC  Model: 4442  Serial#: 0
[    25.735] (II) intel(0): Year: 2006  Week: 0
[    25.735] (II) intel(0): EDID Version: 1.3
[    25.735] (II) intel(0): Digital Display Input
[    25.735] (II) intel(0): Max Image Size [cm]: horiz.: 30  vert.: 19
[    25.735] (II) intel(0): Gamma: 2.20
[    25.735] (II) intel(0): No DPMS capabilities specified
[    25.735] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    25.735] (II) intel(0): First detailed timing is preferred mode
[    25.735] (II) intel(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
[    25.735] (II) intel(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
[    25.735] (II) intel(0): Manufacturer's mask: 0
[    25.735] (II) intel(0): Supported detailed timing:
[    25.735] (II) intel(0): clock: 68.9 MHz   Image Size:  303 x 190 mm
[    25.735] (II) intel(0): h_active: 1280  h_sync: 1292  h_sync_end 1356 h_blank_end 1408 h_border: 0
[    25.735] (II) intel(0): v_active: 800  v_sync: 803  v_sync_end 806 v_blanking: 816 v_border: 0
[    25.735] (II) intel(0): Unknown vendor-specific block f
[    25.735] (II) intel(0):  SAMSUNG
[    25.735] (II) intel(0):  LTN141W3-L01
[    25.735] (II) intel(0): EDID (in hex):
[    25.735] (II) intel(0): 	00ffffffffffff004ca3424400000000
[    25.735] (II) intel(0): 	00100103801e13780a87f594574f8c27
[    25.735] (II) intel(0): 	27505400000001010101010101010101
[    25.735] (II) intel(0): 	010101010101ee1a0080502010300c40
[    25.735] (II) intel(0): 	33002fbe100000190000000f00000000
[    25.735] (II) intel(0): 	00000000002387026400000000fe0053
[    25.735] (II) intel(0): 	414d53554e470a2020202020000000fe
[    25.735] (II) intel(0): 	004c544e31343157332d4c30310a0064
[    25.735] (II) intel(0): EDID vendor "SEC", prod id 17474
[    25.736] (II) intel(0): Printing DDC gathered Modelines:
[    25.736] (II) intel(0): Modeline "1280x800"x0.0   68.94  1280 1292 1356 1408  800 803 806 816 -hsync -vsync (49.0 kHz)
[    25.736] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    25.736] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    25.736] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    25.736] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    25.736] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    25.736] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    25.736] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    25.736] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    25.736] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    25.736] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    25.736] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    25.736] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    25.736] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    25.736] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    25.736] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    25.736] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    25.736] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    25.736] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    25.736] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    25.736] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    25.736] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    25.736] (II) intel(0): Printing probed modes for output LVDS1
[    25.736] (II) intel(0): Modeline "1280x800"x60.0   68.94  1280 1292 1356 1408  800 803 806 816 -hsync -vsync (49.0 kHz)
[    25.736] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    25.736] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    25.736] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    25.736] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    25.752] (II) intel(0): EDID for output VGA1
[    26.002] (II) intel(0): EDID for output TV1
[    26.002] (II) intel(0): Output LVDS1 connected
[    26.002] (II) intel(0): Output VGA1 disconnected
[    26.002] (II) intel(0): Output TV1 disconnected
[    26.002] (II) intel(0): Using exact sizes for initial modes
[    26.002] (II) intel(0): Output LVDS1 using initial mode 1280x800
[    26.002] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    26.002] (II) intel(0): Kernel page flipping support detected, but forcibly disabled.
[    26.002] (**) intel(0): Display dimensions: (300, 190) mm
[    26.002] (**) intel(0): DPI set to (108, 106)
[    26.002] (II) Loading sub module "fb"
[    26.002] (II) LoadModule: "fb"
[    26.002] (II) Loading /usr/lib/xorg/modules/libfb.so
[    26.536] (II) Module fb: vendor="X.Org Foundation"
[    26.536] 	compiled for 1.9.0, module version = 1.0.0
[    26.536] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    26.536] (II) UnloadModule: "vesa"
[    26.536] (II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    26.536] (II) UnloadModule: "fbdev"
[    26.536] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    26.536] (II) UnloadModule: "fbdevhw"
[    26.536] (II) Unloading /usr/lib/xorg/modules/libfbdevhw.so
[    26.536] (==) Depth 24 pixmap format is 32 bpp
[    26.537] (II) intel(0): [DRI2] Setup complete
[    26.537] (II) intel(0): [DRI2]   DRI driver: i965
[    26.537] (**) intel(0): Tiling enabled
[    26.537] (**) intel(0): SwapBuffers wait enabled
[    26.537] (==) intel(0): VideoRam: 262144 KB
[    26.537] (II) intel(0): Allocated new frame buffer 1280x800 stride 5120, tiled
[    26.759] (II) UXA(0): Driver registered support for the following operations:
[    26.759] (II)         solid
[    26.759] (II)         copy
[    26.759] (II)         composite (RENDER acceleration)
[    26.759] (II)         put_image
[    26.759] (II)         get_image
[    26.759] (==) intel(0): Backing store disabled
[    26.759] (==) intel(0): Silken mouse enabled
[    26.763] (II) intel(0): Initializing HW Cursor
[    26.786] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    26.793] (==) intel(0): DPMS enabled
[    26.793] (==) intel(0): Intel XvMC decoder enabled
[    26.793] (II) intel(0): Set up textured video
[    26.793] (II) intel(0): Set up overlay video
[    26.793] (II) intel(0): [XvMC] i965_xvmc driver initialized.
[    26.793] (II) intel(0): direct rendering: DRI2 Enabled
[    26.793] (--) RandR disabled
[    26.793] (II) Initializing built-in extension Generic Event Extension
[    26.793] (II) Initializing built-in extension SHAPE
[    26.793] (II) Initializing built-in extension MIT-SHM
[    26.793] (II) Initializing built-in extension XInputExtension
[    26.793] (II) Initializing built-in extension XTEST
[    26.793] (II) Initializing built-in extension BIG-REQUESTS
[    26.793] (II) Initializing built-in extension SYNC
[    26.793] (II) Initializing built-in extension XKEYBOARD
[    26.793] (II) Initializing built-in extension XC-MISC
[    26.793] (II) Initializing built-in extension SECURITY
[    26.793] (II) Initializing built-in extension XINERAMA
[    26.793] (II) Initializing built-in extension XFIXES
[    26.793] (II) Initializing built-in extension RENDER
[    26.793] (II) Initializing built-in extension RANDR
[    26.793] (II) Initializing built-in extension COMPOSITE
[    26.793] (II) Initializing built-in extension DAMAGE
[    26.793] (II) Initializing built-in extension GESTURE
[    27.714] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    27.714] (II) AIGLX: enabled GLX_INTEL_swap_event
[    27.714] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    27.714] (II) AIGLX: enabled GLX_SGI_make_current_read
[    27.714] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    27.714] (II) AIGLX: Loaded and initialized /usr/lib/dri/i965_dri.so
[    27.714] (II) GLX: Initialized DRI2 GL provider for screen 0
[    27.715] (II) intel(0): Setting screen physical size to 338 x 211
[    28.174] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    28.206] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    28.206] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    28.207] (II) LoadModule: "evdev"
[    28.207] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    28.297] (II) Module evdev: vendor="X.Org Foundation"
[    28.297] 	compiled for 1.9.0, module version = 2.3.2
[    28.297] 	Module class: X.Org XInput Driver
[    28.297] 	ABI class: X.Org XInput driver, version 11.0
[    28.297] (**) Power Button: always reports core events
[    28.297] (**) Power Button: Device: "/dev/input/event3"
[    28.304] (II) Power Button: Found keys
[    28.304] (II) Power Button: Configuring as keyboard
[    28.304] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    28.304] (**) Option "xkb_rules" "evdev"
[    28.304] (**) Option "xkb_model" "pc105"
[    28.304] (**) Option "xkb_layout" "us"
[    28.304] (**) Option "xkb_options" "ctrl:swapcaps,compose:menu"
[    28.308] (II) XKB: reuse xkmfile /var/lib/xkb/server-EF4890335543DB66DB1E17867CACCCE11910BA5E.xkm
[    28.545] (II) config/udev: Adding input device Video Bus (/dev/input/event7)
[    28.545] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    28.545] (**) Video Bus: always reports core events
[    28.545] (**) Video Bus: Device: "/dev/input/event7"
[    28.548] (II) Video Bus: Found keys
[    28.548] (II) Video Bus: Configuring as keyboard
[    28.548] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    28.548] (**) Option "xkb_rules" "evdev"
[    28.548] (**) Option "xkb_model" "pc105"
[    28.548] (**) Option "xkb_layout" "us"
[    28.548] (**) Option "xkb_options" "ctrl:swapcaps,compose:menu"
[    28.551] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    28.551] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    28.551] (**) Power Button: always reports core events
[    28.551] (**) Power Button: Device: "/dev/input/event1"
[    28.551] (II) Power Button: Found keys
[    28.551] (II) Power Button: Configuring as keyboard
[    28.551] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    28.551] (**) Option "xkb_rules" "evdev"
[    28.551] (**) Option "xkb_model" "pc105"
[    28.551] (**) Option "xkb_layout" "us"
[    28.552] (**) Option "xkb_options" "ctrl:swapcaps,compose:menu"
[    28.552] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    28.552] (II) No input driver/identifier specified (ignoring)
[    28.553] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    28.553] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    28.553] (**) Sleep Button: always reports core events
[    28.553] (**) Sleep Button: Device: "/dev/input/event2"
[    28.556] (II) Sleep Button: Found keys
[    28.556] (II) Sleep Button: Configuring as keyboard
[    28.556] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    28.556] (**) Option "xkb_rules" "evdev"
[    28.556] (**) Option "xkb_model" "pc105"
[    28.556] (**) Option "xkb_layout" "us"
[    28.556] (**) Option "xkb_options" "ctrl:swapcaps,compose:menu"
[    28.561] (II) config/udev: Adding input device Acer Crystal Eye webcam (/dev/input/event5)
[    28.561] (**) Acer Crystal Eye webcam: Applying InputClass "evdev keyboard catchall"
[    28.561] (**) Acer Crystal Eye webcam: always reports core events
[    28.561] (**) Acer Crystal Eye webcam: Device: "/dev/input/event5"
[    28.561] (II) Acer Crystal Eye webcam: Found keys
[    28.562] (II) Acer Crystal Eye webcam: Configuring as keyboard
[    28.562] (II) XINPUT: Adding extended input device "Acer Crystal Eye webcam" (type: KEYBOARD)
[    28.562] (**) Option "xkb_rules" "evdev"
[    28.562] (**) Option "xkb_model" "pc105"
[    28.562] (**) Option "xkb_layout" "us"
[    28.562] (**) Option "xkb_options" "ctrl:swapcaps,compose:menu"
[    28.567] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    28.567] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    28.567] (**) AT Translated Set 2 keyboard: always reports core events
[    28.567] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    28.576] (II) AT Translated Set 2 keyboard: Found keys
[    28.576] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    28.576] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    28.576] (**) Option "xkb_rules" "evdev"
[    28.576] (**) Option "xkb_model" "pc105"
[    28.576] (**) Option "xkb_layout" "us"
[    28.576] (**) Option "xkb_options" "ctrl:swapcaps,compose:menu"
[    28.577] (II) config/udev: Adding input device PS/2 Synaptics TouchPad (/dev/input/event6)
[    28.577] (**) PS/2 Synaptics TouchPad: Applying InputClass "evdev pointer catchall"
[    28.577] (**) PS/2 Synaptics TouchPad: always reports core events
[    28.577] (**) PS/2 Synaptics TouchPad: Device: "/dev/input/event6"
[    28.577] (II) PS/2 Synaptics TouchPad: Found 3 mouse buttons
[    28.577] (II) PS/2 Synaptics TouchPad: Found relative axes
[    28.577] (II) PS/2 Synaptics TouchPad: Found x and y relative axes
[    28.577] (II) PS/2 Synaptics TouchPad: Configuring as mouse
[    28.577] (**) PS/2 Synaptics TouchPad: YAxisMapping: buttons 4 and 5
[    28.577] (**) PS/2 Synaptics TouchPad: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    28.577] (II) XINPUT: Adding extended input device "PS/2 Synaptics TouchPad" (type: MOUSE)
[    28.577] (II) PS/2 Synaptics TouchPad: initialized for relative axes.
[    28.578] (II) config/udev: Adding input device PS/2 Synaptics TouchPad (/dev/input/mouse0)
[    28.578] (II) No input driver/identifier specified (ignoring)
[    43.270] (II) intel(0): EDID vendor "SEC", prod id 17474
[    43.270] (II) intel(0): Printing DDC gathered Modelines:
[    43.270] (II) intel(0): Modeline "1280x800"x0.0   68.94  1280 1292 1356 1408  800 803 806 816 -hsync -vsync (49.0 kHz)
[    43.679] (II) intel(0): EDID vendor "SEC", prod id 17474
[    43.679] (II) intel(0): Printing DDC gathered Modelines:
[    43.679] (II) intel(0): Modeline "1280x800"x0.0   68.94  1280 1292 1356 1408  800 803 806 816 -hsync -vsync (49.0 kHz)
[    44.059] (II) intel(0): EDID vendor "SEC", prod id 17474
[    44.059] (II) intel(0): Printing DDC gathered Modelines:
[    44.059] (II) intel(0): Modeline "1280x800"x0.0   68.94  1280 1292 1356 1408  800 803 806 816 -hsync -vsync (49.0 kHz)
[    44.442] (II) intel(0): EDID vendor "SEC", prod id 17474
[    44.442] (II) intel(0): Printing DDC gathered Modelines:
[    44.442] (II) intel(0): Modeline "1280x800"x0.0   68.94  1280 1292 1356 1408  800 803 806 816 -hsync -vsync (49.0 kHz)
[    47.318] (II) intel(0): EDID vendor "SEC", prod id 17474
[    47.611] (II) intel(0): Printing DDC gathered Modelines:
[    47.611] (II) intel(0): Modeline "1280x800"x0.0   68.94  1280 1292 1356 1408  800 803 806 816 -hsync -vsync (49.0 kHz)
[    71.567] (II) intel(0): EDID vendor "SEC", prod id 17474
[    71.567] (II) intel(0): Printing DDC gathered Modelines:
[    71.568] (II) intel(0): Modeline "1280x800"x0.0   68.94  1280 1292 1356 1408  800 803 806 816 -hsync -vsync (49.0 kHz)
[   674.552] (II) AIGLX: Suspending AIGLX clients for VT switch
[   679.296] (II) Open ACPI successful (/var/run/acpid.socket)
[   679.296] (II) AIGLX: Resuming AIGLX clients after VT switch
[   679.296] (EE) intel(0): Couldn't create pixmap for fbcon
[   679.417] (II) intel(0): EDID vendor "SEC", prod id 17474
[   679.417] (II) intel(0): Printing DDC gathered Modelines:
[   679.417] (II) intel(0): Modeline "1280x800"x0.0   68.94  1280 1292 1356 1408  800 803 806 816 -hsync -vsync (49.0 kHz)
[   679.824] (II) Power Button: Device reopened after 1 attempts.
[   679.832] (II) Video Bus: Device reopened after 1 attempts.
[   679.840] (II) Power Button: Device reopened after 1 attempts.
[   679.840] (II) Sleep Button: Device reopened after 1 attempts.
[   679.840] (II) Acer Crystal Eye webcam: Device reopened after 1 attempts.
[   679.844] (II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
[   679.844] (II) PS/2 Synaptics TouchPad: Device reopened after 1 attempts.
[  1112.188] (II) AIGLX: Suspending AIGLX clients for VT switch
[  1115.839] (II) Open ACPI successful (/var/run/acpid.socket)
[  1115.839] (II) AIGLX: Resuming AIGLX clients after VT switch
[  1115.839] (EE) intel(0): Couldn't create pixmap for fbcon
[  1115.969] (II) intel(0): EDID vendor "SEC", prod id 17474
[  1115.969] (II) intel(0): Printing DDC gathered Modelines:
[  1115.969] (II) intel(0): Modeline "1280x800"x0.0   68.94  1280 1292 1356 1408  800 803 806 816 -hsync -vsync (49.0 kHz)
[  1116.372] (II) Power Button: Device reopened after 1 attempts.
[  1116.372] (II) Video Bus: Device reopened after 1 attempts.
[  1116.372] (II) Power Button: Device reopened after 1 attempts.
[  1116.392] (II) Sleep Button: Device reopened after 1 attempts.
[  1116.400] (II) Acer Crystal Eye webcam: Device reopened after 1 attempts.
[  1116.400] (II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
[  1116.400] (II) PS/2 Synaptics TouchPad: Device reopened after 1 attempts.
[  1128.204] (II) AIGLX: Suspending AIGLX clients for VT switch
[  1130.926] (II) Open ACPI successful (/var/run/acpid.socket)
[  1130.930] (II) AIGLX: Resuming AIGLX clients after VT switch
[  1130.937] (EE) intel(0): Couldn't create pixmap for fbcon
[  1131.063] (II) intel(0): EDID vendor "SEC", prod id 17474
[  1131.063] (II) intel(0): Printing DDC gathered Modelines:
[  1131.063] (II) intel(0): Modeline "1280x800"x0.0   68.94  1280 1292 1356 1408  800 803 806 816 -hsync -vsync (49.0 kHz)
[  1131.500] (II) Power Button: Device reopened after 1 attempts.
[  1131.500] (II) Video Bus: Device reopened after 1 attempts.
[  1131.500] (II) Power Button: Device reopened after 1 attempts.
[  1131.504] (II) Sleep Button: Device reopened after 1 attempts.
[  1131.504] (II) Acer Crystal Eye webcam: Device reopened after 1 attempts.
[  1131.504] (II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
[  1131.512] (II) PS/2 Synaptics TouchPad: Device reopened after 1 attempts.
[  1185.900] (II) AIGLX: Suspending AIGLX clients for VT switch
[  1191.311] (II) Open ACPI successful (/var/run/acpid.socket)
[  1191.311] (II) AIGLX: Resuming AIGLX clients after VT switch
[  1191.311] (EE) intel(0): Couldn't create pixmap for fbcon
[  1191.438] (II) intel(0): EDID vendor "SEC", prod id 17474
[  1191.438] (II) intel(0): Printing DDC gathered Modelines:
[  1191.438] (II) intel(0): Modeline "1280x800"x0.0   68.94  1280 1292 1356 1408  800 803 806 816 -hsync -vsync (49.0 kHz)
[  1191.908] (II) Power Button: Device reopened after 1 attempts.
[  1191.924] (II) Video Bus: Device reopened after 1 attempts.
[  1191.924] (II) Power Button: Device reopened after 1 attempts.
[  1191.924] (II) Sleep Button: Device reopened after 1 attempts.
[  1191.928] (II) Acer Crystal Eye webcam: Device reopened after 1 attempts.
[  1191.928] (II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
[  1191.928] (II) PS/2 Synaptics TouchPad: Device reopened after 1 attempts.
[  1202.788] (II) AIGLX: Suspending AIGLX clients for VT switch
[  1204.602] (II) Open ACPI successful (/var/run/acpid.socket)
[  1204.603] (II) AIGLX: Resuming AIGLX clients after VT switch
[  1204.603] (EE) intel(0): Couldn't create pixmap for fbcon
[  1204.720] (II) intel(0): EDID vendor "SEC", prod id 17474
[  1204.721] (II) intel(0): Printing DDC gathered Modelines:
[  1204.721] (II) intel(0): Modeline "1280x800"x0.0   68.94  1280 1292 1356 1408  800 803 806 816 -hsync -vsync (49.0 kHz)
[  1205.116] (II) Power Button: Device reopened after 1 attempts.
[  1205.128] (II) Video Bus: Device reopened after 1 attempts.
[  1205.128] (II) Power Button: Device reopened after 1 attempts.
[  1205.128] (II) Sleep Button: Device reopened after 1 attempts.
[  1205.136] (II) Acer Crystal Eye webcam: Device reopened after 1 attempts.
[  1205.136] (II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
[  1205.137] (II) PS/2 Synaptics TouchPad: Device reopened after 1 attempts.
[  1216.492] (II) AIGLX: Suspending AIGLX clients for VT switch
[  1230.359] (II) Open ACPI successful (/var/run/acpid.socket)
[  1230.359] (II) AIGLX: Resuming AIGLX clients after VT switch
[  1230.359] (EE) intel(0): Couldn't create pixmap for fbcon
[  1230.469] (II) intel(0): EDID vendor "SEC", prod id 17474
[  1230.469] (II) intel(0): Printing DDC gathered Modelines:
[  1230.469] (II) intel(0): Modeline "1280x800"x0.0   68.94  1280 1292 1356 1408  800 803 806 816 -hsync -vsync (49.0 kHz)
[  1230.864] (II) Power Button: Device reopened after 1 attempts.
[  1230.876] (II) Video Bus: Device reopened after 1 attempts.
[  1230.880] (II) Power Button: Device reopened after 1 attempts.
[  1230.880] (II) Sleep Button: Device reopened after 1 attempts.
[  1230.884] (II) Acer Crystal Eye webcam: Device reopened after 1 attempts.
[  1230.912] (II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
[  1230.912] (II) PS/2 Synaptics TouchPad: Device reopened after 1 attempts.
```

---

### Post by rocthrttle on 2011-01-25
check your sata compatibility mode in your BIOS. AHCI doesnt play nice with ubuntu. try something other than AHCI. i saw huge boot times on a toshiba netbook until i changed it to "compatible" mode.

---

### Post by vickychijwani on 2011-01-25
> **rocthrttle said:**
> check your sata compatibility mode in your BIOS. AHCI doesnt play nice with ubuntu. try something other than AHCI. i saw huge boot times on a toshiba netbook until i changed it to "compatible" mode.

Thanks for your reply.

My SATA mode is set to IDE. The only other option is AHCI, which you said not to use (I tried it anyway. It had no effect on the boot time, but the message "ata4.01: failed to resume link (SControl 0)" didn't come up). Any other suggestions? I really do hate having to wait so long for my laptop to boot. ](*,)

---

### Post by Elfy on 2011-01-25
Check the dmesg log and see if the lag is shown there - these are the time stamps [    24.838] - there's could be a large gap possiblity.

It might be worth removing the quiet splash from the boot - you might see the lag then.

Try turning of the autologin - then you'll be able to determine whether the lag is before or after login.

---

### Post by vickychijwani on 2011-01-25
Let me first tell you that I'm kind of a newbie with Linux, so even if there is something significant to see, it's not apparent to me right now.

> **forestpiskie said:**
> Check the dmesg log and see if the lag is shown there - these are the time stamps [    24.838] - there's could be a large gap possiblity.

My dmesg log ends with "[   23.919471] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready"; there's no entry at [   24.838].

dmesg log:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.36-020636-generic (root@zinc) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #201010210905 SMP Thu Oct 21 10:17:53 UTC 2010
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007f6d0000 (usable)
[    0.000000]  BIOS-e820: 000000007f6d0000 - 000000007f6e1000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007f6e1000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled: non-PAE kernel!
[    0.000000] DMI present.
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x7f6d0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-D3FFF write-protect
[    0.000000]   D4000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 07F700000 mask FFFF00000 uncachable
[    0.000000]   2 base 07F800000 mask FFF800000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000002000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (reserved)
[    0.000000]  modified: 0000000000001000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007f6d0000 (usable)
[    0.000000]  modified: 000000007f6d0000 - 000000007f6e1000 (ACPI NVS)
[    0.000000]  modified: 000000007f6e1000 - 0000000080000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  modified: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] found SMP MP-table at [c00f7b80] f7b80
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 15000-1a000
[    0.000000] RAMDISK: 37585000 - 37ff0000
[    0.000000] Allocated new RAMDISK: 009da000 - 014448bd
[    0.000000] Move RAMDISK from 0000000037585000 - 0000000037fef8bc to 009da000 - 014448bc
[    0.000000] ACPI: RSDP 000f7b50 00024 (v02 PTLTD )
[    0.000000] ACPI: XSDT 7f6d3047 0007C (v01 PTLTD  ? XSDT   06040000  LTP 00000000)
[    0.000000] ACPI: FACP 7f6ddda0 000F4 (v03 INTEL  CRESTLNE 06040000 ALAN 00000001)
[    0.000000] ACPI: DSDT 7f6d4f57 08DD5 (v02 INTEL  CRESTLNE 06040000 MSFT 03000001)
[    0.000000] ACPI: FACS 7f6e0fc0 00040
[    0.000000] ACPI: APIC 7f6dde94 00068 (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: HPET 7f6ddefc 00038 (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: MCFG 7f6ddf34 0003C (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: APIC 7f6ddf70 00068 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT 7f6ddfd8 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SSDT 7f6d4908 0064F (v01 SataRe  SataPri 00001000 INTL 20050624)
[    0.000000] ACPI: SSDT 7f6d426c 0069C (v01 SataRe  SataSec 00001000 INTL 20050624)
[    0.000000] ACPI: SSDT 7f6d364f 0025F (v01  PmRef  Cpu0Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT 7f6d35a9 000A6 (v01  PmRef  Cpu1Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT 7f6d30c3 004E6 (v01  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1150MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000001 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007f6d0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000001 -> 0x00000002
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007f6d0
[    0.000000] On node 0 totalpages: 521824
[    0.000000] free_area_init_node: node 0, pgdat c0822bc0, node_mem_map c1446020
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3952 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2302 pages used for memmap
[    0.000000]   HighMem zone: 292308 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] early_res array is doubled to 64 at [16000 - 167ff]
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
[    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:60000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c2800000 s32896 r0 d24448 u2097152
[    0.000000] pcpu-alloc: s32896 r0 d24448 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 517746
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.36-020636-generic root=UUID=848716f4-25e3-4e91-871e-e2a355f4116b ro
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 10438700 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Subtract (54 early reservations)
[    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
[    0.000000]   #2 [0000100000 - 00009d5824]   TEXT DATA BSS
[    0.000000]   #3 [00009d6000 - 00009d9150]             BRK
[    0.000000]   #4 [00000f7b90 - 0000100000]   BIOS reserved
[    0.000000]   #5 [00000f7b80 - 00000f7b90]    MP-table mpf
[    0.000000]   #6 [000009f800 - 000009fd71]   BIOS reserved
[    0.000000]   #7 [000009fedd - 00000f7b80]   BIOS reserved
[    0.000000]   #8 [000009fd71 - 000009fedd]    MP-table mpc
[    0.000000]   #9 [0000010000 - 0000011000]      TRAMPOLINE
[    0.000000]   #10 [0000011000 - 0000015000]     ACPI WAKEUP
[    0.000000]   #11 [0000015000 - 0000016000]         PGTABLE
[    0.000000]   #12 [00009da000 - 0001445000]     NEW RAMDISK
[    0.000000]   #13 [0001445000 - 0001446000]         BOOTMEM
[    0.000000]   #14 [0001446000 - 0002436000]         BOOTMEM
[    0.000000]   #15 [0002436000 - 0002436004]         BOOTMEM
[    0.000000]   #16 [0002436040 - 0002436100]         BOOTMEM
[    0.000000]   #17 [0002436100 - 0002436154]         BOOTMEM
[    0.000000]   #18 [0002436180 - 0002439180]         BOOTMEM
[    0.000000]   #19 [0002439180 - 00024391ec]         BOOTMEM
[    0.000000]   #20 [0002439200 - 000243f200]         BOOTMEM
[    0.000000]   #21 [000243f200 - 000243f225]         BOOTMEM
[    0.000000]   #22 [000243f240 - 000243f267]         BOOTMEM
[    0.000000]   #23 [000243f280 - 000243f45c]         BOOTMEM
[    0.000000]   #24 [000243f480 - 000243f4c0]         BOOTMEM
[    0.000000]   #25 [000243f4c0 - 000243f500]         BOOTMEM
[    0.000000]   #26 [000243f500 - 000243f540]         BOOTMEM
[    0.000000]   #27 [000243f540 - 000243f580]         BOOTMEM
[    0.000000]   #28 [000243f580 - 000243f5c0]         BOOTMEM
[    0.000000]   #29 [000243f5c0 - 000243f600]         BOOTMEM
[    0.000000]   #30 [000243f600 - 000243f640]         BOOTMEM
[    0.000000]   #31 [000243f640 - 000243f680]         BOOTMEM
[    0.000000]   #32 [000243f680 - 000243f6c0]         BOOTMEM
[    0.000000]   #33 [000243f6c0 - 000243f700]         BOOTMEM
[    0.000000]   #34 [000243f700 - 000243f740]         BOOTMEM
[    0.000000]   #35 [000243f740 - 000243f780]         BOOTMEM
[    0.000000]   #36 [000243f780 - 000243f7c0]         BOOTMEM
[    0.000000]   #37 [000243f7c0 - 000243f800]         BOOTMEM
[    0.000000]   #38 [000243f800 - 000243f810]         BOOTMEM
[    0.000000]   #39 [000243f840 - 000243f850]         BOOTMEM
[    0.000000]   #40 [000243f880 - 000243f8e1]         BOOTMEM
[    0.000000]   #41 [000243f900 - 000243f961]         BOOTMEM
[    0.000000]   #42 [0002800000 - 000280e000]         BOOTMEM
[    0.000000]   #43 [0002a00000 - 0002a0e000]         BOOTMEM
[    0.000000]   #44 [0002441980 - 0002441984]         BOOTMEM
[    0.000000]   #45 [00024419c0 - 00024419c4]         BOOTMEM
[    0.000000]   #46 [0002441a00 - 0002441a08]         BOOTMEM
[    0.000000]   #47 [0002441a40 - 0002441a48]         BOOTMEM
[    0.000000]   #48 [0002441a80 - 0002441b28]         BOOTMEM
[    0.000000]   #49 [0002441b40 - 0002441ba8]         BOOTMEM
[    0.000000]   #50 [0002441bc0 - 0002445bc0]         BOOTMEM
[    0.000000]   #51 [0002445bc0 - 00024c5bc0]         BOOTMEM
[    0.000000]   #52 [00024c5bc0 - 0002505bc0]         BOOTMEM
[    0.000000]   #53 [0002a0e000 - 000340282c]         BOOTMEM
[    0.000000] Initializing HighMem for node 0 (000377fe:0007f6d0)
[    0.000000] Memory: 2040076k/2087744k available (5000k kernel code, 47220k reserved, 2406k data, 740k init, 1178440k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc083c000 - 0xc08f5000   ( 740 kB)
[    0.000000]       .data : 0xc05e2039 - 0xc083bb28   (2406 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05e2039   (5000 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] 	Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1866.823 MHz processor.
[    0.004006] Calibrating delay loop (skipped), value calculated using timer frequency.. 3733.64 BogoMIPS (lpj=7467292)
[    0.004118] pid_max: default: 32768 minimum: 301
[    0.004193] Security Framework initialized
[    0.004269] AppArmor: AppArmor initialized
[    0.004375] Mount-cache hash table entries: 512
[    0.004588] Initializing cgroup subsys ns
[    0.004644] Initializing cgroup subsys cpuacct
[    0.004701] Initializing cgroup subsys memory
[    0.004764] Initializing cgroup subsys devices
[    0.004818] Initializing cgroup subsys freezer
[    0.004871] Initializing cgroup subsys net_cls
[    0.004961] CPU: Physical Processor ID: 0
[    0.005012] CPU: Processor Core ID: 0
[    0.005065] mce: CPU supports 6 MCE banks
[    0.005126] CPU0: Thermal monitoring handled by SMI
[    0.005130] using mwait in idle threads.
[    0.005190] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.005350] PEBS disabled due to CPU errata.
[    0.005408] ... version:                2
[    0.005459] ... bit width:              40
[    0.005511] ... generic registers:      2
[    0.005564] ... value mask:             000000ffffffffff
[    0.005620] ... max period:             000000007fffffff
[    0.005674] ... fixed-purpose events:   3
[    0.005727] ... event mask:             0000000700000003
[    0.011254] ACPI: Core revision 20100702
[    0.028011] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.028073] ftrace: allocating 26011 entries in 51 pages
[    0.036069] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.036508] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.078389] CPU0: Intel(R) Pentium(R) Dual  CPU  T2390  @ 1.86GHz stepping 0d
[    0.080000] Booting Node   0, Processors  #1 Ok.
[    0.008000] Initializing CPU#1
[    0.008000] CPU1: Thermal monitoring handled by SMI
[    0.168020] Brought up 2 CPUs
[    0.168124] Total of 2 processors activated (7467.11 BogoMIPS).
[    0.168763] devtmpfs: initialized
[    0.169130] regulator: core version 0.5
[    0.169219] Time: 13:55:10  Date: 01/25/11
[    0.169319] NET: Registered protocol family 16
[    0.169506] EISA bus registered
[    0.169566] ACPI: bus type pci registered
[    0.169704] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.169779] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.169836] PCI: Using MMCONFIG for extended config space
[    0.169891] PCI: Using configuration type 1 for base access
[    0.172375] bio: create slab <bio-0> at 0
[    0.174098] ACPI: EC: Look up EC in DSDT
[    0.180046] ACPI: BIOS _OSI(Linux) query ignored
[    0.181614] ACPI: SSDT 7f6d3f2a 0027A (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.182289] ACPI: Dynamic OEM Table Load:
[    0.182410] ACPI: SSDT (null) 0027A (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.182903] ACPI: SSDT 7f6d38ae 005F7 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.183551] ACPI: Dynamic OEM Table Load:
[    0.183670] ACPI: SSDT (null) 005F7 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.184441] ACPI: SSDT 7f6d41a4 000C8 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.185102] ACPI: Dynamic OEM Table Load:
[    0.185221] ACPI: SSDT (null) 000C8 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.185527] ACPI: SSDT 7f6d3ea5 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.186176] ACPI: Dynamic OEM Table Load:
[    0.186294] ACPI: SSDT (null) 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.204112] ACPI: Interpreter enabled
[    0.204168] ACPI: (supports S0 S3 S4 S5)
[    0.204373] ACPI: Using IOAPIC for interrupt routing
[    0.211089] ACPI: EC: GPE = 0x18, I/O: command/status = 0x66, data = 0x62
[    0.211635] ACPI: No dock devices found.
[    0.211691] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.212510] ACPI Error (psargs-0359): [CDW1] Namespace lookup failure, AE_NOT_FOUND
[    0.212651] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7020270), AE_NOT_FOUND
[    0.212835] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.214302] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.214361] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.214420] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.214491] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    0.214562] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    0.214632] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff]
[    0.214704] pci_root PNP0A08:00: host bridge window [mem 0x80000000-0xdfffffff]
[    0.214775] pci_root PNP0A08:00: host bridge window [mem 0xf0000000-0xfebfffff]
[    0.214932] pci 0000:00:02.0: reg 10: [mem 0xf0000000-0xf00fffff 64bit]
[    0.214945] pci 0000:00:02.0: reg 18: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.214954] pci 0000:00:02.0: reg 20: [io  0x1800-0x1807]
[    0.215012] pci 0000:00:02.1: reg 10: [mem 0xf0100000-0xf01fffff 64bit]
[    0.215179] pci 0000:00:1a.0: reg 20: [io  0x1820-0x183f]
[    0.215287] pci 0000:00:1a.1: reg 20: [io  0x1840-0x185f]
[    0.215373] pci 0000:00:1a.7: reg 10: [mem 0xf0704000-0xf07043ff]
[    0.215477] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.215484] pci 0000:00:1a.7: PME# disabled
[    0.215540] pci 0000:00:1b.0: reg 10: [mem 0xf0500000-0xf0503fff 64bit]
[    0.215638] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.215644] pci 0000:00:1b.0: PME# disabled
[    0.215774] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.215780] pci 0000:00:1c.0: PME# disabled
[    0.215914] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.215920] pci 0000:00:1c.1: PME# disabled
[    0.216063] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.216068] pci 0000:00:1c.2: PME# disabled
[    0.216170] pci 0000:00:1d.0: reg 20: [io  0x1860-0x187f]
[    0.216294] pci 0000:00:1d.1: reg 20: [io  0x1880-0x189f]
[    0.216422] pci 0000:00:1d.2: reg 20: [io  0x18a0-0x18bf]
[    0.216508] pci 0000:00:1d.7: reg 10: [mem 0xf0704400-0xf07047ff]
[    0.216610] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.216617] pci 0000:00:1d.7: PME# disabled
[    0.216846] pci 0000:00:1f.0: quirk: [io  0x1000-0x107f] claimed by ICH6 ACPI/GPIO/TCO
[    0.216920] pci 0000:00:1f.0: quirk: [io  0x1180-0x11bf] claimed by ICH6 GPIO
[    0.216981] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0680 (mask 007f)
[    0.217054] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 0600 (mask 003f)
[    0.217129] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 4 PIO at 0068 (mask 0007)
[    0.217258] pci 0000:00:1f.1: reg 10: [io  0x0000-0x0007]
[    0.217272] pci 0000:00:1f.1: reg 14: [io  0x0000-0x0003]
[    0.217286] pci 0000:00:1f.1: reg 18: [io  0x0000-0x0007]
[    0.217300] pci 0000:00:1f.1: reg 1c: [io  0x0000-0x0003]
[    0.217315] pci 0000:00:1f.1: reg 20: [io  0x1810-0x181f]
[    0.217389] pci 0000:00:1f.2: reg 10: [io  0x1c00-0x1c07]
[    0.217403] pci 0000:00:1f.2: reg 14: [io  0x18f4-0x18f7]
[    0.217417] pci 0000:00:1f.2: reg 18: [io  0x18f8-0x18ff]
[    0.217432] pci 0000:00:1f.2: reg 1c: [io  0x18f0-0x18f3]
[    0.217446] pci 0000:00:1f.2: reg 20: [io  0x18e0-0x18ef]
[    0.217460] pci 0000:00:1f.2: reg 24: [io  0x18d0-0x18df]
[    0.217501] pci 0000:00:1f.2: PME# supported from D3hot
[    0.217507] pci 0000:00:1f.2: PME# disabled
[    0.217541] pci 0000:00:1f.3: reg 10: [mem 0x00000000-0x000000ff]
[    0.217591] pci 0000:00:1f.3: reg 20: [io  0x1c20-0x1c3f]
[    0.217703] pci 0000:00:1c.0: PCI bridge to [bus 02-03]
[    0.217762] pci 0000:00:1c.0:   bridge window [io  0x0000-0x0000] (disabled)
[    0.217769] pci 0000:00:1c.0:   bridge window [mem 0x00000000-0x000fffff] (disabled)
[    0.217779] pci 0000:00:1c.0:   bridge window [mem 0x00000000-0x000fffff pref] (disabled)
[    0.218168] pci 0000:04:00.0: reg 10: [mem 0x00000000-0x00003fff 64bit]
[    0.218461] pci 0000:04:00.0: supports D1 D2
[    0.218464] pci 0000:04:00.0: PME# supported from D0 D3hot D3cold
[    0.218476] pci 0000:04:00.0: PME# disabled
[    0.218656] pci 0000:00:1c.1: PCI bridge to [bus 04-04]
[    0.218714] pci 0000:00:1c.1:   bridge window [io  0x0000-0x0000] (disabled)
[    0.218720] pci 0000:00:1c.1:   bridge window [mem 0x00000000-0x000fffff] (disabled)
[    0.218729] pci 0000:00:1c.1:   bridge window [mem 0x00000000-0x000fffff pref] (disabled)
[    0.218974] pci 0000:05:00.0: reg 10: [mem 0x00000000-0x0000ffff 64bit]
[    0.219283] pci 0000:05:00.0: PME# supported from D3hot D3cold
[    0.219296] pci 0000:05:00.0: PME# disabled
[    0.219447] pci 0000:00:1c.2: PCI bridge to [bus 05-05]
[    0.219505] pci 0000:00:1c.2:   bridge window [io  0x0000-0x0000] (disabled)
[    0.219512] pci 0000:00:1c.2:   bridge window [mem 0x00000000-0x000fffff] (disabled)
[    0.219521] pci 0000:00:1c.2:   bridge window [mem 0x00000000-0x000fffff pref] (disabled)
[    0.219607] pci 0000:0a:09.0: proprietary Ricoh MMC controller disabled (via firewire function)
[    0.219679] pci 0000:0a:09.0: MMC cards are now supported by standard SDHCI controller
[    0.219766] pci 0000:0a:09.0: reg 10: [mem 0xf0400000-0xf04007ff]
[    0.219862] pci 0000:0a:09.0: supports D1 D2
[    0.219865] pci 0000:0a:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.219871] pci 0000:0a:09.0: PME# disabled
[    0.219918] pci 0000:0a:09.1: reg 10: [mem 0xf0400800-0xf04008ff]
[    0.220025] pci 0000:0a:09.1: supports D1 D2
[    0.220028] pci 0000:0a:09.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.220034] pci 0000:0a:09.1: PME# disabled
[    0.220082] pci 0000:0a:09.2: reg 10: [mem 0xf0401000-0xf04010ff]
[    0.220179] pci 0000:0a:09.2: supports D1 D2
[    0.220182] pci 0000:0a:09.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.220188] pci 0000:0a:09.2: PME# disabled
[    0.220233] pci 0000:0a:09.3: reg 10: [mem 0xf0401400-0xf04014ff]
[    0.220331] pci 0000:0a:09.3: supports D1 D2
[    0.220334] pci 0000:0a:09.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.220340] pci 0000:0a:09.3: PME# disabled
[    0.220400] pci 0000:00:1e.0: PCI bridge to [bus 0a-0a] (subtractive decode)
[    0.220461] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.220468] pci 0000:00:1e.0:   bridge window [mem 0xf0400000-0xf04fffff]
[    0.220478] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.220481] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.220485] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.220488] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.220492] pci 0000:00:1e.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.220495] pci 0000:00:1e.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.220499] pci 0000:00:1e.0:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    0.220502] pci 0000:00:1e.0:   bridge window [mem 0x80000000-0xdfffffff] (subtractive decode)
[    0.220506] pci 0000:00:1e.0:   bridge window [mem 0xf0000000-0xfebfffff] (subtractive decode)
[    0.220538] pci_bus 0000:00: on NUMA node 0
[    0.220542] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.220870] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.220951] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.221026] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.221148] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.221245] ACPI Error (psargs-0359): [CDW1] Namespace lookup failure, AE_NOT_FOUND
[    0.221383] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7020270), AE_NOT_FOUND
[    0.230813] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[    0.231342] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.231912] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.232421] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.232992] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.233599] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.234125] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.234697] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 *7 11 12 14 15)
[    0.235180] HEST: Table is not found!
[    0.235314] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.235405] vgaarb: loaded
[    0.235651] SCSI subsystem initialized
[    0.235724] libata version 3.00 loaded.
[    0.235724] usbcore: registered new interface driver usbfs
[    0.235724] usbcore: registered new interface driver hub
[    0.236012] usbcore: registered new device driver usb
[    0.236431] ACPI: WMI: Mapper loaded
[    0.236484] PCI: Using ACPI for IRQ routing
[    0.236539] PCI: pci_cache_line_size set to 64 bytes
[    0.237138] reserve RAM buffer: 0000000000002000 - 000000000000ffff 
[    0.237141] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
[    0.237144] reserve RAM buffer: 000000007f6d0000 - 000000007fffffff 
[    0.237262] NetLabel: Initializing
[    0.237314] NetLabel:  domain hash size = 128
[    0.237367] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.237432] NetLabel:  unlabeled traffic allowed by default
[    0.237525] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.237588] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.237774] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.244026] Switching to clocksource tsc
[    0.253501] AppArmor: AppArmor Filesystem Enabled
[    0.253581] pnp: PnP ACPI init
[    0.253659] ACPI: bus type pnp registered
[    0.256215] pnp: PnP ACPI: found 11 devices
[    0.256270] ACPI: ACPI bus type pnp unregistered
[    0.256325] PnPBIOS: Disabled by ACPI PNP
[    0.256390] system 00:01: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.256449] system 00:01: [mem 0xfed14000-0xfed17fff] has been reserved
[    0.256508] system 00:01: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.256565] system 00:01: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.256623] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.256682] system 00:01: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.256740] system 00:01: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.256798] system 00:01: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.256860] system 00:04: [mem 0xfed00000-0xfed003ff] has been reserved
[    0.256924] system 00:06: [io  0x0680-0x069f] has been reserved
[    0.256981] system 00:06: [io  0x0800-0x080f] has been reserved
[    0.257038] system 00:06: [io  0x1000-0x107f] has been reserved
[    0.257094] system 00:06: [io  0x1180-0x11bf] has been reserved
[    0.257151] system 00:06: [io  0x1640-0x164f] has been reserved
[    0.257208] system 00:06: [io  0xfe00] has been reserved
[    0.293712] pci 0000:00:1c.0: BAR 14: assigned [mem 0x80000000-0x801fffff]
[    0.293774] pci 0000:00:1c.0: BAR 15: assigned [mem 0x80200000-0x803fffff 64bit pref]
[    0.293847] pci 0000:00:1c.1: BAR 14: assigned [mem 0x80400000-0x805fffff]
[    0.293907] pci 0000:00:1c.1: BAR 15: assigned [mem 0x80600000-0x807fffff 64bit pref]
[    0.294890] pci 0000:00:1c.2: BAR 14: assigned [mem 0x80800000-0x809fffff]
[    0.294950] pci 0000:00:1c.2: BAR 15: assigned [mem 0x80a00000-0x80bfffff 64bit pref]
[    0.295024] pci 0000:00:1c.0: BAR 13: assigned [io  0x2000-0x2fff]
[    0.295082] pci 0000:00:1c.1: BAR 13: assigned [io  0x3000-0x3fff]
[    0.295139] pci 0000:00:1c.2: BAR 13: assigned [io  0x4000-0x4fff]
[    0.295198] pci 0000:00:1f.3: BAR 0: assigned [mem 0x80c00000-0x80c000ff]
[    0.295260] pci 0000:00:1f.3: BAR 0: set to [mem 0x80c00000-0x80c000ff] (PCI address [0x80c00000-0x80c000ff]
[    0.295335] pci 0000:00:1c.0: PCI bridge to [bus 02-03]
[    0.295392] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.295454] pci 0000:00:1c.0:   bridge window [mem 0x80000000-0x801fffff]
[    0.295516] pci 0000:00:1c.0:   bridge window [mem 0x80200000-0x803fffff 64bit pref]
[    0.295593] pci 0000:04:00.0: BAR 0: assigned [mem 0x80400000-0x80403fff 64bit]
[    0.295878] pci 0000:04:00.0: BAR 0: set to [mem 0x80400000-0x80403fff 64bit] (PCI address [0x80400000-0x80403fff]
[    0.295954] pci 0000:00:1c.1: PCI bridge to [bus 04-04]
[    0.296011] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    0.296072] pci 0000:00:1c.1:   bridge window [mem 0x80400000-0x805fffff]
[    0.296133] pci 0000:00:1c.1:   bridge window [mem 0x80600000-0x807fffff 64bit pref]
[    0.296212] pci 0000:05:00.0: BAR 0: assigned [mem 0x80800000-0x8080ffff 64bit]
[    0.296337] pci 0000:05:00.0: BAR 0: set to [mem 0x80800000-0x8080ffff 64bit] (PCI address [0x80800000-0x8080ffff]
[    0.296413] pci 0000:00:1c.2: PCI bridge to [bus 05-05]
[    0.296470] pci 0000:00:1c.2:   bridge window [io  0x4000-0x4fff]
[    0.296532] pci 0000:00:1c.2:   bridge window [mem 0x80800000-0x809fffff]
[    0.296593] pci 0000:00:1c.2:   bridge window [mem 0x80a00000-0x80bfffff 64bit pref]
[    0.296671] pci 0000:00:1e.0: PCI bridge to [bus 0a-0a]
[    0.296726] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.296786] pci 0000:00:1e.0:   bridge window [mem 0xf0400000-0xf04fffff]
[    0.296847] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.296920] pci 0000:00:1c.0: enabling device (0000 -> 0003)
[    0.296981]   alloc irq_desc for 17 on node -1
[    0.296983]   alloc kstat_irqs on node -1
[    0.296992] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.297055] pci 0000:00:1c.0: setting latency timer to 64
[    0.297067] pci 0000:00:1c.1: enabling device (0000 -> 0003)
[    0.297124]   alloc irq_desc for 16 on node -1
[    0.297126]   alloc kstat_irqs on node -1
[    0.297132] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.297194] pci 0000:00:1c.1: setting latency timer to 64
[    0.297206] pci 0000:00:1c.2: enabling device (0000 -> 0003)
[    0.297263]   alloc irq_desc for 18 on node -1
[    0.297265]   alloc kstat_irqs on node -1
[    0.297270] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.297333] pci 0000:00:1c.2: setting latency timer to 64
[    0.297343] pci 0000:00:1e.0: setting latency timer to 64
[    0.297348] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.297351] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.297354] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.297357] pci_bus 0000:00: resource 7 [mem 0x000d4000-0x000d7fff]
[    0.297360] pci_bus 0000:00: resource 8 [mem 0x000d8000-0x000dbfff]
[    0.297363] pci_bus 0000:00: resource 9 [mem 0x000dc000-0x000dffff]
[    0.297367] pci_bus 0000:00: resource 10 [mem 0x80000000-0xdfffffff]
[    0.297370] pci_bus 0000:00: resource 11 [mem 0xf0000000-0xfebfffff]
[    0.297373] pci_bus 0000:02: resource 0 [io  0x2000-0x2fff]
[    0.297376] pci_bus 0000:02: resource 1 [mem 0x80000000-0x801fffff]
[    0.297379] pci_bus 0000:02: resource 2 [mem 0x80200000-0x803fffff 64bit pref]
[    0.297383] pci_bus 0000:04: resource 0 [io  0x3000-0x3fff]
[    0.297386] pci_bus 0000:04: resource 1 [mem 0x80400000-0x805fffff]
[    0.297389] pci_bus 0000:04: resource 2 [mem 0x80600000-0x807fffff 64bit pref]
[    0.297392] pci_bus 0000:05: resource 0 [io  0x4000-0x4fff]
[    0.297395] pci_bus 0000:05: resource 1 [mem 0x80800000-0x809fffff]
[    0.297398] pci_bus 0000:05: resource 2 [mem 0x80a00000-0x80bfffff 64bit pref]
[    0.297402] pci_bus 0000:0a: resource 1 [mem 0xf0400000-0xf04fffff]
[    0.297405] pci_bus 0000:0a: resource 4 [io  0x0000-0x0cf7]
[    0.297408] pci_bus 0000:0a: resource 5 [io  0x0d00-0xffff]
[    0.297410] pci_bus 0000:0a: resource 6 [mem 0x000a0000-0x000bffff]
[    0.297413] pci_bus 0000:0a: resource 7 [mem 0x000d4000-0x000d7fff]
[    0.297416] pci_bus 0000:0a: resource 8 [mem 0x000d8000-0x000dbfff]
[    0.297419] pci_bus 0000:0a: resource 9 [mem 0x000dc000-0x000dffff]
[    0.297423] pci_bus 0000:0a: resource 10 [mem 0x80000000-0xdfffffff]
[    0.297426] pci_bus 0000:0a: resource 11 [mem 0xf0000000-0xfebfffff]
[    0.297473] NET: Registered protocol family 2
[    0.297611] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.297984] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.298606] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.299026] TCP: Hash tables configured (established 131072 bind 65536)
[    0.299084] TCP reno registered
[    0.299137] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.299205] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.299400] NET: Registered protocol family 1
[    0.299491] pci 0000:00:02.0: Boot video device
[    0.299962] PCI: CLS 64 bytes, default 64
[    0.300034] Trying to unpack rootfs image as initramfs...
[    0.625066] Freeing initrd memory: 10668k freed
[    0.632822] Simple Boot Flag at 0x35 set to 0x1
[    0.633134] cpufreq-nforce2: No nForce2 chipset.
[    0.633227] Scanning for low memory corruption every 60 seconds
[    0.633487] audit: initializing netlink socket (disabled)
[    0.633560] type=2000 audit(1295963710.628:1): initialized
[    0.645343] highmem bounce pool size: 64 pages
[    0.645406] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.647225] VFS: Disk quotas dquot_6.5.2
[    0.647351] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.648126] fuse init (API version 7.15)
[    0.648290] msgmni has been set to 1703
[    0.648599] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.648672] io scheduler noop registered
[    0.648725] io scheduler deadline registered
[    0.648792] io scheduler cfq registered (default)
[    0.649058] ACPI Error (psargs-0359): [CDW1] Namespace lookup failure, AE_NOT_FOUND
[    0.649201] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7020270), AE_NOT_FOUND
[    0.649425] ACPI Error (psargs-0359): [CDW1] Namespace lookup failure, AE_NOT_FOUND
[    0.649567] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7020270), AE_NOT_FOUND
[    0.649786] ACPI Error (psargs-0359): [CDW1] Namespace lookup failure, AE_NOT_FOUND
[    0.649928] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7020270), AE_NOT_FOUND
[    0.650159] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.650239] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.650415] intel_idle: MWAIT substates: 0x1110
[    0.650417] intel_idle: does not run on family 6 model 15
[    0.650782] ACPI: AC Adapter [ACAD] (on-line)
[    0.650939] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.651059] ACPI: Lid Switch [LID]
[    0.651164] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.651240] ACPI: Power Button [PWRB]
[    0.651340] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    0.651415] ACPI: Sleep Button [SLPB]
[    0.651516] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.651588] ACPI: Power Button [PWRF]
[    0.651876] ACPI: acpi_idle registered with cpuidle
[    0.655112] Monitor-Mwait will be used to enter C-1 state
[    0.655138] Monitor-Mwait will be used to enter C-2 state
[    0.655160] Monitor-Mwait will be used to enter C-3 state
[    0.655167] Marking TSC unstable due to TSC halts in idle
[    0.655282] Switching to clocksource hpet
[    0.658908] thermal LNXTHERM:01: registered as thermal_zone0
[    0.658974] ACPI: Thermal Zone [THRM] (58 C)
[    0.659102] ERST: Table is not found!
[    0.659131] ACPI: Battery Slot [BAT1] (battery absent)
[    0.659224] isapnp: Scanning for PnP cards...
[    1.013524] isapnp: No Plug & Play device found
[    1.013854] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.015777] brd: module loaded
[    1.016519] loop: module loaded
[    1.016800] ata_piix 0000:00:1f.1: version 2.13
[    1.016818]   alloc irq_desc for 19 on node -1
[    1.016820]   alloc kstat_irqs on node -1
[    1.016830] ata_piix 0000:00:1f.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.016937] ata_piix 0000:00:1f.1: setting latency timer to 64
[    1.017058] scsi0 : ata_piix
[    1.017224] scsi1 : ata_piix
[    1.017956] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[    1.018016] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[    1.018102] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.018194] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    1.172061] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.172130] scsi2 : ata_piix
[    1.172267] scsi3 : ata_piix
[    1.173504] ata3: SATA max UDMA/133 cmd 0x1c00 ctl 0x18f4 bmdma 0x18e0 irq 19
[    1.173575] ata4: SATA max UDMA/133 cmd 0x18f8 ctl 0x18f0 bmdma 0x18e8 irq 19
[    1.174062] Fixed MDIO Bus: probed
[    1.174163] PPP generic driver version 2.4.2
[    1.174276] tun: Universal TUN/TAP device driver, 1.6
[    1.174336] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.174499] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.174587] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.174670] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    1.174675] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    1.174779] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    1.174895] ehci_hcd 0000:00:1a.7: debug port 1
[    1.178830] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
[    1.178851] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf0704000
[    1.184020] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    1.184224] hub 1-0:1.0: USB hub found
[    1.184282] hub 1-0:1.0: 4 ports detected
[    1.184437]   alloc irq_desc for 23 on node -1
[    1.184440]   alloc kstat_irqs on node -1
[    1.184448] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.184522] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.184526] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.184626] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    1.184730] ehci_hcd 0000:00:1d.7: debug port 1
[    1.188658] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    1.189023] ata1.00: ATAPI: HL-DT-ST DVDRAM GSA-T40N, JP01, max UDMA/33
[    1.189026] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf0704400
[    1.204246] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.204254] ata1.00: configured for UDMA/33
[    1.204535] hub 2-0:1.0: USB hub found
[    1.204593] hub 2-0:1.0: 6 ports detected
[    1.204742] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.204816] uhci_hcd: USB Universal Host Controller Interface driver
[    1.204909] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.204974] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.204978] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    1.205079] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    1.205191] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001820
[    1.205394] hub 3-0:1.0: USB hub found
[    1.205451] hub 3-0:1.0: 2 ports detected
[    1.205586]   alloc irq_desc for 21 on node -1
[    1.205589]   alloc kstat_irqs on node -1
[    1.205596] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.205661] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    1.205666] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    1.205758] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    1.205869] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001840
[    1.206068] hub 4-0:1.0: USB hub found
[    1.206125] hub 4-0:1.0: 2 ports detected
[    1.206259] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.206323] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.206327] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.206425] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    1.206554] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001860
[    1.206763] hub 5-0:1.0: USB hub found
[    1.206820] hub 5-0:1.0: 2 ports detected
[    1.206955] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.207020] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.207024] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.207121] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    1.207221] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001880
[    1.207469] hub 6-0:1.0: USB hub found
[    1.207525] hub 6-0:1.0: 2 ports detected
[    1.207657] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.207721] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.207725] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.207821] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    1.207922] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018a0
[    1.208172] hub 7-0:1.0: USB hub found
[    1.209061] hub 7-0:1.0: 2 ports detected
[    1.209283] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.209851] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T40N  JP01 PQ: 0 ANSI: 5
[    1.212457] i8042.c: Detected active multiplexing controller, rev 1.1.
[    1.213761] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.213822] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.213883] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.213944] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.214005] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.214148] mice: PS/2 mouse device common for all mice
[    1.214399] rtc_cmos 00:07: RTC can wake from S4
[    1.214511] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    1.214605] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.214781] device-mapper: uevent: version 1.0.3
[    1.214993] device-mapper: ioctl: 4.18.0-ioctl (2010-06-29) initialised: dm-devel@redhat.com
[    1.215172] device-mapper: multipath: version 1.1.1 loaded
[    1.215231] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.215439] EISA: Probing bus 0 at eisa.0
[    1.215494] EISA: Cannot allocate resource for mainboard
[    1.215550] Cannot allocate resource for EISA slot 1
[    1.215606] Cannot allocate resource for EISA slot 2
[    1.215692] Cannot allocate resource for EISA slot 3
[    1.215747] Cannot allocate resource for EISA slot 4
[    1.215802] Cannot allocate resource for EISA slot 5
[    1.215857] Cannot allocate resource for EISA slot 6
[    1.215913] Cannot allocate resource for EISA slot 7
[    1.215967] Cannot allocate resource for EISA slot 8
[    1.216043] EISA: Detected 0 cards.
[    1.216250] cpuidle: using governor ladder
[    1.216455] cpuidle: using governor menu
[    1.216927] TCP cubic registered
[    1.217133] NET: Registered protocol family 10
[    1.217648] lo: Disabled Privacy Extensions
[    1.218016] NET: Registered protocol family 17
[    1.218116] Registering the dns_resolver key type
[    1.218877] Using IPI No-Shortcut mode
[    1.219038] PM: Resume from disk failed.
[    1.219054] registered taskstats version 1
[    1.219928]   Magic number: 11:117:939
[    1.220125] rtc_cmos 00:07: setting system clock to 2011-01-25 13:55:11 UTC (1295963711)
[    1.220199] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.220256] EDD information not available.
[    1.221499] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.221571] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.221752] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.221828] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.244137] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.516074] usb 2-3: new high speed USB device using ehci_hcd and address 2
[    1.968153] ata3.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.968227] ata3.01: SATA link down (SStatus 0 SControl 300)
[    2.024056] ata3.00: ATA-8: WDC WD1600BEVT-22ZCT0, 11.01A11, max UDMA/133
[    2.024114] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.041314] ata3.00: configured for UDMA/133
[    2.041537] scsi 2:0:0:0: Direct-Access     ATA      WDC WD1600BEVT-2 11.0 PQ: 0 ANSI: 5
[    2.041756] sd 2:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    2.041767] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    2.042045] sd 2:0:0:0: [sda] Write Protect is off
[    2.042099] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.042167] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.075353]  sda: sda1 sda2 < sda5 sda6 > sda3 sda4
[    2.076048] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.128046] usb 6-2: new low speed USB device using uhci_hcd and address 2
[    2.520045] ata4.01: failed to resume link (SControl 0)
[    2.531328] ata4.00: SATA link down (SStatus 0 SControl 300)
[    2.531402] ata4.01: SATA link down (SStatus 0 SControl 0)
[    2.531547] Freeing unused kernel memory: 740k freed
[    2.532103] Write protecting the kernel text: 5004k
[    2.532220] Write protecting the kernel read-only data: 2048k
[    2.570671] udev[92]: starting version 163
[    2.731943] sdhci: Secure Digital Host Controller Interface driver
[    2.732064] sdhci: Copyright(c) Pierre Ossman
[    2.734243] sdhci-pci 0000:0a:09.1: SDHCI controller found [1180:0822] (rev 22)
[    2.734344] sdhci-pci 0000:0a:09.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.735452] sdhci-pci 0000:0a:09.1: Will use DMA mode even though HW doesn't fully claim to support it.
[    2.735568] mmc0: no vmmc regulator found
[    2.742380] tg3.c:v3.113 (August 2, 2010)
[    2.742508] tg3 0000:05:00.0: enabling device (0000 -> 0002)
[    2.742611] tg3 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.742688] tg3 0000:05:00.0: setting latency timer to 64
[    2.772219] Registered led device: mmc0::
[    2.778014] mmc0: SDHCI controller on PCI [0000:0a:09.1] using DMA
[    2.778624] firewire_ohci 0000:0a:09.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.821535] tg3 0000:05:00.0: eth0: Tigon3 [partno(BCM95787m) rev b002] (PCI Express) MAC address 00:1e:68:b7:ba:ea
[    2.821616] tg3 0000:05:00.0: eth0: attached PHY is 5787 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[    2.821690] tg3 0000:05:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    2.821761] tg3 0000:05:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    2.835172] usbcore: registered new interface driver hiddev
[    2.850945] input:  USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:1d.1/usb6/6-2/6-2:1.0/input/input5
[    2.851160] generic-usb 0003:15D9:0A4C.0001: input,hidraw0: USB HID v1.11 Mouse [ USB OPTICAL MOUSE] on usb-0000:00:1d.1-2/input0
[    2.851264] usbcore: registered new interface driver usbhid
[    2.851330] usbhid: USB HID core driver
[    2.864136] firewire_ohci: Added fw-ohci device 0000:0a:09.0, OHCI v1.10, 4 IR + 4 IT contexts, quirks 0x1
[    3.232480] EXT3-fs: barriers not enabled
[    3.245239] kjournald starting.  Commit interval 5 seconds
[    3.245291] EXT3-fs (sda6): mounted filesystem with ordered data mode
[    3.364168] firewire_core: created device fw0: GUID 00241b0083dc2301, S400
[    5.553230] Adding 2249064k swap on /dev/sda5.  Priority:-1 extents:1 across:2249064k 
[    6.481624] EXT3-fs (sda6): using internal journal
[    7.218249] udev[378]: starting version 163
[    8.588295] EXT4-fs (sda4): warning: maximal mount count reached, running e2fsck is recommended
[    8.588913] EXT4-fs (sda4): mounted filesystem with ordered data mode. Opts: (null)
[    9.444052] type=1400 audit(1295943919.720:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=535 comm="apparmor_parser"
[    9.444137] type=1400 audit(1295943919.720:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=535 comm="apparmor_parser"
[    9.444200] type=1400 audit(1295943919.720:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=535 comm="apparmor_parser"
[   11.648046] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.650833] lp: driver loaded but no devices found
[   11.704757] lib80211: common routines for IEEE802.11 drivers
[   11.704762] lib80211_crypt: registered algorithm 'NULL'
[   11.833926] Linux video capture interface: v2.00
[   12.032704] Linux agpgart interface v0.103
[   12.147689] uvcvideo: Found UVC 1.00 device Acer Crystal Eye webcam (064e:a103)
[   12.164193] input: Acer Crystal Eye webcam as /devices/pci0000:00/0000:00:1d.7/usb2/2-3/2-3:1.0/input/input6
[   12.164275] usbcore: registered new interface driver uvcvideo
[   12.164278] USB Video Class driver (v0.1.0)
[   12.262531] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
[   12.263172] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
[   12.269520] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[   12.326900] [drm] Initialized drm 1.1.0 20060810
[   12.592289] wl: module license 'MIXED/Proprietary' taints kernel.
[   12.592294] Disabling lock debugging due to kernel taint
[   12.602304] wl 0000:04:00.0: enabling device (0000 -> 0002)
[   12.602320] wl 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.602341] wl 0000:04:00.0: setting latency timer to 64
[   12.782104] r852 0000:0a:09.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   12.782370] r852: driver loaded succesfully
[   12.871782] lib80211_crypt: registered algorithm 'TKIP'
[   12.872414] eth1: Broadcom BCM4315 802.11 Hybrid Wireless Controller 5.60.48.36 
[   12.965436] input: PS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input7
[   13.386766] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.386774] i915 0000:00:02.0: setting latency timer to 64
[   13.410408]   alloc irq_desc for 40 on node -1
[   13.410413]   alloc kstat_irqs on node -1
[   13.410426] i915 0000:00:02.0: irq 40 for MSI/MSI-X
[   13.410442] [drm] set up 7M of stolen space
[   13.516721] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   13.517038] [drm] initialized overlay support
[   14.231974] Console: switching to colour frame buffer device 160x50
[   14.237616] fb0: inteldrmfb frame buffer device
[   14.237618] drm: registered panic notifier
[   14.248972] acpi device:03: registered as cooling_device2
[   14.257141] acpi device:04: registered as cooling_device3
[   14.257994] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input8
[   14.258187] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   14.258358] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   14.258426]   alloc irq_desc for 22 on node -1
[   14.258429]   alloc kstat_irqs on node -1
[   14.258440] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   14.258521]   alloc irq_desc for 41 on node -1
[   14.258524]   alloc kstat_irqs on node -1
[   14.258539] HDA Intel 0000:00:1b.0: irq 41 for MSI/MSI-X
[   14.258579] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   14.420624] hda_codec: ALC268: BIOS auto-probing.
[   16.238852] type=1400 audit(1295943926.512:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=841 comm="apparmor_parser"
[   16.238940] type=1400 audit(1295943926.512:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=841 comm="apparmor_parser"
[   16.239009] type=1400 audit(1295943926.512:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=841 comm="apparmor_parser"
[   16.346258] type=1400 audit(1295943926.620:8): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=840 comm="apparmor_parser"
[   17.641896] type=1400 audit(1295943927.916:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=853 comm="apparmor_parser"
[   17.642110] type=1400 audit(1295943927.916:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=853 comm="apparmor_parser"
[   17.674886] type=1400 audit(1295943927.948:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=861 comm="apparmor_parser"
[   17.675101] type=1400 audit(1295943927.948:12): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=861 comm="apparmor_parser"
[   17.814502] type=1400 audit(1295943928.088:13): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld" pid=867 comm="apparmor_parser"
[   17.935891] type=1400 audit(1295943928.208:14): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld-akonadi" pid=868 comm="apparmor_parser"
[   18.129655] ppdev: user-space parallel port driver
[   22.216034]   alloc irq_desc for 42 on node -1
[   22.216040]   alloc kstat_irqs on node -1
[   22.217266] tg3 0000:05:00.0: irq 42 for MSI/MSI-X
[   22.386769] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.900122] audit_printk_skb: 3 callbacks suppressed
[   22.900127] type=1400 audit(1295943933.176:16): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=842 comm="apparmor_parser"
[   22.900958] type=1400 audit(1295943933.176:17): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=842 comm="apparmor_parser"
[   22.901714] type=1400 audit(1295943933.176:18): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=842 comm="apparmor_parser"
[   23.919243] tg3 0000:05:00.0: eth0: Link is up at 100 Mbps, full duplex
[   23.919248] tg3 0000:05:00.0: eth0: Flow control is on for TX and on for RX
[   23.919471] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

```

> **forestpiskie said:**
> It might be worth removing the quiet splash from the boot - you might see the lag then.

Did that. So I get loads of messages during boot, instead of the splash screen, but there's nothing particularly interesting there.

> **forestpiskie said:**
> Try turning of the autologin - then you'll be able to determine whether the lag is before or after login.

Did that too. I then timed my boot with a stopwatch: 50 seconds to the login screen, followed by another 1 minute 10 seconds to the desktop. That makes it a total of 2 minutes! :(

---

### Post by Peps88 on 2011-06-06
I have the same problem with ubuntu maverick.
Itried to update kernel at version 2.6.39.1 and at /var./log/boot.log there are the same apparmor errors.
```
 * Starting AppArmor profiles       [128G Cache read/write disabled: /sys/kernel/security/apparmor/features interface file missing. (Kernel needs AppArmor 2.4 compatibility patch.) 
Cache read/write disabled: /sys/kernel/security/apparmor/features interface file missing. (Kernel needs AppArmor 2.4 compatibility patch.) 
Warning from /etc/apparmor.d/gdm-guest-session (/etc/apparmor.d/gdm-guest-session line 48): profile /usr/share/gdm/guest-session/Xsession network rules not enforced 
Cache read/write disabled: /sys/kernel/security/apparmor/features interface file missing. (Kernel needs AppArmor 2.4 compatibility patch.) 
Warning from /etc/apparmor.d/sbin.dhclient3 (/etc/apparmor.d/sbin.dhclient3 line 73): profile /sbin/dhclient3 network rules not enforced 
Cache read/write disabled: /sys/kernel/security/apparmor/features interface file missing. (Kernel needs AppArmor 2.4 compatibility patch.) 
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox 
Cache read/write disabled: /sys/kernel/security/apparmor/features interface file missing. (Kernel needs AppArmor 2.4 compatibility patch.) 
Warning from /etc/apparmor.d/usr.sbin.cupsd (/etc/apparmor.d/usr.sbin.cupsd line 165): profile /usr/lib/cups/backend/cups-pdf network rules not enforced 
Warning from /etc/apparmor.d/usr.sbin.cupsd (/etc/apparmor.d/usr.sbin.cupsd line 165): profile /usr/sbin/cupsd network rules not enforced 
Cache read/write disabled: /sys/kernel/security/apparmor/features interface file missing. (Kernel needs AppArmor 2.4 compatibility patch.) 
Warning from /etc/apparmor.d/usr.sbin.tcpdump (/etc/apparmor.d/usr.sbin.tcpdump line 51): profile /usr/sbin/tcpdump network rules not enforced
``` 

i tried also to update apparmor at version 2.6 without solving.

---

