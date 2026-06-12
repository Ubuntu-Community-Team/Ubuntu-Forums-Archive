---
title: "Cyberpower UPS integration with Gnome tools possible?"
date: 2011-06-01
forum: General Help
---

### Post by MadNachos on 2011-06-01
I recently purchased a Cyberpower CP1000PFCLCD UPS and much to my surprise when connected via USB to my PC (running Natty) the Gnome Power Management tool is able to see it and read some data, however the support is not complete. Gnome always thinks the UPS is supplying 0.0V although it is does properly read some data such as 'Time to empty'. Is it possible to configure the Gnome power application to properly speak to the UPS? If its not possible to have Gnome play nice with this UPS is it possible to at least have the UPS be ignored by the power mgmt tools?

I am able to use the Cyberpower utility but it would be slick to be able to use the Gnome tools for its history and statistics. 

[IMG]http://davet.net/images/power-stats.png[/IMG]

Thanks for any assistance.

---

### Post by DanneStrat on 2011-06-01
Hi.

You can integrate NUT (networkupstools) with gnome power manager

to get info from your UPS.

This method is fine for just monitoring your UPS, but if you plan on 

setting up a shutdown when the battery-power goes critically low, this is 

not the right method to use. The reason is that there is a bug in power 

manager that causes no action to be taken when the battery goes low, even if you did set it to shut 

down at low power with NUT.


If you're still interested, follow this guide(section: Use GNOME Power Manager and hal):

[http://blog.shadypixel.com/monitoring-a-ups-with-nut-on-debian-or-ubuntu-linux/](http://blog.shadypixel.com/monitoring-a-ups-with-nut-on-debian-or-ubuntu-linux/)

NOTE: I have a powerware 5115 UPS and I followed that guide when setting it up on 10.04. 
The only difference is that since I wanted to schedule a shutdown, I followed the instructions 
further down on that page(section: Use nutd and upsmon). With that method you get the full benefits 
from NUT and you can still monitor the ups(command-line) or by using knut-client(a KDE frontend for nut).


Good luck.

---

### Post by psusi on 2011-06-01
HAL is dead, so NUT no longer works with g-p-m.  Still waiting for it to be patched to work with UPower.

---

### Post by DanneStrat on 2011-06-01
> **psusi said:**
> HAL is dead, so NUT no longer works with g-p-m.  Still waiting for it to be patched to work with UPower.

OK, thanks for the info.

MadNachos, you can still set up NUT like in the section "Use nutd and upsmon"

from the guide I posted and use "knutclient" package from the repositories to

monitor the ups.

---

### Post by MadNachos on 2011-06-02
Thanks for the input.

---

### Post by MadNachos on 2011-06-02
Just to add for the future:

The "PowerPanel for Linux" package from Cyberpower runs just fine on Natty (I am using powerpanel_1.2_amd64.deb) with this UPS and provides all the typical functions. I was just hoping for something pretty to look at in Gnome ;)

---

### Post by sevenflo on 2011-06-04
Hey MadNachos,

I just got a CyberPower with Natty as well last week. I have the exact issues you do, same supply but the 1500. 

I noticed one thing though. At first what I had done is installed the power supply and then the powerpanel software. Then the USB cable. Gnome showed up a tray icon (Gnome Classic) and showed the UPS Charging at 99%.

I later had some issues with the fact that the powerpanel software shuts the computer down on power failure rather than hibernate (which I have a fix for btw). So I removed the powerpanel software. NOW, Gnome shows that red exclamation mark icon in the tray. 

The situation is still the same with the red exclamation mark icon in the tray after reinstalling the powerpanel software. I'm wondering if I would be able to reproduce my original results if I were able to purge some settings. I know for a fact that the files that would need to be removed are in ~/home. I know this because I reinstalled my system on an SSD and mounted my other drive as /home (it was mounted as /home before) and the settings remained from the last install.

So the point? At one point, GNome recognized the device.

---

### Post by MadNachos on 2011-06-04
> **sevenflo said:**
> 

So the point? At one point, GNome recognized the device.

Interesting. I am pretty sure that I plugged the UPS into the PC before installing the Cyberpower software and Gnome acted the same as it did with Powerpanel but I could be mistaken. Perhaps I'll toss a clean install onto a spare HDD and check it out...

---

### Post by sevenflo on 2011-06-04
Great! Report back with the results. Meanwhile, does your system shutdown (instead of hibernate) upon power loss?

---

### Post by MadNachos on 2011-06-07
> **sevenflo said:**
> Great! Report back with the results. Meanwhile, does your system shutdown (instead of hibernate) upon power loss?

I tried out a clean install of Natty as well as FC15 and both have the same result: Dont work. I have not had a lot of time to really look into this but it seems that UPower simply does not know how to read the data (well, all of the data) from this unit. Not sure how much tweaking it would take to get UPower to read it correctly. If I get some time (ha!) I might dig into it.

---

