---
title: "How can I change my partition back to NTFS so I can  reinstall windows 7?"
date: 2010-08-15
forum: General Help
---

### Post by kaboomx on 2010-08-15
Please help. I'm trying to reinstall windows 7 from the cd, but the problem is I converted my partition to EXT3 when I installed Ubuntu. How do I make the partition NTFS so I can go back to windows 7? I prefer to unintall ubuntu.

---

### Post by howefield on 2010-08-15
You could boot with your Windows CD, and format the partition at the partitioning stage.

---

### Post by kaboomx on 2010-08-15
I don't know if I missed anything, but it would not let me continue the insallation because the drives were of a different partition, and it did not give me     any options to modify it

---

### Post by howefield on 2010-08-15
You should be able to select the partition and delete, then format.

Alternatively, use the Ubuntu Live CD and use GParted to do it.

System > Administration > GParted.

Remember before doing anything destructive to your disk to back up all your valuable data..

---

### Post by rockager on 2010-08-15
you can always use gparted on your ubuntu live cd to reformat the partition to ntfs.

---

