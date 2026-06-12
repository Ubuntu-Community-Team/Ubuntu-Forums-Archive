---
title: "Ath9k wireless fix HERE"
date: 2012-01-05
forum: General Help
---

### Post by jibawakee on 2012-01-05
Open up the terminal and insert this ```
sudo apt-get install linux-backports-modules-cw-2.6.39-natty-generic
```:D:D try that if it doesnt work let me know

---

### Post by QIII on 2012-01-05
Might depend on the kernel someone is using and the particular chipset.
  
  I'm pretty sure that > 2.7 has the driver module already included.
 
 Not so long ago I resurrected and old laptop for my daughter using Bodhi with 3.0.0.   Had to give her a USB wifi adapter.  I'm pretty sure all I did was  modprobed ath9k and made sure the most recent firmware was in the  appropriate directory.  Maybe had to black-list something.  Anything more than two weeks ago is a blur.

Anyway, thanks for helping someone else out.  It might be better next  time to give some information about your system and your OS so that  others can see if their setup is similar enough to yours for that  solution to work.  You have to be careful about making broad-stroke assumptions.  Everyone's system is different.

---

