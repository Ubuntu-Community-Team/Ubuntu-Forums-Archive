---
title: "Full disk and Disk Usage Analyzer problem"
date: 2012-03-20
forum: General Help
---

### Post by DottorBartolo on 2012-03-20
Hi there,

After a MATLAB simulation, I found my hard disk completely full. Then I removed a few log files which were taking up most of my HD space, but the disk has still stayed full.
My df -h says:

Filesystem       Size       Used      Avail    Use%    MOunted on
/dev/sda5       728G      691G          0    100%    /

which is already puzzling as there are (728 - 691)G = 37G missing.
Even more puzzling is that the Disk Usage Analyzer says that the size of / is 293.6GB. Where are all the other files taking up my space?
Any idea?

Thank you.

---

### Post by DottorBartolo on 2012-03-20
Ah, killing the MATLAB processes freed the missing space on the disk. It looks it is more a MATLAB problem then...

---

### Post by dmouck on 2012-03-20
There are several programs that will give you a graphical view of your hard disk and what is taking up your disk space. I like baobab, myself.

---

### Post by dcstar on 2012-03-20
> **DottorBartolo said:**
> 
.........
Even more puzzling is that the Disk Usage Analyzer says that the size of / is 293.6GB. Where are all the other files taking up my space?
Any idea?


```
gksudo baobab
```

---

