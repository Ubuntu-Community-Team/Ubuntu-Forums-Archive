---
title: "Stutters, slowdowns, hangs"
date: 2012-02-18
forum: General Help
---

### Post by mtfr on 2012-02-18
Hi. I installed Lubuntu 11.10 on my laptop which is pretty old (Pentium M @1400 MHz, 1,2 GB RAM, Radeon Mobility 9000). For exactly one month (January 2012) it has run well and I could do some multitasking quite well.

Then maybe 2 weeks ago (beginning of February) the OS started to have very brief but often stutters, slowdowns, hangs, or what is the proper English term. There hasn't been any sort of transition between Lubuntu behaving smooth and stuttering as it is now, it all started all of a sudden in one day. The slowdowns are very short, not even half a second, but they are often as they coincide with spikes of CPU usage (these spikes are normal and caused by my normal workload). For example:

[LIST]
[*]when starting up any application such as a web browser, the mouse cursor freezes for very short moments, but often, until the app eases up on the CPU as it approaces the end of loading up
[*]when scrolling a moderately heavy page in a web browser (it doesn't have to be heavy on Flash content) there are quick freezes of the OS for every little intermediary step of the scrolling (I guess the browser is trying to produce a smooth scroll)
[*]the most obvious way this problem affects is as a massive slowdown of Flash clips (I use my laptop mainly for browsing now until I'll buy a proper desktop computer); to make it clear, only small+low-res clips are watchable now and only when NOT in full-screen, e.g. 360p Youtube clips; before this slowdown problem started I could watch very well 480p YT in full screen (20+ FPS), but now I get an abysmal ~5 FPS combined with huge lags in UI responsiveness; I have to mention that CPU usage was at almost 100% also before the slowdown started, but at least I got very watchable framerate so the CPU usage was understandable
[/LIST]

I have to mention 2 more things that might help somebody understand the issue: first, I thought the video acceleration must be messed up, but I tried glxgears and it produces a good FPS (v-sync-ed 60 FPS in window and 40 FPS in full screen external monitor 1280x1024) and running glxgears doesn't cause any spike in lags or freezing.

And the last relevant piece of information I can think of is that VLC, without any spikes of lags or freezings, is able to play very well a 4 GB DVD ISO, window and full-screen at very good framerate just as if my computer was top notch.

I have no idea what might be causing the slowdowns, I will be grateful if anyone can help. I did regular OS updates when they became available but I didn't realize if the slowdowns appeared immediately after one of the OS updates.

---

### Post by claracc on 2012-02-19
Lubuntu 11.04 installed in an older and less resources machine than yours (pentium II laptop, 1GHz CPU, 512 Mb ram, 64 Mb of it for graphics card, 20 Gb HD) and I can surf the web without any freezing, however when web pages are loaded the CPU goes for 100% (it is logical with the amount of flash).

What web browser are you using?. I discarded firefox or chromium in this old laptop because they consume a lot of resources and the loading of pages or playing the flash videos takes a lot of time.

I use epiphany browser, the 2.30 realease I think, and except some weird crashes in certain web pages when click on back button it renders well. 

Playing flash videos in a so slow and old machine is a little far beyond its capabilities (but you can blame adobe flash for it). For yuotube flash videos I installed greasy monkey script to use my video player: smplayer and it plays them very well without exhausting the CPU resources.

Have you tried smplayer instead of VLC?. In my old machine smplayer works better (less resources, more responsive) than VLC

---

### Post by mardybear on 2012-02-19
> **mtfr said:**
> Hi. I installed Lubuntu 11.10 on my laptop which is pretty old (Pentium M @1400 MHz, 1,2 GB RAM, Radeon Mobility 9000). For exactly one month (January 2012) it has run well and I could do some multitasking quite well.

Then maybe 2 weeks ago (beginning of February) the OS started to have very brief but often stutters, slowdowns, hangs, or what is the proper English term. There hasn't been any sort of transition between Lubuntu behaving smooth and stuttering as it is now, it all started all of a sudden in one day. 


Greetings.

I run Ubuntu on old systems (you don't wanna know my specs) and noticed that the most recent kernel upgrade is causing some problems for me...system hesitates, very slow firefox, poor overall graphic performance.

If you haven't already done so, reboot your computer and select an older kernel from the grub menu and see if this makes a difference...it did for me. Maybe it will help you too.

Ubuntu is a great operating system when you're able to get it running without bugs. Good luck,

mardybear

---

### Post by mtfr on 2012-02-19
Claracc, as I said, VLC still runs impressively fast and top notch for me, because somehow it's the only app on my system that isn't affected by the slowdown (and, well, glxgears). As for web browser, I am using Opera, Firefox and Chromium all the same and they display similar performance (first good, now bad). I'd like to fix the root of the freezings, and not go around it by giving up my usual apps that used to work just fine. But thanks for recommending Epiphany, I'll definitely give it a try. And I didn't know about watching YT clips with SMPlayer, I'll give that a try as well... after I solve the slowdowns :) By the way I'm using plug-ins in the web browsers to block Flash clips until I explicitly start them, and scrolling in the browser still is very heavy after my OS' slowdowns started.

Mardybear, thanks for the advice. I'll have to check how to get into GRUB at boot for doing that, and then I'll come back with an update.

---

### Post by mardybear on 2012-02-19
> **mtfr said:**
> Mardybear, thanks for the advice. I'll have to check how to get into GRUB at boot for doing that, and then I'll come back with an update.

Hi mtfr...

I have a dual boot system and the grub menu shows automatically during the boot process. I use the long term support updates and for me the 2.6.32.25-386 kernel does not work well but the older 2.6.32.21-386 kernel works great.

Maybe this will help you. Doesn't hurt to try, as you can always reboot back into the newer kernel. Good luck,

mardybear

---

### Post by Odexios on 2012-02-19
I'm having the exact same problems with lubuntu 11.10; (almost) everything worked smoothly until February, when I started experiencing slowdowns and so on. A friend of mine is facing the same issues with ubuntu 11.10; I guess an upgrade might have something to do with the problems.

---

### Post by mtfr on 2012-04-08
Wohoo, I found the problem. It's a kernel update. Either 3.0.0-13 or 3.0.0-14. Because when I boot with 3.0.0-12 everything works great as before. So maybe the same issue got introduced in the old branches that Mardybear experiences.

What to do now? I guess I should report this somewhere?

---

### Post by mtfr on 2012-05-08
I have bad news. I did a fresh install of the new Lubuntu 12.04 and it comes with the same huge performance regression: I get multiple short freezes when starting up applications, when scrolling up and down web pages (even if they're not fully loaded with flash plug-ins, even simple ones) and playing Flash videos (e.g. YouTube) happens at half frame-rate than before. Surprisingly video playing with e.g. VLC still works very smooth.

I also bought a Transcend 64 GB IDE SSD for my old laptop and installed it in at the same time when I installed Lubuntu 12.04. The boot-up is visibly faster so I am getting that advantage from the SSD. But unfortunately the freezes still persist, so it's pretty sure coming from the kernel version I mentioned (3.0.0-13 or 3.0.0-14), nothing to do with the hard drive or other components.

---

### Post by mtfr on 2012-06-09
I upgraded my Lubuntu 11.10 to kernel 3.0.0-20 and the performance problem is there too.

---

### Post by mtfr on 2012-08-19
Problem persists all the way through 3.0.0-24. I have to boot using 3.0.0-12 to get my normal performance back.

---

### Post by mtfr on 2012-11-09
Problem persists all the way to 3.0.0-26.

---

