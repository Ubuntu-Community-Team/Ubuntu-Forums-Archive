---
title: "symbolic link"
date: 2012-06-20
forum: General Help
---

### Post by Drenriza on 2012-06-20
Is it possible to create a symbolic link between two servers, without mounting a drive over NFS and then linking from the mounted drive.
But directly from Server1 to Server2.

If so, how?

Thanks on advance.

---

### Post by papibe on 2012-06-20
Hi Drenriza.

Short answer: no.

But if there's a bigger concern behind your question, we may come out with other ideas, if you care to explain it to us ;)

Regards.

---

### Post by Drenriza on 2012-06-20
> **papibe said:**
> Hi Drenriza.

Short answer: no.

But if there's a bigger concern behind your question, we may come out with other ideas, if you care to explain it to us ;)

Regards.

What i have done.
Installed nfs-kernel-server and edited the /etc/exports folder. Where  i can connect to the folders just fine no issues.

My issue (kinda hard to explain).
Is that when i mount the folder on another server. I need to link a file (symbolic link) into the mounted folder (which only should have local significance). But i'am not allowed due to permissions. And i would think that if i managed to do so the sym link would be shown on the external server? O.o i have tried to solve it all morning but didn't get far :D

---

