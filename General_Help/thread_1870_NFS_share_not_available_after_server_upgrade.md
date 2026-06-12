---
title: "NFS share not available after server upgrade"
date: 2004-10-23
forum: General Help
---

### Post by ming0 on 2004-10-23
I did the dist upgrade thingy (as described in the wiki) on my server, and now all my clients can't access the nfs share that I had exported. I tried rebooting the server and the clients, but I get the same error no matter what. I don't have the server firewalled or anything... The error is as follows:
 
dean@dim:~ $ mount /mnt/net/
mount: RPC: Remote system error - Connection refused
 
I don't know what to do! I haven't changed any settings on the server, just upgraded.
 
Thanks,
 
Dean

Note: all servers and clients are running ubuntu!

---

### Post by ming0 on 2004-10-26
This solved it!

[http://www.ubuntulinux.org/support/documentation/faq/nfs-server/view?searchterm=nfs](http://www.ubuntulinux.org/support/documentation/faq/nfs-server/view?searchterm=nfs)

They made some changes to some config files after the update :study:

---

