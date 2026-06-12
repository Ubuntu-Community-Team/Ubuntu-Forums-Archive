---
title: "How to delete GRUB inputs?"
date: 2010-11-27
forum: General Help
---

### Post by NeverHide on 2010-11-27
When i boot and GRUB loads there are too many options for ubuntu.
There are like 7 different ububt options(i think it's for different kernels) and last the windows partition.
Is it possible to get rid of some of the old kernel options?and if yes how?

---

### Post by Enigmapond on 2010-11-27
The easy way to do this would be to install ubuntu-tweak. It has a function to purge all other kernels except for what you want to keep and also a plethora of other very useful things.

---

### Post by sikander3786 on 2010-11-27
You can remove older kernels following this guide. (courtesy of drs305)

[http://ubuntuforums.org/showthread.php?t=1587462](http://ubuntuforums.org/showthread.php?t=1587462)

Remember, it is advised that you keep at least one older kernel so that if you run into problems later, you can boot your previous kernel and diagnose/solve the problem.

Good Luck!

---

### Post by wilee-nilee on 2010-11-27
Here is a link check it out and the signature of the author for all thing grub all the time.;)
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

As Elmer Fudd says be vwery, vwery careful.

---

### Post by drdread on 2010-11-27
for the newbs the best way is to install ubuntu tweak via software centre
great application!

---

### Post by pastalavista on 2010-11-27
Open Synaptic Package Manager and quick-search for "linux-image". From the results, mark for complete removal all but the latest version. The older kernels won't appear in grub after they're removed/uninstalled.

---

