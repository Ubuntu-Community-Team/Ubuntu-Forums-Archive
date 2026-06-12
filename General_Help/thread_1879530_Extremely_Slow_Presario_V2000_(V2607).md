---
title: "Extremely Slow Presario V2000 (V2607)"
date: 2011-11-11
forum: General Help
---

### Post by baekjae on 2011-11-11
Hey, I'm new here, and I'm extremely new to Ubuntu-- linux in general-- having recently decided to give it a shot on an old laptop my cousin gave me. The laptop is a Compaq Presario V2607CL, and appears to be stock as far as hardware is concerned (Turion 64-bit 1.8GHz ML-32, 512MB RAM, ATI 200M IGP), and had previously been running XP Pro w/ SP3 just fine.

So, Ubuntu 11.10 is installed and completely up to date, but is running ridiculously and unbearably slow. Everything works, though it took a little bit of work to get the WiFi running, and for some reason it couldn't detect the battery until a few moments ago, but other than that Thunderbird setup without a hitch, Firefox is working well enough, Terminal works fine, everything has been working... just really slow.

Looking at the system monitor the processor apparently never drops below 60% utilization, and both physical RAM and swap are running at about 50%, which seems normal enough to me. I assumed it would be a hardware issue, but the 'additional drivers' section doesn't pull up anything. Graphics apparently cannot be identified, so idk if maybe there's an issue with hardware acceleration or what.

I've done some searching but I haven't been able to find information that coincides with the problem I am having. I'd assume the V2000 works flawlessly judging by the amount of people who apparently have them working (albeit with wireless issues).

Any ideas? (Sorry for the multi-paragraph)

---

### Post by dcstar on 2011-11-12
> **baekjae said:**
> Hey, I'm new here, and I'm extremely new to Ubuntu-- linux in general-- having recently decided to give it a shot on an old laptop my cousin gave me. The laptop is a Compaq Presario V2607CL, and appears to be stock as far as hardware is concerned (Turion 64-bit 1.8GHz ML-32, **512MB RAM**, ATI 200M IGP), and had previously been running XP Pro w/ SP3 just fine.
..........

Don't try to run modern GUI OSs on such poorly provisioned hardware, how quickly do you think Windows 7 or Vista would run on such hardware?

Linux with a fully featured graphical desktop is not apropriate for out of date hardware.

---

### Post by baekjae on 2011-11-12
Thanks for the reply. Like I said, I'm new to ubuntu, and what had me interested in it was that I was under the impression it was much more lightweight than Windows 7. The laptop has a Windows Vista tag on it, and I gave Windows 7 a shot before loading ubuntu-- Win7 ran stable enough, but was too slow to be really useful, as I expected it would be... still ran better than ubuntu is now though. I plan on bumping up the RAM when I get the chance, but in the meantime I wanted something simple and clean that wasn't XP.
 
Anyway, you highlighted the RAM, and the RAM isn't the issue. On average I have about 220MB of the RAM, and about 60MB swap. The CPU, however, is jumping around between 50-70% utilization. Trying to figure out the cause with top and system monitor.
 
Having spent a little more time playing with settings, I installed XFCE, which runs much smoother; would GNOME Classic run smoother than GNOME/Unity? I'll play around with it and see what happens.
 
Sorry for the noob question; like I said, I saw a lot of hits for the V2000 w/ ubuntu, so I figured it must run smooth enough for others.

---

### Post by efflandt on 2011-11-12
Memory is likely a problem. It is shared with video, so your system may  be swapping and/or reloading more from disk instead of RAM cache.

The V2000 was a low end laptop. I inherited one with Sempron 3300+ (2.2 GHz) when I got someone a newer laptop. But the Sempron (which was an Athlon crippled to 32-bit and smaller cpu cache) along with shared video RAM was much slower than an Athlon64 3200+ (2 GHz) using ATI X1300 video card with its own RAM.  The Athlon was no speed demon for some games like Tuxracer, but it could play Supertuxkart smoothly vs. the laptop 200M video artifacts and tearing. But I had borrowed the 1 GB memory chip for another computer so the laptop only had its original 512 MB instead of ~1.3 GB at the time (with Ubuntu 10.04 or 10.10, which worked better on it than 9.04 or 9.10).  I have not tried 11.04 or 11.10 on it.

There was a time when you could run Linux with X on an 8 MB 386, but times have changed.  There are slim Linux versions available, but I am not familiar with them lately. Linux based IPCop works fine as a squid proxy at our office on an old AMD K6-2/400 w/128 MB RAM, but it does no graphics (not even a monitor connected normally) other than its web interface.

But even though Linux has grown, it uses nowhere near as much RAM as Windows 7.

---

### Post by 3rdalbum on 2011-11-12
Even with that hardware, there is NO WAY your CPU should be utilized 50% or higher when supposedly "idling".

Under System Monitor you should have a look and see if there's a process that is using up high amounts of your CPU. If there is, then kill that process (right-click it and choose "End Process...").

The memory might be an issue. Ubuntu is not intended as a lightweight distribution. Even then I think 512mb should be okay, but you mention it's 50% used with 50% swap used too. This might be a symptom of the runaway process I mentioned earlier, though.

If you do find the process that's using all your CPU time, let us know and we might be able to tell you how to remove or disable it for good - or tell you if it's something that can't be disabled.

---

