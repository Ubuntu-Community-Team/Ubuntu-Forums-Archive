---
title: "segmentation fault from su, passwd, ftp, other"
date: 2010-10-26
forum: General Help
---

### Post by singlow on 2010-10-26
I recently upgraded to meerkat on my desktop. In case it matters, this was originally a jaunty install that had been upgraded at each release and was at lucid prior to the meerkat upgrade. 

I don't know exactly when this started, as I had just done an update today before noticing it, but su, passwd, ftp and other binaries were producing segmentation faults. Dmesg reported "error 6 in libnss_compat-2.12.1.so" so I started googling and didn't find much. 

However after a lot of experimenting I noticed that my /etc/nsswitch.conf file had been updated at some point and there was an nsswitch.conf.lwidentity.orig file next to it. I swapped them and all is working again (cross my fingers).

The diff of the two files:
7,8c7,8
< passwd:         compat
< group:          compat
---
> passwd:         compat lsass
> group:          compat lsass

The working file is the one _without_ lsass.

I hope this can help someone else who runs into the problem. I don't believe I ever modified that file manually, so not sure if this is an artifact of having upgraded through several releases or some other packages I had installed.

---

