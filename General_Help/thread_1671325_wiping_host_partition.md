---
title: "wiping host partition"
date: 2011-01-19
forum: General Help
---

### Post by shacamin on 2011-01-19
Hey there! Quick question which I'm pretty sure I already know the answer to.

A little background: I installed Ubuntu through WUBI to a 30GB partition on my HDD. Since then, my windows partition has become fairly corrupted and will not stay booted for more than a few minutes. In order to fix this, I want to wipe my Windows partition.

Will this delete my Ubuntu partition or any of the data that is saved on it? Is there any way that I can get around this issue, wipe my windows side and keep Ubuntu going?

---

### Post by lisati on 2011-01-19
If you've installed via Wubi, wiping your Windows partition will wipe Ubuntu. There are threads around about migrating a Wubi install to it's own partition.

---

### Post by shacamin on 2011-01-19
Thanks for the quick response. I did a quick search for wubi issues, but I guess I didn't have the correct terminology. I appreciate it!

If I were to do a fresh install and use the migration assistant on the Live CD, would that do the same thing?

---

### Post by bcbc on 2011-01-19
[How to migrate to partition]("http://ubuntuforums.org/showthread.php?t=1519354")

You'll need to create the partitions first.

The only other way is to backup your data, save a list of packages you've installed, and then use that to reinstall.

---

