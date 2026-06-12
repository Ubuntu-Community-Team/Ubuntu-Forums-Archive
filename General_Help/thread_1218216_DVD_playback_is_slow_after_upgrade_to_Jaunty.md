---
title: "DVD playback is slow after upgrade to Jaunty"
date: 2009-07-20
forum: General Help
---

### Post by thenanodude on 2009-07-20
I recently upgraded from Hardy to Jaunty and have discovered than all my DVDs play slowly is both Totem and VLC.  After searching this and other forums for 2 days without finding a solution, I have decided to start a new thread.  Here are some of my specs:

Desktop:  xfce
Computer: HP Pavilion dv2000
Video: nvidia Geforce 6150 Go
Processor: AMD turion 64
dvd+rw-tools version: 7.1-4
libdvdcss2 version: 1.2.10-0.2medibuntu1
libdvdnav4 version: 4.1.3-3
libdvdread3 version: 0.9.7-11ubuntu2
libdvdread4 version: 4.1.3-4ubuntu2
vlc version: 0.9.9a-2ubuntu1
libvlc2 version: 0.9.9a-2ubuntu1
libvlccore0 version: 0.9.9a-2ubuntu1
totem version: 2.26.1-0ubuntu5
totem-gstreamer version: 2.26.1-0ubuntu5

