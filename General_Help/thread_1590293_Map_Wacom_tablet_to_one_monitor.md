---
title: "Map Wacom tablet to one monitor"
date: 2010-10-07
forum: General Help
---

### Post by Commander_Bob on 2010-10-07
I am running 10.04 (soon to be 10.10) and I have a Wacom tablet that has an aspect ratio of 4:3. I am using two monitors, one widescreen and one standard. The secondary (right) screen is the standard one and I would like to map my tablet to either just the right screen or part of the widescreen one.

I've done this in 9.04 but I wanted to know if there is a better/easier way to do it in 10.04/10.10.

Thanks,
Justin

---

### Post by ragtag on 2010-10-07
You no longer need to do it in your xorg.conf file, you can use the xsetwacom command. First run

```
xsetwacom --list
```

Which on my tablet pc outputs.

```
Serial Wacom Tablet eraser ERASER    
Serial Wacom Tablet STYLUS  
```

These are the name of the devices you need to be able to set the different options. You don't need the last capital letter word though. So for instance

```

xsetwacom set "Serial Wacom Tablet" Rotate CW
xsetwacom set "Serial Wacom Tablet eraser" Rotate CW

```

Rotates both my eraser and stylus 90 degree clock wise (or portrait mode). The options you use here are the same as the ones you would previously use in your xorg.conf file.

