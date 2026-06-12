---
title: "apt-get segfaulting"
date: 2006-02-10
forum: General Help
---

### Post by steinnes on 2006-02-10
I was running a dist-ugprade just a few minutes ago, and my system completely froze -- the dist-upgrade was still just downloading files when my system froze.


Anyone have this problem as well? Any information I should post here which might help with understanding the problem?


```
root@hq:~# apt-get dist-upgrade
Reading package lists... Done
Segmentation faulty tree... 0%
```

I attach the output of:

strace -f -ff apt-get dist-upgrade 2>apt-get-strace.txt

with the post, however I grepped out the "gettimeofday" calls, because they bloated the file from 13KB to 190KB, which would have prevented me from posting it here.

Hope someone will be able to help :-)

Best,
Steinn E. Sigurðarson

---

### Post by steinnes on 2006-02-10
I fixed this myself, the problem was with /var/lib/dpkg/status and /var/lib/dpkg/available being corrupted, so I replaced them with the -old versions.

---

