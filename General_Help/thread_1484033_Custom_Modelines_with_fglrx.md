---
title: "Custom Modelines with fglrx?"
date: 2010-05-15
forum: General Help
---

### Post by moep on 2010-05-15
I’m trying to figure out how I can adjust HSyncStart/HSyncEnd and VSyncStart/VSyncEnd when using ATI’s fglrx driver.

I figure the easiest way to do this is to just override the EDID detection and force a custom Modeline, but I can’t seem to find a way to do this.

My issue is that the picture is shifted ~10 pixels to the right and ~10 pixels to the bottom when using 1:1 pixelmapping, so 10 pixels on the right are off-screen and in return there’s a 10 pixel border on the left of the screen.
I figure that it should be possible to shift the whole picture around by changing the timings.


Possibly relevant xorg log snippet:

```
(II) fglrx(0): Connected Display0: DFP on secondary TMDS [tmds2i]
(II) fglrx(0): Display0 EDID data ---------------------------
(II) fglrx(0): Manufacturer: DON  Model: 16  Serial#: 16843009
(II) fglrx(0): Year: 2009  Week: 0
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max Image Size [cm]: horiz.: 110  vert.: 62
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: Off
(II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.683 redY: 0.317   greenX: 0.313 greenY: 0.581
(II) fglrx(0): blueX: 0.139 blueY: 0.050   whiteX: 0.289 whiteY: 0.280
(II) fglrx(0): Supported established timings:
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported standard timings:
(II) fglrx(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): Supported detailed timing:
(II) fglrx(0): clock: 148.5 MHz   Image Size:  1102 x 620 mm
(II) fglrx(0): h_active: 1920  h_sync: 2448  h_sync_end 2492 h_blank_end 2640 h_border: 0
(II) fglrx(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
(II) fglrx(0): Supported detailed timing:
(II) fglrx(0): clock: 148.5 MHz   Image Size:  1102 x 620 mm
(II) fglrx(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
(II) fglrx(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
(II) fglrx(0): Ranges: V min: 23 V max: 61 Hz, H min: 15 H max: 69 kHz, PixClock max 150 MHz
(II) fglrx(0): Monitor name: DENON-AVAMP
(II) fglrx(0): Number of EDID sections to follow: 1
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff0011ee160001010101
(II) fglrx(0): 	00130103806e3e782ad7b3ae51509423
(II) fglrx(0): 	0c4a4721080081800101010101010101
(II) fglrx(0): 	010101010101023a80d072382d40102c
(II) fglrx(0): 	45804e6c4200001e023a801871382d40
(II) fglrx(0): 	582c45004e6c4200001e000000fd0017
(II) fglrx(0): 	3d0f450f000a202020202020000000fc
(II) fglrx(0): 	0044454e4f4e2d4156414d500a20015d
(II) fglrx(0): End of Display0 EDID data --------------------
(II) fglrx(0): Output DFP1 using monitor section aticonfig-Monitor[0]-0
(II) fglrx(0): Output DFP2 has no monitor section
(II) fglrx(0): Output DFP3 has no monitor section
(II) fglrx(0): Output DFP4 has no monitor section
(II) fglrx(0): Output CRT1 has no monitor section
(II) fglrx(0): Output CRT2 has no monitor section
(II) fglrx(0): Output DFP1 disconnected
(II) fglrx(0): Output DFP2 connected
(II) fglrx(0): Output DFP3 disconnected
(II) fglrx(0): Output DFP4 disconnected
(II) fglrx(0): Output CRT1 disconnected
(II) fglrx(0): Output CRT2 disconnected
(II) fglrx(0): Using exact sizes for initial modes
(II) fglrx(0): Output DFP2 using initial mode 1920x1080
(II) fglrx(0): DPI set to (96, 96)
(II) fglrx(0): Adapter ATI Radeon HD 5700 Series has 2 configurable heads and 1 displays connected.
(WW) fglrx(0): Big Desktop related functionalities are replaced by RandR 1.2!
(==) fglrx(0): QBS disabled
(==) fglrx(0):  PseudoColor visuals disabled
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in

```

---

