---
title: "Problem with monitor"
date: 2012-05-17
forum: General Help
---

### Post by doobydave on 2012-05-17
Can anybody come to my assistance?
I have an nvidia card connected to a CRT via a DVI to *edit* VGA adaptor. I have struggled to get 12.04 installed (live cd wouldn't boot without a flag set in grub) and the installed OS will not boot without 'nomodeset' added to the boot options. All is not well though still.

I filled a bug about this issue where there is more detailed info about the symptoms and system. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/991068](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/991068)

I was reading this thread about a similar problem but it concerned an ATI card rather than an nvidia. [http://ubuntuforums.org/showthread.php?t=1938447](http://ubuntuforums.org/showthread.php?t=1938447)

I'm guessing the system is not getting the correct EDID info, but I could be entirely wrong. It's happened before..;)
Thanks.

/longing for times gone by when ctrl alt +/- worked to adjust resolutions and there was a xorg.conf somewhere to edit..

---

### Post by matt_symes on 2012-05-17
Hi

Please post your xorg log file. That may give more information about what is wrong.


```
cat /var/log/Xorg.0.log
```


Use pastebinit if you are having major problems.


Kind regards

---

### Post by doobydave on 2012-05-17
Here goes - this is the xorg.0.log from a failed boot, obtained using ssh.

