---
title: "Very high battery drain in 11.10"
date: 2012-03-11
forum: General Help
---

### Post by Liopleurodon on 2012-03-11
Hello,

Since a few days I have a new laptop (Alienware M17x r3); and I wanted to install the newest Ubuntu version on it.  (Was using 10.10 on my old laptop)
Anyway, my new laptop can only work for about an hour with a fully charged battery (opposed to a few times more when working in Windows 7).
I checked the battery drain rate and it's the whole time around 90W (which seems very high to me; my old laptop only had something like 25W).

I think ubuntu doesn't scale my CPU speed and thus runs on highest speed the whole time.  (This makes my laptop also quite hot in Ubuntu)

I tried setting 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force" in my GRUB config file, but with no avail.

I also installed an app called Jupiter, but it didn't do a lot either.
I have a Radeon card (which I suppose is off; as I didn't install any drivers for it), and an i7 cpu.

I hope someone can help me.
Thank you very much in advance! :)

EDIT: I just booted with a live CD of 10.10 I had, and battery discharge was just somewhere in the 30 watts.  Too bad 10.10 doesn't seem to recognize my wireless card (Bigfoot killer 1103; which is actually an Atheros AR9300), so if it's possible to somehow let that wireless card work, then I'd be happy too. :)

EDIT2: I just saw I set the dist as lubuntu in the thread description, this acutually should be Ubuntu.

---

### Post by Mark Phelps on 2012-03-12
Your thread looks familiar ... did you post this same thread elsewhere ...

Anyway, you've already taken the actions that are recommended for dealing with the known kernel bug in recent Ubuntu versions ... and apparently, they're not working.

The only other thing you could try, since there are claims that the kernel bug has been fixed in 120.04, is download and burn the 12.04 beta ISO and boot from that.  See if that addresses the problem.

---

### Post by Liopleurodon on 2012-03-12
Thank you for your answer.

No, I didn't post this thread anywhere else.
I found out one of the major reasons was Ubuntu not disabling my GPU.  I blacklisted the radeon driver, and now the discharge rate is about 45 watts, which still seems rather high, but a lot better than the 90 watts I got before.
I also installed Jupiter, but that didn't help a lot.
Is a discharge rate of 45 watts normal on an i7 17inch laptop?  Or is it too high?

---

### Post by idoitprone on 2012-03-13
add extra kernel parameters in this link
[http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1)

this should decrease your sandy bridge power usage. These kernel parameters were disable by default because of power regressions

[nvm you have a radeon card. there isnt any goof support for switchable graphics]("https://wiki.ubuntu.com/Bumblebee")

---

### Post by Liopleurodon on 2012-03-17
> **idoitprone said:**
> add extra kernel parameters in this link
[http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1)

this should decrease your sandy bridge power usage. These kernel parameters were disable by default because of power regressions

[nvm you have a radeon card. there isnt any goof support for switchable graphics]("https://wiki.ubuntu.com/Bumblebee")

Thank you very much! I'll try those out tomorrow.

---

