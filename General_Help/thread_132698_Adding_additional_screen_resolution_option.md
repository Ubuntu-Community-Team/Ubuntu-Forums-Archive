---
title: "Adding additional screen resolution option"
date: 2006-02-18
forum: General Help
---

### Post by jmj on 2006-02-18
I've just installed Ubuntu on an old IBM PC.  Got it running fine and even was able to install the Firefox 1.5 after about a week of trying.  My ? is how to add 1024 x 768 as a resolution option.  Right now, I only have 800 x 600 and 640 x 480.  When I had XP on this machine I was able to use 1024 x 768 I thought.  I seem to remember during the install that it was a default choice.  Is it possible to add it?

---

### Post by Piggah on 2006-02-18
I fixed this issue by adding the options I wanted to my xorg.conf.

Backup your xorg.conf first.

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

Then open your xorg.conf:

```
sudo gedit /etc/X11/xorg.conf
```

Find this line:

```

SubSection "Display"
Depth 24
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
EndSection

```

It won't have "1280x1024" and "1024x768" in there like it does in that, so add that just like you see above. 

Then save your xorg.conf and reboot. You should be able to change it. 

If you find that you can't log back in and you have to go into the terminal rather than gnome, enter this:

```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
``` 

and that will take it back to normal.

Good luck. :)

---

### Post by jmj on 2006-02-18
Thanks for your help!

I did exactly what you said, but when I looked inside the file, the resolutions were already there.  Does that mean my monitor doesn't support that resolution?  I could have sworn that I'd used it when I had XP on this machine,but it's a pretty old monitor and I see in the file that it's a 'generic' type monitor.

Here's the code:

Section "Screen"
	Identifier	"Default Screen"
	Device		"Cirrus Logic GD 5465 [Laguna]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

---

### Post by dcstar on 2006-02-18
[QUOTE=jmj]Thanks for your help!

I did exactly what you said, but when I looked inside the file, the resolutions were already there.  Does that mean my monitor doesn't support that resolution?  I could have sworn that I'd used it when I had XP on this machine,but it's a pretty old monitor and I see in the file that it's a 'generic' type monitor.
.....
[/QUOTE]
If the monitor section of your xorg.conf file has sync and refresh settings, try commenting them out and starting X again, for example mine has:

```
Section "Monitor"
	Identifier	"StudioWorks"
	Option		"DPMS"
[B]	HorizSync	30-69
	VertRefresh	50-85[/B]
	DisplaySize	270	203	# 1024x768 96dpi
EndSection
```
so comment out the two highlighted lines and see if you get more choices.

---

