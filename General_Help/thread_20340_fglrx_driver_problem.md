---
title: "fglrx driver problem"
date: 2005-03-16
forum: General Help
---

### Post by mythagel on 2005-03-16
Hello all,

I'm running ubuntu Hoary and when i enable the fglrx driver in xorg.conf, my monitor switches to sleep mode.

I;ve got a Raedon 9100 IGP which is supported, and i don't have this problem with the ati driver.
I *know* my monitor supports 1600x1200 at 65hz because that's what i'm running atm, which is why i'm puzzled that the monitor sleeps as if an invalid mode is being used.

i've included below relevant parts of my x.org log file.

cheers,

-nick

--



(II) Primary Device is: PCI 01:05:0
(--) Chipset RADEON 9100 IGP (RS300 5834) found
(II) Setting vga for screen 0.
(II) fglrx(0): === [R200PreInit] === begin, [s]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/X11R6/lib/modules/libvgahw.a
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.7
(II) fglrx(0): PCI bus 1 card 5 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(==) fglrx(0): Qbs disabled
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) fglrx(0): initializing int10
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(--) fglrx(0): Chipset: "RADEON 9100 IGP (RS300 5834)" (Chipset = 0x5834)
(--) fglrx(0): (PciSubVendor = 0x1043, PciSubDevice = 0x8107)
(--) fglrx(0): board vendor info: third party grafics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xe8000000
(--) fglrx(0): MMIO registers at 0xfd800000
(--) fglrx(0): ROM-BIOS at 0xfd700000
(--) fglrx(0): ChipExtRevID = 0x00
(--) fglrx(0): ChipIntRevID = 0x01
(--) fglrx(0): VideoRAM: 65536 kByte (64-bit DDR SDRAM)
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/X11R6/lib/modules/libddc.a
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Loading /usr/X11R6/lib/modules/libi2c.a
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.7
(II) fglrx(0): I2C bus "DDC" initialized.
(II) fglrx(0): Connector Layout from BIOS -------- 
(II) fglrx(0): Connector0: DDCType-3, DACType-0, TMDSType--1, ConnectorType-2
(II) fglrx(0): Connector1: DDCType-4, DACType-1, TMDSType-1, ConnectorType-4
(II) fglrx(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) fglrx(0): I2C device "DDC:ddc2" removed.
(II) fglrx(0): DDC detected on DDCType 3 with Monitor Type 1
(II) fglrx(0): Primary head:
 Monitor   -- CRT
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- NONE
 DDC Type  -- VGA_DDC
(II) fglrx(0): Secondary head:
 Monitor   -- NONE
 Connector -- DVI-D
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- External
 DDC Type  -- CRT2_DDC
