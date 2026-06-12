---
title: "mouse frozen, even after restart"
date: 2010-08-26
forum: General Help
---

### Post by l0ijoat on 2010-08-26
hello, i'm having an issue with the touchpad on my hp pavilion laptop. as of this afternoon, the cursor has started to freeze immediately as ubuntu is booted up (but it is normal during the login screen process). i think this has happened because i accidently pushed a button i didn't know about right above the touchpad/mouse which froze the mouse, but i was able to toggle this a few times by pushing the button again. the mouse froze completely after toggling this a few times, and it comes back after a restart but only during the login screen - it freezes immediatly as ubuntu is loaded and the cursor changes from black to white. the keyboard is still functional. are there keyboard shortcuts i can use to get to the start menu or the terminal to try and fix this issue? and what do you think i should do about it? i'm pretty new to ubuntu.
thanks!
hart

---

### Post by l0ijoat on 2010-08-26
bump, any ideas?

---

### Post by l0ijoat on 2010-08-26
bump

---

### Post by bobcollard on 2010-08-26
Ctrl/Alt/F1 will get you to Terminal.  Sorry, don't know how to fix it.

---

### Post by linux18 on 2010-08-26
I occasionally have the exact same problem on my hp pavilion. I have managed to solve it by booting in recovery mode and dropping to a root prompt. At the root prompt type" telinit 3 && xinit " once xtern starts type" gnome-panel && meacity && nm-applet & " once everything starts reboot and it should be good to go.

---

### Post by l0ijoat on 2010-08-26
i got to the root prompt and typed the first code you gave me. that works. it then asks me for some kind of "login" - and whenever i try to type anything else, like the second code you gave me, the first letter shows up but the rest don't. it comes back kinda jumbled and it doesn't recognize it as a command...basically it won't allow me to type anything correctly after that first code.

if i type the second code in right after the first it returns:```
(gnome-panel:1407): Gtk-WARNING **: cannot open display
```

also, i've been using a usb mouse which works, but sometimes the left and right clickers become reversed...it's just one thing after another.

---

### Post by linux18 on 2010-08-26
you need to type " xinit " before the second command, in my haste I put an '&&' between two separate commands that require a login.

---

### Post by l0ijoat on 2010-08-26
could you possibly put exactly what you want me to type in code tags? im pretty confused as to what you want me to enter, i've tried it several ways, always ending in some error. do you want me to include those "&&"s or not? 
the way i've been doing it is:
```
telinit 3
```
then logging in with my name/pass, then
```
xinit
``` - and this seems to fail.

---

### Post by linux18 on 2010-08-27
The sequence is:

================================
-telinit 3
--login
-xinit
--once xterm starts
-gnome-panel &
-metacity &
-nm-applet &
--reboot
======================

if your failing at xinit, you may have broken packages or a video card misconfiguration, in which case:
sudo apt-get update
sudo apt-get -f install
sudo apt-get autoremove
sudo apt-get --fix-broken upgrade

or for an nvidia card:
sudo nvidia-xconfig

---

### Post by l0ijoat on 2010-08-27
ok, xinit is still failing to load. i did what you said at the bottom of your last reply as well. here's a log file it points me to:

```
X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux ubuntuHART 2.6.32-24-generic #41-Ubuntu SMP Thu Aug 19 01:12:52 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=d356932b-6a9a-48ec-baf9-2cceecd5bfd4 ro quiet splash
Build Date: 21 July 2010  12:47:34PM
xorg-server 2:1.7.6-2ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Aug 27 12:23:58 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(**) Option "Xinerama" "0"
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
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x81f0e80
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:0:5:0) 10de:0244:103c:30b7 nVidia Corporation C51 [Geforce Go 6150] rev 162, Mem @ 0xb2000000/16777216, 0xc0000000/268435456, 0xb1000000/16777216, BIOS @ 0x????????/131072
(--) PCI: (0:0:10:3) 10de:0271:103c:30b7 nVidia Corporation MCP51 PMU rev 163, Mem @ 0xb0040000/262144
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/extra-modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  195.36.24  Thu Apr 22 10:38:29 PDT 2010
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
(EE) NVIDIA:     system's kernel log for additional error messages.
(II) UnloadModule: "nvidia"
(II) Unloading /usr/lib/xorg/extra-modules/nvidia_drv.so
(EE) Failed to load module "nvidia" (module-specific error, 0)
(EE) No drivers available.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
```

---

### Post by linux18 on 2010-08-27
are you on an upgraded kernel, if so, can you go back to the old kernel?

---

### Post by l0ijoat on 2010-08-27
i'm using ubuntu studio lucid 10.4, i don't think i've ever upgraded the kernel, how would i check that though?

---

