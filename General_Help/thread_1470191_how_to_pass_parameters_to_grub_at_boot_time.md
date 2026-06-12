---
title: "how to pass parameters to grub at boot time??"
date: 2010-05-02
forum: General Help
---

### Post by jerome schatten on 2010-05-02
Old Toshiba laptop model A30 -- tried various installs 8.04/9.04/9.10. They all hung trying to boot the install disks after the initial few screens. 

Finally, I got 9.10 to install, dual booting XP and 9.10 by choosing F6 from the initial menu, and putting an X beside:
ACPI=off
noapic
nolapc
edd=on
nodmaid
and then hitting escape.

But, after the install, I couldn't boot 9.10 from grub as it hangs after about 30 seconds of trying.

The live CD would not work without the above parameters being set as described above, but does work with them set!

So methinks I need those same parameters passed to grub at 9.10 boot time, but I can't figure out how to do that.  I see others have had the same problem, but their threads ended without a solution being posted. 

I've had many successful installs of Ubuntu across a number of desktops and laptops, but I never had to deal with the guts of grub before. It all just worked.

If someone could lead me by the hand here, it would be much appreciated.

jerome

---

### Post by happyhamster on 2010-05-02
Boot into the grub menu: hold the shift key during the early stages of the boot process. That should bring up the grub2 menu. (It could take a few tries to get it right.) It's also possible that the menu appears automatically for you (because of the dual boot.)

Select a kernel you want to boot, and press e. Between all the gibberish will be a huge line beginning with "linux /boot/vmlinuz-". Put the cursor at the beginning of that line and press the End key to get at the end of it (it probably ends with "quiet splash").
Anyway, add your kernel parameters there. Then press Ctrl-x to boot.

- Once logged in, you can edit grub; in a terminal (Applications-->Accessories-->Terminal), type:

gksudo gedit /etc/default/grub

- There should be a line:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

- add your parameters there (between the quotes). Save, and exit the editor. Then run:

sudo update-grub

- to update grub. Reboot. If you suspect something's wrong or if something's unclear, don't edit anything yet, but ask here instead. Good luck.

---

### Post by jerome schatten on 2010-05-02
Thanks for the most clear procedure.

Unfortunately, it still wouldn't boot. I was able to determine that it was acpi=off rather than the other parameters that allowed the live CD to work. 

Grub announced that it accepted acpi=off, but it still hangs in the same place when trying to boot 9.10.

Is there anything anything else you can think of to try -- so close and yet so far away ;-}

With thanks,

jerome

---

### Post by happyhamster on 2010-05-02
Try booting with "acpi=off" as before, but remove the "quiet splash" parameters. It will cause all bootup messages to be visible. Make a note of any errors shown. Also, when the system hangs, see if you can get into a console by pressing ctrl-alt-F3.
Another try is to boot into a recovery kernel (it should be selectable from within the grub menu). Add "acpi=off" to that one as well. You will eventually get into another menu, from which you could try the failsafeX option for example.

---

### Post by jerome schatten on 2010-05-02
OK.... making progress...  I had a carriage return after that long line and had the parameter on the next line. Putting  'acpi=off' in right after where I took out 'quiet splash' successfully booted the system into terminal mode. I was able to log in and look at some logs.

At the prompt I entered 'startx' and X started, came up for a second with a screen, and then crashed back to the command prompt.

Almost there... I may be able to pipe the Xorg logs to a file for you to look at.

I want to thank you for your continued help!

jerome

---

### Post by GSF1200S on 2010-05-02
> **jerome schatten said:**
> OK.... making progress...  I had a carriage return after that long line and had the parameter on the next line. Putting  'acpi=off' in right after where I took out 'quiet splash' successfully booted the system into terminal mode. I was able to log in and look at some logs.

At the prompt I entered 'startx' and X started, came up for a second with a screen, and then crashed back to the command prompt.

