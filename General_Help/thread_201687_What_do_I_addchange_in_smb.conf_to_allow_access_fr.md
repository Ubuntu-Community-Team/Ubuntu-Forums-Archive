---
title: "What do I add/change in smb.conf to allow access from Windows w/o passwd prompt?"
date: 2006-06-22
forum: General Help
---

### Post by KillrBuckeye on 2006-06-22
When I upgraded to Dapper, I forgot to backup my config files.  I had Samba set up to allow access to my Linux shares without prompting Windows users for a username and password.  Now I can't figure out how to do that.  Here is the shares section of my smb.conf that I basically just copied from someone else:

```
[homes]
   comment = Home Directories
   browseable = yes
   public = yes
   writable = yes
   create mask = 0777
   directory mask = 0777
   force user = nobody
   force group = nobody
   guest ok = yes
```

---

### Post by KlausPaiva on 2006-06-22
In the Authentication section, you'll see:

```
####### Authentication #######
security = user
```

Just change the security parameter to:

```
security = share
```

[]'s

---

### Post by KillrBuckeye on 2006-06-22
Thanks!

---

