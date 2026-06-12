---
title: "xorg doesn't detect monitor, won't display higher than 800x600 on a 1400x900 monitor"
date: 2010-04-03
forum: General Help
---

### Post by miatawnt2b on 2010-04-03
I installed Karmic on an older PC I had laying around, and the only trouble I am having is with screen resolution.  It uses an old ATI chipset (onboard) for video, and it doesn't seem to do EDID correctly, so I can't display anything higher than 800x600.  I have tried creating an xorg.conf, but it's still not working.  How can I tell Xorg to ignore the fact it can't detect a widescreen monitor and display something larger than 800x600? I noticed the log says the sync's are out of range, but I am not sure how to fix it.

Here is my current xorg.conf.
```

Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "dri"
	Load  "dbe"
	Load  "record"
	Load  "extmod"
	Load  "dri2"
	Load  "glx"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "probe_sparse"       	# [<bool>]
        #Option     "accel"              	# [<bool>]
        #Option     "crt_display"        	# [<bool>]
        #Option     "composite_sync"     	# [<bool>]
        #Option     "hw_cursor"          	# [<bool>]
        #Option     "force_pci_mode"     	# [<bool>]
        #Option     "dma_mode"           	# <str>
        #Option     "agp_mode"           	# <i>
        #Option     "agp_size"           	# <i>
        #Option     "local_textures"     	# [<bool>]
        #Option     "buffer_size"        	# <i>
        #Option     "tv_out"             	# [<bool>]
        #Option     "tv_standard"        	# <str>
        #Option     "mmio_cache"         	# [<bool>]
        #Option     "test_mmio_cache"    	# [<bool>]
        #Option     "panel_display"      	# [<bool>]
        #Option     "reference_clock"    	# <freq>
        #Option     "shadow_fb"          	# [<bool>]
        #Option     "sw_cursor"          	# [<bool>]
        #Option     "AccelMethod"        	# <str>
        #Option     "RenderAccel"        	# [<bool>]
	Identifier  "Card0"
	Driver      "mach64"
	VendorName  "ATI Technologies Inc"
	BoardName   "Rage XL"
	BusID       "PCI:0:6:0"
	Option "UseEDID" "False"
	Option "NoDDC" "on"
	Option "IgnoreEDID" "on"
	Option "ModeValidation" "NoEdidModes, NoMaxPClkCheck, NoVertRefreshCheck, NoHorizSyncCheck, NoEdidMaxPClkCheck, NoDFPNativeResolutionCheck"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

```

