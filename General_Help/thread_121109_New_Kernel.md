---
title: "New Kernel"
date: 2006-01-24
forum: General Help
---

### Post by jonathanm on 2006-01-24
Is there any reason why Ubuntu is so slow at updating the kernel, a friend at school is running Gentoo and is already on 2.6.12-15-386 while i am still on 2.6.12-10-386.

---

### Post by endersshadow on 2006-01-24
Ubuntu releases on a 6 month release schedule.  The software that Ubuntu comes with at its release remains the software that that release of Ubuntu uses for those 6 months (save security updates).  The newest kernel has not been backported yet, so it is not available.  The backports project is one that ports new versions of software for releases of Ubuntu.  If you would like, you can compile the kernel from source.  RubenGonc has made a great HowTo to compile 2.6.14 [here](http://ubuntuforums.org/showthread.php?t=84174).  Additionally, tseliot has posted a HowTo for generic kernel complation [here](http://ubuntuforums.org/showthread.php?t=85064).

Otherwise, you'll have to wait for Dapper to upgrade your kernel via apt-get.

---