I think the options you are looking for are either ScreenNo and/or MMonitor (see [http://linuxwacom.sourceforge.net/index.php/howto/inputdev](http://linuxwacom.sourceforge.net/index.php/howto/inputdev) for details). It is also possible to set it up so that when it reaches the edge of one screen, it maps to the other. Or set up a button or shortcut to run a simple shell script with some xsetwacom commands, to change how it behaves on the fly. 

I don't know the exact details from the top of my head, and don't have a dual screen setup to test it on right now, but I hope it can at least point you in the right direction. :)

---

### Post by Commander_Bob on 2010-10-07
Awesome! 

xsetwacom set "Wacom Intuos2 6x8" TwinView horizontal

That pretty much did the trick. The only problem is that it assumes that each monitor is the same size so it splits it down the center which is an inch or two from the edge of my larger monitor. However, it's usable now.

I saw there were options for touch and gestures does that mean the bamboo tables with touch work now?

---

### Post by Don_Dragon on 2010-10-10
Hi, is anyone else having some trouble since the upgrade?  My Intuos3 registers when I use the list command, but for some reason, any command I input ends up with 'Cannot find device" Any ideas?

---

### Post by Favux on 2010-10-10
Did you check your:
```
xinput --list
```
to make sure you were using the correct "Device names"?  They might have changed.

---

### Post by Don_Dragon on 2010-10-11
Argh, seems like just yesterday I got this working on my dual screen.  I had setup a script to do restrict my tablet to one screen.  Now that I've updated to 10.10, the command does nothing.  Good tip on the Xlist, alas no dice.  The commands I use to use were:

[PHP]Xsetwacom --set "Wacom Intuos3 6X8" bottomX 35700

Xsetwacom --set "Wacom Intuos3 6X8 eraser" bottomX 35700[/PHP]

---

### Post by Favux on 2010-10-11
The x on xsetwacom shouldn't be capitalized.

```
xsetwacom --get "Wacom Intuos3 6X8" BottomX
```
or
```
xinput list-props "Wacom Intuos3 6X8"
```

---

### Post by Don_Dragon on 2010-10-11
Ooops.  Still, no dice.  Even when I try your commands, I get 
> 
Cannot find device 'Wacom Intuos3 6X8'

Yet my tablet works normally otherwise, and it does show up when I use xinput list.

---

### Post by Favux on 2010-10-11
Hmmm.  That doesn't make sense.  Could I see your:
```
xinput --list
```
output?  I'm thinking we need to look at your Xorg.0.log in /var/log.

---

### Post by Don_Dragon on 2010-10-11
Sure.  Thanks for the help BTW.

> Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Razer Razer Mamba                       	id=8	[slave  pointer  (2)]
&#9116;   &#8627; Razer Razer Mamba                       	id=9	[slave  pointer  (2)]
&#9116;   &#8627; Acer IR  Receiver                       	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos3 6x8 eraser                	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos3 6x8 cursor                	id=14	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos3 6x8 pad                   	id=15	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos3 6x8 stylus                	id=16	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; Logitech USB Multimedia Keyboard        	id=10	[slave  keyboard (3)]
    &#8627; Logitech USB Multimedia Keyboard        	id=11	[slave  keyboard (3)]


---

### Post by Favux on 2010-10-11
OK, the name did change.  Instead of the stylus being:
```
"Wacom Intuos3 6X8"
```
it's now:
```
"Wacom Intuos3 6x8 stylus"
```
Try that in the commands.

---

### Post by Don_Dragon on 2010-10-11
Unfortunately, I already tried that.  The command goes through with no complaint, but nothing seems to happen.

---

### Post by Favux on 2010-10-11
No output with the get or the xinput commands using the correct device name?

If not we do need to look at your Xorg.0.log.

---

### Post by Don_Dragon on 2010-10-11
Xorg0.log?   is that somewhere in etc/X11?

---

### Post by Don_Dragon on 2010-10-11
Here it is

> [    21.081] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    21.081] X Protocol Version 11, Revision 0
[    21.081] Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
[    21.081] Current Operating System: Linux KhanIV 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:32:27 UTC 2010 x86_64
[    21.081] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=0b9a92b8-60e7-4759-8103-18d274474a6c ro quiet splash
[    21.081] Build Date: 16 September 2010  06:18:41PM
[    21.081] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    21.081] Current version of pixman: 0.18.4
[    21.081] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    21.081] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    21.081] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Oct 11 02:18:00 2010
[    21.081] (==) Using config file: "/etc/X11/xorg.conf"
[    21.081] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    21.082] (==) ServerLayout "Layout0"
[    21.082] (**) |-->Screen "Screen0" (0)
[    21.082] (**) |   |-->Monitor "Monitor0"
[    21.082] (**) |   |-->Device "Device0"
[    21.082] (**) Option "Xinerama" "0"
[    21.082] (==) Automatically adding devices
[    21.082] (==) Automatically enabling devices
[    21.082] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    21.082] 	Entry deleted from font path.
[    21.082] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    21.082] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    21.082] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    21.082] (II) Loader magic: 0x7d0200
[    21.082] (II) Module ABI versions:
[    21.082] 	X.Org ANSI C Emulation: 0.4
[    21.082] 	X.Org Video Driver: 8.0
[    21.082] 	X.Org XInput driver : 11.0
[    21.082] 	X.Org Server Extension : 4.0
[    21.083] (--) PCI:*(0:1:0:0) 10de:0614:19f1:0e79 rev 162, Mem @ 0xfa000000/16777216, 0xd0000000/268435456, 0xf8000000/33554432, I/O @ 0x0000df00/128, BIOS @ 0x????????/131072
[    21.083] (II) Open ACPI successful (/var/run/acpid.socket)
[    21.083] (II) LoadModule: "extmod"
[    21.084] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    21.084] (II) Module extmod: vendor="X.Org Foundation"
[    21.084] 	compiled for 1.9.0, module version = 1.0.0
[    21.084] 	Module class: X.Org Server Extension
[    21.084] 	ABI class: X.Org Server Extension, version 4.0
[    21.084] (II) Loading extension MIT-SCREEN-SAVER
[    21.084] (II) Loading extension XFree86-VidModeExtension
[    21.084] (II) Loading extension XFree86-DGA
[    21.084] (II) Loading extension DPMS
[    21.084] (II) Loading extension XVideo
[    21.084] (II) Loading extension XVideo-MotionCompensation
[    21.084] (II) Loading extension X-Resource
[    21.084] (II) LoadModule: "dbe"
[    21.084] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    21.085] (II) Module dbe: vendor="X.Org Foundation"
[    21.085] 	compiled for 1.9.0, module version = 1.0.0
[    21.085] 	Module class: X.Org Server Extension
[    21.085] 	ABI class: X.Org Server Extension, version 4.0
[    21.085] (II) Loading extension DOUBLE-BUFFER
[    21.085] (II) LoadModule: "glx"
[    21.085] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    21.100] (II) Module glx: vendor="NVIDIA Corporation"
[    21.101] 	compiled for 4.0.2, module version = 1.0.0
[    21.101] 	Module class: X.Org Server Extension
[    21.101] (II) NVIDIA GLX Module  260.19.06  Mon Sep 13 04:54:41 PDT 2010
[    21.101] (II) Loading extension GLX
[    21.101] (II) LoadModule: "record"
[    21.101] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    21.101] (II) Module record: vendor="X.Org Foundation"
[    21.101] 	compiled for 1.9.0, module version = 1.13.0
[    21.101] 	Module class: X.Org Server Extension
[    21.101] 	ABI class: X.Org Server Extension, version 4.0
[    21.101] (II) Loading extension RECORD
[    21.101] (II) LoadModule: "dri"
[    21.101] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    21.102] (II) Module dri: vendor="X.Org Foundation"
[    21.102] 	compiled for 1.9.0, module version = 1.0.0
[    21.102] 	ABI class: X.Org Server Extension, version 4.0
[    21.102] (II) Loading extension XFree86-DRI
[    21.102] (II) LoadModule: "dri2"
[    21.102] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    21.102] (II) Module dri2: vendor="X.Org Foundation"
[    21.102] 	compiled for 1.9.0, module version = 1.2.0
[    21.102] 	ABI class: X.Org Server Extension, version 4.0
[    21.102] (II) Loading extension DRI2
[    21.102] (II) LoadModule: "nvidia"
[    21.102] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    21.103] (II) Module nvidia: vendor="NVIDIA Corporation"
[    21.103] 	compiled for 4.0.2, module version = 1.0.0
[    21.103] 	Module class: X.Org Video Driver
[    21.103] (II) NVIDIA dlloader X Driver  260.19.06  Mon Sep 13 04:31:43 PDT 2010
[    21.103] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    21.103] (++) using VT number 7

