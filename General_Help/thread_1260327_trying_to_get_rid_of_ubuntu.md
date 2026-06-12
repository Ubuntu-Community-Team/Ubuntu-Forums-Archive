---
title: "trying to get rid of ubuntu"
date: 2009-09-07
forum: General Help
---

### Post by rlawlals on 2009-09-07
Hey not that i hate ubuntu, but there i installed it with windows XP side by side. it happened to be someone elses computer and i need to get rid of it without getting rid of xp. any help anyone please? thankyou!

---

### Post by ddrichardson on 2009-09-07
Boot from a Windows install CD and choose "Recovery".

Do:
```
bootcfg /rebuild
fixboot
fixmbr
```

Make sure you're happy with these commands and sure about what you're doing.

You'll also need to use the Ubuntu Live CD to run GParted and reallocate the space back to Windows.

---

### Post by ed5000 on 2009-09-07
> **rlawlals said:**
> Hey not that i hate ubuntu, but there i installed it with windows XP side by side. it happened to be someone elses computer and i need to get rid of it without getting rid of xp. any help anyone please? thankyou!

I would just tell them that it started working a lot better but, you have no idea how.

---

### Post by rlawlals on 2009-09-28
sorry for the late reply, i thought they would send a notification mail. but i dont have a windows xp cd... and its  a vista computer... i dunno what to do.

---

### Post by grturner on 2009-09-28
well you could just use the vista partition editor to delete ubuntu, grow the vista partition and then theres a way to boot into the recovery console and restore the mbr, though i dont remember how to off the top of my head

---

### Post by raymondh on 2009-09-28
> **grturner said:**
> well you could just use the vista partition editor to delete ubuntu, grow the vista partition and then theres a way to boot into the recovery console and restore the mbr, though i dont remember how to off the top of my head

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

---

### Post by rlawlals on 2009-09-30
thanks... i did go to recovery mode, and i tried to format the harddrive... didnt work.

---

