---
title: "Shared disk with ACL, not working for copied files"
date: 2010-06-13
forum: General Help
---

### Post by jazzgossen on 2010-06-13
I have two users on my system, and a shared drive (mounted at /mnt/shared) that should be read-writable for all users in the "locals" group. I have set up ACL so that everything works as it should for newly created files.

However, when I *copy* a file from my home directory, with user/group myself/myself and permissions rw-r--r--, the copy in the shared directory is still not group writable, although it does get assigned the "locals" group.

How can I change this behaviour, so that also copied files get rw-rw-r-- permissions, regardless of their original permissions?

---

### Post by sisco311 on 2010-06-17
> **jazzgossen said:**
> 
How can I change this behaviour, so that also copied files get rw-rw-r-- permissions, regardless of their original permissions?

I don't think that's possible.

But, you can use bindfs to (re)mount the partition/directory with different ownership and permissions. The ownership and permissions will apply to all files from the directory. 

e.g.:
```
sudo bindfs -o perms=0700,mirror-only=@locals /media/shared /media/shared
```

[thread=1460472]HowTo: Create a shared directory for local users (with bindfs).[/thread]

---