Almost there... I may be able to pipe the Xorg logs to a file for you to look at.

I want to thank you for your continued help!

jerome

Well, the kernel at least is booting. It seems your problem is with X. Perhaps you could try the following:

At the command prompt type:
```
sudo nano /etc/X11/xorg.conf
```

In the file that opens up, search for the line under Section "Device" that contains the driver name. For example, I have an Nvidia card, so mine looks like:

> Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9800 GTX+"
    BusID          "PCI:2:0:0"
EndSection

Yours may not look the same, but the important line is the one that says:
```
Driver      "nvidia"
```

Change whatever is in the " " to "vesa"
So, for example, it would look like:
```
Driver      "vesa"
```
Hit Ctrl+o, Enter, Ctrl+x, then run:
```
sudo /etc/init.d/gdm restart
```
and see what happens. Also, for us to help you better, what video card do you have? If you dont know, you can give us the results of:
```
lspci
```
You probably want to do this after you open a terminal when X starts.

---

### Post by jerome schatten on 2010-05-03
Here's what I found out:

**Output of 'lspci':**
Display Controller - Intel Corp. 82852/855GM Integrated Graphics Device
[B]
Contents of xorg.conf
[/B]Section    "Device"
Identifier  "Configured Video Device"
Driver:     "vesa"
EndSection

Section    "Monitor"
Identifier  "Configured Monitor"
EndSection

Section    "Screen"
Identifier  "Default Screen"
Monitor    "Configured Monitor"
Device     "Configured Video Device"
EndSection

---

More ideas?
With thanks,
jerome

---

### Post by jerome schatten on 2010-05-03
**Here is the output of Xorg.0.log after X crashes on startup** -- I think the problem is near the end of the file, but I'm not sure what it's telling me.
j.

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux winky-laptop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=128f8fca-8c1c-43ea-aaa9-4352d0d4033e ro acpi=off
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon May  3 11:50:08 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
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
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 5.0
    X.Org XInput driver : 4.0
    X.Org Server Extension : 2.0
(II) Loader running on linux
(--) using VT number 7

