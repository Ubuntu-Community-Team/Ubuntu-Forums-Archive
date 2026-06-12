---
title: "Difference between /usr/local/include and /usr/include"
date: 2010-07-11
forum: General Help
---

### Post by mohitd2000 on 2010-07-11
What is the difference between /usr/local/include and /usr/include? When I compile my program, is both /usr/local/include and /usr/include avaliable? Can I copy a file from /usr/local/include to /usr/include?

---

### Post by gzarkadas on 2010-07-11
**/usr/local** is meant to place files scpecific to the host (computer), such as programs and libraries one compiles by itself. In general, everything that is not supplied as a package by the current distribution repositories should go there.

**/usr** is meant to place files supplied by the packages of the current distribution repositories.

By adhering to this convention one can install any software he/she likes without the danger of overwriting the distribution files and thus breaking his/her system. See for reference: [http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

So, **it is not a good idea** to copy a file from /usr/local/include to /usr/include. If you want the file in /usr/local/include to take precedence, setup your build system to look in /usr/local/include first.

---

