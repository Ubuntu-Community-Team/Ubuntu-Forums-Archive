---
title: "Extream Netbook Battery Drain"
date: 2009-07-07
forum: General Help
---

### Post by TrakerJon on 2009-07-07
Using basically the same power management settings in Win XP SP3 and Ubuntu 9.04 Jaunty the battery drains twice as fast on Ubuntu. I've turned off all unnecessary services and use basically the same types of applications/programs. What's up with that? Anyone else having the same issue?

---

### Post by danwood76 on 2009-07-07
Do you use visual effects in Ubuntu?
These will drain your battery as they require quite some power.

What are you using to calculate the battery drain?
The gnome battery monitor can take a few full charges to get accurate as some ACPI/BIOS are a bit funny with the data they output.

Comparing Ubuntu 9.04 to XP is like comparing Vista to XP. Ubuntu will take more power.

The issues with ACPI and the BIOS which can be fixed with some very complicated workarounds which involve recompiling some of the BIOS code.

What netbook do you have and whats its specs?

---

### Post by TrakerJon on 2009-07-07
> **danwood76 said:**
> Do you use visual effects in Ubuntu?
These will drain your battery as they require quite some power.

What are you using to calculate the battery drain?
The gnome battery monitor can take a few full charges to get accurate as some ACPI/BIOS are a bit funny with the data they output.

Comparing Ubuntu 9.04 to XP is like comparing Vista to XP. Ubuntu will take more power.

The issues with ACPI and the BIOS which can be fixed with some very complicated workarounds which involve recompiling some of the BIOS code.

What netbook do you have and whats its specs?


Ahhhh you're right the desktop effects are a significant draw on the system...along with some other things that I could possibly do without. I'll pass on the BIOS changes for now. MSI Wind Netbook U100 1.6GHz Intel Atom w/ 2Gb SDRAM and Intel Mobile 945GME Express video. I'll be back with an update.

---

### Post by ^_Pepe_^ on 2009-07-07
Hi! 

Interested here! My Medion Akoya Mini 1210 (same as U100, guess) says 1:25h from 100% battery onwards, and 1:50 with XP.

I totally agree with the idea that 9.04 is same as Vista. I've never tried deactivate Compiz, but to be honest, I'd prefer to have a little less battery than renounce to my 3D effects.

I have also tried to "re-calibrate" Gnome indicator by draining completely the battery three times (from full charge, of course). It "gave" me 10 min more.

My question is? Is there any difference without Compiz effects? Strange. I'll try, of course. 

Regards,
^_Pepe_^

---

### Post by danwood76 on 2009-07-07
On my toshiba (a little for powerful graphics than a netbook) I got quite a bit extra time.

You should also adjust the power saving options and see if you can squeeze extra power out of there. XP can default to quite aggressive power management sometimes.

---

### Post by TrakerJon on 2009-07-07
> **danwood76 said:**
> On my toshiba (a little for powerful graphics than a netbook) I got quite a bit extra time.

You should also adjust the power saving options and see if you can squeeze extra power out of there. XP can default to quite aggressive power management sometimes.

Well, I killed off all non-essential services including Compiz and reduced the number of desktops to one...the result was about an hour more out of a nine hour rated battery. On XP SP3 I typically get about 7.5 hours life with basically all power saving options turned off with similar settings on Ubuntu 9.04 Jaunty it says I can squeeze out just over 5 hours. I wouldn't compare Vista to anything short of Win ME, they're both better left for buzzard bait. Anyway, I'm thinking Firefox might be sucking excessive juice out of the battery as well...checking out Opera now.

---

### Post by TrakerJon on 2009-07-07
Firefox squanders a lot more system resources than I expected, looking at htop I see Opera 9.64 uses about 75% less system resources than Firefox 3.0.11. I now have a new browser for use while on battery power.

**Opera for Linux [http://www.opera.com/browser/download/]("http://www.opera.com/browser/download/")**

---

### Post by Siúlóir on 2009-08-08
> **TrakerJon said:**
> Using basically the same power management settings in Win XP SP3 and Ubuntu 9.04 Jaunty the battery drains twice as fast on Ubuntu. I've turned off all unnecessary services and use basically the same types of applications/programs. What's up with that? Anyone else having the same issue?

Last week I upgraded from Intrepid to Jaunty and I discovered that under Intrepid power lasted about 2.5 hours (using Compiz and all) while under Jaunty it hardly lasts 1.5 hours! You could watch the power percentage krell tick down real fast!

So I guess that's Jaunty related!

---

### Post by raiwo on 2009-08-11
i also been wondering power usage in jaunty, i get 1h 15mins nowdays on my laptop, it's been going down on every new release: from 8.10 i got 1h 45min and from 7.10 i got 2h 15min!

 my battery is just fine:
```
Product: PA3465U
Status: Charged
Percentage charge: 100.0%
Vendor: TOSHIBA
Technology: Lithium ion
Serial number: 3658Q
Model: PA3465U
Current charge: 59.2 Wh
Design charge: 59.2 Wh
```

just every release i get less and less time out of my machine... iam using powertop to decrease power usage & i don't use any  visual effects.

is there a laptop mode in ubuntu & how to see if it's working correctly?

---

### Post by Barafu Albino Cheetah on 2009-08-11
The main energy eater is CPU and HDD too. For HDD, lower your **swappiness**. For CPU, make sure that halting CPU when idle, and lowering its speed when not needed, do work. Check for special howtos on this problems

---

