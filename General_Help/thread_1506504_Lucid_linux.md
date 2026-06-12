---
title: "Lucid linux"
date: 2010-06-10
forum: General Help
---

### Post by marcoftheknight on 2010-06-10
I still have theses weird horizontal lines that go up the screen EXTREMELY annoying I think my hardware might be messed lets hope it a setting. If anyone has experience this problem please let me know what you did to fix it thanks





Senario: recently installed 2 hard drives and two fans booted nicely with ubuntu.

Before and after I had been having a warning in grub boot saying ALSA HDA -intel driver to many inputs. But everything was launching correctly. Recently though the sound stopped working and my Next boot was a complete failure. tried rebooting a few time changed some settings in the Bios but still nothing. This boot problem also was just after a recent update that failed because one of the repositories couldnt be accessed. basicaly a hole bunch of things gone wrong!

When I press Ctrl-alt F1 nothing happens same with alt F1 it seems I can't get to the terminal. Any Idead 

Basicaly 1 of my monitors ( Ati card with dual monitors) is purple with ubunt and 5 dots light up red as if it's done loading but nothing happen after that weird.

should I go to the Bios and tweak or what else can I do?

Thanks

---

### Post by dino99 on 2010-06-10
boot line : remove splash, add nomodeset

---

### Post by marcoftheknight on 2010-06-10
Everyday I hate ATI more and more it's called open source or I change video cards and never look back.


Thanks DIne your four words helped in the right direction didnt realize you can hold shift when booting up and I ended up being able to boot in low graphics mode bur I have no idea why this happened. Seems like this is a graphics problem?

Heres my boot.log

fsck from util-linux-ng 2.17.2 
udevd[424]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /lib/udev/rules.d/40-alsa-firmware-loaders.rules:9 
  
udevd[424]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /lib/udev/rules.d/40-alsa-firmware-loaders.rules:9 
  
udevd[424]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /lib/udev/rules.d/40-alsa-firmware-loaders.rules:10 
  
udevd[424]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /lib/udev/rules.d/40-alsa-firmware-loaders.rules:10 
  
udevd[424]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /lib/udev/rules.d/40-alsa-firmware-loaders.rules:12 
  
udevd[424]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /lib/udev/rules.d/40-alsa-firmware-loaders.rules:12 
  
udevd[424]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /lib/udev/rules.d/40-alsa-firmware-loaders.rules:13 
  
udevd[424]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /lib/udev/rules.d/40-alsa-firmware-loaders.rules:13 
  
udevd[424]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /lib/udev/rules.d/40-alsa-firmware-loaders.rules:15 
  
udevd[424]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /lib/udev/rules.d/40-alsa-firmware-loaders.rules:15 
  
udevd[424]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /lib/udev/rules.d/40-alsa-firmware-loaders.rules:16 
  
udevd[424]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /lib/udev/rules.d/40-alsa-firmware-loaders.rules:16 
  
/dev/sda1: clean, 208142/29786112 files, 3605497/119125504 blocks

Heres my xorg log file:



X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux marcoftheknight-desktop 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=dff7596d-b7d4-41cd-ad98-3333a7eedfc2 ro single
Build Date: 09 June 2010  11:00:55AM
xorg-server 2:1.7.6-2ubuntu7.1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.16.4
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Jun 10 20:24:58 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "aticonfig Layout"
(**) |-->Screen "aticonfig-Screen[0]-0" (0)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "aticonfig-Device[0]-0"
(==) No monitor specified for screen "aticonfig-Screen[0]-0".
    Using a default monitor configuration.
(**) |-->Screen "amdcccle-Screen[1]-1" (1)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "amdcccle-Device[1]-1"
(==) No monitor specified for screen "amdcccle-Screen[1]-1".
    Using a default monitor configuration.
(**) Option "Xinerama" "off"
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
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(--) using VT number 7

(--) PCI:*(0:1:0:0) 1002:68b8:1682:2990 ATI Technologies Inc Juniper [Radeon HD 5700 Series] rev 0, Mem @ 0xd0000000/268435456, 0xfdec0000/131072, I/O @ 0x0000ee00/256, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
    compiled for 1.7.1, module version = 8.73.3
    Module class: X.Org Video Driver
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux/libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
    compiled for 1.7.1, module version = 8.73.3
