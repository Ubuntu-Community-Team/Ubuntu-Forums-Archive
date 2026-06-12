---
title: "external drive and suspend problem"
date: 2010-07-14
forum: General Help
---

### Post by dbinder101 on 2010-07-14
I have an external USB hard drive attached to my Ubuntu (10.4) netbook. Because I needed to have certain permissions for this external drive (running Squeezebox Server, for those familiar with the product), I mounted the drive using the following entry in the fstab file:

/dev/sdd1 /musicdrive ntfs rw,user,umask=027,uid=501,gid=502 0 0

This works great EXCEPT: When the netbook goes into suspend mode and then wakes up, the mounted drive is no longer available, even though df -k still shows it as an entry. 

Is there a way I can set up the hard drive so that suspend/wake-up will not affect accessibility to the files on the external drive? Should my fstab entry be changed?

Thank you.

---

