---
title: "Problems with Transmission"
date: 2011-02-22
forum: General Help
---

### Post by rlp1938 on 2011-02-22
Transmission keeps bitching about download X being deleted from Demonoid.com. So to do the right thing I tried to upload the torrent file to Demonoid. Apparently Demonoid don't know how to recognise a torrent file. I really don't care about that. What I want to do is stop Transmission bitching about Demonoid not knowing about what I am downloading. I have searched ./config/transmission without finding anything useful. 

Thanks Bob

---

### Post by rlp1938 on 2011-03-08
> **rlp1938 said:**
> Transmission keeps bitching about download X being deleted from Demonoid.com. So to do the right thing I tried to upload the torrent file to Demonoid. Apparently Demonoid don't know how to recognise a torrent file. I really don't care about that. What I want to do is stop Transmission bitching about Demonoid not knowing about what I am downloading. I have searched ./config/transmission without finding anything useful. 

Thanks Bob

Now solved:
apt-get remove transmission-common
apt-get install ktorrent

---

