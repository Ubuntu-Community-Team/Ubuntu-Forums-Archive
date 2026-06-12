---
title: "No Screen Resolution Past 800x600 on 9.10 Karmic"
date: 2009-11-07
forum: General Help
---

### Post by twallace on 2009-11-07
If anyone knows how to permanently get my screen resolution back on my Toshiba laptop after installing the new Karmic 9.10 please let me know ASAP!!!!!!!!!:mad:

---

### Post by twallace on 2009-11-08
Anybody????

I have been trying some of the stuff suggested on the board with no success...

HELP!!!

---

### Post by Dark9204 on 2009-11-08
Why not just google it? There are lots of pages about this.
anyway, Have a look at: [http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

or

[http://www.ardoros.com/2008/07/how-to-change-x-window-configuration.html](http://www.ardoros.com/2008/07/how-to-change-x-window-configuration.html)


Backup X Config
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

Edit it:
sudo gedit /etc/X11/xorg.conf

Here is an example:
Section "Screen"
    Identifier    "Default Screen"
    Device        "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Monitor        "CM752ET"
    DefaultDepth    16
    SubSection "Display"
        Depth        16
        Modes      "1024x768_75.00"
    EndSubSection
EndSection

Good luck!

---

### Post by twallace on 2009-11-09
Think I may have found a guy who can actually help on this, will keep everyone posted if we have success...

---

### Post by twallace on 2009-11-12
Well still not able to use my laptop since installing 9.10 with the small screen resolution. Thought I was going to hear back from a guy that responded from another forum but nothing so far, actually thinking of putting XP back on it... :-(

---

### Post by Mark Phelps on 2009-11-12
The answer depends a lot on what video chip the laptop is using.

Run the command "sudo lspci" and look for a line about a video adapter.  That will tell you what make and model you have.

Could be that you have a chip that is not well supported in 9.10.

---

### Post by twallace on 2009-11-12
Here is what I have, now what?

00:00.0 Host bridge: ALi Corporation M1672 Northbridge [CyberALADDiN-P4]
00:01.0 PCI bridge: ALi Corporation PCI to AGP Controller
00:04.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:09.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0c.0 USB Controller: NEC Corporation USB (rev 43)
00:0c.1 USB Controller: NEC Corporation USB (rev 43)
00:0c.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
00:10.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
00:11.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 33)
00:12.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 05)
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade XPAi1 (rev 82)

---

### Post by twallace on 2009-11-14
Laptop still unusable and still no fix from the Forum...

---

### Post by Mark Phelps on 2009-11-14
Since you don't have one of the more common Nvidia, ATI, or Intel chipsets, I would suggest that you do a search in the video subforum for threads on the Trident Microsystems video controller -- to see if anyone else has worked a solution for this.

---

### Post by Roger Allott on 2009-11-14
I had exactly this problem with a fresh install of xubuntu 9.10 on a Toshiba laptop.

To see how I resolved the problem, look through this thread from another forum:
[http://www.rushmessageboard.com/cpmb/index.php?showtopic=33283]("http://www.rushmessageboard.com/cpmb/index.php?showtopic=33283")

---

### Post by e.m.fields on 2009-11-16
Same issues here.
Upgrade to Karmic produces low resolution settings, which cannot be changed in in Display settings, and no monitors detected.

System - 
Ubuntu Karmic 9.10
MSI WindPC with integrated Intel 82945G/GZ video chip.

Attempted to manually set resolution in xorg.conf with no results yet.
Anyone find a solution, please post!

---

### Post by arnab_das on 2009-11-16
install the latest nvidia drivers to solve the problem.

if you need a guide for the installation, there's one here:
[http://thoughtsndreams.wordpress.com/2009/10/23/installing-nvidia-drivers-in-ubuntu/](http://thoughtsndreams.wordpress.com/2009/10/23/installing-nvidia-drivers-in-ubuntu/)

---

### Post by esr on 2009-11-24
This is not an nVidia-specific problem.  I have encountered it using an Intel 965 that was complewtely supported in 9.04.

My issue involved an Intel 965 card driving a Samsung 1100DF. The display configurator showed no resolutions above 1280x1024. I knew this was wrong because under 9.04 I'd been happily running at 2048x1536 resolution.

The solution was to generate a 2048x1536 modeline using cvt, then paste it into my x11.conf.

I don't think this is a driver issue.  I think X is failing to process the EDID info from the monitor properly and not generating anything other than bog-standard modelines.

I've included my corrected conf as an attachment...I think.  (The attachment manager on this forum software is very poorly designed.)

No, the attachment didn't succeed, and I don't think repeating the procedure from the edit sequence is going to help.

---

### Post by e.m.fields on 2009-11-24
Thanks for the response, esr.

I also had this problem on a non-nVidia card.  I can't remember the chip number offhand, but it was an integrated Intel video chip.

Is this "cvt" an xorg.conf generator?

---

### Post by esr on 2009-11-24
>Is this "cvt" an xorg.conf generator?

Yes, it is.

All the people that rushed to blame this on proprietary drivers need to be slapped, hard.  This one is not nVidia's fault; it's a fuckup either at X.org or in Ubuntu's system integration.

(I have some creds in this area.  I maintained the XFree86 Video Timings HOWTO for many years. I am deeply disappointed that Ubuntu is regressing back towards the bad old days when having to hack custom modelines was normal.)

---

### Post by twallace on 2009-12-06
Well I thought leaving my laptop sit for awhile and then doing some updates would cure my resolution problem...

119 updates and half a day later on downloads I still only have 800x600 resolution!

Anyone???

---

### Post by Yellow Pasque on 2009-12-06
Post/pastebin your /var/log/Xorg.0.log

---

### Post by twallace on 2009-12-06
Still a Linux newbie, need a little more info on the last response...

---

### Post by Yellow Pasque on 2009-12-06
```
gedit /var/log/Xorg.0.log
```
Copy the file and paste it between [ code ][ /code ] blocks in a new post.

---

### Post by twallace on 2009-12-06
X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux terry-laptop 2.6.31-16-generic #52-Ubuntu SMP Thu Dec 3 22:00:22 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-16-generic root=UUID=d82c73e5-df0d-4287-88cd-91f4fe7525be ro quiet splash
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Dec  6 19:35:53 2009
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 5.0
    X.Org XInput driver : 4.0
    X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0:1:0:0) 1023:8820:1179:0001 Trident Microsystems CyberBlade XPAi1 rev 130, Mem @ 0xfc000000/33554432, 0xfbc00000/4194304, 0xf8000000/33554432, 0xf7ff8000/32768, BIOS @ 0x????????/65536
(==) Using default built-in configuration (30 lines)
(==) --- Start of built-in configuration ---
    Section "Device"
        Identifier    "Builtin Default trident Device 0"
        Driver    "trident"
    EndSection
    Section "Screen"
        Identifier    "Builtin Default trident Screen 0"
        Device    "Builtin Default trident Device 0"
    EndSection
    Section "Device"
        Identifier    "Builtin Default vesa Device 0"
        Driver    "vesa"
    EndSection
    Section "Screen"
        Identifier    "Builtin Default vesa Screen 0"
        Device    "Builtin Default vesa Device 0"
    EndSection
    Section "Device"
        Identifier    "Builtin Default fbdev Device 0"
        Driver    "fbdev"
    EndSection
    Section "Screen"
        Identifier    "Builtin Default fbdev Screen 0"
        Device    "Builtin Default fbdev Device 0"
    EndSection
    Section "ServerLayout"
        Identifier    "Builtin Default Layout"
        Screen    "Builtin Default trident Screen 0"
        Screen    "Builtin Default vesa Screen 0"
        Screen    "Builtin Default fbdev Screen 0"
    EndSection
(==) --- End of built-in configuration ---
(==) ServerLayout "Builtin Default Layout"
(**) |-->Screen "Builtin Default trident Screen 0" (0)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default trident Device 0"
(==) No monitor specified for screen "Builtin Default trident Screen 0".
    Using a default monitor configuration.
(**) |-->Screen "Builtin Default vesa Screen 0" (1)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default vesa Device 0"
(==) No monitor specified for screen "Builtin Default vesa Screen 0".
    Using a default monitor configuration.
(**) |-->Screen "Builtin Default fbdev Screen 0" (2)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default fbdev Device 0"
(==) No monitor specified for screen "Builtin Default fbdev Screen 0".
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
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
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
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
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
(II) LoadModule: "trident"
(II) Loading /usr/lib/xorg/modules/drivers//trident_drv.so
(II) Module trident: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.3.1
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
    compiled for 1.6.3, module version = 2.2.1
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers//fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 0.4.0
    ABI class: X.Org Video Driver, version 5.0
(II) TRIDENT: driver for Trident chipsets: tvga9000, tvga9000i, tvga8900c,
    tvga8900d, tvga9200cxr, tgui9400cxi, cyber9320, cyber9388, cyber9397,
    cyber9397dvd, cyber9520, cyber9525dvd, cyberblade/e4, tgui9420dgi,
    tgui9440agi, tgui9660, tgui9680, providia9682, providia9685,
    cyber9382, cyber9385, 3dimage975, 3dimage985, blade3d, cyberbladei7,
    cyberbladei7d, cyberbladei1, cyberbladei1d, cyberbladeAi1,
    cyberbladeAi1d, bladeXP, cyberbladeXPAi1, cyberbladeXP4, XP5
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 01@00:00:0
(WW) Falling back to old probe method for trident
(--) Assigning device section with no busID to primary device
(--) Chipset cyberbladeXPAi1 found
(II) resource ranges after xf86ClaimFixedResources() call:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux//libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 0.0.2
    ABI class: X.Org Video Driver, version 5.0
(EE) open /dev/fb0: No such file or directory
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] 0    0    0x000a0000 - 0x000affff (0x10000) MS[b]
    [5] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[b]
    [6] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[b]
    [7] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [8] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [9] 0    0    0x000003b0 - 0x000003bb (0xc) IS[b]
    [10] 0    0    0x000003c0 - 0x000003df (0x20) IS[b]
(II) Setting vga for screen 0.
(II) TRIDENT(0): Creating default Display subsection in Screen section
    "Builtin Default trident Screen 0" for depth/fbbpp 24/32
(==) TRIDENT(0): Depth 24, (--) framebuffer bpp 32
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 0.1.0
    ABI class: X.Org Video Driver, version 5.0
(II) TRIDENT(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(==) TRIDENT(0): RGB weight 888
(==) TRIDENT(0): Default visual is TrueColor
(==) TRIDENT(0): Using gamma correction (1.0, 1.0, 1.0)
(==) TRIDENT(0): Using XAA for acceleration
(==) TRIDENT(0): Linear framebuffer at 0xFC000000
(--) TRIDENT(0): IO registers at 0xFBC00000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.1.0
    ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org Video Driver, version 5.0
(II) TRIDENT(0): initializing int10
(II) TRIDENT(0): Primary V_BIOS segment is: 0xc000
(II) TRIDENT(0): VESA BIOS detected
(II) TRIDENT(0): VESA VBE Version 2.0
(II) TRIDENT(0): VESA VBE Total Mem: 32768 kB
(II) TRIDENT(0): VESA VBE OEM: Trident CYBER 8820
(II) TRIDENT(0): VESA VBE OEM Software Rev: 2.0
(II) TRIDENT(0): VESA VBE OEM Vendor: TRIDENT MICROSYSTEMS INC.
(II) TRIDENT(0): VESA VBE OEM Product: CYBER 8820
(II) TRIDENT(0): VESA VBE OEM Product Rev: IXT  7.1 (25.14)  
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
f000:20d1: 01 ILLEGAL EXTENDED X86 OPCODE!
(II) TRIDENT(0): VESA VBE DDC not supported
(--) TRIDENT(0): Revision is 152
(--) TRIDENT(0): Found CyberBladeXPAi1 chip
(--) TRIDENT(0): RAM type is SGRAM
(--) TRIDENT(0): Using HW cursor
(--) TRIDENT(0): VideoRAM: 24576 kByte
(--) TRIDENT(0): TFT Panel 1024x768 found
(--) TRIDENT(0): Memory Clock is 60.00 MHz
(==) TRIDENT(0): Min pixel clock is 12 MHz
(--) TRIDENT(0): Max pixel clock is 115 MHz
(II) TRIDENT(0): <default monitor>: Using default hsync range of 31.50-37.90 kHz
(II) TRIDENT(0): <default monitor>: Using default vrefresh range of 50.00-70.00 Hz
(WW) TRIDENT(0): Unable to estimate virtual size
(II) TRIDENT(0): Clock range:  12.00 to 115.00 MHz
(II) TRIDENT(0): Not using default mode "640x350" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "320x175" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "640x400" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "320x200" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "720x400" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "360x200" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "640x480" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "320x240" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "640x480" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "320x240" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "640x480" (hsync out of range)
(II) TRIDENT(0): Not using default mode "320x240" (hsync out of range)
(II) TRIDENT(0): Not using default mode "800x600" (hsync out of range)
(II) TRIDENT(0): Not using default mode "400x300" (hsync out of range)
(II) TRIDENT(0): Not using default mode "800x600" (hsync out of range)
(II) TRIDENT(0): Not using default mode "400x300" (hsync out of range)
(II) TRIDENT(0): Not using default mode "800x600" (hsync out of range)
(II) TRIDENT(0): Not using default mode "400x300" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1024x768" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "512x384" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "1024x768" (hsync out of range)
(II) TRIDENT(0): Not using default mode "512x384" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1024x768" (hsync out of range)
(II) TRIDENT(0): Not using default mode "512x384" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1024x768" (hsync out of range)
(II) TRIDENT(0): Not using default mode "512x384" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1024x768" (hsync out of range)
(II) TRIDENT(0): Not using default mode "512x384" (hsync out of range)
(II) TRIDENT(0): Removing mode (1152x864) larger than the LCD panel (1024x768)
(II) TRIDENT(0): Not using default mode "1152x864" (unknown reason)
(II) TRIDENT(0): Not using default mode "576x432" (hsync out of range)
(II) TRIDENT(0): Removing mode (1280x960) larger than the LCD panel (1024x768)
(II) TRIDENT(0): Not using default mode "1280x960" (unknown reason)
(II) TRIDENT(0): Not using default mode "640x480" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "640x480" (hsync out of range)
(II) TRIDENT(0): Removing mode (1280x1024) larger than the LCD panel (1024x768)
(II) TRIDENT(0): Not using default mode "1280x1024" (unknown reason)
(II) TRIDENT(0): Not using default mode "640x512" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "640x512" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "640x512" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "800x600" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "800x600" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "800x600" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "800x600" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "800x600" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "896x672" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "928x696" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "832x624" (hsync out of range)
(II) TRIDENT(0): Not using default mode "416x312" (hsync out of range)
(II) TRIDENT(0): Removing mode (1152x864) larger than the LCD panel (1024x768)
(II) TRIDENT(0): Not using default mode "1152x864" (unknown reason)
(II) TRIDENT(0): Not using default mode "576x432" (hsync out of range)
(II) TRIDENT(0): Removing mode (1152x864) larger than the LCD panel (1024x768)
(II) TRIDENT(0): Not using default mode "1152x864" (unknown reason)
(II) TRIDENT(0): Not using default mode "576x432" (hsync out of range)
(II) TRIDENT(0): Removing mode (1152x864) larger than the LCD panel (1024x768)
(II) TRIDENT(0): Not using default mode "1152x864" (unknown reason)
(II) TRIDENT(0): Not using default mode "576x432" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "576x432" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "576x432" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "576x432" (hsync out of range)
(II) TRIDENT(0): Removing mode (1360x768) larger than the LCD panel (1024x76
(II) TRIDENT(0): Not using default mode "1360x768" (unknown reason)
(II) TRIDENT(0): Not using default mode "680x384" (hsync out of range)
(II) TRIDENT(0): Removing mode (1360x768) larger than the LCD panel (1024x76
(II) TRIDENT(0): Not using default mode "1360x768" (unknown reason)
(II) TRIDENT(0): Not using default mode "680x384" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "700x525" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "700x525" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "700x525" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "700x525" (hsync out of range)
(II) TRIDENT(0): Removing mode (1440x900) larger than the LCD panel (1024x76
(II) TRIDENT(0): Not using default mode "1440x900" (unknown reason)
(II) TRIDENT(0): Not using default mode "720x450" (hsync out of range)
(II) TRIDENT(0): Removing mode (1600x1024) larger than the LCD panel (1024x76
(II) TRIDENT(0): Not using default mode "1600x1024" (unknown reason)
(II) TRIDENT(0): Not using default mode "800x512" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "840x525" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "840x525" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "840x525" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "840x525" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "840x525" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1920x1080" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "960x540" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1920x1200" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "960x600" (hsync out of range)
(II) TRIDENT(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(--) TRIDENT(0): Virtual size is 800x600 (pitch 800)
(**) TRIDENT(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) TRIDENT(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) TRIDENT(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) TRIDENT(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) TRIDENT(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) TRIDENT(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) TRIDENT(0): *Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) TRIDENT(0): Modeline "400x300"x60.3   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
(**) TRIDENT(0): *Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) TRIDENT(0): Modeline "400x300"x56.3   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz)
(**) TRIDENT(0): *Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) TRIDENT(0): Modeline "320x240"x60.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz)
(==) TRIDENT(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.2.1
    ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) UnloadModule: "vesa"
(II) Unloading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers//fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux//libfbdevhw.so
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] 0    0    0x000a0000 - 0x000affff (0x10000) MS[b](OprU)
    [5] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[b](OprU)
    [6] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[b](OprU)
    [7] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [8] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [9] 0    0    0x000003b0 - 0x000003bb (0xc) IS[b](OprU)
    [10] 0    0    0x000003c0 - 0x000003df (0x20) IS[b](OprU)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) TRIDENT(0): Initializing int10
