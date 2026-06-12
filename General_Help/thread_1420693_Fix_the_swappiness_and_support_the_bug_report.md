---
title: "Fix the swappiness and support the bug report"
date: 2010-03-03
forum: General Help
---

### Post by Pjotr123 on 2010-03-03
The swappiness (the inclination to use the swap) of Ubuntu is, by default, far too high for desktop use. It's 60, which is only fit for servers. This problem is especially irritating in machines with a relatively small amount of RAM: the hard drive gets hammered ceaselessly.

There are two things you can do about it:

1. Lower the swappiness:
[http://sites.google.com/site/easylinuxtipsproject/bugs#TOC-Computers-with-relatively-low-RAM-m](http://sites.google.com/site/easylinuxtipsproject/bugs#TOC-Computers-with-relatively-low-RAM-m)

2. Help support the bug report on Launchpad:
[https://bugs.launchpad.net/ubuntu/+source/procps/+bug/516834](https://bugs.launchpad.net/ubuntu/+source/procps/+bug/516834)

---

### Post by Pjotr123 on 2010-03-11
Bump.... The Launchpad bug report could use some support, in order to attract the attention of the developers. :P

---

### Post by Pjotr123 on 2010-03-17
The developers have responded: they won't fix it, because the swappiness is being determined by the kernel team (Linux Torvalds and his crew).
[https://bugs.launchpad.net/ubuntu/+source/procps/+bug/516834/comments/5](https://bugs.launchpad.net/ubuntu/+source/procps/+bug/516834/comments/5)

This means that systems with 512 MB RAM or less, will continue to suffer from severe performance issues. A deplorable matter.

Please help support the compromise that I proposed in that Launchpad thread: an init script that automatically lowers the swappiness *when it detects 512 MB RAM or less*.

At the bottom of the thread:
[https://bugs.launchpad.net/ubuntu/+source/procps/+bug/516834](https://bugs.launchpad.net/ubuntu/+source/procps/+bug/516834)

---

