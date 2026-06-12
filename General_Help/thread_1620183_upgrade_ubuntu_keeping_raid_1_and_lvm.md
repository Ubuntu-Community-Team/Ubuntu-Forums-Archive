---
title: "upgrade ubuntu keeping raid 1 and lvm"
date: 2010-11-12
forum: General Help
---

### Post by gettons on 2010-11-12
Hi all,

I hope this is the right section, it looks like though.

I have a small nas ( via artigo a2000 ) with 2 sata hd 1tb each with raid 1 and lvm on top configured and working great.


sda1 and sdb1 ==> md0 raid1 for /boot
sda2 and sdb2 ==> md1 raid1 for swap
sda3 and sdb3 ==> md2 raid1 as physical volume then volume group and lvs on top ( / is a logial volume of these )


I wish to upgrade the current ubuntu 9.04 32bit installation I have on it doing a fresh install. But because I have a lot of data on md2 ( 600GB worth ) which I don't want to copy across somewhere else first, I need to know how ( i am pretty sure i can ) to mount md2 during the installation. This way I can use the data I already have on it.




Thanks in advance.


Tommaso

---

