---
title: "X and GDM not Starting Automatically"
date: 2010-12-12
forum: General Help
---

### Post by Joseph Schwenker on 2010-12-12
I just played around with Plymouth Manager yesterday, and today, my system would not start.  I got some help from #ubuntu, and to my surprise, startx ran without problems.  sudo service gdm start also worked perfectly.  However, when I boot up my computer, I am always taken to the recovery screen.  How can I stop this from happening, get my boot screen back, and make everything work as it should?
I'm on Ubuntu 10.10 32-bit with an nVidia GeForce 8800 GT and version current on the nVidia restricted drivers.

---

### Post by Joseph Schwenker on 2010-12-13
bump
My computer took forever to shut down yesterday--I even tried REISUO, but I ended up just manually shutting it off.

---

### Post by Joseph Schwenker on 2010-12-14
bump
I'm going to try removing an nVidia repository that I added, then reinstalling the nVidia driver.

---

### Post by Joseph Schwenker on 2010-12-15
The placement of applets on my top panel keeps changing around even though all of the applets are locked.  Even after reinstalling the default nVidia drivers, I am still given the recovery menu.  What log files should I be including?

---

### Post by Joseph Schwenker on 2010-12-15
I just ended up missing some chat messages because the mail icon in the indicator applet didn't change like it is supposed to.
Also, when I right click on things, the menu does not appear until I move my mouse pointer onto where the menu is supposed to be.  This only happens some times, though.  Can someone PLEASE help me get my system back to normal?!  I've described everything as best as I can.

---

### Post by Joseph Schwenker on 2010-12-16
Hmm.  Well, the mail icon is working as it should now, though the button arrangement on my panel was all screwed up again today.  I REALLY do need this solved.  
Since I have absolutely no idea which log file to attach, I'll just paste Xorg.0.log here.

