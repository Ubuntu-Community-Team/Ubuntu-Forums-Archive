---
title: "mountall hangs"
date: 2012-04-25
forum: General Help
---

### Post by graemev on 2012-04-25
I recently changed my /etc/fstab :

I used to do NFS mounts from a Debian box, but I changed to NAS .

When I rebooted, the boot hung.

It looks to me like upstart is doing mountall  too early in boot ... we don't have enough networking up to allow dns lookups.

This was a classic Unix bug many years ago. The fix was to do mount -a with options to not 
mount NFS (or RFS or other remote fs) mounts .... then much later it did a mount -a WITH NFS ... has this reoccurred with ubuntu?

---

