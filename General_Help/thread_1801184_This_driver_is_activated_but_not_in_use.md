---
title: "This driver is activated but not in use"
date: 2011-07-10
forum: General Help
---

### Post by srisharan on 2011-07-10
Hello everyone ):P
I just installed natty today after erasing the previous maverick and windows dual boot.Everything works fine.But there is one problem.The propriety driver for Nvidia seems to be activated but not in use.I still get unity desktop,(couldn't get it before installing the propriety driver).

[IMG]http://dl.dropbox.com/u/27544813/Screenshot.png[/IMG]

I have tried removing and activating it again but it ended up the same again.I know that this problem has been encountered lot of times,but I searched everywhere and didn't find anything to help me.If anyone knows what to do please help me.And finally thanks for the help :D

---

### Post by mikewhatever on 2011-07-10
First, make sure the open source nvidia driver is removed:
```
sudo apt-get --purge remove xserver-xorg-video-nouveau
```

...then, try run **sudo nvidia-xconfig**. That should,hopefully, force the system to use the proprietary driver.

---

### Post by wildmanne39 on 2011-07-10
Hi, that is just a bug that says it is not in use, I have the same problem but my nvidia driver works great. If you can see the desktop and the green dots are lit up in additional drivers then they are activated you do not have to worry about it.

---

### Post by srisharan on 2011-07-10
> **mikewhatever said:**
> First, make sure the open source nvidia driver is removed:
```
sudo apt-get --purge remove xserver-xorg-video-nouveau
```

...then, try run **sudo nvidia-xconfig**. That should,hopefully, force the system to use the proprietary driver.

Tried that already,didnt work :(

---

### Post by srisharan on 2011-07-10
> **wildmanne39 said:**
> Hi, that is just a bug that says it is not in use, I have the same problem but my nvidia driver works great. If you can see the desktop and the green dots are lit up in additional drivers then they are activated you do not have to worry about it.
I dont know if that is the case.I still get a Plymouth not just a text there when booting.You dont get a proper Plymouth when booting with an Nvidia card right

---

### Post by realzippy on 2011-07-10
What happens when running nvidia-settings?
It should complain when driver is not in use.
If so,run

```
nvidia-bug-report.sh

```
which produces nvidia-bug-report.log.gz in your home directory,
post that file....

---

### Post by srisharan on 2011-07-10
> **realzippy said:**
> What happens when running nvidia-settings?
It should complain when driver is not in use.
If so,run
.......

No It open the  settings properly.But I ran the bug report anyway.Here is the result
```
____________________________________________

Start of NVIDIA bug report log file.  Please include this file
when reporting a graphics driver bug via the nV News NVIDIA
Linux forum (see www.nvnews.net) or by sending email to
'linux-bugs@nvidia.com'.

nvidia-bug-report.sh Version: 9611234

Date: Thu Jul 14 14:11:55 IST 2011
uname: Linux sharan-Aspire-5738 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux

____________________________________________

*** /etc/issue
*** ls: -rw-r--r-- 1 root root 20 2011-04-21 22:20:43.000000000 +0530 /etc/issue
Ubuntu 11.04 \n \l


____________________________________________

*** /etc/debian_version
*** ls: -rw-r--r-- 1 root root 12 2010-10-21 18:17:40.000000000 +0530 /etc/debian_version
squeeze/sid

____________________________________________

*** /var/log/nvidia-installer.log
*** ls: -rw-r--r-- 1 root root 2890 2011-07-14 04:49:30.134356947 +0530 /var/log/nvidia-installer.log
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Thu Jul 14 04:49:30 2011
installer version: 275.09.07

PATH: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

option status:
  license pre-accepted               : false
  update                             : false
  force update                       : false
  expert                             : false
  uninstall                          : false
  driver info                        : false
  precompiled interfaces             : true
  no ncurses color                   : false
  query latest version               : false
  no questions                       : false
  silent                             : false
  no recursion                       : false
  no backup                          : false
  kernel module only                 : false
  sanity                             : false
  add this kernel                    : false
  no runlevel check                  : false
  no network                         : false
  no ABI note                        : false
  no RPMs                            : false
  no kernel module                   : false
  force SELinux                      : default
  no X server check                  : false
  no cc version check                : false
  run distro scripts                 : true
  no nouveau check                   : false
  run nvidia-xconfig                 : false
  sigwinch work around               : true
  force tls                          : (not specified)
  X install prefix                   : (not specified)
  X library install path             : (not specified)
  X module install path              : (not specified)
  OpenGL install prefix              : (not specified)
  OpenGL install libdir              : (not specified)
  utility install prefix             : (not specified)
  utility install libdir             : (not specified)
  installer prefix                   : (not specified)
  doc install prefix                 : (not specified)
  kernel name                        : (not specified)
  kernel include path                : (not specified)
  kernel source path                 : (not specified)
  kernel output path                 : (not specified)
  kernel install path                : (not specified)
  precompiled kernel interfaces path : (not specified)
  precompiled kernel interfaces url  : (not specified)
  proc mount point                   : /proc
  ui                                 : (not specified)
  tmpdir                             : /tmp
  ftp mirror                         : ftp://download.nvidia.com
  RPM file list                      : (not specified)
  selinux chcon type                 : (not specified)

Using: nvidia-installer ncurses user interface
-> The file '/tmp/.X0-lock' exists and appears to contain the process ID '7821'
   of a runnning X server.

____________________________________________

*** /var/log/Xorg.0.log
*** ls: -rw-r--r-- 1 root root 17982 2011-07-14 13:52:20.122141988 +0530 /var/log/Xorg.0.log
[    16.791] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    16.791] X Protocol Version 11, Revision 0
[    16.791] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    16.791] Current Operating System: Linux sharan-Aspire-5738 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686
[    16.791] Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.38-8-generic root=UUID=4829be89-f413-4aaa-bfc5-b14e8c8ebebf ro quiet splash vt.handoff=7
[    16.791] Build Date: 21 May 2011  11:38:35AM
[    16.791] xorg-server 2:1.10.1-1ubuntu1.1 (For technical support please see http://www.ubuntu.com/support) 
[    16.791] Current version of pixman: 0.20.2
[    16.791] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    16.791] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    16.792] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Jul 14 13:52:17 2011
[    16.792] (==) Using config file: "/etc/X11/xorg.conf"
[    16.792] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    16.792] (==) ServerLayout "Layout0"
[    16.792] (**) |-->Screen "Screen0" (0)
[    16.792] (**) |   |-->Monitor "Monitor0"
[    16.792] (**) |   |-->Device "Device0"
[    16.792] (**) |-->Input Device "Keyboard0"
[    16.792] (**) |-->Input Device "Mouse0"
[    16.792] (==) Automatically adding devices
[    16.792] (==) Automatically enabling devices
[    16.793] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    16.793] 	Entry deleted from font path.
[    16.793] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    16.793] 	Entry deleted from font path.
[    16.793] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    16.793] 	Entry deleted from font path.
[    16.793] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    16.793] 	Entry deleted from font path.
[    16.793] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    16.793] 	Entry deleted from font path.
[    16.793] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    16.793] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    16.793] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    16.793] (WW) Disabling Keyboard0
[    16.793] (WW) Disabling Mouse0
[    16.793] (II) Loader magic: 0x81ffde0
[    16.793] (II) Module ABI versions:
[    16.793] 	X.Org ANSI C Emulation: 0.4
[    16.793] 	X.Org Video Driver: 10.0
[    16.793] 	X.Org XInput driver : 12.3
[    16.793] 	X.Org Server Extension : 5.0
[    16.794] (--) PCI:*(0:1:0:0) 10de:06ec:1025:0205 rev 161, Mem @ 0xf2000000/16777216, 0xd0000000/268435456, 0xf0000000/33554432, I/O @ 0x00002000/128
[    16.794] (II) Open ACPI successful (/var/run/acpid.socket)
[    16.794] (II) LoadModule: "extmod"
[    16.795] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    16.795] (II) Module extmod: vendor="X.Org Foundation"
[    16.795] 	compiled for 1.10.1, module version = 1.0.0
[    16.795] 	Module class: X.Org Server Extension
[    16.795] 	ABI class: X.Org Server Extension, version 5.0
[    16.795] (II) Loading extension MIT-SCREEN-SAVER
[    16.795] (II) Loading extension XFree86-VidModeExtension
[    16.795] (II) Loading extension XFree86-DGA
[    16.795] (II) Loading extension DPMS
[    16.795] (II) Loading extension XVideo
[    16.795] (II) Loading extension XVideo-MotionCompensation
[    16.795] (II) Loading extension X-Resource
[    16.795] (II) LoadModule: "dbe"
[    16.795] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    16.796] (II) Module dbe: vendor="X.Org Foundation"
[    16.796] 	compiled for 1.10.1, module version = 1.0.0
[    16.796] 	Module class: X.Org Server Extension
[    16.796] 	ABI class: X.Org Server Extension, version 5.0
[    16.796] (II) Loading extension DOUBLE-BUFFER
[    16.796] (II) LoadModule: "glx"
[    16.796] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    16.824] (II) Module glx: vendor="NVIDIA Corporation"
[    16.825] 	compiled for 4.0.2, module version = 1.0.0
[    16.825] 	Module class: X.Org Server Extension
[    16.825] (II) NVIDIA GLX Module  270.41.06  Mon Apr 18 15:11:28 PDT 2011
[    16.825] (II) Loading extension GLX
[    16.825] (II) LoadModule: "record"
[    16.825] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    16.825] (II) Module record: vendor="X.Org Foundation"
[    16.825] 	compiled for 1.10.1, module version = 1.13.0
[    16.825] 	Module class: X.Org Server Extension
[    16.825] 	ABI class: X.Org Server Extension, version 5.0
[    16.825] (II) Loading extension RECORD
[    16.825] (II) LoadModule: "dri"
[    16.826] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    16.826] (II) Module dri: vendor="X.Org Foundation"
[    16.826] 	compiled for 1.10.1, module version = 1.0.0
[    16.826] 	ABI class: X.Org Server Extension, version 5.0
[    16.826] (II) Loading extension XFree86-DRI
[    16.826] (II) LoadModule: "dri2"
[    16.826] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    16.826] (II) Module dri2: vendor="X.Org Foundation"
[    16.826] 	compiled for 1.10.1, module version = 1.2.0
[    16.826] 	ABI class: X.Org Server Extension, version 5.0
[    16.826] (II) Loading extension DRI2
[    16.826] (II) LoadModule: "nvidia"
[    16.826] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    16.827] (II) Module nvidia: vendor="NVIDIA Corporation"
[    16.827] 	compiled for 4.0.2, module version = 1.0.0
[    16.827] 	Module class: X.Org Video Driver
[    16.827] (II) NVIDIA dlloader X Driver  270.41.06  Mon Apr 18 14:55:51 PDT 2011
[    16.827] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    16.827] (++) using VT number 7

[    16.827] (II) Loading sub module "fb"
[    16.827] (II) LoadModule: "fb"
[    16.827] (II) Loading /usr/lib/xorg/modules/libfb.so
[    16.827] (II) Module fb: vendor="X.Org Foundation"
[    16.827] 	compiled for 1.10.1, module version = 1.0.0
[    16.827] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    16.827] (II) Loading sub module "wfb"
[    16.827] (II) LoadModule: "wfb"
[    16.828] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    16.828] (II) Module wfb: vendor="X.Org Foundation"
[    16.828] 	compiled for 1.10.1, module version = 1.0.0
[    16.828] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    16.828] (II) Loading sub module "ramdac"
[    16.828] (II) LoadModule: "ramdac"
[    16.828] (II) Module "ramdac" already built-in
[    16.828] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    16.828] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    16.828] (II) Loading /usr/lib/xorg/modules/libfb.so
[    16.828] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    16.828] (==) NVIDIA(0): RGB weight 888
[    16.828] (==) NVIDIA(0): Default visual is TrueColor
[    16.828] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    18.016] (II) NVIDIA(GPU-0): Display (LGD LP156WH2-TLE1 (DFP-0)) does not support NVIDIA 3D
[    18.016] (II) NVIDIA(GPU-0):     Vision stereo.
[    18.018] (II) NVIDIA(0): NVIDIA GPU GeForce G 105M (G98) at PCI:1:0:0 (GPU-0)
[    18.018] (--) NVIDIA(0): Memory: 524288 kBytes
[    18.018] (--) NVIDIA(0): VideoBIOS: 62.98.5a.00.18
[    18.018] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    18.018] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    18.018] (--) NVIDIA(0): Connected display device(s) on GeForce G 105M at PCI:1:0:0
[    18.018] (--) NVIDIA(0):     LGD LP156WH2-TLE1 (DFP-0)
[    18.018] (--) NVIDIA(0): LGD LP156WH2-TLE1 (DFP-0): 330.0 MHz maximum pixel clock
[    18.018] (--) NVIDIA(0): LGD LP156WH2-TLE1 (DFP-0): Internal Dual Link LVDS
[    18.073] (II) NVIDIA(0): Assigned Display Device: DFP-0
[    18.073] (==) NVIDIA(0): 
[    18.073] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    18.073] (==) NVIDIA(0):     will be used as the requested mode.
[    18.073] (==) NVIDIA(0): 
[    18.073] (II) NVIDIA(0): Validated modes:
[    18.073] (II) NVIDIA(0):     "nvidia-auto-select"
[    18.073] (II) NVIDIA(0): Virtual screen size determined to be 1366 x 768
[    19.129] (--) NVIDIA(0): DPI set to (102, 102); computed from "UseEdidDpi" X config
[    19.129] (--) NVIDIA(0):     option
[    19.129] (--) Depth 24 pixmap format is 32 bpp
[    19.129] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    19.136] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    19.461] (II) Loading extension NV-GLX
[    19.507] (==) NVIDIA(0): Disabling shared memory pixmaps
[    19.507] (==) NVIDIA(0): Backing store disabled
[    19.507] (==) NVIDIA(0): Silken mouse enabled
[    19.508] (**) NVIDIA(0): DPMS enabled
[    19.508] (II) Loading extension NV-CONTROL
[    19.508] (II) Loading extension XINERAMA
[    19.508] (II) Loading sub module "dri2"
[    19.508] (II) LoadModule: "dri2"
[    19.509] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    19.509] (II) Module dri2: vendor="X.Org Foundation"
[    19.509] 	compiled for 1.10.1, module version = 1.2.0
[    19.509] 	ABI class: X.Org Server Extension, version 5.0
[    19.509] (II) NVIDIA(0): [DRI2] Setup complete
[    19.509] (==) RandR enabled
[    19.509] (II) Initializing built-in extension Generic Event Extension
[    19.509] (II) Initializing built-in extension SHAPE
[    19.509] (II) Initializing built-in extension MIT-SHM
[    19.509] (II) Initializing built-in extension XInputExtension
[    19.509] (II) Initializing built-in extension XTEST
[    19.509] (II) Initializing built-in extension BIG-REQUESTS
[    19.509] (II) Initializing built-in extension SYNC
[    19.509] (II) Initializing built-in extension XKEYBOARD
[    19.509] (II) Initializing built-in extension XC-MISC
[    19.509] (II) Initializing built-in extension SECURITY
[    19.509] (II) Initializing built-in extension XINERAMA
[    19.509] (II) Initializing built-in extension XFIXES
[    19.509] (II) Initializing built-in extension RENDER
[    19.509] (II) Initializing built-in extension RANDR
[    19.509] (II) Initializing built-in extension COMPOSITE
[    19.509] (II) Initializing built-in extension DAMAGE
[    19.509] (II) Initializing built-in extension GESTURE
[    19.512] (II) Initializing extension GLX
[    19.538] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    19.549] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    19.550] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    19.550] (II) LoadModule: "evdev"
[    19.550] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.550] (II) Module evdev: vendor="X.Org Foundation"
[    19.550] 	compiled for 1.10.0.902, module version = 2.6.0
[    19.550] 	Module class: X.Org XInput Driver
[    19.550] 	ABI class: X.Org XInput driver, version 12.3
[    19.550] (II) Using input driver 'evdev' for 'Power Button'
[    19.550] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.550] (**) Power Button: always reports core events
[    19.550] (**) Power Button: Device: "/dev/input/event2"
[    19.551] (--) Power Button: Found keys
[    19.551] (II) Power Button: Configuring as keyboard
[    19.551] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    19.551] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    19.551] (**) Option "xkb_rules" "evdev"
[    19.551] (**) Option "xkb_model" "pc105"
[    19.551] (**) Option "xkb_layout" "us"
[    19.552] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    19.552] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    19.552] (II) Using input driver 'evdev' for 'Video Bus'
[    19.552] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.552] (**) Video Bus: always reports core events
[    19.552] (**) Video Bus: Device: "/dev/input/event4"
[    19.552] (--) Video Bus: Found keys
[    19.552] (II) Video Bus: Configuring as keyboard
[    19.552] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input4/event4"
[    19.552] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    19.552] (**) Option "xkb_rules" "evdev"
[    19.552] (**) Option "xkb_model" "pc105"
[    19.552] (**) Option "xkb_layout" "us"
[    19.557] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    19.557] (II) No input driver/identifier specified (ignoring)
[    19.557] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    19.557] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    19.557] (II) Using input driver 'evdev' for 'Sleep Button'
[    19.557] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.557] (**) Sleep Button: always reports core events
[    19.557] (**) Sleep Button: Device: "/dev/input/event1"
[    19.557] (--) Sleep Button: Found keys
[    19.557] (II) Sleep Button: Configuring as keyboard
[    19.557] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1/event1"
[    19.557] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    19.557] (**) Option "xkb_rules" "evdev"
[    19.557] (**) Option "xkb_model" "pc105"
[    19.557] (**) Option "xkb_layout" "us"
[    19.560] (II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event6)
[    19.561] (II) No input driver/identifier specified (ignoring)
[    19.564] (II) config/udev: Adding input device CNF7017 (/dev/input/event5)
[    19.564] (**) CNF7017: Applying InputClass "evdev keyboard catchall"
[    19.564] (II) Using input driver 'evdev' for 'CNF7017'
[    19.564] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.564] (**) CNF7017: always reports core events
[    19.564] (**) CNF7017: Device: "/dev/input/event5"
[    19.564] (--) CNF7017: Found keys
[    19.564] (II) CNF7017: Configuring as keyboard
[    19.564] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/input/input5/event5"
[    19.564] (II) XINPUT: Adding extended input device "CNF7017" (type: KEYBOARD)
[    19.564] (**) Option "xkb_rules" "evdev"
[    19.564] (**) Option "xkb_model" "pc105"
[    19.564] (**) Option "xkb_layout" "us"
[    19.569] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    19.569] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    19.569] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    19.569] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.569] (**) AT Translated Set 2 keyboard: always reports core events
[    19.569] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    19.569] (--) AT Translated Set 2 keyboard: Found keys
[    19.569] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    19.569] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    19.569] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    19.569] (**) Option "xkb_rules" "evdev"
[    19.569] (**) Option "xkb_model" "pc105"
[    19.569] (**) Option "xkb_layout" "us"
[    19.570] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event7)
[    19.570] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    19.570] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    19.570] (II) LoadModule: "synaptics"
[    19.570] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    19.570] (II) Module synaptics: vendor="X.Org Foundation"
[    19.570] 	compiled for 1.10.1, module version = 1.3.99
[    19.570] 	Module class: X.Org XInput Driver
[    19.570] 	ABI class: X.Org XInput driver, version 12.3
[    19.570] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    19.570] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    19.570] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    19.570] (**) Option "Device" "/dev/input/event7"
[    19.580] (--) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5720
[    19.580] (--) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4780
[    19.580] (--) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    19.580] (--) SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    19.580] (--) SynPS/2 Synaptics TouchPad: buttons: left right double triple scroll-buttons
[    19.592] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    19.592] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    19.596] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio2/input/input7/event7"
[    19.596] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    19.596] (**) SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    19.596] (**) SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    19.596] (**) SynPS/2 Synaptics TouchPad: AccelFactor is now 0.037
[    19.596] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    19.596] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    19.596] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    19.596] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    19.600] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    19.601] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    19.601] (II) No input driver/identifier specified (ignoring)

____________________________________________

*** /etc/X11/xorg.conf
*** ls: -rw-r--r-- 1 root root 1346 2011-07-14 13:51:19.374491170 +0530 /etc/X11/xorg.conf
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 270.41.06  (buildmeister@swio-display-x86-rhel47-07.nvidia.com)  Mon Apr 18 15:15:12 PDT 2011


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


____________________________________________

*** /var/log/Xorg.0.log.old
*** ls: -rw-r--r-- 1 root root 23512 2011-07-14 13:51:38.046583759 +0530 /var/log/Xorg.0.log.old
[  1238.360] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[  1238.360] X Protocol Version 11, Revision 0
[  1238.360] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[  1238.360] Current Operating System: Linux sharan-Aspire-5738 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686
[  1238.360] Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.38-8-generic root=UUID=4829be89-f413-4aaa-bfc5-b14e8c8ebebf ro quiet splash vt.handoff=7
[  1238.360] Build Date: 21 May 2011  11:38:35AM
[  1238.360] xorg-server 2:1.10.1-1ubuntu1.1 (For technical support please see http://www.ubuntu.com/support) 
[  1238.360] Current version of pixman: 0.20.2
[  1238.360] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[  1238.360] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  1238.360] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Jul 14 13:12:40 2011
[  1238.360] (==) Using config file: "/etc/X11/xorg.conf"
[  1238.361] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  1238.361] (==) No Layout section.  Using the first Screen section.
[  1238.361] (==) No screen section available. Using defaults.
[  1238.361] (**) |-->Screen "Default Screen Section" (0)
[  1238.361] (**) |   |-->Monitor "<default monitor>"
[  1238.361] (==) No device specified for screen "Default Screen Section".
	Using the first device section listed.
[  1238.361] (**) |   |-->Device "Default Device"
[  1238.361] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[  1238.361] (==) Automatically adding devices
[  1238.361] (==) Automatically enabling devices
[  1238.361] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  1238.361] 	Entry deleted from font path.
[  1238.361] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[  1238.361] 	Entry deleted from font path.
[  1238.361] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[  1238.362] 	Entry deleted from font path.
[  1238.362] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[  1238.362] 	Entry deleted from font path.
[  1238.362] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[  1238.362] 	Entry deleted from font path.
[  1238.362] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[  1238.362] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  1238.362] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[  1238.362] (II) Loader magic: 0x81ffde0
[  1238.362] (II) Module ABI versions:
[  1238.362] 	X.Org ANSI C Emulation: 0.4
[  1238.362] 	X.Org Video Driver: 10.0
[  1238.362] 	X.Org XInput driver : 12.3
[  1238.362] 	X.Org Server Extension : 5.0
[  1238.363] (--) PCI:*(0:1:0:0) 10de:06ec:1025:0205 rev 161, Mem @ 0xf2000000/16777216, 0xd0000000/268435456, 0xf0000000/33554432, I/O @ 0x00002000/128
[  1238.363] (II) Open ACPI successful (/var/run/acpid.socket)
[  1238.363] (II) LoadModule: "extmod"
[  1238.364] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[  1238.364] (II) Module extmod: vendor="X.Org Foundation"
[  1238.364] 	compiled for 1.10.1, module version = 1.0.0
[  1238.364] 	Module class: X.Org Server Extension
[  1238.364] 	ABI class: X.Org Server Extension, version 5.0
[  1238.364] (II) Loading extension MIT-SCREEN-SAVER
[  1238.364] (II) Loading extension XFree86-VidModeExtension
[  1238.364] (II) Loading extension XFree86-DGA
[  1238.364] (II) Loading extension DPMS
[  1238.364] (II) Loading extension XVideo
[  1238.364] (II) Loading extension XVideo-MotionCompensation
[  1238.364] (II) Loading extension X-Resource
[  1238.364] (II) LoadModule: "dbe"
[  1238.365] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[  1238.365] (II) Module dbe: vendor="X.Org Foundation"
[  1238.365] 	compiled for 1.10.1, module version = 1.0.0
[  1238.365] 	Module class: X.Org Server Extension
[  1238.365] 	ABI class: X.Org Server Extension, version 5.0
[  1238.365] (II) Loading extension DOUBLE-BUFFER
[  1238.365] (II) LoadModule: "glx"
[  1238.365] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[  1238.396] (II) Module glx: vendor="NVIDIA Corporation"
[  1238.396] 	compiled for 4.0.2, module version = 1.0.0
[  1238.396] 	Module class: X.Org Server Extension
[  1238.396] (II) NVIDIA GLX Module  270.41.06  Mon Apr 18 15:11:28 PDT 2011
[  1238.396] (II) Loading extension GLX
[  1238.396] (II) LoadModule: "record"
[  1238.397] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[  1238.397] (II) Module record: vendor="X.Org Foundation"
[  1238.397] 	compiled for 1.10.1, module version = 1.13.0
[  1238.397] 	Module class: X.Org Server Extension
[  1238.397] 	ABI class: X.Org Server Extension, version 5.0
[  1238.397] (II) Loading extension RECORD
[  1238.397] (II) LoadModule: "dri"
[  1238.397] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[  1238.397] (II) Module dri: vendor="X.Org Foundation"
[  1238.397] 	compiled for 1.10.1, module version = 1.0.0
[  1238.398] 	ABI class: X.Org Server Extension, version 5.0
[  1238.398] (II) Loading extension XFree86-DRI
[  1238.398] (II) LoadModule: "dri2"
[  1238.398] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[  1238.398] (II) Module dri2: vendor="X.Org Foundation"
[  1238.398] 	compiled for 1.10.1, module version = 1.2.0
[  1238.398] 	ABI class: X.Org Server Extension, version 5.0
[  1238.398] (II) Loading extension DRI2
[  1238.398] (==) Matched nvidia as autoconfigured driver 0
[  1238.398] (==) Matched nouveau as autoconfigured driver 1
[  1238.398] (==) Matched nv as autoconfigured driver 2
[  1238.398] (==) Matched vesa as autoconfigured driver 3
[  1238.398] (==) Matched fbdev as autoconfigured driver 4
[  1238.398] (==) Assigned the driver to the xf86ConfigLayout
[  1238.398] (II) LoadModule: "nvidia"
[  1238.398] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[  1238.399] (II) Module nvidia: vendor="NVIDIA Corporation"
[  1238.399] 	compiled for 4.0.2, module version = 1.0.0
[  1238.399] 	Module class: X.Org Video Driver
[  1238.399] (II) LoadModule: "nouveau"
[  1238.399] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[  1238.399] (II) Module nouveau: vendor="X.Org Foundation"
[  1238.399] 	compiled for 1.10.0, module version = 0.0.16
[  1238.399] 	Module class: X.Org Video Driver
[  1238.399] 	ABI class: X.Org Video Driver, version 10.0
[  1238.399] (II) LoadModule: "nv"
[  1238.400] (WW) Warning, couldn't open module nv
[  1238.400] (II) UnloadModule: "nv"
[  1238.400] (II) Unloading nv
[  1238.400] (EE) Failed to load module "nv" (module does not exist, 0)
[  1238.400] (II) LoadModule: "vesa"
[  1238.400] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  1238.400] (II) Module vesa: vendor="X.Org Foundation"
[  1238.400] 	compiled for 1.10.0, module version = 2.3.0
[  1238.400] 	Module class: X.Org Video Driver
[  1238.400] 	ABI class: X.Org Video Driver, version 10.0
[  1238.401] (II) LoadModule: "fbdev"
[  1238.401] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  1238.401] (II) Module fbdev: vendor="X.Org Foundation"
[  1238.401] 	compiled for 1.10.0, module version = 0.4.2
[  1238.401] 	ABI class: X.Org Video Driver, version 10.0
[  1238.401] (II) NVIDIA dlloader X Driver  270.41.06  Mon Apr 18 14:55:51 PDT 2011
[  1238.401] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[  1238.401] (II) NOUVEAU driver Date:   Fri Jan 7 13:33:36 2011 +1000
[  1238.401] (II) NOUVEAU driver for NVIDIA chipset families :
[  1238.401] 	RIVA TNT    (NV04)
[  1238.401] 	RIVA TNT2   (NV05)
[  1238.401] 	GeForce 256 (NV10)
[  1238.401] 	GeForce 2   (NV11, NV15)
[  1238.401] 	GeForce 4MX (NV17, NV18)
[  1238.401] 	GeForce 3   (NV20)
[  1238.401] 	GeForce 4Ti (NV25, NV28)
[  1238.401] 	GeForce FX  (NV3x)
[  1238.401] 	GeForce 6   (NV4x)
[  1238.401] 	GeForce 7   (G7x)
[  1238.401] 	GeForce 8   (G8x)
[  1238.401] (II) VESA: driver for VESA chipsets: vesa
[  1238.401] (II) FBDEV: driver for framebuffer: fbdev
[  1238.401] (--) using VT number 8

[  1238.421] (II) Loading sub module "fb"
[  1238.421] (II) LoadModule: "fb"
[  1238.421] (II) Loading /usr/lib/xorg/modules/libfb.so
[  1238.421] (II) Module fb: vendor="X.Org Foundation"
[  1238.421] 	compiled for 1.10.1, module version = 1.0.0
[  1238.421] 	ABI class: X.Org ANSI C Emulation, version 0.4
[  1238.421] (II) Loading sub module "wfb"
[  1238.421] (II) LoadModule: "wfb"
[  1238.421] (II) Loading /usr/lib/xorg/modules/libwfb.so
[  1238.421] (II) Module wfb: vendor="X.Org Foundation"
[  1238.421] 	compiled for 1.10.1, module version = 1.0.0
[  1238.421] 	ABI class: X.Org ANSI C Emulation, version 0.4
[  1238.421] (II) Loading sub module "ramdac"
[  1238.421] (II) LoadModule: "ramdac"
[  1238.421] (II) Module "ramdac" already built-in
[  1238.421] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[  1238.421] (II) Loading /usr/lib/xorg/modules/libwfb.so
[  1238.422] (II) Loading /usr/lib/xorg/modules/libfb.so
[  1238.422] (WW) Falling back to old probe method for vesa
[  1238.422] (WW) Falling back to old probe method for fbdev
[  1238.422] (II) Loading sub module "fbdevhw"
[  1238.422] (II) LoadModule: "fbdevhw"
[  1238.422] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[  1238.422] (II) Module fbdevhw: vendor="X.Org Foundation"
[  1238.422] 	compiled for 1.10.1, module version = 0.0.2
[  1238.422] 	ABI class: X.Org Video Driver, version 10.0
[  1238.422] (II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[  1238.422] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[  1238.422] (==) NVIDIA(0): RGB weight 888
[  1238.422] (==) NVIDIA(0): Default visual is TrueColor
[  1238.422] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[  1238.422] (**) NVIDIA(0): Option "NoLogo" "True"
[  1239.015] (II) NVIDIA(GPU-0): Display (LGD LP156WH2-TLE1 (DFP-0)) does not support NVIDIA 3D
[  1239.015] (II) NVIDIA(GPU-0):     Vision stereo.
[  1239.016] (II) NVIDIA(0): NVIDIA GPU GeForce G 105M (G98) at PCI:1:0:0 (GPU-0)
[  1239.016] (--) NVIDIA(0): Memory: 524288 kBytes
[  1239.016] (--) NVIDIA(0): VideoBIOS: 62.98.5a.00.18
[  1239.017] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[  1239.017] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[  1239.017] (--) NVIDIA(0): Connected display device(s) on GeForce G 105M at PCI:1:0:0
[  1239.017] (--) NVIDIA(0):     LGD LP156WH2-TLE1 (DFP-0)
[  1239.017] (--) NVIDIA(0): LGD LP156WH2-TLE1 (DFP-0): 330.0 MHz maximum pixel clock
[  1239.017] (--) NVIDIA(0): LGD LP156WH2-TLE1 (DFP-0): Internal Dual Link LVDS
[  1239.070] (II) NVIDIA(0): Assigned Display Device: DFP-0
[  1239.070] (==) NVIDIA(0): 
[  1239.070] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[  1239.070] (==) NVIDIA(0):     will be used as the requested mode.
[  1239.070] (==) NVIDIA(0): 
[  1239.071] (II) NVIDIA(0): Validated modes:
[  1239.071] (II) NVIDIA(0):     "nvidia-auto-select"
[  1239.071] (II) NVIDIA(0): Virtual screen size determined to be 1366 x 768
[  1240.131] (--) NVIDIA(0): DPI set to (102, 102); computed from "UseEdidDpi" X config
[  1240.131] (--) NVIDIA(0):     option
[  1240.131] (II) UnloadModule: "nouveau"
[  1240.131] (II) Unloading nouveau
[  1240.131] (II) UnloadModule: "vesa"
[  1240.131] (II) Unloading vesa
[  1240.131] (II) UnloadModule: "fbdev"
[  1240.131] (II) Unloading fbdev
[  1240.131] (II) UnloadModule: "fbdevhw"
[  1240.131] (II) Unloading fbdevhw
[  1240.131] (--) Depth 24 pixmap format is 32 bpp
[  1240.131] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[  1240.139] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[  1240.417] (II) Loading extension NV-GLX
[  1240.459] (==) NVIDIA(0): Disabling shared memory pixmaps
[  1240.459] (==) NVIDIA(0): Backing store disabled
[  1240.459] (==) NVIDIA(0): Silken mouse enabled
[  1240.460] (==) NVIDIA(0): DPMS enabled
[  1240.460] (II) Loading extension NV-CONTROL
[  1240.460] (II) Loading extension XINERAMA
[  1240.461] (II) Loading sub module "dri2"
[  1240.461] (II) LoadModule: "dri2"
[  1240.461] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[  1240.461] (II) Module dri2: vendor="X.Org Foundation"
[  1240.461] 	compiled for 1.10.1, module version = 1.2.0
[  1240.461] 	ABI class: X.Org Server Extension, version 5.0
[  1240.461] (II) NVIDIA(0): [DRI2] Setup complete
[  1240.461] (==) RandR enabled
[  1240.461] (II) Initializing built-in extension Generic Event Extension
[  1240.461] (II) Initializing built-in extension SHAPE
[  1240.461] (II) Initializing built-in extension MIT-SHM
[  1240.461] (II) Initializing built-in extension XInputExtension
[  1240.461] (II) Initializing built-in extension XTEST
[  1240.461] (II) Initializing built-in extension BIG-REQUESTS
[  1240.461] (II) Initializing built-in extension SYNC
[  1240.461] (II) Initializing built-in extension XKEYBOARD
[  1240.461] (II) Initializing built-in extension XC-MISC
[  1240.461] (II) Initializing built-in extension SECURITY
[  1240.461] (II) Initializing built-in extension XINERAMA
[  1240.461] (II) Initializing built-in extension XFIXES
[  1240.461] (II) Initializing built-in extension RENDER
[  1240.461] (II) Initializing built-in extension RANDR
[  1240.461] (II) Initializing built-in extension COMPOSITE
[  1240.461] (II) Initializing built-in extension DAMAGE
[  1240.461] (II) Initializing built-in extension GESTURE
[  1240.465] (II) Initializing extension GLX
[  1240.491] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  1240.503] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[  1240.503] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  1240.503] (II) LoadModule: "evdev"
[  1240.503] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1240.503] (II) Module evdev: vendor="X.Org Foundation"
[  1240.503] 	compiled for 1.10.0.902, module version = 2.6.0
[  1240.503] 	Module class: X.Org XInput Driver
[  1240.503] 	ABI class: X.Org XInput driver, version 12.3
[  1240.503] (II) Using input driver 'evdev' for 'Power Button'
[  1240.503] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1240.503] (**) Power Button: always reports core events
[  1240.504] (**) Power Button: Device: "/dev/input/event2"
[  1240.504] (--) Power Button: Found keys
[  1240.504] (II) Power Button: Configuring as keyboard
[  1240.504] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[  1240.504] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[  1240.504] (**) Option "xkb_rules" "evdev"
[  1240.504] (**) Option "xkb_model" "pc105"
[  1240.504] (**) Option "xkb_layout" "us"
[  1240.505] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[  1240.505] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[  1240.505] (II) Using input driver 'evdev' for 'Video Bus'
[  1240.505] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1240.505] (**) Video Bus: always reports core events
[  1240.505] (**) Video Bus: Device: "/dev/input/event4"
[  1240.505] (--) Video Bus: Found keys
[  1240.505] (II) Video Bus: Configuring as keyboard
[  1240.505] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input4/event4"
[  1240.505] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[  1240.505] (**) Option "xkb_rules" "evdev"
[  1240.505] (**) Option "xkb_model" "pc105"
[  1240.505] (**) Option "xkb_layout" "us"
[  1240.510] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[  1240.510] (II) No input driver/identifier specified (ignoring)
[  1240.510] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[  1240.510] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[  1240.510] (II) Using input driver 'evdev' for 'Sleep Button'
[  1240.510] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1240.510] (**) Sleep Button: always reports core events
[  1240.510] (**) Sleep Button: Device: "/dev/input/event1"
[  1240.511] (--) Sleep Button: Found keys
[  1240.511] (II) Sleep Button: Configuring as keyboard
[  1240.511] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1/event1"
[  1240.511] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[  1240.511] (**) Option "xkb_rules" "evdev"
[  1240.511] (**) Option "xkb_model" "pc105"
[  1240.511] (**) Option "xkb_layout" "us"
[  1240.514] (II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event6)
[  1240.514] (II) No input driver/identifier specified (ignoring)
[  1240.517] (II) config/udev: Adding input device CNF7017 (/dev/input/event5)
[  1240.517] (**) CNF7017: Applying InputClass "evdev keyboard catchall"
[  1240.517] (II) Using input driver 'evdev' for 'CNF7017'
[  1240.517] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1240.517] (**) CNF7017: always reports core events
[  1240.517] (**) CNF7017: Device: "/dev/input/event5"
[  1240.517] (--) CNF7017: Found keys
[  1240.517] (II) CNF7017: Configuring as keyboard
[  1240.517] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/input/input5/event5"
[  1240.517] (II) XINPUT: Adding extended input device "CNF7017" (type: KEYBOARD)
[  1240.517] (**) Option "xkb_rules" "evdev"
[  1240.517] (**) Option "xkb_model" "pc105"
[  1240.517] (**) Option "xkb_layout" "us"
[  1240.524] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[  1240.524] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[  1240.524] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[  1240.524] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1240.524] (**) AT Translated Set 2 keyboard: always reports core events
[  1240.524] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[  1240.524] (--) AT Translated Set 2 keyboard: Found keys
[  1240.524] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[  1240.524] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[  1240.524] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[  1240.524] (**) Option "xkb_rules" "evdev"
[  1240.524] (**) Option "xkb_model" "pc105"
[  1240.524] (**) Option "xkb_layout" "us"
[  1240.525] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event7)
[  1240.525] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[  1240.525] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[  1240.525] (II) LoadModule: "synaptics"
[  1240.525] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[  1240.526] (II) Module synaptics: vendor="X.Org Foundation"
[  1240.526] 	compiled for 1.10.1, module version = 1.3.99
[  1240.526] 	Module class: X.Org XInput Driver
[  1240.526] 	ABI class: X.Org XInput driver, version 12.3
[  1240.526] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[  1240.526] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[  1240.526] (**) SynPS/2 Synaptics TouchPad: always reports core events
[  1240.526] (**) Option "Device" "/dev/input/event7"
[  1240.532] (--) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5720
[  1240.532] (--) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4780
[  1240.532] (--) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[  1240.532] (--) SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[  1240.532] (--) SynPS/2 Synaptics TouchPad: buttons: left right double triple scroll-buttons
[  1240.544] (--) SynPS/2 Synaptics TouchPad: touchpad found
[  1240.544] (**) SynPS/2 Synaptics TouchPad: always reports core events
[  1240.548] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio2/input/input7/event7"
[  1240.548] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[  1240.548] (**) SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[  1240.548] (**) SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[  1240.548] (**) SynPS/2 Synaptics TouchPad: AccelFactor is now 0.037
[  1240.548] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[  1240.548] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[  1240.548] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[  1240.548] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[  1240.557] (--) SynPS/2 Synaptics TouchPad: touchpad found
[  1240.557] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[  1240.557] (II) No input driver/identifier specified (ignoring)
[  3573.620] (II) Power Button: Close
[  3573.620] (II) UnloadModule: "evdev"
[  3573.620] (II) Unloading evdev
[  3573.656] (II) Video Bus: Close
[  3573.656] (II) UnloadModule: "evdev"
[  3573.656] (II) Unloading evdev
[  3573.680] (II) Sleep Button: Close
[  3573.680] (II) UnloadModule: "evdev"
[  3573.680] (II) Unloading evdev
[  3573.712] (II) CNF7017: Close
[  3573.712] (II) UnloadModule: "evdev"
[  3573.712] (II) Unloading evdev
[  3573.740] (II) AT Translated Set 2 keyboard: Close
[  3573.740] (II) UnloadModule: "evdev"
[  3573.740] (II) Unloading evdev
[  3573.836] (II) UnloadModule: "synaptics"
[  3573.836] (II) Unloading synaptics
[  3575.507] 
Fatal server error:
[  3575.507] xf86CloseConsole: VT_WAITACTIVE failed: Interrupted system call
[  3575.507] 
[  3575.507] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[  3575.507] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[  3575.507] 
[  3575.507] 
Backtrace:
[  3575.507] 0: /usr/bin/X (xorg_backtrace+0x3b) [0x80eab2b]
[  3575.507] 1: /usr/bin/X (0x8048000+0x5fad8) [0x80a7ad8]
[  3575.507] 2: (vdso) (__kernel_rt_sigreturn+0x0) [0xc5540c]
[  3575.507] 3: /usr/bin/X (CloseWellKnownConnections+0x34) [0x80a50f4]
[  3575.507] 4: /usr/bin/X (0x8048000+0x69e9f) [0x80b1e9f]
[  3575.507] 5: /usr/bin/X (0x8048000+0x69f12) [0x80b1f12]
[  3575.507] 6: /usr/bin/X (0x8048000+0x6a02e) [0x80b202e]
[  3575.507] 7: /usr/bin/X (0x8048000+0x12a326) [0x8172326]
[  3575.507] 8: /usr/bin/X (xf86CloseConsole+0x13f) [0x8172b3f]
[  3575.507] 9: /usr/bin/X (ddxSigGiveUp+0xa5) [0x80b6165]
[  3575.507] 10: /usr/bin/X (ddxGiveUp+0x1e) [0x80b618e]
[  3575.507] 11: /usr/bin/X (0x8048000+0x1aa68) [0x8062a68]
[  3575.507] 12: /lib/i386-linux-gnu/libc.so.6 (__libc_start_main+0xe7) [0x14ce37]
[  3575.507] 13: /usr/bin/X (0x8048000+0x1a411) [0x8062411]
[  3575.507] Segmentation fault at address 0x44
[  3575.507] 
Caught signal 11 (Segmentation fault). Server aborting
[  3575.507] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[  3575.507] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[  3575.507] 

____________________________________________

ldd /usr/bin/glxinfo

	linux-gate.so.1 =>  (0x001b4000)
	libGL.so.1 => /usr/lib/nvidia-current/libGL.so.1 (0x005fa000)
	libX11.so.6 => /usr/lib/i386-linux-gnu/libX11.so.6 (0x00a70000)
	libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0x00d38000)
	libnvidia-tls.so.270.41.06 => /usr/lib/nvidia-current/tls/libnvidia-tls.so.270.41.06 (0x00d33000)
	libnvidia-glcore.so.270.41.06 => /usr/lib/nvidia-current/libnvidia-glcore.so.270.41.06 (0x00e99000)
	libXext.so.6 => /usr/lib/i386-linux-gnu/libXext.so.6 (0x00bb1000)
	libdl.so.2 => /lib/i386-linux-gnu/libdl.so.2 (0x00208000)
	libxcb.so.1 => /usr/lib/i386-linux-gnu/libxcb.so.1 (0x0094b000)
	/lib/ld-linux.so.2 (0x00964000)
	libm.so.6 => /lib/i386-linux-gnu/libm.so.6 (0x007b4000)
	libXau.so.6 => /usr/lib/i386-linux-gnu/libXau.so.6 (0x00110000)
	libXdmcp.so.6 => /usr/lib/i386-linux-gnu/libXdmcp.so.6 (0x00854000)

____________________________________________

/usr/bin/lspci -d "10de:*" -v -xxx

01:00.0 VGA compatible controller: nVidia Corporation G98M [GeForce G 105M] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: Acer Incorporated [ALI] Device 0205
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f2000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at f0000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at 2000 [size=128]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: [60] Power Management version 3
	Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
	Capabilities: [78] Express Endpoint, MSI 00
	Capabilities: [100] Virtual Channel
	Capabilities: [128] Power Budgeting <?>
	Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
	Kernel driver in use: nvidia
	Kernel modules: nvidia-current, nouveau, nvidiafb
00: de 10 ec 06 07 00 10 00 a1 00 00 03 00 00 00 00
10: 00 00 00 f2 0c 00 00 d0 00 00 00 00 04 00 00 f0
20: 00 00 00 00 01 20 00 00 00 00 00 00 25 10 05 02
30: 00 00 00 00 60 00 00 00 00 00 00 00 0b 01 00 00
40: 25 10 05 02 00 00 00 00 00 00 00 00 00 00 00 00
50: 01 00 00 00 01 00 00 00 ce d6 23 00 00 00 00 00
60: 01 68 03 00 08 00 00 00 05 78 80 00 00 00 00 00
70: 00 00 00 00 00 00 00 00 10 00 02 00 a0 84 2c 01
80: 10 29 00 00 02 2d 00 00 4a 00 11 10 00 00 00 00
90: 00 00 00 00 00 00 00 00 00 00 00 00 10 00 00 00
a0: 00 00 00 00 00 00 00 00 02 00 00 00 00 00 00 00
b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00


____________________________________________

/usr/bin/lspci -t

-[0000:00]-+-00.0
           +-01.0-[01]----00.0
           +-1a.0
           +-1a.1
           +-1a.7
           +-1b.0
           +-1c.0-[02]----00.0
           +-1c.1-[03]--
           +-1c.2-[04]----00.0
           +-1c.4-[05-07]--
           +-1d.0
           +-1d.1
           +-1d.2
           +-1d.3
           +-1d.7
           +-1e.0-[0d]--
           +-1f.0
           +-1f.2
           \-1f.3

____________________________________________

/usr/bin/lspci -nn

00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port [8086:2a41] (rev 07)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
01:00.0 VGA compatible controller [0300]: nVidia Corporation G98M [GeForce G 105M] [10de:06ec] (rev a1)
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe [14e4:1698] (rev 10)
04:00.0 Network controller [0280]: Intel Corporation WiFi Link 5100 [8086:4232]
____________________________________________

/usr/sbin/lsusb

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f2:b044 Chicony Electronics Co., Ltd Acer CrystalEye Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

____________________________________________

/usr/sbin/dmidecode

# dmidecode 2.9
SMBIOS 2.5 present.
45 structures occupying 1900 bytes.
Table at 0xBFCC0000.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
	Vendor: Phoenix Technologies LTD
	Version: V1.34          
	Release Date: 09/24/2010
	Address: 0xE5330
	Runtime Size: 109776 bytes
	ROM Size: 2048 kB
	Characteristics:
		ISA is supported
		PCI is supported
		PC Card (PCMCIA) is supported
		PNP is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		ESCD support is available
		Boot from CD is supported
		ACPI is supported
		USB legacy is supported
		AGP is supported
		BIOS boot specification is supported
		Targeted content distribution is supported

Handle 0x0001, DMI type 1, 27 bytes
System Information
	Manufacturer: Acer           
	Product Name: Aspire 5738                    
	Version: 0100           
	Serial Number: LXPAN0X0259290C9282000        
	UUID: 6CABB7E0-73F6-11DE-AD6B-FDFA8869A7AF
	Wake-up Type: Power Switch
	SKU Number: Not Specified
	Family: Not Specified

Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
	Manufacturer: Acer           
	Product Name: JV50_MV                        
	Version: Rev            
	Serial Number: LXPAN0X0259290C9282000        
	Asset Tag: Not Specified
	Features: None
	Location In Chassis: Not Specified
	Chassis Handle: 0xFFFF
	Type: Unknown
	Contained Object Handles: 0

Handle 0x0003, DMI type 3, 21 bytes
Chassis Information
	Manufacturer: Acer           
	Type: Notebook
	Lock: Not Present
	Version: N/A            
	Serial Number: None           
	Asset Tag:                                 
	Boot-up State: Safe
	Power Supply State: Safe
	Thermal State: Safe
	Security Status: None
	OEM Information: 0x00001234
	Height: Unspecified
	Number Of Power Cords: Unspecified
	Contained Elements: 0

Handle 0x0004, DMI type 4, 40 bytes
Processor Information
	Socket Designation: U2E1
	Type: Central Processor
	Family: <OUT OF SPEC>
	Manufacturer: Intel
	ID: 7A 06 01 00 FF FB EB BF
	Version: CPU Version
	Voltage: 3.3 V
	External Clock: 200 MHz
	Max Speed: 2100 MHz
	Current Speed: 2100 MHz
	Status: Populated, Enabled
	Upgrade: ZIF Socket
	L1 Cache Handle: 0x0005
	L2 Cache Handle: 0x0006
	L3 Cache Handle: Not Provided
	Serial Number: Not Specified
	Asset Tag: Not Specified
	Part Number: Not Specified
	Core Count: 2
	Core Enabled: 2
	Thread Count: 2
	Characteristics:
		64-bit capable

Handle 0x0005, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L1 Cache
	Configuration: Enabled, Socketed, Level 1
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 64 KB
	Maximum Size: 64 KB
	Supported SRAM Types:
		Burst
		Pipeline Burst
		Asynchronous
	Installed SRAM Type: Asynchronous
	Speed: Unknown
	Error Correction Type: Single-bit ECC
	System Type: Data
	Associativity: 8-way Set-associative

Handle 0x0006, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L2 Cache
	Configuration: Enabled, Socketed, Level 2
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 2048 KB
	Maximum Size: 4096 KB
	Supported SRAM Types:
		Burst
		Pipeline Burst
		Asynchronous
	Installed SRAM Type: Burst
	Speed: Unknown
	Error Correction Type: Single-bit ECC
	System Type: Unified
	Associativity: 8-way Set-associative

Handle 0x0007, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J19
	Internal Connector Type: 9 Pin Dual Inline (pin 10 cut)
	External Reference Designator: COM 1
	External Connector Type: DB-9 male
	Port Type: Serial Port 16550A Compatible

Handle 0x0008, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J1A1
	Internal Connector Type: None
	External Reference Designator: Keyboard
	External Connector Type: Circular DIN-8 male
	Port Type: Keyboard Port

Handle 0x0009, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J1A1
	Internal Connector Type: None
	External Reference Designator: PS/2 Mouse
	External Connector Type: Circular DIN-8 male
	Port Type: Mouse Port

Handle 0x000A, DMI type 9, 13 bytes
System Slot Information
	Designation: PEG Slot J6B2
	Type: 32-bit PCI Express
	Current Usage: In Use
	Length: Long
	ID: 6
	Characteristics:
		5.0 V is provided
		3.3 V is provided

Handle 0x000B, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI Express Slot J6B1
	Type: 32-bit PCI Express
	Current Usage: In Use
	Length: Long
	ID: 7
	Characteristics:
		5.0 V is provided
		3.3 V is provided

Handle 0x000C, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI Express Slot J6D1
	Type: 32-bit PCI Express
	Current Usage: Available
	Length: Long
	ID: 8
	Characteristics:
		5.0 V is provided
		3.3 V is provided

Handle 0x000D, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI Express Slot J8B3
	Type: 32-bit PCI Express
	Current Usage: In Use
	Length: Long
	ID: 9
	Characteristics:
		5.0 V is provided
		3.3 V is provided

Handle 0x000E, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI Express Slot J8D1
	Type: 32-bit PCI Express
	Current Usage: Available
	Length: Long
	ID: 10
	Characteristics:
		5.0 V is provided
		3.3 V is provided

Handle 0x000F, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI Express Slot J7B1
	Type: 32-bit PCI Express
	Current Usage: Available
	Length: Long
	ID: 10
	Characteristics:
		5.0 V is provided
		3.3 V is provided

Handle 0x0010, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI Express Slot 6
	Type: 32-bit PCI Express
	Current Usage: Available
	Length: Long
	ID: 10
	Characteristics:
		5.0 V is provided
		3.3 V is provided

Handle 0x0011, DMI type 10, 6 bytes
On Board Device Information
	Type: Sound
	Status: Disabled
	Description: HD-Audio

Handle 0x0012, DMI type 11, 5 bytes
OEM Strings
	String 1: This is the Intel Cantiga
	String 2: Chipset CRB Platform

Handle 0x0013, DMI type 12, 5 bytes
System Configuration Options
	Option 1: Jumper settings can be described here.

Handle 0x0014, DMI type 15, 29 bytes
System Event Log
	Area Length: 16 bytes
	Header Start Offset: 0x0000
	Header Length: 16 bytes
	Data Start Offset: 0x0010
	Access Method: General-purpose non-volatile data functions
	Access Address: 0x0000
	Status: Invalid, Not Full
	Change Token: 0x00000000
	Header Format: Type 1
	Supported Log Type Descriptors: 3
	Descriptor 1: POST error
	Data Format 1: POST results bitmap
	Descriptor 2: Single-bit ECC memory error
	Data Format 2: Multiple-event
	Descriptor 3: Multi-bit ECC memory error
	Data Format 3: Multiple-event

Handle 0x0015, DMI type 16, 15 bytes
Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: None
	Maximum Capacity: 4 GB
	Error Information Handle: Not Provided
	Number Of Devices: 2

Handle 0x0016, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0015
	Error Information Handle: No Error
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 2048 MB
	Form Factor: SODIMM
	Set: 1
	Locator: M1
	Bank Locator: Bank 0
	Type: <OUT OF SPEC>
	Type Detail: Synchronous
	Speed: 800 MHz (1.2 ns)
	Manufacturer: 80CE            
	Serial Number: 94844E2D        
	Asset Tag: 0928
	Part Number: M471B5673EH1-CF8  

Handle 0x0017, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0015
	Error Information Handle: No Error
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 2048 MB
	Form Factor: SODIMM
	Set: 1
	Locator: M2
	Bank Locator: Bank 1
	Type: <OUT OF SPEC>
	Type Detail: Synchronous
	Speed: 800 MHz (1.2 ns)
	Manufacturer: 80CE            
	Serial Number: 94844E29        
	Asset Tag: 0928
	Part Number: M471B5673EH1-CF8  

Handle 0x0018, DMI type 18, 23 bytes
32-bit Memory Error Information
	Type: OK
	Granularity: Unknown
	Operation: Unknown
	Vendor Syndrome: Unknown
	Memory Array Address: Unknown
	Device Address: Unknown
	Resolution: Unknown

Handle 0x0019, DMI type 18, 23 bytes
32-bit Memory Error Information
	Type: OK
	Granularity: Unknown
	Operation: Unknown
	Vendor Syndrome: Unknown
	Memory Array Address: Unknown
	Device Address: Unknown
	Resolution: Unknown

Handle 0x001A, DMI type 19, 15 bytes
Memory Array Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x000FFFFFFFF
	Range Size: 4 GB
	Physical Array Handle: 0x0015
	Partition Width: 0

Handle 0x001B, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x0007FFFFFFF
	Range Size: 2 GB
	Physical Device Handle: 0x0016
	Memory Array Mapped Address Handle: 0x001A
	Partition Row Position: Unknown
	Interleave Position: Unknown
	Interleaved Data Depth: Unknown

Handle 0x001C, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00080000000
	Ending Address: 0x000FFFFFFFF
	Range Size: 2 GB
	Physical Device Handle: 0x0017
	Memory Array Mapped Address Handle: 0x001A
	Partition Row Position: Unknown
	Interleave Position: Unknown
	Interleaved Data Depth: Unknown

Handle 0x001D, DMI type 22, 26 bytes
Portable Battery
	Location: Rear
	Manufacturer: Intel Corporation
	Name: Intel Corporation
	Chemistry: Lithium Ion
	Design Capacity: 1000 mWh
	Design Voltage: 19 mV
	SBDS Version: BATT_1234
	Maximum Error: 100%
	SBDS Serial Number: 0001
	SBDS Manufacture Date: 1980-00-01
	OEM-specific Information: 0x00000000

Handle 0x001E, DMI type 23, 13 bytes
System Reset
	Status: Enabled
	Watchdog Timer: Present
	Boot Option: Do Not Reboot
	Boot Option On Limit: Do Not Reboot
	Reset Count: Unknown
	Reset Limit: Unknown
	Timer Interval: Unknown
	Timeout: Unknown

Handle 0x001F, DMI type 24, 5 bytes
Hardware Security
	Power-On Password Status: Disabled
	Keyboard Password Status: Unknown
	Administrator Password Status: Disabled
	Front Panel Reset Status: Unknown

Handle 0x0020, DMI type 25, 9 bytes
	System Power Controls
	Next Scheduled Power-on: 12-31 23:59:59

Handle 0x0021, DMI type 26, 20 bytes
Voltage Probe
	Description: Voltage Probe
	Location: Processor
	Status: OK
	Maximum Value: Unknown
	Minimum Value: Unknown
	Resolution: Unknown
	Tolerance: Unknown
	Accuracy: Unknown
	OEM-specific Information: 0x00000000

Handle 0x0022, DMI type 27, 12 bytes
Cooling Device
	Temperature Probe Handle: 0x0023
	Type: Fan
	Status: OK
	OEM-specific Information: 0x00000000

Handle 0x0023, DMI type 28, 20 bytes
Temperature Probe
	Description: Temperature Probe
	Location: Processor
	Status: OK
	Maximum Value: Unknown
	Minimum Value Unknown
	Resolution: Unknown
	Tolerance: Unknown
	Accuracy: Unknown
	OEM-specific Information: 0x00000000

Handle 0x0024, DMI type 29, 20 bytes
Electrical Current Probe
	Description: Electrical Current Probe
	Location: Processor
	Status: OK
	Maximum Value: Unknown
	Minimum Value: Unknown
	Resolution: Unknown
	Tolerance: Unknown
	Accuracy: Unknown
	OEM-specific Information: 0x00000000

Handle 0x0025, DMI type 30, 6 bytes
Out-of-band Remote Access
	Manufacturer Name: Intel
	Inbound Connection: Disabled
	Outbound Connection: Enabled

Handle 0x0026, DMI type 32, 20 bytes
System Boot Information
	Status: No errors detected

Handle 0x0027, DMI type 39, 22 bytes
System Power Supply
	Power Unit Group: 1
	Location: To Be Defined By O.E.M
	Name: To Be Defined By O.E.M
	Manufacturer: To Be Defined By O.E.M
	Serial Number: To Be Defined By O.E.M
	Asset Tag: To Be Defined By O.E.M
	Model Part Number: To Be Defined By O.E.M
	Revision: 2.50
	Max Power Capacity: Unknown
	Status: Present, Unknown
	Type: Unknown
	Input Voltage Range Switching: Unknown
	Plugged: Yes
	Hot Replaceable: No
	Input Voltage Probe Handle: 0x0021
	Cooling Device Handle: 0x0022
	Input Current Probe Handle: 0x0024

Handle 0x0028, DMI type 129, 8 bytes
OEM-specific Type
	Header and Data:
		81 08 28 00 01 01 02 01
	Strings:
		Intel_ASF
		Intel_ASF_001

Handle 0x0029, DMI type 136, 6 bytes
OEM-specific Type
	Header and Data:
		88 06 29 00 FF FF

Handle 0x002A, DMI type 150, 14 bytes
OEM-specific Type
	Header and Data:
		96 0E 2A 00 01 01 00 00 00 00 00 00 00 00
	Strings:
		ABSOLUTE(PHOENIX) CLM

Handle 0x002B, DMI type 200, 7 bytes
OEM-specific Type
	Header and Data:
		C8 07 2B 00 01 02 03
	Strings:
		17C0
		             
		0001

Handle 0x002C, DMI type 127, 4 bytes
End Of Table


____________________________________________

/sbin/modinfo nvidia | grep vermagic


____________________________________________

Scanning kernel log files for NVRM messages:

/var/log/messages is not readable
/var/log/kernel.log is not readable

____________________________________________

dmesg:

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.38-8-generic (buildd@vernadsky) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 (Ubuntu 2.6.38-8.42-generic 2.6.38.2)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d400 (usable)
[    0.000000]  BIOS-e820: 000000000009d400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d0000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf8a1000 (usable)
[    0.000000]  BIOS-e820: 00000000bf8a1000 - 00000000bf8a7000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf8a7000 - 00000000bf9cf000 (usable)
[    0.000000]  BIOS-e820: 00000000bf9cf000 - 00000000bfa0f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfa0f000 - 00000000bfb09000 (usable)
[    0.000000]  BIOS-e820: 00000000bfb09000 - 00000000bfd0f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfd0f000 - 00000000bfd19000 (usable)
[    0.000000]  BIOS-e820: 00000000bfd19000 - 00000000bfd1f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfd1f000 - 00000000bfd5f000 (usable)
[    0.000000]  BIOS-e820: 00000000bfd5f000 - 00000000bfd9f000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfd9f000 - 00000000bfde2000 (usable)
[    0.000000]  BIOS-e820: 00000000bfde2000 - 00000000bfdff000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bfdff000 - 00000000bfe00000 (usable)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI present.
[    0.000000] DMI: Acer            Aspire 5738                    /JV50_MV                        , BIOS V1.34           09/24/2010
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0xbfe00 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-D3FFF write-protect
[    0.000000]   D4000-DBFFF uncachable
[    0.000000]   DC000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 base 100000000 mask FC0000000 write-back
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000c0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] found SMP MP-table at [c00f6c90] f6c90
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 3676a000 - 373ad000
[    0.000000] ACPI: RSDP 000f6b10 00024 (v02 PTLTD )
[    0.000000] ACPI: XSDT bfdf4305 0005C (v01 ACRSYS ACRPRDCT 06040000 INNA 00000000)
[    0.000000] ACPI: FACP bfde4000 000F4 (v03 INTEL  CRESTLNE 06040000 ALAN 00000001)
[    0.000000] ACPI: DSDT bfde5000 0A885 (v02 Intel  CANTIGA  06040000 MSFT 03000000)
[    0.000000] ACPI: FACS bfd9dfc0 00040
[    0.000000] ACPI: HPET bfdfed86 00038 (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: MCFG bfdfedbe 0003C (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: SLIC bfdfedfa 00176 (v01 ACRSYS ACRPRDCT 06040000 ANNI 00000001)
[    0.000000] ACPI: APIC bfdfef70 00068 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT bfdfefd8 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SSDT bfde3000 00655 (v01  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2182MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x000bfe00
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[8] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x000bf8a1
[    0.000000]     0: 0x000bf8a7 -> 0x000bf9cf
[    0.000000]     0: 0x000bfa0f -> 0x000bfb09
[    0.000000]     0: 0x000bfd0f -> 0x000bfd19
[    0.000000]     0: 0x000bfd1f -> 0x000bfd5f
[    0.000000]     0: 0x000bfd9f -> 0x000bfde2
[    0.000000]     0: 0x000bfdff -> 0x000bfe00
[    0.000000] On node 0 totalpages: 785118
[    0.000000] free_area_init_node: node 0, pgdat c1784100, node_mem_map f4f6a200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3949 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4365 pages used for memmap
[    0.000000]   HighMem zone: 553542 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d0000
[    0.000000] PM: Registered nosave memory: 00000000000d0000 - 00000000000d4000
[    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at bfe00000 (gap: bfe00000:40200000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f4800000 s28800 r0 d24448 u2097152
[    0.000000] pcpu-alloc: s28800 r0 d24448 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 778977
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.38-8-generic root=UUID=4829be89-f413-4aaa-bfc5-b14e8c8ebebf ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] allocated 15718080 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:000bfe00)
[    0.000000] Memory: 3077648k/3143680k available (5188k kernel code, 62824k reserved, 2540k data, 700k init, 2231628k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc178d000 - 0xc183c000   ( 700 kB)
[    0.000000]       .data : 0xc15112a1 - 0xc178c480   (2540 kB)
[    0.000000]       .text : 0xc1000000 - 0xc15112a1   (5188 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f3408000 soft=f340a000
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2094.546 MHz processor.
[    0.004003] Calibrating delay loop (skipped), value calculated using timer frequency.. 4189.09 BogoMIPS (lpj=8378184)
[    0.004008] pid_max: default: 32768 minimum: 301
[    0.004031] Security Framework initialized
[    0.004046] AppArmor: AppArmor initialized
[    0.004048] Yama: becoming mindful.
[    0.004104] Mount-cache hash table entries: 512
[    0.004235] Initializing cgroup subsys ns
[    0.004239] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
[    0.004242] Initializing cgroup subsys cpuacct
[    0.004247] Initializing cgroup subsys memory
[    0.004254] Initializing cgroup subsys devices
[    0.004257] Initializing cgroup subsys freezer
[    0.004259] Initializing cgroup subsys net_cls
[    0.004261] Initializing cgroup subsys blkio
[    0.004297] CPU: Physical Processor ID: 0
[    0.004299] CPU: Processor Core ID: 0
[    0.004302] mce: CPU supports 6 MCE banks
[    0.004309] CPU0: Thermal monitoring enabled (TM1)
[    0.004313] using mwait in idle threads.
[    0.010099] ACPI: Core revision 20110112
[    0.016013] ftrace: allocating 23640 entries in 47 pages
[    0.020051] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.020369] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.063776] CPU0: Intel(R) Core(TM)2 Duo CPU     T6500  @ 2.10GHz stepping 0a
[    0.064003] APIC calibration not consistent with PM-Timer: 283ms instead of 100ms
[    0.064003] APIC delta adjusted to PM-Timer: 1246873 (3541077)
[    0.064003] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.064003] ... version:                2
[    0.064003] ... bit width:              40
[    0.064003] ... generic registers:      2
[    0.064003] ... value mask:             000000ffffffffff
[    0.064003] ... max period:             000000007fffffff
[    0.064003] ... fixed-purpose events:   3
[    0.064003] ... event mask:             0000000700000003
[    0.064003] CPU 1 irqstacks, hard=f34ca000 soft=f34cc000
[    0.064003] Booting Node   0, Processors  #1 Ok.
[    0.008000] Initializing CPU#1
[    0.152024] Brought up 2 CPUs
[    0.152027] Total of 2 processors activated (8378.55 BogoMIPS).
[    0.152586] devtmpfs: initialized
[    0.153224] print_constraints: dummy: 
[    0.153250] Time:  8:22:00  Date: 07/14/11
[    0.153288] NET: Registered protocol family 16
[    0.153314] Trying to unpack rootfs image as initramfs...
[    0.153408] EISA bus registered
[    0.153416] ACPI: bus type pci registered
[    0.153488] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.153492] PCI: not using MMCONFIG
[    0.156299] PCI: PCI BIOS revision 3.00 entry at 0xfdb11, last bus=13
[    0.156301] PCI: Using configuration type 1 for base access
[    0.168155] bio: create slab <bio-0> at 0
[    0.170112] ACPI: EC: Look up EC in DSDT
[    0.174691] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.175462] ACPI: SSDT bfd1aca0 00223 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.175912] ACPI: Dynamic OEM Table Load:
[    0.175915] ACPI: SSDT   (null) 00223 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.176092] ACPI: SSDT bfd19620 00549 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.176521] ACPI: Dynamic OEM Table Load:
[    0.176524] ACPI: SSDT   (null) 00549 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.240372] ACPI: SSDT bfd1aa20 001CF (v01  PmRef    ApIst 00003000 INTL 20050624)
[    0.240848] ACPI: Dynamic OEM Table Load:
[    0.240852] ACPI: SSDT   (null) 001CF (v01  PmRef    ApIst 00003000 INTL 20050624)
[    0.268167] ACPI: SSDT bfd1af20 0008D (v01  PmRef    ApCst 00003000 INTL 20050624)
[    0.268617] ACPI: Dynamic OEM Table Load:
[    0.268621] ACPI: SSDT   (null) 0008D (v01  PmRef    ApCst 00003000 INTL 20050624)
[    0.321138] ACPI: Interpreter enabled
[    0.321138] ACPI: (supports S0 S3 S4 S5)
[    0.321138] ACPI: Using IOAPIC for interrupt routing
[    0.321138] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.321145] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.321148] PCI: Using MMCONFIG for extended config space
[    0.332523] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.388223] ACPI: No dock devices found.
[    0.388228] HEST: Table not found.
[    0.388233] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.388626] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.389366] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.389370] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.389372] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.389376] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    0.389378] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    0.389381] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff]
[    0.389383] pci_root PNP0A08:00: host bridge window [mem 0x000e0000-0x000e3fff]
[    0.389387] pci_root PNP0A08:00: host bridge window [mem 0xc0000000-0xdfffffff]
[    0.389389] pci_root PNP0A08:00: host bridge window [mem 0xf0000000-0xfebfffff]
[    0.389411] pci 0000:00:00.0: [8086:2a40] type 0 class 0x000600
[    0.389438] DMAR: Forcing write-buffer flush capability
[    0.389440] DMAR: Disabling IOMMU for graphics on this chipset
[    0.389465] pci 0000:00:01.0: [8086:2a41] type 1 class 0x000604
[    0.389505] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.389508] pci 0000:00:01.0: PME# disabled
[    0.389557] pci 0000:00:1a.0: [8086:2937] type 0 class 0x000c03
[    0.389612] pci 0000:00:1a.0: reg 20: [io  0x1800-0x181f]
[    0.389666] pci 0000:00:1a.1: [8086:2938] type 0 class 0x000c03
[    0.389717] pci 0000:00:1a.1: reg 20: [io  0x1820-0x183f]
[    0.389780] pci 0000:00:1a.7: [8086:293c] type 0 class 0x000c03
[    0.389805] pci 0000:00:1a.7: reg 10: [mem 0xf3404800-0xf3404bff]
[    0.389888] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.389893] pci 0000:00:1a.7: PME# disabled
[    0.389920] pci 0000:00:1b.0: [8086:293e] type 0 class 0x000403
[    0.389938] pci 0000:00:1b.0: reg 10: [mem 0xf3400000-0xf3403fff 64bit]
[    0.390002] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.390007] pci 0000:00:1b.0: PME# disabled
[    0.390030] pci 0000:00:1c.0: [8086:2940] type 1 class 0x000604
[    0.390096] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.390100] pci 0000:00:1c.0: PME# disabled
[    0.390125] pci 0000:00:1c.1: [8086:2942] type 1 class 0x000604
[    0.390191] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.390195] pci 0000:00:1c.1: PME# disabled
[    0.390219] pci 0000:00:1c.2: [8086:2944] type 1 class 0x000604
[    0.390284] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.390288] pci 0000:00:1c.2: PME# disabled
[    0.390314] pci 0000:00:1c.4: [8086:2948] type 1 class 0x000604
[    0.390379] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.390383] pci 0000:00:1c.4: PME# disabled
[    0.390412] pci 0000:00:1d.0: [8086:2934] type 0 class 0x000c03
[    0.390463] pci 0000:00:1d.0: reg 20: [io  0x1840-0x185f]
[    0.390517] pci 0000:00:1d.1: [8086:2935] type 0 class 0x000c03
[    0.390567] pci 0000:00:1d.1: reg 20: [io  0x1860-0x187f]
[    0.390620] pci 0000:00:1d.2: [8086:2936] type 0 class 0x000c03
[    0.390675] pci 0000:00:1d.2: reg 20: [io  0x1880-0x189f]
[    0.390731] pci 0000:00:1d.3: [8086:2939] type 0 class 0x000c03
[    0.390788] pci 0000:00:1d.3: reg 20: [io  0x18a0-0x18bf]
[    0.390852] pci 0000:00:1d.7: [8086:293a] type 0 class 0x000c03
[    0.390876] pci 0000:00:1d.7: reg 10: [mem 0xf3404c00-0xf3404fff]
[    0.390960] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.390965] pci 0000:00:1d.7: PME# disabled
[    0.390987] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    0.391053] pci 0000:00:1f.0: [8086:2919] type 0 class 0x000601
[    0.391178] pci 0000:00:1f.2: [8086:2929] type 0 class 0x000106
[    0.391201] pci 0000:00:1f.2: reg 10: [io  0x18f0-0x18f7]
[    0.391210] pci 0000:00:1f.2: reg 14: [io  0x18e4-0x18e7]
[    0.391220] pci 0000:00:1f.2: reg 18: [io  0x18e8-0x18ef]
[    0.391230] pci 0000:00:1f.2: reg 1c: [io  0x18e0-0x18e3]
[    0.391239] pci 0000:00:1f.2: reg 20: [io  0x18c0-0x18df]
[    0.391249] pci 0000:00:1f.2: reg 24: [mem 0xf3404000-0xf34047ff]
[    0.391288] pci 0000:00:1f.2: PME# supported from D3hot
[    0.391292] pci 0000:00:1f.2: PME# disabled
[    0.391311] pci 0000:00:1f.3: [8086:2930] type 0 class 0x000c05
[    0.391329] pci 0000:00:1f.3: reg 10: [mem 0x00000000-0x000000ff 64bit]
[    0.391355] pci 0000:00:1f.3: reg 20: [io  0x1c00-0x1c1f]
[    0.391432] pci 0000:01:00.0: [10de:06ec] type 0 class 0x000300
[    0.391449] pci 0000:01:00.0: reg 10: [mem 0xf2000000-0xf2ffffff]
[    0.391466] pci 0000:01:00.0: reg 14: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.391483] pci 0000:01:00.0: reg 1c: [mem 0xf0000000-0xf1ffffff 64bit]
[    0.391495] pci 0000:01:00.0: reg 24: [io  0x2000-0x207f]
[    0.391507] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.396043] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.396047] pci 0000:00:01.0:   bridge window [io  0x2000-0x2fff]
[    0.396051] pci 0000:00:01.0:   bridge window [mem 0xf0000000-0xf2ffffff]
[    0.396056] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.396282] pci 0000:02:00.0: [14e4:1698] type 0 class 0x000200
[    0.396308] pci 0000:02:00.0: reg 10: [mem 0xf3000000-0xf300ffff 64bit]
[    0.396422] pci 0000:02:00.0: PME# supported from D3hot D3cold
[    0.396427] pci 0000:02:00.0: PME# disabled
[    0.404194] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.404199] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.404204] pci 0000:00:1c.0:   bridge window [mem 0xf3000000-0xf30fffff]
[    0.404211] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.404260] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.404265] pci 0000:00:1c.1:   bridge window [io  0xf000-0x0000] (disabled)
[    0.404270] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.404277] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.404383] pci 0000:04:00.0: [8086:4232] type 0 class 0x000280
[    0.404438] pci 0000:04:00.0: reg 10: [mem 0xf3100000-0xf3101fff 64bit]
[    0.404600] pci 0000:04:00.0: PME# supported from D0 D3hot D3cold
[    0.404611] pci 0000:04:00.0: PME# disabled
[    0.412067] pci 0000:00:1c.2: PCI bridge to [bus 04-04]
[    0.412072] pci 0000:00:1c.2:   bridge window [io  0xf000-0x0000] (disabled)
[    0.412077] pci 0000:00:1c.2:   bridge window [mem 0xf3100000-0xf31fffff]
[    0.412084] pci 0000:00:1c.2:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.412133] pci 0000:00:1c.4: PCI bridge to [bus 05-07]
[    0.412138] pci 0000:00:1c.4:   bridge window [io  0x3000-0x3fff]
[    0.412143] pci 0000:00:1c.4:   bridge window [mem 0xf4000000-0xf5ffffff]
[    0.412150] pci 0000:00:1c.4:   bridge window [mem 0xf6000000-0xf7ffffff 64bit pref]
[    0.412223] pci 0000:00:1e.0: PCI bridge to [bus 0d-0d] (subtractive decode)
[    0.412227] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.412232] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.412239] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.412242] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.412245] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.412248] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.412251] pci 0000:00:1e.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.412254] pci 0000:00:1e.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.412256] pci 0000:00:1e.0:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    0.412259] pci 0000:00:1e.0:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
[    0.412262] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xdfffffff] (subtractive decode)
[    0.412265] pci 0000:00:1e.0:   bridge window [mem 0xf0000000-0xfebfffff] (subtractive decode)
[    0.412295] pci_bus 0000:00: on NUMA node 0
[    0.412302] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.412498] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[    0.412577] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.412680] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.412732] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.412783] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.412842] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[    0.412912]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.420347] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 *11)
[    0.420400] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 *11)
[    0.420450] ACPI: PCI Interrupt Link [LNKC] (IRQs *10 11)
[    0.420501] ACPI: PCI Interrupt Link [LNKD] (IRQs *10 11)
[    0.420551] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 *11)
[    0.420605] ACPI: PCI Interrupt Link [LNKF] (IRQs *10 11)
[    0.420655] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[    0.420707] ACPI: PCI Interrupt Link [LNKH] (IRQs *10 11)
[    0.420824] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.420829] vgaarb: loaded
[    0.421057] SCSI subsystem initialized
[    0.421123] libata version 3.00 loaded.
[    0.421176] usbcore: registered new interface driver usbfs
[    0.421188] usbcore: registered new interface driver hub
[    0.421216] usbcore: registered new device driver usb
[    0.421878] wmi: Mapper loaded
[    0.421880] PCI: Using ACPI for IRQ routing
[    0.422091] PCI: pci_cache_line_size set to 64 bytes
[    0.422386] reserve RAM buffer: 000000000009d400 - 000000000009ffff 
[    0.422389] reserve RAM buffer: 00000000bf8a1000 - 00000000bfffffff 
[    0.422394] reserve RAM buffer: 00000000bf9cf000 - 00000000bfffffff 
[    0.422398] reserve RAM buffer: 00000000bfb09000 - 00000000bfffffff 
[    0.422403] reserve RAM buffer: 00000000bfd19000 - 00000000bfffffff 
[    0.422406] reserve RAM buffer: 00000000bfd5f000 - 00000000bfffffff 
[    0.422409] reserve RAM buffer: 00000000bfde2000 - 00000000bfffffff 
[    0.422412] reserve RAM buffer: 00000000bfe00000 - 00000000bfffffff 
[    0.422517] NetLabel: Initializing
[    0.422519] NetLabel:  domain hash size = 128
[    0.422520] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.422532] NetLabel:  unlabeled traffic allowed by default
[    0.422570] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.422576] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.422582] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.432077] Switching to clocksource hpet
[    0.435831] Switched to NOHz mode on CPU #0
[    0.435927] Switched to NOHz mode on CPU #1
[    0.440345] AppArmor: AppArmor Filesystem Enabled
[    0.440379] pnp: PnP ACPI init
[    0.440403] ACPI: bus type pnp registered
[    0.440806] pnp 00:00: [bus 00-ff]
[    0.440810] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.440812] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.440814] pnp 00:00: [io  0x0d00-0xffff window]
[    0.440817] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.440820] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.440822] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.440825] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.440827] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.440830] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.440832] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.440834] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.440837] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.440839] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.440842] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.440844] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.440847] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.440849] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    0.440852] pnp 00:00: [mem 0xc0000000-0xdfffffff window]
[    0.440854] pnp 00:00: [mem 0xf0000000-0xfebfffff window]
[    0.440945] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.441044] pnp 00:01: [io  0x0060]
[    0.441046] pnp 00:01: [io  0x0064]
[    0.441058] pnp 00:01: [irq 1]
[    0.441094] pnp 00:01: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.441107] pnp 00:02: [irq 12]
[    0.441144] pnp 00:02: Plug and Play ACPI device, IDs SYN1b22 SYN1b00 SYN0002 PNP0f13 (active)
[    0.441155] pnp 00:03: [io  0x0000-0x001f]
[    0.441158] pnp 00:03: [io  0x0081-0x0091]
[    0.441160] pnp 00:03: [io  0x0093-0x009f]
[    0.441162] pnp 00:03: [io  0x00c0-0x00df]
[    0.441165] pnp 00:03: [dma 4]
[    0.441202] pnp 00:03: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.441214] pnp 00:04: [mem 0xffc00000-0xffffffff]
[    0.441249] pnp 00:04: Plug and Play ACPI device, IDs INT0800 (active)
[    0.441325] pnp 00:05: [mem 0xfed00000-0xfed003ff]
[    0.441394] system 00:05: [mem 0xfed00000-0xfed003ff] has been reserved
[    0.441398] system 00:05: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
[    0.441410] pnp 00:06: [io  0x00f0]
[    0.441416] pnp 00:06: [irq 13]
[    0.441457] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.441472] pnp 00:07: [io  0x002e-0x002f]
[    0.441475] pnp 00:07: [io  0x004e-0x004f]
[    0.441477] pnp 00:07: [io  0x0061]
[    0.441479] pnp 00:07: [io  0x0063]
[    0.441481] pnp 00:07: [io  0x0065]
[    0.441483] pnp 00:07: [io  0x0067]
[    0.441485] pnp 00:07: [io  0x0070]
[    0.441487] pnp 00:07: [io  0x0080]
[    0.441488] pnp 00:07: [io  0x0092]
[    0.441491] pnp 00:07: [io  0x00b2-0x00b3]
[    0.441493] pnp 00:07: [io  0x0068-0x006f]
[    0.441495] pnp 00:07: [io  0x0480-0x048f]
[    0.441497] pnp 00:07: [io  0xffff]
[    0.441499] pnp 00:07: [io  0xffff]
[    0.441501] pnp 00:07: [io  0x0400-0x047f]
[    0.441503] pnp 00:07: [io  0x1180-0x11ff]
[    0.441505] pnp 00:07: [io  0xfe00]
[    0.441508] pnp 00:07: [mem 0xff800000-0xff800fff]
[    0.441577] system 00:07: [io  0x0480-0x048f] has been reserved
[    0.441580] system 00:07: [io  0xffff] has been reserved
[    0.441583] system 00:07: [io  0xffff] has been reserved
[    0.441586] system 00:07: [io  0x0400-0x047f] has been reserved
[    0.441589] system 00:07: [io  0x1180-0x11ff] has been reserved
[    0.441591] system 00:07: [io  0xfe00] has been reserved
[    0.441594] system 00:07: [mem 0xff800000-0xff800fff] has been reserved
[    0.441598] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.441608] pnp 00:08: [io  0x0070-0x0077]
[    0.441614] pnp 00:08: [irq 8]
[    0.441651] pnp 00:08: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.441818] pnp 00:09: [mem 0xfed1c000-0xfed1ffff]
[    0.441821] pnp 00:09: [mem 0xfed10000-0xfed13fff]
[    0.441823] pnp 00:09: [mem 0xfed18000-0xfed18fff]
[    0.441825] pnp 00:09: [mem 0xfed19000-0xfed19fff]
[    0.441828] pnp 00:09: [mem 0xe0000000-0xefffffff]
[    0.441830] pnp 00:09: [mem 0xfed20000-0xfed3ffff]
[    0.441909] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.441912] system 00:09: [mem 0xfed10000-0xfed13fff] has been reserved
[    0.441915] system 00:09: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.441918] system 00:09: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.441921] system 00:09: [mem 0xe0000000-0xefffffff] has been reserved
[    0.441924] system 00:09: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.441927] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.442079] pnp: PnP ACPI: found 10 devices
[    0.442081] ACPI: ACPI bus type pnp unregistered
[    0.442086] PnPBIOS: Disabled by ACPI PNP
[    0.454168] Freeing initrd memory: 12556k freed
[    0.479292] pci 0000:00:1c.0: BAR 15: assigned [mem 0xc0000000-0xc01fffff 64bit pref]
[    0.479298] pci 0000:00:1c.1: BAR 14: assigned [mem 0xc0200000-0xc03fffff]
[    0.479303] pci 0000:00:1c.1: BAR 15: assigned [mem 0xc0400000-0xc05fffff 64bit pref]
[    0.479308] pci 0000:00:1c.2: BAR 15: assigned [mem 0xc0600000-0xc07fffff 64bit pref]
[    0.479312] pci 0000:00:1c.0: BAR 13: assigned [io  0x4000-0x4fff]
[    0.479316] pci 0000:00:1c.1: BAR 13: assigned [io  0x5000-0x5fff]
[    0.479319] pci 0000:00:1c.2: BAR 13: assigned [io  0x6000-0x6fff]
[    0.479324] pci 0000:00:1f.3: BAR 0: assigned [mem 0xc0800000-0xc08000ff 64bit]
[    0.479332] pci 0000:00:1f.3: BAR 0: set to [mem 0xc0800000-0xc08000ff 64bit] (PCI address [0xc0800000-0xc08000ff])
[    0.479337] pci 0000:01:00.0: BAR 6: can't assign mem pref (size 0x20000)
[    0.479340] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.479343] pci 0000:00:01.0:   bridge window [io  0x2000-0x2fff]
[    0.479347] pci 0000:00:01.0:   bridge window [mem 0xf0000000-0xf2ffffff]
[    0.479351] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.479357] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.479360] pci 0000:00:1c.0:   bridge window [io  0x4000-0x4fff]
[    0.479366] pci 0000:00:1c.0:   bridge window [mem 0xf3000000-0xf30fffff]
[    0.479370] pci 0000:00:1c.0:   bridge window [mem 0xc0000000-0xc01fffff 64bit pref]
[    0.479377] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.479380] pci 0000:00:1c.1:   bridge window [io  0x5000-0x5fff]
[    0.479386] pci 0000:00:1c.1:   bridge window [mem 0xc0200000-0xc03fffff]
[    0.479391] pci 0000:00:1c.1:   bridge window [mem 0xc0400000-0xc05fffff 64bit pref]
[    0.479397] pci 0000:00:1c.2: PCI bridge to [bus 04-04]
[    0.479401] pci 0000:00:1c.2:   bridge window [io  0x6000-0x6fff]
[    0.479407] pci 0000:00:1c.2:   bridge window [mem 0xf3100000-0xf31fffff]
[    0.479411] pci 0000:00:1c.2:   bridge window [mem 0xc0600000-0xc07fffff 64bit pref]
[    0.479418] pci 0000:00:1c.4: PCI bridge to [bus 05-07]
[    0.479422] pci 0000:00:1c.4:   bridge window [io  0x3000-0x3fff]
[    0.479427] pci 0000:00:1c.4:   bridge window [mem 0xf4000000-0xf5ffffff]
[    0.479432] pci 0000:00:1c.4:   bridge window [mem 0xf6000000-0xf7ffffff 64bit pref]
[    0.479439] pci 0000:00:1e.0: PCI bridge to [bus 0d-0d]
[    0.479441] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.479446] pci 0000:00:1e.0:   bridge window [mem disabled]
[    0.479450] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.479482] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.479487] pci 0000:00:01.0: setting latency timer to 64
[    0.479494] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.479499] pci 0000:00:1c.0: setting latency timer to 64
[    0.479509] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.479513] pci 0000:00:1c.1: setting latency timer to 64
[    0.479523] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.479528] pci 0000:00:1c.2: setting latency timer to 64
[    0.479535] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.479539] pci 0000:00:1c.4: setting latency timer to 64
[    0.479546] pci 0000:00:1e.0: setting latency timer to 64
[    0.479550] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.479553] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.479555] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.479558] pci_bus 0000:00: resource 7 [mem 0x000d4000-0x000d7fff]
[    0.479560] pci_bus 0000:00: resource 8 [mem 0x000d8000-0x000dbfff]
[    0.479563] pci_bus 0000:00: resource 9 [mem 0x000dc000-0x000dffff]
[    0.479566] pci_bus 0000:00: resource 10 [mem 0x000e0000-0x000e3fff]
[    0.479568] pci_bus 0000:00: resource 11 [mem 0xc0000000-0xdfffffff]
[    0.479571] pci_bus 0000:00: resource 12 [mem 0xf0000000-0xfebfffff]
[    0.479573] pci_bus 0000:01: resource 0 [io  0x2000-0x2fff]
[    0.479576] pci_bus 0000:01: resource 1 [mem 0xf0000000-0xf2ffffff]
[    0.479579] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.479581] pci_bus 0000:02: resource 0 [io  0x4000-0x4fff]
[    0.479584] pci_bus 0000:02: resource 1 [mem 0xf3000000-0xf30fffff]
[    0.479586] pci_bus 0000:02: resource 2 [mem 0xc0000000-0xc01fffff 64bit pref]
[    0.479589] pci_bus 0000:03: resource 0 [io  0x5000-0x5fff]
[    0.479592] pci_bus 0000:03: resource 1 [mem 0xc0200000-0xc03fffff]
[    0.479594] pci_bus 0000:03: resource 2 [mem 0xc0400000-0xc05fffff 64bit pref]
[    0.479597] pci_bus 0000:04: resource 0 [io  0x6000-0x6fff]
[    0.479599] pci_bus 0000:04: resource 1 [mem 0xf3100000-0xf31fffff]
[    0.479602] pci_bus 0000:04: resource 2 [mem 0xc0600000-0xc07fffff 64bit pref]
[    0.479605] pci_bus 0000:05: resource 0 [io  0x3000-0x3fff]
[    0.479607] pci_bus 0000:05: resource 1 [mem 0xf4000000-0xf5ffffff]
[    0.479610] pci_bus 0000:05: resource 2 [mem 0xf6000000-0xf7ffffff 64bit pref]
[    0.479613] pci_bus 0000:0d: resource 4 [io  0x0000-0x0cf7]
[    0.479615] pci_bus 0000:0d: resource 5 [io  0x0d00-0xffff]
[    0.479618] pci_bus 0000:0d: resource 6 [mem 0x000a0000-0x000bffff]
[    0.479621] pci_bus 0000:0d: resource 7 [mem 0x000d4000-0x000d7fff]
[    0.479623] pci_bus 0000:0d: resource 8 [mem 0x000d8000-0x000dbfff]
[    0.479626] pci_bus 0000:0d: resource 9 [mem 0x000dc000-0x000dffff]
[    0.479628] pci_bus 0000:0d: resource 10 [mem 0x000e0000-0x000e3fff]
[    0.479631] pci_bus 0000:0d: resource 11 [mem 0xc0000000-0xdfffffff]
[    0.479633] pci_bus 0000:0d: resource 12 [mem 0xf0000000-0xfebfffff]
[    0.479678] NET: Registered protocol family 2
[    0.479760] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.480051] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.480573] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.480796] TCP: Hash tables configured (established 131072 bind 65536)
[    0.480798] TCP reno registered
[    0.480801] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.480810] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.480889] NET: Registered protocol family 1
[    0.481069] pci 0000:01:00.0: Boot video device
[    0.481251] PCI: CLS 64 bytes, default 64
[    0.481279] Simple Boot Flag at 0x57 set to 0x1
[    0.481486] cpufreq-nforce2: No nForce2 chipset.
[    0.481619] audit: initializing netlink socket (disabled)
[    0.481629] type=2000 audit(1310631719.476:1): initialized
[    0.491525] highmem bounce pool size: 64 pages
[    0.491531] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.493515] VFS: Disk quotas dquot_6.5.2
[    0.493580] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.494299] fuse init (API version 7.16)
[    0.494400] msgmni has been set to 1676
[    0.494669] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.494693] io scheduler noop registered
[    0.494695] io scheduler deadline registered
[    0.494711] io scheduler cfq registered (default)
[    0.494831] pcieport 0000:00:01.0: setting latency timer to 64
[    0.494868] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.494926] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.494967] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.495031] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.495071] pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X
[    0.495134] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.495174] pcieport 0000:00:1c.2: irq 43 for MSI/MSI-X
[    0.495240] pcieport 0000:00:1c.4: setting latency timer to 64
[    0.495281] pcieport 0000:00:1c.4: irq 44 for MSI/MSI-X
[    0.495370] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.495396] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.495471] intel_idle: MWAIT substates: 0x22220
[    0.495473] intel_idle: does not run on family 6 model 23
[    0.496940] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.498048] ACPI: AC Adapter [ADP1] (on-line)
[    0.498168] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.528018] ACPI: Lid Switch [LID0]
[    0.528068] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    0.528097] ACPI: Sleep Button [SLPB]
[    0.528148] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.528152] ACPI: Power Button [PWRF]
[    0.528371] ACPI: acpi_idle registered with cpuidle
[    0.528745] Monitor-Mwait will be used to enter C-1 state
[    0.528772] Monitor-Mwait will be used to enter C-2 state
[    0.528778] Marking TSC unstable due to TSC halts in idle
[    0.543789] thermal LNXTHERM:00: registered as thermal_zone0
[    0.543792] ACPI: Thermal Zone [TZS0] (72 C)
[    0.549618] thermal LNXTHERM:01: registered as thermal_zone1
[    0.549621] ACPI: Thermal Zone [TZS1] (72 C)
[    0.549641] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.549678] ACPI: Battery Slot [BAT0] (battery absent)
[    0.549705] ERST: Table is not found!
[    0.549732] isapnp: Scanning for PnP cards...
[    0.549767] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.902878] isapnp: No Plug & Play device found
[    0.905817] Linux agpgart interface v0.103
[    0.907349] brd: module loaded
[    0.908009] loop: module loaded
[    0.908095] i2c-core: driver [adp5520] using legacy suspend method
[    0.908097] i2c-core: driver [adp5520] using legacy resume method
[    0.908565] Fixed MDIO Bus: probed
[    0.908609] PPP generic driver version 2.4.2
[    0.908647] tun: Universal TUN/TAP device driver, 1.6
[    0.908649] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.908735] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.908759] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 20 (level, low) -> IRQ 20
[    0.908771] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.908775] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.908815] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.908864] ehci_hcd 0000:00:1a.7: debug port 1
[    0.912740] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
[    0.912758] ehci_hcd 0000:00:1a.7: irq 20, io mem 0xf3404800
[    0.928013] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.928150] hub 1-0:1.0: USB hub found
[    0.928155] hub 1-0:1.0: 4 ports detected
[    0.928241] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.928253] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.928256] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.928299] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.928345] ehci_hcd 0000:00:1d.7: debug port 1
[    0.932240] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.932254] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf3404c00
[    0.948012] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.948149] hub 2-0:1.0: USB hub found
[    0.948154] hub 2-0:1.0: 8 ports detected
[    0.948240] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.948254] uhci_hcd: USB Universal Host Controller Interface driver
[    0.948274] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.948280] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.948283] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.948322] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.948360] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00001800
[    0.948485] hub 3-0:1.0: USB hub found
[    0.948489] hub 3-0:1.0: 2 ports detected
[    0.948560] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    0.948566] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.948570] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.948609] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.948646] uhci_hcd 0000:00:1a.1: irq 20, io base 0x00001820
[    0.948772] hub 4-0:1.0: USB hub found
[    0.948776] hub 4-0:1.0: 2 ports detected
[    0.948848] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.948854] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.948858] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.948895] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    0.952039] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001840
[    0.952165] hub 5-0:1.0: USB hub found
[    0.952169] hub 5-0:1.0: 2 ports detected
[    0.952241] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.952247] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.952250] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.952294] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    0.952340] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00001860
[    0.952468] hub 6-0:1.0: USB hub found
[    0.952472] hub 6-0:1.0: 2 ports detected
[    0.952544] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.952550] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.952553] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.952591] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    0.952636] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001880
[    0.952762] hub 7-0:1.0: USB hub found
[    0.952765] hub 7-0:1.0: 2 ports detected
[    0.952836] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 18 (level, low) -> IRQ 18
[    0.952842] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.952846] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.952884] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 8
[    0.952920] uhci_hcd 0000:00:1d.3: irq 18, io base 0x000018a0
[    0.953047] hub 8-0:1.0: USB hub found
[    0.953053] hub 8-0:1.0: 2 ports detected
[    0.953191] i8042: PNP: PS/2 Controller [PNP0303:KBD0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.964312] i8042: Detected active multiplexing controller, rev 1.1
[    0.971740] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.971746] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.971778] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.971808] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.971835] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.971956] mousedev: PS/2 mouse device common for all mice
[    0.972394] rtc_cmos 00:08: RTC can wake from S4
[    0.972453] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    0.972478] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.972557] device-mapper: uevent: version 1.0.3
[    0.972641] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
[    0.972704] device-mapper: multipath: version 1.2.0 loaded
[    0.972706] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.972784] EISA: Probing bus 0 at eisa.0
[    0.972786] EISA: Cannot allocate resource for mainboard
[    0.972789] Cannot allocate resource for EISA slot 1
[    0.972791] Cannot allocate resource for EISA slot 2
[    0.972792] Cannot allocate resource for EISA slot 3
[    0.972794] Cannot allocate resource for EISA slot 4
[    0.972796] Cannot allocate resource for EISA slot 5
[    0.972798] Cannot allocate resource for EISA slot 6
[    0.972800] Cannot allocate resource for EISA slot 7
[    0.972802] Cannot allocate resource for EISA slot 8
[    0.972803] EISA: Detected 0 cards.
[    0.972899] cpuidle: using governor ladder
[    0.972980] cpuidle: using governor menu
[    0.973277] TCP cubic registered
[    0.973416] NET: Registered protocol family 10
[    0.974019] NET: Registered protocol family 17
[    0.974039] Registering the dns_resolver key type
[    0.974612] Using IPI No-Shortcut mode
[    0.974711] PM: Hibernation image not present or could not be loaded.
[    0.974722] registered taskstats version 1
[    0.975205]   Magic number: 3:726:371
[    0.975289] rtc_cmos 00:08: setting system clock to 2011-07-14 08:22:01 UTC (1310631721)
[    0.975292] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.975294] EDD information not available.
[    0.975423] Freeing unused kernel memory: 700k freed
[    0.975693] Write protecting the kernel text: 5192k
[    0.975749] Write protecting the kernel read-only data: 2148k
[    0.993230] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.999217] <30>udev[67]: starting version 167
[    1.183929] tg3.c:v3.116 (December 3, 2010)
[    1.184138] tg3 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.184241] tg3 0000:02:00.0: setting latency timer to 64
[    1.252028] ahci 0000:00:1f.2: version 3.0
[    1.252059] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.252137] ahci 0000:00:1f.2: irq 45 for MSI/MSI-X
[    1.252199] ahci: SSS flag set, parallel bus scan disabled
[    1.252233] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[    1.252237] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ccc ems 
[    1.252243] ahci 0000:00:1f.2: setting latency timer to 64
[    1.276800] scsi0 : ahci
[    1.276920] scsi1 : ahci
[    1.276996] scsi2 : ahci
[    1.277075] scsi3 : ahci
[    1.277160] scsi4 : ahci
[    1.277235] scsi5 : ahci
[    1.277301] ata1: SATA max UDMA/133 abar m2048@0xf3404000 port 0xf3404100 irq 45
[    1.277305] ata2: SATA max UDMA/133 abar m2048@0xf3404000 port 0xf3404180 irq 45
[    1.277307] ata3: DUMMY
[    1.277308] ata4: DUMMY
[    1.277311] ata5: SATA max UDMA/133 abar m2048@0xf3404000 port 0xf3404300 irq 45
[    1.277314] ata6: SATA max UDMA/133 abar m2048@0xf3404000 port 0xf3404380 irq 45
[    1.329133] tg3 0000:02:00.0: eth0: Tigon3 [partno(BCM95784M) rev 5784100] (PCI Express) MAC address 00:1f:16:b3:b9:e2
[    1.329137] tg3 0000:02:00.0: eth0: attached PHY is 5784 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[    1.329140] tg3 0000:02:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.329143] tg3 0000:02:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    1.360043] usb 2-5: new high speed USB device using ehci_hcd and address 2
[    1.596045] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.628232] ata1.00: ATA-8: WDC WD3200BEVT-22ZCT0, 11.01A11, max UDMA/133
[    1.628236] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.630855] ata1.00: configured for UDMA/133
[    1.631056] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200BEVT-2 11.0 PQ: 0 ANSI: 5
[    1.631243] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.631264] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.631319] sd 0:0:0:0: [sda] Write Protect is off
[    1.631322] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.631346] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.644038] usb 2-8: new high speed USB device using ehci_hcd and address 3
[    1.670777]  sda: sda1 sda2 sda3 sda4 < sda5 >
[    1.671204] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.795583] usbcore: registered new interface driver uas
[    2.032041] usb 3-1: new full speed USB device using uhci_hcd and address 2
[    2.352109] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.356194] ata2.00: ATAPI: HL-DT-ST DVDRAM GT20N, CP02, max UDMA/133
[    2.361056] ata2.00: configured for UDMA/133
[    2.366586] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GT20N     CP02 PQ: 0 ANSI: 5
[    2.371527] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.371532] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.371701] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.371781] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.688097] ata5: SATA link down (SStatus 0 SControl 300)
[    3.008096] ata6: SATA link down (SStatus 0 SControl 300)
[    3.013612] Initializing USB Mass Storage driver...
[    3.014426] scsi6 : usb-storage 2-8:1.0
[    3.014670] usbcore: registered new interface driver usb-storage
[    3.014673] USB Mass Storage support registered.
[    3.525143] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    4.014502] scsi 6:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[    4.015095] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    7.668078] usb 2-8: USB disconnect, address 3
[    7.668386] sd 6:0:0:0: [sdb] READ CAPACITY failed
[    7.668389] sd 6:0:0:0: [sdb]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[    7.668393] sd 6:0:0:0: [sdb] Sense not available.
[    7.668418] sd 6:0:0:0: [sdb] Write Protect is off
[    7.668422] sd 6:0:0:0: [sdb] Mode Sense: 00 00 00 00
[    7.668445] sd 6:0:0:0: [sdb] Asking for cache data failed
[    7.668448] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    7.668600] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[   13.954716] <30>udev[306]: starting version 167
[   13.990557] lp: driver loaded but no devices found
[   14.119474] Adding 8821756k swap on /dev/sda5.  Priority:-1 extents:1 across:8821756k 
[   14.155915] acpi device:03: registered as cooling_device2
[   14.156036] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input4
[   14.156097] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   14.224116] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,user_xattr
[   14.268140] cfg80211: Calling CRDA to update world regulatory domain
[   14.320042] Linux video capture interface: v2.00
[   14.328667] nvidia: module license 'NVIDIA' taints kernel.
[   14.328671] Disabling lock debugging due to kernel taint
[   14.342958] type=1400 audit(1310631734.862:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=552 comm="apparmor_parser"
[   14.342968] type=1400 audit(1310631734.862:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=551 comm="apparmor_parser"
[   14.343860] type=1400 audit(1310631734.862:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=552 comm="apparmor_parser"
[   14.343873] type=1400 audit(1310631734.862:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=551 comm="apparmor_parser"
[   14.344448] type=1400 audit(1310631734.866:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=552 comm="apparmor_parser"
[   14.344488] type=1400 audit(1310631734.866:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=551 comm="apparmor_parser"
[   14.417122] uvcvideo: Found UVC 1.00 device CNF7017 (04f2:b044)
[   14.521792] acer-wmi: Acer Laptop ACPI-WMI Extras
[   14.527631] acer-wmi: Brightness must be controlled by generic video driver
[   14.534068] cfg80211: World regulatory domain updated:
[   14.534071] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   14.534074] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.534077] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.534080] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.534082] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.534085] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.542491] input: CNF7017 as /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/input/input5
[   14.543225] usbcore: registered new interface driver uvcvideo
[   14.543228] USB Video Class driver (v1.0.0)
[   14.639844] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[   14.639850] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[   14.639866] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   14.639919] HDA Intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   14.639946] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   14.694574] hda_codec: ALC888: BIOS auto-probing.
[   14.715908] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   15.353619] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   15.353622] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   15.353716] iwlagn 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   15.353724] iwlagn 0000:04:00.0: setting latency timer to 64
[   15.353752] iwlagn 0000:04:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[   15.374443] iwlagn 0000:04:00.0: device EEPROM VER=0x11f, CALIB=0x4
[   15.374445] iwlagn 0000:04:00.0: Device SKU: 0Xb
[   15.374460] iwlagn 0000:04:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   15.374528] iwlagn 0000:04:00.0: irq 47 for MSI/MSI-X
[   15.562052] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.562062] nvidia 0000:01:00.0: setting latency timer to 64
[   15.562067] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   15.562475] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: (null)
[   15.563253] NVRM: loading NVIDIA UNIX x86 Kernel Module  270.41.06  Mon Apr 18 14:54:25 PDT 2011
[   15.692922] iwlagn 0000:04:00.0: loaded firmware version 8.83.5.1 build 33692
[   15.693215] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   15.699842] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   15.887514] type=1400 audit(1310631736.406:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=797 comm="apparmor_parser"
[   15.888342] type=1400 audit(1310631736.410:9): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=796 comm="apparmor_parser"
[   15.900479] type=1400 audit(1310631736.422:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=797 comm="apparmor_parser"
[   15.901065] type=1400 audit(1310631736.422:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=797 comm="apparmor_parser"
[   15.936140] tg3 0000:02:00.0: irq 48 for MSI/MSI-X
[   16.043365] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.071035] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04733/0xa44000/0xa0000
[   16.125882] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input7
[   16.185881] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.443431] vesafb: framebuffer at 0xf1000000, mapped to 0xf8580000, using 1216k, total 1216k
[   16.443435] vesafb: mode is 640x480x32, linelength=2560, pages=0
[   16.443437] vesafb: scrolling: redraw
[   16.443440] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   16.443581] Console: switching to colour frame buffer device 80x30
[   16.443595] fb0: VESA VGA frame buffer device
[   16.474409] ppdev: user-space parallel port driver
[   17.721983] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,user_xattr,commit=0
[   17.725092] EXT4-fs (sda3): re-mounted. Opts: commit=0
[   20.937138] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,user_xattr,commit=0
[   20.984527] EXT4-fs (sda3): re-mounted. Opts: commit=0
[   32.313779] wlan0: direct probe to 00:22:6b:78:2e:64 (try 1/3)
[   32.512023] wlan0: direct probe to 00:22:6b:78:2e:64 (try 2/3)
[   32.522012] wlan0: direct probe responded
[   32.522040] wlan0: authenticate with 00:22:6b:78:2e:64 (try 1)
[   32.542588] wlan0: authenticated
[   32.542618] wlan0: associate with 00:22:6b:78:2e:64 (try 1)
[   32.559753] wlan0: RX AssocResp from 00:22:6b:78:2e:64 (capab=0x401 status=0 aid=8)
[   32.559756] wlan0: associated
[   32.563855] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   32.563916] cfg80211: Calling CRDA for country: US
[   32.568632] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   32.568636] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   32.568638] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   32.568641] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   32.568644] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   32.568646] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   32.568649] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   32.568652] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   32.568654] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   32.568657] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   32.568659] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   32.568662] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   32.568664] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   32.568667] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   32.568669] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   32.568672] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   32.568674] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   32.568677] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   32.568679] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   32.568682] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   32.568684] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   32.568686] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   32.568689] cfg80211: Disabling freq 2467 MHz
[   32.568690] cfg80211: Disabling freq 2472 MHz
[   32.568692] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
[   32.568695] cfg80211: 5170000 KHz - 5250000 KHz @  KHz), (300 mBi, 1700 mBm)
[   32.568697] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
[   32.568700] cfg80211: 5170000 KHz - 5250000 KHz @  KHz), (300 mBi, 1700 mBm)
[   32.568702] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
[   32.568705] cfg80211: 5170000 KHz - 5250000 KHz @  KHz), (300 mBi, 1700 mBm)
[   32.568707] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
[   32.568710] cfg80211: 5170000 KHz - 5250000 KHz @  KHz), (300 mBi, 1700 mBm)
[   32.568712] cfg80211: Updating information on frequency 5260 MHz for a 20 MHz width channel with regulatory rule:
[   32.568715] cfg80211: 5250000 KHz - 5330000 KHz @  KHz), (300 mBi, 2000 mBm)
[   32.568717] cfg80211: Updating information on frequency 5280 MHz for a 20 MHz width channel with regulatory rule:
[   32.568720] cfg80211: 5250000 KHz - 5330000 KHz @  KHz), (300 mBi, 2000 mBm)
[   32.568722] cfg80211: Updating information on frequency 5300 MHz for a 20 MHz width channel with regulatory rule:
[   32.568725] cfg80211: 5250000 KHz - 5330000 KHz @  KHz), (300 mBi, 2000 mBm)
[   32.568727] cfg80211: Updating information on frequency 5320 MHz for a 20 MHz width channel with regulatory rule:
[   32.568730] cfg80211: 5250000 KHz - 5330000 KHz @  KHz), (300 mBi, 2000 mBm)
[   32.568732] cfg80211: Updating information on frequency 5500 MHz for a 20 MHz width channel with regulatory rule:
[   32.568735] cfg80211: 5490000 KHz - 5600000 KHz @  KHz), (300 mBi, 2000 mBm)
[   32.568737] cfg80211: Updating information on frequency 5520 MHz for a 20 MHz width channel with regulatory rule:
[   32.568740] cfg80211: 5490000 KHz - 5600000 KHz @  KHz), (300 mBi, 2000 mBm)
[   32.568742] cfg80211: Updating information on frequency 5540 MHz for a 20 MHz width channel with regulatory rule:
[   32.568745] cfg80211: 5490000 KHz - 5600000 KHz @  KHz), (300 mBi, 2000 mBm)
[   32.568747] cfg80211: Updating information on frequency 5560 MHz for a 20 MHz width channel with regulatory rule:
[   32.568750] cfg80211: 5490000 KHz - 5600000 KHz @  KHz), (300 mBi, 2000 mBm)
[   32.568752] cfg80211: Updating information on frequency 5580 MHz for a 20 MHz width channel with regulatory rule:
[   32.568755] cfg80211: 5490000 KHz - 5600000 KHz @  KHz), (300 mBi, 2000 mBm)
[   32.568757] cfg80211: Disabling freq 5600 MHz
[   32.568758] cfg80211: Disabling freq 5620 MHz
[   32.568760] cfg80211: Disabling freq 5640 MHz
[   32.568762] cfg80211: Updating information on frequency 5660 MHz for a 20 MHz width channel with regulatory rule:
[   32.568765] cfg80211: 5650000 KHz - 5710000 KHz @  KHz), (300 mBi, 2000 mBm)
[   32.568767] cfg80211: Updating information on frequency 5680 MHz for a 20 MHz width channel with regulatory rule:
[   32.568770] cfg80211: 5650000 KHz - 5710000 KHz @  KHz), (300 mBi, 2000 mBm)
[   32.568772] cfg80211: Updating information on frequency 5700 MHz for a 20 MHz width channel with regulatory rule:
[   32.568775] cfg80211: 5650000 KHz - 5710000 KHz @  KHz), (300 mBi, 2000 mBm)
[   32.568777] cfg80211: Updating information on frequency 5745 MHz for a 20 MHz width channel with regulatory rule:
[   32.568780] cfg80211: 5735000 KHz - 5835000 KHz @  KHz), (300 mBi, 3000 mBm)
[   32.568782] cfg80211: Updating information on frequency 5765 MHz for a 20 MHz width channel with regulatory rule:
[   32.568785] cfg80211: 5735000 KHz - 5835000 KHz @  KHz), (300 mBi, 3000 mBm)
[   32.568787] cfg80211: Updating information on frequency 5785 MHz for a 20 MHz width channel with regulatory rule:
[   32.568790] cfg80211: 5735000 KHz - 5835000 KHz @  KHz), (300 mBi, 3000 mBm)
[   32.568792] cfg80211: Updating information on frequency 5805 MHz for a 20 MHz width channel with regulatory rule:
[   32.568795] cfg80211: 5735000 KHz - 5835000 KHz @  KHz), (300 mBi, 3000 mBm)
[   32.568797] cfg80211: Updating information on frequency 5825 MHz for a 20 MHz width channel with regulatory rule:
[   32.568800] cfg80211: 5735000 KHz - 5835000 KHz @  KHz), (300 mBi, 3000 mBm)
[   32.568804] cfg80211: Regulatory domain changed to country: US
[   32.568806] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   32.568808] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   32.568811] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   32.568814] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   32.568816] cfg80211:     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   32.568819] cfg80211:     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   32.568821] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   34.779450] iwlagn 0000:04:00.0: Aggregation not enabled for tid 0 because load = 6
[   42.730201] iwlagn 0000:04:00.0: Aggregation not enabled for tid 0 because load = 0
[   43.424012] wlan0: no IPv6 routers present
[   47.057468] wlan0: deauthenticating from 00:22:6b:78:2e:64 by local choice (reason=3)
[   47.072149] cfg80211: All devices are disconnected, going to restore regulatory settings
[   47.072155] cfg80211: Restoring regulatory settings
[   47.072160] cfg80211: Calling CRDA to update world regulatory domain
[   47.076758] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   47.076764] cfg80211: World regulatory domain updated:
[   47.076766] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   47.076769] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   47.076772] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   47.076775] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   47.076802] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   47.076805] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   49.719344] wlan0: authenticate with 00:25:9c:e1:4b:5d (try 1)
[   49.724177] wlan0: authenticated
[   49.724209] wlan0: associate with 00:25:9c:e1:4b:5d (try 1)
[   49.727846] wlan0: RX AssocResp from 00:25:9c:e1:4b:5d (capab=0x401 status=0 aid=3)
[   49.727850] wlan0: associated
[  104.101780] exe (2055): /proc/2055/oom_adj is deprecated, please use /proc/2055/oom_score_adj instead.
[  723.379301] CPU0: Core temperature above threshold, cpu clock throttled (total events = 1)
[  723.379946] CPU0: Core temperature/speed normal
[  899.988039] [Hardware Error]: Machine check events logged
____________________________________________

Using built-in specs.
COLLECT_GCC=gcc
COLLECT_LTO_WRAPPER=/usr/lib/i386-linux-gnu/gcc/i686-linux-gnu/4.5.2/lto-wrapper
Target: i686-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu/Linaro 4.5.2-8ubuntu4' --with-bugurl=file:///usr/share/doc/gcc-4.5/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-4.5 --enable-shared --enable-multiarch --with-multiarch-defaults=i386-linux-gnu --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib/i386-linux-gnu --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.5 --libdir=/usr/lib/i386-linux-gnu --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --enable-plugin --enable-gold --enable-ld=default --with-plugin-ld=ld.gold --enable-objc-gc --enable-targets=all --disable-werror --with-arch-32=i686 --with-tune=generic --enable-checking=release --build=i686-linux-gnu --host=i686-linux-gnu --target=i686-linux-gnu
Thread model: posix
gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4) 
____________________________________________

Using built-in specs.
COLLECT_GCC=g++
COLLECT_LTO_WRAPPER=/usr/lib/i386-linux-gnu/gcc/i686-linux-gnu/4.5.2/lto-wrapper
Target: i686-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu/Linaro 4.5.2-8ubuntu4' --with-bugurl=file:///usr/share/doc/gcc-4.5/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-4.5 --enable-shared --enable-multiarch --with-multiarch-defaults=i386-linux-gnu --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib/i386-linux-gnu --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.5 --libdir=/usr/lib/i386-linux-gnu --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --enable-plugin --enable-gold --enable-ld=default --with-plugin-ld=ld.gold --enable-objc-gc --enable-targets=all --disable-werror --with-arch-32=i686 --with-tune=generic --enable-checking=release --build=i686-linux-gnu --host=i686-linux-gnu --target=i686-linux-gnu
Thread model: posix
gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4) 
____________________________________________

xset -q:

Keyboard Control:
  auto repeat:  on    key click percent:  0    LED mask:  00000000
  XKB indicators:
    00: Caps Lock:   off    01: Num Lock:    off    02: Scroll Lock: off
    03: Compose:     off    04: Kana:        off    05: Sleep:       off
    06: Suspend:     off    07: Mute:        off    08: Misc:        off
    09: Mail:        off    10: Charging:    off    11: Shift Lock:  off
    12: Group 2:     off    13: Mouse Keys:  off
  auto repeat delay:  500    repeat rate:  30
  auto repeating keys:  00ffffffdffffbbf
                        fadfffefffedffff
                        9fffffffffffffff
                        fff7ffffffffffff
  bell percent:  0    bell pitch:  400    bell duration:  100
Pointer Control:
  acceleration:  2/1    threshold:  4
Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  0    cycle:  0
Colors:
  default colormap:  0x20    BlackPixel:  0    WhitePixel:  16777215
Font Path:
  /usr/share/fonts/X11/misc,/usr/share/fonts/X11/Type1,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,built-ins
DPMS (Energy Star):
  Standby: 0    Suspend: 0    Off: 0
  DPMS is Enabled
  Monitor is On
____________________________________________

nvidia-settings -q all:


Attributes queryable via sharan-Aspire-5738:0.0:

  Attribute 'OperatingSystem' (sharan-Aspire-5738:0.0): 0.
    The valid values for 'OperatingSystem' are in the range 0 - 2
    (inclusive).
    'OperatingSystem' is a read-only attribute.
    'OperatingSystem' can use the following target types: X Screen, GPU.

  Attribute 'NvidiaDriverVersion' (sharan-Aspire-5738:0.0): 270.41.06 
    'NvidiaDriverVersion' is a string attribute.
    'NvidiaDriverVersion' is a read-only attribute.
    'NvidiaDriverVersion' can use the following target types: X Screen,
    GPU.

  Attribute 'NvControlVersion' (sharan-Aspire-5738:0.0): 1.26 
    'NvControlVersion' is a string attribute.
    'NvControlVersion' is a read-only attribute.
    'NvControlVersion' can use the following target types: X Screen.

  Attribute 'GLXServerVersion' (sharan-Aspire-5738:0.0): 1.4 
    'GLXServerVersion' is a string attribute.
    'GLXServerVersion' is a read-only attribute.
    'GLXServerVersion' can use the following target types: X Screen.

  Attribute 'GLXClientVersion' (sharan-Aspire-5738:0.0): 1.4 
    'GLXClientVersion' is a string attribute.
    'GLXClientVersion' is a read-only attribute.
    'GLXClientVersion' can use the following target types: X Screen.

  Attribute 'OpenGLVersion' (sharan-Aspire-5738:0.0): 3.3.0 NVIDIA
  270.41.06 
    'OpenGLVersion' is a string attribute.
    'OpenGLVersion' is a read-only attribute.
    'OpenGLVersion' can use the following target types: X Screen.

  Attribute 'XRandRVersion' (sharan-Aspire-5738:0.0): 1.3 
    'XRandRVersion' is a string attribute.
    'XRandRVersion' is a read-only attribute.
    'XRandRVersion' can use the following target types: X Screen.

  Attribute 'XF86VidModeVersion' (sharan-Aspire-5738:0.0): 2.2 
    'XF86VidModeVersion' is a string attribute.
    'XF86VidModeVersion' is a read-only attribute.
    'XF86VidModeVersion' can use the following target types: X Screen.

  Attribute 'XvVersion' (sharan-Aspire-5738:0.0): 2.2 
    'XvVersion' is a string attribute.
    'XvVersion' is a read-only attribute.
    'XvVersion' can use the following target types: X Screen.

  Attribute 'TwinView' (sharan-Aspire-5738:0.0): 0.
    'TwinView' is a boolean attribute; valid values are: 1 (on/true) and 0
    (off/false).
    'TwinView' is a read-only attribute.
    'TwinView' can use the following target types: X Screen.

  Attribute 'ConnectedDisplays' (sharan-Aspire-5738:0.0): 0x00010000.
    'ConnectedDisplays' is a bitmask attribute.
    'ConnectedDisplays' is a read-only attribute.
    'ConnectedDisplays' can use the following target types: X Screen, GPU.

  Attribute 'EnabledDisplays' (sharan-Aspire-5738:0.0): 0x00010000.
    'EnabledDisplays' is a bitmask attribute.
    'EnabledDisplays' is a read-only attribute.
    'EnabledDisplays' can use the following target types: X Screen, GPU.

  Attribute 'CursorShadow' (sharan-Aspire-5738:0.0): 0.
    'CursorShadow' is a boolean attribute; valid values are: 1 (on/true)
    and 0 (off/false).
    'CursorShadow' can use the following target types: X Screen.

  Attribute 'CursorShadowAlpha' (sharan-Aspire-5738:0.0): 64.
    The valid values for 'CursorShadowAlpha' are in the range 0 - 254
    (inclusive).
    'CursorShadowAlpha' can use the following target types: X Screen.

  Attribute 'CursorShadowRed' (sharan-Aspire-5738:0.0): 0.
    The valid values for 'CursorShadowRed' are in the range 0 - 255
    (inclusive).
    'CursorShadowRed' can use the following target types: X Screen.

  Attribute 'CursorShadowGreen' (sharan-Aspire-5738:0.0): 0.
    The valid values for 'CursorShadowGreen' are in the range 0 - 255
    (inclusive).
    'CursorShadowGreen' can use the following target types: X Screen.

  Attribute 'CursorShadowBlue' (sharan-Aspire-5738:0.0): 0.
    The valid values for 'CursorShadowBlue' are in the range 0 - 255
    (inclusive).
    'CursorShadowBlue' can use the following target types: X Screen.

  Attribute 'CursorShadowXOffset' (sharan-Aspire-5738:0.0): 4.
    The valid values for 'CursorShadowXOffset' are in the range 0 - 32
    (inclusive).
    'CursorShadowXOffset' can use the following target types: X Screen.

  Attribute 'CursorShadowYOffset' (sharan-Aspire-5738:0.0): 2.
    The valid values for 'CursorShadowYOffset' are in the range 0 - 32
    (inclusive).
    'CursorShadowYOffset' can use the following target types: X Screen.

  Attribute 'AssociatedDisplays' (sharan-Aspire-5738:0.0): 0x00010000.
    'AssociatedDisplays' is a bitmask attribute.
    'AssociatedDisplays' can use the following target types: X Screen.

  Attribute 'InitialPixmapPlacement' (sharan-Aspire-5738:0.0): 2.
    The valid values for 'InitialPixmapPlacement' are in the range 0 - 4
    (inclusive).
    'InitialPixmapPlacement' can use the following target types: X Screen.

  Attribute 'DynamicTwinview' (sharan-Aspire-5738:0.0): 1.
    'DynamicTwinview' is an integer attribute.
    'DynamicTwinview' is a read-only attribute.
    'DynamicTwinview' can use the following target types: X Screen.

  Attribute 'MultiGpuDisplayOwner' (sharan-Aspire-5738:0.0): 0.
    'MultiGpuDisplayOwner' is an integer attribute.
    'MultiGpuDisplayOwner' is a read-only attribute.
    'MultiGpuDisplayOwner' can use the following target types: X Screen.

  Attribute 'GlyphCache' (sharan-Aspire-5738:0.0): 1.
    'GlyphCache' is a boolean attribute; valid values are: 1 (on/true) and
    0 (off/false).
    'GlyphCache' can use the following target types: X Screen.

  Attribute 'NotebookDisplayChangeLidEvent' (sharan-Aspire-5738:0.0): 1.
    'NotebookDisplayChangeLidEvent' is an integer attribute.
    'NotebookDisplayChangeLidEvent' can use the following target types: X
    Screen.

  Attribute 'NotebookInternalLCD' (sharan-Aspire-5738:0.0): 0x00010000.
    'NotebookInternalLCD' is a bitmask attribute.
    'NotebookInternalLCD' is a read-only attribute.
    'NotebookInternalLCD' can use the following target types: X Screen,
    GPU.

  Attribute 'Depth30Allowed' (sharan-Aspire-5738:0.0): 0.
    'Depth30Allowed' is a boolean attribute; valid values are: 1 (on/true)
    and 0 (off/false).
    'Depth30Allowed' is a read-only attribute.
    'Depth30Allowed' can use the following target types: X Screen, GPU.

  Attribute 'NoScanout' (sharan-Aspire-5738:0.0): 0.
    'NoScanout' is a boolean attribute; valid values are: 1 (on/true) and 0
    (off/false).
    'NoScanout' is a read-only attribute.
    'NoScanout' can use the following target types: X Screen, GPU.

  Attribute 'XServerUniqueId' (sharan-Aspire-5738:0.0): -870534750.
    'XServerUniqueId' is an integer attribute.
    'XServerUniqueId' is a read-only attribute.
    'XServerUniqueId' can use the following target types: X Screen.

  Attribute 'PixmapCache' (sharan-Aspire-5738:0.0): 1.
    'PixmapCache' is a boolean attribute; valid values are: 1 (on/true) and
    0 (off/false).
    'PixmapCache' can use the following target types: X Screen.

  Attribute 'PixmapCacheRoundSizeKB' (sharan-Aspire-5738:0.0): 1024.
    The valid values for 'PixmapCacheRoundSizeKB' are in the range 4 -
    1048576 (inclusive).
    'PixmapCacheRoundSizeKB' can use the following target types: X Screen.

  Attribute 'SyncToVBlank' (sharan-Aspire-5738:0.0): 0.
    'SyncToVBlank' is a boolean attribute; valid values are: 1 (on/true)
    and 0 (off/false).
    'SyncToVBlank' can use the following target types: X Screen.

  Attribute 'LogAniso' (sharan-Aspire-5738:0.0): 0.
    The valid values for 'LogAniso' are in the range 0 - 4 (inclusive).
    'LogAniso' can use the following target types: X Screen.

  Attribute 'FSAA' (sharan-Aspire-5738:0.0): 0.
    Valid values for 'FSAA' are: 0, 1, 5, 7, 8, 9, 10 and 12.
    'FSAA' can use the following target types: X Screen.

  Attribute 'TextureSharpen' (sharan-Aspire-5738:0.0): 0.
    'TextureSharpen' is a boolean attribute; valid values are: 1 (on/true)
    and 0 (off/false).
    'TextureSharpen' can use the following target types: X Screen.

  Attribute 'AllowFlipping' (sharan-Aspire-5738:0.0): 1.
    'AllowFlipping' is a boolean attribute; valid values are: 1 (on/true)
    and 0 (off/false).
    'AllowFlipping' can use the following target types: X Screen.

  Attribute 'FSAAAppControlled' (sharan-Aspire-5738:0.0): 1.
    'FSAAAppControlled' is a boolean attribute; valid values are: 1
    (on/true) and 0 (off/false).
    'FSAAAppControlled' can use the following target types: X Screen.

  Attribute 'LogAnisoAppControlled' (sharan-Aspire-5738:0.0): 1.
    'LogAnisoAppControlled' is a boolean attribute; valid values are: 1
    (on/true) and 0 (off/false).
    'LogAnisoAppControlled' can use the following target types: X Screen.

  Attribute 'OpenGLImageSettings' (sharan-Aspire-5738:0.0): 1.
    The valid values for 'OpenGLImageSettings' are in the range 0 - 3
    (inclusive).
    'OpenGLImageSettings' can use the following target types: X Screen.

  Attribute 'FSAAAppEnhanced' (sharan-Aspire-5738:0.0): 0.
    'FSAAAppEnhanced' is a boolean attribute; valid values are: 1 (on/true)
    and 0 (off/false).
    'FSAAAppEnhanced' can use the following target types: X Screen.

  Attribute 'SliMosaicModeAvailable' (sharan-Aspire-5738:0.0): 0.
    'SliMosaicModeAvailable' is a boolean attribute; valid values are: 1
    (on/true) and 0 (off/false).
    'SliMosaicModeAvailable' is a read-only attribute.
    'SliMosaicModeAvailable' can use the following target types: X Screen,
    GPU, VCS.

  Attribute 'BusType' (sharan-Aspire-5738:0.0): 2.
    The valid values for 'BusType' are in the range 0 - 3 (inclusive).
    'BusType' is a read-only attribute.
    'BusType' can use the following target types: X Screen, GPU, SDI Input
    Device.

  Attribute 'PCIEMaxLinkSpeed' (sharan-Aspire-5738:0.0): 2500.
    'PCIEMaxLinkSpeed' is an integer attribute.
    'PCIEMaxLinkSpeed' is a read-only attribute.
    'PCIEMaxLinkSpeed' can use the following target types: X Screen, GPU,
    SDI Input Device.

  Attribute 'VideoRam' (sharan-Aspire-5738:0.0): 524288.
    'VideoRam' is an integer attribute.
    'VideoRam' is a read-only attribute.
    'VideoRam' can use the following target types: X Screen, GPU.

  Attribute 'Irq' (sharan-Aspire-5738:0.0): 16.
    'Irq' is an integer attribute.
    'Irq' is a read-only attribute.
    'Irq' can use the following target types: X Screen, GPU, SDI Input
    Device.

  Attribute 'CUDACores' (sharan-Aspire-5738:0.0): 8.
    'CUDACores' is an integer attribute.
    'CUDACores' is a read-only attribute.
    'CUDACores' can use the following target types: X Screen, GPU.

  Attribute 'GPUMemoryInterface' (sharan-Aspire-5738:0.0): 64.
    'GPUMemoryInterface' is an integer attribute.
    'GPUMemoryInterface' is a read-only attribute.
    'GPUMemoryInterface' can use the following target types: X Screen,
    GPU.

  Attribute 'GPUCoreTemp' (sharan-Aspire-5738:0.0): 54.
    'GPUCoreTemp' is an integer attribute.
    'GPUCoreTemp' is a read-only attribute.
    'GPUCoreTemp' can use the following target types: X Screen, GPU.

  Attribute 'GPU2DClockFreqs' (sharan-Aspire-5738:0.0): 169,100.
    The valid values for 'GPU2DClockFreqs' are in the ranges 42 - 338, 25 -
    1416 (inclusive).
    'GPU2DClockFreqs' can use the following target types: X Screen, GPU.

  Attribute 'GPU3DClockFreqs' (sharan-Aspire-5738:0.0): 640,500.
    The valid values for 'GPU3DClockFreqs' are in the ranges 160 - 1280,
    125 - 1416 (inclusive).
    'GPU3DClockFreqs' can use the following target types: X Screen, GPU.

  Attribute 'GPUDefault2DClockFreqs' (sharan-Aspire-5738:0.0): 169,100.
    'GPUDefault2DClockFreqs' is a packed integer attribute.
    'GPUDefault2DClockFreqs' is a read-only attribute.
    'GPUDefault2DClockFreqs' can use the following target types: X Screen,
    GPU.

  Attribute 'GPUDefault3DClockFreqs' (sharan-Aspire-5738:0.0): 640,500.
    'GPUDefault3DClockFreqs' is a packed integer attribute.
    'GPUDefault3DClockFreqs' is a read-only attribute.
    'GPUDefault3DClockFreqs' can use the following target types: X Screen,
    GPU.

  Attribute 'GPUCurrentClockFreqs' (sharan-Aspire-5738:0.0): 640,500.
    'GPUCurrentClockFreqs' is a packed integer attribute.
    'GPUCurrentClockFreqs' is a read-only attribute.
    'GPUCurrentClockFreqs' can use the following target types: X Screen,
    GPU.

  Attribute 'GPUCurrentProcessorClockFreqs' (sharan-Aspire-5738:0.0):
  1600.
    The valid values for 'GPUCurrentProcessorClockFreqs' are in the range
    400 - 3200 (inclusive).
    'GPUCurrentProcessorClockFreqs' can use the following target types: X
    Screen, GPU.

  Attribute 'GPUCurrentClockFreqsString' (sharan-Aspire-5738:0.0):
  nvclock=640, memclock=500, processorclock=1600 
    'GPUCurrentClockFreqsString' is a string attribute.
    'GPUCurrentClockFreqsString' can use the following target types: X
    Screen, GPU.

  Attribute 'BusRate' (sharan-Aspire-5738:0.0): 16.
    The valid values for 'BusRate' are in the range 1 - 16 (inclusive).
    'BusRate' is a read-only attribute.
    'BusRate' can use the following target types: X Screen, GPU, SDI Input
    Device.

  Attribute 'PCIEGen' (sharan-Aspire-5738:0.0): 1.
    'PCIEGen' is an integer attribute.
    'PCIEGen' is a read-only attribute.
    'PCIEGen' can use the following target types: X Screen, GPU, SDI Input
    Device.

  Attribute 'GPUErrors' (sharan-Aspire-5738:0.0): 0.
    'GPUErrors' is an integer attribute.
    'GPUErrors' is a read-only attribute.
    'GPUErrors' can use the following target types: X Screen.

  Attribute 'GPUPowerSource' (sharan-Aspire-5738:0.0): 0.
    'GPUPowerSource' is an integer attribute.
    'GPUPowerSource' is a read-only attribute.
    'GPUPowerSource' can use the following target types: X Screen, GPU.

  Attribute 'GPUCurrentPerfMode' (sharan-Aspire-5738:0.0): 1.
    'GPUCurrentPerfMode' is an integer attribute.
    'GPUCurrentPerfMode' is a read-only attribute.
    'GPUCurrentPerfMode' can use the following target types: X Screen,
    GPU.

  Attribute 'GPUCurrentPerfLevel' (sharan-Aspire-5738:0.0): 3.
    'GPUCurrentPerfLevel' is an integer attribute.
    'GPUCurrentPerfLevel' is a read-only attribute.
    'GPUCurrentPerfLevel' can use the following target types: X Screen,
    GPU.

  Attribute 'GPUAdaptiveClockState' (sharan-Aspire-5738:0.0): 1.
    'GPUAdaptiveClockState' is a boolean attribute; valid values are: 1
    (on/true) and 0 (off/false).
    'GPUAdaptiveClockState' is a read-only attribute.
    'GPUAdaptiveClockState' can use the following target types: X Screen,
    GPU.

  Attribute 'GPUPerfModes' (sharan-Aspire-5738:0.0): perf=0, nvclock=169,
  memclock=100, processorclock=338 ; perf=1, nvclock=275, memclock=250,
  processorclock=550 ; perf=2, nvclock=500, memclock=400,
  processorclock=1000 ; perf=3, nvclock=640, memclock=500,
  processorclock=1600 
    'GPUPerfModes' is a string attribute.
    'GPUPerfModes' is a read-only attribute.
    'GPUPerfModes' can use the following target types: X Screen, GPU.

  Attribute 'ECCSupported' (sharan-Aspire-5738:0.0): 0.
    'ECCSupported' is a boolean attribute; valid values are: 1 (on/true)
    and 0 (off/false).
    'ECCSupported' is a read-only attribute.
    'ECCSupported' can use the following target types: X Screen, GPU.

  Attribute 'ECCConfigurationSupported' (sharan-Aspire-5738:0.0): 0.
    'ECCConfigurationSupported' is a boolean attribute; valid values are: 1
    (on/true) and 0 (off/false).
    'ECCConfigurationSupported' is a read-only attribute.
    'ECCConfigurationSupported' can use the following target types: X
    Screen, GPU.

  Attribute 'GvoSupported' (sharan-Aspire-5738:0.0): 0.
    'GvoSupported' is a boolean attribute; valid values are: 1 (on/true)
    and 0 (off/false).
    'GvoSupported' is a read-only attribute.
    'GvoSupported' can use the following target types: X Screen.

  Attribute 'IsGvoDisplay' (sharan-Aspire-5738:0.0; display device: DFP-0):
  0.
    'IsGvoDisplay' is a boolean attribute; valid values are: 1 (on/true)
    and 0 (off/false).
    'IsGvoDisplay' is a read-only attribute.
    'IsGvoDisplay' is display device specific.
    'IsGvoDisplay' can use the following target types: X Screen, GPU.

  Attribute 'DigitalVibrance' (sharan-Aspire-5738:0.0; display device:
  DFP-0): 0.
    The valid values for 'DigitalVibrance' are in the range -1024 - 1023
    (inclusive).
    'DigitalVibrance' is display device specific.
    'DigitalVibrance' can use the following target types: X Screen, GPU.

  Attribute 'FrontendResolution' (sharan-Aspire-5738:0.0; display device:
  DFP-0): 1366,768.
    'FrontendResolution' is a packed integer attribute.
    'FrontendResolution' is a read-only attribute.
    'FrontendResolution' is display device specific.
    'FrontendResolution' can use the following target types: X Screen,
    GPU.

  Attribute 'BackendResolution' (sharan-Aspire-5738:0.0; display device:
  DFP-0): 1366,768.
    'BackendResolution' is a packed integer attribute.
    'BackendResolution' is a read-only attribute.
    'BackendResolution' is display device specific.
    'BackendResolution' can use the following target types: X Screen, GPU.

  Attribute 'FlatpanelNativeResolution' (sharan-Aspire-5738:0.0; display
  device: DFP-0): 1366,768.
    'FlatpanelNativeResolution' is a packed integer attribute.
    'FlatpanelNativeResolution' is a read-only attribute.
    'FlatpanelNativeResolution' is display device specific.
    'FlatpanelNativeResolution' can use the following target types: X
    Screen, GPU.

  Attribute 'FlatpanelBestFitResolution' (sharan-Aspire-5738:0.0; display
  device: DFP-0): 1366,768.
    'FlatpanelBestFitResolution' is a packed integer attribute.
    'FlatpanelBestFitResolution' is a read-only attribute.
    'FlatpanelBestFitResolution' is display device specific.
    'FlatpanelBestFitResolution' can use the following target types: X
    Screen, GPU.

  Attribute 'DFPScalingActive' (sharan-Aspire-5738:0.0; display device:
  DFP-0): 0.
    'DFPScalingActive' is a boolean attribute; valid values are: 1
    (on/true) and 0 (off/false).
    'DFPScalingActive' is a read-only attribute.
    'DFPScalingActive' is display device specific.
    'DFPScalingActive' can use the following target types: X Screen, GPU.

  Attribute 'GPUScaling' (sharan-Aspire-5738:0.0; display device: DFP-0):
  2,1.
    Valid values for 'GPUScaling' are: [1 and 2], [1, 2 and 3].
    'GPUScaling' is display device specific.
    'GPUScaling' can use the following target types: X Screen, GPU.

  Attribute 'GPUScalingDefaultTarget' (sharan-Aspire-5738:0.0; display
  device: DFP-0): 2.
    'GPUScalingDefaultTarget' is an integer attribute.
    'GPUScalingDefaultTarget' is a read-only attribute.
    'GPUScalingDefaultTarget' is display device specific.
    'GPUScalingDefaultTarget' can use the following target types: X Screen,
    GPU.

  Attribute 'GPUScalingDefaultMethod' (sharan-Aspire-5738:0.0; display
  device: DFP-0): 1.
    'GPUScalingDefaultMethod' is an integer attribute.
    'GPUScalingDefaultMethod' is a read-only attribute.
    'GPUScalingDefaultMethod' is display device specific.
    'GPUScalingDefaultMethod' can use the following target types: X Screen,
    GPU.

  Attribute 'GPUScalingActive' (sharan-Aspire-5738:0.0; display device:
  DFP-0): 0.
    'GPUScalingActive' is a boolean attribute; valid values are: 1
    (on/true) and 0 (off/false).
    'GPUScalingActive' is a read-only attribute.
    'GPUScalingActive' is display device specific.
    'GPUScalingActive' can use the following target types: X Screen, GPU.

  Attribute 'RefreshRate' (sharan-Aspire-5738:0.0; display device: DFP-0):
  59.97 Hz.
    'RefreshRate' is an integer attribute.
    'RefreshRate' is a read-only attribute.
    'RefreshRate' is display device specific.
    'RefreshRate' can use the following target types: X Screen, GPU.

  Attribute 'RefreshRate3' (sharan-Aspire-5738:0.0; display device: DFP-0):
  59.973 Hz.
    'RefreshRate3' is an integer attribute.
    'RefreshRate3' is a read-only attribute.
    'RefreshRate3' is display device specific.
    'RefreshRate3' can use the following target types: X Screen, GPU.

  Attribute 'OverscanCompensation' (sharan-Aspire-5738:0.0; display device:
  DFP-0): 0.
    The valid values for 'OverscanCompensation' are in the range 0 - 200
    (inclusive).
    'OverscanCompensation' is display device specific.
    'OverscanCompensation' can use the following target types: X Screen,
    GPU.

  Attribute 'ColorSpace' (sharan-Aspire-5738:0.0; display device: DFP-0):
  0.
    Valid values for 'ColorSpace' are: 0.
    'ColorSpace' is display device specific.
    'ColorSpace' can use the following target types: X Screen, GPU.

  Attribute 'ColorRange' (sharan-Aspire-5738:0.0; display device: DFP-0):
  0.
    Valid values for 'ColorRange' are: 0 and 1.
    'ColorRange' is display device specific.
    'ColorRange' can use the following target types: X Screen, GPU.

  Attribute 'XVideoTextureBrightness' (sharan-Aspire-5738:0.0): 0.
    The valid values for 'XVideoTextureBrightness' are in the range -1000 -
    1000 (inclusive).
    'XVideoTextureBrightness' can use the following target types: X
    Screen.

  Attribute 'XVideoTextureContrast' (sharan-Aspire-5738:0.0): 0.
    The valid values for 'XVideoTextureContrast' are in the range -1000 -
    1000 (inclusive).
    'XVideoTextureContrast' can use the following target types: X Screen.

  Attribute 'XVideoTextureHue' (sharan-Aspire-5738:0.0): 0.
    The valid values for 'XVideoTextureHue' are in the range -1000 - 1000
    (inclusive).
    'XVideoTextureHue' can use the following target types: X Screen.

  Attribute 'XVideoTextureSaturation' (sharan-Aspire-5738:0.0): 0.
    The valid values for 'XVideoTextureSaturation' are in the range -1000 -
    1000 (inclusive).
    'XVideoTextureSaturation' can use the following target types: X
    Screen.

  Attribute 'XVideoTextureSyncToVBlank' (sharan-Aspire-5738:0.0): 1.
    The valid values for 'XVideoTextureSyncToVBlank' are in the range 0 - 1
    (inclusive).
    'XVideoTextureSyncToVBlank' can use the following target types: X
    Screen.

  Attribute 'XVideoSyncToDisplay' (sharan-Aspire-5738:0.0): 0x00010000.
    'XVideoSyncToDisplay' is a bitmask attribute.
    'XVideoSyncToDisplay' can use the following target types: X Screen.

Attributes queryable via sharan-Aspire-5738:0[gpu:0]:

  Attribute 'OperatingSystem' (sharan-Aspire-5738:0[gpu:0]): 0.
    The valid values for 'OperatingSystem' are in the range 0 - 2
    (inclusive).
    'OperatingSystem' is a read-only attribute.
    'OperatingSystem' can use the following target types: X Screen, GPU.

  Attribute 'NvidiaDriverVersion' (sharan-Aspire-5738:0[gpu:0]): 270.41.06
    'NvidiaDriverVersion' is a string attribute.
    'NvidiaDriverVersion' is a read-only attribute.
    'NvidiaDriverVersion' can use the following target types: X Screen,
    GPU.

  Attribute 'ConnectedDisplays' (sharan-Aspire-5738:0[gpu:0]): 0x00010000.
    'ConnectedDisplays' is a bitmask attribute.
    'ConnectedDisplays' is a read-only attribute.
    'ConnectedDisplays' can use the following target types: X Screen, GPU.

  Attribute 'EnabledDisplays' (sharan-Aspire-5738:0[gpu:0]): 0x00010000.
    'EnabledDisplays' is a bitmask attribute.
    'EnabledDisplays' is a read-only attribute.
    'EnabledDisplays' can use the following target types: X Screen, GPU.

  Attribute 'NotebookInternalLCD' (sharan-Aspire-5738:0[gpu:0]):
  0x00010000.
    'NotebookInternalLCD' is a bitmask attribute.
    'NotebookInternalLCD' is a read-only attribute.
    'NotebookInternalLCD' can use the following target types: X Screen,
    GPU.

  Attribute 'Depth30Allowed' (sharan-Aspire-5738:0[gpu:0]): 0.
    'Depth30Allowed' is a boolean attribute; valid values are: 1 (on/true)
    and 0 (off/false).
    'Depth30Allowed' is a read-only attribute.
    'Depth30Allowed' can use the following target types: X Screen, GPU.

  Attribute 'NoScanout' (sharan-Aspire-5738:0[gpu:0]): 0.
    'NoScanout' is a boolean attribute; valid values are: 1 (on/true) and 0
    (off/false).
    'NoScanout' is a read-only attribute.
    'NoScanout' can use the following target types: X Screen, GPU.

  Attribute 'SliMosaicModeAvailable' (sharan-Aspire-5738:0[gpu:0]): 0.
    'SliMosaicModeAvailable' is a boolean attribute; valid values are: 1
    (on/true) and 0 (off/false).
    'SliMosaicModeAvailable' is a read-only attribute.
    'SliMosaicModeAvailable' can use the following target types: X Screen,
    GPU, VCS.

  Attribute 'BusType' (sharan-Aspire-5738:0[gpu:0]): 2.
    The valid values for 'BusType' are in the range 0 - 3 (inclusive).
    'BusType' is a read-only attribute.
    'BusType' can use the following target types: X Screen, GPU, SDI Input
    Device.

  Attribute 'PCIEMaxLinkSpeed' (sharan-Aspire-5738:0[gpu:0]): 2500.
    'PCIEMaxLinkSpeed' is an integer attribute.
    'PCIEMaxLinkSpeed' is a read-only attribute.
    'PCIEMaxLinkSpeed' can use the following target types: X Screen, GPU,
    SDI Input Device.

  Attribute 'VideoRam' (sharan-Aspire-5738:0[gpu:0]): 524288.
    'VideoRam' is an integer attribute.
    'VideoRam' is a read-only attribute.
    'VideoRam' can use the following target types: X Screen, GPU.

  Attribute 'Irq' (sharan-Aspire-5738:0[gpu:0]): 16.
    'Irq' is an integer attribute.
    'Irq' is a read-only attribute.
    'Irq' can use the following target types: X Screen, GPU, SDI Input
    Device.

  Attribute 'CUDACores' (sharan-Aspire-5738:0[gpu:0]): 8.
    'CUDACores' is an integer attribute.
    'CUDACores' is a read-only attribute.
    'CUDACores' can use the following target types: X Screen, GPU.

  Attribute 'GPUMemoryInterface' (sharan-Aspire-5738:0[gpu:0]): 64.
    'GPUMemoryInterface' is an integer attribute.
    'GPUMemoryInterface' is a read-only attribute.
    'GPUMemoryInterface' can use the following target types: X Screen,
    GPU.

  Attribute 'GPUCoreTemp' (sharan-Aspire-5738:0[gpu:0]): 54.
    'GPUCoreTemp' is an integer attribute.
    'GPUCoreTemp' is a read-only attribute.
    'GPUCoreTemp' can use the following target types: X Screen, GPU.

  Attribute 'GPU2DClockFreqs' (sharan-Aspire-5738:0[gpu:0]): 169,100.
    The valid values for 'GPU2DClockFreqs' are in the ranges 42 - 338, 25 -
    1416 (inclusive).
    'GPU2DClockFreqs' can use the following target types: X Screen, GPU.

  Attribute 'GPU3DClockFreqs' (sharan-Aspire-5738:0[gpu:0]): 640,500.
    The valid values for 'GPU3DClockFreqs' are in the ranges 160 - 1280,
    125 - 1416 (inclusive).
    'GPU3DClockFreqs' can use the following target types: X Screen, GPU.

  Attribute 'GPUDefault2DClockFreqs' (sharan-Aspire-5738:0[gpu:0]):
  169,100.
    'GPUDefault2DClockFreqs' is a packed integer attribute.
    'GPUDefault2DClockFreqs' is a read-only attribute.
    'GPUDefault2DClockFreqs' can use the following target types: X Screen,
    GPU.

  Attribute 'GPUDefault3DClockFreqs' (sharan-Aspire-5738:0[gpu:0]):
  640,500.
    'GPUDefault3DClockFreqs' is a packed integer attribute.
    'GPUDefault3DClockFreqs' is a read-only attribute.
    'GPUDefault3DClockFreqs' can use the following target types: X Screen,
    GPU.

  Attribute 'GPUCurrentClockFreqs' (sharan-Aspire-5738:0[gpu:0]): 640,500.
    'GPUCurrentClockFreqs' is a packed integer attribute.
    'GPUCurrentClockFreqs' is a read-only attribute.
    'GPUCurrentClockFreqs' can use the following target types: X Screen,
    GPU.

  Attribute 'GPUCurrentProcessorClockFreqs' (sharan-Aspire-5738:0[gpu:0]):
  1600.
    The valid values for 'GPUCurrentProcessorClockFreqs' are in the range
    400 - 3200 (inclusive).
    'GPUCurrentProcessorClockFreqs' can use the following target types: X
    Screen, GPU.

  Attribute 'GPUCurrentClockFreqsString' (sharan-Aspire-5738:0[gpu:0]):
  nvclock=640, memclock=500, processorclock=1600 
    'GPUCurrentClockFreqsString' is a string attribute.
    'GPUCurrentClockFreqsString' can use the following target types: X
    Screen, GPU.

  Attribute 'BusRate' (sharan-Aspire-5738:0[gpu:0]): 16.
    The valid values for 'BusRate' are in the range 1 - 16 (inclusive).
    'BusRate' is a read-only attribute.
    'BusRate' can use the following target types: X Screen, GPU, SDI Input
    Device.

  Attribute 'PCIDomain' (sharan-Aspire-5738:0[gpu:0]): 0.
    'PCIDomain' is an integer attribute.
    'PCIDomain' is a read-only attribute.
    'PCIDomain' can use the following target types: GPU, SDI Input Device.

  Attribute 'PCIBus' (sharan-Aspire-5738:0[gpu:0]): 1.
    'PCIBus' is an integer attribute.
    'PCIBus' is a read-only attribute.
    'PCIBus' can use the following target types: GPU, SDI Input Device.

  Attribute 'PCIDevice' (sharan-Aspire-5738:0[gpu:0]): 0.
    'PCIDevice' is an integer attribute.
    'PCIDevice' is a read-only attribute.
    'PCIDevice' can use the following target types: GPU, SDI Input Device.

  Attribute 'PCIFunc' (sharan-Aspire-5738:0[gpu:0]): 0.
    'PCIFunc' is an integer attribute.
    'PCIFunc' is a read-only attribute.
    'PCIFunc' can use the following target types: GPU, SDI Input Device.

  Attribute 'PCIID' (sharan-Aspire-5738:0[gpu:0]): 4318,1772.
    'PCIID' is a packed integer attribute.
    'PCIID' is a read-only attribute.
    'PCIID' can use the following target types: GPU, SDI Input Device.

  Attribute 'PCIEGen' (sharan-Aspire-5738:0[gpu:0]): 1.
    'PCIEGen' is an integer attribute.
    'PCIEGen' is a read-only attribute.
    'PCIEGen' can use the following target types: X Screen, GPU, SDI Input
    Device.

  Attribute 'GPUPowerSource' (sharan-Aspire-5738:0[gpu:0]): 0.
    'GPUPowerSource' is an integer attribute.
    'GPUPowerSource' is a read-only attribute.
    'GPUPowerSource' can use the following target types: X Screen, GPU.

  Attribute 'GPUCurrentPerfMode' (sharan-Aspire-5738:0[gpu:0]): 1.
    'GPUCurrentPerfMode' is an integer attribute.
    'GPUCurrentPerfMode' is a read-only attribute.
    'GPUCurrentPerfMode' can use the following target types: X Screen,
    GPU.

  Attribute 'GPUCurrentPerfLevel' (sharan-Aspire-5738:0[gpu:0]): 3.
    'GPUCurrentPerfLevel' is an integer attribute.
    'GPUCurrentPerfLevel' is a read-only attribute.
    'GPUCurrentPerfLevel' can use the following target types: X Screen,
    GPU.

  Attribute 'GPUAdaptiveClockState' (sharan-Aspire-5738:0[gpu:0]): 1.
    'GPUAdaptiveClockState' is a boolean attribute; valid values are: 1
    (on/true) and 0 (off/false).
    'GPUAdaptiveClockState' is a read-only attribute.
    'GPUAdaptiveClockState' can use the following target types: X Screen,
    GPU.

  Attribute 'GPUPerfModes' (sharan-Aspire-5738:0[gpu:0]): perf=0,
  nvclock=169, memclock=100, processorclock=338 ; perf=1, nvclock=275,
  memclock=250, processorclock=550 ; perf=2, nvclock=500, memclock=400,
  processorclock=1000 ; perf=3, nvclock=640, memclock=500,
  processorclock=1600 
    'GPUPerfModes' is a string attribute.
    'GPUPerfModes' is a read-only attribute.
    'GPUPerfModes' can use the following target types: X Screen, GPU.

  Attribute 'GPUPowerMizerMode' (sharan-Aspire-5738:0[gpu:0]): 0.
    'GPUPowerMizerMode' is an integer attribute.
    'GPUPowerMizerMode' can use the following target types: GPU.

  Attribute 'ECCSupported' (sharan-Aspire-5738:0[gpu:0]): 0.
    'ECCSupported' is a boolean attribute; valid values are: 1 (on/true)
    and 0 (off/false).
    'ECCSupported' is a read-only attribute.
    'ECCSupported' can use the following target types: X Screen, GPU.

  Attribute 'ECCConfigurationSupported' (sharan-Aspire-5738:0[gpu:0]): 0.
    'ECCConfigurationSupported' is a boolean attribute; valid values are: 1
    (on/true) and 0 (off/false).
    'ECCConfigurationSupported' is a read-only attribute.
    'ECCConfigurationSupported' can use the following target types: X
    Screen, GPU.

  Attribute 'IsGvoDisplay' (sharan-Aspire-5738:0[gpu:0]; display device:
  DFP-0): 0.
    'IsGvoDisplay' is a boolean attribute; valid values are: 1 (on/true)
    and 0 (off/false).
    'IsGvoDisplay' is a read-only attribute.
    'IsGvoDisplay' is display device specific.
    'IsGvoDisplay' can use the following target types: X Screen, GPU.

  Attribute 'Dithering' (sharan-Aspire-5738:0[gpu:0]; display device:
  DFP-0): 0.
    'Dithering' is an integer attribute.
    'Dithering' is display device specific.
    'Dithering' can use the following target types: GPU.

  Attribute 'CurrentDithering' (sharan-Aspire-5738:0[gpu:0]; display
  device: DFP-0): 1.
    'CurrentDithering' is a boolean attribute; valid values are: 1
    (on/true) and 0 (off/false).
    'CurrentDithering' is a read-only attribute.
    'CurrentDithering' is display device specific.
    'CurrentDithering' can use the following target types: GPU.

  Attribute 'DitheringMode' (sharan-Aspire-5738:0[gpu:0]; display device:
  DFP-0): 0.
    Valid values for 'DitheringMode' are: 0, 1 and 2.
    'DitheringMode' is display device specific.
    'DitheringMode' can use the following target types: GPU.

  Attribute 'CurrentDitheringMode' (sharan-Aspire-5738:0[gpu:0]; display
  device: DFP-0): 1.
    'CurrentDitheringMode' is an integer attribute.
    'CurrentDitheringMode' is a read-only attribute.
    'CurrentDitheringMode' is display device specific.
    'CurrentDitheringMode' can use the following target types: GPU.

  Attribute 'DitheringDepth' (sharan-Aspire-5738:0[gpu:0]; display device:
  DFP-0): 0.
    'DitheringDepth' is an integer attribute.
    'DitheringDepth' is display device specific.
    'DitheringDepth' can use the following target types: GPU.

  Attribute 'CurrentDitheringDepth' (sharan-Aspire-5738:0[gpu:0]; display
  device: DFP-0): 1.
    'CurrentDitheringDepth' is an integer attribute.
    'CurrentDitheringDepth' is a read-only attribute.
    'CurrentDitheringDepth' is display device specific.
    'CurrentDitheringDepth' can use the following target types: GPU.

  Attribute 'DigitalVibrance' (sharan-Aspire-5738:0[gpu:0]; display device:
  DFP-0): 0.
    The valid values for 'DigitalVibrance' are in the range -1024 - 1023
    (inclusive).
    'DigitalVibrance' is display device specific.
    'DigitalVibrance' can use the following target types: X Screen, GPU.

  Attribute 'FrontendResolution' (sharan-Aspire-5738:0[gpu:0]; display
  device: DFP-0): 1366,768.
    'FrontendResolution' is a packed integer attribute.
    'FrontendResolution' is a read-only attribute.
    'FrontendResolution' is display device specific.
    'FrontendResolution' can use the following target types: X Screen,
    GPU.

  Attribute 'BackendResolution' (sharan-Aspire-5738:0[gpu:0]; display
  device: DFP-0): 1366,768.
    'BackendResolution' is a packed integer attribute.
    'BackendResolution' is a read-only attribute.
    'BackendResolution' is display device specific.
    'BackendResolution' can use the following target types: X Screen, GPU.

  Attribute 'FlatpanelNativeResolution' (sharan-Aspire-5738:0[gpu:0];
  display device: DFP-0): 1366,768.
    'FlatpanelNativeResolution' is a packed integer attribute.
    'FlatpanelNativeResolution' is a read-only attribute.
    'FlatpanelNativeResolution' is display device specific.
    'FlatpanelNativeResolution' can use the following target types: X
    Screen, GPU.

  Attribute 'FlatpanelBestFitResolution' (sharan-Aspire-5738:0[gpu:0];
  display device: DFP-0): 1366,768.
    'FlatpanelBestFitResolution' is a packed integer attribute.
    'FlatpanelBestFitResolution' is a read-only attribute.
    'FlatpanelBestFitResolution' is display device specific.
    'FlatpanelBestFitResolution' can use the following target types: X
    Screen, GPU.

  Attribute 'DFPScalingActive' (sharan-Aspire-5738:0[gpu:0]; display
  device: DFP-0): 0.
    'DFPScalingActive' is a boolean attribute; valid values are: 1
    (on/true) and 0 (off/false).
    'DFPScalingActive' is a read-only attribute.
    'DFPScalingActive' is display device specific.
    'DFPScalingActive' can use the following target types: X Screen, GPU.

  Attribute 'GPUScaling' (sharan-Aspire-5738:0[gpu:0]; display device:
  DFP-0): 2,1.
    Valid values for 'GPUScaling' are: [1 and 2], [1, 2 and 3].
    'GPUScaling' is display device specific.
    'GPUScaling' can use the following target types: X Screen, GPU.

  Attribute 'GPUScalingDefaultTarget' (sharan-Aspire-5738:0[gpu:0]; display
  device: DFP-0): 2.
    'GPUScalingDefaultTarget' is an integer attribute.
    'GPUScalingDefaultTarget' is a read-only attribute.
    'GPUScalingDefaultTarget' is display device specific.
    'GPUScalingDefaultTarget' can use the following target types: X Screen,
    GPU.

  Attribute 'GPUScalingDefaultMethod' (sharan-Aspire-5738:0[gpu:0]; display
  device: DFP-0): 1.
    'GPUScalingDefaultMethod' is an integer attribute.
    'GPUScalingDefaultMethod' is a read-only attribute.
    'GPUScalingDefaultMethod' is display device specific.
    'GPUScalingDefaultMethod' can use the following target types: X Screen,
    GPU.

  Attribute 'GPUScalingActive' (sharan-Aspire-5738:0[gpu:0]; display
  device: DFP-0): 0.
    'GPUScalingActive' is a boolean attribute; valid values are: 1
    (on/true) and 0 (off/false).
    'GPUScalingActive' is a read-only attribute.
    'GPUScalingActive' is display device specific.
    'GPUScalingActive' can use the following target types: X Screen, GPU.

  Attribute 'RefreshRate' (sharan-Aspire-5738:0[gpu:0]; display device:
  DFP-0): 59.97 Hz.
    'RefreshRate' is an integer attribute.
    'RefreshRate' is a read-only attribute.
    'RefreshRate' is display device specific.
    'RefreshRate' can use the following target types: X Screen, GPU.

  Attribute 'RefreshRate3' (sharan-Aspire-5738:0[gpu:0]; display device:
  DFP-0): 59.973 Hz.
    'RefreshRate3' is an integer attribute.
    'RefreshRate3' is a read-only attribute.
    'RefreshRate3' is display device specific.
    'RefreshRate3' can use the following target types: X Screen, GPU.

  Attribute 'OverscanCompensation' (sharan-Aspire-5738:0[gpu:0]; display
  device: DFP-0): 0.
    The valid values for 'OverscanCompensation' are in the range 0 - 200
    (inclusive).
    'OverscanCompensation' is display device specific.
    'OverscanCompensation' can use the following target types: X Screen,
    GPU.

  Attribute 'ColorSpace' (sharan-Aspire-5738:0[gpu:0]; display device:
  DFP-0): 0.
    Valid values for 'ColorSpace' are: 0.
    'ColorSpace' is display device specific.
    'ColorSpace' can use the following target types: X Screen, GPU.

  Attribute 'ColorRange' (sharan-Aspire-5738:0[gpu:0]; display device:
  DFP-0): 0.
    Valid values for 'ColorRange' are: 0 and 1.
    'ColorRange' is display device specific.
    'ColorRange' can use the following target types: X Screen, GPU.

  Attribute 'SynchronousPaletteUpdates' (sharan-Aspire-5738:0[gpu:0];
  display device: DFP-0): 0.
    'SynchronousPaletteUpdates' is a boolean attribute; valid values are: 1
    (on/true) and 0 (off/false).
    'SynchronousPaletteUpdates' is display device specific.
    'SynchronousPaletteUpdates' can use the following target types: GPU.

Attributes queryable via sharan-Aspire-5738:0[thermalsensor:0]:

  Attribute 'ThermalSensorReading' (sharan-Aspire-5738:0[thermalsensor:0]):
  54.
    The valid values for 'ThermalSensorReading' are in the range 0 - 127
    (inclusive).
    'ThermalSensorReading' is a read-only attribute.
    'ThermalSensorReading' can use the following target types: Thermal
    Sensor.

  Attribute 'ThermalSensorProvider'
  (sharan-Aspire-5738:0[thermalsensor:0]): 1.
    'ThermalSensorProvider' is an integer attribute.
    'ThermalSensorProvider' is a read-only attribute.
    'ThermalSensorProvider' can use the following target types: Thermal
    Sensor.

  Attribute 'ThermalSensorTarget' (sharan-Aspire-5738:0[thermalsensor:0]):
  1.
    'ThermalSensorTarget' is an integer attribute.
    'ThermalSensorTarget' is a read-only attribute.
    'ThermalSensorTarget' can use the following target types: Thermal
    Sensor.

____________________________________________

*** /proc/cmdline
*** ls: -r--r--r-- 1 root root 0 2011-07-14 14:11:58.591985704 +0530 /proc/cmdline
BOOT_IMAGE=/vmlinuz-2.6.38-8-generic root=UUID=4829be89-f413-4aaa-bfc5-b14e8c8ebebf ro quiet splash vt.handoff=7

____________________________________________

*** /proc/cpuinfo
*** ls: -r--r--r-- 1 root root 0 2011-07-14 14:11:58.595985729 +0530 /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     T6500  @ 2.10GHz
stepping	: 10
cpu MHz		: 2100.000
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm dts
bogomips	: 4189.09
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     T6500  @ 2.10GHz
stepping	: 10
cpu MHz		: 1200.000
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm dts
bogomips	: 4189.46
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:


____________________________________________

*** /proc/interrupts
*** ls: -r--r--r-- 1 root root 0 2011-07-14 14:11:58.599985745 +0530 /proc/interrupts
           CPU0       CPU1       
  0:     272285     424235   IO-APIC-edge      timer
  1:        852        873   IO-APIC-edge      i8042
  8:          0          1   IO-APIC-edge      rtc0
  9:       8472        267   IO-APIC-fasteoi   acpi
 12:     357428        326   IO-APIC-edge      i8042
 16:      27996      41902   IO-APIC-fasteoi   nvidia
 17:          0          0   IO-APIC-fasteoi   uhci_hcd:usb6
 18:          0          0   IO-APIC-fasteoi   uhci_hcd:usb7, uhci_hcd:usb8
 20:         12         13   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb3, uhci_hcd:usb4
 23:         46         42   IO-APIC-fasteoi   ehci_hcd:usb2, uhci_hcd:usb5
 45:      18217      18122   PCI-MSI-edge      ahci
 46:        314        319   PCI-MSI-edge      hda_intel
 47:      59981       1257   PCI-MSI-edge      iwlagn
 48:          2          2   PCI-MSI-edge      eth0
NMI:          0          0   Non-maskable interrupts
LOC:     606948     565953   Local timer interrupts
SPU:          0          0   Spurious interrupts
PMI:          0          0   Performance monitoring interrupts
IWI:          0          0   IRQ work interrupts
RES:      93753      95105   Rescheduling interrupts
CAL:       1607       4967   Function call interrupts
TLB:      25227      25864   TLB shootdowns
TRM:        160        160   Thermal event interrupts
THR:          0          0   Threshold APIC interrupts
MCE:          0          0   Machine check exceptions
MCP:          4          5   Machine check polls
ERR:          1
MIS:          0

____________________________________________

*** /proc/meminfo
*** ls: -r--r--r-- 1 root root 0 2011-07-14 14:11:58.603985764 +0530 /proc/meminfo
MemTotal:        3090904 kB
MemFree:         2053792 kB
Buffers:           62772 kB
Cached:           456652 kB
SwapCached:            0 kB
Active:           549724 kB
Inactive:         373512 kB
Active(anon):     404868 kB
Inactive(anon):     3532 kB
Active(file):     144856 kB
Inactive(file):   369980 kB
Unevictable:          64 kB
Mlocked:              64 kB
HighTotal:       2231628 kB
HighFree:        1348872 kB
LowTotal:         859276 kB
LowFree:          704920 kB
SwapTotal:       8821756 kB
SwapFree:        8821756 kB
Dirty:                 0 kB
Writeback:             0 kB
AnonPages:        403928 kB
Mapped:           117344 kB
Shmem:              4584 kB
Slab:              45152 kB
SReclaimable:      30364 kB
SUnreclaim:        14788 kB
KernelStack:        2808 kB
PageTables:         6552 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:    10367208 kB
Committed_AS:    1976244 kB
VmallocTotal:     122880 kB
VmallocUsed:       74192 kB
VmallocChunk:      34300 kB
HardwareCorrupted:     0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       4096 kB
DirectMap4k:       61432 kB
DirectMap4M:      847872 kB

____________________________________________

*** /proc/modules
*** ls: -r--r--r-- 1 root root 0 2011-07-14 14:11:58.607985787 +0530 /proc/modules
parport_pc 32111 0 - Live 0xf848e000
ppdev 12849 0 - Live 0xf8479000
vesafb 13449 1 - Live 0xf8412000
binfmt_misc 13213 1 - Live 0xf8359000
joydev 17322 0 - Live 0xf837a000
arc4 12473 2 - Live 0xf8353000
iwlagn 284569 0 - Live 0xf841b000
iwlcore 148965 1 iwlagn, Live 0xf8383000
mac80211 257001 2 iwlagn,iwlcore, Live 0xf8e58000
nvidia 9766978 43 - Live 0xf8e99000 (P)
snd_hda_codec_hdmi 27479 1 - Live 0xf992c000
snd_hda_codec_realtek 255820 1 - Live 0xf9975000
snd_hda_intel 24140 2 - Live 0xf8dfb000
snd_hda_codec 90901 3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel, Live 0xf98ef000
snd_hwdep 13274 1 snd_hda_codec, Live 0xf80a2000
snd_pcm 80244 3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec, Live 0xf990b000
snd_seq_midi 13132 0 - Live 0xf8d46000
snd_rawmidi 25269 1 snd_seq_midi, Live 0xf8dcd000
snd_seq_midi_event 14475 1 snd_seq_midi, Live 0xf805b000
snd_seq 51291 2 snd_seq_midi,snd_seq_midi_event, Live 0xf98e0000
acer_wmi 23123 0 - Live 0xf8dd7000
sparse_keymap 13666 1 acer_wmi, Live 0xf8d61000
snd_timer 28659 2 snd_pcm,snd_seq, Live 0xf8d51000
snd_seq_device 14110 3 snd_seq_midi,snd_rawmidi,snd_seq, Live 0xf82e4000
uvcvideo 66851 0 - Live 0xf8da6000
videodev 75143 1 uvcvideo, Live 0xf8d91000
snd 55295 14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device, Live 0xf8deb000
cfg80211 156212 3 iwlagn,iwlcore,mac80211, Live 0xf8d68000
psmouse 73312 0 - Live 0xf8db9000
serio_raw 12990 0 - Live 0xf8029000
soundcore 12600 1 snd, Live 0xf8055000
snd_page_alloc 14073 2 snd_hda_intel,snd_pcm, Live 0xf82ea000
video 18951 0 - Live 0xf80a9000
lp 13349 0 - Live 0xf8035000
parport 36746 3 parport_pc,ppdev,lp, Live 0xf80b0000
usb_storage 43946 0 - Live 0xf80ba000
uas 17676 0 - Live 0xf803c000
ahci 21591 3 - Live 0xf804d000
libahci 25548 1 ahci, Live 0xf8099000
tg3 131476 0 - Live 0xf8076000

____________________________________________

*** /proc/version
*** ls: -r--r--r-- 1 root root 0 2011-07-14 14:11:58.611985800 +0530 /proc/version
Linux version 2.6.38-8-generic (buildd@vernadsky) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011

____________________________________________

*** /proc/pci does not exist

____________________________________________

*** /proc/iomem
*** ls: -r--r--r-- 1 root root 0 2011-07-14 14:11:58.619985846 +0530 /proc/iomem
00000000-0000ffff : reserved
00010000-0009d3ff : System RAM
0009d400-0009ffff : reserved
000a0000-000bffff : PCI Bus 0000:00
  000a0000-000bffff : Video RAM area
000c0000-000ce7ff : Video ROM
000ce800-000cf7ff : Adapter ROM
000d0000-000d3fff : reserved
000d4000-000d7fff : PCI Bus 0000:00
000d8000-000dbfff : PCI Bus 0000:00
000dc000-000dffff : PCI Bus 0000:00
000e0000-000e3fff : PCI Bus 0000:00
000e4000-000fffff : reserved
  000f0000-000fffff : System ROM
00100000-bf8a0fff : System RAM
  01000000-015112a0 : Kernel code
  015112a1-0178c47f : Kernel data
  01841000-0191afff : Kernel bss
bf8a1000-bf8a6fff : reserved
bf8a7000-bf9cefff : System RAM
bf9cf000-bfa0efff : reserved
bfa0f000-bfb08fff : System RAM
bfb09000-bfd0efff : reserved
bfd0f000-bfd18fff : System RAM
bfd19000-bfd1efff : reserved
bfd1f000-bfd5efff : System RAM
bfd5f000-bfd9efff : ACPI Non-volatile Storage
bfd9f000-bfde1fff : System RAM
bfde2000-bfdfefff : ACPI Tables
bfdff000-bfdfffff : System RAM
bfe00000-bfffffff : RAM buffer
c0000000-dfffffff : PCI Bus 0000:00
  c0000000-c01fffff : PCI Bus 0000:02
  c0200000-c03fffff : PCI Bus 0000:03
  c0400000-c05fffff : PCI Bus 0000:03
  c0600000-c07fffff : PCI Bus 0000:04
  c0800000-c08000ff : 0000:00:1f.3
  d0000000-dfffffff : PCI Bus 0000:01
    d0000000-dfffffff : 0000:01:00.0
e0000000-efffffff : PCI MMCONFIG 0000 [bus 00-ff]
  e0000000-efffffff : pnp 00:09
f0000000-febfffff : PCI Bus 0000:00
  f0000000-f2ffffff : PCI Bus 0000:01
    f0000000-f1ffffff : 0000:01:00.0
      f1000000-f112ffff : vesafb
    f2000000-f2ffffff : 0000:01:00.0
      f2000000-f2ffffff : nvidia
  f3000000-f30fffff : PCI Bus 0000:02
    f3000000-f300ffff : 0000:02:00.0
      f3000000-f300ffff : tg3
  f3100000-f31fffff : PCI Bus 0000:04
    f3100000-f3101fff : 0000:04:00.0
      f3100000-f3101fff : iwlagn
  f3400000-f3403fff : 0000:00:1b.0
    f3400000-f3403fff : ICH HD audio
  f3404000-f34047ff : 0000:00:1f.2
    f3404000-f34047ff : ahci
  f3404800-f3404bff : 0000:00:1a.7
    f3404800-f3404bff : ehci_hcd
  f3404c00-f3404fff : 0000:00:1d.7
    f3404c00-f3404fff : ehci_hcd
  f4000000-f5ffffff : PCI Bus 0000:05
  f6000000-f7ffffff : PCI Bus 0000:05
fec00000-fec003ff : IOAPIC 0
fed00000-fed003ff : HPET 0
  fed00000-fed003ff : pnp 00:05
fed10000-fed13fff : pnp 00:09
fed18000-fed18fff : pnp 00:09
fed19000-fed19fff : pnp 00:09
fed1c000-fed1ffff : pnp 00:09
fed20000-fed3ffff : pnp 00:09
fee00000-fee00fff : Local APIC
ff800000-ff800fff : pnp 00:07

____________________________________________

*** /proc/mtrr
*** ls: -rw-r--r-- 1 root root 0 2011-07-14 13:52:17.314128070 +0530 /proc/mtrr
reg00: base=0x000000000 (    0MB), size= 2048MB, count=1: write-back
reg01: base=0x080000000 ( 2048MB), size= 1024MB, count=1: write-back
reg02: base=0x100000000 ( 4096MB), size= 1024MB, count=1: write-back

____________________________________________

*** /proc/driver/nvidia/version
*** ls: -r--r--r-- 1 root root 0 2011-07-14 14:11:58.627985886 +0530 /proc/driver/nvidia/version
NVRM version: NVIDIA UNIX x86 Kernel Module  270.41.06  Mon Apr 18 14:54:25 PDT 2011
GCC version:  gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4) 

____________________________________________

*** /proc/driver/nvidia/gpus/0/information
*** ls: -r--r--r-- 1 root root 0 2011-07-14 14:11:58.631985901 +0530 /proc/driver/nvidia/gpus/0/information
Model: 		 GeForce G 105M
IRQ:   		 16
Video BIOS: 	 62.98.5a.00.18
Card Type: 	 PCI-E
DMA Size: 	 40 bits
DMA Mask: 	 0xffffffffff
Bus Location: 	 0000:01.00.0

____________________________________________

*** /proc/driver/nvidia/gpus/0/registry
*** ls: -rw-r--r-- 1 root root 0 2011-07-14 14:11:58.635985926 +0530 /proc/driver/nvidia/gpus/0/registry
Binary: ""

____________________________________________

*** /proc/driver/nvidia/warnings/README
*** ls: -r--r--r-- 1 root root 0 2011-07-14 14:11:58.647985986 +0530 /proc/driver/nvidia/warnings/README
The NVIDIA graphics driver tries to detect potential problems
with the host system and warns about them using the system's
logging mechanisms. Important warning message are also logged
to dedicated text files in this directory.

____________________________________________

*** /proc/driver/nvidia/params
*** ls: -r--r--r-- 1 root root 0 2011-07-14 14:11:58.651986002 +0530 /proc/driver/nvidia/params
EnableVia4x: 0
EnableALiAGP: 0
NvAGP: 3
ReqAGPRate: 15
EnableAGPSBA: 0
EnableAGPFW: 0
Mobile: 4294967295
ResmanDebugLevel: 4294967295
RmLogonRC: 1
ModifyDeviceFiles: 1
DeviceFileUID: 0
DeviceFileGID: 0
DeviceFileMode: 438
RemapLimit: 0
UpdateMemoryTypes: 4294967295
InitializeSystemMemoryAllocations: 1
UseVBios: 1
RMEdgeIntrCheck: 1
UsePageAttributeTable: 4294967295
EnableMSI: 0
MapRegistersEarly: 0
RegisterForACPIEvents: 1
RegistryDwords: ""
RmMsg: ""

____________________________________________

*** /proc/driver/nvidia/registry
*** ls: -rw-r--r-- 1 root root 0 2011-07-14 14:11:58.659986042 +0530 /proc/driver/nvidia/registry
Binary: ""

____________________________________________

*** /proc/asound/cards
*** ls: -r--r--r-- 1 root root 0 2011-07-14 14:11:58.667986079 +0530 /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf3400000 irq 46

____________________________________________

*** /proc/asound/pcm
*** ls: -r--r--r-- 1 root root 0 2011-07-14 14:11:58.675986125 +0530 /proc/asound/pcm
00-00: ALC888 Analog : ALC888 Analog : playback 1 : capture 1
00-01: ALC888 Digital : ALC888 Digital : playback 1
00-02: ALC888 Analog : ALC888 Analog : capture 1
00-03: HDMI 0 : HDMI 0 : playback 1

____________________________________________

*** /proc/asound/modules
*** ls: -r--r--r-- 1 root root 0 2011-07-14 14:11:58.679986140 +0530 /proc/asound/modules
 0 snd_hda_intel

____________________________________________

*** /proc/asound/devices
*** ls: -r--r--r-- 1 root root 0 2011-07-14 14:11:58.687986179 +0530 /proc/asound/devices
  1:        : sequencer
  2: [ 0- 3]: digital audio playback
  3: [ 0- 2]: digital audio capture
  4: [ 0- 1]: digital audio playback
  5: [ 0- 0]: digital audio playback
  6: [ 0- 0]: digital audio capture
  7: [ 0- 2]: hardware dependent
  8: [ 0- 1]: hardware dependent
  9: [ 0- 0]: hardware dependent
 10: [ 0]   : control
 33:        : timer

____________________________________________

*** /proc/asound/version
*** ls: -r--r--r-- 1 root root 0 2011-07-14 14:11:58.691986203 +0530 /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.

____________________________________________

*** /proc/asound/timers
*** ls: -r--r--r-- 1 root root 0 2011-07-14 14:11:58.699986242 +0530 /proc/asound/timers
G0: system timer : 4000.000us (10000000 ticks)
P0-0-0: PCM playback 0-0-0 : SLAVE
P0-0-1: PCM capture 0-0-1 : SLAVE
P0-1-0: PCM playback 0-1-0 : SLAVE
P0-2-1: PCM capture 0-2-1 : SLAVE
P0-3-0: PCM playback 0-3-0 : SLAVE

____________________________________________

*** /proc/asound/hwdep
*** ls: -r--r--r-- 1 root root 0 2011-07-14 14:11:58.707986281 +0530 /proc/asound/hwdep
00-02: HDA Codec 2
00-01: HDA Codec 1
00-00: HDA Codec 0

____________________________________________

*** /proc/asound/card0/codec#0
*** ls: -r--r--r-- 1 root root 0 2011-07-14 14:11:58.711986296 +0530 /proc/asound/card0/codec#0
Codec: Realtek ALC888
Address: 0
AFG Function Id: 0x1 (unsol 1)
Vendor Id: 0x10ec0888
Subsystem Id: 0x10250205
Revision Id: 0x100202
No Modem Function Group found
Default PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=2, o=0, i=0, unsolicited=1, wake=1
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x02 [Audio Output] wcaps 0x411: Stereo
  Device: name="ALC888 Analog", type="Audio", device=0
  Converter: stream=5, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x03 [Audio Output] wcaps 0x411: Stereo
  Converter: stream=5, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x04 [Audio Output] wcaps 0x411: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x05 [Audio Output] wcaps 0x411: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x06 [Audio Output] wcaps 0x611: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="IEC958 Default PCM Playback Switch", index=0, device=0
  Device: name="ALC888 Digital", type="SPDIF", device=1
  Converter: stream=5, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x07 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x08 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Control: name="Capture Switch", index=0, device=0
  Control: name="Capture Volume", index=0, device=0
  Device: name="ALC888 Analog", type="Audio", device=0
  Amp-In caps: ofs=0x0b, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x13 0x13]
  Converter: stream=1, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x23
Node 0x09 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Control: name="Capture Switch", index=1, device=0
  Control: name="Capture Volume", index=1, device=0
  Device: name="ALC888 Analog", type="Audio", device=2
  Amp-In caps: ofs=0x0b, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x00 0x00]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x22
Node 0x0a [Audio Input] wcaps 0x100711: Stereo Digital
  Converter: stream=0, channel=0
  SDI-Select: 0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x1f
Node 0x0b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Internal Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Control: name="Internal Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Control: name="Line Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Control: name="Line Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Control: name="Beep Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=5, ofs=0
  Control: name="Beep Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=5, ofs=0
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 10
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17
Node 0x0c [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Control: name="Speaker Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Speaker Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x19 0x19]
  Connection: 2
     0x02 0x0b
Node 0x0d [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Control: name="Headphone Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Headphone Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x19 0x19]
  Connection: 2
     0x03 0x0b
Node 0x0e [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x04 0x0b
Node 0x0f [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x05 0x0b
Node 0x10 [Audio Output] wcaps 0x611: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x11 [Pin Complex] wcaps 0x400780: Mono Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x10
Node 0x12 [Pin Complex] wcaps 0x400401: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x13 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x14 [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0001003e: IN OUT HP EAPD Detect Trigger
  EAPD 0x0:
  Pin Default 0x99130110: [Fixed] Speaker at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x15 [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0001003e: IN OUT HP EAPD Detect Trigger
  EAPD 0x0:
  Pin Default 0x0321101f: [Jack] HP Out at Ext Left
    Conn = 1/8, Color = Black
    DefAssociation = 0x1, Sequence = 0xf
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=04, enabled=1
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c 0x0d* 0x0e 0x0f 0x26
Node 0x16 [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00000036: IN OUT Detect Trigger
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c 0x0d 0x0e* 0x0f 0x26
Node 0x17 [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00000036: IN OUT Detect Trigger
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c 0x0d 0x0e 0x0f* 0x26
Node 0x18 [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Control: name="Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x03a19c30: [Jack] Mic at Ext Left
    Conn = 1/8, Color = Pink
    DefAssociation = 0x3, Sequence = 0x0
  Pin-ctls: 0x21: IN VREF_50
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x19 [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Control: name="Internal Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x99a30931: [Fixed] Mic at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0x3, Sequence = 0x1
    Misc = NO_PRESENCE
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1a [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x0381343f: [Jack] Line In at Ext Left
    Conn = 1/8, Color = Blue
    DefAssociation = 0x3, Sequence = 0xf
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1b [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1c [Pin Complex] wcaps 0x400481: Stereo
  Pincap 0x00000024: IN Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x1d [Pin Complex] wcaps 0x400400: Mono
  Pincap 0x00000020: IN
  Pin Default 0x4016852d: [N/A] Speaker at Ext N/A
    Conn = Digital, Color = Purple
    DefAssociation = 0x2, Sequence = 0xd
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x1e [Pin Complex] wcaps 0x400780: Mono Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x03451120: [Jack] SPDIF Out at Ext Left
    Conn = Optical, Color = Black
    DefAssociation = 0x2, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x06
Node 0x1f [Pin Complex] wcaps 0x400680: Mono Digital
  Pincap 0x00000024: IN Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
  Processing caps: benign=0, ncoeff=25
Node 0x21 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x22 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Input Source", index=1, device=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 12
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b 0x12
Node 0x23 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Input Source", index=0, device=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 11
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b
Node 0x24 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x25 [Audio Output] wcaps 0x411: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x26 [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x25 0x0b

____________________________________________

*** /proc/asound/card0/codec#1
*** ls: -r--r--r-- 1 root root 0 2011-07-14 14:11:58.735986415 +0530 /proc/asound/card0/codec#1
Codec: LSI ID 1040
Address: 1
MFG Function Id: 0x2 (unsol 1)
Vendor Id: 0x11c11040
Subsystem Id: 0x11c10001
Revision Id: 0x100200
Modem Function Group: 0x1

____________________________________________

*** /proc/asound/card0/codec#2
*** ls: -r--r--r-- 1 root root 0 2011-07-14 14:11:58.739986436 +0530 /proc/asound/card0/codec#2
Codec: Nvidia MCP77/78 HDMI
Address: 2
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x10de0003
Subsystem Id: 0x10de0101
Revision Id: 0x100000
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x04 [Audio Output] wcaps 0x211: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=1, device=0
  Control: name="IEC958 Playback Pro Mask", index=1, device=0
  Control: name="IEC958 Playback Default", index=1, device=0
  Control: name="IEC958 Playback Switch", index=1, device=0
  Device: name="HDMI 0", type="HDMI", device=3
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0xc0]: 48000 88200
    bits [0xf]: 8 16 20 24
    formats [0x1]: PCM
Node 0x05 [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x18560110: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x04
Node 0x06 [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0xc0]: 48000 88200
    bits [0xf]: 8 16 20 24
    formats [0x1]: PCM
Node 0x07 [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x58560121: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x1
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x06
Node 0x08 [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0xc0]: 48000 88200
    bits [0xf]: 8 16 20 24
    formats [0x1]: PCM
Node 0x09 [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x58560122: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x2
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x08
Node 0x0a [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0xc0]: 48000 88200
    bits [0xf]: 8 16 20 24
    formats [0x1]: PCM
Node 0x0b [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x58560123: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x3
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x0a
Node 0x0c [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0xc0]: 48000 88200
    bits [0xf]: 8 16 20 24
    formats [0x1]: PCM
Node 0x0d [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x58560124: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x4
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x0c

____________________________________________

End of NVIDIA bug report log file.
```

---

### Post by timgood on 2011-07-10
This is a well known and documented bug which has been reported umpteen times and I'm frankly surprised that it is still extant.

If you are getting Unity, then the driver is working and it is safe to ignore the message.

Info on the bug can be found here: [https://bugs.launchpad.net/ubuntu/+s...73/+bug/777493](https://bugs.launchpad.net/ubuntu/+s...73/+bug/777493)

Hope this helps.

---

### Post by realzippy on 2011-07-10
*wildmanne39* is right.According to your Xorg.0.log the driver is running.

---

### Post by srisharan on 2011-07-10
If you say so.Then marking this as solved

---

### Post by mikewhatever on 2011-07-10
> **timgood said:**
> This is a well known and documented bug which has been reported umpteen times and I'm frankly surprised that it is still extant.

If you are getting Unity, then the driver is working and it is safe to ignore the message.

Info on the bug can be found here: [https://bugs.launchpad.net/ubuntu/+s...73/+bug/777493](https://bugs.launchpad.net/ubuntu/+s...73/+bug/777493)

Hope this helps.

/https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/777493

...fixed the URL.

To say that that particular bug is well documented is a major overstatement. It's not been filed properly, there are no logs, no attachments, just complains and demands to fix it. It's not even clear that all the participants have the same problem.

---

### Post by timgood on 2011-07-10
> **mikewhatever said:**
> /https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/777493

...fixed the URL.

To say that that particular bug is well documented is a major overstatement. It's not been filed properly, there are no logs, no attachments, just complains and demands to fix it. It's not even clear that all the participants have the same problem.

That bug is a duplicate of this one [here]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/772207").

The problem has been around for a while and not yet been fixed. Legitimate criticism is surely good for both Linux in general and Ubuntu in particular. Get over it.

---

### Post by realzippy on 2011-07-10
Since Op's nvidia driver is running,it has nothing to do with that bug...
Anyway,thread solved.

---

### Post by timgood on 2011-07-10
> **realzippy said:**
> Since Op's nvidia driver is running,it has nothing to do with that bug...
Anyway,thread solved.

Yes, the driver is running. But Jockey is reporting it as not running. That's why it's a bug. Read the reports.

---

### Post by mikewhatever on 2011-07-10
> **timgood said:**
> That bug is a duplicate of this one [here]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/772207").

The problem has been around for a while and not yet been fixed. Legitimate criticism is surely good for both Linux in general and Ubuntu in particular. Get over it.

Not sure what legitimate criticism is, and who decides if it is or not. I prefer constructive criticism, but what does it has to do with the bug reports?

Back on topic..., all of those bug reports, 772207 and the duplicates, share the same faults I mentioned. Perhaps this is why there is little more then 'me too' and some complaining there.
Anyway, take it easy.

---

### Post by timgood on 2011-07-10
> **mikewhatever said:**
> 
Back on topic..., all of those bug reports, 772207 and the duplicates, share the same faults I mentioned. Perhaps this is why there is little more then 'me too' and some complaining there.
Anyway, take it easy.

You seem to have a very selective attention span. Log files and terminal output are given for this bug, which also has other duplicates which you may want to examine. As far as 'me too' goes, there is a button which asks you if you are affected by this bug. Does that qualify? If so, why is it there? You would make a very good politician. Or perhaps you already are one?

---

### Post by srisharan on 2011-07-10
Jeez guys!!calm down

---

### Post by timgood on 2011-07-10
OK. I'm calm. I apologise if I offended anyone by putting forward a point of view.:)

---

### Post by wildmanne39 on 2011-07-10
> **srisharan said:**
> I dont know if that is the case.I still get a Plymouth not just a text there when booting.You dont get a proper Plymouth when booting with an Nvidia card right
Hi, yes I do. I am testing oneiric and the bug is still present in it too.

---

### Post by DispDev on 2011-07-15
> **wildmanne39 said:**
> Hi, that is just a bug that says it is not in use, I have the same problem but my nvidia driver works great. If you can see the desktop and the green dots are lit up in additional drivers then they are activated you do not have to worry about it.

Initially, I considered this true.  NVidia X Server Settings could be changed, and remembered.  However, I must confess to sometimes wasting time playing a game called LBreakout2 (available in the repositories).  It's your typical Breakout game with paddle on the bottom of the screen, hitting a ball to break and clear the bricks on the top of the screen. 

In Ubuntu 11.04 when playing the game and the action got rather fast paced with bricks exploding everywhere, the game would stutter.  Reverting to older Nvidia drivers didn't offer any improvement.  A clean install, unlike my update to 11.04 didn't improve the game. The game was mostly unplayable.  It appeared like the 3D acceleration was't working, but required(?).

I downgraded to Ubuntu 10.04 and the game worked fine with the 260.19.06 driver.  Upgraded to Ubuntu 10.10 and the game still works fine with this driver.

I believe trying LBreakout2 is a good test of the Nvidia driver when multiple bricks are exploding at the same time.

For me, I can't get LBreakout2 to run properly in Ubuntu 11.04.  I followed numerous suggestions by others in the forum with no success. I don't doubt, others may indeed have the Nvidea driver working fully.

---

### Post by wildmanne39 on 2011-07-16
Hi, I was just stating that it is in use that it is a bug that says its not, I did not imply that because it is active that you would have good performance because of it being active, there are other issues with the drivers and cards sometimes, for speed issues this link fixes a lot of those issues.
[http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow](http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow)

---

