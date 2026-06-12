---
title: "xorg crashes when booting computer"
date: 2012-05-29
forum: General Help
---

### Post by jake.anq on 2012-05-29
Hi

I realize that this questions or variants of it have been posted in multiple locations but none of the solutions have worked for me so far.

Upon running a general system update (Using the normal update manager), the computer now refuses to load a GUI.  It normally loads the purple screen with ubuntu written on it and the orange/white dots then drops to a tty.

The graphics card is an ATI Mobility Radeon HD 4650 with the fglrx driver and I am running Ubuntu 12.04 64 bit fully updated as of today.  The default desktop manager is lightdm and I use xfce as my desktop.

Some solutions I have already tried:

[LIST]
[*]Changing the default display manager to gdm, kdm, xfce4-session - All of these freeze on the purple screen and don't drop to a shell
[*]sudo apt-get purge lightdm; sudo apt-get install lightdm - Made no difference
[*]Switching to the tty and typing startx - still frozen
[*]Using recovery mode to boot into failsafe x windows - Made no difference
[*]Using a xorg.conf file that doesn't include the fglrx driver - Made no difference
[*]Using the nosplash grub boot flags - Made no difference
[*]Booting into an older kernel version - Made no difference
[*]Running update-grub - Yet again, made no difference
[/LIST]
This is my lightdm.log (/var/log/lightdm/lightdm.log)
```
[+0.00s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.00s] DEBUG: Starting Light Display Manager 1.2.1, UID=0 PID=1484
[+0.00s] DEBUG: Loaded configuration from /etc/lightdm/lightdm.conf
[+0.00s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.00s] DEBUG: Registered seat module xlocal
[+0.00s] DEBUG: Registered seat module xremote
[+0.00s] DEBUG: Adding default seat
[+0.00s] DEBUG: Starting seat
[+0.00s] DEBUG: Starting new display for greeter
[+0.00s] DEBUG: Starting local X display
[+0.01s] DEBUG: X server :0 will replace Plymouth
[+0.03s] DEBUG: Using VT 7
[+0.03s] DEBUG: Activating VT 7
[+0.03s] DEBUG: Logging to /var/log/lightdm/x-0.log
[+0.03s] DEBUG: Writing X server authority to /var/run/lightdm/root/:0
[+0.03s] DEBUG: Launching X Server
[+0.03s] DEBUG: Launching process 1511: /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch -background none
[+0.03s] DEBUG: Waiting for ready signal from X server :0
[+0.03s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.03s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+1.22s] DEBUG: Process 1511 exited with return value 127
[+1.22s] DEBUG: X server stopped
[+1.22s] DEBUG: Removing X server authority /var/run/lightdm/root/:0
[+1.22s] DEBUG: Releasing VT 7
[+1.22s] DEBUG: Stopping Plymouth, X server failed to start
[+1.23s] DEBUG: Display server stopped
[+1.23s] DEBUG: Stopping display
[+1.23s] DEBUG: Display stopped
[+1.23s] DEBUG: Stopping X local seat, failed to start a display
[+1.23s] DEBUG: Stopping seat
[+1.23s] DEBUG: Seat stopped
[+1.23s] DEBUG: Required seat has stopped
[+1.23s] DEBUG: Stopping display manager
[+1.23s] DEBUG: Display manager stopped
[+1.23s] DEBUG: Stopping daemon
[+1.23s] DEBUG: Exiting with return value 1
```And my /var/log/Xorg.0.log

