---
title: "Ubuntu 9.10 awfully slow"
date: 2009-12-25
forum: General Help
---

### Post by raphaelmsx on 2009-12-25
Hi people,

I have this HP Laptop: Turion 1.9GHz dual-core, 2GB RAM, NVIDIA 7150M.

Ubuntu runs awfully slow, anything that I click it takes some delay to open, any window or new tab (like in nautilus) takes a lot of time to open. In the same machine, running Windows XP, everything runs A LOT faster, when I click something it's almost real-time.

I also have here a very old custom-made PC with a lot lower specs than the laptop, Pentium III 800MHz 512MB RAM, and Windows XP on this machine runs faster then Ubuntu on the Turion 1.9GHz dual-core laptop, and running Ubuntu on the Pentium III is even sluggish then the laptop.

I am not blaming Linux, I prefer Linux than XP, I found that the Ubuntu is the best distribution, etc... but, in every machine that I saw that dual-boots Linux with Windows XP, the later is way faster in responsiveness...

I really just want to understand this, I thought Linux would run A LOT faster than Windows XP, it's advertised everywhere that it's lightweight, etc etc...

I don't care about "boot" and "shutdown" times, my computer is always on, this is useless to me....

I am writing this, because I just installed Mame, and it plays slow, choppy, etc... even on early 80's games, like Galaga... and I remember playing Mame years ago on a very modest system (with Windows XP) and it run just fine.

Would someone enlighten me?

Thank you.

---

### Post by tom.swartz07 on 2009-12-25
perhaps your processor is maxing out on some runaway application?

open a terminal and paste the results of the command
```
top
```

If my suspicions are correct, you have one application that is running your processor high, and it should be right there at the top of that list.

Just hit "q" to leave the output of that when youre done then!

---

### Post by raphaelmsx on 2009-12-25
Just firefox (as I am writing this now) with 10% cpu time...

But I am also talking about FRESH installation, and freshly booted...

---

### Post by MaxIBoy on 2009-12-25
On a freshly-installed system, graphics drivers are the #1 cause of poor performance, especially with video playback. Try installing the proprietary Linux drivers from [nVidia's website]("http://www.nvidia.com/Download/index.aspx?lang=en-us").


Also, XP is faster than a stock Ubuntu desktop, because it's an 8-year-old OS which is far less sophisticated. There are a few customizations (installing LXDE instead of GNOME, disabling unused services, etc.) which can make your Ubuntu system quite a bit faster, especially on that Pentium III, if you're willing to go for a more simplistic desktop.

---

### Post by keypox on 2009-12-25
I feel that way sometimes, not as extreme as you describe though. But linux should be lighting fast.  It does use less ram, than vista/7.  About the same as XP.  but it uses so much more cpu than all windows. 

xorg always doing something.

---

### Post by raphaelmsx on 2009-12-25
I referred to the Pentium III just for comparison, my main system is the laptop which is a Turion dual-core 1.9GHz with 2GB ram, and already with the NVIDIA proprietary drivers installed, and made no difference, just eye-candy stuff, which I disabled to test, and did not speed up anything...

So, what do I need to run ubuntu satisfactory?? I thought that with this laptop that I bought two years ago was more than enough... 

Thank you.

> **MaxIBoy said:**
> On a freshly-installed system, graphics drivers are the #1 cause of poor performance, especially with video playback. Try installing the proprietary Linux drivers from [nVidia's website]("http://www.nvidia.com/Download/index.aspx?lang=en-us").


Also, XP is faster than a stock Ubuntu desktop, because it's an 8-year-old OS which is far less sophisticated. There are a few customizations (installing LXDE instead of GNOME, disabling unused services, etc.) which can make your Ubuntu system quite a bit faster, especially on that Pentium III, if you're willing to go for a more simplistic desktop.

---

### Post by MaxIBoy on 2009-12-25
I'm just saying, when video performance is choppy, the main thing to try is installing the proprietary drivers. 

