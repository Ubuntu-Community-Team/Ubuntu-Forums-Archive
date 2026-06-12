---
title: "Clean install"
date: 2010-08-13
forum: General Help
---

### Post by d_darlac on 2010-08-13
HI all, 

how can I completely remove GRASS (Ubuntu 10.04) from my system, so I can make a clean install - now every time I try it it comes on with the same settings = as before

---

### Post by aeiah on 2010-08-13
```
sudo apt-get remove --purge programname
``` will usually remove programname and associated settings

sometimes things still stick though, but that should be tried first. you can also select this kind of thing through synaptic

---

### Post by howefield on 2010-08-13
Probably a configuration folder in /home. Make sure that is gone after you purge.

---

### Post by d_darlac on 2010-08-15
HI guys, 
I did the purge, and removed and folder with grass I could find (actually the only one I found was the download folder)

I rebooted, reinstalled - same problem....
any ideas?

---

### Post by d_darlac on 2010-08-20
I am not sure how my problem solved, but I restarted Grass with the Python interface and that resolved my problems - 
not sure why, but works fine now!

---

