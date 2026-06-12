---
title: "Update manager locking up"
date: 2009-10-28
forum: General Help
---

### Post by smartroad on 2009-10-28
Hi all,
 
Got a problem with update manager, it loads up and gets the list of the updates. When I tell it to then update, it brings up the window to say downloading then locks up. It hasn't downloaded anything and the only way to get rid of the window is to forceably kill it.
 
Had a look around but not found anything as of yet to help solve it, anyone have an idea?
 
Cheers!

---

### Post by P4man on 2009-10-28
try running it from a terminal and copy/paste the output or errors here:

To refresh the list of updates:
```
sudo apt-get update
```

To actually install them:
```
sudo apt-get upgrade
```

---

### Post by smartroad on 2009-10-28
Thanks P4man, I'll do that when I get home :)

---

### Post by smartroad on 2009-10-30
Okay, sorry for delay been having problems with internet at home. I have tried them and update works fine and completes. Upgrade comes up with:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic linux-restricted-modules-generic
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.

```Update manager still locks up when it trys to download the updates.

---

### Post by P4man on 2009-10-30
you could try 
```
sudo apt-get dist-upgrade
``` to upgrade to Karmic though im unsure how smart it is to upgrade something that seems currently broken. At the very least Id test 9.10 with a livecd before taking the plunge.

---

### Post by smartroad on 2009-10-30
Solved! I needed to use: 
apt-get dist-upgrade

Rather then just upgrade :D

---

### Post by smartroad on 2009-10-30
> **P4man said:**
> you could try 
```
sudo apt-get dist-upgrade
``` to upgrade to Karmic though im unsure how smart it is to upgrade something that seems currently broken. At the very least Id test 9.10 with a livecd before taking the plunge.

Cheers! Sorry hadn't refreshed before adding my reply to see yours. doing dist-upgrade has now worked. Thanks for the advice :)

---

### Post by smartroad on 2009-10-30
Upgrade manager is knackered on my machine. It can't even update to 9.10, just locks up when it says it is disabling 3rd party sources. Ahh well, backed up all important files so will have to do a fresh install. Annoying but hay, its free :)

---

