---
title: "file preview in nautilus on 11.04 on networked home drive"
date: 2011-08-02
forum: General Help
---

### Post by bez654 on 2011-08-02
We have recently upgraded to ubuntu 11.04 64bit from 10.04 and 10.10 in a networked office in which our home directories are mounted on a server raid array. Ubuntu considers that the home directory is a local drive rather than on a network
We have noticed that file preview are very very slow in 11.04 for pdf's and pictures in nautilus, causing a lag of around 10 seconds for each file. This can cause a problem for folders which hold multiple files which can be previewed. Preview worked fine in previous versions of ubuntu on the same machine, with the same network setup. Previewing of actual local files works faster, but is slower on 11.04, than previous versions. 
Both the 10.10 and 11.04 systems are up to date with available updates (11.04 - 2.32.2.1 and 2.30.1 on ubuntu 10)
Obviously, there is a work around for this problem - turn off preview. But, it would be nice to turn it on as its a useful feature. 
Has anyone else noticed this problem or, even better, know of a fix?
Thanks
John

---

### Post by brubelsabs on 2011-08-11
I've got exact same problem. It is apparmor stopping evince-thumbnailer to work properly. Bug is described here: [https://bugs.launchpad.net/ubuntu/+source/evince/+bug/778638](https://bugs.launchpad.net/ubuntu/+source/evince/+bug/778638)

Workaround also described there combined comments #7 and #10 made it work for me again.

What I found out to be really stupid is, that if a single program like evince-thumbnailer will not work, WHY_T_F others have to wait??? Complete stupid issue. You don't see anything in top, and the system freezes... so spend almot 2 working days with that :(

---

