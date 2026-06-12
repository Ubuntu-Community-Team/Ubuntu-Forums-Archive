---
title: "Out of Range error"
date: 2012-08-28
forum: General Help
---

### Post by SuperFreak on 2012-08-28
I know this issue has been addressed ad nauseum but I haven't solved it with solutions online so far. I installed 12.04 with xfce de on a friends HP Pavillion a6502f computer with HP w2207 monitor and Integrated graphics using nVidia GeForce 6150SE and get this message on boot up 
Input Signal Out of Range Change Settings to "1680 X 1050 @ 60hz"
If I go into monitor settings 60 hz is not offered for that resolution only 50 or 51hz. If I downgrade to a lower resolution with the right refresh rate I get the message still.
I would not be concerned about this message except it delays boot time to the OS by over a minute

---

### Post by SuperFreak on 2012-08-28
I was able to set the resolution and refresh rate correctly at 1680X1050 60 hz by removing the proprietary nvidia drivers but I am still getting the video input out of range error. 
I also tried [http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?objectID=c00061509&lang=en&cc=us&taskId=101&contentType=SupportFAQ&prodSeriesId=3733085&prodTypeId=12454#c00061509_sleep]("http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?objectID=c00061509&lang=en&cc=us&taskId=101&contentType=SupportFAQ&prodSeriesId=3733085&prodTypeId=12454#c00061509_sleep") instructions with no luck
Any help would be appreciated

---

### Post by Zimmer on 2012-08-28
Have you looked at the xorg log file? What Errors or Warnings does it show ?.

This is symptomatic of an earlier problem I had (may still have cos I do not use them any more )with two older ACER LCD monitors. The monitors did not report their EDID info to XORG so I had to manually adjust the XORG config to ignore EDID and pass the parameters through the xorg.conf file.

Not sure how one does that these days, what with the changes to how XORG does things in the last 5 years.

Have a look at the logs, though...

---

### Post by SuperFreak on 2012-08-28
Thanks

I will have a look at the logs tomorrow although I am not sure what to look for

---

### Post by SuperFreak on 2012-08-29
I have posted the log file below. I don't really understand it but it seems to me that the EDID data you refered to is in fact being recognized





```
[    12.281] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    12.281] X Protocol Version 11, Revision 0
[    12.281] Build Operating System: Linux 2.6.42-26-generic x86_64 Ubuntu
[    12.281] Current Operating System: Linux nancy-KT367AA-A2L-a6502f 3.2.0-29-generic #46-Ubuntu SMP Fri Jul 27 17:03:23 UTC 2012 x86_64
[    12.281] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-29-generic root=UUID=a76fd601-4150-4a05-93df-008064fe3b90 ro quiet splash vt.handoff=7
[    12.281] Build Date: 04 August 2012  01:51:23AM
[    12.281] xorg-server 2:1.11.4-0ubuntu10.7 (For technical support please see http://www.ubuntu.com/support) 
[    12.281] Current version of pixman: 0.24.4
[    12.281] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    12.281] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    12.281] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Aug 29 09:52:39 2012
[    12.281] (==) Using config file: "/etc/X11/xorg.conf"
[    12.281] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    12.282] (==) No Layout section.  Using the first Screen section.
[    12.282] (==) No screen section available. Using defaults.
[    12.282] (**) |-->Screen "Default Screen Section" (0)
[    12.282] (**) |   |-->Monitor "<default monitor>"
[    12.282] (==) No device specified for screen "Default Screen Section".
	Using the first device section listed.
[    12.282] (**) |   |-->Device "Default Device"
[    12.282] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    12.282] (==) Automatically adding devices
[    12.282] (==) Automatically enabling devices
[    12.282] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    12.282] 	Entry deleted from font path.
[    12.282] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    12.282] 	Entry deleted from font path.
[    12.282] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    12.282] 	Entry deleted from font path.
[    12.282] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    12.282] 	Entry deleted from font path.
[    12.282] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    12.282] 	Entry deleted from font path.
[    12.282] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    12.282] 	Entry deleted from font path.
[    12.282] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    12.282] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    12.282] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    12.282] (II) Loader magic: 0x7f9225229b00
[    12.282] (II) Module ABI versions:
[    12.282] 	X.Org ANSI C Emulation: 0.4
[    12.282] 	X.Org Video Driver: 11.0
[    12.282] 	X.Org XInput driver : 16.0
[    12.282] 	X.Org Server Extension : 6.0
[    12.283] (--) PCI:*(0:0:13:0) 10de:03d0:103c:2a6d rev 162, Mem @ 0xfb000000/16777216, 0xe0000000/268435456, 0xfc000000/16777216, BIOS @ 0x????????/131072
[    12.283] (II) Open ACPI successful (/var/run/acpid.socket)
[    12.283] (II) LoadModule: "extmod"
[    12.284] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    12.284] (II) Module extmod: vendor="X.Org Foundation"
[    12.284] 	compiled for 1.11.3, module version = 1.0.0
[    12.284] 	Module class: X.Org Server Extension
[    12.284] 	ABI class: X.Org Server Extension, version 6.0
[    12.284] (II) Loading extension MIT-SCREEN-SAVER
[    12.284] (II) Loading extension XFree86-VidModeExtension
[    12.284] (II) Loading extension XFree86-DGA
[    12.284] (II) Loading extension DPMS
[    12.284] (II) Loading extension XVideo
[    12.284] (II) Loading extension XVideo-MotionCompensation
[    12.284] (II) Loading extension X-Resource
[    12.284] (II) LoadModule: "dbe"
[    12.284] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    12.284] (II) Module dbe: vendor="X.Org Foundation"
[    12.284] 	compiled for 1.11.3, module version = 1.0.0
[    12.284] 	Module class: X.Org Server Extension
[    12.284] 	ABI class: X.Org Server Extension, version 6.0
[    12.284] (II) Loading extension DOUBLE-BUFFER
[    12.284] (II) LoadModule: "glx"
[    12.284] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    12.299] (II) Module glx: vendor="X.Org Foundation"
[    12.299] 	compiled for 1.11.3, module version = 1.0.0
[    12.299] 	ABI class: X.Org Server Extension, version 6.0
[    12.299] (==) AIGLX enabled
[    12.299] (II) Loading extension GLX
[    12.299] (II) LoadModule: "record"
[    12.300] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    12.300] (II) Module record: vendor="X.Org Foundation"
[    12.300] 	compiled for 1.11.3, module version = 1.13.0
[    12.300] 	Module class: X.Org Server Extension
[    12.300] 	ABI class: X.Org Server Extension, version 6.0
[    12.300] (II) Loading extension RECORD
[    12.300] (II) LoadModule: "dri"
[    12.300] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    12.300] (II) Module dri: vendor="X.Org Foundation"
[    12.300] 	compiled for 1.11.3, module version = 1.0.0
[    12.300] 	ABI class: X.Org Server Extension, version 6.0
[    12.300] (II) Loading extension XFree86-DRI
[    12.300] (II) LoadModule: "dri2"
[    12.300] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    12.300] (II) Module dri2: vendor="X.Org Foundation"
[    12.300] 	compiled for 1.11.3, module version = 1.2.0
[    12.301] 	ABI class: X.Org Server Extension, version 6.0
[    12.301] (II) Loading extension DRI2
[    12.301] (==) Matched nvidia as autoconfigured driver 0
[    12.301] (==) Matched nouveau as autoconfigured driver 1
[    12.301] (==) Matched nv as autoconfigured driver 2
[    12.301] (==) Matched vesa as autoconfigured driver 3
[    12.301] (==) Matched fbdev as autoconfigured driver 4
[    12.301] (==) Assigned the driver to the xf86ConfigLayout
[    12.301] (II) LoadModule: "nvidia"
[    12.301] (WW) Warning, couldn't open module nvidia
[    12.301] (II) UnloadModule: "nvidia"
[    12.301] (II) Unloading nvidia
[    12.301] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    12.301] (II) LoadModule: "nouveau"
[    12.301] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    12.302] (II) Module nouveau: vendor="X.Org Foundation"
[    12.302] 	compiled for 1.11.3, module version = 0.0.16
[    12.302] 	Module class: X.Org Video Driver
[    12.302] 	ABI class: X.Org Video Driver, version 11.0
[    12.302] (II) LoadModule: "nv"
[    12.302] (WW) Warning, couldn't open module nv
[    12.302] (II) UnloadModule: "nv"
[    12.302] (II) Unloading nv
[    12.302] (EE) Failed to load module "nv" (module does not exist, 0)
[    12.302] (II) LoadModule: "vesa"
[    12.302] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    12.302] (II) Module vesa: vendor="X.Org Foundation"
[    12.302] 	compiled for 1.11.3, module version = 2.3.0
[    12.302] 	Module class: X.Org Video Driver
[    12.302] 	ABI class: X.Org Video Driver, version 11.0
[    12.302] (II) LoadModule: "fbdev"
[    12.303] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    12.303] (II) Module fbdev: vendor="X.Org Foundation"
[    12.303] 	compiled for 1.11.3, module version = 0.4.2
[    12.303] 	ABI class: X.Org Video Driver, version 11.0
[    12.303] (==) Matched nvidia as autoconfigured driver 0
[    12.303] (==) Matched nouveau as autoconfigured driver 1
[    12.303] (==) Matched nv as autoconfigured driver 2
[    12.303] (==) Matched vesa as autoconfigured driver 3
[    12.303] (==) Matched fbdev as autoconfigured driver 4
[    12.303] (==) Assigned the driver to the xf86ConfigLayout
[    12.303] (II) LoadModule: "nvidia"
[    12.303] (WW) Warning, couldn't open module nvidia
[    12.303] (II) UnloadModule: "nvidia"
[    12.303] (II) Unloading nvidia
[    12.303] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    12.303] (II) LoadModule: "nouveau"
[    12.304] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    12.304] (II) Module nouveau: vendor="X.Org Foundation"
[    12.304] 	compiled for 1.11.3, module version = 0.0.16
[    12.304] 	Module class: X.Org Video Driver
[    12.304] 	ABI class: X.Org Video Driver, version 11.0
[    12.304] (II) UnloadModule: "nouveau"
[    12.304] (II) Unloading nouveau
[    12.304] (II) Failed to load module "nouveau" (already loaded, 0)
[    12.304] (II) LoadModule: "nv"
[    12.304] (WW) Warning, couldn't open module nv
[    12.304] (II) UnloadModule: "nv"
[    12.304] (II) Unloading nv
[    12.304] (EE) Failed to load module "nv" (module does not exist, 0)
[    12.304] (II) LoadModule: "vesa"
[    12.304] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    12.304] (II) Module vesa: vendor="X.Org Foundation"
[    12.304] 	compiled for 1.11.3, module version = 2.3.0
[    12.304] 	Module class: X.Org Video Driver
[    12.305] 	ABI class: X.Org Video Driver, version 11.0
[    12.305] (II) UnloadModule: "vesa"
[    12.305] (II) Unloading vesa
[    12.305] (II) Failed to load module "vesa" (already loaded, 0)
[    12.305] (II) LoadModule: "fbdev"
[    12.305] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    12.305] (II) Module fbdev: vendor="X.Org Foundation"
[    12.305] 	compiled for 1.11.3, module version = 0.4.2
[    12.305] 	ABI class: X.Org Video Driver, version 11.0
[    12.305] (II) UnloadModule: "fbdev"
[    12.305] (II) Unloading fbdev
[    12.305] (II) Failed to load module "fbdev" (already loaded, 0)
[    12.305] (II) NOUVEAU driver Date:   Wed Nov 30 18:56:54 2011 +0100
[    12.305] (II) NOUVEAU driver for NVIDIA chipset families :
[    12.305] 	RIVA TNT        (NV04)
[    12.305] 	RIVA TNT2       (NV05)
[    12.305] 	GeForce 256     (NV10)
[    12.305] 	GeForce 2       (NV11, NV15)
[    12.305] 	GeForce 4MX     (NV17, NV18)
[    12.305] 	GeForce 3       (NV20)
[    12.305] 	GeForce 4Ti     (NV25, NV28)
[    12.305] 	GeForce FX      (NV3x)
[    12.305] 	GeForce 6       (NV4x)
[    12.305] 	GeForce 7       (G7x)
[    12.305] 	GeForce 8       (G8x)
[    12.305] 	GeForce GTX 200 (NVA0)
[    12.305] 	GeForce GTX 400 (NVC0)
[    12.305] (II) VESA: driver for VESA chipsets: vesa
[    12.305] (II) FBDEV: driver for framebuffer: fbdev
[    12.305] (++) using VT number 7

[    12.305] drmOpenDevice: node name is /dev/dri/card0
[    12.305] drmOpenDevice: open result is 8, (OK)
[    12.305] drmOpenByBusid: Searching for BusID pci:0000:00:0d.0
[    12.305] drmOpenDevice: node name is /dev/dri/card0
[    12.305] drmOpenDevice: open result is 8, (OK)
[    12.305] drmOpenByBusid: drmOpenMinor returns 8
[    12.305] drmOpenByBusid: drmGetBusid reports pci:0000:00:0d.0
[    12.305] (II) [drm] nouveau interface version: 0.0.16
[    12.306] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    12.306] (WW) Falling back to old probe method for vesa
[    12.306] (WW) Falling back to old probe method for fbdev
[    12.306] (II) Loading sub module "fbdevhw"
[    12.306] (II) LoadModule: "fbdevhw"
[    12.306] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    12.306] (II) Module fbdevhw: vendor="X.Org Foundation"
[    12.306] 	compiled for 1.11.3, module version = 0.0.2
[    12.306] 	ABI class: X.Org Video Driver, version 11.0
[    12.306] (II) Loading sub module "dri"
[    12.306] (II) LoadModule: "dri"
[    12.306] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    12.306] (II) Module dri: vendor="X.Org Foundation"
[    12.306] 	compiled for 1.11.3, module version = 1.0.0
[    12.306] 	ABI class: X.Org Server Extension, version 6.0
[    12.306] (II) NOUVEAU(0): Loaded DRI module
[    12.306] drmOpenDevice: node name is /dev/dri/card0
[    12.306] drmOpenDevice: open result is 9, (OK)
[    12.306] drmOpenDevice: node name is /dev/dri/card0
[    12.306] drmOpenDevice: open result is 9, (OK)
[    12.306] drmOpenByBusid: Searching for BusID pci:0000:00:0d.0
[    12.306] drmOpenDevice: node name is /dev/dri/card0
[    12.306] drmOpenDevice: open result is 9, (OK)
[    12.306] drmOpenByBusid: drmOpenMinor returns 9
[    12.306] drmOpenByBusid: drmGetBusid reports pci:0000:00:0d.0
[    12.306] (II) [drm] DRM interface version 1.4
[    12.306] (II) [drm] DRM open master succeeded.
[    12.306] (--) NOUVEAU(0): Chipset: "NVIDIA NV4c"
[    12.306] (II) NOUVEAU(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    12.306] (==) NOUVEAU(0): Depth 24, (--) framebuffer bpp 32
[    12.306] (==) NOUVEAU(0): RGB weight 888
[    12.306] (==) NOUVEAU(0): Default visual is TrueColor
[    12.306] (==) NOUVEAU(0): Using HW cursor
[    12.306] (==) NOUVEAU(0): GLX sync to VBlank disabled.
[    12.306] (==) NOUVEAU(0): Page flipping enabled
[    12.411] (II) NOUVEAU(0): Output VGA-1 has no monitor section
[    12.515] (II) NOUVEAU(0): EDID for output VGA-1
[    12.515] (II) NOUVEAU(0): Manufacturer: HWP  Model: 26a8  Serial#: 16843009
[    12.515] (II) NOUVEAU(0): Year: 2008  Week: 20
[    12.515] (II) NOUVEAU(0): EDID Version: 1.3
[    12.515] (II) NOUVEAU(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    12.515] (II) NOUVEAU(0): Sync:  Separate
[    12.515] (II) NOUVEAU(0): Max Image Size [cm]: horiz.: 47  vert.: 30
[    12.515] (II) NOUVEAU(0): Gamma: 2.20
[    12.515] (II) NOUVEAU(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    12.515] (II) NOUVEAU(0): Default color space is primary color space
[    12.515] (II) NOUVEAU(0): First detailed timing is preferred mode
[    12.515] (II) NOUVEAU(0): redX: 0.646 redY: 0.339   greenX: 0.290 greenY: 0.603
[    12.515] (II) NOUVEAU(0): blueX: 0.145 blueY: 0.065   whiteX: 0.313 whiteY: 0.329
[    12.515] (II) NOUVEAU(0): Supported established timings:
[    12.515] (II) NOUVEAU(0): 720x400@70Hz
[    12.515] (II) NOUVEAU(0): 640x480@60Hz
[    12.515] (II) NOUVEAU(0): 640x480@75Hz
[    12.515] (II) NOUVEAU(0): 800x600@60Hz
[    12.515] (II) NOUVEAU(0): 800x600@75Hz
[    12.515] (II) NOUVEAU(0): 832x624@75Hz
[    12.515] (II) NOUVEAU(0): 1024x768@60Hz
[    12.515] (II) NOUVEAU(0): 1024x768@75Hz
[    12.515] (II) NOUVEAU(0): 1280x1024@75Hz
[    12.515] (II) NOUVEAU(0): 1152x864@75Hz
[    12.516] (II) NOUVEAU(0): Manufacturer's mask: 0
[    12.516] (II) NOUVEAU(0): Supported standard timings:
[    12.516] (II) NOUVEAU(0): #0: hsize: 1152  vsize 720  refresh: 60  vid: 113
[    12.516] (II) NOUVEAU(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    12.516] (II) NOUVEAU(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    12.516] (II) NOUVEAU(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    12.516] (II) NOUVEAU(0): #4: hsize: 1600  vsize 1000  refresh: 60  vid: 169
[    12.516] (II) NOUVEAU(0): #5: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    12.516] (II) NOUVEAU(0): Supported detailed timing:
[    12.516] (II) NOUVEAU(0): clock: 146.2 MHz   Image Size:  473 x 296 mm
[    12.516] (II) NOUVEAU(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
[    12.516] (II) NOUVEAU(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
[    12.516] (II) NOUVEAU(0): Ranges: V min: 48 V max: 76 Hz, H min: 24 H max: 83 kHz, PixClock max 165 MHz
[    12.516] (II) NOUVEAU(0): Monitor name: HP w2207
[    12.516] (II) NOUVEAU(0): Serial No: 3CQ8201LK4
[    12.516] (II) NOUVEAU(0): EDID (in hex):
[    12.516] (II) NOUVEAU(0): 	00ffffffffffff0022f0a82601010101
[    12.516] (II) NOUVEAU(0): 	14120103682f1e78eeb535a5564a9a25
[    12.516] (II) NOUVEAU(0): 	105054a56b807100814081809500a900
[    12.516] (II) NOUVEAU(0): 	b3000101010121399030621a274068b0
[    12.516] (II) NOUVEAU(0): 	3600d9281100001c000000fd00304c18
[    12.516] (II) NOUVEAU(0): 	5310000a202020202020000000fc0048
[    12.516] (II) NOUVEAU(0): 	502077323230370a20202020000000ff
[    12.516] (II) NOUVEAU(0): 	00334351383230314c4b340a20200026
[    12.516] (II) NOUVEAU(0): EDID vendor "HWP", prod id 9896
[    12.516] (II) NOUVEAU(0): Using EDID range info for horizontal sync
[    12.516] (II) NOUVEAU(0): Using EDID range info for vertical refresh
[    12.516] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    12.516] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    12.516] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    12.516] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    12.516] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    12.516] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    12.516] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    12.516] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    12.516] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    12.516] (II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    12.516] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    12.516] (II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    12.516] (II) NOUVEAU(0): Modeline "1152x720"x60.0   67.32  1152 1208 1328 1504  720 721 724 746 -hsync +vsync (44.8 kHz)
[    12.516] (II) NOUVEAU(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    12.516] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    12.516] (II) NOUVEAU(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    12.516] (II) NOUVEAU(0): Modeline "1600x1000"x60.0  133.14  1600 1704 1872 2144  1000 1001 1004 1035 -hsync +vsync (62.1 kHz)
[    12.516] (II) NOUVEAU(0): Printing probed modes for output VGA-1
[    12.516] (II) NOUVEAU(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    12.516] (II) NOUVEAU(0): Modeline "1600x1000"x60.0  133.16  1600 1704 1872 2144  1000 1001 1004 1035 -hsync +vsync (62.1 kHz)
[    12.516] (II) NOUVEAU(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    12.516] (II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    12.516] (II) NOUVEAU(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    12.516] (II) NOUVEAU(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    12.516] (II) NOUVEAU(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    12.516] (II) NOUVEAU(0): Modeline "1152x720"x60.0   67.28  1152 1208 1328 1504  720 721 724 746 -hsync +vsync (44.7 kHz)
[    12.516] (II) NOUVEAU(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
[    12.516] (II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    12.516] (II) NOUVEAU(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    12.516] (II) NOUVEAU(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    12.516] (II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    12.516] (II) NOUVEAU(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    12.516] (II) NOUVEAU(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    12.516] (II) NOUVEAU(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    12.516] (II) NOUVEAU(0): Output VGA-1 connected
[    12.516] (II) NOUVEAU(0): Using exact sizes for initial modes
[    12.516] (II) NOUVEAU(0): Output VGA-1 using initial mode 1680x1050
[    12.516] (II) NOUVEAU(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    12.516] (--) NOUVEAU(0): Virtual size is 1680x1050 (pitch 0)
[    12.516] (**) NOUVEAU(0):  Driver mode "1680x1050": 146.2 MHz (scaled from 0.0 MHz), 65.3 kHz, 60.0 Hz
[    12.516] (II) NOUVEAU(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    12.516] (**) NOUVEAU(0):  Mode "1600x1000": 133.2 MHz (scaled from 0.0 MHz), 62.1 kHz, 60.0 Hz
[    12.516] (II) NOUVEAU(0): Modeline "1600x1000"x60.0  133.16  1600 1704 1872 2144  1000 1001 1004 1035 -hsync +vsync (62.1 kHz)
[    12.516] (**) NOUVEAU(0):  Driver mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
[    12.516] (II) NOUVEAU(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    12.516] (**) NOUVEAU(0):  Driver mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
[    12.516] (II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    12.516] (**) NOUVEAU(0):  Driver mode "1440x900": 106.5 MHz (scaled from 0.0 MHz), 55.9 kHz, 59.9 Hz
[    12.516] (II) NOUVEAU(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    12.516] (**) NOUVEAU(0):  Driver mode "1280x960": 108.0 MHz (scaled from 0.0 MHz), 60.0 kHz, 60.0 Hz
[    12.516] (II) NOUVEAU(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    12.516] (**) NOUVEAU(0):  Driver mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
[    12.516] (II) NOUVEAU(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    12.516] (**) NOUVEAU(0):  Mode "1152x720": 67.3 MHz (scaled from 0.0 MHz), 44.7 kHz, 60.0 Hz
[    12.516] (II) NOUVEAU(0): Modeline "1152x720"x60.0   67.28  1152 1208 1328 1504  720 721 724 746 -hsync +vsync (44.7 kHz)
[    12.516] (**) NOUVEAU(0):  Driver mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.1 kHz, 75.1 Hz
[    12.516] (II) NOUVEAU(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
[    12.516] (**) NOUVEAU(0):  Driver mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
[    12.516] (II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    12.516] (**) NOUVEAU(0):  Driver mode "832x624": 57.3 MHz (scaled from 0.0 MHz), 49.7 kHz, 74.6 Hz
[    12.516] (II) NOUVEAU(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    12.516] (**) NOUVEAU(0):  Driver mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
[    12.516] (II) NOUVEAU(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    12.517] (**) NOUVEAU(0):  Driver mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.3 Hz
[    12.517] (II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    12.517] (**) NOUVEAU(0):  Driver mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
[    12.517] (II) NOUVEAU(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    12.517] (**) NOUVEAU(0):  Driver mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
[    12.517] (II) NOUVEAU(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    12.517] (**) NOUVEAU(0):  Driver mode "720x400": 28.3 MHz (scaled from 0.0 MHz), 31.5 kHz, 70.1 Hz
[    12.517] (II) NOUVEAU(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    12.517] (**) NOUVEAU(0): Display dimensions: (470, 300) mm
[    12.517] (**) NOUVEAU(0): DPI set to (90, 88)
[    12.517] (II) Loading sub module "fb"
[    12.517] (II) LoadModule: "fb"
[    12.517] (II) Loading /usr/lib/xorg/modules/libfb.so
[    12.517] (II) Module fb: vendor="X.Org Foundation"
[    12.517] 	compiled for 1.11.3, module version = 1.0.0
[    12.517] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    12.517] (II) Loading sub module "exa"
[    12.517] (II) LoadModule: "exa"
[    12.517] (II) Loading /usr/lib/xorg/modules/libexa.so
[    12.524] (II) Module exa: vendor="X.Org Foundation"
[    12.524] 	compiled for 1.11.3, module version = 2.5.0
[    12.524] 	ABI class: X.Org Video Driver, version 11.0
[    12.524] (II) Loading sub module "shadowfb"
[    12.524] (II) LoadModule: "shadowfb"
[    12.525] (II) Loading /usr/lib/xorg/modules/libshadowfb.so
[    12.529] (II) Module shadowfb: vendor="X.Org Foundation"
[    12.529] 	compiled for 1.11.3, module version = 1.0.0
[    12.529] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    12.529] (II) UnloadModule: "vesa"
[    12.529] (II) Unloading vesa
[    12.529] (II) UnloadModule: "fbdev"
[    12.529] (II) Unloading fbdev
[    12.529] (II) UnloadModule: "fbdevhw"
[    12.529] (II) Unloading fbdevhw
[    12.529] (--) Depth 24 pixmap format is 32 bpp
[    12.530] (II) NOUVEAU(0): Opened GPU channel 1
[    12.530] (II) NOUVEAU(0): [DRI2] Setup complete
[    12.530] (II) NOUVEAU(0): [DRI2]   DRI driver: nouveau
[    12.530] (II) NOUVEAU(0): [DRI2]   VDPAU driver: nouveau
[    12.530] (II) NOUVEAU(0): GART: 64MiB available
[    12.538] (II) NOUVEAU(0): GART: Allocated 16MiB as a scratch buffer
[    12.538] (II) EXA(0): Driver allocated offscreen pixmaps
[    12.538] (II) EXA(0): Driver registered support for the following operations:
[    12.538] (II)         Solid
[    12.538] (II)         Copy
[    12.538] (II)         Composite (RENDER acceleration)
[    12.538] (II)         UploadToScreen
[    12.538] (II)         DownloadFromScreen
[    12.538] (==) NOUVEAU(0): Backing store disabled
[    12.538] (==) NOUVEAU(0): Silken mouse enabled
[    12.538] (II) NOUVEAU(0): [XvMC] Associated with NV40 texture adapter.
[    12.538] (II) NOUVEAU(0): [XvMC] Extension initialized.
[    12.538] (==) NOUVEAU(0): DPMS enabled
[    12.538] (II) NOUVEAU(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    12.538] (WW) NOUVEAU(0): Option "NoLogo" is not used
[    12.538] (--) RandR disabled
[    12.538] (II) Initializing built-in extension Generic Event Extension
[    12.538] (II) Initializing built-in extension SHAPE
[    12.538] (II) Initializing built-in extension MIT-SHM
[    12.538] (II) Initializing built-in extension XInputExtension
[    12.538] (II) Initializing built-in extension XTEST
[    12.538] (II) Initializing built-in extension BIG-REQUESTS
[    12.538] (II) Initializing built-in extension SYNC
[    12.538] (II) Initializing built-in extension XKEYBOARD
[    12.538] (II) Initializing built-in extension XC-MISC
[    12.538] (II) Initializing built-in extension SECURITY
[    12.538] (II) Initializing built-in extension XINERAMA
[    12.538] (II) Initializing built-in extension XFIXES
[    12.538] (II) Initializing built-in extension RENDER
[    12.538] (II) Initializing built-in extension RANDR
[    12.538] (II) Initializing built-in extension COMPOSITE
[    12.538] (II) Initializing built-in extension DAMAGE
[    13.144] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    13.144] (II) AIGLX: enabled GLX_INTEL_swap_event
[    13.144] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    13.144] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    13.145] (II) AIGLX: Loaded and initialized nouveau
[    13.145] (II) GLX: Initialized DRI2 GL provider for screen 0
[    13.149] (II) NOUVEAU(0): NVEnterVT is called.
[    13.214] (II) NOUVEAU(0): Setting screen physical size to 444 x 277
[    13.217] resize called 1680 1050
[    13.226] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    13.230] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    13.230] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    13.230] (II) LoadModule: "evdev"
[    13.230] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.230] (II) Module evdev: vendor="X.Org Foundation"
[    13.230] 	compiled for 1.11.3, module version = 2.7.0
[    13.230] 	Module class: X.Org XInput Driver
[    13.230] 	ABI class: X.Org XInput driver, version 16.0
[    13.230] (II) Using input driver 'evdev' for 'Power Button'
[    13.230] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.230] (**) Power Button: always reports core events
[    13.230] (**) evdev: Power Button: Device: "/dev/input/event1"
[    13.230] (--) evdev: Power Button: Vendor 0 Product 0x1
[    13.230] (--) evdev: Power Button: Found keys
[    13.230] (II) evdev: Power Button: Configuring as keyboard
[    13.230] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    13.230] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    13.230] (**) Option "xkb_rules" "evdev"
[    13.230] (**) Option "xkb_model" "pc105"
[    13.230] (**) Option "xkb_layout" "us"
[    13.231] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    13.231] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    13.231] (II) Using input driver 'evdev' for 'Power Button'
[    13.231] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.231] (**) Power Button: always reports core events
[    13.231] (**) evdev: Power Button: Device: "/dev/input/event0"
[    13.231] (--) evdev: Power Button: Vendor 0 Product 0x1
[    13.231] (--) evdev: Power Button: Found keys
[    13.231] (II) evdev: Power Button: Configuring as keyboard
[    13.231] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    13.231] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    13.231] (**) Option "xkb_rules" "evdev"
[    13.231] (**) Option "xkb_model" "pc105"
[    13.231] (**) Option "xkb_layout" "us"
[    13.232] (II) config/udev: Adding input device HDA NVidia Line-Out Surround (/dev/input/event10)
[    13.232] (II) No input driver specified, ignoring this device.
[    13.232] (II) This device may have been added with another device file.
[    13.232] (II) config/udev: Adding input device HDA NVidia Line-Out Front (/dev/input/event11)
[    13.232] (II) No input driver specified, ignoring this device.
[    13.232] (II) This device may have been added with another device file.
[    13.232] (II) config/udev: Adding input device HDA NVidia Line (/dev/input/event4)
[    13.232] (II) No input driver specified, ignoring this device.
[    13.232] (II) This device may have been added with another device file.
[    13.233] (II) config/udev: Adding input device HDA NVidia Front Mic (/dev/input/event5)
[    13.233] (II) No input driver specified, ignoring this device.
[    13.233] (II) This device may have been added with another device file.
[    13.233] (II) config/udev: Adding input device HDA NVidia Rear Mic (/dev/input/event6)
[    13.233] (II) No input driver specified, ignoring this device.
[    13.233] (II) This device may have been added with another device file.
[    13.233] (II) config/udev: Adding input device HDA NVidia Front Headphone (/dev/input/event7)
[    13.233] (II) No input driver specified, ignoring this device.
[    13.233] (II) This device may have been added with another device file.
[    13.233] (II) config/udev: Adding input device HDA NVidia Line-Out Side (/dev/input/event8)
[    13.234] (II) No input driver specified, ignoring this device.
[    13.234] (II) This device may have been added with another device file.
[    13.234] (II) config/udev: Adding input device HDA NVidia Line-Out CLFE (/dev/input/event9)
[    13.234] (II) No input driver specified, ignoring this device.
[    13.234] (II) This device may have been added with another device file.
[    13.234] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    13.234] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    13.234] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    13.234] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.234] (**) AT Translated Set 2 keyboard: always reports core events
[    13.234] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    13.234] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    13.234] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    13.234] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    13.234] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    13.234] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 8)
[    13.234] (**) Option "xkb_rules" "evdev"
[    13.234] (**) Option "xkb_model" "pc105"
[    13.234] (**) Option "xkb_layout" "us"
[    13.235] (II) config/udev: Adding input device ImPS/2 Logitech Wheel Mouse (/dev/input/event3)
[    13.235] (**) ImPS/2 Logitech Wheel Mouse: Applying InputClass "evdev pointer catchall"
[    13.235] (II) Using input driver 'evdev' for 'ImPS/2 Logitech Wheel Mouse'
[    13.235] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.235] (**) ImPS/2 Logitech Wheel Mouse: always reports core events
[    13.235] (**) evdev: ImPS/2 Logitech Wheel Mouse: Device: "/dev/input/event3"
[    13.235] (--) evdev: ImPS/2 Logitech Wheel Mouse: Vendor 0x2 Product 0x5
[    13.235] (--) evdev: ImPS/2 Logitech Wheel Mouse: Found 3 mouse buttons
[    13.235] (--) evdev: ImPS/2 Logitech Wheel Mouse: Found scroll wheel(s)
[    13.235] (--) evdev: ImPS/2 Logitech Wheel Mouse: Found relative axes
[    13.235] (--) evdev: ImPS/2 Logitech Wheel Mouse: Found x and y relative axes
[    13.235] (II) evdev: ImPS/2 Logitech Wheel Mouse: Configuring as mouse
[    13.235] (II) evdev: ImPS/2 Logitech Wheel Mouse: Adding scrollwheel support
[    13.235] (**) evdev: ImPS/2 Logitech Wheel Mouse: YAxisMapping: buttons 4 and 5
[    13.235] (**) evdev: ImPS/2 Logitech Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    13.235] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input3/event3"
[    13.235] (II) XINPUT: Adding extended input device "ImPS/2 Logitech Wheel Mouse" (type: MOUSE, id 9)
[    13.235] (II) evdev: ImPS/2 Logitech Wheel Mouse: initialized for relative axes.
[    13.236] (**) ImPS/2 Logitech Wheel Mouse: (accel) keeping acceleration scheme 1
[    13.236] (**) ImPS/2 Logitech Wheel Mouse: (accel) acceleration profile 0
[    13.236] (**) ImPS/2 Logitech Wheel Mouse: (accel) acceleration factor: 2.000
[    13.236] (**) ImPS/2 Logitech Wheel Mouse: (accel) acceleration threshold: 4
[    13.236] (II) config/udev: Adding input device ImPS/2 Logitech Wheel Mouse (/dev/input/mouse0)
[    13.236] (II) No input driver specified, ignoring this device.
[    13.236] (II) This device may have been added with another device file.
[    14.323] (II) NOUVEAU(0): EDID vendor "HWP", prod id 9896
[    14.324] (II) NOUVEAU(0): Using hsync ranges from config file
[    14.324] (II) NOUVEAU(0): Using vrefresh ranges from config file
[    14.324] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    14.324] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    14.324] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    14.324] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    14.324] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    14.324] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    14.324] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    14.324] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    14.324] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    14.324] (II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    14.324] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    14.324] (II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    14.324] (II) NOUVEAU(0): Modeline "1152x720"x60.0   67.32  1152 1208 1328 1504  720 721 724 746 -hsync +vsync (44.8 kHz)
[    14.324] (II) NOUVEAU(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    14.324] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    14.324] (II) NOUVEAU(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    14.324] (II) NOUVEAU(0): Modeline "1600x1000"x60.0  133.14  1600 1704 1872 2144  1000 1001 1004 1035 -hsync +vsync (62.1 kHz)
[    14.428] (II) NOUVEAU(0): EDID vendor "HWP", prod id 9896
[    14.428] (II) NOUVEAU(0): Using hsync ranges from config file
[    14.428] (II) NOUVEAU(0): Using vrefresh ranges from config file
[    14.428] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    14.428] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    14.428] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    14.428] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    14.428] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    14.428] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    14.428] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    14.428] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    14.428] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    14.428] (II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    14.428] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    14.428] (II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    14.428] (II) NOUVEAU(0): Modeline "1152x720"x60.0   67.32  1152 1208 1328 1504  720 721 724 746 -hsync +vsync (44.8 kHz)
[    14.428] (II) NOUVEAU(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    14.428] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    14.428] (II) NOUVEAU(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    14.428] (II) NOUVEAU(0): Modeline "1600x1000"x60.0  133.14  1600 1704 1872 2144  1000 1001 1004 1035 -hsync +vsync (62.1 kHz)
[    15.474] (II) NOUVEAU(0): EDID vendor "HWP", prod id 9896
[    15.474] (II) NOUVEAU(0): Using hsync ranges from config file
[    15.474] (II) NOUVEAU(0): Using vrefresh ranges from config file
[    15.474] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    15.474] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    15.474] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    15.474] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    15.474] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    15.474] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    15.474] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    15.474] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    15.474] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    15.474] (II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    15.474] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    15.474] (II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    15.474] (II) NOUVEAU(0): Modeline "1152x720"x60.0   67.32  1152 1208 1328 1504  720 721 724 746 -hsync +vsync (44.8 kHz)
[    15.474] (II) NOUVEAU(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    15.474] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    15.474] (II) NOUVEAU(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    15.474] (II) NOUVEAU(0): Modeline "1600x1000"x60.0  133.14  1600 1704 1872 2144  1000 1001 1004 1035 -hsync +vsync (62.1 kHz)
[    15.480] resize called 1680 1050
[    15.591] (II) NOUVEAU(0): EDID vendor "HWP", prod id 9896
[    15.592] (II) NOUVEAU(0): Using hsync ranges from config file
[    15.592] (II) NOUVEAU(0): Using vrefresh ranges from config file
[    15.592] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    15.592] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    15.592] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    15.592] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    15.592] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    15.592] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    15.592] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    15.592] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    15.592] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    15.592] (II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    15.592] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    15.592] (II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    15.592] (II) NOUVEAU(0): Modeline "1152x720"x60.0   67.32  1152 1208 1328 1504  720 721 724 746 -hsync +vsync (44.8 kHz)
[    15.592] (II) NOUVEAU(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    15.592] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    15.592] (II) NOUVEAU(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    15.592] (II) NOUVEAU(0): Modeline "1600x1000"x60.0  133.14  1600 1704 1872 2144  1000 1001 1004 1035 -hsync +vsync (62.1 kHz)
[    15.696] (II) NOUVEAU(0): EDID vendor "HWP", prod id 9896
[    15.696] (II) NOUVEAU(0): Using hsync ranges from config file
[    15.696] (II) NOUVEAU(0): Using vrefresh ranges from config file
[    15.696] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    15.696] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    15.696] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    15.696] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    15.696] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    15.696] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    15.696] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    15.696] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    15.696] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    15.696] (II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    15.696] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    15.696] (II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    15.696] (II) NOUVEAU(0): Modeline "1152x720"x60.0   67.32  1152 1208 1328 1504  720 721 724 746 -hsync +vsync (44.8 kHz)
[    15.696] (II) NOUVEAU(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    15.696] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    15.696] (II) NOUVEAU(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    15.696] (II) NOUVEAU(0): Modeline "1600x1000"x60.0  133.14  1600 1704 1872 2144  1000 1001 1004 1035 -hsync +vsync (62.1 kHz)
```

---

### Post by Zimmer on 2012-09-02
Can you elaborate on when you get the 'out of range message'? At boot , ie when GRUB starts, or after login to your Ubuntu System?

(According to the logfie it appears you are using the NOUVEAU driver, by the way...)

---

### Post by SuperFreak on 2012-09-02
Sorry I guess I wasn't clear.
When I press the power button on the computer it starts right after post but before Ubuntu starts( however just before post there is a pop up indicating the monitor setting is HDMI even though it is connected to the computer with VGA). I don't see the grub menu though it seems to go straight to Ubuntu.

---

### Post by Zimmer on 2012-09-08
Ok, sorry for delay... went away for a few days..

Long shot, but worked with completely black screen on Mrs Zimmer's Biostar trying to boot Mint XCFE.

Boot the system, then:
Edit the   etc/default/grub   file.. you will need to do this as root.(you might want to save a copy first).
Un comment the following line..
#GRUB_GFXMODE=640x480

but also give it a new resolution. 800x600  maybe (I used 1024x768 as that was the res of her monitor but the GRUB text comes out a bit small..) 
eg.
 GRUB_GFXMODE=800x600
 Save the file.
In a terminal run  sudo update-grub 
Then restart and see if that stops the  'Out of Range' message.

If that does not work you can go back and comment out the line again with a #

---

### Post by SuperFreak on 2012-09-08
Thanks,

I won't have access to my neighbours computer till Monday but I will try your suggestion then

---

### Post by SuperFreak on 2012-09-11
That was very helpful @Zimmer
Before the Grub menu did not appear at all just the out of Range error then straight to desktop. Now the Grub screen pauses at startup for a bit (I changed the timeout in the /etc/default/grub file from 10 sec to 3 sec, but it still stays on for about 20 sec) but it is definitely an improvement.
Thanks for your help!

edit: boots to desktop in under a minute which is much better

---

