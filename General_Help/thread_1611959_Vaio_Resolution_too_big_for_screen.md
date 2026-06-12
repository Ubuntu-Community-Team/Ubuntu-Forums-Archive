---
title: "Vaio: Resolution too big for screen"
date: 2010-11-02
forum: General Help
---

### Post by maikoi15011 on 2010-11-02
EDIT: And I just noticed there is a Hardware & Laptops forum, sorry for that :/

Hello, I've bought a new Sony Vaio F12 laptop (nVIdia Geforce 330M) a few days ago, but haven't been able to get my resolution in Ubuntu right. My screen resolution is 1920x1080 (full HD), but in Ubuntu it automatically picks 2048x1536. It basically looks like the bottom and the right of the desktop are out of the screen, I can't see it. Changing the res to 1920x1080 doesn't fix the problem either, it just gets uglier. 

I've been trying to fix it for days now, trying out a ton of different "solutions", which seemed to work for others but not for me. I'm quite new to Ubuntu, have only been using it for a few weeks. It worked perfectly fine on my Acer Aspire 7720G so I hoped this would be a smooth install as well.

At first I had installed the 32-bit version, tried various ways to fix this problem, then installed the 64-bit in stead but still had the same problem so I guess that doesn't matter much.
I've tried installing the NVIDIA drivers, but then I run into a load of new problems like the max. screen resolution being 800x600, black, white or even purple screens after splash image, a really f*-up looking display,...

I've tried messing with xrandr stuff (as stated in some "solutions"), messed with the xorg.conf file (like making it find a custom EDID file, changing the sections,...)

None of these seemed to work :| 
The only thing I want is the resolution to be correct, 1920x1080 HD. It doesn't matter to me what driver it uses, since I'm not gaming on Ubuntu. 

I'll add my Xorg.0.log, grub and xorg.conf file, if that helps. 
Right now I have the Ubuntu 64-bit version installed.

