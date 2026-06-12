---
title: "Mouse issue with 10.10"
date: 2010-10-13
forum: General Help
---

### Post by zerozechs on 2010-10-13
I'm having mouse issues with 10.10.
 
Equipment: Asus Eee 900, Celeron @ 900 MHz w/ 2 gig memory
Mouse: Rocketfish (but issue replicable with mousepad)
 
When starting a program, the mouse may randomly not work within that program but does work outside of it, or vice-versa. For instance, when starting the text editor, the OS may not recognize mouse clicks inside the program (within the text editing portion, within the text editors menu bar etc.), but it does recognize mouse clicks outside the program (like clicking on the battery icon for battery status). This could also be reversed, where the OS only recognizes mouse clicks within the program but none externally (including the top status bar where the menu options, battery status, and clock are). 
 
IF the mouse is not working inside the program and I click somewhere externally (like the battery status), this seems to temporarily fix the problem and allow clicking inside the program. However, this seems to switch the problem to where I can no longer click externally. This seems to be the only method of switching which area is selectable by mouse, as I have not found a reverse process. This forces me to close the program using Ctrl + Q instead of being able to click out, because the close button is in the top status bar. This seems to happen pretty much universally.
 
If the program is closed, then I can again click any thing on the main screen, including the top status bar.
 
I am currently running the netbook without the power supply plugged in. I will repost later when the power supply is connected to see if it makes a difference.
 
At first I thought the netbook was locked up, but the mouse still moves and if the cursor is active in a text editing area it still responds to keystrokes. It's not a disasterous bug, but it's annoying.

---

### Post by jellevictoor on 2010-10-16
Same issues, but on a desktop pc with 10.10, the problem started a month ago on 10.04. 
Any hints where to look, this happens pretty random, didn't find the cause yet.

---

### Post by jellevictoor on 2010-10-18
Someone who could give pointers where to look? This might seem a small issue but i makes it very tedious to get something done.

---

### Post by rostamiani on 2010-10-18
The problem solved with the last updates :)

---

### Post by jellevictoor on 2010-10-19
What is/was the problem exactly and the cause? I did a upgrade yesterday and it wasn't fixed yet, perhaps this evening.

---

