---
title: "ubuntu 10.10 (64-bit) booting problem"
date: 2010-11-02
forum: General Help
---

### Post by newstargate on 2010-11-02
hello 
i am having this problem since long time and couldnt find any working solution for it

i have dual boot system
windows 7 (64-bit)
ubuntu 10.10 (64-bit)

boot manager: grub2

video card ATI radeon 4800 (updated driver from internet) and still getting the problem (so i dont think it is graphics problem)

problem:
sometimes when i boot ubuntu the blinking courser stays for ever and sometimes booting works like charm (every 3 tries i got one working boot)

i erased the quiet splash from the booting options to see what is going on

here is a screen shot where it stuck
[screenshot]("http://www.iimmgg.com/image/2f12f89a6216e97d382e009a8e307b2c")

i tried the "nomodest" option ..didnt work ..

the problem i cant shutdown i only use the sleep option 
coz a shutdown might put me in a new luck game again :(
plz any idea?

---

### Post by oldfred on 2010-11-02
The same info on screen (your screen shot) is in your System, Administration, Log File Viewer.

After having a slow boot you need to look at your log file and see where the time has a large gap. It saves the previous boot, so see if same gap is there or not. Some gaps are just the time it takes to load whatever process it is loading.

I just noticed on my system that takes about  60 sec to boot that it is seeing an issue on a partition. I must be mounting in fstab without the auto filecheck every 30 boots but now it is starting to have issues and takes about 30 sec extra.

From messages:

```
Nov  1 00:02:40 fred-LucidDT kernel: [   35.120838] EXT2-fs warning: mounting unchecked fs, running e2fsck is recommended
Nov  1 00:03:06 fred-LucidDT kernel: [   61.438632] __ratelimit: 12 callbacks suppressed

```oldfred goes off to run e2fsck on the extra partitions he mounts.:)

---

### Post by newstargate on 2010-11-02
> **oldfred said:**
> The same info on screen (your screen shot) is in your System, Administration, Log File Viewer.

After having a slow boot you need to look at your log file and see where the time has a large gap. It saves the previous boot, so see if same gap is there or not. Some gaps are just the time it takes to load whatever process it is loading.

I just noticed on my system that takes about  60 sec to boot that it is seeing an issue on a partition. I must be mounting in fstab without the auto filecheck every 30 boots but now it is starting to have issues and takes about 30 sec extra.

From messages:

```
Nov  1 00:02:40 fred-LucidDT kernel: [   35.120838] EXT2-fs warning: mounting unchecked fs, running e2fsck is recommended
Nov  1 00:03:06 fred-LucidDT kernel: [   61.438632] __ratelimit: 12 callbacks suppressed

```oldfred goes off to run e2fsck on the extra partitions he mounts.:)

the problem is i am not having a slow boot ..sometime it just wont boot at all and freezes all the time , and sometimes it boots fast successfully

---

### Post by oldfred on 2010-11-02
The log will have the previous boot or two and you should be able to find what it is hanging up on.

Is it different from a cold boot vs. a warm boot? We have seen several users with that issue, but do not have a good answer.

---

### Post by newstargate on 2010-11-02
here are two Xorg.log files 