```
[    28.658] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    28.658] X Protocol Version 11, Revision 0
[    28.658] Build Operating System: Linux 2.6.24-31-server x86_64 Ubuntu
[    28.658] Current Operating System: Linux HAL-9000 3.2.0-24-generic #39-Ubuntu SMP Mon May 21 16:52:17 UTC 2012 x86_64
[    28.659] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-24-generic root=UUID=1a4b48c2-44ca-48db-a19c-2c0bdae58679 ro quiet splash vt.handoff=7
[    28.659] Build Date: 07 May 2012  11:43:21PM
[    28.659] xorg-server 2:1.11.4-0ubuntu10.2 (For technical support please see http://www.ubuntu.com/support) 
[    28.659] Current version of pixman: 0.24.4
[    28.659]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    28.659] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    28.659] (==) Log file: "/var/log/Xorg.0.log", Time: Tue May 29 19:13:20 2012
[    28.659] (==) Using config file: "/etc/X11/xorg.conf"
[    28.659] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    28.659] (==) ServerLayout "aticonfig Layout"
[    28.659] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[    28.659] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[    28.659] (**) |   |-->Device "aticonfig-Device[0]-0"
[    28.659] (==) Automatically adding devices
[    28.659] (==) Automatically enabling devices
[    28.781] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    28.793]     Entry deleted from font path.
[    28.927] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    28.964] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    28.964] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    28.964] (II) Loader magic: 0x7feddd542b00
[    28.964] (II) Module ABI versions:
[    28.964]     X.Org ANSI C Emulation: 0.4
[    28.964]     X.Org Video Driver: 11.0
[    28.964]     X.Org XInput driver : 16.0
[    28.964]     X.Org Server Extension : 6.0
[    28.965] (--) PCI:*(0:1:0:0) 1002:9480:1028:0447 rev 0, Mem @ 0xc0000000/268435456, 0xfbe20000/65536, I/O @ 0x0000e000/256, BIOS @ 0x????????/131072
[    28.965] (II) Open ACPI successful (/var/run/acpid.socket)
[    28.965] (II) "extmod" will be loaded by default.
[    28.965] (II) "dbe" will be loaded by default.
[    28.965] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    28.965] (II) "record" will be loaded by default.
[    28.965] (II) "dri" will be loaded by default.
[    28.965] (II) "dri2" will be loaded by default.
[    28.965] (II) LoadModule: "glx"
[    29.129] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    29.129] (II) Module glx: vendor="X.Org Foundation"
[    29.129]     compiled for 1.11.3, module version = 1.0.0
[    29.129]     ABI class: X.Org Server Extension, version 6.0
[    29.129] (==) AIGLX enabled
[    29.129] (II) Loading extension GLX
[    29.129] (II) LoadModule: "extmod"
[    29.129] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    29.129] (II) Module extmod: vendor="X.Org Foundation"
[    29.129]     compiled for 1.11.3, module version = 1.0.0
[    29.129]     Module class: X.Org Server Extension
[    29.129]     ABI class: X.Org Server Extension, version 6.0
[    29.129] (II) Loading extension MIT-SCREEN-SAVER
[    29.129] (II) Loading extension XFree86-VidModeExtension
[    29.129] (II) Loading extension XFree86-DGA
[    29.129] (II) Loading extension DPMS
[    29.129] (II) Loading extension XVideo
[    29.129] (II) Loading extension XVideo-MotionCompensation
[    29.129] (II) Loading extension X-Resource
[    29.129] (II) LoadModule: "dbe"
[    29.129] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    29.130] (II) Module dbe: vendor="X.Org Foundation"
[    29.130]     compiled for 1.11.3, module version = 1.0.0
[    29.130]     Module class: X.Org Server Extension
[    29.130]     ABI class: X.Org Server Extension, version 6.0
[    29.130] (II) Loading extension DOUBLE-BUFFER
[    29.130] (II) LoadModule: "record"
[    29.130] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    29.130] (II) Module record: vendor="X.Org Foundation"
[    29.130]     compiled for 1.11.3, module version = 1.13.0
[    29.130]     Module class: X.Org Server Extension
[    29.130]     ABI class: X.Org Server Extension, version 6.0
[    29.130] (II) Loading extension RECORD
[    29.130] (II) LoadModule: "dri"
[    29.130] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    29.130] (II) Module dri: vendor="X.Org Foundation"
[    29.130]     compiled for 1.11.3, module version = 1.0.0
[    29.130]     ABI class: X.Org Server Extension, version 6.0
[    29.130] (II) Loading extension XFree86-DRI
[    29.130] (II) LoadModule: "dri2"
[    29.130] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    29.130] (II) Module dri2: vendor="X.Org Foundation"
[    29.130]     compiled for 1.11.3, module version = 1.2.0
[    29.130]     ABI class: X.Org Server Extension, version 6.0
[    29.130] (II) Loading extension DRI2
[    29.130] (II) LoadModule: "fglrx"
[    29.131] (II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
[    29.144] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[    29.144]     compiled for 1.4.99.906, module version = 8.96.4
[    29.144]     Module class: X.Org Video Driver
[    29.144] (II) Loading sub module "fglrxdrm"
[    29.144] (II) LoadModule: "fglrxdrm"
[    29.144] (II) Loading /usr/lib/xorg/modules/linux/libfglrxdrm.so
[    29.144] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    29.144]     compiled for 1.4.99.906, module version = 8.96.4
[    29.144] (II) ATI Proprietary Linux Driver Version Identifier:8.96.4
[    29.144] (II) ATI Proprietary Linux Driver Release Identifier: 8.961                                
[    29.144] (II) ATI Proprietary Linux Driver Build Date: Apr  5 2012 23:06:21
[    29.144] (++) using VT number 7

[    29.145] (WW) Falling back to old probe method for fglrx
[    29.156] (II) Loading PCS database from /etc/ati/amdpcsdb
[    29.156] (--) Chipset Supported AMD Graphics Processor (0x9480) found
[    29.156] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
[    29.157] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[    29.157] (II) AMD Video driver is signed
[    29.157] (II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
[    29.157] (II) Loading /usr/lib/xorg/modules/linux/libfglrxdrm.so
[    29.157] (II) fglrx(0): pEnt->device->identifier=0x7fedde05fac0
[    29.157] (II) fglrx(0): === [xdl_xs111_atiddxPreInit] === begin
[    29.157] (II) Loading sub module "vgahw"
[    29.157] (II) LoadModule: "vgahw"
[    29.157] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    29.157] (II) Module vgahw: vendor="X.Org Foundation"
[    29.157]     compiled for 1.11.3, module version = 0.1.0
[    29.157]     ABI class: X.Org Video Driver, version 11.0
[    29.157] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[    29.157] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    29.157] (==) fglrx(0): Default visual is TrueColor
[    29.157] (**) fglrx(0): Option "DPMS" "true"
[    29.157] (==) fglrx(0): RGB weight 888
[    29.157] (II) fglrx(0): Using 8 bits per RGB 
[    29.157] (==) fglrx(0): Buffer Tiling is ON
[    29.157] (II) Loading sub module "fglrxdrm"
[    29.157] (II) LoadModule: "fglrxdrm"
[    29.157] (II) Loading /usr/lib/xorg/modules/linux/libfglrxdrm.so
[    29.157] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    29.157]     compiled for 1.4.99.906, module version = 8.96.4
[    29.159] ukiDynamicMajor: found major device number 249
[    29.159] ukiDynamicMajor: found major device number 249
[    29.159] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    29.159] ukiOpenDevice: node name is /dev/ati/card0
[    29.159] ukiOpenDevice: open result is 12, (OK)
[    29.159] ukiOpenByBusid: ukiOpenMinor returns 12
[    29.159] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    29.159] (**) fglrx(0): NoAccel = NO
[    29.159] (**) fglrx(0): ATI 2D Acceleration Architecture enabled
[    29.159] (--) fglrx(0): Chipset: "ATI Mobility Radeon HD 4650 " (Chipset = 0x9480)
[    29.159] (--) fglrx(0): (PciSubVendor = 0x1028, PciSubDevice = 0x0447)
[    29.159] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
[    29.159] (--) fglrx(0): Linear framebuffer (phys) at 0xc0000000
[    29.159] (--) fglrx(0): MMIO registers at 0xfbe20000
[    29.159] (--) fglrx(0): I/O port at 0x0000e000
[    29.159] (==) fglrx(0): ROM-BIOS at 0x000c0000
[    29.160] (II) fglrx(0): AC Adapter is used
[    29.162] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
[    29.162] (II) Loading sub module "vbe"
[    29.162] (II) LoadModule: "vbe"
[    29.169] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    29.170] (II) Module vbe: vendor="X.Org Foundation"
[    29.170]     compiled for 1.11.3, module version = 1.1.0
[    29.170]     ABI class: X.Org Video Driver, version 11.0
[    29.170] (II) fglrx(0): VESA BIOS detected
[    29.170] (II) fglrx(0): VESA VBE Version 3.0
[    29.170] (II) fglrx(0): VESA VBE Total Mem: 16384 kB
[    29.170] (II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
[    29.170] (II) fglrx(0): VESA VBE OEM Software Rev: 11.22
[    29.170] (II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
[    29.170] (II) fglrx(0): VESA VBE OEM Product: M96
[    29.170] (II) fglrx(0): VESA VBE OEM Product Rev: 01.00
[    29.203] (II) fglrx(0): ATI Video BIOS revision 9 or later detected
[    29.204] (--) fglrx(0): Video RAM: 1048576 kByte, Type: DDR3
[    29.204] (II) fglrx(0): PCIE card detected
[    29.204] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[    29.204] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[    29.209] (II) fglrx(0): Using adapter: 1:0.0.
[    29.237] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x40000000)
[    29.295] (II) fglrx(0): Interrupt handler installed at IRQ 50.
[    29.295] (II) fglrx(0): RandR 1.2 support is enabled!
[    29.295] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[    29.295] (==) fglrx(0): Center Mode is disabled 
[    29.295] (II) Loading sub module "fb"
[    29.295] (II) LoadModule: "fb"
[    29.295] (II) Loading /usr/lib/xorg/modules/libfb.so
[    29.295] (II) Module fb: vendor="X.Org Foundation"
[    29.295]     compiled for 1.11.3, module version = 1.0.0
[    29.295]     ABI class: X.Org ANSI C Emulation, version 0.4
[    29.295] (II) Loading sub module "ddc"
[    29.295] (II) LoadModule: "ddc"
[    29.295] (II) Module "ddc" already built-in
[    29.651] (II) fglrx(0): Finished Initialize PPLIB!
[    29.656] (II) fglrx(0): Output LVDS using monitor section aticonfig-Monitor[0]-0
[    29.656] (II) fglrx(0): Output DFP1 has no monitor section
[    29.656] (II) fglrx(0): Output CRT1 has no monitor section
[    29.656] (II) Loading sub module "ddc"
[    29.656] (II) LoadModule: "ddc"
[    29.656] (II) Module "ddc" already built-in
[    29.656] (II) fglrx(0): Connected Display0: LVDS
[    29.656] (II) fglrx(0): Display0 EDID data ---------------------------
[    29.656] (II) fglrx(0): Manufacturer: INL  Model: a  Serial#: 0
[    29.656] (II) fglrx(0): Year: 2009  Week: 0
[    29.656] (II) fglrx(0): EDID Version: 1.3
[    29.656] (II) fglrx(0): Digital Display Input
[    29.656] (II) fglrx(0): Max Image Size [cm]: horiz.: 34  vert.: 19
[    29.656] (II) fglrx(0): Gamma: 2.20
[    29.656] (II) fglrx(0): No DPMS capabilities specified
[    29.656] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    29.656] (II) fglrx(0): First detailed timing is preferred mode
[    29.656] (II) fglrx(0): redX: 0.620 redY: 0.340   greenX: 0.330 greenY: 0.605
[    29.656] (II) fglrx(0): blueX: 0.150 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
[    29.656] (II) fglrx(0): Manufacturer's mask: 0
[    29.656] (II) fglrx(0): Supported detailed timing:
[    29.656] (II) fglrx(0): clock: 67.1 MHz   Image Size:  344 x 194 mm
[    29.656] (II) fglrx(0): h_active: 1366  h_sync: 1383  h_sync_end 1395 h_blank_end 1434 h_border: 0
[    29.656] (II) fglrx(0): v_active: 768  v_sync: 771  v_sync_end 773 v_blanking: 781 v_border: 0
[    29.656] (II) fglrx(0): Supported detailed timing:
[    29.656] (II) fglrx(0): clock: 67.1 MHz   Image Size:  344 x 194 mm
[    29.656] (II) fglrx(0): h_active: 1366  h_sync: 1383  h_sync_end 1395 h_blank_end 1434 h_border: 0
[    29.656] (II) fglrx(0): v_active: 768  v_sync: 771  v_sync_end 773 v_blanking: 781 v_border: 0
[    29.656] (II) fglrx(0):  1G5D3Å156GW01
[    29.656] (II) fglrx(0): Unknown vendor-specific block 0
[    29.656] (II) fglrx(0): EDID (in hex):
[    29.656] (II) fglrx(0):     00ffffffffffff0025cc0a0000000000
[    29.656] (II) fglrx(0):     00130103902213780ac8859e57549b26
[    29.656] (II) fglrx(0):     12505400000001010101010101010101
[    29.656] (II) fglrx(0):     010101010101361a564450000d30110c
[    29.656] (II) fglrx(0):     320058c21000001a361a564450000d30
[    29.656] (II) fglrx(0):     110c320058c21000001a000000fe0031
[    29.656] (II) fglrx(0):     47354433813135364757303100000000
[    29.656] (II) fglrx(0):     00000000000000000001010a202000f2
[    29.656] (II) fglrx(0): End of Display0 EDID data --------------------
[    29.813] (II) fglrx(0): EDID for output LVDS
[    29.813] (II) fglrx(0): Manufacturer: INL  Model: a  Serial#: 0
[    29.813] (II) fglrx(0): Year: 2009  Week: 0
[    29.813] (II) fglrx(0): EDID Version: 1.3
[    29.813] (II) fglrx(0): Digital Display Input
[    29.813] (II) fglrx(0): Max Image Size [cm]: horiz.: 34  vert.: 19
[    29.813] (II) fglrx(0): Gamma: 2.20
[    29.813] (II) fglrx(0): No DPMS capabilities specified
[    29.813] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    29.813] (II) fglrx(0): First detailed timing is preferred mode
[    29.813] (II) fglrx(0): redX: 0.620 redY: 0.340   greenX: 0.330 greenY: 0.605
[    29.813] (II) fglrx(0): blueX: 0.150 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
[    29.813] (II) fglrx(0): Manufacturer's mask: 0
[    29.813] (II) fglrx(0): Supported detailed timing:
[    29.813] (II) fglrx(0): clock: 67.1 MHz   Image Size:  344 x 194 mm
[    29.813] (II) fglrx(0): h_active: 1366  h_sync: 1383  h_sync_end 1395 h_blank_end 1434 h_border: 0
[    29.813] (II) fglrx(0): v_active: 768  v_sync: 771  v_sync_end 773 v_blanking: 781 v_border: 0
[    29.813] (II) fglrx(0): Supported detailed timing:
[    29.813] (II) fglrx(0): clock: 67.1 MHz   Image Size:  344 x 194 mm
[    29.813] (II) fglrx(0): h_active: 1366  h_sync: 1383  h_sync_end 1395 h_blank_end 1434 h_border: 0
[    29.813] (II) fglrx(0): v_active: 768  v_sync: 771  v_sync_end 773 v_blanking: 781 v_border: 0
[    29.813] (II) fglrx(0):  1G5D3Å156GW01
[    29.813] (II) fglrx(0): Unknown vendor-specific block 0
[    29.813] (II) fglrx(0): EDID (in hex):
[    29.813] (II) fglrx(0):     00ffffffffffff0025cc0a0000000000
[    29.813] (II) fglrx(0):     00130103902213780ac8859e57549b26
[    29.813] (II) fglrx(0):     12505400000001010101010101010101
[    29.813] (II) fglrx(0):     010101010101361a564450000d30110c
[    29.813] (II) fglrx(0):     320058c21000001a361a564450000d30
[    29.813] (II) fglrx(0):     110c320058c21000001a000000fe0031
[    29.813] (II) fglrx(0):     47354433813135364757303100000000
[    29.813] (II) fglrx(0):     00000000000000000001010a202000f2
[    29.813] (II) fglrx(0): EDID vendor "INL", prod id 10
[    29.813] (II) fglrx(0): Printing DDC gathered Modelines:
[    29.813] (II) fglrx(0): Modeline "1366x768"x0.0   67.10  1366 1383 1395 1434  768 771 773 781 +hsync -vsync (46.8 kHz)
[    29.813] (II) fglrx(0): Printing probed modes for output LVDS
[    29.813] (II) fglrx(0): Modeline "1366x768"x60.0   67.10  1366 1383 1395 1434  768 771 773 781 -hsync +vsync (46.8 kHz)
[    29.813] (II) fglrx(0): Modeline "1280x768"x60.0   67.10  1280 1383 1395 1434  768 771 773 781 -hsync +vsync (46.8 kHz)
[    29.813] (II) fglrx(0): Modeline "1280x720"x60.0   67.10  1280 1383 1395 1434  720 771 773 781 -hsync +vsync (46.8 kHz)
[    29.813] (II) fglrx(0): Modeline "1024x768"x60.0   67.10  1024 1383 1395 1434  768 771 773 781 -hsync +vsync (46.8 kHz)
[    29.813] (II) fglrx(0): Modeline "1024x600"x60.0   67.10  1024 1383 1395 1434  600 771 773 781 -hsync +vsync (46.8 kHz)
[    29.813] (II) fglrx(0): Modeline "800x600"x60.0   67.10  800 1383 1395 1434  600 771 773 781 -hsync +vsync (46.8 kHz)
[    29.813] (II) fglrx(0): Modeline "800x480"x60.0   67.10  800 1383 1395 1434  480 771 773 781 -hsync +vsync (46.8 kHz)
[    29.813] (II) fglrx(0): Modeline "720x480"x60.0   67.10  720 1383 1395 1434  480 771 773 781 -hsync +vsync (46.8 kHz)
[    29.813] (II) fglrx(0): Modeline "640x480"x60.0   67.10  640 1383 1395 1434  480 771 773 781 -hsync +vsync (46.8 kHz)
[    29.813] (II) fglrx(0): EDID for output DFP1
[    29.813] (II) fglrx(0): EDID for output CRT1
[    29.813] (II) fglrx(0): Output LVDS connected
[    29.813] (II) fglrx(0): Output DFP1 disconnected
[    29.813] (II) fglrx(0): Output CRT1 disconnected
[    29.813] (II) fglrx(0): Using user preference for initial modes
[    29.813] (II) fglrx(0): Output LVDS using initial mode 1366x768
[    29.813] (II) fglrx(0): Display dimensions: (340, 190) mm
[    29.813] (II) fglrx(0): DPI set to (102, 102)
[    29.813] (II) fglrx(0): Adapter ATI Mobility Radeon HD 4650  has 2 configurable heads and 1 displays connected.
[    29.813] (==) fglrx(0):  PseudoColor visuals disabled
[    29.813] (II) Loading sub module "ramdac"
[    29.813] (II) LoadModule: "ramdac"
[    29.813] (II) Module "ramdac" already built-in
[    29.813] (==) fglrx(0): NoDRI = NO
[    29.813] (==) fglrx(0): Capabilities: 0x00000000
[    29.813] (==) fglrx(0): CapabilitiesEx: 0x00000000
[    29.813] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[    29.813] (==) fglrx(0): UseFastTLS=0
[    29.813] (II) fglrx(0): Desktop Vsync is enabled.
[    29.813] (--) Depth 24 pixmap format is 32 bpp
[    29.815] (II) Loading extension ATIFGLRXDRI
[    29.815] (II) fglrx(0): doing swlDriScreenInit
[    29.815] (II) fglrx(0): swlDriScreenInit for fglrx driver
[    29.815] ukiDynamicMajor: found major device number 249
[    29.815] ukiDynamicMajor: found major device number 249
[    29.815] ukiDynamicMajor: found major device number 249
[    29.815] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    29.815] ukiOpenDevice: node name is /dev/ati/card0
[    29.815] ukiOpenDevice: open result is 17, (OK)
[    29.815] ukiOpenByBusid: ukiOpenMinor returns 17
[    29.815] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    29.815] (II) fglrx(0): [uki] DRM interface version 1.0
[    29.815] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:1:0:0"
[    29.815] (II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
[    29.815] (II) fglrx(0): [uki] mapped SAREA 0x2000 to 0x7feddd123000
[    29.815] (II) fglrx(0): [uki] framebuffer handle = 0x3000
[    29.815] (II) fglrx(0): [uki] added 1 reserved context for kernel
[    29.815] (II) fglrx(0): swlDriScreenInit done
[    29.815] (II) fglrx(0): Kernel Module Version Information:
[    29.815] (II) fglrx(0):     Name: fglrx
[    29.815] (II) fglrx(0):     Version: 8.96.4
[    29.815] (II) fglrx(0):     Date: Apr  5 2012
[    29.815] (II) fglrx(0):     Desc: ATI FireGL DRM kernel module
[    29.815] (II) fglrx(0): Kernel Module version matches driver.
[    29.815] (II) fglrx(0): Kernel Module Build Time Information:
[    29.815] (II) fglrx(0):     Build-Kernel UTS_RELEASE:        3.2.0-24-generic
[    29.815] (II) fglrx(0):     Build-Kernel MODVERSIONS:        no
[    29.815] (II) fglrx(0):     Build-Kernel __SMP__:            yes
[    29.815] (II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
[    29.815] (II) fglrx(0): [uki] register handle = 0x00004000
[    29.832] (II) fglrx(0): DRI initialization successfull
[    29.832] (II) fglrx(0): FBADPhys: 0xf00000000 FBMappedSize: 0x01004000

```And the /var/log/lightdm/x-0.log
```

X.Org X Server 1.11.3
Release Date: 2011-12-16
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-31-server x86_64 Ubuntu
Current Operating System: Linux HAL-9000 3.2.0-24-generic #39-Ubuntu SMP Mon May 21 16:52:17 UTC 2012 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-24-generic root=UUID=1a4b48c2-44ca-48db-a19c-2c0bdae58679 ro quiet splash vt.handoff=7
Build Date: 07 May 2012  11:43:21PM
xorg-server 2:1.11.4-0ubuntu10.2 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.24.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue May 29 19:13:20 2012
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
/usr/bin/X: symbol lookup error: /usr/lib/xorg/modules/drivers/fglrx_drv.so: undefined symbol: GlxInitVisuals2D
```And last, but not least, the xorg.conf file:
```
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "Default Screen"
    DefaultDepth     24
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
        Modes    "1366x768"
    EndSubSection
EndSection


```

---

### Post by matt_symes on 2012-05-29
Hi

> /usr/bin/X: symbol lookup error: /usr/lib/xorg/modules/drivers/fglrx_drv.so: undefined symbol: GlxInitVisuals2D

I have never had this error but i would suggest reinstalling the ATI driver and see if that fixes it.

Boot into a root console from the command line and reinstall.

You can get the driver from the repositories or from here.

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)

Kind regards

---

