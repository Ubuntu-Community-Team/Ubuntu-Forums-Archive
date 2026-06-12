---
title: "Can't ping LAN computers, Internet works."
date: 2006-02-03
forum: General Help
---

### Post by Granduke on 2006-02-03
I've installed 5.10 on my second machine.  I Can't connect thru Samba to my other LAN computers. 
I can ping this computer from my XP and 1st Ubuntu box, however this one  can not initiate a ping to the others. I don't get an error message. 
Internet does work which puzzles me.

Any ideas?

---

### Post by souki on 2006-02-03
strange,

I would double check the ethernet cable

---

### Post by dcstar on 2006-02-03
[QUOTE=Granduke]I've installed 5.10 on my second machine.  I Can't connect thru Samba to my other LAN computers. 
I can ping this computer from my XP and 1st Ubuntu box, however this one  can not initiate a ping to the others. I don't get an error message. 
Internet does work which puzzles me.

Any ideas?[/QUOTE]
Search for "disable IPv6" and try those solutions.

---

### Post by Granduke on 2006-02-07
SOLVED

Had two problems:
1.Couldn't ping the XP machine because it had Zone Alarm running.  
2.Never determined what was wrong with the other Ubuntu box.  I reinstalled using Kubuntu (wanting check out KDE) and LAN access worked.
Afterwards I installed Ubuntu 5.10 on an old laptop and the network also worked fine.  Guess something just went wrong during my first install.

---

