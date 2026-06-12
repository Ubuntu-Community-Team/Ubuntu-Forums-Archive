---
title: "update-manager broken"
date: 2012-07-28
forum: General Help
---

### Post by meadow7 on 2012-07-28
I believe update-manager has been broken by an update.

I have started to get
peter@peter-desktop:~$ update-manager
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 33, in <module>
    from UpdateManager.UpdateManager import UpdateManager
  File "/usr/lib/python2.7/dist-packages/UpdateManager/UpdateManager.py", line 99, in <module>
    from Core.roam import NetworkManagerHelper
ValueError: bad marshal data (unknown type code)
peter@peter-desktop:~$ 

I am now using apt-get update ; apt-get upgrade

Can any one tell me what is wrong.

---

### Post by raja.genupula on 2012-07-28
whats the matter with the 

```
sudo apt-get install --reinstall update-manager 
```

---

### Post by meadow7 on 2012-07-29
I have reinstalled update-manager.
The problem persists.

I am inclined to think that something has been broken in a patch of update-manager or python.

---

### Post by meadow7 on 2012-07-31
I have just doe an 
apt-get purge update-manager
apt-get purge update-manager-core

and then

 apt-get install update-manager
 apt-get install update-notifier

This fixed my problem which I therefore attribute to down-load problems.

---

