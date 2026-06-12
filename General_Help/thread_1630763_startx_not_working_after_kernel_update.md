---
title: "startx not working after kernel update"
date: 2010-11-25
forum: General Help
---

### Post by ilantal on 2010-11-25
I was having a lot of trouble with my NVIDIA driver, so I tried updating to the latest version 260.19.21. I just received a notice to update my software and of course did so. Upon reboot I can no longer get into anything but a command line. startx tells me that the kernel expect version 260.19.06, which is what I replaced.

Here is the Xorg.0.log file:
[   964.178] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[   964.179] X Protocol Version 11, Revision 0
[   964.179] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[   964.179] Current Operating System: Linux ilan-laptop 2.6.35-23-generic #40-Ubuntu SMP Wed Nov 17 22:15:35 UTC 2010 i686
[   964.179] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-23-generic root=UUID=8b339174-2a10-45ac-85f2-def722ed57e4 ro quiet splash
[   964.180] Build Date: 16 September 2010  05:39:22PM
[   964.180] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[   964.180] Current version of pixman: 0.18.4
[   964.180] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[   964.181] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   964.182] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Nov 25 22:55:18 2010
[   964.182] (==) Using config file: "/etc/X11/xorg.conf"
[   964.183] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   964.183] (==) ServerLayout "Layout0"
[   964.184] (**) |-->Screen "Screen0" (0)
[   964.184] (**) |   |-->Monitor "Monitor0"
[   964.184] (**) |   |-->Device "Device0"
[   964.184] (**) |-->Input Device "Keyboard0"
[   964.184] (**) |-->Input Device "Mouse0"
[   964.184] (==) Automatically adding devices
[   964.184] (==) Automatically enabling devices
[   964.185] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   964.185] 	Entry deleted from font path.
[   964.185] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[   964.185] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   964.185] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[   964.185] (WW) Disabling Keyboard0
[   964.185] (WW) Disabling Mouse0
[   964.185] (II) Loader magic: 0x81f8e00
[   964.185] (II) Module ABI versions:
[   964.185] 	X.Org ANSI C Emulation: 0.4
[   964.185] 	X.Org Video Driver: 8.0
[   964.185] 	X.Org XInput driver : 11.0
[   964.185] 	X.Org Server Extension : 4.0
[   964.187] (--) PCI:*(0:1:0:0) 10de:0428:1462:3fe9 rev 161, Mem @ 0xfd000000/16777216, 0xd0000000/268435456, 0xfa000000/33554432, I/O @ 0x0000cc00/128, BIOS @ 0x????????/131072
[   964.187] (II) Open ACPI successful (/var/run/acpid.socket)
[   964.187] (II) LoadModule: "extmod"
[   964.188] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   964.189] (II) Module extmod: vendor="X.Org Foundation"
[   964.189] 	compiled for 1.9.0, module version = 1.0.0
[   964.189] 	Module class: X.Org Server Extension
[   964.189] 	ABI class: X.Org Server Extension, version 4.0
[   964.189] (II) Loading extension MIT-SCREEN-SAVER
[   964.189] (II) Loading extension XFree86-VidModeExtension
[   964.189] (II) Loading extension XFree86-DGA
[   964.189] (II) Loading extension DPMS
[   964.189] (II) Loading extension XVideo
[   964.189] (II) Loading extension XVideo-MotionCompensation
[   964.189] (II) Loading extension X-Resource
[   964.189] (II) LoadModule: "dbe"
[   964.189] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   964.190] (II) Module dbe: vendor="X.Org Foundation"
[   964.190] 	compiled for 1.9.0, module version = 1.0.0
[   964.190] 	Module class: X.Org Server Extension
[   964.190] 	ABI class: X.Org Server Extension, version 4.0
[   964.190] (II) Loading extension DOUBLE-BUFFER
[   964.190] (II) LoadModule: "glx"
[   964.190] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   964.222] (II) Module glx: vendor="NVIDIA Corporation"
[   964.223] 	compiled for 4.0.2, module version = 1.0.0
[   964.223] 	Module class: X.Org Server Extension
[   964.223] (II) NVIDIA GLX Module  260.19.21  Thu Nov  4 20:52:05 PDT 2010
[   964.223] (II) Loading extension GLX
[   964.223] (II) LoadModule: "record"
[   964.223] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   964.223] (II) Module record: vendor="X.Org Foundation"
[   964.223] 	compiled for 1.9.0, module version = 1.13.0
[   964.223] 	Module class: X.Org Server Extension
[   964.223] 	ABI class: X.Org Server Extension, version 4.0
[   964.223] (II) Loading extension RECORD
[   964.223] (II) LoadModule: "dri"
[   964.223] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   964.224] (II) Module dri: vendor="X.Org Foundation"
[   964.224] 	compiled for 1.9.0, module version = 1.0.0
[   964.224] 	ABI class: X.Org Server Extension, version 4.0
[   964.224] (II) Loading extension XFree86-DRI
[   964.224] (II) LoadModule: "dri2"
[   964.224] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   964.224] (II) Module dri2: vendor="X.Org Foundation"
[   964.224] 	compiled for 1.9.0, module version = 1.2.0
[   964.224] 	ABI class: X.Org Server Extension, version 4.0
[   964.224] (II) Loading extension DRI2
[   964.224] (II) LoadModule: "nvidia"
[   964.225] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[   964.225] (II) Module nvidia: vendor="NVIDIA Corporation"
[   964.225] 	compiled for 4.0.2, module version = 1.0.0
[   964.225] 	Module class: X.Org Video Driver
[   964.225] (II) NVIDIA dlloader X Driver  260.19.21  Thu Nov  4 20:26:43 PDT 2010
[   964.225] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[   964.225] (--) using VT number 8