```
[    45.836] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    45.836] X Protocol Version 11, Revision 0
[    45.836] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    45.836] Current Operating System: Linux joseph 2.6.35-23-generic #41-Ubuntu SMP Wed Nov 24 10:18:49 UTC 2010 i686
[    45.836] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-23-generic root=UUID=7e0dad5a-4b6d-4bc8-b7c4-61c56290a37f ro single
[    45.836] Build Date: 16 September 2010  05:39:22PM
[    45.836] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
[    45.836] Current version of pixman: 0.18.4
[    45.836] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    45.837] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    45.837] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Dec 16 15:38:55 2010
[    45.837] (==) Using config file: "/etc/X11/xorg.conf"
[    45.837] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    45.837] (==) No Layout section.  Using the first Screen section.
[    45.837] (**) |-->Screen "Default Screen" (0)
[    45.837] (**) |   |-->Monitor "<default monitor>"
[    45.837] (==) No device specified for screen "Default Screen".
	Using the first device section listed.
[    45.837] (**) |   |-->Device "Default Device"
[    45.837] (==) No monitor specified for screen "Default Screen".
	Using a default monitor configuration.
[    45.837] (==) Automatically adding devices
[    45.837] (==) Automatically enabling devices
[    45.837] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    45.837] 	Entry deleted from font path.
[    45.837] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    45.837] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    45.837] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    45.837] (II) Loader magic: 0x81f8e00
[    45.837] (II) Module ABI versions:
[    45.837] 	X.Org ANSI C Emulation: 0.4
[    45.837] 	X.Org Video Driver: 8.0
[    45.837] 	X.Org XInput driver : 11.0
[    45.838] 	X.Org Server Extension : 4.0
[    45.838] (--) PCI:*(0:1:0:0) 10de:0611:196e:053c rev 162, Mem @ 0xfa000000/16777216, 0xd0000000/268435456, 0xf8000000/33554432, I/O @ 0x0000af00/128, BIOS @ 0x????????/131072
[    45.838] (II) Open ACPI successful (/var/run/acpid.socket)
[    45.838] (II) "extmod" will be loaded by default.
[    45.838] (II) "dbe" will be loaded by default.
[    45.838] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    45.838] (II) "record" will be loaded by default.
[    45.838] (II) "dri" will be loaded by default.
[    45.838] (II) "dri2" will be loaded by default.
[    45.838] (II) LoadModule: "glx"
[    45.838] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    45.861] (II) Module glx: vendor="NVIDIA Corporation"
[    45.861] 	compiled for 4.0.2, module version = 1.0.0
[    45.861] 	Module class: X.Org Server Extension
[    45.861] (II) NVIDIA GLX Module  260.19.06  Mon Sep 13 07:01:31 PDT 2010
[    45.861] (II) Loading extension GLX
[    45.861] (II) LoadModule: "extmod"
[    45.888] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    45.888] (II) Module extmod: vendor="X.Org Foundation"
[    45.888] 	compiled for 1.9.0, module version = 1.0.0
[    45.888] 	Module class: X.Org Server Extension
[    45.888] 	ABI class: X.Org Server Extension, version 4.0
[    45.888] (II) Loading extension MIT-SCREEN-SAVER
[    45.888] (II) Loading extension XFree86-VidModeExtension
[    45.888] (II) Loading extension XFree86-DGA
[    45.888] (II) Loading extension DPMS
[    45.888] (II) Loading extension XVideo
[    45.888] (II) Loading extension XVideo-MotionCompensation
[    45.888] (II) Loading extension X-Resource
[    45.888] (II) LoadModule: "dbe"
[    45.889] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    45.889] (II) Module dbe: vendor="X.Org Foundation"
[    45.889] 	compiled for 1.9.0, module version = 1.0.0
[    45.889] 	Module class: X.Org Server Extension
[    45.889] 	ABI class: X.Org Server Extension, version 4.0
[    45.889] (II) Loading extension DOUBLE-BUFFER
[    45.889] (II) LoadModule: "record"
[    45.889] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    45.889] (II) Module record: vendor="X.Org Foundation"
[    45.889] 	compiled for 1.9.0, module version = 1.13.0
[    45.889] 	Module class: X.Org Server Extension
[    45.889] 	ABI class: X.Org Server Extension, version 4.0
[    45.889] (II) Loading extension RECORD
[    45.889] (II) LoadModule: "dri"
[    45.890] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    45.890] (II) Module dri: vendor="X.Org Foundation"
[    45.890] 	compiled for 1.9.0, module version = 1.0.0
[    45.890] 	ABI class: X.Org Server Extension, version 4.0
[    45.890] (II) Loading extension XFree86-DRI
[    45.890] (II) LoadModule: "dri2"
[    45.890] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    45.890] (II) Module dri2: vendor="X.Org Foundation"
[    45.890] 	compiled for 1.9.0, module version = 1.2.0
[    45.890] 	ABI class: X.Org Server Extension, version 4.0
[    45.890] (II) Loading extension DRI2
[    45.890] (II) LoadModule: "nvidia"
[    45.890] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    45.891] (II) Module nvidia: vendor="NVIDIA Corporation"
[    45.891] 	compiled for 4.0.2, module version = 1.0.0
[    45.891] 	Module class: X.Org Video Driver
[    45.891] (II) NVIDIA dlloader X Driver  260.19.06  Mon Sep 13 06:37:13 PDT 2010
[    45.891] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    45.891] (++) using VT number 7

[    45.970] (II) Loading sub module "fb"
[    45.970] (II) LoadModule: "fb"
[    45.970] (II) Loading /usr/lib/xorg/modules/libfb.so
[    45.970] (II) Module fb: vendor="X.Org Foundation"
[    45.970] 	compiled for 1.9.0, module version = 1.0.0
[    45.971] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    45.971] (II) Loading sub module "wfb"
[    45.971] (II) LoadModule: "wfb"
[    45.971] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    45.971] (II) Module wfb: vendor="X.Org Foundation"
[    45.971] 	compiled for 1.9.0, module version = 1.0.0
[    45.971] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    45.971] (II) Loading sub module "ramdac"
[    45.971] (II) LoadModule: "ramdac"
[    45.971] (II) Module "ramdac" already built-in
[    45.971] (II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
[    45.971] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    45.971] (==) NVIDIA(0): RGB weight 888
[    45.971] (==) NVIDIA(0): Default visual is TrueColor
[    45.971] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    45.971] (**) NVIDIA(0): Option "NoLogo" "True"
[    45.971] (**) NVIDIA(0): Enabling RENDER acceleration
[    45.971] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[    45.971] (II) NVIDIA(0):     enabled.
[    46.867] (II) NVIDIA(0): NVIDIA GPU GeForce 8800 GT (G92) at PCI:1:0:0 (GPU-0)
[    46.867] (--) NVIDIA(0): Memory: 524288 kBytes
[    46.867] (--) NVIDIA(0): VideoBIOS: 62.92.23.00.51
[    46.867] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    46.867] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    46.867] (--) NVIDIA(0): Connected display device(s) on GeForce 8800 GT at PCI:1:0:0
[    46.867] (--) NVIDIA(0):     Westinghouse Digital Electronics L1916HW (CRT-0)
[    46.867] (--) NVIDIA(0): Westinghouse Digital Electronics L1916HW (CRT-0): 400.0 MHz
[    46.867] (--) NVIDIA(0):     maximum pixel clock
[    46.933] (II) NVIDIA(0): Assigned Display Device: CRT-0
[    46.934] (==) NVIDIA(0): 
[    46.934] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    46.934] (==) NVIDIA(0):     will be used as the requested mode.
[    46.934] (==) NVIDIA(0): 
[    46.934] (II) NVIDIA(0): Validated modes:
[    46.934] (II) NVIDIA(0):     "nvidia-auto-select"
[    46.934] (II) NVIDIA(0): Virtual screen size determined to be 1680 x 1050
[    46.955] (--) NVIDIA(0): DPI set to (104, 102); computed from "UseEdidDpi" X config
[    46.955] (--) NVIDIA(0):     option
[    46.955] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[    46.955] (--) Depth 24 pixmap format is 32 bpp
[    46.955] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    46.956] (II) NVIDIA(0): Initialized GPU GART.
[    46.962] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    46.983] (II) Loading extension NV-GLX
[    47.011] (II) NVIDIA(0): Initialized OpenGL Acceleration
[    47.022] (==) NVIDIA(0): Disabling shared memory pixmaps
[    47.022] (II) NVIDIA(0): Initialized X Rendering Acceleration
[    47.022] (==) NVIDIA(0): Backing store disabled
[    47.022] (==) NVIDIA(0): Silken mouse enabled
[    47.030] (==) NVIDIA(0): DPMS enabled
[    47.030] (II) Loading extension NV-CONTROL
[    47.030] (II) Loading extension XINERAMA
[    47.030] (II) Loading sub module "dri2"
[    47.030] (II) LoadModule: "dri2"
[    47.031] (II) Reloading /usr/lib/xorg/modules/extensions/libdri2.so
[    47.031] (II) NVIDIA(0): [DRI2] Setup complete
[    47.031] (==) RandR enabled
[    47.031] (II) Initializing built-in extension Generic Event Extension
[    47.031] (II) Initializing built-in extension SHAPE
[    47.031] (II) Initializing built-in extension MIT-SHM
[    47.031] (II) Initializing built-in extension XInputExtension
[    47.031] (II) Initializing built-in extension XTEST
[    47.031] (II) Initializing built-in extension BIG-REQUESTS
[    47.031] (II) Initializing built-in extension SYNC
[    47.031] (II) Initializing built-in extension XKEYBOARD
[    47.031] (II) Initializing built-in extension XC-MISC
[    47.031] (II) Initializing built-in extension SECURITY
[    47.031] (II) Initializing built-in extension XINERAMA
[    47.031] (II) Initializing built-in extension XFIXES
[    47.031] (II) Initializing built-in extension RENDER
[    47.031] (II) Initializing built-in extension RANDR
[    47.031] (II) Initializing built-in extension COMPOSITE
[    47.031] (II) Initializing built-in extension DAMAGE
[    47.031] (II) Initializing built-in extension GESTURE
[    47.031] (II) Initializing extension GLX
[    47.063] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    47.071] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    47.071] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    47.071] (II) LoadModule: "evdev"
[    47.071] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    47.071] (II) Module evdev: vendor="X.Org Foundation"
[    47.071] 	compiled for 1.9.0, module version = 2.3.2
[    47.072] 	Module class: X.Org XInput Driver
[    47.072] 	ABI class: X.Org XInput driver, version 11.0
[    47.072] (**) Power Button: always reports core events
[    47.072] (**) Power Button: Device: "/dev/input/event1"
[    47.084] (II) Power Button: Found keys
[    47.084] (II) Power Button: Configuring as keyboard
[    47.084] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    47.084] (**) Option "xkb_rules" "evdev"
[    47.084] (**) Option "xkb_model" "pc105"
[    47.084] (**) Option "xkb_layout" "us"
[    47.086] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    47.086] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    47.086] (**) Power Button: always reports core events
[    47.086] (**) Power Button: Device: "/dev/input/event0"
[    47.100] (II) Power Button: Found keys
[    47.100] (II) Power Button: Configuring as keyboard
[    47.100] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    47.100] (**) Option "xkb_rules" "evdev"
[    47.100] (**) Option "xkb_model" "pc105"
[    47.100] (**) Option "xkb_layout" "us"
[    47.103] (II) config/udev: Adding input device Plus More Enterprise LTD. USB-compliant keyboard (/dev/input/event3)
[    47.103] (**) Plus More Enterprise LTD. USB-compliant keyboard: Applying InputClass "evdev keyboard catchall"
[    47.104] (**) Plus More Enterprise LTD. USB-compliant keyboard: always reports core events
[    47.104] (**) Plus More Enterprise LTD. USB-compliant keyboard: Device: "/dev/input/event3"
[    47.116] (II) Plus More Enterprise LTD. USB-compliant keyboard: Found keys
[    47.116] (II) Plus More Enterprise LTD. USB-compliant keyboard: Configuring as keyboard
[    47.116] (II) XINPUT: Adding extended input device "Plus More Enterprise LTD. USB-compliant keyboard" (type: KEYBOARD)
[    47.116] (**) Option "xkb_rules" "evdev"
[    47.116] (**) Option "xkb_model" "pc105"
[    47.116] (**) Option "xkb_layout" "us"
[    47.117] (II) config/udev: Adding input device Plus More Enterprise LTD. USB-compliant keyboard (/dev/input/event4)
[    47.117] (**) Plus More Enterprise LTD. USB-compliant keyboard: Applying InputClass "evdev keyboard catchall"
[    47.117] (**) Plus More Enterprise LTD. USB-compliant keyboard: always reports core events
[    47.117] (**) Plus More Enterprise LTD. USB-compliant keyboard: Device: "/dev/input/event4"
[    47.132] (II) Plus More Enterprise LTD. USB-compliant keyboard: Found 1 mouse buttons
[    47.132] (II) Plus More Enterprise LTD. USB-compliant keyboard: Found scroll wheel(s)
[    47.132] (II) Plus More Enterprise LTD. USB-compliant keyboard: Found relative axes
[    47.132] (II) Plus More Enterprise LTD. USB-compliant keyboard: Found x and y relative axes
[    47.132] (II) Plus More Enterprise LTD. USB-compliant keyboard: Found absolute axes
[    47.132] (II) evdev-grail: failed to open grail, no gesture support
[    47.132] (II) Plus More Enterprise LTD. USB-compliant keyboard: Found keys
[    47.132] (II) Plus More Enterprise LTD. USB-compliant keyboard: Configuring as mouse
[    47.132] (II) Plus More Enterprise LTD. USB-compliant keyboard: Configuring as keyboard
[    47.132] (**) Plus More Enterprise LTD. USB-compliant keyboard: YAxisMapping: buttons 4 and 5
[    47.132] (**) Plus More Enterprise LTD. USB-compliant keyboard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    47.132] (II) XINPUT: Adding extended input device "Plus More Enterprise LTD. USB-compliant keyboard" (type: KEYBOARD)
[    47.132] (**) Option "xkb_rules" "evdev"
[    47.132] (**) Option "xkb_model" "pc105"
[    47.132] (**) Option "xkb_layout" "us"
[    47.133] (II) Plus More Enterprise LTD. USB-compliant keyboard: initialized for relative axes.
[    47.133] (WW) Plus More Enterprise LTD. USB-compliant keyboard: ignoring absolute axes.
[    47.133] (II) config/udev: Adding input device Plus More Enterprise LTD. USB-compliant keyboard (/dev/input/mouse0)
[    47.133] (II) No input driver/identifier specified (ignoring)
[    47.134] (II) config/udev: Adding input device zc3xx (/dev/input/event2)
[    47.134] (**) zc3xx: Applying InputClass "evdev keyboard catchall"
[    47.134] (**) zc3xx: always reports core events
[    47.134] (**) zc3xx: Device: "/dev/input/event2"
[    47.148] (II) zc3xx: Found keys
[    47.148] (II) zc3xx: Configuring as keyboard
[    47.148] (II) XINPUT: Adding extended input device "zc3xx" (type: KEYBOARD)
[    47.148] (**) Option "xkb_rules" "evdev"
[    47.148] (**) Option "xkb_model" "pc105"
[    47.148] (**) Option "xkb_layout" "us"
[    47.149] (II) config/udev: Adding input device Dynex 5-Button Wired Optical Mouse (/dev/input/event5)
[    47.149] (**) Dynex 5-Button Wired Optical Mouse: Applying InputClass "evdev pointer catchall"
[    47.149] (**) Dynex 5-Button Wired Optical Mouse: always reports core events
[    47.149] (**) Dynex 5-Button Wired Optical Mouse: Device: "/dev/input/event5"
[    47.164] (II) Dynex 5-Button Wired Optical Mouse: Found 9 mouse buttons
[    47.164] (II) Dynex 5-Button Wired Optical Mouse: Found scroll wheel(s)
[    47.164] (II) Dynex 5-Button Wired Optical Mouse: Found relative axes
[    47.164] (II) Dynex 5-Button Wired Optical Mouse: Found x and y relative axes
[    47.164] (II) Dynex 5-Button Wired Optical Mouse: Configuring as mouse
[    47.164] (**) Dynex 5-Button Wired Optical Mouse: YAxisMapping: buttons 4 and 5
[    47.164] (**) Dynex 5-Button Wired Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    47.164] (II) XINPUT: Adding extended input device "Dynex 5-Button Wired Optical Mouse" (type: MOUSE)
[    47.164] (II) Dynex 5-Button Wired Optical Mouse: initialized for relative axes.
[    47.165] (II) config/udev: Adding input device Dynex 5-Button Wired Optical Mouse (/dev/input/mouse1)
[    47.165] (II) No input driver/identifier specified (ignoring)
[  4450.653] (II) NVIDIA(0): Setting mode "1280x800"
[  4741.649] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
```

