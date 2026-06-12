---
title: "rpcbind and NFS problems in 11.10"
date: 2011-10-15
forum: General Help
---

### Post by Mr. Echo on 2011-10-15
I have a fresh install of Ubuntu 11.10 64bit.  I'm having problems with NFS mounts.  It appears that rpcbind is not starting up when the system boots.  That, in turn, causes statd to fail and the NFS directories refuse to mount.  Can someone verify this?  I tried tracking through the rpcbind startup stuff but my understanding of upstart isn't very good.

As a workaround, I've manually started rpcbind and statd in /etc/rc.local, followed by a mount -at nfs.

My NFS server is still running Ubuntu 10.04.3.

---

### Post by getriebesand on 2011-10-15
Yes, I can confirm that. Im running Kubuntu 11.10 Oneiric Ocelot and rpcbind won't start at boot. I can't find the error in upstart.
All bugfixes I found on the net are already applied to 11.10

Thanks for your work-around.
I've added rpcbind -w to rc.local and all is working like expected now

---

### Post by Mr. Echo on 2011-10-16
Thanks for confirming that.  I guess I will open a bug report.

---

### Post by getriebesand on 2011-10-17
Yes, thats a good idea :) Can you then please give me the bug ID or the link? Then I will vote for it.

---

### Post by Mr. Echo on 2011-10-17
Please look at bug 875471 on launchpad.  Its the same basic problem.  I confirmed the bug so hopefully we'll get some attention.

---

