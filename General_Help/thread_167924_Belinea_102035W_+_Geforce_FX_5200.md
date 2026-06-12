---
title: "Belinea 102035W + Geforce FX 5200"
date: 2006-04-29
forum: General Help
---

### Post by pt78 on 2006-04-29
Please ignore this thread, it is supposed to be in other section.

Hello,
I have probelm with native resolution of LCD Belinea 102035W combined with card Nvidia Geforce FX 5200 (from Asus). LCD is connected trough DVI, I haven't VGA connector on my card.

LCD data: 31-83KHz, 56-75Hz, 168 Mhz max (from documentation), native resolution 1680x1050@60Hz. 

Distro: Ubuntu 5.10 + nvidia drivers (installation procedure 1 from HOWTO: latest NVIDIA drivers thread)

Important part of xorg.conf
```

Section "Module"
#	Load	"GLcore"
	Load	"bitmap"
	Load	"ddc"
#	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"B102035W"
	Option		"DPMS"
	HorizSync    31.0 - 83.0
	VertRefresh  56.0 - 75.0
	Option	     "DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Monitor		"B102035W"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680x1050" "1600x1200" "1280x1024" 
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050" "1600x1200" "1280x1024" 
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050" "1600x1200" "1280x1024" 
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050" "1600x1200" "1280x1024" 
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050" "1600x1200" "1280x1024" 
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050" "1600x1200" "1280x1024"
		Virtual 	1680 1050
	EndSubSection
EndSection

```

What I don't like in Xorg.0.log:

```

(II) LoadModule: "nvidia"
(II) Loading /usr/X11R6/lib/modules/drivers/nvidia_drv.o
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.7667
	Module class: XFree86 Video Driver
...
...
....
(II) NVIDIA(0): NVIDIA GPU detected as: GeForce FX 5200
(--) NVIDIA(0): VideoBIOS: 04.34.20.87.00
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): VideoRAM: 131072 kBytes
(II) NVIDIA(0): Connected display device(s): DFP-0
(--) NVIDIA(0): DFP-0: maximum pixel clock: 135 MHz
(--) NVIDIA(0): DFP-0: Internal Single Link TMDS
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/X11R6/lib/modules/libddc.a
(II) NVIDIA(0): B102035W: Using hsync range of 31.00-83.00 kHz
(II) NVIDIA(0): B102035W: Using vrefresh range of 56.00-75.00 Hz
(II) NVIDIA(0): Clock range:  12.00 to 135.00 MHz

```

There is no way to run 1600x1200 and 1650x1050 with 135 MHz only. Adding modelines makes no sense, all reasonable modelines are in range 145-155Mhz. Adding
```

Option	"NODDC"      "1"

```
to device section of xorg.conf has no effect on result.

Using driver "nv" has some better output in Xorg.0.log:
```

(II) NV(0): Supported additional Video Mode:
(II) NV(0): clock: 146.2 MHz   Image Size:  433 x 270 mm
(II) NV(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) NV(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) NV(0): Ranges: V min: 56  V max: 75 Hz, H min: 31  H max: 83 kHz, PixClock max 150 MHz
(II) NV(0): Monitor name: B102035W
(II) NV(0): Probing for EDID on I2C bus B...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(II) NV(0):   ... none found
(--) NV(0): CRTC 0 is currently programmed for DFP
(II) NV(0): Using DFP on CRTC 0
(--) NV(0): Panel size is 1280 x 1024
(--) NV(0): VideoRAM: 131072 kBytes
(==) NV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) NV(0): B102035W: Using hsync range of 31.00-83.00 kHz
(II) NV(0): B102035W: Using vrefresh range of 56.00-75.00 Hz
(II) NV(0): Clock range:  12.00 to 350.00 MHz
(II) NV(0): Mode "1680x1050@60" is larger than BIOS programmed panel size of 1280 x 1024.  Removing.

```
However I don't understand last line

Reconfiguring makes no difference.

I also tried LCD on 845 chipset integrated graphics ("i810" driver). DDC returned max. clock as 150Mhz, but card was not able to deliver resolution no matter which modeline was used (855resolution is must). 

For now, my Ubuntu runs on 1280x1024 with N5200. I can't get any higher resolution to work. (Funny, I got 1600x1200 with i845 and the same panel in both Ubuntu and Slax. ) 

Thank you for any ideas. :-k

Note: changing card is no go. I need low profile AGP in my machine.

---

