---
title: "Use dual core CPU in VBox"
date: 2011-07-08
forum: General Help
---

### Post by Joe- on 2011-07-08
I have a dual core CPU and am currently running one of my versions of Ubuntu in a VBox. Just wondering if I allow the Virtual machine to use both cores of the CPU how much effect will this have on 1. The host PC (3GB RAM)? 2.The performance of Ubuntu running in the VBox?

Cheers Joe.

---

### Post by Joe- on 2011-07-08
Bump

---

### Post by marin123 on 2011-07-08
so, you have ubuntu guest on windows host, right?

if you assign more than 50% of your system's resources to the guest, that could lead to system unstability and crash. if you need better performance, you can always dual boot or wubi.

---

### Post by Joe- on 2011-07-08
Yes that's correct. And I never give the virtual machine more that 1.5GB of RAM, but I was wondering if using dual core could cause I crash on the host PC? I have a Wubi install on another laptop, the one in question is just experimental.

---

### Post by wildmanne39 on 2011-07-08
> **Joe- said:**
> Yes that's correct. And I never give the virtual machine more that 1.5GB of RAM, but I was wondering if using dual core could cause I crash on the host PC? I have a Wubi install on another laptop, the one in question is just experimental.Hi, no it will not cause a crash, it will allow for the work load to be distributed among both cores and not just one, which is better because when using vm it can get one core hot and it can slow the processing down, I have used 2 core setup since it became available. If you have a cpu monitor on your host and you have your vm running you will see how hard it is working with just one available.

---

### Post by pqwoerituytrueiwoq on 2011-07-08
it is in settings
i have have xp bsod on my laptop from it (i think it was cause i was under-clocking during install cause a xp install will make the system hit the max temp and cut off)

---

### Post by marin123 on 2011-07-09
> **Joe- said:**
> Yes that's correct. And I never give the virtual machine more that 1.5GB of RAM, but I was wondering if using dual core could cause I crash on the host PC? I have a Wubi install on another laptop, the one in question is just experimental.

how many cores does vb show? you can assign half of them and be safe as long as you dont do something cpu demanding on host side.

---