And the Xorg.0.log
```


X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux user-desktop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.31-14-generic root=UUID=38803fd9-0ea0-4b36-b568-46dd4513b88d ro quiet splash nomodeset acpi=force
Build Date: 04 March 2010  09:56:47AM
xorg-server 2:1.6.4-2ubuntu4.2 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Apr  3 07:29:36 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "X.org Configured"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Card0"
(**) |-->Input Device "Mouse0"
(**) |-->Input Device "Keyboard0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(**) ModulePath set to "/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Mouse0
(WW) Disabling Keyboard0
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0:0:6:0) 1002:4752:0000:0000 ATI Technologies Inc Rage XL rev 39, Mem @ 0xd4000000/16777216, 0xd6200000/4096, I/O @ 0x0000f000/256, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[9] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[10] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[11] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri2" will be loaded. This was enabled by default and also specified in the config file.
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "mach64"
(II) Loading /usr/lib/xorg/modules/drivers//mach64_drv.so
(II) Module mach64: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 6.8.2
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) MACH64: Driver for ATI Mach64 chipsets
(II) Primary Device is: PCI 00@00:06:0
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[9] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[10] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[11] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(==) MACH64(0): Depth 24, (--) framebuffer bpp 32
(==) MACH64(0): Using XAA acceleration architecture
(II) MACH64: Mach64 in slot 0:6:0 detected.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(II) MACH64(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.1.0
	ABI class: X.Org Video Driver, version 5.0
(II) MACH64(0): VESA BIOS detected
(II) MACH64(0): VESA VBE Version 2.0
(II) MACH64(0): VESA VBE Total Mem: 4096 kB
(II) MACH64(0): VESA VBE OEM: ATI MACH64
(II) MACH64(0): VESA VBE OEM Software Rev: 1.0
(II) MACH64(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) MACH64(0): VESA VBE OEM Product: MACH64GM
(II) MACH64(0): VESA VBE OEM Product Rev: 01.00
(**) MACH64(0): Option "NoDDC" "on"
(II) MACH64(0): BIOS Data:  BIOSSize=0x8000, ROMTable=0x0114.
(II) MACH64(0): BIOS Data:  ClockTable=0x0820, FrequencyTable=0x0000.
(II) MACH64(0): BIOS Data:  LCDTable=0x0000.
(II) MACH64(0): BIOS Data:  VideoTable=0x0000, HardwareTable=0x015E.
(II) MACH64(0): BIOS Data:  I2CType=0x0F, Tuner=0x00, Decoder=0x00, Audio=0x0F.
(--) MACH64(0): ATI 3D Rage XL or XC graphics controller detected.
(--) MACH64(0): Chip type 4752 "GR", version 7, foundry TSMC, class 0, revision 0x00.
(--) MACH64(0): PCI bus interface detected;  block I/O base is 0xF000.
(--) MACH64(0): ATI Mach64 adapter detected.
(!!) MACH64(0): For information on using the multimedia capabilities
	of this adapter, please see http://gatos.sf.net.
(--) MACH64(0): Internal RAMDAC (subtype 1) detected.
(==) MACH64(0): RGB weight 888
(==) MACH64(0): Default visual is TrueColor
(==) MACH64(0): Using gamma correction (1.0, 1.0, 1.0)
(II) MACH64(0): Using Mach64 accelerator CRTC.
(II) MACH64(0): Storing hardware cursor image at 0xD43FFC00.
(II) MACH64(0): Using 8 MB linear aperture at 0xD4000000.
(!!) MACH64(0): Virtual resolutions will be limited to 4095 kB
 due to linear aperture size and/or placement of hardware cursor image area.
(II) MACH64(0): Using Block 0 MMIO aperture at 0xD6200400.
(II) MACH64(0): Using Block 1 MMIO aperture at 0xD6200000.
(II) MACH64(0): MMIO write caching enabled.
(--) MACH64(0): 4096 kB of SGRAM (2:1) 32-bit detected (using 4095 kB).
(WW) MACH64(0): Cannot shadow an accelerated frame buffer.
(II) MACH64(0): Engine XCLK 59.922 MHz;  Refresh rate code 1.
(--) MACH64(0): Internal programmable clock generator detected.
(--) MACH64(0): Reference clock 29.500 MHz.
(II) MACH64(0): Monitor0: Using default hsync range of 31.50-37.90 kHz
(II) MACH64(0): Monitor0: Using default vrefresh range of 50.00-70.00 Hz
(II) MACH64(0): Maximum clock: 119.00 MHz
(II) MACH64(0): Not using default mode "640x350" (vrefresh out of range)
(II) MACH64(0): Not using default mode "320x175" (vrefresh out of range)
(II) MACH64(0): Not using default mode "640x400" (vrefresh out of range)
(II) MACH64(0): Not using default mode "320x200" (vrefresh out of range)
(II) MACH64(0): Not using default mode "720x400" (vrefresh out of range)
(II) MACH64(0): Not using default mode "360x200" (vrefresh out of range)
(II) MACH64(0): Not using default mode "640x480" (vrefresh out of range)
(II) MACH64(0): Not using default mode "320x240" (vrefresh out of range)
(II) MACH64(0): Not using default mode "640x480" (vrefresh out of range)
(II) MACH64(0): Not using default mode "320x240" (vrefresh out of range)
(II) MACH64(0): Not using default mode "640x480" (hsync out of range)
(II) MACH64(0): Not using default mode "320x240" (hsync out of range)
(II) MACH64(0): Not using default mode "800x600" (hsync out of range)
(II) MACH64(0): Not using default mode "400x300" (hsync out of range)
(II) MACH64(0): Not using default mode "800x600" (hsync out of range)
(II) MACH64(0): Not using default mode "400x300" (hsync out of range)
(II) MACH64(0): Not using default mode "800x600" (hsync out of range)
(II) MACH64(0): Not using default mode "400x300" (hsync out of range)
(II) MACH64(0): Not using default mode "1024x768" (vrefresh out of range)
(II) MACH64(0): Not using default mode "512x384" (vrefresh out of range)
(II) MACH64(0): Not using default mode "1024x768" (hsync out of range)
(II) MACH64(0): Not using default mode "512x384" (hsync out of range)
(II) MACH64(0): Not using default mode "1024x768" (hsync out of range)
(II) MACH64(0): Not using default mode "512x384" (hsync out of range)
(II) MACH64(0): Not using default mode "1024x768" (hsync out of range)
(II) MACH64(0): Not using default mode "512x384" (hsync out of range)
(II) MACH64(0): Not using default mode "1024x768" (hsync out of range)
(II) MACH64(0): Not using default mode "512x384" (hsync out of range)
(II) MACH64(0): Not using default mode "1152x864" (hsync out of range)
(II) MACH64(0): Not using default mode "576x432" (hsync out of range)
(II) MACH64(0): Not using default mode "1280x960" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "640x480" (hsync out of range)
(II) MACH64(0): Not using default mode "1280x960" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "640x480" (hsync out of range)
(II) MACH64(0): Not using default mode "1280x1024" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "640x512" (hsync out of range)
(II) MACH64(0): Not using default mode "1280x1024" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "640x512" (hsync out of range)
(II) MACH64(0): Not using default mode "1280x1024" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "640x512" (hsync out of range)
(II) MACH64(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "800x600" (hsync out of range)
(II) MACH64(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "800x600" (hsync out of range)
(II) MACH64(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "800x600" (hsync out of range)
(II) MACH64(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "800x600" (hsync out of range)
(II) MACH64(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "800x600" (hsync out of range)
(II) MACH64(0): Not using default mode "1792x1344" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "896x672" (hsync out of range)
(II) MACH64(0): Not using default mode "1792x1344" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) MACH64(0): Not using default mode "1856x1392" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "928x696" (hsync out of range)
(II) MACH64(0): Not using default mode "1856x1392" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) MACH64(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "960x720" (hsync out of range)
(II) MACH64(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) MACH64(0): Not using default mode "832x624" (hsync out of range)
(II) MACH64(0): Not using default mode "416x312" (hsync out of range)
(II) MACH64(0): Not using default mode "1152x864" (hsync out of range)
(II) MACH64(0): Not using default mode "576x432" (hsync out of range)
(II) MACH64(0): Not using default mode "1152x864" (hsync out of range)
(II) MACH64(0): Not using default mode "576x432" (hsync out of range)
(II) MACH64(0): Not using default mode "1152x864" (hsync out of range)
(II) MACH64(0): Not using default mode "576x432" (hsync out of range)
(II) MACH64(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) MACH64(0): Not using default mode "576x432" (hsync out of range)
(II) MACH64(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) MACH64(0): Not using default mode "576x432" (hsync out of range)
(II) MACH64(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) MACH64(0): Not using default mode "576x432" (hsync out of range)
(II) MACH64(0): Not using default mode "1360x768" (hsync out of range)
(II) MACH64(0): Not using default mode "680x384" (hsync out of range)
(II) MACH64(0): Not using default mode "1360x768" (hsync out of range)
(II) MACH64(0): Not using default mode "680x384" (hsync out of range)
(II) MACH64(0): Not using default mode "1400x1050" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "700x525" (hsync out of range)
(II) MACH64(0): Not using default mode "1400x1050" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "700x525" (hsync out of range)
(II) MACH64(0): Not using default mode "1400x1050" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "700x525" (hsync out of range)
(II) MACH64(0): Not using default mode "1400x1050" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "700x525" (hsync out of range)
(II) MACH64(0): Not using default mode "1440x900" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "720x450" (hsync out of range)
(II) MACH64(0): Not using default mode "1600x1024" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "800x512" (hsync out of range)
(II) MACH64(0): Not using default mode "1680x1050" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "840x525" (hsync out of range)
(II) MACH64(0): Not using default mode "1680x1050" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "840x525" (hsync out of range)
(II) MACH64(0): Not using default mode "1680x1050" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "840x525" (hsync out of range)
(II) MACH64(0): Not using default mode "1680x1050" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "840x525" (hsync out of range)
(II) MACH64(0): Not using default mode "1680x1050" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "840x525" (hsync out of range)
(II) MACH64(0): Not using default mode "1920x1080" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "960x540" (hsync out of range)
(II) MACH64(0): Not using default mode "1920x1200" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "960x600" (hsync out of range)
(II) MACH64(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) MACH64(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) MACH64(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) MACH64(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) MACH64(0): Not using mode "1024x768" (no mode of this name)
(--) MACH64(0): Virtual size is 800x600 (pitch 800)
(**) MACH64(0):  Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) MACH64(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) MACH64(0):  Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) MACH64(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) MACH64(0):  Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) MACH64(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) MACH64(0):  Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) MACH64(0): Modeline "400x300"x60.3   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
(**) MACH64(0):  Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) MACH64(0): Modeline "400x300"x56.3   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz)
(**) MACH64(0):  Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) MACH64(0): Modeline "320x240"x60.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz)
(==) MACH64(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.2.1
	ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) MACH64(0): I2C bus "Mach64" initialized.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[9] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[10] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[11] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(WW) MACH64(0): DRI static buffer allocation failed -- need at least 4687 kB video memory
(II) MACH64(0): Largest offscreen areas (with overlaps):
(II) MACH64(0): 	800 x 710 rectangle at 0,600
(II) MACH64(0): 	320 x 711 rectangle at 0,600
(II) MACH64(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Setting up tile and stipple cache:
		30 128x128 slots
(==) MACH64(0): Backing store disabled
(==) MACH64(0): Silken mouse enabled
(II) MACH64(0): DPMS enabled
(WW) MACH64(0): Option "UseEDID" is not used
(WW) MACH64(0): Option "IgnoreEDID" is not used
(WW) MACH64(0): Option "ModeValidation" is not used
(II) MACH64(0): Direct rendering disabled
(==) RandR enabled
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
(II) AIGLX: Screen 0 is not DRI2 capable
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 2.2.5
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device ImPS/2 Generic Wheel Mouse
(**) ImPS/2 Generic Wheel Mouse: always reports core events
(**) ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event4"
(II) ImPS/2 Generic Wheel Mouse: Found 3 mouse buttons
(II) ImPS/2 Generic Wheel Mouse: Found x and y relative axes
(II) ImPS/2 Generic Wheel Mouse: Found scroll wheel(s)
(II) ImPS/2 Generic Wheel Mouse: Configuring as mouse
(**) ImPS/2 Generic Wheel Mouse: YAxisMapping: buttons 4 and 5
(**) ImPS/2 Generic Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE)
(**) ImPS/2 Generic Wheel Mouse: (accel) keeping acceleration scheme 1
(**) ImPS/2 Generic Wheel Mouse: (accel) filter chain progression: 2.00
(**) ImPS/2 Generic Wheel Mouse: (accel) filter stage 0: 20.00 ms
(**) ImPS/2 Generic Wheel Mouse: (accel) set acceleration profile 0
(II) ImPS/2 Generic Wheel Mouse: initialized for relative axes.
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) Macintosh mouse button emulation: initialized for relative axes.
```


Please help me get something larger than 800x600 on this thing.  I don't think it has the memory to display the full 1400x900 (at least it wouldn't in windows) but I remember it doing 1152x864 in windows.

-J

---

### Post by mikewhatever on 2010-04-03
try this -> [http://ubuntuforums.org/showthread.php?t=1324239&highlight=resolution](http://ubuntuforums.org/showthread.php?t=1324239&highlight=resolution). Although, if the card can't handle high resolutions, I doubt it will help.

---