(II) fglrx(0): EDID data from the display on Primary head ----------------
(II) fglrx(0): Manufacturer: SAM  Model: 48  Serial#: 1128345911
(II) fglrx(0): Year: 2003  Week: 12
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) fglrx(0): Sync:  Separate
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 32  vert.: 24
(II) fglrx(0): Gamma: 2.26
(II) fglrx(0): DPMS capabilities: Off; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.645 redY: 0.318   greenX: 0.276 greenY: 0.596
(II) fglrx(0): blueX: 0.145 blueY: 0.060   whiteX: 0.283 whiteY: 0.298
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@67Hz
(II) fglrx(0): 640x480@72Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@72Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 832x624@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@70Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 640  vsize 480  refresh: 60  vid: 16433
(II) fglrx(0): #1: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) fglrx(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) fglrx(0): #3: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) fglrx(0): #4: hsize: 1280  vsize 1024  refresh: 75  vid: 36737
(II) fglrx(0): #5: hsize: 1600  vsize 1200  refresh: 65  vid: 17833
(II) fglrx(0): #6: hsize: 1792  vsize 1344  refresh: 60  vid: 16577
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 94.5 MHz   Image Size:  312 x 234 mm
(II) fglrx(0): h_active: 1024  h_sync: 1072  h_sync_end 1168 h_blank_end 1376 h_border: 0
(II) fglrx(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 808 v_border: 0
(II) fglrx(0): Ranges: V min: 50  V max: 160 Hz, H min: 30  H max: 85 kHz, PixClock max 180 MHz
(II) fglrx(0): Monitor name: SyncMaster
(II) fglrx(0): Serial No: HMAW303813
(II) fglrx(0): 
(II) fglrx(0): DesktopSetup 0x0000
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Overlay disabled
(==) fglrx(0): Overlay disabled
(II) fglrx(0): PLL parameters: rf=1432 rd=6 min=20000 max=35000
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total 0 valid mode(s) found.
(II) fglrx(0): SyncMaster: Using hsync range of 30.00-85.00 kHz
(II) fglrx(0): SyncMaster: Using vrefresh range of 50.00-160.00 Hz
(II) fglrx(0): Clock range:  20.00 to 350.00 MHz
(II) fglrx(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1280x960" (hsync out of range)
(II) fglrx(0): Not using default mode "640x480" (hsync out of range)
(II) fglrx(0): Not using default mode "1280x1024" (hsync out of range)
(II) fglrx(0): Not using default mode "640x512" (hsync out of range)
(II) fglrx(0): Not using default mode "1600x1200" (hsync out of range)
(II) fglrx(0): Not using default mode "800x600" (hsync out of range)
(II) fglrx(0): Not using default mode "1600x1200" (hsync out of range)
(II) fglrx(0): Not using default mode "800x600" (hsync out of range)
(II) fglrx(0): Not using default mode "1600x1200" (hsync out of range)
(II) fglrx(0): Not using default mode "800x600" (hsync out of range)
(WW) (1792x1344,SyncMaster) mode clock 204.8MHz exceeds DDC maximum 180MHz
(II) fglrx(0): Not using default mode "1792x1344" (hsync out of range)
(II) fglrx(0): Not using default mode "896x672" (hsync out of range)
(II) fglrx(0): Not using default mode "1856x1392" (hsync out of range)
(II) fglrx(0): Not using default mode "928x696" (hsync out of range)
(II) fglrx(0): Not using default mode "1856x1392" (hsync out of range)
(II) fglrx(0): Not using default mode "928x696" (hsync out of range)
(II) fglrx(0): Not using default mode "1920x1440" (hsync out of range)
(II) fglrx(0): Not using default mode "960x720" (hsync out of range)
(II) fglrx(0): Not using default mode "1920x1440" (hsync out of range)
(II) fglrx(0): Not using default mode "960x720" (hsync out of range)
(II) fglrx(0): Not using default mode "1400x1050" (hsync out of range)
(II) fglrx(0): Not using default mode "700x525" (hsync out of range)
(II) fglrx(0): Not using default mode "1920x1200" (hsync out of range)
(II) fglrx(0): Not using default mode "960x600" (hsync out of range)
(II) fglrx(0): Not using default mode "1920x1440" (hsync out of range)
(II) fglrx(0): Not using default mode "960x720" (hsync out of range)
(II) fglrx(0): Not using default mode "2048x1536" (hsync out of range)
(II) fglrx(0): Not using default mode "1024x768" (hsync out of range)
(II) fglrx(0): Not using default mode "2048x1536" (hsync out of range)
(II) fglrx(0): Not using default mode "1024x768" (hsync out of range)
(II) fglrx(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1024x768" (hsync out of range)
(II) fglrx(0): Not using default mode "1792x1344" (width too large for virtual size)
(--) fglrx(0): Virtual size is 1600x1200 (pitch 1600)
(**) fglrx(0): *Default mode "1600x1200": 175.5 MHz, 81.2 kHz, 65.0 Hz
(II) fglrx(0): Modeline "1600x1200"  175.50  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync
(**) fglrx(0): *Default mode "1280x1024": 135.0 MHz, 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(**) fglrx(0): *Default mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1024x768"   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync
(**) fglrx(0): *Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) fglrx(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(**) fglrx(0): *Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
(II) fglrx(0): Modeline "800x600"   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync
(**) fglrx(0): *Default mode "720x400": 35.5 MHz, 37.9 kHz, 85.0 Hz
(II) fglrx(0): Modeline "720x400"   35.50  720 756 828 936  400 401 404 446 -hsync +vsync
(**) fglrx(0): *Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(II) fglrx(0): Modeline "640x480"   36.00  640 696 752 832  480 481 484 509 -hsync -vsync
(**) fglrx(0):  Default mode "1600x1200": 162.0 MHz, 75.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1600x1200"  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync
(**) fglrx(0):  Default mode "1400x1050": 155.8 MHz, 81.5 kHz, 74.8 Hz
(II) fglrx(0): Modeline "1400x1050"  155.80  1400 1464 1784 1912  1050 1052 1064 1090 +hsync +vsync
(**) fglrx(0):  Default mode "1400x1050": 151.0 MHz, 77.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1400x1050"  151.00  1400 1464 1656 1960  1050 1051 1054 1100 +hsync +vsync
(**) fglrx(0):  Default mode "1400x1050": 122.0 MHz, 64.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1400x1050"  122.00  1400 1488 1640 1880  1050 1052 1064 1082 +hsync +vsync
(**) fglrx(0):  Default mode "1280x1024": 108.0 MHz, 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync
(**) fglrx(0):  Default mode "1440x900": 108.8 MHz, 56.9 kHz, 60.2 Hz
(II) fglrx(0): Modeline "1440x900"  108.84  1440 1472 1880 1912  900 918 927 946 +hsync +vsync
(**) fglrx(0):  Default mode "1280x960": 108.0 MHz, 60.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x960"  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync
(**) fglrx(0):  Default mode "1152x864": 121.5 MHz, 77.5 kHz, 85.1 Hz
(II) fglrx(0): Modeline "1152x864"  121.50  1152 1216 1344 1568  864 865 868 911 +hsync -vsync
(**) fglrx(0):  Default mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
(**) fglrx(0):  Default mode "1152x768": 65.0 MHz, 44.2 kHz, 54.8 Hz
(II) fglrx(0): Modeline "1152x768"   65.00  1152 1178 1314 1472  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 78.8 MHz, 60.1 kHz, 75.1 Hz
(II) fglrx(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) fglrx(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) fglrx(0):  Default mode "1024x768": 44.9 MHz, 35.5 kHz, 87.1 Hz (I)
(II) fglrx(0): Modeline "1024x768"   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync
(**) fglrx(0):  Default mode "896x672": 102.4 MHz, 83.7 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "896x672"  102.40  896 960 1060 1224  672 672 674 697 doublescan -hsync +vsync
(**) fglrx(0):  Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(**) fglrx(0):  Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) fglrx(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(**) fglrx(0):  Default mode "800x600": 87.8 MHz, 81.2 kHz, 65.0 Hz (D)
(II) fglrx(0): Modeline "800x600"   87.75  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync
(**) fglrx(0):  Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) fglrx(0):  Default mode "800x600": 81.0 MHz, 75.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "800x600"   81.00  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync
(**) fglrx(0):  Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(**) fglrx(0):  Default mode "700x525": 77.9 MHz, 81.5 kHz, 74.8 Hz (D)
(II) fglrx(0): Modeline "700x525"   77.90  700 732 892 956  525 526 532 545 doublescan +hsync +vsync
(**) fglrx(0):  Default mode "700x525": 75.5 MHz, 77.0 kHz, 70.0 Hz (D)
(II) fglrx(0): Modeline "700x525"   75.50  700 732 828 980  525 525 527 550 doublescan +hsync +vsync
(**) fglrx(0):  Default mode "700x525": 61.0 MHz, 64.9 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "700x525"   61.00  700 744 820 940  525 526 532 541 doublescan +hsync +vsync
(**) fglrx(0):  Default mode "640x512": 67.5 MHz, 80.0 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "640x512"   67.50  640 648 720 844  512 512 514 533 doublescan +hsync +vsync
(**) fglrx(0):  Default mode "640x512": 54.0 MHz, 64.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "640x512"   54.00  640 664 720 844  512 512 514 533 doublescan +hsync +vsync
(**) fglrx(0):  Default mode "720x450": 54.4 MHz, 56.9 kHz, 60.2 Hz (D)
(II) fglrx(0): Modeline "720x450"   54.42  720 736 940 956  450 459 463 473 doublescan +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(**) fglrx(0):  Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(**) fglrx(0):  Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "640x480"   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync
(**) fglrx(0):  Default mode "640x400": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) fglrx(0): Modeline "640x400"   31.50  640 672 736 832  400 401 404 445 -hsync +vsync
(**) fglrx(0):  Default mode "576x432": 60.8 MHz, 77.5 kHz, 85.2 Hz (D)
(II) fglrx(0): Modeline "576x432"   60.75  576 608 672 784  432 432 434 455 doublescan +hsync -vsync
(**) fglrx(0):  Default mode "576x432": 54.0 MHz, 67.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "576x432"   54.00  576 608 672 800  432 432 434 450 doublescan +hsync +vsync
(**) fglrx(0):  Default mode "640x350": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) fglrx(0): Modeline "640x350"   31.50  640 672 736 832  350 382 385 445 +hsync -vsync
(**) fglrx(0):  Default mode "576x384": 32.5 MHz, 44.2 kHz, 54.8 Hz (D)
(II) fglrx(0): Modeline "576x384"   32.50  576 589 657 736  384 385 388 403 doublescan +hsync +vsync
(**) fglrx(0):  Default mode "512x384": 47.2 MHz, 68.7 kHz, 85.0 Hz (D)
(II) fglrx(0): Modeline "512x384"   47.25  512 536 584 688  384 384 386 404 doublescan +hsync +vsync
(**) fglrx(0):  Default mode "512x384": 39.4 MHz, 60.1 kHz, 75.1 Hz (D)
(II) fglrx(0): Modeline "512x384"   39.40  512 520 568 656  384 384 386 400 doublescan +hsync +vsync
(**) fglrx(0):  Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)
(II) fglrx(0): Modeline "512x384"   37.50  512 524 592 664  384 385 388 403 doublescan -hsync -vsync
(**) fglrx(0):  Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "512x384"   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync
(**) fglrx(0):  Default mode "512x384": 22.4 MHz, 35.5 kHz, 87.1 Hz (D)
(II) fglrx(0): Modeline "512x384"   22.45  512 516 604 632  384 384 388 409 interlace doublescan +hsync +vsync
(**) fglrx(0):  Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(II) fglrx(0): Modeline "416x312"   28.64  416 432 464 576  312 312 314 333 doublescan -hsync -vsync
(**) fglrx(0):  Default mode "400x300": 28.1 MHz, 53.7 kHz, 85.3 Hz (D)
(II) fglrx(0): Modeline "400x300"   28.15  400 416 448 524  300 300 302 315 doublescan +hsync +vsync
(**) fglrx(0):  Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(II) fglrx(0): Modeline "400x300"   24.75  400 408 448 528  300 300 302 312 doublescan +hsync +vsync
(**) fglrx(0):  Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(II) fglrx(0): Modeline "400x300"   25.00  400 428 488 520  300 318 321 333 doublescan +hsync +vsync
(**) fglrx(0):  Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) fglrx(0): Modeline "400x300"   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync
(--) fglrx(0): Display dimensions: (320, 240) mm
(--) fglrx(0): DPI set to (126, 126)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/X11R6/lib/modules/libfb.a
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
(II) Module fb: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/X11R6/lib/modules/libramdac.a
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.7
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/X11R6/lib/modules/libxaa.a
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.7
(==) fglrx(0): HPV inactive
(==) fglrx(0): FSAA enabled: NO
(==) fglrx(0): FSAA Gamma enabled
(==) fglrx(0): FSAA Multisample Position is fix
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/X11R6/lib/modules/linux/libfglrxdrm.a
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 4.3.99.902, module version = 8.8.25
	ABI class: X.Org Server Extension, version 0.2
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): cpuFlags: 0x8000001d
(==) fglrx(0): cpuSpeedMHz: 0x00000bb2
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) fglrx(0): Composite extension enabled, disabling direct rendering
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0x3c000000 FBMappedSize: 0x04000000
(==) fglrx(0): Write-combining range (0xe8000000,0x4000000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1600,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1600,1200) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(II) fglrx(0): Using hardware cursor (scanline 1200)
(II) fglrx(0): Largest offscreen area available: 1600 x 6988
(**) Option "dpms"
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid Horizontal and Vertical Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): Direct rendering disabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(==) RandR enabled
(II) Setting vga for screen 0.

