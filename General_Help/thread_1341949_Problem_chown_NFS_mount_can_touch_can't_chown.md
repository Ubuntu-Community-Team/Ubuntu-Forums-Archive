---
title: "Problem chown NFS mount can touch can't chown"
date: 2009-11-30
forum: General Help
---

### Post by sinister1 on 2009-11-30
hello,

I've installed a new server with Ubuntu 8.04. We want to use this server as a mailserver. The maildata being used, is over NFS.

I only can mount the NFS server over NFS4. When it is mounted i can make a file but can't change the permission of any file present on the NFS mount.

Specifications:

Linux LUKKIEN-CGP 2.6.24-24-server #1 SMP Fri Sep 18 17:24:10 UTC 2009 i686 GNU/Linux
ii  libnfsidmap2                          0.20-0build1                  An nfs idmapping library
ii  nfs-common                            1:1.1.2-2ubuntu2.2            NFS support files common to client and serve
rc  nfs-kernel-server                     1:1.1.2-2ubuntu2.2            support for NFS kernel server

MOUNT:
10.10.10.7:/    /test   nfs4     hard,intr,proto=tcp,noauto 0 0

I've downgraded the kernel from 2.6.24.25 tot 2.6.24.24 because of a possible kernelbug related to NFS.

Does someone have a solutions for my problem?

---

