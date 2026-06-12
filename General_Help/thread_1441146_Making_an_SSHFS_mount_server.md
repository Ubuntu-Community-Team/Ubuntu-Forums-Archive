---
title: "Making an SSHFS mount server"
date: 2010-03-28
forum: General Help
---

### Post by codeking on 2010-03-28
I've been wanting to network my computers together using SSH, but I can't figure out how to create a server for SSHFS.  (I can find out how to mount a remote directory via SSHFS, but not how to serve one.)  I've been scouring Google; I think I must be not looking where I should be.  Could anybody prod me in the right direction?

---

### Post by falconindy on 2010-03-28
sshfs isn't designed for what you want to do. Use nfs instead.

---

### Post by codeking on 2010-03-28
Thanks!  I've gotten NFS set up, but having a [few problems with it]("http://ubuntuforums.org/showthread.php?t=1441501").

---

