---
title: "add resolution nvidia settings"
date: 2010-02-14
forum: General Help
---

### Post by wretcher on 2010-02-14
hello i would need help with the same prob

i already postet thread about addin new resoloution in the xorg.conf file
i passed that entry. but the resoulution does not appear in the Nvidia X Settings. 

I want the resoulution of 1280 x 1024. Can anybody help me? so how can i add an resoulution to the nvidia X Server Settings

---

### Post by mikewhatever on 2010-02-14
gksudo nvidia-settings

...and add the resolution you want.
If you've been editing xorg.conf manually, perhaps it's a good idea to post it here for review.

---

### Post by wretcher on 2010-02-14
Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
	SubSection "Display"
		Depth	24
		Modes	"1280x1024"
	EndSubSection
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection


here is the conf file thx for help i hope i can fix it soon

---

### Post by jeduffey on 2010-05-07
I searched and searched for a long time to get my resolution refresh rate to work correctly with an Nvidia GT8600 and an old NEC MultiSync FP950 flatscreen monitor. I tried editing xorg.conf, adding refresh rates, adding resolutions. I specifically wanted 1280x1024_85 +0+0 available. I tried this under Ubuntu 9.04, 9.10, 10.04 but wasn't successful until this week.


The answer for me? It turns out that the Nvidia driver, 175, 190, 195 etc, somehow cross reference the horizontal and vertical refresh rates with what the monitor actually supports. This is what I did.

As Root, edit the x-window configuration file.
Applications - Accessories - Terminal

sudo gedit /etc/X11/xorg.conf

Find the section headed - monitor
This is what was in it on installation
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
EndSection

Next I searched for the specifications for my monitor.
Then I changed the H/S and V/R rates to match those listed in the specifications of the owners manual.

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       31.0 - 110.0
    VertRefresh     55.0 - 160.0
EndSection

Once I made the change, saved the file and rebooted, you could also start and stop xorg but reboot is simpler, the Nvidia driver, 195.36.15 currently, automatically recognised all of the possible resolutions and many refresh rates that are available on my monitor.

Honestly, it shouldn't be this hard. I am glad that it now works correctly. I have benefited greatly from help offered on this forum and wanted to return the favour. Good luck.

---

### Post by jeduffey on 2010-05-07
PS: Once you reboot, System - Aministration - Nvidia X Server Settings.
X Server Display Configuration, then select your resolution and refresh rate.

---

### Post by theohar on 2011-02-10
Worked for me as well!

Laptop: lenovo t410s (1440x900)
External monitor: Samsung SyncMaster 913N

many thanks jeduffey!

---

