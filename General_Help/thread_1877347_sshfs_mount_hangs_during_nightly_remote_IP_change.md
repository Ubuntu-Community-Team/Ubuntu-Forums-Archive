---
title: "sshfs mount hangs during nightly remote IP change"
date: 2011-11-07
forum: General Help
---

### Post by blausand on 2011-11-07
My permanent mount of:
```
sshfs#me@myserver.dyndns.org:/my/remote/path /media/myLocalName fuse.sshfs rw,noexec,nosu
id,nodev,max_read=65536,user=me 0 0
```
works fine using fstab and some public key copied to the server.
howver, every night when the remote machine is receiving a new IP from the ISP, any thread trying to access /media/myLocalName on my machine **hangs** for quite a while. Although they get back after a few minutes or so,

i think this is not graceful. 
Nautilus/Shell/Applications should not hang on this at all.
The user should receive a notification on this event. 

Don't hesitate to ask for more details if necessary.
Ubuntu 10.04 (on BOTH machines).

---

