---
title: "mirror.list"
date: 2011-01-12
forum: General Help
---

### Post by slmood on 2011-01-12
Hello, i'm trying to create a repository for armel repository mirror of:

deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) lucid main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main restricted

However i'm not sure by default that apt-mirror will grab the armel dists of lucid and will try to grab x86 or x64 bit versions of the repository such as /dists/lucid/main/binary-amd64 to grab the packages.gz which in ubuntu-ports would not have that directory to grab from.  Any ideas?

also for reference i'm using apt-mirror

Thanks!

Steve

---

