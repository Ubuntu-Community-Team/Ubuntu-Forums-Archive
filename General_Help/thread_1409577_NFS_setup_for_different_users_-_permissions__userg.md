---
title: "NFS setup for different users - permissions / user:group / sticky-bit / umask ?"
date: 2010-02-17
forum: General Help
---

### Post by Master One on 2010-02-17
What is the best way for a NFS setup, if different users are supposed to be able to access (read/write/create) the same files?

My guess is, that besides the users having to exist on the server, there should be a common group (like "share"), the NFS share has to be owned by someuser:share with the group-sticky-bit set (so that new files are created with the group "share"), and the umask has to be modified on all computers accessing the NFS share, so that new files are created with read/write permissions for the owner & group. Is this the right approach?

Looks rather clumsy. Any better idea?

---

### Post by cariboo on 2010-02-18
I don't know if [this]("https://help.ubuntu.com/community/SettingUpNFSHowTo")  is what you are looking for.

---

### Post by Master One on 2010-02-18
> **cariboo907 said:**
> I don't know if [this]("https://help.ubuntu.com/community/SettingUpNFSHowTo")  is what you are looking for.
That's the page I have used to setup NFS, but it does not tell anything about the configuration for the described scenario.

In a normal NFS setup the users can just access their own files on the share, and that's it. But that way can not be used for actual file-sharing, of two users can not access (read/write/delete/create) a file the same way.

---

