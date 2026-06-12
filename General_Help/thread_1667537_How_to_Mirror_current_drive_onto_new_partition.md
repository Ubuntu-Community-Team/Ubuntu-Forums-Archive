---
title: "How to Mirror current drive onto new partition"
date: 2011-01-15
forum: General Help
---

### Post by Hunter Technologies on 2011-01-15
I have a problem with my invidia graphics card and each time i load the "recommended" drivers my machine freezes during the boot process at checking battery state.  I have went through this numerous times.  I now have ubuntu setup as a like it and it has taken a substantial amount of time.  I would like to revisit the invidia card issue but i dont want to lose current settings.  So the idea is to mirror my current setup on a separate partition that i can experiment on without fear of losing everything and having to start over.

---

### Post by Copperblade on 2011-01-15
If you want to mirror your whole system you can use `rsync -axH --numeric-ids` for each mounted filesystem to make a duplicate of your data.

--

Ok I read your question again.  I've done system replication with rsync as above many times, however if you have multiple partitions it can get complicated.  You will have to do the above and then:

[LIST=1]
[*]Add a grub menu item for your other copy
[*]Modify /etc/fstab on the new copy to make sure it's mounting the right partitions
[/LIST]

---

