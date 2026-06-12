---
title: "Can't access files in mounted Krb5 NFS4 share"
date: 2009-06-28
forum: General Help
---

### Post by rosskouk on 2009-06-28
Hi,

I'm hoping someone can shed some light on an NFS problem...

I've setup NFS4 + krb5 on ubuntu hardy, however although I can mount a share on the client I can only access it as root.

I've read up on idmapd and it seems to be mapping UIDs properly, an ls -l shows the mounted directory is owned by my local user on the client machine, but every time I try to access it as my normal user I get a Permission Denied error. If I become root via sudo -i, I can access the share with no problem.

Can anyone point me in the right direction?

Thanks,
Ross.

---