[    21.115] (II) Loading sub module "fb"
[    21.115] (II) LoadModule: "fb"
[    21.121] (II) Loading /usr/lib/xorg/modules/libfb.so
[    21.121] (II) Module fb: vendor="X.Org Foundation"
[    21.121] 	compiled for 1.9.0, module version = 1.0.0
[    21.121] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    21.121] (II) Loading sub module "wfb"
[    21.121] (II) LoadModule: "wfb"
[    21.122] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    21.122] (II) Module wfb: vendor="X.Org Foundation"
[    21.122] 	compiled for 1.9.0, module version = 1.0.0
[    21.122] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    21.122] (II) Loading sub module "ramdac"
[    21.122] (II) LoadModule: "ramdac"
[    21.122] (II) Module "ramdac" already built-in
[    21.122] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    21.122] (==) NVIDIA(0): RGB weight 888
[    21.122] (==) NVIDIA(0): Default visual is TrueColor
[    21.122] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    21.122] (**) NVIDIA(0): Option "TwinView" "1"
[    21.122] (**) NVIDIA(0): Option "MetaModes" "DFP-0: nvidia-auto-select +0+0, DFP-1: nvidia-auto-select +1920+0"
[    21.122] (**) NVIDIA(0): Enabling RENDER acceleration
[    21.122] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[    21.122] (II) NVIDIA(0):     enabled.
[    22.469] (II) NVIDIA(0): NVIDIA GPU GeForce 9800 GT (G92) at PCI:1:0:0 (GPU-0)
[    22.469] (--) NVIDIA(0): Memory: 1048576 kBytes
[    22.469] (--) NVIDIA(0): VideoBIOS: 62.92.84.00.61
[    22.469] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    22.469] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    22.469] (--) NVIDIA(0): Connected display device(s) on GeForce 9800 GT at PCI:1:0:0
[    22.469] (--) NVIDIA(0):     Samsung SyncMaster (DFP-0)
[    22.469] (--) NVIDIA(0):     Samsung SyncMaster (DFP-1)
[    22.469] (--) NVIDIA(0): Samsung SyncMaster (DFP-0): 330.0 MHz maximum pixel clock
[    22.469] (--) NVIDIA(0): Samsung SyncMaster (DFP-0): Internal Dual Link TMDS
[    22.469] (--) NVIDIA(0): Samsung SyncMaster (DFP-1): 330.0 MHz maximum pixel clock
[    22.469] (--) NVIDIA(0): Samsung SyncMaster (DFP-1): Internal Dual Link TMDS
[    22.473] (**) NVIDIA(0): TwinView enabled
[    22.473] (II) NVIDIA(0): Display Devices found referenced in MetaMode: DFP-0, DFP-1
[    22.473] (WW) NVIDIA(0): The EDID for Samsung SyncMaster (DFP-0) contradicts itself:
[    22.473] (WW) NVIDIA(0):     mode "1920x1080" is specified in the EDID; however, the
[    22.473] (WW) NVIDIA(0):     EDID's valid VertRefresh range (56.000-60.000 Hz) would
[    22.474] (WW) NVIDIA(0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    22.474] (WW) NVIDIA(0):     VertRefresh check for mode "1920x1080".
[    22.474] (WW) NVIDIA(0): The EDID for Samsung SyncMaster (DFP-0) contradicts itself:
[    22.474] (WW) NVIDIA(0):     mode "1280x720" is specified in the EDID; however, the
[    22.474] (WW) NVIDIA(0):     EDID's valid VertRefresh range (56.000-60.000 Hz) would
[    22.474] (WW) NVIDIA(0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    22.474] (WW) NVIDIA(0):     VertRefresh check for mode "1280x720".
[    22.474] (WW) NVIDIA(0): The EDID for Samsung SyncMaster (DFP-0) contradicts itself:
[    22.474] (WW) NVIDIA(0):     mode "720x576" is specified in the EDID; however, the
[    22.474] (WW) NVIDIA(0):     EDID's valid VertRefresh range (56.000-60.000 Hz) would
[    22.474] (WW) NVIDIA(0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    22.474] (WW) NVIDIA(0):     VertRefresh check for mode "720x576".
[    22.474] (WW) NVIDIA(0): The EDID for Samsung SyncMaster (DFP-0) contradicts itself:
[    22.474] (WW) NVIDIA(0):     mode "1920x1080" is specified in the EDID; however, the
[    22.474] (WW) NVIDIA(0):     EDID's valid VertRefresh range (56.000-60.000 Hz) would
[    22.474] (WW) NVIDIA(0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    22.474] (WW) NVIDIA(0):     VertRefresh check for mode "1920x1080".
[    22.474] (WW) NVIDIA(0): The EDID for Samsung SyncMaster (DFP-0) contradicts itself:
[    22.475] (WW) NVIDIA(0):     mode "1280x720" is specified in the EDID; however, the
[    22.475] (WW) NVIDIA(0):     EDID's valid VertRefresh range (56.000-60.000 Hz) would
[    22.475] (WW) NVIDIA(0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    22.475] (WW) NVIDIA(0):     VertRefresh check for mode "1280x720".
[    22.475] (WW) NVIDIA(0): The EDID for Samsung SyncMaster (DFP-0) contradicts itself:
[    22.475] (WW) NVIDIA(0):     mode "720x576" is specified in the EDID; however, the
[    22.475] (WW) NVIDIA(0):     EDID's valid VertRefresh range (56.000-60.000 Hz) would
[    22.475] (WW) NVIDIA(0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    22.475] (WW) NVIDIA(0):     VertRefresh check for mode "720x576".
[    22.568] (II) NVIDIA(0): Assigned Display Devices: DFP-0, DFP-1
[    22.569] (II) NVIDIA(0): Validated modes:
[    22.569] (II) NVIDIA(0):    
[    22.569] (II) NVIDIA(0):     "DFP-0:nvidia-auto-select+0+0,DFP-1:nvidia-auto-select+1920+0"
[    22.569] (II) NVIDIA(0): Virtual screen size determined to be 3360 x 1080
[    22.594] (--) NVIDIA(0): DPI set to (95, 94); computed from "UseEdidDpi" X config
[    22.595] (--) NVIDIA(0):     option
[    22.595] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[    22.595] (--) Depth 24 pixmap format is 32 bpp
[    22.595] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    22.596] (II) NVIDIA(0): Initialized GPU GART.
[    22.605] (II) NVIDIA(0): Setting mode
[    22.605] (II) NVIDIA(0):     "DFP-0:nvidia-auto-select+0+0,DFP-1:nvidia-auto-select+1920+0"
[    22.648] (II) Loading extension NV-GLX
[    22.695] (II) NVIDIA(0): Initialized OpenGL Acceleration
[    22.696] (==) NVIDIA(0): Disabling shared memory pixmaps
[    22.696] (II) NVIDIA(0): Initialized X Rendering Acceleration
[    22.696] (==) NVIDIA(0): Backing store disabled
[    22.696] (==) NVIDIA(0): Silken mouse enabled
[    22.724] (**) NVIDIA(0): DPMS enabled
[    22.725] (II) Loading extension NV-CONTROL
[    22.725] (II) Loading extension XINERAMA
[    22.725] (II) Loading sub module "dri2"
[    22.725] (II) LoadModule: "dri2"
[    22.725] (II) Reloading /usr/lib/xorg/modules/extensions/libdri2.so
[    22.726] (II) NVIDIA(0): [DRI2] Setup complete
[    22.726] (==) RandR enabled
[    22.726] (II) Initializing built-in extension Generic Event Extension
[    22.726] (II) Initializing built-in extension SHAPE
[    22.726] (II) Initializing built-in extension MIT-SHM
[    22.726] (II) Initializing built-in extension XInputExtension
[    22.726] (II) Initializing built-in extension XTEST
[    22.726] (II) Initializing built-in extension BIG-REQUESTS
[    22.726] (II) Initializing built-in extension SYNC
[    22.726] (II) Initializing built-in extension XKEYBOARD
[    22.726] (II) Initializing built-in extension XC-MISC
[    22.726] (II) Initializing built-in extension SECURITY
[    22.726] (II) Initializing built-in extension XINERAMA
[    22.726] (II) Initializing built-in extension XFIXES
[    22.726] (II) Initializing built-in extension RENDER
[    22.726] (II) Initializing built-in extension RANDR
[    22.726] (II) Initializing built-in extension COMPOSITE
[    22.726] (II) Initializing built-in extension DAMAGE
[    22.726] (II) Initializing built-in extension GESTURE
[    22.728] (II) Initializing extension GLX
[    22.764] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    22.775] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    22.775] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    22.775] (II) LoadModule: "evdev"
[    22.776] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.777] (II) Module evdev: vendor="X.Org Foundation"
[    22.777] 	compiled for 1.9.0, module version = 2.3.2
[    22.777] 	Module class: X.Org XInput Driver
[    22.777] 	ABI class: X.Org XInput driver, version 11.0
[    22.777] (**) Power Button: always reports core events
[    22.777] (**) Power Button: Device: "/dev/input/event1"
[    22.833] (II) Power Button: Found keys
[    22.833] (II) Power Button: Configuring as keyboard
[    22.834] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    22.834] (**) Option "xkb_rules" "evdev"
[    22.834] (**) Option "xkb_model" "pc105"
[    22.834] (**) Option "xkb_layout" "ca"
[    22.836] (II) XKB: reuse xkmfile /var/lib/xkb/server-3BCFF748FFB6BCDACC88715CBF6A9DF905CD3181.xkm
[    22.838] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    22.838] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    22.838] (**) Power Button: always reports core events
[    22.838] (**) Power Button: Device: "/dev/input/event0"
[    22.838] (II) Power Button: Found keys
[    22.838] (II) Power Button: Configuring as keyboard
[    22.838] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    22.838] (**) Option "xkb_rules" "evdev"
[    22.839] (**) Option "xkb_model" "pc105"
[    22.839] (**) Option "xkb_layout" "ca"
[    22.843] (II) config/udev: Adding input device Saitek Saitek X52 Flight Control System (/dev/input/event2)
[    22.843] (II) No input driver/identifier specified (ignoring)
[    22.843] (II) config/udev: Adding input device Saitek Saitek X52 Flight Control System (/dev/input/js0)
[    22.843] (II) No input driver/identifier specified (ignoring)
[    22.844] (II) config/udev: Adding input device Razer Razer Mamba (/dev/input/event3)
[    22.844] (**) Razer Razer Mamba: Applying InputClass "evdev pointer catchall"
[    22.844] (**) Razer Razer Mamba: always reports core events
[    22.844] (**) Razer Razer Mamba: Device: "/dev/input/event3"
[    22.911] (II) Razer Razer Mamba: Found 11 mouse buttons
[    22.911] (II) Razer Razer Mamba: Found scroll wheel(s)
[    22.911] (II) Razer Razer Mamba: Found relative axes
[    22.911] (II) Razer Razer Mamba: Found x and y relative axes
[    22.911] (II) Razer Razer Mamba: Configuring as mouse
[    22.911] (**) Razer Razer Mamba: YAxisMapping: buttons 4 and 5
[    22.911] (**) Razer Razer Mamba: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    22.911] (II) XINPUT: Adding extended input device "Razer Razer Mamba" (type: MOUSE)
[    22.911] (II) Razer Razer Mamba: initialized for relative axes.
[    22.912] (II) config/udev: Adding input device Razer Razer Mamba (/dev/input/mouse0)
[    22.912] (II) No input driver/identifier specified (ignoring)
[    22.912] (II) config/udev: Adding input device Razer Razer Mamba (/dev/input/event4)
[    22.912] (**) Razer Razer Mamba: Applying InputClass "evdev keyboard catchall"
[    22.912] (**) Razer Razer Mamba: always reports core events
[    22.912] (**) Razer Razer Mamba: Device: "/dev/input/event4"
[    23.031] (II) Razer Razer Mamba: Found 1 mouse buttons
[    23.031] (II) Razer Razer Mamba: Found scroll wheel(s)
[    23.031] (II) Razer Razer Mamba: Found relative axes
[    23.031] (II) Razer Razer Mamba: Found absolute axes
[    23.031] (II) evdev-grail: failed to open grail, no gesture support
[    23.031] (II) Razer Razer Mamba: Found keys
[    23.031] (II) Razer Razer Mamba: Configuring as mouse
[    23.031] (II) Razer Razer Mamba: Configuring as keyboard
[    23.031] (**) Razer Razer Mamba: YAxisMapping: buttons 4 and 5
[    23.031] (**) Razer Razer Mamba: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    23.031] (II) XINPUT: Adding extended input device "Razer Razer Mamba" (type: KEYBOARD)
[    23.031] (**) Option "xkb_rules" "evdev"
[    23.031] (**) Option "xkb_model" "pc105"
[    23.031] (**) Option "xkb_layout" "ca"
[    23.031] (EE) Razer Razer Mamba: failed to initialize for relative axes.
[    23.031] (II) Razer Razer Mamba: initialized for absolute axes.
[    23.032] (II) config/udev: Adding input device Logitech USB Multimedia Keyboard (/dev/input/event5)
[    23.032] (**) Logitech USB Multimedia Keyboard: Applying InputClass "evdev keyboard catchall"
[    23.032] (**) Logitech USB Multimedia Keyboard: always reports core events
[    23.032] (**) Logitech USB Multimedia Keyboard: Device: "/dev/input/event5"
[    23.111] (II) Logitech USB Multimedia Keyboard: Found keys
[    23.111] (II) Logitech USB Multimedia Keyboard: Configuring as keyboard
[    23.111] (II) XINPUT: Adding extended input device "Logitech USB Multimedia Keyboard" (type: KEYBOARD)
[    23.111] (**) Option "xkb_rules" "evdev"
[    23.111] (**) Option "xkb_model" "pc105"
[    23.111] (**) Option "xkb_layout" "ca"
[    23.112] (II) config/udev: Adding input device Logitech USB Multimedia Keyboard (/dev/input/event6)
[    23.112] (**) Logitech USB Multimedia Keyboard: Applying InputClass "evdev keyboard catchall"
[    23.112] (**) Logitech USB Multimedia Keyboard: always reports core events
[    23.112] (**) Logitech USB Multimedia Keyboard: Device: "/dev/input/event6"
[    23.191] (II) Logitech USB Multimedia Keyboard: Found keys
[    23.191] (II) Logitech USB Multimedia Keyboard: Configuring as keyboard
[    23.191] (II) XINPUT: Adding extended input device "Logitech USB Multimedia Keyboard" (type: KEYBOARD)
[    23.191] (**) Option "xkb_rules" "evdev"
[    23.191] (**) Option "xkb_model" "pc105"
[    23.191] (**) Option "xkb_layout" "ca"
[    23.192] (II) config/udev: Adding input device Acer IR  Receiver (/dev/input/event7)
[    23.192] (**) Acer IR  Receiver: Applying InputClass "evdev keyboard catchall"
[    23.192] (**) Acer IR  Receiver: always reports core events
[    23.192] (**) Acer IR  Receiver: Device: "/dev/input/event7"
[    23.271] (II) Acer IR  Receiver: Found 1 mouse buttons
[    23.271] (II) Acer IR  Receiver: Found scroll wheel(s)
[    23.271] (II) Acer IR  Receiver: Found relative axes
[    23.271] (II) Acer IR  Receiver: Found absolute axes
[    23.271] (II) evdev-grail: failed to open grail, no gesture support
[    23.271] (II) Acer IR  Receiver: Found keys
[    23.271] (II) Acer IR  Receiver: Configuring as mouse
[    23.271] (II) Acer IR  Receiver: Configuring as keyboard
[    23.271] (**) Acer IR  Receiver: YAxisMapping: buttons 4 and 5
[    23.271] (**) Acer IR  Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    23.271] (II) XINPUT: Adding extended input device "Acer IR  Receiver" (type: KEYBOARD)
[    23.271] (**) Option "xkb_rules" "evdev"
[    23.271] (**) Option "xkb_model" "pc105"
[    23.271] (**) Option "xkb_layout" "ca"
[    23.271] (EE) Acer IR  Receiver: failed to initialize for relative axes.
[    23.271] (II) Acer IR  Receiver: initialized for absolute axes.
[    23.273] (II) config/udev: Adding input device Wacom Intuos3 6x8 (/dev/input/event8)
[    23.273] (**) Wacom Intuos3 6x8: Applying InputClass "evdev tablet catchall"
[    23.273] (**) Wacom Intuos3 6x8: Applying InputClass "Wacom class"
[    23.273] (II) LoadModule: "wacom"
[    23.273] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    23.274] (II) Module wacom: vendor="X.Org Foundation"
[    23.274] 	compiled for 1.8.99.905, module version = 0.10.8
[    23.274] 	Module class: X.Org XInput Driver
[    23.274] 	ABI class: X.Org XInput driver, version 11.0
[    23.274] (**) Option "Device" "/dev/input/event8"
[    23.311] (II) Wacom Intuos3 6x8: type not specified, assuming 'stylus'.
[    23.311] (II) Wacom Intuos3 6x8: other types will be automatically added.
[    23.311] (**) Wacom Intuos3 6x8 stylus: always reports core events
[    23.311] (--) Wacom Intuos3 6x8 stylus: using pressure threshold of 27 for button 1
[    23.311] (--) Wacom Intuos3 6x8 stylus: Wacom USB Intuos3 tablet maxX=40640 maxY=30480 maxZ=1023 resX=5080 resY=5080  tilt=enabled
[    23.311] (II) Wacom Intuos3 6x8 stylus: hotplugging dependent devices.
[    23.311] (**) Wacom Intuos3 6x8 eraser: Applying InputClass "evdev tablet catchall"
[    23.311] (**) Wacom Intuos3 6x8 eraser: Applying InputClass "Wacom class"
[    23.311] (**) Option "Device" "/dev/input/event8"
[    23.341] (**) Wacom Intuos3 6x8 eraser: always reports core events
[    23.341] (--) Wacom Intuos3 6x8 eraser: Wacom USB Intuos3 tablet maxX=40640 maxY=30480 maxZ=1023 resX=5080 resY=5080  tilt=enabled
[    23.381] (II) XINPUT: Adding extended input device "Wacom Intuos3 6x8 eraser" (type: ERASER)
[    23.381] (--) Wacom Intuos3 6x8 eraser: top X=0 top Y=0 bottom X=40640 bottom Y=30480 resol X=5080 resol Y=5080
[    23.531] (**) Wacom Intuos3 6x8 cursor: Applying InputClass "evdev tablet catchall"
[    23.531] (**) Wacom Intuos3 6x8 cursor: Applying InputClass "Wacom class"
[    23.531] (**) Option "Device" "/dev/input/event8"
[    23.561] (**) Wacom Intuos3 6x8 cursor: always reports core events
[    23.561] (--) Wacom Intuos3 6x8 cursor: Wacom USB Intuos3 tablet maxX=40640 maxY=30480 maxZ=1023 resX=5080 resY=5080  tilt=enabled
[    23.611] (II) XINPUT: Adding extended input device "Wacom Intuos3 6x8 cursor" (type: CURSOR)
[    23.611] (--) Wacom Intuos3 6x8 cursor: top X=0 top Y=0 bottom X=40640 bottom Y=30480 resol X=5080 resol Y=5080
[    23.611] (**) Wacom Intuos3 6x8 pad: Applying InputClass "evdev tablet catchall"
[    23.611] (**) Wacom Intuos3 6x8 pad: Applying InputClass "Wacom class"
[    23.611] (**) Option "Device" "/dev/input/event8"
[    23.691] (**) Wacom Intuos3 6x8 pad: always reports core events
[    23.691] (--) Wacom Intuos3 6x8 pad: Wacom USB Intuos3 tablet maxX=40640 maxY=30480 maxZ=1023 resX=5080 resY=5080  tilt=enabled
[    23.771] (II) XINPUT: Adding extended input device "Wacom Intuos3 6x8 pad" (type: PAD)
[    23.771] (--) Wacom Intuos3 6x8 pad: top X=0 top Y=0 bottom X=40640 bottom Y=30480 resol X=5080 resol Y=5080
[    23.771] (II) Wacom Intuos3 6x8 stylus: hotplugging completed.
[    23.851] (II) XINPUT: Adding extended input device "Wacom Intuos3 6x8 stylus" (type: STYLUS)
[    23.851] (--) Wacom Intuos3 6x8 stylus: top X=0 top Y=0 bottom X=40640 bottom Y=30480 resol X=5080 resol Y=5080
[    23.852] (II) config/udev: Adding input device Wacom Intuos3 6x8 (/dev/input/mouse1)
[    23.852] (II) No input driver/identifier specified (ignoring)
[   597.204] (II) XKB: reuse xkmfile /var/lib/xkb/server-94BE386FDC5B4C370FF9BD7DA72B7F78B011BEF6.xkm
[   744.089] (II) XKB: reuse xkmfile /var/lib/xkb/server-94BE386FDC5B4C370FF9BD7DA72B7F78B011BEF6.xkm
[  1127.111] (II) XKB: reuse xkmfile /var/lib/xkb/server-94BE386FDC5B4C370FF9BD7DA72B7F78B011BEF6.xkm
[  1294.632] (II) XKB: reuse xkmfile /var/lib/xkb/server-94BE386FDC5B4C370FF9BD7DA72B7F78B011BEF6.xkm
[  1307.422] (II) XKB: reuse xkmfile /var/lib/xkb/server-94BE386FDC5B4C370FF9BD7DA72B7F78B011BEF6.xkm
[  1542.456] (II) XKB: reuse xkmfile /var/lib/xkb/server-94BE386FDC5B4C370FF9BD7DA72B7F78B011BEF6.xkm
[  1566.988] (II) XKB: reuse xkmfile /var/lib/xkb/server-94BE386FDC5B4C370FF9BD7DA72B7F78B011BEF6.xkm
[  2382.895] (II) XKB: reuse xkmfile /var/lib/xkb/server-94BE386FDC5B4C370FF9BD7DA72B7F78B011BEF6.xkm
[  2917.665] (II) XKB: reuse xkmfile /var/lib/xkb/server-94BE386FDC5B4C370FF9BD7DA72B7F78B011BEF6.xkm
[  3001.309] (II) XKB: reuse xkmfile /var/lib/xkb/server-94BE386FDC5B4C370FF9BD7DA72B7F78B011BEF6.xkm