---

### Post by bobmitch on 2005-03-16
Try commenting out the composite extension section in your xorg.conf.
The fglrx driver doesn`t like it.
Hope this helps.

---

### Post by mythagel on 2005-03-16
switched off composite and still no dice...

the screen just goes into sleep mode when the fglrx driver is loaded rather than the ati driver

---

### Post by bobmitch on 2005-03-17
I`m assuming because you had a composite extension section, that you simply altered the xorg.conf manually?

I`ve only ever had success with fglrx using ati's **fglrxconfig** configuration file generation utility.

Run it as sudo from a terminal and answer the questions, and it`ll create an appropriate xorg.conf file for you.

If you are unsure of an answer, just hit return to accept the default - they are mostly ok - except for the agpgart option - choose the opposite of the default for that one.

Good luck.

---

### Post by henriavelabarbe on 2005-03-17
try this : check that you don't have drm module built-in your kernel

#zcat /proc/config.gz | grep DRM

If you see CONFIG_DRM=y, then you may be out of luck.
You may have to reconfigure your kernel with DRM=n.

---

### Post by mythagel on 2005-03-17
excellent, i'll give this a try when i get home tonight and i'll let you know how i go.

yeah i modified xorg.conf manually first to add the composite extension and then to change the driver from ati to fglrx.

totally unrelated side note, xcompmgr looks amazing when enabled

very very nice

-nick

---

