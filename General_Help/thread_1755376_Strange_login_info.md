---
title: "Strange login info"
date: 2011-05-11
forum: General Help
---

### Post by mattf87 on 2011-05-11
Hi, When I log in to my 10.04 server either via SSH or the physical machine the system displays the system info (CPU load, updates etc...) twice. I also noticed that in the second instance of this info the number of updates available 42 while in the first instance there are only 2.

Is this a bug/problem that can by solved. I have included a screenshot which may help.

Thanks.

---

### Post by mattf87 on 2011-05-11
Solved ! :KS it was related to this bug: [https://bugs.launchpad.net/ubuntu/+source/pam/+bug/766827]("https://bugs.launchpad.net/ubuntu/+source/pam/+bug/766827")

Delete /etc/matd.tail to fix the issue.

---

