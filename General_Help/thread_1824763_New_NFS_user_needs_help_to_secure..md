---
title: "New NFS user needs help to secure."
date: 2011-08-14
forum: General Help
---

### Post by Kissell on 2011-08-14
I recently started using NFS on a Ubuntu server, followed an easy setup guide, worked great.  In many cases it seems faster than SMB and VMware can see it as network attached storage.  Awesome.  

Unfortunately, it is really insecure, my /etc/exports file is like this:
> /data 192.168.1.0/24(rw,insecure,no_root_squash,async,no_subtree_check)

So basically anyone on the network can delete anything on the share without a password.  However, any changes I make to the exports file seem to make it not work anymore.  

I've tried changing the network to a single host, I've tried changing "rw" to "ro" and even removing "insecure" but everytime I make a change and then run "exportfs -a" I can no longer access the NFS share until I put it back to the way I have it listed here. :(

---

