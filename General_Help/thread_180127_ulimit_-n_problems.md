---
title: "ulimit -n problems"
date: 2006-05-21
forum: General Help
---

### Post by d_v0id on 2006-05-21
Hi there, ok my problem is that i cannot set ulimit -n it always reverts back to the defalt 1024.

I have added new limits for ulimit -n to /etc/security/limits.conf
myuser hard nofile 33554432
Also i have added  >>    session required        pam_limits.so to /etc/pam.d/common-session

No matter what i try the ulimit -n always goes back to defalt 1024
Any help would be greatly appreciated.

---

### Post by d_v0id on 2006-05-29
Solved the limit i was setting was to high and would not let me change it that high dont know why, changed it to 900000 and its working fine now, just incase anyone had a similar problem :)

---

