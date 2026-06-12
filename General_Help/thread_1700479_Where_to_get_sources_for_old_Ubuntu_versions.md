---
title: "Where to get sources for old Ubuntu versions?"
date: 2011-03-05
forum: General Help
---

### Post by Fanatico on 2011-03-05
I am running Ubuntu 10.04 and I need to build kernel (2.6.27) for old Ubuntu version 8.10 Intrepid.

I read bunch of manuals how to build Ubuntu kernel, but I still can not find answer to two fundamental questions!

I was told, that I can't simply take kernel sources from kernel.org and compile them for Ubuntu.
I need special Ubuntu patched kernel sources, so my question is whether this is correct and where
can I get these sources for old Ubuntu 8.10?

I was also told that I CAN take sources from kernel.org but then I have to apply special Ubuntu patches.
Where can I take these Ubuntu patches for old Ubuntu 8.10?

I tried the following:

This is not good because it will bring me sources for current version 2.6.32-29-generic
apt-get source linux-image-`uname -r` 

The following returned errors
apt-get source linux-image-2.6.29-11
E: Unable to find a source package for linux-image-2.6.29-11

apt-get source linux-image-2.6.28
E: Unable to find a source package for linux-image-2.6.28

apt-get source linux-image-2.6.27
E: Unable to find a source package for linux-image-2.6.27

Thanks

---

### Post by maqtanim on 2011-03-05
As the support of 8.10 has been terminated so you can not find any package for 8.10 with apt-get.

---

### Post by plucky on 2011-03-05
This [Link](https://launchpad.net/ubuntu/intrepid/i386/linux-image-2.6.27-11-generic/2.6.27-11.31) might help.

Good Luck

---