```

[     9.391] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[     9.391] X Protocol Version 11, Revision 0
[     9.391] Build Operating System: Linux 2.6.42-23-generic i686 Ubuntu
[     9.391] Current Operating System: Linux doobz-1204 3.2.0-24-generic-pae #37-Ubuntu SMP Wed Apr 25 10:47:59 UTC 2012 i686
[     9.391] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-24-generic-pae root=UUID=e57566a6-35f9-48d4-854b-68e581f05406 ro quiet splash vt.handoff=7
[     9.391] Build Date: 20 April 2012  05:12:21AM
[     9.391] xorg-server 2:1.11.4-0ubuntu10.1 (For technical support please see http://www.ubuntu.com/support) 
[     9.391] Current version of pixman: 0.24.4
[     9.391] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[     9.391] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     9.391] (==) Log file: "/var/log/Xorg.0.log", Time: Thu May 17 22:40:48 2012
[     9.391] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     9.392] (==) No Layout section.  Using the first Screen section.
[     9.392] (==) No screen section available. Using defaults.
[     9.392] (**) |-->Screen "Default Screen Section" (0)
[     9.392] (**) |   |-->Monitor "<default monitor>"
[     9.392] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[     9.392] (==) Automatically adding devices
[     9.392] (==) Automatically enabling devices
[     9.392] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     9.392] 	Entry deleted from font path.
[     9.392] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     9.392] 	Entry deleted from font path.
[     9.392] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     9.392] 	Entry deleted from font path.
[     9.392] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     9.392] 	Entry deleted from font path.
[     9.392] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     9.392] 	Entry deleted from font path.
[     9.392] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[     9.392] 	Entry deleted from font path.
[     9.392] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[     9.392] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     9.392] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[     9.392] (II) Loader magic: 0xb77d85a0
[     9.392] (II) Module ABI versions:
[     9.392] 	X.Org ANSI C Emulation: 0.4
[     9.392] 	X.Org Video Driver: 11.0
[     9.392] 	X.Org XInput driver : 16.0
[     9.392] 	X.Org Server Extension : 6.0
[     9.393] (--) PCI:*(0:1:0:0) 10de:0191:3842:c831 rev 162, Mem @ 0xf6000000/16777216, 0xe0000000/268435456, 0xf4000000/33554432, I/O @ 0x0000a000/128, BIOS @ 0x????????/131072
[     9.393] (II) Open ACPI successful (/var/run/acpid.socket)
[     9.393] (II) LoadModule: "extmod"
[     9.395] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[     9.395] (II) Module extmod: vendor="X.Org Foundation"
[     9.395] 	compiled for 1.11.3, module version = 1.0.0
[     9.395] 	Module class: X.Org Server Extension
[     9.395] 	ABI class: X.Org Server Extension, version 6.0
[     9.395] (II) Loading extension MIT-SCREEN-SAVER
[     9.395] (II) Loading extension XFree86-VidModeExtension
[     9.395] (II) Loading extension XFree86-DGA
[     9.395] (II) Loading extension DPMS
[     9.395] (II) Loading extension XVideo
[     9.395] (II) Loading extension XVideo-MotionCompensation
[     9.395] (II) Loading extension X-Resource
[     9.395] (II) LoadModule: "dbe"
[     9.395] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[     9.395] (II) Module dbe: vendor="X.Org Foundation"
[     9.395] 	compiled for 1.11.3, module version = 1.0.0
[     9.395] 	Module class: X.Org Server Extension
[     9.395] 	ABI class: X.Org Server Extension, version 6.0
[     9.395] (II) Loading extension DOUBLE-BUFFER
[     9.395] (II) LoadModule: "glx"
[     9.395] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[     9.396] (II) Module glx: vendor="X.Org Foundation"
[     9.396] 	compiled for 1.11.3, module version = 1.0.0
[     9.396] 	ABI class: X.Org Server Extension, version 6.0
[     9.396] (==) AIGLX enabled
[     9.396] (II) Loading extension GLX
[     9.396] (II) LoadModule: "record"
[     9.396] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[     9.396] (II) Module record: vendor="X.Org Foundation"
[     9.396] 	compiled for 1.11.3, module version = 1.13.0
[     9.396] 	Module class: X.Org Server Extension
[     9.396] 	ABI class: X.Org Server Extension, version 6.0
[     9.396] (II) Loading extension RECORD
[     9.396] (II) LoadModule: "dri"
[     9.396] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[     9.396] (II) Module dri: vendor="X.Org Foundation"
[     9.396] 	compiled for 1.11.3, module version = 1.0.0
[     9.396] 	ABI class: X.Org Server Extension, version 6.0
[     9.396] (II) Loading extension XFree86-DRI
[     9.396] (II) LoadModule: "dri2"
[     9.397] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[     9.397] (II) Module dri2: vendor="X.Org Foundation"
[     9.397] 	compiled for 1.11.3, module version = 1.2.0
[     9.397] 	ABI class: X.Org Server Extension, version 6.0
[     9.397] (II) Loading extension DRI2
[     9.397] (==) Matched nvidia as autoconfigured driver 0
[     9.397] (==) Matched nouveau as autoconfigured driver 1
[     9.397] (==) Matched nv as autoconfigured driver 2
[     9.397] (==) Matched vesa as autoconfigured driver 3
[     9.397] (==) Matched fbdev as autoconfigured driver 4
[     9.397] (==) Assigned the driver to the xf86ConfigLayout
[     9.397] (II) LoadModule: "nvidia"
[     9.397] (WW) Warning, couldn't open module nvidia
[     9.397] (II) UnloadModule: "nvidia"
[     9.397] (II) Unloading nvidia
[     9.397] (EE) Failed to load module "nvidia" (module does not exist, 0)
[     9.397] (II) LoadModule: "nouveau"
[     9.398] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[     9.398] (II) Module nouveau: vendor="X.Org Foundation"
[     9.398] 	compiled for 1.11.3, module version = 0.0.16
[     9.398] 	Module class: X.Org Video Driver
[     9.398] 	ABI class: X.Org Video Driver, version 11.0
[     9.398] (II) LoadModule: "nv"
[     9.398] (WW) Warning, couldn't open module nv
[     9.398] (II) UnloadModule: "nv"
[     9.398] (II) Unloading nv
[     9.398] (EE) Failed to load module "nv" (module does not exist, 0)
[     9.398] (II) LoadModule: "vesa"
[     9.399] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     9.399] (II) Module vesa: vendor="X.Org Foundation"
[     9.399] 	compiled for 1.11.3, module version = 2.3.0
[     9.399] 	Module class: X.Org Video Driver
[     9.399] 	ABI class: X.Org Video Driver, version 11.0
[     9.399] (II) LoadModule: "fbdev"
[     9.399] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     9.399] (II) Module fbdev: vendor="X.Org Foundation"
[     9.399] 	compiled for 1.11.3, module version = 0.4.2
[     9.399] 	ABI class: X.Org Video Driver, version 11.0
[     9.399] (==) Matched nvidia as autoconfigured driver 0
[     9.399] (==) Matched nouveau as autoconfigured driver 1
[     9.399] (==) Matched nv as autoconfigured driver 2
[     9.399] (==) Matched vesa as autoconfigured driver 3
[     9.399] (==) Matched fbdev as autoconfigured driver 4
[     9.399] (==) Assigned the driver to the xf86ConfigLayout
[     9.399] (II) LoadModule: "nvidia"
[     9.399] (WW) Warning, couldn't open module nvidia
[     9.399] (II) UnloadModule: "nvidia"
[     9.399] (II) Unloading nvidia
[     9.399] (EE) Failed to load module "nvidia" (module does not exist, 0)
[     9.399] (II) LoadModule: "nouveau"
[     9.400] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[     9.400] (II) Module nouveau: vendor="X.Org Foundation"
[     9.400] 	compiled for 1.11.3, module version = 0.0.16
[     9.400] 	Module class: X.Org Video Driver
[     9.400] 	ABI class: X.Org Video Driver, version 11.0
[     9.400] (II) UnloadModule: "nouveau"
[     9.400] (II) Unloading nouveau
[     9.400] (II) Failed to load module "nouveau" (already loaded, 0)
[     9.400] (II) LoadModule: "nv"
[     9.400] (WW) Warning, couldn't open module nv
[     9.400] (II) UnloadModule: "nv"
[     9.400] (II) Unloading nv
[     9.400] (EE) Failed to load module "nv" (module does not exist, 0)
[     9.400] (II) LoadModule: "vesa"
[     9.400] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     9.400] (II) Module vesa: vendor="X.Org Foundation"
[     9.400] 	compiled for 1.11.3, module version = 2.3.0
[     9.400] 	Module class: X.Org Video Driver
[     9.400] 	ABI class: X.Org Video Driver, version 11.0
[     9.400] (II) UnloadModule: "vesa"
[     9.400] (II) Unloading vesa
[     9.400] (II) Failed to load module "vesa" (already loaded, 0)
[     9.400] (II) LoadModule: "fbdev"
[     9.401] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     9.401] (II) Module fbdev: vendor="X.Org Foundation"
[     9.401] 	compiled for 1.11.3, module version = 0.4.2
[     9.401] 	ABI class: X.Org Video Driver, version 11.0
[     9.401] (II) UnloadModule: "fbdev"
[     9.401] (II) Unloading fbdev
[     9.401] (II) Failed to load module "fbdev" (already loaded, 0)
[     9.401] (II) NOUVEAU driver Date:   Wed Nov 30 18:56:54 2011 +0100
[     9.401] (II) NOUVEAU driver for NVIDIA chipset families :
[     9.401] 	RIVA TNT        (NV04)
[     9.401] 	RIVA TNT2       (NV05)
[     9.401] 	GeForce 256     (NV10)
[     9.401] 	GeForce 2       (NV11, NV15)
[     9.401] 	GeForce 4MX     (NV17, NV18)
[     9.401] 	GeForce 3       (NV20)
[     9.401] 	GeForce 4Ti     (NV25, NV28)
[     9.401] 	GeForce FX      (NV3x)
[     9.401] 	GeForce 6       (NV4x)
[     9.401] 	GeForce 7       (G7x)
[     9.401] 	GeForce 8       (G8x)
[     9.401] 	GeForce GTX 200 (NVA0)
[     9.401] 	GeForce GTX 400 (NVC0)
[     9.401] (II) VESA: driver for VESA chipsets: vesa
[     9.401] (II) FBDEV: driver for framebuffer: fbdev
[     9.401] (++) using VT number 7

[     9.401] drmOpenDevice: node name is /dev/dri/card0
[     9.401] drmOpenDevice: open result is 8, (OK)
[     9.401] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[     9.401] drmOpenDevice: node name is /dev/dri/card0
[     9.401] drmOpenDevice: open result is 8, (OK)
[     9.401] drmOpenByBusid: drmOpenMinor returns 8
[     9.401] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[     9.401] (II) [drm] nouveau interface version: 0.0.16
[     9.401] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[     9.401] (WW) Falling back to old probe method for vesa
[     9.401] (WW) Falling back to old probe method for fbdev
[     9.401] (II) Loading sub module "fbdevhw"
[     9.401] (II) LoadModule: "fbdevhw"
[     9.402] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     9.402] (II) Module fbdevhw: vendor="X.Org Foundation"
[     9.402] 	compiled for 1.11.3, module version = 0.0.2
[     9.402] 	ABI class: X.Org Video Driver, version 11.0
[     9.402] (II) Loading sub module "dri"
[     9.402] (II) LoadModule: "dri"
[     9.402] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[     9.402] (II) Module dri: vendor="X.Org Foundation"
[     9.402] 	compiled for 1.11.3, module version = 1.0.0
[     9.402] 	ABI class: X.Org Server Extension, version 6.0
[     9.402] (II) NOUVEAU(0): Loaded DRI module
[     9.402] drmOpenDevice: node name is /dev/dri/card0
[     9.402] drmOpenDevice: open result is 9, (OK)
[     9.402] drmOpenDevice: node name is /dev/dri/card0
[     9.402] drmOpenDevice: open result is 9, (OK)
[     9.402] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[     9.402] drmOpenDevice: node name is /dev/dri/card0
[     9.402] drmOpenDevice: open result is 9, (OK)
[     9.402] drmOpenByBusid: drmOpenMinor returns 9
[     9.402] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[     9.402] (II) [drm] DRM interface version 1.4
[     9.402] (II) [drm] DRM open master succeeded.
[     9.402] (--) NOUVEAU(0): Chipset: "NVIDIA NV50"
[     9.402] (II) NOUVEAU(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[     9.402] (==) NOUVEAU(0): Depth 24, (--) framebuffer bpp 32
[     9.402] (==) NOUVEAU(0): RGB weight 888
[     9.402] (==) NOUVEAU(0): Default visual is TrueColor
[     9.403] (==) NOUVEAU(0): Using HW cursor
[     9.403] (==) NOUVEAU(0): GLX sync to VBlank disabled.
[     9.403] (==) NOUVEAU(0): Page flipping enabled
[     9.515] (II) NOUVEAU(0): Output DVI-I-1 has no monitor section
[     9.619] (II) NOUVEAU(0): Output DVI-I-2 has no monitor section
[     9.723] (II) NOUVEAU(0): EDID for output DVI-I-1
[     9.723] (II) NOUVEAU(0): Manufacturer: IVM  Model: 2140  Serial#: 10037195
[     9.723] (II) NOUVEAU(0): Year: 2000  Week: 5
[     9.723] (II) NOUVEAU(0): EDID Version: 1.1
[     9.723] (II) NOUVEAU(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[     9.723] (II) NOUVEAU(0): Sync:  Separate  Composite  SyncOnGreen
[     9.723] (II) NOUVEAU(0): Max Image Size [cm]: horiz.: 40  vert.: 30
[     9.723] (II) NOUVEAU(0): Gamma: 2.54
[     9.723] (II) NOUVEAU(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[     9.723] (II) NOUVEAU(0): redX: 0.625 redY: 0.340   greenX: 0.292 greenY: 0.604
[     9.723] (II) NOUVEAU(0): blueX: 0.150 blueY: 0.070   whiteX: 0.283 whiteY: 0.297
[     9.723] (II) NOUVEAU(0): Supported established timings:
[     9.723] (II) NOUVEAU(0): 640x480@60Hz
[     9.723] (II) NOUVEAU(0): 640x480@67Hz
[     9.723] (II) NOUVEAU(0): 640x480@72Hz
[     9.723] (II) NOUVEAU(0): 640x480@75Hz
[     9.723] (II) NOUVEAU(0): 800x600@56Hz
[     9.723] (II) NOUVEAU(0): 800x600@60Hz
[     9.723] (II) NOUVEAU(0): 800x600@72Hz
[     9.723] (II) NOUVEAU(0): 800x600@75Hz
[     9.723] (II) NOUVEAU(0): 832x624@75Hz
[     9.723] (II) NOUVEAU(0): 1024x768@60Hz
[     9.723] (II) NOUVEAU(0): 1024x768@70Hz
[     9.723] (II) NOUVEAU(0): 1024x768@75Hz
[     9.723] (II) NOUVEAU(0): 1280x1024@75Hz
[     9.723] (II) NOUVEAU(0): 1152x864@75Hz
[     9.723] (II) NOUVEAU(0): Manufacturer's mask: 0
[     9.723] (II) NOUVEAU(0): Supported standard timings:
[     9.723] (II) NOUVEAU(0): #0: hsize: 1600  vsize 1200  refresh: 97  vid: 26025
[     9.723] (II) NOUVEAU(0): #1: hsize: 1792  vsize 1344  refresh: 75  vid: 20417
[     9.723] (II) NOUVEAU(0): #2: hsize: 1856  vsize 1392  refresh: 75  vid: 20425
[     9.723] (II) NOUVEAU(0): #3: hsize: 2048  vsize 1536  refresh: 80  vid: 21729
[     9.723] (II) NOUVEAU(0):  
[     9.723] (II) NOUVEAU(0):  
[     9.723] (II) NOUVEAU(0):  
[     9.723] (II) NOUVEAU(0):  
[     9.723] (II) NOUVEAU(0): EDID (in hex):
[     9.723] (II) NOUVEAU(0): 	00ffffffffffff0026cd4021cb279900
[     9.723] (II) NOUVEAU(0): 	050a01010e281e9ae80e88a0574a9a26
[     9.723] (II) NOUVEAU(0): 	12484c3fef80a965c14fc94fe1540101
[     9.723] (II) NOUVEAU(0): 	010101010101000000fe000000000000
[     9.723] (II) NOUVEAU(0): 	0000000000000000000000fe00000000
[     9.723] (II) NOUVEAU(0): 	00000000000000000000000000fe0000
[     9.723] (II) NOUVEAU(0): 	000000000000000000000000000000fe
[     9.723] (II) NOUVEAU(0): 	000000000000000000000000000000ea
[     9.723] (II) NOUVEAU(0): EDID vendor "IVM", prod id 8512
[     9.723] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[     9.723] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[     9.723] (II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[     9.723] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[     9.723] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[     9.723] (II) NOUVEAU(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[     9.723] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[     9.723] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[     9.723] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[     9.723] (II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[     9.723] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[     9.723] (II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[     9.723] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[     9.723] (II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[     9.723] (II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[     9.723] (II) NOUVEAU(0): Modeline "1792x1344"x0.0  261.00  1792 1888 2104 2456  1344 1345 1348 1417 -hsync +vsync (106.3 kHz)
[     9.723] (II) NOUVEAU(0): Modeline "1856x1392"x0.0  288.00  1856 1984 2208 2560  1392 1393 1396 1500 -hsync +vsync (112.5 kHz)
[     9.724] (II) NOUVEAU(0): Printing probed modes for output DVI-I-1
[     9.724] (II) NOUVEAU(0): Modeline "1856x1392"x75.0  288.00  1856 1984 2208 2560  1392 1395 1399 1500 -hsync +vsync (112.5 kHz)
[     9.724] (II) NOUVEAU(0): Modeline "1792x1344"x75.0  261.00  1792 1888 2104 2456  1344 1345 1348 1417 -hsync +vsync (106.3 kHz)
[     9.724] (II) NOUVEAU(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[     9.724] (II) NOUVEAU(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[     9.724] (II) NOUVEAU(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
[     9.724] (II) NOUVEAU(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[     9.724] (II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[     9.724] (II) NOUVEAU(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[     9.724] (II) NOUVEAU(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[     9.724] (II) NOUVEAU(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[     9.724] (II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[     9.724] (II) NOUVEAU(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[     9.724] (II) NOUVEAU(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
[     9.724] (II) NOUVEAU(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[     9.724] (II) NOUVEAU(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[     9.724] (II) NOUVEAU(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[     9.828] (II) NOUVEAU(0): EDID for output DVI-I-2
[     9.828] (II) NOUVEAU(0): Output DVI-I-1 connected
[     9.828] (II) NOUVEAU(0): Output DVI-I-2 disconnected
[     9.828] (II) NOUVEAU(0): Using exact sizes for initial modes
[     9.828] (II) NOUVEAU(0): Output DVI-I-1 using initial mode 1856x1392
[     9.828] (II) NOUVEAU(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[     9.828] (--) NOUVEAU(0): Virtual size is 1856x1392 (pitch 0)
[     9.828] (**) NOUVEAU(0):  Driver mode "1856x1392": 288.0 MHz (scaled from 0.0 MHz), 112.5 kHz, 75.0 Hz
[     9.828] (II) NOUVEAU(0): Modeline "1856x1392"x75.0  288.00  1856 1984 2208 2560  1392 1395 1399 1500 -hsync +vsync (112.5 kHz)
[     9.828] (**) NOUVEAU(0):  Driver mode "1792x1344": 261.0 MHz (scaled from 0.0 MHz), 106.3 kHz, 75.0 Hz
[     9.828] (II) NOUVEAU(0): Modeline "1792x1344"x75.0  261.00  1792 1888 2104 2456  1344 1345 1348 1417 -hsync +vsync (106.3 kHz)
[     9.828] (**) NOUVEAU(0):  Driver mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
[     9.828] (II) NOUVEAU(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[     9.828] (**) NOUVEAU(0):  Driver mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
[     9.828] (II) NOUVEAU(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[     9.828] (**) NOUVEAU(0):  Driver mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.1 kHz, 75.1 Hz
[     9.828] (II) NOUVEAU(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
[     9.828] (**) NOUVEAU(0):  Driver mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.1 Hz
[     9.828] (II) NOUVEAU(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[     9.828] (**) NOUVEAU(0):  Driver mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
[     9.828] (II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[     9.828] (**) NOUVEAU(0):  Driver mode "832x624": 57.3 MHz (scaled from 0.0 MHz), 49.7 kHz, 74.6 Hz
[     9.828] (II) NOUVEAU(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[     9.828] (**) NOUVEAU(0):  Driver mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.2 Hz
[     9.828] (II) NOUVEAU(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[     9.828] (**) NOUVEAU(0):  Driver mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
[     9.828] (II) NOUVEAU(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[     9.828] (**) NOUVEAU(0):  Driver mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.3 Hz
[     9.828] (II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[     9.828] (**) NOUVEAU(0):  Driver mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.2 Hz
[     9.828] (II) NOUVEAU(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[     9.828] (**) NOUVEAU(0):  Driver mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.8 Hz
[     9.828] (II) NOUVEAU(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
[     9.828] (**) NOUVEAU(0):  Driver mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
[     9.828] (II) NOUVEAU(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[     9.828] (**) NOUVEAU(0):  Driver mode "640x480": 30.2 MHz (scaled from 0.0 MHz), 35.0 kHz, 66.7 Hz
[     9.829] (II) NOUVEAU(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[     9.829] (**) NOUVEAU(0):  Driver mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
[     9.829] (II) NOUVEAU(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[     9.829] (**) NOUVEAU(0): Display dimensions: (400, 300) mm
[     9.829] (**) NOUVEAU(0): DPI set to (117, 117)
[     9.829] (II) Loading sub module "fb"
[     9.829] (II) LoadModule: "fb"
[     9.829] (II) Loading /usr/lib/xorg/modules/libfb.so
[     9.829] (II) Module fb: vendor="X.Org Foundation"
[     9.829] 	compiled for 1.11.3, module version = 1.0.0
[     9.829] 	ABI class: X.Org ANSI C Emulation, version 0.4
[     9.829] (II) Loading sub module "exa"
[     9.829] (II) LoadModule: "exa"
[     9.829] (II) Loading /usr/lib/xorg/modules/libexa.so
[     9.829] (II) Module exa: vendor="X.Org Foundation"
[     9.829] 	compiled for 1.11.3, module version = 2.5.0
[     9.829] 	ABI class: X.Org Video Driver, version 11.0
[     9.829] (II) Loading sub module "shadowfb"
[     9.829] (II) LoadModule: "shadowfb"
[     9.829] (II) Loading /usr/lib/xorg/modules/libshadowfb.so
[     9.830] (II) Module shadowfb: vendor="X.Org Foundation"
[     9.830] 	compiled for 1.11.3, module version = 1.0.0
[     9.830] 	ABI class: X.Org ANSI C Emulation, version 0.4
[     9.830] (II) UnloadModule: "vesa"
[     9.830] (II) Unloading vesa
[     9.830] (II) UnloadModule: "fbdev"
[     9.830] (II) Unloading fbdev
[     9.830] (II) UnloadModule: "fbdevhw"
[     9.830] (II) Unloading fbdevhw
[     9.830] (--) Depth 24 pixmap format is 32 bpp
[     9.834] (II) NOUVEAU(0): Opened GPU channel 2
[     9.834] (II) NOUVEAU(0): [DRI2] Setup complete
[     9.834] (II) NOUVEAU(0): [DRI2]   DRI driver: nouveau
[     9.834] (II) NOUVEAU(0): [DRI2]   VDPAU driver: nouveau
[     9.834] (II) NOUVEAU(0): GART: 512MiB available
[     9.842] (II) NOUVEAU(0): GART: Allocated 16MiB as a scratch buffer
[     9.842] (II) EXA(0): Driver allocated offscreen pixmaps
[     9.842] (II) EXA(0): Driver registered support for the following operations:
[     9.842] (II)         Solid
[     9.842] (II)         Copy
[     9.842] (II)         Composite (RENDER acceleration)
[     9.842] (II)         UploadToScreen
[     9.842] (II)         DownloadFromScreen
[     9.842] (==) NOUVEAU(0): Backing store disabled
[     9.842] (==) NOUVEAU(0): Silken mouse enabled
[     9.843] (II) NOUVEAU(0): [XvMC] Associated with Nouveau GeForce 8/9 Textured Video.
[     9.843] (II) NOUVEAU(0): [XvMC] Extension initialized.
[     9.843] (==) NOUVEAU(0): DPMS enabled
[     9.843] (II) NOUVEAU(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[     9.843] (--) RandR disabled
[     9.843] (II) Initializing built-in extension Generic Event Extension
[     9.843] (II) Initializing built-in extension SHAPE
[     9.843] (II) Initializing built-in extension MIT-SHM
[     9.843] (II) Initializing built-in extension XInputExtension
[     9.843] (II) Initializing built-in extension XTEST
[     9.843] (II) Initializing built-in extension BIG-REQUESTS
[     9.843] (II) Initializing built-in extension SYNC
[     9.843] (II) Initializing built-in extension XKEYBOARD
[     9.843] (II) Initializing built-in extension XC-MISC
[     9.843] (II) Initializing built-in extension SECURITY
[     9.843] (II) Initializing built-in extension XINERAMA
[     9.843] (II) Initializing built-in extension XFIXES
[     9.843] (II) Initializing built-in extension RENDER
[     9.843] (II) Initializing built-in extension RANDR
[     9.843] (II) Initializing built-in extension COMPOSITE
[     9.843] (II) Initializing built-in extension DAMAGE
[     9.868] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[     9.868] (II) AIGLX: enabled GLX_INTEL_swap_event
[     9.868] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[     9.868] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[     9.868] (II) AIGLX: Loaded and initialized nouveau
[     9.868] (II) GLX: Initialized DRI2 GL provider for screen 0
[     9.876] (II) NOUVEAU(0): NVEnterVT is called.
[     9.922] (II) NOUVEAU(0): Setting screen physical size to 491 x 368
[     9.922] resize called 1856 1392
[     9.930] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[     9.933] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[     9.933] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     9.933] (II) LoadModule: "evdev"
[     9.933] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     9.933] (II) Module evdev: vendor="X.Org Foundation"
[     9.933] 	compiled for 1.11.3, module version = 2.7.0
[     9.933] 	Module class: X.Org XInput Driver
[     9.933] 	ABI class: X.Org XInput driver, version 16.0
[     9.933] (II) Using input driver 'evdev' for 'Power Button'
[     9.933] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     9.933] (**) Power Button: always reports core events
[     9.933] (**) evdev: Power Button: Device: "/dev/input/event1"
[     9.934] (--) evdev: Power Button: Vendor 0 Product 0x1
[     9.934] (--) evdev: Power Button: Found keys
[     9.934] (II) evdev: Power Button: Configuring as keyboard
[     9.934] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[     9.934] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     9.934] (**) Option "xkb_rules" "evdev"
[     9.934] (**) Option "xkb_model" "pc105"
[     9.934] (**) Option "xkb_layout" "gb"
[     9.936] (II) XKB: reuse xkmfile /var/lib/xkb/server-2B4266AA55228AE7D9557A18F1965DBA19850816.xkm
[     9.937] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[     9.937] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     9.937] (II) Using input driver 'evdev' for 'Power Button'
[     9.937] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     9.937] (**) Power Button: always reports core events
[     9.937] (**) evdev: Power Button: Device: "/dev/input/event0"
[     9.937] (--) evdev: Power Button: Vendor 0 Product 0x1
[     9.937] (--) evdev: Power Button: Found keys
[     9.937] (II) evdev: Power Button: Configuring as keyboard
[     9.937] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[     9.937] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[     9.937] (**) Option "xkb_rules" "evdev"
[     9.937] (**) Option "xkb_model" "pc105"
[     9.937] (**) Option "xkb_layout" "gb"
[     9.937] (II) config/udev: Adding input device Logitech Optical USB Mouse (/dev/input/event3)
[     9.937] (**) Logitech Optical USB Mouse: Applying InputClass "evdev pointer catchall"
[     9.937] (II) Using input driver 'evdev' for 'Logitech Optical USB Mouse'
[     9.937] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     9.937] (**) Logitech Optical USB Mouse: always reports core events
[     9.938] (**) evdev: Logitech Optical USB Mouse: Device: "/dev/input/event3"
[     9.938] (--) evdev: Logitech Optical USB Mouse: Vendor 0x46d Product 0xc016
[     9.938] (--) evdev: Logitech Optical USB Mouse: Found 3 mouse buttons
[     9.938] (--) evdev: Logitech Optical USB Mouse: Found scroll wheel(s)
[     9.938] (--) evdev: Logitech Optical USB Mouse: Found relative axes
[     9.938] (--) evdev: Logitech Optical USB Mouse: Found x and y relative axes
[     9.938] (II) evdev: Logitech Optical USB Mouse: Configuring as mouse
[     9.938] (II) evdev: Logitech Optical USB Mouse: Adding scrollwheel support
[     9.938] (**) evdev: Logitech Optical USB Mouse: YAxisMapping: buttons 4 and 5
[     9.938] (**) evdev: Logitech Optical USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     9.938] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.0/input/input3/event3"
[     9.938] (II) XINPUT: Adding extended input device "Logitech Optical USB Mouse" (type: MOUSE, id 8)
[     9.938] (II) evdev: Logitech Optical USB Mouse: initialized for relative axes.
[     9.938] (**) Logitech Optical USB Mouse: (accel) keeping acceleration scheme 1
[     9.938] (**) Logitech Optical USB Mouse: (accel) acceleration profile 0
[     9.938] (**) Logitech Optical USB Mouse: (accel) acceleration factor: 2.000
[     9.938] (**) Logitech Optical USB Mouse: (accel) acceleration threshold: 4
[     9.938] (II) config/udev: Adding input device Logitech Optical USB Mouse (/dev/input/mouse0)
[     9.938] (II) No input driver specified, ignoring this device.
[     9.938] (II) This device may have been added with another device file.
[     9.939] (II) config/udev: Adding input device ORTEK Smartpad Keyboard (/dev/input/event4)
[     9.939] (**) ORTEK Smartpad Keyboard: Applying InputClass "evdev keyboard catchall"
[     9.939] (II) Using input driver 'evdev' for 'ORTEK Smartpad Keyboard'
[     9.939] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     9.939] (**) ORTEK Smartpad Keyboard: always reports core events
[     9.939] (**) evdev: ORTEK Smartpad Keyboard: Device: "/dev/input/event4"
[     9.939] (--) evdev: ORTEK Smartpad Keyboard: Vendor 0x5a4 Product 0x2000
[     9.939] (--) evdev: ORTEK Smartpad Keyboard: Found keys
[     9.939] (II) evdev: ORTEK Smartpad Keyboard: Configuring as keyboard
[     9.939] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.0/input/input4/event4"
[     9.939] (II) XINPUT: Adding extended input device "ORTEK Smartpad Keyboard" (type: KEYBOARD, id 9)
[     9.939] (**) Option "xkb_rules" "evdev"
[     9.939] (**) Option "xkb_model" "pc105"
[     9.939] (**) Option "xkb_layout" "gb"
[     9.939] (II) config/udev: Adding input device ORTEK Smartpad Keyboard (/dev/input/event5)
[     9.939] (**) ORTEK Smartpad Keyboard: Applying InputClass "evdev pointer catchall"
[     9.939] (**) ORTEK Smartpad Keyboard: Applying InputClass "evdev keyboard catchall"
[     9.939] (II) Using input driver 'evdev' for 'ORTEK Smartpad Keyboard'
[     9.939] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     9.939] (**) ORTEK Smartpad Keyboard: always reports core events
[     9.939] (**) evdev: ORTEK Smartpad Keyboard: Device: "/dev/input/event5"
[     9.939] (--) evdev: ORTEK Smartpad Keyboard: Vendor 0x5a4 Product 0x2000
[     9.939] (--) evdev: ORTEK Smartpad Keyboard: Found 9 mouse buttons
[     9.939] (--) evdev: ORTEK Smartpad Keyboard: Found scroll wheel(s)
[     9.940] (--) evdev: ORTEK Smartpad Keyboard: Found relative axes
[     9.940] (--) evdev: ORTEK Smartpad Keyboard: Found x and y relative axes
[     9.940] (--) evdev: ORTEK Smartpad Keyboard: Found absolute axes
[     9.940] (II) evdev: ORTEK Smartpad Keyboard: Forcing absolute x/y axes to exist.
[     9.940] (--) evdev: ORTEK Smartpad Keyboard: Found keys
[     9.940] (II) evdev: ORTEK Smartpad Keyboard: Configuring as mouse
[     9.940] (II) evdev: ORTEK Smartpad Keyboard: Configuring as keyboard
[     9.940] (II) evdev: ORTEK Smartpad Keyboard: Adding scrollwheel support
[     9.940] (**) evdev: ORTEK Smartpad Keyboard: YAxisMapping: buttons 4 and 5
[     9.940] (**) evdev: ORTEK Smartpad Keyboard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     9.940] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.1/input/input5/event5"
[     9.940] (II) XINPUT: Adding extended input device "ORTEK Smartpad Keyboard" (type: KEYBOARD, id 10)
[     9.940] (**) Option "xkb_rules" "evdev"
[     9.940] (**) Option "xkb_model" "pc105"
[     9.940] (**) Option "xkb_layout" "gb"
[     9.940] (II) evdev: ORTEK Smartpad Keyboard: initialized for relative axes.
[     9.940] (WW) evdev: ORTEK Smartpad Keyboard: ignoring absolute axes.
[     9.940] (**) ORTEK Smartpad Keyboard: (accel) keeping acceleration scheme 1
[     9.940] (**) ORTEK Smartpad Keyboard: (accel) acceleration profile 0
[     9.940] (**) ORTEK Smartpad Keyboard: (accel) acceleration factor: 2.000
[     9.940] (**) ORTEK Smartpad Keyboard: (accel) acceleration threshold: 4
[     9.940] (II) config/udev: Adding input device ORTEK Smartpad Keyboard (/dev/input/mouse1)
[     9.940] (II) No input driver specified, ignoring this device.
[     9.940] (II) This device may have been added with another device file.
[     9.941] (II) config/udev: Adding input device HDA Intel Line-Out (/dev/input/event10)
[     9.941] (II) No input driver specified, ignoring this device.
[     9.941] (II) This device may have been added with another device file.
[     9.941] (II) config/udev: Adding input device HDA Intel Line (/dev/input/event6)
[     9.941] (II) No input driver specified, ignoring this device.
[     9.941] (II) This device may have been added with another device file.
[     9.941] (II) config/udev: Adding input device HDA Intel Front Mic (/dev/input/event7)
[     9.941] (II) No input driver specified, ignoring this device.
[     9.941] (II) This device may have been added with another device file.
[     9.941] (II) config/udev: Adding input device HDA Intel Rear Mic (/dev/input/event8)
[     9.941] (II) No input driver specified, ignoring this device.
[     9.941] (II) This device may have been added with another device file.
[     9.942] (II) config/udev: Adding input device HDA Intel Front Headphone (/dev/input/event9)
[     9.942] (II) No input driver specified, ignoring this device.
[     9.942] (II) This device may have been added with another device file.
[     9.942] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[     9.942] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[     9.942] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[     9.942] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     9.942] (**) AT Translated Set 2 keyboard: always reports core events
[     9.942] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[     9.942] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[     9.942] (--) evdev: AT Translated Set 2 keyboard: Found keys
[     9.942] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[     9.942] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[     9.942] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 11)
[     9.942] (**) Option "xkb_rules" "evdev"
[     9.942] (**) Option "xkb_model" "pc105"
[     9.942] (**) Option "xkb_layout" "gb"
[    10.344] (II) NOUVEAU(0): EDID vendor "IVM", prod id 8512
[    10.345] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    10.345] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    10.345] (II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    10.345] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    10.345] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    10.345] (II) NOUVEAU(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    10.345] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    10.345] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    10.345] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    10.345] (II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    10.345] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    10.345] (II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    10.345] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    10.345] (II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    10.345] (II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    10.345] (II) NOUVEAU(0): Modeline "1792x1344"x0.0  261.00  1792 1888 2104 2456  1344 1345 1348 1417 -hsync +vsync (106.3 kHz)
[    10.345] (II) NOUVEAU(0): Modeline "1856x1392"x0.0  288.00  1856 1984 2208 2560  1392 1393 1396 1500 -hsync +vsync (112.5 kHz)
[    11.089] (II) NOUVEAU(0): EDID vendor "IVM", prod id 8512
[    11.089] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    11.089] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    11.089] (II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    11.089] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    11.089] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    11.089] (II) NOUVEAU(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    11.089] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    11.089] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    11.089] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    11.089] (II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    11.089] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    11.089] (II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    11.089] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    11.089] (II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    11.089] (II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    11.089] (II) NOUVEAU(0): Modeline "1792x1344"x0.0  261.00  1792 1888 2104 2456  1344 1345 1348 1417 -hsync +vsync (106.3 kHz)
[    11.089] (II) NOUVEAU(0): Modeline "1856x1392"x0.0  288.00  1856 1984 2208 2560  1392 1393 1396 1500 -hsync +vsync (112.5 kHz)
[    12.208] (II) XKB: reuse xkmfile /var/lib/xkb/server-03AF3717FF3AB439A4BAABA686CCB40771CDF520.xkm
[    13.586] (II) NOUVEAU(0): EDID vendor "IVM", prod id 8512
[    13.586] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    13.586] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    13.586] (II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    13.586] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    13.586] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    13.586] (II) NOUVEAU(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    13.586] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    13.586] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    13.586] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    13.586] (II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    13.586] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    13.586] (II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    13.586] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    13.586] (II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    13.586] (II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    13.586] (II) NOUVEAU(0): Modeline "1792x1344"x0.0  261.00  1792 1888 2104 2456  1344 1345 1348 1417 -hsync +vsync (106.3 kHz)
[    13.586] (II) NOUVEAU(0): Modeline "1856x1392"x0.0  288.00  1856 1984 2208 2560  1392 1393 1396 1500 -hsync +vsync (112.5 kHz)
[    31.361] (II) NOUVEAU(0): EDID vendor "IVM", prod id 8512
[    31.361] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    31.361] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    31.361] (II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    31.361] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    31.361] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    31.361] (II) NOUVEAU(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    31.361] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    31.361] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    31.361] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    31.361] (II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    31.361] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    31.361] (II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    31.361] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    31.361] (II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    31.361] (II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    31.361] (II) NOUVEAU(0): Modeline "1792x1344"x0.0  261.00  1792 1888 2104 2456  1344 1345 1348 1417 -hsync +vsync (106.3 kHz)
[    31.361] (II) NOUVEAU(0): Modeline "1856x1392"x0.0  288.00  1856 1984 2208 2560  1392 1393 1396 1500 -hsync +vsync (112.5 kHz)

```

