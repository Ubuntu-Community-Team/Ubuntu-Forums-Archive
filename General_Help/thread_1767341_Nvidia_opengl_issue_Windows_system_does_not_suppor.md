---
title: "Nvidia opengl issue :Windows system does not support opengl"
date: 2011-05-25
forum: General Help
---

### Post by endor43 on 2011-05-25
I'd really appreciate some help here. 
So in trying to run Cairo dock (which doesn't by the way) I've discovered that I have a bit of an opengl issue. Anytime i try to run anything glx i get this output:

Windows system does not support opengl

and the application does not run.

This is an extremely similar issue from a few years ago, please read (its very short):

[http://ubuntuforums.org/showthread.php?p=9777834](http://ubuntuforums.org/showthread.php?p=9777834)

I'm having the same problem, but now with the deprecation of xorg.conf, I am having difficulty "editing xorg.conf" for obvious reasons. So I basically cannot run anything,

I have nvidia-173,nvidia-glx-173 installed

```
thomas@tcz:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
01:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 9300M GS] (rev a1)

```

Here is my xorg.0.log:
```
[    13.374] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    13.374] X Protocol Version 11, Revision 0
[    13.374] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[    13.374] Current Operating System: Linux tcz 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64
[    13.374] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=bc9469c9-554e-4db3-bfc7-0bf1f9d38a97 ro quiet splash vt.handoff=7
[    13.374] Build Date: 19 April 2011  03:40:45PM
[    13.374] xorg-server 2:1.10.1-1ubuntu1 (For technical support please see http://www.ubuntu.com/support) 
[    13.374] Current version of pixman: 0.20.2
[    13.374] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    13.374] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    13.374] (==) Log file: "/var/log/Xorg.0.log", Time: Wed May 25 12:29:22 2011
[    13.375] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    13.376] (==) No Layout section.  Using the first Screen section.
[    13.376] (==) No screen section available. Using defaults.
[    13.376] (**) |-->Screen "Default Screen Section" (0)
[    13.376] (**) |   |-->Monitor "<default monitor>"
[    13.376] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    13.376] (==) Automatically adding devices
[    13.376] (==) Automatically enabling devices
[    13.376] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    13.376] 	Entry deleted from font path.
[    13.376] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    13.376] 	Entry deleted from font path.
[    13.376] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    13.376] 	Entry deleted from font path.
[    13.376] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    13.376] 	Entry deleted from font path.
[    13.376] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    13.376] 	Entry deleted from font path.
[    13.376] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    13.376] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    13.376] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    13.376] (II) Loader magic: 0x7e0280
[    13.376] (II) Module ABI versions:
[    13.376] 	X.Org ANSI C Emulation: 0.4
[    13.376] 	X.Org Video Driver: 10.0
[    13.376] 	X.Org XInput driver : 12.3
[    13.376] 	X.Org Server Extension : 5.0
[    13.377] (--) PCI:*(0:0:2:0) 8086:2a42:104d:9025 rev 7, Mem @ 0xe8400000/4194304, 0xd0000000/268435456, I/O @ 0x00008130/8
[    13.377] (--) PCI: (0:1:0:0) 10de:06e5:104d:9025 rev 161, Mem @ 0xe4000000/16777216, 0xc0000000/268435456, 0xe2000000/33554432, I/O @ 0x00007000/128
[    13.377] (II) Open ACPI successful (/var/run/acpid.socket)
[    13.377] (II) LoadModule: "extmod"
[    13.377] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    13.377] (II) Module extmod: vendor="X.Org Foundation"
[    13.377] 	compiled for 1.10.1, module version = 1.0.0
[    13.377] 	Module class: X.Org Server Extension
[    13.377] 	ABI class: X.Org Server Extension, version 5.0
[    13.377] (II) Loading extension MIT-SCREEN-SAVER
[    13.377] (II) Loading extension XFree86-VidModeExtension
[    13.377] (II) Loading extension XFree86-DGA
[    13.377] (II) Loading extension DPMS
[    13.378] (II) Loading extension XVideo
[    13.378] (II) Loading extension XVideo-MotionCompensation
[    13.378] (II) Loading extension X-Resource
[    13.378] (II) LoadModule: "dbe"
[    13.378] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    13.378] (II) Module dbe: vendor="X.Org Foundation"
[    13.378] 	compiled for 1.10.1, module version = 1.0.0
[    13.378] 	Module class: X.Org Server Extension
[    13.378] 	ABI class: X.Org Server Extension, version 5.0
[    13.378] (II) Loading extension DOUBLE-BUFFER
[    13.378] (II) LoadModule: "glx"
[    13.378] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    13.384] (II) Module glx: vendor="NVIDIA Corporation"
[    13.384] 	compiled for 4.0.2, module version = 1.0.0
[    13.384] 	Module class: X.Org Server Extension
[    13.384] (II) NVIDIA GLX Module  173.14.30  Sat Apr 16 22:45:09 PDT 2011
[    13.384] (II) Loading extension GLX
[    13.384] (II) LoadModule: "record"
[    13.385] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    13.385] (II) Module record: vendor="X.Org Foundation"
[    13.385] 	compiled for 1.10.1, module version = 1.13.0
[    13.385] 	Module class: X.Org Server Extension
[    13.385] 	ABI class: X.Org Server Extension, version 5.0
[    13.385] (II) Loading extension RECORD
[    13.385] (II) LoadModule: "dri"
[    13.385] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    13.385] (II) Module dri: vendor="X.Org Foundation"
[    13.385] 	compiled for 1.10.1, module version = 1.0.0
[    13.385] 	ABI class: X.Org Server Extension, version 5.0
[    13.385] (II) Loading extension XFree86-DRI
[    13.385] (II) LoadModule: "dri2"
[    13.385] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    13.385] (II) Module dri2: vendor="X.Org Foundation"
[    13.385] 	compiled for 1.10.1, module version = 1.2.0
[    13.385] 	ABI class: X.Org Server Extension, version 5.0
[    13.385] (II) Loading extension DRI2
[    13.385] (==) Matched intel as autoconfigured driver 0
[    13.385] (==) Matched vesa as autoconfigured driver 1
[    13.385] (==) Matched fbdev as autoconfigured driver 2
[    13.385] (==) Assigned the driver to the xf86ConfigLayout
[    13.385] (II) LoadModule: "intel"
[    13.413] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    13.413] (II) Module intel: vendor="X.Org Foundation"
[    13.413] 	compiled for 1.10.1, module version = 2.14.0
[    13.413] 	Module class: X.Org Video Driver
[    13.413] 	ABI class: X.Org Video Driver, version 10.0
[    13.413] (II) LoadModule: "vesa"
[    13.414] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    13.414] (II) Module vesa: vendor="X.Org Foundation"
[    13.414] 	compiled for 1.10.0, module version = 2.3.0
[    13.414] 	Module class: X.Org Video Driver
[    13.414] 	ABI class: X.Org Video Driver, version 10.0
[    13.414] (II) LoadModule: "fbdev"
[    13.414] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    13.414] (II) Module fbdev: vendor="X.Org Foundation"
[    13.414] 	compiled for 1.10.0, module version = 0.4.2
[    13.414] 	ABI class: X.Org Video Driver, version 10.0
[    13.414] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
	Sandybridge, Sandybridge
[    13.414] (II) VESA: driver for VESA chipsets: vesa
[    13.414] (II) FBDEV: driver for framebuffer: fbdev
[    13.414] (++) using VT number 7

[    13.416] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    13.416] (WW) Falling back to old probe method for vesa
[    13.416] (WW) Falling back to old probe method for fbdev
[    13.416] (II) Loading sub module "fbdevhw"
[    13.416] (II) LoadModule: "fbdevhw"
[    13.416] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    13.416] (II) Module fbdevhw: vendor="X.Org Foundation"
[    13.416] 	compiled for 1.10.1, module version = 0.0.2
[    13.416] 	ABI class: X.Org Video Driver, version 10.0
[    13.417] drmOpenDevice: node name is /dev/dri/card0
[    13.417] drmOpenDevice: open result is 9, (OK)
[    13.417] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    13.417] drmOpenDevice: node name is /dev/dri/card0
[    13.417] drmOpenDevice: open result is 9, (OK)
[    13.417] drmOpenByBusid: drmOpenMinor returns 9
[    13.417] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    13.417] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    13.417] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    13.417] (==) intel(0): RGB weight 888
[    13.417] (==) intel(0): Default visual is TrueColor
[    13.417] (II) intel(0): Integrated Graphics Chipset: Intel(R) GM45
[    13.417] (--) intel(0): Chipset: "GM45"
[    13.417] (**) intel(0): Relaxed fencing enabled
[    13.417] (**) intel(0): Tiling enabled
[    13.417] (**) intel(0): SwapBuffers wait enabled
[    13.417] (==) intel(0): video overlay key set to 0x101fe
[    13.417] (II) intel(0): Output LVDS1 has no monitor section
[    13.417] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
[    13.450] (II) intel(0): Output VGA1 has no monitor section
[    13.450] (II) intel(0): EDID for output LVDS1
[    13.450] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    13.450] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    13.450] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    13.450] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    13.450] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    13.450] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    13.450] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    13.450] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    13.450] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    13.450] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    13.450] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    13.450] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    13.450] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    13.450] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    13.450] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    13.450] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    13.450] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    13.450] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    13.450] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    13.450] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    13.450] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    13.450] (II) intel(0): Printing probed modes for output LVDS1
[    13.450] (II) intel(0): Modeline "1600x900"x59.9   99.93  1600 1664 1728 1832  900 901 902 910 -hsync -vsync (54.5 kHz)
[    13.450] (II) intel(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    13.450] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    13.450] (II) intel(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz)
[    13.450] (II) intel(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
[    13.450] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    13.450] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    13.450] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    13.450] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    13.490] (II) intel(0): EDID for output VGA1
[    13.490] (II) intel(0): Output LVDS1 connected
[    13.490] (II) intel(0): Output VGA1 disconnected
[    13.490] (II) intel(0): Using exact sizes for initial modes
[    13.490] (II) intel(0): Output LVDS1 using initial mode 1600x900
[    13.490] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    13.490] (II) intel(0): Kernel page flipping support detected, enabling
[    13.490] (==) intel(0): DPI set to (96, 96)
[    13.490] (II) Loading sub module "fb"
[    13.490] (II) LoadModule: "fb"
[    13.490] (II) Loading /usr/lib/xorg/modules/libfb.so
[    13.490] (II) Module fb: vendor="X.Org Foundation"
[    13.490] 	compiled for 1.10.1, module version = 1.0.0
[    13.490] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    13.490] (II) UnloadModule: "vesa"
[    13.490] (II) Unloading vesa
[    13.490] (II) UnloadModule: "fbdev"
[    13.490] (II) Unloading fbdev
[    13.490] (II) UnloadModule: "fbdevhw"
[    13.490] (II) Unloading fbdevhw
[    13.490] (==) Depth 24 pixmap format is 32 bpp
[    13.490] (==) intel(0): VideoRam: 262144 KB
[    13.490] (II) intel(0): [DRI2] Setup complete
[    13.490] (II) intel(0): [DRI2]   DRI driver: i965
[    13.490] (II) intel(0): Allocated new frame buffer 1600x900 stride 6656, tiled
[    13.498] (II) UXA(0): Driver registered support for the following operations:
[    13.498] (II)         solid
[    13.498] (II)         copy
[    13.498] (II)         composite (RENDER acceleration)
[    13.498] (II)         put_image
[    13.498] (II)         get_image
[    13.498] (==) intel(0): Backing store disabled
[    13.498] (==) intel(0): Silken mouse enabled
[    13.498] (II) intel(0): Initializing HW Cursor
[    13.520] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    13.522] (==) intel(0): DPMS enabled
[    13.522] (==) intel(0): Intel XvMC decoder enabled
[    13.522] (II) intel(0): Set up textured video
[    13.523] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[    13.523] (II) intel(0): direct rendering: DRI2 Enabled
[    13.523] (==) intel(0): hotplug detection: "enabled"
[    13.523] (--) RandR disabled
[    13.523] (II) Initializing built-in extension Generic Event Extension
[    13.523] (II) Initializing built-in extension SHAPE
[    13.523] (II) Initializing built-in extension MIT-SHM
[    13.523] (II) Initializing built-in extension XInputExtension
[    13.523] (II) Initializing built-in extension XTEST
[    13.523] (II) Initializing built-in extension BIG-REQUESTS
[    13.523] (II) Initializing built-in extension SYNC
[    13.523] (II) Initializing built-in extension XKEYBOARD
[    13.523] (II) Initializing built-in extension XC-MISC
[    13.523] (II) Initializing built-in extension SECURITY
[    13.523] (II) Initializing built-in extension XINERAMA
[    13.523] (II) Initializing built-in extension XFIXES
[    13.523] (II) Initializing built-in extension RENDER
[    13.523] (II) Initializing built-in extension RANDR
[    13.523] (II) Initializing built-in extension COMPOSITE
[    13.523] (II) Initializing built-in extension DAMAGE
[    13.523] (II) Initializing built-in extension GESTURE
[    13.524] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
[    13.527] (II) intel(0): Setting screen physical size to 423 x 238
[    13.535] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    13.545] (II) config/udev: Adding input device Video Bus (/dev/input/event10)
[    13.545] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    13.545] (II) LoadModule: "evdev"
[    13.546] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.546] (II) Module evdev: vendor="X.Org Foundation"
[    13.546] 	compiled for 1.10.0.902, module version = 2.6.0
[    13.546] 	Module class: X.Org XInput Driver
[    13.546] 	ABI class: X.Org XInput driver, version 12.3
[    13.546] (II) Using input driver 'evdev' for 'Video Bus'
[    13.546] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.546] (**) Video Bus: always reports core events
[    13.546] (**) Video Bus: Device: "/dev/input/event10"
[    13.570] (--) Video Bus: Found keys
[    13.570] (II) Video Bus: Configuring as keyboard
[    13.570] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input10/event10"
[    13.570] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    13.570] (**) Option "xkb_rules" "evdev"
[    13.570] (**) Option "xkb_model" "pc105"
[    13.570] (**) Option "xkb_layout" "us"
[    13.570] (II) config/udev: Adding input device Video Bus (/dev/input/event11)
[    13.570] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    13.570] (II) Using input driver 'evdev' for 'Video Bus'
[    13.571] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.571] (**) Video Bus: always reports core events
[    13.571] (**) Video Bus: Device: "/dev/input/event11"
[    13.620] (--) Video Bus: Found keys
[    13.620] (II) Video Bus: Configuring as keyboard
[    13.620] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:06/LNXVIDEO:01/input/input11/event11"
[    13.620] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    13.620] (**) Option "xkb_rules" "evdev"
[    13.620] (**) Option "xkb_model" "pc105"
[    13.620] (**) Option "xkb_layout" "us"
[    13.621] (II) config/udev: Adding input device Sony Vaio Keys (/dev/input/event3)
[    13.621] (**) Sony Vaio Keys: Applying InputClass "evdev keyboard catchall"
[    13.621] (II) Using input driver 'evdev' for 'Sony Vaio Keys'
[    13.621] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.621] (**) Sony Vaio Keys: always reports core events
[    13.621] (**) Sony Vaio Keys: Device: "/dev/input/event3"
[    13.650] (--) Sony Vaio Keys: Found keys
[    13.650] (II) Sony Vaio Keys: Configuring as keyboard
[    13.650] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0d/SNY6001:00/input/input3/event3"
[    13.650] (II) XINPUT: Adding extended input device "Sony Vaio Keys" (type: KEYBOARD)
[    13.650] (**) Option "xkb_rules" "evdev"
[    13.650] (**) Option "xkb_model" "pc105"
[    13.650] (**) Option "xkb_layout" "us"
[    13.655] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    13.655] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    13.655] (II) Using input driver 'evdev' for 'Power Button'
[    13.655] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.655] (**) Power Button: always reports core events
[    13.655] (**) Power Button: Device: "/dev/input/event0"
[    13.700] (--) Power Button: Found keys
[    13.700] (II) Power Button: Configuring as keyboard
[    13.700] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    13.700] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    13.700] (**) Option "xkb_rules" "evdev"
[    13.700] (**) Option "xkb_model" "pc105"
[    13.700] (**) Option "xkb_layout" "us"
[    13.700] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[    13.716] (II) No input driver/identifier specified (ignoring)
[    13.718] (II) config/udev: Adding input device UVC Camera (05ca:18b0) (/dev/input/event5)
[    13.718] (**) UVC Camera (05ca:18b0): Applying InputClass "evdev keyboard catchall"
[    13.718] (II) Using input driver 'evdev' for 'UVC Camera (05ca:18b0)'
[    13.718] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.718] (**) UVC Camera (05ca:18b0): always reports core events
[    13.718] (**) UVC Camera (05ca:18b0): Device: "/dev/input/event5"
[    13.730] (--) UVC Camera (05ca:18b0): Found keys
[    13.730] (II) UVC Camera (05ca:18b0): Configuring as keyboard
[    13.730] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.0/input/input5/event5"
[    13.730] (II) XINPUT: Adding extended input device "UVC Camera (05ca:18b0)" (type: KEYBOARD)
[    13.730] (**) Option "xkb_rules" "evdev"
[    13.730] (**) Option "xkb_model" "pc105"
[    13.730] (**) Option "xkb_layout" "us"
[    13.731] (II) config/udev: Adding input device HDA Intel Mic (/dev/input/event8)
[    13.731] (II) No input driver/identifier specified (ignoring)
[    13.731] (II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event9)
[    13.731] (II) No input driver/identifier specified (ignoring)
[    13.736] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    13.736] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    13.736] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    13.736] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.736] (**) AT Translated Set 2 keyboard: always reports core events
[    13.736] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    13.736] (--) AT Translated Set 2 keyboard: Found keys
[    13.736] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    13.736] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    13.736] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    13.736] (**) Option "xkb_rules" "evdev"
[    13.736] (**) Option "xkb_model" "pc105"
[    13.736] (**) Option "xkb_layout" "us"
[    13.737] (II) config/udev: Adding input device PS/2 Mouse (/dev/input/event6)
[    13.737] (**) PS/2 Mouse: Applying InputClass "evdev pointer catchall"
[    13.737] (II) Using input driver 'evdev' for 'PS/2 Mouse'
[    13.737] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.737] (**) PS/2 Mouse: always reports core events
[    13.737] (**) PS/2 Mouse: Device: "/dev/input/event6"
[    13.740] (--) PS/2 Mouse: Found 3 mouse buttons
[    13.740] (--) PS/2 Mouse: Found relative axes
[    13.740] (--) PS/2 Mouse: Found x and y relative axes
[    13.740] (II) PS/2 Mouse: Configuring as mouse
[    13.740] (**) PS/2 Mouse: YAxisMapping: buttons 4 and 5
[    13.740] (**) PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    13.740] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input6/event6"
[    13.740] (II) XINPUT: Adding extended input device "PS/2 Mouse" (type: MOUSE)
[    13.740] (II) PS/2 Mouse: initialized for relative axes.
[    13.740] (**) PS/2 Mouse: (accel) keeping acceleration scheme 1
[    13.740] (**) PS/2 Mouse: (accel) acceleration profile 0
[    13.740] (**) PS/2 Mouse: (accel) acceleration factor: 2.000
[    13.740] (**) PS/2 Mouse: (accel) acceleration threshold: 4
[    13.740] (II) config/udev: Adding input device PS/2 Mouse (/dev/input/mouse1)
[    13.740] (II) No input driver/identifier specified (ignoring)
[    13.740] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/event7)
[    13.740] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "evdev touchpad catchall"
[    13.740] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "touchpad catchall"
[    13.740] (II) LoadModule: "synaptics"
[    13.741] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    13.741] (II) Module synaptics: vendor="X.Org Foundation"
[    13.741] 	compiled for 1.10.0.902, module version = 1.3.99
[    13.741] 	Module class: X.Org XInput Driver
[    13.741] 	ABI class: X.Org XInput driver, version 12.3
[    13.741] (II) Using input driver 'synaptics' for 'AlpsPS/2 ALPS GlidePoint'
[    13.741] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    13.741] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[    13.741] (**) Option "Device" "/dev/input/event7"
[    13.760] (--) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
[    13.760] (--) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
[    13.760] (--) AlpsPS/2 ALPS GlidePoint: pressure range 0 - 127
[    13.760] (--) AlpsPS/2 ALPS GlidePoint: buttons: left right middle
[    13.760] (--) AlpsPS/2 ALPS GlidePoint: invalid finger width range.  defaulting to 0 - 16
[    13.770] (--) AlpsPS/2 ALPS GlidePoint: touchpad found
[    13.770] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[    13.780] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input7/event7"
[    13.780] (II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD)
[    13.780] (**) AlpsPS/2 ALPS GlidePoint: (accel) MinSpeed is now constant deceleration 2.5
[    13.780] (**) AlpsPS/2 ALPS GlidePoint: MaxSpeed is now 1.75
[    13.780] (**) AlpsPS/2 ALPS GlidePoint: AccelFactor is now 0.156
[    13.780] (**) AlpsPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
[    13.780] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration profile 1
[    13.780] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration factor: 2.000
[    13.780] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration threshold: 4
[    13.880] (II) AlpsPS/2 ALPS GlidePoint: failed to open grail, no gesture support
[    13.880] (--) AlpsPS/2 ALPS GlidePoint: touchpad found
[    13.880] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/mouse2)
[    13.880] (II) No input driver/identifier specified (ignoring)
[    13.884] (II) config/udev: Adding input device Sony Vaio Jogdial (/dev/input/event4)
[    13.884] (II) No input driver/identifier specified (ignoring)
[    13.884] (II) config/udev: Adding input device Sony Vaio Jogdial (/dev/input/mouse0)
[    13.884] (II) No input driver/identifier specified (ignoring)
[    24.036] (II) config/udev: Adding input device Bluetooth Laser Travel Mouse (/dev/input/mouse3)
[    24.036] (II) No input driver/identifier specified (ignoring)
[    24.037] (II) config/udev: Adding input device Bluetooth Laser Travel Mouse (/dev/input/event12)
[    24.037] (**) Bluetooth Laser Travel Mouse: Applying InputClass "evdev pointer catchall"
[    24.037] (II) Using input driver 'evdev' for 'Bluetooth Laser Travel Mouse'
[    24.037] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    24.037] (**) Bluetooth Laser Travel Mouse: always reports core events
[    24.037] (**) Bluetooth Laser Travel Mouse: Device: "/dev/input/event12"
[    24.070] (--) Bluetooth Laser Travel Mouse: Found 12 mouse buttons
[    24.070] (--) Bluetooth Laser Travel Mouse: Found scroll wheel(s)
[    24.070] (--) Bluetooth Laser Travel Mouse: Found relative axes
[    24.070] (--) Bluetooth Laser Travel Mouse: Found x and y relative axes
[    24.070] (II) Bluetooth Laser Travel Mouse: Configuring as mouse
[    24.070] (II) Bluetooth Laser Travel Mouse: Adding scrollwheel support
[    24.070] (**) Bluetooth Laser Travel Mouse: YAxisMapping: buttons 4 and 5
[    24.070] (**) Bluetooth Laser Travel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    24.070] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb8/8-2/8-2:1.0/bluetooth/hci0/hci0:11/input12/event12"
[    24.070] (II) XINPUT: Adding extended input device "Bluetooth Laser Travel Mouse" (type: MOUSE)
[    24.070] (II) Bluetooth Laser Travel Mouse: initialized for relative axes.
[    24.070] (**) Bluetooth Laser Travel Mouse: (accel) keeping acceleration scheme 1
[    24.070] (**) Bluetooth Laser Travel Mouse: (accel) acceleration profile 0
[    24.070] (**) Bluetooth Laser Travel Mouse: (accel) acceleration factor: 2.000
[    24.070] (**) Bluetooth Laser Travel Mouse: (accel) acceleration threshold: 4
```

Specifically I can pick out:

```
Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
```

and

```
[    13.378] (II) LoadModule: "glx"
[    13.378] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    13.384] (II) Module glx: vendor="NVIDIA Corporation"
[    13.384] 	compiled for 4.0.2, module version = 1.0.0
[    13.384] 	Module class: X.Org Server Extension
[    13.384] (II) NVIDIA GLX Module  173.14.30  Sat Apr 16 22:45:09 PDT 2011
[    13.384] (II) Loading extension GLX
```

Is there a way to do what the above post mentions? Or for the case of me and 11.04 get Opengl functioning?

Thank you!

---

### Post by endor43 on 2011-05-25
bump?

---

### Post by UltraZone on 2011-05-25
Well, honestly I don't think that I can help you much, except to tell you to properly upgrade your drivers:

System > Administration > Additional Drivers > Nvidia accelerated graphics driver (version current)

This works great on my NVidia GeForce 7900 GS (on my laptop).  Seeing as you have the 9300, this should not be a problem whatsoever.  The current driver is 270.41.06.

---

### Post by endor43 on 2011-05-29
I tried nvidia-173 nvidia-current and the opensource drivers, none of them work. Suggestions?

Thank you!

---

### Post by linuxinstalledfromhdd on 2011-05-29
Does your motherboard have on-board video svga?

---

### Post by endor43 on 2011-05-30
Yes, I have an integrated video card and a dedicated one. Intel and Nvidia 9300m. My EFI is on manufacturer lockdown, and does not give me fancy options like disabling onboard video. Suggestions?

Thanks.

---

### Post by linuxinstalledfromhdd on 2011-05-30
Hmm.. For now if I was you, until you can get a good reliable work-around for this issue, I would try hooking up the on-board video, and disabling the PCI-Express card for your performance graphics card you are experience issues with..  You -may- find that the performance loss isn't that big of a deal after all, or maybe the performance graphics is overkill on a Ubuntu system.  You should be able to disable the pci-express card from BIOS, and then hook your monitor to the on-board video for now, to see what the result is like performance-wise. It might be worth a try. :)

---

### Post by endor43 on 2011-05-30
Thanks you for the suggestion! The only problem is, I have a laptop, hence the 9300m, I have been desperately trying to find solutions but my machine being a laptop obviously prevents me from simple but effective fixes like the one you mentioned. As I said earlier BIOS has basically no options to disable or enable anything. Thus I find myself in a real bind. Thank you though! Suggestions?

---

### Post by endor43 on 2011-06-01
bump?

Thanks!

---

