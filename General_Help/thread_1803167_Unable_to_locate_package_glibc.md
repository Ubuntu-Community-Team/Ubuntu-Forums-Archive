---
title: "Unable to locate package glibc"
date: 2011-07-12
forum: General Help
---

### Post by wenhao on 2011-07-12
Unable to locate package glibc

sudo apt-get install glibc
Reading package lists...Done
Building dependency tree
Reading state information...Done
E:Unable to locate package glibc

I have already tried to user :
sudo apt-get update
sudo apt-get install glibc
but not work.

could you please guide me how to install it(Ubuntu 11.04) ? thanks a lot.

---

### Post by JedMeister on 2011-07-12
[http://packages.ubuntu.com/search?keywords=glibc&searchon=names&suite=natty&section=all](http://packages.ubuntu.com/search?keywords=glibc&searchon=names&suite=natty&section=all)

suggests that it isn't to be found in the Natty repos! Perhaps it's functionality has been included in another package?

You can also search for packages via the commandline:

apt-cache search <packagename>

---

