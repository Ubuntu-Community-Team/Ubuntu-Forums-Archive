---
title: "firefox randomly logging me out of Ubuntu 10.04"
date: 2010-11-19
forum: General Help
---

### Post by eival on 2010-11-19
this is extremely annoying, the entire screen goes black, then i see the login screen.

its happened on different sites so i have no way to pinpoint whats causing this

and ubuntu doesnt display anything that makes it seem like its a crash.

is there any logs that would show me whats going on?

has anyone else had this happen?

---

### Post by NightwishFan on 2010-11-19
Yes, under System -> Administration -> Log File Viewer. Check syslog and Xorg.log for errors. Probably be related to a segmentation fault. The system logging out means that the display server has crashed, which makes me think this is GPU releated. What model of graphics card are you using and what driver? To find out the former, run this command in the terminal:
```
lshw -C display
```

The latter we can figure out easily after we know the former.

---

### Post by eival on 2010-11-19
> **NightwishFan said:**
> Yes, under System -> Administration -> Log File Viewer. Check syslog and Xorg.log for errors. Probably be related to a segmentation fault. The system logging out means that the display server has crashed, which makes me think this is GPU releated. What model of graphics card are you using and what driver? To find out the former, run this command in the terminal:
```
lshw -C display
```

The latter we can figure out easily after we know the former.

heres my display info

```
  *-display:0             
       description: VGA compatible controller
       product: 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:27 memory:fe400000-fe7fffff memory:e0000000-efffffff(prefetchable) ioport:cc00(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:fe900000-fe9fffff

```

what specifically should i look for in the system logs?

---

### Post by NightwishFan on 2010-11-19
I have this same exact chipset and have no problems. Look for a line that says either:
```
segmentation fault
```
or
```
segfault
```

You can post the logs here using code tags I think (though I would be careful you do them right so the page scrolls and does not post the whole log as text :) )

Also try looking in the log titled "messages"

---

### Post by eival on 2010-11-19
> **NightwishFan said:**
> I have this same exact chipset and have no problems. Look for a line that says either:
```
segmentation fault
```
or
```
segfault
```

You can post the logs here using code tags I think (though I would be careful you do them right so the page scrolls and does not post the whole log as text :) )

Also try looking in the log titled "messages"

since theres no search option in the logger i copied an pasted to gedit and searched for both those terms and neither log had either of those 2 words

---

### Post by eival on 2010-11-19
okay in Messages i did find that error

```
Nov 19 11:32:13 marcus-desktop kernel: [100157.499939] gnome-system-lo[21406]: segfault at 1c ip 004cc1af sp bfdd0120 error 4 in libgtk-x11-2.0.so.0.2000.1[2e3000+3cd000]
```

well thats not the error cause that says 11:32 which was just a few minutes ago.

im trying to copy the message log but every second it seems to update and it takes me back to the bottom so i cant copy the errors from earlier int he day

how do i suspend the log long enough to copy it or look thru it?

---

### Post by NightwishFan on 2010-11-19
I am not quite sure. Though the log file viewer has a built in search, CTRL+F. Sorry I forgot to mention before I left. (It hit me on my way back). I think the killer will be in one of the Xorg logs, check them. Skim them as well (they are shorter) for any error. (Not just segfault). I am sorry I can not be of much more help. I am not really a programmer, just a technical user.

---

### Post by eival on 2010-11-19
> **NightwishFan said:**
> I am not quite sure. Though the log file viewer has a built in search, CTRL+F. Sorry I forgot to mention before I left. (It hit me on my way back). I think the killer will be in one of the Xorg logs, check them. Skim them as well (they are shorter) for any error. (Not just segfault). I am sorry I can not be of much more help. I am not really a programmer, just a technical user.


yeah i found that search option , but like i said it keeps updating every 5 seconds and takes me back to the bottom, but i did get a full copy an pasted it into gedit an that error i showed was the only one listed today.

as for Xorg i dont see anything that shows timestamps, so im not sure if this is the same log your talking about but here it is:

edit-okay i see where they put a EE for errors, theres no errors in this log but there are some warnings WW i highlighted with red

