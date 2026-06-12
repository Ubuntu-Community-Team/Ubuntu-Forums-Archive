---
title: "no NFS server support in 10.10 64bit?"
date: 2010-10-13
forum: General Help
---

### Post by meulie on 2010-10-13
Hi all,

Just installed Ubuntu 10.10, and am unable to install NFS server. Starting nfs-kernel-server keeps returning:
> * Not starting NFS kernel daemon: no support in current kernel.

uname reports:
>  2.6.35-22-virtual #34-Ubuntu SMP Sun Oct 10 12:25:39 UTC 2010 x86_64 GNU/Linux

---

### Post by SeijiSensei on 2010-10-13
> **meulie said:**
> Just installed Ubuntu 10.10, and am unable to install NFS server.

Don't know about "virtual" but nfs-kernel-server works fine with 2.6.35-22-generic x86_64.

---

### Post by meulie on 2010-10-13
> **SeijiSensei said:**
> Don't know about "virtual" but nfs-kernel-server works fine with 2.6.35-22-generic x86_64.

I guess it's been stripped from -virtual...  :roll:

---

### Post by CodeMonkeyX on 2010-12-20
I just ran into this too while making a 10.10 virtual appliance for serving files in our small business.

What would be the best way to add kernel support to the virtual version of the kernel without loosing all the optimizations made?

I assume I could just install the standard server kernel, but seeing as NFS is the only thing I need it seems a shame to get everything else that I assume comes with the full server kernel.

---