(II) TRIDENT(0): Primary V_BIOS segment is: 0xc000
(II) TRIDENT(0): Overriding Horizontal timings.
(II) TRIDENT(0): Shadow on
(II) TRIDENT(0): H-timing shadow registers: 0xa3           0x00 0x84 0x94
(II) TRIDENT(0): H-timing registers:        0x7f 0x63 0x63 0x82 0x69 0x19
(II) TRIDENT(0): V-timing shadow registers: 0x24 0xf5 0x03 0x09           0x24 (0x0
(II) TRIDENT(0): V-timing registers:        0x72 0xf0 0x59 0x2d 0x57 0x00 0x00
(II) TRIDENT(0): Setting BIOS Mode Regs: 13 62 for: 800x600
(II) TRIDENT(0): Found Clock  65.00 n=219 m=23 k=1
(II) TRIDENT(0): Using 1447 scanlines of offscreen memory for area's 
(II) TRIDENT(0): Using 18615424 bytes of offscreen memory for linear (offset=0x63f380)
(II) TRIDENT(0): Using XFree86 Acceleration Architecture (XAA)
    Screen to screen bit blits
    Solid filled rectangles
    8x8 mono pattern filled rectangles
    Solid Horizontal and Vertical Lines
    Setting up tile and stipple cache:
        32 128x128 slots
        8 256x256 slots
(==) TRIDENT(0): Backing store disabled
(==) TRIDENT(0): Silken mouse enabled
(II) TRIDENT(0): DPMS enabled
(II) TRIDENT(0): Trident Video Flags: VID_ZOOM_INV  VID_OFF_SHIFT_4 
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
(II) AIGLX: Screen 0 is not DRI2 capable
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 2.2.5
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Video Bus
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event5"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device AlpsPS/2 ALPS GlidePoint
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.1.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(II) Synaptics touchpad driver version 1.1.2
(**) Option "Device" "/dev/input/event7"
(II) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
(II) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
(II) AlpsPS/2 ALPS GlidePoint: pressure range 0 - 127
(II) AlpsPS/2 ALPS GlidePoint: finger width range 0 - 0
(II) AlpsPS/2 ALPS GlidePoint: buttons: left right middle
(--) AlpsPS/2 ALPS GlidePoint: touchpad found
(**) AlpsPS/2 ALPS GlidePoint: always reports core events
(II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD)
(**) AlpsPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
(**) AlpsPS/2 ALPS GlidePoint: (accel) filter chain progression: 2.00
(**) AlpsPS/2 ALPS GlidePoint: (accel) filter stage 0: 20.00 ms
(**) AlpsPS/2 ALPS GlidePoint: (accel) set acceleration profile 0
(--) AlpsPS/2 ALPS GlidePoint: touchpad found
(II) config/hal: Adding input device PS/2 Mouse
(**) PS/2 Mouse: always reports core events
(**) PS/2 Mouse: Device: "/dev/input/event6"
(II) PS/2 Mouse: Found 3 mouse buttons
(II) PS/2 Mouse: Found x and y relative axes
(II) PS/2 Mouse: Configuring as mouse
(**) PS/2 Mouse: YAxisMapping: buttons 4 and 5
(**) PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "PS/2 Mouse" (type: MOUSE)
(**) PS/2 Mouse: (accel) keeping acceleration scheme 1
(**) PS/2 Mouse: (accel) filter chain progression: 2.00
(**) PS/2 Mouse: (accel) filter stage 0: 20.00 ms
(**) PS/2 Mouse: (accel) set acceleration profile 0
(II) PS/2 Mouse: initialized for relative axes.
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
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

---

### Post by Yellow Pasque on 2009-12-06
The virtual screen size is being set too low (800x600) because X isn't autodetecting it properly. Also, the autodetected horizsync looks low.

Here's a good sample /etc/X11/xorg.conf file to fix those issues:
[http://launchpadlibrarian.net/20399330/F%3A%5CX11_config%5Cxorg.conf](http://launchpadlibrarian.net/20399330/F%3A%5CX11_config%5Cxorg.conf)

---

### Post by twallace on 2009-12-06
Can you take me step by step to fix this? Like I said I am a newb...

---

### Post by Yellow Pasque on 2009-12-06
Go here: [http://launchpadlibrarian.net/20399330/F%3A%5CX11_config%5Cxorg.conf](http://launchpadlibrarian.net/20399330/F%3A%5CX11_config%5Cxorg.conf)
Select all and copy. Then, in the terminal:
```
cd /etc/X11/
sudo mv xorg.conf xorg.conf.bak  #if you don't have an existing xorg.conf, this will complain about file not found, that's okay
gksu gedit xorg.conf
```
Paste. Save. Quit. Reboot.

---

### Post by twallace on 2009-12-06
We are close!!!! Getting a screen complaining about Low Graphic Mode; I just click on the one saying allow for one session and manually changed the setting which now shows 1024x768. Changed it and VIOLA!!! First time I can use my whole screen again. Now how do we fix the Low Graphics thing coming up ever time?

---

### Post by Yellow Pasque on 2009-12-07
There are a lot of reports of benign "low graphics" messages lately. It has something to do with a recent X update. I'm sure it will be fixed soon because it affects a lot of people.

---

### Post by twallace on 2009-12-07
The error box I get says Ubuntu Runiing In Low Graphics Mode; Problem parsing Config file.

What a shame, this is totally killing the fast boot times they say 9.10 has, that was the main reason I upgraded from 9.04!

Well at least the laptop is usable again, THANX for the help!!!

---

### Post by twallace on 2009-12-07
Wonder if it has anything to do with the settings we put in, just noticed the refresh rate shows 0...

---

### Post by cecst on 2009-12-07
This very frustrating problem with resolution almost drove me to go back to 9.04, but who wants to reconfigure all the other things that need reconfiguring?  My Dell gx620 has an Intel Corporation 82945G/GZ Integrated Graphics Controller, but that turns out not to prevent the following solution.

Reasoning that the problem is failure to detect the available modes properly, and noting that /var/log/Xorg.0.log states that the modes are not detected because the horizontal and vertical frequencies were out of range, I followed the advice of Giblet5 in
  [http://ohioloco.ubuntuforums.org/showthread.php?t=1312107](http://ohioloco.ubuntuforums.org/showthread.php?t=1312107)
for setting the horizontal and vertical frequency ranges explictly in /etc/X11/xorg.conf.  Note that this can KILL YOUR MONITOR if you get the numbers wrong (at least the old ones that could not protect themselves), so be careful.  The correct fix would be to fix autodetection of these parameters, but I do not know how to do that.

First, I used the menu system built in my LCD monitor (Viewsonic model VS11756) to see what the model was. Then, I read the user manual for this
model to see that the horizontal frequency range was 24-82 Hz and the vertical frequency range was 40-75 Hz (with a warning not to exceed 75 Hz).

Then, I added the following to the Monitor section of /etc/X11/xorg.conf
  HorizSync       x1.0 - x2.0
  VertRefresh     y1.0 - y2.0
where x1-x2 and y1-y2, respectively are the ranges for horizontal and vertical frequencies, in Hz. Look in the specifications for your own monitor.  When I put in the exact values for my monitor, the X server would not start because of an out-of-range frequency error. I narrowed the horizontal frequency empirically from 24-82 to 30-60 and the vertical frequency from 50-75 to 58-62.  

This narrowed range enabled the X server to restart and also allowed use of the maximum resolution (1440x900).  The Information tab on the monitor showed that the required horizontal frequency was far from the maximum listed in the user manual:
     resolution 800x600:   horiz 37.8 Hz, vertical 60.3 Hz
     resolution 1440x900:  horiz 55.9 Hz, vertical 59.9 Hz

The X server is conveniently restarted with
  /etc/init.d/gdm restart

NB: if the server does not restart (ie, you see a black screen with a warning from the monitor), you DO NOT have to reboot the machine into safe mode. Just hit Control-Alt-F1 to Control-Alt-F5 or so, and your screen will switch to one of the line-oriented login screens that live in the ttys started a boot up.

---

### Post by cecst on 2009-12-07
This very frustrating problem with resolution almost drove me to go back to 9.04, but who wants to reconfigure all the other things that need reconfiguring? My Dell gx620 has an Intel Corporation 82945G/GZ Integrated Graphics Controller, but that turns out not to prevent the following solution. The solution below is better than the one from a month ago in [http://ubuntuforums.org/showthread.php?t=1306018](http://ubuntuforums.org/showthread.php?t=1306018) in that it allows use of the wide-screen 1440x900 mode (16:10 ratio) and another higher-res mode (1280x960 (4:3)) compared with the nomodeset option at boot time, which allowed only up to 1360x768 (16:9 ratio) albeit with no need to set the xorg.conf file as is required below.

Reasoning that the problem is failure to detect the available modes properly, and noting that /var/log/Xorg.0.log states that the modes are not detected because the horizontal and vertical frequencies were out of range, I followed the advice of Giblet5 in
[http://ohioloco.ubuntuforums.org/sho....php?t=1312107](http://ohioloco.ubuntuforums.org/sho....php?t=1312107)
for setting the horizontal and vertical frequency ranges explictly in /etc/X11/xorg.conf. Note that this can KILL YOUR MONITOR if you get the numbers wrong (at least the old ones that could not protect themselves), so be careful. The correct fix would be to fix autodetection of these parameters, but I do not know how to do that.

First, I used the menu system built in my LCD monitor (Viewsonic model VS11756) to see what the model was. Then, I read the user manual for this
model to see that the horizontal frequency range was 24-82 Hz and the vertical frequency range was 40-75 Hz (with a warning not to exceed 75 Hz).

Then, I added the following to the Monitor section of /etc/X11/xorg.conf
HorizSync x1.0 - x2.0
VertRefresh y1.0 - y2.0
where x1-x2 and y1-y2, respectively are the ranges for horizontal and vertical frequencies, in Hz. Look in the specifications for your own monitor. When I put in the exact values for my monitor, the X server would not start because of an out-of-range frequency error. I narrowed the horizontal frequency empirically from 24-82 to 30-60 and the vertical frequency from 50-75 to 58-62.

This narrowed range enabled the X server to restart and also allowed use of the maximum resolution (1440x900). The Information tab on the monitor showed that the required horizontal frequency was far from the maximum listed in the user manual:
resolution 800x600: horiz 37.8 Hz, vertical 60.3 Hz
resolution 1440x900: horiz 55.9 Hz, vertical 59.9 Hz

The X server is conveniently restarted with
/etc/init.d/gdm restart

NB: if the server does not restart (ie, you see a black screen with a warning from the monitor), you DO NOT have to reboot the machine into safe mode. Just hit Control-Alt-F1 to Control-Alt-F5 or so, and your screen will switch to one of the line-oriented login screens that live in the ttys started a boot up.

---

### Post by twallace on 2009-12-07
With a risk of killing the monitor from working maybe I should leave it alone and hope an update will come that fixes it...

---

### Post by dboy on 2009-12-13
I must say I am amazed and disappointed that Ubuntu is this far along in development and there's still no way to make simple resolution adjustments. You'd think this would be a solved problem since Microsoft has had working graphics and graphic settings since Windows 3.1. 

Some docs even refer to the Ubuntu menu path: System/Preferences/Change Display Settings or something like that, that doesn't even exist. System/Preferences/Display (which DOES exist) doesn't allow you to change anything, so again it's completely useless.

And wading through the command-line options for xrandr is pathetic and stupid and nobody should have to do that. I am NOT a new Linux user btw...1995 here. Once we get used to ONE stupid way of handling graphics, some genius comes along and ***** it all up again so it doesn't work..again.

This is really sad and stupid.

dboy

---

### Post by twallace on 2009-12-22
Man I am getting really tired of getting the error messages and running in the low graphics mode, can anyone offer a permanent solution to this problem as it appears as none of the updates are going to fix this.

I am about ready to give Mint 8 a try since Mint 7 worked perfect on my desktop.

---

### Post by Yellow Pasque on 2009-12-22
What does the Xorg.0.log say now? PLEASE use pastebin or [ code ][ /code ] blocks when pasting large amounts of text.

---

### Post by twallace on 2009-12-22
X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux terry-laptop 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-16-generic root=UUID=d82c73e5-df0d-4287-88cd-91f4fe7525be ro quiet splash
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Dec 22 15:38:30 2009
(==) Using config file: "/etc/X11/xorg.conf"
Parse error on line 1 of section (null) in file /etc/X11/xorg.conf
    "ection" is not a valid keyword in this section.
(EE) Problem parsing the config file
(EE) Error parsing the config file

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

(WW) xf86CloseConsole: KDSETMODE failed: Bad file descriptor
(WW) xf86CloseConsole: VT_GETMODE failed: Bad file descriptor
(WW) xf86OpenConsole: VT_GETSTATE failed: Bad file descriptor
 ddxSigGiveUp: Closing log

---

### Post by Yellow Pasque on 2009-12-22
Gotcha

---

### Post by kob0724 on 2009-12-22
I'm having the same problem too on my Toshiba Satellite Pro 4600. Just installed a fresh copy of Karmic and it auto-detecs my maximum resolution to be 800x600. I've had this problem before and i usually just solved it by going to the xorg.conf file and adding the 1024x768 mode in the appropriate place. But the "no xorg.conf in Karmic" is throwing me for a loop.

---

### Post by ST3ALTHPSYCH0 on 2009-12-22
Dunno if any of you have tried the workaround I've posted. You'll need a copy of the 8.04 Live environment (USB or CD in case I lost anyone). I couldn't get an xorg.conf working to save my life by using "cvt", so I used the built in tool in 8.04. Click the rez link in my sig for more info.

---

### Post by sitex on 2009-12-23
[SIZE=3]Hi,

You can change the resolutions with the command "xrandr" .

There is a completed article in the site solutionz.yolasite.com for all ubuntu users, I like to invite you to come and solve your problem with solutionz.yolasite.com

[click here to goto the page..]("http://solutionz.yolasite.com")

Thanks..[/SIZE]

---

### Post by twallace on 2009-12-23
> **sitex said:**
> [SIZE=3]Hi,

You can change the resolutions with the command "xrandr" .

There is a completed article in the site solutionz.yolasite.com for all ubuntu users, I like to invite you to come and solve your problem with solutionz.yolasite.com

[click here to goto the page..]("http://solutionz.yolasite.com/linux/add-a-new-screen-resolution-with-the-terminal-on-ubuntu-9-10")

Thanks..[/SIZE]

This did not work for me, the only thing that has got me close thus far is Temujin's posts. Now I need to get rid of the error messages and the one time only low res stuff...

---

### Post by kob0724 on 2009-12-23
> **sitex said:**
> [SIZE=3]Hi,

You can change the resolutions with the command "xrandr" .

There is a completed article in the site solutionz.yolasite.com for all ubuntu users, I like to invite you to come and solve your problem with solutionz.yolasite.com

[click here to goto the page..]("http://solutionz.yolasite.com/linux/add-a-new-screen-resolution-with-the-terminal-on-ubuntu-9-10")

Thanks..[/SIZE]

This doesn't work because 1024x768 isn't one of the modes that is auto detected. so it wont' let you choose it.

---

### Post by Yellow Pasque on 2009-12-24
> "ection" is not a valid keyword in this section.
You have a typo in your xorg.conf

---

### Post by twallace on 2009-12-26
Any new ideas folks? Would really like to get this fixed ...

---

### Post by &lt;tofer&gt; on 2009-12-28
Yeah I have the same issue, when I try to enter the add command code, I get this:

tofer@tofer-laptop:~$ xrandr--addmode default 1280x1024_60.00
xrandr--addmode: command not found

Is this possibly because it lists my maximum resolution as 800x600? or is my command possibly typed incorrectly? Please bare in mind I am new to Ubuntu (about a month) and not much of a computer geek.

---

### Post by verytired on 2009-12-28
Hi Everyone,
 
I am also stuck with a resolution of 800 x 600.  I have a nvidia 9600gt.  Nothing works.  I am thinking of reverting back to x.org server v1.6.  Will let you know if that worked.

---

### Post by verytired on 2009-12-29
Hi Everyone,

Tried reverting couldn't do it sucessfully!  Installed the 190.40 Nvidia drivers but that did not work either.   Any one else have any ideas?

---

### Post by Redundant Username on 2009-12-29
Have you tried using the envyng drivers?
```
sudo apt-get install envyng
``` it's a terminal program.

---

### Post by verytired on 2009-12-29
Hi,

No I have not tried it.  I will do so tonight.  Thanx.

---

### Post by bbneo on 2009-12-29
Here are some things I found in the Ubuntu release notes documentation for 9.04 and 9.10 which you might find helpful... including some information about restarting the X-server and also stopping and restarting the Gnome desktop from the command line:
 
Good luck with this.  I am trying to get Ubuntu setup to do my taxes this year with TurboTax Online, and I think that Firefox 3.5+ and a screen resolution of 1024 x 768 are necessary for that to work.
 
================================== 
Ctrl-Alt-Backspace to restart X
 
dontzap --disable
 
[http://www.ubuntu.com/getubuntu/releasenotes/904](http://www.ubuntu.com/getubuntu/releasenotes/904)
 
==================================
Stopping and restarting gdm
 
Also -
 
Window corruption with older ATI graphics cards
With older ATI graphics cards with 32MB or less of video RAM some corruption of direct rendered windows, for example OSD notifier windows, might appear. This may be worked around by disabling 'RenderAccel' in the Xorg configuration. (426582) 
 
To do this first exit to the console using the following command: 
 
sudo service gdm stop
 
Then create an Xorg configuration file with the command below: 
 
sudo Xorg -configure
 
Then add the 'RenderAccel' option to /etc/X11/xorg.conf: 
 
Section "Device"
... Driver "radeon" Option "RenderAccel" "off"EndSectionAnd restart X/GDM. 
 
sudo service gdm start
 
==============================================
Using Ctrl-Alt-Backspace to restart X
 
Ctrl-Alt-Backspace disabled by default in Xorg, configured via XKB 
Since Ubuntu 9.04, the Ctrl-Alt-Backspace key combination to force a restart of X is now disabled by default, to eliminate the problem of accidentally triggering the key combination. In addition, the Ctrl-Alt-Backspace option is now configured as an X keymap (XKB) option, replacing the X server "DontZap" option and allowing per-user configuration of this setting. 
 
As a result, enabling or disabling the Ctrl+Alt+Backspace shortcut can now be done easily from the desktop. 
 
Enabling Ctrl-Alt-Backspace for Ubuntu
 
Select "System"->"Preferences"->"Keyboard" 
Select the "Layouts" tab and click on the "Layout Options" button. 
Select "Key sequence to kill the X server" and enable "Control + Alt + Backspace". 
 
Enabling Ctrl-Alt-Backspace for Kubuntu
Click on the Application launcher and select "System Settings" 
Click on "Regional & Language". 
Select "Keyboard Layout". 
Click on "Enable keyboard layouts" (in the Layout tab). 
Select the "Advanced" tab. Then select "Key sequence to kill the X server" and enable "Control + Alt + Backspace". 
For further information, see: [https://wiki.ubuntu.com/X/Config/DontZap](https://wiki.ubuntu.com/X/Config/DontZap)
 
====

---

### Post by rahilm on 2009-12-29
> **<tofer> said:**
> Yeah I have the same issue, when I try to enter the add command code, I get this:

tofer@tofer-laptop:~$ xrandr--addmode default 1280x1024_60.00
xrandr--addmode: command not found

Is this possibly because it lists my maximum resolution as 800x600? or is my command possibly typed incorrectly? Please bare in mind I am new to Ubuntu (about a month) and not much of a computer geek.

That's because there is a space between xrandr and --addmode
it is 
xrandr --addmode


i have used that method to change my resolution in karmic. I had the same problem as the OP. But i found another interesting solution.

I had a puppy linux live cd. I tried to boot into puppy. Surprisingly, puppy detected resolutions without issues. So, I copied the xorg.conf file int /etc/X11 of puppy to the /etc/X11 folder in my ubuntu 9.10 installation.

After that, karmic found the resolutions needed and also some extra.

---

### Post by verytired on 2010-01-04
Hi Everyone,

I found out why it did not work,  my motherboard was the cause of all evil.  Going to replace it soon.

---

### Post by twallace on 2010-02-16
[SIZE=4]Now this is weird! Got my laptop fixed today by doing what was suggested by Temujin and installing Mint 8.

Don't know why this didn't work on Ubuntu 9.10 as this is the same OS that runs Mint 8...:roll: [/SIZE]

---

