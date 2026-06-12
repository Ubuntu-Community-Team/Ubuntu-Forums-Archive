---
title: "kmymoney on kubuntu configure problem"
date: 2006-05-24
forum: General Help
---

### Post by buchocat on 2006-05-24
Hi,
Does anyone have advice on how to overcome this error on running ./configure? 

checking for Qt... configure: error: Qt (>= Qt 3.0 and < 4.0) (headers and libraries) not found. Please check your installation!
For more details about this problem, look at the end of config.log.

I've run just about every possible configure string telling it what path qt3 and kde3 are in (i.e., ./configure --mandir=/usr/share
--prefix=/usr/lib) and I get the same exact "not found" error.

Anyone else have this problem, or do you have any advice? 

Thanks very much,
Andy

---

### Post by warp99 on 2006-05-26
You can just install it with sudo apt-get kmymoney. Just enable the universe repository. The current version is 0.8-6ubuntu2. :cool:

---

