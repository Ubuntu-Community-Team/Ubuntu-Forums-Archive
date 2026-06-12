---
title: "I can't get my screen resolution set higher than 800 X 600."
date: 2010-01-31
forum: General Help
---

### Post by Spalding on 2010-01-31
I can't get my screen resolution set higher than 800 X 600.  I have tried many remedies I found in searches, but I still can't get to 1024 X 768, the max my monitor will support.

I think my main problem is this is a pretty old monitor, a 17" 4:3 Acer AL1715.  I was doing fine using a 19" widescreen, but when I swapped it out for this one, all was fine for a few days, and then it just went to 640 X 480!!  I was using the proprietary Invidia driver, so I swapped that out for the default, and that at least got me to 800 X 600, but I still have the same problem 0 - autodetect doesn't work, and System>Preferences>Screen Resolution only goes up to 800 X 600.  My video card and in fact my whole system are pretty darn old.  It is an nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)

I tried the suggested fix to set the resolution lower and then go back and see if that made a higher choice available - no dice.

I am afraid to just try to hammer the settings into /etc/X11/xorg.conf for fear of ruining the monitor.  Man, I was just getting comfortable with Ubuntu and now this!  Has cost me many hours today so far.

Thanks for any help.

---

### Post by blueshiftoverwatch on 2010-01-31
> **Spalding said:**
> I am afraid to just try to hammer the settings into /etc/X11/xorg.conf for fear of ruining the monitor.
I don't know what the actual risk of ruining your monitor is by doing stuff like that. I think most monitors have something built in where the user can't manually force dangerous settings. If they didn't, you'd think there would be a lot of viruses going around that would modify with settings like the refresh rate that would ruin your monitor.

If the goal of a hacker/cracker is to cause as much destruction as possible, you'd think they'd want to do something that would actually cause physical damage to the user's computer. Not just something that required a formatting of the HD followed by reinstalling Windows.

But I could be wrong.

---

