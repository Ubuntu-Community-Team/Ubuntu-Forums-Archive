---
title: "how to enlarge swap file"
date: 2010-11-30
forum: General Help
---

### Post by big136 on 2010-11-30
Hi,
I have this :
user1@ubuntu:~$ grep MemTotal /proc/meminfo
MemTotal:      1117060 kB
user1@ubuntu:~$ grep SwapTotal /proc/meminfo
SwapTotal:      915664 kB


But I need a swap file 1700MB. How can I enlarge it ?

Thanks.

---

### Post by ptn107 on 2010-11-30
You can install gparted and resize your current partitions (must be done from the live CD though).  Or you can add another swap file with more space without the need for any gparted resizing[1].

1: [http://www.linux.com/archive/feature/113956](http://www.linux.com/archive/feature/113956)

---

