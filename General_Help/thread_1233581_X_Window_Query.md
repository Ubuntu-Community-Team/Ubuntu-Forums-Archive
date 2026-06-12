---
title: "X Window Query"
date: 2009-08-06
forum: General Help
---

### Post by kg84 on 2009-08-06
The attached screenie shows details for X on HTOP, a few minutes after rebooting my laptop (HP DV6). Note the % of memory used.

Prior to this reboot, the laptop had been up for about 28 hours. At this time HTOP showed X using a bit over 30% of memory.

Why does X gradually consume so much memory as time goes on? Is this related to me leaving FF and T'Bird running for al this time?

Cheers :)

---

### Post by kg84 on 2009-08-07
Boo Boo De Boop

:D

---

### Post by kg84 on 2009-08-13
Here we go - another one.

Almost two days of uptime - figure under query now 46%.

Any ideas?

:)

---

### Post by kg84 on 2009-08-15
:-\"](*,):-({|=#-o

---

### Post by P4man on 2009-08-15
Looks like a memory leak. 
[http://en.wikipedia.org/wiki/Memory_leak](http://en.wikipedia.org/wiki/Memory_leak)

Since I dont have it (nearing 20 days uptime now, no real increase in mem usage) Could it be in the video drivers? What version of ubuntu and what videodrivers are you using?

---

### Post by kg84 on 2009-08-15
> **P4man said:**
> Looks like a memory leak. 
[http://en.wikipedia.org/wiki/Memory_leak](http://en.wikipedia.org/wiki/Memory_leak)

Since I dont have it (nearing 20 days uptime now, no real increase in mem usage) Could it be in the video drivers? What version of ubuntu and what videodrivers are you using?

Hey there P4man...

9.04 here and as far as the video drivers go, just the downloadable proprietary ones which I got at the time of the distro install - ATI 8.60.40 for Radeon Mobility HD 4650 card.

Cheers

---

### Post by P4man on 2009-08-15
Im assuming your machine is updated?

An easy (non!) solution is enabling control+alt+backspace to restart X:
[http://www.ubuntugeek.com/howto-enable-ctrl-alt-backspace-in-ubuntu-jaunty.html](http://www.ubuntugeek.com/howto-enable-ctrl-alt-backspace-in-ubuntu-jaunty.html)
And use it once in a while, until a real fix comes up in the repo's.

Or you could try newer ATI drivers from their site, but Im not even sure that is causing your memory leak :s.

---

### Post by kg84 on 2009-08-15
> **P4man said:**
> Im assuming your machine is updated?

An easy (non!) solution is enabling control+alt+backspace to restart X:
[http://www.ubuntugeek.com/howto-enable-ctrl-alt-backspace-in-ubuntu-jaunty.html](http://www.ubuntugeek.com/howto-enable-ctrl-alt-backspace-in-ubuntu-jaunty.html)
And use it once in a while, until a real fix comes up in the repo's.

Or you could try newer ATI drivers from their site, but Im not even sure that is causing your memory leak :s.

Thanks mate - yep, the machine here is updated regularly and I will give the little workaround a go every now and again until this can be sorted properly.

I'll sit tight on the ATI drivers I have for the time being, while I do a little more digging around.

All the best for now :)

---

### Post by P4man on 2009-08-15
Here, you're not alone:
[https://bugs.launchpad.net/ubuntu/+bug/353800](https://bugs.launchpad.net/ubuntu/+bug/353800)

Looks like my guess might be right.

---

### Post by kg84 on 2009-08-15
> **P4man said:**
> Here, you're not alone:
[https://bugs.launchpad.net/ubuntu/+bug/353800](https://bugs.launchpad.net/ubuntu/+bug/353800)

Looks like my guess might be right.


Nice find - thanks very much.

Having a read now. :)

---

