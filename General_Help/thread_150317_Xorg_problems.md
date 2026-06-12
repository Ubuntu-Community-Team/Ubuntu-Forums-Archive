---
title: "Xorg problems"
date: 2006-03-25
forum: General Help
---

### Post by arcanistherogue on 2006-03-25
Hey, I could run linux at 1280 x 1024 before I formatted my computer.  This was using my nVidia 6600, and then after it died in the same install I used an nVidia TNT 2 card.

I got an nVidia 6600GT and reformatted and installed ubuntu.  I was running windows for about a week (I just got to play my games again for the first time in months :D) and I got 1280 x 1024.

I have a 17 inch old CRT monitor from 1996, but it can get 1280 x 1024.  WhenI installed Ubuntu now, I selected 1280 x 1024 during install.   When it loaded the default drivers, all I saw was a bunch of colors and stuff, just scattered on the screen like snow on TVs.  I heard the noises though, and I went to a virtual terminal and installed the proper drivers and edited the /etc/X11/xorg.conf file correctly.

After this, When I rebooted my computer, X started normally but it was only running at 1024 x 768.  

I saw when editing the config file that it had my resolutions set at all depths to max of 1024 x 768, and even adding "1280 x 1024" in front of them did nothing.  I reinstalled ubuntu twice, still the same error. 

One thing I noticed was that when I go to change resolution it says 1024 x 768 at 60 Hz refresh rate, and I am pretty sure my monitor maxes out at 55 Hz.  

How do I configure my computer to get 1280 x 1024, and change the refresh rate?

---

### Post by trent dillman on 2006-03-25
The refresh rate can be specified in your xorg.conf under the monitor section.

---

### Post by arcanistherogue on 2006-03-25
I changed refresh rate from 43-60 to 43-55, and then when I tried to restart X i got this fatal error and had to change it back in nano.  

Any other methods, or is anyone experiencing similar problems?  I really love Ubuntu, but I hate 1024 x 768 with all my heart.  I'm definantly going to change my distro in the meantime if this can't be fixed until I get a new monitor :\

---

### Post by arcanistherogue on 2006-03-26
bump

---

### Post by arcanistherogue on 2006-03-26
bump ;_;

---

### Post by arcanistherogue on 2006-03-26
bump...

---

### Post by kimusabi on 2006-08-25
Aww, Three bump's a charm.
Anyway, once you get to the GDM bit where it screw's up and gives the error, hit CTRL+ALT+F1 and type in this
```
sudo dpkg-reconfigure xserver-xorg
```
This will guide you through the xorg set-up process, in which you can specify you're screen resolution.

-Kimmeh

---

