---
title: "Double partition Ubuntu windows 7"
date: 2011-06-03
forum: General Help
---

### Post by magodiafano on 2011-06-03
Hello I have a problem... with my laptop, I was able to create a double boot vista/ubuntu through the ubuntu installer.
 
With my desktop I tried both with windows xp and with windows 7, but I have always the same problem: during the ubuntu installer, when I create the partition, an error message is displayed and after the only option which I could choose is installing ubuntu erasing windows.
 
What's the problem with my desktop? it could be possible that I have to change the kind of partition?

---

### Post by oldfred on 2011-06-03
Have you used all 4 primary partitions?

From liveCD post this or a screenshot from gparted:

sudo fdisk -lu

Note that all the boot files for the second install of windows are actually in the partition of the first install. If you delete the first windows you have to repair the second windows or it may not be repairable.

---

### Post by Sudheesh.K.S on 2011-06-03
You can try it using the Advanced option for partition, I think you are having more than one partitions on your desktop. If so, empty one partition by moving the data, then try installing Ubuntu to that partition. I am using Widows XP, Windows 7 and Ubuntu 10.10 in this manner. I would be glad to help you within my knowledge. 

Note: I am also new to Ubuntu only 2 years of exp without much exposure  to all these technicalities....

Good Luck. :)

---

