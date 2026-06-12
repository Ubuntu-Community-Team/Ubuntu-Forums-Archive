---
title: "Ubuntu 11.04 monitor config not saving (3 monitors)"
date: 2011-05-15
forum: General Help
---

### Post by rockstar2577 on 2011-05-15
I am a fairly new Linux user.  But thanks to the awesome folks at this forum, i was able to install Catalyst 11.5 on my system :)  But here is the problems I am having.


I have a triple monitor setup, that works fine in Windows (either using Eyefinity, or just extended desktops)  I HAVE been able to get all three monitors working as extended desktops in Ubuntu, but when I set it up, I usually get "Not enough allocated memory to enable this monitor".....OR by some weirdness, all three will work.  but when I reboot or shut down and then come back, only two monitors are working, and I get a message saying that 'the configuration couldnt be saved, or there was a white line in line 1' or something to that effect.

Could someone give me a hand with this? Either get extended desktop working, or Eyefinity.

Thank you :)

System info: 
Mother board Asus M4a78T-e
6 gig RAM
AMD Phenom II x4 965 Black
ATI Radeon HD 5770 Graphics CArd

---

### Post by rockstar2577 on 2011-05-18
Bump.  Anyone anyone?  Bueller?  Bueller?

---

### Post by DouglasAWh on 2011-05-19
I'm on Maverick, but I'd like to know if this is easier on Natty.  I'm running two

"VGA compatible controller: ATI Technologies Inc RV610 [Radeon HD 2400 XT]" according to lspci

I can obviously start a new thread, but I figured this was as good as a bump.

---

### Post by traffas on 2012-05-14
It's still a bug in 12.04. Any ideas or solutions? Re-running the Catalyst control panel on each reboot is arduous.

---

### Post by roelforg on 2012-05-14
The problem is this:
The dash links don't use sudo (not even the administrative one).
Open a terminal and type:
```

sudo amdcccle

```
This one should save (it does for me).

---

