---
title: "related to cpu clock"
date: 2011-02-12
forum: General Help
---

### Post by begroup on 2011-02-12
Hello all,
We are new to ubuntu and using ubuntu 10.04.
We are doing a project related to clock synchronisation. We have two laptops: Compaq and IBM Thinkpad. If we adjust the clocks of two laptops to same time in HH:MM:SS using date function, in about half an hour, both the clock drift by about 10-15 min :confused:
We are wondering how this is possible???

We have compiled kernel 2.6.36.2 on both laptops and set the value of HZ to 1000. Then what is the reason for such a significant drift in short interval of time??
Is this related to crystal oscillator or anything else???
We are really stuck here. 
Any guidance related to this will be appreciated...

---

### Post by Phlosten on 2011-02-12
Are both these installed as the native OS? ie no virtualisation?

Virtualisation and accurate time are very tricky.

Also, does the BIOS time drift. If you leave the machine in the BIOS for an extended period does it also lose time. This would validate a hardware problem

---

### Post by begroup on 2011-02-14
both are installed as native OS.
We monitored the BIOS settings for about half an hour and the system time there was precise upto seconds.
So what should be the problem???

---

### Post by asmoore82 on 2011-02-14
I had this problem a _long_ time ago.

A linux machine with oddball hardware would slowly lose time, but after each reboot,
time would be re-sync'd from the system clock and be OK for a while again.

---

### Post by begroup on 2011-02-14
what is oddball hardware??
How do we check it???

---

### Post by asmoore82 on 2011-02-15
I can't remember...

It could've been that Sis Integrated video, Sis Integrated audio, or ATI video;
or something else entirely. I think it was back when I ran Arch Linux.

---

