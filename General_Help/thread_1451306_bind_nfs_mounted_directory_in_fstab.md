---
title: "bind nfs mounted directory in fstab"
date: 2010-04-10
forum: General Help
---

### Post by eisbaer128 on 2010-04-10
I'm using nfs4 for exporting my server directories to all the available computers. In nfs4 all the export will be exported as one large directory tree. 
Now I would like at least all the home directories to show up on the local /home tree of all the computers. The best to do so is using the bind command, but when I try to bind the nfs mounted directory then Ubuntu is not able to boot properly as it looks like it can not resolve the dependencies. This is true for karmic as well as for lucid.

Here the respective part of the /etc/fstab file:

```

server:/                           /mnt    nfs4    _netdev,auto    0       0
/mnt/server/home       /home   none    bind            0       0

```Any idea on how I can create such setup ?

---

