---
title: "Cannot update dpkg error code"
date: 2012-03-28
forum: General Help
---

### Post by metalcutter on 2012-03-28
[SIZE=2]Hello Dood,  I have the same problem.  Mine will not do updates or upgrades of any kind. Muon package manager won't work, apt-get won't do anything and dpkg does nothing.
I am at the point of reinstalling Fedora or something else ie. BSD
:confused:  It says to report abuse. I 'll take any attention even abuse.  PAY ATTENTION!!!

Possible answer:
[http://www.daniweb.com/hardware-and-software/linux-and-unix/threads/203341/debian-lenny-getting-error-code-2-from-dpkg-trying-to-install-libcups2-dev](http://www.daniweb.com/hardware-and-software/linux-and-unix/threads/203341/debian-lenny-getting-error-code-2-from-dpkg-trying-to-install-libcups2-dev)
[/SIZE]

---

### Post by garvinrick4 on 2012-03-28
Old thread you jumped into: Have no idea what happened metalcutter but you got it stuck updating somehow. 

```
sudo dpkg --configure -a
```or try both one at a time.

```
sudo apt-get -f install
```

Maybe even: one at a time below in terminal
sudo rm /var/lib/apt/lists/* -vf 
sudo apt-get clean all 
sudo apt-get update

---

### Post by raja.genupula on 2012-03-28
> **metalcutter said:**
> [SIZE=2]Hello Dood,  I have the same problem.  Mine will not do updates or upgrades of any kind. Muon package manager won't work, apt-get won't do anything and dpkg does nothing.
I am at the point of reinstalling Fedora or something else ie. BSD
:confused:  It says to report abuse. I 'll take any attention even abuse.  PAY ATTENTION!!!

[/SIZE]

its always better to start your own thread . while coming to your issue please post that error code in terminal  here .

---

### Post by philinux on 2012-03-28
Split off to own thread.

@metalcutter please see this. [http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by Adrian98 on 2012-03-28
Wasn't knowing this much for the Update of dpkg!! Seems like Need to learn more about it!! Thanks!!

---

