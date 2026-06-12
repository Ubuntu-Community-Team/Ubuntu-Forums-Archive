---
title: "Log-in to stripped down ubuntu, save battery life"
date: 2010-11-03
forum: General Help
---

### Post by oldmankit on 2010-11-03
I'm going to be doing a lot of writing from a cafe that doesn't have power sockets, and want to conserve my laptop battery life as much as possible.

The only program I need to use is lyx.  It's a shame it's lyx and not latex, I know, so I will need a graphical window manager.

I'm going to install a lightweight window manager like fluxbox for when I'm in the cafe.  But I figure there must be a way to strip the system down even more.  I found some useful advice [here]("http://lifehacker.com/333798/slim-down-and-speed-up-linux").  I would like to disable all unnecessary processes but only for when I log-in to fluxbox.  I don't want my usual system operation affected.

The tool they recommended was sysv-rc-conf.

Might there be a simple way to make changes like that but only for login to fluxbox?

---

### Post by s3MA00RRNY on 2010-11-03
You can only cut back so much before it becomes inconvenient. Here's what I would do:


[LIST]
[*]Run powertop (apt-get install powertop). It will tell you what programs are waking up the CPU. you may be surprised at the results (Mono tends to be a huge offender)
[*]Get Linux PHC. There's a repository for a special Ubuntu kernel that's required to compile it. Basically it lets you tune down the voltage on your CPU at the possible expense of stability. Use cpuburn's burnMMX to load your CPU while you test this (one burnMMX per CPU). Tune back slowly until the computer crashes. One above that value is usually the stable setting for that speed. Also remember each CPU usually has separate settings. This is completely safe to do, as long as you don't save the unstable settings in a config file.
[*]If you have an NVIDIA BIOS, use NiBiTor to undervolt your GPU. BE CAREFUL WHEN UNDERVOLTING YOUR GPU THIS WAY! Tune the high performance modes first, since they only kick in on load. If you tune the low performance modes too much, you'll be screwed. Run FurMark to load the GPU while you test this. This one is more awkward to do because you have to keep rebooting to test the results.
[/LIST]

Hope this helps, and I realize the last one is super risky, so don't do it unless you feel daring.

Edit: If you need more details, let me know.

---

### Post by oldmankit on 2010-11-04
> **pcdude2143 said:**
> You can only cut back so much before it becomes inconvenient. Here's what I would do:


[LIST]
[*]Run powertop (apt-get install powertop). It will tell you what programs are waking up the CPU. you may be surprised at the results (Mono tends to be a huge offender)
[*]Get Linux PHC. There's a repository for a special Ubuntu kernel that's required to compile it. Basically it lets you tune down the voltage on your CPU at the possible expense of stability. Use cpuburn's burnMMX to load your CPU while you test this (one burnMMX per CPU). Tune back slowly until the computer crashes. One above that value is usually the stable setting for that speed. Also remember each CPU usually has separate settings. This is completely safe to do, as long as you don't save the unstable settings in a config file.
[*]If you have an NVIDIA BIOS, use NiBiTor to undervolt your GPU. BE CAREFUL WHEN UNDERVOLTING YOUR GPU THIS WAY! Tune the high performance modes first, since they only kick in on load. If you tune the low performance modes too much, you'll be screwed. Run FurMark to load the GPU while you test this. This one is more awkward to do because you have to keep rebooting to test the results.
[/LIST]

Hope this helps, and I realize the last one is super risky, so don't do it unless you feel daring.

Edit: If you need more details, let me know.

Thanks for that wealth of information, all of which was completely unknown to me.

If I am more or less continuously typing in lyx, will my CPU will be woken up all the time?  If so, is there any point going through powertop and getting rid of things that are unnecessarily waking it up?  Is it only useful for the periods when I'm not doing anything?

I don't want to do anything risky so won't try the third idea.  But the second one looks interesting.

---

### Post by P4man on 2010-11-05
Its very doubtful the undervolting will work on a laptop. Its even more doubtful it will help a great deal (modern cpu's already scale their speed and voltages automatically and the voltages are determined per individual cpu. You will have very little leeway lowering these settings and it will be pretty tough to accomplish).

A lightweight DE wont do miracles either. Especially if it means forgoing some convenient tools that do minimise battery drain.

Anyway, much depends on the laptop you have, but at the very least you will want to make sure CPU scaling is working properly. If you still have gnome, just add CPU frequency scaling monitor to the panel. See if it scales up/down. Dont think locking the cpu speed at lowest will definately save battery life over the default ondemand governor. Its actually more efficient to have your cpu scale to full speed for a very brief time to finish some task, and allow it go to sleep mode again faster than having it run for longer time loaded at a lower clock speed.

Powertop is an excellent suggestion. Run it from the terminal (it needs sudo) and it will propose a lot of tweaks to lower battery consumption. You can activate those tweaks from within powertop)

LCD is often the biggest power draw. Reduce brightness. Turn off wifi and bluetooth. Consider using a persistent live USB stick to boot from, and disable the harddrive in the bios (or physically remove it if need be). Install proprietary videodrivers if you have an ATI or nVidia videocard. These provide far better power management than the OSS drivers.

