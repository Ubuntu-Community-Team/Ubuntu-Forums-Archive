---
title: "Resolution Blues..."
date: 2006-05-08
forum: General Help
---

### Post by TmP on 2006-05-08
Hi!

I just bought my new monitor. My old 14" CRT is going out the window!

BUT!

I can't seem to access the "1280x1024" resolution. I checked the forums and found out I need to edit the xorg.conf .

> 
Section "Screen"
	Identifier	"Default Screen"
	Device		"S3 Inc. Savage 4"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection


So I did. And nothing changed. I still can't access the new resoution.

Please Help!

---

### Post by GaFFy on 2006-05-08
You will have to run sudo dpkg-reconfigure xserver-xorg and choose your required resolutions

---

### Post by TmP on 2006-05-08
It worked!
Thanx a lot!

---

### Post by Ubuntuud on 2006-05-08
Depth 15?! Is that possible?

---

