---
title: "Compiz Slowdown"
date: 2011-04-30
forum: General Help
---

### Post by lakerssuperman on 2011-04-30
I am running 11.04 an Intel Core i7-2600k and NVIDIA Geforce 560 Ti Superoverclock.  Yet, I will get random slowdowns when minimizing windows or opening programs.  It doesn't slow to a crawl but will clearly become less smooth and stutter for a second.  I have been unable to pin down the problem to any one program.  I have tried seeing if it was video playback, music playback, heavy Flash on web pages, anything that might be engaging the video card but I haven't found anything to reliably reproduce it.  I am running the latest binary drivers and haven't experienced any crashes, just the odd lag which occurs on my laptop and spare desktop as well, all running modern CPU's and some variant of NVIDIA card.

Is anyone else having similar problems with NVIDIA cards or just in general?

---

### Post by lakerssuperman on 2011-04-30
I should also mention that CPU usage isn't spiking in the slightest and remains low on all cores and I experience some tearing when watching fullscreen video even though vsync is enabled and smooth scrolling in both Chrome and Firefox 4 becomes jagged as well.

---

### Post by lakerssuperman on 2011-04-30
I kept playing around with things and eventually noticed that it was in fact being caused by websites with excessive Flash.  I updated to the Flash Square Player ppa and also installed Java, even though I thought I installed it already, and it seems to be much smoother now.  Hopefully it keeps up.

---

### Post by lakerssuperman on 2011-04-30
Further update.  I have compared my 11.04 installation with a fresh install of 10.10.  I updated 10.10 to the latest packages and installed Firefox 4, VLC, Flash Square and the latest NVIDIA drivers from X-Swat so as to get as much of the software the same between the two as possible.  The 10.10 build is still much smoother and doesn't experience any of the lag that 11.04 exhibits when playing back a hd movie on VLC while browsing.  Also running Gnome Mplayer on 11.04 with VDPAU crashes when minimized to the launcher.  I am going to reinstall my 11.04 build and see if perhaps something has simply gone amiss with my 11.04 install.

---

### Post by lakerssuperman on 2011-04-30
I can confirm after a clean install that using Gnome Mplayer with VDPAU crashes when minimizing to the launcher.  Compiz also is still not as consistently smooth as in 10.10 and periodically slows down when running in the Unity environment.  I just ran the same test using the same programs in the Classic environment) with effects) on 11.04 and it does not exhibit any of the slowdowns in unity.  Also, the tearing that was occurring in video playback is gone as well.  I haven't checked for any bug reports on this yet.

---

### Post by lakerssuperman on 2011-04-30
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/687738](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/687738)

I came across this bug report which may have something to do with it.

---

### Post by lakerssuperman on 2011-04-30
While experimenting with video playback in the Classic environment, after a few minutes of playback, minimizing the video player while using VDPAU crashes the player here as well.

---

### Post by lakerssuperman on 2011-05-01
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/600178](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/600178)

This appears to be the bug.  There are a few other threads on the forum so I will direct further posts there.

---

### Post by jebus_beler on 2011-05-02
Just to confirm, I've noticed the same slowdown.  I have very similar hardware - an i7 2600k and an msi gtx 560 twin frozr ii/oc.  When I first used the system it was quite smooth and nice but now after watching a couple of videos and then leaving the system on overnight everything seems to be very laggy.  Moving windows is choppy and various things are slow to respond.  This is very inconsistent however as e.g. window elements in nautilus seem fine.  Typing in an x-term is slow as the text appears only with a lag but I don't get the same problem on gvim.  As you say my cpu usage is very low and I have 8 gigs of ram that are mostly going untapped so that is definitely not the problem.

---

### Post by lakerssuperman on 2011-05-02
Playing with the vsync settings in compiz and NVIDIA can restore smoothness for a time but it will resume and there doesn't seem to be any repeatable way to restore it.  I would imagine that the fault must lie in the X Server or the new Unity environment.  Either way this is a fairly large bug as it damages the overall presentation of the new interface for a number of users.

