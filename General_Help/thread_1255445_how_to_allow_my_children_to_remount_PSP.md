---
title: "how to allow my children to remount PSP"
date: 2009-09-01
forum: General Help
---

### Post by fm1234 on 2009-09-01
Hi,
When the PSP is connected to ubuntu, it is mounted automatically in such a way that it behaves as a read-only file system. This is what mount -l reports:

/dev/sdb1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1001,utf8,umask=077,flush)

Yes, even with an rw option there it doesn't work. I can make it work by

sudo mount /dev/sdb1 /media/disk -t vfat -o rw,uid=1001

I don't have time right now to RTFM and I was hoping someone could tell me how to either:

- fix the ubuntu automount
- given them an easy way to remount the PSP without giving them the admin rights

TIA,
Fernando

---

