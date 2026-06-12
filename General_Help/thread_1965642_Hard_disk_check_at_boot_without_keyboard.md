---
title: "Hard disk check at boot without keyboard"
date: 2012-04-26
forum: General Help
---

### Post by noleteman on 2012-04-26
Hello,
 
I have some linux computer that I want to use as wireless data concentrators. That means that they have no monitor and no keyboard. Some times, the hard disk check returns errors and waits for a user to press S or F. I would like to avoid this. 
 
I added nobootwait to fstab but it just hang the system somehow. I can see the purple Ubuntu 10.4 boot screen but nothing else happens and the system do not start. 
 
Do you know how can I force to fix the error on boot without user input?
 
Thanks!

---

### Post by raja.genupula on 2012-04-26
Hi look at the last paragraph that will tell you that how you can disbale the fsck at start up 

[http://www.cyberciti.biz/faq/linux-unix-bypassing-fsck/](http://www.cyberciti.biz/faq/linux-unix-bypassing-fsck/)


in my considearation disabling that one is the best , so if you want to check in future then you can make it manually . 

all the best

---

### Post by dcstar on 2012-04-26
> **noleteman said:**
> 
.........
Do you know how can I force to fix the error on boot without user input?
 
Thanks!

```
sudo gedit /etc/default/rcS
```

FSCKFIX=yes

---

### Post by noleteman on 2012-04-26
I would prefer just to force fixing the errors but for now I will do it like you said.
 
Thank you vety much.

---

### Post by dcstar on 2012-04-27
> **noleteman said:**
> I would prefer just to force fixing the errors but for now I will do it like you said.
 

That is **exactly** the solution I gave you.

---

### Post by blazer34i on 2013-02-05
I had to also create an empty forcefsck file at the root:

type: sudo touch /forcefsck

Thanks!! Just what I was looking for!!

---

