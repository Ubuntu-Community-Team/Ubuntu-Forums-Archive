---
title: "cp -r Input/Output error"
date: 2010-03-09
forum: General Help
---

### Post by dudemang on 2010-03-09
Hey folks.  I just installed a new 750 gb SATA hd into my machine.  I have an old 200gb PATA with lots of files on it that I'd like to back up.  


When I try to cp -r (directory), sometimes files will copy over, but that majority of the files get Input/Output error.  Any thoughts/suggestions?

---

### Post by dudemang on 2010-03-09
Problem resolved with a simple reboot.  Ahh the joys of computers.

---

### Post by cjhabs on 2010-03-09
Someone may correct me, but I think there are issues when copying files using cp, for example links are not retained, the linked file is copied instead.
When I do something like this I use this convoluted, but reliable method:
tar cvf - source | (cd destination; tar xvpBf -)

---

