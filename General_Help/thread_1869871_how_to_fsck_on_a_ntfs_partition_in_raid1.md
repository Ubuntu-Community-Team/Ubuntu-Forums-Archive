---
title: "how to fsck on a ntfs partition in raid1?"
date: 2011-10-26
forum: General Help
---

### Post by andrew.taylor on 2011-10-26
hi all.
how can I run fsck.ntfs on a ntfs array with raid1?
I have these two ntfs partition working together into raid1 .. after a black-out, at boot ubuntu server 11.04 says
 
```
fsck.ntfs not found
error 2 while executing fsck.ntfs for dev/md2p1
```
 
the partition can be auto-mounted as always, but I'm having issues with the vpn and ip forwarding. maybe a file system check would solve the problem ..
 
can anyone help? thanxs.

---

### Post by Mark Phelps on 2011-10-26
You don't run fsck on NTFS partitions; you run CHKDSK -- and you need to do that from MS Windows.

---

