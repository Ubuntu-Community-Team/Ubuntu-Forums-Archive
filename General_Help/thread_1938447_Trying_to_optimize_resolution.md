---
title: "Trying to optimize resolution"
date: 2012-03-09
forum: General Help
---

### Post by sffvba[e0rt on 2012-03-09
[COLOR="Red"]**NOTE: See the last two pages for a solution that worked for me... all the other pages for ways that didn't work for me but may still be a solution to you :)**[/COLOR]

Hi,

I am currently running 12.04 [s](but my question will pertain to any of the releases of Ubuntu so I don't think posting in +1 is needed).[/s]

I have a Radeon HD 6850 and the drivers coming with Ubuntu where not working properly so I downloaded and installed the drivers from the AMD/ATI site.  Installed and working at the moment I am glad to say.

My issue is that I am getting a maximum resolution (I can use) of 1600x900 and my screen (LG Flatron E2251) has a naitive resolution of 1920x1080.  I was finally able to achieve this in Windows by using a setting in the Catalyst Control Center (which was set to limit the maximum resolution in Windows).  There is no such option in the Catalyst Control Center for Ubuntu.

So I started looking around and found this [site]("https://wiki.ubuntu.com/X/Config/Resolution#Adding_undetected_resolutions") - and I tried to add the resolution of 1920x1080 at a refresh rate of 60hz.

First I:

```
nlsthzn@circle:~$ cvt 1920 1080 60
# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
```

I then:

```
xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
```

Problem is on the next step:

```
nlsthzn@circle:~$ xrandr --addmode CRT1 1920x1080_60.00
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  156 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  49
  Current serial number in output stream:  50

```

Any assistance would be appreciated!


404

---

### Post by sffvba[e0rt on 2012-03-10
Bump for now trying this in Kubuntu 11.10 and getting exactly the same results...


404

---

### Post by tista on 2012-03-11
@404

Well have you already tried this command?:
```
sudo aticonfig --initial
```

above command might be able to make a new config file to fit your hardware...;)

Regards,
Tista

---

### Post by sffvba[e0rt on 2012-03-11
> **tista said:**
> @404

Well have you already tried this command?:
```
sudo aticonfig --initial
```

above command might be able to make a new config file to fit your hardware...;)

Regards,
Tista

Hi,

Now on Kubuntu 12.04 (finally realized I had to remove the ATI drivers from AMD themselves and install the driver that comes with Kubuntu to be able to successfully boot).

Tried what I tried in OP and getting the same error.  Tried running **sudo aticonfig --initial** and no luck.  Made some edits to xorg.conf (not sure what to do there but tried what made sense) and still no luck getting the resolution up :/...


404

---

### Post by sffvba[e0rt on 2012-03-12
BUMP for asking if this thread would be better suited elsewhere?


404

---

### Post by ELD on 2012-03-12
I don't know if it still works nowadays but i read a blog post about resolution problems before, apparently you can add that resolution to the xorg file?

---

### Post by sffvba[e0rt on 2012-03-14
> **ELD said:**
> I don't know if it still works nowadays but i read a blog post about resolution problems before, apparently you can add that resolution to the xorg file?

BUMP for having tried that before... and for moving this from +1


404

---

### Post by sffvba[e0rt on 2012-05-05
Greetings again...  I decided to let this issue sleep until the release of 12.04 so now after a fresh install I can say that it still remains.

So again I appeal to all of the guru's out there to please assist me in getting my resolution up to its native 1920x1080.

The highest I can select in the Catalyst Control Center is 1600x1200 (which will let my screen show an "out of range" error with no way of increasing it to anything higher).

If I install the latest drivers from ATI I can't set the resolution from the Catalyst Control Center at all and it is not detected properly there.

Help me please :KS


404

---

### Post by papibe on 2012-05-05
Hi not found.

I don't have much experience with ATI/AMD cards (though I had lots of wrestles with Nvidia cards), but there may be some clues on the Xorg log (/var/log/Xorg.0.log).

Could you pastebin it so we can take a look?

Kind Regards.

---

### Post by sffvba[e0rt on 2012-05-05
> **papibe said:**
> Hi not found.

I don't have much experience with ATI/AMD cards (though I had lots of wrestles with Nvidia cards), but there may be some clues on the Xorg log (/var/log/Xorg.0.log).

Could you pastebin it so we can take a look?

Kind Regards.

Hi,

Not at home right now (so I will post it much later)... should I post this log after trying xrandr or just as is (I have a clean install again)?


Thanks
404

---

### Post by papibe on 2012-05-05
Right after a regular boot will do fine.

Regards.

---

### Post by sffvba[e0rt on 2012-05-05
/var/log/Xorg.0.log

