---
title: "Games problem - OpenGL? ATI Properity Drivers?"
date: 2010-12-28
forum: General Help
---

### Post by ITCompozer on 2010-12-28
Hi there,
I am new here so take it easy :)
So, I have a problem on my Ubuntu 10.10 32 BIT.
I have closed drivers 10.12 from ATI/AMD Website Installed.
All works with ok excepting some games like Warsow or Alien Arena.
I've got there stripes on menu or console, here si my video showing it, i can't explain it better:
[http://www.youtube.com/watch?v=LFoAGCItmjk](http://www.youtube.com/watch?v=LFoAGCItmjk)

Here is my xorg configuration:
```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
```

I have tried open drivers but with them I got low perfomance :(

I have also reinstalled drivers with ATI/AMD instructions but it doesn't fix my problem...

I have seen that whe I reboot my computer after installation I havent stripes, but when I reboot again I get them...

How to fix my problem?

Please reply me fast :)

Take Care.

---

