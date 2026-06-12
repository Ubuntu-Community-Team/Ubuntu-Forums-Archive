---
title: "2 seperate users accessing network folder on 1 computer"
date: 2010-08-08
forum: General Help
---

### Post by dabbi2000 on 2010-08-08
I've just added my wife as a seperate user on my desktop and have a question about shared network folders.

So /etc/fstab mounts network folders from a second computer and until today I've mounted them to /home/David/NetworkData

This of course means that when my wife logs in she won't see them since they're not mounted to her home folder. So what folder should I use and what tricks so that we both have it visible and accessible in Places from the top menu?




Oh and please notice I am not using Samba and that's not what I want to do!

---

### Post by AlphaLexman on 2010-08-08
> **dabbi2000 said:**
> I've mounted them to /home/David/NetworkData

This of course means that when my wife logs in she won't see them since they're not mounted to her home folder. So what folder should I use and what tricks so that we both have it visible and accessible in Places from the top menu?

She could just make a 'soft link' to the mount point for NetworkData like this:
```
ln -s /home/David/NetworkData/ /home/wifey/NetworkData/
```
Replace 'wifey' with her username.

---

### Post by dabbi2000 on 2010-08-08
thx... guess I was a bit impatient, after some homework this is how I did it:


1) added me and wife to group "users"

2) mounted network folders to /mnt/NetworkFolder

3) changed permission for folder so that group "users" has r/w access

4) made a symlink in each of our home folders:
/home/david/NetworkFolder (linked)
/home/wife/NetworkFolder (linked)

---

