---
title: "apt-get install does not working .. pls help"
date: 2010-07-13
forum: General Help
---

### Post by molykkutti on 2010-07-13
sudo apt-get install autofs



Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package autofs


whats the problem actually ?
pls help ....

---

### Post by jerenept on 2010-07-13
run ```
sudo apt-get update
```

or use the Update Manager.

---

### Post by lisati on 2010-07-13
> **molykkutti said:**
> sudo apt-get install autofs



Reading package lists... Done
Building dependency tree       
Reading state information... Done
[COLOR="Red"]E: Couldn't find package autof[/COLOR]s


whats the problem actually ?
pls help ....

The problem is that apt-get couldn't find autofs. On the software center on my laptop, which runs 10.04, a search for autofs suggests that you might have better luck with autofs5.

---

### Post by garvinrick4 on 2010-07-13
Post 3 is right here is proof.

rick@rick-laptop:~$ aptitude show autofs
Package: autofs                   
State: not installed
Version: 5.0.5-0ubuntu2
Priority: extra
Section: utils
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 49.2k
Depends: autofs5
Conflicts: autofs (< 4.1.4+debian-2.1ubuntu2)
Description: dummy transitional package from autofs to autofs5
 This transitional package helps users to transition from the autofs package to
 the autofs5 package. Once this package and its dependencies are installed you
 can safely remove it.
Homepage: [http://www.kernel.org/pub/linux/daemons/autofs/v5/](http://www.kernel.org/pub/linux/daemons/autofs/v5/)

---

### Post by Dustin2128 on 2010-07-13
if apt-get update doesn't fix it, you could always install from the .deb

---

