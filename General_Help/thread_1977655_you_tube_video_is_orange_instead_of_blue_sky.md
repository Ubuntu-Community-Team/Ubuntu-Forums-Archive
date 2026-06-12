---
title: "you tube video is orange instead of blue sky"
date: 2012-05-10
forum: General Help
---

### Post by geovino on 2012-05-10
I just installed Lubuntu 12.04 64 bit.

All seems to be working fine except, when I test a video of mine on youtube, the video is am orange tone and orange sky instead of blue. Never seen this before. What could cause this? How to fix?

Thanks.

---

### Post by jefsview on 2012-05-10
That's the current state of Adobe Flash. It doesn't play well with Nvidia cards. The workaround is either to downgrade Flash (exposing you to security risks), or to right click on the playing video, head to settings (not global) and un-check acceleration. Reload the video and all should play as intended.

Or use minitube. or only view HTML5 videos.

you could also use Gnash instead, but it doesn't deliver all of the options of Adobe Flash.

-- Jeff

---

### Post by idoitprone on 2012-05-10
> **jefsview said:**
> That's the current state of Adobe Flash. It doesn't play well with Nvidia cards. The workaround is either to downgrade Flash (exposing you to security risks), or to right click on the playing video, head to settings (not global) and un-check acceleration. Reload the video and all should play as intended.

Or use minitube. or only view HTML5 videos.

you could also use Gnash instead, but it doesn't deliver all of the options of Adobe Flash.

-- Jeff

or you can install mozilla plugger and vlc plguins to view flash under totem player
I recommend using both this and html5 since totem player will pick up the slack

the flash plugin should be alias as 11.1 i believe in about:plugins

Cons
Video lower resolution
it only works with youtube

Advantages
No flash
No ads

---

### Post by geovino on 2012-05-10
I think I know why, but I'll check it later (I'm on my Ubuntu hdd).

When installing Lubuntu, I checked off the third party multimedia and updates, which I normally set up after the install. Maybe fluendo is the cause. When I've installed Lubuntu 11.10 on my netbook, I installed lubuntu-restricted-extras and everything was fine. I'll go back to Synaptic and see of I can change things around... I'll let you know what I find.

---

### Post by geovino on 2012-08-11
I've since installed Ubuntu 12.04 on my Asus netbook and the sky is blue. It's the Ubuntu install on my desktop that also has Bodhi Linux on another hdd and Win7 on a third. The desktop has a Nvidia GS8400 video card. 

In Youtube the sky is blue when played in Bodhi and Win7 and orange in Ubuntu 12.04. So the problem is with Ubuntu and not the video card. Why would Ubuntu have this problem and Bodhi does not?

Any clues on how to solve this problem?

---

