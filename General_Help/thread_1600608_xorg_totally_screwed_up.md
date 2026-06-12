---
title: "xorg totally screwed up"
date: 2010-10-19
forum: General Help
---

### Post by sonicb00m on 2010-10-19
I plugged in a second monitor to my new Meerkat installation and xorg stopped working.

When I took the monitor away it still wouldn't work, so I tried entering with safe graphics and that wouldn't work.

I uninstalled xorg and reinstalled and ran the dpkg-reconfigure xserver-xorg but still no luck.

I have tried reverting the vesa driver but it still won't work. The screen flashes like it's trying but just gives up.

I don't know what to do now except reinstall the partition.

---

### Post by sonicb00m on 2010-10-20
This forum is always like a lottery when hoping for a reply.

---

### Post by realzippy on 2010-10-20
> **sonicb00m said:**
> This forum is always like a lottery when hoping for a reply.

....-since you are not that new in the forum,you might have noticed that
giving some information (e.g. graphics card,driver,Xorg.log file) increases
amount of replies drastically.
So?

---

### Post by sonicb00m on 2010-10-20
Yeah, it was quicker to reinstall really.

The reason I didn't write the xorg config was because it's so minimalistic and has barely any information in it that it seems less relevant.

I was hoping there would have been a solution to just do whatever Ubuntu does when it installs the system from scratch and just get everything reset to absolute basics. If it can do that from the install alone there must be a similar process one can follow manually?

---

### Post by realzippy on 2010-10-21
...did not want your xorg.conf file.,.wanted video driver and Xorg.0.log.
Anyway,if issue solved by reinstalling,please mark this thread as solved.

---

### Post by sonicb00m on 2010-10-24
Nvidia card and was using the proprietary drivers.

The log might be a bit messy now since i tried various changes to try and fix it. Why is not possible to get Ubuntu to totally reconfigure it like it would on a fresh install? I would have been happy with the open driver just to get the desktop back working. I couldn't get any driver working in the end...not even the vesa.


