---
title: "Dual monitor no longer working"
date: 2009-10-22
forum: General Help
---

### Post by Naugh on 2009-10-22
I have a Dual monitor set-up and for some reason my second monitor now comes up as a black screen. i cant figure out what i did to make this happen or how to get it working again.
 
any ideas?

---

### Post by howefield on 2009-10-22
What's the make of video card ?

You haven't done any updating just before the problem, particularly to the video drivers, Absolutely nothing ?

---

### Post by Naugh on 2009-10-22
Nvidia 9800GT.

I do believe i updated the driver last time i was running ubuntu, I run a dual boot system and it has been a while since i have booted ubuntu. 

I just download the new update but cant seem to run it

---

### Post by howefield on 2009-10-22
Have you tried using nvidia-settings to reset your configuration ? 

From a terminal type

```
gksu nvidia-settings
```

---

### Post by scouser73 on 2009-10-22
Please follow these instructions for setting up dual monitors.

**1** - Paste this command into terminal: **gksudo nvidia-settings**

**2** - Then go to **X Server Display Configuration** then set up your monitors to your liking

**3** - Once you have done so click **Apply** then click **Save To X Configuration File**

You will now have dual monitors working.

---

### Post by Naugh on 2009-10-27
I have tried this a few times and my result is two blank screens instead of one. I have to restart computer in order to get the 1st screen back.

---

### Post by dhenwood on 2009-11-02
I am experiencing the same problem. 

Dual screens worked fine under Jaunty, but after updating to 9.10 I now only have one screen. Any time I try to change the screen to dual screens again I get two blank screens instead of one and have to reboot, or wait for the timer to trip back to the previous configuration.

Any help fixing this would be great. 

My Nvidia drivers are 185.18.36

---

### Post by JBAGroup on 2009-11-02
I'm having similar wierdness with my dual monitor setup.  [Here's my post.]("http://ubuntuforums.org/showthread.php?t=1307931")  Hope somebody can help with a little insight on this stuff.

---

### Post by dhenwood on 2009-11-03
I forced updates and I now have two screens. 

However only the right screen is active  and usable. The left screen is a copy of my right screen right after login (tool bars, wallpaper, etc) but with no changes, no access. 

I've tried fiddling with the Nvidia settings but it does nothing. 

With the right hand screen I can go off the edge of the screen as it seems to think that they is another screen on the right of it, which there isn't.

---

### Post by dhenwood on 2009-11-03
I've just noticed something. The right hand screen which I have access to has all 9.10 icons at the top right (the new connectivity, and status buttons.)  The screen on the left that I can't interact with or do anything to at all, has 9.04 icons in the top right corner.

Am I running both 9.04 and 9.10 at the same time ? lol  Its one box, with a single graphics card with a splitter coming off of it.

---

### Post by rcragun on 2009-11-03
I'm also having issues after upgrading to 9.10.  In Ubuntu 9.04 my dual monitor setup worked fairly well - my laptop (Lenovo Thinkpad R60) was able to run it's monitor and a Viewsonic 17" LCD monitor both at 1024x768.  It could also do this with projectors (I use it for teaching my classes).  Now, for some reason, it can't run two monitors side-by-side at 1024x768.  The new display preferences dialog is better at supporting "mirror screens" than 9.04, but it's having serious issues doing side-by-side screens.  Not sure why.

Right now I have the ViewSonic monitor running in 800x600 with the laptop running in 1024x768 (I can invert that and it works as well).  It's just running them at the same resolution that isn't working.  Oh, and running the Viewsonic at higher resolutions while the laptop is running at 1024x768 also doesn't work, but if the laptop is at lower resolutions it does.

I'm wary of using the NVidia Xconfiguration tool as I don't have an NVidia card on my computer (it has an integrated Intel 945GM card).  Is it possible to run the NVidia Xconfiguration driver without an NVidia card, or will that screw up my computer?

---

### Post by almahtar on 2009-12-08
I had the same problem. The issue in my case was that I'd chosen a proprietary nvidia driver with the hardware drivers manager then run the updates utility - it updated my kernel and must not have appropriately upgraded my driver.  When I chose a different version of the same driver with the hardware utility it downloaded, installed, restarted, and worked great.

Moral of the story is if your kernel gets updated you may have to reinstall your video drivers.

---

