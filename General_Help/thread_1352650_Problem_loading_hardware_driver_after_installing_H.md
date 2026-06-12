---
title: "Problem loading hardware driver after installing HP3970 Scanner"
date: 2009-12-11
forum: General Help
---

### Post by skinks on 2009-12-11
I have had Ubuntu 9.10 running on my home PC for 2 months and really like it.  I had lots of issues getting the install to work, but was able to solve all problems by browsing on forums like this.

However, now I'm stumped with problem.  I was trying to get my HP 3970 Scanner to work and I downloaded software from this website:  [http://sourceforge.net/projects/hp3900-series/](http://sourceforge.net/projects/hp3900-series/).  Thereafter, when I try to startup, Ubuntu freezes for a while on "loading hardware drivers".  It then goes into a low graphics mode and had message with something about group "scanner" unknown, and some other messaging that move to fast for me capture.  It tells me I'm running in low graphics mode because input devices could not be detected correctly.  If I try to run in low-graphics mode, the screen just goes blank and I"m stuck. 

I ran Ubuntu off boot up CD and then edited the xorg.conf file to as was orginally, but this did nothing to fix problem.    

I'm stuck now and don't know how to recover.  I assume this problem is due to the scanner driver but I don't know how to undo what I did.

---

### Post by skralljt on 2010-01-02
Shot in the dark but maybe you should try booting into text mode and remove sane from your boot scripts.  that would be going to /etc/rc* and removing anything called sane or sane.d by typing rm sane*.  I have a misbehaving hp3970 also, I feel your pain.

---

