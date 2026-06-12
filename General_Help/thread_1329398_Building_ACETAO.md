---
title: "Building ACE/TAO"
date: 2009-11-17
forum: General Help
---

### Post by beleriand on 2009-11-17
I'm wanting to build ACE/TAO and study the examples for purposes of learning.  I have been surprised at how difficult this is to do.  In fact, I've tried several versions of ACE/TAO on different versions of Ubuntu, and still haven't found a working combination.  Has anyone else been able to do this?

Thanks!

---

### Post by Zoot7 on 2009-11-23
What kind of package is that you're trying to build? Have you a link?

A good command for building packages from sources is
```
sudo apt-get build-dep <package name>
```
That pulls in all the build dependencies needed.

---

