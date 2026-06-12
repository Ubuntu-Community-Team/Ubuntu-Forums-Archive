---
title: "where does nautilus store its &quot;sharing options&quot; information?"
date: 2009-12-23
forum: General Help
---

### Post by forumguy on 2009-12-23
I enabled a folder to be shared by right-clicking the folder in Nautilus and choosing to share it with "sharing options" from the menu. The share is through samba.

I was wondering where this share information is stored? It doesn't seem to update /etc/samba/smb.conf . I am wondering because I'd like to set some specific options about a particular share.


Thanks in advance!

---

### Post by dcstar on 2009-12-23
> **forumguy said:**
> I enabled a folder to be shared by right-clicking the folder in Nautilus and choosing to share it with "sharing options" from the menu. The share is through samba.

I was wondering where this share information is stored? It doesn't seem to update /etc/samba/smb.conf . I am wondering because I'd like to set some specific options about a particular share.


/var/lib/samba/usershares

---

### Post by Morbius1 on 2009-12-23
You can also view the "share definition" by issuing the following command: **net usershare info** or **sudo net usershare info** depending on how or who set the share.

> I am wondering because I'd like to set some specific options about a particular share.Can't be done. The one downside of nautilus-share is that all shares are global. You can set one share to allow guest access and another to require authentication for example but you can't set one share to allow access to John without also allowing access to Mary.

For that kind of share specific control you need to use "Classic" Samba. 
shares-admin from the Terminal will allow you to create a classic share definition in smb.conf.

---

### Post by forumguy on 2009-12-23
thanks for the info, working the way I want it to now!

---

