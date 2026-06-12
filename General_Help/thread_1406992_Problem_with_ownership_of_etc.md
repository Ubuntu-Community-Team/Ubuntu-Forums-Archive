---
title: "Problem with ownership of /etc"
date: 2010-02-14
forum: General Help
---

### Post by Nacht on 2010-02-14
I am getting this error:
> sudo: /etc/sudoers is owned by uid 1000, should be 0
Segmentation fault
this is preventing me from doing a variety of things, for example sudo /etc/init.d/privoxy restart

I think the problem is I need to put the owner as root but not sure??

---

### Post by sandyd on 2010-02-14
> **Nacht said:**
> I am getting this error:
this is preventing me from doing a variety of things, for example sudo /etc/init.d/privoxy restart

I think the problem is I need to put the owner as root but not sure??

in recovery mode,
```
chmod 0440 /etc/sudoers
chown root:root /etc/sudoers
```

---