(--) PCI:*(0:0:2:0) 8086:3582:1179:ff00 Intel Corporation 82852/855GM Integrated Graphics Device rev 2, Mem @ 0xe8000000/134217728, 0xe0000000/524288, I/O @ 0x00001800/8
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) No APM support in BIOS or kernel
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
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
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
    compiled for 1.6.3, module version = 2.2.1
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is: PCI 00@00:02:0
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
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
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 32576 kB
(II) VESA(0): VESA VBE OEM: Intel(r)852MG/852MGE/855MG/855MGE Graphics Chip Accelerated VGA BIOS
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
(II) VESA(0): VESA VBE OEM Product: Intel(r)852MG/852MGE/855MG/855MGE Graphics Controller
(II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) VESA(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
(==) VESA(0): Depth 24, (--) framebuffer bpp 32
(==) VESA(0): RGB weight 888
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) VESA(0): VESA VBE DDC supported
(II) VESA(0): VESA VBE DDC Level none
(II) VESA(0): VESA VBE DDC transfer in appr. 0 sec.
(II) VESA(0): VESA VBE DDC read failed
(II) VESA(0): VESA VBE PanelID read successfully
(II) VESA(0): PanelID returned panel resolution 1024x768
(II) VESA(0): Searching for matching VESA mode(s):
Mode: 17c (1024x600)
    ModeAttributes: 0x9a
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0007033
    BytesPerScanline: 1024
    XResolution: 1024
    YResolution: 600
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 55
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xe8000000
    LinBytesPerScanLine: 1024
    BnkNumberOfImagePages: 55
    LinNumberOfImagePages: 55
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
Mode: 17d (1024x600)
    ModeAttributes: 0x9a
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0007033
    BytesPerScanline: 2048
    XResolution: 1024
    YResolution: 600
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 25
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xe8000000
    LinBytesPerScanLine: 2048
    BnkNumberOfImagePages: 25
    LinNumberOfImagePages: 25
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
Mode: 17e (1024x600)
    ModeAttributes: 0x9a
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0007033
    BytesPerScanline: 4096
    XResolution: 1024
    YResolution: 600
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 12
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xe8000000
    LinBytesPerScanLine: 4096
    BnkNumberOfImagePages: 12
    LinNumberOfImagePages: 12
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 230000000
Mode: 13c (1920x1440)
    ModeAttributes: 0x9a
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0007033
    BytesPerScanline: 1920
    XResolution: 1920
    YResolution: 1440
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 11
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xe8000000
    LinBytesPerScanLine: 1920
    BnkNumberOfImagePages: 11
    LinNumberOfImagePages: 11
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
Mode: 14d (1920x1440)
    ModeAttributes: 0x9a
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0007033
    BytesPerScanline: 3840
    XResolution: 1920
    YResolution: 1440
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 5
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xe8000000
    LinBytesPerScanLine: 3840
    BnkNumberOfImagePages: 5
    LinNumberOfImagePages: 5
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
Mode: 15c (1920x1440)
    ModeAttributes: 0x9a
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0007033
    BytesPerScanline: 7680
    XResolution: 1920
    YResolution: 1440
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 2
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xe8000000
    LinBytesPerScanLine: 7680
    BnkNumberOfImagePages: 2
    LinNumberOfImagePages: 2
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 230000000
Mode: 13a (1600x1200)
    ModeAttributes: 0x9a
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0007033
    BytesPerScanline: 1600
    XResolution: 1600
    YResolution: 1200
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 16
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xe8000000
    LinBytesPerScanLine: 1600
    BnkNumberOfImagePages: 16
    LinNumberOfImagePages: 16
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
Mode: 14b (1600x1200)
    ModeAttributes: 0x9a
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0007033
    BytesPerScanline: 3200
    XResolution: 1600
    YResolution: 1200
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 7
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xe8000000
    LinBytesPerScanLine: 3200
    BnkNumberOfImagePages: 7
    LinNumberOfImagePages: 7
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
Mode: 15a (1600x1200)
    ModeAttributes: 0x9a
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0007033
    BytesPerScanline: 6400
    XResolution: 1600
    YResolution: 1200
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 3
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xe8000000
    LinBytesPerScanLine: 6400
    BnkNumberOfImagePages: 3
    LinNumberOfImagePages: 3
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 230000000
Mode: 107 (1280x1024)
    ModeAttributes: 0x9a
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0007033
    BytesPerScanline: 1280
    XResolution: 1280
    YResolution: 1024
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 24
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xe8000000
    LinBytesPerScanLine: 1280
    BnkNumberOfImagePages: 24
    LinNumberOfImagePages: 24
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
Mode: 11a (1280x1024)
    ModeAttributes: 0x9a
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0007033
    BytesPerScanline: 2560
    XResolution: 1280
    YResolution: 1024
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 11
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xe8000000
    LinBytesPerScanLine: 2560
    BnkNumberOfImagePages: 11
    LinNumberOfImagePages: 11
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
Mode: 11b (1280x1024)
    ModeAttributes: 0x9a
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0007033
    BytesPerScanline: 5120
    XResolution: 1280
    YResolution: 1024
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 5
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xe8000000
    LinBytesPerScanLine: 5120
    BnkNumberOfImagePages: 5
    LinNumberOfImagePages: 5
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 230000000
Mode: 105 (1024x768)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0007033
    BytesPerScanline: 1024
    XResolution: 1024
    YResolution: 768
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 41
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xe8000000
    LinBytesPerScanLine: 1024
    BnkNumberOfImagePages: 41
    LinNumberOfImagePages: 41
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
Mode: 117 (1024x768)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0007033
    BytesPerScanline: 2048
    XResolution: 1024
    YResolution: 768
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 20
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xe8000000
    LinBytesPerScanLine: 2048
    BnkNumberOfImagePages: 20
    LinNumberOfImagePages: 20
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
*Mode: 118 (1024x768)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0007033
    BytesPerScanline: 4096
    XResolution: 1024
    YResolution: 768
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 9
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xe8000000
    LinBytesPerScanLine: 4096
    BnkNumberOfImagePages: 9
    LinNumberOfImagePages: 9
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 230000000
*Mode: 112 (640x480)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0007033
    BytesPerScanline: 2560
    XResolution: 640
    YResolution: 480
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 25
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xe8000000
    LinBytesPerScanLine: 2560
    BnkNumberOfImagePages: 25
    LinNumberOfImagePages: 25
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 230000000
Mode: 114 (800x600)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0007033
    BytesPerScanline: 1600
    XResolution: 800
    YResolution: 600
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 32
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xe8000000
    LinBytesPerScanLine: 1600
    BnkNumberOfImagePages: 32
    LinNumberOfImagePages: 32
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
*Mode: 115 (800x600)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0007033
    BytesPerScanline: 3200
    XResolution: 800
    YResolution: 600
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 16
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xe8000000
    LinBytesPerScanLine: 3200
    BnkNumberOfImagePages: 16
    LinNumberOfImagePages: 16
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 230000000
Mode: 101 (640x480)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0007033
    BytesPerScanline: 640
    XResolution: 640
    YResolution: 480
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 100
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xe8000000
    LinBytesPerScanLine: 640
    BnkNumberOfImagePages: 100
    LinNumberOfImagePages: 100
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
Mode: 103 (800x600)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0007033
    BytesPerScanline: 800
    XResolution: 800
    YResolution: 600
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 71
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xe8000000
    LinBytesPerScanLine: 800
    BnkNumberOfImagePages: 71
    LinNumberOfImagePages: 71
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
Mode: 111 (640x480)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0007033
    BytesPerScanline: 1280
    XResolution: 640
    YResolution: 480
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 55
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xe8000000
    LinBytesPerScanLine: 1280
    BnkNumberOfImagePages: 55
    LinNumberOfImagePages: 55
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000

