---
title: "Are diffs supported when upgrading?"
date: 2009-08-13
forum: General Help
---

### Post by feffer on 2009-08-13
We have limited bandwidth. I've heard that apt-get supports diffs (downloads of just the changed parts of the package) at least in debian. Does Ubuntu support package diffs in upgrades? If so, how do I do it?

thx,
feffer

---

### Post by starcraft.man on 2009-08-13
From the man page for apt-get:

```
  --diff-only, --dsc-only, --tar-only
           Download only the diff, dsc, or tar file of a source archive. Configuration Item: APT::Get::Diff-Only, APT::Get::Dsc-Only, and APT::Get::Tar-Only.

```

So yes, apt-get apparently does diff, just append that after command before packages as with all options. Why wouldn't you think Ubuntu supported it though? We use the same apt-get to my knowledge, it's not like we turn it into something else. Hope that works for ya.

---

### Post by feffer on 2009-08-13
Actually I read that, but was still confused. Don't packages usually come from the non-source section of the repo? So If I use those options, I should comment out the non-source repo addresses to force it from the source section? 

Also I saw this [comment](http://www.osnews.com/thread?222107) concerning the package list that apt-get update fetches. I realize the update list is different from the packages themselves, but it made me wonder if the Ubuntu repos could prevent source package diffing too.

Sorry to be persistent about this, but we get nasty notes from our rural ISP when we exceed their stingy limits.

thx,
feffer

---

