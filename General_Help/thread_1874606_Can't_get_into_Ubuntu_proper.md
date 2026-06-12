---
title: "Can't get into Ubuntu proper"
date: 2011-11-03
forum: General Help
---

### Post by Djalmahal on 2011-11-03
HI,

I'm running 11.04 and I did an standard update including new Kernel,acpi etc. Now when I boot it ends up with "Starting daemon monitor: monit" and hangs up. I'm still able to boot into fainsafe graphics mode but that's it.

I'm lost, not knowing what to do.
Any tips?

Could it be that I have to update the nvidia driver for the new kernel or is that just showing up as an error in the log file because I use the graphics failsafe mode?


Andreas

Here is the output of xorg5, if you need any other log files let me know
```
[    21.187] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    21.187] X Protocol Version 11, Revision 0
[    21.187] Build Operating System: Linux 2.6.24-28-server i686 Ubuntu
[    21.187] Current Operating System: Linux andreas-G60JX 2.6.38-12-generic-pae #51-Ubuntu SMP Wed Sep 28 16:11:32 UTC 2011 i686
[    21.187] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-12-generic-pae root=UUID=08452133-3964-47fe-a30b-da79a83bab0c ro quiet splash vt.handoff=7
[    21.187] Build Date: 13 October 2011  05:38:22PM
[    21.187] xorg-server 2:1.10.1-1ubuntu1.3 (For technical support please see http://www.ubuntu.com/support) 
[    21.187] Current version of pixman: 0.20.2
[    21.187] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    21.187] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    21.188] (==) Log file: "/var/log/Xorg.5.log", Time: Thu Nov  3 08:00:05 2011
[    21.188] (==) Using config file: "/etc/X11/xorg.conf"
[    21.188] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    21.188] (==) ServerLayout "Layout0"
[    21.188] (**) |-->Screen "Screen0" (0)
[    21.188] (**) |   |-->Monitor "Monitor0"
[    21.188] (**) |   |-->Device "Device0"
[    21.188] (**) |-->Input Device "Keyboard0"
[    21.188] (**) |-->Input Device "Mouse0"
[    21.188] (==) Automatically adding devices
[    21.188] (==) Automatically enabling devices
[    21.189] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    21.189] 	Entry deleted from font path.
[    21.189] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    21.189] 	Entry deleted from font path.
[    21.189] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    21.189] 	Entry deleted from font path.
[    21.189] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    21.189] 	Entry deleted from font path.
[    21.189] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    21.189] 	Entry deleted from font path.
[    21.189] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    21.189] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    21.189] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    21.189] (WW) Disabling Keyboard0
[    21.189] (WW) Disabling Mouse0
[    21.189] (II) Loader magic: 0x8200ac0
[    21.189] (II) Module ABI versions:
[    21.189] 	X.Org ANSI C Emulation: 0.4
[    21.189] 	X.Org Video Driver: 10.0
[    21.189] 	X.Org XInput driver : 12.3
[    21.189] 	X.Org Server Extension : 5.0
[    21.190] (--) PCI:*(0:1:0:0) 10de:0cb1:1043:203c rev 162, Mem @ 0xf2000000/16777216, 0xe0000000/268435456, 0xf0000000/33554432, I/O @ 0x0000d000/128, BIOS @ 0x????????/524288
[    21.190] (II) Open ACPI successful (/var/run/acpid.socket)
[    21.190] (II) LoadModule: "extmod"
[    21.191] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    21.191] (II) Module extmod: vendor="X.Org Foundation"
[    21.191] 	compiled for 1.10.1, module version = 1.0.0
[    21.191] 	Module class: X.Org Server Extension
[    21.191] 	ABI class: X.Org Server Extension, version 5.0
[    21.191] (II) Loading extension MIT-SCREEN-SAVER
[    21.191] (II) Loading extension XFree86-VidModeExtension
[    21.191] (II) Loading extension XFree86-DGA
[    21.191] (II) Loading extension DPMS
[    21.191] (II) Loading extension XVideo
[    21.191] (II) Loading extension XVideo-MotionCompensation
[    21.191] (II) Loading extension X-Resource
[    21.191] (II) LoadModule: "dbe"
[    21.191] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    21.191] (II) Module dbe: vendor="X.Org Foundation"
[    21.191] 	compiled for 1.10.1, module version = 1.0.0
[    21.191] 	Module class: X.Org Server Extension
[    21.191] 	ABI class: X.Org Server Extension, version 5.0
[    21.191] (II) Loading extension DOUBLE-BUFFER
[    21.191] (II) LoadModule: "glx"
[    21.192] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    21.192] (II) Module glx: vendor="X.Org Foundation"
[    21.192] 	compiled for 1.10.1, module version = 1.0.0
[    21.192] 	ABI class: X.Org Server Extension, version 5.0
[    21.192] (==) AIGLX enabled
[    21.192] (II) Loading extension GLX
[    21.192] (II) LoadModule: "record"
[    21.192] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    21.193] (II) Module record: vendor="X.Org Foundation"
[    21.193] 	compiled for 1.10.1, module version = 1.13.0
[    21.193] 	Module class: X.Org Server Extension
[    21.193] 	ABI class: X.Org Server Extension, version 5.0
[    21.193] (II) Loading extension RECORD
[    21.193] (II) LoadModule: "dri"
[    21.193] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    21.193] (II) Module dri: vendor="X.Org Foundation"
[    21.193] 	compiled for 1.10.1, module version = 1.0.0
[    21.193] 	ABI class: X.Org Server Extension, version 5.0
[    21.193] (II) Loading extension XFree86-DRI
[    21.193] (II) LoadModule: "dri2"
[    21.194] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    21.194] (II) Module dri2: vendor="X.Org Foundation"
[    21.194] 	compiled for 1.10.1, module version = 1.2.0
[    21.194] 	ABI class: X.Org Server Extension, version 5.0
[    21.194] (II) Loading extension DRI2
[    21.194] (II) LoadModule: "nvidia"
[    21.194] (WW) Warning, couldn't open module nvidia
[    21.194] (II) UnloadModule: "nvidia"
[    21.195] (II) Unloading nvidia
[    21.195] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    21.195] (EE) No drivers available.
[    21.195] 
Fatal server error:
[    21.195] no screens found
[    21.195] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[    21.195] Please also check the log file at "/var/log/Xorg.5.log" for additional information.
[    21.195] 

```

---

