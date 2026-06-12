---
title: "NFS mount at startup fails after upgrade to 11.04"
date: 2011-05-22
forum: General Help
---

### Post by cheuschober on 2011-05-22
Hi,

I recently upgraded one of my servers to 11.04 and was surprised to see that my NFSv3 share was no longer mounting at boot (outlined in fstab).

It's important to note that, NFS isn't exactly broken, *mount -a* still works and will bring up the share without error, but for whatever reason, the fstab entry no longer triggers a mount.

The server does not use network manager to manage the network devices, preferring /etc/network/interfaces.

Relevant fstab line is:
```
ser.ver:/sh/are /local/dir nfs rw,intr,rsize=8192,wsize=8192,timeo=14,_netdev
```

I realize that I probably could use autofs but that application has given me more headaches than salvation in the past (when it gets into an inconsistent state it gets in *hard*), so I'd like to avoid it and stick with the static mounts.

Any help or enlightenment would be appreciated.

Warm regards,
C

---

