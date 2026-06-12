---
title: "Ubuntu boots into blank screen"
date: 2011-03-01
forum: General Help
---

### Post by Timokl on 2011-03-01
Hi everyone,

something plagues my Ubuntu box since I upgraded to Ubuntu 10.10 - I end up with a blank screen while booting. I use an Asus F81SE Notebook, and Dual Boot with Windows XP. Everything worked fine with Ubuntu 10.04.

When I start my notebook after the upgrade to Ubuntu 10.10, I come to Grub, and when I select the latest kernel available, the hard disk LED blinks for a second, turns off ... and nothing happens any more. There is just a blinking text cursor.

As I upgraded from the previous Ubuntu version, there was an older kernel left (2.6.32-26-generic), which boots up fine.

I run 64 Bit on an Intel T4200 CPU. Booting the Live CD brings me to the purple screen with the open source logo at the bottom. I tried 32 Bit and 64 Bit versions of Ubuntu 10.10.

I don't seem to find similar problems on this forum. But does anyone know how to find the mistake?

Timo

---

### Post by Timokl on 2011-03-01
I just downloaded Fedora 14 and tried to boot from the Live CD - I end in the same blank screen.

Any suggestions?

---

### Post by vivek.pandey on 2011-03-01
try going in recovery mode your updated version and repair the system. this may help

---

### Post by Timokl on 2011-03-02
> **neo_aryan said:**
> try going in recovery mode your updated version and repair the system. this may help

I tried that already, but it does not work, the boot process stops after about a second. These are the last messages (fotografed the screen and typed it, so I hope there are no typos)

```
PNP: PS/2 Controller [PNP8383:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq

[ 1.984773] i8042.c: Detected active multiplexing controller, rev 1.1.
[ 1.986691] serio: i8042 KBD port at 0x60,0x64 irq 1
L 1.985748] serio: i8042 AUX0 port at 0x60,0x64 irq 12
l 1.988883] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[ 1.988855] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[ 1.986986] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[ 1.987867] mice: PS/2 mouse device common for all mice
[ 1.987365] rtc_cmos 00:00: RTC can wake from S4
[ 1.987491] rtc_cmos 00:00: rtc core: registered rtc_cmos as rtc0
[ 1.987565] rtc0: alarms up to one year, 114 bytes nvram, hpet irqs
[ 1.987771] device-mapper: uevent: version 1.0.3
[ 1.987961] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[ 1.988144] device-mapper: multipath: verslon 1.1.1 loaded
[ 1.988194] device-nnpper: multlpath round-robin: version 1.0.0 loaded
[ 1.988614] cpuidle: using governor ladder
[ 1.988818] cpuidle: using governor menu
[ 1.9893151 ICP cubic registered
[ 1.9895671 NET: Registered protocol family 10
[ 1.9982181 lo: Disabled Prlvacy Extensions
[ 1.9985881 NET: Registered protocol family 17
[ 1.9916831 registered taskstats version 1
```

However, I just tried to open the Live CD in VirtualBox, and it worked in the virtual machine.

Timo

---

### Post by Timokl on 2011-03-05
A friend suggested that an 'over-optimised' piece of hardware might be the reason. So as the last output is the taskstats one, I think the next step in the startup process might be the one that crashes the system.

Any kernel hackers who know what's next in the boot process? And which part of the hardware is involved?

Timo

---

