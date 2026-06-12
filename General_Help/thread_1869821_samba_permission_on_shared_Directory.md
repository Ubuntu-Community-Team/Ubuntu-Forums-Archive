---
title: "samba permission on shared Directory"
date: 2011-10-26
forum: General Help
---

### Post by b-boy on 2011-10-26
Hi 

I have a samba share **Docs** and sub folders Day1 Day2. I have managed to give a user1 write permissions and user2 read permission. But what I need is for user2 to have write permission on 1 Day1 and read for any other Directory. user1 permission are fine.

my smb.conf is

```
[Docs]
        comment = Docs
        path = /home/admin/Docs
        write list = user1
        browseable = yes
        guest ok = no
```


alternatively how can I make samba use files system permission? as my above issue can easily be solved if samba uses file system permission.

---

