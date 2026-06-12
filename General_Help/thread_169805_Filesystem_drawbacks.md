---
title: "Filesystem drawbacks"
date: 2006-05-03
forum: General Help
---

### Post by Cirrocco on 2006-05-03
I'm trying to decide on a filesystem for my internal storage drives, but I've run into to obstacles.  they each seem to have 1 big drawback.

here's what i've learned so far:
ext2 - no journalling
ext3 - forced e2fsck takes forever, and is manditory after 20 (or whatever) consecutive mounts
reiserfs - crazy long mount times
reiser4 - too new, I don't trust it yet
xfs - my house loses power often, and my UPS is substandard. I can't afford to use this filesystem for it's tendancy to lose data.

I don't know anything about JFS
can someone let me in on it's secret giant glaring fault?
and if there aren't any, I'll likely switch, but I need to know how to label it in the fstab (exact syntax) (ie: /dev/hdx /mount/point/ jfs <options> 0 1 (whatever 0 1 does...))

---

### Post by Ramses de Norre on 2006-05-03
[QUOTE=Cirrocco]
ext3 - forced e2fsck takes forever, and is manditory after 20 (or whatever) consecutive mounts[/QUOTE]
You can turn that off, it's one of the two last numbers in fstab.

---

