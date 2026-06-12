---
title: "Hello I have ubuntu 10.04, and I have a question regarding the update software."
date: 2010-09-07
forum: General Help
---

### Post by chrissy.millichamp on 2010-09-07
Why do I get this following error message?
Failed to fetch [http://ppa.launchpad.net/gonmenu-team/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/gonmenu-team/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found

---

### Post by davidmohammed on 2010-09-07
messages like that are probably due to the owner of the ppa having deleted that package - just go to system --> administration --> software sources and untick the ppa that corresponds to your error message.

---

### Post by plucky on 2010-09-07
There is a spelling mistake in the listing 

gonmenu-team should be gnomenu-team

Edit the entry in Software Sources and then reload and see if you get the same problem.

Good Luck

---