### Post by rostamiani on 2010-10-19
Oh !
It did not fixed completely !
There is no problem when I chang my language anymore... but it happens when I enable Num Lock ! :(

---

### Post by jellevictoor on 2010-10-19
The content of my /var/log/Xorg.0.log
I don't know if this is relevant.
```
[    17.708] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    17.708] X Protocol Version 11, Revision 0
[    17.708] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    17.708] Current Operating System: Linux jelle-desktop 2.6.35-22-generic #34-Ubuntu SMP Sun Oct 10 09:24:00 UTC 2010 i686
[    17.708] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=b15aaa0f-4fd9-4399-b9cb-c380c05b643b ro quiet splash
[    17.708] Build Date: 16 September 2010  05:39:22PM
[    17.708] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
[    17.708] Current version of pixman: 0.18.4
[    17.708] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    17.708] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    17.708] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Oct 19 18:20:10 2010
[    17.708] (==) Using config file: "/etc/X11/xorg.conf"
[    17.708] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    17.709] (==) No Layout section.  Using the first Screen section.
[    17.709] (**) |-->Screen "Default Screen" (0)
[    17.709] (**) |   |-->Monitor "<default monitor>"
[    17.709] (==) No device specified for screen "Default Screen".
	Using the first device section listed.
[    17.709] (**) |   |-->Device "Default Device"
[    17.709] (==) No monitor specified for screen "Default Screen".
	Using a default monitor configuration.
[    17.709] (==) Automatically adding devices
[    17.709] (==) Automatically enabling devices
[    17.709] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    17.709] 	Entry deleted from font path.
[    17.709] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    17.709] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    17.709] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    17.709] (II) Loader magic: 0x81f8e00
[    17.709] (II) Module ABI versions:
[    17.709] 	X.Org ANSI C Emulation: 0.4
[    17.709] 	X.Org Video Driver: 8.0
[    17.709] 	X.Org XInput driver : 11.0
[    17.709] 	X.Org Server Extension : 4.0
[    17.710] (--) PCI:*(0:1:0:0) 10de:0193:1043:823c rev 162, Mem @ 0xfd000000/16777216, 0xd0000000/268435456, 0xfa000000/33554432, I/O @ 0x0000cc00/128, BIOS @ 0x????????/131072
[    17.710] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    17.710] (II) "extmod" will be loaded by default.
[    17.710] (II) "dbe" will be loaded by default.
[    17.710] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    17.710] (II) "record" will be loaded by default.
[    17.710] (II) "dri" will be loaded by default.
[    17.710] (II) "dri2" will be loaded by default.
[    17.710] (II) LoadModule: "glx"
[    17.710] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    17.723] (II) Module glx: vendor="NVIDIA Corporation"
[    17.723] 	compiled for 4.0.2, module version = 1.0.0
[    17.723] 	Module class: X.Org Server Extension
[    17.723] (II) NVIDIA GLX Module  173.14.28  Wed Sep 29 10:17:05 PDT 2010
[    17.723] (II) Loading extension GLX
[    17.723] (II) LoadModule: "extmod"
[    17.723] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    17.724] (II) Module extmod: vendor="X.Org Foundation"
[    17.724] 	compiled for 1.9.0, module version = 1.0.0
[    17.724] 	Module class: X.Org Server Extension
[    17.724] 	ABI class: X.Org Server Extension, version 4.0
[    17.724] (II) Loading extension MIT-SCREEN-SAVER
[    17.724] (II) Loading extension XFree86-VidModeExtension
[    17.724] (II) Loading extension XFree86-DGA
[    17.724] (II) Loading extension DPMS
[    17.724] (II) Loading extension XVideo
[    17.724] (II) Loading extension XVideo-MotionCompensation
[    17.724] (II) Loading extension X-Resource
[    17.724] (II) LoadModule: "dbe"
[    17.724] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    17.724] (II) Module dbe: vendor="X.Org Foundation"
[    17.724] 	compiled for 1.9.0, module version = 1.0.0
[    17.724] 	Module class: X.Org Server Extension
[    17.724] 	ABI class: X.Org Server Extension, version 4.0
[    17.724] (II) Loading extension DOUBLE-BUFFER
[    17.724] (II) LoadModule: "record"
[    17.724] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    17.724] (II) Module record: vendor="X.Org Foundation"
[    17.724] 	compiled for 1.9.0, module version = 1.13.0
[    17.724] 	Module class: X.Org Server Extension
[    17.724] 	ABI class: X.Org Server Extension, version 4.0
[    17.724] (II) Loading extension RECORD
[    17.724] (II) LoadModule: "dri"
[    17.724] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    17.724] (II) Module dri: vendor="X.Org Foundation"
[    17.724] 	compiled for 1.9.0, module version = 1.0.0
[    17.724] 	ABI class: X.Org Server Extension, version 4.0
[    17.724] (II) Loading extension XFree86-DRI
[    17.724] (II) LoadModule: "dri2"
[    17.725] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    17.725] (II) Module dri2: vendor="X.Org Foundation"
[    17.725] 	compiled for 1.9.0, module version = 1.2.0
[    17.725] 	ABI class: X.Org Server Extension, version 4.0
[    17.725] (II) Loading extension DRI2
[    17.725] (II) LoadModule: "nvidia"
[    17.725] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    17.725] (II) Module nvidia: vendor="NVIDIA Corporation"
[    17.725] 	compiled for 4.0.2, module version = 1.0.0
[    17.725] 	Module class: X.Org Video Driver
[    17.725] (II) NVIDIA dlloader X Driver  173.14.28  Wed Sep 29 09:55:18 PDT 2010
[    17.725] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    17.725] (++) using VT number 7

[    17.728] (II) Loading sub module "fb"
[    17.728] (II) LoadModule: "fb"
[    17.728] (II) Loading /usr/lib/xorg/modules/libfb.so
[    17.728] (II) Module fb: vendor="X.Org Foundation"
[    17.728] 	compiled for 1.9.0, module version = 1.0.0
[    17.728] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    17.728] (II) Loading sub module "wfb"
[    17.728] (II) LoadModule: "wfb"
[    17.728] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    17.728] (II) Module wfb: vendor="X.Org Foundation"
[    17.728] 	compiled for 1.9.0, module version = 1.0.0
[    17.728] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    17.728] (II) Loading sub module "ramdac"
[    17.728] (II) LoadModule: "ramdac"
[    17.728] (II) Module "ramdac" already built-in
[    17.728] (II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
[    17.728] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    17.728] (==) NVIDIA(0): RGB weight 888
[    17.728] (==) NVIDIA(0): Default visual is TrueColor
[    17.728] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    17.728] (**) NVIDIA(0): Option "NoLogo" "True"
[    17.728] (**) NVIDIA(0): Enabling RENDER acceleration
[    17.728] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[    17.728] (II) NVIDIA(0):     enabled.
[    18.363] (II) NVIDIA(0): NVIDIA GPU GeForce 8800 GTS (G80) at PCI:1:0:0 (GPU-0)
[    18.363] (--) NVIDIA(0): Memory: 327680 kBytes
[    18.363] (--) NVIDIA(0): VideoBIOS: 60.80.18.00.01
[    18.363] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    18.363] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    18.363] (--) NVIDIA(0): Connected display device(s) on GeForce 8800 GTS at PCI:1:0:0:
[    18.363] (--) NVIDIA(0):     Samsung SyncMaster (CRT-1)
[    18.363] (--) NVIDIA(0): Samsung SyncMaster (CRT-1): 400.0 MHz maximum pixel clock
[    18.461] (II) NVIDIA(0): Assigned Display Device: CRT-1
[    18.461] (==) NVIDIA(0): 
[    18.461] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    18.461] (==) NVIDIA(0):     will be used as the requested mode.
[    18.461] (==) NVIDIA(0): 
[    18.461] (II) NVIDIA(0): Validated modes:
[    18.461] (II) NVIDIA(0):     "nvidia-auto-select"
[    18.461] (II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
[    18.486] (--) NVIDIA(0): DPI set to (95, 96); computed from "UseEdidDpi" X config
[    18.486] (--) NVIDIA(0):     option
[    18.486] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[    18.486] (--) Depth 24 pixmap format is 32 bpp
[    18.490] (II) NVIDIA(0): Initialized GPU GART.
[    18.497] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    18.519] (II) Loading extension NV-GLX
[    18.539] (II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
[    18.542] (II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
[    18.542] (==) NVIDIA(0): Backing store disabled
[    18.542] (==) NVIDIA(0): Silken mouse enabled
[    18.547] (==) NVIDIA(0): DPMS enabled
[    18.547] (II) Loading extension NV-CONTROL
[    18.548] (==) RandR enabled
[    18.548] (II) Initializing built-in extension Generic Event Extension
[    18.548] (II) Initializing built-in extension SHAPE
[    18.548] (II) Initializing built-in extension MIT-SHM
[    18.548] (II) Initializing built-in extension XInputExtension
[    18.548] (II) Initializing built-in extension XTEST
[    18.548] (II) Initializing built-in extension BIG-REQUESTS
[    18.548] (II) Initializing built-in extension SYNC
[    18.548] (II) Initializing built-in extension XKEYBOARD
[    18.548] (II) Initializing built-in extension XC-MISC
[    18.548] (II) Initializing built-in extension SECURITY
[    18.548] (II) Initializing built-in extension XINERAMA
[    18.548] (II) Initializing built-in extension XFIXES
[    18.548] (II) Initializing built-in extension RENDER
[    18.548] (II) Initializing built-in extension RANDR
[    18.548] (II) Initializing built-in extension COMPOSITE
[    18.548] (II) Initializing built-in extension DAMAGE
[    18.548] (II) Initializing built-in extension GESTURE
[    18.548] (II) Initializing extension GLX
[    18.584] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    18.593] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    18.593] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    18.593] (II) LoadModule: "evdev"
[    18.594] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.594] (II) Module evdev: vendor="X.Org Foundation"
[    18.594] 	compiled for 1.9.0, module version = 2.3.2
[    18.594] 	Module class: X.Org XInput Driver
[    18.594] 	ABI class: X.Org XInput driver, version 11.0
[    18.594] (**) Power Button: always reports core events
[    18.594] (**) Power Button: Device: "/dev/input/event1"
[    18.600] (II) Power Button: Found keys
[    18.600] (II) Power Button: Configuring as keyboard
[    18.600] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    18.600] (**) Option "xkb_rules" "evdev"
[    18.600] (**) Option "xkb_model" "pc105"
[    18.600] (**) Option "xkb_layout" "be"
[    18.602] (II) XKB: reuse xkmfile /var/lib/xkb/server-BCDBD3DBC93B3E588F97965C4D87FE91FAEC6B41.xkm
[    18.604] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    18.604] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    18.604] (**) Power Button: always reports core events
[    18.604] (**) Power Button: Device: "/dev/input/event0"
[    18.616] (II) Power Button: Found keys
[    18.616] (II) Power Button: Configuring as keyboard
[    18.616] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    18.616] (**) Option "xkb_rules" "evdev"
[    18.616] (**) Option "xkb_model" "pc105"
[    18.616] (**) Option "xkb_layout" "be"
[    18.617] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event2)
[    18.617] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[    18.617] (**) Logitech USB Receiver: always reports core events
[    18.617] (**) Logitech USB Receiver: Device: "/dev/input/event2"
[    18.628] (II) Logitech USB Receiver: Found 20 mouse buttons
[    18.628] (II) Logitech USB Receiver: Found scroll wheel(s)
[    18.628] (II) Logitech USB Receiver: Found relative axes
[    18.628] (II) Logitech USB Receiver: Found x and y relative axes
[    18.628] (II) Logitech USB Receiver: Configuring as mouse
[    18.628] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    18.628] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    18.628] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: MOUSE)
[    18.628] (II) Logitech USB Receiver: initialized for relative axes.
[    18.628] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse0)
[    18.628] (II) No input driver/identifier specified (ignoring)
[    18.629] (II) config/udev: Adding input device Lite-On Technology USB Productivity Option Keyboard( has the hub in # 1 ) (/dev/input/event3)
[    18.629] (**) Lite-On Technology USB Productivity Option Keyboard( has the hub in # 1 ): Applying InputClass "evdev keyboard catchall"
[    18.629] (**) Lite-On Technology USB Productivity Option Keyboard( has the hub in # 1 ): always reports core events
[    18.629] (**) Lite-On Technology USB Productivity Option Keyboard( has the hub in # 1 ): Device: "/dev/input/event3"
[    18.640] (II) Lite-On Technology USB Productivity Option Keyboard( has the hub in # 1 ): Found keys
[    18.640] (II) Lite-On Technology USB Productivity Option Keyboard( has the hub in # 1 ): Configuring as keyboard
[    18.640] (II) XINPUT: Adding extended input device "Lite-On Technology USB Productivity Option Keyboard( has the hub in # 1 )" (type: KEYBOARD)
[    18.640] (**) Option "xkb_rules" "evdev"
[    18.640] (**) Option "xkb_model" "pc105"
[    18.640] (**) Option "xkb_layout" "be"
[    18.640] (II) config/udev: Adding input device Lite-On Technology USB Productivity Option Keyboard( has the hub in # 1 ) (/dev/input/event4)
[    18.640] (**) Lite-On Technology USB Productivity Option Keyboard( has the hub in # 1 ): Applying InputClass "evdev keyboard catchall"
[    18.640] (**) Lite-On Technology USB Productivity Option Keyboard( has the hub in # 1 ): always reports core events
[    18.640] (**) Lite-On Technology USB Productivity Option Keyboard( has the hub in # 1 ): Device: "/dev/input/event4"
[    18.652] (II) Lite-On Technology USB Productivity Option Keyboard( has the hub in # 1 ): Found 12 mouse buttons
[    18.652] (II) Lite-On Technology USB Productivity Option Keyboard( has the hub in # 1 ): Found keys
[    18.652] (II) Lite-On Technology USB Productivity Option Keyboard( has the hub in # 1 ): Configuring as mouse
[    18.652] (II) Lite-On Technology USB Productivity Option Keyboard( has the hub in # 1 ): Configuring as keyboard
[    18.652] (**) Lite-On Technology USB Productivity Option Keyboard( has the hub in # 1 ): YAxisMapping: buttons 4 and 5
[    18.652] (**) Lite-On Technology USB Productivity Option Keyboard( has the hub in # 1 ): EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    18.652] (II) XINPUT: Adding extended input device "Lite-On Technology USB Productivity Option Keyboard( has the hub in # 1 )" (type: KEYBOARD)
[    18.652] (**) Option "xkb_rules" "evdev"
[    18.652] (**) Option "xkb_model" "pc105"
[    18.652] (**) Option "xkb_layout" "be"
[    75.128] (II) XKB: generating xkmfile /var/lib/xkb/server-4A22CD55152AA21ED8325BB615E97BD3D31ED1E3.xkm
[  3908.877] Warning: Xalloc: requesting unpleasantly large amount of memory: 0 bytes.
[  4827.274] Warning: Xalloc: requesting unpleasantly large amount of memory: 0 bytes.

```

---

### Post by jellevictoor on 2010-10-23
This problems keeps persisting, no one who can point me in a direction to where to search the problem?

---

### Post by paultag on 2010-11-05
Bug looks to be reported at:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/636094](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/636094)

Please comment on the bug, thanks!

---