xorg.conf after trying out one of the other solutions. There was no xorg.conf initially.
```
Section "Device"
    Identifier     "n"
    Driver        "nouveau"
EndSection
```Log file
```

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux linsey-laptop 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=8b6e4181-1211-45e7-ad06-429cfd18984b ro i8042.nopnp quiet splash video=uvesafb:mode_option=1600x1200-24
Build Date: 21 July 2010  01:03:39PM
xorg-server 2:1.7.6-2ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Nov  2 18:30:43 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(==) No screen section available. Using defaults.
(**) |-->Screen "Default Screen Section" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No device specified for screen "Default Screen Section".
    Using the first device section listed.
(**) |   |-->Device "n"
(==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
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
(II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:1:0:0) 10de:0a29:104d:9067 nVidia Corporation rev 162, Mem @ 0xe2000000/16777216, 0xd0000000/268435456, 0xe0000000/33554432, I/O @ 0x0000d000/128, BIOS @ 0x????????/524288
(II) Open ACPI successful (/var/run/acpid.socket)
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
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
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
(II) LoadModule: "nouveau"
(II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
(II) Module nouveau: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.0.15
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) NOUVEAU driver Date:   Wed Feb 10 18:43:39 2010 +0100
(II) NOUVEAU driver for NVIDIA chipset families :
    RIVA TNT    (NV04)
    RIVA TNT2   (NV05)
    GeForce 256 (NV10)
    GeForce 2   (NV11, NV15)
    GeForce 4MX (NV17, NV18)
    GeForce 3   (NV20)
    GeForce 4Ti (NV25, NV28)
    GeForce FX  (NV3x)
    GeForce 6   (NV4x)
    GeForce 7   (G7x)
    GeForce 8   (G8x)
(II) Primary Device is: PCI 01@00:00:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) [drm] nouveau interface version: 0.0.15
(II) Loading sub module "dri"
(II) LoadModule: "dri"
(II) Reloading /usr/lib/xorg/modules/extensions/libdri.so
(II) NOUVEAU(0): Loaded DRI module
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(--) NOUVEAU(0): Chipset: "NVIDIA NVa5"
(II) NOUVEAU(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
(==) NOUVEAU(0): Depth 24, (--) framebuffer bpp 32
(==) NOUVEAU(0): RGB weight 888
(==) NOUVEAU(0): Default visual is TrueColor
(==) NOUVEAU(0): Using HW cursor
(II) NOUVEAU(0): Output LVDS-1 has no monitor section
(II) NOUVEAU(0): Output VGA-1 has no monitor section
(II) NOUVEAU(0): Output DVI-D-1 has no monitor section
(II) NOUVEAU(0): EDID for output LVDS-1
(II) NOUVEAU(0): Not using default mode "640x350" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "320x175" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "640x400" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "320x200" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "720x400" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "360x200" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "640x480" (unknown reason)
(II) NOUVEAU(0): Not using default mode "320x240" (unknown reason)
(II) NOUVEAU(0): Not using default mode "640x480" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "320x240" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "640x480" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "320x240" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "640x480" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "320x240" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "800x600" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "400x300" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "800x600" (unknown reason)
(II) NOUVEAU(0): Not using default mode "400x300" (unknown reason)
(II) NOUVEAU(0): Not using default mode "800x600" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "400x300" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "800x600" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "400x300" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "800x600" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "400x300" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1024x768" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "512x384" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1024x768" (unknown reason)
(II) NOUVEAU(0): Not using default mode "512x384" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1024x768" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "512x384" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1024x768" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "512x384" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1024x768" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "512x384" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1152x864" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "576x432" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1280x960" (unknown reason)
(II) NOUVEAU(0): Not using default mode "640x480" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1280x960" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "640x480" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1280x1024" (unknown reason)
(II) NOUVEAU(0): Not using default mode "640x512" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "640x512" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "640x512" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1600x1200" (unknown reason)
(II) NOUVEAU(0): Not using default mode "800x600" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "800x600" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "800x600" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "800x600" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "800x600" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1792x1344" (unknown reason)
(II) NOUVEAU(0): Not using default mode "896x672" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1792x1344" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "896x672" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1856x1392" (unknown reason)
(II) NOUVEAU(0): Not using default mode "928x696" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1856x1392" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "928x696" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1920x1440" (unknown reason)
(II) NOUVEAU(0): Not using default mode "960x720" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "960x720" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "832x624" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "416x312" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1152x864" (unknown reason)
(II) NOUVEAU(0): Not using default mode "576x432" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1152x864" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "576x432" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1152x864" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "576x432" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1152x864" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "576x432" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1152x864" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "576x432" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1152x864" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "576x432" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) NOUVEAU(0): Not using default mode "680x384" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1360x768" (unknown reason)
(II) NOUVEAU(0): Not using default mode "680x384" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1400x1050" (unknown reason)
(II) NOUVEAU(0): Not using default mode "700x525" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "700x525" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "700x525" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "700x525" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1440x900" (unknown reason)
(II) NOUVEAU(0): Not using default mode "720x450" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1600x1024" (unknown reason)
(II) NOUVEAU(0): Not using default mode "800x512" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) NOUVEAU(0): Not using default mode "840x525" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1680x1050" (unknown reason)
(II) NOUVEAU(0): Not using default mode "840x525" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "840x525" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "840x525" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "840x525" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) NOUVEAU(0): Not using default mode "960x540" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) NOUVEAU(0): Not using default mode "960x600" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "960x720" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "2048x1536" (hsync out of range)
(II) NOUVEAU(0): Not using default mode "1024x768" (hsync out of range)
(II) NOUVEAU(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1024x768" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1024x768" (vrefresh out of range)
(II) NOUVEAU(0): Printing probed modes for output LVDS-1
(II) NOUVEAU(0): Modeline "2048x1536"x60.0  200.00  2048 2096 2112 2144  1536 1553 1554 1555 +hsync +vsync (93.3 kHz)
(II) NOUVEAU(0): Modeline "1920x1200"x59.9  193.25  1920 2056 2256 2592  1200 1203 1209 1245 -hsync +vsync (74.6 kHz)
(II) NOUVEAU(0): Modeline "1920x1080"x60.0  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync (67.2 kHz)
(II) NOUVEAU(0): Modeline "1600x1200"x59.9  161.00  1600 1712 1880 2160  1200 1203 1207 1245 -hsync +vsync (74.5 kHz)
(II) NOUVEAU(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) NOUVEAU(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) NOUVEAU(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x60.0   81.75  1152 1216 1336 1520  864 867 871 897 -hsync +vsync (53.8 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
(II) NOUVEAU(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
(II) NOUVEAU(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
(II) NOUVEAU(0): Modeline "720x400"x59.6   22.25  720 744 808 896  400 403 413 417 -hsync +vsync (24.8 kHz)
(II) NOUVEAU(0): Modeline "640x400"x60.0   20.00  640 664 720 800  400 403 409 417 -hsync +vsync (25.0 kHz)
(II) NOUVEAU(0): Modeline "640x350"x59.8   17.50  640 664 720 800  350 353 363 366 -hsync +vsync (21.9 kHz)
(II) NOUVEAU(0): EDID for output VGA-1
(II) NOUVEAU(0): EDID for output DVI-D-1
(II) NOUVEAU(0): Output LVDS-1 connected
(II) NOUVEAU(0): Output VGA-1 disconnected
(II) NOUVEAU(0): Output DVI-D-1 disconnected
(II) NOUVEAU(0): Using exact sizes for initial modes
(II) NOUVEAU(0): Output LVDS-1 using initial mode 2048x1536
(II) NOUVEAU(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
(--) NOUVEAU(0): Virtual size is 2048x1536 (pitch 2048)
(**) NOUVEAU(0):  Driver mode "2048x1536": 200.0 MHz (scaled from 0.0 MHz), 93.3 kHz, 60.0 Hz
(II) NOUVEAU(0): Modeline "2048x1536"x60.0  200.00  2048 2096 2112 2144  1536 1553 1554 1555 +hsync +vsync (93.3 kHz)
(**) NOUVEAU(0):  Driver mode "1920x1200": 193.2 MHz (scaled from 0.0 MHz), 74.6 kHz, 59.9 Hz
(II) NOUVEAU(0): Modeline "1920x1200"x59.9  193.25  1920 2056 2256 2592  1200 1203 1209 1245 -hsync +vsync (74.6 kHz)
(**) NOUVEAU(0):  Driver mode "1920x1080": 173.0 MHz (scaled from 0.0 MHz), 67.2 kHz, 60.0 Hz
(II) NOUVEAU(0): Modeline "1920x1080"x60.0  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync (67.2 kHz)
(**) NOUVEAU(0):  Driver mode "1600x1200": 161.0 MHz (scaled from 0.0 MHz), 74.5 kHz, 59.9 Hz
(II) NOUVEAU(0): Modeline "1600x1200"x59.9  161.00  1600 1712 1880 2160  1200 1203 1207 1245 -hsync +vsync (74.5 kHz)
(**) NOUVEAU(0):  Driver mode "1680x1050": 146.2 MHz (scaled from 0.0 MHz), 65.3 kHz, 60.0 Hz
(II) NOUVEAU(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(**) NOUVEAU(0):  Driver mode "1400x1050": 121.8 MHz (scaled from 0.0 MHz), 65.3 kHz, 60.0 Hz
(II) NOUVEAU(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
(**) NOUVEAU(0):  Driver mode "1280x1024": 109.0 MHz (scaled from 0.0 MHz), 63.7 kHz, 59.9 Hz
(II) NOUVEAU(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(**) NOUVEAU(0):  Driver mode "1280x960": 101.2 MHz (scaled from 0.0 MHz), 59.7 kHz, 59.9 Hz
(II) NOUVEAU(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(**) NOUVEAU(0):  Driver mode "1152x864": 81.8 MHz (scaled from 0.0 MHz), 53.8 kHz, 60.0 Hz
(II) NOUVEAU(0): Modeline "1152x864"x60.0   81.75  1152 1216 1336 1520  864 867 871 897 -hsync +vsync (53.8 kHz)
(**) NOUVEAU(0):  Driver mode "1024x768": 63.5 MHz (scaled from 0.0 MHz), 47.8 kHz, 59.9 Hz
(II) NOUVEAU(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
(**) NOUVEAU(0):  Driver mode "800x600": 38.2 MHz (scaled from 0.0 MHz), 37.4 kHz, 59.9 Hz
(II) NOUVEAU(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
(**) NOUVEAU(0):  Driver mode "640x480": 23.8 MHz (scaled from 0.0 MHz), 29.7 kHz, 59.4 Hz
(II) NOUVEAU(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
(**) NOUVEAU(0):  Driver mode "720x400": 22.2 MHz (scaled from 0.0 MHz), 24.8 kHz, 59.6 Hz
(II) NOUVEAU(0): Modeline "720x400"x59.6   22.25  720 744 808 896  400 403 413 417 -hsync +vsync (24.8 kHz)
(**) NOUVEAU(0):  Driver mode "640x400": 20.0 MHz (scaled from 0.0 MHz), 25.0 kHz, 60.0 Hz
(II) NOUVEAU(0): Modeline "640x400"x60.0   20.00  640 664 720 800  400 403 409 417 -hsync +vsync (25.0 kHz)
(**) NOUVEAU(0):  Driver mode "640x350": 17.5 MHz (scaled from 0.0 MHz), 21.9 kHz, 59.8 Hz
(II) NOUVEAU(0): Modeline "640x350"x59.8   17.50  640 664 720 800  350 353 363 366 -hsync +vsync (21.9 kHz)
(==) NOUVEAU(0): DPI set to (96, 96)
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules/libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules/libexa.so
(II) Module exa: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.5.0
    ABI class: X.Org Video Driver, version 6.0
(II) Loading sub module "shadowfb"
(II) LoadModule: "shadowfb"
(II) Loading /usr/lib/xorg/modules/libshadowfb.so
(II) Module shadowfb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(--) Depth 24 pixmap format is 32 bpp
(II) NOUVEAU(0): Opened GPU channel 2
(II) NOUVEAU(0): [DRI2] Setup complete
(II) NOUVEAU(0): GART: 512MiB available
(II) NOUVEAU(0): GART: Allocated 16MiB as a scratch buffer
(II) EXA(0): Driver allocated offscreen pixmaps
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(II)         UploadToScreen
(II)         DownloadFromScreen
(==) NOUVEAU(0): Backing store disabled
(==) NOUVEAU(0): Silken mouse enabled
(II) NOUVEAU(0): [XvMC] Associated with Nouveau GeForce 8/9 Textured Video.
(II) NOUVEAU(0): [XvMC] Extension initialized.
(II) NOUVEAU(0): NVEnterVT is called.
(==) NOUVEAU(0): DPMS enabled
(II) NOUVEAU(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(--) RandR disabled
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
(II) AIGLX error: dlopen of /usr/lib/dri/nouveau_dri.so failed (/usr/lib/dri/nouveau_dri.so: cannot open shared object file: No such file or directory)
(II) AIGLX: reverting to software rendering
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) NOUVEAU(0): Setting screen physical size to 541 x 406
resize called 2048 1536
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Sony Vaio Keys (/dev/input/event5)
(**) Sony Vaio Keys: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) Sony Vaio Keys: always reports core events
(**) Sony Vaio Keys: Device: "/dev/input/event5"
(II) Sony Vaio Keys: Found keys
(II) Sony Vaio Keys: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sony Vaio Keys" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "be"
(II) XKB: reuse xkmfile /var/lib/xkb/server-BCDBD3DBC93B3E588F97965C4D87FE91FAEC6B41.xkm
(II) config/udev: Adding input device Video Bus (/dev/input/event4)
(**) Video Bus: Applying InputClass "evdev keyboard catchall"
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event4"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "be"
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "be"
(II) config/udev: Adding input device Lid Switch (/dev/input/event0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device UVC Camera (05ca:18ba) (/dev/input/event7)
(**) UVC Camera (05ca:18ba): Applying InputClass "evdev keyboard catchall"
(**) UVC Camera (05ca:18ba): always reports core events
(**) UVC Camera (05ca:18ba): Device: "/dev/input/event7"
(II) UVC Camera (05ca:18ba): Found keys
(II) UVC Camera (05ca:18ba): Configuring as keyboard
(II) XINPUT: Adding extended input device "UVC Camera (05ca:18ba)" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "be"
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "be"
(II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/event8)
(**) ImPS/2 Generic Wheel Mouse: Applying InputClass "evdev pointer catchall"
(**) ImPS/2 Generic Wheel Mouse: always reports core events
(**) ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event8"
(II) ImPS/2 Generic Wheel Mouse: Found 3 mouse buttons
(II) ImPS/2 Generic Wheel Mouse: Found scroll wheel(s)
(II) ImPS/2 Generic Wheel Mouse: Found relative axes
(II) ImPS/2 Generic Wheel Mouse: Found x and y relative axes
(II) ImPS/2 Generic Wheel Mouse: Configuring as mouse
(**) ImPS/2 Generic Wheel Mouse: YAxisMapping: buttons 4 and 5
(**) ImPS/2 Generic Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE)
(II) ImPS/2 Generic Wheel Mouse: initialized for relative axes.
(II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/mouse2)
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
(II) config/udev: Adding input device Sony Vaio Jogdial (/dev/input/event6)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Sony Vaio Jogdial (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
resize called 2048 1536

```Grub, these settings seemed to really enhance the grub menu resolution, the" i8042.nopnp" made me able to use my touchpad.
```
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash video=uvesafb:mode_option=1600x1200-24"
GRUB_CMDLINE_LINUX="i8042.nopnp"

...

GRUB_GFXMODE=1600x1200

```I really hope someone can help me out here, I'm really desparate >_<
Thanks in advance.

