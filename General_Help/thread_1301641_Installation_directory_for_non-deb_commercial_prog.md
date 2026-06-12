---
title: "Installation directory for non-deb commercial programs"
date: 2009-10-26
forum: General Help
---

### Post by salukibob on 2009-10-26
Hi There,

Recently I've installed two commercial bits of software that supply their own linux installers and not .deb installers. Both these installers asked where I would like to install the programs, and it got me wondering where exactly is the appropriate place to install such software?

One suggested /usr/local, and the other /opt. I recognise /opt as a more 'Unix' style software installation location, and actually did change it to /usr/local. But for these situations, where is the ubuntu 'Correct' location?

Regards
Rob Smith

---

### Post by QLee on 2009-10-26
You can choose any directory you want as long as it has the necessary permissions and is in a path for the user to run the software and/or you symlink it.

Here is a framework but recognise that different distros and at times different in history some of the directories have been favoured over others. 
Linux Filesystem Hierarchy
[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/index.html](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/index.html)

---

