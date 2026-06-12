---
title: "lucid - problems at boot time"
date: 2010-05-06
forum: General Help
---

### Post by syphodias on 2010-05-06
hello, i have just upgraded to lucid, i am experiencing some boot problems.

after the file system check it hungs

```
fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
/dev/sdc1: clean, 167540/655360 files, 832546/2620595 blocks
/dev/sda5 has been mounted 39 times without being checked, check forced.
Films: clean, 64/9117696 files, 14702411/36451485 blocks
**init: ureadahead-other main process (859) terminated with status 4**
```

then if I press ctrl+alt+canc surprisingly it continues and boots succesfully. If not, it will stays like this (i think till the end of the universe).

does someone have similar problems?

---

### Post by viralmeme on 2010-05-06
[http://art.ubuntuforums.org/showthread.php?t=1437567](http://art.ubuntuforums.org/showthread.php?t=1437567)

---

### Post by syphodias on 2010-05-06
my lucid wasn't stuck, it was doing the check on sda5, but i couldn't see any progress since i disabled the spalsh screen.

i am very dumb. check finished -> normal boot

---