---

### Post by Quackers on 2010-11-02
Welcome to UF.
Have you been to Systam > Admin > Hardware drivers (or Additional drivers in 10.10) and checked for proprietary drivers?

---

### Post by maikoi15011 on 2010-11-02
Very fast reply! ^^

There are some NVIDIA accelerated graphic drivers there (proprietary). When I tried installing them it would fix the screen range problem, but I'd be stuck with a max. resolution of 800x600 :/

When I try installing them again right now, (I have been following some of the other guides today...) my screen goes mad and I see it flickering something like a commandline and some text multiple times, but too fast for me to read. Then I get a window that says:

"Ubuntu is running in low-graphics mode" and gives me two errors:
"No display devices found for this X screen."
"Screen(s) found, but none have a usable configuration."

The graphics look very odd as well, besides a low resolution it now also "moves" left/right. I also mentioned this in the first post as the screen being "really f*-uped".

---

### Post by Quackers on 2010-11-02
Does that happen when you choose the driver that has recommended in brackets? It may possibly be due to the newish video card you have, or possibly a Xorg problem. Sadly I don't have experience with either :-(

---

### Post by maikoi15011 on 2010-11-02
This happens after installing the recommended NVIDIA drivers in the "Hardware Drivers" window.

If I then choose "Reconfigure graphics -> Use default configuration" in the window, it resets my xorg.config file to default and I get a normal screen again, but with a max. resolution stuck at 800x600. The boundaries of the desktop do match with the screen now though.

