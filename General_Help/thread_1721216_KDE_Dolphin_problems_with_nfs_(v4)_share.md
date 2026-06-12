---
title: "KDE Dolphin problems with nfs (v4) share"
date: 2011-04-04
forum: General Help
---

### Post by umsorg on 2011-04-04
I just started to use NFSv4, but Dolphin seems to have problems with it. For example if I copy something from local partition to the nfs partition dolphin stops to response. I cannot launch another dolphin or browse the current dolphin. After copying is completed the dolphin starts to work again. I also have cifs partitions via samba, but with those I don't have this problem. Something wrong with my NFS configuration maybe?

```
/export         192.168.0.0/24(rw,fsid=0,no_subtree_check,async,no_root_squash)
/export/alpha   192.168.0.0/24(rw,no_subtree_check,async,nohide,no_root_squash)
/export/beta   192.168.0.0/24(rw,no_subtree_check,async,nohide,no_root_squash)
/export/gamma   192.168.0.0/24(rw,no_subtree_check,async,nohide,no_root_squash)
/export/delta   192.168.0.0/24(rw,no_subtree_check,async,nohide,no_root_squash)
```

---

### Post by SeijiSensei on 2011-04-04
Try adding "rsize=65536,wsize=65536" to the /etc/fstab entries for the mounted filesystems on the client.

---

