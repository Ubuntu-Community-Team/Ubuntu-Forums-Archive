---
title: "apport won't start"
date: 2009-11-07
forum: General Help
---

### Post by DavidFourer on 2009-11-07
I am trying to get apport to work in a brand new install of Karmic on an HP Pavilion p6100z.  I checked synaptic and apport is installed.  Following the wiki here ([https://wiki.ubuntu.com/Apport):](https://wiki.ubuntu.com/Apport):)
> david@david-desktop:~$ sudo force_start=1 /etc/init.d/apport start
[sudo] password for david: 
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service apport start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start apport
start: Job failed to startso then I tried> 
david@david-desktop:~$ sudo service apport start
start: Job failed to start
david@david-desktop:~$ sudo start apport
start: Job failed to start
It worked in Jaunty on my old computer. 
What am I doing wrong?
Thanks.

---

### Post by mrtorrent on 2009-11-23
I had this same problem too. The only thing you can do is edit /etc/default/apport and set enabled=1. From the sounds of this bug, it seems like it won't be fixed in Karmic: [https://bugs.launchpad.net/ubuntu/karmic/+source/apport/+bug/476513](https://bugs.launchpad.net/ubuntu/karmic/+source/apport/+bug/476513)

---