### Post by pqwoerituytrueiwoq on 2012-08-11
another workaround is to disable hardware acceleration
```
~$ cat /etc/adobe/mms.cfg 
OverrideGPUValidation=false
EnableLinuxHWVideoDecode=0
```find any flash element right click it and lets you click settings and uncheck the hardware acceleration option
there is anotherway
[http://www.nvnews.net/vbulletin/showpost.php?p=2518770&postcount=104](http://www.nvnews.net/vbulletin/showpost.php?p=2518770&postcount=104) it is a bit complicated

---

### Post by SeijiSensei on 2012-08-11
Rather than editing files, you can open a YouTube video, make it full screen, then right-click on the image and choose Settings.  Uncheck the hardware acceleration box.  Leave firefox and restart.

This is a problem that only concerns Flash videos that use Adobe's "Stage Video" methods to take advantage of H.264 hardware acceleration on NVIDIA cards.  They reversed the red and blue channels in the current, and final, version of Flash for Linux, 11.2.  Since Adobe has abandoned us, the problem will never be fixed.

---

### Post by geovino on 2012-08-14
> **SeijiSensei said:**
> Rather than editing files, you can open a YouTube video, make it full screen, then right-click on the image and choose Settings.  Uncheck the hardware acceleration box.  Leave firefox and restart.

This is a problem that only concerns Flash videos that use Adobe's "Stage Video" methods to take advantage of H.264 hardware acceleration on NVIDIA cards.  They reversed the red and blue channels in the current, and final, version of Flash for Linux, 11.2.  Since Adobe has abandoned us, the problem will never be fixed.

I'll check it out when I'm back on Ubuntu.

Right now I'm using Bodhi 2.0 (based on Ubuntu 12.04) on another hard drive on the same computer and I don't have that video problem with Youtube. Go figure?

---

### Post by SeijiSensei on 2012-08-17
So today I see a new copy of adobe-flashplugin and installed it.  Of course it doesn't fix the problem many people here have complained about for months now -- the reversed color channels.  Why bother releasing updates if they don't actually fix the problems we all know are there?

---

### Post by QIII on 2012-08-17
A few things to keep in mind here, as I see it:

1.  Adobe unilaterally chose to support hardware acceleration only for NVIDIA in Flash.

2.  The most recent Linux NVIDIA drivers are producing this "smurf"  effect when hardware acceleration is enabled in Flash and the solution is either to use an older version of Flash  (unsafe), an older NVIDIA driver, turn off hardware acceleration in  Flash or run without the NVIDIA driver and use the open source driver.  The least irksome solution is  to turn off hardware acceleration in Flash -- even though that dumps the work on your CPU.

3.  The Windows NVIDIA driver is a matter entirely separate from the Linux NVIDIA driver, so any comparison between what Windows and Ubuntu are doing is of no value.

4.  Adobe has discontinued development of the Linux version of Flash except for security updates.  Any updates we are getting right now are security only and not functional.  But for security reasons, updates are being released.

5.  If Bodhi works and Ubuntu doesn't, one has to ask if the same driver is installed on both.

---

### Post by geovino on 2012-08-17
> **QIII said:**
> A few things to keep in mind here, as I see it:

1.  Adobe unilaterally chose to support hardware acceleration only for NVIDIA in Flash.

2.  The most recent Linux NVIDIA drivers are producing this "smurf"  effect when hardware acceleration is enabled in Flash and the solution is either to use an older version of Flash  (unsafe), an older NVIDIA driver, turn off hardware acceleration in  Flash or run without the NVIDIA driver and use the open source driver.  The least irksome solution is  to turn off hardware acceleration in Flash -- even though that dumps the work on your CPU.

3.  The Windows NVIDIA driver is a matter entirely separate from the Linux NVIDIA driver, so any comparison between what Windows and Ubuntu are doing is of no value.

4.  Adobe has discontinued development of the Linux version of Flash except for security updates.  Any updates we are getting right now are security only and not functional.

5.  If Bodhi works and Ubuntu doesn't, one has to ask if the same driver is installed on both.


Good point. I now remember that I installed whatever driver Ubuntu selected for my nvidia 8400. With Bodhi I didn't install any additional drivers. But the Enlightenment desktop has 3D shading on windows and its smooth and fast without any additional drivers. Maybe that's why its called Enlightenment. :)

---

### Post by SeijiSensei on 2012-08-17
I'm aware that this is an issue with NVIDIA hardware acceleration.  However the problem is in the Adobe player, not the NVIDIA driver.  I also realize that they have discontinued development of the driver, but how hard would it be to fix a minor bug that reverses the red and blue channels in software?  This is all Adobe's fault, and they have no interest in fixing it.  Introducing a profound bug like this one in the final release of their software, then walking away from it, is yet another reason why Adobe ranks high on my list of most-despised commercial software vendors.

---

### Post by QIII on 2012-08-17
Just the facts.  There was no intent to implicate NVIDIA itself.  I said the least irksome solution was to turn off hardware acceleration in Flash.

We'll never know if this was some sort of "parting shot" by the Adobe developers and Flash is dead to us in any case.

---

### Post by Habitual on 2012-08-18
[http://askubuntu.com/questions/117127/flash-video-appears-blue](http://askubuntu.com/questions/117127/flash-video-appears-blue)
maybe relevant?

---

### Post by mc4man on 2012-08-18
> **Habitual said:**
> [http://askubuntu.com/questions/117127/flash-video-appears-blue](http://askubuntu.com/questions/117127/flash-video-appears-blue)
maybe relevant?
For 11.10 * 12.04 users there is a ppa recommended in above ask ubuntu  that will provide you with a patched libvdpau. This works quite fine & is the best solution.

Ubuntu is providing a patched libvdpau but atm is only in 12.10
(you can use the 12.10 package(s) in 12.04 but the ppa route is likely better for most users

---

### Post by geovino on 2012-08-19
Just installed latest updates with a new flash plugin and now the sky is blue again on youtube video.

---

### Post by geovino on 2012-08-23
.... that didn't last long. today people in youtube video have a blue cast. And the sky is orange again. what makes it change? :(

maybe I should uninstall the nvidia driver? If I uninstall the nvidia driver in synaptic will it go back to the generic driver after a reboot?

---

### Post by geovino on 2012-08-26
If I try to Uncheck the hardware acceleration box, it freezes up.

This only happens with videos in Youtube. All other videos sites have been OK.

---

### Post by geovino on 2012-08-27
Just tried an experiment...

Ran youtube.com/html5

Using html5 instead of flash, the sky is BLUE :)

So the problem is the flash component in youtube.

I'll be glad when flash is gone and html5 takes over all video online.

---

