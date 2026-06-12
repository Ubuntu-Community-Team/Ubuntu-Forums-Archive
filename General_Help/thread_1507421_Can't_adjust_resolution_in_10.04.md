---
title: "Can't adjust resolution in 10.04"
date: 2010-06-11
forum: General Help
---

### Post by lbmounse on 2010-06-11
I have just did a fresh install of Ubuntu 10.04 to a computer with a generic, low end, on board graphics card. 

It will not allow me to change the resolution to something other than 800x600 or lower.  8.04 allowed me to set the resolution to as high as 1600x1200 using the same monitor/graphics card.  

What should I do?  Please help.

---

### Post by dcstar on 2010-06-12
> **lbmounse said:**
> I have just did a fresh install of Ubuntu 10.04 to a computer with a generic, low end, on board graphics card. 

It will not allow me to change the resolution to something other than 800x600 or lower.  8.04 allowed me to set the resolution to as high as 1600x1200 using the same monitor/graphics card.  

What should I do?  Please help.

Some older video hardware is not supported in later releases, read the release notes for details.

---

### Post by bigsmitty64 on 2010-06-12
Did you try updating hardware drivers?  System/Administration/Hardware Drivers?

---

### Post by lbmounse on 2010-06-12
This is the graphics adapter: 01:00.0 VGA compatible controller: VIA Technologies, Inc. CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro] (rev 01)

It worked fine in Hardy using the VIA driver.
Now that Lucid switched to the OpenChrome driver, I can't set the resolution higher than 800x600.

Is there anyway I can go back to the old driver.

---

### Post by lbmounse on 2010-06-12
It appears to be working now.  I think it was a problem with ubuntu not detecting my monitor, not a problem with the Openchrome driver.

I followed this thread:

[http://ubuntuforums.org/showthread.php?t=1488040&highlight=openchrome](http://ubuntuforums.org/showthread.php?t=1488040&highlight=openchrome)

They had a similar monitor to mine (I have the dell P990), so I just copied the "Monitor" section into my xorg.conf. 

[HTML]
Section "Monitor"
	Identifier "Monitor0"
	VendorName "dell"
	ModelName "p990"
	HorizSync 30-107
	VertRefresh 48-120
Modeline "1280x1024_85.00"  159.50  1280 1376 1512 1744  1024 1027 1034 1078 -hsync +vsync
EndSection
[/HTML]

Now I can set my resolution to as high as 1856x1392 (or as low as 640x480, lol).

---

