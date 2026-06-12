---
title: "scrolling crashes x server"
date: 2009-08-14
forum: General Help
---

### Post by treehouse on 2009-08-14
I just upgraded to 9.04. Whenever I scroll in any web browser (Firefox, Galeon, and Kazehakaze all included), and many other programs, X server restarts, and I have to log in again to a blank session. This is crippling my ability to use my computer. I can't even scroll through the known bug thread to find a solution, as it will kill my whole session. I have no idea how to begin fixing this problem whatsoever and I need a solution that involves not scrolling a page on a 1280x1040 monitor.

---

### Post by SoftwareExplorer on 2009-08-14
Try this: Ctrl + Alt + F4. You are now on virtual screen 4. Most graphical virtual screens start with 7.
Login.  Run 'less /var/log/Xorg.0.log' to try to find the problem. Space will take you to the next screen of text.
Ctrl + Alt + F7 (or whatever Function key gets you the graphical interface.)
Report back.
PS:does a link like [COLOR=SeaGreen][this]("http://ubuntuforums.org/showthread.php?t=1240611&goto=newpost")[/COLOR] let you see the end of the thread, or does it cause a crash?
---------old post-------
It just when you use your scroll wheel, or is it when you use the scroll bars on programs to? If it's with the scroll bars, its probably a video card thing, in which case people will want to know what video card you are using.

