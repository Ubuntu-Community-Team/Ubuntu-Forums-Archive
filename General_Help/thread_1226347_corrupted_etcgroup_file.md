---
title: "corrupted /etc/group file"
date: 2009-07-29
forum: General Help
---

### Post by dmazzone on 2009-07-29
OK so I go to boot up my HP dv4000 laptop running Ubuntu 9.04 32bit and I find that I can't shutdown, sudo, or anything with admin privelage. I look at my /etc/group file find it only contains three entries the only one I remember is root (should have saved it). 

I fixed it by copying my /var/backup/group.bak which fixed most of my problems. However, now policykit is all messed up. I manually added my user to do most things, I just cannot get access to the Users & Groups program form Admin -> Users & Groups.

Anyone have a clue why this happened in the first place or how to restore my authorizations?

---

### Post by Zill on 2009-07-29
This *may* be related to [bug #240437]("https://bugs.launchpad.net/ubuntu/+source/liboobs/+bug/240437").

If some kind 9.04 user will post their working /etc/group file then you should be able to use this to compare with yours. (Sorry but I only have 6.06 and 8.04!).

---

### Post by michy99 on 2009-07-29
When you restore your group file, you need to restore gshadow also. Probably a good idea to restore passwd and shadow at the same time.

---

### Post by dmazzone on 2009-07-30
Do you think restoring /etc/group /etc/shadow and /etc/passwd from /var/backups will suffice? 

Also what is gshadow?

---

### Post by Zill on 2009-07-30
> **dmazzone said:**
> Do you think restoring /etc/group /etc/shadow and /etc/passwd from /var/backups will suffice?
Don't know - but it's worth a try :-)
> **dmazzone said:**
> Also what is gshadow?
```
man gshadow
```

ps.  I recommend you *always* make a separate backup copy of these files *before* changing them!

---

