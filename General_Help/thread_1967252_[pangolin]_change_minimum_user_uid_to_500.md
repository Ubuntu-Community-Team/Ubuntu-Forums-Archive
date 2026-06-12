---
title: "[pangolin] change minimum user uid to 500?"
date: 2012-04-27
forum: General Help
---

### Post by jamesvan on 2012-04-27
How do I change the minimum user uid from 1000 to 500 in 12.04 LTS?

Due to existing NFS and VirtualBox infrastructure I needs my user uid to  be 502.  This was possible in previous versions of ubuntu but has  become messier in 12.04.  The best solution is just dhange a *.conf file  somewhere to make the range of recognized user uids include 502.

---