---

### Post by Favux on 2010-10-11
If the xinput list-props command doesn't give output, which it should, then the Xorg.0.log is in /var/log.

---

### Post by Favux on 2010-10-11
We have a mystery because your Xorg.0.log looks normal:
```
[ 23.273] (II) config/udev: Adding input device Wacom Intuos3 6x8 (/dev/input/event
[ 23.273] (**) Wacom Intuos3 6x8: Applying InputClass "evdev tablet catchall"
[ 23.273] (**) Wacom Intuos3 6x8: Applying InputClass "Wacom class"
[ 23.273] (II) LoadModule: "wacom"
[ 23.273] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[ 23.274] (II) Module wacom: vendor="X.Org Foundation"
[ 23.274] compiled for 1.8.99.905, module version = 0.10.8
[ 23.274] Module class: X.Org XInput Driver
[ 23.274] ABI class: X.Org XInput driver, version 11.0
[ 23.274] (**) Option "Device" "/dev/input/event8"
[ 23.311] (II) Wacom Intuos3 6x8: type not specified, assuming 'stylus'.
[ 23.311] (II) Wacom Intuos3 6x8: other types will be automatically added.
[ 23.311] (**) Wacom Intuos3 6x8 stylus: always reports core events
[ 23.311] (--) Wacom Intuos3 6x8 stylus: using pressure threshold of 27 for button 1
[ 23.311] (--) Wacom Intuos3 6x8 stylus: Wacom USB Intuos3 tablet maxX=40640 maxY=30480 maxZ=1023 resX=5080 resY=5080 tilt=enabled
[ 23.311] (II) Wacom Intuos3 6x8 stylus: hotplugging dependent devices.
[ 23.311] (**) Wacom Intuos3 6x8 eraser: Applying InputClass "evdev tablet catchall"
[ 23.311] (**) Wacom Intuos3 6x8 eraser: Applying InputClass "Wacom class"
[ 23.311] (**) Option "Device" "/dev/input/event8"
[ 23.341] (**) Wacom Intuos3 6x8 eraser: always reports core events
[ 23.341] (--) Wacom Intuos3 6x8 eraser: Wacom USB Intuos3 tablet maxX=40640 maxY=30480 maxZ=1023 resX=5080 resY=5080 tilt=enabled
[ 23.381] (II) XINPUT: Adding extended input device "Wacom Intuos3 6x8 eraser" (type: ERASER)
[ 23.381] (--) Wacom Intuos3 6x8 eraser: top X=0 top Y=0 bottom X=40640 bottom Y=30480 resol X=5080 resol Y=5080
[ 23.531] (**) Wacom Intuos3 6x8 cursor: Applying InputClass "evdev tablet catchall"
[ 23.531] (**) Wacom Intuos3 6x8 cursor: Applying InputClass "Wacom class"
[ 23.531] (**) Option "Device" "/dev/input/event8"
[ 23.561] (**) Wacom Intuos3 6x8 cursor: always reports core events
[ 23.561] (--) Wacom Intuos3 6x8 cursor: Wacom USB Intuos3 tablet maxX=40640 maxY=30480 maxZ=1023 resX=5080 resY=5080 tilt=enabled
[ 23.611] (II) XINPUT: Adding extended input device "Wacom Intuos3 6x8 cursor" (type: CURSOR)
[ 23.611] (--) Wacom Intuos3 6x8 cursor: top X=0 top Y=0 bottom X=40640 bottom Y=30480 resol X=5080 resol Y=5080
[ 23.611] (**) Wacom Intuos3 6x8 pad: Applying InputClass "evdev tablet catchall"
[ 23.611] (**) Wacom Intuos3 6x8 pad: Applying InputClass "Wacom class"
[ 23.611] (**) Option "Device" "/dev/input/event8"
[ 23.691] (**) Wacom Intuos3 6x8 pad: always reports core events
[ 23.691] (--) Wacom Intuos3 6x8 pad: Wacom USB Intuos3 tablet maxX=40640 maxY=30480 maxZ=1023 resX=5080 resY=5080 tilt=enabled
[ 23.771] (II) XINPUT: Adding extended input device "Wacom Intuos3 6x8 pad" (type: PAD)
[ 23.771] (--) Wacom Intuos3 6x8 pad: top X=0 top Y=0 bottom X=40640 bottom Y=30480 resol X=5080 resol Y=5080
[ 23.771] (II) Wacom Intuos3 6x8 stylus: hotplugging completed.
[ 23.851] (II) XINPUT: Adding extended input device "Wacom Intuos3 6x8 stylus" (type: STYLUS)
[ 23.851] (--) Wacom Intuos3 6x8 stylus: top X=0 top Y=0 bottom X=40640 bottom Y=30480 resol X=5080 resol Y=5080
[ 23.852] (II) config/udev: Adding input device Wacom Intuos3 6x8 (/dev/input/mouse1)
[ 23.852] (II) No input driver/identifier specified (ignoring)
```
The only thing I can come up with right now is somehow the xsetwacom part of the default xf86-input-wacom 0.10.8 didn't install right.  So go to Synaptic Package Manager and find the package xserver-xorg-input-wacom and tell Synaptic to reinstall it and then reboot.

