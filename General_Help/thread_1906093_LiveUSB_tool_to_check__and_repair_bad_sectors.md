---
title: "LiveUSB tool to check  and repair bad sectors?"
date: 2012-01-08
forum: General Help
---

### Post by deckoff on 2012-01-08
I need a tool, that will help me check and repair a hard-disk of a laptop. It has no operating system, and if I boot with a conventional Ubuntu release, and go with fsck or others, the system complains that it cannot read /etc/sudoers.
So, I tool that will let me check and repair that hard-disk. I cannot install Ubuntu, cannot re-partition.

---

### Post by deckoff on 2012-01-09
BUMP!
I managed to boot via USB with DamnSmall Linux.
I found this post [here]("http://superuser.com/questions/66820/full-physical-hd-check"), and run
```
sudo badblocks -wvs /dev/sdx
```.
This command runs for almost a day now, on a 40GB 4200 rpm hard-disk. Is this OK, whould I have to wait even more.
Any help, am I on the right way.

---

