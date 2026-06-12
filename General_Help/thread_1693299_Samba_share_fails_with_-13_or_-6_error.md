---
title: "Samba share fails with -13 or -6 error"
date: 2011-02-22
forum: General Help
---

### Post by KLStringer on 2011-02-22
I'm trying to setup a share from one Ubuntu server to another using:

```
mount.cifs //%IPADDRESS%/SHARE/SHARE /loca/mount/point -o user=user,pass=password
```which gives me  "cifs vfs: cifs_mount failed w/return code -6"

When I try it w/o the user & password options I'm prompted for the password which gives me "cifs vfs: cifs_mount failed w/return code -13"

I know this is a simple problem but I just can't seam to figure it out.

---

