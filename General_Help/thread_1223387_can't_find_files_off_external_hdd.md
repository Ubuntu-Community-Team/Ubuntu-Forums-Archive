---
title: "can't find files off external hdd"
date: 2009-07-26
forum: General Help
---

### Post by chersen on 2009-07-26
hi. 
sorta new to the linux arena. been testing out different distros for a while, and never had this problem. however, i just did a fresh install of jaunty on a new partition and i can't find some files. 

listen:

recently took all of "my documents" files off of windows onto an nfts external hdd. when testing different distros' livecds, i was able to find and play all the songs in "my music" off of the external harddrive. however, after installing jaunty and trying to copy files from the external to my new ubuntu partition, "my music" shows up empty. i rebooted in windows (dual-boot for work purposes) and found the files just fine. what gives? anyone know whats going on? 

thanks in advance

-chersen

---

### Post by merlinus on 2009-07-26
Is your external hdd mounted in ubuntu?

---

### Post by Bucky Ball on 2009-07-26
Run:

sudo blkid

... in a terminal with the external drive switched on. Does it show?

---

### Post by chersen on 2009-07-26
yes the external is mounted as soon as i plug it in. i can retrieve everything else in "my documents" (e.g. my videos, my pictures, etc.) except for my music

---

