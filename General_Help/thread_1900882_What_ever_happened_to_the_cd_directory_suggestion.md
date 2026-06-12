---
title: "What ever happened to the cd directory suggestion?"
date: 2011-12-27
forum: General Help
---

### Post by VanJr on 2011-12-27
Yep, old school here. Grew up with AT&T, SCO Xenix/Unix, AIX, HP-UX..

**What ever happened to the directory suggestion prompting when you attempted to *cd* to a directory that was invalid?** For example, in the old days, one may have done:

```
$ cd /usr/spol/mail
```and I would be presented with the following suggestion/hint/question:

```
/usr/spool/mail (Y/n)?
```I sure do miss that feature. **Is there a way to turn that feature on?**

---

### Post by dandnsmith on 2011-12-27
That, along with an apparent version of rm to query if you really wanted to perform the deletion, and several others, were implemented as aliases at the system level.
Look to /etc/bash.bashrc and the man pages for some elaboration.

---

### Post by Frogs Hair on 2011-12-27
I don't remember seeing this on Ubuntu , but I have only been using it since 9.10. I have only seen no such file or directory .

---

### Post by dandnsmith on 2011-12-27
The file is there!
With different distros, you may find a different basic shell is in use, so you may have a different /etc/*.*shrc to configure.
There may/will also be a local version in the individual home folders.

---

### Post by jwbrase on 2011-12-27
> **VanJr said:**
> **What ever happened to the directory suggestion prompting when you attempted to *cd* to a directory that was invalid?**

I think a big part of it is that with tab completion people don't really miss it.

---

