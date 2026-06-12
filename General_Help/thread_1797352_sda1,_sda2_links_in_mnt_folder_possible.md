---
title: "sda1, sda2 links in mnt folder possible?"
date: 2011-07-04
forum: General Help
---

### Post by rng on 2011-07-04
Ubuntu mounts all partitions in /media/partiton-label folders. 

Can I make links named sda1, sda2 etc in /mnt folder which point to the partitions mounted in /media folder? 

Also can there be a script which automatically creates these links?

Sometimes it is easier to remember and type /mnt/sda1 etc rather than /media/partition-label.

---

### Post by nzjethro on 2011-07-04
You could use the "ln" command to create a symbolic link. For example:

```
sudo ln /mnt/sda1 /where/you/want/link
```

You could also create a script that will do this for all devices in /mnt/, and then execute this script on start-up (but my scripting isn't good enough to tell you how :P).

---