---

### Post by doobydave on 2012-05-18
Many of the modelines appear to be set at 0.0 Hz

The monitor is very capable (120Hz at the lower resolutions) - one of the reasons I haven't thrown it yet.

---

### Post by matt_symes on 2012-05-18
Hi

Well it is getting EDID information. I am not convinced the EDID information is your problem yet although i am surprised as it looks like you are getting v1.0 data back.

Can you post a link to the DVI to RGB adaptor you are using.

Can you also give a description of the issues you are currently having.

Does the monitor have a standard VGA connector. If so, can you plug into that (bypassing the dvi adaptor) and boot up and post the new Xorg.0.log file.

What is the exact make and model of your monitor and video card ?

For the graphics card.

```
sudo lshw -c display
```

For the monitor

```
sudo apt-get install read-edid
```

```
get-edid | parse-edid
```

You said you had to disable kernel mode setting to boot into the live CD. Did you do this for your install after you installed it to the hard drive ?

Have you tried the proprietary drivers from nvidia (as you are currently using nouveau) ?

Kind regards

---

### Post by doobydave on 2012-05-18
So sorry, it is a DVI to VGA (rather than RGB) adapter that I am using (never been very good with video TLAs) - made by XFX I believe.

Monitor is an iiyama vision master pro 510, card is an nvidia 8800gtx (i think) with 2 dvi outputs only. I do not have a native DVI monitor to hand, only a small LCD with VGA.

```

:~$ sudo lshw -c display
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: G80 [GeForce 8800 GTX]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:f6000000-f6ffffff memory:e0000000-efffffff memory:f4000000-f5ffffff ioport:a000(size=128) memory:f7000000-f701ffff

```
Had to use ACPI=OFF (I think) to boot live CD - otherwise machine would hang before boot had completed - flashing purple screen (this yielded one quater of the (hung) boot screen when I swapped monitors)

Have to use nomodeset to boot to the desktop otherwise get flashing grey screen (though machine has booted, as I can ssh in or ctrl-alt-f1 to an invisible terminal)

```

:~$ sudo get-edid | parse-edid
parse-edid: parse-edid version 2.0.0
get-edid: get-edid version 2.0.0

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
	Function supported
	Call successful

	VBE version 300
	VBE string at 0x2110 "NVIDIA"

VBE/DDC service about to be called
	Report DDC capabilities

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f15 bx=0x0 cx=0x0
	Function supported
	Call successful

	Monitor and video card combination does not support DDC1 transfers
	Monitor and video card combination does not support DDC2 transfers
	0 seconds per 128 byte EDID block transfer
	Screen is not blanked during DDC transfer

Reading next EDID block

VBE/DDC service about to be called
	Read EDID

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
	Function supported
	Call failed

The EDID data should not be trusted as the VBE call failed
Error: output block unchanged
parse-edid: IO error reading EDID

```

---

### Post by doobydave on 2012-05-18
As for trying the proprietary drivers, is that not what Ubuntu is doing without the 'nomodeset' flag?

---

### Post by doobydave on 2012-05-18
There appears to be a lot of EDID related problems surfacing recently - I imagine many people aren't sure why their machines don't work with recent linux distros. It's by no means limited to Ubuntu.

I am looking at trying to get the correct EDID from my windows install and creating a xorg.conf (or whatever needs to be done to get the nouveau driver to drive the display properly).

/shameless triple-posting bump

---

### Post by scottsdale on 2012-05-18
I have the same set up here. Right down to the monitor type and using a converter connector. Only difference is I have an 8600GT. Runing fresh install 12.04 LTS.
 
I downloaded my driver from nvidia but that would not work.
 
So then I used PPA in terminal and got the new drivers but then my **nvidia x server settings** claimed that I needed to configure my settings and restart. I followed many guides for this part of the process to no avail. 
 
I have searched the net for many hours without coming up with a solid solution. Everyone that has this problem reaches this dead end and ends up choosing to switch back to  nouveau. I would really like for the drivers to work so I can use dual screen properly and my eyes don't burn out from 60hz !
 
If anyone has further information or would like me to run a command to get my settings please let me know. I know my newbie style post is not incredibly helpful so please tell me what you need. 
 
Thanks so much!

---

### Post by doobydave on 2012-05-18
Is your monitor driven correctly with the open-source driver? Can you select the appropriate resolutions and refresh rates?

---

### Post by scottsdale on 2012-05-18
[SIZE=3][FONT=Calibri]Hi doobydave. [/FONT][/SIZE]
[SIZE=3][FONT=Calibri]I have tried both nouveau & the recommended drivers. (although I have now removed nouveau from my machine). I am not worried about the removal because since its a fresh install I can reinstall ubuntu if something goes horribly wrong. Just trying to see if I can get the refresh rate and resolution sorted out for now.[/FONT][/SIZE]
[FONT=Calibri][SIZE=3][/SIZE][/FONT] 
[SIZE=3][FONT=Calibri]The appropriate refesh rates and resolutions do not appear for my display in system settings if I am understanding the second part of your question correctly.[/FONT][/SIZE]
 
I am at the same stage as this user [http://ubuntuforums.org/showthread.php?t=1980033](http://ubuntuforums.org/showthread.php?t=1980033) with the same problem and I have tried all of the remedies listed in this thread except installing the older version because It did not work for him. He finally gave up.
 
if there is anything that is not mentioned in this thread or the one that I have posted that I should be trying please let me know.

---

### Post by doobydave on 2012-05-18
Sorry, I guess I was asking the same question in two ways.

I'm struggling to generate a new xorg.conf. In order to run Xorg -configure, one needs to stop the GUI. Took me a while to realise it's called lightdm..
Trouble is, the machine hangs when stopping the desktop manager. Just like it does on logout. Just like it does if I try to switch to a terminal with the ctrl-alt-f1/6 combos.

Booting into recovery mode did the trick, but I get errors running Xorg -configure. I would post them only I didn't take a photo..

---

### Post by doobydave on 2012-05-18
```

Log of Xorg -configure 
Sat May 19 00:07:34 2012


X.Org X Server 1.11.3
Release Date: 2011-12-16
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.42-23-generic i686 Ubuntu
Current Operating System: Linux doobz-1204 3.2.0-24-generic-pae #37-Ubuntu SMP Wed Apr 25 10:47:59 UTC 2012 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-24-generic-pae root=UUID=e57566a6-35f9-48d4-854b-68e581f05406 ro recovery nomodeset
Build Date: 20 April 2012  05:12:21AM
xorg-server 2:1.11.4-0ubuntu10.1 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.24.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat May 19 00:07:34 2012
List of video drivers:
	ati
	sisusb
	openchrome
	s3
	mach64
	savage
	sis
	trident
	siliconmotion
	vmware
	mga
	intel
	neomagic
	geode
	qxl
	r128
	radeon
	cirrus
	ztv
	tdfx
	nouveau
	fbdev
	vesa
(++) Using config file: "/root/xorg.conf.new"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(EE) [drm] No DRICreatePCIBusID symbol
(EE) open /dev/fb0: No such file or directory
Number of created screens does not match number of detected devices.
  Configuration failed.
 ddxSigGiveUp: Closing log
Server terminated with error (2). Closing log file.

```

---

### Post by matt_symes on 2012-05-18
Hi

> VBE/DDC service about to be called
	Report DDC capabilities

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f15 bx=0x0 cx=0x0
	Function supported
	Call successful

	[B]Monitor and video card combination does not support DDC1 transfers
	Monitor and video card combination does not support DDC2 transfers[/B]
	0 seconds per 128 byte EDID block transfer
	Screen is not blanked during DDC transfer

Reading next EDID block

VBE/DDC service about to be called
	Read EDID

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
	Function supported
	Call failed

The EDID data should not be trusted as the VBE call failed
Error: output block unchanged
parse-edid: IO error reading EDID

You *do* have an edid problem. The EDID information logged in your Xorg.0.log is invalid. Because you cannot get DCC1/2 transfers from the monitor to your card, you are not getting the correct timings information.

> **doobydave said:**
> As for trying the proprietary drivers, is that not what Ubuntu is doing without the 'nomodeset' flag?

No. The nomodeset switch turns off kernel mode setting and switches resolution in user mode. Kernel/user mode setting can happen with both the open source and proprietary drivers.

> **doobydave said:**
> There appears to be a lot of EDID related problems surfacing recently - I imagine many people aren't sure why their machines don't work with recent linux distros. It's by no means limited to Ubuntu.

I am looking at trying to get the correct EDID from my windows install and creating a xorg.conf (or whatever needs to be done to get the nouveau driver to drive the display properly).

/shameless triple-posting bump

Try using Phoenix EDID Designer to get the EDID information under windows XP. 

[http://downloads.yahoo.com/software/windows-web-tools-phoenix-edid-designer-s21726](http://downloads.yahoo.com/software/windows-web-tools-phoenix-edid-designer-s21726)

I suspect you will have the same problem in windows that you are having in Linux though.

> **scottsdale said:**
> I have the same set up here. Right down to the monitor type and using a converter connector. Only difference is I have an 8600GT. Runing fresh install 12.04 LTS.
 
I downloaded my driver from nvidia but that would not work.
 
So then I used PPA in terminal and got the new drivers but then my **nvidia x server settings** claimed that I needed to configure my settings and restart. I followed many guides for this part of the process to no avail. 
 
I have searched the net for many hours without coming up with a solid solution. Everyone that has this problem reaches this dead end and ends up choosing to switch back to  nouveau. I would really like for the drivers to work so I can use dual screen properly and my eyes don't burn out from 60hz !
 
If anyone has further information or would like me to run a command to get my settings please let me know. I know my newbie style post is not incredibly helpful so please tell me what you need. 
 
Thanks so much!

The nVidia drivers will not make a difference here. The EDID information is the problem.

> **doobydave said:**
> Sorry, I guess I was asking the same question in two ways.

I'm struggling to generate a new xorg.conf. In order to run Xorg -configure, one needs to stop the GUI. Took me a while to realise it's called lightdm..
Trouble is, the machine hangs when stopping the desktop manager. Just like it does on logout. Just like it does if I try to switch to a terminal with the ctrl-alt-f1/6 combos.

Booting into recovery mode did the trick, but I get errors running Xorg -configure. I would post them only I didn't take a photo..

You can manually create you own xorg.conf file. Try to get the edid information first from Windows then we can look at creating a xorg.conf file for you.

Kind regards

---

### Post by doobydave on 2012-05-18
Thanks for popping back.

I have obtained the edid info from windows using the phoenix app. It gave a warning about some version incompatibility, and that the edid info would/could be altered slightly in the translation. I have exported this as a *.raw file.

I called it a night though after Xorg -configure refused to play.
:)

---

### Post by doobydave on 2012-05-19
Right. I'm back, and I'm not giving up until -

a) I have a functional workaround
b) This issue is acknowledged as a bug, and someone in the know is attempting to fix it.

