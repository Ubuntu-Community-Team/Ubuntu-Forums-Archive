---
title: "Faild apt-get upgrade attempts"
date: 2009-09-09
forum: General Help
---

### Post by Cardale on 2009-09-09
When I tried to upgrade a few packages I ran into a problem.  3 packages supposed wouldn't upgrade.

The following packages have been kept back:
  linux-image-server linux-restricted-modules-server linux-server
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

What to do?

---

### Post by shylent on 2009-09-09
It's fine really and it does not mean that anything "failed". It is just one of the possible results of apt-get upgrade.  

Now I must tell you that apt-get upgrade will *not* install new packages. Therefore, if the package gains a dependency, it will not get upgraded through apt-get upgrade. You can, for example, run apt-get -s dist-upgrade (-s for a dry-run - nothing will be installed, it will just show you what it is about to do). That will probably do it. If not, you can just install those packages manually through apt-get install _blah_.  There can be other causes for that "held back" state, but this one is the most common.

By the way, if you are unsure about what apt-get is about to do, always use the -s argument. Saved me a ton of trouble, I'm telling you.  

Just to reiterate, "held back" doesn't mean "failed".

---

