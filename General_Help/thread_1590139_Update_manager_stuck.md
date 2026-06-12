---
title: "Update manager stuck"
date: 2010-10-07
forum: General Help
---

### Post by lsutiger on 2010-10-07
Verion 10.04. Update manager has been stuck on samba-common overnight. I can not close it by normal means. I am sure I could kill it, but is this wise to do in the middle of an update?


It is important this computer stay live on the network for others to access it's shares.

---

### Post by sikander3786 on 2010-10-07
Not wise definitely. It can and surely will break the system. If it has been left overnight, I think there is no other choice. Is it stuck at configuring samba-common or at downloading?

After quitting you can try to install the missing dependencies via

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

Or Fix Broken in Synaptic Package Manager.

Not a solution but I am unable to find any other workaround in this case.

---

