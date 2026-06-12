---
title: "What Partition Holds What?"
date: 2010-02-16
forum: General Help
---

### Post by Wataru8675 on 2010-02-16
Hello,

Awhile ago, I decided to put my /home on a separate partition, and did so successfully, but wasn't sure how much space to allocate to it.  So I basically split /home and the Ubuntu boot whatchyamacallemy about 50/50.  Now I know (/am pretty sure) that the Ubuntu Boot partition only needs about 2GB of space (though I'm going to give it 5GB for leeway's sake), but I don't remember which partition holds /home because I didn't think well enough to label it...  Is there a way to check this?

Thanks,
wataru8675

---

### Post by mcduck on 2010-02-16
Sure. Just run "df -h" in a terminal to see your filesystems/partitions, where they ar emounted and used & available space on them.

---

