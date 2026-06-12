---
title: "Segmentation Fault for everything!"
date: 2009-10-14
forum: General Help
---

### Post by Dex Luther on 2009-10-14
No matter how many times I install Ubuntu or try to solve this problem, it just doesn't go away. There's a 75% change that anything that is running or trying to start in Ubuntu will suddenly stop. 

The most common victim of this is Firefox. I start Firefox, Starting Firefox appear, then after 2-4 seconds it disappears as it should. Only Firefox never opened.

I try to watch a show. I have used Mplayer, SMplayer and VLC. Randomly either will suddenly disappear right in the middle of playback. I used Mplayer first. Thinking it was maybe a codec or version issue I installed the latest version of VLC. It crashes the same way, so I installed SMplayer. Still no help.

To try and figure out what exactly was the problem I started using the terminal to start my media playing apps. I started with VLC. Sometimes I'm able to play a whole file with no problem. When I try to play that file again or play a new one, *poof* it's gone. All that I get in the terminal is a annoyingly unhelpful 'segmentation fault' message.  

I have this problem with absolutely EVERYTHING run on Ubuntu. Firefox, Nautilus, Vuse, media players. I think sometimes even the core files get 'segmentation fault'-ed and I crash out to the log-in screen. 

In an effort to try and solve this problem on my own (or at least figure out WHY this was happening) I've exhausted many searches. Unfortunately, unlike Windows, there's about a million different versions of Ubuntu/Linux. Finding relevant information that could actually apply to me is next to impossible and confusing. 

So I'm looking for help solving these segmentation fault problems. There's no tell-tale error messages I can post other than the aforementioned 'segmentation fault' error, but I'll gladly try and post anything others my find helpful in resolving this.  

Thanks in advance,
Dex

---

### Post by khelben1979 on 2009-10-14
Have you ever considered that you might have a hardware problem?

---

### Post by Dex Luther on 2009-10-14
> **khelben1979 said:**
> Have you ever considered that you might have a hardware problem?

Hmm. I had thought of that, but I have no idea what the problem could be. I've tested the memory with memtest and the hard drive with Hdata (I used Hirens, but don't remember exactly what the test was called). Everything checks out fine. I have no idea how I would go about testing things like the CPU or Power Supply; if that's even possible.

---

### Post by khelben1979 on 2009-10-15
You can check if your temperature on the CPU is too hot if you have a tool which can report back to you how it looks like. If you're uncertain about the temperature, I'm sure there's documentation on it, just let us know your hardware configuration.

Other than that, it could be something else as well, but we'll try and focus on the problem step by step.

---

### Post by Dex Luther on 2009-10-15
My hardware is as follows:

