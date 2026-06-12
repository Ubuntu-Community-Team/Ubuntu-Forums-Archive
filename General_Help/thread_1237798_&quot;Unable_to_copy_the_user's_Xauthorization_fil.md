---
title: "&quot;Unable to copy the user's Xauthorization file.&quot; What to do?"
date: 2009-08-11
forum: General Help
---

### Post by SoftwareExplorer on 2009-08-11
I tried to run System->Administration>Gparted and got the error message:


**Failed to run /usr/sbin/gparted as user root.**

Unable to copy the user's Xauthorization file.
                                       [Close]

It seems to have this problem with gksudo (i think that's what it is) randomly. It seemed to happen after I put my /home on a separate partition and symlinked to it. After that it worked fine. So the separate /home could be the cause but it might not be. I just want to include anything that could have to do with it. If I restart the problem is solved.

---

### Post by dcstar on 2009-08-11
> **SoftwareExplorer said:**
> I tried to run System->Administration>Gparted and got the error message:


**Failed to run /usr/sbin/gparted as user root.**

Unable to copy the user's Xauthorization file.
                                       [Close]

It seems to have this problem with gksudo (i think that's what it is) randomly. It seemed to happen after I put my /home on a separate partition and symlinked to it. After that it worked fine. So the separate /home could be the cause but it might not be. I just want to include anything that could have to do with it. If I restart the problem is solved.

If the partition is not a native Linux filesystem, then that could be a factor.

There are many ways to have a separate /home partition that works correctly, you should check them out.

---

### Post by SoftwareExplorer on 2009-08-11
It's ext3, but on another drive. Could being on another drive be a factor?

---

### Post by SoftwareExplorer on 2009-08-12
After some testing, it seems to work after I re-log in (which a restart would cause).

---

### Post by SoftwareExplorer on 2009-08-12
> **dcstar said:**
> If the partition is not a native Linux filesystem, then that could be a factor.

There are many ways to have a separate /home partition that works correctly, you should check them out.
It works properly most of the time, so I doubt the home thing is the problem, It's just a possibility because the error happened sometime after I changed it.

---

### Post by SoftwareExplorer on 2009-10-04
Hasn't happened in a long while, so I'll mark this thread as solved.

---

### Post by drs305 on 2009-10-04
If it happens again, check to see if your system partition is almost full. That is another instance which can cause this to happen.

---

### Post by AgentY on 2009-10-06
> **drs305 said:**
> If it happens again, check to see if your system partition is almost full. That is another instance which can cause this to happen.

 Just to add some more info to this;  I just had this issue aswell, and noticed I am all out of free HDD space.Backing up to another HDD now which hopefully resolves the problem!  Thanks!  Y

---

### Post by TACITVS on 2011-07-19
Relogging fixed my xauthorization error; gparted is working fine now.

---

