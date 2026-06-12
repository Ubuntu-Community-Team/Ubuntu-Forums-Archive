---
title: "monitor Acer S202HL issue"
date: 2011-03-09
forum: General Help
---

### Post by abrazafi on 2011-03-09
Hi,

Tried to install the resolution of the 20" monitor Acer S202HL
on kubuntu 10.10 without success.

Any suggestion will be welcomed.

See attached the Xorg.0.log.
I had to put the following default xorg.conf:

***** start of xorg.conf
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fbdev"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
**** end of xorg.conf

---

