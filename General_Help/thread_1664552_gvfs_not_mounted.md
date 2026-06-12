---
title: "gvfs not mounted"
date: 2011-01-11
forum: General Help
---

### Post by maxxer on 2011-01-11
Hi.

I've a brand new install of Ubuntu 10.10, with pam_ldap configured.
I've several other clients installed this way working perfectly.
This one won't mount $USER/.gvfs
I've double-checked the directory permissions with the working clients and everything is set correctly.
If I manually run gvfs-fuse-daemon I get the following:
```
$  /usr/lib/gvfs/gvfs-fuse-daemon -v /home/user/.gvfs/
fusermount: mount failed: Operation not permitted

```

the .gvfs directory exists, and has rwx------ permission. Setting to r-x------ results in the above command saying the user has no write permission to the dir.

The user is in the fuse group (even tough the working clients are not!).

What can I check? 
thanks

---

