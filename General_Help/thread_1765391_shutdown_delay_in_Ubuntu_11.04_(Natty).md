---
title: "shutdown delay in Ubuntu 11.04 (Natty)"
date: 2011-05-23
forum: General Help
---

### Post by Humanity to others on 2011-05-23
Kindly help me to solve shutdown delay in Ubuntu 11.04 (Natty) This problem occurred after I mounted ntfs drives permanently using storage device manager and I also mounted network drives permanently using  smbfs in fstab. 

The problem is after doing this system taking much time for shutdown. 

Please help. Thanks in advance..

---

### Post by Humanity to others on 2012-05-08
I found a solution for this problem

The solution:

 Rename the links in /etc/rc0.d and rc6.d as follows:

- S31umountnfs.sh to S05umountnfs.sh
- S35networking to S15networking

Thread [https://bugs.launchpad.net/ubuntu/+source/netbase/+bug/903825](https://bugs.launchpad.net/ubuntu/+source/netbase/+bug/903825)

---

