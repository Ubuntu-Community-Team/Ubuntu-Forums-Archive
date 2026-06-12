---
title: "non-contiguous files"
date: 2009-07-21
forum: General Help
---

### Post by ffixcollector on 2009-07-21
I know I have asked this before, but how many "non-contiguous" files should the HDD be kept at? is 16% to much. I know on a NTFS drive it would be about time to defrag.
Running ext3, maybe I shouldn't worry, but I have been seeing performance diminish, and the drive is starting to make loud grinding noises after only 60 mounts.


Here is fsck output.
```
46018/61054976 files (16.3% non-contiguous), 163702943/244190000 blocks
```

---

### Post by oldos2er on 2009-07-21
"Loud grinding noises" could mean the drive is about to fail. I'd backup any sensitive data if I were you.

---

### Post by Rob_H on 2009-07-21
> **oldos2er said:**
> "Loud grinding noises" could mean the drive is about to fail. I'd backup any sensitive data if I were you.

Agreed. Grinding noises signal a hardware problem, not a file system problem.

---

### Post by ffixcollector on 2009-07-21
S.M.A.R.T shows that everything thing is working fine. Regardless, thais does not answer my non-contiguous files question.

---

### Post by WIGGMPk on 2009-07-21
I dont have a recommendation on the %. But that grinding noise is most likely one of two problems. Either the read/write arm is scrapping the platter, which is incrediably NOT good (if the grinding noise is constant). Or I would say that the platter is off-center (if the grinding noise is incremental)

But following everyones suggestion, I would backup and replace that drive ASAP before you find yourself doing disaster recovery for senstive/important data.

---

### Post by ffixcollector on 2010-12-31
So is there a defrag program for Ubuntu?

---

### Post by oldos2er on 2010-12-31
What file system are you using?

Found this: [http://polishlinux.org/apps/cli/ext4-defragmentation-with-e4defrag/](http://polishlinux.org/apps/cli/ext4-defragmentation-with-e4defrag/)
but reading through the article and comments, it's not something I'd personally care to try on my ext4 partitions.

---

### Post by ffixcollector on 2010-12-31
Excellent, thank you. I also found another thread with another approach. 
[http://ubuntuforums.org/showthread.php?t=1201298](http://ubuntuforums.org/showthread.php?t=1201298)

---

