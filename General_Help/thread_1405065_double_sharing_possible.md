---
title: "double sharing possible?"
date: 2010-02-12
forum: General Help
---

### Post by linuxcss on 2010-02-12
Is it possible to double share in ubuntu?

for example:

server1 has share A

I want server2 to have a local share pointing back to shareA on server1

The reason for this is I want to limit access to a virtual machine guest session (VMGS)
to host only mode networking running on host (server2).

Or is there another way to achieve and limit VMGS only to see that external share on server1?

---

### Post by t4thfavor on 2010-02-12
share it on machine 1, and then permanently mount it on machine2 with sshfs, or samba or nfs, then share that folder again. It will do what you need.

---

