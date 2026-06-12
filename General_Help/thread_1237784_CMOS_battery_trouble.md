---
title: "CMOS battery trouble"
date: 2009-08-11
forum: General Help
---

### Post by Jaunty Jackalope on 2009-08-11
I own the following notebook:
Compaq Presario 711CL (manufactured c. 2002): 
1.0 GHz AMD ® Mobile Duron™ Processor, 64KB Cache | 14.1" TFT XGA Display | 384MB 133MHz RAM | 18.0 GB Hard Drive | Toshiba 8X DVD-ROM Drive | 10/100 Base-T Ethernet Port, 56K ITU V.92 PCI modem | S3 Integrated VIA Twister-K, 16MB video memory | Ubuntu 9.04

For the past month or so I have been receiving the "System CMOS checksum bad" message before booting. I don't think that it has anything to do with the OS or the hard drive, since I have turned it on without the HD inserted and I get the same message. I have read that the message could also be due to a bad power supply, but the AC cord is brand new. Lastly, I arrived at the conclusion that it is the CMOS battery because most of them last 5 years and it has been more than that since it was manufactured.

Last night I talked with a Live Chat technician for HP, and since the 1 yr warantee is long expired, he said that $298 would get the notebook a new motherboard including the "HP brand" CMOS battery. But $298 is a lot of money and I could probably buy a netbook for around the same. I would hate to get rid of it even though it is old and has multiple cracks because I use it as a netbook when I go out. I would leave it the way it is but it is extremely tedious to reset the time/date every time I turn it on.

Today I stopped by a repair shop and the owner says that he can do it for $45 plus the cost of the battery.

I was going to try opening the notebook but I stopped and canceled the "operation." Before I go ahead and pay the $45+ I wanted to know if there is a way that I can do it myself. The case is held together by torx or star screws. I would appreciate a step-by step instruction set if possible with pictures and/or diagrams.

---

### Post by michy99 on 2009-08-11
The main problem is that laptop CMOS batteries are usually soldered to the motherboard. Unless your soldering skills are very good, it would be worth the $45 to get it done right. One slip with the soldering iron and the motherboard is toast.

---

### Post by Jaunty Jackalope on 2009-08-11
> **michy99 said:**
> The main problem is that laptop CMOS batteries are usually soldered to the motherboard. Unless your soldering skills are very good, it would be worth the $45 to get it done right. One slip with the soldering iron and the motherboard is toast.
Oh I see, thanks.

---

### Post by host47 on 2009-08-11
I have an old laptop with a similar problem. In the boot process there is a messeges warning me about bad bios checksum. Despite of this, the laptop work well. Replacing the battery should solve the problem.

---

### Post by dcstar on 2009-08-11
> **Jaunty Jackalope said:**
> I own the following notebook:
Compaq Presario 711CL (manufactured c. 2002): 
.......

Any hardware that old will have major reliability issues sooner or later, you may want to look at replacing it before you are up for a new CPU fan (when that inevitably fails) and possibly a new CPU (if you can actually get a replacement) if the fan failure kills it.

The battery issue may be a good opportunity to upgrade, otherwise you could be throwing good money at something that may not have much life in it anyway.

---

### Post by friskypiro on 2009-12-11
OK where do i start... I have a Toshiba a105 that a friend gave me because his girlfrends puppy peed on (it was also upside-down and went in the vents).
 
this was after 3 weeks of letting it dry out... ewwwww...
 
Found a dismanteling guide, cleaned it with alchohol. wiped the drive. installed ubuntu.
 
Rtc battery bad error 251 275 bad checksum load defaults... flashed a bios update(was really out. like version 1.4 to 6.4)
 
-come to find out when you hold down the "~" key during turn on keep holding......
-beeps (alot) and get error
-enter cmos set date and time / save and exit
 
every thing is fine...so far no more errors no soddering
 
There might be a fix out there for you like this... just find a guide and update the bios.  Read the reade me very carefully... this fix was hidden in it(i've been told)
 
On another note the recovery dvd's blow goat. If it hangs during install you can copy the files onto another dvd(or cd depending on whitch one it hangs on) and it will install fine/ or atleast mine did.
 
Good luck and hope

---

