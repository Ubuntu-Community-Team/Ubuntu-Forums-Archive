---
title: "SSD Xubuntu 10.04"
date: 2011-08-07
forum: General Help
---

### Post by fleamour on 2011-08-07
Anyone know what tweaks are needed for above set up?

---

### Post by pqwoerituytrueiwoq on 2011-08-07
update kernel for trim support
if you are using ext3/ext4 use the noatime and nodiratime options in fstab 
put */home*, */var*, */tmp*, and */root* on a mechnical hard drive to maximize the life of the ssd
you can make */tmp* a ram disk if you have enough ram
*tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0*

---

### Post by fleamour on 2011-08-07
Are there any step by step instructions? 

I am using ext4 & only have 512MB RAM.  I take it the 10.04 stock kernel does not have TRIM support?

Also it's a laptop so was gonna replace mechanical disk entirely.

---

### Post by pqwoerituytrueiwoq on 2011-08-07
Be sure to get a quality ssd then one with a good write tolerance
i saw your sig if you have the same ssd as in my sig you really need to use the fstab options asap i did not know about that trick and my ssd failed in 3 power on days (may have just been defective a little paranoid not as a result and make a backup about every week or 2 re-downloading apps is a pita on <1Mbps DSL)
cost me 8$ to in shipping to rma under warranty currently as 14.4 power on days and running good
edit i was skimming when i read your sig

---

### Post by fleamour on 2011-08-08
From what I have read on these forums:

Update kernel for trim support.

Check!

Add discard command to fstab.

Check!

> **pqwoerituytrueiwoq said:**
>  
if you are using ext3/ext4 use the noatime and nodiratime options in fstab

???

Not sure of this?  Please elaborate.

---

### Post by fleamour on 2011-08-08
[http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/](http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/)

Got you.

Cheerz.

:grin::mrgreen::grin:

---

