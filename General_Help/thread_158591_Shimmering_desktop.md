---
title: "Shimmering desktop"
date: 2006-04-11
forum: General Help
---

### Post by Neky on 2006-04-11
I installed Ubuntu 5.10 "Breezy Badger" today, nothing was wrong, everything went so smooth, like it was announcing a dissaster. And there it was...a dissaster. I knew there is something wrong by the first look at my desktop. Resolution was 640x480@60Hz and there was no way to change it. My desktop is also shimmering, I can`t read anything. Same thing with the Live CD.
Here is my PC configuration :

CPU: Intel Celeron 2.40 GHz
MB: MSI PM8M-V ( integrated S3 UniChrome graphics chip ) - I think this is problem
RAM: 256MB DDR, 400MHz
HDD: 80GB Maxtor, 7200 RPM

other is irelevant, I think.

---

### Post by badrinarayan on 2006-04-12
You may want to see this post: [http://ubuntuforums.org/showpost.php?p=414445&postcount=6](http://ubuntuforums.org/showpost.php?p=414445&postcount=6)

---

### Post by Neky on 2006-04-12
Thanks for this but there is NO xorg.conf in /usr/X11R6/lib/X11/ I replaced original driver file with the one I downloaded and X server wont boot. Problem is in xorg.conf but i can`t find it anywhere...Where is "Search" in Ubuntu?

---

### Post by gibson on 2006-04-12
The file you want is in /etx/X11/xorg.conf

as for searching, try the "find" or "locate" commands. more info can be found by opening a terminal any typing "man find" or "man locate".

Hope this helps

---

### Post by gibson on 2006-04-12
Dont want to jump the gun here, but if you have not modified xorg.conf before, i think i should explain what was meant by the tutorial as it was fairly breif...

to change the driver locate the section regarding your gfx card:

> Section "Device"
	Identifier	"NVIDIA Corporation NV20 [GeForce3 Ti 200]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option 		"RenderAccel"		"true" 
	Option 		"AllowGLXWithComposite"	"true"
EndSection

Then change the driver value to "via".

Remeber to backup your xord file before doing anything with

> cp xorg.conf xorg.conf.backup

hope this helps

---

### Post by Neky on 2006-04-12
Here is that section in my xorg.conf


> Section "Device"
	Identifier	"VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video"
	Driver		"via"
	BusID		"PCI:1:0:0"
EndSection

It says "via" but it wont boot. Thank you guys very much, I'm total begginer.

---

