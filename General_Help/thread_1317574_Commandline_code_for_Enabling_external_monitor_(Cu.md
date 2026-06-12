---
title: "Commandline code for Enabling external monitor? (Currently set to Disabled)"
date: 2009-11-06
forum: General Help
---

### Post by cowcow1212 on 2009-11-06
So when I had Ubuntu working, I had accidentally set my external monitor to Disabled. 

I was reviewing the possible fixes by reading the manual on a Live CD of Kubuntu 9.10 and it gave the following command: 

```
systemsettings & 
```I tried to execute the above command on the live CD in another terminal, but it cannot connect to X server. Would this change the settings only when the server is off? 

Nor can it execute commands because X server is running on 0.

Any help here? Are there any command codes to enable a disabled screen (via preferences menu)? If there are, please tell me. 

(xrandr and editing xorg.conf seems unsuccessful, even though they are successful on bootup.. they fail once the kde console starts).

---

### Post by cowcow1212 on 2009-11-06
anyone know how to manipulate the process, acpid through the command line?

Looking at the log, on my LIVE boot CD, the process that registers the turning off of my broken, unviewable screen. The message I see in Daemons log is: 

Process: acpid
Message: client 2951[0:0] has disconnected 

Does anyone now to to make the client, 2951[0:1] connect through the command line?

Here is the output log for turning on the non-working monitor.
[PHP]	Information	init memmap
	Information	init common
	Information	init crtc1
	Information	init pll1
	Information	restore memmap
	Information	RADEON(0): RADEONRestoreMemMapRegisters() : 
	Information	RADEON(0):   MC_FB_LOCATION   : 0xf3fff000 0xf3fff000
	Information	RADEON(0):   MC_AGP_LOCATION  : 0xec7fec00
	Information	restore common
	Information	restore crtc1
	Information	restore pll1
	Information	set RMX
	Information	set LVDS
	Information	enable primary dac
	Information	enable LVDS
	Information	RADEON(0): EDID for output VGA-0
	Information	RADEON(0): Manufacturer: NEC  Model: 66a5  Serial#: 16843009
	Information	RADEON(0): Year: 2006  Week: 52
	Information	RADEON(0): EDID Version: 1.3
	Information	RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
	Information	RADEON(0): Sync:  Separate
	Information	RADEON(0): Max Image Size [cm]: horiz.: 34  vert.: 27
	Information	RADEON(0): Gamma: 2.20
	Information	RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
	Information	RADEON(0): First detailed timing is preferred mode
	Information	RADEON(0): redX: 0.641 redY: 0.341   greenX: 0.285 greenY: 0.610
	Information	RADEON(0): blueX: 0.142 blueY: 0.077   whiteX: 0.312 whiteY: 0.330
	Information	RADEON(0): Supported established timings:
	Information	RADEON(0): 720x400@70Hz
	Information	RADEON(0): 640x480@60Hz
	Information	RADEON(0): 640x480@67Hz
	Information	RADEON(0): 640x480@72Hz
	Information	RADEON(0): 640x480@75Hz
	Information	RADEON(0): 800x600@56Hz
	Information	RADEON(0): 800x600@60Hz
	Information	RADEON(0): 800x600@72Hz
	Information	RADEON(0): 800x600@75Hz
	Information	RADEON(0): 832x624@75Hz
	Information	RADEON(0): 1024x768@60Hz
	Information	RADEON(0): 1024x768@70Hz
	Information	RADEON(0): 1024x768@75Hz
	Information	RADEON(0): 1280x1024@75Hz
	Information	RADEON(0): 1152x870@75Hz
	Information	RADEON(0): Manufacturer's mask: 0
	Information	RADEON(0): Supported standard timings:
	Information	RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
	Information	RADEON(0): #1: hsize: 1280  vsize 960  refresh: 75  vid: 20353
	Information	RADEON(0): Supported detailed timing:
	Information	RADEON(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
	Information	RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
	Information	RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
	Information	RADEON(0): Ranges: V min: 56 V max: 75 Hz, H min: 31 H max: 81 kHz, PixClock max 140 MHz
	Information	RADEON(0): Monitor name: LCD175VXM
	Information	RADEON(0): Serial No: 6ZE00566NA
	Information	RADEON(0): EDID (in hex):
	Information	RADEON(0): 	00ffffffffffff0038a3a56601010101
	Information	RADEON(0): 	3410010308221b78ea117ea457499c24
	Information	RADEON(0): 	134f54bfef80714f814f010101010101
	Information	RADEON(0): 	010101010101302a009851002a403070
	Information	RADEON(0): 	1300520e1100001e000000fd00384b1f
	Information	RADEON(0): 	510e000a202020202020000000fc004c
	Information	RADEON(0): 	434431373556584d0a202020000000ff
	Information	RADEON(0): 	00365a4530303536364e410a202000e4
	Information	RADEON(0): EDID vendor "NEC", prod id 26277
	Information	RADEON(0): Using hsync ranges from config file
	Information	RADEON(0): Using vrefresh ranges from config file
	Information	RADEON(0): Printing DDC gathered Modelines:
	Information	RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
	Information	RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
	Information	RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
	Information	RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
	Information	RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
	Information	RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
	Information	RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
	Information	RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
	Information	RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
	Information	RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
	Information	RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
	Information	RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
	Information	RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
	Information	RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
	Information	RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
	Information	RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
	Information	RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
	Information	RADEON(0): Modeline "1280x960"x75.0  129.86  1280 1368 1504 1728  960 961 964 1002 -hsync +vsync (75.2 kHz)
	Information	RADEON(0): Output: VGA-0, Detected Monitor Type: 1
	Information	RADEON(0): EDID data from the display on output: VGA-0 ----------------------
	Information	RADEON(0): Manufacturer: NEC  Model: 66a5  Serial#: 16843009
	Information	RADEON(0): Year: 2006  Week: 52
	Information	RADEON(0): EDID Version: 1.3
	Information	RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
	Information	RADEON(0): Sync:  Separate
	Information	RADEON(0): Max Image Size [cm]: horiz.: 34  vert.: 27
	Information	RADEON(0): Gamma: 2.20
	Information	RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
	Information	RADEON(0): First detailed timing is preferred mode
	Information	RADEON(0): redX: 0.641 redY: 0.341   greenX: 0.285 greenY: 0.610
	Information	RADEON(0): blueX: 0.142 blueY: 0.077   whiteX: 0.312 whiteY: 0.330
	Information	RADEON(0): Supported established timings:
	Information	RADEON(0): 720x400@70Hz
	Information	RADEON(0): 640x480@60Hz
	Information	RADEON(0): 640x480@67Hz
	Information	RADEON(0): 640x480@72Hz
	Information	RADEON(0): 640x480@75Hz
	Information	RADEON(0): 800x600@56Hz
	Information	RADEON(0): 800x600@60Hz
	Information	RADEON(0): 800x600@72Hz
	Information	RADEON(0): 800x600@75Hz
	Information	RADEON(0): 832x624@75Hz
	Information	RADEON(0): 1024x768@60Hz
	Information	RADEON(0): 1024x768@70Hz
	Information	RADEON(0): 1024x768@75Hz
	Information	RADEON(0): 1280x1024@75Hz
	Information	RADEON(0): 1152x870@75Hz
	Information	RADEON(0): Manufacturer's mask: 0
	Information	RADEON(0): Supported standard timings:
	Information	RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
	Information	RADEON(0): #1: hsize: 1280  vsize 960  refresh: 75  vid: 20353
	Information	RADEON(0): Supported detailed timing:
	Information	RADEON(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
	Information	RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
	Information	RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
	Information	RADEON(0): Ranges: V min: 56 V max: 75 Hz, H min: 31 H max: 81 kHz, PixClock max 140 MHz
	Information	RADEON(0): Monitor name: LCD175VXM
	Information	RADEON(0): Serial No: 6ZE00566NA
	Information	RADEON(0): EDID (in hex):
	Information	RADEON(0): 	00ffffffffffff0038a3a56601010101
	Information	RADEON(0): 	3410010308221b78ea117ea457499c24
	Information	RADEON(0): 	134f54bfef80714f814f010101010101
	Information	RADEON(0): 	010101010101302a009851002a403070
	Information	RADEON(0): 	1300520e1100001e000000fd00384b1f
	Information	RADEON(0): 	510e000a202020202020000000fc004c
	Information	RADEON(0): 	434431373556584d0a202020000000ff
	Information	RADEON(0): 	00365a4530303536364e410a202000e4
	Information	RADEON(0): EDID vendor "NEC", prod id 26277
	Information	RADEON(0): Printing probed modes for output VGA-0
	Information	RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
	Information	RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
	Information	RADEON(0): Modeline "1280x960"x75.0  129.86  1280 1368 1504 1728  960 961 964 1002 -hsync +vsync (75.2 kHz)
	Information	RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
	Information	RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
	Information	RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
	Information	RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
	Information	RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
	Information	RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
	Information	RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
	Information	RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
	Information	RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
	Information	RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
	Information	RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
	Information	RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
	Information	RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
	Information	RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
	Information	RADEON(0): Output: LVDS, Detected Monitor Type: 2
	Information	RADEON(0): Added native panel mode: 1024x768
	Information	RADEON(0): Not using default mode "640x350" (vrefresh out of range)
	Information	RADEON(0): Not using default mode "640x400" (vrefresh out of range)
	Information	RADEON(0): Not using default mode "720x400" (vrefresh out of range)
	Information	RADEON(0): Not using default mode "640x480" (vrefresh out of range)
	Information	RADEON(0): Not using default mode "640x480" (vrefresh out of range)
	Information	RADEON(0): Not using default mode "640x480" (vrefresh out of range)
	Information	RADEON(0): Not using default mode "800x600" (vrefresh out of range)
	Information	RADEON(0): Not using default mode "800x600" (vrefresh out of range)
	Information	RADEON(0): Not using default mode "800x600" (vrefresh out of range)
	Information	RADEON(0): Not using default mode "800x600" (vrefresh out of range)
	Information	RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
	Information	RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
	Information	RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
	Information	RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
	Information	RADEON(0): Not using default mode "1280x960" (hsync out of range)
	Information	RADEON(0): Not using default mode "1280x960" (vrefresh out of range)
	Information	RADEON(0): Not using default mode "1280x1024" (hsync out of range)
	Information	RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
	Information	RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
	Information	RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
	Information	RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
	Information	RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
	Information	RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
	Information	RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
	Information	RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
	Information	RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
	Information	RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
	Information	RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
	Information	RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
	Information	RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
	Information	RADEON(0): Not using default mode "832x624" (vrefresh out of range)
	Information	RADEON(0): Not using default mode "1152x864" (hsync out of range)
	Information	RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
	Information	RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
	Information	RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
	Information	RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
	Information	RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
	Information	RADEON(0): Not using default mode "1360x768" (width too large for virtual size)
	Information	RADEON(0): Not using default mode "1360x768" (width too large for virtual size)
	Information	RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
	Information	RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
	Information	RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
	Information	RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
	Information	RADEON(0): Not using default mode "1440x900" (width too large for virtual size)
	Information	RADEON(0): Not using default mode "1600x1024" (width too large for virtual size)
	Information	RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
	Information	RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
	Information	RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
	Information	RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
	Information	RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
	Information	RADEON(0): Not using default mode "1920x1080" (width too large for virtual size)
	Information	RADEON(0): Not using default mode "1920x1200" (width too large for virtual size)
	Information	RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
	Information	RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
	Information	RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
	Information	RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
	Information	RADEON(0): Printing probed modes for output LVDS
	Information	RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1040 1176 1344  768 770 776 806 (48.4 kHz)
	Information	RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
	Information	RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
	Information	RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
	Information	RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
	Information	RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[/PHP]
The settings I had chose were 1024x768 for my non-working monitor (LVDS) 

Here is the log file when turning off LVDS, below. 
[PHP]	Information	AIGLX: Suspending AIGLX clients for VT switch
	Information	disable primary dac
	Information	RADEON(0): RADEONRestoreMemMapRegisters() : 
	Information	RADEON(0):   MC_FB_LOCATION   : 0xffff0000 0xf3fff000
	Information	RADEON(0):   MC_AGP_LOCATION  : 0x003fffc0
	Information	finished PLL2
[/PHP]

I have to switch to another console (Ctl+alt+Fn) because the my external monitor shuts off, below is the log file from that event:

[PHP]
	Information	finished PLL1
	Information	Entering Restore TV
	Information	Restore TV PLL
	Information	Restore TVHV
	Information	Restore TV Restarts
	Information	Restore Timing Tables
	Information	Restore TV standard
	Information	Leaving Restore TV
	Information	Open ACPI successful (/var/run/acpid.socket)
	Information	AIGLX: Resuming AIGLX clients after VT switch
	Information	disable primary dac
	Information	disable LVDS
	Information	disable primary dac
	Information	init memmap
	Information	init common
	Information	init crtc2
	Information	init pll2
	Information	freq: 129859000
	Information	best_freq: 129857143
	Information	best_feedback_div: 101
	Information	best_frac_feedback_div: 0
	Information	best_ref_div: 21
	Information	best_post_div: 1
	Information	restore memmap
	Information	RADEON(0): RADEONRestoreMemMapRegisters() : 
	Information	RADEON(0):   MC_FB_LOCATION   : 0xf3fff000 0xffff0000
	Information	RADEON(0):   MC_AGP_LOCATION  : 0xec7fec00
	Information	restore common
	Information	restore crtc2
	Information	restore pll2
[/PHP]

does anyone know how to run AIGLX from the command line, when you are at the log in screen of KDE?

I hope this info I have posted can help me out and help my aid figure out how to execute these commands from command line!

Thanks again for the time,

cowcow

---

