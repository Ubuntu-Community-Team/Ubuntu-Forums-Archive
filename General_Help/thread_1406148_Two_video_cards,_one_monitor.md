---
title: "Two video cards, one monitor"
date: 2010-02-13
forum: General Help
---

### Post by dhess31 on 2010-02-13
OK.  I have a Mac Pro that has two video cards in it.  One, an crappy EFI card and the other a GTX 260.

I run three OS's, Snow Leopard, Win 7 and Ubuntu 9.10.

The problem I have is Ubuntu boots up, and subsequently uses the EFI card instead of the GTX 260.

How do I get Ubuntu to use the 260 instead?  I don't care if it boots using the EFI card, but once X starts I want Ubuntu to use the 260 and not the 7300.

Any suggestions?

Don

---

### Post by flippo on 2010-02-13
You'll have to install the nvidia proprietary drivers, then tell Xorg to load them.  Nvidia has a tool called nvidia-settings which will set up xorg.conf for you, once you install the nvidia drivers.

---

### Post by dhess31 on 2010-02-13
I did that already, but didn't see any options for changing the card around.  It does have a "monitor detect" button, so I unplugged from the 7300 and plugged into the 260. Before I did this, I put the mouse on the "detect monitor" button (because after I move the monitor cable around the screen is blank lol) then clicked the button  but it still only used the 7300.

There are options for dual monitors, but that's not what I need.

Don

---

### Post by flippo on 2010-02-13
Ahhh, I see.  I've never done this myself, but in your xorg.conf there should be a "Device" section.  It should list your card, device and PCI bus point.  Try configuring that section manually to use your GTX 260.  (I think you can find the PCI bus of your device with "sudo lspci | grep nVidia").  Make sure you reference the correct device in all subsequent sections.

---

### Post by dhess31 on 2010-02-13
Well, with the new Xorg.conf layout, it just loads the driver and doesn't have all the old sections like it used to.  lol.

I'll figure it out.

D.

---

### Post by dhess31 on 2010-02-13
No luck.  I configured an additional screen for the second card, then disabled the first one (the 7300) but when I rebooted, it was back to the original way.

Any other thoughts?

D.

---

### Post by flippo on 2010-02-13
Can you post your Xorg.conf just to be sure everything looks good?  I would also check Xorg.0.log (/var/log/Xorg.0.log) and see if that notes detecting the card.

---

### Post by dhess31 on 2010-02-13
Here's the xorg.conf


Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

Here the log:


X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server x86_64 Ubuntu
Current Operating System: Linux MylesUbuntu 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 02:39:34 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-19-generic root=UUID=54348eed-bf1a-404f-831b-a87d724a3648 ro quiet splash
Build Date: 14 November 2009  05:48:57PM
xorg-server 2:1.6.4-2ubuntu4.1 (buildd@) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Feb 13 15:40:58 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No device specified for screen "Default Screen".
	Using the first device section listed.
(**) |   |-->Device "Default Device"
(==) No monitor specified for screen "Default Screen".
	Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0xb40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0:3:0:0) 10de:0393:0000:0400 nVidia Corporation G73 [GeForce 7300 GT] rev 161, Mem @ 0xc5000000/16777216, 0xa0000000/268435456, 0xc4000000/16777216, I/O @ 0x00003000/128, BIOS @ 0x????????/131072
