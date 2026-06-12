---
title: "Can I force NFSv3?"
date: 2011-03-25
forum: General Help
---

### Post by Tipo on 2011-03-25
Hello,

I have an NFS server (which I don't have admin access to) which is advertising a share as both NFSv4 and NFSv3. Ubuntu's mounting it by default at NFSv4, which is causing some problems (I don't think NFSv4 is configured properly on the server). So I'd like to force my client machine to mount via NFSv3.

It's currently using autofs to get the share, but it's pulling mount options from LDAP, so I can't just throw a nfsvers=3 into the mount options in the autofs config file.

On Fedora, I'm able to edit two variables in /etc/nfsmount.conf to make this happen: 

```

Defaultvers=3
Nfsvers=3

```

I see that Ubuntu doesn't have this config file -- is there an equivalent one that I can edit (already tried /etc/default/nfs-common), or another way to force NFSv3?

Thanks in advance.

---

