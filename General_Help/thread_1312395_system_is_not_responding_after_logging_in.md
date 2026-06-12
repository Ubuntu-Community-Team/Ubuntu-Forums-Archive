---
title: "system is not responding after logging in"
date: 2009-11-03
forum: General Help
---

### Post by alex_sv on 2009-11-03
Hi all!

I am using Ubuntu for more than half a year. An issue mentioned in the thread's subject revealed after updating to 9.10. I never seen this problem when I had Ubuntu 8 or 9.04.

More detailed problem description is as follows:

1. I turn on laptop and he wakes from hibernation or I am switching from one user to another.

2. Login screen appears and I enter the password.

3. System accepts the password and continues logging in, but suddenly screen turning off and laptop does not respond on *any* key presses - switching to terminal Ctrl+Alt+F[1,2...] does not work, Ctrl+Alt+Backspace does not work either, pressing Caps Lock does not result in flashing of the corresponding led.
Only power off can cure but this is quite annoying.

Sometimes after logging in my system refuses to respond on any key presses, but mouse does work. Logging out and logging in again can cure (system starts to respond on keyboard key presses right after login screen appears).

I don't know whether it is an OS bug or a result of some misconfiguration (I use hand-written xorg.conf for dual monitor configuration). Could you please point me how can I find the root cause?

P.S.:
1. no proprietary drivers are in use on my system.

2. the result of uname -a is as follows:
Linux udellalex 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux

3. My xorg.conf is as follows:
```

Section "Monitor"
	Identifier	"Monitor0"
	ModelName       "Dell Inspiron 1501 Monitor"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"Monitor1"
	ModelName       "Samsung SyncMaster 960BG"
	HorizSync       30-81
	VertRefresh     56-76
EndSection

Section "Screen"
	Identifier	"Screen0"
	Monitor		"Monitor0"
	Device		"Radeon 200M"
	DefaultDepth	24
	SubSection "Display"
		Depth	24
		Modes	"1280x800"
		Virtual	2560 1024
	EndSubSection
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Device"
	Identifier	"Radeon 200M"
	Driver		"ati"
	BusID		"PCI:01:05:00"
	Option		"XAANoOffscreenPixmaps"
EndSection

```

---

