---
title: "How to let &quot;mount&quot; cmd auto-create mount folder if necessary"
date: 2010-12-28
forum: General Help
---

### Post by pstein on 2010-12-28
Normally I can mount new partitions by a cmd like
 
mount /dev/sdb1 /mnt/sdb1
 
therefore the folder /mnt/sdb1 must exist.
I always forget to create it and have to restart again with
 
sudo mkdir /mnt/sdb1
 
Isn't there an additional flag which let me auto-create the mount point /mnt/sdb1 (only if necessary)? Something like
 
 
mount /dev/sdb1 -autocreateifnecessary /mnt/sdb1
 
Peter

---

### Post by lungten on 2010-12-28
AFAIK, mount command doesn't have any such option. Your only option might be to use automounter which should be installed by default if you are running Ubuntu.

---

