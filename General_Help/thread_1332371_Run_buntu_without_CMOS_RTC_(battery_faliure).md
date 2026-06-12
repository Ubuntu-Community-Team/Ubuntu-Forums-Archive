---
title: "Run *buntu without CMOS RTC (battery faliure)"
date: 2009-11-20
forum: General Help
---

### Post by Ylon on 2009-11-20
be: I already know that change the battery will "solve" my problem... this, indeed, is more a challenge for me to discover new things on linux.



I own this (very old) Compaq laptop wich it's battery (both RTC and power battery) are failed (it work only with power cable).

This mean that sometime it boot with random clock/date settings: 10/12/1935...30/30/3043 etc..etc...

So, obviously, any linux distro I'd try to boot.. didn't work: since it looks like is so "essential" the RTC to make check&co.
I can't have access to the network until the GUI is fully loaded (I use wifi and different networks to connect it).

Which is the best way to solve it (besides change RTC battery or keep it always connect to power cable)?

---

### Post by niteshifter on 2009-11-20
Hi,

Enter the machine's BIOS and set the clock.

---

### Post by fluffman86 on 2009-11-20
But setting the clock in the BIOS won't help if the battery is dead...it'll just reset when the computer loses power.

It's really not that hard to replace the battery.  Just pop it out, take it to the store, and buy a new one.  They are less than $1 in the US.

Or if you don't want to do that, you can buy a $50 - $100 Uninteruptable Power Supply from an office store and just use your computer as an always on server.

---

### Post by falconindy on 2009-11-20
> **Ylon said:**
> be: I already know that change the battery will "solve" my problem... this, indeed, is more a challenge for me to discover new things on linux.



I own this (very old) Compaq laptop wich it's battery (both RTC and power battery) are failed (it work only with power cable).

This mean that sometime it boot with random clock/date settings: 10/12/1935...30/30/3043 etc..etc...

So, obviously, any linux distro I'd try to boot.. didn't work: since it looks like is so "essential" the RTC to make check&co.
I can't have access to the network until the GUI is fully loaded (I use wifi and different networks to connect it).

Which is the best way to solve it (besides change RTC battery or keep it always connect to power cable)?
Getting rid of the clock isn't an option. It's essential for far too many things. Case in point: I accidentally compiled a kernel **without** the means to access my clocksource and I couldn't boot.

---

### Post by Ylon on 2009-11-20
Thanks to all the advices. By sure changing clock setting in the bios (yet, I can't) or the battery (not for the $/&#8364;, but dismantle a (old) notebook isn't my thing) would solve my problem.
But I am more likely to find something (script-like) that would temporary allow me access to system until I'd find better hardware solution.



I am more likely to use "date -s xx" and "hwclock -w" command... but I need to find somewhere to place in /etc/init.d


this command has to be executed before anything.


Plus, I would like that this script will updated with cron (every ~5min) taking the time somewhere in internet (when connected).

Is such thing possible?
for example, i put in in /a/file/date.txt and /a/file/time.txt the content of clock and date (the last taken from internet).
then, everytime the pc boot a script run something like:

date -s < /a/file/date.txt
date -s < /a/file/time.txt
hwclock -w



is possible make such thing work?

---

### Post by P4man on 2009-11-20
I dont see how you can run any script before the kernel has booted, and Im not sure, but the kernel may not like not having a valid clocksource, it may not like mounting your filesystem when the date is off. 

What happens when you try to boot with a 1935 or 3000+ date?

---

### Post by Ylon on 2009-11-20
> **P4man said:**
> I dont see how you can run any script before the kernel has booted, and Im not sure, but the kernel may not like not having a valid clocksource, it may not like mounting your filesystem when the date is off. 

What happens when you try to boot with a 1935 or 3000+ date?

It vary... sometime ask for me fsck since some essential file where "closed/modified" in the future (when clock is too much in the past).


Where can I add some script to run in init 1?

---

### Post by P4man on 2009-11-20
Im no expert but I would guess in /etc/rc1.d/
But again by that time your file system is mounted and its "too late".

---

