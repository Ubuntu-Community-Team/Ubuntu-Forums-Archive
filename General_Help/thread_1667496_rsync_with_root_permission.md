---
title: "rsync with root permission ?"
date: 2011-01-14
forum: General Help
---

### Post by garyed on 2011-01-14
I'm trying to use rsync to copy some files between computers that have root permissions. I can use sudo to become root on the computer I'm copying the files from but I still can't get permission from the computer I'm copying the files to. I've got SSH working fine between computers with both user & root so thats not a problem. I want to use rsync in a shell script so I'm trying to figure how to get past the permission thing first. I've been searching tutorials on rsync online but I haven't found anything that works yet.
Any ideas?

---

### Post by Copperblade on 2011-01-14
sudo only works locally--you'll need to do something like sudo rsync /some/dir root@remote:/another/dir

---

### Post by garyed on 2011-01-14
> **Copperblade said:**
> sudo only works locally--you'll need to do something like sudo rsync /some/dir root@remote:/another/dir

Thanks,

That was easy enough.

---

