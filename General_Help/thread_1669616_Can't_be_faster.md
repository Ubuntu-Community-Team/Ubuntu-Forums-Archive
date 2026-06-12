---
title: "Can't be faster?"
date: 2011-01-18
forum: General Help
---

### Post by LePresident on 2011-01-18
Hello guys!

I'd like to know whether the booting process at my laptop can be faster.  Currently, it takes 40 sec to start... is it ok or is it slow? (sorry, I'm a noob :P)

These are my specs:

Acer Aspire 5580
Ubuntu 10.10
Gnome 2.32.0
Kernel: both, 2.6.35-22 and 2.6.35-24
CPU: Intel core2  T5500@1.66 GHz
RAM: 2 GB

Thanks in advance!

---

### Post by LePresident on 2011-01-18
C'mon! I know you guys are smart enough to give me an answer! XD

---

### Post by mikewhatever on 2011-01-18
I think 40 seconds is ok.;)
If suspending to RAM/disk works for you, use those, they should be faster.

---

### Post by Quackers on 2011-01-18
40 seconds is a little bit faster than mine :-) That's plenty! I take it you don't remember XP or Vista then :-)

---

### Post by sammiev on 2011-01-18
Usually mine is about 17 seconds. After an update it can take a little longer. Seen folks here post longer wait periods than you. GL :)

---

### Post by efflandt on 2011-01-18
It depends what speed your hard drive is.  I did not realize that the 4200 RPM hard drive in my laptop was as slow as it was (as slow as fastest USB 2.0) until I tested it with sudo hdparm -t before using the laptop to install Maverick to an SSD (solid state drive).  The SSD was 4 times faster (limited by SATA1), and another 2 times faster when moved to my SATA2 desktop.

While SSD's are expensive, if you do have a slower drive, you may benefit from a faster drive, 7200 RPM vs. 5400 RPM or 4200 RPM.  But it depends what you are used to and if you have the money.  I booted Ubuntu on my new PC from a WD Passport on USB for awhile before installing it to my internal drive, which was not much slower than my old desktop or laptop, and was quick enough after booting with things cached in RAM.

---