```

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-28-server i686 Ubuntu
Current Operating System: Linux marcus-desktop 2.6.32-25-generic #45-Ubuntu SMP Sat Oct 16 19:48:22 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-25-generic root=UUID=90b10e71-95b3-42c0-a532-a5d5987e34b4 ro quiet splash
Build Date: 10 November 2010  11:25:26AM
xorg-server 2:1.7.6-2ubuntu7.4 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
[COLOR="Red"]	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.[/COLOR]
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Nov 19 10:43:06 2010
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(==) No screen section available. Using defaults.
(**) |-->Screen "Default Screen Section" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
[COLOR="DarkRed"](WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.[/COLOR]
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
(II) Loader magic: 0x81f1b20
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(--) using VT number 8

(--) PCI:*(0:0:2:0) 8086:2e22:103c:2a94 Intel Corporation 4 Series Chipset Integrated Graphics Controller rev 3, Mem @ 0xfe400000/4194304, 0xe0000000/268435456, I/O @ 0x0000cc00/8
(--) PCI: (0:0:2:1) 8086:2e23:103c:2a94 Intel Corporation 4 Series Chipset Integrated Graphics Controller rev 3, Mem @ 0xfe900000/1048576
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
(==) Matched intel as autoconfigured driver 0
(==) Matched vesa as autoconfigured driver 1
(==) Matched fbdev as autoconfigured driver 2
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.9.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.4.1
	ABI class: X.Org Video Driver, version 6.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, Clarkdale, Arrandale
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 00@00:02:0
[COLOR="DarkRed"](WW) Falling back to old probe method for vesa[/COLOR]
[COLOR="DarkRed"](WW) Falling back to old probe method for fbdev[/COLOR]
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.0.2
	ABI class: X.Org Video Driver, version 6.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) G45/G43
(--) intel(0): Chipset: "G45/G43"
(II) intel(0): Output VGA1 has no monitor section
(II) intel(0): Output HDMI1 has no monitor section
(II) intel(0): Output DP1 has no monitor section
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: SHP  Model: ffc  Serial#: 0
(II) intel(0): Year: 2007  Week: 255
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.714/0.286 V
(II) intel(0): Sync:  Separate
(II) intel(0): Indeterminate output size
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.633 redY: 0.333   greenX: 0.205 greenY: 0.702
(II) intel(0): blueX: 0.150 blueY: 0.081   whiteX: 0.292 whiteY: 0.322
(II) intel(0): Supported established timings:
(II) intel(0): 720x400@70Hz
(II) intel(0): 640x480@60Hz
(II) intel(0): 640x480@72Hz
(II) intel(0): 640x480@75Hz
(II) intel(0): 800x600@56Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 800x600@72Hz
(II) intel(0): 800x600@75Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): 1024x768@70Hz
(II) intel(0): 1024x768@75Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) intel(0): #1: hsize: 1400  vsize 1050  refresh: 60  vid: 16528
(II) intel(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 121.8 MHz   Image Size:  0 x 0 mm
(II) intel(0): h_active: 1400  h_sync: 1488  h_sync_end 1632 h_blank_end 1864 h_border: 0
(II) intel(0): v_active: 1050  v_sync: 1053  v_sync_end 1057 v_blanking: 1089 v_border: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 85.5 MHz   Image Size:  0 x 0 mm
(II) intel(0): h_active: 1360  h_sync: 1424  h_sync_end 1536 h_blank_end 1792 h_border: 0
(II) intel(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 795 v_border: 0
(II) intel(0): Ranges: V min: 55 V max: 76 Hz, H min: 31 H max: 75 kHz, PixClock max 170 MHz
(II) intel(0): Monitor name: SHARP LCD
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff004d10fc0f00000000
(II) intel(0): 	ff110103280000782a1bbea25534b326
(II) intel(0): 	144a52afce00a9409040818001010101
(II) intel(0): 	0101010101018f2f78d0511a27405890
(II) intel(0): 	340000000000001e662150b051001b30
(II) intel(0): 	4070360000000000001e000000fd0037
(II) intel(0): 	4c1f4b11000a202020202020000000fc
(II) intel(0): 	005348415250204c43440a202020001d
(II) intel(0): EDID vendor "SHP", prod id 4092
(II) intel(0): Using EDID range info for horizontal sync
(II) intel(0): Using EDID range info for vertical refresh
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1400x1050"x0.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 +hsync +vsync (65.3 kHz)
(II) intel(0): Modeline "1360x768"x0.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) intel(0): Modeline "1400x1050"x0.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 +hsync +vsync (65.3 kHz)
(II) intel(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) intel(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
(II) intel(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1360x768"x60.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz)
(II) intel(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): EDID for output HDMI1
(II) intel(0): Manufacturer: ACI  Model: 22f2  Serial#: 16843009
(II) intel(0): Year: 2010  Week: 34
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 48  vert.: 27
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: StandBy Suspend Off
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): Default color space is primary color space
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.640 redY: 0.340   greenX: 0.290 greenY: 0.609
(II) intel(0): blueX: 0.140 blueY: 0.069   whiteX: 0.310 whiteY: 0.330
(II) intel(0): Supported established timings:
(II) intel(0): 720x400@70Hz
(II) intel(0): 640x480@60Hz
(II) intel(0): 640x480@67Hz
(II) intel(0): 640x480@72Hz
(II) intel(0): 640x480@75Hz
(II) intel(0): 800x600@56Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 800x600@72Hz
(II) intel(0): 800x600@75Hz
(II) intel(0): 832x624@75Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): 1024x768@70Hz
(II) intel(0): 1024x768@75Hz
(II) intel(0): 1280x1024@75Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) intel(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) intel(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) intel(0): #4: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) intel(0): #5: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) intel(0): #6: hsize: 1920  vsize 1080  refresh: 60  vid: 49361
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 148.5 MHz   Image Size:  477 x 268 mm
(II) intel(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
(II) intel(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
(II) intel(0): Ranges: V min: 50 V max: 76 Hz, H min: 31 H max: 83 kHz, PixClock max 170 MHz
(II) intel(0): Monitor name: VH226
(II) intel(0): Serial No: A8LMQS018484
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff000469f22201010101
(II) intel(0): 	2214010380301b78eec4f6a3574a9c23
(II) intel(0): 	114f54bfef00714f818081409500a940
(II) intel(0): 	b300d1c00101023a801871382d40582c
(II) intel(0): 	4500dd0c1100001e000000fd00324c1f
(II) intel(0): 	5311000a202020202020000000fc0056
(II) intel(0): 	483232360a20202020202020000000ff
(II) intel(0): 	0041384c4d51533031383438340a0008
(II) intel(0): Printing probed modes for output HDMI1
(II) intel(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) intel(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) intel(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): EDID for output DP1
(II) intel(0): Output VGA1 connected
(II) intel(0): Output HDMI1 connected
(II) intel(0): Output DP1 disconnected
(II) intel(0): Using fuzzy aspect match for initial modes
(II) intel(0): Output VGA1 using initial mode 1600x1200
(II) intel(0): Output HDMI1 using initial mode 1600x1200
(II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) UnloadModule: "vesa"
(II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(==) Depth 24 pixmap format is 32 bpp
(II) intel(0): [DRI2] Setup complete
(**) intel(0): Framebuffer compression disabled
(**) intel(0): Tiling enabled
(**) intel(0): SwapBuffers wait enabled
(==) intel(0): VideoRam: 262144 KB
(II) intel(0): Attempting memory allocation with tiled buffers.
(II) intel(0): Tiled allocation successful.
(II) UXA(0): Driver registered support for the following operations:
(II)         solid
(II)         copy
(II)         composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): No memory allocations
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(==) intel(0): DPMS enabled
(==) intel(0): Intel XvMC decoder disabled
(II) intel(0): Set up textured video
(II) intel(0): direct rendering: DRI2 Enabled
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
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_make_current_read
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
(II) AIGLX: Loaded and initialized /usr/lib/dri/i965_dri.so
(II) GLX: Initialized DRI2 GL provider for screen 0
(II) intel(0): Setting screen physical size to 423 x 317
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event7)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device CHICONY HP USB Multimedia Keyboard (/dev/input/event3)
(**) CHICONY HP USB Multimedia Keyboard: Applying InputClass "evdev keyboard catchall"
(**) CHICONY HP USB Multimedia Keyboard: always reports core events
(**) CHICONY HP USB Multimedia Keyboard: Device: "/dev/input/event3"
(II) CHICONY HP USB Multimedia Keyboard: Found keys
(II) CHICONY HP USB Multimedia Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "CHICONY HP USB Multimedia Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device CHICONY HP USB Multimedia Keyboard (/dev/input/event4)
(**) CHICONY HP USB Multimedia Keyboard: Applying InputClass "evdev keyboard catchall"
(**) CHICONY HP USB Multimedia Keyboard: always reports core events
(**) CHICONY HP USB Multimedia Keyboard: Device: "/dev/input/event4"
(II) CHICONY HP USB Multimedia Keyboard: Found keys
(II) CHICONY HP USB Multimedia Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "CHICONY HP USB Multimedia Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device PS2 to USB (/dev/input/event5)
(**) PS2 to USB: Applying InputClass "evdev keyboard catchall"
(**) PS2 to USB: always reports core events
(**) PS2 to USB: Device: "/dev/input/event5"
(II) PS2 to USB: Found keys
(II) PS2 to USB: Configuring as keyboard
(II) XINPUT: Adding extended input device "PS2 to USB" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device PS2 to USB (/dev/input/event6)
(**) PS2 to USB: Applying InputClass "evdev pointer catchall"
(**) PS2 to USB: Applying InputClass "evdev keyboard catchall"
(**) PS2 to USB: always reports core events
(**) PS2 to USB: Device: "/dev/input/event6"
(II) PS2 to USB: Found 9 mouse buttons
(II) PS2 to USB: Found scroll wheel(s)
(II) PS2 to USB: Found relative axes
(II) PS2 to USB: Found x and y relative axes
(II) PS2 to USB: Found absolute axes
(II) PS2 to USB: Found keys
(II) PS2 to USB: Configuring as mouse
(II) PS2 to USB: Configuring as keyboard
(**) PS2 to USB: YAxisMapping: buttons 4 and 5
(**) PS2 to USB: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "PS2 to USB" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) PS2 to USB: initialized for relative axes.
[COLOR="DarkRed"](WW) PS2 to USB: ignoring absolute axes.[/COLOR]
(II) config/udev: Adding input device PS2 to USB (/dev/input/mouse1)
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
(II) intel(0): EDID vendor "SHP", prod id 4092
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1400x1050"x0.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 +hsync +vsync (65.3 kHz)
(II) intel(0): Modeline "1360x768"x0.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) intel(0): Modeline "1400x1050"x0.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): EDID vendor "SHP", prod id 4092
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1400x1050"x0.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 +hsync +vsync (65.3 kHz)
(II) intel(0): Modeline "1360x768"x0.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) intel(0): Modeline "1400x1050"x0.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): EDID vendor "SHP", prod id 4092
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1400x1050"x0.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 +hsync +vsync (65.3 kHz)
(II) intel(0): Modeline "1360x768"x0.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) intel(0): Modeline "1400x1050"x0.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): EDID vendor "SHP", prod id 4092
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1400x1050"x0.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 +hsync +vsync (65.3 kHz)
(II) intel(0): Modeline "1360x768"x0.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) intel(0): Modeline "1400x1050"x0.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): EDID vendor "SHP", prod id 4092
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1400x1050"x0.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 +hsync +vsync (65.3 kHz)
(II) intel(0): Modeline "1360x768"x0.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) intel(0): Modeline "1400x1050"x0.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): EDID vendor "SHP", prod id 4092
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1400x1050"x0.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 +hsync +vsync (65.3 kHz)
(II) intel(0): Modeline "1360x768"x0.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) intel(0): Modeline "1400x1050"x0.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Allocate new frame buffer 1920x1080 stride 1920
(II) intel(0): EDID vendor "SHP", prod id 4092
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1400x1050"x0.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 +hsync +vsync (65.3 kHz)
(II) intel(0): Modeline "1360x768"x0.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) intel(0): Modeline "1400x1050"x0.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)

```

