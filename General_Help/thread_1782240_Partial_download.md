---
title: "Partial download"
date: 2011-06-14
forum: General Help
---

### Post by run6run1 on 2011-06-14
I tried to download WINE software from the Ubuntu site but whilst downloading it hung and after 20 minutes I turned the computer power off.When resuming I found that the software had loaded on to the front screen.
When I went to download further software from Ubuntu,I got the erre message that further down loads could not be comleted because the prevous one had only been partially completed.I have tried to remove WINE but again only get the message that it can not be removed because it has not been fully downloaded.Update manger will not now work and synaptic manager gives a message stating that E dpkg was interupted you must manually run sudo dpkg configure a E cache open failed please report. I have tried to run sudo dpkg in terminal but only receive the message command not found.

---

### Post by jerrrys on 2011-06-14
try

sudo dpkg configure  -a

---

### Post by ajgreeny on 2011-06-14
Should be ```
sudo dpkg --configure -a
```the **--configure** is important.

---

### Post by jerrrys on 2011-06-14
oops, thanks for catching that

---

### Post by run6run1 on 2011-06-15
> **ajgreeny said:**
> Should be ```
sudo dpkg --configure -a
```the **--configure** is important.

I have tried the above suggestion,thank you, it would appear that the fonts from Microsoft are now only available from 3rd party sources.after submitting your sudo data the terminal continues to search for data from (dl) channels or sites to update the downloaded software.Has anybody else experienced these problems with WINE.If I could get rid of the software I would do.

---

### Post by run6run1 on 2011-06-16
Managed to remove Wine from the system and now everything appears to be working and updating properly Thanks for the help:D

---

