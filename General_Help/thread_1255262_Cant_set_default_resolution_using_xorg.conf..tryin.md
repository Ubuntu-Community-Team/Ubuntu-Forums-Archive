---
title: "Cant set default resolution using xorg.conf..trying 3rd day :("
date: 2009-09-01
forum: General Help
---

### Post by warrior.bin on 2009-09-01
--xorg.conf------
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
        	Depth 16
		Modes   "800x600"
    	EndSubSection
EndSection
-------
My old monitor need 800x600@75 .But cant set it as default. It goes to 1024x768@65 flickering screen. I have even tried modeline (using x386 modeline generator.py) but it doesn't work. I have every details specifications of my monitor. My graphics card is Intel 845GLLY and monitor is Philips 105E. Please guide..

---

### Post by P4man on 2009-09-01
Try this:

```

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
      [B]  HorizSync     31-54
       VertRefresh    60-85
[/B]

EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
        	Depth 16
		Modes   "800x600**_75.00**"
    	EndSubSection
EndSection
```

---

