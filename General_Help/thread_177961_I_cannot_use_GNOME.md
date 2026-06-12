---
title: "I cannot use GNOME"
date: 2006-05-17
forum: General Help
---

### Post by gos1 on 2006-05-17
Hi ;  
 I made some changes on my NVIDIA card (tried to install XGL) and now Gnome cannot start is there a wy for me to reinstall all the components from the UBUNTU cd without loosing any data ??? I want to reinstall kernel and GNOME

---

### Post by DougC on 2006-05-17
Do you have a seperate /home filesystem? If so you could copy everything you need to keep to there, reinstall without formatting your /home then copy everything back. 

Bit of a pain if you've installed lots of programs though.

---

### Post by gos1 on 2006-05-17
But in red at and other dists I could do that with the rescue mode is there anything in ubuntu to do or can I apt-get the kernel  ? and the gnome ?

---

### Post by dg_w on 2006-05-17
Ok

Which method did you use for installing XGL ?
Look for backups of /etc/X11/xorg.conf,
/etc/gdm/gdm.conf-custom etc ?

apt-get remove "package name" to remove what you installed
apt-get install --reinstall "package name to re-install drivers etc 

ie to re-install nvidia drivers
sudo apt-get install --reinstall nvidia-glx nvidia-kernel-common
sudo apt-get install --reinstall ubuntu-desktop (gnome etc)

When you say you can not run gnome ... what error are you getting ? xserver erros ? or gdm error ?

dg_w

---

### Post by gos1 on 2006-05-17
the screen locks down for 3 or 4 times and then a blue error page appears. There it says I cannot find the drivers of NVIDIA etc and after that just the console works. 
 I played with the system files for a long time thats why I want to reinstall gnome and the kernel from console. Anybody knows how to  ???

---

