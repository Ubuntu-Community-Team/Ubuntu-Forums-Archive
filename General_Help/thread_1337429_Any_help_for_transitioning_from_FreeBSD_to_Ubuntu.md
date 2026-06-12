---
title: "Any help for transitioning from FreeBSD to Ubuntu?"
date: 2009-11-25
forum: General Help
---

### Post by markintellect on 2009-11-25
I have a home server running FreeNAS (based on FreeBSD), and I want to see if it would be possible to transition it to running a Linux distro with a proper OS. Problem is that all my data (on one 1TB drive) is formatted as UFS, which I know that Linux can have quite flaky support for. I've tried the x86_64 Desktop LiveCD and it can't see any of the data on the drive (it knows it is formatted as a FreeBSD drive, but that is it). Is there any simple way of letting Ubuntu read, write or do anything but delete the UFS partition?

---

### Post by cariboo on 2009-11-25
Have a look at this [howto]("http://tldp.org/HOWTO/Linux+FreeBSD-5.html"), it should help solve your problem.

---

