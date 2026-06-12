---
title: "Where can I find devel packages for ubuntu 12.04"
date: 2012-09-05
forum: General Help
---

### Post by kjartani on 2012-09-05
Hello.

Im running Ubuntu 12.04 lts.
To be able to compile a program I must install some devel packages.
The devel packages I need are: x11, x11-proto, xinput and gnu gsl.

Anybody who knows where to find these?

Regards

Kjartan Iversen

---

### Post by gandaran on 2012-09-05
usually you can find everything in the Ubuntu software repositories but under a different name usually begining with [COLOR="Red"]lib[/COLOR]something if it is a library not application.
install synaptic package manager its better than ubuntu software center to check and find whats in the repos

---

### Post by Cheesemill on 2012-09-05
You can either use Synaptic package manager to search for them or use [http://packages.ubuntu.com](http://packages.ubuntu.com)

By the looks of things two of the packages you need are:

[x11proto-core-dev]("apt://x11proto-core-dev")
[libgsl0-dev]("apt://libgsl0-dev")

I'll leave you to find the others.

---

### Post by kjartani on 2012-09-05
Thanks to both of you....
Ill try your proposals....

Kjartan

---

### Post by sisco311 on 2012-09-05
If the source code is in the repositories, then you can use apt-get to install the build dependencies:
```
sudo apt-get build-dep *pkgname*
```

---

