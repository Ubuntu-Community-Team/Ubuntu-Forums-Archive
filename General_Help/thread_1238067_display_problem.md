---
title: "display problem"
date: 2009-08-12
forum: General Help
---

### Post by zmzach on 2009-08-12
Just upgraded to 9.04 and am liking it so far. just one quick question, I run dual monitors, laptop and desktop monitor. I've got it set up as big screen using my display manager. However the desktop is the primary monitor right now. I would like the laptop to be the primary.

Is there an easy way of fixing this? I'm sure I could install ATI catalyst control and make it work, but I'd rather not have to install another whole program if there's an easy way of doing this

thanks

---

### Post by P4man on 2009-08-12
ew.. dual monitors on ATI. If you got it working at all, consider yourself lucky :) Are you using the binary ATI fglrx driver, or the opensource ati or radeon one?

---

### Post by zmzach on 2009-08-12
Huh, I really don't know. Where would I look to find that?
And it works no problem, just installed and it worked. Runnin a IBM thinkpad T60

---

### Post by P4man on 2009-08-12
Try running this in  a terminal, and copy/paste the output here:

```
cat /var/log/Xorg.0.log
```

---

### Post by zmzach on 2009-08-13
Alright, here it is, but it's a big one. Looks like some of it got cut off too

> (II) RADEON(0): 	4080b7004ccf1000001c000000fd003c
(II) RADEON(0): 	461f3207000a202020202020000000ff
(II) RADEON(0): 	004646575a35413031393335305500a0
(II) RADEON(0): EDID vendor "PTS", prod id 1503
(II) RADEON(0): EDID vendor "LEN", prod id 16416
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   54.16  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (40.3 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: LEN  Model: 4020  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 29  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.590 redY: 0.342   greenX: 0.319 greenY: 0.540
(II) RADEON(0): blueX: 0.152 blueY: 0.137   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  286 x 214 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 54.2 MHz   Image Size:  286 x 214 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  LTN141XA-L01
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0030ae204000000000
(II) RADEON(0): 	000f0103801d1578ea2d059757518a27
(II) RADEON(0): 	23505421080001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	36001ed6100000192815004041002630
(II) RADEON(0): 	188836001ed6100000190000000f0061
(II) RADEON(0): 	43326143280f01004ca35841000000fe
(II) RADEON(0): 	004c544e31343158412d4c30310a00e9
(II) RADEON(0): EDID vendor "LEN", prod id 16416
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
invalid output device for dac detection
Unhandled monitor type 0
(WW) EDID preferred timing clock 80.50MHz exceeds claimed max 70MHz, fixing
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: PTS  Model: 5df  Serial#: 19350
(II) RADEON(0): Year: 2005  Week: 41
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 20
(II) RADEON(0): Gamma: 2.37
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.635 redY: 0.331   greenX: 0.283 greenY: 0.591
(II) RADEON(0): blueX: 0.139 blueY: 0.052   whiteX: 0.303 whiteY: 0.313
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): Manufacturer's mask: 10
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 70.0 MHz   Image Size:  332 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1290  h_sync_end 1300 h_blank_end 1400 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 802  v_sync_end 812 v_blanking: 833 v_border: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 80.5 MHz   Image Size:  332 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1472 h_blank_end 1664 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 779  v_sync_end 786 v_blanking: 806 v_border: 0
(II) RADEON(0): Ranges: V min: 60 V max: 70 Hz, H min: 31 H max: 50 kHz, PixClock max 81 MHz
(II) RADEON(0): Serial No: FFWZ5A019350U
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004293df05964b0000
(II) RADEON(0): 	290f0103682114892ab999a254489723
(II) RADEON(0): 	0d4d50a1081001010101010101010101
(II) RADEON(0): 	010101010101581b0078502021300a0a
(II) RADEON(0): 	2a004ccf1000001e721f008051002630
(II) RADEON(0): 	4080b7004ccf1000001c000000fd003c
(II) RADEON(0): 	461f3207000a202020202020000000ff
(II) RADEON(0): 	004646575a35413031393335305500a0
(II) RADEON(0): EDID vendor "PTS", prod id 1503
(II) RADEON(0): EDID vendor "LEN", prod id 16416
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   54.16  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (40.3 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: LEN  Model: 4020  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 29  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.590 redY: 0.342   greenX: 0.319 greenY: 0.540
(II) RADEON(0): blueX: 0.152 blueY: 0.137   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  286 x 214 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 54.2 MHz   Image Size:  286 x 214 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  LTN141XA-L01
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0030ae204000000000
(II) RADEON(0): 	000f0103801d1578ea2d059757518a27
(II) RADEON(0): 	23505421080001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	36001ed6100000192815004041002630
(II) RADEON(0): 	188836001ed6100000190000000f0061
(II) RADEON(0): 	43326143280f01004ca35841000000fe
(II) RADEON(0): 	004c544e31343158412d4c30310a00e9
(II) RADEON(0): EDID vendor "LEN", prod id 16416
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
invalid output device for dac detection
Unhandled monitor type 0
Blank CRTC 1 success
Disable CRTC 1 success
Lock CRTC 1 success
Output CRT1 disable success
Output LCD1 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Mode 1024x768 - 1344 806 10
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xdbffd800 0xdbffd800
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
freq: 65000000
best_freq: 65000000
best_feedback_div: 260
best_ref_div: 9
best_post_div: 12
(II) RADEON(0): crtc(0) Clock: mode 65000, PLL 65000
(II) RADEON(0): crtc(0) PLL  : refdiv 9, fbdiv 0x104(260), pdiv 12
Set CRTC 0 PLL success
Set CRTC Timing success
Set CRTC 0 Overscan success
Not using RMX
scaler 0 setup success
Set CRTC 0 Source success
crtc 0 YUV disable setup success
Output digital setup success
Enable CRTC 1 success
Unblank CRTC 1 success
Unlock CRTC 1 success
Output CRT1 enable success
Output LCD1 enable success
Enable CRTC 0 success
Unblank CRTC 0 success
(WW) EDID preferred timing clock 80.50MHz exceeds claimed max 70MHz, fixing
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: PTS  Model: 5df  Serial#: 19350
(II) RADEON(0): Year: 2005  Week: 41
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 20
(II) RADEON(0): Gamma: 2.37
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.635 redY: 0.331   greenX: 0.283 greenY: 0.591
(II) RADEON(0): blueX: 0.139 blueY: 0.052   whiteX: 0.303 whiteY: 0.313
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): Manufacturer's mask: 10
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 70.0 MHz   Image Size:  332 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1290  h_sync_end 1300 h_blank_end 1400 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 802  v_sync_end 812 v_blanking: 833 v_border: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 80.5 MHz   Image Size:  332 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1472 h_blank_end 1664 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 779  v_sync_end 786 v_blanking: 806 v_border: 0
(II) RADEON(0): Ranges: V min: 60 V max: 70 Hz, H min: 31 H max: 50 kHz, PixClock max 81 MHz
(II) RADEON(0): Serial No: FFWZ5A019350U
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004293df05964b0000
(II) RADEON(0): 	290f0103682114892ab999a254489723
(II) RADEON(0): 	0d4d50a1081001010101010101010101
(II) RADEON(0): 	010101010101581b0078502021300a0a
(II) RADEON(0): 	2a004ccf1000001e721f008051002630
(II) RADEON(0): 	4080b7004ccf1000001c000000fd003c
(II) RADEON(0): 	461f3207000a202020202020000000ff
(II) RADEON(0): 	004646575a35413031393335305500a0
(II) RADEON(0): EDID vendor "PTS", prod id 1503
(II) RADEON(0): EDID vendor "LEN", prod id 16416
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   54.16  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (40.3 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: LEN  Model: 4020  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 29  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.590 redY: 0.342   greenX: 0.319 greenY: 0.540
(II) RADEON(0): blueX: 0.152 blueY: 0.137   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  286 x 214 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 54.2 MHz   Image Size:  286 x 214 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  LTN141XA-L01
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0030ae204000000000
(II) RADEON(0): 	000f0103801d1578ea2d059757518a27
(II) RADEON(0): 	23505421080001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	36001ed6100000192815004041002630
(II) RADEON(0): 	188836001ed6100000190000000f0061
(II) RADEON(0): 	43326143280f01004ca35841000000fe
(II) RADEON(0): 	004c544e31343158412d4c30310a00e9
(II) RADEON(0): EDID vendor "LEN", prod id 16416
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
invalid output device for dac detection
Unhandled monitor type 0
(WW) EDID preferred timing clock 80.50MHz exceeds claimed max 70MHz, fixing
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: PTS  Model: 5df  Serial#: 19350
(II) RADEON(0): Year: 2005  Week: 41
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 20
(II) RADEON(0): Gamma: 2.37
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.635 redY: 0.331   greenX: 0.283 greenY: 0.591
(II) RADEON(0): blueX: 0.139 blueY: 0.052   whiteX: 0.303 whiteY: 0.313
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): Manufacturer's mask: 10
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 70.0 MHz   Image Size:  332 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1290  h_sync_end 1300 h_blank_end 1400 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 802  v_sync_end 812 v_blanking: 833 v_border: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 80.5 MHz   Image Size:  332 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1472 h_blank_end 1664 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 779  v_sync_end 786 v_blanking: 806 v_border: 0
(II) RADEON(0): Ranges: V min: 60 V max: 70 Hz, H min: 31 H max: 50 kHz, PixClock max 81 MHz
(II) RADEON(0): Serial No: FFWZ5A019350U
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004293df05964b0000
(II) RADEON(0): 	290f0103682114892ab999a254489723
(II) RADEON(0): 	0d4d50a1081001010101010101010101
(II) RADEON(0): 	010101010101581b0078502021300a0a
(II) RADEON(0): 	2a004ccf1000001e721f008051002630
(II) RADEON(0): 	4080b7004ccf1000001c000000fd003c
(II) RADEON(0): 	461f3207000a202020202020000000ff
(II) RADEON(0): 	004646575a35413031393335305500a0
(II) RADEON(0): EDID vendor "PTS", prod id 1503
(II) RADEON(0): EDID vendor "LEN", prod id 16416
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   54.16  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (40.3 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: LEN  Model: 4020  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 29  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.590 redY: 0.342   greenX: 0.319 greenY: 0.540
(II) RADEON(0): blueX: 0.152 blueY: 0.137   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  286 x 214 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 54.2 MHz   Image Size:  286 x 214 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  LTN141XA-L01
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0030ae204000000000
(II) RADEON(0): 	000f0103801d1578ea2d059757518a27
(II) RADEON(0): 	23505421080001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	36001ed6100000192815004041002630
(II) RADEON(0): 	188836001ed6100000190000000f0061
(II) RADEON(0): 	43326143280f01004ca35841000000fe
(II) RADEON(0): 	004c544e31343158412d4c30310a00e9
(II) RADEON(0): EDID vendor "LEN", prod id 16416
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
invalid output device for dac detection
Unhandled monitor type 0
(WW) EDID preferred timing clock 80.50MHz exceeds claimed max 70MHz, fixing
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: PTS  Model: 5df  Serial#: 19350
(II) RADEON(0): Year: 2005  Week: 41
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 20
(II) RADEON(0): Gamma: 2.37
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.635 redY: 0.331   greenX: 0.283 greenY: 0.591
(II) RADEON(0): blueX: 0.139 blueY: 0.052   whiteX: 0.303 whiteY: 0.313
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): Manufacturer's mask: 10
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 70.0 MHz   Image Size:  332 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1290  h_sync_end 1300 h_blank_end 1400 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 802  v_sync_end 812 v_blanking: 833 v_border: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 80.5 MHz   Image Size:  332 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1472 h_blank_end 1664 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 779  v_sync_end 786 v_blanking: 806 v_border: 0
(II) RADEON(0): Ranges: V min: 60 V max: 70 Hz, H min: 31 H max: 50 kHz, PixClock max 81 MHz
(II) RADEON(0): Serial No: FFWZ5A019350U
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004293df05964b0000
(II) RADEON(0): 	290f0103682114892ab999a254489723
(II) RADEON(0): 	0d4d50a1081001010101010101010101
(II) RADEON(0): 	010101010101581b0078502021300a0a
(II) RADEON(0): 	2a004ccf1000001e721f008051002630
(II) RADEON(0): 	4080b7004ccf1000001c000000fd003c
(II) RADEON(0): 	461f3207000a202020202020000000ff
(II) RADEON(0): 	004646575a35413031393335305500a0
(II) RADEON(0): EDID vendor "PTS", prod id 1503
(II) RADEON(0): EDID vendor "LEN", prod id 16416
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   54.16  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (40.3 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: LEN  Model: 4020  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 29  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.590 redY: 0.342   greenX: 0.319 greenY: 0.540
(II) RADEON(0): blueX: 0.152 blueY: 0.137   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  286 x 214 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 54.2 MHz   Image Size:  286 x 214 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  LTN141XA-L01
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0030ae204000000000
(II) RADEON(0): 	000f0103801d1578ea2d059757518a27
(II) RADEON(0): 	23505421080001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	36001ed6100000192815004041002630
(II) RADEON(0): 	188836001ed6100000190000000f0061
(II) RADEON(0): 	43326143280f01004ca35841000000fe
(II) RADEON(0): 	004c544e31343158412d4c30310a00e9
(II) RADEON(0): EDID vendor "LEN", prod id 16416
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
invalid output device for dac detection
Unhandled monitor type 0


---

### Post by P4man on 2009-08-14
You're using the opensource ATI drivers.. Dont have those,but try installing grandr. You can find it in add/remove programs, search for " Multiple Screens". Once installed, it appears in system > administration

Or you can use the easy way:
```

sudo apt-get install grandr
```


Another possible fix: just switch the video cables at your video card :)

---