---

### Post by jebus_beler on 2011-05-02
Thanks, it was your thread that directed me to the bug report.  Can I ask: where are you changing your vsync settings?  I don't see vsync settings in cccm or the nvidia control panel.  Do you mean 'Sync to Vblank"?

Also, do you get this problem even if you don't ever watch videos?  I mean is it avoidable or will it always eventually crop up on an nvidia card with natty?

---

### Post by lakerssuperman on 2011-05-02
Yes I mean Vblank in both the NVIDIA settings and in Compiz Settings Manager.  

The behavior appears to be random.  Last night I was humming along and everything was extremely smooth while watching video and doing web browsing.  Today I was using my computer after work and it started to degrade in performance while I was using Chrome.  Prior to some of this other behavior, I thought that there may have been a bug in the smooth scroll plugin with Chrome but it wasn't exactly reproducible, but may be one of the things that causing the degradation in performance.

I have not had any hard locks or crashes, the desktop simply becomes laggy and much less smooth.

---

### Post by lakerssuperman on 2011-05-07
Just wanted to update my findings.  I pulled out my old Radeon 4870 to see what kind of performance it gets with Unity and the latest Catalyst drivers.  I hooked it in to my Core 2 Q6600 quad machine and did a fresh install of 11.04.

At first Unity is terribly laggy.  However, if you you enable "Tear Free Desktop" in the Catalyst control center, disable "Sync to Vblank" in the Compiz Settings Manager and disable "Detect Refresh Rate" in the Compiz Settings Manager, you get an extremely fluid desktop.  I even have VLC working with VAAPI and GPU acceleration with no slow downs.

My first thought was how smooth and problem free the Catalyst driver performed.  For awhile, and maybe still, ATI/AMD drivers have been a nightmare.  I had to abandon this card because of the lack of proper vsync and constant tearing, but it seems they have raised the quality as of late.

My second thought is this problem may be due to the NVIDIA driver and not some other component.  Besides the poor Unity performance, I was playing with the latest drivers on my Windows 7 install on my main desktop and have experienced some really buggy performance lately from the latest drivers.  There are random crashes in my games and lagginess.  I have had to revert to an older beta driver just to keep stability.  As the NVIDIA driver shares much core code between Linux and Windows it seems as though NVIDIA is having some driver issues as of late.

---

### Post by jebus_beler on 2011-05-10
Please let me know if you manage to do this and it works.  The problem was so annoying with me that I downgraded to 10.04 though I've kept my 11.04 install around to go back and check on it every once in a while.  I have to double check but it is my impression that while 11.04 is running normally it is noticeably smoother and faster than 10.04 (of course once the lagging sets in its much worse).  I'm not sure if this is an nvidia driver improvement or is maybe due to the "200 line" kernel patch.  In 10.04 the nvidia driver does not have any lagginess but there is an almost unnoticeable tearing when windows are moved but my recollection is that in 11.04 there is absolutely no tearing (again when its working well).  Applications also seemed to launch more quickly in 11.04 so I have several reasons I'd like to go back to it but this nvidia issue really was too annoying -- having to restart the machine every few hours is not tenable.

---

### Post by lakerssuperman on 2011-05-13
I will.  I've been watching the updates and waiting for a new release from NVIDIA.  My Radeon shows none of these problems so I hope NVIDIA can sort this out quickly and get things rolling smoothly again.

---

### Post by lakerssuperman on 2011-05-15
Latest update

I wiped out my 11.04 install and went back to a heavily modified 10.04 install.  Everything is smooth as silk.  1080p video playing in the background does nothing to the system.  This is with the latest 20 driver off the website.  I still think this latest round of drivers from NVIDIA are pure garbage but it may well be the combo of Unity and NVIDIA at this point is a no go.

I'm not happy about this as I really like Unity and using the latest Ubuntu but I prefer a stable smooth desktop over anything.  I have reverted to using Docky/Gnome Do to replace some of the functionality I lost from switching back.  