---

### Post by Joseph Schwenker on 2010-12-17
Yesterday, my computer did not shut down, and I had to manually shut it down again.  I had the same problems today, but with a few extra surprises.  Don't believe me after the *fifth* day of this unanswered thread?  Take a look at the screenshots.  My panel was screwed up.  My theme was screwed up, then randomly changed back, only to have certain elements not changed back.
In the first screenshot, you can see the screwed up theme.  In the second, you can see the screwed up panel--with an entirely different theme after just opening the Appearance settings, without changing anything.  In the third, you can see that even after the theme appears normal, I have screwed up drop down menus.  Oh, and did I mention that drop down menus still need to have the mouse pointer moved onto them before they are shown for the first time?

Guys--this is bad for my system.  The system is not shutting down normally, and my settings are getting screwed up.  I'll attach any log files that you need, just tell me which ones!

---

### Post by Joseph Schwenker on 2010-12-19
System would not shut down again last night.  This morning my windows had no title bars in Compiz, I had to manually run gtk-window-decorator --replace.  Can I at least get a reply so that I know that there isn't some boycott of this thread that I haven't heard about?  ;)

---

### Post by Joseph Schwenker on 2010-12-20
bump

---

### Post by Joseph Schwenker on 2010-12-22
bump

---

### Post by Joseph Schwenker on 2010-12-24
bump
This issue still persists.

---

### Post by Joseph Schwenker on 2010-12-25
bump
The best Christmas present ever would be this issue solved...

---

### Post by Joseph Schwenker on 2011-01-03
bump
Happy Three Week Anniversary!

---

### Post by Joseph Schwenker on 2011-01-05
bump
CAN I AT LEAST GET ONE REPLY?!

---

### Post by Joseph Schwenker on 2011-01-05
This issue might even be a security problem.  There are options on the recovery menu involving root which may or may not require the root password.  My system is in potential danger.  PLEASE HELP ME!  JESUS!  IT'S BEEN THREE WEEKS!

---

### Post by Joseph Schwenker on 2011-01-05
I just got some help from the people in #ubuntu on IRC.  They solved the problem for me.  The problem was with /etc/default/grub.  

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=>>1680x1050-24<<,mtrr=3,scroll=ywrap"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
GRUB_GFXMODE=640x480
```

This file was my previous grub.  After changing GRUB_CMDLINE_LINUX_DEFAULT= to "quiet splash" (running sudo update-grub after I changed the file, of course) I was able to get a properly functioning system.  Thanks for your help in #ubuntu, guys!

---

