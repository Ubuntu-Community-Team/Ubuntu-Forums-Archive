---
title: "How do I manually change screen resolution?"
date: 2006-03-16
forum: General Help
---

### Post by dlhansen on 2006-03-16
The highest screen res on the scr res panel is 1024x768, how do I manually go in and change it to 1280x1024? I am extremely new so I am most likely going to need a step by step of how to do this. Thanks.

---

### Post by Irony on 2006-03-16
First make a back up of your xorg.conf file;

[PHP]sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup[/PHP]

If you end up in text mode on booting up do;

[PHP]sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf[/PHP]

and reboot

You'll need to edit your xorg.conf file;

[PHP]sudo gedit /etc/X11/xorg.conf[/PHP]

You'll need to check that your HorizSync VertRefresh figures are correct for your monitor (look at the manual or google). Also check that you have a "1280x1024" entry. Save the file and reboot. It should look something like;

[PHP]Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-81
	VertRefresh	56-76
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon X800 Pro (R420 JI)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection[/PHP]

---

### Post by Ramses de Norre on 2006-03-16
sudo gedit /etc/X11/xorg.conf
search for the screen section and add a line similar to the existing with your prefered resolution.

EDIT: too late:)

---

### Post by Koobi on 2006-03-16
and please make sure you know your HorizSync and VertRefresh ranges for your monitor as Irony suggested.

i once messed with xorg and entered mismatching resolutions with refresh rates and busted my monitor.

so make sure you know the rates or YOU CAN CAUSE PHYSICAL DAMAGE TO YOUR PC.



also, on a much lighter note, you can switch your resolution using Ctrl+Alt++ or Ctrl+Alt+- in Gnome :D (might work in KDE as well, but i can't verify that.)

---

### Post by dlhansen on 2006-03-16
Thanks. I edited the file and rebooted, but nothing happened. I went in to the scr res panel and it did not show up as an option. Any ideas?

---

### Post by Koobi on 2006-03-17
that's odd behaviour.
mind showing us what your xorg.conf file looks like? or at least the relevant part of it.

---

### Post by dlhansen on 2006-03-17
Here is how it reads:
> Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync    	30-81
    	VertRefresh    	59-76 
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection


Is that correct? 
Thanks

---

