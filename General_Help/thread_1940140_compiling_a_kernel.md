---
title: "compiling a kernel"
date: 2012-03-13
forum: General Help
---

### Post by bibble235 on 2012-03-13
Trying to follow

[http://blog.avirtualhome.com/2011/10/28/how-to-compile-a-new-ubuntu-11-10-oneiric-kernel/](http://blog.avirtualhome.com/2011/10/28/how-to-compile-a-new-ubuntu-11-10-oneiric-kernel/)

And cannot get past 

apt-get build-dep linux-image-$(uname -r)

which returns

with

Picking 'linux' as source package instead of 'linux-image-3.0.0-13-generic-pae'
E: Unable to find a source package for linux

---

### Post by bibble235 on 2012-03-13
Just add

deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric main restricted universe multiverse

I liked the old way make xconfig they were the days

---

