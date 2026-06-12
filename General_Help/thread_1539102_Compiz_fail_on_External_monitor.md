---
title: "Compiz fail on External monitor"
date: 2010-07-26
forum: General Help
---

### Post by TIPSotto on 2010-07-26
H guys. I have a Hp dv5000 Laptop (not that it matters) with ATI 200M graphics chip and Ubuntu 10.04 LTS. Compiz works perfectly on my laptop screen. But when using my 23" Monitor it just doesn't. 

If I try enabling desktop effects it tells me it can't. Through terminal ( runnning 'compiz')I get the following error:

compiz (core) - Fatal: Root visual is not a GL visual
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

Launching fallback window manager


My /etc/X11/xorg.conf looks like this: 

Section "Screen"
	Identifier	"Configured Screen Device"
	Device	"Configured Video Device"
	SubSection "Display"
		Virtual	3200 1080
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection


Any help is extremely appreciated. I would love to use my new LED 23" with the nice looks of Compiz.

---

### Post by P4man on 2010-07-26
Just guessing you dont have enough video ram. Since you have an integrated video chip; you can probably configure the amount of system ram to use as graphics memory in the bios. Try increasing it?

---

### Post by TIPSotto on 2010-07-27
Thank you P4man. But I don't think that is the problem. I don't even think my bois is capable of doing that. :(

---

