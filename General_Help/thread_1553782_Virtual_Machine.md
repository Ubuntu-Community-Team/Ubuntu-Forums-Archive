---
title: "Virtual Machine"
date: 2010-08-15
forum: General Help
---

### Post by gavdari on 2010-08-15
I'm using Ubuntu Lucid as the host OS and Windows XP SP3 as the guest one. Is it possible to share an entire hard drive with the guest OS?

---

### Post by sdennie on 2010-08-15
I don't think it's possible to do that if both the host and guest are aware of the drive at the same time.  I might be wrong but, the host kernel probably wouldn't be pleased about the guest fiddling with things on the disk.  However, the guest can certainly mount a raw partition.  You can also export things from the host via Samba, NFS or, with something like the built in VirtualBox shared folders.

---

### Post by Ginsu543 on 2010-08-15
I don't think you can share an entire drive, but what you can do is create a partition as large as you want, and then create a shared folder (by itself) in that partition. Once you've done that on the Ubuntu/VirtualBox-side, you can map that shared folder as a drive inside Windows. As far as Windows is concerned, that drive will be as large as the shared folder is, which can grow as large as the partition is.

---

