---
title: "ATI driver unable to install properly on Natty"
date: 2011-04-30
forum: General Help
---

### Post by deludrien on 2011-04-30
Hi, I've recently switched over to Ubuntu 11.04. I installed Natty by wiping out Maverick entirely. Everything worked well, until I tried to install ATI graphics drivers through the instructions found here:

[http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide)

The installation goes fine without any errors; however, when I reboot, nothing shows up on the screen. I can hear Ubuntu's startup sounds, but there are no visuals. When I attempt to go to the ATI Catalyst Control Center in Recovery Mode, I get this error:

> There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.

No ATI graphics driver is installed, or the ATI driver is not functioning properly.
Please install the ATI driver appropriate for you ATI hardware, or configure using aticonfig.
I've tried uninstalling and reinstalling these drivers multiple times, and I've also tried using the generic driver detected by "Additional Drivers". None of these work at all, I cannot see anything on the screen when any ATI drivers are enabled. I've even tried re-updating Natty via CD, but none of this works.

I have a Radeon HD 3450 graphics card, and my CPU is an AMD Athlon 64 X2 Dual Core Processor 5400+. I'm on 64 bit Ubuntu. I had no problems with my drivers on Maverick.

Please advise.

---

### Post by auwally on 2011-04-30
I had similar problems after upgrading to 11.04 - all blank screens  except in safe mode.  Checked drivers and uploaded nvidia accelerated  graphics driver (version 173).  Went to system - administration -  additional drivers.  No problems now all screens up and running.

---

### Post by deludrien on 2011-04-30
> **auwally said:**
> I had similar problems after upgrading to 11.04 - all blank screens  except in safe mode.  Checked drivers and uploaded nvidia accelerated  graphics driver (version 173).  Went to system - administration -  additional drivers.  No problems now all screens up and running.
  
Activating drivers from additional drivers are not working as well - the system works without any drivers installed, it's when I try to install them that it breaks. I also have an ATI card, not an nvidia one.

---

### Post by deludrien on 2011-04-30
Okay, I have managed to get the general ATI driver from "Additional Drivers" working, but I'd really like the more specific driver from the ATI website. Does anyone have any idea why the driver offered from Additional Drivers would work, but not the ati-driver-installer-11-4-x86x86_64.run that I got from the website?

---

### Post by Johnkozz on 2011-05-01
Please keep me posted. I am having the exact problems with almost the exact same hardware. D:   So sad, and sick of 1024 x 768.

---

