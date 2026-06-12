---
title: "I mised up my upgrade to 12.04"
date: 2012-04-28
forum: General Help
---

### Post by mld9373 on 2012-04-28
Well did it again. I was upgrading to 12.04 an did not let the upgrade finish before i turned the computer off. now when i try to upgrade i get another error,Not all updates can be installed. Run a partial upgrade. Well when i try to run a partial upgrade i get another error: unable to get exclusive lock.This usually means that another package management application(like apt-get or aptitude) already running. Please close that application first ?

                                                                        Please Help  :confused:

---

### Post by plucky on 2012-04-28
> **mld9373 said:**
> Well did it again. I was upgrading to 12.04 an did not let the upgrade finish before i turned the computer off. now when i try to upgrade i get another error,Not all updates can be installed. Run a partial upgrade. Well when i try to run a partial upgrade i get another error: unable to get exclusive lock.This usually means that another package management application(like apt-get or aptitude) already running. Please close that application first ?

                                                                        Please Help  :confused:

If you haven't re-installed as yet,you could try removing the lock file that was left over from the previous upgrade.
Open a terminal and use ```
sudo rm /var/lib/dpkg/lock
``` and then see if you are able to run ```
sudo dpkg --configure -a
```

Good Luck

---

### Post by paulkiss on 2012-07-30
Just had the same trouble, thanks a lot for the advice it helped to solve the problem

---

