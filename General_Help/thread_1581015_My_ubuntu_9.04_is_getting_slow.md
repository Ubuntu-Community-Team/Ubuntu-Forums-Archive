---
title: "My ubuntu 9.04 is getting slow"
date: 2010-09-24
forum: General Help
---

### Post by xetero on 2010-09-24
Hi, can somebody help me? My ubuntu is getting slow. Every time I save a document(.doc, .ppt) using open office, It takes like 30 seconds before it show the directory where open office will save the document...  and this also happens when I am uploading a file using firefox in yahoo mail, It takes long time before the firefox shows the directory of the file that I am going to download. it doesn't happen to me before, by the way, Im using a pentium 4 @ 3.0gHz PC with 512 ram and 500gB HDD...  what can you suggest?

---

### Post by mikewhatever on 2010-09-24
Check the RAM usage with **free -m** .

---

### Post by arubislander on 2010-09-24
Is everything getting slow or just the showing of directory contents. Is this with every directory or just the Documents and Downloads?

---

### Post by mörgæs on 2010-09-24
9.04 is running out of support in a month. Rather than troubleshooting I would try a live boot of 10.04 and do a fresh install if it works well.

---

### Post by xetero on 2010-09-25
> **arubislander said:**
> Is everything getting slow or just the showing of directory contents. Is this with every directory or just the Documents and Downloads?

just the showing of directory....

---

### Post by xetero on 2010-09-25
> **mikewhatever said:**
> Check the RAM usage with **free -m** .


I've tried checking the ram usage and it shows me that I'm currently using 441

---

### Post by mörgæs on 2010-09-25
Really? That is a lot. Please post the output of **free -m**.

---

### Post by xetero on 2010-09-25
> **mörgæs said:**
> Really? That is a lot. Please post the output of **free -m**.

here it is...

                                                total       used       free     shared    buffers     cached
Mem:                               481        472              8                0                   8                168
-/+ buffers/cache:            295          186
Swap:                             400         63           336

---

### Post by mikewhatever on 2010-09-26
> total used free shared buffers cached
Mem: 481 472 8 0 8 168
-/+ buffers/cache: 295 186
Swap: 400 63 336

That RAM usage seems to be within reasonable bounds. Are those very large .docs and .ppts?

---

### Post by mörgæs on 2010-09-26
This indicates 295 MB used:
[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

Still a fairly high number, if you have a plain vanilla installation. Was it measured straight after boot?

Again, rather go for 10.04. It is a waste of time to troubleshoot an (almost) obsolete version.

---

### Post by xetero on 2010-10-02
> **mörgæs said:**
> This indicates 295 MB used:
[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

Still a fairly high number, if you have a plain vanilla installation. Was it measured straight after boot?

Again, rather go for 10.04. It is a waste of time to troubleshoot an (almost) obsolete version.


how do I update to 10.04? will I lose all my files and customizations? (themes, docks, etc)

---

### Post by cgroza on 2010-10-02
If you don't have a backup make one. From 9.04 you must do it in 2 steps (upgrade to karmic ,then to lucid) so i recommend using a CD because it will install Lucid directly and much faster. Do you have all your data in the home directory? Is the home directory on another partition?

---

### Post by mörgæs on 2010-10-02
Yes, go for a back up and a fresh installation. Chances are that you don't want to apply any customisations to 10.04, as the look and feels is much different from 9.04.

---

### Post by xetero on 2010-10-05
> **cgroza said:**
> If you don't have a backup make one. From 9.04 you must do it in 2 steps (upgrade to karmic ,then to lucid) so i recommend using a CD because it will install Lucid directly and much faster. Do you have all your data in the home directory? Is the home directory on another partition?

all my files is on my external hard disk except for applications... I think, I'm just going to have a fresh installation... by the ways, thanks guys for your help! :)

---

### Post by mörgæs on 2010-10-05
You are welcome. Good luck.

Just remember to have wired internet access while installing.

---

