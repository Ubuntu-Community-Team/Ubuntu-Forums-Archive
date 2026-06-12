---
title: "Interesting virus experience ?"
date: 2009-11-12
forum: General Help
---

### Post by sledge73 on 2009-11-12
I just installed a Karmic live cd to a flash drive & took it to my buddies house so he could check it out. He liked the live cd & wanted to try the wubi install, so he booted windows & plugged the flash drive in & low and behold his virus scanner reported it as a virus! Virus???? It was a new flash drive, when I scanned it with clamav it showed clean. Just wandering if anyone else has had this happen??


I know Bill Gates thinks Linux is a windows virus but come on! 

Any thoughts???

---

### Post by fluffman86 on 2009-11-12
What file did the AV scanner find?  Which AV scanner?  If it was wubi.exe, then yeah, that kinda makes sense (since wubi can make pretty steep changes to your system, including editing your boot.ini) even though it's still a false positive.  

If it's finding Wubi, then you should report it to your AV company.  They'll be happy to accecpt a copy of the file to test it and whitelist it.

---

### Post by sledge73 on 2009-11-12
I think he was using comodo but the exact virus we didn't write down. He ended up trusting me & installing anyway (which was kind of nice). But I will pass on the info & when I go to my sisters I will have her scan it to see what becomes of it. I personally don't have a windows box in the house!

---

### Post by panicy on 2009-11-13
I'm a malware analyst for a software company and I work with clamav everyday....  Trust me when I say that it has more than a couple of false positives.  Im sure it was probably wubi that caused it and I wouldn't worry about it at all.  Clamav is really only designed for email scanning on the server side.  Its open source so with ALOT of code modification it could be used on a desktop pc, but generally I would avoid it.  Hope that helps

-dp

---

