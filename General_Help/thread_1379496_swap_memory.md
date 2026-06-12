---
title: "swap memory"
date: 2010-01-12
forum: General Help
---

### Post by mihe on 2010-01-12
Hi, 
I am running a computation software om my ubuntu 8.04. In the software I can adjust the amount of memory that it is available. I have 2GB RAM.

If I state in the settings of the program that it should only use for example 1200MB I can ses i the system monitor that it does not use more than that -ok. 

However I can also see that it uses swap. It does not matter if I set in the program that 2000MB or 1200MB is available, still it takes about 50MB swap. I suspect that this may cause my computation to run slow.

I have set my vm.swappiness=0. 

Question: If I set it to use 1200MB (and I can see in the the system monitor that it only uses 1200MB) -why does it use swap?

Kind regards,
Micke

---

### Post by john newbuntu on 2010-01-13
Setting swappiness to 0 only puts off writing to the swap for a while - perhaps the data from other processes.  But in case you think you can handle most of your program in RAM, have you tried turning giving your app over 95% of the RAM and possibly even switching swapoff?

---

### Post by mihe on 2010-01-13
swapoff -ok I will try that! Thank you/Micke

---

