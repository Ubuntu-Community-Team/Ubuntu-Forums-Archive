---
title: "remaining space warnings - incorrect?"
date: 2010-08-27
forum: General Help
---

### Post by poldie on 2010-08-27
I've got Ubuntu 10.04 64 bit.  Over the last few weeks I get warnings, like when I do a system upgrade, about disk space.  I'm told I have 1.5, 1.8, 2.0 gigs remaining.  But when I use the disk usage analyzer, and then click on preferences to see how much space I have on my main partition (because otherwise it pointlessly lumps in other drives), I can see I have 5 gigs.  

So, do I have 1.8 or 5, and if I have 5, why is it complaining?

---

### Post by arrange on 2010-08-27
Do you mean system upgrade lucid &#8594; maverick, or you mean classic system update (via Update Manager)?

Can you also provide output from the [Terminal](https://help.ubuntu.com/community/GnomeTerminal)?```
df -Th
```

---

### Post by poldie on 2010-08-27
> **arrange said:**
> Do you mean system upgrade lucid &#8594; maverick, or you mean classic system update (via Update Manager)?

Can you also provide output from the [Terminal](https://help.ubuntu.com/community/GnomeTerminal)?```
df -Th
```

OK, that command gives:

Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda1     ext4     66G   61G  1.8G  98% /
none      devtmpfs    2.0G  312K  2.0G   1% /dev
none         tmpfs    2.0G  1.3M  2.0G   1% /dev/shm
none         tmpfs    2.0G  336K  2.0G   1% /var/run
none         tmpfs    2.0G     0  2.0G   0% /var/lock
none         tmpfs    2.0G     0  2.0G   0% /lib/init/rw
none       debugfs     66G   61G  1.8G  98% /var/lib/ureadahead/debugfs

Not sure about all the 2gb ones, but dev/sda1 has 1.8g free which ties up with what I saw earlier (after update manager - the one from system/administration/update manager).

When I go Accessories/disk usage manager, it says:
capacity: 65.3gb 
used: 60.3gb
available 5gb

and edit/preferences gives the same numbers and confirms it's talking about /dev/sda1

So..the bug is in disk usage manager?

---

### Post by arrange on 2010-08-28
Disk Usage Manager might not (just guessing) take into consideration the reserved part of the partition, which by default is 5% of the capacity. Generally I would trust *df* more. ;)

---

### Post by dcstar on 2010-08-28
> **poldie said:**
> 
........
So, do I have 1.8 or 5, and if I have 5, why is it complaining?

Because less than 2% available in a root filesystem is a problem.

---

