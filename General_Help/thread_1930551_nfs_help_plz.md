---
title: "nfs help plz"
date: 2012-02-23
forum: General Help
---

### Post by macele on 2012-02-23
I'm sure I've missed something, but I could use some help. I've discovered that samba from linux -> linux is slow, unless using smbclient which supports async transfers, so I have to use nfs.

My /etc/exports file is as follows:
```
# /etc/exports: the access control list for filesystems which may be exported
#               to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
#
#/mnt           *(rw,async,nohide)
/mnt    10.0.1.0/24(rw,async)
#/mnt/2tb  10.0.1.0/24(rw,async)
#/mnt/250a 10.0.1.0/24(rw,async)
#/mnt/250b  10.0.1.0/24(rw,async)

```

Now as I understand it that should share my /mnt directory with everyone on the 10.0.1.0/24 network. It seems to work except on thing... although I can access the files in /mnt I can't access the directories. The directories show up, but I can't see the contents.

Anybody have any ideas?

---