---

### Post by NightwishFan on 2010-11-19
Interesting, everything looks solid. I can only say next time this happens (crash back to login screen) note the exact time, and peruse "syslog" and "messages" at the proper time. I am unsure what to do if the log keeps moving you. (Select all copy/paste perhaps)

---

### Post by eival on 2010-11-19
okay i think i found it, cause these errors happened in close proximity and around the time i posted this thread,
```

Nov 19 10:40:38 marcus-desktop pulseaudio[20004]: main.c: Failed to acquire autospawn lock
Nov 19 10:40:43 marcus-desktop pulseaudio[20006]: core-util.c: Home directory /home/marcus not ours.
Nov 19 10:40:43 marcus-desktop pulseaudio[20006]: lock-autospawn.c: Cannot access autospawn lock.
Nov 19 10:40:43 marcus-desktop pulseaudio[20006]: main.c: Failed to acquire autospawn lock
Nov 19 10:40:47 marcus-desktop kernel: [97071.599826] [drm:i915_gem_do_execbuffer] *ERROR* Failed to pin buffer 2 of 3, total 131940352 bytes: -28
Nov 19 10:40:47 marcus-desktop kernel: [97071.599831] [drm:i915_gem_do_execbuffer] *ERROR* 1083 objects [7 pinned], 192040960 object bytes [82812928 pinned], 82812928/234881024 gtt bytes
Nov 19 10:40:49 marcus-desktop acpid: client connected from 20022[0:0]
Nov 19 10:40:49 marcus-desktop acpid: 1 client rule loaded
Nov 19 10:40:53 marcus-desktop rtkit-daemon[20064]: Sucessfully called chroot.
Nov 19 10:40:53 marcus-desktop rtkit-daemon[20064]: Sucessfully dropped privileges.
Nov 19 10:40:53 marcus-desktop rtkit-daemon[20064]: Sucessfully limited resources.
Nov 19 10:40:53 marcus-desktop rtkit-daemon[20064]: Running.
Nov 19 10:40:53 marcus-desktop rtkit-daemon[20064]: Canary thread running.
Nov 19 10:40:53 marcus-desktop rtkit-daemon[20064]: Watchdog thread running.
Nov 19 10:40:53 marcus-desktop rtkit-daemon[20064]: Sucessfully made thread 20062 of process 20062 (n/a) owned by '114' high priority at nice level -11.
Nov 19 10:40:53 marcus-desktop rtkit-daemon[20064]: Supervising 1 threads of 1 processes of 1 users.
Nov 19 10:40:53 marcus-desktop gdm-simple-greeter[20057]: Gtk-WARNING: /build/buildd/gtk+2.0-2.20.1/gtk/gtkwidget.c:5636: widget not within a GtkWindow
Nov 19 10:40:54 marcus-desktop rtkit-daemon[20064]: Sucessfully made thread 20073 of process 20062 (n/a) owned by '114' RT at priority 5.
Nov 19 10:40:54 marcus-desktop rtkit-daemon[20064]: Supervising 2 threads of 1 processes of 1 users.
Nov 19 10:40:54 marcus-desktop rtkit-daemon[20064]: Sucessfully made thread 20074 of process 20062 (n/a) owned by '114' RT at priority 5.
Nov 19 10:40:54 marcus-desktop rtkit-daemon[20064]: Supervising 3 threads of 1 processes of 1 users.
Nov 19 10:41:00 marcus-desktop gdm-session-worker[20058]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Nov 19 10:41:03 marcus-desktop gdm-session-worker[20098]: WARNING: could not save session and language settings: Failed to create file '/home/marcus/.dmrc.LANOMV': Permission denied
Nov 19 10:41:24 marcus-desktop pulseaudio[20139]: core-util.c: Home directory /home/marcus not ours.
Nov 19 10:41:24 marcus-desktop pulseaudio[20139]: lock-autospawn.c: Cannot access autospawn lock.
Nov 19 10:41:24 marcus-desktop pulseaudio[20139]: main.c: Failed to acquire autospawn lock
Nov 19 10:41:25 marcus-desktop pulseaudio[20142]: core-util.c: Home directory /home/marcus not ours.
Nov 19 10:41:25 marcus-desktop pulseaudio[20142]: lock-autospawn.c: Cannot access autospawn lock.
Nov 19 10:41:25 marcus-desktop pulseaudio[20142]: main.c: Failed to acquire autospawn lock
Nov 19 10:41:25 marcus-desktop gnome-session[20098]: Gtk-CRITICAL: gtk_main_quit: assertion `main_loops != NULL' failed
Nov 19 10:41:26 marcus-desktop pulseaudio[20153]: core-util.c: Home directory /home/marcus not ours.
Nov 19 10:41:26 marcus-desktop pulseaudio[20153]: lock-autospawn.c: Cannot access autospawn lock.
Nov 19 10:41:26 marcus-desktop pulseaudio[20153]: main.c: Failed to acquire autospawn lock
Nov 19 10:41:26 marcus-desktop pulseaudio[20157]: core-util.c: Home directory /home/marcus not ours.
Nov 19 10:41:26 marcus-desktop pulseaudio[20157]: lock-autospawn.c: Cannot access autospawn lock.
Nov 19 10:41:26 marcus-desktop pulseaudio[20157]: main.c: Failed to acquire autospawn lock
Nov 19 10:41:27 marcus-desktop pulseaudio[20172]: core-util.c: Home directory /home/marcus not ours.
Nov 19 10:41:27 marcus-desktop pulseaudio[20172]: lock-autospawn.c: Cannot access autospawn lock.
Nov 19 10:41:27 marcus-desktop pulseaudio[20172]: main.c: Failed to acquire autospawn lock
Nov 19 10:41:32 marcus-desktop pulseaudio[20189]: core-util.c: Home directory /home/marcus not ours.
Nov 19 10:41:32 marcus-desktop pulseaudio[20189]: lock-autospawn.c: Cannot access autospawn lock.
Nov 19 10:41:32 marcus-desktop pulseaudio[20189]: main.c: Failed to acquire autospawn lock
Nov 19 10:41:37 marcus-desktop gnome-session[20098]: WARNING: Application 'metacity.desktop' failed to register before timeout
Nov 19 10:41:37 marcus-desktop pulseaudio[20192]: core-util.c: Home directory /home/marcus not ours.
Nov 19 10:41:37 marcus-desktop pulseaudio[20192]: lock-autospawn.c: Cannot access autospawn lock.
Nov 19 10:41:37 marcus-desktop pulseaudio[20192]: main.c: Failed to acquire autospawn lock
Nov 19 10:41:42 marcus-desktop pulseaudio[20237]: core-util.c: Home directory /home/marcus not ours.
Nov 19 10:41:42 marcus-desktop pulseaudio[20237]: lock-autospawn.c: Cannot access autospawn lock.
Nov 19 10:41:42 marcus-desktop pulseaudio[20237]: main.c: Failed to acquire autospawn lock
Nov 19 10:41:45 marcus-desktop pulseaudio[20242]: core-util.c: Home directory /home/marcus not ours.
Nov 19 10:41:45 marcus-desktop pulseaudio[20242]: lock-autospawn.c: Cannot access autospawn lock.
Nov 19 10:41:45 marcus-desktop pulseaudio[20242]: main.c: Failed to acquire autospawn lock
Nov 19 10:41:47 marcus-desktop pulseaudio[20262]: core-util.c: Home directory /home/marcus not ours.
Nov 19 10:41:47 marcus-desktop pulseaudio[20262]: lock-autospawn.c: Cannot access autospawn lock.
Nov 19 10:41:47 marcus-desktop pulseaudio[20262]: main.c: Failed to acquire autospawn lock
Nov 19 10:41:52 marcus-desktop pulseaudio[20297]: core-util.c: Home directory /home/marcus not ours.
Nov 19 10:41:52 marcus-desktop pulseaudio[20297]: lock-autospawn.c: Cannot access autospawn lock.
Nov 19 10:41:52 marcus-desktop pulseaudio[20297]: main.c: Failed to acquire autospawn lock
Nov 19 10:41:57 marcus-desktop pulseaudio[20300]: core-util.c: Home directory /home/marcus not ours.
Nov 19 10:41:57 marcus-desktop pulseaudio[20300]: lock-autospawn.c: Cannot access autospawn lock.
Nov 19 10:41:57 marcus-desktop pulseaudio[20300]: main.c: Failed to acquire autospawn lock
Nov 19 10:42:02 marcus-desktop pulseaudio[20302]: core-util.c: Home directory /home/marcus not ours.
Nov 19 10:42:02 marcus-desktop pulseaudio[20302]: lock-autospawn.c: Cannot access autospawn lock.
Nov 19 10:42:02 marcus-desktop pulseaudio[20302]: main.c: Failed to acquire autospawn lock
Nov 19 10:42:07 marcus-desktop pulseaudio[20304]: core-util.c: Home directory /home/marcus not ours.
Nov 19 10:42:07 marcus-desktop pulseaudio[20304]: lock-autospawn.c: Cannot access autospawn lock.
Nov 19 10:42:07 marcus-desktop pulseaudio[20304]: main.c: Failed to acquire autospawn lock
Nov 19 10:42:12 marcus-desktop pulseaudio[20307]: core-util.c: Home directory /home/marcus not ours.
Nov 19 10:42:12 marcus-desktop pulseaudio[20307]: lock-autospawn.c: Cannot access autospawn lock.
Nov 19 10:42:12 marcus-desktop pulseaudio[20307]: main.c: Failed to acquire autospawn lock
Nov 19 10:42:17 marcus-desktop pulseaudio[20309]: core-util.c: Home directory /home/marcus not ours.
Nov 19 10:42:17 marcus-desktop pulseaudio[20309]: lock-autospawn.c: Cannot access autospawn lock.
Nov 19 10:42:17 marcus-desktop pulseaudio[20309]: main.c: Failed to acquire autospawn lock
Nov 19 10:42:22 marcus-desktop pulseaudio[20311]: core-util.c: Home directory /home/marcus not ours.
Nov 19 10:42:22 marcus-desktop pulseaudio[20311]: lock-autospawn.c: Cannot access autospawn lock.
Nov 19 10:42:22 marcus-desktop pulseaudio[20311]: main.c: Failed to acquire autospawn lock
Nov 19 10:42:27 marcus-desktop pulseaudio[20313]: core-util.c: Home directory /home/marcus not ours.
Nov 19 10:42:27 marcus-desktop pulseaudio[20313]: lock-autospawn.c: Cannot access autospawn lock.
Nov 19 10:42:27 marcus-desktop pulseaudio[20313]: main.c: Failed to acquire autospawn lock
Nov 19 10:42:32 marcus-desktop pulseaudio[20315]: core-util.c: Home directory /home/marcus not ours.
Nov 19 10:42:32 marcus-desktop pulseaudio[20315]: lock-autospawn.c: Cannot access autospawn lock.
Nov 19 10:42:32 marcus-desktop pulseaudio[20315]: main.c: Failed to acquire autospawn lock
Nov 19 10:42:37 marcus-desktop pulseaudio[20322]: core-util.c: Home directory /home/marcus not ours.
Nov 19 10:42:37 marcus-desktop pulseaudio[20322]: lock-autospawn.c: Cannot access autospawn lock.
Nov 19 10:42:37 marcus-desktop pulseaudio[20322]: main.c: Failed to acquire autospawn lock
Nov 19 10:42:40 marcus-desktop AptDaemon: INFO: Initializing daemon
Nov 19 10:42:42 marcus-desktop pulseaudio[20336]: core-util.c: Home directory /home/marcus not ours.
Nov 19 10:42:42 marcus-desktop pulseaudio[20336]: lock-autospawn.c: Cannot access autospawn lock.
Nov 19 10:42:42 marcus-desktop pulseaudio[20336]: main.c: Failed to acquire autospawn lock
Nov 19 10:42:47 marcus-desktop pulseaudio[20338]: core-util.c: Home directory /home/marcus not ours.
Nov 19 10:42:47 marcus-desktop pulseaudio[20338]: lock-autospawn.c: Cannot access autospawn lock.
Nov 19 10:42:47 marcus-desktop pulseaudio[20338]: main.c: Failed to acquire autospawn lock
Nov 19 10:42:52 marcus-desktop pulseaudio[20341]: core-util.c: Home directory /home/marcus not ours.
Nov 19 10:42:52 marcus-desktop pulseaudio[20341]: lock-autospawn.c: Cannot access autospawn lock.
Nov 19 10:42:52 marcus-desktop pulseaudio[20341]: main.c: Failed to acquire autospawn lock
Nov 19 10:42:57 marcus-desktop pulseaudio[20343]: core-util.c: Home directory /home/marcus not ours.
Nov 19 10:42:57 marcus-desktop pulseaudio[20343]: lock-autospawn.c: Cannot access autospawn lock.
Nov 19 10:42:57 marcus-desktop pulseaudio[20343]: main.c: Failed to acquire autospawn lock
Nov 19 10:43:02 marcus-desktop pulseaudio[20345]: core-util.c: Home directory /home/marcus not ours.
Nov 19 10:43:02 marcus-desktop pulseaudio[20345]: lock-autospawn.c: Cannot access autospawn lock.
Nov 19 10:43:02 marcus-desktop pulseaudio[20345]: main.c: Failed to acquire autospawn lock
Nov 19 10:43:05 marcus-desktop kernel: [97209.970430] [drm:i915_gem_do_execbuffer] *ERROR* Failed to pin buffer 2 of 3, total 131940352 bytes: -28
Nov 19 10:43:05 marcus-desktop kernel: [97209.970436] [drm:i915_gem_do_execbuffer] *ERROR* 970 objects [7 pinned], 181141504 object bytes [82812928 pinned], 82812928/234881024 gtt bytes
Nov 19 10:43:06 marcus-desktop acpid: client 20022[0:0] has disconnected
Nov 19 10:43:06 marcus-desktop acpid: client connected from 20362[0:0]
Nov 19 10:43:06 marcus-desktop acpid: 1 client rule loaded
Nov 19 10:43:09 marcus-desktop rtkit-daemon[20064]: Sucessfully made thread 20403 of process 20403 (n/a) owned by '114' high priority at nice level -11.
Nov 19 10:43:09 marcus-desktop rtkit-daemon[20064]: Supervising 1 threads of 1 processes of 1 users.
Nov 19 10:43:09 marcus-desktop gdm-simple-greeter[20398]: Gtk-WARNING: /build/buildd/gtk+2.0-2.20.1/gtk/gtkwidget.c:5636: widget not within a GtkWindow
Nov 19 10:43:09 marcus-desktop rtkit-daemon[20064]: Sucessfully made thread 20410 of process 20403 (n/a) owned by '114' RT at priority 5.
Nov 19 10:43:09 marcus-desktop rtkit-daemon[20064]: Supervising 2 threads of 1 processes of 1 users.
Nov 19 10:43:09 marcus-desktop rtkit-daemon[20064]: Sucessfully made thread 20411 of process 20403 (n/a) owned by '114' RT at priority 5.
Nov 19 10:43:09 marcus-desktop rtkit-daemon[20064]: Supervising 3 threads of 1 processes of 1 users.
Nov 19 10:43:13 marcus-desktop gdm-session-worker[20399]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Nov 19 10:43:36 marcus-desktop pulseaudio[20475]: core-util.c: Home directory /home/marcus not ours.
Nov 19 10:43:36 marcus-desktop pulseaudio[20475]: lock-autospawn.c: Cannot access autospawn lock.
Nov 19 10:43:36 marcus-desktop pulseaudio[20475]: main.c: Failed to acquire autospawn lock
Nov 19 10:43:37 marcus-desktop pulseaudio[20478]: core-util.c: Home directory /home/marcus not ours.
Nov 19 10:43:37 marcus-desktop pulseaudio[20478]: lock-autospawn.c: Cannot access autospawn lock.
Nov 19 10:43:37 marcus-desktop pulseaudio[20478]: main.c: Failed to acquire autospawn lock
Nov 19 10:43:37 marcus-desktop gnome-session[20434]: Gtk-CRITICAL: gtk_main_quit: assertion `main_loops != NULL' failed
Nov 19 10:43:37 marcus-desktop pulseaudio[20489]: core-util.c: Home directory /home/marcus not ours.
Nov 19 10:43:37 marcus-desktop pulseaudio[20489]: lock-autospawn.c: Cannot access autospawn lock.
Nov 19 10:43:37 marcus-desktop pulseaudio[20489]: main.c: Failed to acquire autospawn lock
Nov 19 10:43:37 marcus-desktop pulseaudio[20493]: core-util.c: Home directory /home/marcus not ours.
Nov 19 10:43:37 marcus-desktop pulseaudio[20493]: lock-autospawn.c: Cannot access autospawn lock.
Nov 19 10:43:37 marcus-desktop pulseaudio[20493]: main.c: Failed to acquire autospawn lock
Nov 19 10:43:38 marcus-desktop pulseaudio[20508]: core-util.c: Home directory /home/marcus not ours.
Nov 19 10:43:38 marcus-desktop pulseaudio[20508]: lock-autospawn.c: Cannot access autospawn lock.
Nov 19 10:43:38 marcus-desktop pulseaudio[20508]: main.c: Failed to acquire autospawn lock
Nov 19 10:43:44 marcus-desktop pulseaudio[20528]: core-util.c: Home directory /home/marcus not ours.
Nov 19 10:43:44 marcus-desktop pulseaudio[20528]: lock-autospawn.c: Cannot access autospawn lock.
Nov 19 10:43:44 marcus-desktop pulseaudio[20528]: main.c: Failed to acquire autospawn lock
Nov 19 10:43:49 marcus-desktop gnome-session[20434]: WARNING: Application 'metacity.desktop' failed to register before timeout
Nov 19 10:43:49 marcus-desktop pulseaudio[20532]: core-util.c: Home directory /home/marcus not ours.
Nov 19 10:43:49 marcus-desktop pulseaudio[20532]: lock-autospawn.c: Cannot access autospawn lock.
Nov 19 10:43:49 marcus-desktop pulseaudio[20532]: main.c: Failed to acquire autospawn lock
Nov 19 10:43:54 marcus-desktop pulseaudio[20577]: core-util.c: Home directory /home/marcus not ours.
```


