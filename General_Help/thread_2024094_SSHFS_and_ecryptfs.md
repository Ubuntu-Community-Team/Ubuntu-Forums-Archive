---
title: "SSHFS and ecryptfs"
date: 2012-07-13
forum: General Help
---

### Post by Seeked on 2012-07-13
Hello all,

I am trying to mount SSHFS and then mount an ecryptfs encrypted directory inside of it.  I have been able to do this with root.  I have added the mounts to fstab with a user option so I can have non-root users mounting them.  Using a non-root user I am able to mount SSHFS and I can mount an ecryptfs directory as long as the ecryptfs directory is not located within the SSHFS mount.  When I try to mount the ecryptfs directory within an SSHFS directory using a non-root use I am presented with an error that there is a misconfiguration.

Anybody have any insight?  I am stumped.

Thank You

---

### Post by Seeked on 2012-07-18
Use enfs instead of eCryptfs.

encfs works in the user space instead of the kernal space by default.

---

