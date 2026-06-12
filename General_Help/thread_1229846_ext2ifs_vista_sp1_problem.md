---
title: "ext2ifs vista sp1 problem"
date: 2009-08-02
forum: General Help
---

### Post by blur xc on 2009-08-02
I have the same problem as posted in this thread- [http://ubuntuforums.org/showthread.php?t=942024&highlight=ext3ifs+vista](http://ubuntuforums.org/showthread.php?t=942024&highlight=ext3ifs+vista)

I don't know a solution.  I installed it after a clean install of vista sp1, and when I click on a drive letter it asks me to format the drive.  I definitely don't want to do that.

Thanks,
BM

---

### Post by rainwalker on 2009-08-02
The ext2ifs driver can only handle directory inode sizes of 128. Newer Linux releases like Ubuntu 9.04 use an inode size of 256, so there's nothing you can do unless you want to reformat your Ubuntu install completely. The other option is using the ext2fsd driver, but that won't work for you (or me) because Vista doesn't allow unsigned drivers to be run unless you're in "test mode", so really there's not much we can do.

---

### Post by rainwalker on 2009-08-03
Ah! I was wrong, ext2fsd has been updated!
[http://www.ext2fsd.com/](http://www.ext2fsd.com/)

---

### Post by blur xc on 2009-08-03
Hey, thanks, I downloaded them and will give it a try asap.

BM

---

### Post by blur xc on 2009-08-07
update- dl'd it, and it works like a charm, so far at least...

thanks!

BM

---

