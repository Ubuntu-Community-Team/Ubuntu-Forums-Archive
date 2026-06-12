---
title: "Screen resolution"
date: 2006-06-24
forum: General Help
---

### Post by ato on 2006-06-24
Hi all,
I have a Samsung 204B LCD with native resoultion of 1600x1200, the max resolution that i reach is 1280x1024.

Tthis is a part of my xorg.conf

```

Section "Device"
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600?]"
	Driver		"nv"
	BusID		"PCI:4:0:0"
EndSection

Section "Monitor"
	Identifier	"Samsung SyncMaster 204B"
	Option		"DPMS"
	HorizSync	30-81
	VertRefresh	56-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV43 [GeForce 6600?]"
	Monitor		"Samsung SyncMaster 204B"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"4095x4095" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"4095x4095" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"4095x4095" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"4095x4095" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"4095x4095" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"4095x4095" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

```

oh yes, I have a GeForce 6600 that support 1600x1200 resolution. ;) 

Someone can help me?

Thanks

---

### Post by bscbrit on 2006-06-24
There is an obvious error in your Xorg.conf file.  The entries "4095x4095" are wrong - if the maximum resolution is 1600x1200 then there is no point in trying to set a resolution of 4095x4095.  Remove all instances of "4095x4095", including the quotes.
Reboot, or at least restart X and see if that helps correct the problem.

---

### Post by ato on 2006-06-24
Hi
I had already try to  delete that values but with the same result.

Now I uncovered that my glx don't work.

There's more than one problem.
Before i had a Philips 109T and all was working correctly.
](*,)

---

### Post by scxtt on 2006-06-24
does the nv driver support 16x12? ... i never used to have 16x12 w/ vesa, wasn't until i used a less generic driver that i got it ... using fglrx now ... maybe you can use "nvidia" driver ...

---

### Post by skymt on 2006-06-24
You have "Driver" set to "nv" (open-source, non-accelerated). If you want glx, you have to change that to "nvidia" (closed-source, accelerated), assuming you have the nvidia drivers installed. That may also fix your resolution troubles.

---

### Post by ato on 2006-06-24
Well, it's true.
thanks all

---

### Post by ShamoIdol on 2006-06-24
[QUOTE=ato]Well, it's true.
thanks all[/QUOTE]

Did you solved you problem?

---

### Post by ShamoIdol on 2006-06-28
[http://ubuntuforums.org/showthread.php?p=1177523](http://ubuntuforums.org/showthread.php?p=1177523)

Since my thread was closed by the moderator because it was belived to be related to this I'll post here. Actually my problem has no relation with this one except the same resolution :-).
Anyway it seems to be I have solved mine.
The problem was because /usr/bin/Xorg was not suid root. When I chmod +s it then I was able to start an X session at 1600x1200 as a reguar user.
Have no Idea why its required for Xorg to be a suid in order to run at a resolution higher then 1280x1024.

Also I've found that this is already known bug at least in the recent Debian:
[http://lists.debian.org/debian-x/2006/05/msg01062.html](http://lists.debian.org/debian-x/2006/05/msg01062.html)
and thus should be fixed soon.

---

### Post by scxtt on 2006-06-28
[quote=Shamoldol]Have no Idea why its required for Xorg to be a suid in order to run at a resolution higher then 1280x1024.[/quote]wasn't the case for me ...

---

