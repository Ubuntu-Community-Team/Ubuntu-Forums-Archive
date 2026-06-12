---
title: "broken graphics drivers."
date: 2009-12-30
forum: General Help
---

### Post by amiga78 on 2009-12-30
My Ubuntu 9.1 (desktop i386) is not starting. It hangs when loading the graphic drivers and the screen starts to flicker between a command prompt and a black screen. 

I think this happened after I tried to install some Nvidia drivers. I have two gfx cards one PCI and one AGP. I tried to get them both to work and I failed. :(

So I would like to just remove ALL graphic drivers and restore default ones that ubuntu was instaled with to at least be able to boot. 

I can boot up to the command prompt when choosing the safeboot option at startup. But I don't know the commands to continue. 

All help is appreciated. =)

---

### Post by amiga78 on 2009-12-30
(I have a GeForce 2 GTS in AGP and ATI Rage II 64 in PCI works fine under windoze)

---

### Post by amiga78 on 2009-12-30
[FONT=Fixedsys]_apt-get -f install_[/FONT] told me to do a [FONT=Fixedsys]_apt-get autoremove_[/FONT] and removed [FONT=Fixedsys]_binutils-static nvidia-180-modaliases_
[/FONT] 
Then [FONT=Fixedsys]_startx_[/FONT] gives me 
[FONT=Fixedsys][U]Fatal server error:
 No screens found[/U][/FONT]

after reboot its all the same again. just blinking between a loginprompt and black screen. 

Heeeelp :confused:

---

### Post by ST3ALTHPSYCH0 on 2009-12-30
try choosing a recovery kernel from grub.
at the menu that appears choose root prompt with networking
run the following commands
```

apt-get install envyng-qt
envyng -t

```

you won't need "sudo" b/c you'll be root.

choose the option to remove appropriate drivers from that menu and reboot

---

### Post by amiga78 on 2009-12-30
Thanx. =) 

I removed all the drivers and tried to restart but couldn't so I reinstalled the drivers suggested in envyng and still same problem. it stops at a prompt asking for login and password and starts switching between that screen and a blank screen on the PCI card which is selected as default display device in bios. 

when I try to start x when in safe boot I still get no screen found 

The Xorg.0.log sais:
```

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux frysen2 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686
Kernel command line: root=UUID=2124c262-4f06-4228-8ccc-4ee4de384e98 ro  single
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Dec 30 19:25:49 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
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
(--) using VT number 2

(--) PCI:*(0:0:17:0) 1002:4755:1002:4755 ATI Technologies Inc 3D Rage II+ 215GTB [Mach64 GTB] rev 154, Mem @ 0xcf000000/16777216, 0xcefff000/4096, I/O @ 0x0000d800/256, BIOS @ 0x????????/131072
(--) PCI: (0:1:0:0) 10de:0150:1043:4016 nVidia Corporation NV15 [GeForce2 GTS/Pro] rev 163, Mem @ 0xcc000000/16777216, 0xc0000000/134217728, BIOS @ 0x????????/65536
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) No APM support in BIOS or kernel
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
(WW) "dri2" will not be loaded unless you've specified it to be loaded elsewhere.
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded even though the default is to disable it.
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
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
(II) LoadModule: "type1"
(WW) Warning, couldn't open module type1
(II) UnloadModule: "type1"
(EE) Failed to load module "type1" (module does not exist, 0)
(II) LoadModule: "freetype"
(WW) Warning, couldn't open module freetype
(II) UnloadModule: "freetype"
(EE) Failed to load module "freetype" (module does not exist, 0)
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="FireGL - ATI Technologies Inc."
    compiled for 7.4.0, module version = 1.0.0
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
(II) Primary Device is: PCI 00@00:11:0
(WW) Falling back to old probe method for fglrx
(II) ATI Proprietary Linux Driver Version Identifier:8.66.10
(II) ATI Proprietary Linux Driver Release Identifier: 8.66.1                               
(II) ATI Proprietary Linux Driver Build Date: Sep  3 2009 21:35:19
(II) PCS database file /etc/ati/amdpcsdb not found
(II)   Creating PCS database from initial defaults instead
(--) Assigning device section with no busID to primary device
(EE) No devices detected.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
```Any suggestion ?

---

### Post by amiga78 on 2009-12-30
Is it possible to use the Package Manager on the live cd to sort the packages in the ubuntu installation on my harddrive ?

---

### Post by amiga78 on 2009-12-30
By the way, when booting in to the previous kernel from the grub menu the same thing happens. :(

---

### Post by amiga78 on 2009-12-30
Is there some easy way to see what packages are installed on my harddisk so that I can do some : sudo apt-get remove on them ?

---

### Post by amiga78 on 2010-01-06
What is the command to list all packages that can be removed with the "apt-get" ? Please ..

---