[   964.240] (II) Loading sub module "fb"
[   964.240] (II) LoadModule: "fb"
[   964.240] (II) Loading /usr/lib/xorg/modules/libfb.so
[   964.240] (II) Module fb: vendor="X.Org Foundation"
[   964.240] 	compiled for 1.9.0, module version = 1.0.0
[   964.240] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   964.240] (II) Loading sub module "wfb"
[   964.240] (II) LoadModule: "wfb"
[   964.240] (II) Loading /usr/lib/xorg/modules/libwfb.so
[   964.241] (II) Module wfb: vendor="X.Org Foundation"
[   964.241] 	compiled for 1.9.0, module version = 1.0.0
[   964.241] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   964.241] (II) Loading sub module "ramdac"
[   964.241] (II) LoadModule: "ramdac"
[   964.241] (II) Module "ramdac" already built-in
[   964.241] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[   964.241] (==) NVIDIA(0): RGB weight 888
[   964.241] (==) NVIDIA(0): Default visual is TrueColor
[   964.241] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[   964.241] (**) NVIDIA(0): Enabling RENDER acceleration
[   964.241] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[   964.241] (II) NVIDIA(0):     enabled.
[   964.242] (EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
[   964.242] (EE) NVIDIA(0):     system's kernel log for additional error messages and
[   964.242] (EE) NVIDIA(0):     consult the NVIDIA README for details.
[   964.242] (EE) NVIDIA(0):  *** Aborting ***
[   964.242] (II) UnloadModule: "nvidia"
[   964.242] (II) UnloadModule: "wfb"
[   964.242] (II) UnloadModule: "fb"
[   964.242] (EE) Screen(s) found, but none have a usable configuration.
[   964.242] 
Fatal server error:
[   964.242] no screens found
[   964.242] 
Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[   964.242] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[   964.242] 
[   964.256]  ddxSigGiveUp: Closing log

What do I do to get my Ubuntu back up and running? I don't want to be stuck at the command line level.

Thanks,
Ilan

---

### Post by tredegar on 2010-11-25
When the kernel is updated, the NVIDIA driver needs to be reinstalled so it can link in properly.

On some PCs, I do this myself, D/Ling the driver from NV, stopping X, and compiling / installing the module. This takes all of 3 minutes. I have slow hardware.
On others, ubuntu seems to manage it itself (somewhat to my surpise).

All of my hardware is much older than yours.

How did you install the NVIDIA driver in the first place? Clicky-clicky the ubuntu way, or manually, with the CLI and a D/L from NVIDIA?

If manually, from the command line, then you need to do it again (just follow the steps you took the last time).
If the clicky-clicky ubuntu way, and this has failed, then try the manual way (Disable  / uninstall ) the clicky thing first though, or there'll probably be trouble.

I maintain a number of very different linux PCs and have had to leave a note on each to the effect of "NVIDIA handled by 'buntu or myself", because I forget. If one way doesn't work, the other always has done, but this seems to be hardware specific.

Hope this helps.

---

### Post by WorMzy on 2010-11-25
Try logging in and running
```
sudo apt-get install --reinstall nvidia-current
startx
```

---

### Post by ilantal on 2010-11-26
Thank you very much gentlemen for the replies. It is always a very nice feeling when someone is willing to take the time to help you out of troubles.
Since I did the clicky-click install, I couldn't use tredgar help, but thanks anyway. I don't have enough knowledge to use it.
WorMzy's suggestion with the sudo install worked like a charm. It took a couple of minutes to grind through all the mechanics, but at least it was the computer grinding and not me.

In any case I am posting this reply from my now living Ubuntu machine, so it shows that it is back in working order.

Thanks again,
Ilan

---