Try installing LXDE and see you get any speed boost out of that. It's a more minimalist desktop, but it's a lot lighter, see screenshots:
[http://lxde.org/image/tid/1](http://lxde.org/image/tid/1)
LXpanel can support multiple panels like GNOME does, though none of the screenshots show it that way.

---

### Post by raphaelmsx on 2009-12-25
The video performance is choppy in some games and very choppy in Mame, not in Gnome... it's kinda difficult to explain here... using gnome, firefox, nautilus, etc.. it just doesn't feel fast, it's not related to video performance, I think post #5 could explain better than me...

I am talking about the usability in general of the system.

I can't believe that with a 2GHz dual-core CPUs, 2GB RAM, 7200RPM drives, etc etc... a linux distro like ubuntu can't run at the speed of the light...

I use computers for about 25 years already, and I'm yet to see something as fast as my Amiga 3000 with a 68030 16MHz CPU, 8MB RAM, 80MB scsi drive... or my 486 with MS-DOS... Of course I am not talking about doing raw speed comparison of compiling a program, rendering something in lightwave (or any open-source equivalent for that matter), or 3D FPS games, of course anything now will beat old systems, but talking about responsiveness, everything is so bloated these days... see, I just made some typos, and had to hit the backspace a lot of times, and it take seconds to delete sometimes, or if I type very fast (as I do), sometimes it delays for 3 or 4 seconds before it displays the rest of the text.

Either I am being so nostalgic, or linux has gone into the bloat as well...

Thank you.

> **MaxIBoy said:**
> I'm just saying, when video performance is choppy, the main thing to try is installing the proprietary drivers. 

Try installing LXDE and see you get any speed boost out of that. It's a more minimalist desktop, but it's a lot lighter, see screenshots:
[http://lxde.org/image/tid/1](http://lxde.org/image/tid/1)
LXpanel can support multiple panels like GNOME does, though none of the screenshots show it that way.

---

### Post by MaxIBoy on 2009-12-25
> **raphaelmsx said:**
> The video performance is choppy in some games and very choppy in Mame, not in Gnome... it's kinda difficult to explain here... using gnome, firefox, nautilus, etc.. it just doesn't feel fast, it's not related to video performance, I think post #5 could explain better than me...
If video file playback and games aren't running fast, like I say you should try the proprietary drivers. At least with ATI cards, 2D performance with the stock drivers is very poor (you can actually watch as the pixels are filled out.) Although this is improving with time and it might be different with nVidia...


Without some more detailed info on your system and the specific performance problems you have (and I understand if you yourself aren't sure,) there isn't much I can suggest. However, you can try playing with alternate kernels. 


For one, you can try the realtime low-latency kernel:
```
sudo apt-get install linux-rt linux-headers-rt
```This is mainly intended for realtime audio and video work, where short stops and delays can mess up a recording session, but it can also improve desktop performance. It works by making the kernel preemptible and increasing how often it switches between processes, making the system feel more responsive and zippy.


Another one to try is a kernel with [BFS]("http://ck.kolivas.org/patches/bfs/sched-BFS.txt") and [BFQ]("http://kerneltrap.org/taxonomy/term/1231") support:[ https://launchpad.net/~darxus/+archive/bfsbfq]("https://launchpad.net/%7Edarxus/+archive/bfsbfq") 
BFS is a process scheduler optimized for home PCs with 16 or fewer CPUs, instead of the standard CFS, which is geared toward 1024 CPUs or more with relatively poor performance on home PCs. BFQ is an input/output scheduler with similar goals. That link gives you a kernel precompiled with both modifications. It's a [PPA]("https://help.launchpad.net/Packaging/PPA/InstallingSoftware"). You have to do a bit of initial work to install software from it, but afterward you get automatic updates from it, because you have added the repository it provides.


If you feel really adventurous you can compile your own kernel as well and make some system-specific optimizations, but tread carefully, be sure you know about the details of your computer, and be sure you have plenty of time on your hands:
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

---

