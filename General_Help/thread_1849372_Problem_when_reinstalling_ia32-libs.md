---
title: "Problem when reinstalling ia32-libs"
date: 2011-09-24
forum: General Help
---

### Post by BoPe86 on 2011-09-24
Hi! I'm using x64 Ubuntu. Few month ago i accidently messed groups/owners of ALL files from "/" (don't even ask how, it's embarrassing). Instead of re installing system, i have decided to "punish" mu self for stupidity and bring back all the way it should be using Ubuntu installed on "VBox".

But, right now i have a problem that is, for sure, related to things i mentioned. When i try to re install "ia32-libs" (Skype is causing problems so i have to reinstall those libs) i got error message ```
/var/lib/dpkg/info/ia32-libs.postinst: 40: /usr/lib32/gdk-pixbuf-2.0/gdk-pixbuf-query-loaders: Permission denied
```

ls -al of /usr/lib32/gdk-pixbuf-2.0/ is this:
```
total 476
drwxr-xr-x  3 root root   4096 2011-09-24 17:08 .
drwxr-xr-x 53 root root 143360 2011-09-24 17:08 ..
drwxr-xr-x  3 root root     40 2011-09-24 04:44 2.10.0
-rwxr-xr-x  1 root root   9648 2011-04-05 00:40 gdk-pixbuf-query-loaders
```

I have tried to re install gdk-pixbuff-2.0 but no luck :\

What should i do? Please help!

EDIT: Problem was solved after:
chown root:root /lib*/*
chmod a+rx /lib*/ld-* /lib*/*/
chmod -R a+r /lib

---

