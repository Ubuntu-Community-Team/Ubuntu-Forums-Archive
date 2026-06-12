---
title: "High CPU because of Xorg (no other processes running)"
date: 2009-08-20
forum: General Help
---

### Post by auddin2 on 2009-08-20
Hello all,
A little bit of history before I describe my problem:
  * I upgraded from 8.04 to 8.10 to 9.04, to find my dual monitors not working (with my Matrox G450 graphics card).
  * After trying a lot of things to fix it, I bought a new gfx card that I would make things easier (an nvidia card)
  * Dual monitors worked, but everything was so slow because of high CPU usage.  I thought it was probably due to some issue with 9.04.
  * I learned my lesson about upgrading to new releases, and made a new home partition, and reinstalled 8.04 in an effort to get it back the way it was before.
  * It seems that cpu usage was high even with a new install of 8.04, so I thought it was just the gfx card that was bad; everything will be fine once I go back to my old Matrox G450 gfx card.

Everything is not fine, as you can see when I run top:

```
Tasks: 105 total,   3 running, 102 sleeping,   0 stopped,   0 zombie
Cpu(s): 55.1%us,  5.0%sy,  0.0%ni, 39.9%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2074192k total,   855152k used,  1219040k free,    29092k buffers
Swap:  3004112k total,        0k used,  3004112k free,   516044k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                               
 5379 root      20   0  108m  53m 8508 R 39.9  2.7  22:21.53 [COLOR="DarkRed"]Xorg[/COLOR]                                  
 5903 atif      20   0  232m 122m  22m S  9.0  6.0   5:03.11 firefox                               
 6002 atif      20   0 39992  19m  12m S  6.7  1.0   0:15.58 gnome-system-mo                       
 5551 atif      20   0 20620  11m 7468 S  1.3  0.6   0:07.26 metacity                              
 5542 atif      20   0 15324 4876 3900 S  0.7  0.2   0:03.72 gnome-screensav                       
 5555 atif      20   0 54856  20m  12m S  0.7  1.0   0:06.17 gnome-panel                           
    1 root      20   0  2844 1688  544 S  0.0  0.1   0:01.46 init                                  
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd                              
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0                           
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0                           
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                            
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.18 events/0                              
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper                               
   41 root      15  -5     0    0    0 S  0.0  0.0   0:00.08 kblockd/0                             
   44 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid                                
   45 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify                          
  108 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod                               
  145 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                               
  146 root      20   0     0    0    0 S  0.0  0.0   0:00.18 pdflush                               
  147 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kswapd0                               
  188 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0                                 
 1425 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd                         
 1427 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khubd                                 
 1458 root      15  -5     0    0    0 S  0.0  0.0   0:00.60 ata/0                                 
 1464 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux                               
 1668 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0                             
 1670 root      15  -5     0    0    0 S  0.0  0.0   0:01.18 scsi_eh_1                             
 2411 root      15  -5     0    0    0 S  0.0  0.0   0:00.04 kjournald      
```

