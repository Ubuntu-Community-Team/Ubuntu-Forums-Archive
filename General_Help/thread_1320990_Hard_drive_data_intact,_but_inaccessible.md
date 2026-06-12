---
title: "Hard drive data intact, but inaccessible?"
date: 2009-11-09
forum: General Help
---

### Post by gobrien on 2009-11-09
I can't access the date on my second hard drive

/dev/sdb mounted as /mnt/disk ext3 formatted 

Everything was fine before a restart, I can access the information from windows and RIP. It appears to be mounted in 9.10.

Any ideas? Many thanks.

---

### Post by jbrown96 on 2009-11-09
You probably don't want to mount the entire device but a partition. Try /dev/sdb1 instead of /dev/sdb

---

### Post by gobrien on 2009-11-09
I'll give that a go thanks, but something has gone wrong as it's not displaying the drives contents, even though it appears to be mounted.
It's installed to mount the drive automatically on startup, rather than manually, which it appears to do, it just isn't displaying the contents. 
I'm back in vista until this is resolved, it's horrible, help! :)

I noticed ubuntu trying to initiate a disk check during boot, I checked this disk and all is well. I was reluctant to do this as it's 1TB and takes a while.

---

