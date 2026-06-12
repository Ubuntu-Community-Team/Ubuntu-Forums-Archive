---
title: "Very Slow to Shut Down"
date: 2012-02-02
forum: General Help
---

### Post by dccombs on 2012-02-02
IBM T60 laptop - core duo 1.83 - 3GB RAM (4GB installed, chipset only sees 3GB) - ubuntu 11.10
 
New install, dual boot w/win7.
 
Most of the time when I try to shut down or restart, the system hangs for at least 30 seconds before it starts to shut down.  Once in a while it will shut down/restart right away, but not very often.
 
Any suggestions?

---

### Post by dccombs on 2012-02-02
After playing around some more, the system only hangs before shutdown/restart/logout when booted into Ubuntu 2D. It shuts down instantly when I am in 3D. Is there any way I can shut down in verbose mode to see what's causing it to hang up?

---

### Post by rattskjelke on 2012-03-09
I have the same problem. It also affects Xubuntu. During the time it hangs it is actively sending/receiving data on my DSL modem. 

I aksed about it in this thread [http://ubuntuforums.org/showthread.php?t=1861688](http://ubuntuforums.org/showthread.php?t=1861688) and never got an answer.

---

### Post by jerrrys on 2012-03-09
maybe ?

[https://bugs.launchpad.net/ubuntu/+source/netbase/+bug/903825](https://bugs.launchpad.net/ubuntu/+source/netbase/+bug/903825)

---

### Post by rattskjelke on 2012-03-10
> **jerrrys said:**
> maybe ?

[https://bugs.launchpad.net/ubuntu/+source/netbase/+bug/903825](https://bugs.launchpad.net/ubuntu/+source/netbase/+bug/903825)

I renamed the scripts as suggested in the link and it appears to have fixed the problem on Xubuntu 11.10 and Linux Mint 12 LXDE.

---

### Post by synaptix on 2012-03-10
> **jerrrys said:**
> maybe ?

[https://bugs.launchpad.net/ubuntu/+source/netbase/+bug/903825](https://bugs.launchpad.net/ubuntu/+source/netbase/+bug/903825)

Solution confirmed working on Ubuntu 11.10 and Lubuntu 11.10. Shutdown is pretty much near instant.

---

