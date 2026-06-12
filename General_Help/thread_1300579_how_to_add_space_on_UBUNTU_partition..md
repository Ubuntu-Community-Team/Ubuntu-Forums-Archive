---
title: "how to add space on UBUNTU partition."
date: 2009-10-25
forum: General Help
---

### Post by henryfranz2005 on 2009-10-25
hello I have a (unique) problem. I installed ubuntu on a 2.5gb partition on my hard drive. Afterwards I need a larger space so I wanted to add space on ubuntu partion. How can I accomplish this? thanks! BTW I have no free space on my hard drive but I have free space on my windows partion, Can I get some space there? and transfer it to ubuntu? Thanks!

---

### Post by dv3500ea on 2009-10-25
Boot from the live CD and run system->administration->partition manager
You can then move, resize, reformat etc your partitions.
Shrink your windows partition then grow your ubuntu partition.

---

### Post by P4man on 2009-10-25
Your problem is so unique I guess its the most frequently asked question here :)

Have a look here:
[http://ubuntuforums.org/showthread.php?p=7658271](http://ubuntuforums.org/showthread.php?p=7658271) and
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)

---

### Post by henryfranz2005 on 2009-10-25
lols, well p4man I think I'm wrong sorry. This is a common problem for users installing side-by-side with windows aka wubi install. 

> UPDATE: This bug is being actively worked on. It will definitely be fixed in Karmic. The default once a fix is introduced will be to take (available space - 2.5GB) and use the midpoint. Until the bug is fixed, users must continue to manually select a larger default as explained below.
Reinstalling might be the solution, then move the slider as seen here, thanks to drs305




[IMG]http://ubuntuforums.org/attachment.php?attachmentid=121997&d=1248267874[/IMG]

---

### Post by egalvan on 2009-10-25
> **henryfranz2005 said:**
> ... This is a common problem for users **installing side-by-side** with windows aka **wubi** install. 


Wubi is NOT a "side-by-side" install...
it is installing Linux **INSIDE** Windows, in a dedicated file.

---

### Post by P4man on 2009-10-26
as written above. if you did not do a wubi install, but installed ubuntu "side by side" on its own partition then you can fix it without reinstallation. Check the links.

---

