---
title: "Any way to use 2 xorg.conf? Or alternately, a script to change nvidia monitor setting"
date: 2010-07-20
forum: General Help
---

### Post by indstr on 2010-07-20
I have a dual monitor setup running in Xubuntu studio Karmic. I am using nvidia binary drivers. The resolution is 2048x768 when both monitors are active. 
 
Here is the goal:
 
Quickly change monitor/resolution/rotation settings so I can load up lower resolution video games on one screen and make them take up the whole screen, without having to click through a bunch of menus (and then change the settings back when I am done)
 
I have tried 2 approaches, and a solution to either of them would be acceptable. The ultimate question for each approach is bolded.
 
1) xrandr -- Currently I use xrandr to rotate the screen, which I know could be set up easily as a script. However, the problem is that I do not know how to turn off the second monitor with xrandr, because currently my "screen", setting in xorg.conf is just one large "virtual screen" of 2048x768, so when I run xrandr, the "min" and "max" resolution are both 2048x768, so "xrandr -r" does not do anything. **Do I need to fix my xorg.conf to have both monitors/output devices?**
 
2) A virtual X session - ( [http://ubuntuforums.org/showthread.php?t=271674](http://ubuntuforums.org/showthread.php?t=271674) ) I tried this, and it is a really neat idea. I was able to change the resolution in the virtual session using the nvidia-settings panel, and it was great to go back and forth between it and the "real" one. However, the problem is that when you save changes with nvidia-settings, it updates the xorg.conf ....  The same one that the "real" XFCE is using. **Is there any way to make the virtual X session use a different xorg.conf file?**
 
3) If I do have to edit my xorg.conf for option 1, **does anybody know of a good tutorial that breaks it down very simply so it is easy to understand and quick to do?** I have messed with it before and didn't find it an entertaining experience. I have also tried a GUI configuration program (I believe it's just called xorg.conf gui) and it was just about useless. 
 
Thanks for any help

---

### Post by LowSky on 2010-07-20
Just go into nvidia-settings and change the resolution from there. Why make it more complicated than it has to be? Also you should really update to a newer verison of Ubuntu.

---

### Post by indstr on 2010-07-20
> **LowSky said:**
> Just go into nvidia-settings and change the resolution from there. Why make it more complicated than it has to be? 
 
That requires:
 
1) clicking on my nvidia-settings icon
2) selecting the monitor on the right
3) choosing either "clones" or "off"
4) clicking "apply"
5) going over to the left monitor
6) selecting the correct resolution and possibly refresh rate
7) clicking "apply" again 
8) sometimes changing the "virtual display" area to 1024x768, while leaving the res at 640x480 (sometimes, depending on what game I am playing)
9) opening up a console
10) typing xrandr -o left (sometimes)
 
(all of this again in reverse when I am done playing a game for 10 minutes)
 
That equates to somewhere between 15-20 unnecessary steps just to play a game for a few minutes. This is after already standing up to physically rotate my monitor for games with vertical orientation. Can you see why I wouldn't really want to do this?
 
Vs. 1) Click on script that does all of the above instantly
 
 
> **LowSky said:**
> Also you should really update to a newer verison of Ubuntu.
 
(Appologies in advance for the rant...)
 
Wow, are you serious? There are some of us who don't feel the need to be on the "bleeding edge", and don't like to waste all our time upgrading our OS every six months, only to have some of the stuff break on it and require messing around with it all night just to fix it back. 
 
I compiled my own kernel specifically for low latency music production. It's tweaked how I want it. It's stable. It does everything I need it to do. (Except the resolution switching, heh). I'm not messing with it for a while. 
 
P.S... Something like 50% of all computers in the world still run Windows XP (Came out in 2001 mind you). And I get hounded for running an OS that is 9 months old? What the ??
 
Edit: I've also considered using my Windows XP dual boot for gaming, but that, too, takes time. Which is something I don't have a lot of. 
 
Can you see that I'm trying to save myself some time here? It's all about the efficiency, man. That's what we have computers for in the first place, isn't it? To automatically do all the stuff that we shouldn't have to do repeatedly, freeing up our own time for more meaningful things.

---

### Post by endotherm on 2010-07-20
> **indstr said:**
> 
Wow, are you serious? There are some of us who don't feel the need to be on the "bleeding edge", and don't like to waste all our time upgrading our OS every six months, only to have some of the stuff break on it and require messing around with it all night just to fix it back. 
 
I compiled my own kernel specifically for low latency music production. It's tweaked how I want it. It's stable. It does everything I need it to do. (Except the resolution switching, heh). I'm not messing with it for a while. 
 
P.S... Something like 50% of all computers in the world still run Windows XP (Came out in 2001 mind you). And I get hounded for running an OS that is 9 months old? What the ??

karmic isn't really that old, but it has also been widely touted as the least stable version of ubuntu released. the last release before an LTS is essentially a beta and staging for the new stuff coming soon, so they are usually problematic. upgrading to an LTS is a good move, especially for folks like you who want to get it set up and then sit on it for a few years.

---

### Post by Primefalcon on 2010-07-20
> **endotherm said:**
> karmic isn't really that old, but it has also been widely touted as the least stable version of ubuntu released. the last release before an LTS is essentially a beta and staging for the new stuff coming soon, so they are usually problematic. upgrading to an LTS is a good move, especially for folks like you who want to get it set up and then sit on it for a few years.
A lot of people only run LTS version, and then sometimes wait till their LTS is being close to non-supported to upgrade to the next LTS in the list, as such a lot are still running 8.04 hardy for that reason, and probably wont upgrade to 10.04 for another year.... And considering server support wont run out on 8.04 LTS until 2013, some wont upgrade their servers until then...

I have until now upgraded every cycle, however I am getting a little tired of beta testing the standard releases effectively, so I am considering skipping the next  few releases myself until the next LTS, and then waiting a month until after it's release to upgrade

---

### Post by indstr on 2010-07-21
After a bit of messing around tonight, I've pretty much figured out what I need to do. I added some metamodes to my xorg.conf tailored to my needs. Unfortunately, the XFCE panels don't like to recognize the second monitor once it has been disabled, and re-enabled. And for some reason, XFCE won't even start when I added cloned screen metamodes. (Although gnome does) So I am still forced to use a virtual X server...  

Here's what I did:

1) Made some custom metamodes (and custom modelines too for odd resolutions like 450x600) 
2) Installed a nice little xrandr gui called "arandr" which can make some scripts 
3) Using the virtual X server to load another XFCE just so it doesn't mess up my panels on my primary one (Gnome/KDE users may not have this problem ? ) 

What the heck do I use 450x600 for? 

[IMG]http://www.caiman.us/freepix/2762-3.jpg[/IMG]

Getting sweet bullet hell shooters like "Flew fighter" to take up the full screen in vertical orientation, even though the game was designed for 4:3 and just has bars on the left and right.   :D

---

### Post by indstr on 2010-07-21
I also figured out how to fix the xfce panel even in my default xfce session: xkill it, and then when it automatically restarts, it comes back on both screens. Now I have lots of options. 
 
Took a while to setup, but it should be extremely useful for a long time to come. \\:D/

---

