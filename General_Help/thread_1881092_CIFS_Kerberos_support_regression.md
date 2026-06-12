---
title: "CIFS Kerberos support regression?"
date: 2011-11-14
forum: General Help
---

### Post by billc.cn on 2011-11-14
(I want to be sure that this is a bug before I post it.)

I want to mount a Windows file share using Kerberos authentication. The command I used is 
```

sudo mount -t cifs -o sec=krb5i,user=bc //host-name-in-domain//share-name mount-point

```but this only returns
```

mount error(126): Required key not available
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

```However, I know this command should work, so I set cifsFYI level to 7 and I got this interesting line from dmsg:
```

[ 2611.958585] /build/buildd/linux-3.0.0/fs/cifs/cifs_spnego.c: key description = ver=0x2;host=b*****e;ip6=2001:******;sec=krb5;uid=0x0;creduid=0x0;user=bc;pid=0x1405

```Obviously, creduid should be my uid (1000) instead of 0. To verify that this is the problem, I did kinit for root and was able to mount with the same command successfully. It also works if I add "uid=1000" to the mount options, and modify the "request-key.conf" so cifs.upcall uses the uid as opposed to creduid.

Thus everything is working except the kernel routine that calculates the creduid argument. Is there anyone else having a similar problem? Can anyone check if this is a bug?

---

