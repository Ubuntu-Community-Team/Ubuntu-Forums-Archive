---
title: "APT : can it recognize manually installed software"
date: 2012-04-08
forum: General Help
---

### Post by coffeetrinker on 2012-04-08
Hi, all!

The question is the following: is there any way to make APT package manager to find the software, that was installed without using apt-get (for example, directly compiled from source)?

---

### Post by roelforg on 2012-04-08
apt is a frontend for dpkg
So you're asking how to create a deb
and you're asking about running a private deb repo
Cleared it up?

---

### Post by cody1233 on 2012-04-08
I think it can, but not with everything.  If you install a dependency with a tar.gz file, it should be fulfilled most of the time, but with some frontends it doesn't like to work.

---

### Post by roelforg on 2012-04-08
> **cody1233 said:**
> I think it can, but not with everything.  If you install a dependency with a tar.gz file, it should be fulfilled most of the time, but with some frontends it doesn't like to work.

As long as i feed it .deb
dpkg keeps the list

syntax:
```

sudo dpkg -i /path/to/file.deb

```

---

### Post by cody1233 on 2012-04-08
yeah

---