---

### Post by thskyt on 2010-12-13
Has anyone found a solution to the dual-head resolution issue where xsetwacom thinks both screens have the same resolution?

---

### Post by Favux on 2010-12-13
Hi thskyt,

Welcome to Ubuntu forums!

I don't have an answer for you.  There's suppose to be a new xsetwacom command (if your xf86-input-wacom is up to date enough) in the form of:
```
xsetwacom set <device name> "MapToOutput" VGA1
```
Which is suppose to only apply once, so if you change output you have to rerun it. We haven't figured out how to use it yet. So far trying to run it we get the error:
> "Server does not support transformation" 

---

### Post by Favux on 2011-01-15
Hi Don_Dragon,

Another thing you could check is if you have two xsetwacom executables.  Check in /usr/local/bin for xsetwacom (it should be in /usr/bin). This may mean you forgot the '--prefix=/usr' flag on the xf86-input-wacom configure line. In which case you may have a xsetwacom executable in both locations and are experiencing version conflict. Delete the one in the wrong location, i.e. /usr/local/bin.


Hi thskyt,

I have a solution for you now.  See "[**HOW TO Setup a Wacom Tablet with Multi-Monitors in Maverick and Natty**]("http://ubuntuforums.org/showthread.php?t=1656089")".  As the title says you must have at least Maverick (Xserver 1.9).

---