```
[    15.748] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    15.748] X Protocol Version 11, Revision 0
[    15.748] Build Operating System: Linux 2.6.42-23-generic i686 Ubuntu
[    15.748] Current Operating System: Linux circle 3.2.0-24-generic-pae #37-Ubuntu SMP Wed Apr 25 10:47:59 UTC 2012 i686
[    15.748] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-24-generic-pae root=UUID=e86df17f-0c9e-46f2-8dbc-518ff8a39fe2 ro quiet splash vt.handoff=7
[    15.748] Build Date: 20 April 2012  05:12:21AM
[    15.748] xorg-server 2:1.11.4-0ubuntu10.1 (For technical support please see http://www.ubuntu.com/support) 
[    15.748] Current version of pixman: 0.24.4
[    15.748] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    15.748] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    15.748] (==) Log file: "/var/log/Xorg.0.log", Time: Sat May  5 11:42:47 2012
[    15.763] (==) Using config file: "/etc/X11/xorg.conf"
[    15.763] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    16.149] (==) ServerLayout "aticonfig Layout"
[    16.149] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[    16.149] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[    16.184] (**) |   |-->Device "aticonfig-Device[0]-0"
[    16.184] (==) Automatically adding devices
[    16.184] (==) Automatically enabling devices
[    16.221] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    16.221] 	Entry deleted from font path.
[    16.221] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    16.221] 	Entry deleted from font path.
[    16.221] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    16.221] 	Entry deleted from font path.
[    16.256] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    16.256] 	Entry deleted from font path.
[    16.256] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    16.256] 	Entry deleted from font path.
[    16.256] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    16.256] 	Entry deleted from font path.
[    16.256] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    16.256] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    16.256] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    16.271] (II) Loader magic: 0xb774d5a0
[    16.272] (II) Module ABI versions:
[    16.272] 	X.Org ANSI C Emulation: 0.4
[    16.272] 	X.Org Video Driver: 11.0
[    16.272] 	X.Org XInput driver : 16.0
[    16.272] 	X.Org Server Extension : 6.0
[    16.272] (--) PCI:*(0:1:0:0) 1002:6739:174b:174b rev 0, Mem @ 0xe0000000/268435456, 0xfe620000/131072, I/O @ 0x0000e000/256, BIOS @ 0x????????/131072
[    16.272] (II) Open ACPI successful (/var/run/acpid.socket)
[    16.272] (II) "extmod" will be loaded by default.
[    16.272] (II) "dbe" will be loaded by default.
[    16.272] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    16.272] (II) "record" will be loaded by default.
[    16.272] (II) "dri" will be loaded by default.
[    16.272] (II) "dri2" will be loaded by default.
[    16.272] (II) LoadModule: "glx"
[    16.357] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/modules/extensions/libglx.so
[    16.390] (II) Module glx: vendor="Advanced Micro Devices, Inc."
[    16.390] 	compiled for 6.9.0, module version = 1.0.0
[    16.390] (II) Loading extension GLX
[    16.390] (II) LoadModule: "extmod"
[    16.462] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    16.474] (II) Module extmod: vendor="X.Org Foundation"
[    16.474] 	compiled for 1.11.3, module version = 1.0.0
[    16.474] 	Module class: X.Org Server Extension
[    16.474] 	ABI class: X.Org Server Extension, version 6.0
[    16.474] (II) Loading extension MIT-SCREEN-SAVER
[    16.474] (II) Loading extension XFree86-VidModeExtension
[    16.474] (II) Loading extension XFree86-DGA
[    16.475] (II) Loading extension DPMS
[    16.475] (II) Loading extension XVideo
[    16.475] (II) Loading extension XVideo-MotionCompensation
[    16.475] (II) Loading extension X-Resource
[    16.475] (II) LoadModule: "dbe"
[    16.475] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    16.491] (II) Module dbe: vendor="X.Org Foundation"
[    16.491] 	compiled for 1.11.3, module version = 1.0.0
[    16.491] 	Module class: X.Org Server Extension
[    16.491] 	ABI class: X.Org Server Extension, version 6.0
[    16.491] (II) Loading extension DOUBLE-BUFFER
[    16.491] (II) LoadModule: "record"
[    16.491] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    16.492] (II) Module record: vendor="X.Org Foundation"
[    16.492] 	compiled for 1.11.3, module version = 1.13.0
[    16.492] 	Module class: X.Org Server Extension
[    16.492] 	ABI class: X.Org Server Extension, version 6.0
[    16.492] (II) Loading extension RECORD
[    16.492] (II) LoadModule: "dri"
[    16.492] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    16.548] (II) Module dri: vendor="X.Org Foundation"
[    16.548] 	compiled for 1.11.3, module version = 1.0.0
[    16.548] 	ABI class: X.Org Server Extension, version 6.0
[    16.548] (II) Loading extension XFree86-DRI
[    16.548] (II) LoadModule: "dri2"
[    16.549] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    16.650] (II) Module dri2: vendor="X.Org Foundation"
[    16.650] 	compiled for 1.11.3, module version = 1.2.0
[    16.650] 	ABI class: X.Org Server Extension, version 6.0
[    16.650] (II) Loading extension DRI2
[    16.650] (II) LoadModule: "fglrx"
[    16.650] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so
[    16.956] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[    16.977] 	compiled for 1.4.99.906, module version = 8.96.4
[    16.977] 	Module class: X.Org Video Driver
[    16.978] (II) Loading sub module "fglrxdrm"
[    16.978] (II) LoadModule: "fglrxdrm"
[    16.978] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    17.033] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    17.033] 	compiled for 1.4.99.906, module version = 8.96.4
[    17.048] (II) ATI Proprietary Linux Driver Version Identifier:8.96.4
[    17.048] (II) ATI Proprietary Linux Driver Release Identifier: 8.96.7                               
[    17.048] (II) ATI Proprietary Linux Driver Build Date: Mar 12 2012 13:06:47
[    17.048] (++) using VT number 7

[    17.048] (WW) Falling back to old probe method for fglrx
[    17.154] (II) Loading PCS database from /etc/ati/amdpcsdb
[    17.155] (--) Chipset Supported AMD Graphics Processor (0x6739) found
[    17.156] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
[    17.156] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[    17.156] (II) AMD Video driver is signed
[    17.156] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so
[    17.156] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    17.156] (II) fglrx(0): pEnt->device->identifier=0xb9034db8
[    17.156] (II) fglrx(0): === [xdl_xs111_atiddxPreInit] === begin
[    17.157] (II) Loading sub module "vgahw"
[    17.157] (II) LoadModule: "vgahw"
[    17.175] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    17.181] (II) Module vgahw: vendor="X.Org Foundation"
[    17.181] 	compiled for 1.11.3, module version = 0.1.0
[    17.181] 	ABI class: X.Org Video Driver, version 11.0
[    17.181] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[    17.181] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    17.181] (==) fglrx(0): Default visual is TrueColor
[    17.181] (**) fglrx(0): Option "DPMS" "true"
[    17.181] (==) fglrx(0): RGB weight 888
[    17.181] (II) fglrx(0): Using 8 bits per RGB 
[    17.181] (==) fglrx(0): Buffer Tiling is ON
[    17.182] (II) Loading sub module "fglrxdrm"
[    17.182] (II) LoadModule: "fglrxdrm"
[    17.182] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    17.182] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    17.182] 	compiled for 1.4.99.906, module version = 8.96.4
[    17.183] ukiDynamicMajor: found major device number 250
[    17.183] ukiDynamicMajor: found major device number 250
[    17.183] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    17.183] ukiOpenDevice: node name is /dev/ati/card0
[    17.183] ukiOpenDevice: open result is 12, (OK)
[    17.183] ukiOpenByBusid: ukiOpenMinor returns 12
[    17.183] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    17.183] (**) fglrx(0): NoAccel = NO
[    17.183] (**) fglrx(0): ATI 2D Acceleration Architecture enabled
[    17.183] (--) fglrx(0): Chipset: "AMD Radeon HD 6800 Series " (Chipset = 0x6739)
[    17.183] (--) fglrx(0): (PciSubVendor = 0x174b, PciSubDevice = 0x174b)
[    17.183] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
[    17.183] (--) fglrx(0): Linear framebuffer (phys) at 0xe0000000
[    17.183] (--) fglrx(0): MMIO registers at 0xfe620000
[    17.183] (--) fglrx(0): I/O port at 0x0000e000
[    17.183] (==) fglrx(0): ROM-BIOS at 0x000c0000
[    17.197] (II) fglrx(0): AC Adapter is used
[    17.216] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
[    17.217] (II) Loading sub module "vbe"
[    17.217] (II) LoadModule: "vbe"
[    17.217] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    17.218] (II) Module vbe: vendor="X.Org Foundation"
[    17.218] 	compiled for 1.11.3, module version = 1.1.0
[    17.218] 	ABI class: X.Org Video Driver, version 11.0
[    17.218] (II) fglrx(0): VESA BIOS detected
[    17.218] (II) fglrx(0): VESA VBE Version 3.0
[    17.218] (II) fglrx(0): VESA VBE Total Mem: 16384 kB
[    17.218] (II) fglrx(0): VESA VBE OEM: AMD ATOMBIOS
[    17.218] (II) fglrx(0): VESA VBE OEM Software Rev: 13.12
[    17.218] (II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2010, AMD Technologies Inc. 
[    17.218] (II) fglrx(0): VESA VBE OEM Product: BARTS
[    17.218] (II) fglrx(0): VESA VBE OEM Product Rev: 01.00
[    17.254] (II) fglrx(0): ATI Video BIOS revision 9 or later detected
[    17.254] (--) fglrx(0): Video RAM: 1048576 kByte, Type: GDDR5
[    17.254] (II) fglrx(0): PCIE card detected
[    17.254] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[    17.254] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[    17.259] (II) fglrx(0): Using adapter: 1:0.0.
[    17.287] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x40000000)
[    17.445] (II) fglrx(0): Interrupt handler installed at IRQ 56.
[    17.445] (II) fglrx(0): RandR 1.2 support is enabled!
[    17.445] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[    17.445] (==) fglrx(0): Center Mode is disabled 
[    17.445] (II) Loading sub module "fb"
[    17.445] (II) LoadModule: "fb"
[    17.445] (II) Loading /usr/lib/xorg/modules/libfb.so
[    17.500] (II) Module fb: vendor="X.Org Foundation"
[    17.500] 	compiled for 1.11.3, module version = 1.0.0
[    17.500] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    17.500] (II) Loading sub module "ddc"
[    17.500] (II) LoadModule: "ddc"
[    17.500] (II) Module "ddc" already built-in
[    17.816] (II) fglrx(0): Finished Initialize PPLIB!
[    17.818] (II) fglrx(0): Output DFP1 using monitor section aticonfig-Monitor[0]-0
[    17.818] (II) fglrx(0): Output DFP2 has no monitor section
[    17.818] (II) fglrx(0): Output DFP3 has no monitor section
[    17.818] (II) fglrx(0): Output DFP4 has no monitor section
[    17.818] (II) fglrx(0): Output DFP5 has no monitor section
[    17.818] (II) fglrx(0): Output DFP6 has no monitor section
[    17.818] (II) fglrx(0): Output DFP7 has no monitor section
[    17.818] (II) fglrx(0): Output CRT1 has no monitor section
[    17.818] (II) Loading sub module "ddc"
[    17.818] (II) LoadModule: "ddc"
[    17.818] (II) Module "ddc" already built-in
[    17.818] (II) fglrx(0): Connected Display0: CRT1
[    17.818] (II) fglrx(0):  Display0: Failed to get EDID information. 
[    17.818] (II) fglrx(0): EDID for output DFP1
[    17.818] (II) fglrx(0): EDID for output DFP2
[    17.818] (II) fglrx(0): EDID for output DFP3
[    17.818] (II) fglrx(0): EDID for output DFP4
[    17.818] (II) fglrx(0): EDID for output DFP5
[    17.818] (II) fglrx(0): EDID for output DFP6
[    17.818] (II) fglrx(0): EDID for output DFP7
[    17.818] (II) fglrx(0): Cannot get EDID information for CRT1
[    17.818] (II) fglrx(0): EDID for output CRT1
[    17.818] (II) fglrx(0): Not using mode "640x350" (vrefresh out of range)
[    17.818] (II) fglrx(0): Not using mode "640x400" (vrefresh out of range)
[    17.818] (II) fglrx(0): Not using mode "720x400" (vrefresh out of range)
[    17.818] (II) fglrx(0): Not using mode "640x480" (vrefresh out of range)
[    17.818] (II) fglrx(0): Not using mode "640x480" (vrefresh out of range)
[    17.818] (II) fglrx(0): Not using mode "640x480" (vrefresh out of range)
[    17.818] (II) fglrx(0): Not using mode "800x600" (vrefresh out of range)
[    17.818] (II) fglrx(0): Not using mode "800x600" (vrefresh out of range)
[    17.818] (II) fglrx(0): Not using mode "800x600" (vrefresh out of range)
[    17.818] (II) fglrx(0): Not using mode "800x600" (vrefresh out of range)
[    17.818] (II) fglrx(0): Not using mode "800x600" (vrefresh out of range)
[    17.818] (II) fglrx(0): Not using mode "848x480" (unknown reason)
[    17.818] (II) fglrx(0): Not using mode "1024x768i" (vrefresh out of range)
[    17.818] (II) fglrx(0): Not using mode "1024x768" (vrefresh out of range)
[    17.818] (II) fglrx(0): Not using mode "1024x768" (vrefresh out of range)
[    17.818] (II) fglrx(0): Not using mode "1024x768" (vrefresh out of range)
[    17.818] (II) fglrx(0): Not using mode "1024x768" (vrefresh out of range)
[    17.818] (II) fglrx(0): Not using mode "1152x864" (vrefresh out of range)
[    17.818] (II) fglrx(0): Not using mode "1280x768" (monitor doesn't support reduced blanking)
[    17.818] (II) fglrx(0): Not using mode "1280x768" (vrefresh out of range)
[    17.818] (II) fglrx(0): Not using mode "1280x768" (vrefresh out of range)
[    17.818] (II) fglrx(0): Not using mode "1280x768" (vrefresh out of range)
[    17.818] (II) fglrx(0): Not using mode "1280x800" (monitor doesn't support reduced blanking)
[    17.818] (II) fglrx(0): Not using mode "1280x800" (vrefresh out of range)
[    17.818] (II) fglrx(0): Not using mode "1280x800" (vrefresh out of range)
[    17.818] (II) fglrx(0): Not using mode "1280x800" (vrefresh out of range)
[    17.818] (II) fglrx(0): Not using mode "1280x960" (unknown reason)
[    17.818] (II) fglrx(0): Not using mode "1280x960" (vrefresh out of range)
[    17.818] (II) fglrx(0): Not using mode "1280x960" (vrefresh out of range)
[    17.818] (II) fglrx(0): Not using mode "1280x1024" (vrefresh out of range)
[    17.818] (II) fglrx(0): Not using mode "1280x1024" (vrefresh out of range)
[    17.818] (II) fglrx(0): Not using mode "1280x1024" (vrefresh out of range)
[    17.818] (II) fglrx(0): Not using mode "1360x768" (vrefresh out of range)
[    17.818] (II) fglrx(0): Not using mode "1400x1050" (monitor doesn't support reduced blanking)
[    17.818] (II) fglrx(0): Not using mode "1400x1050" (unknown reason)
[    17.818] (II) fglrx(0): Not using mode "1400x1050" (vrefresh out of range)
[    17.818] (II) fglrx(0): Not using mode "1400x1050" (vrefresh out of range)
[    17.818] (II) fglrx(0): Not using mode "1400x1050" (vrefresh out of range)
[    17.818] (II) fglrx(0): Not using mode "1440x900" (monitor doesn't support reduced blanking)
[    17.818] (II) fglrx(0): Not using mode "1440x900" (vrefresh out of range)
[    17.818] (II) fglrx(0): Not using mode "1440x900" (vrefresh out of range)
[    17.818] (II) fglrx(0): Not using mode "1440x900" (vrefresh out of range)
[    17.818] (II) fglrx(0): Not using mode "1600x1200" (vrefresh out of range)
[    17.818] (II) fglrx(0): Not using mode "1600x1200" (vrefresh out of range)
[    17.818] (II) fglrx(0): Not using mode "1600x1200" (vrefresh out of range)
[    17.818] (II) fglrx(0): Not using mode "1600x1200" (vrefresh out of range)
[    17.818] (II) fglrx(0): Not using mode "1600x1200" (vrefresh out of range)
[    17.818] (II) fglrx(0): Not using mode "1680x1050" (width too large for virtual size)
[    17.818] (II) fglrx(0): Not using mode "1680x1050" (width too large for virtual size)
[    17.818] (II) fglrx(0): Not using mode "1680x1050" (width too large for virtual size)
[    17.818] (II) fglrx(0): Not using mode "1680x1050" (width too large for virtual size)
[    17.818] (II) fglrx(0): Not using mode "1680x1050" (width too large for virtual size)
[    17.818] (II) fglrx(0): Not using mode "1792x1344" (width too large for virtual size)
[    17.818] (II) fglrx(0): Not using mode "1792x1344" (width too large for virtual size)
[    17.818] (II) fglrx(0): Not using mode "1792x1344" (width too large for virtual size)
[    17.818] (II) fglrx(0): Not using mode "1856x1392" (width too large for virtual size)
[    17.818] (II) fglrx(0): Not using mode "1856x1392" (width too large for virtual size)
[    17.818] (II) fglrx(0): Not using mode "1856x1392" (width too large for virtual size)
[    17.818] (II) fglrx(0): Not using mode "1920x1200" (width too large for virtual size)
[    17.818] (II) fglrx(0): Not using mode "1920x1200" (width too large for virtual size)
[    17.818] (II) fglrx(0): Not using mode "1920x1200" (width too large for virtual size)
[    17.818] (II) fglrx(0): Not using mode "1920x1200" (width too large for virtual size)
[    17.818] (II) fglrx(0): Not using mode "1920x1200" (width too large for virtual size)
[    17.818] (II) fglrx(0): Not using mode "1920x1440" (width too large for virtual size)
[    17.818] (II) fglrx(0): Not using mode "1920x1440" (width too large for virtual size)
[    17.818] (II) fglrx(0): Not using mode "1920x1440" (width too large for virtual size)
[    17.818] (II) fglrx(0): Not using mode "2560x1600" (width too large for virtual size)
[    17.818] (II) fglrx(0): Not using mode "2560x1600" (width too large for virtual size)
[    17.818] (II) fglrx(0): Not using mode "2560x1600" (width too large for virtual size)
[    17.818] (II) fglrx(0): Not using mode "2560x1600" (width too large for virtual size)
[    17.819] (II) fglrx(0): Not using mode "2560x1600" (width too large for virtual size)
[    17.819] (II) fglrx(0): Printing probed modes for output CRT1
[    17.819] (II) fglrx(0): Modeline "1600x900"x60.0  108.00  1600 1624 1704 1800  900 901 904 1000 +hsync +vsync (60.0 kHz)
[    17.819] (II) fglrx(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    17.819] (II) fglrx(0): Modeline "1400x1050"x60.0  122.61  1400 1488 1640 1880  1050 1051 1054 1087 -hsync +vsync (65.2 kHz)
[    17.819] (II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    17.819] (II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    17.819] (II) fglrx(0): Modeline "1280x960"x60.0  102.10  1280 1360 1496 1712  960 961 964 994 -hsync +vsync (59.6 kHz)
[    17.819] (II) fglrx(0): Modeline "1366x768"x60.0   85.50  1366 1436 1579 1792  768 771 774 798 +hsync +vsync (47.7 kHz)
[    17.819] (II) fglrx(0): Modeline "1360x768"x60.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz)
[    17.819] (II) fglrx(0): Modeline "1280x800"x60.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
[    17.819] (II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
[    17.819] (II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 -hsync +vsync (47.8 kHz)
[    17.819] (II) fglrx(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    17.819] (II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    17.819] (II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    17.819] (II) fglrx(0): Modeline "720x480"x60.0   27.03  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    17.819] (II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    17.819] (II) fglrx(0): Output DFP1 disconnected
[    17.819] (II) fglrx(0): Output DFP2 disconnected
[    17.819] (II) fglrx(0): Output DFP3 disconnected
[    17.819] (II) fglrx(0): Output DFP4 disconnected
[    17.819] (II) fglrx(0): Output DFP5 disconnected
[    17.819] (II) fglrx(0): Output DFP6 disconnected
[    17.819] (II) fglrx(0): Output DFP7 disconnected
[    17.819] (II) fglrx(0): Output CRT1 connected
[    17.819] (II) fglrx(0): Using user preference for initial modes
[    17.819] (II) fglrx(0): Output CRT1 using initial mode 1600x900
[    17.819] (II) fglrx(0): DPI set to (96, 96)
[    17.819] (II) fglrx(0): Eyefinity capable adapter detected.
[    17.819] (II) fglrx(0): Adapter AMD Radeon HD 6800 Series  has 6 configurable heads and 1 displays connected.
[    17.819] (==) fglrx(0):  PseudoColor visuals disabled
[    17.819] (II) Loading sub module "ramdac"
[    17.819] (II) LoadModule: "ramdac"
[    17.819] (II) Module "ramdac" already built-in
[    17.819] (==) fglrx(0): NoDRI = NO
[    17.819] (==) fglrx(0): Capabilities: 0x00000000
[    17.819] (==) fglrx(0): CapabilitiesEx: 0x00000000
[    17.819] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[    17.819] (==) fglrx(0): UseFastTLS=0
[    17.819] (==) fglrx(0): BlockSignalsOnLock=1
[    17.819] (--) Depth 24 pixmap format is 32 bpp
[    17.824] (II) Loading extension ATIFGLRXDRI
[    17.824] (II) fglrx(0): doing swlDriScreenInit
[    17.824] (II) fglrx(0): swlDriScreenInit for fglrx driver
[    17.824] ukiDynamicMajor: found major device number 250
[    17.824] ukiDynamicMajor: found major device number 250
[    17.824] ukiDynamicMajor: found major device number 250
[    17.824] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    17.824] ukiOpenDevice: node name is /dev/ati/card0
[    17.824] ukiOpenDevice: open result is 17, (OK)
[    17.824] ukiOpenByBusid: ukiOpenMinor returns 17
[    17.824] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    17.824] (II) fglrx(0): [uki] DRM interface version 1.0
[    17.824] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:1:0:0"
[    17.824] (II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
[    17.824] (II) fglrx(0): [uki] mapped SAREA 0x2000 to 0xb5f50000
[    17.824] (II) fglrx(0): [uki] framebuffer handle = 0x3000
[    17.824] (II) fglrx(0): [uki] added 1 reserved context for kernel
[    17.824] (II) fglrx(0): swlDriScreenInit done
[    17.824] (II) fglrx(0): Kernel Module Version Information:
[    17.824] (II) fglrx(0):     Name: fglrx
[    17.824] (II) fglrx(0):     Version: 8.96.4
[    17.824] (II) fglrx(0):     Date: Mar 12 2012
[    17.824] (II) fglrx(0):     Desc: ATI FireGL DRM kernel module
[    17.824] (II) fglrx(0): Kernel Module version matches driver.
[    17.824] (II) fglrx(0): Kernel Module Build Time Information:
[    17.824] (II) fglrx(0):     Build-Kernel UTS_RELEASE:        3.2.0-24-generic-pae
[    17.824] (II) fglrx(0):     Build-Kernel MODVERSIONS:        no
[    17.824] (II) fglrx(0):     Build-Kernel __SMP__:            yes
[    17.824] (II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
[    17.824] (II) fglrx(0): [uki] register handle = 0x00004000
[    17.849] (II) fglrx(0): DRI initialization successfull
[    17.853] (II) fglrx(0): FBADPhys: 0xf00000000 FBMappedSize: 0x01068000
[    17.859] (==) fglrx(0): Backing store disabled
[    17.859] (II) Loading extension FGLRXEXTENSION
[    17.859] (**) fglrx(0): DPMS enabled
[    17.859] (II) fglrx(0): Initialized in-driver Xinerama extension
[    17.859] (**) fglrx(0): Textured Video is enabled.
[    17.859] (II) LoadModule: "glesx"
[    17.859] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/modules/glesx.so
[    17.945] (II) Module glesx: vendor="X.Org Foundation"
[    17.945] 	compiled for 1.4.99.906, module version = 1.0.0
[    17.945] (II) Loading extension GLESX
[    17.945] (II) fglrx(0): GLESX enableFlags = 592
[    17.946] (II) fglrx(0): GLESX is enabled
[    17.946] (II) LoadModule: "amdxmm"
[    17.946] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/modules/amdxmm.so
[    17.954] (II) Module amdxmm: vendor="X.Org Foundation"
[    17.954] 	compiled for 1.4.99.906, module version = 2.0.0
[    17.964] (II) Loading extension AMDXVOPL
[    17.964] (II) Loading extension AMDXVBA
[    17.966] (II) fglrx(0): UVD feature is enabled(II) fglrx(0): 
[    17.967] (II) fglrx(0): Enable composite support successfully
[    17.967] (WW) fglrx(0): Option "VendorName" is not used
[    17.967] (WW) fglrx(0): Option "ModelName" is not used
[    17.967] (II) fglrx(0): X context handle = 0x1
[    17.967] (II) fglrx(0): [DRI] installation complete
[    17.968] (==) fglrx(0): Silken mouse enabled
[    17.968] (==) fglrx(0): Using HW cursor of display infrastructure!
[    17.968] (II) fglrx(0): Disabling in-server RandR and enabling in-driver RandR 1.2.
[    18.020] (--) RandR disabled
[    18.020] (II) Initializing built-in extension Generic Event Extension
[    18.020] (II) Initializing built-in extension SHAPE
[    18.020] (II) Initializing built-in extension MIT-SHM
[    18.020] (II) Initializing built-in extension XInputExtension
[    18.020] (II) Initializing built-in extension XTEST
[    18.020] (II) Initializing built-in extension BIG-REQUESTS
[    18.020] (II) Initializing built-in extension SYNC
[    18.020] (II) Initializing built-in extension XKEYBOARD
[    18.020] (II) Initializing built-in extension XC-MISC
[    18.020] (II) Initializing built-in extension SECURITY
[    18.020] (II) Initializing built-in extension XINERAMA
[    18.020] (II) Initializing built-in extension XFIXES
[    18.020] (II) Initializing built-in extension RENDER
[    18.020] (II) Initializing built-in extension RANDR
[    18.020] (II) Initializing built-in extension COMPOSITE
[    18.020] (II) Initializing built-in extension DAMAGE
[    18.066] ukiDynamicMajor: found major device number 250
[    18.066] ukiDynamicMajor: found major device number 250
[    18.066] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    18.066] ukiOpenDevice: node name is /dev/ati/card0
[    18.066] ukiOpenDevice: open result is 19, (OK)
[    18.066] ukiOpenByBusid: ukiOpenMinor returns 19
[    18.066] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    18.564] (II) AIGLX: Loaded and initialized OpenGL driver(II) GLX: Initialized DRI GL provider for screen 0
[    18.564] (II) fglrx(0): Enable the clock gating!
[    18.564] (II) fglrx(0): Setting screen physical size to 423 x 238
[    18.665] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    18.686] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    18.686] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    18.686] (II) LoadModule: "evdev"
[    18.687] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.717] (II) Module evdev: vendor="X.Org Foundation"
[    18.717] 	compiled for 1.11.3, module version = 2.7.0
[    18.717] 	Module class: X.Org XInput Driver
[    18.717] 	ABI class: X.Org XInput driver, version 16.0
[    18.717] (II) Using input driver 'evdev' for 'Power Button'
[    18.717] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.717] (**) Power Button: always reports core events
[    18.717] (**) evdev: Power Button: Device: "/dev/input/event1"
[    18.717] (--) evdev: Power Button: Vendor 0 Product 0x1
[    18.717] (--) evdev: Power Button: Found keys
[    18.717] (II) evdev: Power Button: Configuring as keyboard
[    18.717] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    18.717] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    18.717] (**) Option "xkb_rules" "evdev"
[    18.717] (**) Option "xkb_model" "pc105"
[    18.717] (**) Option "xkb_layout" "us"
[    18.718] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    18.718] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    18.718] (II) Using input driver 'evdev' for 'Power Button'
[    18.718] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.718] (**) Power Button: always reports core events
[    18.718] (**) evdev: Power Button: Device: "/dev/input/event0"
[    18.718] (--) evdev: Power Button: Vendor 0 Product 0x1
[    18.718] (--) evdev: Power Button: Found keys
[    18.718] (II) evdev: Power Button: Configuring as keyboard
[    18.718] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    18.718] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    18.718] (**) Option "xkb_rules" "evdev"
[    18.718] (**) Option "xkb_model" "pc105"
[    18.718] (**) Option "xkb_layout" "us"
[    18.718] (II) config/udev: Adding input device HD-Audio Generic HDMI/DP,pcm=3 (/dev/input/event12)
[    18.718] (II) No input driver specified, ignoring this device.
[    18.718] (II) This device may have been added with another device file.
[    18.718] (II) config/udev: Adding input device   USB Keyboard (/dev/input/event2)
[    18.718] (**)   USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    18.718] (II) Using input driver 'evdev' for '  USB Keyboard'
[    18.718] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.718] (**)   USB Keyboard: always reports core events
[    18.718] (**) evdev:   USB Keyboard: Device: "/dev/input/event2"
[    18.718] (--) evdev:   USB Keyboard: Vendor 0x4d9 Product 0x1702
[    18.718] (--) evdev:   USB Keyboard: Found keys
[    18.718] (II) evdev:   USB Keyboard: Configuring as keyboard
[    18.718] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input2/event2"
[    18.718] (II) XINPUT: Adding extended input device "  USB Keyboard" (type: KEYBOARD, id 8)
[    18.718] (**) Option "xkb_rules" "evdev"
[    18.718] (**) Option "xkb_model" "pc105"
[    18.718] (**) Option "xkb_layout" "us"
[    18.719] (II) config/udev: Adding input device   USB Keyboard (/dev/input/event3)
[    18.719] (**)   USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    18.719] (II) Using input driver 'evdev' for '  USB Keyboard'
[    18.719] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.719] (**)   USB Keyboard: always reports core events
[    18.719] (**) evdev:   USB Keyboard: Device: "/dev/input/event3"
[    18.719] (--) evdev:   USB Keyboard: Vendor 0x4d9 Product 0x1702
[    18.719] (--) evdev:   USB Keyboard: Found keys
[    18.719] (II) evdev:   USB Keyboard: Configuring as keyboard
[    18.719] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.1/input/input3/event3"
[    18.719] (II) XINPUT: Adding extended input device "  USB Keyboard" (type: KEYBOARD, id 9)
[    18.719] (**) Option "xkb_rules" "evdev"
[    18.719] (**) Option "xkb_model" "pc105"
[    18.719] (**) Option "xkb_layout" "us"
[    18.719] (II) config/udev: Adding input device La-VIEW Technology SteelSeries   (/dev/input/event4)
[    18.719] (**) La-VIEW Technology SteelSeries  : Applying InputClass "evdev pointer catchall"
[    18.719] (II) Using input driver 'evdev' for 'La-VIEW Technology SteelSeries  '
[    18.719] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.719] (**) La-VIEW Technology SteelSeries  : always reports core events
[    18.719] (**) evdev: La-VIEW Technology SteelSeries  : Device: "/dev/input/event4"
[    18.719] (--) evdev: La-VIEW Technology SteelSeries  : Vendor 0x1038 Product 0x1361
[    18.719] (--) evdev: La-VIEW Technology SteelSeries  : Found 12 mouse buttons
[    18.719] (--) evdev: La-VIEW Technology SteelSeries  : Found scroll wheel(s)
[    18.719] (--) evdev: La-VIEW Technology SteelSeries  : Found relative axes
[    18.719] (--) evdev: La-VIEW Technology SteelSeries  : Found x and y relative axes
[    18.719] (II) evdev: La-VIEW Technology SteelSeries  : Configuring as mouse
[    18.719] (II) evdev: La-VIEW Technology SteelSeries  : Adding scrollwheel support
[    18.719] (**) evdev: La-VIEW Technology SteelSeries  : YAxisMapping: buttons 4 and 5
[    18.719] (**) evdev: La-VIEW Technology SteelSeries  : EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    18.719] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input4/event4"
[    18.719] (II) XINPUT: Adding extended input device "La-VIEW Technology SteelSeries  " (type: MOUSE, id 10)
[    18.719] (II) evdev: La-VIEW Technology SteelSeries  : initialized for relative axes.
[    18.719] (**) La-VIEW Technology SteelSeries  : (accel) keeping acceleration scheme 1
[    18.719] (**) La-VIEW Technology SteelSeries  : (accel) acceleration profile 0
[    18.719] (**) La-VIEW Technology SteelSeries  : (accel) acceleration factor: 2.000
[    18.719] (**) La-VIEW Technology SteelSeries  : (accel) acceleration threshold: 4
[    18.719] (II) config/udev: Adding input device La-VIEW Technology SteelSeries   (/dev/input/mouse0)
[    18.719] (II) No input driver specified, ignoring this device.
[    18.719] (II) This device may have been added with another device file.
[    18.720] (II) config/udev: Adding input device HDA Intel PCH Line-Out Surround (/dev/input/event10)
[    18.720] (II) No input driver specified, ignoring this device.
[    18.720] (II) This device may have been added with another device file.
[    18.720] (II) config/udev: Adding input device HDA Intel PCH Line-Out Front (/dev/input/event11)
[    18.720] (II) No input driver specified, ignoring this device.
[    18.720] (II) This device may have been added with another device file.
[    18.720] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event5)
[    18.720] (II) No input driver specified, ignoring this device.
[    18.720] (II) This device may have been added with another device file.
[    18.720] (II) config/udev: Adding input device HDA Intel PCH Front Mic (/dev/input/event6)
[    18.720] (II) No input driver specified, ignoring this device.
[    18.720] (II) This device may have been added with another device file.
[    18.720] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event7)
[    18.720] (II) No input driver specified, ignoring this device.
[    18.720] (II) This device may have been added with another device file.
[    18.720] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event8)
[    18.720] (II) No input driver specified, ignoring this device.
[    18.720] (II) This device may have been added with another device file.
[    18.720] (II) config/udev: Adding input device HDA Intel PCH Line-Out CLFE (/dev/input/event9)
[    18.720] (II) No input driver specified, ignoring this device.
[    18.720] (II) This device may have been added with another device file.
[    18.744] (II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
[    23.023] (II) fglrx(0): Cannot get EDID information for CRT1
[    24.512] (II) fglrx(0): Cannot get EDID information for CRT1
[   378.260] (II) fglrx(0): Cannot get EDID information for CRT1
[   379.104] (II) fglrx(0): Cannot get EDID information for CRT1
[   380.625] (II) fglrx(0): Cannot get EDID information for CRT1
[   387.436] (II) XKB: reuse xkmfile /var/lib/xkb/server-03AF3717FF3AB439A4BAABA686CCB40771CDF520.xkm
[   400.414] (II) fglrx(0): Cannot get EDID information for CRT1
[  2900.479] (II) fglrx(0): Cannot get EDID information for CRT1
[  3668.405] (II) fglrx(0): Cannot get EDID information for CRT1
```


