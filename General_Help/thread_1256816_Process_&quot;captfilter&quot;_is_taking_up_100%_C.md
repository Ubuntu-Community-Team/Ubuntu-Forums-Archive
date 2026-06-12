---
title: "Process &quot;captfilter&quot; is taking up 100% CPU?"
date: 2009-09-03
forum: General Help
---

### Post by Invicta on 2009-09-03
Hiya, linux-noob here. 
Having a problem in 9.04 - after installing a Canon LPB-1120 printer and printing a test page (worked fine), a process called captfilter (by user "lp"!?) is taking 100% of my CPU, causing the system to run slow. Any ideas what this process does, how to disable it and how wise would that be? I assume it has something to do with the printer driver?

Thanks in advance!

---

### Post by P4man on 2009-09-03
its definitely part of the canon drivers. Killing it should be ok, at worst you might not be able to print until you log out/in, but even that would surprise me. Would be kind of annoying if this happens all the time though. 

I quickly googled on your printer, which capt driver did you download ? This (probably obsolete) page here:
[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900)

says that capt 1.80 isnt working on ubuntu 8.10, and they recommend the 1.60 driver instead. Not sure that applies to jaunty (9.04) though..

---

