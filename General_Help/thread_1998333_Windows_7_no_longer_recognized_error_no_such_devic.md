---
title: "Windows 7 no longer recognized: error: no such device"
date: 2012-06-06
forum: General Help
---

### Post by ChemMeister on 2012-06-06
After a recent upgrade to 12.04 and after restarting the computer, i get "error: no such device". I booted from livecd ran boot-repair and generate the summary info. I dont fully understand the output, but it seems that it is not recognizing Windows 7 on its partition. 
The following link is the bootinfo summary. 
[http://paste.ubuntu.com/1027227/](http://paste.ubuntu.com/1027227/)

Any ideas? Thanks in advance

---

### Post by Basher101 on 2012-06-06
From the bootscript i can see that there is no NTFS partition, my guess is that the windows partition got somehow corrupted (e.g. all your data is lost. Hope you have backups?)

To verify this, install Gparted and run it. Make a screenshot of it and post it here (btw, you have 2 swap partitions. You only need 1. You could delete the seconds one and get a few GB of space back)


regards

---

