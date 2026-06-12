---
title: "FGLRX/9.10 Problem"
date: 2010-02-15
forum: General Help
---

### Post by MDSmith2 on 2010-02-15
Hello.

This seems like a somewhat common problem from other forum posts but it seems nobody has found a solution for it yet.

I have an ATI Radeon 9600 and tried using envyng to download the fglrx driver but when it did, it wouldn't load. It kept complaining about not finding the device. Now, it of course works with generic drivers and the radeon driver, but I need the 3d acceleration for FlightGear. In this process, I have seemed to of messed up glx, too.

xorg.conf:
```
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "dri2"
    Load  "glx"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    #DisplaySize      370   230    # mm
    Identifier   "Monitor0"
    VendorName   "HAI"
    ModelName    "Haier BBY19"
    HorizSync    24.0 - 71.0
    VertRefresh  55.0 - 75.0
    Option        "DPMS"
EndSection

Section "Device"
        Option     "DRI"                    "true"
        Option     "GLX"                    "true"
    Identifier  "Card0"
    Driver      "FGLRX"
    VendorName  "ATI Technologies Inc"
    BoardName   "RV350 [Mobility Radeon 9600 M10]"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
        Resolution 1280x1024
    EndSubSection
EndSection
```glxinfo output:
```
name of display: :0.0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  130 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  16
  Current serial number in output stream:  16
```Xorg.0.log:
```

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux mdsmiths 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=706dbfb0-e8e9-4a0c-bda4-9b686fb8e70c ro text
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Mon Feb 15 12:04:03 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "X.org Configured"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Card0"
(**) |-->Input Device "Mouse0"
(**) |-->Input Device "Keyboard0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(**) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins,
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(**) ModulePath set to "/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Mouse0
(WW) Disabling Keyboard0
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 5.0
    X.Org XInput driver : 4.0
    X.Org Server Extension : 2.0
(II) Loader running on linux
(--) using VT number 8

(--) PCI:*(0:1:0:0) 1002:4e50:0000:4e50 ATI Technologies Inc RV350 [Mobility Radeon 9600 M10] rev 0, Mem @ 0xb0000000/268435456, 0xcfef0000/65536, I/O @ 0x0000b800/256, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded. This was enabled by default and also specified in the config file.
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="FireGL - ATI Technologies Inc."
    compiled for 7.4.0, module version = 1.0.0
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
    compiled for 7.4.0, module version = 1.0.0
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
    compiled for 1.4.99.906, module version = 8.66.10
(II) Loading extension XFree86-DRI
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
    compiled for 1.4.99.906, module version = 8.66.10
    Module class: X.Org Video Driver
(II) Primary Device is: PCI 01@00:00:0
(WW) Falling back to old probe method for fglrx
(II) ATI Proprietary Linux Driver Version Identifier:8.66.10
(II) ATI Proprietary Linux Driver Release Identifier: 8.66.1                               
(II) ATI Proprietary Linux Driver Build Date: Sep  3 2009 21:35:19
(II) Loading PCS database from /etc/ati/amdpcsdb
(EE) No devices detected.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.1.log" for additional information.

 ddxSigGiveUp: Closing log
```lspci: 
```

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 746 Host (rev 10)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 04)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:0b.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]

```I will be glad to post any more info needed and test any fixes,

uname -a:
```

Linux mdsmiths 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux
```

I will be glad to post any more info needed and test any fixes,
MDSmith2

---

### Post by pme 72 on 2010-02-15
It looks like the fglrx driver is no longer supported for your card in Karmic Koala:

[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.24&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.24&lang=English)

If you must have the fglrx driver you do have the option of installing 8.10 Intrepid Ibex, the last Ubuntu release that supported fglrx for your card. 

Some other options could be replacing your ATI Radeon 9600 with a card that has better 3D support, running the game in Windows or waiting to see if the 3D capabilities of the open source driver in subsequent releases will expand. 

There is interesting reading about video cards and drivers for Linux on the Phoronix website: 