I'm keeping my 11.04 install on my laptop as I don't leave it on long enough to notice much of a performance loss.  I'll keep it up to date and hopefully report back when some issues have been resolved.

---

### Post by lakerssuperman on 2011-05-16
After leaving the system running over night, I have begun to notice performance issues while running 10.04.  However, they are not as severe as when running Unity.  It seems clear that the driver is at issue here.

---

### Post by Seamyst on 2011-05-23
I'm having this problem too, with an ATI Mobility Radeon HD 4200 Series card in a Toshiba Satellite C655D. When running 10.04, the video was fine. I did a clean install of 11.04 yesterday, and now the video is laggy in Ubuntu Classic (I don't like Unity).

If I'm just checking email on Chrome it's not too bad, mainly noticeable as the "page loading" tab icon is slow and a bit jerky, like it's dropping a frame here and there. A music video on Youtube, however, gets noticeably out of sync within the first minute (and that's after the whole thing loaded, since my connection isn't the fastest). Scrolling on pages also is jerky, and there's a definite lag while I'm typing this. (That actually takes me back to an early-09s-era learn to type program, as I could type faster than it would recognize.)

For what it's worth, the CPU usage with just Chrome open (and two tabs, both forum pages) ranges from 37% to around 57%, and it might be changing based on my typing - I'm not sure of that. With Youtube also open in a tab, playing that music video, CPU usage goes up above 80%.

---

### Post by wildmanne39 on 2011-05-23
> **Seamyst said:**
> I'm having this problem too, with an ATI Mobility Radeon HD 4200 Series card in a Toshiba Satellite C655D. When running 10.04, the video was fine. I did a clean install of 11.04 yesterday, and now the video is laggy in Ubuntu Classic (I don't like Unity).

If I'm just checking email on Chrome it's not too bad, mainly noticeable as the "page loading" tab icon is slow and a bit jerky, like it's dropping a frame here and there. A music video on Youtube, however, gets noticeably out of sync within the first minute (and that's after the whole thing loaded, since my connection isn't the fastest). Scrolling on pages also is jerky, and there's a definite lag while I'm typing this. (That actually takes me back to an early-09s-era learn to type program, as I could type faster than it would recognize.)

For what it's worth, the CPU usage with just Chrome open (and two tabs, both forum pages) ranges from 37% to around 57%, and it might be changing based on my typing - I'm not sure of that. With Youtube also open in a tab, playing that music video, CPU usage goes up above 80%.
Hi, I am curious are any of you using the cube or other effects.

---

### Post by Seamyst on 2011-05-24
wildmanne39, I'm not using cube or any other effects; in fact, I disabled animations last night.

Okay, I disabled animations, Sync to VBlank, and Detect Refresh Rate in the CompizConfig Settings Manager, and enabled Tear Free Desktop in Catalyst. Youtube videos were noticeably smoother, with little or no sync problems. The loading page tab icon seemed smoother as well. I left the laptop running overnight and all day while I was at work.

There seemed to be no lag earlier this evening, and a ripped episode of Law & Order was perfectly synced. Watching a DVD, however, is another thing altogether. With Tear Free disabled, the movie is not nearly as laggy, but it tears regularly. Enabled, the tearing is gone, but it lags a lot more. Right now I'm ripping the movie so I can at least watch it comfortably, but I'd rather not have to do that every time I want to watch one of my own movies.

Typing (and erasing) also lags again.

---

### Post by ScottDeagan on 2011-09-13
I'm having the same problem - everything working fine, UI is buttery smooth, then at some random point it becomes laggy. It's extremely annoying, especially with Wobbly Windows enabled (I can't live without Wobbly Windows!).

Not sure if it's related, but there's a bug report from 2009 that sounds similar: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/380129](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/380129)

I'm running an AMD A8-3850 CPU with an nVidia GTX460 graphics card and the nVidia 280.13 drivers.

---

