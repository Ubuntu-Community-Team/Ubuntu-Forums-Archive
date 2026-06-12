---
title: "The Transition From Windows 7"
date: 2012-05-08
forum: General Help
---

### Post by gn2tx on 2012-05-08
I got a brand[ new ZT]("http://www.ztsystems.com/default.aspx?tabid=1239&productid=28072") in November and I'm starting to have problems with windows (for starters word stoped working on me), I'm feed up with the updates slowing down my new quad-core and the malware bombarding me 24/7.
I started looking into Ubuntu a few years ago and would have switched over BUT! I'm not the only one using the computer.
So my question is, from personal experiences if I dump windows how easy will it be for an unwilling user to adapt to Ubuntu?

---

### Post by wilee-nilee on 2012-05-08
Keep both, there are uses for them.

A OEM install has a lot of extras you don't need as far as the W7, I would check with the manufacturer and see if you can get a straight W7 install dvd that is minus the OEM stuff and can use the OEM key.

I started on open source myself and bought W7 in a student upgrade, very cheap, and use Word to write college papers it is just a bit easier that way. 

The transition is tough for some easier for others, they are different OS's, so I would suggest a dual boot as of now myself, good luck. :)

---

### Post by gn2tx on 2012-05-08
I tried a duel boot maybe 2 years ago and had a lot of problems, granted that computer had seen better days. I'm still sort of worried about doing it again.

---

### Post by wilee-nilee on 2012-05-08
> **gn2tx said:**
> I tried a duel boot maybe 2 years ago and had a lot of problems, granted the that computer had seen better days. I'm still sort of worried about doing it again.

Two years ago was probably grub legacy where you have to modify the menu.list by hand at times. Now we have grub 2 it has a os-prober that finds other OS's it is quite easy really.

What you have to be careful with here most of all is to not go over the four primary partition limit on a single HD, if it is standard mbr partitioning. You also want to use the windows disk manager to resize any windows partitions for leaving a unallocated space for a new OS, to be safe. This will allow you to reboot windows let it run its auto-chkdsk and make sure windows is fine, before installing another OS.

If you remove any partitions do not remove the windows boot partition before checking with us, it has boot files that if removed will keep windows from booting. We can get you set up so it can be removed so just let us know what you want to do.

**Do complete back up of the windows OS before anything, you are allowed at least one on a OEM install below W7 Pro.**

---

