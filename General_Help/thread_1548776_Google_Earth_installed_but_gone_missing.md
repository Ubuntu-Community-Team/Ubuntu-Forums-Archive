---
title: "Google Earth installed but gone missing"
date: 2010-08-08
forum: General Help
---

### Post by Quackers on 2010-08-08
I've been reading a lot about problems with GE when running Lucid Lynx and being of an inquisitive nature I've installed it through Synaptics :-) It installed ok but I can't find it :( Where did it go?
Could somebody enlighten me please?

---

### Post by clhsharky on 2010-08-08
Quackers

Have you looked in (Applications ->Internet)?

Sharky

---

### Post by Quackers on 2010-08-08
Yes, I have Sharky. In fact I think I've looked everywhere!
I just installed it the "old" way - from Google Earth and sh command. I've now got a desktop icon but it says it's not a trusted application or something. I'll try the edit offered in an earlier post on the subject.
Cheers ears

---

### Post by Quackers on 2010-08-08
Aha! I just right-clicked on the desktop icon and selected properties then ticked the run as executable box. It runs fine - no problem at all so far.
In fact I'm just looking at my mate's boat outside his house in Nassau. Lucky 
B*******d :-)

---

### Post by jcolyn on 2010-08-08
Uninstall the version you installed. Next go to the terminal and enter 

sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list 
http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && 
sudo apt-get --quiet update && sudo apt-get --yes --quiet 
--allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet 
updateOnce done enter sudo apt-get update

This will enable and update the packages from Medibuntu

Go to synaptics package manager and type googleearth find the one from medibuntu and mark for installation. This is the only version of googleearth I have found that works.

---

### Post by Quackers on 2010-08-08
Thanks jcolyn for your reply. It is now working but I will bookmark this thread and try your instructions if problems arise.

---

