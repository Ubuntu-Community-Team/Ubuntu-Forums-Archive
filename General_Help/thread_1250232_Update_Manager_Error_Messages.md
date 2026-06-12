---
title: "Update Manager Error Messages"
date: 2009-08-26
forum: General Help
---

### Post by odiear3rd on 2009-08-26
When I first log on to Firefox, the update Manager pops up and I try to install updates I get the following error message:

Not enough free disk space

The upgrade needs a total of 395M free space on disk '/'. Please free at least an additional 363M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.

How can I solve this problem?? How can I give it more disk space??

---

### Post by michy99 on 2009-08-26
It is very likely that you have installed Ubuntu on a partition that is too small. Check out this thread to see how to fix it:

[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)

You can free up some space by running```
sudo apt-get clean
```

---

### Post by odiear3rd on 2009-08-27
I solved the problem by reinstalling Ubuntu. Orginally I Partitioned Ubuntu to 30BG but it only gave me 3gb instead. Thanks for your advise.

---

