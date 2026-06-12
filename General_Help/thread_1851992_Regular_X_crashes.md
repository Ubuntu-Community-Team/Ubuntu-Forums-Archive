---
title: "Regular X crashes"
date: 2011-09-29
forum: General Help
---

### Post by HeyChinaski on 2011-09-29
Every now and again my work laptop (dell latitude e6520 running ubuntu 11.04) crashes.  I assume this is X crashing as both monitors go blank and after a second the ubuntu login screen reappears.  This used to occur around once a day but today it's got a lot worse.

Any ideas how to diagnose this issue?

---

### Post by 2F4U on 2011-09-29
Look into the file .xsession-errors in your home directory and also into /var/log/Xorg.0.log. What graphics card do you have and what graphics drivers are you using?

---

### Post by HeyChinaski on 2011-09-29
I'm pretty sure I have an NVIDIA NVS 4200M and am using the proprietary Nvidia drivers.

I'm guessing this is the pertinent log output (from .xsession-errors.old):

```
gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
nm-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
gnome-settings-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
applet.py: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
polkit-gnome-authentication-agent-1: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
evolution-alarm-notify: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
gnome-power-manager: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
dropbox: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
<unknown>: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
nautilus: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
bluetooth-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
screenlets-daemon.py: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
no daemon yet
unity-window-decorator: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gnome-terminal: Fatal IO error 104 (Connection reset by peer) on X server :0.
gdu-notification-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
[17090:17090:15363976113:ERROR:browser_main_gtk.cc(75)] X IO Error detected
update-notifier: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
[17295:17295:15363991003:ERROR:x11_util.cc(67)] X IO Error detected
** (process:16018): DEBUG: zeitgeist-datahub.vala:58: Zeitgeist-daemon disappeared from the bus, exitting...

** (process:16018): WARNING **: zeitgeist-datahub.vala:218: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
```


Here's the entirety of Xorg.0.log but I'm guessing this is after the crash. Doesn't seem to be an Xorg.0.log.old :

