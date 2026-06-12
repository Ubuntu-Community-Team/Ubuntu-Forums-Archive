---
title: "New Refresh Rate Problem"
date: 2005-01-29
forum: General Help
---

### Post by pseudonym on 2005-01-29
Hi. After enabling higher refresh rates by adding in my monitor's frequency ranges to XF86Config-4, I now find that it won't stick to the desired rate of 75Hz. Instead, it sometimes goes up to the maximum of 85.

The problem only occurs whenever I exit back to the desktop out of a game. I can trace it back to the first game (Deus Ex) I installed after downloading Cedega. The game hung at the main menu (hey, it's Cedega :) ) so I Ctrl+F2 out of it then did shutdown -r now. When I tried to play again it still hung so I pressed Ctrl+F2 but instead of rebooting this time I just stopped and restarted gdm.

Since then I've been getting the problem described above. I did dpkg-reconfigure xserver-xfree86 but nothing changed. I tried adding a couple of modelines to see if it would 'lock' the refresh rate, but that didn't work either.I've no idea what to do next. Can anyone help?

Here are the relevant sections my XF86Config-4. My monitor is a Sampo AlphaScan 712 -

Section "Monitor"
	Identifier	"Generic Monitor"
	# HorizSync	30-70
	# VertRefresh	50-120
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV25 [GeForce4 Ti 4400]"
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

### Post by pseudonym on 2005-01-30
Just a little amendment to the above. The problem only occurs when running *native* linux games (specifically Q3 and RTCW). WineX/Cedega games are fine. But the problem did start occurring after that issue with DeusEx and Cedega mentioned above...

---

