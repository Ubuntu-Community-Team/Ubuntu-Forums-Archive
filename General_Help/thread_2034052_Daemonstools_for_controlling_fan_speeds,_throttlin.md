---
title: "Daemons/tools for controlling fan speeds, throttling frequencies?"
date: 2012-07-27
forum: General Help
---

### Post by User4519 on 2012-07-27
Hello :)

I have this gaming/music making box which has been running Windows 7 for awhile now. I've used my server box with Kubuntu for my stationary work, but I want to make it just drive XBMC from now on, and use the gaming box for both the gaming/music stuff **and** Kubuntu. Already installed Kubuntu on it, which is great, it performs like crazy.

Thing is, this box - being a gamer box also - is seriously overclocked. It has a massive cooler with lots of airpipes and an insane CPU fan I salvaged from a weird Dell computer once. Without software controlling it (I use the ASUS utility for my motherboard in Windows 7), the fan isn't quite up to the job, or rather, it doesn't behave properly. It sets in too quickly (and it's really noisy when it does), but it also fails to set in massively when the CPU is under full load for more than just a short amount of time, causing the system to lock up.

So, I'm looking to find what would be a good daemon, or combo of daemons, to control my fan speeds, and also, if possible my FSB or CPU multipliers. If possible, my ATI card would also be nice to be able to control (I use ATI TrayTools in Windows for that).

Some specifics I'd like to be able to do:

* Throttle down clock and fan speeds on the ATI card (don't need all that juice except when gaming, which I won't be doing in Linux)
* Create a fan speed "pattern" based on sampling of CPU core temperatures.
* Control FSB and/or clock multipliers (i7 920) based on case temperature (e.g. today was the hottest day of the year, and not surprisingly, my overclock from March wouldn't make the cut on a day like this). E.g. if case temp <= 25C, set FSB to 195, if higher, set FSB lower.

Any good experiences with daemons or tools that'd help me achieve these goals?

Thanks in advance,
Daniel :)

---

### Post by Nixarter on 2012-07-27
Perhaps nvclock?

Read [here](http://forums.bit-tech.net/showthread.php?t=176111).

---

### Post by User4519 on 2012-07-29
Hi Nixarter, thanks for the tip :)

Though, nvclock is for Nvidia's graphics adapters, so it's not going to help me.

I'm looking into c2ctl, however, and I think it might be useful to me :)

---

### Post by User4519 on 2012-07-31
c2ctl's no good for my i7...

I can't seem to find anything useful for my rig. That's okay, though, I'd be changing BCLK pretty rarely anyway (by season).

I know have to figure out how to get my fan controllable via fancontrol, though, and it's proving difficult (new post to follow).

Thanks for input!

---

### Post by gifford on 2012-07-31
Maybe this link will help.
[http://manpages.ubuntu.com/manpages/precise/man8/fancontrol.8.html](http://manpages.ubuntu.com/manpages/precise/man8/fancontrol.8.html)

---

