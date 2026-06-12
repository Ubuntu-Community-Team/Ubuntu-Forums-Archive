---
title: "Start up goes to black screen and nothing else"
date: 2011-01-12
forum: General Help
---

### Post by checoimg on 2011-01-12
Well my problem is described simple as that Black screen on start up. y laptop became a bloodless zombie after I installed BOCHS, Avast 32 bits (forced architecture) and the one I think may be the problem: Driver Manager or something like that wich is PySDM I think. This one is supose to configure mi Hard disk to automount.

---

### Post by checoimg on 2011-01-12
Well no replies. This was Solved by the lead I had on FSTAB problems done by PySDM, yes I confirmed that was the name of the app I used. Well did I make a mistake?? maybe...
Anyways I had a fstab-backup file I booted from a USB cause my DVD drive can burn right now or since some time and opened a terminal after mounting the partition the human way and typed something easy
sudo nautilus

that way I  get write permissions on partition went to the folder "etc" and typed "fstab" (something nautilus has that comes very handy with the windows open just type on keyboard and nautilus will find within the opened folder. Finally got the fstab and had a look to it changes were very basic but I just deleted the file and renamed fstab-backup to fstab rebooted and here I am writing this on ubuntu booted from my hard drive.

Hope this helps some one!!

---

### Post by Johannes Eva on 2011-01-14
Same problem with Ubuntu 9.10 "Karmic Koala".
Normal startup, but no desktop appears - black screen. 

Any idea?

---