After reading this article: [https://wiki.ubuntu.com/X/Troubleshooting/HighCPU](https://wiki.ubuntu.com/X/Troubleshooting/HighCPU) , I tried this command:

```
$ glxinfo | grep render
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

```

I have attached my xorg.conf file, and here is my Xorg.0.log:
```
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Aug 20 12:23:58 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "DELL E173FP"
(**) |   |-->Device "G450 2"
(**) |-->Screen "Screen2" (1)
(**) |   |-->Monitor "DELL E173FP2"
(**) |   |-->Device "G450"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(**) Option "Xinerama"
(==) Automatically adding devices
(==) Automatically enabling devices
(**) Xinerama: enabled
(WW) The directory "/usr/share/X11/fonts/misc" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/Type1" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi" does not exist.
	Entry deleted from font path.
(==) Including the default font path /usr/share/fonts/X11/misc,/usr/share/fonts/X11/cyrillic,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81dc500
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 2.0
	X.Org XInput driver : 2.0
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2570 card 1028,01d5 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 8086,2572 card 1028,01d5 rev 02 class 03,80,00 hdr 00
(II) PCI: 00:1d:0: chip 8086,24d2 card 1028,01d5 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24d4 card 1028,01d5 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,24de card 1028,01d5 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24dd card 1028,01d5 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev c2 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24d0 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24db card 1028,01d5 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,24d3 card 1028,01d5 rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,24d5 card 1028,01d5 rev 02 class 04,01,00 hdr 00
(II) PCI: 01:00:0: chip 3388,0021 card 0000,0000 rev 15 class 06,04,00 hdr 01
(II) PCI: 01:08:0: chip 8086,1050 card 1028,01d5 rev 02 class 02,00,00 hdr 00
(II) PCI: 02:00:0: chip 102b,0525 card 102b,0d43 rev 85 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:30:0), (0,1,2), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfe000000 - 0xfeafffff (0xb00000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (1:0:0), (1,2,2), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfe000000 - 0xfe9fffff (0xa00000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B]
(--) PCI: (0:2:0) Intel Corporation 82865G Integrated Graphics Controller rev 2, Mem @ 0xe8000000/27, 0xfeb80000/19, I/O @ 0xed98/3
(--) PCI:*(2:0:0) Matrox Graphics, Inc. MGA G400/G450 rev 133, Mem @ 0xf8000000/25, 0xfe8fc000/14, 0xfe000000/23, BIOS @ 0xfe900000/17
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xf0000000 from 0xf7ffffff to 0xefffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfeaff000 - 0xfeafffff (0x1000) MX[B]
	[1] -1	0	0xfeb7f900 - 0xfeb7f9ff (0x100) MX[B]
	[2] -1	0	0xfeb7fa00 - 0xfeb7fbff (0x200) MX[B]
	[3] -1	0	0xfeb7fc00 - 0xfeb7ffff (0x400) MX[B]
	[4] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[5] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[6] -1	0	0xfe900000 - 0xfe91ffff (0x20000) MX[B](B)
	[7] -1	0	0xfe000000 - 0xfe7fffff (0x800000) MX[B](B)
	[8] -1	0	0xfe8fc000 - 0xfe8fffff (0x4000) MX[B](B)
	[9] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[10] -1	0	0x0000df40 - 0x0000df7f (0x40) IX[B]
	[11] -1	0	0x0000edc0 - 0x0000edff (0x40) IX[B]
	[12] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[13] -1	0	0x0000eda0 - 0x0000edbf (0x20) IX[B]
	[14] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[15] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[16] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[17] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[20] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[21] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
(II) Inactive PCI resource ranges:
	[0] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[1] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[2] -1	0	0x0000ed98 - 0x0000ed9f (0x8) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfeaff000 - 0xfeafffff (0x1000) MX[B]
	[1] -1	0	0xfeb7f900 - 0xfeb7f9ff (0x100) MX[B]
	[2] -1	0	0xfeb7fa00 - 0xfeb7fbff (0x200) MX[B]
	[3] -1	0	0xfeb7fc00 - 0xfeb7ffff (0x400) MX[B]
	[4] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[5] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[6] -1	0	0xfe900000 - 0xfe91ffff (0x20000) MX[B](B)
	[7] -1	0	0xfe000000 - 0xfe7fffff (0x800000) MX[B](B)
	[8] -1	0	0xfe8fc000 - 0xfe8fffff (0x4000) MX[B](B)
	[9] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[10] -1	0	0x0000df40 - 0x0000df7f (0x40) IX[B]
	[11] -1	0	0x0000edc0 - 0x0000edff (0x40) IX[B]
	[12] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[13] -1	0	0x0000eda0 - 0x0000edbf (0x20) IX[B]
	[14] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[15] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[16] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[17] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[20] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[21] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[1] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[2] -1	0	0x0000ed98 - 0x0000ed9f (0x8) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfeaff000 - 0xfeafffff (0x1000) MX[B]
	[5] -1	0	0xfeb7f900 - 0xfeb7f9ff (0x100) MX[B]
	[6] -1	0	0xfeb7fa00 - 0xfeb7fbff (0x200) MX[B]
	[7] -1	0	0xfeb7fc00 - 0xfeb7ffff (0x400) MX[B]
	[8] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[9] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[10] -1	0	0xfe900000 - 0xfe91ffff (0x20000) MX[B](B)
	[11] -1	0	0xfe000000 - 0xfe7fffff (0x800000) MX[B](B)
	[12] -1	0	0xfe8fc000 - 0xfe8fffff (0x4000) MX[B](B)
	[13] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[14] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[15] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000df40 - 0x0000df7f (0x40) IX[B]
	[19] -1	0	0x0000edc0 - 0x0000edff (0x40) IX[B]
	[20] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[21] -1	0	0x0000eda0 - 0x0000edbf (0x20) IX[B]
	[22] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[23] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[24] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[25] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[28] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[29] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[30] -1	0	0x0000ed98 - 0x0000ed9f (0x8) IX[B](B)
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded. This was enabled by default and also specified in the config file.
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  169.12  Thu Feb 14 18:45:56 PST 2008
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "type1"
(WW) Warning, couldn't open module type1
(II) UnloadModule: "type1"
(EE) Failed to load module "type1" (module does not exist, 0)
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "mga"
(II) Loading /usr/lib/xorg/modules/drivers//mga_drv.so
(II) Module mga: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.4.8
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) Wacom driver level: 47-0.7.9-8 $
(II) MGA: driver for Matrox chipsets: mga2064w, mga1064sg, mga2164w,
	mga2164w AGP, mgag100, mgag100 PCI, mgag200, mgag200 PCI,
	mgag200 SE A PCI, mgag200 SE B PCI, mgag400, mgag550
(II) Primary Device is: PCI 02:00:0
(--) Assigning device section with no busID to primary device
(--) Assigning device section with no busID to primary device
(WW) MGA: More than one matching Device section found: G450
(--) Chipset mgag400 found
(--) Chipset mgag400 found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfeaff000 - 0xfeafffff (0x1000) MX[B]
	[5] -1	0	0xfeb7f900 - 0xfeb7f9ff (0x100) MX[B]
	[6] -1	0	0xfeb7fa00 - 0xfeb7fbff (0x200) MX[B]
	[7] -1	0	0xfeb7fc00 - 0xfeb7ffff (0x400) MX[B]
	[8] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[9] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[10] -1	0	0xfe900000 - 0xfe91ffff (0x20000) MX[B](B)
	[11] -1	0	0xfe000000 - 0xfe7fffff (0x800000) MX[B](B)
	[12] -1	0	0xfe8fc000 - 0xfe8fffff (0x4000) MX[B](B)
	[13] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[14] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[15] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000df40 - 0x0000df7f (0x40) IX[B]
	[19] -1	0	0x0000edc0 - 0x0000edff (0x40) IX[B]
	[20] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[21] -1	0	0x0000eda0 - 0x0000edbf (0x20) IX[B]
	[22] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[23] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[24] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[25] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[28] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[29] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[30] -1	0	0x0000ed98 - 0x0000ed9f (0x8) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfeaff000 - 0xfeafffff (0x1000) MX[B]
	[5] -1	0	0xfeb7f900 - 0xfeb7f9ff (0x100) MX[B]
	[6] -1	0	0xfeb7fa00 - 0xfeb7fbff (0x200) MX[B]
	[7] -1	0	0xfeb7fc00 - 0xfeb7ffff (0x400) MX[B]
	[8] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[9] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[10] -1	0	0xfe900000 - 0xfe91ffff (0x20000) MX[B](B)
	[11] -1	0	0xfe000000 - 0xfe7fffff (0x800000) MX[B](B)
	[12] -1	0	0xfe8fc000 - 0xfe8fffff (0x4000) MX[B](B)
	[13] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[14] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[15] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000df40 - 0x0000df7f (0x40) IX[B]
	[22] -1	0	0x0000edc0 - 0x0000edff (0x40) IX[B]
	[23] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[24] -1	0	0x0000eda0 - 0x0000edbf (0x20) IX[B]
	[25] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[26] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[27] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[28] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[30] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[31] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[32] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[33] -1	0	0x0000ed98 - 0x0000ed9f (0x8) IX[B](B)
	[34] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[35] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Setting vga for screen 1.
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(--) MGA(0): Chipset: "mgag400" (G450)
(**) MGA(0): Depth 24, (--) framebuffer bpp 32
(==) MGA(0): RGB weight 888
(**) MGA(0): Option "HWcursor" "true"
(==) MGA(0): Using AGP 1x mode
(==) MGA(0): Using XAA acceleration
(--) MGA(0): Linear framebuffer at 0xF8000000
(**) MGA(0): MMIO registers at 0xFE8FC000
(--) MGA(0): Pseudo-DMA transfer window at 0xFE000000
(--) MGA(0): BIOS at 0xFE900000
(II) Attempted to read BIOS 128KB from /sys/bus/pci/devices/0000:02:00.0/rom: got 36KB
(--) MGA(0): Video BIOS info block at offset 0x07CE0
(--) MGA(0): Crtc2 will use 8192K of VideoRam
(**) MGA(0): VideoRAM: 8192 kByte
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(==) MGA(0): Write-combining range (0xf8000000,0x800000)
(II) MGA(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) MGA(0): I2C bus "DDC P1" initialized.
(II) MGA(0): I2C device "DDC P1:ddc2" registered at address 0xA0.
(II) MGA(0): I2C Monitor info: 0x824dbe0
(II) MGA(0): Manufacturer: DEL  Model: a00b  Serial#: 859395155
(II) MGA(0): Year: 2005  Week: 16
(II) MGA(0): EDID Version: 1.3
(II) MGA(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) MGA(0): Sync:  Separate
(II) MGA(0): Max H-Image Size [cm]: horiz.: 34  vert.: 27
(II) MGA(0): Gamma: 2.20
(II) MGA(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) MGA(0): Default color space is primary color space
(II) MGA(0): First detailed timing is preferred mode
(II) MGA(0): redX: 0.640 redY: 0.340   greenX: 0.279 greenY: 0.619
(II) MGA(0): blueX: 0.140 blueY: 0.069   whiteX: 0.310 whiteY: 0.330
(II) MGA(0): Supported VESA Video Modes:
(II) MGA(0): 720x400@70Hz
(II) MGA(0): 640x480@60Hz
(II) MGA(0): 640x480@75Hz
(II) MGA(0): 800x600@60Hz
(II) MGA(0): 800x600@75Hz
(II) MGA(0): 1024x768@60Hz
(II) MGA(0): 1024x768@75Hz
(II) MGA(0): 1280x1024@75Hz
(II) MGA(0): Manufacturer's mask: 0
(II) MGA(0): Supported Future Video Modes:
(II) MGA(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) MGA(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) MGA(0): Supported additional Video Mode:
(II) MGA(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) MGA(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) MGA(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) MGA(0): Ranges: V min: 56  V max: 75 Hz, H min: 31  H max: 80 kHz, PixClock max 140 MHz
(II) MGA(0): Serial No: D542854C39TS
(II) MGA(0): Monitor name: DELL E173FP
(II) MGA(0): EDID (in hex):
(II) MGA(0): 	00ffffffffffff0010ac0ba053543933
(II) MGA(0): 	100f010368221b78eecaf6a357479e23
(II) MGA(0): 	114f54a54b00714f8180010101010101
(II) MGA(0): 	010101010101302a009851002a403070
(II) MGA(0): 	1300520e1100001e000000fd00384b1f
(II) MGA(0): 	500e000a202020202020000000ff0044
(II) MGA(0): 	35343238353443333954530a000000fc
(II) MGA(0): 	0044454c4c204531373346500a2000b9
(II) MGA(0): end of I2C Monitor info
(II) MGA(0): EDID vendor "DEL", prod id 40971
(II) MGA(0): Using EDID range info for horizontal sync
(II) MGA(0): Using EDID range info for vertical refresh
(II) MGA(0): Printing DDC gathered Modelines:
(II) MGA(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) MGA(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) MGA(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) MGA(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) MGA(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) MGA(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) MGA(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) MGA(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) MGA(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) MGA(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) MGA(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(==) MGA(0): Using gamma correction (1.0, 1.0, 1.0)
(==) MGA(0): Min pixel clock is 17 MHz
(--) MGA(0): Max pixel clock is 1200 MHz
(II) MGA(0): DELL E173FP: Using hsync range of 31.00-80.00 kHz
(II) MGA(0): DELL E173FP: Using vrefresh range of 56.00-75.00 Hz
(II) MGA(0): DELL E173FP: Using maximum pixel clock of 140.00 MHz
(II) MGA(0): Clock range:  17.75 to 1200.00 MHz
(II) MGA(0): Not using default mode "640x350" (vrefresh out of range)
(II) MGA(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) MGA(0): Not using default mode "640x400" (vrefresh out of range)
(II) MGA(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) MGA(0): Not using default mode "720x400" (vrefresh out of range)
(II) MGA(0): Not using default mode "360x200" (vrefresh out of range)
(II) MGA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) MGA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) MGA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) MGA(0): Not using default mode "640x480" (vrefresh out of range)
(II) MGA(0): Not using default mode "320x240" (vrefresh out of range)
(II) MGA(0): Not using default mode "800x600" (vrefresh out of range)
(II) MGA(0): Not using default mode "400x300" (vrefresh out of range)
(II) MGA(0): Not using default mode "1024x768" (vrefresh out of range)
(II) MGA(0): Not using default mode "512x384" (vrefresh out of range)
(II) MGA(0): Not using default mode "1024x768" (vrefresh out of range)
(II) MGA(0): Not using default mode "512x384" (vrefresh out of range)
(II) MGA(0): Not using default mode "1280x960" (hsync out of range)
(II) MGA(0): Not using default mode "640x480" (hsync out of range)
(II) MGA(0): Not using default mode "1280x1024" (hsync out of range)
(II) MGA(0): Not using default mode "640x512" (hsync out of range)
(II) MGA(0): Not using default mode "1600x1200" (mode clock too high)
(II) MGA(0): Not using default mode "1600x1200" (hsync out of range)
(II) MGA(0): Not using default mode "800x600" (hsync out of range)
(II) MGA(0): Not using default mode "1600x1200" (hsync out of range)
(II) MGA(0): Not using default mode "800x600" (hsync out of range)
(II) MGA(0): Not using default mode "1600x1200" (hsync out of range)
(II) MGA(0): Not using default mode "800x600" (hsync out of range)
(II) MGA(0): Not using default mode "1600x1200" (hsync out of range)
(II) MGA(0): Not using default mode "800x600" (hsync out of range)
(II) MGA(0): Not using default mode "1792x1344" (insufficient memory for mode)
(II) MGA(0): Not using default mode "896x672" (hsync out of range)
(II) MGA(0): Not using default mode "1792x1344" (insufficient memory for mode)
(II) MGA(0): Not using default mode "896x672" (hsync out of range)
(II) MGA(0): Not using default mode "1856x1392" (insufficient memory for mode)
(II) MGA(0): Not using default mode "928x696" (hsync out of range)
(II) MGA(0): Not using default mode "1856x1392" (insufficient memory for mode)
(II) MGA(0): Not using default mode "928x696" (hsync out of range)
(II) MGA(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) MGA(0): Not using default mode "960x720" (hsync out of range)
(II) MGA(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) MGA(0): Not using default mode "960x720" (hsync out of range)
(II) MGA(0): Not using default mode "1152x768" (vrefresh out of range)
(II) MGA(0): Not using default mode "576x384" (vrefresh out of range)
(II) MGA(0): Not using default mode "1152x864" (vrefresh out of range)
(II) MGA(0): Not using default mode "576x432" (vrefresh out of range)
(II) MGA(0): Not using default mode "1400x1050" (mode clock too high)
(II) MGA(0): Not using default mode "1400x1050" (hsync out of range)
(II) MGA(0): Not using default mode "700x525" (hsync out of range)
(II) MGA(0): Not using default mode "1400x1050" (hsync out of range)
(II) MGA(0): Not using default mode "700x525" (hsync out of range)
(II) MGA(0): Not using default mode "1680x1050" (mode clock too high)
(II) MGA(0): Not using default mode "1920x1200" (insufficient memory for mode)
(II) MGA(0): Not using default mode "1920x1200" (insufficient memory for mode)
(II) MGA(0): Not using default mode "960x600" (hsync out of range)
(II) MGA(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) MGA(0): Not using default mode "960x720" (hsync out of range)
(II) MGA(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) MGA(0): Not using default mode "1024x768" (hsync out of range)
(II) MGA(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) MGA(0): Not using default mode "1024x768" (hsync out of range)
(II) MGA(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) MGA(0): Not using default mode "1024x768" (hsync out of range)
(--) MGA(0): Has SDRAM
(--) MGA(0): Virtual size is 1280x1024 (pitch 1280)
(**) MGA(0): *Driver mode "1280x1024": 108.0 MHz, 64.0 kHz, 60.0 Hz
(II) MGA(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(**) MGA(0): Display dimensions: (340, 270) mm
(**) MGA(0): DPI set to (95, 96)
(II) MGA(0): YDstOrg is set to 0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.2.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Reloading /usr/lib/xorg/modules//libvgahw.so
(--) MGA(1): Chipset: "mgag400" (G450)
(**) MGA(1): Depth 24, (--) framebuffer bpp 32
(==) MGA(1): RGB weight 888
(**) MGA(1): Option "HWcursor" "true"
(==) MGA(1): Using AGP 1x mode
(==) MGA(1): Using XAA acceleration
(--) MGA(1): Linear framebuffer at 0xF8000000
(**) MGA(1): MMIO registers at 0xFE8FC000
(--) MGA(1): Pseudo-DMA transfer window at 0xFE000000
(--) MGA(1): BIOS at 0xFE900000
(II) Attempted to read BIOS 128KB from /sys/bus/pci/devices/0000:02:00.0/rom: got 36KB
(--) MGA(1): Video BIOS info block at offset 0x07CE0
(**) MGA(1): VideoRAM: 8192 kByte
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(==) MGA(1): Write-combining range (0xf8800000,0x800000)
(II) MGA(1): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) MGA(1): I2C bus "DDC P2" initialized.
(II) MGA(1): I2C bus "MAVEN" initialized.
(II) MGA(1): Failed to register MGA-TVO I2C device!
(II) MGA(1): I2C device "DDC P2:ddc2" registered at address 0xA0.
(II) MGA(1): I2C Monitor info: 0x824f828
(II) MGA(1): Manufacturer: DEL  Model: a00b  Serial#: 810242636
(II) MGA(1): Year: 2004  Week: 33
(II) MGA(1): EDID Version: 1.3
(II) MGA(1): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) MGA(1): Sync:  Separate
(II) MGA(1): Max H-Image Size [cm]: horiz.: 34  vert.: 27
(II) MGA(1): Gamma: 2.20
(II) MGA(1): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) MGA(1): Default color space is primary color space
(II) MGA(1): First detailed timing is preferred mode
(II) MGA(1): redX: 0.640 redY: 0.340   greenX: 0.279 greenY: 0.619
(II) MGA(1): blueX: 0.140 blueY: 0.069   whiteX: 0.310 whiteY: 0.330
(II) MGA(1): Supported VESA Video Modes:
(II) MGA(1): 720x400@70Hz
(II) MGA(1): 640x480@60Hz
(II) MGA(1): 640x480@75Hz
(II) MGA(1): 800x600@60Hz
(II) MGA(1): 800x600@75Hz
(II) MGA(1): 1024x768@60Hz
(II) MGA(1): 1024x768@75Hz
(II) MGA(1): 1280x1024@75Hz
(II) MGA(1): Manufacturer's mask: 0
(II) MGA(1): Supported Future Video Modes:
(II) MGA(1): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) MGA(1): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) MGA(1): Supported additional Video Mode:
(II) MGA(1): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) MGA(1): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) MGA(1): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) MGA(1): Serial No: U493148B0KRL
(II) MGA(1): Monitor name: DELL E173FP
(II) MGA(1): Ranges: V min: 56  V max: 75 Hz, H min: 31  H max: 80 kHz, PixClock max 140 MHz
(II) MGA(1): EDID (in hex):
(II) MGA(1): 	00ffffffffffff0010ac0ba04c524b30
(II) MGA(1): 	210e010368221b78eecaf6a357479e23
(II) MGA(1): 	114f54a54b00714f8180010101010101
(II) MGA(1): 	010101010101302a009851002a403070
(II) MGA(1): 	1300520e1100001e000000ff00553439
(II) MGA(1): 	3331343842304b524c0a000000fc0044
(II) MGA(1): 	454c4c204531373346500a20000000fd
(II) MGA(1): 	00384b1f500e000a202020202020008c
(II) MGA(1): end of I2C Monitor info
(II) MGA(1): EDID vendor "DEL", prod id 40971
(II) MGA(1): Using EDID range info for horizontal sync
(II) MGA(1): Using EDID range info for vertical refresh
(II) MGA(1): Printing DDC gathered Modelines:
(II) MGA(1): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) MGA(1): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) MGA(1): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) MGA(1): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) MGA(1): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) MGA(1): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) MGA(1): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) MGA(1): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) MGA(1): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) MGA(1): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) MGA(1): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(==) MGA(1): Using gamma correction (1.0, 1.0, 1.0)
(==) MGA(1): Min pixel clock is 17 MHz
(--) MGA(1): Max pixel clock is 234 MHz
(II) MGA(1): DELL E173FP2: Using hsync range of 31.00-80.00 kHz
(II) MGA(1): DELL E173FP2: Using vrefresh range of 56.00-75.00 Hz
(II) MGA(1): DELL E173FP2: Using maximum pixel clock of 140.00 MHz
(II) MGA(1): Clock range:  17.75 to 234.00 MHz
(II) MGA(1): Not using default mode "640x350" (vrefresh out of range)
(II) MGA(1): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) MGA(1): Not using default mode "640x400" (vrefresh out of range)
(II) MGA(1): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) MGA(1): Not using default mode "720x400" (vrefresh out of range)
(II) MGA(1): Not using default mode "360x200" (vrefresh out of range)
(II) MGA(1): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) MGA(1): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) MGA(1): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) MGA(1): Not using default mode "640x480" (vrefresh out of range)
(II) MGA(1): Not using default mode "320x240" (vrefresh out of range)
(II) MGA(1): Not using default mode "800x600" (vrefresh out of range)
(II) MGA(1): Not using default mode "400x300" (vrefresh out of range)
(II) MGA(1): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) MGA(1): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) MGA(1): Not using default mode "1024x768" (vrefresh out of range)
(II) MGA(1): Not using default mode "512x384" (vrefresh out of range)
(II) MGA(1): Not using default mode "1280x960" (hsync out of range)
(II) MGA(1): Not using default mode "640x480" (hsync out of range)
(II) MGA(1): Not using default mode "1280x1024" (hsync out of range)
(II) MGA(1): Not using default mode "640x512" (hsync out of range)
(II) MGA(1): Not using default mode "1600x1200" (mode clock too high)
(II) MGA(1): Not using default mode "1600x1200" (hsync out of range)
(II) MGA(1): Not using default mode "800x600" (hsync out of range)
(II) MGA(1): Not using default mode "1600x1200" (hsync out of range)
(II) MGA(1): Not using default mode "800x600" (hsync out of range)
(II) MGA(1): Not using default mode "1600x1200" (hsync out of range)
(II) MGA(1): Not using default mode "800x600" (hsync out of range)
(II) MGA(1): Not using default mode "1600x1200" (hsync out of range)
(II) MGA(1): Not using default mode "800x600" (hsync out of range)
(II) MGA(1): Not using default mode "1792x1344" (insufficient memory for mode)
(II) MGA(1): Not using default mode "896x672" (hsync out of range)
(II) MGA(1): Not using default mode "1792x1344" (insufficient memory for mode)
(II) MGA(1): Not using default mode "896x672" (hsync out of range)
(II) MGA(1): Not using default mode "1856x1392" (insufficient memory for mode)
(II) MGA(1): Not using default mode "928x696" (hsync out of range)
(II) MGA(1): Not using default mode "1856x1392" (insufficient memory for mode)
(II) MGA(1): Not using default mode "928x696" (hsync out of range)
(II) MGA(1): Not using default mode "1920x1440" (insufficient memory for mode)
(II) MGA(1): Not using default mode "960x720" (hsync out of range)
(II) MGA(1): Not using default mode "1920x1440" (insufficient memory for mode)
(II) MGA(1): Not using default mode "960x720" (hsync out of range)
(II) MGA(1): Not using default mode "1152x768" (vrefresh out of range)
(II) MGA(1): Not using default mode "576x384" (vrefresh out of range)
(II) MGA(1): Not using default mode "1152x864" (vrefresh out of range)
(II) MGA(1): Not using default mode "576x432" (vrefresh out of range)
(II) MGA(1): Not using default mode "1400x1050" (mode clock too high)
(II) MGA(1): Not using default mode "1400x1050" (hsync out of range)
(II) MGA(1): Not using default mode "700x525" (hsync out of range)
(II) MGA(1): Not using default mode "1400x1050" (hsync out of range)
(II) MGA(1): Not using default mode "700x525" (hsync out of range)
(II) MGA(1): Not using default mode "1680x1050" (mode clock too high)
(II) MGA(1): Not using default mode "1920x1200" (insufficient memory for mode)
(II) MGA(1): Not using default mode "1920x1200" (insufficient memory for mode)
(II) MGA(1): Not using default mode "960x600" (hsync out of range)
(II) MGA(1): Not using default mode "1920x1440" (insufficient memory for mode)
(II) MGA(1): Not using default mode "960x720" (hsync out of range)
(II) MGA(1): Not using default mode "2048x1536" (insufficient memory for mode)
(II) MGA(1): Not using default mode "1024x768" (hsync out of range)
(II) MGA(1): Not using default mode "2048x1536" (insufficient memory for mode)
(II) MGA(1): Not using default mode "1024x768" (hsync out of range)
(II) MGA(1): Not using default mode "2048x1536" (insufficient memory for mode)
(II) MGA(1): Not using default mode "1024x768" (hsync out of range)
(--) MGA(1): Has SDRAM
(--) MGA(1): Virtual size is 1280x1024 (pitch 1280)
(**) MGA(1): *Driver mode "1280x1024": 108.0 MHz, 64.0 kHz, 60.0 Hz
(II) MGA(1): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(**) MGA(1): Display dimensions: (340, 270) mm
(**) MGA(1): DPI set to (95, 96)
(II) MGA(1): YDstOrg is set to 0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Reloading /usr/lib/xorg/modules//libfb.so
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Reloading /usr/lib/xorg/modules//libxaa.so
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  Yes, I do.
(II) resource ranges after preInit:
	[0] 0	0	0xfe000000 - 0xfe7fffff (0x800000) MX[B]
	[1] 0	0	0xfe8fc000 - 0xfe8fffff (0x4000) MX[B]
	[2] 0	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B]
	[3] 0	0	0xfe000000 - 0xfe7fffff (0x800000) MX[B]
	[4] 0	0	0xfe8fc000 - 0xfe8fffff (0x4000) MX[B]
	[5] 0	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B]
	[6] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[7] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[8] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[9] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[10] -1	0	0xfeaff000 - 0xfeafffff (0x1000) MX[B]
	[11] -1	0	0xfeb7f900 - 0xfeb7f9ff (0x100) MX[B]
	[12] -1	0	0xfeb7fa00 - 0xfeb7fbff (0x200) MX[B]
	[13] -1	0	0xfeb7fc00 - 0xfeb7ffff (0x400) MX[B]
	[14] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[15] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[16] -1	0	0xfe900000 - 0xfe91ffff (0x20000) MX[B](B)
	[17] -1	0	0xfe000000 - 0xfe7fffff (0x800000) MX[B](B)
	[18] -1	0	0xfe8fc000 - 0xfe8fffff (0x4000) MX[B](B)
	[19] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[20] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[21] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[22] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[23] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[24] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[25] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[26] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[27] -1	0	0x0000df40 - 0x0000df7f (0x40) IX[B]
	[28] -1	0	0x0000edc0 - 0x0000edff (0x40) IX[B]
	[29] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[30] -1	0	0x0000eda0 - 0x0000edbf (0x20) IX[B]
	[31] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[32] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[33] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[34] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[35] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[36] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[37] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[38] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[39] -1	0	0x0000ed98 - 0x0000ed9f (0x8) IX[B](B)
	[40] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[41] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(==) MGA(0): Write-combining range (0xf8000000,0x800000)
(II) MGA(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(--) MGA(0): 16 DWORD fifo
(==) MGA(0): Default visual is TrueColor
(EE) MGA(0): Static buffer allocation failed, not initializing the DRI
(EE) MGA(0): Need at least 15360 kB video memory at this resolution, bit depth
(II) MGA(0): Using 614 lines for offscreen memory.
(II) MGA(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid filled trapezoids
	8x8 mono pattern filled rectangles
	8x8 mono pattern filled trapezoids
	Indirect CPU to Screen color expansion
	Screen to Screen color expansion
	Solid Lines
	Dashed Lines
	Scanline Image Writes
	Setting up tile and stipple cache:
		20 128x128 slots
		5 256x256 slots
(==) MGA(0): Backing store disabled
(==) MGA(0): Silken mouse enabled
(**) Option "dpms"
(**) MGA(0): DPMS enabled
(II) MGA(0): Using overlay video
(WW) MGA(0): Direct rendering disabled
(==) RandR enabled
(==) MGA(1): Write-combining range (0xf8800000,0x800000)
(II) MGA(1): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(--) MGA(1): 16 DWORD fifo
(EE) MGA(1): Not initializing the DRI on the second head
(II) MGA(1): Using 614 lines for offscreen memory.
(II) MGA(1): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid filled trapezoids
	8x8 mono pattern filled rectangles
	8x8 mono pattern filled trapezoids
	Indirect CPU to Screen color expansion
	Screen to Screen color expansion
	Solid Lines
	Dashed Lines
	Scanline Image Writes
	Setting up tile and stipple cache:
		20 128x128 slots
		5 256x256 slots
(==) MGA(1): Backing store disabled
(==) MGA(1): Silken mouse enabled
(**) Option "dpms"
(**) MGA(1): DPMS enabled
(WW) MGA(1): Direct rendering disabled
(==) RandR enabled
(II) Entity 0 shares no resources
(II) Entity 1 shares no resources
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) evaluating device (eraser)
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) evaluating device (cursor)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) evaluating device (stylus)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
```

---

### Post by jocampo on 2009-08-20
Not sure, but your CPU is not high in my opinion ...

```

Cpu(s): [COLOR="Red"]55.1[/COLOR]%us,  5.0%sy,  0.0%ni, 39.9%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st

```

```

PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                               
 5379 root      20   0  108m  53m 8508 R [COLOR="Red"]39.9[/COLOR]  2.7  22:21.53 Xorg          

```

Try uptime command...leave it alone ... try uptime command again and compare results. %id should be higher, around 90% or so, which is idle value if I recall well ...

---

### Post by auddin2 on 2009-08-20
well, as soon I get other programs running, like thunderbird, and eclipse, the cpu % shoots up much higher.
It shouldn't take me like 2 seconds to switch from one tab in Firefox to another...it didn't use to be so slow.

---

### Post by bodhi.zazen on 2009-08-20
Most of the time it is because of a poor driver. What video card are you using ?

---

### Post by auddin2 on 2009-08-21
Thanks for the quick replies.
I'm using a Matrox G450. 
I looked in synaptic package manager and the latest version according to it is xserver-xorg-video-mga  1:1.4.8.dfsg.1-1

I went to the Matrox website ([http://www.matrox.com/graphics/en/support/drivers/download/certified/](http://www.matrox.com/graphics/en/support/drivers/download/certified/)) and downloaded this: matrox_driver-x86_32-4.4.0

When I ran the install script, it says:
```

:~/matrox_driver-x86_32-4.4.0$ sudo ./install.sh
[: 43: ==: unexpected operator
./install.sh: 57: function: not found
./install.sh: 69: function: not found
./install.sh: 78: function: not found
./install.sh: 95: function: not found

Please enter the full path to your current X11R6 directory: 
Example: /usr/X11R6
/usr/X11R6
./install.sh: 141: function: not found
test: 178: 0: unexpected operator
[: 178: ==: unexpected operator
[: 178: ==: unexpected operator
[: 178: ==: unexpected operator
[: 178: ==: unexpected operator
[: 178: ==: unexpected operator
-e \E[31mERROR: The X server drivers included in this installation package
-e        do not support the current version of your X server.

```

Any ideas?

---

### Post by auddin2 on 2009-08-21
Here is my Xorg version info

```
$ Xorg -version

This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux atif-desktop 2.6.24-24-generic #1 SMP Tue Aug 18 17:04:53 UTC 2009 i686
Build Date: 13 June 2008  01:08:21AM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present


```

---

### Post by auddin2 on 2009-08-24
Here is what I get when I run xrandr --verbose
```

$ xrandr --verbose
Xlib:  extension "RANDR" missing on display ":0.0".
RandR extension missing

```

---

### Post by bodhi.zazen on 2009-08-24
Since the driver you are needing is a 3rd party application, you will need to contact Matrox directly.

Do they not have a board, email address, or some type of technical assistance ?

> -e \E[31mERROR: The X server drivers included in this installation package[FONT=monospace]
[/FONT]-e        do not support the current version of your X server.

Ask them to publish an updated driver.

Your other options are:

1. Start hacking the driver or xorg yourself.

2. Buy a slightly older, inexpensive ati or nvidia card and replace your Matrox card. Make sure the card you buy is linux compatible, lol.

---

### Post by auddin2 on 2009-08-28
Ok, I've sent an email to Matrox Customer support.  
While I wait for them to reply back to me, I've installed the Nvidia card, and it's taking more CPU than my Matrox card.

What can I do now?  (Besides trying to email Nvidia support which I will do)

---

### Post by bodhi.zazen on 2009-08-28
What nvidia driver are you using ?

---

### Post by auddin2 on 2009-08-28
Thanks for the quick reply.

The version of xserver-xorg-video-nv that I have is 1:2.1.8-ubuntu(hardy).

Is that what you're looking for?

---

### Post by bodhi.zazen on 2009-08-28
I suggest you try the nvidia driver, either nvidia-glx-new, or installing the driver from the nvidia site .

---

### Post by auddin2 on 2009-08-31
Ok Installed the driver 173.14.20 from the Nvidia site following these instructions: [https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

The installer was successful in installing, but the X server keeps starting in low graphics mode.
Even if I run nvidia-xconfig, it still starts in low-graphics mode.
When I log in to X in low graphics mode I try running nvidia-settings, but it says, "It appears you're not using the nvidia driver" even though xorg.conf is configured to use the nvidia driver.

Here are a few commands that I ran:
```

$ cat /var/log/Xorg.0.log | grep EE
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

```

```
$dmesg | grep -i nv
[    0.000000]  BIOS-e820: 000000007fe70000 - 000000007fe72000 (ACPI NVS)
[   25.755762] nvidia: module license 'NVIDIA' taints kernel.
[   26.619157] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[338577.762816] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.20  Thu Jun 25 19:23:24 PDT 2009
[338636.427312] NVRM: loading NVIDIA Linux x86 Kernel Module  96.43.05  Tue Jan 22 19:36:58 PST 2008
[338636.428778] NVRM: API mismatch: the client has the version 173.14.20, but
[338636.428782] NVRM: this kernel module has the version 96.43.05.  Please
[338636.428783] NVRM: make sure that this kernel module and all NVIDIA driver
[338636.428785] NVRM: components have the same version.

```

What can I do now? (Besides asking Nvidia forums or support)

---

### Post by bodhi.zazen on 2009-08-31
Did you install nvidia-glx ?

You will need to remove teh nvidia driver, remove nvidia-glx, and remove the nv driver.

The re-install the nvidia driver (ths script NVIDIA-xyz.sh)

---

### Post by auddin2 on 2009-08-31
I think I removed all those packages, so I ran the uninstall script and tried installing again, but it still gave the same error message.  It's obvious that I haven't completely removed the previous kernel module (96.43.05)
Based on what I see in my synaptic package manager, I have removed nvidia-glx-new, and xserver-xorg-video-nv...which I thought was enough.  What else do I need to remove?  
I attempted to remove nvidia-kernel-common, but it says going to remove linux-generic, linux-restricted-modules, linux-restricted-modules-2.6.24-24-generic, and linux-restricted-modules-generic...so I canceled out of that and didn't remove it.  Is that what I need to remove?

---

### Post by auddin2 on 2009-08-31
Also, I removed /etc/init.d/nvidia-kernel and I did a search for nvidia.ko (couldn't find it in the file system) , so I'm wondering what else I have to remove...

---

### Post by bodhi.zazen on 2009-08-31
try rebooting =)

---

### Post by auddin2 on 2009-09-01
It worked.....it finally worked....now I have dual monitors, and it does the CPU does shoot up to 70%, but it will eventually go back down again.
Thanks!


Is there anything else I can do this at this point to tweak the performance? like over-clock the GPU?

---

### Post by bodhi.zazen on 2009-09-01
Awesome. There are many performance tweaks you can research. I find the defaults ar every reasonable, but happy exploring your system.

One to the few times rebooting is best (the nvidia drivers are a kernel module). Rebooting is not strictly necessary, it is the easiest and most reliable.

---