(II) ATI Proprietary Linux Driver Version Identifier:8.73.3
(II) ATI Proprietary Linux Driver Release Identifier: 8.732                                
(II) ATI Proprietary Linux Driver Build Date: May  4 2010 21:16:34
(II) Primary Device is: PCI 01@00:00:0
(WW) Falling back to old probe method for fglrx
(II) Loading PCS database from /etc/ati/amdpcsdb
(--) Chipset Supported AMD Graphics Processor (0x68B8) found
(--) Chipset Supported AMD Graphics Processor (0x68B8) found
[U](WW) fglrx: No matching Device section for instance (BusID PCI:0@0:17:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:1) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:3) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:4) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:5) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:21:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:22:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:22:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
(II) AMD Video driver is running on a device belonging to a group targeted for [/U]this release
(II) AMD Video driver is signed
(II) fglrx(0): pEnt->device->identifier=0x2255830
(II) fglrx(1): pEnt->device->identifier=0x2255830
(II) fglrx(0): === [atiddxPreInit] === begin
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.1.0
    ABI class: X.Org Video Driver, version 6.0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB 
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux/libfglrxdrm.so
ukiDynamicMajor: found major device number 250
ukiDynamicMajor: found major device number 250
ukiOpenByBusid: Searching for BusID PCI:1:0:0
ukiOpenDevice: node name is /dev/ati/card0
ukiOpenDevice: open result is 12, (OK)
ukiOpenByBusid: ukiOpenMinor returns 12
ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
(==) fglrx(0): NoAccel = NO
(--) fglrx(0): Chipset: "ATI Radeon HD 5700 Series" (Chipset = 0x68b8)
(--) fglrx(0): (PciSubVendor = 0x1682, PciSubDevice = 0x2990)
(==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
(--) fglrx(0): MMIO registers at 0xfdec0000
(--) fglrx(0): I/O port at 0x0000ee00
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) fglrx(0): AC Adapter is used
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Video Driver, version 6.0
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 12.13
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: -113-C01301-007
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
(--) fglrx(0): Video RAM: 1048576 kByte, Type: GDDR5
(II) fglrx(0): PCIE card detected
(--) fglrx(0): Using per-process page tables (PPPT) as GART.
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) fglrx(0): Using adapter: 1:0.0.
(II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x40000000)
(II) fglrx(0): Interrupt handler installed at IRQ 31.
(II) fglrx(0): RandR 1.2 support is enabled!
(II) fglrx(0): RandR 1.2 rotation support is enabled!
(==) fglrx(0): Center Mode is disabled 
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) fglrx(0): Finished Initialize PPLIB!
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) fglrx(0): Connected Display0: CRT on primary DAC [crt1]
(II) fglrx(0): Display0 EDID data ---------------------------
(II) fglrx(0): Manufacturer: PHL  Model: c032  Serial#: 4932
(II) fglrx(0): Year: 2009  Week: 36
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) fglrx(0): Sync:  Separate  Composite  SyncOnGreen
(II) fglrx(0): Max Image Size [cm]: horiz.: 41  vert.: 23
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: Off; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.647 redY: 0.334   greenX: 0.284 greenY: 0.607
(II) fglrx(0): blueX: 0.151 blueY: 0.071   whiteX: 0.312 whiteY: 0.329
(II) fglrx(0): Supported established timings:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@67Hz
(II) fglrx(0): 640x480@72Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@56Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@72Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 832x624@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@70Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): 1152x864@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported standard timings:
(II) fglrx(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) fglrx(0): #1: hsize: 1280  vsize 720  refresh: 75  vid: 53121
(II) fglrx(0): Supported detailed timing:
(II) fglrx(0): clock: 85.5 MHz   Image Size:  413 x 234 mm
(II) fglrx(0): h_active: 1366  h_sync: 1436  h_sync_end 1579 h_blank_end 1792 h_border: 0
(II) fglrx(0): v_active: 768  v_sync: 771  v_sync_end 774 v_blanking: 798 v_border: 0
(II) fglrx(0): Serial No: AU40936004932
(II) fglrx(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 83 kHz, PixClock max 170 MHz
(II) fglrx(0): Monitor name: Philips 192E
(II) fglrx(0): EDID (in hex):
(II) fglrx(0):     00ffffffffffff00410c32c044130000
(II) fglrx(0):     241301036e2917782aeed1a555489b26
(II) fglrx(0):     125054bfef80714f81cf010101010101
(II) fglrx(0):     010101010101662156aa51001e30468f
(II) fglrx(0):     33009dea1000001e000000ff00415534
(II) fglrx(0):     30393336303034393332000000fd0038
(II) fglrx(0):     4c1e5311000a202020202020000000fc
(II) fglrx(0):     005068696c69707320313932450a00c6
(II) fglrx(0): End of Display0 EDID data --------------------
(II) fglrx(0): Output DFP1 has no monitor section
(II) fglrx(0): Output DFP2 using monitor section 0-DFP2
(**) fglrx(0): Option "PreferredMode" "1920x1080"
(**) fglrx(0): Option "Position" "0 0"
(**) fglrx(0): Option "Disable" "false"
(**) fglrx(0): Option "Rotate" "normal"
(**) fglrx(0): Option "TargetRefresh" "30"
(II) fglrx(0): Output DFP3 has no monitor section
(II) fglrx(0): Output DFP4 has no monitor section
(II) fglrx(0): Output CRT1 has no monitor section
(II) fglrx(0): Output CRT2 has no monitor section
(II) fglrx(0): Output DFP1 disconnected
(II) fglrx(0): Output DFP2 disconnected
(II) fglrx(0): Output DFP3 disconnected
(II) fglrx(0): Output DFP4 disconnected
(II) fglrx(0): Output CRT1 connected
(II) fglrx(0): Output CRT2 disconnected
(II) fglrx(0): Using user preference for initial modes
(II) fglrx(0): Output CRT1 using initial mode 1366x768
(II) fglrx(0): DPI set to (96, 96)
(II) fglrx(0): Adapter ATI Radeon HD 5700 Series has 2 configurable heads and 1 displays connected.
(==) fglrx(0): QBS disabled
(==) fglrx(0):  PseudoColor visuals disabled
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(==) fglrx(0): NoDRI = NO
(**) fglrx(0): Capabilities: 0x00000800
(**) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(II) fglrx(1): === [atiddxPreInit] === begin
(WW) fglrx(1): Quitting screen 1 -- no monitor specified.
(II) fglrx(1): === [atiddxPreInit] === end
(II) UnloadModule: "fglrx"
(II) UnloadModule: "fglrxdrm"
(--) Depth 24 pixmap format is 32 bpp
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing swlDriScreenInit
(II) fglrx(0): swlDriScreenInit for fglrx driver
ukiDynamicMajor: found major device number 250
ukiDynamicMajor: found major device number 250
ukiDynamicMajor: found major device number 250
ukiOpenByBusid: Searching for BusID PCI:1:0:0
ukiOpenDevice: node name is /dev/ati/card0
ukiOpenDevice: open result is 17, (OK)
ukiOpenByBusid: ukiOpenMinor returns 17
ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
(II) fglrx(0): [uki] DRM interface version 1.0
(II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
(II) fglrx(0): [uki] mapped SAREA 0x2000 to 0x7f1d0ad41000
(II) fglrx(0): [uki] framebuffer handle = 0x3000
(II) fglrx(0): [uki] added 1 reserved context for kernel
(II) fglrx(0): swlDriScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.73.3
(II) fglrx(0):     Date: May  4 2010
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.32-22-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
(II) fglrx(0):     Build-Kernel __SMP__:            yes
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [uki] register handle = 0x00004000
(II) fglrx(0): Display width adjusted to to 1664 due to alignment constraints
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xf00000000 FBMappedSize: 0x01110000

BOttom half og the debug log:

ream=0x5, channel=4, format=0x4015
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.380211] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x9
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.380295] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x9
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.380412] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x9
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.380576] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x9
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.380862] ALSA hda_intel.c:1642: azx_pcm_prepare: bufsize=0x3700, format=0x4011
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.380870] ALSA hda_codec.c:1157: hda_codec_setup_stream: NID=0x9, stream=0x1, channel=0, format=0x4011
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.400065] ALSA hda_intel.c:1642: azx_pcm_prepare: bufsize=0x3700, format=0x4011
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.400073] ALSA hda_codec.c:1157: hda_codec_setup_stream: NID=0x9, stream=0x1, channel=0, format=0x4011
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.420041] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x9
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.420056] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x9
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.420419] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x2
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.420422] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x3
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.420424] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x4
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.420439] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x2
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.420442] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x3
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.420444] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x4
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.420634] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x2
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.420637] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x3
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.420639] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x4
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.420805] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x2
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.420807] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x3
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.420810] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x4
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.421034] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x2
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.421037] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x3
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.421039] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x4
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.421320] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x2
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.421323] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x3
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.421325] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x4
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.421488] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x2
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.421491] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x3
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.421493] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x4
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.421654] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x2
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.421657] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x3
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.421659] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x4
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.421877] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x2
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.421880] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x3
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.421882] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x4
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.422162] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x2
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.422165] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x3
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.422167] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x4
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.422330] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x2
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.422332] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x3
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.422335] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x4
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.422493] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x2
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.422496] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x3
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.422498] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x4
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.422717] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x2
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.422720] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x3
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.422722] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x4
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.422999] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x2
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.423002] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x3
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.423004] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x4
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.423168] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x2
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.423170] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x3
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.423173] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x4
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.423331] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x2
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.423334] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x3
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.423336] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x4
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.423555] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x2
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.423557] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x3
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.423560] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x4
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.423836] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x2
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.423838] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x3
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.423841] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x4
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.424002] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x2
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.424005] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x3
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.424007] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x4
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.424166] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x2
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.424169] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x3
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.424171] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x4
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.424394] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x2
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.424396] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x3
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.424398] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x4
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.424677] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x2
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.424679] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x3
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.424681] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x4
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.424973] ALSA hda_intel.c:1642: azx_pcm_prepare: bufsize=0x3700, format=0x4011
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.424998] ALSA hda_codec.c:1157: hda_codec_setup_stream: NID=0x6, stream=0x8, channel=0, format=0x4011
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.440063] ALSA hda_intel.c:1642: azx_pcm_prepare: bufsize=0x3700, format=0x4011
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.440072] ALSA hda_codec.c:1157: hda_codec_setup_stream: NID=0x6, stream=0x8, channel=0, format=0x4011
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.460164] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x9
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.460245] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x9
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.460356] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x9
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.460517] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x9
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.460775] ALSA hda_intel.c:1642: azx_pcm_prepare: bufsize=0x3700, format=0x4011
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.460782] ALSA hda_codec.c:1157: hda_codec_setup_stream: NID=0x9, stream=0x1, channel=0, format=0x4011
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.480058] ALSA hda_intel.c:1642: azx_pcm_prepare: bufsize=0x3700, format=0x4011
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.480065] ALSA hda_codec.c:1157: hda_codec_setup_stream: NID=0x9, stream=0x1, channel=0, format=0x4011
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.500041] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x9
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.500050] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x9
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.500406] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x6
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.500435] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x6
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.500656] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x6
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.500860] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x6
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.501104] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x6
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.501400] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x6
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.501601] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x6
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.501799] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x6
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.502037] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x6
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.502327] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x6
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.502528] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x6
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.502724] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x6
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.502962] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x6
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.503253] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x6
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.503452] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x6
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.503649] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x6
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.503887] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x6
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.504177] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x6
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.504378] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x6
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.504575] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x6
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.504813] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x6
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.505103] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x6
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.505864] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x9
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.505939] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x9
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.506046] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x9
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.506204] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x9
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.506464] ALSA hda_intel.c:1642: azx_pcm_prepare: bufsize=0x3700, format=0x4011
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.506471] ALSA hda_codec.c:1157: hda_codec_setup_stream: NID=0x9, stream=0x1, channel=0, format=0x4011
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.520059] ALSA hda_intel.c:1642: azx_pcm_prepare: bufsize=0x3700, format=0x4011
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.520066] ALSA hda_codec.c:1157: hda_codec_setup_stream: NID=0x9, stream=0x1, channel=0, format=0x4011
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.540054] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x9
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.540095] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x9
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.676147] ALSA hda_intel.c:1642: azx_pcm_prepare: bufsize=0x10000, format=0x4011
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.676157] ALSA hda_codec.c:1157: hda_codec_setup_stream: NID=0x6, stream=0x8, channel=0, format=0x4011
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.690053] ALSA hda_intel.c:1642: azx_pcm_prepare: bufsize=0x10000, format=0x4011
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.690063] ALSA hda_codec.c:1157: hda_codec_setup_stream: NID=0x6, stream=0x8, channel=0, format=0x4011
Jun 10 20:28:24 marcoftheknight-desktop rtkit-daemon[1368]: Supervising 3 threads of 1 processes of 1 users.
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.715436] ALSA hda_intel.c:1642: azx_pcm_prepare: bufsize=0x10000, format=0x4011
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.715444] ALSA hda_codec.c:1157: hda_codec_setup_stream: NID=0x9, stream=0x1, channel=0, format=0x4011
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.730048] ALSA hda_intel.c:1642: azx_pcm_prepare: bufsize=0x10000, format=0x4011
Jun 10 20:28:24 marcoftheknight-desktop kernel: [   48.730055] ALSA hda_codec.c:1157: hda_codec_setup_stream: NID=0x9, stream=0x1, channel=0, format=0x4011
Jun 10 20:28:24 marcoftheknight-desktop rtkit-daemon[1368]: Supervising 4 threads of 1 processes of 1 users.
Jun 10 20:28:25 marcoftheknight-desktop kernel: [   49.167160] CPU0 attaching NULL sched-domain.
Jun 10 20:28:25 marcoftheknight-desktop kernel: [   49.167164] CPU1 attaching NULL sched-domain.
Jun 10 20:28:25 marcoftheknight-desktop kernel: [   49.167166] CPU2 attaching NULL sched-domain.
Jun 10 20:28:25 marcoftheknight-desktop kernel: [   49.167168] CPU3 attaching NULL sched-domain.
Jun 10 20:28:25 marcoftheknight-desktop kernel: [   49.231328] CPU0 attaching sched-domain:
Jun 10 20:28:25 marcoftheknight-desktop kernel: [   49.231330]  domain 0: span 0-3 level MC
Jun 10 20:28:25 marcoftheknight-desktop kernel: [   49.231332]   groups: 0 1 2 3
Jun 10 20:28:25 marcoftheknight-desktop kernel: [   49.231335] CPU1 attaching sched-domain:
Jun 10 20:28:25 marcoftheknight-desktop kernel: [   49.231336]  domain 0: span 0-3 level MC
Jun 10 20:28:25 marcoftheknight-desktop kernel: [   49.231338]   groups: 1 2 3 0
Jun 10 20:28:25 marcoftheknight-desktop kernel: [   49.231340] CPU2 attaching sched-domain:
Jun 10 20:28:25 marcoftheknight-desktop kernel: [   49.231341]  domain 0: span 0-3 level MC
Jun 10 20:28:25 marcoftheknight-desktop kernel: [   49.231342]   groups: 2 3 0 1
Jun 10 20:28:25 marcoftheknight-desktop kernel: [   49.231344] CPU3 attaching sched-domain:
Jun 10 20:28:25 marcoftheknight-desktop kernel: [   49.231345]  domain 0: span 0-3 level MC
Jun 10 20:28:25 marcoftheknight-desktop kernel: [   49.231346]   groups: 3 0 1 2
Jun 10 20:28:25 marcoftheknight-desktop rtkit-daemon[1368]: Supervising 5 threads of 2 processes of 1 users.
Jun 10 20:28:30 marcoftheknight-desktop kernel: [   54.357116] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x9
Jun 10 20:28:30 marcoftheknight-desktop kernel: [   54.357130] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x9
Jun 10 20:28:30 marcoftheknight-desktop kernel: [   54.357719] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x2
Jun 10 20:28:30 marcoftheknight-desktop kernel: [   54.357754] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x2
Jun 10 20:28:38 marcoftheknight-desktop kernel: [   62.741547] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x6
Jun 10 20:28:38 marcoftheknight-desktop kernel: [   62.741589] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x6
Jun 10 20:28:52 marcoftheknight-desktop kernel: [   76.670059] No probe response from AP 00:24:01:68:94:60 after 500ms, disconnecting.
Jun 10 20:28:53 marcoftheknight-desktop kernel: [   77.818709] wlan0: direct probe to AP 00:24:01:68:94:60 (try 1)
Jun 10 20:28:54 marcoftheknight-desktop kernel: [   78.011910] wlan0: direct probe to AP 00:24:01:68:94:60 (try 2)
Jun 10 20:28:54 marcoftheknight-desktop kernel: [   78.210024] wlan0: direct probe to AP 00:24:01:68:94:60 (try 3)
Jun 10 20:28:54 marcoftheknight-desktop kernel: [   78.420024] wlan0: direct probe to AP 00:24:01:68:94:60 timed out
Jun 10 20:28:58 marcoftheknight-desktop NetworkManager: <debug> [1276216138.002182] periodic_update(): Roamed from BSSID 00:24:01:68:94:60 (startrekenterprise) to (none) ((none))
Jun 10 20:29:04 marcoftheknight-desktop kernel: [   88.619375] wlan0: direct probe to AP 00:24:01:68:94:60 (try 1)
Jun 10 20:29:04 marcoftheknight-desktop kernel: [   88.627228] wlan0: direct probe responded
Jun 10 20:29:04 marcoftheknight-desktop kernel: [   88.627231] wlan0: authenticate with AP 00:24:01:68:94:60 (try 1)
Jun 10 20:29:04 marcoftheknight-desktop kernel: [   88.629368] wlan0: authenticated
Jun 10 20:29:04 marcoftheknight-desktop kernel: [   88.629380] wlan0: associate with AP 00:24:01:68:94:60 (try 1)
Jun 10 20:29:04 marcoftheknight-desktop kernel: [   88.639578] wlan0: RX AssocResp from 00:24:01:68:94:60 (capab=0x431 status=0 aid=2)
Jun 10 20:29:04 marcoftheknight-desktop kernel: [   88.639580] wlan0: associated
Jun 10 20:29:10 marcoftheknight-desktop NetworkManager: <debug> [1276216150.003518] periodic_update(): Roamed from BSSID (none) ((none)) to 00:24:01:68:94:60 (startrekenterprise)
Jun 10 20:29:52 marcoftheknight-desktop kernel: [  136.660022] No probe response from AP 00:24:01:68:94:60 after 500ms, disconnecting.
Jun 10 20:29:53 marcoftheknight-desktop kernel: [  137.808769] wlan0: direct probe to AP 00:24:01:68:94:60 (try 1)
Jun 10 20:29:54 marcoftheknight-desktop kernel: [  138.000054] wlan0: direct probe to AP 00:24:01:68:94:60 (try 2)
Jun 10 20:29:54 marcoftheknight-desktop kernel: [  138.005090] wlan0: direct probe responded
Jun 10 20:29:54 marcoftheknight-desktop kernel: [  138.005093] wlan0: authenticate with AP 00:24:01:68:94:60 (try 1)
Jun 10 20:29:54 marcoftheknight-desktop kernel: [  138.010634] wlan0: authenticated
Jun 10 20:29:54 marcoftheknight-desktop kernel: [  138.010646] wlan0: associate with AP 00:24:01:68:94:60 (try 1)
Jun 10 20:29:54 marcoftheknight-desktop kernel: [  138.016583] wlan0: RX AssocResp from 00:24:01:68:94:60 (capab=0x431 status=0 aid=2)
Jun 10 20:29:54 marcoftheknight-desktop kernel: [  138.016585] wlan0: associated
Jun 10 20:35:39 marcoftheknight-desktop kernel: [  483.369791] ALSA hda_intel.c:1642: azx_pcm_prepare: bufsize=0x10000, format=0x4011
Jun 10 20:35:39 marcoftheknight-desktop kernel: [  483.369802] ALSA hda_codec.c:1157: hda_codec_setup_stream: NID=0x6, stream=0x8, channel=0, format=0x4011
Jun 10 20:35:39 marcoftheknight-desktop kernel: [  483.380672] ALSA hda_intel.c:1642: azx_pcm_prepare: bufsize=0x10000, format=0x4011
Jun 10 20:35:39 marcoftheknight-desktop kernel: [  483.380682] ALSA hda_codec.c:1157: hda_codec_setup_stream: NID=0x6, stream=0x8, channel=0, format=0x4011
Jun 10 20:35:45 marcoftheknight-desktop kernel: [  489.459845] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x6
Jun 10 20:35:45 marcoftheknight-desktop kernel: [  489.459880] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x6
Jun 10 20:39:39 marcoftheknight-desktop kernel: [  723.516179] ALSA hda_intel.c:1642: azx_pcm_prepare: bufsize=0x10000, format=0x4011
Jun 10 20:39:39 marcoftheknight-desktop kernel: [  723.516190] ALSA hda_codec.c:1157: hda_codec_setup_stream: NID=0x6, stream=0x8, channel=0, format=0x4011
Jun 10 20:39:39 marcoftheknight-desktop kernel: [  723.540694] ALSA hda_intel.c:1642: azx_pcm_prepare: bufsize=0x10000, format=0x4011
Jun 10 20:39:39 marcoftheknight-desktop kernel: [  723.540703] ALSA hda_codec.c:1157: hda_codec_setup_stream: NID=0x6, stream=0x8, channel=0, format=0x4011
Jun 10 20:39:47 marcoftheknight-desktop kernel: [  731.279108] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x6
Jun 10 20:39:47 marcoftheknight-desktop kernel: [  731.279147] ALSA hda_codec.c:1175: hda_codec_cleanup_stream: NID=0x6

---

### Post by afrodeity on 2010-08-15
[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/550319](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/550319)

---

### Post by bodhi.zazen on 2010-08-15
Note: I closed the poll.

---

