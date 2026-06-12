---
title: "NFS: can't sync data to other machine"
date: 2012-05-06
forum: General Help
---

### Post by rockballad on 2012-05-06
Hello,

I setup a cluster of MPI, following instruction here [https://help.ubuntu.com/community/MpichCluster](https://help.ubuntu.com/community/MpichCluster)

The master node, I installed NFS to share the folder /mirror to all other machines on the cluster. It means if I change the content of master:/mirror, the folder /mirror on other nodes will change the same. But it doesn't work. Do you know what's wrong here?

Thank you in advance!

---

### Post by rockballad on 2012-05-21
OK I forgot to install nfs-common. Fix it now. Thanks.

---

