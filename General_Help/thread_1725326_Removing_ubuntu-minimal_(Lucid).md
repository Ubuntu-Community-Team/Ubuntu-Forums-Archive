---
title: "Removing ubuntu-minimal? (Lucid)"
date: 2011-04-09
forum: General Help
---

### Post by Kopachris on 2011-04-09
I'm running 10.04 64-bit, and I want to install e4rat.  Unfortunately, the 64-bit .deb file from Sourceforge conflicts with ureadahead.  Removing ureadahead also removes ubuntu-minimal.  Will I be fine removing ubuntu-minimal to install e4rat?

EDIT: Looks like it *should* be fine, since it's only a meta-package.  I'd still like someone to confirm that it won't mess up regular updates before I do it, though.

---

### Post by TeoBigusGeekus on 2011-04-09
According to [this]("http://packages.ubuntu.com/hardy/ubuntu-minimal"), I'd rather not.
The page is about hardy, but I couldn't find anything newer...

---

### Post by mcduck on 2011-04-09
Removing that metapackage *should* be safe considering normal updates, but you'd definitely have to reinstall it if you wanted to upgrade to a new Ubuntu release.

---

