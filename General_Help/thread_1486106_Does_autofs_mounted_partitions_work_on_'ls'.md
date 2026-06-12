---
title: "Does autofs mounted partitions work on 'ls'"
date: 2010-05-17
forum: General Help
---

### Post by foobar66 on 2010-05-17
I have got 2 automount partitions set uo via autofs.

After a reboot, the partitions are not mounted.

When I do:

> cd /partition

Then I can see that the partition gets mounted by the automounter.

However, when I do (after a clean reboot):

> ls /partition

Then the partition does not get mounted.

Is this a normal condition? I.e. does one actually have to "cd" into the directory?

---

