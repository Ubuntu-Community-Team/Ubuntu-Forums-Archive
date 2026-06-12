---
title: "Lost without a map"
date: 2010-01-16
forum: General Help
---

### Post by willazilla on 2010-01-16
OK, I'm lost. So, I'll start here.;) I have a Toshiba that shipped with 64-bit Vista. Vista ate my homework in July, so I re-installed, and partitioned it, setting up Ubuntu 9.04 as the primary. (Would have gone solo with Ubuntu, but I needed a Win or Mac OS for my iPhone). Things went swimmingly until last week. My fan has been going on and staying on after only a short while from boot. This morning I tried extracting some files using archive manager, but they went askew with no main or sub-folders being put in place. I thought it may be that I needed to upgrade to Ubuntu 9.10, so I downloaded that but it wouldn't start and the only option was to cancel. Now what!? Direction to anywhere that makes sense would be greatly and dearly appreciated. There are so many technical issues here that I don't believe one forum topic will cover the sitch. So, where would you start?

---

### Post by clonne4crw on 2010-01-16
Geeze, I hate it when this weird stuff just happens with no real explanation. You're best off backing up your stuff, and then doing a fresh install of 9.10. Upgrades just never seem to work that great.

---

### Post by steveneddy on 2010-01-16
backup data - DL the ubuntu version you want, burn it and perform a fresh install

updating rarely works well - most of us do a fresh install when a version we want to run comes out

Reinstall and see where you are

if you have other issues, post a topic in the appropriate section of UF

only one subject or issue per thread for the best results

any questions, search the forums of Google and if you don't find the answer, post a thread

---

### Post by steveneddy on 2010-01-16
also check out the links in my sig

---

### Post by Xbehave on 2010-01-16
use df to check for full disks
aptitude to check for a broken install
If neither of those to fix it then Giving up and reinstalling might be the easiest thing to do, but if you want to fix it:
debsums -a > ./debsums 2> ./debsums.errors (then read the files to see if any packages are corrupt)
Look though your logs (/var/log) for hints at the error. If you attach /var/log/dmesg and /var/log/dmesg.0 , I can have a look for anything obvious and hopefully somebody who knows more can too.

---

### Post by MasterNetra on 2010-01-16
Just backup and do a fresh install. Like the others say updating rarely ends well. A issue canonical should look into. ^.^

---

### Post by cariboo on 2010-01-16
Moved to General Help, as you will get better answers here, than in the Cafe.

---

### Post by willazilla on 2010-01-17
Right to the point! Thank you all so much. I did move to the general discussion yesterday after all.

---