```
[    15.204] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    15.204] X Protocol Version 11, Revision 0
[    15.204] Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
[    15.204] Current Operating System: Linux main-pc 2.6.35-22-generic #34-Ubuntu SMP Sun Oct 10 09:26:05 UTC 2010 x86_64
[    15.204] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=13b78382-aeec-40df-8fa7-cfeed55a2c40 ro quiet splash
[    15.204] Build Date: 16 September 2010  06:18:41PM
[    15.204] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    15.204] Current version of pixman: 0.18.4
[    15.204]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    15.204] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    15.204] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Oct 19 13:10:22 2010
[    15.204] (==) Using config file: "/etc/X11/xorg.conf"
[    15.204] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    15.204] (==) No Layout section.  Using the first Screen section.
[    15.204] (**) |-->Screen "Default Screen" (0)
[    15.204] (**) |   |-->Monitor "<default monitor>"
[    15.204] (==) No device specified for screen "Default Screen".
    Using the first device section listed.
[    15.204] (**) |   |-->Device "Default Device"
[    15.204] (==) No monitor specified for screen "Default Screen".
    Using a default monitor configuration.
[    15.204] (==) Automatically adding devices
[    15.205] (==) Automatically enabling devices
[    15.205] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    15.205]     Entry deleted from font path.
[    15.205] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    15.205] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    15.205] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    15.205] (II) Loader magic: 0x7d0200
[    15.205] (II) Module ABI versions:
[    15.205]     X.Org ANSI C Emulation: 0.4
[    15.205]     X.Org Video Driver: 8.0
[    15.205]     X.Org XInput driver : 11.0
[    15.205]     X.Org Server Extension : 4.0
[    15.205] (--) PCI:*(0:1:0:0) 10de:0ca3:10b0:0401 rev 162, Mem @ 0xfd000000/16777216, 0xd0000000/268435456, 0xce000000/33554432, I/O @ 0x0000dc00/128, BIOS @ 0x????????/524288
[    15.205] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    15.205] (II) "extmod" will be loaded by default.
[    15.205] (II) "dbe" will be loaded by default.
[    15.205] (II) "glx" will be loaded by default.
[    15.205] (II) "record" will be loaded by default.
[    15.205] (II) "dri" will be loaded by default.
[    15.205] (II) "dri2" will be loaded by default.
[    15.205] (II) LoadModule: "extmod"
[    15.211] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    15.211] (II) Module extmod: vendor="X.Org Foundation"
[    15.211]     compiled for 1.9.0, module version = 1.0.0
[    15.211]     Module class: X.Org Server Extension
[    15.211]     ABI class: X.Org Server Extension, version 4.0
[    15.211] (II) Loading extension MIT-SCREEN-SAVER
[    15.211] (II) Loading extension XFree86-VidModeExtension
[    15.211] (II) Loading extension XFree86-DGA
[    15.211] (II) Loading extension DPMS
[    15.211] (II) Loading extension XVideo
[    15.211] (II) Loading extension XVideo-MotionCompensation
[    15.211] (II) Loading extension X-Resource
[    15.211] (II) LoadModule: "dbe"
[    15.211] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    15.211] (II) Module dbe: vendor="X.Org Foundation"
[    15.211]     compiled for 1.9.0, module version = 1.0.0
[    15.211]     Module class: X.Org Server Extension
[    15.211]     ABI class: X.Org Server Extension, version 4.0
[    15.211] (II) Loading extension DOUBLE-BUFFER
[    15.211] (II) LoadModule: "glx"
[    15.211] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    15.220] (II) Module glx: vendor="NVIDIA Corporation"
[    15.220]     compiled for 4.0.2, module version = 1.0.0
[    15.220]     Module class: X.Org Server Extension
[    15.220] (II) NVIDIA GLX Module  260.19.06  Mon Sep 13 04:54:41 PDT 2010
[    15.220] (II) Loading extension GLX
[    15.220] (II) LoadModule: "record"
[    15.220] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    15.220] (II) Module record: vendor="X.Org Foundation"
[    15.220]     compiled for 1.9.0, module version = 1.13.0
[    15.220]     Module class: X.Org Server Extension
[    15.220]     ABI class: X.Org Server Extension, version 4.0
[    15.220] (II) Loading extension RECORD
[    15.220] (II) LoadModule: "dri"
[    15.221] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    15.221] (II) Module dri: vendor="X.Org Foundation"
[    15.221]     compiled for 1.9.0, module version = 1.0.0
[    15.221]     ABI class: X.Org Server Extension, version 4.0
[    15.221] (II) Loading extension XFree86-DRI
[    15.221] (II) LoadModule: "dri2"
[    15.223] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    15.223] (II) Module dri2: vendor="X.Org Foundation"
[    15.223]     compiled for 1.9.0, module version = 1.2.0
[    15.223]     ABI class: X.Org Server Extension, version 4.0
[    15.223] (II) Loading extension DRI2
[    15.223] (II) LoadModule: "vesa"
[    15.223] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    15.270] (II) Module vesa: vendor="X.Org Foundation"
[    15.270]     compiled for 1.8.99.905, module version = 2.3.0
[    15.270]     Module class: X.Org Video Driver
[    15.270]     ABI class: X.Org Video Driver, version 8.0
[    15.270] (II) VESA: driver for VESA chipsets: vesa
[    15.270] (++) using VT number 7

[    15.272] (II) Loading sub module "vbe"
[    15.272] (II) LoadModule: "vbe"
[    15.272] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    15.341] (II) Module vbe: vendor="X.Org Foundation"
[    15.341]     compiled for 1.9.0, module version = 1.1.0
[    15.341]     ABI class: X.Org Video Driver, version 8.0
[    15.341] (II) Loading sub module "int10"
[    15.341] (II) LoadModule: "int10"
[    15.341] (II) Loading /usr/lib/xorg/modules/libint10.so
[    15.349] (II) Module int10: vendor="X.Org Foundation"
[    15.349]     compiled for 1.9.0, module version = 1.0.0
[    15.349]     ABI class: X.Org Video Driver, version 8.0
[    15.349] (II) VESA(0): initializing int10
[    15.349] (II) VESA(0): Bad V_BIOS checksum
[    15.349] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    15.395] (II) VESA(0): VESA BIOS detected
[    15.395] (II) VESA(0): VESA VBE Version 3.0
[    15.395] (II) VESA(0): VESA VBE Total Mem: 14336 kB
[    15.395] (II) VESA(0): VESA VBE OEM: NVIDIA
[    15.395] (II) VESA(0): VESA VBE OEM Software Rev: 112.21
[    15.395] (II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
[    15.395] (II) VESA(0): VESA VBE OEM Product: BIOS-P/N@N5899
[    15.395] (II) VESA(0): VESA VBE OEM Product Rev: GW-CLK@èIèIg
[    15.471] (II) VESA(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
[    15.471] (**) VESA(0): Depth 24, (--) framebuffer bpp 32
[    15.471] (==) VESA(0): RGB weight 888
[    15.471] (==) VESA(0): Default visual is TrueColor
[    15.471] (==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
[    15.471] (II) Loading sub module "ddc"
[    15.471] (II) LoadModule: "ddc"
[    15.471] (II) Module "ddc" already built-in
[    15.473] (II) VESA(0): VESA VBE DDC supported
[    15.473] (II) VESA(0): VESA VBE DDC Level 2
[    15.473] (II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
[    15.527] (II) VESA(0): VESA VBE DDC read successfully
[    15.527] (II) VESA(0): Manufacturer: BNQ  Model: 7842  Serial#: 21573
[    15.527] (II) VESA(0): Year: 2010  Week: 12
[    15.527] (II) VESA(0): EDID Version: 1.3
[    15.527] (II) VESA(0): Digital Display Input
[    15.527] (II) VESA(0): Max Image Size [cm]: horiz.: 53  vert.: 29
[    15.527] (II) VESA(0): Gamma: 2.20
[    15.527] (II) VESA(0): DPMS capabilities: Off
[    15.527] (II) VESA(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    15.527] (II) VESA(0): Default color space is primary color space
[    15.527] (II) VESA(0): First detailed timing is preferred mode
[    15.527] (II) VESA(0): redX: 0.649 redY: 0.338   greenX: 0.289 greenY: 0.609
[    15.527] (II) VESA(0): blueX: 0.146 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
[    15.527] (II) VESA(0): Supported established timings:
[    15.527] (II) VESA(0): 720x400@70Hz
[    15.527] (II) VESA(0): 640x480@60Hz
[    15.527] (II) VESA(0): 640x480@75Hz
[    15.527] (II) VESA(0): 800x600@60Hz
[    15.527] (II) VESA(0): 800x600@75Hz
[    15.527] (II) VESA(0): 832x624@75Hz
[    15.527] (II) VESA(0): 1024x768@60Hz
[    15.527] (II) VESA(0): 1024x768@75Hz
[    15.527] (II) VESA(0): 1280x1024@75Hz
[    15.527] (II) VESA(0): 1152x864@75Hz
[    15.527] (II) VESA(0): Manufacturer's mask: 0
[    15.527] (II) VESA(0): Supported standard timings:
[    15.527] (II) VESA(0): #0: hsize: 1152  vsize 720  refresh: 60  vid: 113
[    15.527] (II) VESA(0): #1: hsize: 1280  vsize 720  refresh: 60  vid: 49281
[    15.527] (II) VESA(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    15.527] (II) VESA(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    15.527] (II) VESA(0): #4: hsize: 1600  vsize 900  refresh: 60  vid: 49321
[    15.527] (II) VESA(0): #5: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    15.527] (II) VESA(0): #6: hsize: 1920  vsize 1080  refresh: 60  vid: 49361
[    15.527] (II) VESA(0): Supported detailed timing:
[    15.527] (II) VESA(0): clock: 148.5 MHz   Image Size:  477 x 268 mm
[    15.527] (II) VESA(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    15.527] (II) VESA(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    15.527] (II) VESA(0): Serial No: K3A03445SL000
[    15.527] (II) VESA(0): Ranges: V min: 50 V max: 76 Hz, H min: 24 H max: 83 kHz, PixClock max 175 MHz
[    15.527] (II) VESA(0): Monitor name: BenQ G2420HDB
[    15.527] (II) VESA(0): EDID (in hex):
[    15.527] (II) VESA(0):     00ffffffffffff0009d1427845540000
[    15.527] (II) VESA(0):     0c14010380351d782e6085a6564a9c25
[    15.527] (II) VESA(0):     125054a56b80710081c081408180a9c0
[    15.527] (II) VESA(0):     b300d1c00101023a801871382d40582c
[    15.527] (II) VESA(0):     4500dd0c1100001e000000ff004b3341
[    15.527] (II) VESA(0):     3033343435534c303030000000fd0032
[    15.527] (II) VESA(0):     4c185311000a202020202020000000fc
[    15.527] (II) VESA(0):     0042656e512047323432304844420010
[    15.527] (II) VESA(0): EDID vendor "BNQ", prod id 30786
[    15.527] (II) VESA(0): Using EDID range info for horizontal sync
[    15.527] (II) VESA(0): Using EDID range info for vertical refresh
[    15.527] (II) VESA(0): Printing DDC gathered Modelines:
[    15.527] (II) VESA(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    15.527] (II) VESA(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    15.527] (II) VESA(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    15.527] (II) VESA(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    15.527] (II) VESA(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    15.527] (II) VESA(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    15.527] (II) VESA(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    15.527] (II) VESA(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    15.528] (II) VESA(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    15.528] (II) VESA(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    15.528] (II) VESA(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    15.528] (II) VESA(0): Modeline "1152x720"x60.0   67.32  1152 1208 1328 1504  720 721 724 746 -hsync +vsync (44.8 kHz)
[    15.528] (II) VESA(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
[    15.528] (II) VESA(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    15.528] (II) VESA(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    15.528] (II) VESA(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz)
[    15.528] (II) VESA(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    15.528] (II) VESA(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz)
[    15.528] (II) VESA(0): Searching for matching VESA mode(s):
[    15.529] Mode: 100 (640x400)
[    15.529]     ModeAttributes: 0x3bf
[    15.529]     WinAAttributes: 0x7
[    15.529]     WinBAttributes: 0x0
[    15.529]     WinGranularity: 64
[    15.529]     WinSize: 64
[    15.529]     WinASegment: 0xa000
[    15.529]     WinBSegment: 0x0
[    15.529]     WinFuncPtr: 0xc0006161
[    15.529]     BytesPerScanline: 640
[    15.529]     XResolution: 640
[    15.529]     YResolution: 400
[    15.529]     XCharSize: 8
[    15.529]     YCharSize: 16
[    15.529]     NumberOfPlanes: 1
[    15.529]     BitsPerPixel: 8
[    15.529]     NumberOfBanks: 1
[    15.529]     MemoryModel: 4
[    15.529]     BankSize: 0
[    15.529]     NumberOfImages: 14
[    15.529]     RedMaskSize: 0
[    15.529]     RedFieldPosition: 0
[    15.529]     GreenMaskSize: 0
[    15.529]     GreenFieldPosition: 0
[    15.529]     BlueMaskSize: 0
[    15.529]     BlueFieldPosition: 0
[    15.529]     RsvdMaskSize: 0
[    15.529]     RsvdFieldPosition: 0
[    15.529]     DirectColorModeInfo: 0
[    15.529]     PhysBasePtr: 0xcf000000
[    15.529]     LinBytesPerScanLine: 640
[    15.529]     BnkNumberOfImagePages: 14
[    15.529]     LinNumberOfImagePages: 14
[    15.529]     LinRedMaskSize: 0
[    15.529]     LinRedFieldPosition: 0
[    15.529]     LinGreenMaskSize: 0
[    15.529]     LinGreenFieldPosition: 0
[    15.529]     LinBlueMaskSize: 0
[    15.529]     LinBlueFieldPosition: 0
[    15.529]     LinRsvdMaskSize: 0
[    15.529]     LinRsvdFieldPosition: 0
[    15.529]     MaxPixelClock: 229500000
[    15.530] Mode: 101 (640x480)
[    15.530]     ModeAttributes: 0x3bf
[    15.530]     WinAAttributes: 0x7
[    15.530]     WinBAttributes: 0x0
[    15.530]     WinGranularity: 64
[    15.530]     WinSize: 64
[    15.530]     WinASegment: 0xa000
[    15.530]     WinBSegment: 0x0
[    15.530]     WinFuncPtr: 0xc0006161
[    15.530]     BytesPerScanline: 640
[    15.530]     XResolution: 640
[    15.530]     YResolution: 480
[    15.530]     XCharSize: 8
[    15.530]     YCharSize: 16
[    15.530]     NumberOfPlanes: 1
[    15.530]     BitsPerPixel: 8
[    15.530]     NumberOfBanks: 1
[    15.530]     MemoryModel: 4
[    15.530]     BankSize: 0
[    15.530]     NumberOfImages: 10
[    15.530]     RedMaskSize: 0
[    15.530]     RedFieldPosition: 0
[    15.530]     GreenMaskSize: 0
[    15.530]     GreenFieldPosition: 0
[    15.530]     BlueMaskSize: 0
[    15.530]     BlueFieldPosition: 0
[    15.530]     RsvdMaskSize: 0
[    15.530]     RsvdFieldPosition: 0
[    15.530]     DirectColorModeInfo: 0
[    15.530]     PhysBasePtr: 0xcf000000
[    15.530]     LinBytesPerScanLine: 640
[    15.530]     BnkNumberOfImagePages: 10
[    15.530]     LinNumberOfImagePages: 10
[    15.530]     LinRedMaskSize: 0
[    15.530]     LinRedFieldPosition: 0
[    15.530]     LinGreenMaskSize: 0
[    15.530]     LinGreenFieldPosition: 0
[    15.530]     LinBlueMaskSize: 0
[    15.530]     LinBlueFieldPosition: 0
[    15.530]     LinRsvdMaskSize: 0
[    15.530]     LinRsvdFieldPosition: 0
[    15.530]     MaxPixelClock: 229500000
[    15.531] Mode: 102 (800x600)
[    15.531]     ModeAttributes: 0x33f
[    15.531]     WinAAttributes: 0x7
[    15.531]     WinBAttributes: 0x0
[    15.531]     WinGranularity: 64
[    15.531]     WinSize: 64
[    15.531]     WinASegment: 0xa000
[    15.531]     WinBSegment: 0x0
[    15.531]     WinFuncPtr: 0xc0006161
[    15.531]     BytesPerScanline: 100
[    15.531]     XResolution: 800
[    15.531]     YResolution: 600
[    15.531]     XCharSize: 8
[    15.531]     YCharSize: 16
[    15.531]     NumberOfPlanes: 4
[    15.531]     BitsPerPixel: 4
[    15.531]     NumberOfBanks: 1
[    15.531]     MemoryModel: 3
[    15.531]     BankSize: 0
[    15.531]     NumberOfImages: 2
[    15.531]     RedMaskSize: 0
[    15.531]     RedFieldPosition: 0
[    15.531]     GreenMaskSize: 0
[    15.531]     GreenFieldPosition: 0
[    15.531]     BlueMaskSize: 0
[    15.531]     BlueFieldPosition: 0
[    15.531]     RsvdMaskSize: 0
[    15.531]     RsvdFieldPosition: 0
[    15.531]     DirectColorModeInfo: 0
[    15.531]     PhysBasePtr: 0x0
[    15.531]     LinBytesPerScanLine: 100
[    15.531]     BnkNumberOfImagePages: 2
[    15.531]     LinNumberOfImagePages: 2
[    15.531]     LinRedMaskSize: 0
[    15.531]     LinRedFieldPosition: 0
[    15.531]     LinGreenMaskSize: 0
[    15.531]     LinGreenFieldPosition: 0
[    15.531]     LinBlueMaskSize: 0
[    15.531]     LinBlueFieldPosition: 0
[    15.531]     LinRsvdMaskSize: 0
[    15.531]     LinRsvdFieldPosition: 0
[    15.531]     MaxPixelClock: 108500000
[    15.532] Mode: 103 (800x600)
[    15.532]     ModeAttributes: 0x3bf
[    15.532]     WinAAttributes: 0x7
[    15.532]     WinBAttributes: 0x0
[    15.532]     WinGranularity: 64
[    15.532]     WinSize: 64
[    15.532]     WinASegment: 0xa000
[    15.532]     WinBSegment: 0x0
[    15.532]     WinFuncPtr: 0xc0006161
[    15.532]     BytesPerScanline: 800
[    15.532]     XResolution: 800
[    15.532]     YResolution: 600
[    15.532]     XCharSize: 8
[    15.532]     YCharSize: 16
[    15.532]     NumberOfPlanes: 1
[    15.532]     BitsPerPixel: 8
[    15.532]     NumberOfBanks: 1
[    15.532]     MemoryModel: 4
[    15.532]     BankSize: 0
[    15.532]     NumberOfImages: 6
[    15.532]     RedMaskSize: 0
[    15.532]     RedFieldPosition: 0
[    15.532]     GreenMaskSize: 0
[    15.532]     GreenFieldPosition: 0
[    15.532]     BlueMaskSize: 0
[    15.532]     BlueFieldPosition: 0
[    15.532]     RsvdMaskSize: 0
[    15.532]     RsvdFieldPosition: 0
[    15.532]     DirectColorModeInfo: 0
[    15.533]     PhysBasePtr: 0xcf000000
[    15.533]     LinBytesPerScanLine: 800
[    15.533]     BnkNumberOfImagePages: 6
[    15.533]     LinNumberOfImagePages: 6
[    15.533]     LinRedMaskSize: 0
[    15.533]     LinRedFieldPosition: 0
[    15.533]     LinGreenMaskSize: 0
[    15.533]     LinGreenFieldPosition: 0
[    15.533]     LinBlueMaskSize: 0
[    15.533]     LinBlueFieldPosition: 0
[    15.533]     LinRsvdMaskSize: 0
[    15.533]     LinRsvdFieldPosition: 0
[    15.533]     MaxPixelClock: 229500000
[    15.534] Mode: 104 (1024x768)
[    15.534]     ModeAttributes: 0x33f
[    15.534]     WinAAttributes: 0x7
[    15.534]     WinBAttributes: 0x0
[    15.534]     WinGranularity: 64
[    15.534]     WinSize: 64
[    15.534]     WinASegment: 0xa000
[    15.534]     WinBSegment: 0x0
[    15.534]     WinFuncPtr: 0xc0006161
[    15.534]     BytesPerScanline: 128
[    15.534]     XResolution: 1024
[    15.534]     YResolution: 768
[    15.534]     XCharSize: 8
[    15.534]     YCharSize: 16
[    15.534]     NumberOfPlanes: 4
[    15.534]     BitsPerPixel: 4
[    15.534]     NumberOfBanks: 1
[    15.534]     MemoryModel: 3
[    15.534]     BankSize: 0
[    15.534]     NumberOfImages: 1
[    15.534]     RedMaskSize: 0
[    15.534]     RedFieldPosition: 0
[    15.534]     GreenMaskSize: 0
[    15.534]     GreenFieldPosition: 0
[    15.534]     BlueMaskSize: 0
[    15.534]     BlueFieldPosition: 0
[    15.534]     RsvdMaskSize: 0
[    15.534]     RsvdFieldPosition: 0
[    15.534]     DirectColorModeInfo: 0
[    15.534]     PhysBasePtr: 0x0
[    15.534]     LinBytesPerScanLine: 128
[    15.534]     BnkNumberOfImagePages: 1
[    15.534]     LinNumberOfImagePages: 1
[    15.534]     LinRedMaskSize: 0
[    15.534]     LinRedFieldPosition: 0
[    15.534]     LinGreenMaskSize: 0
[    15.534]     LinGreenFieldPosition: 0
[    15.534]     LinBlueMaskSize: 0
[    15.534]     LinBlueFieldPosition: 0
[    15.534]     LinRsvdMaskSize: 0
[    15.534]     LinRsvdFieldPosition: 0
[    15.534]     MaxPixelClock: 108500000
[    15.535] Mode: 105 (1024x768)
[    15.535]     ModeAttributes: 0x3bf
[    15.535]     WinAAttributes: 0x7
[    15.535]     WinBAttributes: 0x0
[    15.535]     WinGranularity: 64
[    15.535]     WinSize: 64
[    15.535]     WinASegment: 0xa000
[    15.535]     WinBSegment: 0x0
[    15.535]     WinFuncPtr: 0xc0006161
[    15.535]     BytesPerScanline: 1024
[    15.535]     XResolution: 1024
[    15.535]     YResolution: 768
[    15.535]     XCharSize: 8
[    15.535]     YCharSize: 16
[    15.535]     NumberOfPlanes: 1
[    15.535]     BitsPerPixel: 8
[    15.535]     NumberOfBanks: 1
[    15.535]     MemoryModel: 4
[    15.535]     BankSize: 0
[    15.535]     NumberOfImages: 3
[    15.535]     RedMaskSize: 0
[    15.535]     RedFieldPosition: 0
[    15.535]     GreenMaskSize: 0
[    15.535]     GreenFieldPosition: 0
[    15.535]     BlueMaskSize: 0
[    15.535]     BlueFieldPosition: 0
[    15.535]     RsvdMaskSize: 0
[    15.535]     RsvdFieldPosition: 0
[    15.535]     DirectColorModeInfo: 0
[    15.535]     PhysBasePtr: 0xcf000000
[    15.535]     LinBytesPerScanLine: 1024
[    15.535]     BnkNumberOfImagePages: 3
[    15.535]     LinNumberOfImagePages: 3
[    15.535]     LinRedMaskSize: 0
[    15.535]     LinRedFieldPosition: 0
[    15.535]     LinGreenMaskSize: 0
[    15.535]     LinGreenFieldPosition: 0
[    15.535]     LinBlueMaskSize: 0
[    15.535]     LinBlueFieldPosition: 0
[    15.535]     LinRsvdMaskSize: 0
[    15.535]     LinRsvdFieldPosition: 0
[    15.535]     MaxPixelClock: 229500000
[    15.536] Mode: 106 (1280x1024)
[    15.536]     ModeAttributes: 0x33f
[    15.536]     WinAAttributes: 0x7
[    15.536]     WinBAttributes: 0x0
[    15.536]     WinGranularity: 64
[    15.536]     WinSize: 64
[    15.536]     WinASegment: 0xa000
[    15.536]     WinBSegment: 0x0
[    15.536]     WinFuncPtr: 0xc0006161
[    15.536]     BytesPerScanline: 160
[    15.536]     XResolution: 1280
[    15.536]     YResolution: 1024
[    15.536]     XCharSize: 8
[    15.536]     YCharSize: 16
[    15.536]     NumberOfPlanes: 4
[    15.536]     BitsPerPixel: 4
[    15.536]     NumberOfBanks: 1
[    15.536]     MemoryModel: 3
[    15.536]     BankSize: 0
[    15.536]     NumberOfImages: 1
[    15.536]     RedMaskSize: 0
[    15.536]     RedFieldPosition: 0
[    15.536]     GreenMaskSize: 0
[    15.536]     GreenFieldPosition: 0
[    15.536]     BlueMaskSize: 0
[    15.536]     BlueFieldPosition: 0
[    15.536]     RsvdMaskSize: 0
[    15.536]     RsvdFieldPosition: 0
[    15.536]     DirectColorModeInfo: 0
[    15.536]     PhysBasePtr: 0x0
[    15.536]     LinBytesPerScanLine: 160
[    15.536]     BnkNumberOfImagePages: 1
[    15.536]     LinNumberOfImagePages: 1
[    15.536]     LinRedMaskSize: 0
[    15.536]     LinRedFieldPosition: 0
[    15.536]     LinGreenMaskSize: 0
[    15.536]     LinGreenFieldPosition: 0
[    15.536]     LinBlueMaskSize: 0
[    15.536]     LinBlueFieldPosition: 0
[    15.536]     LinRsvdMaskSize: 0
[    15.536]     LinRsvdFieldPosition: 0
[    15.536]     MaxPixelClock: 108500000
[    15.537] Mode: 107 (1280x1024)
[    15.537]     ModeAttributes: 0x3bf
[    15.537]     WinAAttributes: 0x7
[    15.537]     WinBAttributes: 0x0
[    15.537]     WinGranularity: 64
[    15.537]     WinSize: 64
[    15.537]     WinASegment: 0xa000
[    15.537]     WinBSegment: 0x0
[    15.537]     WinFuncPtr: 0xc0006161
[    15.537]     BytesPerScanline: 1280
[    15.537]     XResolution: 1280
[    15.537]     YResolution: 1024
[    15.537]     XCharSize: 8
[    15.537]     YCharSize: 16
[    15.537]     NumberOfPlanes: 1
[    15.537]     BitsPerPixel: 8
[    15.537]     NumberOfBanks: 1
[    15.537]     MemoryModel: 4
[    15.537]     BankSize: 0
[    15.537]     NumberOfImages: 1
[    15.537]     RedMaskSize: 0
[    15.537]     RedFieldPosition: 0
[    15.537]     GreenMaskSize: 0
[    15.537]     GreenFieldPosition: 0
[    15.537]     BlueMaskSize: 0
[    15.537]     BlueFieldPosition: 0
[    15.537]     RsvdMaskSize: 0
[    15.537]     RsvdFieldPosition: 0
[    15.537]     DirectColorModeInfo: 0
[    15.537]     PhysBasePtr: 0xcf000000
[    15.537]     LinBytesPerScanLine: 1280
[    15.537]     BnkNumberOfImagePages: 1
[    15.537]     LinNumberOfImagePages: 1
[    15.537]     LinRedMaskSize: 0
[    15.537]     LinRedFieldPosition: 0
[    15.537]     LinGreenMaskSize: 0
[    15.537]     LinGreenFieldPosition: 0
[    15.537]     LinBlueMaskSize: 0
[    15.537]     LinBlueFieldPosition: 0
[    15.537]     LinRsvdMaskSize: 0
[    15.537]     LinRsvdFieldPosition: 0
[    15.537]     MaxPixelClock: 229500000
[    15.539] Mode: 10e (320x200)
[    15.539]     ModeAttributes: 0x3bf
[    15.539]     WinAAttributes: 0x7
[    15.539]     WinBAttributes: 0x0
[    15.539]     WinGranularity: 64
[    15.539]     WinSize: 64
[    15.539]     WinASegment: 0xa000
[    15.539]     WinBSegment: 0x0
[    15.539]     WinFuncPtr: 0xc0006161
[    15.539]     BytesPerScanline: 640
[    15.539]     XResolution: 320
[    15.539]     YResolution: 200
[    15.539]     XCharSize: 8
[    15.539]     YCharSize: 8
[    15.539]     NumberOfPlanes: 1
[    15.539]     BitsPerPixel: 16
[    15.539]     NumberOfBanks: 1
[    15.539]     MemoryModel: 6
[    15.539]     BankSize: 0
[    15.539]     NumberOfImages: 30
[    15.539]     RedMaskSize: 5
[    15.539]     RedFieldPosition: 11
[    15.539]     GreenMaskSize: 6
[    15.539]     GreenFieldPosition: 5
[    15.539]     BlueMaskSize: 5
[    15.539]     BlueFieldPosition: 0
[    15.539]     RsvdMaskSize: 0
[    15.539]     RsvdFieldPosition: 0
[    15.539]     DirectColorModeInfo: 0
[    15.539]     PhysBasePtr: 0xcf000000
[    15.539]     LinBytesPerScanLine: 640
[    15.539]     BnkNumberOfImagePages: 30
[    15.539]     LinNumberOfImagePages: 30
[    15.539]     LinRedMaskSize: 5
[    15.539]     LinRedFieldPosition: 11
[    15.539]     LinGreenMaskSize: 6
[    15.539]     LinGreenFieldPosition: 5
[    15.539]     LinBlueMaskSize: 5
[    15.539]     LinBlueFieldPosition: 0
[    15.539]     LinRsvdMaskSize: 0
[    15.539]     LinRsvdFieldPosition: 0
[    15.539]     MaxPixelClock: 229500000
[    15.540] *Mode: 10f (320x200)
[    15.540]     ModeAttributes: 0x3bf
[    15.540]     WinAAttributes: 0x7
[    15.540]     WinBAttributes: 0x0
[    15.540]     WinGranularity: 64
[    15.540]     WinSize: 64
[    15.540]     WinASegment: 0xa000
[    15.540]     WinBSegment: 0x0
[    15.540]     WinFuncPtr: 0xc0006161
[    15.540]     BytesPerScanline: 1280
[    15.540]     XResolution: 320
[    15.540]     YResolution: 200
[    15.540]     XCharSize: 8
[    15.540]     YCharSize: 8
[    15.540]     NumberOfPlanes: 1
[    15.540]     BitsPerPixel: 32
[    15.540]     NumberOfBanks: 1
[    15.540]     MemoryModel: 6
[    15.540]     BankSize: 0
[    15.540]     NumberOfImages: 14
[    15.540]     RedMaskSize: 8
[    15.540]     RedFieldPosition: 16
[    15.540]     GreenMaskSize: 8
[    15.540]     GreenFieldPosition: 8
[    15.540]     BlueMaskSize: 8
[    15.540]     BlueFieldPosition: 0
[    15.540]     RsvdMaskSize: 8
[    15.540]     RsvdFieldPosition: 24
[    15.540]     DirectColorModeInfo: 0
[    15.540]     PhysBasePtr: 0xcf000000
[    15.540]     LinBytesPerScanLine: 1280
[    15.540]     BnkNumberOfImagePages: 14
[    15.540]     LinNumberOfImagePages: 14
[    15.540]     LinRedMaskSize: 8
[    15.540]     LinRedFieldPosition: 16
[    15.540]     LinGreenMaskSize: 8
[    15.540]     LinGreenFieldPosition: 8
[    15.540]     LinBlueMaskSize: 8
[    15.540]     LinBlueFieldPosition: 0
[    15.540]     LinRsvdMaskSize: 8
[    15.540]     LinRsvdFieldPosition: 24
[    15.540]     MaxPixelClock: 229500000
[    15.541] Mode: 111 (640x480)
[    15.541]     ModeAttributes: 0x3bf
[    15.541]     WinAAttributes: 0x7
[    15.541]     WinBAttributes: 0x0
[    15.541]     WinGranularity: 64
[    15.541]     WinSize: 64
[    15.541]     WinASegment: 0xa000
[    15.541]     WinBSegment: 0x0
[    15.541]     WinFuncPtr: 0xc0006161
[    15.541]     BytesPerScanline: 1280
[    15.541]     XResolution: 640
[    15.541]     YResolution: 480
[    15.541]     XCharSize: 8
[    15.541]     YCharSize: 16
[    15.541]     NumberOfPlanes: 1
[    15.541]     BitsPerPixel: 16
[    15.541]     NumberOfBanks: 1
[    15.541]     MemoryModel: 6
[    15.541]     BankSize: 0
[    15.541]     NumberOfImages: 4
[    15.541]     RedMaskSize: 5
[    15.541]     RedFieldPosition: 11
[    15.541]     GreenMaskSize: 6
[    15.541]     GreenFieldPosition: 5
[    15.541]     BlueMaskSize: 5
[    15.541]     BlueFieldPosition: 0
[    15.541]     RsvdMaskSize: 0
[    15.541]     RsvdFieldPosition: 0
[    15.541]     DirectColorModeInfo: 0
[    15.541]     PhysBasePtr: 0xcf000000
[    15.541]     LinBytesPerScanLine: 1280
[    15.541]     BnkNumberOfImagePages: 4
[    15.541]     LinNumberOfImagePages: 4
[    15.541]     LinRedMaskSize: 5
[    15.541]     LinRedFieldPosition: 11
[    15.541]     LinGreenMaskSize: 6
[    15.541]     LinGreenFieldPosition: 5
[    15.541]     LinBlueMaskSize: 5
[    15.541]     LinBlueFieldPosition: 0
[    15.541]     LinRsvdMaskSize: 0
[    15.541]     LinRsvdFieldPosition: 0
[    15.541]     MaxPixelClock: 229500000
[    15.542] *Mode: 112 (640x480)
[    15.542]     ModeAttributes: 0x3bf
[    15.542]     WinAAttributes: 0x7
[    15.542]     WinBAttributes: 0x0
[    15.542]     WinGranularity: 64
[    15.542]     WinSize: 64
[    15.542]     WinASegment: 0xa000
[    15.542]     WinBSegment: 0x0
[    15.542]     WinFuncPtr: 0xc0006161
[    15.542]     BytesPerScanline: 2560
[    15.542]     XResolution: 640
[    15.542]     YResolution: 480
[    15.542]     XCharSize: 8
[    15.542]     YCharSize: 16
[    15.542]     NumberOfPlanes: 1
[    15.542]     BitsPerPixel: 32
[    15.542]     NumberOfBanks: 1
[    15.542]     MemoryModel: 6
[    15.542]     BankSize: 0
[    15.542]     NumberOfImages: 1
[    15.542]     RedMaskSize: 8
[    15.542]     RedFieldPosition: 16
[    15.542]     GreenMaskSize: 8
[    15.542]     GreenFieldPosition: 8
[    15.542]     BlueMaskSize: 8
[    15.542]     BlueFieldPosition: 0
[    15.542]     RsvdMaskSize: 8
[    15.542]     RsvdFieldPosition: 24
[    15.542]     DirectColorModeInfo: 0
[    15.542]     PhysBasePtr: 0xcf000000
[    15.542]     LinBytesPerScanLine: 2560
[    15.542]     BnkNumberOfImagePages: 1
[    15.542]     LinNumberOfImagePages: 1
[    15.542]     LinRedMaskSize: 8
[    15.542]     LinRedFieldPosition: 16
[    15.542]     LinGreenMaskSize: 8
[    15.542]     LinGreenFieldPosition: 8
[    15.542]     LinBlueMaskSize: 8
[    15.542]     LinBlueFieldPosition: 0
[    15.542]     LinRsvdMaskSize: 8
[    15.542]     LinRsvdFieldPosition: 24
[    15.542]     MaxPixelClock: 229500000
[    15.543] Mode: 114 (800x600)
[    15.543]     ModeAttributes: 0x3bf
[    15.543]     WinAAttributes: 0x7
[    15.543]     WinBAttributes: 0x0
[    15.543]     WinGranularity: 64
[    15.543]     WinSize: 64
[    15.544]     WinASegment: 0xa000
[    15.544]     WinBSegment: 0x0
[    15.544]     WinFuncPtr: 0xc0006161
[    15.544]     BytesPerScanline: 1600
[    15.544]     XResolution: 800
[    15.544]     YResolution: 600
[    15.544]     XCharSize: 8
[    15.544]     YCharSize: 16
[    15.544]     NumberOfPlanes: 1
[    15.544]     BitsPerPixel: 16
[    15.544]     NumberOfBanks: 1
[    15.544]     MemoryModel: 6
[    15.544]     BankSize: 0
[    15.544]     NumberOfImages: 2
[    15.544]     RedMaskSize: 5
[    15.544]     RedFieldPosition: 11
[    15.544]     GreenMaskSize: 6
[    15.544]     GreenFieldPosition: 5
[    15.544]     BlueMaskSize: 5
[    15.544]     BlueFieldPosition: 0
[    15.544]     RsvdMaskSize: 0
[    15.544]     RsvdFieldPosition: 0
[    15.544]     DirectColorModeInfo: 0
[    15.544]     PhysBasePtr: 0xcf000000
[    15.544]     LinBytesPerScanLine: 1600
[    15.544]     BnkNumberOfImagePages: 2
[    15.544]     LinNumberOfImagePages: 2
[    15.544]     LinRedMaskSize: 5
[    15.544]     LinRedFieldPosition: 11
[    15.544]     LinGreenMaskSize: 6
[    15.544]     LinGreenFieldPosition: 5
[    15.544]     LinBlueMaskSize: 5
[    15.544]     LinBlueFieldPosition: 0
[    15.544]     LinRsvdMaskSize: 0
[    15.544]     LinRsvdFieldPosition: 0
[    15.544]     MaxPixelClock: 229500000
[    15.545] *Mode: 115 (800x600)
[    15.545]     ModeAttributes: 0x3bf
[    15.545]     WinAAttributes: 0x7
[    15.545]     WinBAttributes: 0x0
[    15.545]     WinGranularity: 64
[    15.545]     WinSize: 64
[    15.545]     WinASegment: 0xa000
[    15.545]     WinBSegment: 0x0
[    15.545]     WinFuncPtr: 0xc0006161
[    15.545]     BytesPerScanline: 3200
[    15.545]     XResolution: 800
[    15.545]     YResolution: 600
[    15.545]     XCharSize: 8
[    15.545]     YCharSize: 16
[    15.545]     NumberOfPlanes: 1
[    15.545]     BitsPerPixel: 32
[    15.545]     NumberOfBanks: 1
[    15.545]     MemoryModel: 6
[    15.545]     BankSize: 0
[    15.545]     NumberOfImages: 1
[    15.545]     RedMaskSize: 8
[    15.545]     RedFieldPosition: 16
[    15.545]     GreenMaskSize: 8
[    15.545]     GreenFieldPosition: 8
[    15.545]     BlueMaskSize: 8
[    15.545]     BlueFieldPosition: 0
[    15.545]     RsvdMaskSize: 8
[    15.545]     RsvdFieldPosition: 24
[    15.545]     DirectColorModeInfo: 0
[    15.545]     PhysBasePtr: 0xcf000000
[    15.545]     LinBytesPerScanLine: 3200
[    15.545]     BnkNumberOfImagePages: 1
[    15.545]     LinNumberOfImagePages: 1
[    15.545]     LinRedMaskSize: 8
[    15.545]     LinRedFieldPosition: 16
[    15.545]     LinGreenMaskSize: 8
[    15.545]     LinGreenFieldPosition: 8
[    15.545]     LinBlueMaskSize: 8
[    15.545]     LinBlueFieldPosition: 0
[    15.545]     LinRsvdMaskSize: 8
[    15.545]     LinRsvdFieldPosition: 24
[    15.545]     MaxPixelClock: 229500000
[    15.546] Mode: 117 (1024x768)
[    15.546]     ModeAttributes: 0x3bf
[    15.546]     WinAAttributes: 0x7
[    15.546]     WinBAttributes: 0x0
[    15.546]     WinGranularity: 64
[    15.546]     WinSize: 64
[    15.546]     WinASegment: 0xa000
[    15.546]     WinBSegment: 0x0
[    15.546]     WinFuncPtr: 0xc0006161
[    15.546]     BytesPerScanline: 2048
[    15.546]     XResolution: 1024
[    15.546]     YResolution: 768
[    15.546]     XCharSize: 8
[    15.546]     YCharSize: 16
[    15.546]     NumberOfPlanes: 1
[    15.546]     BitsPerPixel: 16
[    15.546]     NumberOfBanks: 1
[    15.546]     MemoryModel: 6
[    15.546]     BankSize: 0
[    15.546]     NumberOfImages: 1
[    15.546]     RedMaskSize: 5
[    15.546]     RedFieldPosition: 11
[    15.546]     GreenMaskSize: 6
[    15.546]     GreenFieldPosition: 5
[    15.546]     BlueMaskSize: 5
[    15.546]     BlueFieldPosition: 0
[    15.546]     RsvdMaskSize: 0
[    15.546]     RsvdFieldPosition: 0
[    15.546]     DirectColorModeInfo: 0
[    15.546]     PhysBasePtr: 0xcf000000
[    15.546]     LinBytesPerScanLine: 2048
[    15.546]     BnkNumberOfImagePages: 1
[    15.546]     LinNumberOfImagePages: 1
[    15.546]     LinRedMaskSize: 5
[    15.546]     LinRedFieldPosition: 11
[    15.546]     LinGreenMaskSize: 6
[    15.546]     LinGreenFieldPosition: 5
[    15.546]     LinBlueMaskSize: 5
[    15.546]     LinBlueFieldPosition: 0
[    15.546]     LinRsvdMaskSize: 0
[    15.546]     LinRsvdFieldPosition: 0
[    15.546]     MaxPixelClock: 229500000
[    15.547] *Mode: 118 (1024x768)
[    15.547]     ModeAttributes: 0x3bf
[    15.547]     WinAAttributes: 0x7
[    15.547]     WinBAttributes: 0x0
[    15.547]     WinGranularity: 64
[    15.547]     WinSize: 64
[    15.547]     WinASegment: 0xa000
[    15.547]     WinBSegment: 0x0
[    15.547]     WinFuncPtr: 0xc0006161
[    15.547]     BytesPerScanline: 4096
[    15.547]     XResolution: 1024
[    15.547]     YResolution: 768
[    15.547]     XCharSize: 8
[    15.547]     YCharSize: 16
[    15.547]     NumberOfPlanes: 1
[    15.547]     BitsPerPixel: 32
[    15.547]     NumberOfBanks: 1
[    15.547]     MemoryModel: 6
[    15.547]     BankSize: 0
[    15.547]     NumberOfImages: 1
[    15.547]     RedMaskSize: 8
[    15.547]     RedFieldPosition: 16
[    15.547]     GreenMaskSize: 8
[    15.547]     GreenFieldPosition: 8
[    15.547]     BlueMaskSize: 8
[    15.547]     BlueFieldPosition: 0
[    15.547]     RsvdMaskSize: 8
[    15.547]     RsvdFieldPosition: 24
[    15.547]     DirectColorModeInfo: 0
[    15.547]     PhysBasePtr: 0xcf000000
[    15.547]     LinBytesPerScanLine: 4096
[    15.547]     BnkNumberOfImagePages: 1
[    15.547]     LinNumberOfImagePages: 1
[    15.547]     LinRedMaskSize: 8
[    15.547]     LinRedFieldPosition: 16
[    15.547]     LinGreenMaskSize: 8
[    15.547]     LinGreenFieldPosition: 8
[    15.547]     LinBlueMaskSize: 8
[    15.547]     LinBlueFieldPosition: 0
[    15.547]     LinRsvdMaskSize: 8
[    15.547]     LinRsvdFieldPosition: 24
[    15.547]     MaxPixelClock: 229500000
[    15.548] Mode: 11a (1280x1024)
[    15.548]     ModeAttributes: 0x3bf
[    15.548]     WinAAttributes: 0x7
[    15.548]     WinBAttributes: 0x0
[    15.548]     WinGranularity: 64
[    15.548]     WinSize: 64
[    15.548]     WinASegment: 0xa000
[    15.548]     WinBSegment: 0x0
[    15.548]     WinFuncPtr: 0xc0006161
[    15.548]     BytesPerScanline: 2560
[    15.548]     XResolution: 1280
[    15.548]     YResolution: 1024
[    15.548]     XCharSize: 8
[    15.548]     YCharSize: 16
[    15.548]     NumberOfPlanes: 1
[    15.548]     BitsPerPixel: 16
[    15.548]     NumberOfBanks: 1
[    15.548]     MemoryModel: 6
[    15.548]     BankSize: 0
[    15.548]     NumberOfImages: 1
[    15.548]     RedMaskSize: 5
[    15.548]     RedFieldPosition: 11
[    15.548]     GreenMaskSize: 6
[    15.548]     GreenFieldPosition: 5
[    15.548]     BlueMaskSize: 5
[    15.548]     BlueFieldPosition: 0
[    15.549]     RsvdMaskSize: 0
[    15.549]     RsvdFieldPosition: 0
[    15.549]     DirectColorModeInfo: 0
[    15.549]     PhysBasePtr: 0xcf000000
[    15.549]     LinBytesPerScanLine: 2560
[    15.549]     BnkNumberOfImagePages: 1
[    15.549]     LinNumberOfImagePages: 1
[    15.549]     LinRedMaskSize: 5
[    15.549]     LinRedFieldPosition: 11
[    15.549]     LinGreenMaskSize: 6
[    15.549]     LinGreenFieldPosition: 5
[    15.549]     LinBlueMaskSize: 5
[    15.549]     LinBlueFieldPosition: 0
[    15.549]     LinRsvdMaskSize: 0
[    15.549]     LinRsvdFieldPosition: 0
[    15.549]     MaxPixelClock: 229500000
[    15.550] *Mode: 11b (1280x1024)
[    15.550]     ModeAttributes: 0x3bf
[    15.550]     WinAAttributes: 0x7
[    15.550]     WinBAttributes: 0x0
[    15.550]     WinGranularity: 64
[    15.550]     WinSize: 64
[    15.550]     WinASegment: 0xa000
[    15.550]     WinBSegment: 0x0
[    15.550]     WinFuncPtr: 0xc0006161
[    15.550]     BytesPerScanline: 5120
[    15.550]     XResolution: 1280
[    15.550]     YResolution: 1024
[    15.550]     XCharSize: 8
[    15.550]     YCharSize: 16
[    15.550]     NumberOfPlanes: 1
[    15.550]     BitsPerPixel: 32
[    15.550]     NumberOfBanks: 1
[    15.550]     MemoryModel: 6
[    15.550]     BankSize: 0
[    15.550]     NumberOfImages: 1
[    15.550]     RedMaskSize: 8
[    15.550]     RedFieldPosition: 16
[    15.550]     GreenMaskSize: 8
[    15.550]     GreenFieldPosition: 8
[    15.550]     BlueMaskSize: 8
[    15.550]     BlueFieldPosition: 0
[    15.550]     RsvdMaskSize: 8
[    15.550]     RsvdFieldPosition: 24
[    15.550]     DirectColorModeInfo: 0
[    15.550]     PhysBasePtr: 0xcf000000
[    15.550]     LinBytesPerScanLine: 5120
[    15.550]     BnkNumberOfImagePages: 1
[    15.550]     LinNumberOfImagePages: 1
[    15.550]     LinRedMaskSize: 8
[    15.550]     LinRedFieldPosition: 16
[    15.550]     LinGreenMaskSize: 8
[    15.550]     LinGreenFieldPosition: 8
[    15.550]     LinBlueMaskSize: 8
[    15.550]     LinBlueFieldPosition: 0
[    15.550]     LinRsvdMaskSize: 8
[    15.550]     LinRsvdFieldPosition: 24
[    15.550]     MaxPixelClock: 229500000
[    15.551] Mode: 130 (320x200)
[    15.551]     ModeAttributes: 0x3bf
[    15.551]     WinAAttributes: 0x7
[    15.551]     WinBAttributes: 0x0
[    15.551]     WinGranularity: 64
[    15.551]     WinSize: 64
[    15.551]     WinASegment: 0xa000
[    15.551]     WinBSegment: 0x0
[    15.551]     WinFuncPtr: 0xc0006161
[    15.551]     BytesPerScanline: 320
[    15.551]     XResolution: 320
[    15.551]     YResolution: 200
[    15.551]     XCharSize: 8
[    15.551]     YCharSize: 8
[    15.551]     NumberOfPlanes: 1
[    15.551]     BitsPerPixel: 8
[    15.551]     NumberOfBanks: 1
[    15.551]     MemoryModel: 4
[    15.551]     BankSize: 0
[    15.551]     NumberOfImages: 62
[    15.551]     RedMaskSize: 0
[    15.551]     RedFieldPosition: 0
[    15.551]     GreenMaskSize: 0
[    15.551]     GreenFieldPosition: 0
[    15.551]     BlueMaskSize: 0
[    15.551]     BlueFieldPosition: 0
[    15.551]     RsvdMaskSize: 0
[    15.551]     RsvdFieldPosition: 0
[    15.551]     DirectColorModeInfo: 0
[    15.551]     PhysBasePtr: 0xcf000000
[    15.551]     LinBytesPerScanLine: 320
[    15.551]     BnkNumberOfImagePages: 62
[    15.551]     LinNumberOfImagePages: 62
[    15.551]     LinRedMaskSize: 0
[    15.551]     LinRedFieldPosition: 0
[    15.551]     LinGreenMaskSize: 0
[    15.551]     LinGreenFieldPosition: 0
[    15.551]     LinBlueMaskSize: 0
[    15.551]     LinBlueFieldPosition: 0
[    15.551]     LinRsvdMaskSize: 0
[    15.551]     LinRsvdFieldPosition: 0
[    15.551]     MaxPixelClock: 229500000
[    15.552] Mode: 131 (320x400)
[    15.552]     ModeAttributes: 0x3bf
[    15.552]     WinAAttributes: 0x7
[    15.552]     WinBAttributes: 0x0
[    15.552]     WinGranularity: 64
[    15.552]     WinSize: 64
[    15.552]     WinASegment: 0xa000
[    15.552]     WinBSegment: 0x0
[    15.552]     WinFuncPtr: 0xc0006161
[    15.552]     BytesPerScanline: 320
[    15.552]     XResolution: 320
[    15.552]     YResolution: 400
[    15.552]     XCharSize: 8
[    15.552]     YCharSize: 16
[    15.552]     NumberOfPlanes: 1
[    15.552]     BitsPerPixel: 8
[    15.552]     NumberOfBanks: 1
[    15.552]     MemoryModel: 4
[    15.552]     BankSize: 0
[    15.552]     NumberOfImages: 30
[    15.552]     RedMaskSize: 0
[    15.552]     RedFieldPosition: 0
[    15.552]     GreenMaskSize: 0
[    15.552]     GreenFieldPosition: 0
[    15.552]     BlueMaskSize: 0
[    15.552]     BlueFieldPosition: 0
[    15.552]     RsvdMaskSize: 0
[    15.552]     RsvdFieldPosition: 0
[    15.552]     DirectColorModeInfo: 0
[    15.552]     PhysBasePtr: 0xcf000000
[    15.552]     LinBytesPerScanLine: 320
[    15.552]     BnkNumberOfImagePages: 30
[    15.552]     LinNumberOfImagePages: 30
[    15.552]     LinRedMaskSize: 0
[    15.552]     LinRedFieldPosition: 0
[    15.552]     LinGreenMaskSize: 0
[    15.552]     LinGreenFieldPosition: 0
[    15.552]     LinBlueMaskSize: 0
[    15.552]     LinBlueFieldPosition: 0
[    15.552]     LinRsvdMaskSize: 0
[    15.552]     LinRsvdFieldPosition: 0
[    15.552]     MaxPixelClock: 229500000
[    15.553] Mode: 132 (320x400)
[    15.553]     ModeAttributes: 0x3bf
[    15.553]     WinAAttributes: 0x7
[    15.553]     WinBAttributes: 0x0
[    15.553]     WinGranularity: 64
[    15.553]     WinSize: 64
[    15.553]     WinASegment: 0xa000
[    15.553]     WinBSegment: 0x0
[    15.553]     WinFuncPtr: 0xc0006161
[    15.553]     BytesPerScanline: 640
[    15.553]     XResolution: 320
[    15.553]     YResolution: 400
[    15.553]     XCharSize: 8
[    15.553]     YCharSize: 16
[    15.553]     NumberOfPlanes: 1
[    15.553]     BitsPerPixel: 16
[    15.553]     NumberOfBanks: 1
[    15.553]     MemoryModel: 6
[    15.553]     BankSize: 0
[    15.553]     NumberOfImages: 14
[    15.553]     RedMaskSize: 5
[    15.553]     RedFieldPosition: 11
[    15.553]     GreenMaskSize: 6
[    15.553]     GreenFieldPosition: 5
[    15.553]     BlueMaskSize: 5
[    15.553]     BlueFieldPosition: 0
[    15.553]     RsvdMaskSize: 0
[    15.553]     RsvdFieldPosition: 0
[    15.553]     DirectColorModeInfo: 0
[    15.553]     PhysBasePtr: 0xcf000000
[    15.553]     LinBytesPerScanLine: 640
[    15.553]     BnkNumberOfImagePages: 14
[    15.553]     LinNumberOfImagePages: 14
[    15.553]     LinRedMaskSize: 5
[    15.553]     LinRedFieldPosition: 11
[    15.553]     LinGreenMaskSize: 6
[    15.553]     LinGreenFieldPosition: 5
[    15.553]     LinBlueMaskSize: 5
[    15.553]     LinBlueFieldPosition: 0
[    15.553]     LinRsvdMaskSize: 0
[    15.553]     LinRsvdFieldPosition: 0
[    15.553]     MaxPixelClock: 229500000
[    15.554] *Mode: 133 (320x400)
[    15.554]     ModeAttributes: 0x3bf
[    15.554]     WinAAttributes: 0x7
[    15.554]     WinBAttributes: 0x0
[    15.554]     WinGranularity: 64
[    15.554]     WinSize: 64
[    15.554]     WinASegment: 0xa000
[    15.555]     WinBSegment: 0x0
[    15.555]     WinFuncPtr: 0xc0006161
[    15.555]     BytesPerScanline: 1280
[    15.555]     XResolution: 320
[    15.555]     YResolution: 400
[    15.555]     XCharSize: 8
[    15.555]     YCharSize: 16
[    15.555]     NumberOfPlanes: 1
[    15.555]     BitsPerPixel: 32
[    15.555]     NumberOfBanks: 1
[    15.555]     MemoryModel: 6
[    15.555]     BankSize: 0
[    15.555]     NumberOfImages: 6
[    15.555]     RedMaskSize: 8
[    15.555]     RedFieldPosition: 16
[    15.555]     GreenMaskSize: 8
[    15.555]     GreenFieldPosition: 8
[    15.555]     BlueMaskSize: 8
[    15.555]     BlueFieldPosition: 0
[    15.555]     RsvdMaskSize: 8
[    15.555]     RsvdFieldPosition: 24
[    15.555]     DirectColorModeInfo: 0
[    15.555]     PhysBasePtr: 0xcf000000
[    15.555]     LinBytesPerScanLine: 1280
[    15.555]     BnkNumberOfImagePages: 6
[    15.555]     LinNumberOfImagePages: 6
[    15.555]     LinRedMaskSize: 8
[    15.555]     LinRedFieldPosition: 16
[    15.555]     LinGreenMaskSize: 8
[    15.555]     LinGreenFieldPosition: 8
[    15.555]     LinBlueMaskSize: 8
[    15.555]     LinBlueFieldPosition: 0
[    15.555]     LinRsvdMaskSize: 8
[    15.555]     LinRsvdFieldPosition: 24
[    15.555]     MaxPixelClock: 229500000
[    15.556] Mode: 134 (320x240)
[    15.556]     ModeAttributes: 0x3bf
[    15.556]     WinAAttributes: 0x7
[    15.556]     WinBAttributes: 0x0
[    15.556]     WinGranularity: 64
[    15.556]     WinSize: 64
[    15.556]     WinASegment: 0xa000
[    15.556]     WinBSegment: 0x0
[    15.556]     WinFuncPtr: 0xc0006161
[    15.556]     BytesPerScanline: 320
[    15.556]     XResolution: 320
[    15.556]     YResolution: 240
[    15.556]     XCharSize: 8
[    15.556]     YCharSize: 8
[    15.556]     NumberOfPlanes: 1
[    15.556]     BitsPerPixel: 8
[    15.556]     NumberOfBanks: 1
[    15.556]     MemoryModel: 4
[    15.556]     BankSize: 0
[    15.556]     NumberOfImages: 30
[    15.556]     RedMaskSize: 0
[    15.556]     RedFieldPosition: 0
[    15.556]     GreenMaskSize: 0
[    15.556]     GreenFieldPosition: 0
[    15.556]     BlueMaskSize: 0
[    15.556]     BlueFieldPosition: 0
[    15.556]     RsvdMaskSize: 0
[    15.556]     RsvdFieldPosition: 0
[    15.556]     DirectColorModeInfo: 0
[    15.556]     PhysBasePtr: 0xcf000000
[    15.556]     LinBytesPerScanLine: 320
[    15.556]     BnkNumberOfImagePages: 30
[    15.556]     LinNumberOfImagePages: 30
[    15.556]     LinRedMaskSize: 0
[    15.556]     LinRedFieldPosition: 0
[    15.556]     LinGreenMaskSize: 0
[    15.556]     LinGreenFieldPosition: 0
[    15.556]     LinBlueMaskSize: 0
[    15.556]     LinBlueFieldPosition: 0
[    15.556]     LinRsvdMaskSize: 0
[    15.556]     LinRsvdFieldPosition: 0
[    15.556]     MaxPixelClock: 229500000
[    15.557] Mode: 135 (320x240)
[    15.557]     ModeAttributes: 0x3bf
[    15.557]     WinAAttributes: 0x7
[    15.557]     WinBAttributes: 0x0
[    15.557]     WinGranularity: 64
[    15.557]     WinSize: 64
[    15.557]     WinASegment: 0xa000
[    15.557]     WinBSegment: 0x0
[    15.557]     WinFuncPtr: 0xc0006161
[    15.557]     BytesPerScanline: 640
[    15.557]     XResolution: 320
[    15.557]     YResolution: 240
[    15.557]     XCharSize: 8
[    15.557]     YCharSize: 8
[    15.557]     NumberOfPlanes: 1
[    15.557]     BitsPerPixel: 16
[    15.557]     NumberOfBanks: 1
[    15.557]     MemoryModel: 6
[    15.557]     BankSize: 0
[    15.557]     NumberOfImages: 19
[    15.557]     RedMaskSize: 5
[    15.557]     RedFieldPosition: 11
[    15.557]     GreenMaskSize: 6
[    15.557]     GreenFieldPosition: 5
[    15.557]     BlueMaskSize: 5
[    15.557]     BlueFieldPosition: 0
[    15.557]     RsvdMaskSize: 0
[    15.557]     RsvdFieldPosition: 0
[    15.557]     DirectColorModeInfo: 0
[    15.557]     PhysBasePtr: 0xcf000000
[    15.557]     LinBytesPerScanLine: 640
[    15.557]     BnkNumberOfImagePages: 19
[    15.557]     LinNumberOfImagePages: 19
[    15.557]     LinRedMaskSize: 5
[    15.557]     LinRedFieldPosition: 11
[    15.557]     LinGreenMaskSize: 6
[    15.557]     LinGreenFieldPosition: 5
[    15.557]     LinBlueMaskSize: 5
[    15.557]     LinBlueFieldPosition: 0
[    15.557]     LinRsvdMaskSize: 0
[    15.557]     LinRsvdFieldPosition: 0
[    15.557]     MaxPixelClock: 229500000
[    15.558] *Mode: 136 (320x240)
[    15.558]     ModeAttributes: 0x3bf
[    15.558]     WinAAttributes: 0x7
[    15.558]     WinBAttributes: 0x0
[    15.558]     WinGranularity: 64
[    15.558]     WinSize: 64
[    15.558]     WinASegment: 0xa000
[    15.558]     WinBSegment: 0x0
[    15.558]     WinFuncPtr: 0xc0006161
[    15.558]     BytesPerScanline: 1280
[    15.558]     XResolution: 320
[    15.558]     YResolution: 240
[    15.558]     XCharSize: 8
[    15.558]     YCharSize: 8
[    15.558]     NumberOfPlanes: 1
[    15.558]     BitsPerPixel: 32
[    15.558]     NumberOfBanks: 1
[    15.558]     MemoryModel: 6
[    15.558]     BankSize: 0
[    15.558]     NumberOfImages: 10
[    15.558]     RedMaskSize: 8
[    15.558]     RedFieldPosition: 16
[    15.558]     GreenMaskSize: 8
[    15.558]     GreenFieldPosition: 8
[    15.558]     BlueMaskSize: 8
[    15.558]     BlueFieldPosition: 0
[    15.558]     RsvdMaskSize: 8
[    15.558]     RsvdFieldPosition: 24
[    15.558]     DirectColorModeInfo: 0
[    15.558]     PhysBasePtr: 0xcf000000
[    15.558]     LinBytesPerScanLine: 1280
[    15.558]     BnkNumberOfImagePages: 10
[    15.558]     LinNumberOfImagePages: 10
[    15.558]     LinRedMaskSize: 8
[    15.558]     LinRedFieldPosition: 16
[    15.558]     LinGreenMaskSize: 8
[    15.558]     LinGreenFieldPosition: 8
[    15.558]     LinBlueMaskSize: 8
[    15.558]     LinBlueFieldPosition: 0
[    15.558]     LinRsvdMaskSize: 8
[    15.558]     LinRsvdFieldPosition: 24
[    15.558]     MaxPixelClock: 229500000
[    15.559] Mode: 13d (640x400)
[    15.559]     ModeAttributes: 0x3bf
[    15.559]     WinAAttributes: 0x7
[    15.559]     WinBAttributes: 0x0
[    15.559]     WinGranularity: 64
[    15.559]     WinSize: 64
[    15.559]     WinASegment: 0xa000
[    15.559]     WinBSegment: 0x0
[    15.559]     WinFuncPtr: 0xc0006161
[    15.559]     BytesPerScanline: 1280
[    15.559]     XResolution: 640
[    15.559]     YResolution: 400
[    15.559]     XCharSize: 8
[    15.559]     YCharSize: 16
[    15.559]     NumberOfPlanes: 1
[    15.559]     BitsPerPixel: 16
[    15.559]     NumberOfBanks: 1
[    15.559]     MemoryModel: 6
[    15.559]     BankSize: 0
[    15.559]     NumberOfImages: 6
[    15.559]     RedMaskSize: 5
[    15.559]     RedFieldPosition: 11
[    15.559]     GreenMaskSize: 6
[    15.559]     GreenFieldPosition: 5
[    15.559]     BlueMaskSize: 5
[    15.559]     BlueFieldPosition: 0
[    15.559]     RsvdMaskSize: 0
[    15.559]     RsvdFieldPosition: 0
[    15.559]     DirectColorModeInfo: 0
[    15.559]     PhysBasePtr: 0xcf000000
[    15.559]     LinBytesPerScanLine: 1280
[    15.559]     BnkNumberOfImagePages: 6
[    15.559]     LinNumberOfImagePages: 6
[    15.559]     LinRedMaskSize: 5
[    15.559]     LinRedFieldPosition: 11
[    15.559]     LinGreenMaskSize: 6
[    15.559]     LinGreenFieldPosition: 5
[    15.559]     LinBlueMaskSize: 5
[    15.560]     LinBlueFieldPosition: 0
[    15.560]     LinRsvdMaskSize: 0
[    15.560]     LinRsvdFieldPosition: 0
[    15.560]     MaxPixelClock: 229500000
[    15.561] *Mode: 13e (640x400)
[    15.561]     ModeAttributes: 0x3bf
[    15.561]     WinAAttributes: 0x7
[    15.561]     WinBAttributes: 0x0
[    15.561]     WinGranularity: 64
[    15.561]     WinSize: 64
[    15.561]     WinASegment: 0xa000
[    15.561]     WinBSegment: 0x0
[    15.561]     WinFuncPtr: 0xc0006161
[    15.561]     BytesPerScanline: 2560
[    15.561]     XResolution: 640
[    15.561]     YResolution: 400
[    15.561]     XCharSize: 8
[    15.561]     YCharSize: 16
[    15.561]     NumberOfPlanes: 1
[    15.561]     BitsPerPixel: 32
[    15.561]     NumberOfBanks: 1
[    15.561]     MemoryModel: 6
[    15.561]     BankSize: 0
[    15.561]     NumberOfImages: 2
[    15.561]     RedMaskSize: 8
[    15.561]     RedFieldPosition: 16
[    15.561]     GreenMaskSize: 8
[    15.561]     GreenFieldPosition: 8
[    15.561]     BlueMaskSize: 8
[    15.561]     BlueFieldPosition: 0
[    15.561]     RsvdMaskSize: 8
[    15.561]     RsvdFieldPosition: 24
[    15.561]     DirectColorModeInfo: 0
[    15.561]     PhysBasePtr: 0xcf000000
[    15.561]     LinBytesPerScanLine: 2560
[    15.561]     BnkNumberOfImagePages: 2
[    15.561]     LinNumberOfImagePages: 2
[    15.561]     LinRedMaskSize: 8
[    15.561]     LinRedFieldPosition: 16
[    15.561]     LinGreenMaskSize: 8
[    15.561]     LinGreenFieldPosition: 8
[    15.561]     LinBlueMaskSize: 8
[    15.561]     LinBlueFieldPosition: 0
[    15.561]     LinRsvdMaskSize: 8
[    15.561]     LinRsvdFieldPosition: 24
[    15.561]     MaxPixelClock: 229500000
[    15.562] Mode: 160 (1280x800)
[    15.562]     ModeAttributes: 0x3bf
[    15.562]     WinAAttributes: 0x7
[    15.562]     WinBAttributes: 0x0
[    15.562]     WinGranularity: 64
[    15.562]     WinSize: 64
[    15.562]     WinASegment: 0xa000
[    15.562]     WinBSegment: 0x0
[    15.562]     WinFuncPtr: 0xc0006161
[    15.562]     BytesPerScanline: 1280
[    15.562]     XResolution: 1280
[    15.562]     YResolution: 800
[    15.562]     XCharSize: 8
[    15.562]     YCharSize: 16
[    15.562]     NumberOfPlanes: 1
[    15.562]     BitsPerPixel: 8
[    15.562]     NumberOfBanks: 1
[    15.562]     MemoryModel: 4
[    15.562]     BankSize: 0
[    15.562]     NumberOfImages: 2
[    15.562]     RedMaskSize: 0
[    15.562]     RedFieldPosition: 0
[    15.562]     GreenMaskSize: 0
[    15.562]     GreenFieldPosition: 0
[    15.562]     BlueMaskSize: 0
[    15.562]     BlueFieldPosition: 0
[    15.562]     RsvdMaskSize: 0
[    15.562]     RsvdFieldPosition: 0
[    15.562]     DirectColorModeInfo: 0
[    15.562]     PhysBasePtr: 0xcf000000
[    15.562]     LinBytesPerScanLine: 1280
[    15.562]     BnkNumberOfImagePages: 2
[    15.562]     LinNumberOfImagePages: 2
[    15.562]     LinRedMaskSize: 0
[    15.562]     LinRedFieldPosition: 0
[    15.562]     LinGreenMaskSize: 0
[    15.562]     LinGreenFieldPosition: 0
[    15.562]     LinBlueMaskSize: 0
[    15.562]     LinBlueFieldPosition: 0
[    15.562]     LinRsvdMaskSize: 0
[    15.562]     LinRsvdFieldPosition: 0
[    15.562]     MaxPixelClock: 229500000
[    15.563] *Mode: 161 (1280x800)
[    15.563]     ModeAttributes: 0x3bf
[    15.563]     WinAAttributes: 0x7
[    15.563]     WinBAttributes: 0x0
[    15.563]     WinGranularity: 64
[    15.563]     WinSize: 64
[    15.563]     WinASegment: 0xa000
[    15.563]     WinBSegment: 0x0
[    15.563]     WinFuncPtr: 0xc0006161
[    15.563]     BytesPerScanline: 5120
[    15.563]     XResolution: 1280
[    15.563]     YResolution: 800
[    15.563]     XCharSize: 8
[    15.563]     YCharSize: 16
[    15.563]     NumberOfPlanes: 1
[    15.563]     BitsPerPixel: 32
[    15.563]     NumberOfBanks: 1
[    15.563]     MemoryModel: 6
[    15.563]     BankSize: 0
[    15.563]     NumberOfImages: 1
[    15.563]     RedMaskSize: 8
[    15.563]     RedFieldPosition: 16
[    15.563]     GreenMaskSize: 8
[    15.563]     GreenFieldPosition: 8
[    15.563]     BlueMaskSize: 8
[    15.563]     BlueFieldPosition: 0
[    15.563]     RsvdMaskSize: 8
[    15.563]     RsvdFieldPosition: 24
[    15.563]     DirectColorModeInfo: 0
[    15.563]     PhysBasePtr: 0xcf000000
[    15.563]     LinBytesPerScanLine: 5120
[    15.563]     BnkNumberOfImagePages: 1
[    15.563]     LinNumberOfImagePages: 1
[    15.563]     LinRedMaskSize: 8
[    15.563]     LinRedFieldPosition: 16
[    15.563]     LinGreenMaskSize: 8
[    15.563]     LinGreenFieldPosition: 8
[    15.563]     LinBlueMaskSize: 8
[    15.563]     LinBlueFieldPosition: 0
[    15.563]     LinRsvdMaskSize: 8
[    15.563]     LinRsvdFieldPosition: 24
[    15.563]     MaxPixelClock: 229500000
[    15.564] Mode: 162 (768x480)
[    15.564]     ModeAttributes: 0x3bf
[    15.564]     WinAAttributes: 0x7
[    15.564]     WinBAttributes: 0x0
[    15.564]     WinGranularity: 64
[    15.564]     WinSize: 64
[    15.564]     WinASegment: 0xa000
[    15.564]     WinBSegment: 0x0
[    15.564]     WinFuncPtr: 0xc0006161
[    15.564]     BytesPerScanline: 768
[    15.564]     XResolution: 768
[    15.564]     YResolution: 480
[    15.564]     XCharSize: 8
[    15.564]     YCharSize: 16
[    15.564]     NumberOfPlanes: 1
[    15.564]     BitsPerPixel: 8
[    15.564]     NumberOfBanks: 1
[    15.564]     MemoryModel: 4
[    15.564]     BankSize: 0
[    15.564]     NumberOfImages: 8
[    15.564]     RedMaskSize: 0
[    15.564]     RedFieldPosition: 0
[    15.564]     GreenMaskSize: 0
[    15.564]     GreenFieldPosition: 0
[    15.564]     BlueMaskSize: 0
[    15.564]     BlueFieldPosition: 0
[    15.564]     RsvdMaskSize: 0
[    15.564]     RsvdFieldPosition: 0
[    15.564]     DirectColorModeInfo: 0
[    15.564]     PhysBasePtr: 0xcf000000
[    15.564]     LinBytesPerScanLine: 768
[    15.564]     BnkNumberOfImagePages: 8
[    15.564]     LinNumberOfImagePages: 8
[    15.564]     LinRedMaskSize: 0
[    15.565]     LinRedFieldPosition: 0
[    15.565]     LinGreenMaskSize: 0
[    15.565]     LinGreenFieldPosition: 0
[    15.565]     LinBlueMaskSize: 0
[    15.565]     LinBlueFieldPosition: 0
[    15.565]     LinRsvdMaskSize: 0
[    15.565]     LinRsvdFieldPosition: 0
[    15.565]     MaxPixelClock: 229500000
[    15.566] *Mode: 17b (1280x720)
[    15.566]     ModeAttributes: 0x3bf
[    15.566]     WinAAttributes: 0x7
[    15.566]     WinBAttributes: 0x0
[    15.566]     WinGranularity: 64
[    15.566]     WinSize: 64
[    15.566]     WinASegment: 0xa000
[    15.566]     WinBSegment: 0x0
[    15.566]     WinFuncPtr: 0xc0006161
[    15.566]     BytesPerScanline: 5120
[    15.566]     XResolution: 1280
[    15.566]     YResolution: 720
[    15.566]     XCharSize: 8
[    15.566]     YCharSize: 16
[    15.566]     NumberOfPlanes: 1
[    15.566]     BitsPerPixel: 32
[    15.566]     NumberOfBanks: 1
[    15.566]     MemoryModel: 6
[    15.566]     BankSize: 0
[    15.566]     NumberOfImages: 1
[    15.566]     RedMaskSize: 8
[    15.566]     RedFieldPosition: 16
[    15.566]     GreenMaskSize: 8
[    15.566]     GreenFieldPosition: 8
[    15.566]     BlueMaskSize: 8
[    15.566]     BlueFieldPosition: 0
[    15.566]     RsvdMaskSize: 8
[    15.566]     RsvdFieldPosition: 24
[    15.566]     DirectColorModeInfo: 0
[    15.566]     PhysBasePtr: 0xcf000000
[    15.566]     LinBytesPerScanLine: 5120
[    15.566]     BnkNumberOfImagePages: 1
[    15.566]     LinNumberOfImagePages: 1
[    15.566]     LinRedMaskSize: 8
[    15.566]     LinRedFieldPosition: 16
[    15.566]     LinGreenMaskSize: 8
[    15.566]     LinGreenFieldPosition: 8
[    15.566]     LinBlueMaskSize: 8
[    15.566]     LinBlueFieldPosition: 0
[    15.566]     LinRsvdMaskSize: 8
[    15.566]     LinRsvdFieldPosition: 24
[    15.566]     MaxPixelClock: 229500000
[    15.566] 
[    15.566] (II) VESA(0): Total Memory: 224 64KB banks (14336kB)
[    15.566] (II) VESA(0): <default monitor>: Using hsync range of 24.00-83.00 kHz
[    15.566] (II) VESA(0): <default monitor>: Using vrefresh range of 50.00-76.00 Hz
[    15.566] (II) VESA(0): <default monitor>: Using maximum pixel clock of 175.00 MHz
[    15.566] (WW) VESA(0): Unable to estimate virtual size
[    15.566] (II) VESA(0): Not using built-in mode "1280x800" (no mode of this name)
[    15.568] (II) VESA(0): Not using built-in mode "640x400" (no mode of this name)
[    15.568] (II) VESA(0): Not using built-in mode "320x400" (no mode of this name)
[    15.568] (II) VESA(0): Not using built-in mode "320x240" (no mode of this name)
[    15.568] (II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
[    15.568] (--) VESA(0): Virtual size is 1280x1024 (pitch 1280)
[    15.568] (**) VESA(0): *Built-in mode "1280x1024"
[    15.568] (**) VESA(0): *Built-in mode "1280x720"
[    15.568] (**) VESA(0): *Built-in mode "1024x768"
[    15.568] (**) VESA(0): *Built-in mode "800x600"
[    15.568] (**) VESA(0): *Built-in mode "640x480"
[    15.568] (**) VESA(0): Display dimensions: (530, 290) mm
[    15.568] (**) VESA(0): DPI set to (61, 89)
[    15.568] (**) VESA(0): Using "Shadow Framebuffer"
[    15.568] (II) Loading sub module "shadow"
[    15.568] (II) LoadModule: "shadow"
[    15.568] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    15.575] (II) Module shadow: vendor="X.Org Foundation"
[    15.575]     compiled for 1.9.0, module version = 1.1.0
[    15.575]     ABI class: X.Org ANSI C Emulation, version 0.4
[    15.575] (II) Loading sub module "fb"
[    15.576] (II) LoadModule: "fb"
[    15.576] (II) Loading /usr/lib/xorg/modules/libfb.so
[    15.576] (II) Module fb: vendor="X.Org Foundation"
[    15.576]     compiled for 1.9.0, module version = 1.0.0
[    15.576]     ABI class: X.Org ANSI C Emulation, version 0.4
[    15.576] (==) Depth 24 pixmap format is 32 bpp
[    15.576] (II) Loading sub module "int10"
[    15.576] (II) LoadModule: "int10"
[    15.576] (II) Reloading /usr/lib/xorg/modules/libint10.so
[    15.576] (II) VESA(0): initializing int10
[    15.576] (II) VESA(0): Bad V_BIOS checksum
[    15.576] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    15.621] (II) VESA(0): VESA BIOS detected
[    15.621] (II) VESA(0): VESA VBE Version 3.0
[    15.621] (II) VESA(0): VESA VBE Total Mem: 14336 kB
[    15.621] (II) VESA(0): VESA VBE OEM: NVIDIA
[    15.621] (II) VESA(0): VESA VBE OEM Software Rev: 112.21
[    15.621] (II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
[    15.621] (II) VESA(0): VESA VBE OEM Product: BIOS-P/N@N5899
[    15.621] (II) VESA(0): VESA VBE OEM Product Rev: GW-CLK@èIèIg
[    15.623] (II) VESA(0): virtual address = 0x7f7ce4abc000,
    physical address = 0xcf000000, size = 14680064
[    15.645] (II) VESA(0): Setting up VESA Mode 0x11B (1280x1024)
[    15.758] (==) VESA(0): Default visual is TrueColor
[    15.759] (==) VESA(0): Backing store disabled
[    15.759] (==) VESA(0): DPMS enabled
[    15.759] (WW) VESA(0): Option "NoLogo" is not used
[    15.759] (==) RandR enabled
[    15.759] (II) Initializing built-in extension Generic Event Extension
[    15.759] (II) Initializing built-in extension SHAPE
[    15.759] (II) Initializing built-in extension MIT-SHM
[    15.759] (II) Initializing built-in extension XInputExtension
[    15.759] (II) Initializing built-in extension XTEST
[    15.759] (II) Initializing built-in extension BIG-REQUESTS
[    15.759] (II) Initializing built-in extension SYNC
[    15.759] (II) Initializing built-in extension XKEYBOARD
[    15.759] (II) Initializing built-in extension XC-MISC
[    15.759] (II) Initializing built-in extension SECURITY
[    15.759] (II) Initializing built-in extension XINERAMA
[    15.759] (II) Initializing built-in extension XFIXES
[    15.759] (II) Initializing built-in extension RENDER
[    15.759] (II) Initializing built-in extension RANDR
[    15.759] (II) Initializing built-in extension COMPOSITE
[    15.759] (II) Initializing built-in extension DAMAGE
[    15.759] (II) Initializing built-in extension GESTURE
[    15.760] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
[    15.777] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    15.783] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    15.783] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    15.783] (II) LoadModule: "evdev"
[    15.783] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    15.783] (II) Module evdev: vendor="X.Org Foundation"
[    15.783]     compiled for 1.9.0, module version = 2.3.2
[    15.783]     Module class: X.Org XInput Driver
[    15.783]     ABI class: X.Org XInput driver, version 11.0
[    15.783] (**) Power Button: always reports core events
[    15.783] (**) Power Button: Device: "/dev/input/event1"
[    15.820] (II) Power Button: Found keys
[    15.820] (II) Power Button: Configuring as keyboard
[    15.820] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    15.820] (**) Option "xkb_rules" "evdev"
[    15.820] (**) Option "xkb_model" "pc105"
[    15.820] (**) Option "xkb_layout" "se"
[    15.821] (II) XKB: reuse xkmfile /var/lib/xkb/server-523B07B557B20588EB459118C97940B7C9FF61EB.xkm
[    15.822] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    15.822] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    15.822] (**) Power Button: always reports core events
[    15.822] (**) Power Button: Device: "/dev/input/event0"
[    15.870] (II) Power Button: Found keys
[    15.870] (II) Power Button: Configuring as keyboard
[    15.870] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    15.870] (**) Option "xkb_rules" "evdev"
[    15.870] (**) Option "xkb_model" "pc105"
[    15.870] (**) Option "xkb_layout" "se"
[    15.872] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event2)
[    15.872] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    15.872] (**) Logitech USB Receiver: always reports core events
[    15.872] (**) Logitech USB Receiver: Device: "/dev/input/event2"
[    15.910] (II) Logitech USB Receiver: Found keys
[    15.910] (II) Logitech USB Receiver: Configuring as keyboard
[    15.910] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    15.910] (**) Option "xkb_rules" "evdev"
[    15.910] (**) Option "xkb_model" "pc105"
[    15.910] (**) Option "xkb_layout" "se"
[    15.910] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event3)
[    15.910] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[    15.910] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    15.910] (**) Logitech USB Receiver: always reports core events
[    15.910] (**) Logitech USB Receiver: Device: "/dev/input/event3"
[    15.950] (II) Logitech USB Receiver: Found 12 mouse buttons
[    15.950] (II) Logitech USB Receiver: Found scroll wheel(s)
[    15.950] (II) Logitech USB Receiver: Found relative axes
[    15.950] (II) Logitech USB Receiver: Found x and y relative axes
[    15.950] (II) Logitech USB Receiver: Found absolute axes
[    15.950] (II) evdev-grail: failed to open grail, no gesture support
[    15.950] (II) Logitech USB Receiver: Found keys
[    15.950] (II) Logitech USB Receiver: Configuring as mouse
[    15.950] (II) Logitech USB Receiver: Configuring as keyboard
[    15.950] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    15.950] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    15.950] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    15.950] (**) Option "xkb_rules" "evdev"
[    15.950] (**) Option "xkb_model" "pc105"
[    15.950] (**) Option "xkb_layout" "se"
[    15.950] (II) Logitech USB Receiver: initialized for relative axes.
[    15.950] (WW) Logitech USB Receiver: ignoring absolute axes.
[    15.950] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse0)
[    15.950] (II) No input driver/identifier specified (ignoring)
[    16.370] (II) Power Button: Close
[    16.370] (II) UnloadModule: "evdev"
[    16.411] (II) Power Button: Close
[    16.411] (II) UnloadModule: "evdev"
[    16.460] (II) Logitech USB Receiver: Close
[    16.460] (II) UnloadModule: "evdev"
[    16.520] (II) Logitech USB Receiver: Close
[    16.520] (II) UnloadModule: "evdev"
[    16.695]  ddxSigGiveUp: Closing log
```

