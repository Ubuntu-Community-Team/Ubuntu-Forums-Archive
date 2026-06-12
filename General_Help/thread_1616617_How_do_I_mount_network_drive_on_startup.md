---
title: "How do I mount network drive on startup"
date: 2010-11-08
forum: General Help
---

### Post by tehpwnerer1918 on 2010-11-08
I work at a school where we are experimenting with Ubuntu 10.10. On our Windows machines, when the users sign in, their "U:" drive automatically mounts up so that can access their network shared storage. Is there a way to set this up in Linux so it automounts, rather than them have to go and find it out on the network every time? Thanks in advance.

---

### Post by nothingspecial on 2010-11-08
If you have ssh you can use sshfs and fstab

Read this

[https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)

---

### Post by dcstar on 2010-11-09
> **tehpwnerer1918 said:**
> I work at a school where we are experimenting with Ubuntu 10.10. On our Windows machines, when the users sign in, their "U:" drive automatically mounts up so that can access their network shared storage. Is there a way to set this up in Linux so it automounts, rather than them have to go and find it out on the network every time? Thanks in advance.

You make an entry in the /etc/fstab file. Search for details of mounting network shares.

---

