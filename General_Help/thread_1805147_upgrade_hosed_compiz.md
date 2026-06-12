---
title: "upgrade hosed compiz"
date: 2011-07-15
forum: General Help
---

### Post by ftravers on 2011-07-15
just did an upgrade and my compiz broke:

Here is the Synaptic > File > History for the upgrade:

Commit Log for Fri Jul 15 11:41:45 2011


Upgraded the following packages:
libimobiledevice0 (0.9.7-1ubuntu1) to 0.9.7-1ubuntu1.1
linux-generic (2.6.32.32.38) to 2.6.32.33.39
linux-headers-generic (2.6.32.32.38) to 2.6.32.33.39
linux-image-generic (2.6.32.32.38) to 2.6.32.33.39
linux-libc-dev (2.6.32-32.62) to 2.6.32-33.70

Installed the following packages:
linux-headers-2.6.32-33 (2.6.32-33.70)
linux-headers-2.6.32-33-generic (2.6.32-33.70)
linux-image-2.6.32-33-generic (2.6.32-33.70)


Here is the output of launching 'compiz' from the terminal:


$ compiz
compiz (core) - Fatal: Root visual is not a GL visual
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

Launching fallback window manager
Window manager warning: "" found in configuration database is not a valid value for keybinding "activate_window_menu"


Here is my xorg.conf:


$ grep -v ^# /etc/X11/xorg.conf

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Virtual	3000 2000
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:0:1:0"
EndSection


Any advice how to get my lovely compiz back!!!

---

