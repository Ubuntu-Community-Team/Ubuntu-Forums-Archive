---
title: "help with dd"
date: 2012-07-14
forum: General Help
---

### Post by orange_roughy on 2012-07-14
Hi,

I have home on its own partition. I'm trying to clone this to a new machine and use it as the home directory there. This is what I've done:

1. Create same user on all systems, and make sure it's got the same uid/group on all (my lame attempt to keep permissions working across systems)

2. Edit new machine's partition home is /dev/sda2.

3. ```
dd if=/dev/sdc2 of=/dev/sda2 bs=512k conv=notrun,noerror
``` This works.

But when I boot the new machines, I'm told that home/ cannot be mounted. One of the partitions (I think it's home, not sure) doesn't start on a partition boundary.

All the tutorials I read (and I've read many) just tell you to use dd to copy the partition. They don't say anything else.

What should I do?

thanks,
orange_roughy

---

