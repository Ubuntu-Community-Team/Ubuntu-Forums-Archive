---
title: "How to add 1280x800"
date: 2010-01-06
forum: General Help
---

### Post by cherripez on 2010-01-06
So after having a few people tell me to try out Ubuntu, I've finally decided to give it a shot. Everythings gone smooth up until this point. My resolution should be 1280x800. It's what I've been using for years now. In the nvidia X server settings, it skips from 1280x720 to 1280x960. I've tried Google and got past the errors with not being able to write the xorg.conf file. I've tried to edit that, but I have absolutely no clue what I'm doing, so that didn't work. Any help would be appreciated. I've been getting quite frustrated this morning with this.

---

### Post by phDaemon on 2010-01-06
What nvidia graphics driver do you have?
If your resolution should be 1280 x 800, try downloading a different (maybe newer driver) and see if it works.

---

### Post by cherripez on 2010-01-06
I was using the nvidia accelerated driver 185 first, then I switched down to the 173 driver.

---

### Post by phDaemon on 2010-01-06
Another question ( i dont think it should matter but just in case ) are you using DVI or VGA? have you tried switching?

I would go to [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us) look for your video card, and download the latest drivers (including betas) and seeing if your resolution is supported in one of those.

---

### Post by fragos on 2010-01-06
I have a different display which is recognized by brand, model and 1440x900 size. 1280x800 isn't my list of settable resolutions. My Dell laptop has 1280x800 as well but it has an Intel display driver. If you run "Nvidia X Server Settings" and select "X Server Display Configuration" you'll notice a button "Advanced...". After clicking you'll have a "Panning:" parameter which is set to your max determined display size. Is that number 1280x800? Using xorg.conf to resolution used to be standard and should still work to override the determined values. You may find [http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973) helpful.

---

### Post by cherripez on 2010-01-06
I've given up on trying. Nothings working. Thanks for the help though.

---

