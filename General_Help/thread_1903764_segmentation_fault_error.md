---
title: "segmentation fault error"
date: 2012-01-03
forum: General Help
---

### Post by thegreeneyes on 2012-01-03
Hi, I am running a code on a system with 12 cores, and 48GB of RAM. with UBUNTU 10.10.

The code has run ok many times. This code reads, depending on the input files, data libraries describing different materials properties used in the simulation. I have run the same input file changing (increasing) the number of materials used in the simulation, and beyond certain limit, a "segmentation fault error" comes to the screen while the code is being executed. Apparently the amount of memory the code is using is 100% of the available memory. 

Is the swapping memory available always for the code to be used, or the code only runs using the physical memory?.

Is there a way to assign the code some extra space of "virtual memory" as in windows systems, or should I just increase the swap disk size in order to let the code access more memory?

Any suggestions?

Thanks

TGE

---