[http://www.phoronix.com/scan.php?page=home](http://www.phoronix.com/scan.php?page=home)

---

### Post by MDSmith2 on 2010-02-15
> **pme 72 said:**
> It looks like the fglrx driver is no longer supported for your card in Karmic Koala:

[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.24&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.24&lang=English)

If you must have the fglrx driver you do have the option of installing 8.10 Intrepid Ibex, the last Ubuntu release that supported fglrx for your card. 

Some other options could be replacing your ATI Radeon 9600 with a card that has better 3D support, running the game in Windows or waiting to see if the 3D capabilities of the open source driver in subsequent releases will expand. 

There is interesting reading about video cards and drivers for Linux on the Phoronix website: 

[http://www.phoronix.com/scan.php?page=home](http://www.phoronix.com/scan.php?page=home)
> ATI Radeon 9600 Series

That is on the support list and thats my card, isn't it?

---

### Post by clhsharky on 2010-02-15
HI 

Yes its listed, did you not read the rest of the page.

Including this

[HTML] The Linux ATI Catalyst™ driver will only be supported in Linux distributions prior to February 2009 for the legacy products listed above[/HTML]

All newer "fglrx drivers/Linux distributions" do not support that card.

Legacy cards are supported with radeon drivers. 

I see your trying to use KMS/DRI2, UMS may be better for some games. Gallium will help many people with r300 cards when released. 
If the game is not cross-platform, native, or ported can't help you.

Sharky

---

### Post by MDSmith2 on 2010-02-16
> **clhsharky said:**
> HI 

Yes its listed, did you not read the rest of the page.

Including this

[HTML] The Linux ATI Catalyst™ driver will only be supported in Linux distributions prior to February 2009 for the legacy products listed above[/HTML]All newer "fglrx drivers/Linux distributions" do not support that card.

Legacy cards are supported with radeon drivers. 

I see your trying to use KMS/DRI2, UMS may be better for some games. Gallium will help many people with r300 cards when released. 
If the game is not cross-platform, native, or ported can't help you.

Sharky
FlightGear is cross platform, yes but I have never been able to get descent performance with the open source driver.

Anyway, what about the glxinfo problem? Can I at least fix that somehow?

---

### Post by andydread on 2010-03-11
I am having similar issues.  I can't install the legacy ATI driver in Karmic because its not supported for later kernels apparently.  
I get this 
```
Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.31-20-generic; make sure that the version is being
correctly set by --iscurrentdistro
```

The open source driver sucks.  Flickering during some games like foobillard.  And weird flickering if a GL screensaver is running.  

Here are some graphics anomalies that the open source driver displays that the fglrx did not in older Ubuntus. With this same hardware. 
[http://i.imgur.com/Eo0DS.jpg](http://i.imgur.com/Eo0DS.jpg)
[http://i.imgur.com/X9QUx.png](http://i.imgur.com/X9QUx.png)


So I can't even play Flight Gear or TORCS.  Games that are in the repos.
yet I am using hardware that is capable of playing these games.  It's sad that one has to use an obsolete version of Ubuntu to play these games.  Which means I would be playing older versions of these games too.  Unless I want to backport stuff from Karmic to Intrepid.  

Basically what this means then is that if you have legacy ATI cards with 3D acceleration and you use a current version of Ubuntu you are screwed

1. If you want to play decent 3D/OGL games that are in the current Ubuntu Repos. 

2. because have to disable Compiz to play 3D games because in the year 2010 we still have conflicts and anomalies with Compiz and some 3D games on ATI hardware??.

---

### Post by Mark Phelps on 2010-03-11
You're basically correct in what you say.  So, if you're saying this to tell folks about it, that's great.  

However, if you're saying this to vent frustration, then the folks that need to hear this are AMD/ATI --  THEY are the ones that dropped Linux support for the Legacy cards.

The open source drivers are improving with every Ubuntu release, but it remains to be seen if they will be better for the Legacy cards than the current drivers.

---

### Post by dcstar on 2010-03-11
> **Mark Phelps said:**
> 
........
The **open source drivers** are improving with every Ubuntu release, but it remains to be seen if they will be better for the Legacy cards than the current drivers.

They have to be improving because the upcoming 10.04 release has no propriety ATI driver support at the moment...... ](*,)

---