the unsuccessful boot log file 
```


[    14.310] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    14.310] X Protocol Version 11, Revision 0
[    14.310] Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
[    14.310] Current Operating System: Linux zix-ubuntu 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:45:36 UTC 2010 x86_64
[    14.310] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=7fd351d3-a366-436c-aae9-3617758d8f94 ro
[    14.310] Build Date: 16 September 2010  06:18:41PM
[    14.310] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
[    14.310] Current version of pixman: 0.18.4
[    14.310]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    14.310] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    14.310] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Nov  3 01:13:34 2010
[    14.310] (==) Using config file: "/etc/X11/xorg.conf"
[    14.310] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    14.310] (==) No Layout section.  Using the first Screen section.
[    14.310] (**) |-->Screen "Default Screen" (0)
[    14.310] (**) |   |-->Monitor "<default monitor>"
[    14.310] (==) No device specified for screen "Default Screen".
    Using the first device section listed.
[    14.310] (**) |   |-->Device "Default Device"
[    14.310] (==) No monitor specified for screen "Default Screen".
    Using a default monitor configuration.
[    14.310] (==) Automatically adding devices
[    14.310] (==) Automatically enabling devices
[    14.310] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    14.310]     Entry deleted from font path.
[    14.310] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    14.310] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    14.310] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    14.310] (II) Loader magic: 0x7d0200
[    14.310] (II) Module ABI versions:
[    14.310]     X.Org ANSI C Emulation: 0.4
[    14.310]     X.Org Video Driver: 8.0
[    14.310]     X.Org XInput driver : 11.0
[    14.310]     X.Org Server Extension : 4.0
[    14.311] (--) PCI:*(0:1:0:0) 1002:9442:1462:1530 rev 0, Mem @ 0xd0000000/268435456, 0xfbce0000/65536, I/O @ 0x0000c000/256, BIOS @ 0x????????/131072
[    14.311] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    14.311] (II) "extmod" will be loaded by default.
[    14.311] (II) "dbe" will be loaded by default.
[    14.311] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    14.311] (II) "record" will be loaded by default.
[    14.311] (II) "dri" will be loaded by default.
[    14.311] (II) "dri2" will be loaded by default.
[    14.311] (II) LoadModule: "glx"
[    14.311] (II) Loading /usr/lib/xorg/extra-modules/modules/extensions/libglx.so
[    14.311] (II) Module glx: vendor="FireGL - ATI Technologies Inc."
[    14.311]     compiled for 7.6.0, module version = 1.0.0
[    14.311] (II) Loading extension GLX
[    14.311] (II) LoadModule: "extmod"
[    14.318] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    14.318] (II) Module extmod: vendor="X.Org Foundation"
[    14.318]     compiled for 1.9.0, module version = 1.0.0
[    14.318]     Module class: X.Org Server Extension
[    14.318]     ABI class: X.Org Server Extension, version 4.0
[    14.318] (II) Loading extension MIT-SCREEN-SAVER
[    14.318] (II) Loading extension XFree86-VidModeExtension
[    14.318] (II) Loading extension XFree86-DGA
[    14.318] (II) Loading extension DPMS
[    14.318] (II) Loading extension XVideo
[    14.318] (II) Loading extension XVideo-MotionCompensation
[    14.318] (II) Loading extension X-Resource
[    14.318] (II) LoadModule: "dbe"
[    14.318] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    14.318] (II) Module dbe: vendor="X.Org Foundation"
[    14.318]     compiled for 1.9.0, module version = 1.0.0
[    14.318]     Module class: X.Org Server Extension
[    14.318]     ABI class: X.Org Server Extension, version 4.0
[    14.318] (II) Loading extension DOUBLE-BUFFER
[    14.318] (II) LoadModule: "record"
[    14.319] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    14.319] (II) Module record: vendor="X.Org Foundation"
[    14.319]     compiled for 1.9.0, module version = 1.13.0
[    14.319]     Module class: X.Org Server Extension
[    14.319]     ABI class: X.Org Server Extension, version 4.0
[    14.319] (II) Loading extension RECORD
[    14.319] (II) LoadModule: "dri"
[    14.319] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    14.319] (II) Module dri: vendor="X.Org Foundation"
[    14.319]     compiled for 1.9.0, module version = 1.0.0
[    14.319]     ABI class: X.Org Server Extension, version 4.0
[    14.319] (II) Loading extension XFree86-DRI
[    14.319] (II) LoadModule: "dri2"
[    14.319] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    14.319] (II) Module dri2: vendor="X.Org Foundation"
[    14.319]     compiled for 1.9.0, module version = 1.2.0
[    14.319]     ABI class: X.Org Server Extension, version 4.0
[    14.319] (II) Loading extension DRI2
[    14.319] (II) LoadModule: "fglrx"
[    14.319] (II) Loading /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so
[    14.329] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[    14.329]     compiled for 1.4.99.906, module version = 8.78.30
[    14.329]     Module class: X.Org Video Driver
[    14.329] (II) Loading sub module "fglrxdrm"
[    14.329] (II) LoadModule: "fglrxdrm"
[    14.329] (II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    14.329] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    14.329]     compiled for 1.8.99.905, module version = 8.78.30
[    14.329] (II) ATI Proprietary Linux Driver Version Identifier:8.78.30
[    14.329] (II) ATI Proprietary Linux Driver Release Identifier: 8.78.3                               
[    14.329] (II) ATI Proprietary Linux Driver Build Date: Sep 20 2010 21:31:08
[    14.329] (++) using VT number 7

[    14.330] (WW) Falling back to old probe method for fglrx
[    14.333] (II) Loading PCS database from /etc/ati/amdpcsdb
[    14.333] (--) Assigning device section with no busID to primary device
[    14.333] (--) Chipset Supported AMD Graphics Processor (0x9442) found
[    14.333] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
[    14.333] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[    14.333] (II) AMD Video driver is signed
[    14.333] (II) fglrx(0): pEnt->device->identifier=0x1d6a2b0
[    14.333] (II) fglrx(0): === [xdl_x760_atiddxPreInit] === begin
[    14.334] (II) Loading sub module "vgahw"
[    14.334] (II) LoadModule: "vgahw"
[    14.334] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    14.334] (II) Module vgahw: vendor="X.Org Foundation"
[    14.334]     compiled for 1.9.0, module version = 0.1.0
[    14.334]     ABI class: X.Org Video Driver, version 8.0
[    14.334] (II) fglrx(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
[    14.334] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[    14.334] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    14.334] (==) fglrx(0): Default visual is TrueColor
[    14.334] (==) fglrx(0): RGB weight 888
[    14.334] (II) fglrx(0): Using 8 bits per RGB 
[    14.334] (==) fglrx(0): Buffer Tiling is ON
[    14.334] (II) Loading sub module "fglrxdrm"
[    14.334] (II) LoadModule: "fglrxdrm"
[    14.334] (II) Reloading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    14.335] ukiDynamicMajor: found major device number 250
[    14.335] ukiDynamicMajor: found major device number 250
[    14.335] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    14.335] ukiOpenDevice: node name is /dev/ati/card0
[    14.335] ukiOpenDevice: open result is 10, (OK)
[    14.335] ukiOpenByBusid: ukiOpenMinor returns 10
[    14.335] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    14.335] (==) fglrx(0): NoAccel = NO
[    14.335] (==) fglrx(0): ATI 2D Acceleration Architecture enabled
[    14.335] (--) fglrx(0): Chipset: "ATI Radeon HD 4800 Series" (Chipset = 0x9442)
[    14.335] (--) fglrx(0): (PciSubVendor = 0x1462, PciSubDevice = 0x1530)
[    14.335] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
[    14.335] (--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
[    14.335] (--) fglrx(0): MMIO registers at 0xfbce0000
[    14.335] (--) fglrx(0): I/O port at 0x0000c000
[    14.335] (==) fglrx(0): ROM-BIOS at 0x000c0000
[    14.336] (II) fglrx(0): AC Adapter is used
[    14.338] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
[    14.432] (II) Loading sub module "vbe"
[    14.432] (II) LoadModule: "vbe"
[    14.432] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    14.432] (II) Module vbe: vendor="X.Org Foundation"
[    14.432]     compiled for 1.9.0, module version = 1.1.0
[    14.432]     ABI class: X.Org Video Driver, version 8.0
[    14.432] (II) fglrx(0): VESA BIOS detected
[    14.432] (II) fglrx(0): VESA VBE Version 3.0
[    14.432] (II) fglrx(0): VESA VBE Total Mem: 16384 kB
[    14.432] (II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
[    14.432] (II) fglrx(0): VESA VBE OEM Software Rev: 11.10
[    14.432] (II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
[    14.432] (II) fglrx(0): VESA VBE OEM Product: RV770
[    14.432] (II) fglrx(0): VESA VBE OEM Product Rev: 01.00
[    14.466] (II) fglrx(0): ATI Video BIOS revision 9 or later detected
[    14.466] (--) fglrx(0): Video RAM: 1048576 kByte, Type: GDDR3
[    14.466] (II) fglrx(0): PCIE card detected
[    14.466] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[    14.466] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[    14.467] (II) fglrx(0): Using adapter: 1:0.0.
[    14.495] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x40000000)
[    14.561] (II) fglrx(0): Interrupt handler installed at IRQ 54.
[    14.561] (II) fglrx(0): RandR 1.2 support is enabled!
[    14.561] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[    14.561] (==) fglrx(0): Center Mode is disabled 
[    14.561] (II) Loading sub module "fb"
[    14.561] (II) LoadModule: "fb"
[    14.561] (II) Loading /usr/lib/xorg/modules/libfb.so
[    14.561] (II) Module fb: vendor="X.Org Foundation"
[    14.561]     compiled for 1.9.0, module version = 1.0.0
[    14.561]     ABI class: X.Org ANSI C Emulation, version 0.4
[    14.561] (==) fglrx(0): Active stereo disabled
[    14.561] (II) Loading sub module "ddc"
[    14.561] (II) LoadModule: "ddc"
[    14.561] (II) Module "ddc" already built-in
[    15.862] (II) fglrx(0): Finished Initialize PPLIB!
[    15.864] (II) fglrx(0): Output DFP1 has no monitor section
[    15.864] (II) fglrx(0): Output DFP2 has no monitor section
[    15.864] (II) fglrx(0): Output CRT1 has no monitor section
[    15.864] (II) fglrx(0): Output CRT2 has no monitor section
[    15.864] (II) fglrx(0): Output TV has no monitor section
[    15.864] (II) fglrx(0): Output CV has no monitor section
[    15.864] (II) Loading sub module "ddc"
[    15.864] (II) LoadModule: "ddc"
[    15.864] (II) Module "ddc" already built-in
[    15.864] (II) fglrx(0): Connected Display0: CRT1
[    15.864] (II) fglrx(0): Display0 EDID data ---------------------------
[    15.864] (II) fglrx(0): Manufacturer: SAM  Model: 523  Serial#: 1280455218
[    15.864] (II) fglrx(0): Year: 2010  Week: 3
[    15.864] (II) fglrx(0): EDID Version: 1.3
[    15.864] (II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[    15.864] (II) fglrx(0): Sync:  Separate  Composite  SyncOnGreen
[    15.864] (II) fglrx(0): Max Image Size [cm]: horiz.: 48  vert.: 27
[    15.864] (II) fglrx(0): Gamma: 2.20
[    15.864] (II) fglrx(0): DPMS capabilities: Off; RGB/Color Display
[    15.864] (II) fglrx(0): First detailed timing is preferred mode
[    15.864] (II) fglrx(0): redX: 0.648 redY: 0.339   greenX: 0.282 greenY: 0.603
[    15.864] (II) fglrx(0): blueX: 0.143 blueY: 0.070   whiteX: 0.312 whiteY: 0.329
[    15.864] (II) fglrx(0): Supported established timings:
[    15.864] (II) fglrx(0): 640x480@60Hz
[    15.864] (II) fglrx(0): 800x600@56Hz
[    15.864] (II) fglrx(0): 800x600@60Hz
[    15.864] (II) fglrx(0): 1024x768@60Hz
[    15.864] (II) fglrx(0): Manufacturer's mask: 0
[    15.864] (II) fglrx(0): Supported standard timings:
[    15.864] (II) fglrx(0): #0: hsize: 1280  vsize 800  refresh: 60  vid: 129
[    15.864] (II) fglrx(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    15.864] (II) fglrx(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    15.864] (II) fglrx(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    15.864] (II) fglrx(0): #4: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
[    15.864] (II) fglrx(0): #5: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    15.864] (II) fglrx(0): Supported detailed timing:
[    15.864] (II) fglrx(0): clock: 148.5 MHz   Image Size:  477 x 268 mm
[    15.864] (II) fglrx(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    15.864] (II) fglrx(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    15.864] (II) fglrx(0): Ranges: V min: 56 V max: 60 Hz, H min: 30 H max: 81 kHz, PixClock max 175 MHz
[    15.864] (II) fglrx(0): Monitor name: SyncMaster
[    15.864] (II) fglrx(0): Serial No: HVCZ117558
[    15.864] (II) fglrx(0): EDID (in hex):
[    15.864] (II) fglrx(0):     00ffffffffffff004c2d23053232524c
[    15.864] (II) fglrx(0):     031401030e301b782a3581a656489a24
[    15.864] (II) fglrx(0):     1250542308008100814081809500a940
[    15.864] (II) fglrx(0):     b30001010101023a801871382d40582c
[    15.864] (II) fglrx(0):     4500dd0c1100001e000000fd00383c1e
[    15.864] (II) fglrx(0):     5111000a202020202020000000fc0053
[    15.864] (II) fglrx(0):     796e634d61737465720a2020000000ff
[    15.864] (II) fglrx(0):     004856435a3131373535380a202000a8
[    15.864] (II) fglrx(0): End of Display0 EDID data --------------------
[    15.984] (II) fglrx(0): Output DFP1 disconnected
[    15.984] (II) fglrx(0): Output DFP2 disconnected
[    15.984] (II) fglrx(0): Output CRT1 connected
[    15.984] (II) fglrx(0): Output CRT2 disconnected
[    15.984] (II) fglrx(0): Output TV disconnected
[    15.984] (II) fglrx(0): Output CV disconnected
[    15.984] (II) fglrx(0): Using exact sizes for initial modes
[    15.984] (II) fglrx(0): Output CRT1 using initial mode 1920x1080
[    15.984] (II) fglrx(0): DPI set to (96, 96)
[    15.984] (II) fglrx(0): Adapter ATI Radeon HD 4800 Series has 2 configurable heads and 1 displays connected.
[    15.984] (==) fglrx(0):  PseudoColor visuals disabled
[    15.984] (II) Loading sub module "ramdac"
[    15.984] (II) LoadModule: "ramdac"
[    15.984] (II) Module "ramdac" already built-in
[    15.984] (==) fglrx(0): NoDRI = NO
[    15.984] (==) fglrx(0): Capabilities: 0x00000000
[    15.984] (==) fglrx(0): CapabilitiesEx: 0x00000000
[    15.984] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[    15.984] (==) fglrx(0): UseFastTLS=0
[    15.984] (==) fglrx(0): BlockSignalsOnLock=1
[    15.984] (--) Depth 24 pixmap format is 32 bpp
[    15.984] (II) Loading extension ATIFGLRXDRI
[    15.984] (II) fglrx(0): doing swlDriScreenInit
[    15.984] (II) fglrx(0): swlDriScreenInit for fglrx driver
[    15.984] ukiDynamicMajor: found major device number 250
[    15.984] ukiDynamicMajor: found major device number 250
[    15.984] ukiDynamicMajor: found major device number 250
[    15.984] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    15.984] ukiOpenDevice: node name is /dev/ati/card0
[    15.984] ukiOpenDevice: open result is 15, (OK)
[    15.984] ukiOpenByBusid: ukiOpenMinor returns 15
[    15.984] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    15.984] (II) fglrx(0): [uki] DRM interface version 1.0
[    15.984] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:1:0:0"
[    15.984] (II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
[    15.984] (II) fglrx(0): [uki] mapped SAREA 0x2000 to 0x7f4d9a6f8000
[    15.984] (II) fglrx(0): [uki] framebuffer handle = 0x3000
[    15.984] (II) fglrx(0): [uki] added 1 reserved context for kernel
[    15.984] (II) fglrx(0): swlDriScreenInit done
[    15.984] (II) fglrx(0): Kernel Module Version Information:
[    15.984] (II) fglrx(0):     Name: fglrx
[    15.984] (II) fglrx(0):     Version: 8.78.30
[    15.984] (II) fglrx(0):     Date: Sep 20 2010
[    15.984] (II) fglrx(0):     Desc: ATI FireGL DRM kernel module
[    15.984] (II) fglrx(0): Kernel Module version matches driver.
[    15.984] (II) fglrx(0): Kernel Module Build Time Information:
[    15.984] (II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.35-22-generic
[    15.984] (II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
[    15.984] (II) fglrx(0):     Build-Kernel __SMP__:            yes
[    15.984] (II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
[    15.984] (II) fglrx(0): [uki] register handle = 0x00004000
[    16.000] (II) fglrx(0): DRI initialization successfull
[    16.000] (II) fglrx(0): FBADPhys: 0xf00000000 FBMappedSize: 0x01068000
[    16.000] (II) fglrx(0): FBMM initialized for area (0,0)-(1920,2240)
[    16.000] (II) fglrx(0): FBMM auto alloc for area (0,0)-(1920,1920) (front color buffer - assumption)
[    16.000] (II) fglrx(0): Largest offscreen area available: 1920 x 320
[    16.000] (==) fglrx(0): Backing store disabled
[    16.000] (II) Loading extension FGLRXEXTENSION
[    16.000] (==) fglrx(0): DPMS enabled
[    16.000] (II) fglrx(0): Initialized in-driver Xinerama extension
[    16.001] (**) fglrx(0): Textured Video is enabled.
[    16.001] (II) LoadModule: "glesx"
[    16.001] (II) Loading /usr/lib/xorg/extra-modules/modules/glesx.so
[    16.001] (II) Module glesx: vendor="X.Org Foundation"
[    16.001]     compiled for 1.8.99.905, module version = 1.0.0
[    16.001] (II) Loading extension GLESX
[    16.001] (II) fglrx(0): GLESX enableFlags = 528
[    16.001] (II) fglrx(0): GLESX is enabled
[    16.001] (II) fglrx(0): Acceleration enabled
[    16.001] (II) LoadModule: "amdxmm"
[    16.001] (II) Loading /usr/lib/xorg/extra-modules/modules/amdxmm.so
[    16.001] (II) Module amdxmm: vendor="X.Org Foundation"
[    16.001]     compiled for 1.8.99.905, module version = 1.0.0
[    16.001] (II) Loading extension AMDXVOPL
[    16.002] (II) fglrx(0): UVD2 feature is available
[    16.003] (II) fglrx(0): Enable composite support successfully
[    16.003] (II) fglrx(0): X context handle = 0x1
[    16.003] (II) fglrx(0): [DRI] installation complete
[    16.003] (==) fglrx(0): Silken mouse enabled
[    16.003] (==) fglrx(0): Using HW cursor of display infrastructure!
[    16.003] (II) fglrx(0): Disabling in-server RandR and enabling in-driver RandR 1.2.
[    16.004] (II) fglrx(0): Cannot get TV Format. Set all TV geometry value to zero!
[    16.004] (II) fglrx(0): Cannot get TV Format for trying to adjust horizontal position after horizontal size changed. 
[    16.168] (--) RandR disabled
[    16.168] (II) Initializing built-in extension Generic Event Extension
[    16.168] (II) Initializing built-in extension SHAPE
[    16.168] (II) Initializing built-in extension MIT-SHM
[    16.168] (II) Initializing built-in extension XInputExtension
[    16.168] (II) Initializing built-in extension XTEST
[    16.168] (II) Initializing built-in extension BIG-REQUESTS
[    16.168] (II) Initializing built-in extension SYNC
[    16.168] (II) Initializing built-in extension XKEYBOARD
[    16.168] (II) Initializing built-in extension XC-MISC
[    16.168] (II) Initializing built-in extension SECURITY
[    16.168] (II) Initializing built-in extension XINERAMA
[    16.168] (II) Initializing built-in extension XFIXES
[    16.168] (II) Initializing built-in extension RENDER
[    16.168] (II) Initializing built-in extension RANDR
[    16.168] (II) Initializing built-in extension COMPOSITE
[    16.168] (II) Initializing built-in extension DAMAGE
[    16.168] (II) Initializing built-in extension GESTURE
[    16.177] ukiDynamicMajor: found major device number 250
[    16.177] ukiDynamicMajor: found major device number 250
[    16.177] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    16.177] ukiOpenDevice: node name is /dev/ati/card0
[    16.177] ukiOpenDevice: open result is 16, (OK)
[    16.177] ukiOpenByBusid: ukiOpenMinor returns 16
[    16.177] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    16.216] (II) AIGLX: Loaded and initialized /usr/lib64/dri/fglrx_dri.so
[    16.216] (II) GLX: Initialized DRI GL provider for screen 0
[    16.216] (II) fglrx(0): Enable the clock gating!
[    16.216] (II) fglrx(0): Setting screen physical size to 508 x 285
[    16.226] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    16.230] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    16.230] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    16.230] (II) LoadModule: "evdev"
[    16.231] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.231] (II) Module evdev: vendor="X.Org Foundation"
[    16.231]     compiled for 1.9.0, module version = 2.3.2
[    16.231]     Module class: X.Org XInput Driver
[    16.231]     ABI class: X.Org XInput driver, version 11.0
[    16.231] (**) Power Button: always reports core events
[    16.231] (**) Power Button: Device: "/dev/input/event1"
[    16.310] (II) Power Button: Found keys
[    16.310] (II) Power Button: Configuring as keyboard
[    16.310] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    16.310] (**) Option "xkb_rules" "evdev"
[    16.310] (**) Option "xkb_model" "pc105"
[    16.310] (**) Option "xkb_layout" "us"
[    16.311] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    16.311] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    16.311] (**) Power Button: always reports core events
[    16.311] (**) Power Button: Device: "/dev/input/event0"
[    16.381] (II) Power Button: Found keys
[    16.381] (II) Power Button: Configuring as keyboard
[    16.381] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    16.381] (**) Option "xkb_rules" "evdev"
[    16.381] (**) Option "xkb_model" "pc105"
[    16.381] (**) Option "xkb_layout" "us"
[    16.383] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event2)
[    16.383] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    16.383] (**) Logitech USB Receiver: always reports core events
[    16.383] (**) Logitech USB Receiver: Device: "/dev/input/event2"
[    16.461] (II) Logitech USB Receiver: Found keys
[    16.461] (II) Logitech USB Receiver: Configuring as keyboard
[    16.461] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    16.461] (**) Option "xkb_rules" "evdev"
[    16.461] (**) Option "xkb_model" "pc105"
[    16.461] (**) Option "xkb_layout" "us"
[    16.461] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event3)
[    16.461] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[    16.461] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    16.461] (**) Logitech USB Receiver: always reports core events
[    16.461] (**) Logitech USB Receiver: Device: "/dev/input/event3"
[    16.540] (II) Logitech USB Receiver: Found 12 mouse buttons
[    16.540] (II) Logitech USB Receiver: Found scroll wheel(s)
[    16.540] (II) Logitech USB Receiver: Found relative axes
[    16.540] (II) Logitech USB Receiver: Found x and y relative axes
[    16.540] (II) Logitech USB Receiver: Found absolute axes
[    16.540] (II) evdev-grail: failed to open grail, no gesture support
[    16.540] (II) Logitech USB Receiver: Found keys
[    16.540] (II) Logitech USB Receiver: Configuring as mouse
[    16.540] (II) Logitech USB Receiver: Configuring as keyboard
[    16.540] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    16.540] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    16.540] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    16.540] (**) Option "xkb_rules" "evdev"
[    16.540] (**) Option "xkb_model" "pc105"
[    16.540] (**) Option "xkb_layout" "us"
[    16.540] (II) Logitech USB Receiver: initialized for relative axes.
[    16.540] (WW) Logitech USB Receiver: ignoring absolute axes.
[    16.540] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse0)
[    16.540] (II) No input driver/identifier specified (ignoring)
[    16.551] (II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
[    17.288] (II) fglrx(0): EDID vendor "SAM", prod id 1315
[    17.288] (II) fglrx(0): Using EDID range info for horizontal sync
[    17.288] (II) fglrx(0): Using EDID range info for vertical refresh
[    17.288] (II) fglrx(0): Printing DDC gathered Modelines:
[    17.288] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    17.288] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    17.288] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    17.288] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    17.288] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    17.288] (II) fglrx(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
[    17.288] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    17.288] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    17.288] (II) fglrx(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    17.288] (II) fglrx(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    17.288] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    17.438] (WW) fglrx(0): Cannot get updated TV attributes.
[    17.747] (II) fglrx(0): EDID vendor "SAM", prod id 1315
[    17.747] (II) fglrx(0): Using hsync ranges from config file
[    17.747] (II) fglrx(0): Using vrefresh ranges from config file
[    17.747] (II) fglrx(0): Printing DDC gathered Modelines:
[    17.747] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    17.747] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    17.747] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    17.747] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    17.747] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    17.747] (II) fglrx(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
[    17.747] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    17.747] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    17.747] (II) fglrx(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    17.747] (II) fglrx(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    17.747] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    17.898] (WW) fglrx(0): Cannot get updated TV attributes.
[    18.206] (II) fglrx(0): EDID vendor "SAM", prod id 1315
[    18.206] (II) fglrx(0): Using hsync ranges from config file
[    18.207] (II) fglrx(0): Using vrefresh ranges from config file
[    18.207] (II) fglrx(0): Printing DDC gathered Modelines:
[    18.207] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    18.207] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    18.207] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    18.207] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    18.207] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    18.207] (II) fglrx(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
[    18.207] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    18.207] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    18.207] (II) fglrx(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    18.207] (II) fglrx(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    18.207] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    18.356] (WW) fglrx(0): Cannot get updated TV attributes.
[    18.661] (II) fglrx(0): EDID vendor "SAM", prod id 1315
[    18.661] (II) fglrx(0): Using hsync ranges from config file
[    18.661] (II) fglrx(0): Using vrefresh ranges from config file
[    18.661] (II) fglrx(0): Printing DDC gathered Modelines:
[    18.661] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    18.661] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    18.661] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    18.661] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    18.661] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    18.661] (II) fglrx(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
[    18.661] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    18.661] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    18.661] (II) fglrx(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    18.661] (II) fglrx(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    18.661] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    18.810] (WW) fglrx(0): Cannot get updated TV attributes.
[    19.462] (II) fglrx(0): EDID vendor "SAM", prod id 1315
[    19.462] (II) fglrx(0): Using hsync ranges from config file
[    19.462] (II) fglrx(0): Using vrefresh ranges from config file
[    19.462] (II) fglrx(0): Printing DDC gathered Modelines:
[    19.462] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    19.462] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    19.462] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    19.462] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    19.462] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    19.462] (II) fglrx(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
[    19.462] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    19.462] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    19.462] (II) fglrx(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    19.462] (II) fglrx(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    19.462] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    24.411] (II) fglrx(0): EDID vendor "SAM", prod id 1315
[    24.411] (II) fglrx(0): Using hsync ranges from config file
[    24.411] (II) fglrx(0): Using vrefresh ranges from config file
[    24.411] (II) fglrx(0): Printing DDC gathered Modelines:
[    24.411] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    24.411] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    24.411] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    24.411] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    24.411] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    24.411] (II) fglrx(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
[    24.411] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    24.411] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    24.411] (II) fglrx(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    24.411] (II) fglrx(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    24.411] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    24.583] (WW) fglrx(0): Cannot get updated TV attributes.

```