---

### Post by realzippy on 2010-10-24
..how did you try to install the nvidia-driver?

---

### Post by sonicb00m on 2010-10-25
The nvidia driver was installed via the restricted driver manager and was working just fine.

It all went to hell when I tried to add a second monitor to my card. Xorg refused to start. When I took the monitor away again xorg still refused to start. I tried the reconfigure option and nothing would work. It wouldn't even go into safe graphics mode. Then I uninstalled xorg completely and reinstalled it and it still reproduced the same behaviour.

I still don't understand why it became such a problem and why I can't simply reset it to how Ubuntu would have installed it from scratch.

---

### Post by un234567 on 2010-10-25
You have the 260.19 driver installed, try installing nvidia 256.53 driver. I am facing the same problem with the new nvidia driver and i get the same xorg logs. It looks like the X server is loading the vesa module instead of the nvidia module because the nvidia module failed to load. I suggest you give 256.53 a try because many ppl are having problems with the latest driver.

---

### Post by realzippy on 2010-10-25
> **sonicb00m said:**
> The nvidia driver was installed via the restricted driver manager and was working just fine.

It all went to hell when I tried to add a second monitor to my card. Xorg refused to start. When I took the monitor away again xorg still refused to start. I tried the reconfigure option and nothing would work. It wouldn't even go into safe graphics mode. Then I uninstalled xorg completely and reinstalled it and it still reproduced the same behaviour.