### Post by gos1 on 2006-05-18
ok let me send you the Xorg.93.log.  When I restart my computer I see this file as error message ,
-------------------------------------

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.12 i686
Current Operating System: Linux master 2.6.12-10-386 #1 Fri Apr 28 13:13:44 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.93.log", Time: Thu May 18 01:24:47 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "NVIDIA Corporation NVCrush11 [GeForce2 MX Integrated Graphics]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/CID" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.8
	X.Org XInput driver : 0.5
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,01a4 card 0000,0000 rev b2 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 10de,01ac card 1462,3730 rev b2 class 05,00,00 hdr 80
(II) PCI: 00:00:2: chip 10de,01ad card 1462,3730 rev b2 class 05,00,00 hdr 80
(II) PCI: 00:00:3: chip 10de,01ab card 1462,3730 rev b2 class 05,00,00 hdr 80
(II) PCI: 00:01:0: chip 10de,01b2 card 1462,3730 rev c3 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,01b4 card 1462,3730 rev c1 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,01c2 card 1462,3730 rev c3 class 0c,03,10 hdr 00
(II) PCI: 00:03:0: chip 10de,01c2 card 1462,3730 rev c3 class 0c,03,10 hdr 00
(II) PCI: 00:04:0: chip 10de,01c3 card 1462,373c rev c2 class 02,00,00 hdr 00
(II) PCI: 00:05:0: chip 10de,01b0 card 1462,3730 rev c2 class 04,01,00 hdr 00
(II) PCI: 00:06:0: chip 10de,01b1 card 1462,3730 rev c2 class 04,01,00 hdr 80
(II) PCI: 00:06:1: chip 10de,01c1 card 1462,3730 rev c1 class 07,03,00 hdr 80
(II) PCI: 00:08:0: chip 10de,01b8 card 0000,0000 rev c2 class 06,04,00 hdr 01
(II) PCI: 00:09:0: chip 10de,01bc card 1462,3730 rev c3 class 01,01,8a hdr 00
(II) PCI: 00:1e:0: chip 10de,01b7 card 0000,0000 rev b2 class 06,04,00 hdr 01
(II) PCI: 02:00:0: chip 10de,01a0 card 1462,3738 rev b1 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:8:0), (0,1,1), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x000e (VGA_EN is set)
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xec000000 - 0xedffffff (0x2000000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B]
(--) PCI:*(2:0:0) nVidia Corporation NVCrush11 [GeForce2 MX Integrated Graphics] rev 177, Mem @ 0xec000000/24, 0xe0000000/27
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xe8000000 from 0xebffffff to 0xe7ffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xee082000 - 0xee082fff (0x1000) MX[B]
	[1] -1	0	0xee081000 - 0xee081fff (0x1000) MX[B]
	[2] -1	0	0xee000000 - 0xee07ffff (0x80000) MX[B]
	[3] -1	0	0xee084000 - 0xee0843ff (0x400) MX[B]
	[4] -1	0	0xee083000 - 0xee083fff (0x1000) MX[B]
	[5] -1	0	0xee080000 - 0xee080fff (0x1000) MX[B]
	[6] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[7] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[8] -1	0	0xec000000 - 0xecffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[10] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B]
	[11] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[12] -1	0	0x0000d400 - 0x0000d47f (0x80) IX[B]
	[13] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[14] -1	0	0x0000cc00 - 0x0000cc07 (0x8) IX[B]
	[15] -1	0	0x00006000 - 0x0000601f (0x20) IX[B]
	[16] -1	0	0x00005020 - 0x0000502f (0x10) IX[B]
	[17] -1	0	0x00005000 - 0x0000500f (0x10) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xee082000 - 0xee082fff (0x1000) MX[B]
	[1] -1	0	0xee081000 - 0xee081fff (0x1000) MX[B]
	[2] -1	0	0xee000000 - 0xee07ffff (0x80000) MX[B]
	[3] -1	0	0xee084000 - 0xee0843ff (0x400) MX[B]
	[4] -1	0	0xee083000 - 0xee083fff (0x1000) MX[B]
	[5] -1	0	0xee080000 - 0xee080fff (0x1000) MX[B]
	[6] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[7] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[8] -1	0	0xec000000 - 0xecffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[10] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B]
	[11] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[12] -1	0	0x0000d400 - 0x0000d47f (0x80) IX[B]
	[13] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[14] -1	0	0x0000cc00 - 0x0000cc07 (0x8) IX[B]
	[15] -1	0	0x00006000 - 0x0000601f (0x20) IX[B]
	[16] -1	0	0x00005020 - 0x0000502f (0x10) IX[B]
	[17] -1	0	0x00005000 - 0x0000500f (0x10) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xee082000 - 0xee082fff (0x1000) MX[B]
	[6] -1	0	0xee081000 - 0xee081fff (0x1000) MX[B]
	[7] -1	0	0xee000000 - 0xee07ffff (0x80000) MX[B]
	[8] -1	0	0xee084000 - 0xee0843ff (0x400) MX[B]
	[9] -1	0	0xee083000 - 0xee083fff (0x1000) MX[B]
	[10] -1	0	0xee080000 - 0xee080fff (0x1000) MX[B]
	[11] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[12] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0xec000000 - 0xecffffff (0x1000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[17] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B]
	[18] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[19] -1	0	0x0000d400 - 0x0000d47f (0x80) IX[B]
	[20] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[21] -1	0	0x0000cc00 - 0x0000cc07 (0x8) IX[B]
	[22] -1	0	0x00006000 - 0x0000601f (0x20) IX[B]
	[23] -1	0	0x00005020 - 0x0000502f (0x10) IX[B]
	[24] -1	0	0x00005000 - 0x0000500f (0x10) IX[B]
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions/libGLcore.so
dlopen: /usr/lib/xorg/modules/extensions/libGLcore.so: undefined symbol: __glXLastContext
(EE) Failed to load /usr/lib/xorg/modules/extensions/libGLcore.so
(II) UnloadModule: "GLcore"
(EE) Failed to load module "GLcore" (loader failed, 7)
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
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
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.0.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions/libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "nv"
(WW) Warning, couldn't open module nv
(II) UnloadModule: "nv"
(EE) Failed to load module "nv" (module does not exist, 0)
(II) LoadModule: "kbd"
(WW) Warning, couldn't open module kbd
(II) UnloadModule: "kbd"
(EE) Failed to load module "kbd" (module does not exist, 0)
(II) LoadModule: "mouse"
(WW) Warning, couldn't open module mouse
(II) UnloadModule: "mouse"
(EE) Failed to load module "mouse" (module does not exist, 0)
(EE) No drivers available.

Fatal server error:
no screens found
------------------------
What should I do to fix it ? ?

---

### Post by dg_w on 2006-05-18
Have you tried the above ?

From a console (ALT+CTRL+F2)
sudo apt-get update

sudo apt-get remove ubuntu-desktop
sudo apt-get remove nvidia-glx nvidia-kernel-com

sudo apt-get purge ubuntu-desktop
sudo apt-get purge nvidia-glx nvidia-kernel

sudo apt-get install -reinstall linux-386
sudo apt-get install ubuntu-desktop
sudo apt-get install nvidia-glx nvidia-kernel

---

### Post by thirdmusketeer on 2006-05-18
The above solution might just work for me as well, but when I tried to remove ubuntu-desktop, it came back with the message that ubuntu-desktop is not installed.

---

### Post by gos1 on 2006-05-18
Thanks a lot for your help but after logging into my console I realised that I am not connected to internet tried a few commands to connect like ethtool but couldnt find out the way does anybody know how to ?

---

### Post by dg_w on 2006-05-18
ok how do you connect via a router ?
presumeing your router is on 192.168.0.1  (change these settings to match your ip address)
ifconfig eth0 192.168.0.5 
(gives you that ip address)
route add default gw 192.168.0.1
(your router)
No try . make sure the router is in your resolv.conf
sudo vi /etc/resolv.conf

nameserver 192.168.0.1

now see if you can connect ....

let me know

---

