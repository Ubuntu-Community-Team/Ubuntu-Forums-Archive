---
title: "Upgrading system using LAN"
date: 2009-08-24
forum: General Help
---

### Post by babbar.ankit on 2009-08-24
If I have upgraded a central server, Can I upgrade other computers on LAN (not having Internet connection)... using the central server???

Can I also use my apt-get package to install from a server???
Plz reply asap...

---

### Post by P4man on 2009-08-24
yes you can, using an apt proxy. There are a few options out there, I find apt-cacher-ng to work quite well. its in the repo's, and only requires a small configuration line to the clients:

[http://www.unix-ag.uni-kl.de/~bloch/acng/](http://www.unix-ag.uni-kl.de/~bloch/acng/)

---

