---
title: "older ATI card acceleration support ?"
date: 2005-03-09
forum: General Help
---

### Post by ivar on 2005-03-09
I've been struggling with this for some time now.. I'm desperately trying to enable 3D acceleration on a ATI Mobility Radeon 7500.
I found the discussion at [http://ubuntuforums.org/archive/index.php/t-4343.html](http://ubuntuforums.org/archive/index.php/t-4343.html) when I realized the fglrx drivers weren't going to work for me (card is too old..) My main issue is that I still haven't been able to turn on the (albeit feeble) 3D acceleration - at least glxinfo always says "direct rendering: No".  From the thread referenced above, I was hoping that I could just load an "ati" module, but either it doesn't exist or I don't know where to find it. Anyone have any hints or pointers ?

---

### Post by taniwha on 2005-03-15
Try this
[http://ubuntuforums.org/showpost.php?p=92837&postcount=4](http://ubuntuforums.org/showpost.php?p=92837&postcount=4)

---

### Post by zep24 on 2005-03-17
First uninstall fglrx driver if you installed it. Then you will have to edit the Device section of your XF86Config-4 (warty) or xorg.conf (hoary) file. At the end this should look like this for a singlehead configuration (remember it's just an example you must customize depending on your hardware and your needs):

> Section "Device"
	Identifier	"*your ATI board*"  # you probably already have this line, don't change your default settings 
	Driver		"radeon"
	BusID		"PCI:1:0:0" # you probably already have this line, don't change your default settings 
	Option 		"AGPMode" "*1, 2 or 4 depending of your hardware* "
	Option 		"AGPFastWrite" "true" # use at your own risk if something goes wrong comment this line out
	Option 		"MonitorLayout" "CRT, NONE"
	Option 		"EnablePageFlip" "true"
	Option 		"RenderAccel" "true"
	Option 		"SubPixelOrder" "NONE"
	Option 		"MergedFB" "false" # only for hoary
	Option		"BackingStore" "true"

EndSection


Now you should have 3d acceleration working!

---

