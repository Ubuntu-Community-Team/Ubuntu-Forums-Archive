---
title: "How set free space as new disk?"
date: 2006-05-05
forum: General Help
---

### Post by uhh on 2006-05-05
By installation Ubuntu I have splitted my hard disk to 4 partitions: 
/dev/hda1, and it contains:
1. root
/dev/hda2, as extended and it contains:
2. swap
3. FREE SPACE
4. /home
Now i have problem to installate PCBSD on this free partition. Installation just cant see this free space I left for it.
How can I set up this free space as recognizable disk without destroying files on other partitions.

---

### Post by Ptero-4 on 2006-05-05
set it as FAT32 in the ubuntu's partition manager. PCBSD should then be able to see it and you'll be able to change it's format to whatever PCBSD uses.

---

