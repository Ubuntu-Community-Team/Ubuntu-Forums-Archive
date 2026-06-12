---
title: "nvidia graphics failure"
date: 2010-07-30
forum: General Help
---

### Post by mansourk on 2010-07-30
Hi All,
 before i installed ubuntu My pc had had an installed nvidia geforce 6200 256MB graphics plus an onboard intel graohics. it was for times that i wanted to install ubuntu  on my pc, but it failed. so i tried to remove the nvidia and install ubuntu with the onboard graphics, and it was successful , i managed to install ubuntu 10.04 amd64 on my pc. now  i want to reinstall the nvidia card but i can't. when i put it on my pc and turn it on and chose ubuntu from grub it fails to load ubuntu. 
so i tried to first install "NVIDIA-Linux-x86_64-180.60-pkg2.run" and then assemble the nvidia card on my pc. but "NVIDIA-Linux-x86_64-180.60-pkg2.run" fails to install.
 the nvidia-installer.log file is attached to this post.

what should i do now? please help me on this issue.

---

### Post by sydbat on 2010-07-30
> **mansourk said:**
> Hi All,
 before i installed ubuntu My pc had had an installed nvidia geforce 6200 256MB graphics plus an onboard intel graohics. it was for times that i wanted to install ubuntu  on my pc, but it failed. so i tried to remove the nvidia and install ubuntu with the onboard graphics, and it was successful , i managed to install ubuntu 10.04 amd64 on my pc. now  i want to reinstall the nvidia card but i can't. when i put it on my pc and turn it on and chose ubuntu from grub it fails to load ubuntu. 
so i tried to first install "NVIDIA-Linux-x86_64-180.60-pkg2.run" and then assemble the nvidia card on my pc. but "NVIDIA-Linux-x86_64-180.60-pkg2.run" fails to install.
 the nvidia-installer.log file is attached to this post.

what should i do now? please help me on this issue.Have you gone into BIOS and disabled the onboard graphics AND enabled/chosen the correct option for the nVidia card?

---

### Post by mansourk on 2010-07-30
No, how could i do that?

---

### Post by mansourk on 2010-07-30
Hi, 
I changed the BIOS settings so as to boot up with the onboard graphics. i logged into ubuntu and typed the command "sudo sh NVIDIA-Linux-x86_64-180.60-pkg2.run " into terminal. but this error has occurred  : 
         "ERROR: You appear to be running an X server; please exit X before            
         installing.  For further details, please see the section INSTALLING   
         THE NVIDIA DRIVER in the README available on the Linux driver         
         download page at www.nvidia.com."
now what should i do?

---