EDIT: Actually, after re-checking, there is no xorg.conf in my /etc/X11 folder anymore.

---

### Post by Quackers on 2010-11-02
Try going to System > Preferences > Monitors
It will say in a box
It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?
Answer yes and in the Nvidia screen that opens up go through all the different sections and see if the option to change resolution exists.

---

### Post by maikoi15011 on 2010-11-02
When I go there I get a message saying 

"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run 'nvidia-xconfig' as root), and restart the X server."

When I press ok the message disappears and I can access the settings, but all I can tick off is

Enable ToolTips
Display Status Bar
Slider Text Entires
Include X display names in the config file
Show "really quit?" dialog

Besides that I can only press "help" and quit".

---

### Post by Quackers on 2010-11-02
Does your Additional Drivers window look like this with one of the options having a green button on the left) ie Activated

---

### Post by maikoi15011 on 2010-11-02
Gah, internet fails when you need it >.<;

I only have the 2nd option available on that picture, there are no other options listed. The bulb left to it is green, and at the bottom there is another green bulb saying "This driver is activated and currently in use."

---

### Post by Quackers on 2010-11-02
I'm afraid I don't know why your system thinks you are not using the proprietary driver when Additional Hardware says that you are. It may be a Xorg thing I just don't have any experience with it, but I think there should be a xorg.conf file in /etc/X11, but I suspect that would be made once the driver is recognised. I just don't know enough to advise you.
Have you googled or used the forum search quoting your graphics card details?

---

### Post by maikoi15011 on 2010-11-02
I did what you said and looked around on the forums a bit more, then came across a thread I hadn't noticed before. 

[http://ubuntuforums.org/showthread.php?t=1577779](http://ubuntuforums.org/showthread.php?t=1577779)

I did just as the OP stated after doing a clean install,  and now my screen is completely fixed! :)

Thanks a lot for your time and the quick replies! Next time I'll be sure to more thoroughly scan the forums heh.

---

### Post by Quackers on 2010-11-02
Nice one, well done :-)
If you mark the thread as solved with the thread tools it may help others when searching for the same problem. Thanks.

---

