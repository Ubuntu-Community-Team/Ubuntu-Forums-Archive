---
title: "Destop Effect And Compiz Not Working With ATI Radeon And Ubuntu 10.10"
date: 2010-11-14
forum: General Help
---

### Post by Tapas Bose, India on 2010-11-14
Hello everybody.
I had upgraded my Ubuntu to Maverick two days ago from Lucid. Just after the up-gradation I was facing trouble with it. 
The scenario from the beginning was that first I installed Lucid then the Proprietary ATI Radeon driver; after that compiz and cairo dock. These all were going fine. The caro dock with opengl was working well. Then I upgraded Lucid and restarted my machine. 
The first thing I saw was that black background around the cairo dock and compiz stopped working. I reinstall both the software, but nothing was fruitful. In Lucid compiz was installed with unsupported-extra plugin, after up-gradation Synaptic informed me that this pluging no longer available and Synaptic kept in under local or obsolete software category. I also removed that.
In new CompizConfig Settings Manager whenever I am trying to check the desktop cube plugin it is informing me that it needs to enable OpenGl and Composite, but practically nothing is enabling. 
When I check the Extra setting from Visual Effect of Appearance Preference, it is searching for driver, blinking the monitor's display and throwing a message box with "Desktop effect could not be enabled" and again it turns back into None mode.
The last thing I test is that the [Compiz-Check]("http://forlong.blogage.de/entries/pages/Compiz-Check"). The result is :
```

tanmoy@My-Child:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 10.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RV710 [Radeon HD 4350]
 Driver in use:         fglrx
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 

```Lastly the output of fglrxinfo is:
```

tanmoy@My-Child:~$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4300/4500 Series
OpenGL version string: 3.3.10237 Compatibility Profile Context

```If anybody please help me out regarding these problems it will be very helpful to me.
Thank you.
Note: Proprietary Driver is installed in my machine no open source driver.

---

### Post by coffeecat on 2010-11-14
Your problem could be:

> **Tapas Bose, India said:**
> Note: Proprietary Driver is installed in my machine no open source driver.

Compare with the output of my compiz-check:

```
coffeecat@amd4-maverick:~/Desktop$ ./compiz-check 

Gathering information about your system...

 Distribution:          Ubuntu 10.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RV710 [Radeon HD 4350]
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]
```I have the same ATI chipset as you and I'm using the open-source driver and I get all the compiz effects I want. In fact I can get compiz just fine in Lucid as well with this card and the open-source driver.

**EDIT:** thinking about this, you should be able to get compiz with this card and the fglrx driver. I did try it (the proprietary driver) briefly, but as it gave me no more than the open-source and made a mess of Plymouth, I prefer the OS driver. Have you looked in Catalyst Control Centre to see if you can change settings there? It should be somewhere in your System menus. Failing that, an edit to your xorg.conf might be needed, but exactly what I don't know. That's why I prefer the OS driver - it works out-of-the-box with no xorg.conf to worry about.

---

### Post by Tapas Bose, India on 2010-11-14
@[coffeecat]("http://ubuntuforums.org/member.php?u=129087")
Thank you.
So what should I do now? How can I install open source ati driver?

---

### Post by cpmman on 2010-11-14
I had a compiz problem and followed this advice which corrected it:-