```
[ 15364.059] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[ 15364.059] X Protocol Version 11, Revision 0
[ 15364.059] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[ 15364.059] Current Operating System: Linux tomm-linux 2.6.38-11-generic-pae #50-Ubuntu SMP Mon Sep 12 22:21:04 UTC 2011 i686
[ 15364.059] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-11-generic-pae root=UUID=32535d65-68a6-407d-8807-36f354cb532b ro quiet splash vt.handoff=7
[ 15364.059] Build Date: 11 August 2011  03:47:56PM
[ 15364.059] xorg-server 2:1.10.1-1ubuntu1.2 (For technical support please see http://www.ubuntu.com/support) 
[ 15364.059] Current version of pixman: 0.20.2
[ 15364.059] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[ 15364.059] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[ 15364.059] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Sep 29 15:40:34 2011
[ 15364.059] (==) Using config file: "/etc/X11/xorg.conf"
[ 15364.059] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[ 15364.059] (==) ServerLayout "Layout0"
[ 15364.059] (**) |-->Screen "Screen0" (0)
[ 15364.059] (**) |   |-->Monitor "Monitor0"
[ 15364.059] (**) |   |-->Device "Device0"
[ 15364.059] (**) |-->Input Device "Keyboard0"
[ 15364.059] (**) |-->Input Device "Mouse0"
[ 15364.059] (**) Option "Xinerama" "0"
[ 15364.059] (==) Automatically adding devices
[ 15364.059] (==) Automatically enabling devices
[ 15364.059] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[ 15364.059] 	Entry deleted from font path.
[ 15364.059] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[ 15364.059] 	Entry deleted from font path.
[ 15364.059] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[ 15364.059] 	Entry deleted from font path.
[ 15364.059] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[ 15364.059] 	Entry deleted from font path.
[ 15364.059] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[ 15364.059] 	Entry deleted from font path.
[ 15364.059] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[ 15364.060] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[ 15364.060] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[ 15364.060] (WW) Disabling Keyboard0
[ 15364.060] (WW) Disabling Mouse0
[ 15364.060] (II) Loader magic: 0x81ffde0
[ 15364.060] (II) Module ABI versions:
[ 15364.060] 	X.Org ANSI C Emulation: 0.4
[ 15364.060] 	X.Org Video Driver: 10.0
[ 15364.060] 	X.Org XInput driver : 12.3
[ 15364.060] 	X.Org Server Extension : 5.0
[ 15364.060] (--) PCI:*(0:1:0:0) 10de:1056:1028:0494 rev 161, Mem @ 0xe4000000/16777216, 0xd0000000/268435456, 0xe0000000/33554432, I/O @ 0x00004000/128, BIOS @ 0x????????/524288
[ 15364.060] (II) Open ACPI successful (/var/run/acpid.socket)
[ 15364.060] (II) LoadModule: "extmod"
[ 15364.061] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[ 15364.061] (II) Module extmod: vendor="X.Org Foundation"
[ 15364.061] 	compiled for 1.10.1, module version = 1.0.0
[ 15364.061] 	Module class: X.Org Server Extension
[ 15364.061] 	ABI class: X.Org Server Extension, version 5.0
[ 15364.061] (II) Loading extension MIT-SCREEN-SAVER
[ 15364.061] (II) Loading extension XFree86-VidModeExtension
[ 15364.061] (II) Loading extension XFree86-DGA
[ 15364.061] (II) Loading extension DPMS
[ 15364.061] (II) Loading extension XVideo
[ 15364.061] (II) Loading extension XVideo-MotionCompensation
[ 15364.061] (II) Loading extension X-Resource
[ 15364.061] (II) LoadModule: "dbe"
[ 15364.061] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[ 15364.061] (II) Module dbe: vendor="X.Org Foundation"
[ 15364.061] 	compiled for 1.10.1, module version = 1.0.0
[ 15364.061] 	Module class: X.Org Server Extension
[ 15364.061] 	ABI class: X.Org Server Extension, version 5.0
[ 15364.061] (II) Loading extension DOUBLE-BUFFER
[ 15364.061] (II) LoadModule: "glx"
[ 15364.061] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[ 15364.074] (II) Module glx: vendor="NVIDIA Corporation"
[ 15364.074] 	compiled for 4.0.2, module version = 1.0.0
[ 15364.074] 	Module class: X.Org Server Extension
[ 15364.074] (II) NVIDIA GLX Module  270.41.06  Mon Apr 18 15:11:28 PDT 2011
[ 15364.074] (II) Loading extension GLX
[ 15364.074] (II) LoadModule: "record"
[ 15364.075] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[ 15364.075] (II) Module record: vendor="X.Org Foundation"
[ 15364.075] 	compiled for 1.10.1, module version = 1.13.0
[ 15364.075] 	Module class: X.Org Server Extension
[ 15364.075] 	ABI class: X.Org Server Extension, version 5.0
[ 15364.075] (II) Loading extension RECORD
[ 15364.075] (II) LoadModule: "dri"
[ 15364.075] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[ 15364.075] (II) Module dri: vendor="X.Org Foundation"
[ 15364.075] 	compiled for 1.10.1, module version = 1.0.0
[ 15364.075] 	ABI class: X.Org Server Extension, version 5.0
[ 15364.075] (II) Loading extension XFree86-DRI
[ 15364.075] (II) LoadModule: "dri2"
[ 15364.076] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[ 15364.076] (II) Module dri2: vendor="X.Org Foundation"
[ 15364.076] 	compiled for 1.10.1, module version = 1.2.0
[ 15364.076] 	ABI class: X.Org Server Extension, version 5.0
[ 15364.076] (II) Loading extension DRI2
[ 15364.076] (II) LoadModule: "nvidia"
[ 15364.076] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[ 15364.076] (II) Module nvidia: vendor="NVIDIA Corporation"
[ 15364.076] 	compiled for 4.0.2, module version = 1.0.0
[ 15364.076] 	Module class: X.Org Video Driver
[ 15364.076] (II) NVIDIA dlloader X Driver  270.41.06  Mon Apr 18 14:55:51 PDT 2011
[ 15364.076] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[ 15364.076] (--) using VT number 9

[ 15364.090] (II) Loading sub module "fb"
[ 15364.090] (II) LoadModule: "fb"
[ 15364.090] (II) Loading /usr/lib/xorg/modules/libfb.so
[ 15364.090] (II) Module fb: vendor="X.Org Foundation"
[ 15364.090] 	compiled for 1.10.1, module version = 1.0.0
[ 15364.090] 	ABI class: X.Org ANSI C Emulation, version 0.4
[ 15364.090] (II) Loading sub module "wfb"
[ 15364.090] (II) LoadModule: "wfb"
[ 15364.090] (II) Loading /usr/lib/xorg/modules/libwfb.so
[ 15364.090] (II) Module wfb: vendor="X.Org Foundation"
[ 15364.090] 	compiled for 1.10.1, module version = 1.0.0
[ 15364.090] 	ABI class: X.Org ANSI C Emulation, version 0.4
[ 15364.090] (II) Loading sub module "ramdac"
[ 15364.090] (II) LoadModule: "ramdac"
[ 15364.090] (II) Module "ramdac" already built-in
[ 15364.090] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[ 15364.090] (II) Loading /usr/lib/xorg/modules/libwfb.so
[ 15364.090] (II) Loading /usr/lib/xorg/modules/libfb.so
[ 15364.090] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[ 15364.090] (==) NVIDIA(0): RGB weight 888
[ 15364.090] (==) NVIDIA(0): Default visual is TrueColor
[ 15364.090] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[ 15364.090] (**) NVIDIA(0): Option "TwinView" "1"
[ 15364.090] (**) NVIDIA(0): Option "MetaModes" "DFP-0: 1920x1080 +1920+0, DFP-5: nvidia-auto-select +0+0"
[ 15364.091] (**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "DFP-0"
[ 15364.481] (II) NVIDIA(GPU-0): Display (Seiko/Epson (DFP-0)) does not support NVIDIA 3D
[ 15364.481] (II) NVIDIA(GPU-0):     Vision stereo.
[ 15364.489] (II) NVIDIA(GPU-0): Display (DELL U2711 (DFP-5)) does not support NVIDIA 3D Vision
[ 15364.489] (II) NVIDIA(GPU-0):     stereo.
[ 15364.490] (II) NVIDIA(0): NVIDIA GPU NVS 4200M (GF119) at PCI:1:0:0 (GPU-0)
[ 15364.490] (--) NVIDIA(0): Memory: 524288 kBytes
[ 15364.490] (--) NVIDIA(0): VideoBIOS: 75.19.17.01.02
[ 15364.490] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[ 15364.490] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[ 15364.490] (--) NVIDIA(0): Connected display device(s) on NVS 4200M at PCI:1:0:0
[ 15364.490] (--) NVIDIA(0):     Seiko/Epson (DFP-0)
[ 15364.490] (--) NVIDIA(0):     DELL U2711 (DFP-5)
[ 15364.490] (--) NVIDIA(0): Seiko/Epson (DFP-0): 330.0 MHz maximum pixel clock
[ 15364.490] (--) NVIDIA(0): Seiko/Epson (DFP-0): Internal Dual Link LVDS
[ 15364.490] (--) NVIDIA(0): DELL U2711 (DFP-5): 480.0 MHz maximum pixel clock
[ 15364.490] (--) NVIDIA(0): DELL U2711 (DFP-5): Internal DisplayPort
[ 15364.492] (**) NVIDIA(0): TwinView enabled
[ 15364.492] (II) NVIDIA(0): Display Devices found referenced in MetaMode: DFP-0, DFP-5
[ 15364.506] (WW) NVIDIA(0): The EDID for DELL U2711 (DFP-5) contradicts itself: mode
[ 15364.506] (WW) NVIDIA(0):     "720x480" is specified in the EDID; however, the EDID's
[ 15364.506] (WW) NVIDIA(0):     valid HorizSync range (29.000-113.000 kHz) would exclude
[ 15364.506] (WW) NVIDIA(0):     this mode's HorizSync (15.7 kHz); ignoring HorizSync check
[ 15364.506] (WW) NVIDIA(0):     for mode "720x480".
[ 15364.506] (WW) NVIDIA(0): The EDID for DELL U2711 (DFP-5) contradicts itself: mode
[ 15364.506] (WW) NVIDIA(0):     "720x576" is specified in the EDID; however, the EDID's
[ 15364.506] (WW) NVIDIA(0):     valid HorizSync range (29.000-113.000 kHz) would exclude
[ 15364.506] (WW) NVIDIA(0):     this mode's HorizSync (15.6 kHz); ignoring HorizSync check
[ 15364.506] (WW) NVIDIA(0):     for mode "720x576".
[ 15364.506] (WW) NVIDIA(0): The EDID for DELL U2711 (DFP-5) contradicts itself: mode
[ 15364.506] (WW) NVIDIA(0):     "720x480" is specified in the EDID; however, the EDID's
[ 15364.506] (WW) NVIDIA(0):     valid HorizSync range (29.000-113.000 kHz) would exclude
[ 15364.506] (WW) NVIDIA(0):     this mode's HorizSync (15.7 kHz); ignoring HorizSync check
[ 15364.506] (WW) NVIDIA(0):     for mode "720x480".
[ 15364.506] (WW) NVIDIA(0): The EDID for DELL U2711 (DFP-5) contradicts itself: mode
[ 15364.506] (WW) NVIDIA(0):     "720x576" is specified in the EDID; however, the EDID's
[ 15364.506] (WW) NVIDIA(0):     valid HorizSync range (29.000-113.000 kHz) would exclude
[ 15364.506] (WW) NVIDIA(0):     this mode's HorizSync (15.6 kHz); ignoring HorizSync check
[ 15364.506] (WW) NVIDIA(0):     for mode "720x576".
[ 15364.506] (WW) NVIDIA(0): The EDID for DELL U2711 (DFP-5) contradicts itself: mode
[ 15364.506] (WW) NVIDIA(0):     "1920x1080" is specified in the EDID; however, the EDID's
[ 15364.506] (WW) NVIDIA(0):     valid HorizSync range (29.000-113.000 kHz) would exclude
[ 15364.506] (WW) NVIDIA(0):     this mode's HorizSync (28.1 kHz); ignoring HorizSync check
[ 15364.506] (WW) NVIDIA(0):     for mode "1920x1080".
[ 15364.506] (WW) NVIDIA(0): The EDID for DELL U2711 (DFP-5) contradicts itself: mode
[ 15364.506] (WW) NVIDIA(0):     "1920x1080" is specified in the EDID; however, the EDID's
[ 15364.506] (WW) NVIDIA(0):     valid HorizSync range (29.000-113.000 kHz) would exclude
[ 15364.506] (WW) NVIDIA(0):     this mode's HorizSync (27.0 kHz); ignoring HorizSync check
[ 15364.506] (WW) NVIDIA(0):     for mode "1920x1080".
[ 15364.506] (WW) NVIDIA(0): The EDID for DELL U2711 (DFP-5) contradicts itself: mode
[ 15364.506] (WW) NVIDIA(0):     "1920x1080" is specified in the EDID; however, the EDID's
[ 15364.506] (WW) NVIDIA(0):     valid VertRefresh range (49.000-86.000 Hz) would exclude
[ 15364.506] (WW) NVIDIA(0):     this mode's VertRefresh (24.0 Hz); ignoring VertRefresh
[ 15364.506] (WW) NVIDIA(0):     check for mode "1920x1080".
[ 15364.510] (WW) NVIDIA(0): The EDID for DELL U2711 (DFP-5) contradicts itself: mode
[ 15364.510] (WW) NVIDIA(0):     "720x480" is specified in the EDID; however, the EDID's
[ 15364.510] (WW) NVIDIA(0):     valid HorizSync range (29.000-113.000 kHz) would exclude
[ 15364.510] (WW) NVIDIA(0):     this mode's HorizSync (15.7 kHz); ignoring HorizSync check
[ 15364.510] (WW) NVIDIA(0):     for mode "720x480".
[ 15364.510] (WW) NVIDIA(0): The EDID for DELL U2711 (DFP-5) contradicts itself: mode
[ 15364.510] (WW) NVIDIA(0):     "720x576" is specified in the EDID; however, the EDID's
[ 15364.510] (WW) NVIDIA(0):     valid HorizSync range (29.000-113.000 kHz) would exclude
[ 15364.510] (WW) NVIDIA(0):     this mode's HorizSync (15.6 kHz); ignoring HorizSync check
[ 15364.510] (WW) NVIDIA(0):     for mode "720x576".
[ 15364.511] (WW) NVIDIA(0): The EDID for DELL U2711 (DFP-5) contradicts itself: mode
[ 15364.511] (WW) NVIDIA(0):     "720x480" is specified in the EDID; however, the EDID's
[ 15364.511] (WW) NVIDIA(0):     valid HorizSync range (29.000-113.000 kHz) would exclude
[ 15364.511] (WW) NVIDIA(0):     this mode's HorizSync (15.7 kHz); ignoring HorizSync check
[ 15364.511] (WW) NVIDIA(0):     for mode "720x480".
[ 15364.513] (WW) NVIDIA(0): The EDID for DELL U2711 (DFP-5) contradicts itself: mode
[ 15364.513] (WW) NVIDIA(0):     "720x576" is specified in the EDID; however, the EDID's
[ 15364.514] (WW) NVIDIA(0):     valid HorizSync range (29.000-113.000 kHz) would exclude
[ 15364.514] (WW) NVIDIA(0):     this mode's HorizSync (15.6 kHz); ignoring HorizSync check
[ 15364.514] (WW) NVIDIA(0):     for mode "720x576".
[ 15364.515] (WW) NVIDIA(0): The EDID for DELL U2711 (DFP-5) contradicts itself: mode
[ 15364.515] (WW) NVIDIA(0):     "1920x1080" is specified in the EDID; however, the EDID's
[ 15364.515] (WW) NVIDIA(0):     valid HorizSync range (29.000-113.000 kHz) would exclude
[ 15364.515] (WW) NVIDIA(0):     this mode's HorizSync (28.1 kHz); ignoring HorizSync check
[ 15364.515] (WW) NVIDIA(0):     for mode "1920x1080".
[ 15364.516] (WW) NVIDIA(0): The EDID for DELL U2711 (DFP-5) contradicts itself: mode
[ 15364.516] (WW) NVIDIA(0):     "1920x1080" is specified in the EDID; however, the EDID's
[ 15364.516] (WW) NVIDIA(0):     valid HorizSync range (29.000-113.000 kHz) would exclude
[ 15364.516] (WW) NVIDIA(0):     this mode's HorizSync (27.0 kHz); ignoring HorizSync check
[ 15364.516] (WW) NVIDIA(0):     for mode "1920x1080".
[ 15364.517] (WW) NVIDIA(0): The EDID for DELL U2711 (DFP-5) contradicts itself: mode
[ 15364.517] (WW) NVIDIA(0):     "1920x1080" is specified in the EDID; however, the EDID's
[ 15364.517] (WW) NVIDIA(0):     valid VertRefresh range (49.000-86.000 Hz) would exclude
[ 15364.517] (WW) NVIDIA(0):     this mode's VertRefresh (24.0 Hz); ignoring VertRefresh
[ 15364.517] (WW) NVIDIA(0):     check for mode "1920x1080".
[ 15364.620] (II) NVIDIA(0): Assigned Display Devices: DFP-0, DFP-5
[ 15364.621] (II) NVIDIA(0): Validated modes:
[ 15364.621] (II) NVIDIA(0):     "DFP-0:1920x1080+1920+0,DFP-5:nvidia-auto-select+0+0"
[ 15364.621] (II) NVIDIA(0): Virtual screen size determined to be 3840 x 1200
[ 15365.156] (--) NVIDIA(0): DPI set to (143, 144); computed from "UseEdidDpi" X config
[ 15365.156] (--) NVIDIA(0):     option
[ 15365.156] (--) Depth 24 pixmap format is 32 bpp
[ 15365.156] (II) NVIDIA: Using 1024.00 MB of virtual memory for indirect memory
[ 15365.156] (II) NVIDIA:     access.
[ 15365.164] (II) NVIDIA(0): Setting mode
[ 15365.164] (II) NVIDIA(0):     "DFP-0:1920x1080+1920+0,DFP-5:nvidia-auto-select+0+0"
[ 15365.165] (WW) NVIDIA(GPU-0): DELL U2711 (DFP-5): Failed to set DisplayPort power state
[ 15365.502] (II) Loading extension NV-GLX
[ 15365.545] (==) NVIDIA(0): Disabling shared memory pixmaps
[ 15365.545] (==) NVIDIA(0): Backing store disabled
[ 15365.545] (==) NVIDIA(0): Silken mouse enabled
[ 15365.545] (**) NVIDIA(0): DPMS enabled
[ 15365.545] (II) Loading extension NV-CONTROL
[ 15365.545] (II) Loading extension XINERAMA
[ 15365.545] (II) Loading sub module "dri2"
[ 15365.545] (II) LoadModule: "dri2"
[ 15365.545] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[ 15365.545] (II) Module dri2: vendor="X.Org Foundation"
[ 15365.545] 	compiled for 1.10.1, module version = 1.2.0
[ 15365.545] 	ABI class: X.Org Server Extension, version 5.0
[ 15365.545] (II) NVIDIA(0): [DRI2] Setup complete
[ 15365.545] (==) RandR enabled
[ 15365.545] (II) Initializing built-in extension Generic Event Extension
[ 15365.545] (II) Initializing built-in extension SHAPE
[ 15365.545] (II) Initializing built-in extension MIT-SHM
[ 15365.545] (II) Initializing built-in extension XInputExtension
[ 15365.545] (II) Initializing built-in extension XTEST
[ 15365.545] (II) Initializing built-in extension BIG-REQUESTS
[ 15365.545] (II) Initializing built-in extension SYNC
[ 15365.545] (II) Initializing built-in extension XKEYBOARD
[ 15365.545] (II) Initializing built-in extension XC-MISC
[ 15365.545] (II) Initializing built-in extension SECURITY
[ 15365.545] (II) Initializing built-in extension XINERAMA
[ 15365.545] (II) Initializing built-in extension XFIXES
[ 15365.545] (II) Initializing built-in extension RENDER
[ 15365.545] (II) Initializing built-in extension RANDR
[ 15365.545] (II) Initializing built-in extension COMPOSITE
[ 15365.545] (II) Initializing built-in extension DAMAGE
[ 15365.545] (II) Initializing built-in extension GESTURE
[ 15365.547] (II) Initializing extension GLX
[ 15365.561] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[ 15365.567] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[ 15365.567] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[ 15365.567] (II) LoadModule: "evdev"
[ 15365.567] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 15365.567] (II) Module evdev: vendor="X.Org Foundation"
[ 15365.567] 	compiled for 1.10.0.902, module version = 2.6.0
[ 15365.567] 	Module class: X.Org XInput Driver
[ 15365.567] 	ABI class: X.Org XInput driver, version 12.3
[ 15365.567] (II) Using input driver 'evdev' for 'Power Button'
[ 15365.567] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 15365.567] (**) Power Button: always reports core events
[ 15365.567] (**) Power Button: Device: "/dev/input/event3"
[ 15365.567] (--) Power Button: Found keys
[ 15365.567] (II) Power Button: Configuring as keyboard
[ 15365.567] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[ 15365.567] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[ 15365.568] (**) Option "xkb_rules" "evdev"
[ 15365.568] (**) Option "xkb_model" "pc105"
[ 15365.568] (**) Option "xkb_layout" "gb"
[ 15365.574] (II) XKB: reuse xkmfile /var/lib/xkb/server-2B4266AA55228AE7D9557A18F1965DBA19850816.xkm
[ 15365.580] (II) config/udev: Adding input device Video Bus (/dev/input/event14)
[ 15365.580] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[ 15365.580] (II) Using input driver 'evdev' for 'Video Bus'
[ 15365.580] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 15365.580] (**) Video Bus: always reports core events
[ 15365.580] (**) Video Bus: Device: "/dev/input/event14"
[ 15365.580] (--) Video Bus: Found keys
[ 15365.580] (II) Video Bus: Configuring as keyboard
[ 15365.580] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:13/LNXVIDEO:00/input/input14/event14"
[ 15365.580] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[ 15365.580] (**) Option "xkb_rules" "evdev"
[ 15365.580] (**) Option "xkb_model" "pc105"
[ 15365.580] (**) Option "xkb_layout" "gb"
[ 15365.584] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[ 15365.584] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[ 15365.584] (II) Using input driver 'evdev' for 'Power Button'
[ 15365.584] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 15365.584] (**) Power Button: always reports core events
[ 15365.584] (**) Power Button: Device: "/dev/input/event1"
[ 15365.584] (--) Power Button: Found keys
[ 15365.584] (II) Power Button: Configuring as keyboard
[ 15365.584] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[ 15365.584] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[ 15365.584] (**) Option "xkb_rules" "evdev"
[ 15365.584] (**) Option "xkb_model" "pc105"
[ 15365.584] (**) Option "xkb_layout" "gb"
[ 15365.585] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[ 15365.585] (II) No input driver/identifier specified (ignoring)
[ 15365.585] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[ 15365.585] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[ 15365.585] (II) Using input driver 'evdev' for 'Sleep Button'
[ 15365.585] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 15365.585] (**) Sleep Button: always reports core events
[ 15365.585] (**) Sleep Button: Device: "/dev/input/event2"
[ 15365.585] (--) Sleep Button: Found keys
[ 15365.585] (II) Sleep Button: Configuring as keyboard
[ 15365.585] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2"
[ 15365.585] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[ 15365.585] (**) Option "xkb_rules" "evdev"
[ 15365.585] (**) Option "xkb_model" "pc105"
[ 15365.585] (**) Option "xkb_layout" "gb"
[ 15365.587] (II) config/udev: Adding input device Laptop_Integrated_Webcam_FHD (/dev/input/event7)
[ 15365.587] (**) Laptop_Integrated_Webcam_FHD: Applying InputClass "evdev keyboard catchall"
[ 15365.587] (II) Using input driver 'evdev' for 'Laptop_Integrated_Webcam_FHD'
[ 15365.587] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 15365.587] (**) Laptop_Integrated_Webcam_FHD: always reports core events
[ 15365.587] (**) Laptop_Integrated_Webcam_FHD: Device: "/dev/input/event7"
[ 15365.587] (--) Laptop_Integrated_Webcam_FHD: Found keys
[ 15365.587] (II) Laptop_Integrated_Webcam_FHD: Configuring as keyboard
[ 15365.587] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/input/input7/event7"
[ 15365.587] (II) XINPUT: Adding extended input device "Laptop_Integrated_Webcam_FHD" (type: KEYBOARD)
[ 15365.587] (**) Option "xkb_rules" "evdev"
[ 15365.587] (**) Option "xkb_model" "pc105"
[ 15365.587] (**) Option "xkb_layout" "gb"
[ 15365.589] (II) config/udev: Adding input device HDA Intel PCH Mic at Sep Left Jack (/dev/input/event10)
[ 15365.589] (II) No input driver/identifier specified (ignoring)
[ 15365.589] (II) config/udev: Adding input device HDA Intel PCH Mic at Ext Left Jack (/dev/input/event11)
[ 15365.589] (II) No input driver/identifier specified (ignoring)
[ 15365.589] (II) config/udev: Adding input device HDA Intel PCH Line Out at Sep Left Jack (/dev/input/event12)
[ 15365.589] (II) No input driver/identifier specified (ignoring)
[ 15365.589] (II) config/udev: Adding input device HDA Intel PCH HP Out at Ext Left Jack (/dev/input/event13)
[ 15365.589] (II) No input driver/identifier specified (ignoring)
[ 15365.591] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event5)
[ 15365.591] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[ 15365.591] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[ 15365.591] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 15365.592] (**) Logitech USB Receiver: always reports core events
[ 15365.592] (**) Logitech USB Receiver: Device: "/dev/input/event5"
[ 15365.592] (--) Logitech USB Receiver: Found keys
[ 15365.592] (II) Logitech USB Receiver: Configuring as keyboard
[ 15365.592] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/input/input5/event5"
[ 15365.592] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[ 15365.592] (**) Option "xkb_rules" "evdev"
[ 15365.592] (**) Option "xkb_model" "pc105"
[ 15365.592] (**) Option "xkb_layout" "gb"
[ 15365.592] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event6)
[ 15365.592] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[ 15365.592] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[ 15365.592] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[ 15365.592] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 15365.592] (**) Logitech USB Receiver: always reports core events
[ 15365.592] (**) Logitech USB Receiver: Device: "/dev/input/event6"
[ 15365.592] (--) Logitech USB Receiver: Found 20 mouse buttons
[ 15365.592] (--) Logitech USB Receiver: Found scroll wheel(s)
[ 15365.592] (--) Logitech USB Receiver: Found relative axes
[ 15365.592] (--) Logitech USB Receiver: Found x and y relative axes
[ 15365.592] (--) Logitech USB Receiver: Found absolute axes
[ 15365.593] (II) evdev-grail: failed to open grail, no gesture support
[ 15365.593] (--) Logitech USB Receiver: Found keys
[ 15365.593] (II) Logitech USB Receiver: Configuring as mouse
[ 15365.593] (II) Logitech USB Receiver: Configuring as keyboard
[ 15365.593] (II) Logitech USB Receiver: Adding scrollwheel support
[ 15365.593] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[ 15365.593] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[ 15365.593] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.1/input/input6/event6"
[ 15365.593] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[ 15365.593] (**) Option "xkb_rules" "evdev"
[ 15365.593] (**) Option "xkb_model" "pc105"
[ 15365.593] (**) Option "xkb_layout" "gb"
[ 15365.593] (II) Logitech USB Receiver: initialized for relative axes.
[ 15365.593] (WW) Logitech USB Receiver: ignoring absolute axes.
[ 15365.593] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[ 15365.593] (**) Logitech USB Receiver: (accel) acceleration profile 0
[ 15365.593] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[ 15365.593] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[ 15365.594] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse0)
[ 15365.594] (II) No input driver/identifier specified (ignoring)
[ 15365.599] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[ 15365.599] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[ 15365.599] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[ 15365.599] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 15365.599] (**) AT Translated Set 2 keyboard: always reports core events
[ 15365.599] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[ 15365.599] (--) AT Translated Set 2 keyboard: Found keys
[ 15365.599] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[ 15365.599] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[ 15365.599] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[ 15365.599] (**) Option "xkb_rules" "evdev"
[ 15365.599] (**) Option "xkb_model" "pc105"
[ 15365.599] (**) Option "xkb_layout" "gb"
[ 15365.600] (II) config/udev: Adding input device ImPS/2 ALPS GlidePoint (/dev/input/event9)
[ 15365.600] (**) ImPS/2 ALPS GlidePoint: Applying InputClass "evdev pointer catchall"
[ 15365.600] (II) Using input driver 'evdev' for 'ImPS/2 ALPS GlidePoint'
[ 15365.600] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 15365.601] (**) ImPS/2 ALPS GlidePoint: always reports core events
[ 15365.601] (**) ImPS/2 ALPS GlidePoint: Device: "/dev/input/event9"
[ 15365.601] (--) ImPS/2 ALPS GlidePoint: Found 3 mouse buttons
[ 15365.601] (--) ImPS/2 ALPS GlidePoint: Found scroll wheel(s)
[ 15365.601] (--) ImPS/2 ALPS GlidePoint: Found relative axes
[ 15365.601] (--) ImPS/2 ALPS GlidePoint: Found x and y relative axes
[ 15365.601] (II) ImPS/2 ALPS GlidePoint: Configuring as mouse
[ 15365.601] (II) ImPS/2 ALPS GlidePoint: Adding scrollwheel support
[ 15365.601] (**) ImPS/2 ALPS GlidePoint: YAxisMapping: buttons 4 and 5
[ 15365.601] (**) ImPS/2 ALPS GlidePoint: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[ 15365.601] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input9/event9"
[ 15365.601] (II) XINPUT: Adding extended input device "ImPS/2 ALPS GlidePoint" (type: MOUSE)
[ 15365.601] (II) ImPS/2 ALPS GlidePoint: initialized for relative axes.
[ 15365.601] (**) ImPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
[ 15365.601] (**) ImPS/2 ALPS GlidePoint: (accel) acceleration profile 0
[ 15365.601] (**) ImPS/2 ALPS GlidePoint: (accel) acceleration factor: 2.000
[ 15365.601] (**) ImPS/2 ALPS GlidePoint: (accel) acceleration threshold: 4
[ 15365.601] (II) config/udev: Adding input device ImPS/2 ALPS GlidePoint (/dev/input/mouse1)
[ 15365.601] (II) No input driver/identifier specified (ignoring)
[ 15365.608] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event8)
[ 15365.608] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[ 15365.608] (II) Using input driver 'evdev' for 'Dell WMI hotkeys'
[ 15365.608] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 15365.608] (**) Dell WMI hotkeys: always reports core events
[ 15365.608] (**) Dell WMI hotkeys: Device: "/dev/input/event8"
[ 15365.609] (--) Dell WMI hotkeys: Found keys
[ 15365.609] (II) Dell WMI hotkeys: Configuring as keyboard
[ 15365.609] (**) Option "config_info" "udev:/sys/devices/virtual/input/input8/event8"
[ 15365.609] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD)
[ 15365.609] (**) Option "xkb_rules" "evdev"
[ 15365.609] (**) Option "xkb_model" "pc105"
[ 15365.609] (**) Option "xkb_layout" "gb"

```