### Post by oldfred on 2011-03-05
The liveCd uses a low level video card driver. The install updates it to a "better" drive that often does not work. What video card do you have?

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll
Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line
[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

---

### Post by Timokl on 2011-03-07
Thanks for the advice. I'll have a try with the different settings.

I have an ATI video card. You can see my hardware in the attached file. I got this by

```
sudo lshw -html > hardware.html
```

---

### Post by oldfred on 2011-03-07
I have nVidia and nomodeset worked for me. I have had to add nomodeset on every install since 10.04.

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

---

### Post by Timokl on 2011-03-07
This got me one step further!

I tried the following boot parameters with these results:

noapic = fail
*nolapic* = boots until login screen, but loads just the background image and shows mouse cursor; system freezed at that point, mouse cursor does not react
noacpi = fail
noirqpoll = fail
nosmp = fail
irqpoll = fail
**acpi=off** = can boot and log into Ubuntu 10.10, seems to work
nomodeset=0 = fail

One thing I remarked was, shortly before the computer freezes, the Bluetooth LED goes on.

I'll have to check on the possible consequences for acpi=off and decide.

As driver for my video card, I use the fglrx binary driver - I'll try an open source driver to see if it will improve anything.

---

### Post by oldfred on 2011-03-07
There are some BIOS settings that make a difference. 

Some issues on booting install:
BIOS settings need USB mouse & keyboard
BIOS in not updated to latest revision
BIOS not set to boot CD or USB first
BIOS shows floppy or firewire and you do not have those
changing newer BIOS SATA from 6 Gbs to a 3Gbs 
Other BIOS settings - Security or locked down Boot sector, Bitlocker
Disable Quickboot in BIOS 
core unlocker feature on asus m4a87td usb3 was causing the problem
Old BIOS, new drive 137GB max boot size
NTFS partition needs chkdsk, gparted will not see drive if chkdsk flag set, flag is set on resize
Raid meta data on drive - even if one drive (Vendor happend to set it on)
BIOS setting, Keyboard response in grub really slow

The mode for the disc was set to AUTO. Changed it to LBA. Then it worked.
Change SATA controller mode from AHCI to Compatibility (AHCI should be ok for Vista/7 & Linux), XP may not have AHCI driver.
[http://ubuntuforums.org/showthread.php?t=1694750&page=8](http://ubuntuforums.org/showthread.php?t=1694750&page=8) post #79
Standard BIOS Settings -> [drive you want to change] -> IDE Access -> “Large”, did the trick. 

SATA mode should stay in AHCI unless you are getting nasty issues (which shouldn't happen with linux or vista/win7). The main reason why people change SATA mode to 'compatibility' is because winXP wont work with AHCI without loading the drivers..and you need a floppy drive to load the drivers, which most newer computers don't have (and lots of people are lazy anyway).

---

### Post by Timokl on 2011-03-08
Some new developments ... when I booted the updated kernel with acpi=off parameter, X-Server crashed. Here's the /var/log/Xorg.0.log:

```
[    77.736] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    77.736] X Protocol Version 11, Revision 0
[    77.736] Build Operating System: Linux 2.6.24-28-server x86_64 Ubuntu
[    77.736] Current Operating System: Linux doppelhirn 2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:39:03 UTC 2011 x86_64
[    77.736] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-28-generic root=UUID=40cc4a58-8f75-4264-9b59-68e21a424923 ro quiet splash acpi=off
[    77.737] Build Date: 09 January 2011  12:14:27PM
[    77.737] xorg-server 2:1.9.0-0ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
[    77.737] Current version of pixman: 0.18.4
[    77.737] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    77.737] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    77.738] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Mar  8 20:57:10 2011
[    77.738] (==) Using config file: "/etc/X11/xorg.conf"
[    77.738] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    77.739] (==) ServerLayout "amdcccle Layout"
[    77.739] (**) |-->Screen "amdcccle-Screen[1]-0" (0)
[    77.739] (**) |   |-->Monitor "<default monitor>"
[    77.739] (**) |   |-->Device "amdcccle-Device[1]-0"
[    77.739] (==) No monitor specified for screen "amdcccle-Screen[1]-0".
	Using a default monitor configuration.
[    77.739] (**) Option "Xinerama" "off"
[    77.739] (==) Automatically adding devices
[    77.739] (==) Automatically enabling devices
[    77.739] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    77.739] 	Entry deleted from font path.
[    77.739] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    77.739] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    77.739] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    77.739] (II) Loader magic: 0x7d17a0
[    77.739] (II) Module ABI versions:
[    77.739] 	X.Org ANSI C Emulation: 0.4
[    77.739] 	X.Org Video Driver: 8.0
[    77.739] 	X.Org XInput driver : 11.0
[    77.739] 	X.Org Server Extension : 4.0
[    77.740] (--) PCI:*(0:1:0:0) 1002:9553:1043:1b32 rev 0, Mem @ 0xd0000000/268435456, 0xfdef0000/65536, I/O @ 0x0000d800/256, BIOS @ 0x????????/131072
[    77.740] (II) Open ACPI successful (/var/run/acpid.socket)
[    77.740] (II) "extmod" will be loaded by default.
[    77.740] (II) "dbe" will be loaded by default.
[    77.740] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    77.740] (II) "record" will be loaded by default.
[    77.740] (II) "dri" will be loaded by default.
[    77.740] (II) "dri2" will be loaded by default.
[    77.740] (II) LoadModule: "glx"
[    77.741] (II) Loading /usr/lib/xorg/extra-modules/modules/extensions/libglx.so
[    77.741] (II) Module glx: vendor="FireGL - ATI Technologies Inc."
[    77.741] 	compiled for 7.6.0, module version = 1.0.0
[    77.741] (II) Loading extension GLX
[    77.741] (II) LoadModule: "extmod"
[    77.742] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    77.742] (II) Module extmod: vendor="X.Org Foundation"
[    77.742] 	compiled for 1.9.0, module version = 1.0.0
[    77.742] 	Module class: X.Org Server Extension
[    77.742] 	ABI class: X.Org Server Extension, version 4.0
[    77.742] (II) Loading extension MIT-SCREEN-SAVER
[    77.742] (II) Loading extension XFree86-VidModeExtension
[    77.742] (II) Loading extension XFree86-DGA
[    77.742] (II) Loading extension DPMS
[    77.742] (II) Loading extension XVideo
[    77.742] (II) Loading extension XVideo-MotionCompensation
[    77.742] (II) Loading extension X-Resource
[    77.742] (II) LoadModule: "dbe"
[    77.742] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    77.742] (II) Module dbe: vendor="X.Org Foundation"
[    77.742] 	compiled for 1.9.0, module version = 1.0.0
[    77.742] 	Module class: X.Org Server Extension
[    77.742] 	ABI class: X.Org Server Extension, version 4.0
[    77.742] (II) Loading extension DOUBLE-BUFFER
[    77.742] (II) LoadModule: "record"
[    77.742] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    77.743] (II) Module record: vendor="X.Org Foundation"
[    77.743] 	compiled for 1.9.0, module version = 1.13.0
[    77.743] 	Module class: X.Org Server Extension
[    77.743] 	ABI class: X.Org Server Extension, version 4.0
[    77.743] (II) Loading extension RECORD
[    77.743] (II) LoadModule: "dri"
[    77.743] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    77.743] (II) Module dri: vendor="X.Org Foundation"
[    77.743] 	compiled for 1.9.0, module version = 1.0.0
[    77.743] 	ABI class: X.Org Server Extension, version 4.0
[    77.743] (II) Loading extension XFree86-DRI
[    77.743] (II) LoadModule: "dri2"
[    77.743] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    77.743] (II) Module dri2: vendor="X.Org Foundation"
[    77.743] 	compiled for 1.9.0, module version = 1.2.0
[    77.743] 	ABI class: X.Org Server Extension, version 4.0
[    77.743] (II) Loading extension DRI2
[    77.744] (II) LoadModule: "fglrx"
[    77.744] (II) Loading /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so
[    77.763] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[    77.763] 	compiled for 1.4.99.906, module version = 8.78.30
[    77.763] 	Module class: X.Org Video Driver
[    77.763] (II) Loading sub module "fglrxdrm"
[    77.763] (II) LoadModule: "fglrxdrm"
[    77.763] (II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    77.764] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    77.764] 	compiled for 1.8.99.905, module version = 8.78.30
[    77.764] (II) ATI Proprietary Linux Driver Version Identifier:8.78.30
[    77.764] (II) ATI Proprietary Linux Driver Release Identifier: 8.78.3                               
[    77.764] (II) ATI Proprietary Linux Driver Build Date: Sep 20 2010 21:31:08
[    77.764] (--) using VT number 8

[    77.771] (WW) Falling back to old probe method for fglrx
[    77.775] (II) Loading PCS database from /etc/ati/amdpcsdb
[    77.776] (--) Chipset Supported AMD Graphics Processor (0x9553) found
[    77.776] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
[    77.776] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[    77.776] (II) AMD Video driver is signed
[    77.776] (II) fglrx(0): pEnt->device->identifier=0xacdf90
[    77.777] (II) fglrx(0): === [xdl_x760_atiddxPreInit] === begin
[    77.777] (II) Loading sub module "vgahw"
[    77.777] (II) LoadModule: "vgahw"
[    77.777] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    77.777] (II) Module vgahw: vendor="X.Org Foundation"
[    77.777] 	compiled for 1.9.0, module version = 0.1.0
[    77.777] 	ABI class: X.Org Video Driver, version 8.0
[    77.777] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[    77.777] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    77.777] (==) fglrx(0): Default visual is TrueColor
[    77.777] (==) fglrx(0): RGB weight 888
[    77.777] (II) fglrx(0): Using 8 bits per RGB 
[    77.777] (==) fglrx(0): Buffer Tiling is ON
[    77.777] (II) Loading sub module "fglrxdrm"
[    77.777] (II) LoadModule: "fglrxdrm"
[    77.778] (II) Reloading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    77.780] ukiDynamicMajor: failed to open /proc/ati/major
[    77.780] ukiDynamicMajor: failed to open /proc/ati/major
[    77.780] (==) fglrx(0): NoAccel = NO
[    77.780] (==) fglrx(0): ATI 2D Acceleration Architecture enabled
[    77.780] (--) fglrx(0): Chipset: "ATI Mobility Radeon HD 4500 Series" (Chipset = 0x9553)
[    77.780] (--) fglrx(0): (PciSubVendor = 0x1043, PciSubDevice = 0x1b32)
[    77.780] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
[    77.780] (--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
[    77.780] (--) fglrx(0): MMIO registers at 0xfdef0000
[    77.780] (--) fglrx(0): I/O port at 0x0000d800
[    77.780] (==) fglrx(0): ROM-BIOS at 0x000c0000
[    77.783] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
[    77.783] (EE) fglrx(0): ACPI: DRM connection failed
[    77.874] (II) Loading sub module "vbe"
[    77.875] (II) LoadModule: "vbe"
[    77.875] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    77.875] (II) Module vbe: vendor="X.Org Foundation"
[    77.875] 	compiled for 1.9.0, module version = 1.1.0
[    77.875] 	ABI class: X.Org Video Driver, version 8.0
[    77.875] (II) fglrx(0): VESA BIOS detected
[    77.875] (II) fglrx(0): VESA VBE Version 3.0
[    77.876] (II) fglrx(0): VESA VBE Total Mem: 16384 kB
[    77.876] (II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
[    77.876] (II) fglrx(0): VESA VBE OEM Software Rev: 11.20
[    77.876] (II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
[    77.876] (II) fglrx(0): VESA VBE OEM Product: M92
[    77.876] (II) fglrx(0): VESA VBE OEM Product Rev: 01.00
[    77.913] (II) fglrx(0): ATI Video BIOS revision 9 or later detected
[    77.913] (--) fglrx(0): Video RAM: 524288 kByte, Type: DDR2
[    77.913] (II) fglrx(0): PCIE card detected
[    77.914] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[    77.914] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[    77.914] (EE) fglrx(0): ACPI: DRM connection failed
[    77.914] (WW) fglrx(0): Hasn't establisted DRM connection
[    77.914] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x20000000)
[    77.914] (WW) fglrx(0): No DRM connection for driver fglrx.
[    77.914] (II) fglrx(0): RandR 1.2 support is enabled!
[    77.914] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[    77.914] (==) fglrx(0): Center Mode is disabled 
[    77.914] (II) Loading sub module "fb"
[    77.914] (II) LoadModule: "fb"
[    77.914] (II) Loading /usr/lib/xorg/modules/libfb.so
[    77.915] (II) Module fb: vendor="X.Org Foundation"
[    77.915] 	compiled for 1.9.0, module version = 1.0.0
[    77.915] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    77.915] (==) fglrx(0): Active stereo disabled
[    77.915] (II) Loading sub module "ddc"
[    77.915] (II) LoadModule: "ddc"
[    77.915] (II) Module "ddc" already built-in
[    78.064] (II) fglrx(0): Output LVDS using monitor section 0-LVDS
[    78.064] (**) fglrx(0): Option "PreferredMode" "1366x768"
[    78.064] (**) fglrx(0): Option "Position" "0 0"
[    78.064] (**) fglrx(0): Option "Disable" "false"
[    78.064] (**) fglrx(0): Option "Rotate" "normal"
[    78.064] (**) fglrx(0): Option "TargetRefresh" "60"
[    78.064] (II) fglrx(0): Output DFP1 using monitor section 0-DFP1
[    78.064] (**) fglrx(0): Option "PreferredMode" "1366x768"
[    78.064] (**) fglrx(0): Option "Position" "0 0"
[    78.064] (**) fglrx(0): Option "Disable" "false"
[    78.064] (**) fglrx(0): Option "Rotate" "normal"
[    78.064] (**) fglrx(0): Option "TargetRefresh" "60"
[    78.064] (II) fglrx(0): Output CRT1 has no monitor section
[    78.065] (II) Loading sub module "ddc"
[    78.065] (II) LoadModule: "ddc"
[    78.065] (II) Module "ddc" already built-in
[    78.065] (II) fglrx(0): Connected Display0: LVDS
[    78.065] (II) fglrx(0): Display0 EDID data ---------------------------
[    78.065] (II) fglrx(0): Manufacturer: AUO  Model: 103c  Serial#: 0
[    78.065] (II) fglrx(0): Year: 2008  Week: 1
[    78.065] (II) fglrx(0): EDID Version: 1.3
[    78.065] (II) fglrx(0): Digital Display Input
[    78.065] (II) fglrx(0): Max Image Size [cm]: horiz.: 31  vert.: 17
[    78.065] (II) fglrx(0): Gamma: 2.20
[    78.065] (II) fglrx(0): No DPMS capabilities specified
[    78.065] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    78.065] (II) fglrx(0): First detailed timing is preferred mode
[    78.065] (II) fglrx(0): redX: 0.610 redY: 0.355   greenX: 0.333 greenY: 0.610
[    78.065] (II) fglrx(0): blueX: 0.152 blueY: 0.100   whiteX: 0.313 whiteY: 0.329
[    78.065] (II) fglrx(0): Manufacturer's mask: 0
[    78.065] (II) fglrx(0): Supported detailed timing:
[    78.065] (II) fglrx(0): clock: 72.0 MHz   Image Size:  309 x 173 mm
[    78.065] (II) fglrx(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1494 h_border: 0
[    78.065] (II) fglrx(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 803 v_border: 0
[    78.065] (II) fglrx(0): Unknown vendor-specific block f
[    78.065] (II) fglrx(0):  AUO
[    78.065] (II) fglrx(0):  B140XW01 V0
[    78.065] (II) fglrx(0): EDID (in hex):
[    78.065] (II) fglrx(0): 	00ffffffffffff0006af3c1000000000
[    78.065] (II) fglrx(0): 	01120103801f11780a45259c5b559c27
[    78.065] (II) fglrx(0): 	19505400000001010101010101010101
[    78.065] (II) fglrx(0): 	010101010101201c5680500023303020
[    78.065] (II) fglrx(0): 	360035ad100000180000000f00000000
[    78.065] (II) fglrx(0): 	00000000000000000020000000fe0041
[    78.065] (II) fglrx(0): 	554f0a202020202020202020000000fe
[    78.065] (II) fglrx(0): 	004231343058573031205630200a0040
[    78.065] (II) fglrx(0): End of Display0 EDID data --------------------
[    78.240] (II) fglrx(0): EDID vendor "AUO", prod id 4156
[    78.240] (II) fglrx(0): Printing DDC gathered Modelines:
[    78.240] (II) fglrx(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[    78.240] (II) fglrx(0): Output LVDS connected
[    78.240] (II) fglrx(0): Output DFP1 disconnected
[    78.240] (II) fglrx(0): Output CRT1 disconnected
[    78.240] (II) fglrx(0): Using user preference for initial modes
[    78.240] (II) fglrx(0): Output LVDS using initial mode 1366x768
[    78.240] (II) fglrx(0): Display dimensions: (310, 170) mm
[    78.240] (II) fglrx(0): DPI set to (111, 114)
[    78.240] (II) fglrx(0): Adapter ATI Mobility Radeon HD 4500 Series has 2 configurable heads and 1 displays connected.
[    78.240] (==) fglrx(0):  PseudoColor visuals disabled
[    78.240] (II) Loading sub module "ramdac"
[    78.240] (II) LoadModule: "ramdac"
[    78.240] (II) Module "ramdac" already built-in
[    78.240] (==) fglrx(0): NoDRI = NO
[    78.240] (==) fglrx(0): Capabilities: 0x00000000
[    78.240] (==) fglrx(0): CapabilitiesEx: 0x00000000
[    78.240] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[    78.240] (==) fglrx(0): UseFastTLS=0
[    78.240] (==) fglrx(0): BlockSignalsOnLock=1
[    78.240] (--) Depth 24 pixmap format is 32 bpp
[    78.241] (EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
[    78.241] (WW) fglrx(0): ***********************************************************
[    78.241] (WW) fglrx(0): * DRI initialization failed                               *
[    78.241] (WW) fglrx(0): * kernel module (fglrx.ko) may be missing or incompatible *
[    78.241] (WW) fglrx(0): * 2D and 3D acceleration disabled                         *
[    78.241] (WW) fglrx(0): ***********************************************************
[    78.241] (II) fglrx(0): FBADPhys: 0xf00000000 FBMappedSize: 0x10000000
[    78.305] (II) fglrx(0): FBMM initialized for area (0,0)-(1600,8191)
[    78.305] (II) fglrx(0): FBMM auto alloc for area (0,0)-(1600,1600) (front color buffer - assumption)
[    78.305] (II) fglrx(0): Largest offscreen area available: 1600 x 6591
[    78.305] (==) fglrx(0): Backing store disabled
[    78.305] (II) Loading extension FGLRXEXTENSION
[    78.305] (==) fglrx(0): DPMS enabled
[    78.306] (II) fglrx(0): Initialized in-driver Xinerama extension
[    78.306] (WW) fglrx(0): Textured Video not supported without DRI enabled.
[    78.306] (II) LoadModule: "glesx"
[    78.306] (II) Loading /usr/lib/xorg/extra-modules/modules/glesx.so
[    78.307] (II) Module glesx: vendor="X.Org Foundation"
[    78.307] 	compiled for 1.8.99.905, module version = 1.0.0
[    78.307] (II) Loading extension GLESX
[    78.307] (II) fglrx(0): GLESX enableFlags = 512
[    78.307] (II) fglrx(0): Acceleration enabled
[    78.307] (II) LoadModule: "amdxmm"
[    78.307] (II) Loading /usr/lib/xorg/extra-modules/modules/amdxmm.so
[    78.307] (II) Module amdxmm: vendor="X.Org Foundation"
[    78.307] 	compiled for 1.8.99.905, module version = 1.0.0
[    78.307] (EE) fglrx(0): XMM failed to open CMMQS connection.
[    78.307] (EE) fglrx(0): XMM failed to initialize
[    78.307] (WW) fglrx(0): No XV video playback available
[    78.307] (II) fglrx(0): Enable composite support successfully
[    78.307] (==) fglrx(0): Silken mouse enabled
[    78.308] (==) fglrx(0): Using HW cursor of display infrastructure!
[    78.308] (II) fglrx(0): Disabling in-server RandR and enabling in-driver RandR 1.2.
[    78.308] (II) fglrx(0): 'LVDS LCD' ConnectorType, abstracted as 'Panel'
[    78.308] (II) fglrx(0): 'eDP LCD' ConnectorType, abstracted as 'Panel'
[    78.356] (II) fglrx(0): User Preference Output LVDS using refresh rate 60.0 Hz.
[    79.302] (--) RandR disabled
[    79.302] (II) Initializing built-in extension Generic Event Extension
[    79.302] (II) Initializing built-in extension SHAPE
[    79.302] (II) Initializing built-in extension MIT-SHM
[    79.302] (II) Initializing built-in extension XInputExtension
[    79.302] (II) Initializing built-in extension XTEST
[    79.302] (II) Initializing built-in extension BIG-REQUESTS
[    79.302] (II) Initializing built-in extension SYNC
[    79.302] (II) Initializing built-in extension XKEYBOARD
[    79.302] (II) Initializing built-in extension XC-MISC
[    79.302] (II) Initializing built-in extension SECURITY
[    79.302] (II) Initializing built-in extension XINERAMA
[    79.302] (II) Initializing built-in extension XFIXES
[    79.302] (II) Initializing built-in extension RENDER
[    79.302] (II) Initializing built-in extension RANDR
[    79.302] (II) Initializing built-in extension COMPOSITE
[    79.302] (II) Initializing built-in extension DAMAGE
[    79.302] (II) Initializing built-in extension GESTURE
[    79.305] [glesx] __glESXExtensionInit: No GL ES2.0 capable screen found!
[    79.309] 
Backtrace:
[    79.309] 0: /usr/bin/X (xorg_backtrace+0x28) [0x45c5a8]
[    79.309] 1: /usr/bin/X (0x400000+0x5a87d) [0x45a87d]
[    79.309] 2: /lib/libpthread.so.0 (0x7f5a4cdd7000+0xfb40) [0x7f5a4cde6b40]
[    79.309] 3: /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so (xdl_x760_swlDriOpenConnection+0x3a) [0x7f5a499778aa]
[    79.309] 4: /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so (swlDriOpenConnection+0xd) [0x7f5a498afa8d]
[    79.309] 5: /usr/lib/xorg/extra-modules/modules/extensions/libglx.so (0x7f5a4ae68000+0x1a163) [0x7f5a4ae82163]
[    79.309] 6: /usr/lib/xorg/extra-modules/modules/extensions/libglx.so (0x7f5a4ae68000+0x1c325) [0x7f5a4ae84325]
[    79.309] 7: /usr/bin/X (InitExtensions+0x89) [0x4945f9]
[    79.310] 8: /usr/bin/X (0x400000+0x216d5) [0x4216d5]
[    79.310] 9: /lib/libc.so.6 (__libc_start_main+0xfe) [0x7f5a4bd42d8e]
[    79.310] 10: /usr/bin/X (0x400000+0x21409) [0x421409]
[    79.310] **Segmentation fault at address 0xa0**
[    79.310] 
**Caught signal 11 (Segmentation fault). Server aborting**
[    79.310] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[    79.310] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    79.310] 
[    79.855] (EE) fglrx(0): firegl_SetSuspendResumeState FAILED -9.
[    79.861]  ddxSigGiveUp: Closing log
```

Problem seemed to be fglrx driver, so I finally decided to get rid of it, following [these instructions]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch"), but there seemed to be a problem with the installation.

```
timo@doppelhirn:~$ sudo apt-get remove --purge xorg-driver-fglrx fglrx*
[sudo] password for timo: 
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Statusinformationen werden eingelesen... Fertig
Hinweis: »fglrx-modaliases« wird für regulären Ausdruck »fglrx*« gewählt.
Hinweis: »fglrx« wird für regulären Ausdruck »fglrx*« gewählt.
Hinweis: »fglrx-amdcccle« wird für regulären Ausdruck »fglrx*« gewählt.
Hinweis: »fglrx-driver« wird für regulären Ausdruck »fglrx*« gewählt.
Hinweis: »fglrx-kernel-source« wird für regulären Ausdruck »fglrx*« gewählt.
Hinweis: »xfree86-driver-fglrx« wird für regulären Ausdruck »fglrx*« gewählt.
Hinweis: »xorg-driver-fglrx« wird für regulären Ausdruck »fglrx*« gewählt.
Hinweis: »fglrx-control« wird für regulären Ausdruck »fglrx*« gewählt.
Hinweis: »fglrx-control-qt2« wird für regulären Ausdruck »fglrx*« gewählt.
Hinweis: »fglrx-dev« wird für regulären Ausdruck »fglrx*« gewählt.
Hinweis: »fglrx-driver-dev« wird für regulären Ausdruck »fglrx*« gewählt.
Hinweis: »xfree86-driver-fglrx-dev« wird für regulären Ausdruck »fglrx*« gewählt.
Hinweis: »xorg-driver-fglrx-dev« wird für regulären Ausdruck »fglrx*« gewählt.
Paket fglrx-amdcccle ist nicht installiert, wird also auch nicht entfernt.
Paket fglrx-dev ist nicht installiert, wird also auch nicht entfernt.
Die folgenden Pakete werden ENTFERNT:
  fglrx* fglrx-modaliases* xorg-driver-fglrx*
0 aktualisiert, 0 neu installiert, 3 zu entfernen und 12 nicht aktualisiert.
Nach dieser Operation werden 108MB Plattenplatz freigegeben.
Möchten Sie fortfahren [J/n]? j
(Lese Datenbank ... 444767 Dateien und Verzeichnisse sind derzeit installiert.)
Entferne fglrx ...
Removing all DKMS Modules
Done.
update-alternatives: Verwende /usr/lib/mesa/ld.so.conf, um /etc/ld.so.conf.d/GL.conf (gl_conf) in Auto-Modus bereitzustellen.
dpkg-divert: Keine Übereinstimmung mit Paket
  beim Entfernen von »Umleitung von /usr/lib/libGL.so.1.2 zu /usr/lib/fglrx/libGL.so.1.2.xlibmesa durch fglrx«
  »Umleitung von /usr/lib/libGL.so.1.2 zu /usr/lib/fglrx/libGL.so.1.2.xlibmesa durch xorg-driver-fglrx« gefunden
dpkg: Fehler beim Bearbeiten von fglrx (--purge):
 Unterprozess installiertes post-removal-Skript gab den Fehlerwert 2 zurück
Entferne fglrx-modaliases ...
Entferne xorg-driver-fglrx ...
Lösche Konfigurationsdateien von xorg-driver-fglrx ...
Verarbeite Trigger für python-gmenu ...
Rebuilding /usr/share/applications/desktop.de_DE.utf8.cache...
Verarbeite Trigger für libc-bin ...
ldconfig deferred processing now taking place
Verarbeite Trigger für ureadahead ...
ureadahead will be reprofiled on next reboot
Verarbeite Trigger für man-db ...
Verarbeite Trigger für python-support ...
Fehler traten auf beim Bearbeiten von:
 fglrx
E: Sub-process /usr/bin/dpkg returned an error code (1)
timo@doppelhirn:~$ sudo /usr/share/ati/fglrx-uninstall.sh  # (if it exists)
sudo: /usr/share/ati/fglrx-uninstall.sh: command not found
timo@doppelhirn:~$ sudo apt-get remove --purge fglrx*
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Statusinformationen werden eingelesen... Fertig
Hinweis: »fglrx-modaliases« wird für regulären Ausdruck »fglrx*« gewählt.
Hinweis: »fglrx« wird für regulären Ausdruck »fglrx*« gewählt.
Hinweis: »fglrx-amdcccle« wird für regulären Ausdruck »fglrx*« gewählt.
Hinweis: »fglrx-driver« wird für regulären Ausdruck »fglrx*« gewählt.
Hinweis: »fglrx-kernel-source« wird für regulären Ausdruck »fglrx*« gewählt.
Hinweis: »xfree86-driver-fglrx« wird für regulären Ausdruck »fglrx*« gewählt.
Hinweis: »xorg-driver-fglrx« wird für regulären Ausdruck »fglrx*« gewählt.
Hinweis: »fglrx-control« wird für regulären Ausdruck »fglrx*« gewählt.
Hinweis: »fglrx-control-qt2« wird für regulären Ausdruck »fglrx*« gewählt.
Hinweis: »fglrx-dev« wird für regulären Ausdruck »fglrx*« gewählt.
Hinweis: »fglrx-driver-dev« wird für regulären Ausdruck »fglrx*« gewählt.
Hinweis: »xfree86-driver-fglrx-dev« wird für regulären Ausdruck »fglrx*« gewählt.
Hinweis: »xorg-driver-fglrx-dev« wird für regulären Ausdruck »fglrx*« gewählt.
Paket fglrx-modaliases ist nicht installiert, wird also auch nicht entfernt.
Paket fglrx-amdcccle ist nicht installiert, wird also auch nicht entfernt.
Paket fglrx-dev ist nicht installiert, wird also auch nicht entfernt.
Die folgenden Pakete werden ENTFERNT:
  fglrx
0 aktualisiert, 0 neu installiert, 1 zu entfernen und 12 nicht aktualisiert.
1 nicht vollständig installiert oder entfernt.
Nach dieser Operation werden 108MB Plattenplatz freigegeben.
Möchten Sie fortfahren [J/n]? j
(Lese Datenbank ... 444596 Dateien und Verzeichnisse sind derzeit installiert.)
Entferne fglrx ...
dpkg-divert: Keine Übereinstimmung mit Paket
  beim Entfernen von »Umleitung von /usr/lib/libGL.so.1.2 zu /usr/lib/fglrx/libGL.so.1.2.xlibmesa durch fglrx«
  »Umleitung von /usr/lib/libGL.so.1.2 zu /usr/lib/fglrx/libGL.so.1.2.xlibmesa durch xorg-driver-fglrx« gefunden
dpkg: Fehler beim Bearbeiten von fglrx (--remove):
 Unterprozess installiertes post-removal-Skript gab den Fehlerwert 2 zurück
Verarbeite Trigger für ureadahead ...
Fehler traten auf beim Bearbeiten von:
 fglrx
E: Sub-process /usr/bin/dpkg returned an error code (1)
timo@doppelhirn:~$ sudo touch /usr/lib/fglrx/libGL.so.1.2.xlibmesa
timo@doppelhirn:~$ man ln
timo@doppelhirn:~$ sudo ln -s /usr/lib/fglrx/libGL.so.1.2.xlibmesa /usr/lib/libGL.so.1.2
timo@doppelhirn:~$ sudo apt-get remove --purge fglrx*
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Statusinformationen werden eingelesen... Fertig
Hinweis: »fglrx-modaliases« wird für regulären Ausdruck »fglrx*« gewählt.
Hinweis: »fglrx« wird für regulären Ausdruck »fglrx*« gewählt.
Hinweis: »fglrx-amdcccle« wird für regulären Ausdruck »fglrx*« gewählt.
Hinweis: »fglrx-driver« wird für regulären Ausdruck »fglrx*« gewählt.
Hinweis: »fglrx-kernel-source« wird für regulären Ausdruck »fglrx*« gewählt.
Hinweis: »xfree86-driver-fglrx« wird für regulären Ausdruck »fglrx*« gewählt.
Hinweis: »xorg-driver-fglrx« wird für regulären Ausdruck »fglrx*« gewählt.
Hinweis: »fglrx-control« wird für regulären Ausdruck »fglrx*« gewählt.
Hinweis: »fglrx-control-qt2« wird für regulären Ausdruck »fglrx*« gewählt.
Hinweis: »fglrx-dev« wird für regulären Ausdruck »fglrx*« gewählt.
Hinweis: »fglrx-driver-dev« wird für regulären Ausdruck »fglrx*« gewählt.
Hinweis: »xfree86-driver-fglrx-dev« wird für regulären Ausdruck »fglrx*« gewählt.
Hinweis: »xorg-driver-fglrx-dev« wird für regulären Ausdruck »fglrx*« gewählt.
Paket fglrx-modaliases ist nicht installiert, wird also auch nicht entfernt.
Paket fglrx-amdcccle ist nicht installiert, wird also auch nicht entfernt.
Paket fglrx-dev ist nicht installiert, wird also auch nicht entfernt.
Die folgenden Pakete werden ENTFERNT:
  fglrx
0 aktualisiert, 0 neu installiert, 1 zu entfernen und 12 nicht aktualisiert.
1 nicht vollständig installiert oder entfernt.
Nach dieser Operation werden 108MB Plattenplatz freigegeben.
Möchten Sie fortfahren [J/n]? j
(Lese Datenbank ... 444596 Dateien und Verzeichnisse sind derzeit installiert.)
Entferne fglrx ...
[B]dpkg-divert: Keine Übereinstimmung mit Paket
  beim Entfernen von »Umleitung von /usr/lib/libGL.so.1.2 zu /usr/lib/fglrx/libGL.so.1.2.xlibmesa durch fglrx«[/B]
  »Umleitung von /usr/lib/libGL.so.1.2 zu /usr/lib/fglrx/libGL.so.1.2.xlibmesa durch xorg-driver-fglrx« gefunden
dpkg: Fehler beim Bearbeiten von fglrx (--remove):
 Unterprozess installiertes post-removal-Skript gab den Fehlerwert 2 zurück
Verarbeite Trigger für ureadahead ...
Fehler traten auf beim Bearbeiten von:
 fglrx
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Sorry for the German, basically it says that one file (/usr/lib/fglrx/libGL.so.1.2.xlibmesa) and one link to that file (/usr/lib/libGL.so.1.2) are missing.

So, I think I'll have to find a way to get rid of the fglrx driver and use the open source driver instead - and continue from there.

---

### Post by Timokl on 2011-03-08
Hoorray, I got rid of the fglrx driver. There was one slight issue, as some proprietary bits were left in xorg.conf. Deleting xorg.conf and starting the X-server from command line got everything up and running.

---

### Post by Timokl on 2011-03-13
As acpi=off worked for me, I have marked this Thread as solved - but I'm a bit unsatisfied about this solution.

---

### Post by Timokl on 2011-03-13
Quite interestingly - another solution was to boot with *initrd*. ACPI now seems to be working ...

---