[***_http://ubuntuforums.org/showpost.php?p=9964610&postcount=2_***]("http://ubuntuforums.org/showpost.php?p=9964610&postcount=2")

---

### Post by realzippy on 2010-11-14
...can you post your

/var/log/Xorg.0.log

also?

---

### Post by Tapas Bose, India on 2010-11-14
What should I do now? purge compiz ppa or use the open source driver?

---

### Post by Tapas Bose, India on 2010-11-14
Xorg.0.log , here it is
```

[    12.696] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    12.696] X Protocol Version 11, Revision 0
[    12.696] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    12.696] Current Operating System: Linux My-Child 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:36:48 UTC 2010 i686
[    12.696] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=7b15fdfe-4624-4204-82b2-4baa5fe8fb65 ro quiet splash nomodeset video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap
[    12.696] Build Date: 16 September 2010  05:39:22PM
[    12.696] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
[    12.696] Current version of pixman: 0.18.4
[    12.696]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    12.696] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    12.696] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Nov 14 17:47:00 2010
[    12.696] (==) Using config file: "/etc/X11/xorg.conf"
[    12.696] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    12.696] (==) No Layout section.  Using the first Screen section.
[    12.696] (**) |-->Screen "Default Screen" (0)
[    12.696] (**) |   |-->Monitor "<default monitor>"
[    12.697] (==) No device specified for screen "Default Screen".
    Using the first device section listed.
[    12.697] (**) |   |-->Device "Default Device"
[    12.697] (==) No monitor specified for screen "Default Screen".
    Using a default monitor configuration.
[    12.697] (==) Automatically adding devices
[    12.697] (==) Automatically enabling devices
[    12.697] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    12.697]     Entry deleted from font path.
[    12.697] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    12.697] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    12.697] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    12.697] (II) Loader magic: 0x81f8e00
[    12.697] (II) Module ABI versions:
[    12.697]     X.Org ANSI C Emulation: 0.4
[    12.697]     X.Org Video Driver: 8.0
[    12.697]     X.Org XInput driver : 11.0
[    12.697]     X.Org Server Extension : 4.0
[    12.698] (--) PCI:*(0:1:0:0) 1002:954f:1682:2465 rev 0, Mem @ 0xd0000000/268435456, 0xff820000/65536, I/O @ 0x0000e000/256, BIOS @ 0x????????/131072
[    12.698] (II) Open ACPI successful (/var/run/acpid.socket)
[    12.698] (II) "extmod" will be loaded by default.
[    12.698] (II) "dbe" will be loaded by default.
[    12.698] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    12.698] (II) "record" will be loaded by default.
[    12.698] (II) "dri" will be loaded by default.
[    12.698] (II) "dri2" will be loaded by default.
[    12.698] (II) LoadModule: "glx"
[    12.698] (II) Loading /usr/lib/xorg/extra-modules/modules/extensions/libglx.so
[    12.698] (II) Module glx: vendor="FireGL - ATI Technologies Inc."
[    12.698]     compiled for 7.6.0, module version = 1.0.0
[    12.698] (II) Loading extension GLX
[    12.698] (II) LoadModule: "extmod"
[    12.706] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    12.706] (II) Module extmod: vendor="X.Org Foundation"
[    12.706]     compiled for 1.9.0, module version = 1.0.0
[    12.706]     Module class: X.Org Server Extension
[    12.706]     ABI class: X.Org Server Extension, version 4.0
[    12.706] (II) Loading extension MIT-SCREEN-SAVER
[    12.706] (II) Loading extension XFree86-VidModeExtension
[    12.706] (II) Loading extension XFree86-DGA
[    12.706] (II) Loading extension DPMS
[    12.706] (II) Loading extension XVideo
[    12.706] (II) Loading extension XVideo-MotionCompensation
[    12.706] (II) Loading extension X-Resource
[    12.706] (II) LoadModule: "dbe"
[    12.706] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    12.706] (II) Module dbe: vendor="X.Org Foundation"
[    12.706]     compiled for 1.9.0, module version = 1.0.0
[    12.706]     Module class: X.Org Server Extension
[    12.706]     ABI class: X.Org Server Extension, version 4.0
[    12.706] (II) Loading extension DOUBLE-BUFFER
[    12.706] (II) LoadModule: "record"
[    12.707] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    12.707] (II) Module record: vendor="X.Org Foundation"
[    12.707]     compiled for 1.9.0, module version = 1.13.0
[    12.707]     Module class: X.Org Server Extension
[    12.707]     ABI class: X.Org Server Extension, version 4.0
[    12.707] (II) Loading extension RECORD
[    12.707] (II) LoadModule: "dri"
[    12.707] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    12.707] (II) Module dri: vendor="X.Org Foundation"
[    12.707]     compiled for 1.9.0, module version = 1.0.0
[    12.707]     ABI class: X.Org Server Extension, version 4.0
[    12.707] (II) Loading extension XFree86-DRI
[    12.707] (II) LoadModule: "dri2"
[    12.708] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    12.708] (II) Module dri2: vendor="X.Org Foundation"
[    12.708]     compiled for 1.9.0, module version = 1.2.0
[    12.708]     ABI class: X.Org Server Extension, version 4.0
[    12.708] (II) Loading extension DRI2
[    12.708] (II) LoadModule: "fglrx"
[    12.708] (II) Loading /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so
[    12.719] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[    12.719]     compiled for 1.4.99.906, module version = 8.78.30
[    12.720]     Module class: X.Org Video Driver
[    12.720] (II) Loading sub module "fglrxdrm"
[    12.720] (II) LoadModule: "fglrxdrm"
[    12.720] (II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    12.720] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    12.720]     compiled for 1.8.99.905, module version = 8.78.30
[    12.720] (II) ATI Proprietary Linux Driver Version Identifier:8.78.30
[    12.720] (II) ATI Proprietary Linux Driver Release Identifier: 8.78.3                               
[    12.720] (II) ATI Proprietary Linux Driver Build Date: Sep 20 2010 21:30:49
[    12.720] (++) using VT number 7

[    12.720] (WW) Falling back to old probe method for fglrx
[    12.724] (II) Loading PCS database from /etc/ati/amdpcsdb
[    12.725] (--) Assigning device section with no busID to primary device
[    12.725] (--) Chipset Supported AMD Graphics Processor (0x954F) found
[    12.725] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
[    12.725] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[    12.725] (II) AMD Video driver is signed
[    12.725] (II) fglrx(0): pEnt->device->identifier=0x9998190
[    12.725] (II) fglrx(0): === [xdl_x760_atiddxPreInit] === begin
[    12.725] (II) Loading sub module "vgahw"
[    12.725] (II) LoadModule: "vgahw"
[    12.726] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    12.726] (II) Module vgahw: vendor="X.Org Foundation"
[    12.726]     compiled for 1.9.0, module version = 0.1.0
[    12.726]     ABI class: X.Org Video Driver, version 8.0
[    12.726] (II) fglrx(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
[    12.726] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[    12.726] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    12.726] (==) fglrx(0): Default visual is TrueColor
[    12.726] (==) fglrx(0): RGB weight 888
[    12.726] (II) fglrx(0): Using 8 bits per RGB 
[    12.726] (==) fglrx(0): Buffer Tiling is ON
[    12.726] (II) Loading sub module "fglrxdrm"
[    12.726] (II) LoadModule: "fglrxdrm"
[    12.726] (II) Reloading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    12.727] ukiDynamicMajor: found major device number 250
[    12.727] ukiDynamicMajor: found major device number 250
[    12.727] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    12.727] ukiOpenDevice: node name is /dev/ati/card0
[    12.727] ukiOpenDevice: open result is 11, (OK)
[    12.727] ukiOpenByBusid: ukiOpenMinor returns 11
[    12.727] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    12.728] (==) fglrx(0): NoAccel = NO
[    12.728] (==) fglrx(0): ATI 2D Acceleration Architecture enabled
[    12.728] (--) fglrx(0): Chipset: "ATI Radeon HD 4300/4500 Series" (Chipset = 0x954f)
[    12.728] (--) fglrx(0): (PciSubVendor = 0x1682, PciSubDevice = 0x2465)
[    12.728] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
[    12.728] (--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
[    12.728] (--) fglrx(0): MMIO registers at 0xff820000
[    12.728] (--) fglrx(0): I/O port at 0x0000e000
[    12.728] (==) fglrx(0): ROM-BIOS at 0x000c0000
[    12.728] (II) fglrx(0): AC Adapter is used
[    12.736] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
[    12.737] (II) Loading sub module "vbe"
[    12.737] (II) LoadModule: "vbe"
[    12.737] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    12.737] (II) Module vbe: vendor="X.Org Foundation"
[    12.737]     compiled for 1.9.0, module version = 1.1.0
[    12.737]     ABI class: X.Org Video Driver, version 8.0
[    12.737] (II) fglrx(0): VESA BIOS detected
[    12.737] (II) fglrx(0): VESA VBE Version 3.0
[    12.737] (II) fglrx(0): VESA VBE Total Mem: 16384 kB
[    12.737] (II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
[    12.737] (II) fglrx(0): VESA VBE OEM Software Rev: 11.21
[    12.737] (II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
[    12.737] (II) fglrx(0): VESA VBE OEM Product: 
[    12.737] (II) fglrx(0): VESA VBE OEM Product Rev: 01.00
[    12.775] (II) fglrx(0): ATI Video BIOS revision 9 or later detected
[    12.775] (--) fglrx(0): Video RAM: 1048576 kByte, Type: DDR2
[    12.775] (II) fglrx(0): PCIE card detected
[    12.775] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[    12.775] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[    12.777] (II) fglrx(0): Using adapter: 1:0.0.
[    12.808] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x40000000)
[    12.912] (II) fglrx(0): Interrupt handler installed at IRQ 46.
[    12.912] (II) fglrx(0): RandR 1.2 support is enabled!
[    12.912] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[    12.912] (==) fglrx(0): Center Mode is disabled 
[    12.912] (II) Loading sub module "fb"
[    12.912] (II) LoadModule: "fb"
[    12.912] (II) Loading /usr/lib/xorg/modules/libfb.so
[    12.912] (II) Module fb: vendor="X.Org Foundation"
[    12.912]     compiled for 1.9.0, module version = 1.0.0
[    12.912]     ABI class: X.Org ANSI C Emulation, version 0.4
[    12.912] (==) fglrx(0): Active stereo disabled
[    12.912] (II) Loading sub module "ddc"
[    12.912] (II) LoadModule: "ddc"
[    12.912] (II) Module "ddc" already built-in
[    13.443] (II) fglrx(0): Finished Initialize PPLIB!
[    13.450] (II) fglrx(0): Output DFP1 has no monitor section
[    13.450] (II) fglrx(0): Output DFP2 has no monitor section
[    13.450] (II) fglrx(0): Output CRT1 has no monitor section
[    13.450] (II) fglrx(0): Output CRT2 has no monitor section
[    13.450] (II) Loading sub module "ddc"
[    13.450] (II) LoadModule: "ddc"
[    13.450] (II) Module "ddc" already built-in
[    13.450] (II) fglrx(0): Connected Display0: CRT2
[    13.450] (II) fglrx(0): Display0 EDID data ---------------------------
[    13.450] (II) fglrx(0): Manufacturer: GSM  Model: 4e9d  Serial#: 2632
[    13.450] (II) fglrx(0): Year: 2000  Week: 2
[    13.450] (II) fglrx(0): EDID Version: 1.3
[    13.450] (II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    13.450] (II) fglrx(0): Sync:  Separate  SyncOnGreen
[    13.450] (II) fglrx(0): Max Image Size [cm]: horiz.: 45  vert.: 25
[    13.450] (II) fglrx(0): Gamma: 2.20
[    13.450] (II) fglrx(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    13.450] (II) fglrx(0): First detailed timing is preferred mode
[    13.450] (II) fglrx(0): redX: 0.646 redY: 0.334   greenX: 0.302 greenY: 0.615
[    13.450] (II) fglrx(0): blueX: 0.146 blueY: 0.066   whiteX: 0.312 whiteY: 0.328
[    13.450] (II) fglrx(0): Supported established timings:
[    13.450] (II) fglrx(0): 720x400@70Hz
[    13.450] (II) fglrx(0): 640x480@60Hz
[    13.450] (II) fglrx(0): 640x480@75Hz
[    13.450] (II) fglrx(0): 800x600@56Hz
[    13.450] (II) fglrx(0): 800x600@60Hz
[    13.450] (II) fglrx(0): 800x600@75Hz
[    13.450] (II) fglrx(0): 832x624@75Hz
[    13.450] (II) fglrx(0): 1024x768@60Hz
[    13.450] (II) fglrx(0): 1024x768@75Hz
[    13.450] (II) fglrx(0): 1152x864@75Hz
[    13.450] (II) fglrx(0): Manufacturer's mask: 0
[    13.450] (II) fglrx(0): Supported standard timings:
[    13.450] (II) fglrx(0): #0: hsize: 1600  vsize 900  refresh: 60  vid: 49321
[    13.450] (II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    13.450] (II) fglrx(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    13.450] (II) fglrx(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    13.450] (II) fglrx(0): Supported detailed timing:
[    13.450] (II) fglrx(0): clock: 108.0 MHz   Image Size:  443 x 249 mm
[    13.451] (II) fglrx(0): h_active: 1600  h_sync: 1624  h_sync_end 1704 h_blank_end 1800 h_border: 0
[    13.451] (II) fglrx(0): v_active: 900  v_sync: 901  v_sync_end 904 v_blanking: 1000 v_border: 0
[    13.451] (II) fglrx(0): Supported detailed timing:
[    13.451] (II) fglrx(0): clock: 108.0 MHz   Image Size:  443 x 249 mm
[    13.451] (II) fglrx(0): h_active: 1600  h_sync: 1624  h_sync_end 1704 h_blank_end 1800 h_border: 0
[    13.451] (II) fglrx(0): v_active: 900  v_sync: 901  v_sync_end 904 v_blanking: 1000 v_border: 0
[    13.451] (II) fglrx(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 155 MHz
[    13.451] (II) fglrx(0): Monitor name: W2043
[    13.451] (II) fglrx(0): EDID (in hex):
[    13.451] (II) fglrx(0):     00ffffffffffff001e6d9d4e480a0000
[    13.451] (II) fglrx(0):     020a01036a2d1978eaa680a5554d9d25
[    13.451] (II) fglrx(0):     115054a76a80a9c081808140714f0101
[    13.451] (II) fglrx(0):     010101010101302a40c8608464301850
[    13.451] (II) fglrx(0):     1300bbf91000001e302a40c860846430
[    13.451] (II) fglrx(0):     18501300bbf91000001e000000fd0038
[    13.451] (II) fglrx(0):     4b1e530f000a202020202020000000fc
[    13.451] (II) fglrx(0):     0057323034330a202020202020200076
[    13.451] (II) fglrx(0): End of Display0 EDID data --------------------
[    13.686] (II) fglrx(0): Output DFP1 disconnected
[    13.686] (II) fglrx(0): Output DFP2 disconnected
[    13.686] (II) fglrx(0): Output CRT1 disconnected
[    13.686] (II) fglrx(0): Output CRT2 connected
[    13.686] (II) fglrx(0): Using exact sizes for initial modes
[    13.686] (II) fglrx(0): Output CRT2 using initial mode 1600x900
[    13.686] (II) fglrx(0): DPI set to (96, 96)
[    13.686] (II) fglrx(0): Adapter ATI Radeon HD 4300/4500 Series has 2 configurable heads and 1 displays connected.
[    13.686] (==) fglrx(0):  PseudoColor visuals disabled
[    13.686] (II) Loading sub module "ramdac"
[    13.686] (II) LoadModule: "ramdac"
[    13.686] (II) Module "ramdac" already built-in
[    13.686] (==) fglrx(0): NoDRI = NO
[    13.686] (==) fglrx(0): Capabilities: 0x00000000
[    13.687] (==) fglrx(0): CapabilitiesEx: 0x00000000
[    13.687] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[    13.687] (==) fglrx(0): UseFastTLS=0
[    13.687] (==) fglrx(0): BlockSignalsOnLock=1
[    13.687] (--) Depth 24 pixmap format is 32 bpp
[    13.687] (II) Loading extension ATIFGLRXDRI
[    13.687] (II) fglrx(0): doing swlDriScreenInit
[    13.687] (II) fglrx(0): swlDriScreenInit for fglrx driver
[    13.688] ukiDynamicMajor: found major device number 250
[    13.688] ukiDynamicMajor: found major device number 250
[    13.688] ukiDynamicMajor: found major device number 250
[    13.688] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    13.688] ukiOpenDevice: node name is /dev/ati/card0
[    13.688] ukiOpenDevice: open result is 17, (OK)
[    13.688] ukiOpenByBusid: ukiOpenMinor returns 17
[    13.688] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    13.688] (II) fglrx(0): [uki] DRM interface version 1.0
[    13.688] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:1:0:0"
[    13.688] (II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
[    13.688] (II) fglrx(0): [uki] mapped SAREA 0x2000 to 0xb7796000
[    13.688] (II) fglrx(0): [uki] framebuffer handle = 0x3000
[    13.688] (II) fglrx(0): [uki] added 1 reserved context for kernel
[    13.688] (II) fglrx(0): swlDriScreenInit done
[    13.688] (II) fglrx(0): Kernel Module Version Information:
[    13.688] (II) fglrx(0):     Name: fglrx
[    13.688] (II) fglrx(0):     Version: 8.78.30
[    13.688] (II) fglrx(0):     Date: Sep 20 2010
[    13.688] (II) fglrx(0):     Desc: ATI FireGL DRM kernel module
[    13.688] (II) fglrx(0): Kernel Module version matches driver.
[    13.688] (II) fglrx(0): Kernel Module Build Time Information:
[    13.688] (II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.35-22-generic
[    13.688] (II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
[    13.688] (II) fglrx(0):     Build-Kernel __SMP__:            yes
[    13.688] (II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
[    13.688] (II) fglrx(0): [uki] register handle = 0x00004000
[    13.699] (II) fglrx(0): Display width adjusted to to 1664 due to alignment constraints
[    13.699] (II) fglrx(0): DRI initialization successfull
[    13.699] (II) fglrx(0): FBADPhys: 0xf00000000 FBMappedSize: 0x010a8000
[    13.700] (II) fglrx(0): FBMM initialized for area (0,0)-(1664,2624)
[    13.700] (II) fglrx(0): FBMM auto alloc for area (0,0)-(1664,1664) (front color buffer - assumption)
[    13.700] (II) fglrx(0): Largest offscreen area available: 1664 x 960
[    13.700] (==) fglrx(0): Backing store disabled
[    13.700] (II) Loading extension FGLRXEXTENSION
[    13.700] (==) fglrx(0): DPMS enabled
[    13.700] (II) fglrx(0): Initialized in-driver Xinerama extension
[    13.700] (**) fglrx(0): Textured Video is enabled.
[    13.700] (II) LoadModule: "glesx"
[    13.700] (II) Loading /usr/lib/xorg/extra-modules/modules/glesx.so
[    13.701] (II) Module glesx: vendor="X.Org Foundation"
[    13.701]     compiled for 1.8.99.905, module version = 1.0.0
[    13.701] (II) Loading extension GLESX
[    13.701] (II) fglrx(0): GLESX enableFlags = 528
[    13.701] (II) fglrx(0): GLESX is enabled
[    13.701] (II) fglrx(0): Acceleration enabled
[    13.701] (II) LoadModule: "amdxmm"
[    13.701] (II) Loading /usr/lib/xorg/extra-modules/modules/amdxmm.so
[    13.701] (II) Module amdxmm: vendor="X.Org Foundation"
[    13.701]     compiled for 1.8.99.905, module version = 1.0.0
[    13.702] (II) Loading extension AMDXVOPL
[    13.702] (II) fglrx(0): UVD2 feature is available
[    13.704] (II) fglrx(0): Enable composite support successfully
[    13.704] (II) fglrx(0): X context handle = 0x1
[    13.704] (II) fglrx(0): [DRI] installation complete
[    13.704] (==) fglrx(0): Silken mouse enabled
[    13.704] (==) fglrx(0): Using HW cursor of display infrastructure!
[    13.704] (II) fglrx(0): Disabling in-server RandR and enabling in-driver RandR 1.2.
[    13.806] (--) RandR disabled
[    13.807] (II) Initializing built-in extension Generic Event Extension
[    13.807] (II) Initializing built-in extension SHAPE
[    13.807] (II) Initializing built-in extension MIT-SHM
[    13.807] (II) Initializing built-in extension XInputExtension
[    13.807] (II) Initializing built-in extension XTEST
[    13.807] (II) Initializing built-in extension BIG-REQUESTS
[    13.807] (II) Initializing built-in extension SYNC
[    13.807] (II) Initializing built-in extension XKEYBOARD
[    13.807] (II) Initializing built-in extension XC-MISC
[    13.807] (II) Initializing built-in extension SECURITY
[    13.807] (II) Initializing built-in extension XINERAMA
[    13.807] (II) Initializing built-in extension XFIXES
[    13.807] (II) Initializing built-in extension RENDER
[    13.807] (II) Initializing built-in extension RANDR
[    13.807] (II) Initializing built-in extension COMPOSITE
[    13.807] (II) Initializing built-in extension DAMAGE
[    13.807] (II) Initializing built-in extension GESTURE
[    13.823] ukiDynamicMajor: found major device number 250
[    13.823] ukiDynamicMajor: found major device number 250
[    13.823] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    13.823] ukiOpenDevice: node name is /dev/ati/card0
[    13.823] ukiOpenDevice: open result is 18, (OK)
[    13.823] ukiOpenByBusid: ukiOpenMinor returns 18
[    13.823] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    13.884] (II) AIGLX: Loaded and initialized /usr/lib/dri/fglrx_dri.so
[    13.884] (II) GLX: Initialized DRI GL provider for screen 0
[    13.884] (II) fglrx(0): Enable the clock gating!
[    13.884] (II) fglrx(0): Setting screen physical size to 423 x 238
[    13.909] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    13.915] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    13.915] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    13.915] (II) LoadModule: "evdev"
[    13.916] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.916] (II) Module evdev: vendor="X.Org Foundation"
[    13.916]     compiled for 1.9.0, module version = 2.3.2
[    13.916]     Module class: X.Org XInput Driver
[    13.916]     ABI class: X.Org XInput driver, version 11.0
[    13.916] (**) Power Button: always reports core events
[    13.916] (**) Power Button: Device: "/dev/input/event2"
[    13.932] (II) Power Button: Found keys
[    13.932] (II) Power Button: Configuring as keyboard
[    13.932] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    13.932] (**) Option "xkb_rules" "evdev"
[    13.932] (**) Option "xkb_model" "pc105"
[    13.932] (**) Option "xkb_layout" "us"
[    13.933] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    13.933] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    13.933] (**) Power Button: always reports core events
[    13.933] (**) Power Button: Device: "/dev/input/event1"
[    13.948] (II) Power Button: Found keys
[    13.948] (II) Power Button: Configuring as keyboard
[    13.948] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    13.948] (**) Option "xkb_rules" "evdev"
[    13.948] (**) Option "xkb_model" "pc105"
[    13.948] (**) Option "xkb_layout" "us"
[    13.948] (II) config/udev: Adding input device Sleep Button (/dev/input/event0)
[    13.948] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    13.948] (**) Sleep Button: always reports core events
[    13.948] (**) Sleep Button: Device: "/dev/input/event0"
[    13.964] (II) Sleep Button: Found keys
[    13.964] (II) Sleep Button: Configuring as keyboard
[    13.964] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    13.964] (**) Option "xkb_rules" "evdev"
[    13.964] (**) Option "xkb_model" "pc105"
[    13.964] (**) Option "xkb_layout" "us"
[    13.965] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event3)
[    13.965] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    13.965] (**) Logitech USB Receiver: always reports core events
[    13.965] (**) Logitech USB Receiver: Device: "/dev/input/event3"
[    13.980] (II) Logitech USB Receiver: Found keys
[    13.980] (II) Logitech USB Receiver: Configuring as keyboard
[    13.980] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    13.980] (**) Option "xkb_rules" "evdev"
[    13.980] (**) Option "xkb_model" "pc105"
[    13.980] (**) Option "xkb_layout" "us"
[    13.980] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event4)
[    13.980] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[    13.980] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    13.980] (**) Logitech USB Receiver: always reports core events
[    13.980] (**) Logitech USB Receiver: Device: "/dev/input/event4"
[    13.996] (II) Logitech USB Receiver: Found 20 mouse buttons
[    13.996] (II) Logitech USB Receiver: Found scroll wheel(s)
[    13.996] (II) Logitech USB Receiver: Found relative axes
[    13.996] (II) Logitech USB Receiver: Found x and y relative axes
[    13.996] (II) Logitech USB Receiver: Found absolute axes
[    13.996] (II) evdev-grail: failed to open grail, no gesture support
[    13.996] (II) Logitech USB Receiver: Found keys
[    13.996] (II) Logitech USB Receiver: Configuring as mouse
[    13.996] (II) Logitech USB Receiver: Configuring as keyboard
[    13.996] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    13.996] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    13.996] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    13.996] (**) Option "xkb_rules" "evdev"
[    13.996] (**) Option "xkb_model" "pc105"
[    13.996] (**) Option "xkb_layout" "us"
[    13.996] (II) Logitech USB Receiver: initialized for relative axes.
[    13.996] (WW) Logitech USB Receiver: ignoring absolute axes.
[    13.996] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse0)
[    13.996] (II) No input driver/identifier specified (ignoring)
[    13.997] (II) config/udev: Adding input device Sirius USB2.0 Camera (/dev/input/event5)
[    13.997] (**) Sirius USB2.0 Camera: Applying InputClass "evdev keyboard catchall"
[    13.997] (**) Sirius USB2.0 Camera: always reports core events
[    13.997] (**) Sirius USB2.0 Camera: Device: "/dev/input/event5"
[    14.016] (II) Sirius USB2.0 Camera: Found keys
[    14.016] (II) Sirius USB2.0 Camera: Configuring as keyboard
[    14.016] (II) XINPUT: Adding extended input device "Sirius USB2.0 Camera" (type: KEYBOARD)
[    14.016] (**) Option "xkb_rules" "evdev"
[    14.016] (**) Option "xkb_model" "pc105"
[    14.016] (**) Option "xkb_layout" "us"
[    14.086] (II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
[    14.622] (II) fglrx(0): EDID vendor "GSM", prod id 20125
[    14.622] (II) fglrx(0): Using EDID range info for horizontal sync
[    14.622] (II) fglrx(0): Using EDID range info for vertical refresh
[    14.622] (II) fglrx(0): Printing DDC gathered Modelines:
[    14.622] (II) fglrx(0): Modeline "1600x900"x0.0  108.00  1600 1624 1704 1800  900 901 904 1000 +hsync +vsync (60.0 kHz)
[    14.622] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    14.622] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    14.622] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    14.623] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    14.623] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    14.623] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    14.623] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    14.623] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    14.623] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    14.623] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    14.623] (II) fglrx(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz)
[    14.623] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    14.623] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    14.962] (II) fglrx(0): EDID vendor "GSM", prod id 20125
[    14.962] (II) fglrx(0): Using hsync ranges from config file
[    14.962] (II) fglrx(0): Using vrefresh ranges from config file
[    14.962] (II) fglrx(0): Printing DDC gathered Modelines:
[    14.962] (II) fglrx(0): Modeline "1600x900"x0.0  108.00  1600 1624 1704 1800  900 901 904 1000 +hsync +vsync (60.0 kHz)
[    14.962] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    14.962] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    14.962] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    14.962] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    14.962] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    14.962] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    14.962] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    14.962] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    14.962] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    14.962] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    14.962] (II) fglrx(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz)
[    14.962] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    14.962] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    15.308] (II) fglrx(0): EDID vendor "GSM", prod id 20125
[    15.309] (II) fglrx(0): Using hsync ranges from config file
[    15.309] (II) fglrx(0): Using vrefresh ranges from config file
[    15.309] (II) fglrx(0): Printing DDC gathered Modelines:
[    15.309] (II) fglrx(0): Modeline "1600x900"x0.0  108.00  1600 1624 1704 1800  900 901 904 1000 +hsync +vsync (60.0 kHz)
[    15.309] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    15.309] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    15.309] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    15.309] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    15.309] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    15.309] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    15.309] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    15.309] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    15.309] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    15.309] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    15.309] (II) fglrx(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz)
[    15.309] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    15.309] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    15.648] (II) fglrx(0): EDID vendor "GSM", prod id 20125
[    15.648] (II) fglrx(0): Using hsync ranges from config file
[    15.648] (II) fglrx(0): Using vrefresh ranges from config file
[    15.648] (II) fglrx(0): Printing DDC gathered Modelines:
[    15.648] (II) fglrx(0): Modeline "1600x900"x0.0  108.00  1600 1624 1704 1800  900 901 904 1000 +hsync +vsync (60.0 kHz)
[    15.648] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    15.648] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    15.648] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    15.648] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    15.648] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    15.648] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    15.648] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    15.648] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    15.648] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    15.648] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    15.648] (II) fglrx(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz)
[    15.648] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    15.648] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    22.788] (II) fglrx(0): EDID vendor "GSM", prod id 20125
[    22.788] (II) fglrx(0): Using hsync ranges from config file
[    22.788] (II) fglrx(0): Using vrefresh ranges from config file
[    22.788] (II) fglrx(0): Printing DDC gathered Modelines:
[    22.788] (II) fglrx(0): Modeline "1600x900"x0.0  108.00  1600 1624 1704 1800  900 901 904 1000 +hsync +vsync (60.0 kHz)
[    22.788] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    22.788] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    22.788] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    22.788] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    22.788] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    22.788] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    22.788] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    22.788] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    22.788] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    22.788] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    22.788] (II) fglrx(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz)
[    22.788] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    22.788] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    23.128] (II) fglrx(0): EDID vendor "GSM", prod id 20125
[    23.128] (II) fglrx(0): Using hsync ranges from config file
[    23.128] (II) fglrx(0): Using vrefresh ranges from config file
[    23.128] (II) fglrx(0): Printing DDC gathered Modelines:
[    23.128] (II) fglrx(0): Modeline "1600x900"x0.0  108.00  1600 1624 1704 1800  900 901 904 1000 +hsync +vsync (60.0 kHz)
[    23.128] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    23.128] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    23.128] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    23.129] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    23.129] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    23.129] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    23.129] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    23.129] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    23.129] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    23.129] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    23.129] (II) fglrx(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz)
[    23.129] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    23.129] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    23.468] (II) fglrx(0): EDID vendor "GSM", prod id 20125
[    23.468] (II) fglrx(0): Using hsync ranges from config file
[    23.468] (II) fglrx(0): Using vrefresh ranges from config file
[    23.468] (II) fglrx(0): Printing DDC gathered Modelines:
[    23.468] (II) fglrx(0): Modeline "1600x900"x0.0  108.00  1600 1624 1704 1800  900 901 904 1000 +hsync +vsync (60.0 kHz)
[    23.468] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    23.468] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    23.468] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    23.468] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    23.468] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    23.468] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    23.468] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    23.468] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    23.468] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    23.468] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    23.468] (II) fglrx(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz)
[    23.468] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    23.468] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    23.808] (II) fglrx(0): EDID vendor "GSM", prod id 20125
[    23.809] (II) fglrx(0): Using hsync ranges from config file
[    23.809] (II) fglrx(0): Using vrefresh ranges from config file
[    23.809] (II) fglrx(0): Printing DDC gathered Modelines:
[    23.809] (II) fglrx(0): Modeline "1600x900"x0.0  108.00  1600 1624 1704 1800  900 901 904 1000 +hsync +vsync (60.0 kHz)
[    23.809] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    23.809] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    23.809] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    23.809] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    23.809] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    23.809] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    23.809] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    23.809] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    23.809] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    23.809] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    23.809] (II) fglrx(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz)
[    23.809] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    23.809] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    29.422] (II) fglrx(0): EDID vendor "GSM", prod id 20125
[    29.422] (II) fglrx(0): Using hsync ranges from config file
[    29.422] (II) fglrx(0): Using vrefresh ranges from config file
[    29.422] (II) fglrx(0): Printing DDC gathered Modelines:
[    29.422] (II) fglrx(0): Modeline "1600x900"x0.0  108.00  1600 1624 1704 1800  900 901 904 1000 +hsync +vsync (60.0 kHz)
[    29.422] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    29.422] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    29.422] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    29.422] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    29.422] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    29.422] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    29.422] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    29.422] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    29.422] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    29.422] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    29.422] (II) fglrx(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz)
[    29.422] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    29.422] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
```

---

### Post by coffeecat on 2010-11-14
> **cpmman said:**
> I had a compiz problem and followed this advice which corrected it:-

[***_http://ubuntuforums.org/showpost.php?p=9964610&postcount=2_***]("http://ubuntuforums.org/showpost.php?p=9964610&postcount=2")

That's for an experimental ppa package. The OP did not say they were using a PPA repository.

> **Tapas Bose, India said:**
> @[coffeecat]("http://ubuntuforums.org/member.php?u=129087")
Thank you.
So what should I do now? How can I install open source ati driver?

Have a look at my edit to my post. You should be able to get compiz with the fglrx driver. However, if you do want to revert to the OS driver, simply disable the proprietary one in System > Adminstration > Additional Drivers.

If anything goes wrong with that (it used to in earlier versions of Ubuntu, but should be OK in Maverick), have a look here:

[https://help.ubuntu.com/community/RadeonHD#Preparation](https://help.ubuntu.com/community/RadeonHD#Preparation)

What they've omitted in that link is that you also need to remove or rename (to disable it) your /etc/X11/xorg.conf file when reverting to the OS driver. If you use Additional Drivers to dsiable the fglrx, make sure it has removed/renamed your xorg.conf otherwise the GUI will fail when you reboot.

---

### Post by Tapas Bose, India on 2010-11-14
> **coffeecat said:**
> 
However, if you do want to revert to the OS driver, simply disable the proprietary one in System > Adminstration > Additional Drivers.


So just disabling the proprietary driver revert the Os's default radeon driver back?

---

### Post by Tapas Bose, India on 2010-11-14
I have uninstalled it from System > Administration > Additional  Drivers and restart my machine. But the desktop effect giving same  information "Desktop effect could not be enabled" and compiz check boxes  (Desktop Cube, OpenGl...) not working as before.
I didn't install any driver/software after un-installing Proprietary Driver. Now what I should do?

---

### Post by Tapas Bose, India on 2010-11-14
And the ./compiz-check result now is:
```
Gathering information about your system...

 Distribution:          Ubuntu 10.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RV710 [Radeon HD 4350]
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [SKIP]
 Checking for non power of two support...          [SKIP]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [SKIP]
 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: glxinfo not installed 


```I also tried this in the mean time :
```

  sudo /usr/share/ati/fglrx-uninstall.sh  # (it does not exist)
  sudo apt-get remove --purge fglrx*
  sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
  sudo apt-get install xserver-xorg-video-ati
  sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
  sudo dpkg-reconfigure xserver-xorg

```But no gain.

---

### Post by coffeecat on 2010-11-14
You need to install the package mesa-utils to get glxinfo for compiz-check.

---

### Post by Tapas Bose, India on 2010-11-14
./compiz-check is telling me that I do not have mesa-utils installed in my machine so I installed it and then the result of ./compiz-check is:
```

tanmoy@My-Child:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 10.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RV710 [Radeon HD 4350]
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

```
Now I tried to launch CompizConfig Settings Manager from terminal by ccsm and trying to check Desktop Cube then in terminal I saw these:
```

tanmoy@My-Child:~$ ccsm
Info: No sexy-python package found, don't worry it's optional.
Backend     : ini
Integration : true
Profile     : default
Adding plugins
Initializing core options...done
Loading icons...
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/ccm/Utils.py", line 250, in ParseSettings
    plugin.Update ()
  File "compizconfig.pyx", line 766, in compizconfig.Plugin.Update
KeyError: 'active_plugins'
Initializing composite options...done
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/ccm/Widgets.py", line 1420, in enable_plugin
    if conflict.Resolve ():
  File "/usr/lib/python2.6/dist-packages/ccm/Conflicts.py", line 341, in Resolve
    if con.Resolve():
  File "/usr/lib/python2.6/dist-packages/ccm/Conflicts.py", line 341, in Resolve
    if con.Resolve():
  File "/usr/lib/python2.6/dist-packages/ccm/Conflicts.py", line 380, in Resolve
    for setting in GetSettings(self.Plugin):
  File "/usr/lib/python2.6/dist-packages/ccm/Utils.py", line 396, in GetSettings
    display = group.Display.itervalues()
  File "compizconfig.pyx", line 945, in compizconfig.Plugin.Display.__get__
  File "compizconfig.pyx", line 766, in compizconfig.Plugin.Update
KeyError: 'slow_animations_key'

```
and it behaves same as before.

---

### Post by coffeecat on 2010-11-14
Compiz-check is happy and yet the Visual Effects tab of the Appearance Preferences window won't enable compiz (if I read you correctly). Strange. Long shot this, but do you have onboard graphics and is the Radeon HD4350 a PCIe card? If so, check that the onboard is disabled in the BIOS. Most BIOS's autodisable the motherboard graphics when you plug a card in but I had a machine that gave me some very strange trouble until I discovered that I had to disable the onboard graphics myself.

---

### Post by Tapas Bose, India on 2010-11-14
> **coffeecat said:**
> Compiz-check is happy and yet the Visual Effects tab of the Appearance Preferences window won't enable compiz (if I read you correctly). Strange. Long shot this, but do you have onboard graphics and is the Radeon HD4350 a PCIe card? If so, check that the onboard is disabled in the BIOS. Most BIOS's autodisable the motherboard graphics when you plug a card in but I had a machine that gave me some very strange trouble until I discovered that I had to disable the onboard graphics myself.
I am too newbie to set BIOS, but I as I have dual boot with Windows-7 so I can guess that Graphics Card working well. Is the problem created on up-gradation to Ubuntu 10.10? Is fresh installation of Maverick Meerkat can solve it?

---

### Post by coffeecat on 2010-11-14
> **Tapas Bose, India said:**
> I am too newbie to set BIOS, but I as I have dual boot with Windows-7 so I can guess that Graphics Card working well. Is the problem created on up-gradation to Ubuntu 10.10? Is fresh installation of Maverick Meerkat can solve it?

As far as the graphics card is concerned that fact that Windows 7 is happy may not be relevant. The problem I had with another machine was in Linux only and was as a result of the Linux xserver (the underpinnings to the GUI) and/or the Linux graphics driver getting confused when both graphics chipsets were enabled in the BIOS. Do you know if your computer motherboard has onboard graphics? Or let's take one step back. I was assuming yours is a desktop computer. Is it a desktop or laptop?

As far as a fresh installation of Maverick is concerned, it is easy to find out without having to do a fresh install first. You'll need a Maverick live CD. Boot up with the live CD and go to the desktop rather than the installer. Once you're in the desktop it will have automatically enabled the open-source ATI driver. If my experience is anything to go by with the same graphics chip as you it will have automatically  enabled compiz too. Open System > Preferences > Appearance > Visual Effects Tab. Which setting is it at? If 'None' can you enable any of the others? Try 'Extra'. That gives you wobbly windows which is a quick check to see if compiz is working.

If you can't enable compiz in the live session with your machine then that means the problem must be in your hardware. To be clear: I can get compiz with the default open-source driver in Maverick with the same ATI graphics, in both the live-CD session and my HD installation.

---

### Post by Tapas Bose, India on 2010-11-14
> **coffeecat said:**
> As far as the graphics card is concerned that fact that Windows 7 is happy may not be relevant. The problem I had with another machine was in Linux only and was as a result of the Linux xserver (the underpinnings to the GUI) and/or the Linux graphics driver getting confused when both graphics chipsets were enabled in the BIOS. Do you know if your computer motherboard has onboard graphics? Or let's take one step back. I was assuming yours is a desktop computer. Is it a desktop or laptop?

As far as a fresh installation of Maverick is concerned, it is easy to find out without having to do a fresh install first. You'll need a Maverick live CD. Boot up with the live CD and go to the desktop rather than the installer. Once you're in the desktop it will have automatically enabled the open-source ATI driver. If my experience is anything to go by with the same graphics chip as you it will have automatically  enabled compiz too. Open System > Preferences > Appearance > Visual Effects Tab. Which setting is it at? If 'None' can you enable any of the others? Try 'Extra'. That gives you wobbly windows which is a quick check to see if compiz is working.

If you can't enable compiz in the live session with your machine then that means the problem must be in your hardware. To be clear: I can get compiz with the default open-source driver in Maverick with the same ATI graphics, in both the live-CD session and my HD installation.
Okay I will try and inform here as I don't have Live CD now in hand. Thank you for giving suggestions.

---

### Post by Tapas Bose, India on 2010-11-14
> **coffeecat said:**
> As far as the graphics card is concerned that fact that Windows 7 is happy may not be relevant. The problem I had with another machine was in Linux only and was as a result of the Linux xserver (the underpinnings to the GUI) and/or the Linux graphics driver getting confused when both graphics chipsets were enabled in the BIOS. Do you know if your computer motherboard has onboard graphics? Or let's take one step back. I was assuming yours is a desktop computer. Is it a desktop or laptop?

As far as a fresh installation of Maverick is concerned, it is easy to find out without having to do a fresh install first. You'll need a Maverick live CD. Boot up with the live CD and go to the desktop rather than the installer. Once you're in the desktop it will have automatically enabled the open-source ATI driver. If my experience is anything to go by with the same graphics chip as you it will have automatically  enabled compiz too. Open System > Preferences > Appearance > Visual Effects Tab. Which setting is it at? If 'None' can you enable any of the others? Try 'Extra'. That gives you wobbly windows which is a quick check to see if compiz is working.

If you can't enable compiz in the live session with your machine then that means the problem must be in your hardware. To be clear: I can get compiz with the default open-source driver in Maverick with the same ATI graphics, in both the live-CD session and my HD installation.
I am in Desktop. I will try and inform here as I don't have Live CD now in hand. Thank you for giving suggestions.

---

