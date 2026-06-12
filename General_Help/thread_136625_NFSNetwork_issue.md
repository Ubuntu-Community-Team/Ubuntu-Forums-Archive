---
title: "NFS/Network issue"
date: 2006-02-26
forum: General Help
---

### Post by poctob on 2006-02-26
Hi, I got an issue with NFS shares after latest upgrade :
I have two PCs that both run Breezy
192.168.1.102 Server
192.168.1.106 Client
One is NFS sever with two shares
here is a /etc/exports:

#/etc/exports: the access control list for filesystems which may be exported
#		to NFS clients.  See exports(5).
/home/alex/ 192.168.1.106(rw,sync)

/usr/backups/ 192.168.1.106(rw,sync) 

Both shares have same owner and permissions, I can mount first share just fine on the client machine, second share I get:
mount 192.168.1.102:/usr/backups/ failed, reason given by server: Permission denied

Even more I cannot ping my client from the server, I get destination host unreachable error.  I cannot ssh into client from server with the same error, but I can ssh into server from the client, then while still logged in through ssh I can ping and ssh back into the client with no problems.  Still can't mount second share though.  Also I have an XP box that pings both ways with client and server without any issues. Any takers?

---

### Post by poctob on 2006-02-26
I got it resolved, multiple interfaces were conflicting.

---

