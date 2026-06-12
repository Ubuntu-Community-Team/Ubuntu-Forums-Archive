---
title: "sshfs over VPN breaks when connection lost?"
date: 2010-12-02
forum: General Help
---

### Post by BrettThomas on 2010-12-02
Hey, I've noticed some awkward behavior when mounting remote directories - wondering if I'm doing something wrong or it's a bug. 

I am mounting a remote directory using sshfs, over VPN. If the VPN connection is lost, the directory obviously can't be read. But, when I try to "ls" in its parent directory, the command just stalls. No error messages, and ctrl-d, ctrl-c, ctrl-z don't do anything. Anybody seen that?

The command I ran to mount the directory was: 
```
sshfs -o workaround=rename bt@example.com:/dir1 /dir1
```

---

### Post by TSJason on 2010-12-02
This is a caveat when using networked filesystems over routed connections. The best thing to do (if it can't auto re-establish the connection) it to do a lazy unmount and wait a few minutes for the system to recover. If there are any applications which are locking the location they may have to be forcibly killed. Even just having a terminal window open and cd'd into that location will cause a lock.

Lazy umount just uses the "-l" flag. 

```
umount -l /dir1
```

---

### Post by czr114 on 2010-12-02
The command in the parent stalls because the child object is timing out.

You can unmount as suggested, or create the mount directory inside of a local directory inside of wherever it is now. This will isolate the network mount point. It's a kludge, but it works.

---

