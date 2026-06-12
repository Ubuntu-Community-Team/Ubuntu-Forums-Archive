---
title: "need help with cluster.."
date: 2010-04-05
forum: General Help
---

### Post by blink309 on 2010-04-05
Hello all, first off im pretty new to Linux in general but ive made it a project to get a simple cluster running.  My main goal initially is to cluster 3 machines together for the purpose of running boinic or folding@home type applications.

Ive found this guide:
[https://wiki.ubuntu.com/EasyUbuntuClustering/UbuntuKerrighedClusterGuide](https://wiki.ubuntu.com/EasyUbuntuClustering/UbuntuKerrighedClusterGuide)

but its for ubuntu 8.04 where im running 9.10 and things don't seem to be matching up.  that and when i try to set up the dhcp server in the terminal im getting "permission denied"

Unfortunately I can't get past the first setp lol.  Ive been doing as much research as i can but most of it isn't making any sense to me.

If anyone can help me get the dhcp server put together i can try and go from there.  any other guides would be helpful, basically any help at this point is really appreciated.

-Blink

---

### Post by cjhabs on 2010-04-05
Make sure you run the s/w installation with "sudo":

sudo aptitude install dhcp3-server

---

