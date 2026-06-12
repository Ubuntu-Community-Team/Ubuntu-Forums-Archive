---
title: "Base Ubuntu install Size"
date: 2009-12-14
forum: General Help
---

### Post by habtish on 2009-12-14
Hello,

I have an Ubuntu install image (9.04) within a windows XP image that we load in our lab computers. We use VMWare Player to give students a chance to "play" with Linux while still in a windows environment that they are familiar with. 

After upgrading this Ubuntu install from 8.10 to 9.04 this past summer, the size of the install image (.vmdk) grew to over 4GB. We use Novell ZenWorks to image our windows machines, which has a 4GB file size limit. My question is, after upgrading the current Ubuntu image to 9.10, what files and caches can I can get rid of to shrink the size of this base Ubuntu image to the smallest possible working image? Should I be looking into apt caches and dpkg? 
 
 Appreciate all your helpful ideas..

Thanks!

---

### Post by solar george on 2009-12-14
Try 
```
apt-get clean
```
to clear the dpkg caches.

My kubuntu weighs in at around 4.7gb but thats with quite a few additional programs installed.

---