(II) VESA(0): Total Memory: 509 64KB banks (32576kB)
(II) VESA(0): Configured Monitor: Using hsync range of 31.50-47.30 kHz
(II) VESA(0): Configured Monitor: Using vrefresh range of 56.00-59.87 Hz
(WW) VESA(0): Unable to estimate virtual size
(II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
(II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
(WW) VESA(0): No valid modes left. Trying less strict filter...
(II) VESA(0): Configured Monitor: Using hsync range of 31.50-47.30 kHz
(II) VESA(0): Configured Monitor: Using vrefresh range of 56.00-59.87 Hz
(WW) VESA(0): Unable to estimate virtual size
(II) VESA(0): Not using built-in mode "640x480" (hsync out of range)
(--) VESA(0): Virtual size is 1024x768 (pitch 1024)
(**) VESA(0): *Built-in mode "1024x768"
(**) VESA(0): *Built-in mode "800x600"
(==) VESA(0): DPI set to (96, 96)
(II) VESA(0): Attempting to use 60Hz refresh for mode "800x600" (115)
(**) VESA(0): Using "Shadow Framebuffer"
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules//libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.1.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 32576 kB
(II) VESA(0): VESA VBE OEM: Intel(r)852MG/852MGE/855MG/855MGE Graphics Chip Accelerated VGA BIOS
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
(II) VESA(0): VESA VBE OEM Product: Intel(r)852MG/852MGE/855MG/855MGE Graphics Controller
(II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) VESA(0): virtual address = 0xb577b000,
    physical address = 0xe8000000, size = 33357824
(II) VESA(0): Setting up VESA Mode 0x118 (1024x768)
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Backing store disabled
(II) VESA(0): DPMS enabled
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
 ddxSigGiveUp: Closing log

---

### Post by happyhamster on 2010-05-03
- You could try reconfiguring xorg: boot into grub, select a recovery kernel, add "acpi=off" to it, and boot into it. When you get the recovery menu, choose "Boot into a root shell" or such.
You'll drop into a root shell immediately, so be careful from now on.

- Then, in order:

cd /etc/X11
cp xorg.conf xorg.conf.backup
Xorg -configure
cp /root/xorg.conf.new xorg.conf
reboot

- There's no need for sudo, because you're root. Also, notice the letter x is sometimes upper case and sometimes lower case.

- Anyway, first command navigates to the proper folder. 
- Second one makes a backup of the current xorg.conf
- Third creates a fresh configuration file: /root/xorg.conf.new You can take a look at it first if you so desire:

cat /root/xorg.conf.new

- Fourth command does the overwriting of xorg.conf
- Fifth speaks for itself. Reboot any way you want, it doesn't matter.

- In case things didn't work out, boot into a shell once more, and copy the old xorg.conf back again:

cd /etc/X11
cp xorg.conf.backup xorg.conf


- BTW, if you post huge logs or such, it's best to put the text between [noparse]```
 
```[/noparse] or [noparse]>  [/noparse] tags, because it will be friendlier on the layout of the page.

Good luck.

---

### Post by jerome schatten on 2010-05-03
Thank you again HH!

Well, I was able to do everything as you outlined. The new xorg.conf file showed that it wanted to use the 'intel' driver rather than the 'vesa' driver. There was an enormous log file generated with all sorts of errors. So, I re-edited one line that had the Driver selection -- changing it from 'intel' to 'vesa' and rebooted.

Still no joy, but hardly any errors. In the end the only thing I could see from Xorg.0.log was that everything was going along nicely when it got a Sig11 and it quit.  

I looked at the tail of 'messages' and saw a bunch of segfaults -- error 4 in libdevkit-pwr-gobject.so1.0.1, and in other libraries, which I guess is what killed X. 

Sigh...
j.

P.S. Thanks for the tip on posting large chunks of code.

Anyway, I am stumped

---

### Post by happyhamster on 2010-05-03
> **jerome schatten said:**
> I looked at the tail of 'messages' and saw a bunch of segfaults -- error 4 in libdevkit-pwr-gobject.so1.0.1, and in other libraries, which I guess is what killed X.
That's pretty interesting, because libdevkit-pwr is associated with powermanagement and the same holds for (parts of) acpi. My guess is that the laptop's BIOS is broken (broken in the sense that stuff will only work correctly when using vendor-applied drivers, but those will only exist for windows). For linux, you would be looking at finding the right combination of kernel, kernelparameters, perhaps blacklisting drivers etc. I have to repeat that I'm just guessing here though.

A general first try would be to do a BIOS upgrade (if available), but flashing firmware is always dangerous (it could do damage to the hardware beyond repair). And it's sometimes near impossible to actually *apply* such an upgrade, especially on laptops because they lack stuff like floppy drives and such.

> Anyway, I am stumped
Well so am I. If you enjoy testing this kind of stuff, look into applying kernel parameters again. For example: acpi=off disables acpi completely, while it is also possible to shut down only parts of it (pci=noacpi, etc) **. Another one is to force/disable apm (advanced power management), or trying the more crude stuff like irqpoll or pci=nomsi. This is just a guessing game however.
Note that messing with parameters can be dangerous as well, you might for example boot into a running system but without any fans working or such.

One other thing you could try: boot into a live session, and collect info about that environment.

Finally, an option that comes to mind is to install virtualbox under winxp, and create a virtual machine to run ubuntu in. Perhaps not what you're looking for, but it is safe (and fun :)).

Good luck.


** A full list of kernelparameters, including some basic info, is available in the "kernel-parameters.txt" file that comes with the source code of the kernel. Go here: [http://www.kernel.org/](http://www.kernel.org/) to download the kernel source, extract it, and the file will be in the Documentation folder.

---

### Post by jerome schatten on 2010-05-03
> **happyhamster said:**
> That's pretty interesting, because libdevkit-pwr is associated with powermanagement and the same holds for (parts of) acpi. My guess is that the laptop's BIOS is broken (broken in the sense that stuff will only work correctly when using vendor-applied drivers, but those will only exist for windows). For linux, you would be looking at finding the right combination of kernel, kernelparameters, perhaps blacklisting drivers etc. I have to repeat that I'm just guessing here though.

A general first try would be to do a BIOS upgrade (if available), but flashing firmware is always dangerous (it could do damage to the hardware beyond repair). And it's sometimes near impossible to actually *apply* such an upgrade, especially on laptops because they lack stuff like floppy drives and such.

[B]Jerome says: You're absolutely correct here to wit:  

This laptop belongs to a senior lady who had managed to get it infected with a bad virus (many times). She is addicted to Hearts and Solitaire. So my first thought was to put Ubuntu on there. I've got an old Compac laptop of same vintage and resources and 9.10 plays beautifully on it. That, I felt would get her out of the path of future virii. She also uses the net for email and for light browsing (recipes 'n stuff).

When Ubuntu failed to install, I reloaded XP on her machine(not the OEM version), and saw that my XP couldn't deal with the lack of drivers that had existed on the OEM version. Although it played OK, it couldn't even find the realtek ethernet card or deal with the sound. So I solved the problem by brute force: Use Puppy Linux live CD for the net related stuff and drop to XP to play the games. This would work for me, but it's tough for her. 

So this will be the fallback if I can't get it working. With Puppy, BTW, the sound worked, the net worked -- but try as I might, and I know the Solitaire game pet exists, I couldn't find a download site that worked. Nor could I find Hearts.

Scouring the net, I did find out the bios on that particular model (apparently only sold in Canada) was indeed screwed up. But as you say, it only affects windoze. And the games play. 

So, that's the reason for Ubuntu -- the games exist; good security; and easy to operate -- if I can get it going.
[/B]   
Well so am I. If you enjoy testing this kind of stuff, look into applying kernel parameters again. For example: acpi=off disables acpi completely, while it is also possible to shut down only parts of it (pci=noacpi, etc) **. Another one is to force/disable apm (advanced power management), or trying the more crude stuff like irqpoll or pci=nomsi. This is just a guessing game however.
Note that messing with parameters can be dangerous as well, you might for example boot into a running system but without any fans working or such.

One other thing you could try: boot into a live session, and collect info about that environment. 

**J: Yeah... there's a really good idea -- I should be able to see what xorg.conf looks like when it works, wouldn't you think? And other things too!**
[B]
In the meantime, I will look for Hearts for Ubuntu and put it on my laptop and let her use my machine until I make hers work, or give up.
[/B] 
Finally, an option that comes to mind is to install virtualbox under winxp, and create a virtual machine to run ubuntu in. Perhaps not what you're looking for, but it is safe (and fun :)). 

[B]J. says: That's one direction I don't want to go in -- not enough memory and it would be tough for her to manage.
[/B] 
Good luck.


** A full list of kernelparameters, including some basic info, is available in the "kernel-parameters.txt" file that comes with the source code of the kernel. Go here: [http://www.kernel.org/](http://www.kernel.org/) to download the kernel source, extract it, and the file will be in the Documentation folder.

[B]Thanks for all the info and help -- I'm learning lots.
j.
[/B]

---

### Post by jerome schatten on 2010-05-04
Solved it is!  The gui boots fine if 'quiet splash' is inserted back along with 'acpi=off' into /etc/default/grub and grub is updated.

Is there a known problem getting to the gui from the command line with 'startx' if 'quiet splash' is removed?

Anyway it works fine, the niggling question notwithstanding.

Thanks HH for all the help!
j.

---