Regarding b), is there now a reason why I cannot reference the buggy EDID software in my bug report on launchpad?

---

### Post by matt_symes on 2012-05-19
Hi

Have you considered using a specific mode line in your xorg.conf file ?

From here 

[http://tweakers.mobi/nieuws/7516](http://tweakers.mobi/nieuws/7516)

it looks like your monitor can handle "1600X1280 at 85Hz"

```
matthew@matthew-Aspire-7540 ~ % cvt 1600 1280 85     
# 1600x1280 84.99 Hz (CVT 2.05M4) hsync: 114.39 kHz; pclk: 250.75 MHz
Modeline "1600x1280_85.00"  250.75  1600 1728 1896 2192  1280 1283 1290 1346 -hsync +vsync
matthew@matthew-Aspire-7540 ~ %
```

Kind regards

---

### Post by doobydave on 2012-05-19
That's strange. I've never seen that resolution before. I have just double checked the available resolutions in XP and the closest one is 1600x1200.

I need to look into (or be helped) creating an appropriate xorg.conf. I'm not sure what goes in which section or if it is even used anymore. It appears that the separate sections have been replace by individual files in xorg.conf.d.

And I'm unsure about drivers. Ultimately, I imagine I will want the proprietary nvidia driver, but I am loathe to install it just now and call it a solution. Ubuntu (and others) should be able to drive this hardware at basic setiings without proprietary drivers.

Is Ubuntu trying first with nouveau and, when failing, attempting to use VESA?


Up until recently, I have been using Sabayon with the proprietary nvidia drivers, but that has become unusable. I was thinking of copying the xorg.conf from that install, but perhaps thats not such a good idea.

Tbh, I'm a little out of my depth here. My instinct is that someone cleverer than me needs to work out why windows can get the EDID, yet the software that all major linux distos have adopted to do the job, can't.

---

### Post by doobydave on 2012-05-20
I cannot believe how many people experiencing similar problems over many distros. Most are 'solved' by using different hardware, giving up, or in the case of the proprietary driver you can force an EDID obtained elsewhere. Maybe some put up with vesa, no KMS and a tweeked xorg.conf.

Try googling
' EDID "no screens found" ' or 
' "xorg -configure" "DRICreatePCIBusID" '

Single quotes mine, double quotes google's.

---

### Post by matt_symes on 2012-05-22
Hi

> **doobydave said:**
> That's strange. I've never seen that resolution before. I have just double checked the available resolutions in XP and the closest one is 1600x1200.

Yes it is an unusual resolution. I only mentioned it because it was in the link. Your monitor - video card combination is not one i have used.

> 
I need to look into (or be helped) creating an appropriate xorg.conf. I'm not sure what goes in which section or if it is even used anymore. It appears that the separate sections have been replace by individual files in xorg.conf.d.

Nowadays, kernel mode setting is used to set the video resolution from the EDID information retrieved from the monitor. 

This helps, amongst other things, to reduce flickering when changing resolution and allows a framebuffer to run at native resolution before X starts.

This is all fine and dandy as long the EDID information is retrieved from the monitor.

If it is not, you run into the problems you have.

If you create a xorg.conf file it should override these settings, allowing you to specify you own resolutions, mode lines and timings.

You can do this for propriety and open source drivers. 

> 
And I'm unsure about drivers. Ultimately, I imagine I will want the proprietary nvidia driver, but I am loathe to install it just now and call it a solution. Ubuntu (and others) should be able to drive this hardware at basic setiings without proprietary drivers.

I am not sure about this but it may be due to the DVI to VGA connector you are using. That would need research to confirm or deny this though.

> 
Is Ubuntu trying first with nouveau and, when failing, attempting to use VESA?


> Up until recently, I have been using Sabayon with the proprietary nvidia drivers, but that has become unusable. I was thinking of copying the xorg.conf from that install, but perhaps thats not such a good idea.

Tbh, I'm a little out of my depth here. My instinct is that someone cleverer than me needs to work out why windows can get the EDID, yet the software that all major linux distos have adopted to do the job, can't.

The xorg.conf file should be standard. Try copying across. You can always boot into recovery mode and delete it. When you reboot you should be back to where you are now.

There is something i want to check though. Can you post the output of 

```
lspci -nnk | grep -iA3 vga
```

Kind regards

---

### Post by doobydave on 2012-05-23
Output of lspci -nnk | grep -iA3 vga (standard boot)
```

01:00.0 VGA compatible controller [0300]: NVIDIA Corporation G80 [GeForce 8800 GTX] [10de:0191] (rev a2)
	Subsystem: eVga.com. Corp. Device [3842:c831]
	Kernel driver in use: nouveau
	Kernel modules: nouveau, nvidiafb
03:00.0 IDE interface [0101]: JMicron Technology Corp. JMB368 IDE controller [197b:2368]

```

and booted with nomodeset
```

01:00.0 VGA compatible controller [0300]: NVIDIA Corporation G80 [GeForce 8800 GTX] [10de:0191] (rev a2)
	Subsystem: eVga.com. Corp. Device [3842:c831]
	Kernel modules: nouveau, nvidiafb
03:00.0 IDE interface [0101]: JMicron Technology Corp. JMB368 IDE controller [197b:2368]
	Subsystem: Giga-byte Technology Device [1458:b000]

```

Dunno where the extra line has appeared from..


I forgot to mention I have a laptop with a VGA port on it, I could use that to interrogate the monitor without the DVI>VGA adapter (though thinking back to my first ubuntu experience, the monitor was connected directly to an ATI graphics card, and I remember there being similar issues).

---

### Post by matt_symes on 2012-05-24
Hi

> I forgot to mention I have a laptop with a VGA port on it, I could use that to interrogate the monitor without the DVI>VGA adapter (though thinking back to my first ubuntu experience, the monitor was connected directly to an ATI graphics card, and I remember there being similar issues).

Do that and try to pull of the edid information over VGA using if possible. It will implicate/eliminate the dvi->vga connector.

```
sudo get-edit > monitor.edid
```

If you can get the edid information via the vga connector, we may be able to use that on your other machine. 

Transfer it to your other machine and then we can try to create an xorg file.

Post back any error messages from the laptop machine.

Kind regards

---

### Post by doobydave on 2012-05-24
Good news - I'm posting from my laptop booted with the 1204 live cd, with the CRT plugged into the VGA - with two desktops and a visible terminal
Bad news - The unity task bar (on the left) utterly failed to materialise making posting this message harder than it ought. After remembering the keyboard shortcut to bring up the terminal in X, firefox fires up, albeit with errors.
```

ubuntu@ubuntu:~$ firefox
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 30
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 30
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 55
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 56
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 59
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 58
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 30

```

Xorg.0.log
```

[   112.395] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[   112.395] X Protocol Version 11, Revision 0
[   112.395] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[   112.395] Current Operating System: Linux ubuntu 3.2.0-23-generic-pae #36-Ubuntu SMP Tue Apr 10 22:19:09 UTC 2012 i686
[   112.395] Kernel command line: file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --
[   112.395] Build Date: 04 April 2012  11:58:38PM
[   112.395] xorg-server 2:1.11.4-0ubuntu10 (For technical support please see http://www.ubuntu.com/support) 
[   112.395] Current version of pixman: 0.24.4
[   112.395] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[   112.395] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   112.395] (==) Log file: "/var/log/Xorg.0.log", Time: Thu May 24 13:42:30 2012
[   112.414] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   112.793] (==) No Layout section.  Using the first Screen section.
[   112.793] (==) No screen section available. Using defaults.
[   112.793] (**) |-->Screen "Default Screen Section" (0)
[   112.793] (**) |   |-->Monitor "<default monitor>"
[   112.793] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[   112.793] (==) Automatically adding devices
[   112.793] (==) Automatically enabling devices
[   113.667] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   113.667] 	Entry deleted from font path.
[   113.667] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   113.667] 	Entry deleted from font path.
[   113.667] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   113.667] 	Entry deleted from font path.
[   114.338] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   114.338] 	Entry deleted from font path.
[   114.338] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   114.338] 	Entry deleted from font path.
[   114.339] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[   114.339] 	Entry deleted from font path.
[   114.339] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[   114.339] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   114.339] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[   114.339] (II) Loader magic: 0xb77215a0
[   114.339] (II) Module ABI versions:
[   114.339] 	X.Org ANSI C Emulation: 0.4
[   114.339] 	X.Org Video Driver: 11.0
[   114.339] 	X.Org XInput driver : 16.0
[   114.339] 	X.Org Server Extension : 6.0
[   114.340] (--) PCI:*(0:1:0:0) 10de:0398:1025:0090 rev 161, Mem @ 0xd1000000/16777216, 0xc0000000/268435456, 0xd0000000/16777216, I/O @ 0x00002000/128
[   114.340] (II) Open ACPI successful (/var/run/acpid.socket)
[   114.340] (II) LoadModule: "extmod"
[   114.343] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   114.488] (II) Module extmod: vendor="X.Org Foundation"
[   114.488] 	compiled for 1.11.3, module version = 1.0.0
[   114.488] 	Module class: X.Org Server Extension
[   114.488] 	ABI class: X.Org Server Extension, version 6.0
[   114.488] (II) Loading extension MIT-SCREEN-SAVER
[   114.488] (II) Loading extension XFree86-VidModeExtension
[   114.488] (II) Loading extension XFree86-DGA
[   114.488] (II) Loading extension DPMS
[   114.488] (II) Loading extension XVideo
[   114.488] (II) Loading extension XVideo-MotionCompensation
[   114.488] (II) Loading extension X-Resource
[   114.488] (II) LoadModule: "dbe"
[   114.489] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   114.548] (II) Module dbe: vendor="X.Org Foundation"
[   114.548] 	compiled for 1.11.3, module version = 1.0.0
[   114.548] 	Module class: X.Org Server Extension
[   114.548] 	ABI class: X.Org Server Extension, version 6.0
[   114.548] (II) Loading extension DOUBLE-BUFFER
[   114.548] (II) LoadModule: "glx"
[   114.549] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   114.709] (II) Module glx: vendor="X.Org Foundation"
[   114.709] 	compiled for 1.11.3, module version = 1.0.0
[   114.709] 	ABI class: X.Org Server Extension, version 6.0
[   114.711] (==) AIGLX enabled
[   114.711] (II) Loading extension GLX
[   114.711] (II) LoadModule: "record"
[   114.711] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   114.718] (II) Module record: vendor="X.Org Foundation"
[   114.718] 	compiled for 1.11.3, module version = 1.13.0
[   114.718] 	Module class: X.Org Server Extension
[   114.718] 	ABI class: X.Org Server Extension, version 6.0
[   114.718] (II) Loading extension RECORD
[   114.718] (II) LoadModule: "dri"
[   114.718] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   114.885] (II) Module dri: vendor="X.Org Foundation"
[   114.885] 	compiled for 1.11.3, module version = 1.0.0
[   114.885] 	ABI class: X.Org Server Extension, version 6.0
[   114.885] (II) Loading extension XFree86-DRI
[   114.885] (II) LoadModule: "dri2"
[   114.886] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   114.886] (II) Module dri2: vendor="X.Org Foundation"
[   114.886] 	compiled for 1.11.3, module version = 1.2.0
[   114.886] 	ABI class: X.Org Server Extension, version 6.0
[   114.886] (II) Loading extension DRI2
[   114.886] (==) Matched nvidia as autoconfigured driver 0
[   114.886] (==) Matched nouveau as autoconfigured driver 1
[   114.886] (==) Matched nv as autoconfigured driver 2
[   114.886] (==) Matched vesa as autoconfigured driver 3
[   114.886] (==) Matched fbdev as autoconfigured driver 4
[   114.886] (==) Assigned the driver to the xf86ConfigLayout
[   114.886] (II) LoadModule: "nvidia"
[   114.887] (WW) Warning, couldn't open module nvidia
[   114.887] (II) UnloadModule: "nvidia"
[   114.887] (II) Unloading nvidia
[   114.887] (EE) Failed to load module "nvidia" (module does not exist, 0)
[   114.887] (II) LoadModule: "nouveau"
[   114.887] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[   115.224] (II) Module nouveau: vendor="X.Org Foundation"
[   115.224] 	compiled for 1.11.3, module version = 0.0.16
[   115.224] 	Module class: X.Org Video Driver
[   115.224] 	ABI class: X.Org Video Driver, version 11.0
[   115.224] (II) LoadModule: "nv"
[   115.226] (WW) Warning, couldn't open module nv
[   115.226] (II) UnloadModule: "nv"
[   115.226] (II) Unloading nv
[   115.226] (EE) Failed to load module "nv" (module does not exist, 0)
[   115.226] (II) LoadModule: "vesa"
[   115.226] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   115.228] (II) Module vesa: vendor="X.Org Foundation"
[   115.228] 	compiled for 1.11.3, module version = 2.3.0
[   115.228] 	Module class: X.Org Video Driver
[   115.228] 	ABI class: X.Org Video Driver, version 11.0
[   115.228] (II) LoadModule: "fbdev"
[   115.228] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   115.232] (II) Module fbdev: vendor="X.Org Foundation"
[   115.232] 	compiled for 1.11.3, module version = 0.4.2
[   115.232] 	ABI class: X.Org Video Driver, version 11.0
[   115.232] (==) Matched nvidia as autoconfigured driver 0
[   115.232] (==) Matched nouveau as autoconfigured driver 1
[   115.233] (==) Matched nv as autoconfigured driver 2
[   115.233] (==) Matched vesa as autoconfigured driver 3
[   115.233] (==) Matched fbdev as autoconfigured driver 4
[   115.233] (==) Assigned the driver to the xf86ConfigLayout
[   115.233] (II) LoadModule: "nvidia"
[   115.233] (WW) Warning, couldn't open module nvidia
[   115.233] (II) UnloadModule: "nvidia"
[   115.233] (II) Unloading nvidia
[   115.233] (EE) Failed to load module "nvidia" (module does not exist, 0)
[   115.233] (II) LoadModule: "nouveau"
[   115.234] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[   115.234] (II) Module nouveau: vendor="X.Org Foundation"
[   115.234] 	compiled for 1.11.3, module version = 0.0.16
[   115.234] 	Module class: X.Org Video Driver
[   115.234] 	ABI class: X.Org Video Driver, version 11.0
[   115.234] (II) UnloadModule: "nouveau"
[   115.234] (II) Unloading nouveau
[   115.234] (II) Failed to load module "nouveau" (already loaded, 0)
[   115.234] (II) LoadModule: "nv"
[   115.234] (WW) Warning, couldn't open module nv
[   115.234] (II) UnloadModule: "nv"
[   115.234] (II) Unloading nv
[   115.235] (EE) Failed to load module "nv" (module does not exist, 0)
[   115.235] (II) LoadModule: "vesa"
[   115.235] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   115.235] (II) Module vesa: vendor="X.Org Foundation"
[   115.235] 	compiled for 1.11.3, module version = 2.3.0
[   115.235] 	Module class: X.Org Video Driver
[   115.235] 	ABI class: X.Org Video Driver, version 11.0
[   115.235] (II) UnloadModule: "vesa"
[   115.235] (II) Unloading vesa
[   115.235] (II) Failed to load module "vesa" (already loaded, 0)
[   115.235] (II) LoadModule: "fbdev"
[   115.235] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   115.235] (II) Module fbdev: vendor="X.Org Foundation"
[   115.235] 	compiled for 1.11.3, module version = 0.4.2
[   115.235] 	ABI class: X.Org Video Driver, version 11.0
[   115.235] (II) UnloadModule: "fbdev"
[   115.235] (II) Unloading fbdev
[   115.235] (II) Failed to load module "fbdev" (already loaded, 0)
[   115.235] (II) NOUVEAU driver Date:   Wed Nov 30 18:56:54 2011 +0100
[   115.235] (II) NOUVEAU driver for NVIDIA chipset families :
[   115.235] 	RIVA TNT        (NV04)
[   115.235] 	RIVA TNT2       (NV05)
[   115.235] 	GeForce 256     (NV10)
[   115.235] 	GeForce 2       (NV11, NV15)
[   115.235] 	GeForce 4MX     (NV17, NV18)
[   115.235] 	GeForce 3       (NV20)
[   115.235] 	GeForce 4Ti     (NV25, NV28)
[   115.235] 	GeForce FX      (NV3x)
[   115.235] 	GeForce 6       (NV4x)
[   115.235] 	GeForce 7       (G7x)
[   115.235] 	GeForce 8       (G8x)
[   115.235] 	GeForce GTX 200 (NVA0)
[   115.235] 	GeForce GTX 400 (NVC0)
[   115.235] (II) VESA: driver for VESA chipsets: vesa
[   115.235] (II) FBDEV: driver for framebuffer: fbdev
[   115.235] (++) using VT number 7

[   115.236] drmOpenDevice: node name is /dev/dri/card0
[   115.236] drmOpenDevice: open result is 8, (OK)
[   115.236] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[   115.236] drmOpenDevice: node name is /dev/dri/card0
[   115.236] drmOpenDevice: open result is 8, (OK)
[   115.236] drmOpenByBusid: drmOpenMinor returns 8
[   115.236] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[   115.236] (II) [drm] nouveau interface version: 0.0.16
[   115.236] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[   115.236] (WW) Falling back to old probe method for vesa
[   115.236] (WW) Falling back to old probe method for fbdev
[   115.236] (II) Loading sub module "fbdevhw"
[   115.236] (II) LoadModule: "fbdevhw"
[   115.236] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   115.462] (II) Module fbdevhw: vendor="X.Org Foundation"
[   115.462] 	compiled for 1.11.3, module version = 0.0.2
[   115.462] 	ABI class: X.Org Video Driver, version 11.0
[   115.463] (II) Loading sub module "dri"
[   115.463] (II) LoadModule: "dri"
[   115.463] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   115.463] (II) Module dri: vendor="X.Org Foundation"
[   115.463] 	compiled for 1.11.3, module version = 1.0.0
[   115.463] 	ABI class: X.Org Server Extension, version 6.0
[   115.463] (II) NOUVEAU(0): Loaded DRI module
[   115.463] drmOpenDevice: node name is /dev/dri/card0
[   115.463] drmOpenDevice: open result is 9, (OK)
[   115.463] drmOpenDevice: node name is /dev/dri/card0
[   115.463] drmOpenDevice: open result is 9, (OK)
[   115.463] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[   115.463] drmOpenDevice: node name is /dev/dri/card0
[   115.463] drmOpenDevice: open result is 9, (OK)
[   115.463] drmOpenByBusid: drmOpenMinor returns 9
[   115.463] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[   115.463] (II) [drm] DRM interface version 1.4
[   115.463] (II) [drm] DRM open master succeeded.
[   115.463] (--) NOUVEAU(0): Chipset: "NVIDIA NV4b"
[   115.463] (II) NOUVEAU(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[   115.463] (==) NOUVEAU(0): Depth 24, (--) framebuffer bpp 32
[   115.463] (==) NOUVEAU(0): RGB weight 888
[   115.463] (==) NOUVEAU(0): Default visual is TrueColor
[   115.463] (==) NOUVEAU(0): Using HW cursor
[   115.463] (==) NOUVEAU(0): GLX sync to VBlank disabled.
[   115.463] (==) NOUVEAU(0): Page flipping enabled
[   115.708] (II) NOUVEAU(0): Output VGA-1 has no monitor section
[   115.840] (II) NOUVEAU(0): Output LVDS-1 has no monitor section
[   115.896] (II) NOUVEAU(0): Output TV-1 has no monitor section
[   115.906] (II) NOUVEAU(0): Output DVI-D-1 has no monitor section
[   116.190] (II) NOUVEAU(0): EDID for output VGA-1
[   116.190] (II) NOUVEAU(0): Manufacturer: IVM  Model: 2140  Serial#: 10037195
[   116.190] (II) NOUVEAU(0): Year: 2000  Week: 5
[   116.190] (II) NOUVEAU(0): EDID Version: 1.1
[   116.190] (II) NOUVEAU(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[   116.190] (II) NOUVEAU(0): Sync:  Separate  Composite  SyncOnGreen
[   116.190] (II) NOUVEAU(0): Max Image Size [cm]: horiz.: 40  vert.: 30
[   116.190] (II) NOUVEAU(0): Gamma: 2.54
[   116.190] (II) NOUVEAU(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[   116.190] (II) NOUVEAU(0): redX: 0.625 redY: 0.340   greenX: 0.292 greenY: 0.604
[   116.190] (II) NOUVEAU(0): blueX: 0.150 blueY: 0.070   whiteX: 0.283 whiteY: 0.297
[   116.190] (II) NOUVEAU(0): Supported established timings:
[   116.190] (II) NOUVEAU(0): 640x480@60Hz
[   116.190] (II) NOUVEAU(0): 640x480@67Hz
[   116.190] (II) NOUVEAU(0): 640x480@72Hz
[   116.190] (II) NOUVEAU(0): 640x480@75Hz
[   116.190] (II) NOUVEAU(0): 800x600@56Hz
[   116.190] (II) NOUVEAU(0): 800x600@60Hz
[   116.190] (II) NOUVEAU(0): 800x600@72Hz
[   116.190] (II) NOUVEAU(0): 800x600@75Hz
[   116.190] (II) NOUVEAU(0): 832x624@75Hz
[   116.190] (II) NOUVEAU(0): 1024x768@60Hz
[   116.190] (II) NOUVEAU(0): 1024x768@70Hz
[   116.190] (II) NOUVEAU(0): 1024x768@75Hz
[   116.190] (II) NOUVEAU(0): 1280x1024@75Hz
[   116.190] (II) NOUVEAU(0): 1152x864@75Hz
[   116.190] (II) NOUVEAU(0): Manufacturer's mask: 0
[   116.190] (II) NOUVEAU(0): Supported standard timings:
[   116.190] (II) NOUVEAU(0): #0: hsize: 1600  vsize 1200  refresh: 97  vid: 26025
[   116.190] (II) NOUVEAU(0): #1: hsize: 1792  vsize 1344  refresh: 75  vid: 20417
[   116.190] (II) NOUVEAU(0): #2: hsize: 1856  vsize 1392  refresh: 75  vid: 20425
[   116.190] (II) NOUVEAU(0): #3: hsize: 2048  vsize 1536  refresh: 80  vid: 21729
[   116.190] (II) NOUVEAU(0):  
[   116.190] (II) NOUVEAU(0):  
[   116.190] (II) NOUVEAU(0):  
[   116.190] (II) NOUVEAU(0):  
[   116.190] (II) NOUVEAU(0): EDID (in hex):
[   116.190] (II) NOUVEAU(0): 	00ffffffffffff0026cd4021cb279900
[   116.190] (II) NOUVEAU(0): 	050a01010e281e9ae80e88a0574a9a26
[   116.190] (II) NOUVEAU(0): 	12484c3fef80a965c14fc94fe1540101
[   116.190] (II) NOUVEAU(0): 	010101010101000000fe000000000000
[   116.190] (II) NOUVEAU(0): 	0000000000000000000000fe00000000
[   116.190] (II) NOUVEAU(0): 	00000000000000000000000000fe0000
[   116.190] (II) NOUVEAU(0): 	000000000000000000000000000000fe
[   116.190] (II) NOUVEAU(0): 	000000000000000000000000000000ea
[   116.190] (II) NOUVEAU(0): EDID vendor "IVM", prod id 8512
[   116.190] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   116.190] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   116.190] (II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   116.190] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   116.190] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[   116.190] (II) NOUVEAU(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[   116.190] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   116.190] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   116.190] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   116.190] (II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   116.190] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   116.190] (II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   116.190] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   116.190] (II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   116.190] (II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   116.190] (II) NOUVEAU(0): Modeline "1792x1344"x0.0  261.00  1792 1888 2104 2456  1344 1345 1348 1417 -hsync +vsync (106.3 kHz)
[   116.190] (II) NOUVEAU(0): Modeline "1856x1392"x0.0  288.00  1856 1984 2208 2560  1392 1393 1396 1500 -hsync +vsync (112.5 kHz)
[   116.190] (II) NOUVEAU(0): Printing probed modes for output VGA-1
[   116.190] (II) NOUVEAU(0): Modeline "1856x1392"x75.0  288.00  1856 1984 2208 2560  1392 1395 1399 1500 -hsync +vsync (112.5 kHz)
[   116.190] (II) NOUVEAU(0): Modeline "1792x1344"x75.0  261.00  1792 1888 2104 2456  1344 1345 1348 1417 -hsync +vsync (106.3 kHz)
[   116.190] (II) NOUVEAU(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   116.190] (II) NOUVEAU(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   116.190] (II) NOUVEAU(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
[   116.190] (II) NOUVEAU(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   116.191] (II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   116.191] (II) NOUVEAU(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   116.191] (II) NOUVEAU(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   116.191] (II) NOUVEAU(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   116.191] (II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   116.191] (II) NOUVEAU(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   116.191] (II) NOUVEAU(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
[   116.191] (II) NOUVEAU(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   116.191] (II) NOUVEAU(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[   116.191] (II) NOUVEAU(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   116.324] (II) NOUVEAU(0): EDID for output LVDS-1
[   116.324] (II) NOUVEAU(0): Manufacturer: CMO  Model: 1554  Serial#: 0
[   116.324] (II) NOUVEAU(0): Year: 2007  Week: 40
[   116.324] (II) NOUVEAU(0): EDID Version: 1.3
[   116.324] (II) NOUVEAU(0): Digital Display Input
[   116.324] (II) NOUVEAU(0): Max Image Size [cm]: horiz.: 33  vert.: 21
[   116.324] (II) NOUVEAU(0): Gamma: 2.20
[   116.324] (II) NOUVEAU(0): No DPMS capabilities specified
[   116.324] (II) NOUVEAU(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[   116.324] (II) NOUVEAU(0): First detailed timing is preferred mode
[   116.324] (II) NOUVEAU(0): redX: 0.602 redY: 0.340   greenX: 0.306 greenY: 0.530
[   116.324] (II) NOUVEAU(0): blueX: 0.151 blueY: 0.120   whiteX: 0.313 whiteY: 0.329
[   116.324] (II) NOUVEAU(0): Manufacturer's mask: 0
[   116.324] (II) NOUVEAU(0): Supported detailed timing:
[   116.324] (II) NOUVEAU(0): clock: 71.0 MHz   Image Size:  331 x 207 mm
[   116.324] (II) NOUVEAU(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
[   116.324] (II) NOUVEAU(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
[   116.324] (II) NOUVEAU(0):  N154I3-L03
[   116.324] (II) NOUVEAU(0):  CMO
[   116.324] (II) NOUVEAU(0):  N154I3-L03
[   116.324] (II) NOUVEAU(0): EDID (in hex):
[   116.324] (II) NOUVEAU(0): 	00ffffffffffff000daf541500000000
[   116.324] (II) NOUVEAU(0): 	28110103802115780a07f59a574e8726
[   116.324] (II) NOUVEAU(0): 	1e505400000001010101010101010101
[   116.324] (II) NOUVEAU(0): 	010101010101bc1b00a0502017303020
[   116.324] (II) NOUVEAU(0): 	36004bcf10000018000000fe004e3135
[   116.324] (II) NOUVEAU(0): 	3449332d4c30330a2020000000fe0043
[   116.324] (II) NOUVEAU(0): 	4d4f0a202020202020202020000000fe
[   116.324] (II) NOUVEAU(0): 	004e31353449332d4c30330a202000a5
[   116.324] (II) NOUVEAU(0): Printing probed modes for output LVDS-1
[   116.324] (II) NOUVEAU(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[   116.324] (II) NOUVEAU(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
[   116.324] (II) NOUVEAU(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[   116.324] (II) NOUVEAU(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[   116.324] (II) NOUVEAU(0): Modeline "720x400"x59.6   22.25  720 744 808 896  400 403 413 417 -hsync +vsync (24.8 kHz)
[   116.324] (II) NOUVEAU(0): Modeline "640x400"x60.0   20.00  640 664 720 800  400 403 409 417 -hsync +vsync (25.0 kHz)
[   116.324] (II) NOUVEAU(0): Modeline "640x350"x59.8   17.50  640 664 720 800  350 353 363 366 -hsync +vsync (21.9 kHz)
[   116.380] (II) NOUVEAU(0): EDID for output TV-1
[   116.397] (II) NOUVEAU(0): EDID for output DVI-D-1
[   116.397] (II) NOUVEAU(0): Output VGA-1 connected
[   116.397] (II) NOUVEAU(0): Output LVDS-1 connected
[   116.397] (II) NOUVEAU(0): Output TV-1 disconnected
[   116.397] (II) NOUVEAU(0): Output DVI-D-1 disconnected
[   116.397] (II) NOUVEAU(0): Using fuzzy aspect match for initial modes
[   116.397] (II) NOUVEAU(0): Output VGA-1 using initial mode 1024x768
[   116.397] (II) NOUVEAU(0): Output LVDS-1 using initial mode 1024x768
[   116.397] (II) NOUVEAU(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[   116.397] (--) NOUVEAU(0): Virtual size is 1024x768 (pitch 0)
[   116.397] (**) NOUVEAU(0):  Driver mode "1024x768": 63.5 MHz (scaled from 0.0 MHz), 47.8 kHz, 59.9 Hz
[   116.397] (II) NOUVEAU(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
[   116.397] (**) NOUVEAU(0):  Driver mode "800x600": 38.2 MHz (scaled from 0.0 MHz), 37.4 kHz, 59.9 Hz
[   116.397] (II) NOUVEAU(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[   116.397] (**) NOUVEAU(0):  Driver mode "640x480": 23.8 MHz (scaled from 0.0 MHz), 29.7 kHz, 59.4 Hz
[   116.397] (II) NOUVEAU(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[   116.397] (**) NOUVEAU(0):  Driver mode "720x400": 22.2 MHz (scaled from 0.0 MHz), 24.8 kHz, 59.6 Hz
[   116.397] (II) NOUVEAU(0): Modeline "720x400"x59.6   22.25  720 744 808 896  400 403 413 417 -hsync +vsync (24.8 kHz)
[   116.397] (**) NOUVEAU(0):  Driver mode "640x400": 20.0 MHz (scaled from 0.0 MHz), 25.0 kHz, 60.0 Hz
[   116.397] (II) NOUVEAU(0): Modeline "640x400"x60.0   20.00  640 664 720 800  400 403 409 417 -hsync +vsync (25.0 kHz)
[   116.397] (**) NOUVEAU(0):  Driver mode "640x350": 17.5 MHz (scaled from 0.0 MHz), 21.9 kHz, 59.8 Hz
[   116.397] (II) NOUVEAU(0): Modeline "640x350"x59.8   17.50  640 664 720 800  350 353 363 366 -hsync +vsync (21.9 kHz)
[   116.397] (**) NOUVEAU(0):  Driver mode "1280x800": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 59.9 Hz
[   116.397] (II) NOUVEAU(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[   116.397] (**) NOUVEAU(0): Display dimensions: (400, 300) mm
[   116.397] (**) NOUVEAU(0): DPI set to (65, 65)
[   116.397] (II) Loading sub module "fb"
[   116.397] (II) LoadModule: "fb"
[   116.398] (II) Loading /usr/lib/xorg/modules/libfb.so
[   116.404] (II) Module fb: vendor="X.Org Foundation"
[   116.404] 	compiled for 1.11.3, module version = 1.0.0
[   116.404] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   116.404] (II) Loading sub module "exa"
[   116.404] (II) LoadModule: "exa"
[   116.404] (II) Loading /usr/lib/xorg/modules/libexa.so
[   116.406] (II) Module exa: vendor="X.Org Foundation"
[   116.406] 	compiled for 1.11.3, module version = 2.5.0
[   116.406] 	ABI class: X.Org Video Driver, version 11.0
[   116.406] (II) Loading sub module "shadowfb"
[   116.406] (II) LoadModule: "shadowfb"
[   116.406] (II) Loading /usr/lib/xorg/modules/libshadowfb.so
[   116.412] (II) Module shadowfb: vendor="X.Org Foundation"
[   116.412] 	compiled for 1.11.3, module version = 1.0.0
[   116.412] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   116.412] (II) UnloadModule: "vesa"
[   116.412] (II) Unloading vesa
[   116.412] (II) UnloadModule: "fbdev"
[   116.412] (II) Unloading fbdev
[   116.412] (II) UnloadModule: "fbdevhw"
[   116.412] (II) Unloading fbdevhw
[   116.412] (--) Depth 24 pixmap format is 32 bpp
[   116.415] (II) NOUVEAU(0): Opened GPU channel 1
[   116.415] (II) NOUVEAU(0): [DRI2] Setup complete
[   116.415] (II) NOUVEAU(0): [DRI2]   DRI driver: nouveau
[   116.415] (II) NOUVEAU(0): [DRI2]   VDPAU driver: nouveau
[   116.424] (II) NOUVEAU(0): GART: 512MiB available
[   116.446] (II) NOUVEAU(0): GART: Allocated 16MiB as a scratch buffer
[   116.464] (II) EXA(0): Driver allocated offscreen pixmaps
[   116.464] (II) EXA(0): Driver registered support for the following operations:
[   116.464] (II)         Solid
[   116.464] (II)         Copy
[   116.464] (II)         Composite (RENDER acceleration)
[   116.464] (II)         UploadToScreen
[   116.464] (II)         DownloadFromScreen
[   116.464] (==) NOUVEAU(0): Backing store disabled
[   116.464] (==) NOUVEAU(0): Silken mouse enabled
[   116.464] (II) NOUVEAU(0): [XvMC] Associated with NV40 texture adapter.
[   116.465] (II) NOUVEAU(0): [XvMC] Extension initialized.
[   116.465] (==) NOUVEAU(0): DPMS enabled
[   116.465] (II) NOUVEAU(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[   116.465] (--) RandR disabled
[   116.465] (II) Initializing built-in extension Generic Event Extension
[   116.465] (II) Initializing built-in extension SHAPE
[   116.465] (II) Initializing built-in extension MIT-SHM
[   116.465] (II) Initializing built-in extension XInputExtension
[   116.465] (II) Initializing built-in extension XTEST
[   116.465] (II) Initializing built-in extension BIG-REQUESTS
[   116.465] (II) Initializing built-in extension SYNC
[   116.465] (II) Initializing built-in extension XKEYBOARD
[   116.465] (II) Initializing built-in extension XC-MISC
[   116.465] (II) Initializing built-in extension SECURITY
[   116.465] (II) Initializing built-in extension XINERAMA
[   116.465] (II) Initializing built-in extension XFIXES
[   116.465] (II) Initializing built-in extension RENDER
[   116.465] (II) Initializing built-in extension RANDR
[   116.465] (II) Initializing built-in extension COMPOSITE
[   116.465] (II) Initializing built-in extension DAMAGE
[   122.075] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[   122.075] (II) AIGLX: enabled GLX_INTEL_swap_event
[   122.075] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[   122.075] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[   122.075] (II) AIGLX: Loaded and initialized nouveau
[   122.075] (II) GLX: Initialized DRI2 GL provider for screen 0
[   122.078] (II) NOUVEAU(0): NVEnterVT is called.
[   122.527] (II) NOUVEAU(0): Setting screen physical size to 270 x 203
[   122.527] resize called 1024 768
[   123.092] (II) XKB: generating xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   124.165] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[   124.165] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   124.165] (II) LoadModule: "evdev"
[   124.165] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   124.169] (II) Module evdev: vendor="X.Org Foundation"
[   124.169] 	compiled for 1.11.3, module version = 2.7.0
[   124.169] 	Module class: X.Org XInput Driver
[   124.169] 	ABI class: X.Org XInput driver, version 16.0
[   124.169] (II) Using input driver 'evdev' for 'Power Button'
[   124.169] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   124.169] (**) Power Button: always reports core events
[   124.169] (**) evdev: Power Button: Device: "/dev/input/event3"
[   124.169] (--) evdev: Power Button: Vendor 0 Product 0x1
[   124.169] (--) evdev: Power Button: Found keys
[   124.169] (II) evdev: Power Button: Configuring as keyboard
[   124.169] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[   124.169] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[   124.169] (**) Option "xkb_rules" "evdev"
[   124.169] (**) Option "xkb_model" "pc105"
[   124.169] (**) Option "xkb_layout" "us"
[   124.170] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[   124.170] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[   124.170] (II) Using input driver 'evdev' for 'Video Bus'
[   124.170] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   124.170] (**) Video Bus: always reports core events
[   124.170] (**) evdev: Video Bus: Device: "/dev/input/event5"
[   124.170] (--) evdev: Video Bus: Vendor 0 Product 0x6
[   124.170] (--) evdev: Video Bus: Found keys
[   124.170] (II) evdev: Video Bus: Configuring as keyboard
[   124.170] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input5/event5"
[   124.170] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[   124.170] (**) Option "xkb_rules" "evdev"
[   124.170] (**) Option "xkb_model" "pc105"
[   124.170] (**) Option "xkb_layout" "us"
[   124.171] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[   124.171] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   124.171] (II) Using input driver 'evdev' for 'Power Button'
[   124.171] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   124.171] (**) Power Button: always reports core events
[   124.171] (**) evdev: Power Button: Device: "/dev/input/event2"
[   124.171] (--) evdev: Power Button: Vendor 0 Product 0x1
[   124.171] (--) evdev: Power Button: Found keys
[   124.171] (II) evdev: Power Button: Configuring as keyboard
[   124.171] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2/event2"
[   124.171] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[   124.171] (**) Option "xkb_rules" "evdev"
[   124.171] (**) Option "xkb_model" "pc105"
[   124.171] (**) Option "xkb_layout" "us"
[   124.172] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[   124.172] (II) No input driver specified, ignoring this device.
[   124.172] (II) This device may have been added with another device file.
[   124.172] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[   124.172] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[   124.172] (II) Using input driver 'evdev' for 'Sleep Button'
[   124.172] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   124.172] (**) Sleep Button: always reports core events
[   124.172] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[   124.172] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[   124.172] (--) evdev: Sleep Button: Found keys
[   124.172] (II) evdev: Sleep Button: Configuring as keyboard
[   124.172] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1/event1"
[   124.172] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[   124.172] (**) Option "xkb_rules" "evdev"
[   124.172] (**) Option "xkb_model" "pc105"
[   124.172] (**) Option "xkb_layout" "us"
[   124.173] (II) config/udev: Adding input device ORTEK Smartpad Keyboard (/dev/input/event6)
[   124.173] (**) ORTEK Smartpad Keyboard: Applying InputClass "evdev keyboard catchall"
[   124.173] (II) Using input driver 'evdev' for 'ORTEK Smartpad Keyboard'
[   124.173] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   124.173] (**) ORTEK Smartpad Keyboard: always reports core events
[   124.173] (**) evdev: ORTEK Smartpad Keyboard: Device: "/dev/input/event6"
[   124.173] (--) evdev: ORTEK Smartpad Keyboard: Vendor 0x5a4 Product 0x2000
[   124.173] (--) evdev: ORTEK Smartpad Keyboard: Found keys
[   124.173] (II) evdev: ORTEK Smartpad Keyboard: Configuring as keyboard
[   124.173] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input6/event6"
[   124.173] (II) XINPUT: Adding extended input device "ORTEK Smartpad Keyboard" (type: KEYBOARD, id 10)
[   124.173] (**) Option "xkb_rules" "evdev"
[   124.173] (**) Option "xkb_model" "pc105"
[   124.173] (**) Option "xkb_layout" "us"
[   124.174] (II) config/udev: Adding input device ORTEK Smartpad Keyboard (/dev/input/event7)
[   124.174] (**) ORTEK Smartpad Keyboard: Applying InputClass "evdev pointer catchall"
[   124.174] (**) ORTEK Smartpad Keyboard: Applying InputClass "evdev keyboard catchall"
[   124.174] (II) Using input driver 'evdev' for 'ORTEK Smartpad Keyboard'
[   124.174] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   124.174] (**) ORTEK Smartpad Keyboard: always reports core events
[   124.174] (**) evdev: ORTEK Smartpad Keyboard: Device: "/dev/input/event7"
[   124.174] (--) evdev: ORTEK Smartpad Keyboard: Vendor 0x5a4 Product 0x2000
[   124.174] (--) evdev: ORTEK Smartpad Keyboard: Found 9 mouse buttons
[   124.174] (--) evdev: ORTEK Smartpad Keyboard: Found scroll wheel(s)
[   124.174] (--) evdev: ORTEK Smartpad Keyboard: Found relative axes
[   124.174] (--) evdev: ORTEK Smartpad Keyboard: Found x and y relative axes
[   124.174] (--) evdev: ORTEK Smartpad Keyboard: Found absolute axes
[   124.174] (II) evdev: ORTEK Smartpad Keyboard: Forcing absolute x/y axes to exist.
[   124.174] (--) evdev: ORTEK Smartpad Keyboard: Found keys
[   124.174] (II) evdev: ORTEK Smartpad Keyboard: Configuring as mouse
[   124.174] (II) evdev: ORTEK Smartpad Keyboard: Configuring as keyboard
[   124.174] (II) evdev: ORTEK Smartpad Keyboard: Adding scrollwheel support
[   124.174] (**) evdev: ORTEK Smartpad Keyboard: YAxisMapping: buttons 4 and 5
[   124.174] (**) evdev: ORTEK Smartpad Keyboard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   124.174] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.1/input/input7/event7"
[   124.174] (II) XINPUT: Adding extended input device "ORTEK Smartpad Keyboard" (type: KEYBOARD, id 11)
[   124.174] (**) Option "xkb_rules" "evdev"
[   124.174] (**) Option "xkb_model" "pc105"
[   124.174] (**) Option "xkb_layout" "us"
[   124.175] (II) evdev: ORTEK Smartpad Keyboard: initialized for relative axes.
[   124.175] (WW) evdev: ORTEK Smartpad Keyboard: ignoring absolute axes.
[   124.175] (**) ORTEK Smartpad Keyboard: (accel) keeping acceleration scheme 1
[   124.175] (**) ORTEK Smartpad Keyboard: (accel) acceleration profile 0
[   124.175] (**) ORTEK Smartpad Keyboard: (accel) acceleration factor: 2.000
[   124.175] (**) ORTEK Smartpad Keyboard: (accel) acceleration threshold: 4
[   124.175] (II) config/udev: Adding input device ORTEK Smartpad Keyboard (/dev/input/mouse0)
[   124.175] (II) No input driver specified, ignoring this device.
[   124.175] (II) This device may have been added with another device file.
[   124.176] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[   124.176] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[   124.176] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[   124.176] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   124.176] (**) AT Translated Set 2 keyboard: always reports core events
[   124.176] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[   124.176] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[   124.176] (--) evdev: AT Translated Set 2 keyboard: Found keys
[   124.176] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[   124.176] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[   124.176] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 12)
[   124.176] (**) Option "xkb_rules" "evdev"
[   124.176] (**) Option "xkb_model" "pc105"
[   124.176] (**) Option "xkb_layout" "us"
[   124.176] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event8)
[   124.176] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[   124.176] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[   124.176] (II) LoadModule: "synaptics"
[   124.177] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[   124.178] (II) Module synaptics: vendor="X.Org Foundation"
[   124.178] 	compiled for 1.11.3, module version = 1.5.99
[   124.178] 	Module class: X.Org XInput Driver
[   124.178] 	ABI class: X.Org XInput driver, version 16.0
[   124.178] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[   124.178] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[   124.178] (**) SynPS/2 Synaptics TouchPad: always reports core events
[   124.178] (**) Option "Device" "/dev/input/event8"
[   124.204] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[   124.204] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[   124.204] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[   124.204] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[   124.204] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple scroll-buttons
[   124.204] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[   124.204] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[   124.204] (**) SynPS/2 Synaptics TouchPad: always reports core events
[   124.248] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio4/input/input8/event8"
[   124.248] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 13)
[   124.248] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[   124.248] (**) synaptics: SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[   124.248] (**) synaptics: SynPS/2 Synaptics TouchPad: AccelFactor is now 0.040
[   124.248] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[   124.248] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[   124.248] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[   124.248] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[   124.248] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[   124.248] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[   124.248] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[   135.073] (II) NOUVEAU(0): EDID vendor "CMO", prod id 5460
[   135.073] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   135.073] (II) NOUVEAU(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[   163.122] (II) NOUVEAU(0): EDID vendor "CMO", prod id 5460
[   163.123] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   163.123] (II) NOUVEAU(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[   177.147] (II) NOUVEAU(0): EDID vendor "CMO", prod id 5460
[   177.147] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   177.147] (II) NOUVEAU(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[   181.647] (II) NOUVEAU(0): EDID vendor "CMO", prod id 5460
[   181.647] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   181.647] (II) NOUVEAU(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[   201.759] (II) XKB: generating xkmfile /var/lib/xkb/server-03AF3717FF3AB439A4BAABA686CCB40771CDF520.xkm
[   501.888] (II) AIGLX: Suspending AIGLX clients for VT switch
[   501.888] (II) NOUVEAU(0): NVLeaveVT is called.
[  1220.411] (II) Open ACPI successful (/var/run/acpid.socket)
[  1220.411] (II) AIGLX: Resuming AIGLX clients after VT switch
[  1220.411] (II) NOUVEAU(0): NVEnterVT is called.
[  1221.071] (II) NOUVEAU(0): EDID vendor "CMO", prod id 5460
[  1221.071] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[  1221.071] (II) NOUVEAU(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[  1221.145] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[  1235.960] (II) AIGLX: Suspending AIGLX clients for VT switch
[  1235.960] (II) NOUVEAU(0): NVLeaveVT is called.
[  1859.830] (II) Open ACPI successful (/var/run/acpid.socket)
[  1859.830] (II) AIGLX: Resuming AIGLX clients after VT switch
[  1859.830] (II) NOUVEAU(0): NVEnterVT is called.
[  1860.489] (II) NOUVEAU(0): EDID vendor "CMO", prod id 5460
[  1860.489] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[  1860.489] (II) NOUVEAU(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[  1860.565] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found

```

I wasn't able to run the command you asked. I wasn't able to install read-edid for some reason. I'm guessing this is why I got nothing. I did assume there was a typo (edit>edid), but it didn't work either way.
```

ubuntu@ubuntu:~$ sudo apt-get install read-edid
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package read-edid

```

---

### Post by doobydave on 2012-05-25
I have ubuntu 10.04 installed on the laptop and it appears read-edid is already intalled. Running the command you asked gave -
```

~$ sudo get-edid > monitor.edid
get-edid: get-edid version 2.0.0

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
	Function supported
	Call successful

	VBE version 300
	VBE string at 0x11100 "NVIDIA"

VBE/DDC service about to be called
	Report DDC capabilities

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f15 bx=0x0 cx=0x0
	Function supported
	Call successful

	Monitor and video card combination does not support DDC1 transfers
	Monitor and video card combination supports DDC2 transfers
	0 seconds per 128 byte EDID block transfer
	Screen is not blanked during DDC transfer

Reading next EDID block

VBE/DDC service about to be called
	Read EDID

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
	Function supported
	Call successful

```

---

### Post by matt_symes on 2012-05-25
Hi

Dave. Have a look in the file monitor.edid on your laptop.

It should contain some unreadable characters.

Check this out from my laptop.

 ```
% sudo get-edid > monitor.edid
[sudo] password for matthew: 
get-edid: get-edid version 2.0.0

        Performing real mode VBE call
        Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
        Function supported
        Call successful

        VBE version 300
        VBE string at 0xc01d0 "ATI ATOMBIOS"

VBE/DDC service about to be called
        Report DDC capabilities

        Performing real mode VBE call
        Interrupt 0x10 ax=0x4f15 bx=0x0 cx=0x0
        Function supported
        Call successful

        Monitor and video card combination does not support DDC1 transfers
        Monitor and video card combination supports DDC2 transfers
        0 seconds per 128 byte EDID block transfer
        Screen is not blanked during DDC transfer

Reading next EDID block

VBE/DDC service about to be called
        Read EDID

        Performing real mode VBE call
        Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
        Function supported
        Call successful

matthew@matthew-Aspire-7540 ~/my_storage/linux-3.4.0-3.7
 % cat monitor.edid 
&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;0&#65533;&#65533;&#65533;&x
&#65533;&#65533;XP&#65533;&PT/&@&#65533;`&#65533;000#~&#65533;&#65533;LGDisplay
&#65533;LP173WD1-TLA1x%                                                                                                                                                            matthew@matthew-Aspire-7540 ~/my_storage/linux-3.4.0-3.7
 %
```

The file monitor should contain (in binary which is why it looks like gobbledygook) your monitor edid information.

You should be able to take that file and move it over to your other machine and plug that file into your xorg.conf file.

I think we may have to create an xorg.conf for you though.

It looks like it may be the DVI->VGA connector that is causing you problems.

Kind regards

---

### Post by doobydave on 2012-05-25
Ok, so I have the file - 
```

$ cat monitor.edid 
&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&&#65533;@!&#65533;'&#65533;
(&#65533;&#65533;&#65533;WJ&#65533;&HL?&#61481;e&#65533;O&#65533;O&#65533;T&#65533;&#65533;&#65533;&#65533;

```

Just to let you know, I am using the proprietary nvidia driver on my laptop, which (up until six weeks ago) didn't noticebly suffer from these issues.

---

### Post by matt_symes on 2012-05-25
Hi

Let's see if that makes any difference. 

Copy the monitor.edid file onto a pen drive stick.

Boot into you problem PC, press ALT + F2 and type 

```
gksudo nautilus
```

Enter your password. Move the monitor.edid file to the folder /etc/X11 and then close nautilus.

Press CTRL + ALT + F1 together to bring up a console. 

Stop X running by stopping the display manager. Type

```
sudo service lightdm stop
```

If you still using gdm type

```
sudo service gdm stop
```

Make a backup of your existing xorg.conf file (if you have one)

```
sudo cp /etc/X11/xorg.conf{,bk}
```

Create a new xorg.conf file for your nvidia card.

```
sudo nvidia-xconfig --custom-edid=/etc/X11/monitor.edid
```

Check the xorg.conf file (Post it back into your next thread anyway)

```
cat /etc/X11/xorg.conf
```

You'll be looking for a line that says

```
Option	"CustomEDID" "DVI-I-1:/etc/X11/monitor.edid"
```

Reboot your computer normally by typing

```
sudo reboot
```

How does that get on ?

Kind regards

---

### Post by doobydave on 2012-05-25
Is that method valid for the open-source drivers?

---

### Post by matt_symes on 2012-05-25
Hi

Ahh. Your using nouveau on the problem PC. 

Sorry i misread the post where you said you used nvidia on the laptop and thought that was the problem PC ('tis been a long  couple of days here).

I'm not sure if the nouveau driver allows a custom EDID file to be used.

Is there any reason you cannot use the nvidia driver ?

Kind regards

---

### Post by doobydave on 2012-05-25
I don't blame you for the confusion, and thanks again for your time.

Like I said, I'm loathe to install the nvidia driver and call it a solution - despite ultimately probably wanting to use it. I will do so however if you think it will help with understanding the issue.

What makes you think the issue is the adapter? Looking through the Xorg.0.log from the 12.04 live cd boot on the laptop shows it loading and unloading several drivers, like the box using the adapter.

I read somewhere about forcing the VESA driver to use a certain resolution from GRUB - I tried one or two values, but they didn't really help (they did alter the behaviour, however)

Booting up to two desktops, neither of which have the unity bar on is not normal. If you like, I can repeat this to double check if the monitor is responsible for this omission (I can almost guarantee it is). I should also have mentioned that the display on the crt was the correct aspect ratio, but the display on the laptop was stretched.

---

### Post by doobydave on 2012-05-25
I've just been playing with Debian, and it appears (like Ubuntu) to be happier on the laptop.

I've just posted this to Debian Bugs (673669):-
"I booted my laptop from the live CD with the CRT plugged in directly, and while things are better, I'm not sure if everything is OK. I believe the nouveau driver is working, but the available resolution and refresh rates are incomplete. Looking through Xorg.0.log there are several bunches of modelines - not one group has all the correct resolutions, and many appear to be set at 0.0Hz.
Also, the hex EDID seems to have many 00 in it - could be fine, just looks strange.

UPDATE
Just been looking at the EDID extracted from windows (using Phoenix I think). It is different. I will include the two files extracted *.dat *.raw When extracting using this software, it gave a waning about converting data from one version to another. Maybe this is where the differences came from."

Debian X info gathering script
```

X server symlink status:
------------------------
lrwxrwxrwx 1 root root 13 Jan 29 11:06 /etc/X11/X -> /usr/bin/Xorg
-rwxr-xr-x 1 root root 1889472 Oct 29  2011 /usr/bin/Xorg

VGA-compatible devices on PCI bus:
----------------------------------
01:00.0 VGA compatible controller [0300]: nVidia Corporation G73 [GeForce Go 7600] [10de:0398] (rev a1)

/etc/X11/xorg.conf does not exist.

/etc/X11/xorg.conf.d does not exist.

KMS configuration files:
------------------------
/etc/modprobe.d/i915-kms.conf:
  options i915 modeset=1
/etc/modprobe.d/radeon-kms.conf:
  options radeon modeset=1

Kernel version (/proc/version):
-------------------------------
Linux version 2.6.32-5-amd64 (Debian 2.6.32-41) (ben@decadent.org.uk) (gcc version 4.3.5 (Debian 4.3.5-4) ) #1 SMP Mon Jan 16 16:22:28 UTC 2012

Xorg X server log files on system:
----------------------------------
-rw-r--r-- 1 root root 30725 May 25 22:36 /var/log/Xorg.0.log

Contents of most recent Xorg X server log file (/var/log/Xorg.0.log):
---------------------------------------------------------------------

X.Org X Server 1.7.7
Release Date: 2010-05-04
X Protocol Version 11, Revision 0
Build Operating System: Linux 3.0.0-1-amd64 x86_64 Debian
Current Operating System: Linux debian 2.6.32-5-amd64 #1 SMP Mon Jan 16 16:22:28 UTC 2012 x86_64
Kernel command line: initrd=/live/initrd.img boot=live config   quiet BOOT_IMAGE=/live/vmlinuz 
Build Date: 29 October 2011  06:58:14PM
xorg-server 2:1.7.7-14 (Julien Cristau <jcristau@debian.org>) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri May 25 22:22:05 2012
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(==) No screen section available. Using defaults.
(**) |-->Screen "Default Screen Section" (0)
(**) |   |-->Monitor "<default monitor>"
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
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x7c8a40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:1:0:0) 10de:0398:1025:0090 nVidia Corporation G73 [GeForce Go 7600] rev 161, Mem @ 0xd1000000/16777216, 0xc0000000/268435456, 0xd0000000/16777216, I/O @ 0x00002000/128
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.7.7, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension SELinux
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
	compiled for 1.7.7, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.7.7, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.7, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.7.7, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.7, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(==) Matched nouveau as autoconfigured driver 0
(==) Matched nv as autoconfigured driver 1
(==) Matched vesa as autoconfigured driver 2
(==) Matched fbdev as autoconfigured driver 3
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "nouveau"
(II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
(II) Module nouveau: vendor="X.Org Foundation"
	compiled for 1.7.7, module version = 0.0.15
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "nv"
(II) Loading /usr/lib/xorg/modules/drivers/nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
	compiled for 1.7.7, module version = 2.1.17
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.7.7, module version = 2.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
	compiled for 1.7.6.901, module version = 0.4.2
	ABI class: X.Org Video Driver, version 6.0
(II) NOUVEAU driver Date:   Tue Mar 16 13:08:37 2010 +1000
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
(II) NOUVEAU driver Date:   Tue Mar 16 13:08:37 2010 +1000
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
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 01@00:00:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) [drm] nouveau interface version: 0.0.15
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 1.7.7, module version = 0.0.2
	ABI class: X.Org Video Driver, version 6.0
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
(--) NOUVEAU(0): Chipset: "NVIDIA NV4b"
(II) NOUVEAU(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
(==) NOUVEAU(0): Depth 24, (--) framebuffer bpp 32
(==) NOUVEAU(0): RGB weight 888
(==) NOUVEAU(0): Default visual is TrueColor
(==) NOUVEAU(0): Using HW cursor
(II) NOUVEAU(0): Output VGA-1 has no monitor section
(II) NOUVEAU(0): Output LVDS-1 has no monitor section
(II) NOUVEAU(0): Output TV-1 has no monitor section
(II) NOUVEAU(0): Output DVI-D-1 has no monitor section
(II) NOUVEAU(0): EDID for output VGA-1
(II) NOUVEAU(0): Manufacturer: IVM  Model: 2140  Serial#: 10037195
(II) NOUVEAU(0): Year: 2000  Week: 5
(II) NOUVEAU(0): EDID Version: 1.1
(II) NOUVEAU(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) NOUVEAU(0): Sync:  Separate  Composite  SyncOnGreen
(II) NOUVEAU(0): Max Image Size [cm]: horiz.: 40  vert.: 30
(II) NOUVEAU(0): Gamma: 2.54
(II) NOUVEAU(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) NOUVEAU(0): redX: 0.625 redY: 0.340   greenX: 0.292 greenY: 0.604
(II) NOUVEAU(0): blueX: 0.150 blueY: 0.070   whiteX: 0.283 whiteY: 0.297
(II) NOUVEAU(0): Supported established timings:
(II) NOUVEAU(0): 640x480@60Hz
(II) NOUVEAU(0): 640x480@67Hz
(II) NOUVEAU(0): 640x480@72Hz
(II) NOUVEAU(0): 640x480@75Hz
(II) NOUVEAU(0): 800x600@56Hz
(II) NOUVEAU(0): 800x600@60Hz
(II) NOUVEAU(0): 800x600@72Hz
(II) NOUVEAU(0): 800x600@75Hz
(II) NOUVEAU(0): 832x624@75Hz
(II) NOUVEAU(0): 1024x768@60Hz
(II) NOUVEAU(0): 1024x768@70Hz
(II) NOUVEAU(0): 1024x768@75Hz
(II) NOUVEAU(0): 1280x1024@75Hz
(II) NOUVEAU(0): 1152x864@75Hz
(II) NOUVEAU(0): Manufacturer's mask: 0
(II) NOUVEAU(0): Supported standard timings:
(II) NOUVEAU(0): #0: hsize: 1600  vsize 1200  refresh: 97  vid: 26025
(II) NOUVEAU(0): #1: hsize: 1792  vsize 1344  refresh: 75  vid: 20417
(II) NOUVEAU(0): #2: hsize: 1856  vsize 1392  refresh: 75  vid: 20425
(II) NOUVEAU(0): #3: hsize: 2048  vsize 1536  refresh: 80  vid: 21729
(II) NOUVEAU(0):  
(II) NOUVEAU(0):  
(II) NOUVEAU(0):  
(II) NOUVEAU(0):  
(II) NOUVEAU(0): EDID (in hex):
(II) NOUVEAU(0): 	00ffffffffffff0026cd4021cb279900
(II) NOUVEAU(0): 	050a01010e281e9ae80e88a0574a9a26
(II) NOUVEAU(0): 	12484c3fef80a965c14fc94fe1540101
(II) NOUVEAU(0): 	010101010101000000fe000000000000
(II) NOUVEAU(0): 	0000000000000000000000fe00000000
(II) NOUVEAU(0): 	00000000000000000000000000fe0000
(II) NOUVEAU(0): 	000000000000000000000000000000fe
(II) NOUVEAU(0): 	000000000000000000000000000000ea
(II) NOUVEAU(0): EDID vendor "IVM", prod id 8512
(II) NOUVEAU(0): Printing DDC gathered Modelines:
(II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NOUVEAU(0): Modeline "1792x1344"x0.0  261.00  1792 1888 2104 2456  1344 1345 1348 1417 -hsync +vsync (106.3 kHz)
(II) NOUVEAU(0): Modeline "1856x1392"x0.0  288.00  1856 1984 2208 2560  1392 1393 1396 1500 -hsync +vsync (112.5 kHz)
(II) NOUVEAU(0): Printing probed modes for output VGA-1
(II) NOUVEAU(0): Modeline "1856x1392"x75.0  288.00  1856 1984 2208 2560  1392 1395 1399 1500 -hsync +vsync (112.5 kHz)
(II) NOUVEAU(0): Modeline "1792x1344"x75.0  261.00  1792 1888 2104 2456  1344 1345 1348 1417 -hsync +vsync (106.3 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NOUVEAU(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) NOUVEAU(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) NOUVEAU(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NOUVEAU(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) NOUVEAU(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NOUVEAU(0): EDID for output LVDS-1
(II) NOUVEAU(0): Manufacturer: CMO  Model: 1554  Serial#: 0
(II) NOUVEAU(0): Year: 2007  Week: 40
(II) NOUVEAU(0): EDID Version: 1.3
(II) NOUVEAU(0): Digital Display Input
(II) NOUVEAU(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) NOUVEAU(0): Gamma: 2.20
(II) NOUVEAU(0): No DPMS capabilities specified
(II) NOUVEAU(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) NOUVEAU(0): First detailed timing is preferred mode
(II) NOUVEAU(0): redX: 0.602 redY: 0.340   greenX: 0.306 greenY: 0.530
(II) NOUVEAU(0): blueX: 0.151 blueY: 0.120   whiteX: 0.313 whiteY: 0.329
(II) NOUVEAU(0): Manufacturer's mask: 0
(II) NOUVEAU(0): Supported detailed timing:
(II) NOUVEAU(0): clock: 71.0 MHz   Image Size:  331 x 207 mm
(II) NOUVEAU(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) NOUVEAU(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
(II) NOUVEAU(0):  N154I3-L03
(II) NOUVEAU(0):  CMO
(II) NOUVEAU(0):  N154I3-L03
(II) NOUVEAU(0): EDID (in hex):
(II) NOUVEAU(0): 	00ffffffffffff000daf541500000000
(II) NOUVEAU(0): 	28110103802115780a07f59a574e8726
(II) NOUVEAU(0): 	1e505400000001010101010101010101
(II) NOUVEAU(0): 	010101010101bc1b00a0502017303020
(II) NOUVEAU(0): 	36004bcf10000018000000fe004e3135
(II) NOUVEAU(0): 	3449332d4c30330a2020000000fe0043
(II) NOUVEAU(0): 	4d4f0a202020202020202020000000fe
(II) NOUVEAU(0): 	004e31353449332d4c30330a202000a5
(II) NOUVEAU(0): Printing probed modes for output LVDS-1
(II) NOUVEAU(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
(II) NOUVEAU(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
(II) NOUVEAU(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
(II) NOUVEAU(0): Modeline "720x400"x59.6   22.25  720 744 808 896  400 403 413 417 -hsync +vsync (24.8 kHz)
(II) NOUVEAU(0): Modeline "640x400"x60.0   20.00  640 664 720 800  400 403 409 417 -hsync +vsync (25.0 kHz)
(II) NOUVEAU(0): Modeline "640x350"x59.8   17.50  640 664 720 800  350 353 363 366 -hsync +vsync (21.9 kHz)
(II) NOUVEAU(0): EDID for output TV-1
(II) NOUVEAU(0): EDID for output DVI-D-1
(II) NOUVEAU(0): Output VGA-1 connected
(II) NOUVEAU(0): Output LVDS-1 connected
(II) NOUVEAU(0): Output TV-1 disconnected
(II) NOUVEAU(0): Output DVI-D-1 disconnected
(II) NOUVEAU(0): Using fuzzy aspect match for initial modes
(II) NOUVEAU(0): Output VGA-1 using initial mode 1024x768
(II) NOUVEAU(0): Output LVDS-1 using initial mode 1024x768
(II) NOUVEAU(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
(--) NOUVEAU(0): Virtual size is 1024x768 (pitch 1024)
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
(**) NOUVEAU(0):  Driver mode "1280x800": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 59.9 Hz
(II) NOUVEAU(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
(**) NOUVEAU(0): Display dimensions: (400, 300) mm
(**) NOUVEAU(0): DPI set to (65, 65)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.7.7, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules/libexa.so
(II) Module exa: vendor="X.Org Foundation"
	compiled for 1.7.7, module version = 2.5.0
	ABI class: X.Org Video Driver, version 6.0
(II) Loading sub module "shadowfb"
(II) LoadModule: "shadowfb"
(II) Loading /usr/lib/xorg/modules/libshadowfb.so
(II) Module shadowfb: vendor="X.Org Foundation"
	compiled for 1.7.7, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) UnloadModule: "nv"
(II) Unloading /usr/lib/xorg/modules/drivers/nv_drv.so
(II) UnloadModule: "vesa"
(II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(--) Depth 24 pixmap format is 32 bpp
(II) NOUVEAU(0): Opened GPU channel 1
(II) NOUVEAU(0): [DRI2] Setup complete
(II) NOUVEAU(0): GART: 64MiB available
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
(II) NOUVEAU(0): [XvMC] Associated with NV40 texture adapter.
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
SELinux: Disabled on system, not enabling in X server
(II) AIGLX error: dlopen of /usr/lib/dri/nouveau_dri.so failed (/usr/lib/dri/nouveau_dri.so: cannot open shared object file: No such file or directory)
(II) AIGLX: reverting to software rendering
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) NOUVEAU(0): Setting screen physical size to 270 x 203
resize called 1024 768
(II) config/udev: Adding input device Power Button (/dev/input/event7)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.7.6.901, module version = 2.3.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event7"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Video Bus (/dev/input/event9)
(**) Video Bus: Applying InputClass "evdev keyboard catchall"
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event9"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Power Button (/dev/input/event6)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event6"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Lid Switch (/dev/input/event4)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Sleep Button (/dev/input/event5)
(**) Sleep Button: Applying InputClass "evdev keyboard catchall"
(**) Sleep Button: always reports core events
(**) Sleep Button: Device: "/dev/input/event5"
(II) Sleep Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event11)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device ORTEK Smartpad Keyboard (/dev/input/event2)
(**) ORTEK Smartpad Keyboard: Applying InputClass "evdev keyboard catchall"
(**) ORTEK Smartpad Keyboard: always reports core events
(**) ORTEK Smartpad Keyboard: Device: "/dev/input/event2"
(II) ORTEK Smartpad Keyboard: Found keys
(II) ORTEK Smartpad Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "ORTEK Smartpad Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device ORTEK Smartpad Keyboard (/dev/input/event3)
(**) ORTEK Smartpad Keyboard: Applying InputClass "evdev pointer catchall"
(**) ORTEK Smartpad Keyboard: Applying InputClass "evdev keyboard catchall"
(**) ORTEK Smartpad Keyboard: always reports core events
(**) ORTEK Smartpad Keyboard: Device: "/dev/input/event3"
(II) ORTEK Smartpad Keyboard: Found 9 mouse buttons
(II) ORTEK Smartpad Keyboard: Found scroll wheel(s)
(II) ORTEK Smartpad Keyboard: Found relative axes
(II) ORTEK Smartpad Keyboard: Found x and y relative axes
(II) ORTEK Smartpad Keyboard: Found absolute axes
(II) ORTEK Smartpad Keyboard: Found keys
(II) ORTEK Smartpad Keyboard: Configuring as mouse
(II) ORTEK Smartpad Keyboard: Configuring as keyboard
(**) ORTEK Smartpad Keyboard: YAxisMapping: buttons 4 and 5
(**) ORTEK Smartpad Keyboard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "ORTEK Smartpad Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) ORTEK Smartpad Keyboard: initialized for relative axes.
(WW) ORTEK Smartpad Keyboard: ignoring absolute axes.
(II) config/udev: Adding input device ORTEK Smartpad Keyboard (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event1)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event1"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event10)
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.7.6.901, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(II) Synaptics touchpad driver version 1.2.2
(**) Option "Device" "/dev/input/event10"
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
(II) SynPS/2 Synaptics TouchPad: buttons: left right middle double triple
(--) SynPS/2 Synaptics TouchPad: touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
(--) SynPS/2 Synaptics TouchPad: touchpad found
(II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse2)
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
(II) Synaptics touchpad driver version 1.2.2
SynPS/2 Synaptics TouchPad no synaptics event device found
(**) Option "Device" "/dev/input/mouse2"
Query no Synaptics: 6003C8
(--) SynPS/2 Synaptics TouchPad: no supported touchpad found
(EE) SynPS/2 Synaptics TouchPad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "SynPS/2 Synaptics TouchPad"
(II) UnloadModule: "synaptics"
(II) config/udev: Adding input device PC Speaker (/dev/input/event8)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event0)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
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
(II) config/udev: Adding input device ACPI Virtual Keyboard Device (/dev/input/event12)
(**) ACPI Virtual Keyboard Device: Applying InputClass "evdev keyboard catchall"
(**) ACPI Virtual Keyboard Device: always reports core events
(**) ACPI Virtual Keyboard Device: Device: "/dev/input/event12"
(II) ACPI Virtual Keyboard Device: Found keys
(II) ACPI Virtual Keyboard Device: Configuring as keyboard
(II) XINPUT: Adding extended input device "ACPI Virtual Keyboard Device" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) NOUVEAU(0): EDID vendor "CMO", prod id 5460
(II) NOUVEAU(0): Printing DDC gathered Modelines:
(II) NOUVEAU(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
(II) NOUVEAU(0): EDID vendor "CMO", prod id 5460
(II) NOUVEAU(0): Printing DDC gathered Modelines:
(II) NOUVEAU(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
(II) NOUVEAU(0): EDID vendor "CMO", prod id 5460
(II) NOUVEAU(0): Printing DDC gathered Modelines:
(II) NOUVEAU(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
(II) NOUVEAU(0): EDID vendor "CMO", prod id 5460
(II) NOUVEAU(0): Printing DDC gathered Modelines:
(II) NOUVEAU(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
(II) NOUVEAU(0): EDID vendor "CMO", prod id 5460
(II) NOUVEAU(0): Printing DDC gathered Modelines:
(II) NOUVEAU(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)

udev information:
-----------------
P: /devices/LNXSYSTM:00/LNXPWRBN:00/input/input7/event7
N: input/event7
S: char/13:71
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input7/event7
E: MAJOR=13
E: MINOR=71
E: DEVNAME=/dev/input/event7
E: SUBSYSTEM=input
E: ID_INPUT=1
E: ID_INPUT_KEY=1
E: XKBMODEL=pc105
E: XKBLAYOUT=us
E: DEVLINKS=/dev/char/13:71
E: DMI_VENDOR=Acer

P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/LNXVIDEO:00/input/input9/event9
N: input/event9
S: char/13:73
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/LNXVIDEO:00/input/input9/event9
E: MAJOR=13
E: MINOR=73
E: DEVNAME=/dev/input/event9
E: SUBSYSTEM=input
E: ID_INPUT=1
E: ID_INPUT_KEY=1
E: XKBMODEL=pc105
E: XKBLAYOUT=us
E: DEVLINKS=/dev/char/13:73
E: DMI_VENDOR=Acer

P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input6/event6
N: input/event6
S: char/13:70
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input6/event6
E: MAJOR=13
E: MINOR=70
E: DEVNAME=/dev/input/event6
E: SUBSYSTEM=input
E: ID_INPUT=1
E: ID_INPUT_KEY=1
E: XKBMODEL=pc105
E: XKBLAYOUT=us
E: DEVLINKS=/dev/char/13:70
E: DMI_VENDOR=Acer

P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input4/event4
N: input/event4
S: char/13:68
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input4/event4
E: MAJOR=13
E: MINOR=68
E: DEVNAME=/dev/input/event4
E: SUBSYSTEM=input
E: ID_INPUT=1
E: DMI_VENDOR=Acer
E: DEVLINKS=/dev/char/13:68

P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input5/event5
N: input/event5
S: char/13:69
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input5/event5
E: MAJOR=13
E: MINOR=69
E: DEVNAME=/dev/input/event5
E: SUBSYSTEM=input
E: ID_INPUT=1
E: ID_INPUT_KEY=1
E: XKBMODEL=pc105
E: XKBLAYOUT=us
E: DEVLINKS=/dev/char/13:69
E: DMI_VENDOR=Acer

P: /devices/pci0000:00/0000:00:1b.0/input/input11/event11
N: input/event11
S: char/13:75
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/input/input11/event11
E: MAJOR=13
E: MINOR=75
E: DEVNAME=/dev/input/event11
E: SUBSYSTEM=input
E: ID_INPUT=1
E: ID_PATH=pci-0000:00:1b.0
E: DMI_VENDOR=Acer
E: DEVLINKS=/dev/char/13:75

P: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input2/event2
N: input/event2
S: char/13:66
S: input/by-id/usb-ORTEK_Smartpad_Keyboard-event-kbd
S: input/by-path/pci-0000:00:1d.0-usb-0:1:1.0-event-kbd
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input2/event2
E: MAJOR=13
E: MINOR=66
E: DEVNAME=/dev/input/event2
E: SUBSYSTEM=input
E: ID_INPUT=1
E: ID_INPUT_KEY=1
E: ID_INPUT_KEYBOARD=1
E: ID_VENDOR=ORTEK
E: ID_VENDOR_ENC=ORTEK
E: ID_VENDOR_ID=05a4
E: ID_MODEL=Smartpad_Keyboard
E: ID_MODEL_ENC=Smartpad\x20Keyboard
E: ID_MODEL_ID=2000
E: ID_REVISION=1110
E: ID_SERIAL=ORTEK_Smartpad_Keyboard
E: ID_TYPE=hid
E: ID_BUS=usb
E: ID_USB_INTERFACES=:030101:030102:
E: ID_USB_INTERFACE_NUM=00
E: ID_USB_DRIVER=usbhid
E: ID_PATH=pci-0000:00:1d.0-usb-0:1:1.0
E: XKBMODEL=pc105
E: XKBLAYOUT=us
E: DEVLINKS=/dev/char/13:66 /dev/input/by-id/usb-ORTEK_Smartpad_Keyboard-event-kbd /dev/input/by-path/pci-0000:00:1d.0-usb-0:1:1.0-event-kbd

P: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.1/input/input3/event3
N: input/event3
S: char/13:67
S: input/by-id/usb-ORTEK_Smartpad_Keyboard-event-mouse
S: input/by-path/pci-0000:00:1d.0-usb-0:1:1.1-event-mouse
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.1/input/input3/event3
E: MAJOR=13
E: MINOR=67
E: DEVNAME=/dev/input/event3
E: SUBSYSTEM=input
E: ID_INPUT=1
E: ID_INPUT_MOUSE=1
E: ID_INPUT_KEY=1
E: ID_VENDOR=ORTEK
E: ID_VENDOR_ENC=ORTEK
E: ID_VENDOR_ID=05a4
E: ID_MODEL=Smartpad_Keyboard
E: ID_MODEL_ENC=Smartpad\x20Keyboard
E: ID_MODEL_ID=2000
E: ID_REVISION=1110
E: ID_SERIAL=ORTEK_Smartpad_Keyboard
E: ID_TYPE=hid
E: ID_BUS=usb
E: ID_USB_INTERFACES=:030101:030102:
E: ID_USB_INTERFACE_NUM=01
E: ID_USB_DRIVER=usbhid
E: ID_PATH=pci-0000:00:1d.0-usb-0:1:1.1
E: XKBMODEL=pc105
E: XKBLAYOUT=us
E: DEVLINKS=/dev/char/13:67 /dev/input/by-id/usb-ORTEK_Smartpad_Keyboard-event-mouse /dev/input/by-path/pci-0000:00:1d.0-usb-0:1:1.1-event-mouse

P: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.1/input/input3/mouse1
N: input/mouse1
S: char/13:33
S: input/by-id/usb-ORTEK_Smartpad_Keyboard-mouse
S: input/by-path/pci-0000:00:1d.0-usb-0:1:1.1-mouse
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.1/input/input3/mouse1
E: MAJOR=13
E: MINOR=33
E: DEVNAME=/dev/input/mouse1
E: SUBSYSTEM=input
E: ID_INPUT=1
E: ID_INPUT_MOUSE=1
E: ID_INPUT_KEY=1
E: ID_VENDOR=ORTEK
E: ID_VENDOR_ENC=ORTEK
E: ID_VENDOR_ID=05a4
E: ID_MODEL=Smartpad_Keyboard
E: ID_MODEL_ENC=Smartpad\x20Keyboard
E: ID_MODEL_ID=2000
E: ID_REVISION=1110
E: ID_SERIAL=ORTEK_Smartpad_Keyboard
E: ID_TYPE=hid
E: ID_BUS=usb
E: ID_USB_INTERFACES=:030101:030102:
E: ID_USB_INTERFACE_NUM=01
E: ID_USB_DRIVER=usbhid
E: ID_PATH=pci-0000:00:1d.0-usb-0:1:1.1
E: DEVLINKS=/dev/char/13:33 /dev/input/by-id/usb-ORTEK_Smartpad_Keyboard-mouse /dev/input/by-path/pci-0000:00:1d.0-usb-0:1:1.1-mouse

P: /devices/platform/i8042/serio0/input/input1/event1
N: input/event1
S: char/13:65
S: input/by-path/platform-i8042-serio-0-event-kbd
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/i8042/serio0/input/input1/event1
E: MAJOR=13
E: MINOR=65
E: DEVNAME=/dev/input/event1
E: SUBSYSTEM=input
E: ID_INPUT=1
E: ID_INPUT_KEY=1
E: ID_INPUT_KEYBOARD=1
E: ID_SERIAL=noserial
E: ID_PATH=platform-i8042-serio-0
E: XKBMODEL=pc105
E: XKBLAYOUT=us
E: DEVLINKS=/dev/char/13:65 /dev/input/by-path/platform-i8042-serio-0-event-kbd
E: DMI_VENDOR=Acer

P: /devices/platform/i8042/serio4/input/input10/event10
N: input/event10
S: char/13:74
S: input/by-path/platform-i8042-serio-4-event-mouse
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/i8042/serio4/input/input10/event10
E: MAJOR=13
E: MINOR=74
E: DEVNAME=/dev/input/event10
E: SUBSYSTEM=input
E: ID_INPUT=1
E: ID_INPUT_TOUCHPAD=1
E: ID_SERIAL=noserial
E: ID_PATH=platform-i8042-serio-4
E: DMI_VENDOR=Acer
E: DEVLINKS=/dev/char/13:74 /dev/input/by-path/platform-i8042-serio-4-event-mouse

P: /devices/platform/i8042/serio4/input/input10/mouse2
N: input/mouse2
S: char/13:34
S: input/by-path/platform-i8042-serio-4-mouse
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/i8042/serio4/input/input10/mouse2
E: MAJOR=13
E: MINOR=34
E: DEVNAME=/dev/input/mouse2
E: SUBSYSTEM=input
E: ID_INPUT=1
E: ID_INPUT_TOUCHPAD=1
E: ID_SERIAL=noserial
E: ID_PATH=platform-i8042-serio-4
E: DEVLINKS=/dev/char/13:34 /dev/input/by-path/platform-i8042-serio-4-mouse

P: /devices/platform/pcspkr/input/input8/event8
N: input/event8
S: char/13:72
S: input/by-path/platform-pcspkr-event-spkr
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/pcspkr/input/input8/event8
E: MAJOR=13
E: MINOR=72
E: DEVNAME=/dev/input/event8
E: SUBSYSTEM=input
E: ID_INPUT=1
E: ID_SERIAL=noserial
E: ID_PATH=platform-pcspkr
E: DMI_VENDOR=Acer
E: DEVLINKS=/dev/char/13:72 /dev/input/by-path/platform-pcspkr-event-spkr

P: /devices/virtual/input/input0/event0
N: input/event0
S: char/13:64
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/input/input0/event0
E: MAJOR=13
E: MINOR=64
E: DEVNAME=/dev/input/event0
E: SUBSYSTEM=input
E: ID_INPUT=1
E: ID_INPUT_MOUSE=1
E: ID_SERIAL=noserial
E: DMI_VENDOR=Acer
E: DEVLINKS=/dev/char/13:64

P: /devices/virtual/input/input0/mouse0
N: input/mouse0
S: char/13:32
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/input/input0/mouse0
E: MAJOR=13
E: MINOR=32
E: DEVNAME=/dev/input/mouse0
E: SUBSYSTEM=input
E: ID_INPUT=1
E: ID_INPUT_MOUSE=1
E: ID_SERIAL=noserial
E: DEVLINKS=/dev/char/13:32

P: /devices/virtual/input/input12/event12
N: input/event12
S: char/13:76
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/input/input12/event12
E: MAJOR=13
E: MINOR=76
E: DEVNAME=/dev/input/event12
E: SUBSYSTEM=input
E: ID_INPUT=1
E: ID_INPUT_KEY=1
E: ID_INPUT_KEYBOARD=1
E: ID_SERIAL=noserial
E: XKBMODEL=pc105
E: XKBLAYOUT=us
E: DEVLINKS=/dev/char/13:76
E: DMI_VENDOR=Acer


DRM Information from dmesg:
---------------------------

```

EDID from windows
```

EDID BYTES:
0x   00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
    ------------------------------------------------
00 | 00 FF FF FF FF FF FF 00 26 CD 40 21 CB 27 99 00
10 | 05 0A 01 03 0E 28 1E 9A E8 0E 88 A0 57 4A 9A 26
20 | 12 48 4C 3F EF 80 A9 65 C1 4F C9 4F E1 54 01 01
30 | 01 01 01 01 01 01 00 00 00 FE 00 00 00 00 00 00
40 | 00 00 00 00 00 00 00 00 00 00 00 FE 00 00 00 00
50 | 00 00 00 00 00 00 00 00 00 00 00 00 00 FE 00 00
60 | 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 FE
70 | 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 E8

```

---

### Post by matt_symes on 2012-05-28
Hi
 
Try both the EDID from Windows and Ubuntu. 
 
You may have to use the nvidia driver though.
 
Kind regards

---

### Post by doobydave on 2012-06-10
I will double check, (when I have another spare day) but I think the state of play currently is this;

Both the nvidia driver and the open source drivers obtain the same EDID.
All open source drivers fail to drive my CRT as CRT, instead they try to run it as an LCD widescreen, using LCD resolution/refresh rates.

---

