---
title: "Please help Wacky issue?"
date: 2010-08-24
forum: General Help
---

### Post by fabio1989 on 2010-08-24
I had a Ext4 partitioned harddrive working in ubuntu and decided to see if i could mount it under a windows system. I didnt get far. I didnt want to lose the information on the disk so i didnt format or any such thing. However once I placed the 250gb hd into my windows machine it claimed that 120gb of it was fat.

When i went to put it back into Ubuntu it would no longer recognize the partition.

How can I fix this?! The information on the disk is important to me.

Thanks

---

### Post by MilesTails on 2010-08-25
Try running fs check on the drive

  sudo fsck.ext4 /dev/(insert your drive here)

---

