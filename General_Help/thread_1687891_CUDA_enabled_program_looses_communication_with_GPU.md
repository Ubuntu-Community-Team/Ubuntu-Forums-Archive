---
title: "CUDA enabled program looses communication with GPUs"
date: 2011-02-14
forum: General Help
---

### Post by markusan on 2011-02-14
I have had a problem for several weeks now with a software called NAMD. At this point I do not know where the error lies (if it is the OS, conflicting programs, driver issue, or something else). NAMD is a free to use, open source molecular dynamics program ([http://www.ks.uiuc.edu/Research/namd/](http://www.ks.uiuc.edu/Research/namd/)).

The problem is basically that I start a simulation and it works fine for a short time, regularly printing output. After a short while though, the output is stopped being printed but the processors are still being used at 100%. What happens is that the program looses contact with the GPUs and keeps polling them. I have a 64 bit installation of Ubuntu and NAMD is a 64 bit program. I have tried leaving the software running over night but it does not find the GPUs again. Since the program does not properly crash, there is no error log produced. 

I wonder if anyone has seen anything similar? What can disrupt the communication between the GPUs and the program? I have been in contact with the developers of NAMD and they cannot reproduce my problem, using my input files. I have checked the hardware and there is no physical problem with the two GeForce 580GTX cards I am using. I have tried installing two of the latest Linux Display drivers (260.19.36 and 260.19.29). Both give the same problem. I have blacklisted Nouveau prior to the installation of the Nvidia drivers. 

Prior to trying the simulations in Ubuntu I tried running them in Fedora 12. I thought it was a problem associated with Fedora 12 so I changed to Ubuntu 10.10, but now I see the same problem. 

Any ideas that can help me troubleshoot would be great!

---

