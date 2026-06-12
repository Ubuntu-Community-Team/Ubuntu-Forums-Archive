---
title: "Backup &amp; Restore"
date: 2010-04-29
forum: General Help
---

### Post by mastermindg on 2010-04-29
If I backup Ubuntu and my system crashes causing me to reinstall from scratch...can I still restore the system from backup?

Karmic 2.6.31.14 - fresh install

---

### Post by gordintoronto on 2010-04-29
What program are you using for backup and restore?

---

### Post by mastermindg on 2010-04-29
Bacula 5.0.2

---

### Post by mastermindg on 2010-04-30
I've decided to go with G4L. I can put it on a pen drive and have an all in one backup/restore solution.

---

### Post by 98cwitr on 2010-04-30
g4l ate my hard drives...I used [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page) to take an image w/ partimg. Two annoyingly stupid requirements:

1. Has to have the same format on the drive already...no blank slates

2. Has to be the EXACT same size drive as before...ie: you cant lay your image on an 80GB drive if it can from a 500GB, even if the image is significantly smaller than 80GB. It's really dumb. 

If Im incorrect on either of these points, tell me wtf Im doing wrong. 

Anyway, I use sbackup (Simple Backup) for my file/data backups, and it has a nice, simple, and automated scheduling feature and plenty of include/exclude options. I might try bacula for a "one tool to rule" backups.

---

