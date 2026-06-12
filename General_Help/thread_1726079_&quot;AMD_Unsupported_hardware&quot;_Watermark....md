---
title: "&quot;AMD Unsupported hardware&quot; Watermark..."
date: 2011-04-10
forum: General Help
---

### Post by paulstonervw on 2011-04-10
Hey gang.  This is new to me - Installed 10.10 on my laptop and it detected that I had the ATI/AMD graphics chip.  So, going into the "Additional Drivers", I activated the ATI/AMD driver.  Everything looks awesome - except this time there is this awful watermark in  the bottom right hand corner of my screen that says "AMD Unsupported hardware" - is there any way to tell this thing to get rid of the watermark?

---

### Post by TeoBigusGeekus on 2011-04-10
Can you post a screenshot? Never heard of this before.

---

### Post by paulstonervw on 2011-04-10
WOW...I just used the Take Screenshot tool in accessories and the watermark does not show up in the image!!!  It's something local with the ATI Catalyst Control Center.  While I was fussing with that to see if I could get rid of the watermark, it disappeared for a short time and a red box showed in the top left hand corner with the number '1' in it (assuming that meant this was display number 1)....

---

### Post by 3Miro on 2011-04-10
What is your video card? Older video cards are no supported by the proprietary AMD driver and the old FOSS (default) drivers were not very good (both drivers are good on new cards). If you have an old ATI card, I would upgrade the hardware. Either that, or try using the default driver (disable the driver in the additional drivers section).

---

### Post by Philip550c on 2011-04-16
I'm having the same issue on a friends brand new computer. This is one reason I use nvidia with ubuntu. I bought a laptop once with ati and the proprietary drivers made videos and games blink and be unusable and the open drivers lacked opengl support, making it useless. BUMP for a solution.

---

### Post by Yellow Pasque on 2011-04-16
Installing a recent version of Catalyst will make the watermark go away (unless you have a recently released RadeonHD 6k card). [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually)

> Older video cards are no supported by the proprietary AMD driver
This has nothing to do with a watermark. Old cards won't run Catalyst (>= 9-4) at all. Only cards newer than the Catalyst version have the watermark issue.

> If you have an old ATI card, I would upgrade the hardware. Either that, or try using the default driver (disable the driver in the additional drivers section).
Old cards won't show the ATI driver in the "additional drivers" dialog. Also, the open-source r300g 3D driver has made rapid progress as of late, and is faster than Catalyst in some apps, so buying new hardware isn't the answer for most people. [http://www.phoronix.com/scan.php?page=article&item=amd_radeon_histq111&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_radeon_histq111&num=1)

---

