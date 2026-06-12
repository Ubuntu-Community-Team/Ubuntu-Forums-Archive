---
title: "Can i expand space to ubuntu"
date: 2012-09-17
forum: General Help
---

### Post by Mohan1289 on 2012-09-17
hey guys i installed ubuntu with 20 GB space using WUBI

where i installed Windows on LocalDisk(C)

when i opened ubuntu it became slow very slow.

If i opened a terminal and say firefox with 5 or 6 tab's and geditor and if i switched between them fastly the system is getting struck.

I don't know why can anyone tell me why and how to resolve this??

and can't we assign More than 30 GB when we are installing ubuntu using WUBI??

Thank you

---

### Post by mastablasta on 2012-09-17
> **Mohan1289 said:**
>  
I don't know why can anyone tell me why and how to resolve this??

What are you system specifications? RAM, CPU and graphics chip?
 
> 
and can't we assign More than 30 GB when we are installing ubuntu using WUBI??

 
i don't think so. wubi has it's limits as it works in a virtual disk that is created inside windows partition. you can however do a side by side dual boot.

---

### Post by Mohan1289 on 2012-09-17
CPU 2.66Ghz
2.67GHz,0.99 GB of RAM
250GB HDD
Processor Dual Core..

It doesn't have Graphic Card..

---

### Post by oldos2er on 2012-09-17
> **Mohan1289 said:**
> It doesn't have Graphic Card..

Most PCs won't boot without a video card, but that doesn't seem to be your problem.  :)

Can you run ```
lspci | grep VGA
``` in a terminal, and copy the output here?

---

### Post by Mohan1289 on 2012-09-18
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)

---

