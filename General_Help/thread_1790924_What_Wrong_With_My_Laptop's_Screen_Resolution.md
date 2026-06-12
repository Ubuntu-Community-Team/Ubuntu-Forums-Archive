---
title: "What Wrong With My Laptop's Screen Resolution?"
date: 2011-06-25
forum: General Help
---

### Post by LonelyAspie on 2011-06-25
I have my laptop hooked up to an external monitor, and the let's me shooce from 640x480 and 800x600 resolution (4:3). The monitor's resolution is 1440:900 ([16:10]("http://www.youtube.com/watch?v=DGPsvw4nzAQ#")) and my laptop's screen resolution is 1600:900 (16:9).

I haven't seen this before.

Here is a video of it:
[http://www.youtube.com/watch?v=DGPsvw4nzAQ](http://www.youtube.com/watch?v=DGPsvw4nzAQ)

---

### Post by Yellow Pasque on 2011-06-25
LOL @ video.
Post your /var/log/Xorg.0.log

---

### Post by LonelyAspie on 2011-06-25
```
[   768.394] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[   768.394] X Protocol Version 11, Revision 0
[   768.394] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[   768.394] Current Operating System: Linux MyLaptop 2.6.38-8-generic-pae #42-Ubuntu SMP Mon Apr 11 05:17:09 UTC 2011 i686
[   768.394] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=dc9fed97-79e4-45c3-b364-9d2d0e084fa6 ro quiet splash vt.handoff=7
[   768.394] Build Date: 21 May 2011  11:38:35AM
[   768.394] xorg-server 2:1.10.1-1ubuntu1.1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[   768.394] Current version of pixman: 0.20.2
[   768.394]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[   768.394] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   768.394] (==) Log file: "/var/log/Xorg.1.log", Time: Mon Jun 13 14:05:14 2011
[   768.394] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   768.395] (==) No Layout section.  Using the first Screen section.
[   768.395] (==) No screen section available. Using defaults.
[   768.395] (**) |-->Screen "Default Screen Section" (0)
[   768.395] (**) |   |-->Monitor "<default monitor>"
[   768.396] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[   768.396] (==) Automatically adding devices
[   768.396] (==) Automatically enabling devices
[   768.396] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   768.396]     Entry deleted from font path.
[   768.396] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   768.396]     Entry deleted from font path.
[   768.396] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   768.396]     Entry deleted from font path.
[   768.396] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   768.396]     Entry deleted from font path.
[   768.396] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   768.396]     Entry deleted from font path.
[   768.396] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[   768.396] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   768.396] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   768.396] (II) Loader magic: 0x81ffde0
[   768.396] (II) Module ABI versions:
[   768.396]     X.Org ANSI C Emulation: 0.4
[   768.396]     X.Org Video Driver: 10.0
[   768.396]     X.Org XInput driver : 12.3
[   768.396]     X.Org Server Extension : 5.0
[   768.398] (--) PCI:*(0:0:2:0) 8086:0046:1179:fd00 rev 2, Mem @ 0x90000000/4194304, 0x80000000/268435456, I/O @ 0x00006050/8
[   768.398] (II) Open ACPI successful (/var/run/acpid.socket)
[   768.398] (II) LoadModule: "extmod"
[   768.399] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   768.399] (II) Module extmod: vendor="X.Org Foundation"
[   768.399]     compiled for 1.10.1, module version = 1.0.0
[   768.399]     Module class: X.Org Server Extension
[   768.399]     ABI class: X.Org Server Extension, version 5.0
[   768.399] (II) Loading extension MIT-SCREEN-SAVER
[   768.399] (II) Loading extension XFree86-VidModeExtension
[   768.399] (II) Loading extension XFree86-DGA
[   768.399] (II) Loading extension DPMS
[   768.399] (II) Loading extension XVideo
[   768.399] (II) Loading extension XVideo-MotionCompensation
[   768.399] (II) Loading extension X-Resource
[   768.399] (II) LoadModule: "dbe"
[   768.400] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   768.400] (II) Module dbe: vendor="X.Org Foundation"
[   768.400]     compiled for 1.10.1, module version = 1.0.0
[   768.400]     Module class: X.Org Server Extension
[   768.400]     ABI class: X.Org Server Extension, version 5.0
[   768.400] (II) Loading extension DOUBLE-BUFFER
[   768.400] (II) LoadModule: "glx"
[   768.400] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   768.400] (II) Module glx: vendor="X.Org Foundation"
[   768.400]     compiled for 1.10.1, module version = 1.0.0
[   768.400]     ABI class: X.Org Server Extension, version 5.0
[   768.400] (==) AIGLX enabled
[   768.400] (II) Loading extension GLX
[   768.400] (II) LoadModule: "record"
[   768.400] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   768.401] (II) Module record: vendor="X.Org Foundation"
[   768.401]     compiled for 1.10.1, module version = 1.13.0
[   768.401]     Module class: X.Org Server Extension
[   768.401]     ABI class: X.Org Server Extension, version 5.0
[   768.401] (II) Loading extension RECORD
[   768.401] (II) LoadModule: "dri"
[   768.401] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   768.401] (II) Module dri: vendor="X.Org Foundation"
[   768.401]     compiled for 1.10.1, module version = 1.0.0
[   768.401]     ABI class: X.Org Server Extension, version 5.0
[   768.401] (II) Loading extension XFree86-DRI
[   768.401] (II) LoadModule: "dri2"
[   768.401] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   768.401] (II) Module dri2: vendor="X.Org Foundation"
[   768.401]     compiled for 1.10.1, module version = 1.2.0
[   768.401]     ABI class: X.Org Server Extension, version 5.0
[   768.401] (II) Loading extension DRI2
[   768.401] (==) Matched intel as autoconfigured driver 0
[   768.401] (==) Matched vesa as autoconfigured driver 1
[   768.401] (==) Matched fbdev as autoconfigured driver 2
[   768.401] (==) Assigned the driver to the xf86ConfigLayout
[   768.401] (II) LoadModule: "intel"
[   768.402] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[   768.402] (II) Module intel: vendor="X.Org Foundation"
[   768.402]     compiled for 1.10.1, module version = 2.14.0
[   768.402]     Module class: X.Org Video Driver
[   768.402]     ABI class: X.Org Video Driver, version 10.0
[   768.402] (II) LoadModule: "vesa"
[   768.402] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   768.403] (II) Module vesa: vendor="X.Org Foundation"
[   768.403]     compiled for 1.10.0, module version = 2.3.0
[   768.403]     Module class: X.Org Video Driver
[   768.403]     ABI class: X.Org Video Driver, version 10.0
[   768.403] (II) LoadModule: "fbdev"
[   768.403] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   768.403] (II) Module fbdev: vendor="X.Org Foundation"
[   768.403]     compiled for 1.10.0, module version = 0.4.2
[   768.403]     ABI class: X.Org Video Driver, version 10.0
[   768.403] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
    Sandybridge, Sandybridge
[   768.403] (II) VESA: driver for VESA chipsets: vesa
[   768.403] (II) FBDEV: driver for framebuffer: fbdev
[   768.404] (--) using VT number 8

[   768.790] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[   768.790] (WW) Falling back to old probe method for vesa
[   768.790] (WW) Falling back to old probe method for fbdev
[   768.790] (II) Loading sub module "fbdevhw"
[   768.790] (II) LoadModule: "fbdevhw"
[   768.791] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   768.791] (II) Module fbdevhw: vendor="X.Org Foundation"
[   768.791]     compiled for 1.10.1, module version = 0.0.2
[   768.791]     ABI class: X.Org Video Driver, version 10.0
[   768.791] drmOpenDevice: node name is /dev/dri/card0
[   768.793] drmOpenDevice: open result is 9, (OK)
[   768.793] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[   768.793] drmOpenDevice: node name is /dev/dri/card0
[   768.793] drmOpenDevice: open result is 9, (OK)
[   768.793] drmOpenByBusid: drmOpenMinor returns 9
[   768.793] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[   768.793] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[   768.793] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[   768.793] (==) intel(0): RGB weight 888
[   768.793] (==) intel(0): Default visual is TrueColor
[   768.793] (II) intel(0): Integrated Graphics Chipset: Intel(R) Arrandale
[   768.793] (--) intel(0): Chipset: "Arrandale"
[   768.793] (**) intel(0): Relaxed fencing enabled
[   768.793] (**) intel(0): Tiling enabled
[   768.793] (**) intel(0): SwapBuffers wait enabled
[   768.793] (==) intel(0): video overlay key set to 0x101fe
[   768.794] (II) intel(0): Output LVDS1 has no monitor section
[   768.794] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
[   768.855] (II) intel(0): Output VGA1 has no monitor section
[   768.860] (II) intel(0): Output HDMI1 has no monitor section
[   768.861] (II) intel(0): Output DP1 has no monitor section
[   768.861] (II) intel(0): EDID for output LVDS1
[   768.861] (II) intel(0): Manufacturer: LGD  Model: 1ca  Serial#: 0
[   768.861] (II) intel(0): Year: 2008  Week: 0
[   768.861] (II) intel(0): EDID Version: 1.3
[   768.861] (II) intel(0): Digital Display Input
[   768.861] (II) intel(0): Max Image Size [cm]: horiz.: 38  vert.: 21
[   768.861] (II) intel(0): Gamma: 2.20
[   768.861] (II) intel(0): No DPMS capabilities specified
[   768.861] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[   768.861] (II) intel(0): First detailed timing is preferred mode
[   768.861] (II) intel(0): redX: 0.615 redY: 0.346   greenX: 0.314 greenY: 0.602
[   768.861] (II) intel(0): blueX: 0.151 blueY: 0.109   whiteX: 0.312 whiteY: 0.328
[   768.861] (II) intel(0): Manufacturer's mask: 0
[   768.861] (II) intel(0): Supported detailed timing:
[   768.861] (II) intel(0): clock: 97.8 MHz   Image Size:  382 x 215 mm
[   768.861] (II) intel(0): h_active: 1600  h_sync: 1648  h_sync_end 1696 h_blank_end 1784 h_border: 0
[   768.861] (II) intel(0): v_active: 900  v_sync: 902  v_sync_end 905 v_blanking: 912 v_border: 0
[   768.861] (II) intel(0):  
[   768.861] (II) intel(0):  LP173WD1-TLA1
[   768.861] (II) intel(0): EDID (in hex):
[   768.861] (II) intel(0):     00ffffffffffff0030e4ca0100000000
[   768.861] (II) intel(0):     00120103802615780aa8c09d58509a26
[   768.861] (II) intel(0):     1c505400000001010101010101010101
[   768.861] (II) intel(0):     0101010101012f2640b860840c303030
[   768.861] (II) intel(0):     23007ed7100000190000000000000000
[   768.861] (II) intel(0):     00000000000000000000000000fe0000
[   768.861] (II) intel(0):     00004c47446973706c61790a000000fe
[   768.861] (II) intel(0):     004c503137335744312d544c41310078
[   768.861] (II) intel(0): EDID vendor "LGD", prod id 458
[   768.861] (II) intel(0): Printing DDC gathered Modelines:
[   768.861] (II) intel(0): Modeline "1600x900"x0.0   97.75  1600 1648 1696 1784  900 902 905 912 -hsync -vsync (54.8 kHz)
[   768.861] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[   768.861] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[   768.861] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[   768.861] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[   768.861] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[   768.861] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[   768.861] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[   768.861] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[   768.861] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[   768.861] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[   768.861] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[   768.861] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[   768.861] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[   768.862] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[   768.862] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[   768.862] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[   768.862] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[   768.862] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[   768.862] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[   768.862] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[   768.862] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[   768.862] (II) intel(0): Printing probed modes for output LVDS1
[   768.862] (II) intel(0): Modeline "1600x900"x60.1   97.75  1600 1648 1696 1784  900 902 905 912 -hsync -vsync (54.8 kHz)
[   768.862] (II) intel(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[   768.862] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[   768.862] (II) intel(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz)
[   768.862] (II) intel(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
[   768.862] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   768.862] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   768.862] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   768.862] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   768.923] (II) intel(0): EDID for output VGA1
[   768.923] (II) intel(0): Manufacturer: SHP  Model: 214a  Serial#: 16843009
[   768.923] (II) intel(0): Year: 2005  Week: 15
[   768.923] (II) intel(0): EDID Version: 1.3
[   768.923] (II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[   768.923] (II) intel(0): Sync:  Separate  Composite  SyncOnGreen
[   768.923] (II) intel(0): Max Image Size [cm]: horiz.: 34  vert.: 27
[   768.923] (II) intel(0): Gamma: 2.20
[   768.923] (II) intel(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[   768.923] (II) intel(0): First detailed timing is preferred mode
[   768.923] (II) intel(0): redX: 0.640 redY: 0.349   greenX: 0.284 greenY: 0.617
[   768.923] (II) intel(0): blueX: 0.142 blueY: 0.067   whiteX: 0.313 whiteY: 0.329
[   768.923] (II) intel(0): Supported established timings:
[   768.923] (II) intel(0): 720x400@70Hz
[   768.923] (II) intel(0): 640x480@60Hz
[   768.923] (II) intel(0): 640x480@67Hz
[   768.923] (II) intel(0): 640x480@72Hz
[   768.923] (II) intel(0): 640x480@75Hz
[   768.923] (II) intel(0): 800x600@56Hz
[   768.923] (II) intel(0): 800x600@60Hz
[   768.923] (II) intel(0): 800x600@72Hz
[   768.923] (II) intel(0): 800x600@75Hz
[   768.923] (II) intel(0): 832x624@75Hz
[   768.923] (II) intel(0): 1024x768@60Hz
[   768.923] (II) intel(0): 1024x768@70Hz
[   768.923] (II) intel(0): 1024x768@75Hz
[   768.923] (II) intel(0): 1280x1024@75Hz
[   768.923] (II) intel(0): 1152x864@75Hz
[   768.923] (II) intel(0): Manufacturer's mask: 0
[   768.923] (II) intel(0): Supported standard timings:
[   768.923] (II) intel(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[   768.923] (II) intel(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[   768.923] (II) intel(0): #2: hsize: 1280  vsize 1024  refresh: 67  vid: 34689
[   768.923] (II) intel(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[   768.923] (II) intel(0): #4: hsize: 1024  vsize 768  refresh: 66  vid: 18017
[   768.923] (II) intel(0): #5: hsize: 1280  vsize 1024  refresh: 76  vid: 36993
[   768.923] (II) intel(0): Supported detailed timing:
[   768.923] (II) intel(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
[   768.923] (II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[   768.923] (II) intel(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[   768.923] (II) intel(0): Monitor name: LL-173C-B
[   768.923] (II) intel(0): Ranges: V min: 55 V max: 77 Hz, H min: 24 H max: 82 kHz, PixClock max 145 MHz
[   768.923] (II) intel(0): Serial No: 5X004504
[   768.923] (II) intel(0): EDID (in hex):
[   768.923] (II) intel(0):     00ffffffffffff004d104a2101010101
[   768.923] (II) intel(0):     0f0f01030e221b78eadc55a359489e24
[   768.923] (II) intel(0):     115054bfef80818081408187714f6146
[   768.923] (II) intel(0):     819001010101302a009851002a403070
[   768.923] (II) intel(0):     1300520e1100001e000000fc004c4c2d
[   768.923] (II) intel(0):     313733432d420a202020000000fd0037
[   768.923] (II) intel(0):     4d18520e000a202020202020000000ff
[   768.923] (II) intel(0):     0035583030343530340a20202020009e
[   768.923] (II) intel(0): Printing probed modes for output VGA1
[   768.923] (II) intel(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   768.923] (II) intel(0): Modeline "1280x1024"x76.0  141.81  1280 1376 1512 1744  1024 1025 1028 1070 -hsync +vsync (81.3 kHz)
[   768.923] (II) intel(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   768.924] (II) intel(0): Modeline "1280x1024"x67.0  123.23  1280 1368 1504 1728  1024 1025 1028 1064 -hsync +vsync (71.3 kHz)
[   768.924] (II) intel(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[   768.924] (II) intel(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   768.924] (II) intel(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
[   768.924] (II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   768.924] (II) intel(0): Modeline "1024x768"x66.0   71.64  1024 1080 1192 1360  768 769 772 798 -hsync +vsync (52.7 kHz)
[   768.924] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   768.924] (II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   768.924] (II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   768.924] (II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   768.924] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   768.924] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   768.924] (II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
[   768.924] (II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   768.924] (II) intel(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[   768.924] (II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   768.924] (II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   768.928] (II) intel(0): EDID for output HDMI1
[   768.929] (II) intel(0): EDID for output DP1
[   768.929] (II) intel(0): Output LVDS1 connected
[   768.929] (II) intel(0): Output VGA1 connected
[   768.929] (II) intel(0): Output HDMI1 disconnected
[   768.929] (II) intel(0): Output DP1 disconnected
[   768.929] (II) intel(0): Using fuzzy aspect match for initial modes
[   768.929] (II) intel(0): Output LVDS1 using initial mode 1152x864
[   768.929] (II) intel(0): Output VGA1 using initial mode 1152x864
[   768.929] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[   768.929] (II) intel(0): Kernel page flipping support detected, enabling
[   768.929] (**) intel(0): Display dimensions: (380, 210) mm
[   768.929] (**) intel(0): DPI set to (77, 104)
[   768.929] (II) Loading sub module "fb"
[   768.929] (II) LoadModule: "fb"
[   768.930] (II) Loading /usr/lib/xorg/modules/libfb.so
[   768.930] (II) Module fb: vendor="X.Org Foundation"
[   768.930]     compiled for 1.10.1, module version = 1.0.0
[   768.930]     ABI class: X.Org ANSI C Emulation, version 0.4
[   768.930] (II) UnloadModule: "vesa"
[   768.930] (II) Unloading vesa
[   768.930] (II) UnloadModule: "fbdev"
[   768.930] (II) Unloading fbdev
[   768.930] (II) UnloadModule: "fbdevhw"
[   768.930] (II) Unloading fbdevhw
[   768.930] (==) Depth 24 pixmap format is 32 bpp
[   768.930] (==) intel(0): VideoRam: 262144 KB
[   768.930] (II) intel(0): [DRI2] Setup complete
[   768.930] (II) intel(0): [DRI2]   DRI driver: i965
[   768.930] (II) intel(0): Allocated new frame buffer 1152x864 stride 4608, tiled
[   768.940] (II) UXA(0): Driver registered support for the following operations:
[   768.940] (II)         solid
[   768.940] (II)         copy
[   768.940] (II)         composite (RENDER acceleration)
[   768.940] (II)         put_image
[   768.940] (II)         get_image
[   768.940] (==) intel(0): Backing store disabled
[   768.940] (==) intel(0): Silken mouse enabled
[   768.940] (II) intel(0): Initializing HW Cursor
[   769.242] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[   769.246] (==) intel(0): DPMS enabled
[   769.246] (==) intel(0): Intel XvMC decoder enabled
[   769.246] (II) intel(0): Set up textured video
[   769.246] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[   769.247] (II) intel(0): direct rendering: DRI2 Enabled
[   769.247] (==) intel(0): hotplug detection: "enabled"
[   769.247] (--) RandR disabled
[   769.247] (II) Initializing built-in extension Generic Event Extension
[   769.247] (II) Initializing built-in extension SHAPE
[   769.247] (II) Initializing built-in extension MIT-SHM
[   769.247] (II) Initializing built-in extension XInputExtension
[   769.247] (II) Initializing built-in extension XTEST
[   769.247] (II) Initializing built-in extension BIG-REQUESTS
[   769.247] (II) Initializing built-in extension SYNC
[   769.247] (II) Initializing built-in extension XKEYBOARD
[   769.247] (II) Initializing built-in extension XC-MISC
[   769.247] (II) Initializing built-in extension SECURITY
[   769.247] (II) Initializing built-in extension XINERAMA
[   769.247] (II) Initializing built-in extension XFIXES
[   769.247] (II) Initializing built-in extension RENDER
[   769.247] (II) Initializing built-in extension RANDR
[   769.247] (II) Initializing built-in extension COMPOSITE
[   769.247] (II) Initializing built-in extension DAMAGE
[   769.247] (II) Initializing built-in extension GESTURE
[   769.265] (II) AIGLX: Trying DRI driver /usr/lib/dri/i965_dri.so
[   769.268] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[   769.268] (II) AIGLX: enabled GLX_INTEL_swap_event
[   769.268] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[   769.268] (II) AIGLX: enabled GLX_SGI_make_current_read
[   769.268] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[   769.268] (II) AIGLX: Loaded and initialized i965
[   769.268] (II) GLX: Initialized DRI2 GL provider for screen 0
[   769.269] (II) intel(0): Setting screen physical size to 304 x 228
[   769.279] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   769.288] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[   769.288] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   769.288] (II) LoadModule: "evdev"
[   769.288] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   769.289] (II) Module evdev: vendor="X.Org Foundation"
[   769.289]     compiled for 1.10.0.902, module version = 2.6.0
[   769.289]     Module class: X.Org XInput Driver
[   769.289]     ABI class: X.Org XInput driver, version 12.3
[   769.289] (II) Using input driver 'evdev' for 'Power Button'
[   769.289] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   769.289] (**) Power Button: always reports core events
[   769.289] (**) Power Button: Device: "/dev/input/event2"
[   769.304] (--) Power Button: Found keys
[   769.304] (II) Power Button: Configuring as keyboard
[   769.304] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[   769.304] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[   769.304] (**) Option "xkb_rules" "evdev"
[   769.304] (**) Option "xkb_model" "pc105"
[   769.304] (**) Option "xkb_layout" "us"
[   769.306] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[   769.306] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[   769.306] (II) Using input driver 'evdev' for 'Video Bus'
[   769.306] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   769.306] (**) Video Bus: always reports core events
[   769.306] (**) Video Bus: Device: "/dev/input/event4"
[   769.307] (--) Video Bus: Found keys
[   769.307] (II) Video Bus: Configuring as keyboard
[   769.307] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:02/input/input4/event4"
[   769.307] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[   769.307] (**) Option "xkb_rules" "evdev"
[   769.307] (**) Option "xkb_model" "pc105"
[   769.307] (**) Option "xkb_layout" "us"
[   769.428] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[   769.428] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   769.428] (II) Using input driver 'evdev' for 'Power Button'
[   769.428] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   769.428] (**) Power Button: always reports core events
[   769.428] (**) Power Button: Device: "/dev/input/event1"
[   769.432] (--) Power Button: Found keys
[   769.432] (II) Power Button: Configuring as keyboard
[   769.432] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[   769.432] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[   769.432] (**) Option "xkb_rules" "evdev"
[   769.432] (**) Option "xkb_model" "pc105"
[   769.432] (**) Option "xkb_layout" "us"
[   769.433] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[   769.433] (II) No input driver/identifier specified (ignoring)
[   769.443] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[   769.443] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[   769.443] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[   769.443] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   769.443] (**) AT Translated Set 2 keyboard: always reports core events
[   769.443] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[   769.443] (--) AT Translated Set 2 keyboard: Found keys
[   769.443] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[   769.443] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[   769.443] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[   769.443] (**) Option "xkb_rules" "evdev"
[   769.443] (**) Option "xkb_model" "pc105"
[   769.443] (**) Option "xkb_layout" "us"
[   769.444] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event5)
[   769.444] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[   769.444] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[   769.444] (II) LoadModule: "synaptics"
[   769.445] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[   769.445] (II) Module synaptics: vendor="X.Org Foundation"
[   769.445]     compiled for 1.10.0.902, module version = 1.3.99
[   769.445]     Module class: X.Org XInput Driver
[   769.445]     ABI class: X.Org XInput driver, version 12.3
[   769.445] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[   769.445] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[   769.445] (**) SynPS/2 Synaptics TouchPad: always reports core events
[   769.445] (**) Option "Device" "/dev/input/event5"
[   769.445] (--) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5692
[   769.445] (--) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4680
[   769.445] (--) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[   769.445] (--) SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[   769.446] (--) SynPS/2 Synaptics TouchPad: buttons: left right double triple
[   769.446] (--) SynPS/2 Synaptics TouchPad: touchpad found
[   769.446] (**) SynPS/2 Synaptics TouchPad: always reports core events
[   769.446] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input5/event5"
[   769.446] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[   769.446] (**) SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[   769.446] (**) SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[   769.446] (**) SynPS/2 Synaptics TouchPad: AccelFactor is now 0.037
[   769.446] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[   769.446] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[   769.446] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[   769.446] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[   769.448] (--) SynPS/2 Synaptics TouchPad: touchpad found
[   769.448] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[   769.448] (II) No input driver/identifier specified (ignoring)
[   769.831] (II) intel(0): EDID vendor "SHP", prod id 8522
[   769.831] (II) intel(0): Using hsync ranges from config file
[   769.831] (II) intel(0): Using vrefresh ranges from config file
[   769.831] (II) intel(0): Printing DDC gathered Modelines:
[   769.831] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   769.831] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   769.831] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   769.831] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   769.831] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[   769.831] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[   769.831] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   769.832] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   769.832] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   769.832] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   769.832] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   769.832] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   769.832] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   769.832] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   769.832] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   769.832] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   769.832] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[   769.832] (II) intel(0): Modeline "1280x1024"x67.0  123.19  1280 1368 1504 1728  1024 1025 1028 1064 -hsync +vsync (71.3 kHz)
[   769.832] (II) intel(0): Modeline "1024x768"x66.0   71.63  1024 1080 1192 1360  768 769 772 798 -hsync +vsync (52.7 kHz)
[   769.832] (II) intel(0): Modeline "1280x1024"x76.0  141.82  1280 1376 1512 1744  1024 1025 1028 1070 -hsync +vsync (81.3 kHz)
[   769.900] (II) intel(0): EDID vendor "SHP", prod id 8522
[   769.900] (II) intel(0): Using hsync ranges from config file
[   769.900] (II) intel(0): Using vrefresh ranges from config file
[   769.900] (II) intel(0): Printing DDC gathered Modelines:
[   769.900] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   769.900] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   769.900] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   769.900] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   769.900] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[   769.900] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[   769.901] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   769.901] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   769.901] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   769.901] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   769.901] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   769.901] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   769.901] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   769.901] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   769.901] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   769.901] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   769.901] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[   769.901] (II) intel(0): Modeline "1280x1024"x67.0  123.19  1280 1368 1504 1728  1024 1025 1028 1064 -hsync +vsync (71.3 kHz)
[   769.901] (II) intel(0): Modeline "1024x768"x66.0   71.63  1024 1080 1192 1360  768 769 772 798 -hsync +vsync (52.7 kHz)
[   769.901] (II) intel(0): Modeline "1280x1024"x76.0  141.82  1280 1376 1512 1744  1024 1025 1028 1070 -hsync +vsync (81.3 kHz)
[   769.970] (II) intel(0): EDID vendor "SHP", prod id 8522
[   769.970] (II) intel(0): Using hsync ranges from config file
[   769.970] (II) intel(0): Using vrefresh ranges from config file
[   769.970] (II) intel(0): Printing DDC gathered Modelines:
[   769.970] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   769.970] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   769.970] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   769.970] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   769.970] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[   769.970] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[   769.970] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   769.970] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   769.970] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   769.970] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   769.970] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   769.970] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   769.970] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   769.970] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   769.970] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   769.970] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   769.970] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[   769.970] (II) intel(0): Modeline "1280x1024"x67.0  123.19  1280 1368 1504 1728  1024 1025 1028 1064 -hsync +vsync (71.3 kHz)
[   769.971] (II) intel(0): Modeline "1024x768"x66.0   71.63  1024 1080 1192 1360  768 769 772 798 -hsync +vsync (52.7 kHz)
[   769.971] (II) intel(0): Modeline "1280x1024"x76.0  141.82  1280 1376 1512 1744  1024 1025 1028 1070 -hsync +vsync (81.3 kHz)
[   770.039] (II) intel(0): EDID vendor "SHP", prod id 8522
[   770.039] (II) intel(0): Using hsync ranges from config file
[   770.039] (II) intel(0): Using vrefresh ranges from config file
[   770.039] (II) intel(0): Printing DDC gathered Modelines:
[   770.039] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   770.039] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   770.039] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   770.039] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   770.039] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[   770.039] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[   770.039] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   770.039] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   770.039] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   770.039] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   770.039] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   770.039] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   770.039] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   770.039] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   770.039] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   770.039] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   770.039] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[   770.039] (II) intel(0): Modeline "1280x1024"x67.0  123.19  1280 1368 1504 1728  1024 1025 1028 1064 -hsync +vsync (71.3 kHz)
[   770.039] (II) intel(0): Modeline "1024x768"x66.0   71.63  1024 1080 1192 1360  768 769 772 798 -hsync +vsync (52.7 kHz)
[   770.039] (II) intel(0): Modeline "1280x1024"x76.0  141.82  1280 1376 1512 1744  1024 1025 1028 1070 -hsync +vsync (81.3 kHz)
[   773.477] (II) AIGLX: Suspending AIGLX clients for VT switch
[  1493.713] (II) Open ACPI successful (/var/run/acpid.socket)
[  1493.713] (II) AIGLX: Resuming AIGLX clients after VT switch
[  1493.890] (II) intel(0): EDID vendor "SHP", prod id 8522
[  1493.890] (II) intel(0): Using hsync ranges from config file
[  1493.890] (II) intel(0): Using vrefresh ranges from config file
[  1493.890] (II) intel(0): Printing DDC gathered Modelines:
[  1493.890] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  1493.890] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  1493.890] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[  1493.890] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  1493.890] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[  1493.890] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[  1493.890] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  1493.890] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  1493.890] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[  1493.890] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  1493.890] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[  1493.890] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  1493.890] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[  1493.890] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  1493.890] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[  1493.890] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[  1493.890] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[  1493.890] (II) intel(0): Modeline "1280x1024"x67.0  123.19  1280 1368 1504 1728  1024 1025 1028 1064 -hsync +vsync (71.3 kHz)
[  1493.890] (II) intel(0): Modeline "1024x768"x66.0   71.63  1024 1080 1192 1360  768 769 772 798 -hsync +vsync (52.7 kHz)
[  1493.890] (II) intel(0): Modeline "1280x1024"x76.0  141.82  1280 1376 1512 1744  1024 1025 1028 1070 -hsync +vsync (81.3 kHz)
[  1494.064] (--) SynPS/2 Synaptics TouchPad: touchpad found
[  1495.849] (II) AIGLX: Suspending AIGLX clients for VT switch
[  2534.405] (II) Open ACPI successful (/var/run/acpid.socket)
[  2534.405] (II) AIGLX: Resuming AIGLX clients after VT switch
[  2534.581] (II) intel(0): EDID vendor "SHP", prod id 8522
[  2534.582] (II) intel(0): Using hsync ranges from config file
[  2534.582] (II) intel(0): Using vrefresh ranges from config file
[  2534.582] (II) intel(0): Printing DDC gathered Modelines:
[  2534.582] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  2534.582] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  2534.582] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[  2534.582] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  2534.582] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[  2534.582] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[  2534.582] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  2534.582] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  2534.582] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[  2534.582] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  2534.582] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[  2534.582] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  2534.582] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[  2534.582] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  2534.582] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[  2534.582] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[  2534.582] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[  2534.582] (II) intel(0): Modeline "1280x1024"x67.0  123.19  1280 1368 1504 1728  1024 1025 1028 1064 -hsync +vsync (71.3 kHz)
[  2534.582] (II) intel(0): Modeline "1024x768"x66.0   71.63  1024 1080 1192 1360  768 769 772 798 -hsync +vsync (52.7 kHz)
[  2534.582] (II) intel(0): Modeline "1280x1024"x76.0  141.82  1280 1376 1512 1744  1024 1025 1028 1070 -hsync +vsync (81.3 kHz)
[  2534.752] (--) SynPS/2 Synaptics TouchPad: touchpad found
[  2536.552] (II) AIGLX: Suspending AIGLX clients for VT switch
[  3835.729] (II) Open ACPI successful (/var/run/acpid.socket)
[  3835.729] (II) AIGLX: Resuming AIGLX clients after VT switch
[  3835.905] (II) intel(0): EDID vendor "SHP", prod id 8522
[  3835.905] (II) intel(0): Using hsync ranges from config file
[  3835.905] (II) intel(0): Using vrefresh ranges from config file
[  3835.905] (II) intel(0): Printing DDC gathered Modelines:
[  3835.905] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  3835.905] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  3835.905] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[  3835.905] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  3835.905] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[  3835.905] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[  3835.905] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  3835.905] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  3835.905] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[  3835.905] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  3835.905] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[  3835.905] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  3835.906] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[  3835.906] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  3835.906] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[  3835.906] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[  3835.906] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[  3835.906] (II) intel(0): Modeline "1280x1024"x67.0  123.19  1280 1368 1504 1728  1024 1025 1028 1064 -hsync +vsync (71.3 kHz)
[  3835.906] (II) intel(0): Modeline "1024x768"x66.0   71.63  1024 1080 1192 1360  768 769 772 798 -hsync +vsync (52.7 kHz)
[  3835.906] (II) intel(0): Modeline "1280x1024"x76.0  141.82  1280 1376 1512 1744  1024 1025 1028 1070 -hsync +vsync (81.3 kHz)
[  3836.124] (--) SynPS/2 Synaptics TouchPad: touchpad found
[  3838.002] (II) AIGLX: Suspending AIGLX clients for VT switch
[  5846.483] (II) Open ACPI successful (/var/run/acpid.socket)
[  5846.483] (II) AIGLX: Resuming AIGLX clients after VT switch
[  5846.658] (II) intel(0): EDID vendor "SHP", prod id 8522
[  5846.659] (II) intel(0): Using hsync ranges from config file
[  5846.659] (II) intel(0): Using vrefresh ranges from config file
[  5846.659] (II) intel(0): Printing DDC gathered Modelines:
[  5846.659] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  5846.659] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  5846.659] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[  5846.659] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  5846.659] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[  5846.659] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[  5846.659] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  5846.659] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  5846.659] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[  5846.659] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  5846.659] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[  5846.659] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  5846.659] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[  5846.659] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  5846.659] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[  5846.659] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[  5846.659] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[  5846.659] (II) intel(0): Modeline "1280x1024"x67.0  123.19  1280 1368 1504 1728  1024 1025 1028 1064 -hsync +vsync (71.3 kHz)
[  5846.659] (II) intel(0): Modeline "1024x768"x66.0   71.63  1024 1080 1192 1360  768 769 772 798 -hsync +vsync (52.7 kHz)
[  5846.659] (II) intel(0): Modeline "1280x1024"x76.0  141.82  1280 1376 1512 1744  1024 1025 1028 1070 -hsync +vsync (81.3 kHz)
[  5846.803] (--) SynPS/2 Synaptics TouchPad: touchpad found
[  5848.249] (II) AIGLX: Suspending AIGLX clients for VT switch
[  6418.908] (II) Open ACPI successful (/var/run/acpid.socket)
[  6418.908] (II) AIGLX: Resuming AIGLX clients after VT switch
[  6419.083] (II) intel(0): EDID vendor "SHP", prod id 8522
[  6419.083] (II) intel(0): Using hsync ranges from config file
[  6419.083] (II) intel(0): Using vrefresh ranges from config file
[  6419.083] (II) intel(0): Printing DDC gathered Modelines:
[  6419.083] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  6419.083] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  6419.083] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[  6419.083] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  6419.083] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[  6419.083] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[  6419.083] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  6419.083] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  6419.083] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[  6419.083] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  6419.083] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[  6419.083] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  6419.083] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[  6419.083] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  6419.083] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[  6419.083] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[  6419.083] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[  6419.083] (II) intel(0): Modeline "1280x1024"x67.0  123.19  1280 1368 1504 1728  1024 1025 1028 1064 -hsync +vsync (71.3 kHz)
[  6419.083] (II) intel(0): Modeline "1024x768"x66.0   71.63  1024 1080 1192 1360  768 769 772 798 -hsync +vsync (52.7 kHz)
[  6419.083] (II) intel(0): Modeline "1280x1024"x76.0  141.82  1280 1376 1512 1744  1024 1025 1028 1070 -hsync +vsync (81.3 kHz)
[  6419.188] (--) SynPS/2 Synaptics TouchPad: touchpad found
[  6439.336] (II) AIGLX: Suspending AIGLX clients for VT switch
[  6973.029] (II) Open ACPI successful (/var/run/acpid.socket)
[  6973.029] (II) AIGLX: Resuming AIGLX clients after VT switch
[  6973.205] (II) intel(0): EDID vendor "SHP", prod id 8522
[  6973.205] (II) intel(0): Using hsync ranges from config file
[  6973.205] (II) intel(0): Using vrefresh ranges from config file
[  6973.205] (II) intel(0): Printing DDC gathered Modelines:
[  6973.205] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  6973.205] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  6973.205] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[  6973.205] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  6973.205] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[  6973.205] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[  6973.205] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  6973.205] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  6973.205] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[  6973.205] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  6973.205] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[  6973.206] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  6973.206] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[  6973.206] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  6973.206] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[  6973.206] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[  6973.206] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[  6973.206] (II) intel(0): Modeline "1280x1024"x67.0  123.19  1280 1368 1504 1728  1024 1025 1028 1064 -hsync +vsync (71.3 kHz)
[  6973.206] (II) intel(0): Modeline "1024x768"x66.0   71.63  1024 1080 1192 1360  768 769 772 798 -hsync +vsync (52.7 kHz)
[  6973.206] (II) intel(0): Modeline "1280x1024"x76.0  141.82  1280 1376 1512 1744  1024 1025 1028 1070 -hsync +vsync (81.3 kHz)
[  6973.432] (--) SynPS/2 Synaptics TouchPad: touchpad found
[  6975.096] (II) AIGLX: Suspending AIGLX clients for VT switch
[  7291.351] (II) Open ACPI successful (/var/run/acpid.socket)
[  7291.351] (II) AIGLX: Resuming AIGLX clients after VT switch
[  7291.525] (II) intel(0): EDID vendor "SHP", prod id 8522
[  7291.525] (II) intel(0): Using hsync ranges from config file
[  7291.525] (II) intel(0): Using vrefresh ranges from config file
[  7291.525] (II) intel(0): Printing DDC gathered Modelines:
[  7291.525] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  7291.525] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  7291.525] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[  7291.525] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  7291.526] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[  7291.526] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[  7291.526] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  7291.526] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  7291.526] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[  7291.526] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  7291.526] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[  7291.526] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  7291.526] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[  7291.526] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  7291.526] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[  7291.526] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[  7291.526] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[  7291.526] (II) intel(0): Modeline "1280x1024"x67.0  123.19  1280 1368 1504 1728  1024 1025 1028 1064 -hsync +vsync (71.3 kHz)
[  7291.526] (II) intel(0): Modeline "1024x768"x66.0   71.63  1024 1080 1192 1360  768 769 772 798 -hsync +vsync (52.7 kHz)
[  7291.526] (II) intel(0): Modeline "1280x1024"x76.0  141.82  1280 1376 1512 1744  1024 1025 1028 1070 -hsync +vsync (81.3 kHz)
[  7291.744] (--) SynPS/2 Synaptics TouchPad: touchpad found
[  7293.173] (II) AIGLX: Suspending AIGLX clients for VT switch
[  9940.198] (II) Open ACPI successful (/var/run/acpid.socket)
[  9940.198] (II) AIGLX: Resuming AIGLX clients after VT switch
[  9940.373] (II) intel(0): EDID vendor "SHP", prod id 8522
[  9940.373] (II) intel(0): Using hsync ranges from config file
[  9940.373] (II) intel(0): Using vrefresh ranges from config file
[  9940.373] (II) intel(0): Printing DDC gathered Modelines:
[  9940.373] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  9940.373] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  9940.373] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[  9940.373] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  9940.373] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[  9940.374] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[  9940.374] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  9940.374] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  9940.374] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[  9940.374] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  9940.374] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[  9940.374] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  9940.374] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[  9940.374] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  9940.374] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[  9940.374] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[  9940.374] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[  9940.374] (II) intel(0): Modeline "1280x1024"x67.0  123.19  1280 1368 1504 1728  1024 1025 1028 1064 -hsync +vsync (71.3 kHz)
[  9940.374] (II) intel(0): Modeline "1024x768"x66.0   71.63  1024 1080 1192 1360  768 769 772 798 -hsync +vsync (52.7 kHz)
[  9940.374] (II) intel(0): Modeline "1280x1024"x76.0  141.82  1280 1376 1512 1744  1024 1025 1028 1070 -hsync +vsync (81.3 kHz)
[  9940.604] (--) SynPS/2 Synaptics TouchPad: touchpad found
[  9942.289] (II) AIGLX: Suspending AIGLX clients for VT switch
[  9966.861] (II) UnloadModule: "synaptics"
[  9966.861] (II) Unloading synaptics
[  9966.861] (II) AT Translated Set 2 keyboard: Close
[  9966.861] (II) UnloadModule: "evdev"
[  9966.861] (II) Unloading evdev
[  9966.861] (II) Power Button: Close
[  9966.861] (II) UnloadModule: "evdev"
[  9966.861] (II) Unloading evdev
[  9966.861] (II) Video Bus: Close
[  9966.861] (II) UnloadModule: "evdev"
[  9966.861] (II) Unloading evdev
[  9966.861] (II) Power Button: Close
[  9966.861] (II) UnloadModule: "evdev"
[  9966.861] (II) Unloading evdev
[  9966.867]  ddxSigGiveUp: Closing log
```

---

### Post by LonelyAspie on 2011-06-25
Also, my sound is gone. When I goto the Sound Profiles, All I have is Off and HDMI thingie. I used to have 4-5 things.

---

### Post by LonelyAspie on 2011-07-07
What happened was, I took the screen off of my old laptop and somehow this caused the res to go all funny, when I put the screen back on, it was normal, but I don't think I had that happen on a laptop before. I also have a new laptop now.

---

