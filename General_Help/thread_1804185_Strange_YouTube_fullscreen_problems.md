---
title: "Strange YouTube fullscreen problems"
date: 2011-07-14
forum: General Help
---

### Post by zorblek on 2011-07-14
For the last couple of weeks, I've started having odd problems with YouTube videos in fullscreen mode.

Not always, but more often than not, when I make a video fullscreen I don't see the video, just a black screen. The controls appear as normal, and I can hear the audio, but there's no picture. Sometimes if I mess around with the controls (pausing and unpausing it, selecting a different bitrate, exiting then reentering fullscreen, etc.) I can make the picture appear, but not always.

Today I started getting another odd glitch: sometimes, instead of not showing the video, it will show it in black-and-white instead of color!

As far as I can tell, this only happens with YouTube videos and only in fullscreen. I've had the same thing happen with both Firefox and Chrome, so I don't think it's a browser issue.

I've tried a variety of things - deleting my Flash profile, using the Flash-Aid Firefox extension to install different versions of Flash with different settings - and nothing has helped.

I'm really puzzled, and I haven't found anyone else with this same issue. Any insight would be greatly appreciated.

---

### Post by CatKiller on 2011-07-14
> **zorblek said:**
> Not always, but more often than not, when I make a video fullscreen I don't see the video, just a black screen. 

Uncheck Override GPU Validation in Flash Aid.

> Today I started getting another odd glitch: sometimes, instead of not showing the video, it will show it in black-and-white instead of color!

That's because that application is no longer receiving input. Install *compizconfig-settings-manager* and uncheck Dim Unresponsive Windows in the Fading Windows plugin of Compiz.

---

### Post by zorblek on 2011-07-14
I should have been more specific in my original post - I've tried pretty much all permutations of Flash versions and enabling/disabling GPU validation.

And I'm pretty sure the black-and-white effect is not the dimming that happens as the result of an unresponsive window. The window seemed to be responding fine, and only the video was affected, not the controls, which appeared with normal coloration.

Thanks, though.

---

### Post by zorblek on 2011-07-14
I checked just to be sure, and disabling window fading has no effect.

---

### Post by zorblek on 2011-07-19
Further information: the black screen problem seems to have been completely replaced by the black-and-white video problem. As far as I can tell I always get the former now and never the latter.

I've also noticed something else about the black-and-white video phenomenon. It's definitely just the video. Even annotation bubbles show up in color over it. Sometimes the toolbar the video controls doesn't display properly, though. It displays in full color, but sometimes when it autohides, parts of it don't show up when I move the mouse to the bottom of the screen again.

As far as I can tell, none of this has happened because of anything I changed. The initial problem happened with no warning, and the change of problems (from no video to black-and-white video) happened well after I had stopped trying to fix it.

---

### Post by t.h.w. on 2011-08-11
> **zorblek said:**
> Further information: the black screen problem seems to have been completely replaced by the black-and-white video problem. As far as I can tell I always get the former now and never the latter.

I've also noticed something else about the black-and-white video phenomenon. It's definitely just the video. Even annotation bubbles show up in color over it. Sometimes the toolbar the video controls doesn't display properly, though. It displays in full color, but sometimes when it autohides, parts of it don't show up when I move the mouse to the bottom of the screen again.

As far as I can tell, none of this has happened because of anything I changed. The initial problem happened with no warning, and the change of problems (from no video to black-and-white video) happened well after I had stopped trying to fix it.

Same problem here....

---

### Post by zorblek on 2011-08-12
I found a workaround: If I change the video's resolution to a lower value, make the video fullscreen, and then change the resolution back that usually fixes the black-and-white video problem - until the next time I need to play a video fullscreen.

---

### Post by NoBody122 on 2011-09-13
I'm not a common Ubuntu-user, but I did find this topic whilst Googling this exact same issue, which I'm currently experiëncing as well (but on Gentoo, with KDE).

I found out that to get colors back in fullscreen mode, you have to disable 'Hardware acceleration' in Flash settings (rightclick any embedded Flash-app, then click 'Settings', there you can disable it). That at least is what got my colors back.

Probably an issue between the Linux Flash-plugin and (some) VGA-drivers, at least the Ati-one using the new KMS kernel-drivers. Not sure whether changing to the old Ati-kerneldrivers helps.

As this topic is 'only' 4 weeks old, I thought this information may still be helpful to the TS and/or others stumbling upon this topic in the (near) future :)

---

### Post by zorblek on 2011-09-13
I've gotten a new computer since I last posted here, so I'm no longer having this problem. However, I do have a piece of information. A friend of mine who uses Windows XP had the exact same issue, so it's definitely not an Ubuntu-specific problem.

---

