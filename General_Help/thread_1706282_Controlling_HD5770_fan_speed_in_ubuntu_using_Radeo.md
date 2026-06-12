---
title: "Controlling HD5770 fan speed in ubuntu using Radeon OS Driver."
date: 2011-03-13
forum: General Help
---

### Post by skaneda on 2011-03-13
Running 10.04 LTS, wondering if there was a way to control fan speed using the open source radeon driver with a HD5770, it's currently far too loud  even when not really being in use.

---

### Post by turtle153 on 2011-03-13
[http://forums.fedoraforum.org/showthread.php?p=1386622](http://forums.fedoraforum.org/showthread.php?p=1386622)

---

### Post by olof_ on 2011-05-03
I am experiencing the opposite issue, my fan is at a too low setting. The link is to control the fan speed using fglrx, and not the free radeon drivers.

---

### Post by Mark Phelps on 2011-05-03
Could be that your card GPU has the ability to throttle back when not requiring 3D acceleration -- but such features are only provided in the restricted drivers.

If it's LOUD, that's because the GPU is running HOT. If you forcibly turn down the fan speed, you will burn out your video card. Is that really what you want to do?

As to it NOT being in use -- as long as there is a display on the screen, it IS in use.

---

### Post by olze on 2012-03-11
> If it's LOUD, that's because the GPU is running HOT. If you forcibly  turn down the fan speed, you will burn out your video card. Is that  really what you want to do?
Thats simply wrong. I am facing the same problem on Fedora F17 (yea i know that this is alpha, and as i'm alpha tester i know that, so plz dont flame on this, kthx). The radeon HD series is designed to fullpower its FANs when the sensors are not detected in a correct way. It doesnt care if its just on startup or on a running OS. Thats also the reason why the HD Series fullpowers its FANs on startup. And no, thats NOT a cleaning function! It is simply that way AMD tries to prevent damages! As the system does not know is it running on 30°C or on 100°C, so it expects the worst and uses the max. value as default.

Anyway. Does someone know a way how to handle the free radeon driver regarding that FAN stuff?

And btw. sorry for bringing up such old thread, but as i'm facing a nearby problem, i commented on it.

---

### Post by Mark Phelps on 2012-03-11
> **olze said:**
> Thats simply wrong. 
NO -- it's not!  

Even you said:
> It is simply that way AMD tries to prevent damages! As the system does not know is it running on 30°C or on 100°C, so it expects the worst and uses the max. value as default.
Right -- and if you have no way to monitor the GPU temps, but do have a way to Force the fan to run slower, then you're risking damage to the GPU if the fan then does not speed up when the GPU gets warmer.

> Anyway. Does someone know a way how to handle the free radeon driver regarding that FAN stuff?
No -- the Radeon driver doesn't do fan management.

---

### Post by olze on 2012-03-12
Who needs any fan control when working on a regular desktop? If i would be that paranoid, than i even wont turn on any pc, because it could overheat in any way.

I would not call it "force", i would call it set to a lower profile. Btw you _can_ control the fan - take a look into /sys/ and search for fb0. 

I questioned wrong. I'm no native english speaker so maybe sometimes i say a but mean b. I did not mean "how to tell the radeon driver to handle fan management" i meant "how do I manage the fan control".
I found a way:
[http://l33tbox.de/index.php?/archives/10-Radeon-HD-5770-fancontrol-without-fglrx-installed-on-Fedora-17.html](http://l33tbox.de/index.php?/archives/10-Radeon-HD-5770-fancontrol-without-fglrx-installed-on-Fedora-17.html)

I hope that link is ok. Otherwise plz remove.

edit: and its working fine (and silent). Until now my radeon did not burn down.

---

### Post by lumingzou on 2012-03-15
I also have the same problem, but I donot think you could resolve the problem by controlling the fan speed, because the fan got crazy because of your computer was overheated.

---

### Post by Mark Phelps on 2012-03-15
> **olze said:**
>  Until now my radeon did not burn down.

You're right -- but that's because you're setting a POWER profile; you're not just forcing the fan to run slower.  You're slowing down the GPU -- which will generate less heat, and cause the fan to run slower (and quieter).

And, in deference to you -- I stand corrected.  I did not know that you could do power management on AMD boards without using the fglrx drivers.

But then, I don't mess around with Fedora, either.

Nice find!

---

### Post by olze on 2012-03-17
> I also have the same problem, but I donot think you could resolve the  problem by controlling the fan speed, because the fan got crazy because  of your computer was overheated. 	
once again. this is _wrong_!
You can get your GPU temps. from the /sys labirynth. It was displaying about 30°C - thats not too hot!

When you start(!) the PC even when it was idle for about 2h and even if the temperature from outside has -30°C the _same_ will happen with the fan. 

@Mark
Yea thats what i meant. As mentioned before, i'm no native english speaker. Thats why i said "setting a lower profile" and not forcing the fan.
Btw. its not an AMD board, it is a asrock p55 pro.

---

