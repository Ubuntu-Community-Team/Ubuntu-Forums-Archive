---
title: "delay start of 1 init.d script"
date: 2011-11-15
forum: General Help
---

### Post by brodos1 on 2011-11-15
Hi
I have a Ubuntu running transmission-daemon (bittorrent)
I have a nfs mount that is mounted in fstab, but transmission-daemon starts before nfs share is mounted.

The way I understand it the /etc/init.d/transmission-daemon script starts the client at boot.

I am looking for a way to delay the execution of the init.d script for 2-3 minutes.

Any help is appriciated :D

---