I still don't understand why it became such a problem and why I can't simply reset it to how Ubuntu would have installed it from scratch.

to resume:

Installation of nvidia driver (via System/Administration/AdditionalDrivers) works,means,after reboot the nvidia driver is working.
Correct?
Connected is a BenQ G2420HDB monitor;do you plug in the 2nd monitor when machine is powered off or do you hotplug it?
You could start in recovery mode and purge nvidia and reinstall nouveau:
```
sudo nvidia-settings --uninstall
  sudo apt-get remove --purge nvidia*
  sudo apt-get remove --purge xserver-xorg-video-nv xserver-xorg-video-nouveau
  sudo apt-get install nvidia-common
  sudo apt-get install xserver-xorg-video-nouveau
  sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
  sudo dpkg-reconfigure xserver-xorg
```

from
([https://wiki.edubuntu.org/X/Troubleshooting/NvidiaDriverSwitching](https://wiki.edubuntu.org/X/Troubleshooting/NvidiaDriverSwitching))

Or you could try to reinstall the nvidia-driver:
```
sudo apt-get --reinstall install nvidia-current
```
that would be the "reset" you demand,but reinstalling (as noticed) is a fast alternative.
When having the nvidia driver running again we can go on.

---

### Post by realzippy on 2010-10-25
> **un234567 said:**
> You have the 260.19 driver installed, try installing nvidia 256.53 driver. I am facing the same problem with the new nvidia driver and i get the same xorg logs. It looks like the X server is loading the vesa module instead of the nvidia module with the newer driver. Just look under DRI 2 extension and u will see tht. Currently im trying to stop this wired behavior through blacklisting vesa but for now you have to stick with 256.53

Means,you had 260.19.12 installed and after plugging in 2nd monitor
X screwed up?Ran an "nvidia-xconfig" in recovery mode e.g.?

Anyway,if you *know* that downgrading to 256.xx helps,I would recommend this to sonicb00m.

---

