---
title: "Big Problem, need help"
date: 2006-05-26
forum: General Help
---

### Post by 2pacalypse on 2006-05-26
I got a BIG Problem

I got Ubuntu Version 5.10 with all the updates and with the Kernel 2.6 thingie (i have no idea what 'Kernel 2.6' means :P)but the problem that its wont load, he just gives me the following screens

1
[click here to see the photo](http://img405.imageshack.us/img405/6681/img9512l3qn.jpg)
for those who cant see the photo or cant understand the writing it says
> Failed to start the X server(your graphical interface). it is likely that it is not set up correctly. would you like to view the X server output to  diagnose the problem?

all besides that is jibrish
2
[click here to see the photo](http://img259.imageshack.us/img259/7594/img9517l4ll.jpg)
for those who cant see the photo or cant understand the writing it says
> X Windows System Version 6.8.2 (Ubuntu 6.8.2-77.1 20060503192905 [email]root@terranova.warthogs.hbd.com[/email])
Release date: 9 Feburary 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operation system: Linux 2.6.12 i686 [ELF]
Current Operation System: Linux 2pacalypse 2.6.12-10-386 #1 Fri Apr 28 13:13:44 UTC 2006 i686
Build Date: 03 May 2006
Before reporting problems, check [http://wiki.X.org](http://wiki.X.org) to make sure that you have the latest version
Module Loader present
OS Kernel: Linux version 2.6.12-10-386 (buildd@terranova) (gcc version 3.4.5 20050809 (prereleased) (buntu 3.4.4-6Ubuntu8.1)) #1 Fri Apr 28 13:13:44 UTC 2006 T
Markers: (--) probed, (**) from config file, (--) default setting

all besides that is jibrish

afterwards he gives me a dos like screen asking for username and password

This happend after i used EasyUbuntu to install Nvidia Gforce Drivers automaticly along with all the other options (except the ATI Video drivers) so EasyUbuntu probably misconfigured my Gforce 5200FX

however, when i tried to reconfigure it correctly using this command
```

sudo dpkg-reconfigure xserver-xorg

```
unfortunantly, although I reconfigured it into what i believe is the correct thing (im not sure cuz im pretty much a Linux beginner) he still gives me those cursed screen and keeps throwing me into a terminal like screen instead of a Desktop enviorment. what should i do? I've been asking for 3 weeks about it at the linuxiso forums but i barly got responce (only 1 guy responded and he taught me the command). i really need a stable working computer so can any1 please help me with this problem

Thanks in advance

---

### Post by ifokkema on 2006-05-26
Hi,

The second screen you got, allowed you to go through the error log to see what's wrong. You can move down the list with the arrow keys.

Alternatively, from the console, type:
```
less /var/log/Xorg.0.log
```

and use the arrow keys to go down (you can quit by typing 'q'). There should be a clear error summary at the bottom of the file. Could you send us that?

Ivo

---

### Post by bruce89 on 2006-05-26
```
sudo nano /etc/X11/xorg.conf
```
> Section "Device"
        Identifier      "(whatever it says here)"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
EndSection

Change to
> Section "Device"
        Identifier      "(whatever it says here)"
        Driver          "nv"
        BusID           "PCI:1:0:0"
EndSection

edit - Keep getting beaten to it!

---

### Post by arnieboy on 2006-05-26
log into console with your user name and password.
then do the following:
```
sudo nano /etc/X11/xorg.conf
```
scroll down the file when the text editor opens and find the section called "Devices"
under that you will see the word "**nvidia**"
change that to "**nv**"
now press **ctrl-X**
and hit **Y** to save and exit.
Now just restart your computer.

---

### Post by 2pacalypse on 2006-05-26
aight, when i ran
```

less /var/log/Xorg.0.log

```
i recevied this reply 
```


X Window System Version 6.8.2 (Ubuntu 6.8.2-77.1 20060503192905 root@terranova.warthogs.hbd.com)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.12 i686 [ELF]
Current Operating System: Linux 2pacalypse 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686
Build Date: 03 May 2006
        Before reporting problems, check http://wiki.X.Org
        to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-9-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:14:36 BST 2005 T
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri May 26 20:19:43 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "NVIDIA Corporation NV34 [GeForce FX 5200]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
        Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/CID" does not exist.
        Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
        Entry deleted from font path.
        (Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(==) ModulePath set to "/usr/X11R6/lib/modules"
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) Module ABI versions:
        X.Org ANSI C Emulation: 0.2
        X.Org Video Driver: 0.7
        X.Org XInput driver : 0.4
        X.Org Server Extension : 0.2
        X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
:

```

when i ran
```

sudo nano /etc/xll/xorg.conf

```
i noticed that its its completely empty, and i dont know what should be written there and i dont want to mess up my system any worse. any tips?

---

### Post by ifokkema on 2006-05-26
[QUOTE=2pacalypse]aight, when i ran
```

less /var/log/Xorg.0.log

```
i recevied this reply 
(...)

when i ran
```

sudo nano /etc/xll/xorg.conf

```
i noticed that its its completely empty, and i dont know what should be written there and i dont want to mess up my system any worse. any tips?[/QUOTE]

Hi,

1) This is only the first bit of the file. You can move down using your arrow keys. Maybe you can attach the file to this thread, or try and paste the rest of the output (especially the last bit)?

2) You need to capitalyze the X in X11:
```
sudo nano /etc/X11/xorg.conf
```

Ivo

---

### Post by 2pacalypse on 2006-05-26
heres the rest of the text, be ready. theres alot of it
```

(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/X11R6/lib/modules/libpcidata.a
(II) Module pcidata: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 1.0.0
        ABI class: X.Org Video Driver, version 0.7
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1039,0746 card 1039,0746 rev 10 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1039,0002 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:02:0: chip 1039,0963 card 0000,0000 rev 25 class 06,01,00 hdr 80
(II) PCI: 00:02:1: chip 1039,0016 card 0000,0000 rev 00 class 0c,05,00 hdr 00
(II) PCI: 00:02:5: chip 1039,5513 card 1039,5513 rev 00 class 01,01,80 hdr 00
(II) PCI: 00:02:7: chip 1039,7012 card 1458,a002 rev a0 class 04,01,00 hdr 00
(II) PCI: 00:03:0: chip 1039,7001 card 1039,7001 rev 0f class 0c,03,10 hdr 80
(II) PCI: 00:03:1: chip 1039,7001 card 1039,7001 rev 0f class 0c,03,10 hdr 00
(II) PCI: 00:03:3: chip 1039,7002 card 1458,5004 rev 00 class 0c,03,20 hdr 00
(II) PCI: 00:04:0: chip 1039,0900 card 1458,e000 rev 90 class 02,00,00 hdr 00
(II) PCI: 00:0a:0: chip 14f1,2f00 card 14f1,2004 rev 01 class 07,80,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0322 card 0000,0000 rev a1 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
        [0] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000e (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
        [0] -1  0       0xe4000000 - 0xe5ffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
        [0] -1  0       0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:2:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV34 [GeForce FX 5200] rev 161, Mem @ 0xe4000000/24, 0xd0000000/28
(II) Addressable bus resource ranges are
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
        [1] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
   [0] -1  0       0xffe00000 - 0xffffffff (0x200000) MX[B](B)
        [1] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [2] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [3] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [4] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [5] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [6] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xe3ffffff to 0xdfffffff
(II) Active PCI resource ranges:
        [0] -1  0       0xe7000000 - 0xe700ffff (0x10000) MX[B]
        [1] -1  0       0xe7011000 - 0xe7011fff (0x1000) MX[B]
        [2] -1  0       0xe7010000 - 0xe7010fff (0x1000) MX[B]
        [3] -1  0       0xe7013000 - 0xe7013fff (0x1000) MX[B]
        [4] -1  0       0xe7012000 - 0xe7012fff (0x1000) MX[B]
        [5] -1  0       0xe0000000 - 0xdfffffff (0x0) MX[B]O
        [6] -1  0       0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
        [7] -1  0       0xe4000000 - 0xe4ffffff (0x1000000) MX[B](B)
        [8] -1  0       0x0000e400 - 0x0000e407 (0x8) IX[B]
        [9] -1  0       0x0000e000 - 0x0000e0ff (0x100) IX[B]
        [10] -1 0       0x0000dc00 - 0x0000dc7f (0x80) IX[B]
        [11] -1 0       0x0000d800 - 0x0000d8ff (0x100) IX[B]
        [12] -1 0       0x0000f000 - 0x0000f00f (0x10) IX[B]
        [13] -1 0       0x00001400 - 0x0000141f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
        [0] -1  0       0xe7000000 - 0xe700ffff (0x10000) MX[B]
        [1] -1  0       0xe7011000 - 0xe7011fff (0x1000) MX[B]
        [2] -1  0       0xe7010000 - 0xe7010fff (0x1000) MX[B]
        [3] -1  0       0xe7013000 - 0xe7013fff (0x1000) MX[B]
        [4] -1  0       0xe7012000 - 0xe7012fff (0x1000) MX[B]
        [5] -1  0       0xe0000000 - 0xdfffffff (0x0) MX[B]O
        [6] -1  0       0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
        [7] -1  0       0xe4000000 - 0xe4ffffff (0x1000000) MX[B](B)
        [8] -1  0       0x0000e400 - 0x0000e407 (0x8) IX[B]
        [9] -1  0       0x0000e000 - 0x0000e0ff (0x100) IX[B]
        [10] -1 0       0x0000dc00 - 0x0000dc7f (0x80) IX[B]
        [11] -1 0       0x0000d800 - 0x0000d8ff (0x100) IX[B]
        [12] -1 0       0x0000f000 - 0x0000f00f (0x10) IX[B]
        [13] -1 0       0x00001400 - 0x0000141f (0x20) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
        [0] -1  0       0xffe00000 - 0xffffffff (0x200000) MX[B](B)
        [1] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [2] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [3] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [4] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [5] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [6] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
        [0] -1  0       0xffe00000 - 0xffffffff (0x200000) MX[B](B)
        [1] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [2] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [3] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [4] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [5] -1  0       0xe7000000 - 0xe700ffff (0x10000) MX[B]
        [6] -1  0       0xe7011000 - 0xe7011fff (0x1000) MX[B]
        [7] -1  0       0xe7010000 - 0xe7010fff (0x1000) MX[B]
        [8] -1  0       0xe7013000 - 0xe7013fff (0x1000) MX[B]
        [9] -1  0       0xe7012000 - 0xe7012fff (0x1000) MX[B]
        [10] -1 0       0xe0000000 - 0xdfffffff (0x0) MX[B]O
        [11] -1 0       0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
        [12] -1 0       0xe4000000 - 0xe4ffffff (0x1000000) MX[B](B)
        [13] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [14] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [15] -1 0       0x0000e400 - 0x0000e407 (0x8) IX[B]
        [16] -1 0       0x0000e000 - 0x0000e0ff (0x100) IX[B]
        [17] -1 0       0x0000dc00 - 0x0000dc7f (0x80) IX[B]
        [18] -1 0       0x0000d800 - 0x0000d8ff (0x100) IX[B]
        [19] -1 0       0x0000f000 - 0x0000f00f (0x10) IX[B]
        [20] -1 0       0x00001400 - 0x0000141f (0x20) IX[B]
(WW) Ignoring request to load module GLcore
(II) LoadModule: "bitmap"
(II) Reloading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Loading font Bitmap
(II) LoadModule: "dbe"
(II) Loading /usr/X11R6/lib/modules/extensions/libdbe.a
(II) Module dbe: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.2
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "ddc"
(II) Loading /usr/X11R6/lib/modules/libddc.a
(II) Module ddc: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 1.0.0
        ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "dri"
(II) Loading /usr/X11R6/lib/modules/extensions/libdri.a
(II) Module dri: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/X11R6/lib/modules/linux/libdrm.a
(II) Module drm: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/X11R6/lib/modules/extensions/libextmod.a
(II) Module extmod: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.2
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/X11R6/lib/modules/fonts/libfreetype.a
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
        compiled for 6.8.2, module version = 2.1.0
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/X11R6/lib/modules/extensions/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.7667
        Module class: XFree86 Server Extension
        ABI class: XFree86 Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/X11R6/lib/modules/linux/libint10.a
(II) Module int10: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 1.0.0
        ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "record"
(II) Loading /usr/X11R6/lib/modules/extensions/librecord.a
(II) Module record: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 1.13.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.2
(II) Loading extension RECORD
(II) LoadModule: "type1"
(II) Loading /usr/X11R6/lib/modules/fonts/libtype1.a
(II) Module type1: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 1.0.2
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) Loading font CID
(II) LoadModule: "v4l"
(II) Loading /usr/X11R6/lib/modules/drivers/linux/v4l_drv.o
(II) Module v4l: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 0.0.1
        ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "vbe"
(II) Loading /usr/X11R6/lib/modules/libvbe.a
(II) Module vbe: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 1.1.0
        ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "nvidia"
(II) Loading /usr/X11R6/lib/modules/drivers/nvidia_drv.o
(II) Module nvidia: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.7667
        Module class: XFree86 Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/X11R6/lib/modules/input/kbd_drv.o
(II) Module kbd: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 1.0.0
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.4
(II) LoadModule: "mouse"
(II) Loading /usr/X11R6/lib/modules/input/mouse_drv.o
(II) Module mouse: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 1.0.0
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.4
(II) v4l driver for Video4Linux
(II) NVIDIA X Driver  1.0-7667  Fri Jun 17 07:03:12 PDT 2005
(II) NVIDIA Unified Driver for all NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(II) resource ranges after xf86ClaimFixedResources() call:
        [0] -1  0       0xffe00000 - 0xffffffff (0x200000) MX[B](B)
        [1] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [2] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [3] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [4] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [5] -1  0       0xe7000000 - 0xe700ffff (0x10000) MX[B]
        [6] -1  0       0xe7011000 - 0xe7011fff (0x1000) MX[B]
        [7] -1  0       0xe7010000 - 0xe7010fff (0x1000) MX[B]
        [8] -1  0       0xe7013000 - 0xe7013fff (0x1000) MX[B]
        [9] -1  0       0xe7012000 - 0xe7012fff (0x1000) MX[B]
        [10] -1 0       0xe0000000 - 0xdfffffff (0x0) MX[B]O
        [11] -1 0       0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
        [12] -1 0       0xe4000000 - 0xe4ffffff (0x1000000) MX[B](B)
        [13] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [14] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [15] -1 0       0x0000e400 - 0x0000e407 (0x8) IX[B]
        [16] -1 0       0x0000e000 - 0x0000e0ff (0x100) IX[B]
        [17] -1 0       0x0000dc00 - 0x0000dc7f (0x80) IX[B]
        [18] -1 0       0x0000d800 - 0x0000d8ff (0x100) IX[B]
        [19] -1 0       0x0000f000 - 0x0000f00f (0x10) IX[B]
        [20] -1 0       0x00001400 - 0x0000141f (0x20) IX[B]
(II) resource ranges after probing:
        [0] -1  0       0xffe00000 - 0xffffffff (0x200000) MX[B](B)
        [1] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [2] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [3] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [4] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [5] -1  0       0xe7000000 - 0xe700ffff (0x10000) MX[B]
        [6] -1  0       0xe7011000 - 0xe7011fff (0x1000) MX[B]
        [7] -1  0       0xe7010000 - 0xe7010fff (0x1000) MX[B]
        [8] -1  0       0xe7013000 - 0xe7013fff (0x1000) MX[B]
        [9] -1  0       0xe7012000 - 0xe7012fff (0x1000) MX[B]
        [10] -1 0       0xe0000000 - 0xdfffffff (0x0) MX[B]O
        [11] -1 0       0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
        [12] -1 0       0xe4000000 - 0xe4ffffff (0x1000000) MX[B](B)
        [13] 0  0       0x000a0000 - 0x000affff (0x10000) MS[B]
        [14] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[B]
        [15] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[B]
        [16] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [17] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [18] -1 0       0x0000e400 - 0x0000e407 (0x8) IX[B]
        [19] -1 0       0x0000e000 - 0x0000e0ff (0x100) IX[B]
        [20] -1 0       0x0000dc00 - 0x0000dc7f (0x80) IX[B]
        [21] -1 0       0x0000d800 - 0x0000d8ff (0x100) IX[B]
        [22] -1 0       0x0000f000 - 0x0000f00f (0x10) IX[B]
        [23] -1 0       0x00001400 - 0x0000141f (0x20) IX[B]
        [24] 0  0       0x000003b0 - 0x000003bb (0xc) IS[B]
        [25] 0  0       0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(--) NVIDIA(0): Linear framebuffer at 0xD0000000
(--) NVIDIA(0): MMIO registers at 0xE4000000
(II) NVIDIA(0): NVIDIA GPU detected as: GeForce FX 5200
(--) NVIDIA(0): VideoBIOS: 04.34.20.27.06
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): VideoRAM: 131072 kBytes
(II) NVIDIA(0): Connected display device(s): CRT-0, TV-0
(WW) NVIDIA(0): Multiple displays connected, but only one display allowed;
(WW) NVIDIA(0):      using first display
(--) NVIDIA(0): CRT-0: maximum pixel clock: 350 MHz
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/X11R6/lib/modules/libddc.a
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) NVIDIA(0): Primary V_BIOS segment is: 0xc000
(II) NVIDIA(0): Generic Monitor: Using hsync range of 30.00-70.00 kHz
(II) NVIDIA(0): Generic Monitor: Using vrefresh range of 50.00-160.00 Hz
(II) NVIDIA(0): Clock range:  12.00 to 350.00 MHz
(II) NVIDIA(0): Not using default mode "1280x960" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x480" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1280x1024" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x512" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1280x1024" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x512" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1792x1344" (hsync out of range)
(II) NVIDIA(0): Not using default mode "896x672" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1792x1344" (hsync out of range)
(II) NVIDIA(0): Not using default mode "896x672" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1856x1392" (hsync out of range)
(II) NVIDIA(0): Not using default mode "928x696" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1856x1392" (hsync out of range)
(II) NVIDIA(0): Not using default mode "928x696" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1152x864" (hsync out of range)
(II) NVIDIA(0): Not using default mode "576x432" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(0): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(0): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(0): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using mode "1856x1392" (no mode of this name)
(II) NVIDIA(0): Not using mode "1792x1344" (no mode of this name)
(II) NVIDIA(0): Not using mode "1600x1200" (no mode of this name)
(II) NVIDIA(0): Not using mode "1280x854" (no mode of this name)
(II) NVIDIA(0): Not using mode "1200x800" (no mode of this name)
(WW) NVIDIA(0): Not using mode "1680x1050" (width 1680 is larger than
(WW) NVIDIA(0):      EDID-specified maximum 1600)
(WW) NVIDIA(0): Not using mode "1152x768":
(WW) NVIDIA(0):   horizontal sync start (1178) not a multiple of 8
(WW) NVIDIA(0): Not using mode "576x384":
(WW) NVIDIA(0):   horizontal sync start (589) not a multiple of 8
(WW) NVIDIA(0): Not using mode "360x200":
(WW) NVIDIA(0):   horizontal sync start (378) not a multiple of 8
(**) NVIDIA(0): Validated modes for display device CRT-0:
(**) NVIDIA(0):      Default mode "1440x900": 108.8 MHz, 56.9 kHz, 60.2 Hz
(**) NVIDIA(0):      Default mode "1400x1050": 122.0 MHz, 64.9 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "1280x1024": 108.0 MHz, 64.0 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "1280x960": 108.0 MHz, 60.0 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "1280x800": 83.5 MHz, 49.7 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "1280x768": 80.1 MHz, 47.7 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
(**) NVIDIA(0):      Default mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(**) NVIDIA(0):      Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
(**) NVIDIA(0):      Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(**) NVIDIA(0):      Mode "1280x800@60": 83.9 MHz, 50.7 kHz, 60.3 Hz
(**) NVIDIA(0):      Default mode "1024x768": 78.8 MHz, 60.1 kHz, 75.1 Hz
(**) NVIDIA(0):      Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(**) NVIDIA(0):      Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "1024x768": 44.9 MHz, 35.5 kHz, 87.0 Hz (I)
(**) NVIDIA(0):      Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(**) NVIDIA(0):      Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(**) NVIDIA(0):      Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(**) NVIDIA(0):      Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(**) NVIDIA(0):      Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(**) NVIDIA(0):      Default mode "840x525": 73.6 MHz, 65.2 kHz, 60.1 Hz (D)
(**) NVIDIA(0):      Default mode "700x525": 61.0 MHz, 64.9 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "640x512": 54.0 MHz, 64.0 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "720x450": 54.4 MHz, 56.9 kHz, 60.2 Hz (D)
(**) NVIDIA(0):      Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(**) NVIDIA(0):      Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(**) NVIDIA(0):      Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "720x400": 35.5 MHz, 37.9 kHz, 85.0 Hz
(**) NVIDIA(0):      Default mode "640x400": 31.5 MHz, 37.9 kHz, 85.1 Hz
(**) NVIDIA(0):      Default mode "640x400": 41.7 MHz, 49.7 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "576x432": 54.0 MHz, 67.5 kHz, 75.0 Hz (D)
(**) NVIDIA(0):      Default mode "640x384": 40.1 MHz, 47.7 kHz, 60.1 Hz (D)
(**) NVIDIA(0):      Default mode "640x350": 31.5 MHz, 37.9 kHz, 85.1 Hz
(**) NVIDIA(0):      Default mode "512x384": 47.2 MHz, 68.7 kHz, 85.0 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 39.4 MHz, 60.1 kHz, 75.1 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 22.4 MHz, 35.5 kHz, 86.9 Hz (D)
(**) NVIDIA(0):      Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 28.1 MHz, 53.7 kHz, 85.3 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 18.0 MHz, 43.3 kHz, 85.2 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 15.8 MHz, 37.5 kHz, 75.0 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 15.8 MHz, 37.9 kHz, 72.8 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(**) NVIDIA(0):      Default mode "320x200": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(**) NVIDIA(0):      Default mode "320x175": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(II) NVIDIA(0): Virtual screen size determined to be 1440 x 1050
(--) NVIDIA(0): Display dimensions: (320, 240) mm
(--) NVIDIA(0): DPI set to (114, 111)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/X11R6/lib/modules/libfb.a
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
(II) Module fb: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/X11R6/lib/modules/libramdac.a
(II) Module ramdac: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 0.1.0
        ABI class: X.Org Video Driver, version 0.7
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
        [0] 0   0       0xd0000000 - 0xdfffffff (0x10000000) MX[B]
        [1] 0   0       0xe4000000 - 0xe4ffffff (0x1000000) MX[B]
        [2] -1  0       0xffe00000 - 0xffffffff (0x200000) MX[B](B)
        [3] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [4] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [5] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [6] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [7] -1  0       0xe7000000 - 0xe700ffff (0x10000) MX[B]
        [8] -1  0       0xe7011000 - 0xe7011fff (0x1000) MX[B]
        [9] -1  0       0xe7010000 - 0xe7010fff (0x1000) MX[B]
        [10] -1 0       0xe7013000 - 0xe7013fff (0x1000) MX[B]
        [11] -1 0       0xe7012000 - 0xe7012fff (0x1000) MX[B]
        [12] -1 0       0xe0000000 - 0xdfffffff (0x0) MX[B]O
        [13] -1 0       0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
        [14] -1 0       0xe4000000 - 0xe4ffffff (0x1000000) MX[B](B)
        [15] 0  0       0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
        [16] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
        [17] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
        [18] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [19] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [20] -1 0       0x0000e400 - 0x0000e407 (0x8) IX[B]
        [21] -1 0       0x0000e000 - 0x0000e0ff (0x100) IX[B]
        [22] -1 0       0x0000dc00 - 0x0000dc7f (0x80) IX[B]
        [23] -1 0       0x0000d800 - 0x0000d8ff (0x100) IX[B]
        [24] -1 0       0x0000f000 - 0x0000f00f (0x10) IX[B]
        [25] -1 0       0x00001400 - 0x0000141f (0x20) IX[B]
        [26] 0  0       0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
        [27] 0  0       0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1440x900"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
864"
Got unexpected buttonTimer in state 0

```

---

### Post by 2pacalypse on 2006-05-26
sry for the double post but the entire log wont enter in 1 post,heres the rest plus my reply to the secound part of your reply

```

(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
Symbol __glXgetActiveScreen from module /usr/X11R6/lib/modules/extensions/libdri.a is unresolved!
Symbol __glXgetActiveScreen from module /usr/X11R6/lib/modules/extensions/libdri.a is unresolved!
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension LBX
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us,he,ru"
(**) Generic Keyboard: XkbLayout: "us,he,ru"
(**) Option "XkbOptions" "games"
(**) Generic Keyboard: XkbOptions: "games"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 5
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
(II) NVIDIA(0): Setting mode "1152x

```
and about the secound thing, im pretty sure i already did that but ill check against just to be sure

EDIT

i checked it again, and even when i write

```

sudo nano /etc/X11/xorg.conf

```
its giving me totally blank, black page with options below (^R etc.)

p.s.

I know this forum isnt the support team for third party things (in this case a game). but my game constantly crashes and i get these replies in the terminal. 

```

yaniv@2pacalypse:~$ /opt/planeshift/psclient
DEBUG: Software Renderer Initializing..
NOTIFY: Configured for driver [crystalspace.sndsys.software.driver.alsa]

planeshift.application.client:
  PlaneShift Crystal Blue
  This game uses Crystal Space Engine created by Jorrit and others
  0.99 r0 [Unix-x86-GCC]
All LOGS are off.
Mounting skin: /this/art/skins/elves.zip
Mounting skin: /planeshift/art/skins/base/client_base.zip
  psEngine initialized.
Using fontsize 16 for resolution 1024x768
WARNING! Object 'spikes_02' is not closed!
WARNING! Object '_s_sigil_06' is not closed!
WARNING! Object '_s_stairs_01' is not closed!
WARNING! Object '_s_sigil_04' is not closed!
WARNING! Object 'spikes_01' is not closed!
WARNING! Object '_s_sigil_02' is not closed!
...

crystalspace.graphics3d.shader.fixed:
  Multitexture units: moderate 4

planeshift.application.client:
  PSLoader: step 2: success

<src/common/util/psxmlparser.cpp:282> ParseFile:
  Could not find file: /planeshift/world/podium/sound.xml

planeshift.application.client:
  PSLoader: step 3: success

<src/client/psclientdr.cpp:251> HandleStatsUpdate:
  Stat request failed because CelClient not ready for 1388

crystalspace.engine.warning:
  Lightmaps are not up to date (no 'lm_precalc_info' found in cache).
  Use -relight cmd option to calc lighting.
Region hydlaa_common loaded successfully in 4214ms

<src/client/zonehandler.cpp:157> HandleMessage:
  Still loading maps, ignoring crossing to sector
  SectorWhereWeKeepEntitiesResidingInUnloadedMaps.

crystalspace.thingloader.parse:
  Bad UV coordinates for polygons in this thing![node:
  world,sector(name=hydlaa_plaza),meshobj(name=_s_laanx_statue_01V15a_02),param
  s]
  Bad UV coordinates for polygons in this thing![node:
  world,sector(name=hydlaa_plaza),meshobj(name=hydlaaplaza),params]
  Bad UV coordinates for polygons in this thing![node:
  world,sector(name=hydlaa_plaza),meshobj(name=_s_WoodsEnd01),params]

crystalspace.engine.warning:
  Lightmaps are not up to date (no 'lm_precalc_info' found in cache).
  Use -relight cmd option to calc lighting.
  Couldn't load cached lighting for 1 object(s):
      _s_fence_02_014
  Use -relight cmd option to refresh lighting.
Region hydlaa_plaza loaded successfully in 5397ms

<src/client/psengine.cpp:1622> BuildAppearance:
  Failed to set trait <traits><trait id="141" next="0" loc="HAIR_COLOR"
  mesh="0" mat="0" tex="0" shader="0.30,0.16,0.16"/></traits> for mesh.

<src/client/zonehandler.cpp:157> HandleMessage:
  Still loading maps, ignoring crossing to sector hydlaa_plaza.

<src/client/psclientdr.cpp:226> HandleDeadReckon:
  Sector crossed from SectorWhereWeKeepEntitiesResidingInUnloadedMaps to
  hydlaa_plaza after received DR.

<src/client/psclientdr.cpp:205> HandleDeadReckon:
  Got DR message for unknown entity 985.
  Got DR message for unknown entity 985.

<src/client/zonehandler.cpp:157> HandleMessage:
  Still loading maps, ignoring crossing to sector hydlaa_plaza.

crystalspace.engine.warning:
  Lightmaps are not up to date (no 'lm_precalc_info' found in cache).
  Use -relight cmd option to calc lighting.
  Couldn't load cached lighting for 1 object(s):
      openbook01
  Use -relight cmd option to refresh lighting.
Region laanx loaded successfully in 1439ms
  Lightmaps are not up to date (no 'lm_precalc_info' found in cache).
  Use -relight cmd option to calc lighting.
Region hydungeon loaded successfully in 165ms
  Lightmaps are not up to date (no 'lm_precalc_info' found in cache).
  Use -relight cmd option to calc lighting.
Region tavern_de_kadel loaded successfully in 1457ms
  Lightmaps are not up to date (no 'lm_precalc_info' found in cache).
  Use -relight cmd option to calc lighting.
  Couldn't load cached lighting for 32 object(s):
      _s_stairs_01_014
      _s_stairs_borders_01_010
      _s_stairs_borders_01_011
      _s_dungeon_ceiling_01_051
      ...
  Use -relight cmd option to refresh lighting.
Region wtower loaded successfully in 1405ms
  Lightmaps are not up to date (no 'lm_precalc_info' found in cache).
  Use -relight cmd option to calc lighting.
Region hyarena loaded successfully in 1711ms
  Lightmaps are not up to date (no 'lm_precalc_info' found in cache).
  Use -relight cmd option to calc lighting.
Region hyjayose loaded successfully in 174ms
  Lightmaps are not up to date (no 'lm_precalc_info' found in cache).
  Use -relight cmd option to calc lighting.
Region hyojapath loaded successfully in 391ms
  Lightmaps are not up to date (no 'lm_precalc_info' found in cache).
  Use -relight cmd option to calc lighting.
Region hysewers loaded successfully in 1437ms

planeshift.application.client:
  PSLoader: step 4: success

<src/client/pscelclient.cpp:1181> SetDRData:
  Ignoring DR pkt version 80 for entity Minknur Aureate with version 84.
  Ignoring DR pkt version 154 for entity Svend Svin with version 157.

crystalspace.maploader.parse.image:
  Could not open image file '/this/art/effects/arrowUV.jpg' on VFS!

crystalspace.maploader.parse.texture:
  Could not load texture 'arrowUV', using checkerboard instead[node:
  library,textures,texture(name=arrowUV)]

crystalspace.maploader.parse.image:
  Could not open image file '/this/art/effects/rect_texture1.png' on VFS!

crystalspace.maploader.parse.texture:
  Could not load texture 'rect_texture1', using checkerboard instead[node:
  library,textures,texture(name=rect_texture1)]

crystalspace.maploader.parse.image:
  Could not open image file '/this/art/effects/target.png' on VFS!

crystalspace.maploader.parse.texture:
  Could not load texture 'target', using checkerboard instead[node:
  library,textures,texture(name=target)]

planeshift.application.client:
  PSLoader: step 5: success
Segmentation fault
yaniv@2pacalypse:~$

```
what could be causing them? is it the computers/OS's fault or the game itself?

---

### Post by ifokkema on 2006-05-27
[QUOTE=2pacalypse]sry for the double post but the entire log wont enter in 1 post,heres the rest plus my reply to the secound part of your reply

(...)

```

sudo nano /etc/X11/xorg.conf

```
its giving me totally blank, black page with options below (^R etc.)[/QUOTE]

Hi,

1) This still wasn't the whole log file. Could you just paste the last bit then, it's usually the most informative in the case of an error.

2) Could you send the output of:
```
ls -lh /etc/X11/
```

Ivo

---

### Post by tseliot on 2006-05-27
Why don't you try my script (so as to install the latest Nvidia driver)?
[http://www.albertomilone.eu/europeo/nvidia_scripts1.html]("http://www.albertomilone.eu/europeo/nvidia_scripts1.html")

---

### Post by [S|G] on 2006-05-27
Try this:
```

sudo apt-get remove nvidia-glx nvidia-kernel-common nvidia-kernel-source linux-restricted-modules*

```

This will remove the installed NVidia drivers. Then try to install them again:
```

sudo apt-get install nvidia-glx nvidia-kernel-common nvidia-kernel-source linux-restricted-modules-`uname -r` linux-restricted-modules-common

```

After you do that, try to start X again.

---

### Post by 2pacalypse on 2006-05-27
[QUOTE=tseliot]Why don't you try my script (so as to install the latest Nvidia driver)?
[http://www.albertomilone.eu/europeo/nvidia_scripts1.html]("http://www.albertomilone.eu/europeo/nvidia_scripts1.html")[/QUOTE]

no thanks. a bad scrip has caused this problem in the first place.

besides, [S|G]'s  solution seems to have worked :D

Thank's [S|G] and everyone for helping

---

