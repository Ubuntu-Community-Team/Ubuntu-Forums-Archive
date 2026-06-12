---
title: "How do I put my home folder onto another hard drive?"
date: 2009-08-24
forum: General Help
---

### Post by nachomania on 2009-08-24
I have two hard drives, one is about 35 GB, the other is a 5GB drive I recently acquired. I have Ubuntu on the 35GB drive, and just installed Crunchbang on the 5GB drive. 

What I want to do is use the 35GB drive for /home for Crunchbang. I have already transferred documents and things to the 5GB drive, and have yet to wipe the 35GB drive. I'm guessing I can use gparted to wipe it, but I don't know how to make my /home on the 5GB drive go to the 35gb drive.

---

### Post by tuxxy on 2009-08-24
If you going to do a fresh install then you can set it up at installation, give the 35GB drive the mount point /home and then the 5GB drive would be /

[This link]("http://www.psychocats.net/ubuntu/separatehome") will explain the process in more detail.  If you didnt plan to fresh install then here is [a guide]("http://ubuntuforums.org/showthread.php?t=250104") for moving your current /home

---

### Post by nachomania on 2009-08-24
Thanks for the links, it worked perfectly!

---

