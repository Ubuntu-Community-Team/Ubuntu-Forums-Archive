---
title: "how much ram do I have"
date: 2010-10-31
forum: General Help
---

### Post by wscg on 2010-10-31
i wanted to check how much ram I had on my computer. And I typed in Free in the terminal and this popped up 


      total       used       free     shared    buffers     cached
Mem:        508484     461612      46872          0      16840     225856
-/+ buffers/cache:     218916     289568
Swap:      1486844      34796    1452048

Does this mean I 508mb ram? I ask because on the boot screen it says 128mb ram. I am currently running lubuntu on this desktop but if I can run xubuntu than I will opt for that if it is an option now.

---

### Post by dondiego2 on 2010-10-31
> **wscg said:**
> i wanted to check how much ram I had on my computer. And I typed in Free in the terminal and this popped up 


      total       used       free     shared    buffers     cached
Mem:        508484     461612      46872          0      16840     225856
-/+ buffers/cache:     218916     289568
Swap:      1486844      34796    1452048

Does this mean I 508mb ram? I ask because on the boot screen it says 128mb ram. I am currently running lubuntu on this desktop but if I can run xubuntu than I will opt for that if it is an option now.


Here's mine
```
            total       used       free     shared    buffers     cached
Mem:        959912     897444      62468          0       4968     118080
```

I have to 508 chips installed, so I guess it's not finding it all or there is some bad memory?

---

### Post by spiky001 on 2010-10-31
Have a look in system/administration/system monitor use system tab

---

### Post by Verbeck on 2010-10-31
try** free -m**
it would give in megabytes

---

### Post by wscg on 2010-10-31
I couldn't find system monitor (lubuntu menu) but system profiler showed what I already posted.

free -m yielded this 

       total       used       free     shared    buffers     cached
Mem:           496        339        157          0         21        185
-/+ buffers/cache:        132        363
Swap:         1451          0       1451


and task manager showed 162 of 496 mb used. 

So is it safe to say that I have 496mb ram? therefore meet the ram requirments of xubuntu

---

### Post by P4man on 2010-10-31
> **wscg said:**
> 
So is it safe to say that I have 496mb ram? therefore meet the ram requirments of xubuntu

Quite safe. In fact you probably have 512MB in the system, but some of it is used by the videocontroller. Doesnt change the fact it should be plenty for xubuntu.

---

### Post by dondiego2 on 2010-11-01
> **dondiego2 said:**
> Here's mine
```
            total       used       free     shared    buffers     cached
Mem:        959912     897444      62468          0       4968     118080
```I have to 508 chips installed, so I guess it's not finding it all or there is some bad memory?


I meant to say I have two 512 memory cards installed.

---