In VLC I set my video output to X11, as suggested in some posts (although flickering is not the problem): [http://ubuntuforums.org/showthread.php?t=974321](http://ubuntuforums.org/showthread.php?t=974321)  This seemed to help slightly, but not completely.

One potentially related problem:  when I insert a DVD I get the following errors indicating problems with mounting the device.  However, the DVD does indeed mount, so it just seems something is trying to mount it twice.
```

mount: block device /dev/sr0 is write-protected, mounting read-only
mount: /dev/sr0 already mounted or /media/cdrom0 busy
mount: according to mtab, /dev/sr0 is already mounted on /media/cdrom0.
```

I have looked at the system monitor while the video is playing back, and typically less than 25% of both processors and the memory is being used, so it is clearly not a resource issue.

Any help is appreciated.  Thanks!

---

### Post by thenanodude on 2009-07-27
Since my first post a week ago, I have continued to look into the problem, but with little progress.  It does seem that perhaps the read rates from my DVD are slow.  

from sudo hdparm -tT /dev/sda:
```
/dev/sda:
 Timing cached reads:   832 MB in  2.00 seconds = 415.52 MB/sec
 Timing buffered disk reads:   98 MB in  3.11 seconds =  31.48 MB/sec

```

I have seen that some have had a similar problem when DMA was not enabled:
[http://ubuntuforums.org/showthread.php?p=7525114](http://ubuntuforums.org/showthread.php?p=7525114)

I don't think this is my problem, but perhaps someone can confirm this.  I have a SATA drive, "so sudo hdparm -d1 /dev/sda" yields:

```
/dev/sda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device

```

Apparently you cannot set the DMA on a SATA drive with hdparm. (?) 

"sudo hdparm -v -i /dev/sda" results in:

```

/dev/sda:
 IO_support    =  0 (default) 
 readonly      =  0 (off)
 readahead     = 6144 (on)
 geometry      = 12161/255/63, sectors = 195371568, start = 0

 Model=ST9100824AS, FwRev=7.24    , SerialNo= 5PL24YLN
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=8192kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=195371568
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=yes: unknown setting WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode

```

Others have noted a problem arising from a conflict with the ATA_GENERIC driver:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/175022](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/175022)
[http://ubuntuforums.org/showthread.php?t=435706](http://ubuntuforums.org/showthread.php?t=435706)
[http://ubuntuforums.org/showthread.php?t=678153](http://ubuntuforums.org/showthread.php?t=678153)

I did find the ata_generic module was being loaded.  

output of "lsmod | grep -i libata"
```
libata                171488  4 ata_generic,pata_acpi,sata_nv,pata_amd
scsi_mod              161896  4 sd_mod,sg,sr_mod,libata

```

so I disabled it, but this did not help.

Finally, here is some output from "dmesg | grep -i ata":
```
[    0.451022] ACPI: EC: GPE = 0x1, I/O: command/status = 0x66, data = 0x62
[    2.455053] libata version 3.00 loaded.
[    3.006583] pata_amd 0000:00:0d.0: version 0.3.10
[    3.006636] pata_amd 0000:00:0d.0: setting latency timer to 64
[    3.007832] scsi0 : pata_amd
[    3.008742] scsi1 : pata_amd
[    3.009611] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x3080 irq 14
[    3.009615] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x3088 irq 15
[    3.337336] ata2.00: ATAPI: HL-DT-ST DVDRAM GSA-4084N, KQ09, max MWDMA2
[    3.337369] ata2: nv_mode_filter: 0x39f&0x7001->0x1, BIOS=0x0 (0x0) ACPI=0x7001 (60:600:0x11)
[    3.352359] ata2.00: configured for PIO0
[    3.472442] sata_nv 0000:00:0e.0: version 3.5
[    3.472456] sata_nv 0000:00:0e.0: enabling device (0005 -> 0007)
[    3.472946] sata_nv 0000:00:0e.0: PCI INT A -> Link[LTID] -> GSI 16 (level, high) -> IRQ 16
[    3.472950] sata_nv 0000:00:0e.0: Using SWNCQ mode
[    3.473038] sata_nv 0000:00:0e.0: setting latency timer to 64
[    3.474374] scsi2 : sata_nv
[    3.474501] scsi3 : sata_nv
[    3.474716] ata3: SATA max UDMA/133 cmd 0x30b0 ctl 0x30a4 bmdma 0x3090 irq 16
[    3.474721] ata4: SATA max UDMA/133 cmd 0x30a8 ctl 0x30a0 bmdma 0x3098 irq 16
[    4.352070] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.360237] ata3.00: ATA-7: ST9100824AS, 7.24, max UDMA/100
[    4.360241] ata3.00: 195371568 sectors, multi 16: LBA48 
[    4.376654] ata3.00: configured for UDMA/100
[    5.110602] ata4: SATA link down (SStatus 0 SControl 300)
[    5.110734] scsi 2:0:0:0: Direct-Access ATA ST9100824AS 7.24 PQ: 0 ANSI: 5

```

Any thoughts?!

---

### Post by Yellow Pasque on 2009-07-27
I don't see any issues with the drive or DVD. I would start looking into video driver issues. You may want to examine/post your /var/log/Xorg.0.log

---

### Post by thenanodude on 2009-07-27
Temüjin:

thanks for taking a look at my problem.  I have looked around for issues with my card (nvidia Geforce 6150 Go), but to no avail.  There seem to be some issues with the 8000/9000 series cards, but I haven't found anything with the 6000 series that seemed relevant.  Also, some very early versions of the drivers had problems, but I'm using a fairly recent one (180.44).  I'll keep looking, though!

Here is my /var/log/Xorg.0.log: 

```

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-15-server x86_64 Ubuntu
Current Operating System: Linux TheNanoDudE 2.6.28.9jd03 #1 SMP Sat Jul 25 19:35:47 EDT 2009 x86_64
Build Date: 09 April 2009  02:11:54AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@crested.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Jul 27 05:38:53 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Videocard0"
(**) Option "DontZap" "False"
(**) Option "Xinerama" "0"
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
(**) Extension "Composite" is enabled
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

(--) PCI:*(0@0:5:0) nVidia Corporation C51 [Geforce 6150 Go] rev 162, Mem @ 0xb2000000/16777216, 0xc0000000/268435456, 0xb1000000/16777216, BIOS @ 0x????????/131072
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
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "type1"
(WW) Warning, couldn't open module type1
(II) UnloadModule: "type1"
(EE) Failed to load module "type1" (module does not exist, 0)
(II) LoadModule: "freetype"
(WW) Warning, couldn't open module freetype
(II) UnloadModule: "freetype"
(EE) Failed to load module "freetype" (module does not exist, 0)
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  180.44  Tue Mar 24 06:11:47 PST 2009
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  180.44  Tue Mar 24 05:51:43 PST 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 00@00:05:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
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
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "RenderAccel" "true"
(**) NVIDIA(0): Option "TwinView" "1"
(**) NVIDIA(0): Option "MetaModes" "CRT: nvidia-auto-select +0+0, DFP: nvidia-auto-select +0+0"
(**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "CRT-0"
(**) NVIDIA(0): Option "AllowGLXWithComposite" "True"
(**) NVIDIA(0): Option "TripleBuffer" "1"
(**) NVIDIA(0): Option "UseEvents" "false"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Option "DisableGLXRootClipping" "true"
(**) NVIDIA(0): Option "DamageEvents" "1"
(**) NVIDIA(0): Option "OnDemandVBlankInterrupts" "true"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce Go 6150 (C51) at PCI:0:5:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.51.28.52.25
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce Go 6150 at PCI:0:5:0:
(--) NVIDIA(0):     Nvidia Default Flat Panel (DFP-0)
(--) NVIDIA(0): Nvidia Default Flat Panel (DFP-0): 310.0 MHz maximum pixel
(--) NVIDIA(0):     clock
(--) NVIDIA(0): Nvidia Default Flat Panel (DFP-0): Internal Dual Link LVDS
(**) NVIDIA(0): TwinView enabled
(II) NVIDIA(0): Display Device found referenced in MetaMode: DFP-0
(WW) NVIDIA(0): TwinView requested, but only 1 display devices found.
(II) NVIDIA(0): Assigned Display Device: DFP-0
(WW) NVIDIA(0): Invalid display device in Mode Description
(WW) NVIDIA(0):     "CRT:nvidia-auto-select+0+0"
(WW) NVIDIA(0): Not using mode description "CRT:nvidia-auto-select+0+0";
(WW) NVIDIA(0):     unable to map to display device
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "CRT:nvidia-auto-select+0+0,DFP:nvidia-auto-select+0+0"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 800
(--) NVIDIA(0): DPI set to (101, 101); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(**) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
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
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): ACPI display change hotkey events enabled: the X server is new
(II) NVIDIA(0):     enough to receive ACPI display change hotkey events.
(II) NVIDIA(0): Setting mode
(II) NVIDIA(0):     "CRT:nvidia-auto-select+0+0,DFP:nvidia-auto-select+0+0"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
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
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event0"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
(II) config/hal: Adding input device Video Bus
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event5"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Video Bus: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Video Bus: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Video Bus: xkb_layout: "us"
(II) config/hal: Adding input device SynPS/2 Synaptics TouchPad
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.99.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) Synaptics touchpad driver version 0.99.3
(**) Option "Device" "/dev/input/event8"
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
(II) SynPS/2 Synaptics TouchPad: buttons: left right middle double triple
(--) SynPS/2 Synaptics TouchPad touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) filter chain progression: 2.00
(**) SynPS/2 Synaptics TouchPad: (accel) filter stage 0: 20.00 ms
(**) SynPS/2 Synaptics TouchPad: (accel) set acceleration profile 0
(--) SynPS/2 Synaptics TouchPad touchpad found

```

Here are the relevant sections from /etc/X11/xorg.conf 

```
Section "Screen"
	Identifier	"Screen0"
	Device		"Videocard0"
	Monitor		"Monitor0"
	Option		"TwinView"	"1"
	Option		"TwinViewXineramaInfoOrder"	"CRT-0"
	Option		"metamodes"	"CRT: nvidia-auto-select +0+0, DFP: nvidia-auto-select +0+0"
	Option		"AddARGBGLXVisuals"	"True"
	DefaultDepth	24
	Option 		"AllowGLXWithComposite" "True
	SubSection "Display"
	Depth	24
	EndSubSection
EndSection

Section "Device"
	Identifier	"Videocard0"
	Vendorname	"NVIDIA Corporation"
	Boardname	"GeForce Go 6150"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
	Option	"RenderAccel" "true"
	Option	"UseEvents" "false"
	Option	"TripleBuffer" "1"
	Option	"DamageEvents" "1"
	Option	"DisableGLXRootClipping" "true"
        Option         "OnDemandVBlankInterrupts" "true"
EndSection
```

I have tried adding a few options I found here:

[http://techbase.kde.org/User:Lemma/KDE4-NVIDIA](http://techbase.kde.org/User:Lemma/KDE4-NVIDIA)
[http://www.nvnews.net/vbulletin/showpost.php?p=1704073&postcount=1](http://www.nvnews.net/vbulletin/showpost.php?p=1704073&postcount=1) (and links therein)

but with no noticeable changes.

---

### Post by Neo40 on 2009-08-07
Hello,

I have this issue too with Jaunty (and LinuxMint 7). I have the same machine like you. I tried everything and finally found no real solution. This is why I switched back to Ubuntu 8.04. 

If you fix your problem, let me know!

---

### Post by thenanodude on 2009-08-09
I have not yet found the source of the problem, but I found that, by changing some settings in VLC, movies are at least watchable.  Here is what I did:

1. Go to Tools -> Preferences
2. Click the "All" button under "Show settings"
3. Under "Video -> General video settings" the following are enabled:
 Enable video
 Embedded video
 Drop late frames
 Skip frames
 Overly video output
 Disable screensaver
 
4. Under "Video: Output modules":
 Select XVideo extenstion video
  (may also be able to use X11)

5. Under "Video: Output modules: XVideo:
 Disable "Use shared memory"
  (If using X11 instead of XVideo, disable "Use shared memory" in the X11 options)

I've been playing around with settings in MPlayer as well, but I haven't found a great combination.  Setting the video output to "X11" seems to work best, but note that you need to include the line zoom="1" in ~/.mplayer/config to be able to use fullscreen mode.  

If anybody knows better settings for VLC or MPlayer, please let me know!

---

### Post by devoncabdb on 2011-01-12
> **thenanodude said:**
> I recently upgraded from Hardy to Jaunty and have discovered than all my DVDs play slowly is both Totem and VLC. After searching this and other forums for 2 days without finding a solution, I have decided to start a new thread. Here are some of my specs:Desktop: xfceComputer: HP Pavilion dv2000Video: nvidia Geforce 6150 GoProcessor: AMD turion 64dvd+rw-tools version: 7.1-4libdvdcss2 version: 1.2.10-0.2medibuntu1libdvdnav4 version: 4.1.3-3libdvdread3 version: 0.9.7-11ubuntu2libdvdread4 version: 4.1.3-4ubuntu2vlc version: 0.9.9a-2ubuntu1libvlc2 version: 0.9.9a-2ubuntu1libvlccore0 version: 0.9.9a-2ubuntu1totem version: 2.26.1-0ubuntu5totem-gstreamer version: 2.26.1-0ubuntu5In VLC I set my [[COLOR=#000000]video[/COLOR]](http://www.****************.com/mov-video-format/convert-avi-video-to-mov-format.html) output to X11, as suggested in some posts (although flickering is not the problem): [http://ubuntuforums.org/showthread.php?t=974321](http://ubuntuforums.org/showthread.php?t=974321) This seemed to help slightly, but not completely.One potentially related problem: when I insert a DVD I get the following errors indicating problems with mounting the device. However, the DVD does indeed mount, so it just seems something is trying to mount it twice.[code]I have looked at the system monitor while the video is playing back, and typically less than 25% of both processors and the memory is being used, so it is clearly not a resource issue.Any help is appreciated. Thanks!I got more deep understanding about this part, Many thanks to your description!

---