Regards
404

---

### Post by papibe on 2012-05-06
```
[    17.818] (II) fglrx(0): Cannot get EDID information for CRT1
```

It looks like a recurrent problem these days: a modern monitor that does not report correctly its resolution and timings (EDID) over an analog connection (VGA connection?).

Do you have any way to connect the monitor (DVI or HDMI)?

Regards.

---

### Post by T. Amaral on 2012-05-06
> **not found said:**
> My issue is that I am getting a maximum resolution (I can use) of 1600x900 and my screen (LG Flatron E2251) has a naitive resolution of 1920x1080.
See post #2 (by gruffy-06) in the thread linked below. It once solved a similar issue I had. The idea is to find out the signal frequencies for your screen as documented by the manufacturer, then edit them manually in xorg.conf. After that, log out and log in and see if the wanted resolution becomes available.
[http://ubuntuforums.org/showthread.php?t=1205547](http://ubuntuforums.org/showthread.php?t=1205547)

---

### Post by sffvba[e0rt on 2012-05-06
Thanks papibe, I was suspecting that is the case.

Thanks T. Amaral, I will look into it and post how it goes.


Regards
404

---

### Post by Bandit on 2012-05-06
Hey NF, are you still having resolution issues?
If you are post what brand, model and year is of your monitor. Have to look that up to get the correct mode lines.
I noticed the mode lines you imputed were incorrect as per your log file and they totally skipped 1920x1080 resolution.

---

### Post by sffvba[e0rt on 2012-05-06
> **Bandit said:**
> Hey NF, are you still having resolution issues?
If you are post what brand, model and year is of your monitor. Have to look that up to get the correct mode lines.
I noticed the mode lines you imputed were incorrect as per your log file and they totally skipped 1920x1080 resolution.

Hi,

I will do so when I get home :)