failed to pin buffer seems to the issue

---

### Post by NightwishFan on 2010-11-19
Here is a bug report:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/528432](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/528432)

A forum thread:
[http://ubuntuforums.org/showthread.php?t=1493225](http://ubuntuforums.org/showthread.php?t=1493225)

This seems to be a known issue. You can probably discuss the topic there if you have a launchpad account (or bump the thread here). I am skimming it now to see whats up. I have this exact chip, so I have had similar problems (rarely).

The only fix I know is to update xorg/intel drivers (which is not really a solution to be honest). This might be fixed in 10.10. Unless this happens quite often I advise you stay with 10.04. If you do decide to update/reinstall to 10.10, test using a live cd first for a while to ensure your hardware works and the problem is fixed.

Also, try disabling compiz (desktop effects)

---

### Post by eival on 2010-11-19
yeah i always turn all that extra effects off.

and since this is the LTS i assume they would fix it, once a fix is found right?

---

### Post by NightwishFan on 2010-11-19
If possible in a clean way yes. If it breaks compatibility perhaps not. Later I will check back if I find a simple way to upgrade for you.

---

### Post by eival on 2010-11-19
also another thing that might be worth noting, i think there was a new kernel update yesterday, it could be something to do with that.

cause prior to today this NEVER happened and ive had 10.4 for a few months now.

---

### Post by NightwishFan on 2010-11-19
Do you still have the old kernel in grub? If you have only Ubuntu installed you need to hold shift right after the post screen to see the grub menu. As a workaround and a test you can boot to the old kernel to see if that works.

---

### Post by eival on 2010-11-19
yeah i actually have a dual boot so i see that option everytime.

but this hasent happened again since tahts why its weird

---

### Post by eival on 2012-08-20
here we are 2 years later and this is still happening.

same 10.04 LTS

same computer hardware

stable release versions of Firefox and plugin/addons

i dont understand how they havent figured this out yet.

its a popular dated hardware configuration(3+yo) from a major manufacture (Intel) not some obscure homebuilt hardware config and its the LTS version of the OS

Which means theres nothing new being added to worry about incorporating...just patching up issues found over the last 3 years and this was found almost right after this LTS's lifecycle began

---

### Post by uRock on 2012-08-20
This is a very odd issue. Can you start Firefox with the following command and hopefully the errors causing the problem will show themselves in the output.```
firefox 2> firecrash.txt
```The **2>** in the command tells the system to send all error info to the **firecrash.txt** file which can be found in your home folder after running Firefox until it crashes.

PS, we may be able to get better attention by closing this thread and creating a new one, since it shows up with having so many replies in the parent forum.

---

### Post by pqwoerituytrueiwoq on 2012-08-20
sounds like Xorg is crashing
check [FONT=Courier New]/var/log/Xorg.*.log[/FONT]
what video card you you have
[FONT=Courier New]lspci | grep VGA[/FONT]

---

