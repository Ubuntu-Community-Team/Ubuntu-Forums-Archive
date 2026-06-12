---
title: "Mounted file system permissions"
date: 2011-12-31
forum: General Help
---

### Post by grogling on 2011-12-31
I am having trouble with permissions while mounting a CIFS file system located on my OpenMediaVault server.

If I mount it through Nautilus, everything works fine. Unfortunately, that doesn't allow me to access that data in every program, so I am trying to mount using the /etc/fstab file at startup.

For example, I have the below line in fstab:

//192.168.1.11/test  /home/glen/test-folder  cifs  guest,_netdev  0  0

The server is setup so the share is public. Everything created on the server is owned by nobody:nogroup, but when I go into ~/test-folder in Nautilus, some things are marked as read only and I cannot modify or delete them.

---