the successful boot log file

```
[  9588.853] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[  9588.853] X Protocol Version 11, Revision 0
[  9588.853] Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
[  9588.853] Current Operating System: Linux zix-ubuntu 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:32:27 UTC 2010 x86_64
[  9588.853] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=7fd351d3-a366-436c-aae9-3617758d8f94 ro quiet splash
[  9588.853] Build Date: 16 September 2010  06:18:41PM
[  9588.853] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
[  9588.853] Current version of pixman: 0.18.4
[  9588.853]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[  9588.853] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  9588.854] (==) Log file: "/var/log/Xorg.1.log", Time: Wed Oct 27 20:43:43 2010
[  9588.854] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  9588.879] (==) No Layout section.  Using the first Screen section.
[  9588.879] (==) No screen section available. Using defaults.
[  9588.879] (**) |-->Screen "Default Screen Section" (0)
[  9588.879] (**) |   |-->Monitor "<default monitor>"
[  9588.879] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[  9588.879] (==) Automatically adding devices
[  9588.879] (==) Automatically enabling devices
[  9588.879] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  9588.879]     Entry deleted from font path.
[  9588.879] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[  9588.879] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  9588.879] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[  9588.879] (II) Loader magic: 0x7d0200
[  9588.879] (II) Module ABI versions:
[  9588.879]     X.Org ANSI C Emulation: 0.4
[  9588.879]     X.Org Video Driver: 8.0
[  9588.879]     X.Org XInput driver : 11.0
[  9588.879]     X.Org Server Extension : 4.0
[  9588.880] (--) PCI:*(0:1:0:0) 1002:9442:1462:1530 rev 0, Mem @ 0xd0000000/268435456, 0xfbce0000/65536, I/O @ 0x0000c000/256, BIOS @ 0x????????/131072
[  9588.881] (II) Open ACPI successful (/var/run/acpid.socket)
[  9588.881] (II) LoadModule: "extmod"
[  9588.881] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[  9588.886] (II) Module extmod: vendor="X.Org Foundation"
[  9588.886]     compiled for 1.9.0, module version = 1.0.0
[  9588.886]     Module class: X.Org Server Extension
[  9588.886]     ABI class: X.Org Server Extension, version 4.0
[  9588.886] (II) Loading extension MIT-SCREEN-SAVER
[  9588.886] (II) Loading extension XFree86-VidModeExtension
[  9588.886] (II) Loading extension XFree86-DGA
[  9588.886] (II) Loading extension DPMS
[  9588.886] (II) Loading extension XVideo
[  9588.886] (II) Loading extension XVideo-MotionCompensation
[  9588.886] (II) Loading extension X-Resource
[  9588.886] (II) LoadModule: "dbe"
[  9588.886] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[  9588.896] (II) Module dbe: vendor="X.Org Foundation"
[  9588.896]     compiled for 1.9.0, module version = 1.0.0
[  9588.896]     Module class: X.Org Server Extension
[  9588.896]     ABI class: X.Org Server Extension, version 4.0
[  9588.896] (II) Loading extension DOUBLE-BUFFER
[  9588.896] (II) LoadModule: "glx"
[  9588.896] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[  9588.897] (II) Module glx: vendor="X.Org Foundation"
[  9588.897]     compiled for 1.9.0, module version = 1.0.0
[  9588.897]     ABI class: X.Org Server Extension, version 4.0
[  9588.897] (==) AIGLX enabled
[  9588.897] (II) Loading extension GLX
[  9588.897] (II) LoadModule: "record"
[  9588.898] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[  9588.898] (II) Module record: vendor="X.Org Foundation"
[  9588.898]     compiled for 1.9.0, module version = 1.13.0
[  9588.898]     Module class: X.Org Server Extension
[  9588.898]     ABI class: X.Org Server Extension, version 4.0
[  9588.898] (II) Loading extension RECORD
[  9588.898] (II) LoadModule: "dri"
[  9588.899] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[  9588.899] (II) Module dri: vendor="X.Org Foundation"
[  9588.899]     compiled for 1.9.0, module version = 1.0.0
[  9588.899]     ABI class: X.Org Server Extension, version 4.0
[  9588.899] (II) Loading extension XFree86-DRI
[  9588.899] (II) LoadModule: "dri2"
[  9588.900] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[  9588.900] (II) Module dri2: vendor="X.Org Foundation"
[  9588.900]     compiled for 1.9.0, module version = 1.2.0
[  9588.900]     ABI class: X.Org Server Extension, version 4.0
[  9588.900] (II) Loading extension DRI2
[  9588.900] (==) Matched ati as autoconfigured driver 0
[  9588.900] (==) Matched vesa as autoconfigured driver 1
[  9588.900] (==) Matched fbdev as autoconfigured driver 2
[  9588.900] (==) Assigned the driver to the xf86ConfigLayout
[  9588.900] (II) LoadModule: "ati"
[  9588.900] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[  9588.907] (II) Module ati: vendor="X.Org Foundation"
[  9588.907]     compiled for 1.9.0, module version = 6.13.1
[  9588.907]     Module class: X.Org Video Driver
[  9588.907]     ABI class: X.Org Video Driver, version 8.0
[  9588.907] (II) LoadModule: "radeon"
[  9588.908] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[  9588.915] (II) Module radeon: vendor="X.Org Foundation"
[  9588.915]     compiled for 1.9.0, module version = 6.13.1
[  9588.915]     Module class: X.Org Video Driver
[  9588.915]     ABI class: X.Org Video Driver, version 8.0
[  9588.915] (II) LoadModule: "vesa"
[  9588.915] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  9588.919] (II) Module vesa: vendor="X.Org Foundation"
[  9588.919]     compiled for 1.8.99.905, module version = 2.3.0
[  9588.919]     Module class: X.Org Video Driver
[  9588.919]     ABI class: X.Org Video Driver, version 8.0
[  9588.919] (II) LoadModule: "fbdev"
[  9588.919] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  9588.926] (II) Module fbdev: vendor="X.Org Foundation"
[  9588.926]     compiled for 1.8.99.905, module version = 0.4.2
[  9588.926]     ABI class: X.Org Video Driver, version 8.0
[  9588.926] (II) RADEON: Driver for ATI Radeon chipsets:
    ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
    ATI Radeon Mobility X300 (M24) 3152 (PCIE),
    ATI FireGL M24 GL 3154 (PCIE), ATI FireMV 2400 3155 (PCI),
    ATI Radeon X600 (RV380) 3E50 (PCIE),
    ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
    ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
    ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
    ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
    ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
    ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
    ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
    ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
    ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
    ATI Radeon 8500 AIW BB (AGP), ATI Radeon 8500 AIW BC (AGP),
    ATI Radeon IGP320M (U1) 4336, ATI Radeon IGP330M/340M/350M (U2) 4337,
    ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
    ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
    ATI Radeon X800PRO (R420) JI (AGP),
    ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
    ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
    ATI Radeon Mobility 9800 (M18) JN (AGP),
    ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
    ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
    ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
    ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
    ATI Radeon Mobility M7 LW (AGP),
    ATI Mobility FireGL 7800 M7 LX (AGP),
    ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
    ATI FireGL Mobility 9000 (M9) Ld (AGP),
    ATI Radeon Mobility 9000 (M9) Lf (AGP),
    ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
    ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
    ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
    ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
    ATI Radeon 9800XT NJ (AGP),
    ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
    ATI Radeon Mobility 9600 (M10) NQ (AGP),
    ATI Radeon Mobility 9600 (M11) NR (AGP),
    ATI Radeon Mobility 9600 (M10) NS (AGP),
    ATI FireGL Mobility T2 (M10) NT (AGP),
    ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
    ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
    ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
    ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
    ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
    ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
    ATI Radeon Mobility X300 (M22) 5460 (PCIE),
    ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
    ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
    ATI Radeon X800PRO (R423) UI (PCIE),
    ATI Radeon X800LE (R423) UJ (PCIE),
    ATI Radeon X800SE (R423) UK (PCIE),
    ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
    ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
    ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
    ATI FireGL unknown (R423) UR (PCIE),
    ATI FireGL unknown (R423) UT (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility Radeon X700 XL (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
    ATI Radeon Mobility 9100 IGP (U3) 5835,
    ATI Radeon XPRESS 200 5954 (PCIE),
    ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
    ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
    ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
    ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
    ATI Radeon XPRESS 200M 5975 (PCIE),
    ATI Radeon XPRESS 200 5A41 (PCIE),
    ATI Radeon XPRESS 200M 5A42 (PCIE),
    ATI Radeon XPRESS 200 5A61 (PCIE),
    ATI Radeon XPRESS 200M 5A62 (PCIE),
    ATI Radeon X300 (RV370) 5B60 (PCIE),
    ATI Radeon X600 (RV370) 5B62 (PCIE),
    ATI Radeon X550 (RV370) 5B63 (PCIE),
    ATI FireGL V3100 (RV370) 5B64 (PCIE),
    ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
    ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
    ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
    ATI Mobility Radeon X800 XT (M28) (PCIE),
    ATI Mobility FireGL V5100 (M28) (PCIE),
    ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
    ATI Radeon X850 XT PE (R480) (PCIE),
    ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
    ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
    ATI Radeon X850 XT (R480) (PCIE),
    ATI Radeon X800XT (R423) 5D57 (PCIE),
    ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
    ATI Radeon X700 PRO (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
    ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
    ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
    ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
    ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
    ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
    ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
    ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
    ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
    ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
    ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
    ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
    ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
    ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
    ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
    ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
    ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
    ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
    ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
    ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
    ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
    ATI Mobility Radeon X1700, ATI Radeon X2300HD,
    ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
    ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
    ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
    ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
    ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
    ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
    ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
    ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
    ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
    ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
    ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
    ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
    ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
    ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
    ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
    ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
    AMD FireStream 9250, ATI FirePro V8700 (FireGL),
    ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
    ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
    ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
    ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
    ATI Mobility Radeon HD 4670, ATI FirePro M5750,
    ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
    ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
    ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
    ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
    ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
    ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
    ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
    ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
    ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
    ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
    ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
    ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
    ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
    ATI Mobility Radeon HD 3850 X2, ATI RV670,
    ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
    ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
    ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
    ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
    ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
    ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
    ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
    ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
    ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
    ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
    ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
    ATI FireGL V3600, ATI Radeon HD 2600 LE,
    ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
    ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
    ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
    ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
    ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
    ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
    ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
    ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
    ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
    ATI Radeon 3000 Graphics, ATI Radeon HD 4200, ATI Radeon 4100,
    ATI Mobility Radeon HD 4200, ATI Mobility Radeon 4100,
    ATI Radeon HD 4290, ATI Radeon HD 4290, CYPRESS,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5900 Series, ATI Radeon HD 5900 Series,
    ATI Mobility Radeon HD 5800 Series,
    ATI Mobility Radeon HD 5800 Series,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 5700 Series,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
    ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, CEDAR, CEDAR, CEDAR,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, CEDAR, ATI Radeon HD 5450,
    CEDAR
[  9588.932] (II) VESA: driver for VESA chipsets: vesa
[  9588.932] (II) FBDEV: driver for framebuffer: fbdev
[  9588.932] (--) using VT number 8

[  9589.565] (II) [KMS] Kernel modesetting enabled.
[  9589.565] (WW) Falling back to old probe method for vesa
[  9589.565] (WW) Falling back to old probe method for fbdev
[  9589.565] (II) Loading sub module "fbdevhw"
[  9589.565] (II) LoadModule: "fbdevhw"
[  9589.565] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[  9589.572] (II) Module fbdevhw: vendor="X.Org Foundation"
[  9589.572]     compiled for 1.9.0, module version = 0.0.2
[  9589.572]     ABI class: X.Org Video Driver, version 8.0
[  9589.572] (II) RADEON(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[  9589.572] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[  9589.572] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[  9589.572] (==) RADEON(0): Default visual is TrueColor
[  9589.572] (==) RADEON(0): RGB weight 888
[  9589.572] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[  9589.572] (--) RADEON(0): Chipset: "ATI Radeon 4800 Series" (ChipID = 0x9442)
[  9589.573] (II) RADEON(0): PCIE card detected
[  9589.573] (WW) RADEON(0): Color tiling is not yet supported on R600/R700
[  9589.573] (II) RADEON(0): KMS Color Tiling: disabled
[  9589.573] drmOpenDevice: node name is /dev/dri/card0
[  9589.573] drmOpenDevice: open result is 9, (OK)
[  9589.573] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[  9589.573] drmOpenDevice: node name is /dev/dri/card0
[  9589.573] drmOpenDevice: open result is 9, (OK)
[  9589.573] drmOpenByBusid: drmOpenMinor returns 9
[  9589.573] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[  9589.591] (II) RADEON(0): Output DVI-0 has no monitor section
[  9589.611] (II) RADEON(0): Output DIN has no monitor section
[  9589.667] (II) RADEON(0): Output DVI-1 has no monitor section
[  9589.682] (II) RADEON(0): EDID for output DVI-0
[  9589.702] (II) RADEON(0): EDID for output DIN
[  9589.757] (II) RADEON(0): EDID for output DVI-1
[  9589.757] (II) RADEON(0): Manufacturer: SAM  Model: 523  Serial#: 1280455218
[  9589.757] (II) RADEON(0): Year: 2010  Week: 3
[  9589.757] (II) RADEON(0): EDID Version: 1.3
[  9589.757] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[  9589.757] (II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
[  9589.757] (II) RADEON(0): Max Image Size [cm]: horiz.: 48  vert.: 27
[  9589.757] (II) RADEON(0): Gamma: 2.20
[  9589.757] (II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
[  9589.757] (II) RADEON(0): First detailed timing is preferred mode
[  9589.757] (II) RADEON(0): redX: 0.648 redY: 0.339   greenX: 0.282 greenY: 0.603
[  9589.757] (II) RADEON(0): blueX: 0.143 blueY: 0.070   whiteX: 0.312 whiteY: 0.329
[  9589.757] (II) RADEON(0): Supported established timings:
[  9589.757] (II) RADEON(0): 640x480@60Hz
[  9589.757] (II) RADEON(0): 800x600@56Hz
[  9589.757] (II) RADEON(0): 800x600@60Hz
[  9589.757] (II) RADEON(0): 1024x768@60Hz
[  9589.757] (II) RADEON(0): Manufacturer's mask: 0
[  9589.757] (II) RADEON(0): Supported standard timings:
[  9589.757] (II) RADEON(0): #0: hsize: 1280  vsize 800  refresh: 60  vid: 129
[  9589.757] (II) RADEON(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[  9589.757] (II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[  9589.757] (II) RADEON(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
[  9589.757] (II) RADEON(0): #4: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
[  9589.757] (II) RADEON(0): #5: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[  9589.757] (II) RADEON(0): Supported detailed timing:
[  9589.757] (II) RADEON(0): clock: 148.5 MHz   Image Size:  477 x 268 mm
[  9589.757] (II) RADEON(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[  9589.757] (II) RADEON(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[  9589.757] (II) RADEON(0): Ranges: V min: 56 V max: 60 Hz, H min: 30 H max: 81 kHz, PixClock max 175 MHz
[  9589.757] (II) RADEON(0): Monitor name: SyncMaster
[  9589.757] (II) RADEON(0): Serial No: HVCZ117558
[  9589.757] (II) RADEON(0): EDID (in hex):
[  9589.757] (II) RADEON(0):     00ffffffffffff004c2d23053232524c
[  9589.757] (II) RADEON(0):     031401030e301b782a3581a656489a24
[  9589.757] (II) RADEON(0):     1250542308008100814081809500a940
[  9589.757] (II) RADEON(0):     b30001010101023a801871382d40582c
[  9589.757] (II) RADEON(0):     4500dd0c1100001e000000fd00383c1e
[  9589.757] (II) RADEON(0):     5111000a202020202020000000fc0053
[  9589.757] (II) RADEON(0):     796e634d61737465720a2020000000ff
[  9589.757] (II) RADEON(0):     004856435a3131373535380a202000a8
[  9589.757] (II) RADEON(0): Printing probed modes for output DVI-1
[  9589.757] (II) RADEON(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[  9589.757] (II) RADEON(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[  9589.757] (II) RADEON(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[  9589.757] (II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  9589.757] (II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[  9589.757] (II) RADEON(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[  9589.757] (II) RADEON(0): Modeline "1280x800"x59.8   83.50  1280 1352 1480 1680  800 803 809 831 +hsync -vsync (49.7 kHz)
[  9589.757] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  9589.757] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  9589.757] (II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[  9589.757] (II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  9589.757] (II) RADEON(0): Output DVI-0 disconnected
[  9589.757] (II) RADEON(0): Output DIN disconnected
[  9589.757] (II) RADEON(0): Output DVI-1 connected
[  9589.757] (II) RADEON(0): Using exact sizes for initial modes
[  9589.757] (II) RADEON(0): Output DVI-1 using initial mode 1920x1080
[  9589.757] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[  9589.757] (II) RADEON(0): mem size init: gart size :1fdff000 vram size: s:40000000 visible:3f7d7000
[  9589.757] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[  9589.757] (==) RADEON(0): DPI set to (96, 96)
[  9589.757] (II) Loading sub module "fb"
[  9589.757] (II) LoadModule: "fb"
[  9589.757] (II) Loading /usr/lib/xorg/modules/libfb.so
[  9589.776] (II) Module fb: vendor="X.Org Foundation"
[  9589.776]     compiled for 1.9.0, module version = 1.0.0
[  9589.776]     ABI class: X.Org ANSI C Emulation, version 0.4
[  9589.776] (II) Loading sub module "ramdac"
[  9589.776] (II) LoadModule: "ramdac"
[  9589.776] (II) Module "ramdac" already built-in
[  9589.776] (II) Loading sub module "exa"
[  9589.776] (II) LoadModule: "exa"
[  9589.777] (II) Loading /usr/lib/xorg/modules/libexa.so
[  9589.777] (II) Module exa: vendor="X.Org Foundation"
[  9589.777]     compiled for 1.9.0, module version = 2.5.0
[  9589.777]     ABI class: X.Org Video Driver, version 8.0
[  9589.777] (II) UnloadModule: "vesa"
[  9589.777] (II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  9589.777] (II) UnloadModule: "fbdev"
[  9589.777] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  9589.777] (II) UnloadModule: "fbdevhw"
[  9589.777] (II) Unloading /usr/lib/xorg/modules/libfbdevhw.so
[  9589.777] (--) Depth 24 pixmap format is 32 bpp
[  9589.777] (II) RADEON(0): [DRI2] Setup complete
[  9589.777] (II) RADEON(0): [DRI2]   DRI driver: r600
[  9589.777] (II) RADEON(0): Front buffer size: 8704K
[  9589.777] (II) RADEON(0): VRAM usage limit set to 928364K
[  9589.777] (==) RADEON(0): Backing store disabled
[  9589.777] (II) RADEON(0): Direct rendering enabled
[  9589.777] (II) RADEON(0): Setting EXA maxPitchBytes
[  9589.778] (II) EXA(0): Driver allocated offscreen pixmaps
[  9589.778] (II) EXA(0): Driver registered support for the following operations:
[  9589.778] (II)         Solid
[  9589.778] (II)         Copy
[  9589.778] (II)         Composite (RENDER acceleration)
[  9589.778] (II)         UploadToScreen
[  9589.778] (II)         DownloadFromScreen
[  9589.778] (II) RADEON(0): Acceleration enabled
[  9589.778] (==) RADEON(0): DPMS enabled
[  9589.778] (==) RADEON(0): Silken mouse enabled
[  9589.778] (II) RADEON(0): Set up textured video
[  9589.778] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[  9589.778] (--) RandR disabled
[  9589.778] (II) Initializing built-in extension Generic Event Extension
[  9589.778] (II) Initializing built-in extension SHAPE
[  9589.778] (II) Initializing built-in extension MIT-SHM
[  9589.778] (II) Initializing built-in extension XInputExtension
[  9589.778] (II) Initializing built-in extension XTEST
[  9589.778] (II) Initializing built-in extension BIG-REQUESTS
[  9589.778] (II) Initializing built-in extension SYNC
[  9589.778] (II) Initializing built-in extension XKEYBOARD
[  9589.778] (II) Initializing built-in extension XC-MISC
[  9589.778] (II) Initializing built-in extension SECURITY
[  9589.778] (II) Initializing built-in extension XINERAMA
[  9589.778] (II) Initializing built-in extension XFIXES
[  9589.778] (II) Initializing built-in extension RENDER
[  9589.778] (II) Initializing built-in extension RANDR
[  9589.778] (II) Initializing built-in extension COMPOSITE
[  9589.778] (II) Initializing built-in extension DAMAGE
[  9589.778] (II) Initializing built-in extension GESTURE
[  9589.785] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[  9589.785] (II) AIGLX: enabled GLX_INTEL_swap_event
[  9589.785] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[  9589.785] (II) AIGLX: enabled GLX_SGI_make_current_read
[  9589.785] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[  9589.785] (II) AIGLX: Loaded and initialized /usr/lib/dri/r600_dri.so
[  9589.785] (II) GLX: Initialized DRI2 GL provider for screen 0
[  9589.786] (II) RADEON(0): Setting screen physical size to 508 x 285
[  9589.847] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  9589.854] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[  9589.854] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  9589.854] (II) LoadModule: "evdev"
[  9589.854] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  9589.876] (II) Module evdev: vendor="X.Org Foundation"
[  9589.876]     compiled for 1.9.0, module version = 2.3.2
[  9589.876]     Module class: X.Org XInput Driver
[  9589.876]     ABI class: X.Org XInput driver, version 11.0
[  9589.876] (**) Power Button: always reports core events
[  9589.876] (**) Power Button: Device: "/dev/input/event1"
[  9589.931] (II) Power Button: Found keys
[  9589.931] (II) Power Button: Configuring as keyboard
[  9589.931] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[  9589.931] (**) Option "xkb_rules" "evdev"
[  9589.931] (**) Option "xkb_model" "pc105"
[  9589.931] (**) Option "xkb_layout" "us"
[  9589.934] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[  9589.934] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  9589.934] (**) Power Button: always reports core events
[  9589.934] (**) Power Button: Device: "/dev/input/event0"
[  9590.051] (II) Power Button: Found keys
[  9590.051] (II) Power Button: Configuring as keyboard
[  9590.051] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[  9590.051] (**) Option "xkb_rules" "evdev"
[  9590.051] (**) Option "xkb_model" "pc105"
[  9590.051] (**) Option "xkb_layout" "us"
[  9590.056] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event2)
[  9590.056] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[  9590.056] (**) Logitech USB Receiver: always reports core events
[  9590.056] (**) Logitech USB Receiver: Device: "/dev/input/event2"
[  9590.201] (II) Logitech USB Receiver: Found keys
[  9590.201] (II) Logitech USB Receiver: Configuring as keyboard
[  9590.201] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[  9590.201] (**) Option "xkb_rules" "evdev"
[  9590.201] (**) Option "xkb_model" "pc105"
[  9590.201] (**) Option "xkb_layout" "us"
[  9590.202] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event3)
[  9590.202] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[  9590.202] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[  9590.202] (**) Logitech USB Receiver: always reports core events
[  9590.202] (**) Logitech USB Receiver: Device: "/dev/input/event3"
[  9590.280] (II) Logitech USB Receiver: Found 12 mouse buttons
[  9590.280] (II) Logitech USB Receiver: Found scroll wheel(s)
[  9590.280] (II) Logitech USB Receiver: Found relative axes
[  9590.280] (II) Logitech USB Receiver: Found x and y relative axes
[  9590.280] (II) Logitech USB Receiver: Found absolute axes
[  9590.280] (II) evdev-grail: failed to open grail, no gesture support
[  9590.280] (II) Logitech USB Receiver: Found keys
[  9590.280] (II) Logitech USB Receiver: Configuring as mouse
[  9590.280] (II) Logitech USB Receiver: Configuring as keyboard
[  9590.280] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[  9590.280] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  9590.280] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[  9590.280] (**) Option "xkb_rules" "evdev"
[  9590.280] (**) Option "xkb_model" "pc105"
[  9590.280] (**) Option "xkb_layout" "us"
[  9590.281] (II) Logitech USB Receiver: initialized for relative axes.
[  9590.281] (WW) Logitech USB Receiver: ignoring absolute axes.
[  9590.281] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse0)
[  9590.281] (II) No input driver/identifier specified (ignoring)
[  9590.787] (II) RADEON(0): EDID vendor "SAM", prod id 1315
[  9590.787] (II) RADEON(0): Using EDID range info for horizontal sync
[  9590.787] (II) RADEON(0): Using EDID range info for vertical refresh
[  9590.787] (II) RADEON(0): Printing DDC gathered Modelines:
[  9590.787] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[  9590.787] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  9590.787] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[  9590.787] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  9590.787] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  9590.787] (II) RADEON(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
[  9590.787] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[  9590.787] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  9590.787] (II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[  9590.787] (II) RADEON(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[  9590.787] (II) RADEON(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[  9590.906] (II) RADEON(0): EDID vendor "SAM", prod id 1315
[  9590.906] (II) RADEON(0): Using hsync ranges from config file
[  9590.906] (II) RADEON(0): Using vrefresh ranges from config file
[  9590.906] (II) RADEON(0): Printing DDC gathered Modelines:
[  9590.906] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[  9590.906] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  9590.906] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[  9590.906] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  9590.906] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  9590.906] (II) RADEON(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
[  9590.906] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[  9590.906] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  9590.906] (II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[  9590.906] (II) RADEON(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[  9590.906] (II) RADEON(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[  9591.006] (II) RADEON(0): EDID vendor "SAM", prod id 1315
[  9591.006] (II) RADEON(0): Using hsync ranges from config file
[  9591.006] (II) RADEON(0): Using vrefresh ranges from config file
[  9591.006] (II) RADEON(0): Printing DDC gathered Modelines:
[  9591.006] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[  9591.006] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  9591.006] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[  9591.006] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  9591.006] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  9591.006] (II) RADEON(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
[  9591.006] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[  9591.006] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  9591.006] (II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[  9591.006] (II) RADEON(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[  9591.006] (II) RADEON(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[  9591.096] (II) RADEON(0): EDID vendor "SAM", prod id 1315
[  9591.096] (II) RADEON(0): Using hsync ranges from config file
[  9591.096] (II) RADEON(0): Using vrefresh ranges from config file
[  9591.096] (II) RADEON(0): Printing DDC gathered Modelines:
[  9591.096] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[  9591.096] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  9591.096] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[  9591.096] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  9591.096] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  9591.096] (II) RADEON(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
[  9591.096] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[  9591.096] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  9591.096] (II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[  9591.096] (II) RADEON(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[  9591.096] (II) RADEON(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[ 10542.276] (II) RADEON(0): EDID vendor "SAM", prod id 1315
[ 10542.276] (II) RADEON(0): Using hsync ranges from config file
[ 10542.276] (II) RADEON(0): Using vrefresh ranges from config file
[ 10542.276] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10542.276] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[ 10542.276] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[ 10542.276] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[ 10542.276] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[ 10542.276] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[ 10542.276] (II) RADEON(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
[ 10542.276] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[ 10542.276] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[ 10542.276] (II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[ 10542.276] (II) RADEON(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[ 10542.276] (II) RADEON(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[ 16110.680] (II) AIGLX: Suspending AIGLX clients for VT switch
[ 22976.155] (II) Logitech USB Receiver: Close
[ 22976.214] (II) UnloadModule: "evdev"
[ 22976.214] (II) Logitech USB Receiver: Close
[ 22976.214] (II) UnloadModule: "evdev"
[ 22976.214] (II) Power Button: Close
[ 22976.214] (II) UnloadModule: "evdev"
[ 22976.214] (II) Power Button: Close
[ 22976.214] (II) UnloadModule: "evdev"
[ 22976.215]  ddxSigGiveUp: Closing log

```


please review it and tell me if there is something i can do

---

### Post by oldfred on 2010-11-02
One thing about computer is that they always are consistent, not.

They look like two different systems with different xorg files.

I do not know enough about ATI to really be able to help.

---

### Post by newstargate on 2010-11-02
> **oldfred said:**
> One thing about computer is that they always are consistent, not.

They look like two different systems with different xorg files.

I do not know enough about ATI to really be able to help.

:'(

---

### Post by newstargate on 2010-11-03
plz guys help me..

my friend suggested to go and try fedora ..but i liked this distro so much ..i dont want to remove it :((((

---

### Post by oldfred on 2010-11-03
Some others with Radeon and a few suggestions but it seems to be a problem.

[http://ubuntuforums.org/showthread.php?t=1611022](http://ubuntuforums.org/showthread.php?t=1611022)

---

### Post by newstargate on 2010-11-03
> **oldfred said:**
> Some others with Radeon and a few suggestions but it seems to be a problem.

[http://ubuntuforums.org/showthread.php?t=1611022](http://ubuntuforums.org/showthread.php?t=1611022)

all these people have persistent problem -they cant boot at all ..
i dont think they have the same situation
and i think i wont get help ..this problem seems unsolvable ...
so i will just go back to windows :(

---