---

### Post by HeyChinaski on 2011-09-30
It happened again.  Here is the Xorg.0.log:

```
Release Date: 2011-04-15
[     5.773] X Protocol Version 11, Revision 0
[     5.773] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[     5.773] Current Operating System: Linux tomm-linux 2.6.38-11-generic-pae #50-Ubuntu SMP Mon Sep 12 22:21:04 UTC 2011 i686
[     5.773] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-11-generic-pae root=UUID=32535d65-68a6-407d-8807-36f354cb532b ro quiet splash vt.handoff=7
[     5.773] Build Date: 11 August 2011  03:47:56PM
[     5.773] xorg-server 2:1.10.1-1ubuntu1.2 (For technical support please see http://www.ubuntu.com/support) 
[     5.773] Current version of pixman: 0.20.2
[     5.773] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[     5.773] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     5.773] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Sep 30 09:07:34 2011
[     5.773] (==) Using config file: "/etc/X11/xorg.conf"
[     5.773] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     5.773] (==) ServerLayout "Layout0"
[     5.773] (**) |-->Screen "Screen0" (0)
[     5.773] (**) |   |-->Monitor "Monitor0"
[     5.773] (**) |   |-->Device "Device0"
[     5.773] (**) |-->Input Device "Keyboard0"
[     5.773] (**) |-->Input Device "Mouse0"
[     5.773] (**) Option "Xinerama" "0"
[     5.773] (==) Automatically adding devices
[     5.773] (==) Automatically enabling devices
[     5.774] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     5.774] 	Entry deleted from font path.
[     5.774] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     5.774] 	Entry deleted from font path.
[     5.774] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     5.774] 	Entry deleted from font path.
[     5.774] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     5.774] 	Entry deleted from font path.
[     5.774] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     5.774] 	Entry deleted from font path.
[     5.774] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[     5.774] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     5.774] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[     5.774] (WW) Disabling Keyboard0
[     5.774] (WW) Disabling Mouse0
[     5.774] (II) Loader magic: 0x81ffde0
[     5.774] (II) Module ABI versions:
[     5.774] 	X.Org ANSI C Emulation: 0.4
[     5.774] 	X.Org Video Driver: 10.0
[     5.774] 	X.Org XInput driver : 12.3
[     5.774] 	X.Org Server Extension : 5.0
[     5.774] (--) PCI:*(0:1:0:0) 10de:1056:1028:0494 rev 161, Mem @ 0xe4000000/16777216, 0xd0000000/268435456, 0xe0000000/33554432, I/O @ 0x00004000/128, BIOS @ 0x????????/524288
[     5.775] (II) Open ACPI successful (/var/run/acpid.socket)
[     5.775] (II) LoadModule: "extmod"
[     5.790] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[     5.790] (II) Module extmod: vendor="X.Org Foundation"
[     5.790] 	compiled for 1.10.1, module version = 1.0.0
[     5.790] 	Module class: X.Org Server Extension
[     5.790] 	ABI class: X.Org Server Extension, version 5.0
[     5.790] (II) Loading extension MIT-SCREEN-SAVER
[     5.790] (II) Loading extension XFree86-VidModeExtension
[     5.790] (II) Loading extension XFree86-DGA
[     5.790] (II) Loading extension DPMS
[     5.790] (II) Loading extension XVideo
[     5.790] (II) Loading extension XVideo-MotionCompensation
[     5.790] (II) Loading extension X-Resource
[     5.790] (II) LoadModule: "dbe"
[     5.791] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[     5.791] (II) Module dbe: vendor="X.Org Foundation"
[     5.791] 	compiled for 1.10.1, module version = 1.0.0
[     5.791] 	Module class: X.Org Server Extension
[     5.791] 	ABI class: X.Org Server Extension, version 5.0
[     5.791] (II) Loading extension DOUBLE-BUFFER
[     5.791] (II) LoadModule: "glx"
[     5.791] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[     5.804] (II) Module glx: vendor="NVIDIA Corporation"
[     5.804] 	compiled for 4.0.2, module version = 1.0.0
[     5.804] 	Module class: X.Org Server Extension
[     5.804] (II) NVIDIA GLX Module  270.41.06  Mon Apr 18 15:11:28 PDT 2011
[     5.804] (II) Loading extension GLX
[     5.804] (II) LoadModule: "record"
[     5.804] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[     5.804] (II) Module record: vendor="X.Org Foundation"
[     5.804] 	compiled for 1.10.1, module version = 1.13.0
[     5.804] 	Module class: X.Org Server Extension
[     5.804] 	ABI class: X.Org Server Extension, version 5.0
[     5.804] (II) Loading extension RECORD
[     5.804] (II) LoadModule: "dri"
[     5.804] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[     5.805] (II) Module dri: vendor="X.Org Foundation"
[     5.805] 	compiled for 1.10.1, module version = 1.0.0
[     5.805] 	ABI class: X.Org Server Extension, version 5.0
[     5.805] (II) Loading extension XFree86-DRI
[     5.805] (II) LoadModule: "dri2"
[     5.805] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[     5.805] (II) Module dri2: vendor="X.Org Foundation"
[     5.805] 	compiled for 1.10.1, module version = 1.2.0
[     5.805] 	ABI class: X.Org Server Extension, version 5.0
[     5.805] (II) Loading extension DRI2
[     5.805] (II) LoadModule: "nvidia"
[     5.805] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[     5.805] (II) Module nvidia: vendor="NVIDIA Corporation"
[     5.805] 	compiled for 4.0.2, module version = 1.0.0
[     5.805] 	Module class: X.Org Video Driver
[     5.805] (II) NVIDIA dlloader X Driver  270.41.06  Mon Apr 18 14:55:51 PDT 2011
[     5.806] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[     5.806] (++) using VT number 7

[     5.806] (II) Loading sub module "fb"
[     5.806] (II) LoadModule: "fb"
[     5.806] (II) Loading /usr/lib/xorg/modules/libfb.so
[     5.806] (II) Module fb: vendor="X.Org Foundation"
[     5.806] 	compiled for 1.10.1, module version = 1.0.0
[     5.806] 	ABI class: X.Org ANSI C Emulation, version 0.4
[     5.806] (II) Loading sub module "wfb"
[     5.806] (II) LoadModule: "wfb"
[     5.806] (II) Loading /usr/lib/xorg/modules/libwfb.so
[     5.806] (II) Module wfb: vendor="X.Org Foundation"
[     5.806] 	compiled for 1.10.1, module version = 1.0.0
[     5.806] 	ABI class: X.Org ANSI C Emulation, version 0.4
[     5.806] (II) Loading sub module "ramdac"
[     5.806] (II) LoadModule: "ramdac"
[     5.806] (II) Module "ramdac" already built-in
[     5.806] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[     5.806] (II) Loading /usr/lib/xorg/modules/libwfb.so
[     5.806] (II) Loading /usr/lib/xorg/modules/libfb.so
[     5.806] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[     5.807] (==) NVIDIA(0): RGB weight 888
[     5.807] (==) NVIDIA(0): Default visual is TrueColor
[     5.807] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[     5.807] (**) NVIDIA(0): Option "TwinView" "1"
[     5.807] (**) NVIDIA(0): Option "MetaModes" "DFP-0: 1920x1080 +1920+0, DFP-5: nvidia-auto-select +0+0"
[     5.807] (**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "DFP-0"
[     6.672] (II) NVIDIA(GPU-0): Display (Seiko/Epson (DFP-0)) does not support NVIDIA 3D
[     6.672] (II) NVIDIA(GPU-0):     Vision stereo.
[     6.680] (II) NVIDIA(GPU-0): Display (DELL U2711 (DFP-5)) does not support NVIDIA 3D Vision
[     6.680] (II) NVIDIA(GPU-0):     stereo.
[     6.681] (II) NVIDIA(0): NVIDIA GPU NVS 4200M (GF119) at PCI:1:0:0 (GPU-0)
[     6.681] (--) NVIDIA(0): Memory: 524288 kBytes
[     6.681] (--) NVIDIA(0): VideoBIOS: 75.19.17.01.02
[     6.681] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[     6.681] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[     6.681] (--) NVIDIA(0): Connected display device(s) on NVS 4200M at PCI:1:0:0
[     6.681] (--) NVIDIA(0):     Seiko/Epson (DFP-0)
[     6.681] (--) NVIDIA(0):     DELL U2711 (DFP-5)
[     6.681] (--) NVIDIA(0): Seiko/Epson (DFP-0): 330.0 MHz maximum pixel clock
[     6.681] (--) NVIDIA(0): Seiko/Epson (DFP-0): Internal Dual Link LVDS
[     6.681] (--) NVIDIA(0): DELL U2711 (DFP-5): 480.0 MHz maximum pixel clock
[     6.681] (--) NVIDIA(0): DELL U2711 (DFP-5): Internal DisplayPort
[     6.683] (**) NVIDIA(0): TwinView enabled
[     6.683] (II) NVIDIA(0): Display Devices found referenced in MetaMode: DFP-0, DFP-5
[     6.701] (WW) NVIDIA(0): The EDID for DELL U2711 (DFP-5) contradicts itself: mode
[     6.701] (WW) NVIDIA(0):     "720x480" is specified in the EDID; however, the EDID's
[     6.701] (WW) NVIDIA(0):     valid HorizSync range (29.000-113.000 kHz) would exclude
[     6.701] (WW) NVIDIA(0):     this mode's HorizSync (15.7 kHz); ignoring HorizSync check
[     6.701] (WW) NVIDIA(0):     for mode "720x480".
[     6.701] (WW) NVIDIA(0): The EDID for DELL U2711 (DFP-5) contradicts itself: mode
[     6.701] (WW) NVIDIA(0):     "720x576" is specified in the EDID; however, the EDID's
[     6.701] (WW) NVIDIA(0):     valid HorizSync range (29.000-113.000 kHz) would exclude
[     6.701] (WW) NVIDIA(0):     this mode's HorizSync (15.6 kHz); ignoring HorizSync check
[     6.701] (WW) NVIDIA(0):     for mode "720x576".
[     6.701] (WW) NVIDIA(0): The EDID for DELL U2711 (DFP-5) contradicts itself: mode
[     6.701] (WW) NVIDIA(0):     "720x480" is specified in the EDID; however, the EDID's
[     6.701] (WW) NVIDIA(0):     valid HorizSync range (29.000-113.000 kHz) would exclude
[     6.701] (WW) NVIDIA(0):     this mode's HorizSync (15.7 kHz); ignoring HorizSync check
[     6.701] (WW) NVIDIA(0):     for mode "720x480".
[     6.701] (WW) NVIDIA(0): The EDID for DELL U2711 (DFP-5) contradicts itself: mode
[     6.701] (WW) NVIDIA(0):     "720x576" is specified in the EDID; however, the EDID's
[     6.701] (WW) NVIDIA(0):     valid HorizSync range (29.000-113.000 kHz) would exclude
[     6.701] (WW) NVIDIA(0):     this mode's HorizSync (15.6 kHz); ignoring HorizSync check
[     6.701] (WW) NVIDIA(0):     for mode "720x576".
[     6.701] (WW) NVIDIA(0): The EDID for DELL U2711 (DFP-5) contradicts itself: mode
[     6.701] (WW) NVIDIA(0):     "1920x1080" is specified in the EDID; however, the EDID's
[     6.701] (WW) NVIDIA(0):     valid HorizSync range (29.000-113.000 kHz) would exclude
[     6.702] (WW) NVIDIA(0):     this mode's HorizSync (28.1 kHz); ignoring HorizSync check
[     6.702] (WW) NVIDIA(0):     for mode "1920x1080".
[     6.702] (WW) NVIDIA(0): The EDID for DELL U2711 (DFP-5) contradicts itself: mode
[     6.702] (WW) NVIDIA(0):     "1920x1080" is specified in the EDID; however, the EDID's
[     6.702] (WW) NVIDIA(0):     valid HorizSync range (29.000-113.000 kHz) would exclude
[     6.702] (WW) NVIDIA(0):     this mode's HorizSync (27.0 kHz); ignoring HorizSync check
[     6.702] (WW) NVIDIA(0):     for mode "1920x1080".
[     6.702] (WW) NVIDIA(0): The EDID for DELL U2711 (DFP-5) contradicts itself: mode
[     6.702] (WW) NVIDIA(0):     "1920x1080" is specified in the EDID; however, the EDID's
[     6.702] (WW) NVIDIA(0):     valid VertRefresh range (49.000-86.000 Hz) would exclude
[     6.702] (WW) NVIDIA(0):     this mode's VertRefresh (24.0 Hz); ignoring VertRefresh
[     6.702] (WW) NVIDIA(0):     check for mode "1920x1080".
[     6.706] (WW) NVIDIA(0): The EDID for DELL U2711 (DFP-5) contradicts itself: mode
[     6.706] (WW) NVIDIA(0):     "720x480" is specified in the EDID; however, the EDID's
[     6.706] (WW) NVIDIA(0):     valid HorizSync range (29.000-113.000 kHz) would exclude
[     6.706] (WW) NVIDIA(0):     this mode's HorizSync (15.7 kHz); ignoring HorizSync check
[     6.706] (WW) NVIDIA(0):     for mode "720x480".
[     6.706] (WW) NVIDIA(0): The EDID for DELL U2711 (DFP-5) contradicts itself: mode
[     6.706] (WW) NVIDIA(0):     "720x576" is specified in the EDID; however, the EDID's
[     6.706] (WW) NVIDIA(0):     valid HorizSync range (29.000-113.000 kHz) would exclude
[     6.706] (WW) NVIDIA(0):     this mode's HorizSync (15.6 kHz); ignoring HorizSync check
[     6.706] (WW) NVIDIA(0):     for mode "720x576".
[     6.707] (WW) NVIDIA(0): The EDID for DELL U2711 (DFP-5) contradicts itself: mode
[     6.707] (WW) NVIDIA(0):     "720x480" is specified in the EDID; however, the EDID's
[     6.707] (WW) NVIDIA(0):     valid HorizSync range (29.000-113.000 kHz) would exclude
[     6.707] (WW) NVIDIA(0):     this mode's HorizSync (15.7 kHz); ignoring HorizSync check
[     6.707] (WW) NVIDIA(0):     for mode "720x480".
[     6.709] (WW) NVIDIA(0): The EDID for DELL U2711 (DFP-5) contradicts itself: mode
[     6.709] (WW) NVIDIA(0):     "720x576" is specified in the EDID; however, the EDID's
[     6.709] (WW) NVIDIA(0):     valid HorizSync range (29.000-113.000 kHz) would exclude
[     6.709] (WW) NVIDIA(0):     this mode's HorizSync (15.6 kHz); ignoring HorizSync check
[     6.709] (WW) NVIDIA(0):     for mode "720x576".
[     6.709] (WW) NVIDIA(0): The EDID for DELL U2711 (DFP-5) contradicts itself: mode
[     6.709] (WW) NVIDIA(0):     "1920x1080" is specified in the EDID; however, the EDID's
[     6.709] (WW) NVIDIA(0):     valid HorizSync range (29.000-113.000 kHz) would exclude
[     6.709] (WW) NVIDIA(0):     this mode's HorizSync (28.1 kHz); ignoring HorizSync check
[     6.709] (WW) NVIDIA(0):     for mode "1920x1080".
[     6.710] (WW) NVIDIA(0): The EDID for DELL U2711 (DFP-5) contradicts itself: mode
[     6.710] (WW) NVIDIA(0):     "1920x1080" is specified in the EDID; however, the EDID's
[     6.710] (WW) NVIDIA(0):     valid HorizSync range (29.000-113.000 kHz) would exclude
[     6.710] (WW) NVIDIA(0):     this mode's HorizSync (27.0 kHz); ignoring HorizSync check
[     6.710] (WW) NVIDIA(0):     for mode "1920x1080".
[     6.710] (WW) NVIDIA(0): The EDID for DELL U2711 (DFP-5) contradicts itself: mode
[     6.710] (WW) NVIDIA(0):     "1920x1080" is specified in the EDID; however, the EDID's
[     6.710] (WW) NVIDIA(0):     valid VertRefresh range (49.000-86.000 Hz) would exclude
[     6.710] (WW) NVIDIA(0):     this mode's VertRefresh (24.0 Hz); ignoring VertRefresh
[     6.710] (WW) NVIDIA(0):     check for mode "1920x1080".
[     6.806] (II) NVIDIA(0): Assigned Display Devices: DFP-0, DFP-5
[     6.806] (II) NVIDIA(0): Validated modes:
[     6.806] (II) NVIDIA(0):     "DFP-0:1920x1080+1920+0,DFP-5:nvidia-auto-select+0+0"
[     6.806] (II) NVIDIA(0): Virtual screen size determined to be 3840 x 1200
[     7.339] (--) NVIDIA(0): DPI set to (143, 144); computed from "UseEdidDpi" X config
[     7.339] (--) NVIDIA(0):     option
[     7.339] (--) Depth 24 pixmap format is 32 bpp
[     7.340] (II) NVIDIA: Using 1024.00 MB of virtual memory for indirect memory
[     7.340] (II) NVIDIA:     access.
[     7.344] (II) NVIDIA(0): Setting mode
[     7.344] (II) NVIDIA(0):     "DFP-0:1920x1080+1920+0,DFP-5:nvidia-auto-select+0+0"
[     7.344] (WW) NVIDIA(GPU-0): DELL U2711 (DFP-5): Failed to set DisplayPort power state
[     7.681] (II) Loading extension NV-GLX
[     7.723] (==) NVIDIA(0): Disabling shared memory pixmaps
[     7.723] (==) NVIDIA(0): Backing store disabled
[     7.723] (==) NVIDIA(0): Silken mouse enabled
[     7.723] (**) NVIDIA(0): DPMS enabled
[     7.723] (II) Loading extension NV-CONTROL
[     7.723] (II) Loading extension XINERAMA
[     7.723] (II) Loading sub module "dri2"
[     7.723] (II) LoadModule: "dri2"
[     7.724] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[     7.724] (II) Module dri2: vendor="X.Org Foundation"
[     7.724] 	compiled for 1.10.1, module version = 1.2.0
[     7.724] 	ABI class: X.Org Server Extension, version 5.0
[     7.724] (II) NVIDIA(0): [DRI2] Setup complete
[     7.724] (==) RandR enabled
[     7.724] (II) Initializing built-in extension Generic Event Extension
[     7.724] (II) Initializing built-in extension SHAPE
[     7.724] (II) Initializing built-in extension MIT-SHM
[     7.724] (II) Initializing built-in extension XInputExtension
[     7.724] (II) Initializing built-in extension XTEST
[     7.724] (II) Initializing built-in extension BIG-REQUESTS
[     7.724] (II) Initializing built-in extension SYNC
[     7.724] (II) Initializing built-in extension XKEYBOARD
[     7.724] (II) Initializing built-in extension XC-MISC
[     7.724] (II) Initializing built-in extension SECURITY
[     7.724] (II) Initializing built-in extension XINERAMA
[     7.724] (II) Initializing built-in extension XFIXES
[     7.724] (II) Initializing built-in extension RENDER
[     7.724] (II) Initializing built-in extension RANDR
[     7.724] (II) Initializing built-in extension COMPOSITE
[     7.724] (II) Initializing built-in extension DAMAGE
[     7.724] (II) Initializing built-in extension GESTURE
[     7.725] (II) Initializing extension GLX
[     7.739] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[     7.745] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[     7.745] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     7.745] (II) LoadModule: "evdev"
[     7.745] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     7.745] (II) Module evdev: vendor="X.Org Foundation"
[     7.745] 	compiled for 1.10.0.902, module version = 2.6.0
[     7.745] 	Module class: X.Org XInput Driver
[     7.745] 	ABI class: X.Org XInput driver, version 12.3
[     7.745] (II) Using input driver 'evdev' for 'Power Button'
[     7.745] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     7.745] (**) Power Button: always reports core events
[     7.745] (**) Power Button: Device: "/dev/input/event3"
[     7.764] (--) Power Button: Found keys
[     7.764] (II) Power Button: Configuring as keyboard
[     7.764] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[     7.764] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[     7.764] (**) Option "xkb_rules" "evdev"
[     7.764] (**) Option "xkb_model" "pc105"
[     7.764] (**) Option "xkb_layout" "gb"
[     7.765] (II) XKB: reuse xkmfile /var/lib/xkb/server-2B4266AA55228AE7D9557A18F1965DBA19850816.xkm
[     7.767] (II) config/udev: Adding input device Video Bus (/dev/input/event14)
[     7.767] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[     7.767] (II) Using input driver 'evdev' for 'Video Bus'
[     7.767] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     7.767] (**) Video Bus: always reports core events
[     7.767] (**) Video Bus: Device: "/dev/input/event14"
[     7.800] (--) Video Bus: Found keys
[     7.800] (II) Video Bus: Configuring as keyboard
[     7.800] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:13/LNXVIDEO:00/input/input14/event14"
[     7.800] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[     7.800] (**) Option "xkb_rules" "evdev"
[     7.800] (**) Option "xkb_model" "pc105"
[     7.800] (**) Option "xkb_layout" "gb"
[     7.804] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[     7.804] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     7.804] (II) Using input driver 'evdev' for 'Power Button'
[     7.804] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     7.804] (**) Power Button: always reports core events
[     7.804] (**) Power Button: Device: "/dev/input/event1"
[     7.828] (--) Power Button: Found keys
[     7.828] (II) Power Button: Configuring as keyboard
[     7.828] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[     7.828] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[     7.828] (**) Option "xkb_rules" "evdev"
[     7.828] (**) Option "xkb_model" "pc105"
[     7.828] (**) Option "xkb_layout" "gb"
[     7.828] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[     7.828] (II) No input driver/identifier specified (ignoring)
[     7.828] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[     7.828] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[     7.828] (II) Using input driver 'evdev' for 'Sleep Button'
[     7.828] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     7.828] (**) Sleep Button: always reports core events
[     7.828] (**) Sleep Button: Device: "/dev/input/event2"
[     7.832] (--) Sleep Button: Found keys
[     7.832] (II) Sleep Button: Configuring as keyboard
[     7.832] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2"
[     7.832] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[     7.832] (**) Option "xkb_rules" "evdev"
[     7.832] (**) Option "xkb_model" "pc105"
[     7.832] (**) Option "xkb_layout" "gb"
[     7.834] (II) config/udev: Adding input device Laptop_Integrated_Webcam_FHD (/dev/input/event7)
[     7.834] (**) Laptop_Integrated_Webcam_FHD: Applying InputClass "evdev keyboard catchall"
[     7.834] (II) Using input driver 'evdev' for 'Laptop_Integrated_Webcam_FHD'
[     7.834] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     7.834] (**) Laptop_Integrated_Webcam_FHD: always reports core events
[     7.834] (**) Laptop_Integrated_Webcam_FHD: Device: "/dev/input/event7"
[     7.834] (--) Laptop_Integrated_Webcam_FHD: Found keys
[     7.834] (II) Laptop_Integrated_Webcam_FHD: Configuring as keyboard
[     7.834] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/input/input7/event7"
[     7.834] (II) XINPUT: Adding extended input device "Laptop_Integrated_Webcam_FHD" (type: KEYBOARD)
[     7.834] (**) Option "xkb_rules" "evdev"
[     7.834] (**) Option "xkb_model" "pc105"
[     7.834] (**) Option "xkb_layout" "gb"
[     7.834] (II) config/udev: Adding input device HDA Intel PCH Mic at Sep Left Jack (/dev/input/event10)
[     7.834] (II) No input driver/identifier specified (ignoring)
[     7.835] (II) config/udev: Adding input device HDA Intel PCH Mic at Ext Left Jack (/dev/input/event11)
[     7.835] (II) No input driver/identifier specified (ignoring)
[     7.835] (II) config/udev: Adding input device HDA Intel PCH Line Out at Sep Left Jack (/dev/input/event12)
[     7.835] (II) No input driver/identifier specified (ignoring)
[     7.835] (II) config/udev: Adding input device HDA Intel PCH HP Out at Ext Left Jack (/dev/input/event13)
[     7.835] (II) No input driver/identifier specified (ignoring)
[     7.836] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event5)
[     7.836] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[     7.836] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[     7.836] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     7.836] (**) Logitech USB Receiver: always reports core events
[     7.836] (**) Logitech USB Receiver: Device: "/dev/input/event5"
[     7.836] (--) Logitech USB Receiver: Found keys
[     7.836] (II) Logitech USB Receiver: Configuring as keyboard
[     7.836] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/input/input5/event5"
[     7.836] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[     7.836] (**) Option "xkb_rules" "evdev"
[     7.836] (**) Option "xkb_model" "pc105"
[     7.836] (**) Option "xkb_layout" "gb"
[     7.837] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event6)
[     7.837] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[     7.837] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[     7.837] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[     7.837] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     7.837] (**) Logitech USB Receiver: always reports core events
[     7.837] (**) Logitech USB Receiver: Device: "/dev/input/event6"
[     7.837] (--) Logitech USB Receiver: Found 20 mouse buttons
[     7.837] (--) Logitech USB Receiver: Found scroll wheel(s)
[     7.837] (--) Logitech USB Receiver: Found relative axes
[     7.837] (--) Logitech USB Receiver: Found x and y relative axes
[     7.837] (--) Logitech USB Receiver: Found absolute axes
[     7.837] (II) evdev-grail: failed to open grail, no gesture support
[     7.837] (--) Logitech USB Receiver: Found keys
[     7.837] (II) Logitech USB Receiver: Configuring as mouse
[     7.837] (II) Logitech USB Receiver: Configuring as keyboard
[     7.837] (II) Logitech USB Receiver: Adding scrollwheel support
[     7.837] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[     7.837] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     7.837] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.1/input/input6/event6"
[     7.837] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[     7.837] (**) Option "xkb_rules" "evdev"
[     7.837] (**) Option "xkb_model" "pc105"
[     7.837] (**) Option "xkb_layout" "gb"
[     7.837] (II) Logitech USB Receiver: initialized for relative axes.
[     7.837] (WW) Logitech USB Receiver: ignoring absolute axes.
[     7.837] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[     7.837] (**) Logitech USB Receiver: (accel) acceleration profile 0
[     7.837] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[     7.837] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[     7.837] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse0)
[     7.837] (II) No input driver/identifier specified (ignoring)
[     7.840] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[     7.840] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[     7.840] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[     7.840] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     7.840] (**) AT Translated Set 2 keyboard: always reports core events
[     7.840] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[     7.840] (--) AT Translated Set 2 keyboard: Found keys
[     7.840] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[     7.840] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[     7.840] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[     7.840] (**) Option "xkb_rules" "evdev"
[     7.840] (**) Option "xkb_model" "pc105"
[     7.840] (**) Option "xkb_layout" "gb"
[     7.840] (II) config/udev: Adding input device ImPS/2 ALPS GlidePoint (/dev/input/event9)
[     7.840] (**) ImPS/2 ALPS GlidePoint: Applying InputClass "evdev pointer catchall"
[     7.840] (II) Using input driver 'evdev' for 'ImPS/2 ALPS GlidePoint'
[     7.841] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     7.841] (**) ImPS/2 ALPS GlidePoint: always reports core events
[     7.841] (**) ImPS/2 ALPS GlidePoint: Device: "/dev/input/event9"
[     7.841] (--) ImPS/2 ALPS GlidePoint: Found 3 mouse buttons
[     7.841] (--) ImPS/2 ALPS GlidePoint: Found scroll wheel(s)
[     7.841] (--) ImPS/2 ALPS GlidePoint: Found relative axes
[     7.841] (--) ImPS/2 ALPS GlidePoint: Found x and y relative axes
[     7.841] (II) ImPS/2 ALPS GlidePoint: Configuring as mouse
[     7.841] (II) ImPS/2 ALPS GlidePoint: Adding scrollwheel support
[     7.841] (**) ImPS/2 ALPS GlidePoint: YAxisMapping: buttons 4 and 5
[     7.841] (**) ImPS/2 ALPS GlidePoint: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     7.841] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input9/event9"
[     7.841] (II) XINPUT: Adding extended input device "ImPS/2 ALPS GlidePoint" (type: MOUSE)
[     7.841] (II) ImPS/2 ALPS GlidePoint: initialized for relative axes.
[     7.841] (**) ImPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
[     7.841] (**) ImPS/2 ALPS GlidePoint: (accel) acceleration profile 0
[     7.841] (**) ImPS/2 ALPS GlidePoint: (accel) acceleration factor: 2.000
[     7.841] (**) ImPS/2 ALPS GlidePoint: (accel) acceleration threshold: 4
[     7.841] (II) config/udev: Adding input device ImPS/2 ALPS GlidePoint (/dev/input/mouse1)
[     7.841] (II) No input driver/identifier specified (ignoring)
[     7.844] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event8)
[     7.844] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[     7.844] (II) Using input driver 'evdev' for 'Dell WMI hotkeys'
[     7.844] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     7.844] (**) Dell WMI hotkeys: always reports core events
[     7.844] (**) Dell WMI hotkeys: Device: "/dev/input/event8"
[     7.844] (--) Dell WMI hotkeys: Found keys
[     7.844] (II) Dell WMI hotkeys: Configuring as keyboard
[     7.844] (**) Option "config_info" "udev:/sys/devices/virtual/input/input8/event8"
[     7.844] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD)
[     7.844] (**) Option "xkb_rules" "evdev"
[     7.844] (**) Option "xkb_model" "pc105"
[     7.844] (**) Option "xkb_layout" "gb"
[ 13165.916] (WW) NVIDIA(GPU-0): DELL U2711 (DFP-5): Failed to set DisplayPort power state
[ 14646.786] (WW) NVIDIA(GPU-0): DELL U2711 (DFP-5): Failed to set DisplayPort power state
[ 18835.802] 
Backtrace:
[ 18835.802] 0: /usr/bin/X (xorg_backtrace+0x3b) [0x80eab8b]
[ 18835.802] 1: /usr/bin/X (0x8048000+0x5fb38) [0x80a7b38]
[ 18835.803] 2: (vdso) (__kernel_rt_sigreturn+0x0) [0xb775e40c]
[ 18835.803] 3: /usr/bin/X (0x8048000+0xdf46e) [0x812746e]
[ 18835.803] 4: /usr/bin/X (0x8048000+0xe28bd) [0x812a8bd]
[ 18835.803] 5: /usr/bin/X (0x8048000+0x24988) [0x806c988]
[ 18835.803] 6: /usr/bin/X (0x8048000+0x28167) [0x8070167]
[ 18835.803] 7: /usr/bin/X (0x8048000+0x1a81c) [0x806281c]
[ 18835.803] 8: /lib/i386-linux-gnu/libc.so.6 (__libc_start_main+0xe7) [0xb747be37]
[ 18835.803] 9: /usr/bin/X (0x8048000+0x1a411) [0x8062411]
[ 18835.803] Segmentation fault at address 0x1b
[ 18835.803] 
Caught signal 11 (Segmentation fault). Server aborting
[ 18835.803] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[ 18835.803] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[ 18835.803] 
[ 18835.805] (II) Power Button: Close
[ 18835.805] (II) UnloadModule: "evdev"
[ 18835.805] (II) Unloading evdev
[ 18835.805] (II) Video Bus: Close
[ 18835.806] (II) UnloadModule: "evdev"
[ 18835.806] (II) Unloading evdev
[ 18835.806] (II) Power Button: Close
[ 18835.806] (II) UnloadModule: "evdev"
[ 18835.806] (II) Unloading evdev
[ 18835.806] (II) Sleep Button: Close
[ 18835.807] (II) UnloadModule: "evdev"
[ 18835.807] (II) Unloading evdev
[ 18835.807] (II) Laptop_Integrated_Webcam_FHD: Close
[ 18835.807] (II) UnloadModule: "evdev"
[ 18835.807] (II) Unloading evdev
[ 18835.807] (II) Logitech USB Receiver: Close
[ 18835.808] (II) UnloadModule: "evdev"
[ 18835.808] (II) Unloading evdev
[ 18835.810] (II) Logitech USB Receiver: Close
[ 18835.810] (II) UnloadModule: "evdev"
[ 18835.810] (II) Unloading evdev
[ 18835.812] (II) AT Translated Set 2 keyboard: Close
[ 18835.812] (II) UnloadModule: "evdev"
[ 18835.812] (II) Unloading evdev
[ 18835.813] (II) ImPS/2 ALPS GlidePoint: Close
[ 18835.813] (II) UnloadModule: "evdev"
[ 18835.813] (II) Unloading evdev
[ 18835.814] (II) Dell WMI hotkeys: Close
[ 18835.814] (II) UnloadModule: "evdev"
[ 18835.814] (II) Unloading evdev
[ 18837.005]  ddxSigGiveUp: Closing log

```

---

### Post by Wayne_V on 2011-09-30
I would try logging everything in a non-X terminal session -- either via Ctrl-Alt-F1 (Ctrl-Alt-F7 to go back to X) or by ssh'ng in from another system, and then running "sudo tail -f /var/log/{dmesg,messages,*log} | tee myErrors.log".   Then, when your session terminates ^C the tail and check the myErrors.log file.

I would probably also drop back to the open source nvidia drivers and see if the problem goes away.

---

