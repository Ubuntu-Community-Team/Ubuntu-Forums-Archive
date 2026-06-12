---
title: "NFS permissions umask"
date: 2011-02-02
forum: General Help
---

### Post by housetier on 2011-02-02
I have a problem with a nfs-mount: I want to mount the nfs-filesystem, so that every user (from a specific group) has write access, i.e. new created files should have permissions like rwxrwxr-- or so...

I tried:
```
sudo mount -t nfs -o umask=002 remoteserver:/tomount/ /mnt/something

```
But I got:
```
mount.nfs: an incorrect mount option was specified

```
As far as I could figure out, umask cannot be applied to nfs-mounts, can someone approve this?

Another way would be to change umask in /etc/profile - which I dont like, because it affects also all permissions in home-folders.

At least it would be possible to use ACLs. But I hope, there is a way avoiding ACLs. So has anybody another solution? Something like a umask on a specific folder or another workaround?

---

### Post by housetier on 2011-02-03
So, I think I solved the problem - and I want to report in short what I did: I change the permissions of the mounted root-folder to:
```
sudo chmod 2774 /mnt/something
```
This should map the permissions of all files in that folder to the same permissions. So everybody, who is in the folder-owners group can read an write files in that folder, I think.

---

### Post by rnerwein on 2011-02-03
> **housetier said:**
> So, I think I solved the problem - and I want to report in short what I did: I change the permissions of the mounted root-folder to:
```
sudo chmod 2774 /mnt/something
```This should map the permissions of all files in that folder to the same permissions. So everybody, who is in the folder-owners group can read an write files in that folder, I think.

hi
i think to give the group an executable bit is not the right way ( security ). you have to see that all uesers - e.g. groups have the same "UID and / or GID" on the client machines as the server get.

have a look at NIS/YP.

ciao

---

