---
title: "E: Couldn't find package build-essentials"
date: 2010-01-07
forum: General Help
---

### Post by Silvernail on 2010-01-07
Version 9.10

What would cause this message?
> dave@dave:~$ sudo apt-get install build-essentials
[sudo] password for dave: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-essentials


I checked '/etc/apt/sources.list' and everything is marked as available.

---

### Post by drs305 on 2010-01-07
Drop the trailing "s" and you will probably find it:
*build-essential*
It's in the *main* repository.

*Please mark the thread solved via the Thread Tools link near the upper right of the original post when you no longer need assistance.*

---

