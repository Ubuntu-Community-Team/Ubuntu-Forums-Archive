---
title: "can not remove  moblock"
date: 2009-12-29
forum: General Help
---

### Post by yon2501 on 2009-12-29
every time i try to remove moblock from my system i get this in console.

```
sudo aptitude remove moblock blockcontrol
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```
 am i missing something i have both blockcontrol and blockcontrol watchdog stopped ive shut moblock off as much as i know how so how to i remove it completely from the system? im running ubuntu 9.10 32bit

---

### Post by jre on 2009-12-31
[QUOTE=yon2501;8577546]
```

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

This is the problem! You need to stop all other instances of dpkg/apt/synaptic/aptitude.
If you don't know which is running you can find all those processes with
```
ps aux|grep dpkg
ps aux|grep apt
```

So this is a general problem. It is not related to moblock/blockcontrol. You don't have to stop moblock/blockcontrol in order to uninstall them, this happens automatically.

---

