---
title: "Help Recovering Data"
date: 2006-04-01
forum: General Help
---

### Post by double_d on 2006-04-01
Me, being the noob that I am, wanted to label a partition.
So, I saw that parted had a "mklabel" command, and thinking that it would label the partition, ran it.
Well, I then restarted to let the changes take effect.
The partition got erased, but I read on the internet that it's possible to get it back.
Can anybody help me?
EDIT : Doesn't matter anymore, I'll just redownload it all.  It's pretty much all replacable.

---

### Post by dcstar on 2006-04-02
[QUOTE=double_d]Me, being the noob that I am, wanted to label a partition.
So, I saw that parted had a "mklabel" command, and thinking that it would label the partition, ran it.
Well, I then restarted to let the changes take effect.
The partition got erased, but I read on the internet that it's possible to get it back.
Can anybody help me?
EDIT : Doesn't matter anymore, I'll just redownload it all.  It's pretty much all replacable.[/QUOTE]
If you want to label EXT2 partitions, there are tools to do this, have a look here:

[http://ubuntuforums.org/showthread.php?t=139535](http://ubuntuforums.org/showthread.php?t=139535)

---

### Post by kikkum on 2006-04-02
Tip for if you're having second thoughts: check out gpart. This tool scans your disk for lost (or still existing, it doesn't really matter: it just scans) partitions and gives you it's positions on the disk so you can then use fdisk to rebuild a correct partition table, effectively restoring all your deleted partitions.

---

