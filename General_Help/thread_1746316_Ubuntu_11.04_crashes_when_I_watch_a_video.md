---
title: "Ubuntu 11.04 crashes when I watch a video"
date: 2011-05-01
forum: General Help
---

### Post by Blue_Mercury on 2011-05-01
I upgraded to 11.04 yesterday and now every time I try to watch a video using either Totem or VLC it will play for a few seconds but the screen goes black then I am brought to the log in screen.

---

### Post by Finalfantasykid on 2011-05-01
Sounds like X is crashing.  You can check the log file viewer to see if there were any errors in your X log.  I'm no X expert, but there are many here so you can paste the output, and maybe someone can help you.

```
cat /var/log/Xorg.0.log
```

pasting that in a terminal should give you the same output.

---

### Post by Blue_Mercury on 2011-05-01
I'm not really sure where this would show the crash event.
It was working the last time I used Totem, then I put it to full screen and it crashed and logged me out.


[   240.428] (II) CHROME(0): ViaFirstCRTCModeValid
[   240.428] (II) CHROME(0): ViaValidMode: Validating 640x350 (Clock: 31500)
[   240.428] (II) CHROME(0): ViaFirstCRTCModeValid
[   240.428] (--) CHROME(0): Virtual size is 1600x1200 (pitch 1600)
[   240.428] (**) CHROME(0): *Default mode "1600x1200": 189.0 MHz, 87.5 kHz, 70.0 Hz
[   240.428] (II) CHROME(0): Modeline "1600x1200"x70.0  189.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (87.5 kHz)
[   240.428] (**) CHROME(0): *Default mode "1600x1200": 175.5 MHz, 81.2 kHz, 65.0 Hz
[   240.428] (II) CHROME(0): Modeline "1600x1200"x65.0  175.50  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (81.2 kHz)
[   240.428] (**) CHROME(0): *Default mode "1600x1200": 162.0 MHz, 75.0 kHz, 60.0 Hz
[   240.428] (II) CHROME(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[   240.428] (**) CHROME(0): *Default mode "1400x1050": 179.3 MHz, 93.8 kHz, 85.0 Hz
[   240.428] (II) CHROME(0): Modeline "1400x1050"x85.0  179.26  1400 1504 1656 1912  1050 1051 1054 1103 -hsync +vsync (93.8 kHz)
[   240.428] (**) CHROME(0): *Default mode "1400x1050": 145.1 MHz, 76.5 kHz, 70.0 Hz
[   240.428] (II) CHROME(0): Modeline "1400x1050"x70.0  145.06  1400 1496 1648 1896  1050 1051 1054 1093 -hsync +vsync (76.5 kHz)
[   240.428] (**) CHROME(0): *Default mode "1400x1050": 122.0 MHz, 64.9 kHz, 60.0 Hz
[   240.428] (II) CHROME(0): Modeline "1400x1050"x60.0  122.00  1400 1488 1640 1880  1050 1052 1064 1082 +hsync +vsync (64.9 kHz)
[   240.428] (**) CHROME(0): *Driver mode "1280x1024": 157.5 MHz, 91.1 kHz, 85.0 Hz
[   240.428] (II) CHROME(0): Modeline "1280x1024"x85.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync (91.1 kHz)
[   240.428] (**) CHROME(0): *Driver mode "1280x1024": 135.0 MHz, 80.0 kHz, 75.0 Hz
[   240.428] (II) CHROME(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   240.428] (**) CHROME(0): *Default mode "1280x1024": 157.5 MHz, 91.1 kHz, 85.0 Hz
[   240.428] (II) CHROME(0): Modeline "1280x1024"x85.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync (91.1 kHz)
[   240.428] (**) CHROME(0): *Default mode "1280x1024": 135.0 MHz, 80.0 kHz, 75.0 Hz
[   240.428] (II) CHROME(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   240.428] (**) CHROME(0): *Default mode "1280x1024": 108.0 MHz, 64.0 kHz, 60.0 Hz
[   240.428] (II) CHROME(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   240.428] (**) CHROME(0): *Default mode "1440x900": 106.5 MHz, 55.9 kHz, 59.9 Hz
[   240.428] (II) CHROME(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[   240.428] (**) CHROME(0): *Default mode "1280x960": 148.5 MHz, 85.9 kHz, 85.0 Hz
[   240.428] (II) CHROME(0): Modeline "1280x960"x85.0  148.50  1280 1344 1504 1728  960 961 964 1011 +hsync +vsync (85.9 kHz)
[   240.428] (**) CHROME(0): *Default mode "1280x960": 108.0 MHz, 60.0 kHz, 60.0 Hz
[   240.428] (II) CHROME(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[   240.428] (**) CHROME(0): *Default mode "1360x768": 84.8 MHz, 47.7 kHz, 59.8 Hz
[   240.428] (II) CHROME(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[   240.428] (**) CHROME(0): *Driver mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
[   240.428] (II) CHROME(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   240.428] (**) CHROME(0): *Default mode "1152x864": 143.5 MHz, 91.5 kHz, 100.0 Hz
[   240.429] (II) CHROME(0): Modeline "1152x864"x100.0  143.47  1152 1232 1360 1568  864 865 868 915 -hsync +vsync (91.5 kHz)
[   240.429] (**) CHROME(0): *Default mode "1152x864": 121.5 MHz, 77.5 kHz, 85.1 Hz
[   240.429] (II) CHROME(0): Modeline "1152x864"x85.1  121.50  1152 1216 1344 1568  864 865 868 911 +hsync -vsync (77.5 kHz)
[   240.429] (**) CHROME(0): *Default mode "1152x864": 119.7 MHz, 77.1 kHz, 85.0 Hz
[   240.429] (II) CHROME(0): Modeline "1152x864"x85.0  119.65  1152 1224 1352 1552  864 865 868 907 -hsync +vsync (77.1 kHz)
[   240.429] (**) CHROME(0): *Default mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
[   240.429] (II) CHROME(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   240.434] (**) CHROME(0): *Default mode "1152x864": 105.0 MHz, 67.6 kHz, 75.0 Hz
[   240.434] (II) CHROME(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.6 kHz)
[   240.434] (**) CHROME(0): *Default mode "1152x864": 96.8 MHz, 63.0 kHz, 70.0 Hz
[   240.434] (II) CHROME(0): Modeline "1152x864"x70.0   96.77  1152 1224 1344 1536  864 865 868 900 -hsync +vsync (63.0 kHz)
[   240.434] (**) CHROME(0): *Default mode "1152x864": 81.6 MHz, 53.7 kHz, 60.0 Hz
[   240.434] (II) CHROME(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
[   240.434] (**) CHROME(0): *Driver mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
[   240.434] (II) CHROME(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
[   240.434] (**) CHROME(0): *Driver mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
[   240.434] (II) CHROME(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   240.434] (**) CHROME(0): *Driver mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
[   240.434] (II) CHROME(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   240.434] (**) CHROME(0): *Driver mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
[   240.434] (II) CHROME(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   240.434] (**) CHROME(0): *Default mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
[   240.434] (II) CHROME(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
[   240.434] (**) CHROME(0): *Default mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
[   240.434] (II) CHROME(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   240.434] (**) CHROME(0): *Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
[   240.434] (II) CHROME(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   240.434] (**) CHROME(0): *Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
[   240.434] (II) CHROME(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   240.434] (**) CHROME(0): *Driver mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
[   240.435] (II) CHROME(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   240.435] (**) CHROME(0): *Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
[   240.435] (II) CHROME(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   240.435] (**) CHROME(0): *Driver mode "800x600": 56.2 MHz, 53.7 kHz, 85.1 Hz
[   240.435] (II) CHROME(0): Modeline "800x600"x85.1   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
[   240.435] (**) CHROME(0): *Driver mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
[   240.435] (II) CHROME(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   240.435] (**) CHROME(0): *Driver mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
[   240.435] (II) CHROME(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   240.435] (**) CHROME(0): *Driver mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
[   240.435] (II) CHROME(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   240.435] (**) CHROME(0): *Driver mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
[   240.435] (II) CHROME(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   240.435] (**) CHROME(0): *Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
[   240.435] (II) CHROME(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
[   240.435] (**) CHROME(0): *Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
[   240.435] (II) CHROME(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   240.435] (**) CHROME(0): *Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
[   240.435] (II) CHROME(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   240.435] (**) CHROME(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
[   240.435] (II) CHROME(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   240.435] (**) CHROME(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
[   240.435] (II) CHROME(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   240.435] (**) CHROME(0): *Driver mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
[   240.435] (II) CHROME(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
[   240.435] (**) CHROME(0): *Driver mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
[   240.435] (II) CHROME(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   240.435] (**) CHROME(0): *Driver mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
[   240.435] (II) CHROME(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[   240.435] (**) CHROME(0): *Driver mode "640x480": 30.2 MHz, 35.0 kHz, 66.7 Hz
[   240.435] (II) CHROME(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[   240.435] (**) CHROME(0): *Driver mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
[   240.435] (II) CHROME(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   240.435] (**) CHROME(0): *Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
[   240.435] (II) CHROME(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
[   240.435] (**) CHROME(0): *Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
[   240.435] (II) CHROME(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   240.435] (**) CHROME(0): *Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
[   240.435] (II) CHROME(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[   240.435] (**) CHROME(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
[   240.435] (II) CHROME(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   240.435] (**) CHROME(0): *Driver mode "720x400": 35.5 MHz, 39.4 kHz, 87.8 Hz
[   240.435] (II) CHROME(0): Modeline "720x400"x87.8   35.50  720 738 846 900  400 421 423 449 -hsync -vsync (39.4 kHz)
[   240.435] (**) CHROME(0): *Driver mode "720x400": 28.3 MHz, 31.5 kHz, 70.1 Hz
[   240.435] (II) CHROME(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   240.435] (**) CHROME(0): *Default mode "720x400": 35.5 MHz, 37.9 kHz, 85.0 Hz
[   240.435] (II) CHROME(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
[   240.435] (**) CHROME(0): *Default mode "640x400": 31.5 MHz, 37.9 kHz, 85.1 Hz
[   240.435] (II) CHROME(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
[   240.435] (**) CHROME(0): *Default mode "640x350": 31.5 MHz, 37.9 kHz, 85.1 Hz
[   240.435] (II) CHROME(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
[   240.435] (**) CHROME(0): Display dimensions: (350, 260) mm
[   240.435] (**) CHROME(0): DPI set to (116, 117)
[   240.435] (II) Loading sub module "fb"
[   240.435] (II) LoadModule: "fb"
[   240.436] (II) Loading /usr/lib/xorg/modules/libfb.so
[   240.436] (II) Module fb: vendor="X.Org Foundation"
[   240.436] 	compiled for 1.10.1, module version = 1.0.0
[   240.436] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   240.436] (II) Loading sub module "xaa"
[   240.436] (II) LoadModule: "xaa"
[   240.436] (II) Loading /usr/lib/xorg/modules/libxaa.so
[   240.436] (II) Module xaa: vendor="X.Org Foundation"
[   240.436] 	compiled for 1.10.1, module version = 1.2.1
[   240.436] 	ABI class: X.Org Video Driver, version 10.0
[   240.436] (II) Loading sub module "ramdac"
[   240.436] (II) LoadModule: "ramdac"
[   240.436] (II) Module "ramdac" already built-in
[   240.436] (II) CHROME(0): VIAUnmapMem
[   240.437] (II) UnloadModule: "vesa"
[   240.437] (II) Unloading vesa
[   240.437] (II) UnloadModule: "fbdev"
[   240.437] (II) Unloading fbdev
[   240.437] (II) UnloadModule: "fbdevhw"
[   240.437] (II) Unloading fbdevhw
[   240.437] (--) Depth 24 pixmap format is 32 bpp
[   240.437] (II) CHROME(0): VIAScreenInit
[   240.437] (II) CHROME(0): VIAMapFB
[   240.437] (--) CHROME(0): mapping framebuffer @ 0xa0000000 with size 0x4000000
[   240.448] (--) CHROME(0): Frame buffer start: 0x7f56f7fa8000, free start: 0x753000 end: 0x4000000
[   240.448] (II) CHROME(0): VIAMapMMIO
[   240.448] (--) CHROME(0): mapping MMIO @ 0xc8000000 with size 0x9000
[   240.448] (--) CHROME(0): mapping BitBlt MMIO @ 0xc8200000 with size 0x200000
[   240.449] (II) CHROME(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
[   240.449] (II) CHROME(0): VIASave
[   240.449] (II) CHROME(0): Primary
[   240.450] (II) CHROME(0): Primary Adapter! saving VGA_SR_ALL !!
[   240.450] (II) CHROME(0): Crtc...
[   240.450] (II) CHROME(0): TVSave...
[   240.450] (II) CHROME(0): VIAWriteMode
[   240.450] (II) CHROME(0): ViaModeSet
[   240.450] (II) CHROME(0): Name: 1600x1200
[   240.450] (II) CHROME(0): Clock: 189000
[   240.450] (II) CHROME(0): VRefresh: 70.000000
[   240.450] (II) CHROME(0): HSync: 87.500000
[   240.450] (II) CHROME(0): HDisplay: 1600
[   240.450] (II) CHROME(0): HSyncStart: 1664
[   240.450] (II) CHROME(0): HSyncEnd: 1856
[   240.450] (II) CHROME(0): HTotal: 2160
[   240.450] (II) CHROME(0): HSkew: 0
[   240.450] (II) CHROME(0): VDisplay: 1200
[   240.450] (II) CHROME(0): VSyncStart: 1201
[   240.450] (II) CHROME(0): VSyncEnd: 1204
[   240.450] (II) CHROME(0): VTotal: 1250
[   240.450] (II) CHROME(0): VScan: 0
[   240.450] (II) CHROME(0): Flags: 5
[   240.450] (II) CHROME(0): CrtcHDisplay: 0x640
[   240.450] (II) CHROME(0): CrtcHBlankStart: 0x640
[   240.450] (II) CHROME(0): CrtcHSyncStart: 0x680
[   240.450] (II) CHROME(0): CrtcHSyncEnd: 0x740
[   240.450] (II) CHROME(0): CrtcHBlankEnd: 0x870
[   240.450] (II) CHROME(0): CrtcHTotal: 0x870
[   240.450] (II) CHROME(0): CrtcHSkew: 0x0
[   240.450] (II) CHROME(0): CrtcVDisplay: 0x4b0
[   240.450] (II) CHROME(0): CrtcVBlankStart: 0x4b0
[   240.450] (II) CHROME(0): CrtcVSyncStart: 0x4b1
[   240.450] (II) CHROME(0): CrtcVSyncEnd: 0x4b4
[   240.450] (II) CHROME(0): CrtcVBlankEnd: 0x4e2
[   240.450] (II) CHROME(0): CrtcVTotal: 0x4e2
[   240.450] (II) CHROME(0): ViaDisplaySetStreamOnCRT
[   240.450] (II) CHROME(0): ViaDisplayEnableCRT
[   240.450] (II) CHROME(0): ViaModeFirstCRTC
[   240.450] (II) CHROME(0): ViaFirstCRTCSetMode
[   240.450] (II) CHROME(0): Setting up 1600x1200
[   240.450] (II) CHROME(0): ViaSetPrimaryFIFO
[   240.450] (II) CHROME(0): ViaSetDotclock to 0x04f065
[   240.450] (II) CHROME(0): ViaSetUseExternalClock
[   240.450] (II) CHROME(0): ViaDisplayDisableSimultaneous
[   240.450] (II) CHROME(0): VIAAdjustFrame 0x0
[   240.450] (II) CHROME(0): ViaFirstCRTCSetStartingAddress
[   240.450] (II) CHROME(0): VIAAdjustFrame 0x0
[   240.450] (II) CHROME(0): ViaFirstCRTCSetStartingAddress
[   240.450] (II) CHROME(0): - Blanked
[   240.451] (II) CHROME(0): - Visuals set up
[   240.451] (II) CHROME(0): VIAInternalScreenInit
[   240.451] (II) CHROME(0): - B & W
[   240.451] (II) CHROME(0): CursorStart: 0x3fc0000
[   240.451] (II) CHROME(0): Frame Buffer From (0,0) To (1600,4800)
[   240.451] (II) CHROME(0): Using 3600 lines for offscreen memory.
[   240.451] (II) CHROME(0): Using XFree86 Acceleration Architecture (XAA)
[   240.451] 	Screen to screen bit blits
[   240.451] 	Solid filled rectangles
[   240.451] 	8x8 mono pattern filled rectangles
[   240.451] 	8x8 color pattern filled rectangles
[   240.451] 	Solid Lines
[   240.451] 	Dashed Lines
[   240.452] 	Setting up tile and stipple cache:
[   240.452] 		32 128x128 slots
[   240.452] 		24 256x256 slots
[   240.452] 		13 512x512 slots
[   240.452] 		32 8x8 color pattern slots
[   240.452] (==) CHROME(0): Backing store disabled
[   240.452] (II) CHROME(0): - Backing store set up
[   240.452] (II) CHROME(0): - SW cursor set up
[   240.452] (II) CHROME(0): VIAHWCursorInit
[   240.452] (II) CHROME(0): HWCursor ARGB enabled
[   240.452] (II) CHROME(0): - Def Color map set up
[   240.452] (II) CHROME(0): VIALoadPalette: numColors: 256
[   240.452] (II) CHROME(0): VIALoadRgbLut
[   240.453] (II) CHROME(0): - Palette loaded
[   240.453] (==) CHROME(0): DPMS enabled
[   240.453] (II) CHROME(0): - DPMS set up
[   240.453] (II) CHROME(0): - Color maps etc. set up
[   240.453] (II) CHROME(0): direct rendering disabled
[   240.458] (II) CHROME(0): Using default xfree86 memcpy for video.
[   240.458] (WW) CHROME(0): [XvMC] Cannot use XvMC without DRI!
[   240.458] (II) CHROME(0): - Done
[   240.458] (==) RandR enabled
[   240.458] (II) Initializing built-in extension Generic Event Extension
[   240.458] (II) Initializing built-in extension SHAPE
[   240.458] (II) Initializing built-in extension MIT-SHM
[   240.458] (II) Initializing built-in extension XInputExtension
[   240.458] (II) Initializing built-in extension XTEST
[   240.458] (II) Initializing built-in extension BIG-REQUESTS
[   240.458] (II) Initializing built-in extension SYNC
[   240.458] (II) Initializing built-in extension XKEYBOARD
[   240.458] (II) Initializing built-in extension XC-MISC
[   240.458] (II) Initializing built-in extension SECURITY
[   240.458] (II) Initializing built-in extension XINERAMA
[   240.458] (II) Initializing built-in extension XFIXES
[   240.458] (II) Initializing built-in extension RENDER
[   240.458] (II) Initializing built-in extension RANDR
[   240.458] (II) Initializing built-in extension COMPOSITE
[   240.458] (II) Initializing built-in extension DAMAGE
[   240.458] (II) Initializing built-in extension GESTURE
[   240.474] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
[   240.547] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   240.559] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[   240.559] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   240.559] (II) LoadModule: "evdev"
[   240.560] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   240.560] (II) Module evdev: vendor="X.Org Foundation"
[   240.560] 	compiled for 1.10.0.902, module version = 2.6.0
[   240.560] 	Module class: X.Org XInput Driver
[   240.560] 	ABI class: X.Org XInput driver, version 12.3
[   240.560] (II) Using input driver 'evdev' for 'Power Button'
[   240.561] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   240.561] (**) Power Button: always reports core events
[   240.561] (**) Power Button: Device: "/dev/input/event2"
[   240.561] (--) Power Button: Found keys
[   240.561] (II) Power Button: Configuring as keyboard
[   240.561] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[   240.561] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[   240.561] (**) Option "xkb_rules" "evdev"
[   240.561] (**) Option "xkb_model" "pc105"
[   240.561] (**) Option "xkb_layout" "us"
[   240.563] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[   240.564] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   240.564] (II) Using input driver 'evdev' for 'Power Button'
[   240.564] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   240.564] (**) Power Button: always reports core events
[   240.564] (**) Power Button: Device: "/dev/input/event0"
[   240.564] (--) Power Button: Found keys
[   240.564] (II) Power Button: Configuring as keyboard
[   240.564] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[   240.564] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[   240.564] (**) Option "xkb_rules" "evdev"
[   240.564] (**) Option "xkb_model" "pc105"
[   240.564] (**) Option "xkb_layout" "us"
[   240.565] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[   240.565] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[   240.565] (II) Using input driver 'evdev' for 'Sleep Button'
[   240.565] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   240.565] (**) Sleep Button: always reports core events
[   240.565] (**) Sleep Button: Device: "/dev/input/event1"
[   240.565] (--) Sleep Button: Found keys
[   240.565] (II) Sleep Button: Configuring as keyboard
[   240.565] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1/event1"
[   240.565] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[   240.565] (**) Option "xkb_rules" "evdev"
[   240.565] (**) Option "xkb_model" "pc105"
[   240.565] (**) Option "xkb_layout" "us"
[   240.570] (II) config/udev: Adding input device Logitech Optical USB Mouse (/dev/input/event4)
[   240.570] (**) Logitech Optical USB Mouse: Applying InputClass "evdev pointer catchall"
[   240.570] (II) Using input driver 'evdev' for 'Logitech Optical USB Mouse'
[   240.570] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   240.570] (**) Logitech Optical USB Mouse: always reports core events
[   240.570] (**) Logitech Optical USB Mouse: Device: "/dev/input/event4"
[   240.570] (--) Logitech Optical USB Mouse: Found 3 mouse buttons
[   240.570] (--) Logitech Optical USB Mouse: Found scroll wheel(s)
[   240.570] (--) Logitech Optical USB Mouse: Found relative axes
[   240.570] (--) Logitech Optical USB Mouse: Found x and y relative axes
[   240.570] (II) Logitech Optical USB Mouse: Configuring as mouse
[   240.570] (II) Logitech Optical USB Mouse: Adding scrollwheel support
[   240.570] (**) Logitech Optical USB Mouse: YAxisMapping: buttons 4 and 5
[   240.571] (**) Logitech Optical USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   240.571] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:10.1/usb3/3-1/3-1:1.0/input/input4/event4"
[   240.575] (II) XINPUT: Adding extended input device "Logitech Optical USB Mouse" (type: MOUSE)
[   240.575] (II) Logitech Optical USB Mouse: initialized for relative axes.
[   240.576] (**) Logitech Optical USB Mouse: (accel) keeping acceleration scheme 1
[   240.576] (**) Logitech Optical USB Mouse: (accel) acceleration profile 0
[   240.576] (**) Logitech Optical USB Mouse: (accel) acceleration factor: 2.000
[   240.576] (**) Logitech Optical USB Mouse: (accel) acceleration threshold: 4
[   240.576] (II) config/udev: Adding input device Logitech Optical USB Mouse (/dev/input/mouse0)
[   240.576] (II) No input driver/identifier specified (ignoring)
[   240.579] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[   240.579] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[   240.579] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[   240.579] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   240.579] (**) AT Translated Set 2 keyboard: always reports core events
[   240.579] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[   240.579] (--) AT Translated Set 2 keyboard: Found keys
[   240.579] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[   240.579] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[   240.579] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[   240.579] (**) Option "xkb_rules" "evdev"
[   240.579] (**) Option "xkb_model" "pc105"
[   240.579] (**) Option "xkb_layout" "us"
[   242.977] (II) CHROME(0): VIASwitchMode
[   242.977] (II) CHROME(0): VIAWriteMode
[   242.977] (II) CHROME(0): ViaModeSet
[   242.977] (II) CHROME(0): Name: 1280x960
[   242.977] (II) CHROME(0): Clock: 148500
[   242.977] (II) CHROME(0): VRefresh: 85.002472
[   242.977] (II) CHROME(0): HSync: 85.937500
[   242.977] (II) CHROME(0): HDisplay: 1280
[   242.977] (II) CHROME(0): HSyncStart: 1344
[   242.977] (II) CHROME(0): HSyncEnd: 1504
[   242.977] (II) CHROME(0): HTotal: 1728
[   242.977] (II) CHROME(0): HSkew: 0
[   242.977] (II) CHROME(0): VDisplay: 960
[   242.977] (II) CHROME(0): VSyncStart: 961
[   242.977] (II) CHROME(0): VSyncEnd: 964
[   242.977] (II) CHROME(0): VTotal: 1011
[   242.977] (II) CHROME(0): VScan: 0
[   242.977] (II) CHROME(0): Flags: 5
[   242.977] (II) CHROME(0): CrtcHDisplay: 0x500
[   242.977] (II) CHROME(0): CrtcHBlankStart: 0x500
[   242.977] (II) CHROME(0): CrtcHSyncStart: 0x540
[   242.977] (II) CHROME(0): CrtcHSyncEnd: 0x5e0
[   242.977] (II) CHROME(0): CrtcHBlankEnd: 0x6c0
[   242.977] (II) CHROME(0): CrtcHTotal: 0x6c0
[   242.977] (II) CHROME(0): CrtcHSkew: 0x0
[   242.977] (II) CHROME(0): CrtcVDisplay: 0x3c0
[   242.977] (II) CHROME(0): CrtcVBlankStart: 0x3c0
[   242.977] (II) CHROME(0): CrtcVSyncStart: 0x3c1
[   242.977] (II) CHROME(0): CrtcVSyncEnd: 0x3c4
[   242.977] (II) CHROME(0): CrtcVBlankEnd: 0x3f3
[   242.977] (II) CHROME(0): CrtcVTotal: 0x3f3
[   242.977] (II) CHROME(0): ViaDisplaySetStreamOnCRT
[   242.977] (II) CHROME(0): ViaDisplayEnableCRT
[   242.977] (II) CHROME(0): ViaModeFirstCRTC
[   242.977] (II) CHROME(0): ViaFirstCRTCSetMode
[   242.977] (II) CHROME(0): Setting up 1280x960
[   242.977] (II) CHROME(0): ViaSetPrimaryFIFO
[   242.977] (II) CHROME(0): ViaSetDotclock to 0x053049
[   242.977] (II) CHROME(0): ViaSetUseExternalClock
[   242.977] (II) CHROME(0): ViaDisplayDisableSimultaneous
[   242.978] (II) CHROME(0): VIAAdjustFrame 0x0
[   242.978] (II) CHROME(0): ViaFirstCRTCSetStartingAddress
[   242.978] (II) CHROME(0): VIALoadPalette: numColors: 256
[   242.978] (II) CHROME(0): VIALoadRgbLut
[   242.978] (II) CHROME(0): VIAAdjustFrame 0x0
[   242.978] (II) CHROME(0): ViaFirstCRTCSetStartingAddress
[   242.978] (II) CHROME(0): VIAAdjustFrame 1x1
[   242.978] (II) CHROME(0): ViaFirstCRTCSetStartingAddress
[   242.978] (II) CHROME(0): VIAAdjustFrame 0x0
[   242.978] (II) CHROME(0): ViaFirstCRTCSetStartingAddress

---

### Post by Blue_Mercury on 2011-05-08
I reformatted and installed Ubuntu 10.04 to solve this issue
Videos play perfectly

---

### Post by raxhonp on 2011-05-10
I have the same problem, it appears to come from the driver for the VIA embedded video chipsets (OpenChrome), as already reported in various places on this forum:
- [http://ubuntuforums.org/showthread.php?t=1752988](http://ubuntuforums.org/showthread.php?t=1752988)
- [http://ubuntuforums.org/showthread.php?p=10759093](http://ubuntuforums.org/showthread.php?p=10759093)

As soon as a video is playing in VLC, mplayer ... a click on the desktop would cause the x server to crash and the session to restart. I noticed that pausing the video using the keyboard (hitting space) doesn't crash X.

Other than reformatting and installing Ubuntu 10.04, something I would prefer not to have to do, what else can be done?

KR

---

### Post by Blue_Mercury on 2011-05-10
Unfortunately I formatted my computer because I could not find a solution to this.

---

### Post by FrDarryl on 2011-05-10
Same here. If I limit events/ops to the media player app itself (including totem, mplayer and banshee) doesn't necessarily kill my login (some sort of seg vio?). But whilst running media, if I do a mouse-driven event in another app, or even on Unity real estate, the evil kill occurs - consistently. Very annoying.

---

### Post by Blue_Mercury on 2011-05-10
You could try reinstalling 11.04 instead of dropping back to 10.04.
In my experience on several computers upgrading from 8.10 to 11.04 without missing any distribution on several different computers and generally I find unexpected issues arise after an upgrade that do not occur after a clean install.

---

### Post by asdacap on 2011-05-27
Change the driver to vesa solves the problem. But when playing video, cpu usage will be very high (constant 100%), and it's not a very good experience at all. But still, even with the openchrome driver working, I think it will still use very high cpu. But in my monitor, vesa has another problem, it cannot use 1600x900 resolution. The monitor setting enable me to set 1600x900, but my monitor only detect 1400x900, meaning 1600x900 mode is a stretched 1400x900 mode, so it's look ugly. But don't worry, I'll get myself a cheap ATI or Nvidia card as soon as I can.:)

---

### Post by linuxinstalledfromhdd on 2011-05-27
I have found dropping back to 10.10 has solved some issues that I couldn't get resolved in 11.04.  It's really up to you if you want to hang in there or you need a working system now.

---

### Post by raxhonp on 2011-06-15
See [http://ubuntuforums.org/showpost.php?p=10941121&postcount=12](http://ubuntuforums.org/showpost.php?p=10941121&postcount=12). That could solve your problem for good.

---