The log I posted is a clean one without me having tried xrandr like in the OP.  Not sure if it would have made a difference however.


404

---

### Post by sffvba[e0rt on 2012-05-09
Added my monitor information into xorg.conf and still not having luck.

Irony is that my monitor is going out of range with either 74.9Hz or 75.1Hz where my maximum is 75Hz...

Here is my xorg.conf... maybe I am still doing it wrong :/

```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	HorizSync    30.0 - 83.0
	VertRefresh  56.0 - 75.0
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1600x900"
	EndSubSection
EndSection

```

If I change "Modes" from 1600x900 to 1920x1080 the screen goes out of range... and if I remove it completely the same happens (I suspect it is trying to go to 1600x1200 which is listed as the preferred resolution in the Catalyst Control Centre and is also the highest listed there still.


404

---

### Post by papibe on 2012-05-09
Hi again.

I found a user with a similar problem [here]("http://www.tomshardware.com/forum/63996-3-e2251-super-flatron-monitor-gaming-issues"). It seems s/he was able to get the EDID info.

With that information it could be possible to build an EDID.bin file and hardcode it into xorg.conf. Take a look at this [thread]("http://ubuntuforums.org/showthread.php?t=1857772&highlight=customEDID") for details (different problem but similar solution).

Tell me if you need more help with that.

Good Night, I'll come back tomorrow.
Kind Regards.

---

### Post by sffvba[e0rt on 2012-05-09
> **papibe said:**
> Hi again.

I found a user with a similar problem [here]("http://www.tomshardware.com/forum/63996-3-e2251-super-flatron-monitor-gaming-issues"). It seems s/he was able to get the EDID info.

With that information it could be possible to build an EDID.bin file and hardcode it into xorg.conf. Take a look at this [thread]("http://ubuntuforums.org/showthread.php?t=1857772&highlight=customEDID") for details (different problem but similar solution).

Tell me if you need more help with that.

Good Night, I'll come back tomorrow.
Kind Regards.

Thanks for the assistance... as it stands I am unable to get the EDID information from any of the utilities I have tried from the links.  Neither read-edid or Phoenix EDID extractor (tried in Windows) are working... both fail :/

At this point I am almost ready to live in 1600x900... something as trivial as slightly higher resolution shouldn't need this much effort :p


404

---

### Post by papibe on 2012-05-09
He was able to get the EDID data, and s/he posted it (check the end of post of the first link).

With that text, I was able to create a edid.bin using the method described on the second link. This is what parse-bin reports about it:
```
parse-edid < edid.bin 

parse-edid: parse-edid version 2.0.0
parse-edid: EDID checksum passed.

	# EDID version 1 revision 3
Section "Monitor"
	# Block type: 2:0 3:fd
	# Block type: 2:0 3:fc
	Identifier "E2251"
	VendorName "GSM"
	ModelName "E2251"
	# Block type: 2:0 3:fd
	HorizSync 30-83
	VertRefresh 56-75
	# Max dot clock (video bandwidth) 150 MHz
	# Block type: 2:0 3:fc
	# Block type: 2:0 3:ff
	# DPMS capabilities: Active off:yes  Suspend:yes  Standby:yes

	Mode 	"1920x1080"	# vfreq 60.000Hz, hfreq 67.500kHz
		DotClock	148.500000
		HTimings	1920 2008 2052 2200
		VTimings	1080 1084 1089 1125
		Flags	"+HSync" "+VSync"
	EndMode
	# Block type: 2:0 3:fd
	# Block type: 2:0 3:fc
	# Block type: 2:0 3:ff
EndSection
```

I've attached the file. Uncompress it and follow the steps of the 2nd link to use it in your xorg.conf. I've also suggest commenting out the 1600x900 mode (so you get default resolution as described on the edid.bin).

Let me know how it goes, and if you need more help with that.
Regards.

---

### Post by sffvba[e0rt on 2012-05-09
Oh wow... so if I actually understood a bit more about what I was reading I would have been able to see that a solution was right there in the links :( ...

aticonfig doesn't seem to have an import tool for edid files so I edited it into my xorg.conf myself ending up with:

```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	"CustomEDID" "DFP-1:/etc/X11/edid.bin"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
```

Did not work :/  


404

---

### Post by papibe on 2012-05-09
Change
```
DFP-1
```
For the actual name that the driver handles your monitor. I think it is:
```
CRT1
```
(from your /var/log/Xorg.0.log)

Regards.

---

### Post by sffvba[e0rt on 2012-05-09
> **papibe said:**
> Change
```
DFP-1
```
For the actual name that the driver handles your monitor. I think it is:
```
CRT1
```
(from your /var/log/Xorg.0.log)

Regards.

I was wondering about that actually... :p

Let me give it a go!


404

---

### Post by sffvba[e0rt on 2012-05-09
Nope... changing it to CRT1 still did not have the desired affect :(

Sleepy time for me... maybe the new day brings new inspiration :)


404

---

### Post by papibe on 2012-05-09
Move your customEDID line from the 'Monitor' section to the 'Device' section.

If that don't work, add this line in the 'Device' section:
```
Option "UseEDID" "False"
```

If you still have problems, please post your /var/log/Xorg.0.log to take a another look (right after a bad boot).

Regards.

---

### Post by sffvba[e0rt on 2012-05-10
> **papibe said:**
> Move your customEDID line from the 'Monitor' section to the 'Device' section.

If that don't work, add this line in the 'Device' section:
```
Option "UseEDID" "False"
```

If you still have problems, please post your /var/log/Xorg.0.log to take a another look (right after a bad boot).

Regards.

Thanks for your patience...

I tried both ways... this is the log after moving the line back to Monitor and adding the line "Option "UseEDID" "False" to Device:


```
[     9.279] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[     9.279] X Protocol Version 11, Revision 0
[     9.279] Build Operating System: Linux 2.6.42-23-generic i686 Ubuntu
[     9.279] Current Operating System: Linux circle 3.2.0-24-generic-pae #37-Ubuntu SMP Wed Apr 25 10:47:59 UTC 2012 i686
[     9.279] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-24-generic-pae root=UUID=e86df17f-0c9e-46f2-8dbc-518ff8a39fe2 ro quiet splash vt.handoff=7
[     9.279] Build Date: 20 April 2012  05:12:21AM
[     9.279] xorg-server 2:1.11.4-0ubuntu10.1 (For technical support please see http://www.ubuntu.com/support) 
[     9.279] Current version of pixman: 0.24.4
[     9.279] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[     9.279] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     9.279] (==) Log file: "/var/log/Xorg.0.log", Time: Thu May 10 09:46:43 2012
[     9.279] (==) Using config file: "/etc/X11/xorg.conf"
[     9.279] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     9.279] (==) ServerLayout "aticonfig Layout"
[     9.279] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[     9.279] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[     9.280] (**) |   |-->Device "aticonfig-Device[0]-0"
[     9.280] (==) Automatically adding devices
[     9.280] (==) Automatically enabling devices
[     9.280] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     9.280] 	Entry deleted from font path.
[     9.280] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     9.280] 	Entry deleted from font path.
[     9.280] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     9.280] 	Entry deleted from font path.
[     9.280] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     9.280] 	Entry deleted from font path.
[     9.280] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     9.280] 	Entry deleted from font path.
[     9.280] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[     9.280] 	Entry deleted from font path.
[     9.280] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[     9.280] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     9.280] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[     9.280] (II) Loader magic: 0xb77b65a0
[     9.280] (II) Module ABI versions:
[     9.280] 	X.Org ANSI C Emulation: 0.4
[     9.280] 	X.Org Video Driver: 11.0
[     9.280] 	X.Org XInput driver : 16.0
[     9.280] 	X.Org Server Extension : 6.0
[     9.280] (--) PCI:*(0:1:0:0) 1002:6739:174b:174b rev 0, Mem @ 0xe0000000/268435456, 0xfe620000/131072, I/O @ 0x0000e000/256, BIOS @ 0x????????/131072
[     9.280] (II) Open ACPI successful (/var/run/acpid.socket)
[     9.280] (II) "extmod" will be loaded by default.
[     9.280] (II) "dbe" will be loaded by default.
[     9.280] (II) "glx" will be loaded by default.
[     9.280] (II) "record" will be loaded by default.
[     9.280] (II) "dri" will be loaded by default.
[     9.280] (II) "dri2" will be loaded by default.
[     9.280] (II) LoadModule: "extmod"
[     9.305] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[     9.305] (II) Module extmod: vendor="X.Org Foundation"
[     9.305] 	compiled for 1.11.3, module version = 1.0.0
[     9.305] 	Module class: X.Org Server Extension
[     9.305] 	ABI class: X.Org Server Extension, version 6.0
[     9.305] (II) Loading extension MIT-SCREEN-SAVER
[     9.305] (II) Loading extension XFree86-VidModeExtension
[     9.305] (II) Loading extension XFree86-DGA
[     9.305] (II) Loading extension DPMS
[     9.305] (II) Loading extension XVideo
[     9.305] (II) Loading extension XVideo-MotionCompensation
[     9.305] (II) Loading extension X-Resource
[     9.305] (II) LoadModule: "dbe"
[     9.305] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[     9.305] (II) Module dbe: vendor="X.Org Foundation"
[     9.305] 	compiled for 1.11.3, module version = 1.0.0
[     9.305] 	Module class: X.Org Server Extension
[     9.305] 	ABI class: X.Org Server Extension, version 6.0
[     9.305] (II) Loading extension DOUBLE-BUFFER
[     9.305] (II) LoadModule: "glx"
[     9.305] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/modules/extensions/libglx.so
[     9.306] (II) Module glx: vendor="Advanced Micro Devices, Inc."
[     9.306] 	compiled for 6.9.0, module version = 1.0.0
[     9.306] (II) Loading extension GLX
[     9.306] (II) LoadModule: "record"
[     9.306] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[     9.306] (II) Module record: vendor="X.Org Foundation"
[     9.306] 	compiled for 1.11.3, module version = 1.13.0
[     9.306] 	Module class: X.Org Server Extension
[     9.306] 	ABI class: X.Org Server Extension, version 6.0
[     9.306] (II) Loading extension RECORD
[     9.306] (II) LoadModule: "dri"
[     9.306] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[     9.306] (II) Module dri: vendor="X.Org Foundation"
[     9.306] 	compiled for 1.11.3, module version = 1.0.0
[     9.306] 	ABI class: X.Org Server Extension, version 6.0
[     9.306] (II) Loading extension XFree86-DRI
[     9.306] (II) LoadModule: "dri2"
[     9.306] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[     9.306] (II) Module dri2: vendor="X.Org Foundation"
[     9.306] 	compiled for 1.11.3, module version = 1.2.0
[     9.306] 	ABI class: X.Org Server Extension, version 6.0
[     9.306] (II) Loading extension DRI2
[     9.306] (II) LoadModule: "fglrx"
[     9.306] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so
[     9.316] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[     9.316] 	compiled for 1.4.99.906, module version = 8.96.4
[     9.316] 	Module class: X.Org Video Driver
[     9.316] (II) Loading sub module "fglrxdrm"
[     9.316] (II) LoadModule: "fglrxdrm"
[     9.316] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[     9.316] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[     9.316] 	compiled for 1.4.99.906, module version = 8.96.4
[     9.316] (II) ATI Proprietary Linux Driver Version Identifier:8.96.4
[     9.316] (II) ATI Proprietary Linux Driver Release Identifier: 8.96.7                               
[     9.316] (II) ATI Proprietary Linux Driver Build Date: Mar 12 2012 13:06:47
[     9.316] (++) using VT number 7

[     9.316] (WW) Falling back to old probe method for fglrx
[     9.320] (II) Loading PCS database from /etc/ati/amdpcsdb
[     9.320] (--) Chipset Supported AMD Graphics Processor (0x6739) found
[     9.320] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
[     9.321] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[     9.321] (II) AMD Video driver is signed
[     9.321] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so
[     9.321] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[     9.321] (II) fglrx(0): pEnt->device->identifier=0xb7804dd0
[     9.321] (II) fglrx(0): === [xdl_xs111_atiddxPreInit] === begin
[     9.321] (II) Loading sub module "vgahw"
[     9.321] (II) LoadModule: "vgahw"
[     9.351] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[     9.351] (II) Module vgahw: vendor="X.Org Foundation"
[     9.351] 	compiled for 1.11.3, module version = 0.1.0
[     9.351] 	ABI class: X.Org Video Driver, version 11.0
[     9.351] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[     9.351] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[     9.351] (==) fglrx(0): Default visual is TrueColor
[     9.351] (**) fglrx(0): Option "DPMS" "true"
[     9.351] (==) fglrx(0): RGB weight 888
[     9.351] (II) fglrx(0): Using 8 bits per RGB 
[     9.351] (==) fglrx(0): Buffer Tiling is ON
[     9.351] (II) Loading sub module "fglrxdrm"
[     9.351] (II) LoadModule: "fglrxdrm"
[     9.351] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[     9.351] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[     9.351] 	compiled for 1.4.99.906, module version = 8.96.4
[     9.352] ukiDynamicMajor: found major device number 249
[     9.352] ukiDynamicMajor: found major device number 249
[     9.352] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[     9.352] ukiOpenDevice: node name is /dev/ati/card0
[     9.352] ukiOpenDevice: open result is 12, (OK)
[     9.352] ukiOpenByBusid: ukiOpenMinor returns 12
[     9.352] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[     9.352] (**) fglrx(0): NoAccel = NO
[     9.352] (**) fglrx(0): ATI 2D Acceleration Architecture enabled
[     9.352] (--) fglrx(0): Chipset: "AMD Radeon HD 6800 Series " (Chipset = 0x6739)
[     9.352] (--) fglrx(0): (PciSubVendor = 0x174b, PciSubDevice = 0x174b)
[     9.352] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
[     9.352] (--) fglrx(0): Linear framebuffer (phys) at 0xe0000000
[     9.352] (--) fglrx(0): MMIO registers at 0xfe620000
[     9.352] (--) fglrx(0): I/O port at 0x0000e000
[     9.352] (==) fglrx(0): ROM-BIOS at 0x000c0000
[     9.353] (II) fglrx(0): AC Adapter is used
[     9.355] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
[     9.355] (II) Loading sub module "vbe"
[     9.355] (II) LoadModule: "vbe"
[     9.355] (II) Loading /usr/lib/xorg/modules/libvbe.so
[     9.355] (II) Module vbe: vendor="X.Org Foundation"
[     9.355] 	compiled for 1.11.3, module version = 1.1.0
[     9.355] 	ABI class: X.Org Video Driver, version 11.0
[     9.355] (II) fglrx(0): VESA BIOS detected
[     9.355] (II) fglrx(0): VESA VBE Version 3.0
[     9.355] (II) fglrx(0): VESA VBE Total Mem: 16384 kB
[     9.355] (II) fglrx(0): VESA VBE OEM: AMD ATOMBIOS
[     9.355] (II) fglrx(0): VESA VBE OEM Software Rev: 13.12
[     9.355] (II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2010, AMD Technologies Inc. 
[     9.355] (II) fglrx(0): VESA VBE OEM Product: BARTS
[     9.355] (II) fglrx(0): VESA VBE OEM Product Rev: 01.00
[     9.385] (II) fglrx(0): ATI Video BIOS revision 9 or later detected
[     9.385] (--) fglrx(0): Video RAM: 1048576 kByte, Type: GDDR5
[     9.385] (II) fglrx(0): PCIE card detected
[     9.385] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[     9.385] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[     9.392] (II) fglrx(0): Using adapter: 1:0.0.
[     9.419] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x40000000)
[     9.577] (II) fglrx(0): Interrupt handler installed at IRQ 56.
[     9.577] (II) fglrx(0): RandR 1.2 support is enabled!
[     9.577] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[     9.577] (==) fglrx(0): Center Mode is disabled 
[     9.577] (II) Loading sub module "fb"
[     9.577] (II) LoadModule: "fb"
[     9.577] (II) Loading /usr/lib/xorg/modules/libfb.so
[     9.577] (II) Module fb: vendor="X.Org Foundation"
[     9.577] 	compiled for 1.11.3, module version = 1.0.0
[     9.577] 	ABI class: X.Org ANSI C Emulation, version 0.4
[     9.577] (II) Loading sub module "ddc"
[     9.577] (II) LoadModule: "ddc"
[     9.577] (II) Module "ddc" already built-in
[     9.719] (II) fglrx(0): Finished Initialize PPLIB!
[     9.720] (II) fglrx(0): Output DFP1 using monitor section aticonfig-Monitor[0]-0
[     9.720] (II) fglrx(0): Output DFP2 has no monitor section
[     9.720] (II) fglrx(0): Output DFP3 has no monitor section
[     9.720] (II) fglrx(0): Output DFP4 has no monitor section
[     9.720] (II) fglrx(0): Output DFP5 has no monitor section
[     9.720] (II) fglrx(0): Output DFP6 has no monitor section
[     9.720] (II) fglrx(0): Output DFP7 has no monitor section
[     9.720] (II) fglrx(0): Output CRT1 has no monitor section
[     9.720] (II) Loading sub module "ddc"
[     9.720] (II) LoadModule: "ddc"
[     9.720] (II) Module "ddc" already built-in
[     9.720] (II) fglrx(0): Connected Display0: CRT1
[     9.720] (II) fglrx(0):  Display0: Failed to get EDID information. 
[     9.720] (II) fglrx(0): EDID for output DFP1
[     9.720] (II) fglrx(0): EDID for output DFP2
[     9.720] (II) fglrx(0): EDID for output DFP3
[     9.720] (II) fglrx(0): EDID for output DFP4
[     9.720] (II) fglrx(0): EDID for output DFP5
[     9.720] (II) fglrx(0): EDID for output DFP6
[     9.720] (II) fglrx(0): EDID for output DFP7
[     9.720] (II) fglrx(0): Cannot get EDID information for CRT1
[     9.720] (II) fglrx(0): EDID for output CRT1
[     9.720] (II) fglrx(0): Not using mode "640x350" (vrefresh out of range)
[     9.720] (II) fglrx(0): Not using mode "640x400" (vrefresh out of range)
[     9.720] (II) fglrx(0): Not using mode "720x400" (vrefresh out of range)
[     9.720] (II) fglrx(0): Not using mode "640x480" (vrefresh out of range)
[     9.720] (II) fglrx(0): Not using mode "640x480" (vrefresh out of range)
[     9.720] (II) fglrx(0): Not using mode "640x480" (vrefresh out of range)
[     9.720] (II) fglrx(0): Not using mode "800x600" (vrefresh out of range)
[     9.720] (II) fglrx(0): Not using mode "800x600" (vrefresh out of range)
[     9.720] (II) fglrx(0): Not using mode "800x600" (vrefresh out of range)
[     9.720] (II) fglrx(0): Not using mode "800x600" (vrefresh out of range)
[     9.720] (II) fglrx(0): Not using mode "800x600" (vrefresh out of range)
[     9.720] (II) fglrx(0): Not using mode "848x480" (unknown reason)
[     9.720] (II) fglrx(0): Not using mode "1024x768i" (vrefresh out of range)
[     9.720] (II) fglrx(0): Not using mode "1024x768" (vrefresh out of range)
[     9.720] (II) fglrx(0): Not using mode "1024x768" (vrefresh out of range)
[     9.720] (II) fglrx(0): Not using mode "1024x768" (vrefresh out of range)
[     9.720] (II) fglrx(0): Not using mode "1024x768" (vrefresh out of range)
[     9.720] (II) fglrx(0): Not using mode "1152x864" (vrefresh out of range)
[     9.720] (II) fglrx(0): Not using mode "1280x768" (monitor doesn't support reduced blanking)
[     9.720] (II) fglrx(0): Not using mode "1280x768" (vrefresh out of range)
[     9.720] (II) fglrx(0): Not using mode "1280x768" (vrefresh out of range)
[     9.720] (II) fglrx(0): Not using mode "1280x768" (vrefresh out of range)
[     9.720] (II) fglrx(0): Not using mode "1280x800" (monitor doesn't support reduced blanking)
[     9.720] (II) fglrx(0): Not using mode "1280x800" (vrefresh out of range)
[     9.720] (II) fglrx(0): Not using mode "1280x800" (vrefresh out of range)
[     9.720] (II) fglrx(0): Not using mode "1280x800" (vrefresh out of range)
[     9.720] (II) fglrx(0): Not using mode "1280x960" (unknown reason)
[     9.720] (II) fglrx(0): Not using mode "1280x960" (vrefresh out of range)
[     9.720] (II) fglrx(0): Not using mode "1280x960" (vrefresh out of range)
[     9.720] (II) fglrx(0): Not using mode "1280x1024" (vrefresh out of range)
[     9.720] (II) fglrx(0): Not using mode "1280x1024" (vrefresh out of range)
[     9.720] (II) fglrx(0): Not using mode "1280x1024" (vrefresh out of range)
[     9.720] (II) fglrx(0): Not using mode "1360x768" (vrefresh out of range)
[     9.720] (II) fglrx(0): Not using mode "1400x1050" (monitor doesn't support reduced blanking)
[     9.720] (II) fglrx(0): Not using mode "1400x1050" (unknown reason)
[     9.720] (II) fglrx(0): Not using mode "1400x1050" (vrefresh out of range)
[     9.720] (II) fglrx(0): Not using mode "1400x1050" (vrefresh out of range)
[     9.720] (II) fglrx(0): Not using mode "1400x1050" (vrefresh out of range)
[     9.720] (II) fglrx(0): Not using mode "1440x900" (monitor doesn't support reduced blanking)
[     9.720] (II) fglrx(0): Not using mode "1440x900" (vrefresh out of range)
[     9.720] (II) fglrx(0): Not using mode "1440x900" (vrefresh out of range)
[     9.720] (II) fglrx(0): Not using mode "1440x900" (vrefresh out of range)
[     9.720] (II) fglrx(0): Not using mode "1600x1200" (vrefresh out of range)
[     9.720] (II) fglrx(0): Not using mode "1600x1200" (vrefresh out of range)
[     9.720] (II) fglrx(0): Not using mode "1600x1200" (vrefresh out of range)
[     9.720] (II) fglrx(0): Not using mode "1600x1200" (vrefresh out of range)
[     9.720] (II) fglrx(0): Not using mode "1600x1200" (vrefresh out of range)
[     9.720] (II) fglrx(0): Not using mode "1680x1050" (width too large for virtual size)
[     9.720] (II) fglrx(0): Not using mode "1680x1050" (width too large for virtual size)
[     9.720] (II) fglrx(0): Not using mode "1680x1050" (width too large for virtual size)
[     9.720] (II) fglrx(0): Not using mode "1680x1050" (width too large for virtual size)
[     9.720] (II) fglrx(0): Not using mode "1680x1050" (width too large for virtual size)
[     9.720] (II) fglrx(0): Not using mode "1792x1344" (width too large for virtual size)
[     9.720] (II) fglrx(0): Not using mode "1792x1344" (width too large for virtual size)
[     9.720] (II) fglrx(0): Not using mode "1792x1344" (width too large for virtual size)
[     9.720] (II) fglrx(0): Not using mode "1856x1392" (width too large for virtual size)
[     9.720] (II) fglrx(0): Not using mode "1856x1392" (width too large for virtual size)
[     9.720] (II) fglrx(0): Not using mode "1856x1392" (width too large for virtual size)
[     9.720] (II) fglrx(0): Not using mode "1920x1200" (width too large for virtual size)
[     9.720] (II) fglrx(0): Not using mode "1920x1200" (width too large for virtual size)
[     9.720] (II) fglrx(0): Not using mode "1920x1200" (width too large for virtual size)
[     9.720] (II) fglrx(0): Not using mode "1920x1200" (width too large for virtual size)
[     9.720] (II) fglrx(0): Not using mode "1920x1200" (width too large for virtual size)
[     9.721] (II) fglrx(0): Not using mode "1920x1440" (width too large for virtual size)
[     9.721] (II) fglrx(0): Not using mode "1920x1440" (width too large for virtual size)
[     9.721] (II) fglrx(0): Not using mode "1920x1440" (width too large for virtual size)
[     9.721] (II) fglrx(0): Not using mode "2560x1600" (width too large for virtual size)
[     9.721] (II) fglrx(0): Not using mode "2560x1600" (width too large for virtual size)
[     9.721] (II) fglrx(0): Not using mode "2560x1600" (width too large for virtual size)
[     9.721] (II) fglrx(0): Not using mode "2560x1600" (width too large for virtual size)
[     9.721] (II) fglrx(0): Not using mode "2560x1600" (width too large for virtual size)
[     9.721] (II) fglrx(0): Printing probed modes for output CRT1
[     9.721] (II) fglrx(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[     9.721] (II) fglrx(0): Modeline "1400x1050"x60.0  122.61  1400 1488 1640 1880  1050 1051 1054 1087 -hsync +vsync (65.2 kHz)
[     9.721] (II) fglrx(0): Modeline "1600x900"x60.0  108.00  1600 1624 1704 1800  900 901 904 1000 +hsync +vsync (60.0 kHz)
[     9.721] (II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[     9.721] (II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[     9.721] (II) fglrx(0): Modeline "1280x960"x60.0  102.10  1280 1360 1496 1712  960 961 964 994 -hsync +vsync (59.6 kHz)
[     9.721] (II) fglrx(0): Modeline "1366x768"x60.0   85.50  1366 1436 1579 1792  768 771 774 798 +hsync +vsync (47.7 kHz)
[     9.721] (II) fglrx(0): Modeline "1360x768"x60.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz)
[     9.721] (II) fglrx(0): Modeline "1280x800"x60.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
[     9.721] (II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
[     9.721] (II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 -hsync +vsync (47.8 kHz)
[     9.721] (II) fglrx(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[     9.721] (II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[     9.721] (II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[     9.721] (II) fglrx(0): Modeline "720x480"x60.0   27.03  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[     9.721] (II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[     9.721] (II) fglrx(0): Output DFP1 disconnected
[     9.721] (II) fglrx(0): Output DFP2 disconnected
[     9.721] (II) fglrx(0): Output DFP3 disconnected
[     9.721] (II) fglrx(0): Output DFP4 disconnected
[     9.721] (II) fglrx(0): Output DFP5 disconnected
[     9.721] (II) fglrx(0): Output DFP6 disconnected
[     9.721] (II) fglrx(0): Output DFP7 disconnected
[     9.721] (II) fglrx(0): Output CRT1 connected
[     9.721] (II) fglrx(0): Using exact sizes for initial modes
[     9.721] (II) fglrx(0): Output CRT1 using initial mode 1600x1200
[     9.721] (II) fglrx(0): DPI set to (96, 96)
[     9.721] (II) fglrx(0): Eyefinity capable adapter detected.
[     9.721] (II) fglrx(0): Adapter AMD Radeon HD 6800 Series  has 6 configurable heads and 1 displays connected.
[     9.721] (==) fglrx(0):  PseudoColor visuals disabled
[     9.721] (II) Loading sub module "ramdac"
[     9.721] (II) LoadModule: "ramdac"
[     9.721] (II) Module "ramdac" already built-in
[     9.721] (==) fglrx(0): NoDRI = NO
[     9.721] (==) fglrx(0): Capabilities: 0x00000000
[     9.721] (==) fglrx(0): CapabilitiesEx: 0x00000000
[     9.721] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[     9.721] (==) fglrx(0): UseFastTLS=0
[     9.721] (==) fglrx(0): BlockSignalsOnLock=1
[     9.721] (--) Depth 24 pixmap format is 32 bpp
[     9.726] (II) Loading extension ATIFGLRXDRI
[     9.726] (II) fglrx(0): doing swlDriScreenInit
[     9.726] (II) fglrx(0): swlDriScreenInit for fglrx driver
[     9.726] ukiDynamicMajor: found major device number 249
[     9.726] ukiDynamicMajor: found major device number 249
[     9.726] ukiDynamicMajor: found major device number 249
[     9.726] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[     9.726] ukiOpenDevice: node name is /dev/ati/card0
[     9.726] ukiOpenDevice: open result is 17, (OK)
[     9.726] ukiOpenByBusid: ukiOpenMinor returns 17
[     9.726] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[     9.726] (II) fglrx(0): [uki] DRM interface version 1.0
[     9.726] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:1:0:0"
[     9.726] (II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
[     9.726] (II) fglrx(0): [uki] mapped SAREA 0x2000 to 0xb5fb8000
[     9.726] (II) fglrx(0): [uki] framebuffer handle = 0x3000
[     9.726] (II) fglrx(0): [uki] added 1 reserved context for kernel
[     9.726] (II) fglrx(0): swlDriScreenInit done
[     9.726] (II) fglrx(0): Kernel Module Version Information:
[     9.726] (II) fglrx(0):     Name: fglrx
[     9.726] (II) fglrx(0):     Version: 8.96.4
[     9.726] (II) fglrx(0):     Date: Mar 12 2012
[     9.726] (II) fglrx(0):     Desc: ATI FireGL DRM kernel module
[     9.726] (II) fglrx(0): Kernel Module version matches driver.
[     9.726] (II) fglrx(0): Kernel Module Build Time Information:
[     9.726] (II) fglrx(0):     Build-Kernel UTS_RELEASE:        3.2.0-24-generic-pae
[     9.726] (II) fglrx(0):     Build-Kernel MODVERSIONS:        no
[     9.726] (II) fglrx(0):     Build-Kernel __SMP__:            yes
[     9.726] (II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
[     9.726] (II) fglrx(0): [uki] register handle = 0x00004000
[     9.736] (II) fglrx(0): DRI initialization successfull
[     9.736] (II) fglrx(0): FBADPhys: 0xf00000000 FBMappedSize: 0x01068000
[     9.736] (==) fglrx(0): Backing store disabled
[     9.736] (II) Loading extension FGLRXEXTENSION
[     9.736] (**) fglrx(0): DPMS enabled
[     9.736] (II) fglrx(0): Initialized in-driver Xinerama extension
[     9.736] (**) fglrx(0): Textured Video is enabled.
[     9.736] (II) LoadModule: "glesx"
[     9.736] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/modules/glesx.so
[     9.736] (II) Module glesx: vendor="X.Org Foundation"
[     9.736] 	compiled for 1.4.99.906, module version = 1.0.0
[     9.736] (II) Loading extension GLESX
[     9.736] (II) fglrx(0): GLESX enableFlags = 592
[     9.737] (II) fglrx(0): GLESX is enabled
[     9.737] (II) LoadModule: "amdxmm"
[     9.737] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/modules/amdxmm.so
[     9.737] (II) Module amdxmm: vendor="X.Org Foundation"
[     9.737] 	compiled for 1.4.99.906, module version = 2.0.0
[     9.747] (II) Loading extension AMDXVOPL
[     9.747] (II) Loading extension AMDXVBA
[     9.748] (II) fglrx(0): UVD feature is enabled(II) fglrx(0): 
[     9.749] (II) fglrx(0): Enable composite support successfully
[     9.749] (WW) fglrx(0): Option "UseEDID" is not used
[     9.749] (WW) fglrx(0): Option "VendorName" is not used
[     9.749] (WW) fglrx(0): Option "ModelName" is not used
[     9.749] (WW) fglrx(0): Option "CustomEDID" is not used
[     9.749] (II) fglrx(0): X context handle = 0x1
[     9.749] (II) fglrx(0): [DRI] installation complete
[     9.749] (==) fglrx(0): Silken mouse enabled
[     9.749] (==) fglrx(0): Using HW cursor of display infrastructure!
[     9.750] (II) fglrx(0): Disabling in-server RandR and enabling in-driver RandR 1.2.
[     9.814] (--) RandR disabled
[     9.814] (II) Initializing built-in extension Generic Event Extension
[     9.814] (II) Initializing built-in extension SHAPE
[     9.814] (II) Initializing built-in extension MIT-SHM
[     9.814] (II) Initializing built-in extension XInputExtension
[     9.814] (II) Initializing built-in extension XTEST
[     9.814] (II) Initializing built-in extension BIG-REQUESTS
[     9.814] (II) Initializing built-in extension SYNC
[     9.814] (II) Initializing built-in extension XKEYBOARD
[     9.814] (II) Initializing built-in extension XC-MISC
[     9.814] (II) Initializing built-in extension SECURITY
[     9.814] (II) Initializing built-in extension XINERAMA
[     9.814] (II) Initializing built-in extension XFIXES
[     9.814] (II) Initializing built-in extension RENDER
[     9.814] (II) Initializing built-in extension RANDR
[     9.814] (II) Initializing built-in extension COMPOSITE
[     9.814] (II) Initializing built-in extension DAMAGE
[     9.815] ukiDynamicMajor: found major device number 249
[     9.815] ukiDynamicMajor: found major device number 249
[     9.815] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[     9.815] ukiOpenDevice: node name is /dev/ati/card0
[     9.815] ukiOpenDevice: open result is 18, (OK)
[     9.815] ukiOpenByBusid: ukiOpenMinor returns 18
[     9.815] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[     9.865] (II) AIGLX: Loaded and initialized OpenGL driver(II) GLX: Initialized DRI GL provider for screen 0
[     9.875] (II) fglrx(0): Enable the clock gating!
[     9.875] (II) fglrx(0): Setting screen physical size to 423 x 317
[     9.879] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[     9.881] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[     9.881] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     9.881] (II) LoadModule: "evdev"
[     9.881] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     9.881] (II) Module evdev: vendor="X.Org Foundation"
[     9.881] 	compiled for 1.11.3, module version = 2.7.0
[     9.881] 	Module class: X.Org XInput Driver
[     9.881] 	ABI class: X.Org XInput driver, version 16.0
[     9.881] (II) Using input driver 'evdev' for 'Power Button'
[     9.881] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     9.881] (**) Power Button: always reports core events
[     9.881] (**) evdev: Power Button: Device: "/dev/input/event1"
[     9.881] (--) evdev: Power Button: Vendor 0 Product 0x1
[     9.881] (--) evdev: Power Button: Found keys
[     9.881] (II) evdev: Power Button: Configuring as keyboard
[     9.881] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[     9.881] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     9.881] (**) Option "xkb_rules" "evdev"
[     9.881] (**) Option "xkb_model" "pc105"
[     9.881] (**) Option "xkb_layout" "us"
[     9.882] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[     9.882] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     9.882] (II) Using input driver 'evdev' for 'Power Button'
[     9.882] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     9.882] (**) Power Button: always reports core events
[     9.882] (**) evdev: Power Button: Device: "/dev/input/event0"
[     9.882] (--) evdev: Power Button: Vendor 0 Product 0x1
[     9.882] (--) evdev: Power Button: Found keys
[     9.882] (II) evdev: Power Button: Configuring as keyboard
[     9.882] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[     9.882] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[     9.882] (**) Option "xkb_rules" "evdev"
[     9.882] (**) Option "xkb_model" "pc105"
[     9.882] (**) Option "xkb_layout" "us"
[     9.882] (II) config/udev: Adding input device HD-Audio Generic HDMI/DP,pcm=3 (/dev/input/event12)
[     9.882] (II) No input driver specified, ignoring this device.
[     9.882] (II) This device may have been added with another device file.
[     9.882] (II) config/udev: Adding input device   USB Keyboard (/dev/input/event2)
[     9.882] (**)   USB Keyboard: Applying InputClass "evdev keyboard catchall"
[     9.882] (II) Using input driver 'evdev' for '  USB Keyboard'
[     9.882] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     9.882] (**)   USB Keyboard: always reports core events
[     9.882] (**) evdev:   USB Keyboard: Device: "/dev/input/event2"
[     9.882] (--) evdev:   USB Keyboard: Vendor 0x4d9 Product 0x1702
[     9.882] (--) evdev:   USB Keyboard: Found keys
[     9.882] (II) evdev:   USB Keyboard: Configuring as keyboard
[     9.882] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input2/event2"
[     9.882] (II) XINPUT: Adding extended input device "  USB Keyboard" (type: KEYBOARD, id 8)
[     9.882] (**) Option "xkb_rules" "evdev"
[     9.882] (**) Option "xkb_model" "pc105"
[     9.882] (**) Option "xkb_layout" "us"
[     9.883] (II) config/udev: Adding input device   USB Keyboard (/dev/input/event3)
[     9.883] (**)   USB Keyboard: Applying InputClass "evdev keyboard catchall"
[     9.883] (II) Using input driver 'evdev' for '  USB Keyboard'
[     9.883] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     9.883] (**)   USB Keyboard: always reports core events
[     9.883] (**) evdev:   USB Keyboard: Device: "/dev/input/event3"
[     9.883] (--) evdev:   USB Keyboard: Vendor 0x4d9 Product 0x1702
[     9.883] (--) evdev:   USB Keyboard: Found keys
[     9.883] (II) evdev:   USB Keyboard: Configuring as keyboard
[     9.883] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.1/input/input3/event3"
[     9.883] (II) XINPUT: Adding extended input device "  USB Keyboard" (type: KEYBOARD, id 9)
[     9.883] (**) Option "xkb_rules" "evdev"
[     9.883] (**) Option "xkb_model" "pc105"
[     9.883] (**) Option "xkb_layout" "us"
[     9.883] (II) config/udev: Adding input device La-VIEW Technology SteelSeries   (/dev/input/event4)
[     9.883] (**) La-VIEW Technology SteelSeries  : Applying InputClass "evdev pointer catchall"
[     9.883] (II) Using input driver 'evdev' for 'La-VIEW Technology SteelSeries  '
[     9.883] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     9.883] (**) La-VIEW Technology SteelSeries  : always reports core events
[     9.883] (**) evdev: La-VIEW Technology SteelSeries  : Device: "/dev/input/event4"
[     9.883] (--) evdev: La-VIEW Technology SteelSeries  : Vendor 0x1038 Product 0x1361
[     9.883] (--) evdev: La-VIEW Technology SteelSeries  : Found 12 mouse buttons
[     9.883] (--) evdev: La-VIEW Technology SteelSeries  : Found scroll wheel(s)
[     9.883] (--) evdev: La-VIEW Technology SteelSeries  : Found relative axes
[     9.883] (--) evdev: La-VIEW Technology SteelSeries  : Found x and y relative axes
[     9.883] (II) evdev: La-VIEW Technology SteelSeries  : Configuring as mouse
[     9.883] (II) evdev: La-VIEW Technology SteelSeries  : Adding scrollwheel support
[     9.883] (**) evdev: La-VIEW Technology SteelSeries  : YAxisMapping: buttons 4 and 5
[     9.883] (**) evdev: La-VIEW Technology SteelSeries  : EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     9.883] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input4/event4"
[     9.883] (II) XINPUT: Adding extended input device "La-VIEW Technology SteelSeries  " (type: MOUSE, id 10)
[     9.883] (II) evdev: La-VIEW Technology SteelSeries  : initialized for relative axes.
[     9.883] (**) La-VIEW Technology SteelSeries  : (accel) keeping acceleration scheme 1
[     9.883] (**) La-VIEW Technology SteelSeries  : (accel) acceleration profile 0
[     9.883] (**) La-VIEW Technology SteelSeries  : (accel) acceleration factor: 2.000
[     9.883] (**) La-VIEW Technology SteelSeries  : (accel) acceleration threshold: 4
[     9.883] (II) config/udev: Adding input device La-VIEW Technology SteelSeries   (/dev/input/mouse0)
[     9.883] (II) No input driver specified, ignoring this device.
[     9.883] (II) This device may have been added with another device file.
[     9.884] (II) config/udev: Adding input device HDA Intel PCH Line-Out Surround (/dev/input/event10)
[     9.884] (II) No input driver specified, ignoring this device.
[     9.884] (II) This device may have been added with another device file.
[     9.884] (II) config/udev: Adding input device HDA Intel PCH Line-Out Front (/dev/input/event11)
[     9.884] (II) No input driver specified, ignoring this device.
[     9.884] (II) This device may have been added with another device file.
[     9.884] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event5)
[     9.884] (II) No input driver specified, ignoring this device.
[     9.884] (II) This device may have been added with another device file.
[     9.884] (II) config/udev: Adding input device HDA Intel PCH Front Mic (/dev/input/event6)
[     9.884] (II) No input driver specified, ignoring this device.
[     9.884] (II) This device may have been added with another device file.
[     9.884] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event7)
[     9.884] (II) No input driver specified, ignoring this device.
[     9.884] (II) This device may have been added with another device file.
[     9.884] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event8)
[     9.884] (II) No input driver specified, ignoring this device.
[     9.884] (II) This device may have been added with another device file.
[     9.884] (II) config/udev: Adding input device HDA Intel PCH Line-Out CLFE (/dev/input/event9)
[     9.884] (II) No input driver specified, ignoring this device.
[     9.884] (II) This device may have been added with another device file.
[     9.908] (II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
[    10.258] (II) fglrx(0): Cannot get EDID information for CRT1
[    11.432] (II) fglrx(0): Cannot get EDID information for CRT1
[   114.588] (II) AIGLX: Suspending AIGLX clients for VT switch
[   114.588] (II) fglrx(0): Backup framebuffer data.
[   114.594] (II) fglrx(0): Backup complete.
```


404

---

### Post by papibe on 2012-05-10
```
[     9.749] (WW) fglrx(0): Option "UseEDID" is not used
[     9.749] (WW) fglrx(0): Option "CustomEDID" is not used
```

Yikes :confused: It looks like fglrx doesn't honor those options.

I think a possible solution would be to create a custom modeline, but using the values of the EDID we got from the link I found (post #21). Something like:
```
Modeline  "1920x1080"  148.50 1920 2008 2052 2200 1080 1084 1089 1125 +HSync +VSync
```

Regards.

---

### Post by FishboyFive on 2012-05-10
what does your Boot screen plymouth look like with these drivers installed ?

and shutdown screen ?

thanks

---

### Post by sffvba[e0rt on 2012-05-10
> **papibe said:**
> ```
[     9.749] (WW) fglrx(0): Option "UseEDID" is not used
[     9.749] (WW) fglrx(0): Option "CustomEDID" is not used
```

Yikes :confused: It looks like fglrx doesn't honor those options.

I think a possible solution would be to create a custom modeline, but using the values of the EDID we got from the link I found (post #21). Something like:
```
Modeline  "1920x1080"  148.50 1920 2008 2052 2200 1080 1084 1089 1125 +HSync +VSync
```

Regards.

Hi,

I get the same error I got in the OP:

```
nlsthzn@circle:~$ xrandr --newmode "1920x1080"  148.50 1920 2008 2052 2200 1080 1084 1089 1125 +HSync +VSync
nlsthzn@circle:~$ xrandr --addmode CRT1 1920x1080
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  157 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  49
  Current serial number in output stream:  50
nlsthzn@circle:~$ xrandr --addmode CRT1 1920x1080_60.0
xrandr: cannot find mode "1920x1080_60.0"
nlsthzn@circle:~$ xrandr --addmode CRT1 1920x1080
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  157 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  49
  Current serial number in output stream:  50
nlsthzn@circle:~$ 

```

> **FishboyFive said:**
> what does your Boot screen plymouth look like with these drivers installed ?

and shutdown screen ?

thanks

The splash screens show... very large and a bit fuzzy... then once it has to go to the log in screen the monitor goes out of range.  I even logged in once (I had some issues with lightdm not honouring the resolution set) but still the monitor stays out of range (I suspect it is because it falls back to a resolution of 1600x1200 which the monitor can't handle).


Cheers
404

---

### Post by chamber on 2012-05-10
Should it not be

```
cvt 1920 1080
```

Which has generated the following for you

"1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync

Then,

```
xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsyn
```

Then, (note the quotes, which you didn't have)

```
xrandr --addmode CRT1 "1920x1080_60.00"
```

Then

```
xrandr --output CRT1 --mode "1920x1080_60.0"
```

---

### Post by sffvba[e0rt on 2012-05-10
> **chamber said:**
> Should it not be

```
cvt 1920 1080
```

Which has generated the following for you

"1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync

Then,

```
xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsyn
```

Then, (note the quotes, which you didn't have)

```
xrandr --addmode CRT1 "1920x1080_60.00"
```

Then

```
xrandr --output CRT1 --mode "1920x1080_60.0"
```

Hi, 

See the opening post ;)


404

---

### Post by chamber on 2012-05-10
> **not found said:**
> Hi, 

See the opening post ;)


404

I did indeed see the opening post.

You had

xrandr --addmode CRT1 1920x1080_60.00

I suggested

xrandr --addmode CRT1 [COLOR="Red"]"[/COLOR]1920x1080_60.00[COLOR="Red"]"[/COLOR]

notice the quotations in red.

---

### Post by sffvba[e0rt on 2012-05-10
> **chamber said:**
> I did indeed see the opening post.

You had

xrandr --addmode CRT1 1920x1080_60.00

I suggested

xrandr --addmode CRT1 [COLOR="Red"]"[/COLOR]1920x1080_60.00[COLOR="Red"]"[/COLOR]

notice the quotations in red.

```
nlsthzn@circle:~$ xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsyn
nlsthzn@circle:~$ xrandr --addmode CRT1 "1920x1080_60.00"
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  157 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  49
  Current serial number in output stream:  50
nlsthzn@circle:~$ 

```

Getting the same error still... thanks for the assistance.


404

---

### Post by chamber on 2012-05-10
Have you tried modifying your /etc/X11/xorg.conf so that it displays the following, you had previously mentioned about just changing the preferred mode but what about adding the Modeline to it?

```

Section "Monitor"
	Identifier "aticonfig-Screen[0]-0"
    Modeline        "1920x1080_60.00" 173.00 1920 2048 2248 2576 1080 1083 1088 1120 -hsync +vsync
    Option          "PreferredMode" "1920x1080_60.00"
EndSection
```

---

### Post by sffvba[e0rt on 2012-05-11
> **chamber said:**
> Have you tried modifying your /etc/X11/xorg.conf so that it displays the following, you had previously mentioned about just changing the preferred mode but what about adding the Modeline to it?

```

Section "Monitor"
	Identifier "aticonfig-Screen[0]-0"
    Modeline        "1920x1080_60.00" 173.00 1920 2048 2248 2576 1080 1083 1088 1120 -hsync +vsync
    Option          "PreferredMode" "1920x1080_60.00"
EndSection
```

I have not tried that... will do once I am home again, thanks.


404

---

### Post by lukax on 2012-05-15
I'm having the exact same problem with the same monitor brand :(:(
still using windows only because of this... And I've tried almost everything.. (Thinking about buying a new monitor just to use linux?)
Please help, my card is the 6950

---

### Post by matt_symes on 2012-05-15
Hi

Interesting thread. It seems fglrx is a right pain to use a custom EDID with. 

Radeon is not so much of a problem. Any reason you cannot use the radeon driver ?

Anyway, take a read of this. 

[http://ati.cchtml.com/show_bug.cgi?id=415](http://ati.cchtml.com/show_bug.cgi?id=415)

Comment 2 may suggest a way to use a binary custom EDID for fglrx. I cannot comment on it though.

Kind regards

---

### Post by lukax on 2012-05-15
Thank you for your reply, I'm going to try that right now:P

---

### Post by lukax on 2012-05-15
OMG!!1 I can`t believe it worked!!? :lolflag:
this is what I did:

1: Extract the edid with the Phoenix tool in Windows
2: boot ubuntu with the option "nomodeset" right after "splash quiet" without this option your screen is gonna go out of range
3: Install ubuntu
4: boot ubuntu again with the option "nomodeset"
5: Download and install ATI's driver
6: Before reboot, Open up terminal and type "aticonfig --initial"
7: reboot with the option "text" right after "splash quiet"
8: copy the edid extracted from Windows to /etc/ati/
9: rename edid.raw to "your output".edid, mine was crt1 therefore crt1.edid
10: be happy enjoying this great OS with your awesome resolution

EDIT:
Attached my monitor's edid, it works for 1920x1080@60Hz

---

### Post by matt_symes on 2012-05-15
Hi

> **lukax said:**
> OMG!!1 I can`t believe it worked!!? :lolflag:
this is what I did:

1: Extract the edid the the Phoenix tool in Windows
2: boot ubuntu with the option "nomodeset" right after "splash quiet" without this option your screen is gonna go out of range
3: Install ubuntu
4: boot ubuntu again with the option "nomodeset"
5: Download and install ATI's driver
6: Before reboot, Open up terminal and type "aticonfig --initial"
7: reboot with the option "text" right after "splash quiet"
8: copy the edid extracted from Windows to /etc/ati/
9: rename edid.raw to "your output".edid, mine was crt1 therefore crt1.edid
10: be happy enjoying this great OS with your awesome resolution

LOL. :guitar:

Also, thanks for posting the steps you took.

**EDIT:** Any chance you can zip up your edid file and add as an attachment here ?

Kind regards

---

### Post by lukax on 2012-05-15
> **matt_symes said:**
> Hi



LOL. :guitar:

Also, thanks for posting the steps you took.

**EDIT:** Any chance you can zip up your edid file and add as an attachment here ?

Kind regards

Sure.. attached
Thanks

---

### Post by sffvba[e0rt on 2012-05-17
> **matt_symes said:**
> Hi

Interesting thread. It seems fglrx is a right pain to use a custom EDID with. 

Radeon is not so much of a problem. Any reason you cannot use the radeon driver ?

Anyway, take a read of this. 

[http://ati.cchtml.com/show_bug.cgi?id=415](http://ati.cchtml.com/show_bug.cgi?id=415)

Comment 2 may suggest a way to use a binary custom EDID for fglrx. I cannot comment on it though.

Kind regards

> **lukax said:**
> OMG!!1 I can`t believe it worked!!? :lolflag:


Oh my goodness!!

Thanks so much to both of you :) 

matt_symes thanks for the PM and the link, lukax thanks for trying it and the steps and also the edid file (saved me having to go and make another).

Been away for a couple of days, had even removed Ubuntu and installed openSUSE to see if I could make this work... AWSOME!!


Regards
404

---

### Post by doobydave on 2012-05-17
Would any of you EDID / Xorg experts be able to assist? I have a similar problem only with an nvidia card and a CRT monitor.

[http://ubuntuforums.org/showthread.php?p=11945014#post11945014](http://ubuntuforums.org/showthread.php?p=11945014#post11945014)

And thanks Lukax - my system needed the nomodeset flag.

/Does it count as thread hijacking if the original problem is solved?
:)

---