(Let me take my 33% chance correct guess: it's an Intel card)

---

### Post by treehouse on 2009-08-14
Anything that either I do or a program does that causes the window to scroll crashes it. My video card is a 3dfx Voodoo3. This reply will bring the thread below the window, so I'm going to have to figure out a way to read any more replies now...

---

### Post by Finalfantasykid on 2009-08-14
If you are able to, can you check what your log file says?  Administration > Log File Viewer > Xorg.0.log

There is lots of scrolling, but the program is simple enough that it might not break your session.  Scroll down to the bottom, and it might give you some insight on the reason for why it is crashing.  It might be that you are not using the right drivers for your system or something like that.

Also for a temporary fix for while you try to fix the problem, you might be able to try lowering the resolution of your screen so that there is less stress of the graphics card.

---

### Post by SoftwareExplorer on 2009-08-14
I just 'added' a new 'post'. I edited my first post in case you can't read this one. I added this so that you will get the message that the thread has updated.

---

### Post by treehouse on 2009-08-15
nothing in the log seems out of line. None of the lines are preceded by (!!) and they all seem in line with the settings for my card and my fstab. Here's the lines if there's anything you know to look for but I wouldn't blame you for not reading this hug chunk of stuff.

```

(II) Loading /usr/lib/xorg/modules/drivers//tdfx_drv.so
(II) Module tdfx: vendor="X.Org Foundation"
        compiled for 1.5.99.3, module version = 1.4.0
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 5.0
(II) TDFX: Driver for 3dfx Banshee/Voodoo3 chipsets: 3dfx Banshee,
        3dfx Voodoo3, 3dfx Voodoo5
(II) Primary Device is: PCI 00@00:09:0
(II) TDFX(0): PIO base = 0xe400
(II) resource ranges after probing:
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x00000000 (0x1) IX[B]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 0.1.0
        ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 5.0
(II) TDFX(0): Softbooting the board (through the int10 interface).
(II) TDFX(0): Primary V_BIOS segment is: 0xc000
(II) TDFX(0): Softbooting the board succeeded.
(**) TDFX(0): Depth 16, (--) framebuffer bpp 16
(==) TDFX(0): RGB weight 565
(==) TDFX(0): Default visual is TrueColor
(--) TDFX(0): Chipset: "3dfx Voodoo3"
(--) TDFX(0): Linear framebuffer at 0xD6000000
(--) TDFX(0): MMIO registers at addr 0xD4000000
(--) TDFX(0): PIO registers at addr 0xE400
(II) TDFX(0): DRAMINIT1 read 0x202031, programming 0x202031 (not Banshee)
(II) TDFX(0): TDFXInitChips: numchips = 1
(II) TDFX(0): TDFXInitChips: cfgbits = 0x00000000, initbits = 0x00000001
(II) TDFX(0): TDFXInitChips: mem0base = 0xd4000000, mem1base = 0xd6000008
(II) TDFX(0): TDFXInitChips: mem0size = 0x02000000, mem1size = 0x02000000
(II) TDFX(0): TDFXInitChips: mem0bits = 0x00000005, mem1bits = 0x00000050
(II) TDFX(0): TDFXInitChips: cfgbits = 0x00000055
(II) TDFX(0): TDFXInitChips: MMIOAddr[0] = 0xd4000000
(II) TDFX(0): TDFXInitChips: LinearAddr[0] = 0xd6000008
(--) TDFX(0): VideoRAM: 16384 kByte Mapping 32768 kByte
(==) TDFX(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.2.1
        ABI class: X.Org Video Driver, version 5.0
(**) TDFX(0): ShowCache Disabled
(**) TDFX(0): video key default 0x1e
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) TDFX(0): I2C bus "DDC" initialized.
(II) TDFX(0): I2C device "DDC:E-EDID segment register" registered at address 0x60.
(II) TDFX(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) TDFX(0): Manufacturer: STN  Model: 6  Serial#: 1347301687
(II) TDFX(0): Year: 2002  Week: 36
(II) TDFX(0): EDID Version: 1.3
(II) TDFX(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) TDFX(0): Sync:  Separate
(II) TDFX(0): Max Image Size [cm]: horiz.: 32  vert.: 24
(II) TDFX(0): Gamma: 2.08
(II) TDFX(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) TDFX(0): First detailed timing is preferred mode
(II) TDFX(0): GTF timings supported
(II) TDFX(0): redX: 0.639 redY: 0.323   greenX: 0.275 greenY: 0.597
(II) TDFX(0): blueX: 0.143 blueY: 0.062   whiteX: 0.283 whiteY: 0.298
(II) TDFX(0): Supported VESA Video Modes:
(II) TDFX(0): 720x400@70Hz
(II) TDFX(0): 720x400@88Hz
(II) TDFX(0): 640x480@60Hz
(II) TDFX(0): 640x480@67Hz
(II) TDFX(0): 640x480@72Hz
(II) TDFX(0): 640x480@75Hz
(II) TDFX(0): 800x600@56Hz
(II) TDFX(0): 800x600@60Hz
(II) TDFX(0): 800x600@72Hz
(II) TDFX(0): 800x600@75Hz
(II) TDFX(0): 832x624@75Hz
(II) TDFX(0): 1024x768@87Hz (interlaced)
(II) TDFX(0): 1024x768@60Hz
(II) TDFX(0): 1024x768@70Hz
(II) TDFX(0): 1024x768@75Hz
(II) TDFX(0): 1152x870@75Hz
(II) TDFX(0): Manufacturer's mask: 0
(II) TDFX(0): Supported Future Video Modes:
(II) TDFX(0): #0: hsize: 640  vsize 480  refresh: 60  vid: 16433
(II) TDFX(0): #1: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) TDFX(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) TDFX(0): #3: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) TDFX(0): #4: hsize: 1280  vsize 1024  refresh: 65  vid: 34177
(II) TDFX(0): Supported additional Video Mode:
(II) TDFX(0): clock: 94.5 MHz   Image Size:  312 x 234 mm
(II) TDFX(0): h_active: 1024  h_sync: 1072  h_sync_end 1168 h_blank_end 1376 h_border: 0
(II) TDFX(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 808 v_border: 0
(II) TDFX(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 70 kHz, PixClock max 110 MHz
(II) TDFX(0): Monitor name: S/T 77/76DFX
(II) TDFX(0): Serial No: HMAT901774
(II) TDFX(0): EDID (in hex):
(II) TDFX(0):   00ffffffffffff004e8e060037314e50
(II) TDFX(0):   240c01030820186cebbbb9a352469824
(II) TDFX(0):   0f484cfffe8031403159455961598185
(II) TDFX(0):   010101010101ea240060410028303060
(II) TDFX(0):   130038ea1000001e000000fd0032a01e
(II) TDFX(0):   460b000a202020202020000000fc0053
(II) TDFX(0):   2f542037372f37364446580a000000ff
(II) TDFX(0):   00484d41543930313737340a202000d0
(II) TDFX(0): EDID vendor "STN", prod id 6
(II) TDFX(0): Using hsync ranges from config file
(II) TDFX(0): Using vrefresh ranges from config file
(II) TDFX(0): Printing DDC gathered Modelines:
(II) TDFX(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772808 +hsync +vsync (68.7 kHz)
(II) TDFX(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628+hsync +vsync (37.9 kHz)
(II) TDFX(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625:
+hsync +vsync (35.2 kHz)
(II) TDFX(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) TDFX(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) TDFX(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) TDFX(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) TDFX(0): Modeline "720x400"x0.0   35.50  720 738 846 900  400 421 423 449 -hsync -vsync (39.4 kHz)
(II) TDFX(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) TDFX(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772800 +hsync +vsync (60.0 kHz)
(II) TDFX(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777806 -hsync -vsync (56.5 kHz)
(II) TDFX(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777806 -hsync -vsync (48.4 kHz)
(II) TDFX(0): Modeline "1024x768"x0.0   44.90  1024 1032 1208 1264  768 768 772817 interlace +hsync +vsync (35.5 kHz)
(II) TDFX(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667-hsync -vsync (49.7 kHz)
(II) TDFX(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625+hsync +vsync (46.9 kHz)
(II) TDFX(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666+hsync +vsync (48.1 kHz)
(II) TDFX(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868900 +hsync +vsync (67.5 kHz)
(II) TDFX(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) TDFX(0): Modeline "640x480"x0.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) TDFX(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631+hsync +vsync (53.7 kHz)
(II) TDFX(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772808 +hsync +vsync (68.7 kHz)
(II) TDFX(0): Modeline "1280x1024"x65.0  119.40  1280 1368 1504 1728  1024 10251028 1063 -hsync +vsync (69.1 kHz)
(II) TDFX(0): Generic Monitor: Using hsync range of 30.00-70.00 kHz
(II) TDFX(0): Generic Monitor: Using vrefresh range of 50.00-160.00 Hz
(II) TDFX(0): Generic Monitor: Using maximum pixel clock of 110.00 MHz
(II) TDFX(0): Clock range:  12.00 to 300.00 MHz
(II) TDFX(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) TDFX(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) TDFX(0): Not using default mode "1280x960" (hsync out of range)
(II) TDFX(0): Not using default mode "640x480" (hsync out of range)
(II) TDFX(0): Not using default mode "1280x1024" (hsync out of range)
(II) TDFX(0): Not using default mode "640x512" (hsync out of range)
(II) TDFX(0): Not using default mode "1280x1024" (hsync out of range)
(II) TDFX(0): Not using default mode "640x512" (hsync out of range)
(II) TDFX(0): Not using default mode "1600x1200" (hsync out of range)
(II) TDFX(0): Not using default mode "800x600" (hsync out of range)
(II) TDFX(0): Not using default mode "1600x1200" (hsync out of range)
(II) TDFX(0): Not using default mode "800x600" (hsync out of range)
(II) TDFX(0): Not using default mode "1600x1200" (hsync out of range)
(II) TDFX(0): Not using default mode "800x600" (hsync out of range)
(II) TDFX(0): Not using default mode "1600x1200" (hsync out of range)
(II) TDFX(0): Not using default mode "800x600" (hsync out of range)
(II) TDFX(0): Not using default mode "1600x1200" (hsync out of range)
(II) TDFX(0): Not using default mode "800x600" (hsync out of range)
(II) TDFX(0): Not using default mode "1792x1344" (hsync out of range)
(II) TDFX(0): Not using default mode "896x672" (hsync out of range)
(II) TDFX(0): Not using default mode "1792x1344" (hsync out of range)
(II) TDFX(0): Not using default mode "896x672" (hsync out of range)
(II) TDFX(0): Not using default mode "1856x1392" (hsync out of range)
(II) TDFX(0): Not using default mode "928x696" (hsync out of range)
(II) TDFX(0): Not using default mode "1856x1392" (hsync out of range)
(II) TDFX(0): Not using default mode "928x696" (hsync out of range)
(II) TDFX(0): Not using default mode "1920x1440" (hsync out of range)
(II) TDFX(0): Not using default mode "960x720" (hsync out of range)
(II) TDFX(0): Not using default mode "1920x1440" (hsync out of range)
(II) TDFX(0): Not using default mode "960x720" (hsync out of range)
(II) TDFX(0): Not using default mode "1152x864" (hsync out of range)
(II) TDFX(0): Not using default mode "576x432" (hsync out of range)
(II) TDFX(0): Not using default mode "1152x864" (hsync out of range)
(II) TDFX(0): Not using default mode "576x432" (hsync out of range)
(II) TDFX(0): Not using default mode "1152x864" (hsync out of range)
(II) TDFX(0): Not using default mode "576x432" (hsync out of range)
(II) TDFX(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) TDFX(0): Not using default mode "1400x1050" (mode clock too high)
(II) TDFX(0): rejecting mode with horizontal resolution 1400 not divisibile by 16 and clock 145060 greater than 135000
(II) TDFX(0): Not using default mode "1400x1050" (unknown reason)
(II) TDFX(0): Not using default mode "700x525" (hsync out of range)
(II) TDFX(0): rejecting mode with horizontal resolution 1400 not divisibile by 16 and clock 155800 greater than 135000
(II) TDFX(0): Not using default mode "1400x1050" (unknown reason)
(II) TDFX(0): Not using default mode "700x525" (hsync out of range)
(II) TDFX(0): rejecting mode with horizontal resolution 1400 not divisibile by 16 and clock 179260 greater than 135000
(II) TDFX(0): Not using default mode "1400x1050" (unknown reason)
(II) TDFX(0): Not using default mode "700x525" (hsync out of range)
(II) TDFX(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) TDFX(0): Not using default mode "1680x1050" (mode clock too high)
(II) TDFX(0): Not using default mode "1680x1050" (hsync out of range)
(II) TDFX(0): Not using default mode "840x525" (hsync out of range)
(II) TDFX(0): Not using default mode "1680x1050" (hsync out of range)
(II) TDFX(0): Not using default mode "840x525" (hsync out of range)
(II) TDFX(0): Not using default mode "1680x1050" (hsync out of range)
(II) TDFX(0): Not using default mode "840x525" (hsync out of range)
(II) TDFX(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) TDFX(0): Not using default mode "1920x1200" (hsync out of range)
(II) TDFX(0): Not using default mode "960x600" (hsync out of range)
(II) TDFX(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) TDFX(0): Not using default mode "960x720" (hsync out of range)
(II) TDFX(0): Not using default mode "2048x1536" (hsync out of range)
(II) TDFX(0): Not using default mode "1024x768" (hsync out of range)
(II) TDFX(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) TDFX(0): Not using default mode "1024x768" (hsync out of range)
(II) TDFX(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) TDFX(0): Not using default mode "1024x768" (hsync out of range)
(II) TDFX(0): Not using driver mode "1024x768" (bad mode clock/interlace/doublescan)
(II) TDFX(0): Not using driver mode "1280x1024" (mode clock too high)
(II) TDFX(0): Not using default mode "1440x900" (width too large for virtual size)
(II) TDFX(0): Not using default mode "1360x768" (width too large for virtual size)
(--) TDFX(0): Virtual size is 1280x1024 (pitch 1280)
(**) TDFX(0): *Default mode "1280x1024": 108.0 MHz, 64.0 kHz, 60.0 Hz
(II) TDFX(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 10251028 1066 +hsync +vsync (64.0 kHz)
(**) TDFX(0): *Driver mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(II) TDFX(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(**) TDFX(0):  Default mode "1280x960": 108.0 MHz, 60.0 kHz, 60.0 Hz
(II) TDFX(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(**) TDFX(0):  Driver mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
(II) TDFX(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(**) TDFX(0):  Default mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
(II) TDFX(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(**) TDFX(0):  Default mode "1152x864": 105.0 MHz, 67.6 kHz, 75.0 Hz
(II) TDFX(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.6 kHz)
(**) TDFX(0):  Default mode "1152x864": 96.8 MHz, 63.0 kHz, 70.0 Hz
(II) TDFX(0): Modeline "1152x864"x70.0   96.77  1152 1224 1344 1536  864 865 868 900 -hsync +vsync (63.0 kHz)
(**) TDFX(0):  Default mode "1152x864": 81.6 MHz, 53.7 kHz, 60.0 Hz
(II) TDFX(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(**) TDFX(0):  Driver mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(II) TDFX(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(**) TDFX(0):  Driver mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
(II) TDFX(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(**) TDFX(0):  Driver mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) TDFX(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(**) TDFX(0):  Driver mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) TDFX(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) TDFX(0):  Default mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(II) TDFX(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(**) TDFX(0):  Default mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
(II) TDFX(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(**) TDFX(0):  Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) TDFX(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(**) TDFX(0):  Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) TDFX(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) TDFX(0):  Driver mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) TDFX(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(**) TDFX(0):  Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) TDFX(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(**) TDFX(0):  Driver mode "800x600": 56.2 MHz, 53.7 kHz, 85.1 Hz
(II) TDFX(0): Modeline "800x600"x85.1   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(**) TDFX(0):  Driver mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) TDFX(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) TDFX(0):  Driver mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) TDFX(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(**) TDFX(0):  Driver mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) TDFX(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) TDFX(0):  Driver mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) TDFX(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) TDFX(0):  Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
(II) TDFX(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(**) TDFX(0):  Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) TDFX(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) TDFX(0):  Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) TDFX(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(**) TDFX(0):  Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) TDFX(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) TDFX(0):  Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) TDFX(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) TDFX(0):  Default mode "840x525": 73.1 MHz, 65.3 kHz, 60.0 Hz (D)
(II) TDFX(0): Modeline "840x525"x60.0   73.12  840 892 980 1120  525 526 529 544 doublescan -hsync +vsync (65.3 kHz)
(**) TDFX(0):  Default mode "700x525": 61.0 MHz, 64.9 kHz, 60.0 Hz (D)
(II) TDFX(0): Modeline "700x525"x60.0   61.00  700 744 820 940  525 526 532 541doublescan +hsync +vsync (64.9 kHz)
(**) TDFX(0):  Default mode "640x512": 54.0 MHz, 64.0 kHz, 60.0 Hz (D)
(II) TDFX(0): Modeline "640x512"x60.0   54.00  640 664 720 844  512 512 514 533doublescan +hsync +vsync (64.0 kHz)
(**) TDFX(0):  Default mode "720x450": 53.2 MHz, 55.9 kHz, 59.9 Hz (D)
(II) TDFX(0): Modeline "720x450"x59.9   53.25  720 760 836 952  450 451 454 467doublescan -hsync +vsync (55.9 kHz)
(**) TDFX(0):  Driver mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(II) TDFX(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509-hsync -vsync (43.3 kHz)
(**) TDFX(0):  Driver mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) TDFX(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500-hsync -vsync (37.5 kHz)
(**) TDFX(0):  Driver mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) TDFX(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520-hsync -vsync (37.9 kHz)
(**) TDFX(0):  Driver mode "640x480": 30.2 MHz, 35.0 kHz, 66.7 Hz
(II) TDFX(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525-hsync -vsync (35.0 kHz)
(**) TDFX(0):  Driver mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) TDFX(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525-hsync -vsync (31.5 kHz)
(**) TDFX(0):  Driver mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) TDFX(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525-hsync -vsync (31.5 kHz)
(**) TDFX(0):  Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(II) TDFX(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509-hsync -vsync (43.3 kHz)
(**) TDFX(0):  Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) TDFX(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500-hsync -vsync (37.5 kHz)
(**) TDFX(0):  Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) TDFX(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520-hsync -vsync (37.9 kHz)
(**) TDFX(0):  Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
(II) TDFX(0): Modeline "640x480"x60.0   54.00  640 688 744 900  480 480 482 500doublescan +hsync +vsync (60.0 kHz)
(**) TDFX(0):  Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) TDFX(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525-hsync -vsync (31.5 kHz)
(**) TDFX(0):  Driver mode "720x400": 35.5 MHz, 39.4 kHz, 87.8 Hz
(II) TDFX(0): Modeline "720x400"x87.8   35.50  720 738 846 900  400 421 423 449-hsync -vsync (39.4 kHz)
(**) TDFX(0):  Driver mode "720x400": 28.3 MHz, 31.5 kHz, 70.1 Hz
(II) TDFX(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449-hsync +vsync (31.5 kHz)
(**) TDFX(0):  Default mode "720x400": 35.5 MHz, 37.9 kHz, 85.0 Hz
(II) TDFX(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446-hsync +vsync (37.9 kHz)
(**) TDFX(0):  Default mode "680x384": 36.0 MHz, 47.4 kHz, 60.0 Hz (D)
(II) TDFX(0): Modeline "680x384"x60.0   36.00  680 704 720 760  384 385 390 395doublescan +hsync -vsync (47.4 kHz)
(**) TDFX(0):  Default mode "680x384": 42.4 MHz, 47.7 kHz, 59.8 Hz (D)
(II) TDFX(0): Modeline "680x384"x59.8   42.38  680 716 784 888  384 385 390 399doublescan -hsync +vsync (47.7 kHz)
(**) TDFX(0):  Default mode "640x400": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) TDFX(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445-hsync +vsync (37.9 kHz)
(**) TDFX(0):  Default mode "576x432": 54.0 MHz, 67.5 kHz, 75.0 Hz (D)
(II) TDFX(0): Modeline "576x432"x75.0   54.00  576 608 672 800  432 432 434 450doublescan +hsync +vsync (67.5 kHz)
(**) TDFX(0):  Default mode "576x432": 52.5 MHz, 67.6 kHz, 75.0 Hz (D)
(II) TDFX(0): Modeline "576x432"x75.0   52.49  576 612 676 776  432 432 434 451
doublescan -hsync +vsync (67.6 kHz)
(**) TDFX(0):  Default mode "576x432": 48.4 MHz, 63.0 kHz, 70.0 Hz (D)
(II) TDFX(0): Modeline "576x432"x70.0   48.38  576 612 672 768  432 432 434 450doublescan -hsync +vsync (63.0 kHz)
(**) TDFX(0):  Default mode "576x432": 40.8 MHz, 53.7 kHz, 60.1 Hz (D)
(II) TDFX(0): Modeline "576x432"x60.1   40.81  576 608 668 760  432 432 434 447doublescan -hsync +vsync (53.7 kHz)
(**) TDFX(0):  Default mode "640x350": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) TDFX(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445+hsync -vsync (37.9 kHz)
(**) TDFX(0):  Default mode "512x384": 47.2 MHz, 68.7 kHz, 85.0 Hz (D)
(II) TDFX(0): Modeline "512x384"x85.0   47.25  512 536 584 688  384 384 386 404doublescan +hsync +vsync (68.7 kHz)
(**) TDFX(0):  Default mode "512x384": 39.4 MHz, 60.0 kHz, 75.0 Hz (D)
(II) TDFX(0): Modeline "512x384"x75.0   39.38  512 520 568 656  384 384 386 400doublescan +hsync +vsync (60.0 kHz)
(**) TDFX(0):  Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)
(II) TDFX(0): Modeline "512x384"x70.1   37.50  512 524 592 664  384 385 388 403doublescan -hsync -vsync (56.5 kHz)
(**) TDFX(0):  Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(II) TDFX(0): Modeline "512x384"x60.0   32.50  512 524 592 672  384 385 388 403doublescan -hsync -vsync (48.4 kHz)
(**) TDFX(0):  Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(II) TDFX(0): Modeline "416x312"x74.7   28.64  416 432 464 576  312 312 314 333doublescan -hsync -vsync (49.7 kHz)
(**) TDFX(0):  Default mode "400x300": 28.1 MHz, 53.7 kHz, 85.3 Hz (D)
(II) TDFX(0): Modeline "400x300"x85.3   28.15  400 416 448 524  300 300 302 315doublescan +hsync +vsync (53.7 kHz)
(**) TDFX(0):  Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(II) TDFX(0): Modeline "400x300"x75.1   24.75  400 408 448 528  300 300 302 312doublescan +hsync +vsync (46.9 kHz)
(**) TDFX(0):  Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(II) TDFX(0): Modeline "400x300"x72.2   25.00  400 428 488 520  300 318 321 333doublescan +hsync +vsync (48.1 kHz)
(**) TDFX(0):  Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) TDFX(0): Modeline "400x300"x60.3   20.00  400 420 484 528  300 300 302 314doublescan +hsync +vsync (37.9 kHz)
(**) TDFX(0):  Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) TDFX(0): Modeline "400x300"x56.3   18.00  400 412 448 512  300 300 301 312doublescan +hsync +vsync (35.2 kHz)
(**) TDFX(0):  Default mode "320x240": 18.0 MHz, 43.3 kHz, 85.2 Hz (D)
(II) TDFX(0): Modeline "320x240"x85.2   18.00  320 348 376 416  240 240 242 254doublescan -hsync -vsync (43.3 kHz)
(**) TDFX(0):  Default mode "320x240": 15.8 MHz, 37.5 kHz, 75.0 Hz (D)
(II) TDFX(0): Modeline "320x240"x75.0   15.75  320 328 360 420  240 240 242 250doublescan -hsync -vsync (37.5 kHz)
(**) TDFX(0):  Default mode "320x240": 15.8 MHz, 37.9 kHz, 72.8 Hz (D)
(II) TDFX(0): Modeline "320x240"x72.8   15.75  320 332 352 416  240 244 246 260doublescan -hsync -vsync (37.9 kHz)
(**) TDFX(0):  Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) TDFX(0): Modeline "320x240"x60.1   12.59  320 328 376 400  240 245 246 262doublescan -hsync -vsync (31.5 kHz)
(**) TDFX(0):  Default mode "360x200": 17.8 MHz, 37.9 kHz, 85.0 Hz (D)
(II) TDFX(0): Modeline "360x200"x85.0   17.75  360 378 414 468  200 200 202 223doublescan -hsync +vsync (37.9 kHz)
(**) TDFX(0):  Default mode "320x200": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(II) TDFX(0): Modeline "320x200"x85.3   15.75  320 336 368 416  200 200 202 222doublescan -hsync +vsync (37.9 kHz)
(**) TDFX(0):  Default mode "320x175": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(II) TDFX(0): Modeline "320x175"x85.3   15.75  320 336 368 416  175 191 192 222doublescan +hsync -vsync (37.9 kHz)
(**) TDFX(0): Display dimensions: (320, 240) mm
(**) TDFX(0): DPI set to (101, 108)
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x00000000 (0x1) IX[B]
(II) TDFX(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0xe100
(II) TDFX(0): Changing back offset from 0x00aff000 to 0x00afe000
(II) TDFX(0): Textures Memory 7.58 MB
(II) TDFX(0): Cursor Offset: [0x00000000,0x00001000)
(II) TDFX(0): Fifo Offset: [0x00001000, 0x00041000)
(II) TDFX(0): Front Buffer Offset: [0x00041000, 0x00369C00)
(II) TDFX(0): Texture Offset: [0x00369C00, 0x00AFE000)
(II) TDFX(0): BackOffset: [0x00AFE000, 0x00D7E000)
(II) TDFX(0): DepthOffset: [0x00D7F000, 0x00FFF000)
(II) TDFX(0): Minimum 270, Maximum 1023 lines of offscreen memory available
(II) TDFX(0): [dri] VideoRAM = 16384, VirtualXres = 1280, VirtualYres= 1024,
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:09.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports pci:0000:00:09.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) TDFX(0): [drm] Using the DRM lock SAREA also for drawables.
(II) TDFX(0): [drm] framebuffer handle = 0xd6000000
(II) TDFX(0): [drm] added 1 reserved context for kernel
(II) TDFX(0): X context handle = 0x1
(II) TDFX(0): [drm] installed DRM signal handler
(II) TDFX(0): [drm] Registers = 0xd4000000
(II) TDFX(0): visual configs initialized
(II) TDFX(0): Using XFree86 Acceleration Architecture (XAA)
        Screen to screen bit blits
        Solid filled rectangles
        8x8 mono pattern filled rectangles
        Indirect CPU to Screen color expansion
        Solid Lines
        Dashed Lines
        Driver provided NonTEGlyphRenderer replacement
        Setting up tile and stipple cache:
                32 128x128 slots
                9 256x256 slots
(==) TDFX(0): Backing store disabled
(==) TDFX(0): Silken mouse enabled
(**) Option "dpms"
(**) TDFX(0): DPMS enabled
(II) TDFX(0): [DRI] installation complete
(II) TDFX(0): Direct rendering enabled
(==) RandR enabled

```
After that is all input devices.

The hyperlink works. It opens a new tab that's already scrolled to the end. If I attempt to scroll up or down from there it crashes. The text box I'm in now scrolls without crashing for some reason though, just the bar from the whole window is giving me the issues. Also, when I try to resize my terminal window it will crash the same way, but it scrolls just fine. I'm incredibly perplexed.

Thanks for your patience.

---

### Post by SoftwareExplorer on 2009-08-15
I'm glad the link works. I read through the log, but I don't know all that much about X and couldn't see anything that looked bad. Sorry I couldn't be of more help. I guess it's time for the **[SIZE=2]X[/SIZE]**perts!

---

