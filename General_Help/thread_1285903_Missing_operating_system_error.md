---
title: "Missing operating system error"
date: 2009-10-08
forum: General Help
---

### Post by Aspras on 2009-10-08
Hello, I recently downloaded 9.10 and tried to dual boot with windows. I shrinked the windows partition and created a new ext3 one for ubuntu, I then installed ubuntu on there and since that I keep getting a "Missing operating system error" whenever I start my computer up. Anyone knows how to fix this ?

---

### Post by CharlesA on 2009-10-08
Try repairing the mbr in windows and then add GRUB, so you can select which OS you want to use.

Overall, I have had horrible luck with resizing windows partitions, usually end up having to just delete the partition and reinstall fresh.

---

### Post by Aspras on 2009-10-08
I want to stick to GRUB2 since its better than the older version and from what people told me on IRC they are all using it without issues. I think the problem is somewhere inside grub.cfg although I can't open it up.

---

### Post by Aspras on 2009-10-09
Problem fixed , GRUB was being by default installed on a different hard drive where I kept files only. I was lucky to figure that out since I had to click "Advanced" at the final step of the installation.

---

