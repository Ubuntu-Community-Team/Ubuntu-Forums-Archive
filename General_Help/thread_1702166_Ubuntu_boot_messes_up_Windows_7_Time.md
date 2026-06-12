---
title: "Ubuntu boot messes up Windows 7 Time"
date: 2011-03-07
forum: General Help
---

### Post by alphaamanitin on 2011-03-07
Hey Guys,

I boot Ubuntu off of an external hard drive just so I don't deal with partitions and crap on the same drive my Windows 7 Ultimate is on.  This is a Gateway laptop, BTW.  Anyway, after I boot Ubuntu, when I boot into Windows again my time is off by a few time zones.  Any thoughts?

AlphaA

---

### Post by alphaamanitin on 2011-03-09
Was told by a linux using friend that if linux is set to use local time it can cause this issue.  Will test at next convenience and update.

AlphaA

---

### Post by celldweller1591 on 2011-03-09
1) Press Alt+F2 
2) Type 

> gksu gedit /etc/default/rcS

3) Enter the password and a gedit window will pop up.
4) Search for UTC and set UTC=yes or UTC=no (or accordingly how you wish)
5) Reboot and you are done..!!!!

---

### Post by alphaamanitin on 2011-03-16
> **celldweller1591 said:**
> 1) Press Alt+F2 
2) Type 



3) Enter the password and a gedit window will pop up.
4) Search for UTC and set UTC=yes or UTC=no (or accordingly how you wish)
5) Reboot and you are done..!!!!


Hmm, I don't understand why that would work if the supposed problem is having different time servers on the Windows 7 boot and Ubuntu boot.  For that matter I don't get why it should be, oh wait....  If Ubuntu is using GMT-0 (UTC) it would reset the hardware BIOS wouldn't it?  

Anyway, how do I find what time server Ubuntu is using?  I know I can google it, but as I already have a thread.

Alphaa

---

### Post by Mark Phelps on 2011-03-16
> **alphaamanitin said:**
> Anyway, how do I find what time server Ubuntu is using?  I know I can google it, but as I already have a thread.

Alphaa
You're making this harder than it needs to be.  If you're currently experience the time resetting problem, just change the Ubuntu setting to the opposite of what it is now.

---

### Post by alphaamanitin on 2011-03-16
> **Mark Phelps said:**
> You're making this harder than it needs to be.  If you're currently experience the time resetting problem, just change the Ubuntu setting to the opposite of what it is now.


It is not about making it easy, it is about understanding.  Yes, I could follow any steps given to me, but if I understand why there is a problem, why the solution fixes it, then I have learned something.  I think it is always preferable to learn about and fix a problem, instead of simply fixing it.

Id

---

### Post by Dave_L on 2011-03-16
Here's another topic on this issue, which includes an alternative solution of changing Windows to use UTC:
[http://ubuntuforums.org/showthread.php?t=1591792](http://ubuntuforums.org/showthread.php?t=1591792)

Also, the current BIOS clock can be viewed from Ubuntu with this command:
```
sudo hwclock -r
```

---

### Post by alphaamanitin on 2011-03-16
I solved it by changing the UTC to no and adding a time server in Ubuntu, time.nist.gov.  I like the idea of changing windows though as I feel linux usually does things better and windows is more often the problem.

AlphaA

---

