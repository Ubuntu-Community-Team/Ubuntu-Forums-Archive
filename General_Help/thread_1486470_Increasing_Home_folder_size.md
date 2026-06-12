---
title: "Increasing Home folder size"
date: 2010-05-17
forum: General Help
---

### Post by Zireth ZH on 2010-05-17
Hey guys.. i guess im running into a problem.. i got low space left on my home folder .. i installed ubuntu and set home folder's size to 20 gbs and 70 gbs for my "/" partition , 2gbs for swap.

Is there a way  to increse those 20 gbs ? maybe take a lil from my "/" partition?

---

### Post by jbrown96 on 2010-05-17
You can try to resize the partitions. This is not absolutely secure (although I have never had any problems), but you should backup any important data first. 

You need to boot the LiveCD or LiveUSB and open gparted (system-->admin-->partition editor) and then you should be able to shrink / and expand /home). 

In the future, you probably won't ever need more than 10GB (even if you install lots of software) for /, so dedicate most to /home. 

There is another possibility to store some of your data on / and link it to /home, but that's not really recommended.

---

### Post by drs305 on 2010-05-17
You can do this from the LiveCD using Gparted. Backup important data before moving partitions around.

I wrote a post about resizing / to deal with a bug in Jaunty. It is about expanding / but the tips and principles presented in the second half of the post would be applicable to your situation:
[http://ubuntuforums.org/showthread.php?t=1219270]("http://ubuntuforums.org/showthread.php?t=1219270")

---

