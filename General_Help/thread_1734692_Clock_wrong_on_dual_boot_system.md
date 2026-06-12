---
title: "Clock wrong on dual boot system?"
date: 2011-04-20
forum: General Help
---

### Post by Replay345 on 2011-04-20
Hi,

I've set-up dual boot on my laptop. Ubuntu installed first, then Windows 7 so it uses Grub2 to control the booting on start-up.

I've noticed that my system clock goes out by an hour on both OS's, I change the clock to correct time & on reboot the time is usually (not always straight away) an hour behind.

Has anyone else had this problem & know how to fix it?

Thanks, Nick

---

### Post by ububeginner on 2011-04-20
Sounds like a summer daylight savings problem.

In Ubuntu you can right click on the clock and select preferences. under the locations tab you type the name of your city/country and the time will then sync with an online server that provides the accurate time. (and temperature)

I think that Windows has a similar option

---

### Post by r-senior on 2011-04-20
I don't know from practical experience if this is still true because it's a long time since I had a dual boot, but Windows used to adjust for daylight saving time by actually changing the system clock. Linux, OTOH, tends to leaves the system clock fixed (at UTC?) and compensates in the system call that gives your localized time.

This document:

[https://help.ubuntu.com/community/UbuntuTime#Make%20Windows%20use%20UTC](https://help.ubuntu.com/community/UbuntuTime#Make%20Windows%20use%20UTC)

gives ways of making the two play nicely - either make Ubuntu use local time for the system clock, or make Windows use UTC.

---

### Post by tredegar on 2011-04-20
Windows doesn't know how to handle time or timezones properly. 

Linux does, because (IIRC) it keeps your **h**ard**w**are **c**lock (powered by the battery on your MoBo) syncronised to UTC, then it makes adjustments for your chosen timezone with software. You can tell linux you have moved to a new timezone, the HWC isn't changed but the time your system sees is magically adjusted.

The above links should get you started, otherwise [http://google.com/linux](http://google.com/linux) will help.

I am not just (lazily) pointing you at google, but google's linux-specific search engine. Check the link, it is *better*.

---

### Post by Replay345 on 2011-04-22
> **r-senior said:**
> I don't know from practical experience if this is still true because it's a long time since I had a dual boot, but Windows used to adjust for daylight saving time by actually changing the system clock. Linux, OTOH, tends to leaves the system clock fixed (at UTC?) and compensates in the system call that gives your localized time.

This document:

[https://help.ubuntu.com/community/UbuntuTime#Make%20Windows%20use%20UTC](https://help.ubuntu.com/community/UbuntuTime#Make%20Windows%20use%20UTC)

gives ways of making the two play nicely - either make Ubuntu use local time for the system clock, or make Windows use UTC.

Thank you, sorted :)

---

