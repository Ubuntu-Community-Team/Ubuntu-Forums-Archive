---
title: "Ubuntu 10.10 boots straight into console after attempting to install CUDA tools"
date: 2011-09-26
forum: General Help
---

### Post by Evanfoo on 2011-09-26
So as the title states, I was trying to install CUDA drivers yesterday and i havent seen a GUI since the installation process. I was following the following instructions: [http://www.r-tutor.com/gpu-computing/cuda-installation/cuda4.0-ubuntu](http://www.r-tutor.com/gpu-computing/cuda-installation/cuda4.0-ubuntu)

I think that things went awry after the installation of the developer driver, because after that reboot, i haven't been able to access GNOME, that is, my pc reboots straight into console. After this, i still installed the CUDA toolkit, but it didnt change anything. 

So far I have tried pressing alt+f7 and i also tried sudo services gdm start. None of the above have worked. I was able to login using failsafe graphics mode, but i'm not sure what to do after that. 

Can anyone suggest something I could try next please, i'm relatively new to linux :/ 

Btw, my OS is ubuntu linux 10.10 32 bit and my gfx card is a gtx460

---

### Post by matt_symes on 2011-09-26
Hi

It sounds like X is crashing. Have you had a look in the log files in /var/log. I would suggest having a look at syslog or messages.

That may give an indication as to the problem.

Kind regards

---

