---
title: "Monitor user actions in a Directory"
date: 2011-01-10
forum: General Help
---

### Post by chrislynch8 on 2011-01-10
Hi,

We have a shared directory that is very important, lately strange things have been happening, users claiming file are missing etc. All permissions are OK, and as far as I can see files are not going missing. 

I look for ether a program out there all ready, or guidlines on a script that will monitor the dates and times a user accesses this directory, if they create a new file, remove an old one etc.

Any pointers in the write direction wouldbe great.

Rgds
Chris

---

### Post by Habitual on 2011-01-11
Have a look at [http://www.ibm.com/developerworks/linux/library/l-inotify/index.html](http://www.ibm.com/developerworks/linux/library/l-inotify/index.html)

or [http://www.cyberciti.biz/faq/linux-inotify-examples-to-replicate-directories/](http://www.cyberciti.biz/faq/linux-inotify-examples-to-replicate-directories/)

those should get you started "in the right direction". Others may have a more direct solution. :)

---

