---
title: "How to add ufs support to gparted"
date: 2010-12-05
forum: General Help
---

### Post by tanoloco on 2010-12-05
Hello :D

Once installed gparted has some filesystems greyed out as (if I remember right):
> fat16 fat32 hfs hfs+ jfs ntfs reiser4 reiserfs ufs xfs
I could activate them by installing some packages as:
> ntfsprogrs xfsprogs reiser4progs jfsutils hfsprogs hfsutils Any filesystem was activated except ufs which still remains greyed out.
I tried to install
> ufsutilswithout luck.

Is there anyone knowing how to solve it? How can I activate ufs support in gparted?

I'm using maverick.

Many thanks in advance!
Bye

---

### Post by nireubu on 2011-11-16
The UFS file system is used by Berkeley Unix.  It is not native to GNU/Linux
it isn't actually supported

you can read this  

[http://gparted-forum.surf4.info/viewtopic.php?id=14833](http://gparted-forum.surf4.info/viewtopic.php?id=14833)

the Cfdisk partition program can appoint FreeBSD file system type only

you can change UFS file system to XFS file system, it working for BSD kernels and is sopported to GNU/Linux

;)

---

### Post by tanoloco on 2011-11-17
Thank you very much for the tip!

I'm flattered by the fact that you spent your first post to reply me!
A big thank!

---