---

### Post by oldmankit on 2010-11-08
It's great to have various opinions to work with, thanks.

I've put the frequency scaling monitor and it shows my two processors scaling between 800Mhz (44%) and 1.8GHz (100%).  There only seem to be two steps.

I'm aware of how much power an LCD uses. Fortunately I can view lyx nicely even in bright sunlight on the lowest setting.  Running like that I got about 3.5 hours out of the battery the other day, not bad.

Regarding powertop, as I asked before, with lyx I am almost continuously typing or moving paragraphs around.  I don't give it much of a chance to sleep.  Are the improvements due to powertop only useful when I'm not actually typing or doing something with the mouse, giving my computer a chance to rest?

I have noticed that fluxbox doesn't have much in the way of power options, so maybe I will give it a miss.

I will probably not try undervolting since it seems quite difficult and potentially not helpful, unless there are any more comments on that?

Running Ubuntu purely on a flash drive sounds like a good idea.  I've done that before but didn't realise there were significant power-saving implications.  I suppose a hard drive must take more power than a little solid-state flash drive.

I really appreciate the help.

---

### Post by P4man on 2010-11-09
> **oldmankit said:**
> 
Regarding powertop, as I asked before, with lyx I am almost continuously typing or moving paragraphs around.  I don't give it much of a chance to sleep.

I dont mean sleep as in suspend, but the cpu will go to low power state and remain there >95% of the time (check powertop for the exact value).

Typing isnt exactly cpu intensive. From a CPU perspective, the time between two keystrokes is an eternity no matter how fast you type. Keep in mind 800 MHz is 800 million clock cycles per second. To process your keystrokes and put it on screen or even spellcheck what you type it needs maybe a few hundred or thousand cycles. So it will wake up, but not all that often ;)

> 
  Are the improvements due to powertop only useful when I'm not actually typing or doing something with the mouse, giving my computer a chance to rest?

See above. No matter how hard you hammer the keyboard or mouse, its barely going to affect your computers "sleep pattern" :).

> 
I will probably not try undervolting since it seems quite difficult and potentially not helpful, unless there are any more comments on that?


I highly doubt it will work on a laptop, and it will be a lot of work trying, thats why I wouldnt bother.

> 
Running Ubuntu purely on a flash drive sounds like a good idea.  I've done that before but didn't realise there were significant power-saving implications.  I suppose a hard drive must take more power than a little solid-state flash drive.

Yes. Powerdraw of a hdd isnt massive but its substantial nonetheless. A few watt when in use. And ubuntu doesnt seem very good at putting the hdd to sleep. A live CD has the added advantage of mounting most of the filesystem in RAM, which should reduce IO no matter if its USB stick or hdd. DOnt expect quantum leaps, but it will help.

---

### Post by oldmankit on 2010-11-12
> **P4man said:**
> Typing isnt exactly cpu intensive. From a CPU perspective, the time between two keystrokes is an eternity no matter how fast you type. 
Thanks for clarifying that one!

I've dug into powertop a bit and my computer seems to function OK.  The biggest cause of wakeups is "[kernel scheduler] Load balancing tick", but this is a known bug with the kernel.  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/524281](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/524281)

I actually already had a persistent installation of 9.10 on a flash drive which uses an older kernel version and doesn't have this problem.  Running this I can maintain about >95% time in sleep with 20ms duration, which the powertop website said was good.

The only problem is that when running powertop from a flash drive, it keeps saying that my USB device is active 100% of the time and suggests something to 'fix' it, which of course doesn't do anything. I can't get at its other power saving suggestions because it's focused on this USB device.

The fact is that most of the interrupts are from my mouse and keyboard (or from the kernel load balancing tick when using 10.10), so I won't spend too long trying to reduce the other issues, which are relatively small.

> Yes. Powerdraw of a hdd isnt massive but its substantial nonetheless. A few watt when in use. And ubuntu doesnt seem very good at putting the hdd to sleep. A live CD has the added advantage of mounting most of the filesystem in RAM, which should reduce IO no matter if its USB stick or hdd. DOnt expect quantum leaps, but it will help.I would love to disable the hard drive but can't find a way to do it in my bios (Phoenix trusted core). I did a quick search and I don't think there's any way to do it from Ubuntu either, so I might be stuck there.  I don't want to open up my laptop every time and pull it out physically!

---

### Post by P4man on 2010-11-13
to make the disk spin down, make sure you dont mount any of the partitions, including swap. By default a live session will mount and use any swap it finds. Then open gconf-editor and browse to

/apps/gnome-power-manager/disks/

configure it so it puts the disk asleep.

---

### Post by oldmankit on 2010-11-16
> **P4man said:**
> to make the disk spin down, make sure you dont mount any of the partitions, including swap. By default a live session will mount and use any swap it finds. Then open gconf-editor and browse to

/apps/gnome-power-manager/disks/

configure it so it puts the disk asleep.

Thanks!

---

