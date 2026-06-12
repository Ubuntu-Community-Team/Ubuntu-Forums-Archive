---
title: "Clock runs too slow. Big clock skew after a while."
date: 2010-11-03
forum: General Help
---

### Post by BlueLionCostas on 2010-11-03
Hello everyone,

For a while now I have been plagued by my clock running too slow.
When I boot my computer the time is perfectly ok, but after a while, about an hour, it starts getting behind on time. When I reboot it, it's fine again.
Since I leave my computer running for a large part of the day the clock skew can get quite large. Right now my clock says 21:11, while it is in fact 21:56.
I'm not entirely sure if I had this problem on Lucid, but I don't think so, because I would probably have called for help sooner.
All the clocks give the wrong time, the date command, the gnome-applet and cairo-clock. I tried this, because I was hoping, maybe I could narrow it down somehow. I really have no clue on how to find useful about a slow clock!
Also, one time when the clock was more than an hour behind it suddenly jumped forward 2 hours, being suddenly almost 1 hour ahead. It then continued running slow. This probably won't make finding the source of the problem easier though...
So, think this my motherboard, Ubuntu or something completely different? I really have no idea myself and I couldn't seem to find anyone with a similar problem.
At first, I thought it was probably my motherboard, but than realized the time was right after a reboot, so BIOS time should be running fine.

I'm running Ubuntu 10.10 64-bit.

Thanks in advance

---

### Post by bwestover on 2010-11-03
PCs in general, do not make good clocks. Especially laptops.

My wife's netbook gets off by about 10-20 minutes after a week or so. Which is pretty bad.

However, you are noticably off in less than an hour!! This is almost certainly a hardware problem.

Is this a desktop or a laptop?

I think, but am not certain, that Ubuntu syncs the clock with NTP on each reboot. Which is why your clock is correct right as you boot up.

Have a look at document here. Perhaps you could just tweak these to keep you synced a little more often.
[https://help.ubuntu.com/community/UbuntuTime](https://help.ubuntu.com/community/UbuntuTime)

---

### Post by BlueLionCostas on 2010-11-03
This is a desktop computer. The hardware is not that old, not more than three years I think. Some would consider this old maybe, but it still takes everything I throw at it (except for the clock, of course -_-')

I'll try your suggestion, as that would explain why the time is right after a reboot. This will also come in handy on my little server, which doesn't get rebooted very often. Until now, I never considered it would skew as well.

I also just realised I could test if it's a hardware problem by running a while in windows. Can't believe I hadn't thought of that, then again, I haven't used it in quite a while. :p
Will post back with the results.

Thanks

Update:
I added the following to /etc/cron.hourly/ntpdate
```

ntpdate ntp.ubuntu.com

```Afterwards I ran the command once and time was set correctly almost instantly. (I remember on windows it would take almost a minute or more! I wonder how they managed to do that.)
Anyway, this should fix my problem for now, but I would still like a more satisfying explanation, seeing as this is more of a workaround than a fix. I should probably look at my motherboard for this, shouldn't I? Can hardly believe it would be because of my CPU and can't imagine another component messing with the clock.

---

### Post by ratcheer on 2010-11-03
Install and configure ntp and it will automatically keep your clock updated, all the time.

Tim

---

### Post by dtfinch on 2010-11-03
I've seen clock drift on an old system with buggy APIC support. It would also hard-freeze after a few hours. Booting with the noapic kernel option fixed both issues.

edit: That was on an old single core celeron made around 2002. If this is a fairly new system with multiple cores, using noapic may hurt performance (not sure how noticeable), forcing all interrupts to be handled by one cpu.

---

### Post by BlueLionCostas on 2010-11-03
> **ratcheer said:**
> Install and configure ntp and it will automatically keep your clock updated, all the time.

Tim
Thank you, I hadn't read the provided page that well it seems. I thought it said ntpd was a blunt instrument, but it was referring to ntpdate, so what you suggest should indeed be better. Still sounds like a workaround to me though, not really a fix.
Also, anyone have an idea how this could so suddenly happen, because I was fine for a _long_ time. That's also why I doubt it's due to buggy APIC support. It's also a relatively new system, with a BIOS that has been updated not too long ago (Gigabyte board).

---

### Post by bwestover on 2010-11-03
Indeed, using NTP to sync up constantly is a hack... albeit one that will probably work just fine. NTP is pretty lightweight.

Still, you shouldn't be seeing skew this bad in such a short period of time.

Running windows, or some other distro for a while is a good test to see if its specific to this version of Ubuntu or not.

Since you're drifting so quickly, you might consider booting to your bios. Usually there is a screen with the clock on it. Let it sit there for an hour and see if you notice the drift.

Normally that wouldn't be recommended simply because no one wants to disable their computer like that for days at a time... but in your case, an hour or two should tell you if its a simple CMOS clock issue. If it is... change the battery. Those little coin batteries are hit and miss. I've seen one last 5+ years, and others die in 1 year.

---

### Post by BlueLionCostas on 2010-11-03
> **bwestover said:**
> Indeed, using NTP to sync up constantly is a hack... albeit one that will probably work just fine. NTP is pretty lightweight.

Still, you shouldn't be seeing skew this bad in such a short period of time.

Running windows, or some other distro for a while is a good test to see if its specific to this version of Ubuntu or not.

Since you're drifting so quickly, you might consider booting to your bios. Usually there is a screen with the clock on it. Let it sit there for an hour and see if you notice the drift.

Normally that wouldn't be recommended simply because no one wants to disable their computer like that for days at a time... but in your case, an hour or two should tell you if its a simple CMOS clock issue. If it is... change the battery. Those little coin batteries are hit and miss. I've seen one last 5+ years, and others die in 1 year.

Thanks for the reply.
I'll try both your suggestions tomorrow, I could leave it in the BIOS while I'm at the university and Windows to play some games in the morning, so it shouldn't be much of a hassle :p
I actually considered the battery, but I always assumed they were only used in case of a power outage to keep the clock running. Guess I was wrong.
Anyway, time for some sleep, will post an update tomorrow, see what I find out.

Update:
Windows doesn't seem affected at all. I checked whether it synced to a time server, but only once every few days, so maybe it's not hardware?...
I'm going to leave it on the BIOS for a while now, see what happens.

---

### Post by BlueLionCostas on 2010-11-04
BIOS is also unaffected. So it's only in Ubuntu. With ntpd, it's also running better, but still not perfect. I'm really quite surprised it's only my Ubuntu installation that's affected. Anyone have any idea's?

---

### Post by bwestover on 2010-11-04
I have no idea, no... but I think you've definitely ruled out hardware, and targeted it to Ubuntu.. at least this version.

Some good info here
[http://ubuntuforums.org/showthread.php?t=956263](http://ubuntuforums.org/showthread.php?t=956263)

They even mention how CMOS battery and NTP aren't typically the answer.. which you've proven as well.

---

### Post by binoplaza on 2011-01-11
Same problem here on a regular Desktop with an ubuntu 10.04 server installation .. Not a really practical feature for a server :(

---

