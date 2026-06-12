---
title: "Limited choice of resolution"
date: 2006-06-11
forum: General Help
---

### Post by Warlord88 on 2006-06-11
I have installed ATI drivers from the site [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide) for my Radeon 9550. Now I have a number of resolution options but I dont see my favourite 1280*960 in the options. When I go to System -> Preferences -> Screen Resolution there are other choices but not the one mentioned. 

The /etc/X11/xorg.cong file also appears to be fine. Here is the concerned section:
-----------------------------------------------------------------------------------------------------------
Section "Screen"
	Identifier "Default Screen"
	Device     "Generic Video Card"
	Monitor    "T710SH"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
-------------------------------------------------------------------------------------------------------

All the modes shown except 1280*960 (which I want :( ) do work and show in options. 

Can someone tell me how to bring the required resolution?

---

### Post by yaztromo on 2006-06-11
I had the same problem with 1280x960. I knew the refresh rate my monitor needed for 1280 so got it working with a modeline.

Go here [http://www.dkfz.de/spec/linux/modeline/](http://www.dkfz.de/spec/linux/modeline/) and select1280x960 and type in the desired frame rate. If your frame rate is too high, X will fall back to another mode. This will give you a modedline to put in your xorg.conf

Then sudo nano /etc/X11/xorg.conf -w

Under the monitor section add in your modeline. This is mine for 1280x960@70hz.

> 
Section "Monitor"
        Identifier      "NEC FE770"
        Option          "DPMS"
        Modeline "1280x960" 125.14  1280 1344 1496 1784   960  960  963 1002
EndSection


Then add the name of the modeline to depth 24 of your screen section

> 
SubSection "Display"
                Depth           24
                Modes           "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection


If it doesn't work, try dropping your refresh rate in the modeline tool and try agan. My IBM monitor didn't work until I hit 68.9Hz.

---

### Post by Warlord88 on 2006-06-11
Hey.. this worked like a charm.. I'm so glad to see my favourite resolution back. Thanks a lot.

Few more things:
Can I add more modelines so that I can run 1280*960 at different refresh rates just by selecting from the system menu? I am currently running the same at 60 Hz. Is this safe enough for my eyes? I heard that too less frequency can be painful to eyes and too high frequency can damage the monitor? What frequency should I keep for the golden mean? I have a LG Flatron E700SH with standard frequency ranges (30-71 kHz horizontal and 50-160 kHz vertical).

---

### Post by yaztromo on 2006-06-11
I'm not sure if you can add multiple refresh rates. 

60hz is a bit too flickery for me it gives me a headache. Just try upping the refresh rate and keep restarting X to see what your monitor can do.  I would imagine it is like mine and has a maximum of around 70hz at 1280x960.

---

### Post by Warlord88 on 2006-06-11
Well I tried adding multiple refresh rates and it worked. You just have to add the required modelines. 70 Hz works for me.

---