(--) PCI: (0:8:0:0) 10de:05e2:3842:1257 nVidia Corporation GT200 [GeForce GTX 260] rev 161, Mem @ 0xc2000000/16777216, 0xb0000000/268435456, 0xc0000000/33554432, I/O @ 0x00001000/128, BIOS @ 0x????????/524288
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
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[21] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[22] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[23] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[24] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[25] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[26] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[27] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[28] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[29] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[30] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[31] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[32] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[33] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[34] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[35] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[36] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[37] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[38] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[39] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[40] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[41] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[42] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[43] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[44] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[45] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[46] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[47] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[48] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[49] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[50] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[51] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[52] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[53] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[54] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[55] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[56] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[57] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[58] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[59] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[60] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[61] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[62] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[63] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[64] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[65] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[66] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[67] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[68] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[69] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[70] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[71] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  185.18.36  Fri Aug 14 18:27:24 PDT 2009
(II) Loading extension GLX
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
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  185.18.36  Fri Aug 14 17:51:02 PDT 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 03@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[21] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[22] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[23] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[24] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[25] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[26] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[27] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[28] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[29] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[30] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[31] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[32] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[33] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[34] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[35] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[36] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[37] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[38] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[39] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[40] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[41] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[42] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[43] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[44] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[45] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[46] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[47] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[48] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[49] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[50] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[51] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[52] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[53] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[54] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[55] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[56] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[57] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[58] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[59] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[60] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[61] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[62] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[63] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[64] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[65] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[66] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[67] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[68] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[69] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[70] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[71] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 7300 GT (G73) at PCI:3:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.73.22.29.a1
(II) NVIDIA(0): Detected PCI Express Link width: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7300 GT at PCI:3:0:0:
(--) NVIDIA(0):     Proview (CRT-0)
(--) NVIDIA(0): Proview (CRT-0): 400.0 MHz maximum pixel clock
(WW) NVIDIA(0): The EDID for Proview (CRT-0) contradicts itself: mode
(WW) NVIDIA(0):     "800x600" is specified in the EDID; however, the EDID's
(WW) NVIDIA(0):     valid VertRefresh range (60.000-75.000 Hz) would exclude
(WW) NVIDIA(0):     this mode's VertRefresh (56.2 Hz); ignoring VertRefresh
(WW) NVIDIA(0):     check for mode "800x600".
(II) NVIDIA(0): Assigned Display Device: CRT-0
(==) NVIDIA(0): 
(==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) NVIDIA(0):     will be used as the requested mode.
(==) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1440 x 900
(--) NVIDIA(0): DPI set to (89, 87); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
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
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[21] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[22] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[23] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[24] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[25] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[26] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[27] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[28] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[29] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[30] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[31] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[32] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[33] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[34] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[35] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[36] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[37] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[38] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[39] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[40] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[41] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[42] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[43] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[44] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[45] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[46] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[47] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[48] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[49] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[50] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[51] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[52] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[53] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[54] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[55] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[56] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[57] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[58] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[59] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[60] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[61] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[62] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[63] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[64] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[65] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[66] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[67] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[68] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[69] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[70] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[71] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(GPU-1): NVIDIA GPU GeForce GTX 260 (GT200) at PCI:8:0:0 (GPU-1)
(--) NVIDIA(GPU-1): Memory: 917504 kBytes
(--) NVIDIA(GPU-1): VideoBIOS: 62.00.38.00.50
(II) NVIDIA(GPU-1): Detected PCI Express Link width: 16X
(--) NVIDIA(GPU-1): Interlaced video modes are supported on this GPU
(--) NVIDIA(GPU-1): Connected display device(s) on GeForce GTX 260 at PCI:8:0:0:
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
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
(II) Initializing extension GLX
(II) config/hal: Adding input device UVC Camera (046d:09a4)
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 2.2.5
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) UVC Camera (046d:09a4): always reports core events
(**) UVC Camera (046d:09a4): Device: "/dev/input/event6"
(II) UVC Camera (046d:09a4): Found keys
(II) UVC Camera (046d:09a4): Configuring as keyboard
(II) XINPUT: Adding extended input device "UVC Camera (046d:09a4)" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_variant" "mac"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) config/hal: Adding input device Mitsumi Electric Apple Extended USB Keyboard
(**) Mitsumi Electric Apple Extended USB Keyboard: always reports core events
(**) Mitsumi Electric Apple Extended USB Keyboard: Device: "/dev/input/event5"
(II) Mitsumi Electric Apple Extended USB Keyboard: Found keys
(II) Mitsumi Electric Apple Extended USB Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Mitsumi Electric Apple Extended USB Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_variant" "mac"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) config/hal: Adding input device Mitsumi Electric Apple Extended USB Keyboard
(**) Mitsumi Electric Apple Extended USB Keyboard: always reports core events
(**) Mitsumi Electric Apple Extended USB Keyboard: Device: "/dev/input/event4"
(II) Mitsumi Electric Apple Extended USB Keyboard: Found keys
(II) Mitsumi Electric Apple Extended USB Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Mitsumi Electric Apple Extended USB Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_variant" "mac"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_variant" "mac"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_variant" "mac"
(**) Option "xkb_options" "lv3:ralt_switch"
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
(II) config/hal: Adding input device Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): always reports core events
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Device: "/dev/input/event3"
(II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found 3 mouse buttons
(II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found x and y relative axes
(II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found scroll wheel(s)
(II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Configuring as mouse
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): YAxisMapping: buttons 4 and 5
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)" (type: MOUSE)
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): (accel) keeping acceleration scheme 1
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): (accel) filter chain progression: 2.00
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): (accel) filter stage 0: 20.00 ms
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): (accel) set acceleration profile 0
(II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): initialized for relative axes.

---

### Post by flippo on 2010-02-13
It looks like the card you want to use is on PCI:8:0:0.  try adding ```

DeviceName  "GeForce GTX 260"
BusId  "PCI:8:0:0"

``` to your device section, and see what happens.

---

### Post by dhess31 on 2010-02-13
Didn't work.

D.

---

### Post by flippo on 2010-02-13
Does the Option "NoLogo" "True" that you have in there work, or is the device your specifying just not being used?

---

### Post by dhess31 on 2010-02-13
I changed Nologo to false, but it didn't seem to do anything.

I didn't see an Nvidia splash screen.

D.

---

### Post by flippo on 2010-02-13
Hmm, try changing your xorg.conf to use the "nv" driver instead of the nvidia one, that should have a very big difference.  If it doesn't work, then xorg is not using your .conf file for some reason.  If it does work then we just need to set up the correct xorg.conf.  

If you need to configure the xorg.conf correctly:
Here are the relevant portions of mine, I also use an nvidia card.  Just modify the device part to use your card and it may work.
```

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    Option         "Xinerama" "0"
EndSection

Section "Device"
    Identifier     "Card0"
    Driver         "nvidia"
    VendorName     "nVidia Corporation"
    BoardName      "GeForce 8600M GT"
    BusID          "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

if using nv causes a difference try using this as your xorg.conf, but change the relevant parts of your device section (BoardName and BusId).

---

### Post by dhess31 on 2010-02-13
Success!  That actually worked!

Thanks for all the help man.

D.

---