AMD Athalon XP 3000+
2 gigs ram
Via KM266 motherboard
1 Seagate Baracuda 7200.10 HDD (500gigs)
1 Maxtor DiamondMax Plus 9 HDD (120gigs) <--- Ubuntu is installed on a 20gig partition on this harddrive
Nvidia 6800 Geoforce (has Asus stamped on it and it has 512mb of ram versus the normal 256 the 6800's usually have)

That's about it. I think my CPU is too old to have any kind of heat sensor on it. If there is one I don't know/have never been able to use it. If there's anything else that could help out my cause please let me know.

Thanks again,
-Dex

---

### Post by khelben1979 on 2009-10-15
There's a chance that your problem will be solved if you will change to a better cooler on that cpu.

Other than that, you can always try with using different Linux kernels. Some kernels don't like certain hardware. Search for them using [Synaptic Package Manager]("http://en.wikipedia.org/wiki/Synaptic_package_manager") and you'll see what Ubuntu has.

---

### Post by Dex Luther on 2009-10-16
> **khelben1979 said:**
> There's a chance that your problem will be solved if you will change to a better cooler on that cpu.

Other than that, you can always try with using different Linux kernels. Some kernels don't like certain hardware. Search for them using [Synaptic Package Manager]("http://en.wikipedia.org/wiki/Synaptic_package_manager") and you'll see what Ubuntu has.

Is there anyway to tell which would be better with my current setup?

---

### Post by DeMus on 2009-10-16
> **khelben1979 said:**
> There's a chance that your problem will be solved if you will change to a better cooler on that cpu.

Other than that, you can always try with using different Linux kernels. Some kernels don't like certain hardware. Search for them using [Synaptic Package Manager]("http://en.wikipedia.org/wiki/Synaptic_package_manager") and you'll see what Ubuntu has.

Khelben1979: Why you jump to the conclusion it is a temperature matter? The OP did not give any temp yet, so how do you know it is a too high temperature?

Dex Luther: Which OS do you run, and more importantly which kernel version?
Please open a terminal and type: 
```
dmesg | grep Linux
```
and
```
uname -r
```
and copy paste the answers here.

---

### Post by khelben1979 on 2009-10-16
> **DeMus said:**
> Khelben1979: Why you jump to the conclusion it is a temperature matter? The OP did not give any temp yet, so how do you know it is a too high temperature?

Personal experience.

---

### Post by Crafty Kisses on 2009-10-16
Test your RAM.

---

### Post by P4man on 2009-10-16
sure sounds like a hardware problem to me, and I concur with the above poster that it may well be a overheating problem if its not a RAM or HDD problem. Athlon XPs didn't have any thermal protection. Now many motherboards did have cpu sensors in the cpu socket, so you might be able to get a temperature reading in the BIOS or by installing lm-sensors.

If not, just open the case, and check your cpu fan. See if its spinning and not entirely clogged with dust.

edit:
If its not the cpu overheating, it could be a powersupply or motherboard problem. Can you check your voltages in the BIOS? And if you have the case open, check for bad caps:

[http://www.badcaps.net/images/caps/kt7/kt4.html](http://www.badcaps.net/images/caps/kt7/kt4.html)
[http://www.badcaps.net](http://www.badcaps.net)

Motherboards of that age frequently suffered from bad caps (Ive personally had 2 like that).

---

### Post by Dex Luther on 2009-10-17
> **DeMus said:**
> Khelben1979: 
Dex Luther: Which OS do you run, and more importantly which kernel version?
Please open a terminal and type: 
```
dmesg | grep Linux
```and
```
uname -r
```and copy paste the answers here.

```
[    0.000000] Linux version 2.6.28-15-generic (buildd@rothera) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009 (Ubuntu 2.6.28-15.52-generic)
[    0.004061] SELinux:  Disabled at boot.
[    9.766837] Linux agpgart interface v0.103

``````
2.6.28-15-generic
```And a copy of Windows XP Home Edition on a seperate partition.

> **Codename said:**
> Test your RAM.

I've already tested my RAM many times.

> **P4man said:**
> sure sounds like a hardware problem to me, and I concur with the above poster that it may well be a overheating problem if its not a RAM or HDD problem. Athlon XPs didn't have any thermal protection. Now many motherboards did have cpu sensors in the cpu socket, so you might be able to get a temperature reading in the BIOS or by installing lm-sensors.

If not, just open the case, and check your cpu fan. See if its spinning and not entirely clogged with dust.

edit:
If its not the cpu overheating, it could be a powersupply or motherboard problem. Can you check your voltages in the BIOS? And if you have the case open, check for bad caps

There was a little dust on the fan. I took it off cleaned it up, re-oiled the fan, and now it seems to spin a little better. I don't let my computer get too dusty, but that re-oiling might have been a little over due. I don't know if that was the problem or if it was just compounding the real problem. I got a friend to pick me up some thermal paste (I got the Arctic Silver stuff). Maybe that'll solve the problem. Hopefully before any damage was done.

---

### Post by P4man on 2009-10-17
> **Dex Luther said:**
> 
There was a little dust on the fan. I took it off cleaned it up, re-oiled the fan, and now it seems to spin a little better. I don't let my computer get too dusty, but that re-oiling might have been a little over due. I don't know if that was the problem  

By the sound of it, id say its not likely. Those heatsinks do have enough margin to withstand a bit of dust or a fan running slightly slower. Especially since you have problems without actually stressing (ie heating) your cpu.

Did you check the bios for temperatures and (mostly) voltages?  Low or unstable voltages in the bios would point to a bad motherboard or a bad powersupply.

---

### Post by Dex Luther on 2009-10-22
The only thing in the BIOS for voltage/temp was this:

CPU Host/AGP/PCI Clock: 166/66/33mhz

---

### Post by P4man on 2009-10-22
are you having problems in XP as well?
edit oh and are you sure the drive is not full? Run 
```

df -h
```

---

### Post by Dex Luther on 2009-10-22
> **P4man said:**
> are you having problems in XP as well?
edit oh and are you sure the drive is not full? Run 
```

df -h
```

Yes, drives are not full. I have a 20gb partition with nothing but Ubuntu on it.

I've been having problems with Windows, which is why I started using Linux. In Xp I'll randomly get IRQL_NOT_LESS_OR_EQUAL BSODs.

The last couple days it's been less noisy around here, and I've been hearing a faint clicking noise coming from my computer. This happens in Ubuntu and XP. Sounds like the PC speaker decides to make a clicking sound for some reason. I don't know if it's part of the problem, but it's strange.

EDIT: Not sure if it's the PC speaker or something else. It's one of those things you hear when you're not expecting it Get closer to try and figure out where it's coming from, and what ever was making the noise stops.

---

