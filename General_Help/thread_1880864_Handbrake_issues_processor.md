---
title: "Handbrake issues: processor"
date: 2011-11-14
forum: General Help
---

### Post by bfmetcalf on 2011-11-14
I am using handbrake to resize/re-format some movies for my new transformer tablet.  When I start the process it almost immediatly pegs my processor at 100%.  I will put my specs below.  Any ideas on this, I would prefer it to take less than 8 hours to encode a movie...

I have an AMD Turin X2 processor dual core I believe it is 2.7Ghz
4gig ram
Ubuntu 10.10

If you need more info let me know, also how to find it, still don't know my way around like I should

---

### Post by bfmetcalf on 2011-11-14
After a little more digging it looks like handbrake is keeping my cpu speeds down at 525Mhz.  When it is not running I can get the CPU back up to 2.1Ghz but as soon as I run handbrake it slows back down to 525Mhz.  Any ideas how to stop this from happening?

---

### Post by JohnAStebbins on 2011-11-14
> **bfmetcalf said:**
> After a little more digging it looks like handbrake is keeping my cpu speeds down at 525Mhz.  When it is not running I can get the CPU back up to 2.1Ghz but as soon as I run handbrake it slows back down to 525Mhz.  Any ideas how to stop this from happening?

Check your CPU temperatures.  This sounds like thermal throttling to me.  HandBrake is very CPU intensive and will put it under more stress than most applications.

---

### Post by bfmetcalf on 2011-11-14
I think I got this figured out.  I had to start up in kernal 2.6.20 for some reason as 2.6.35 wouldn't start for some reason and put a fan blowing directly on the laptop.  It seems to be working fine right now.  Not sure if it was the fan or the kernal version, but it is working, still using 100% of the cpu but at lease it has 2X2.1Ghz instead of 2X.53Ghz.

---

