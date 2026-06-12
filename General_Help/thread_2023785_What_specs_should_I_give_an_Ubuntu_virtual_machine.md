---
title: "What specs should I give an Ubuntu virtual machine."
date: 2012-07-12
forum: General Help
---

### Post by Hydera5 on 2012-07-12
Due to the fact that I was advised to stay away from working with partitions and I have a decent machine I don't see the problem with running it in a VM.  I have a quad core i7, a 750GB hard drive, and 8GB of RAM.  My question is what is the recommended specs I give Ubuntu?  I want Ubuntu to run well but if it crashes I don't want it to bring the host OS down.

Thanks!

---

### Post by holycow131415 on 2012-07-12
These are minimum:
512+ ram
8gb+ hdd
enable 3d acceleration
the rest default.

install guest additions once ubuntu is installed. Reboot VM. Wa la.

---

### Post by uRock on 2012-07-12
I give my VMs 2 out of 4 CPUs as well as 50% of the GPU RAM and 2GB of RAM. They  fast and smooth.

---

### Post by Rsjc741 on 2012-07-13
No one here is wrong, but heres a more detailed opinion:
 
First, turn on VT-x and EPT in the BIOS. Most anything that have the words "Virtual, Guest OS, Hypervision(though this might be an AMD-specific term)"
 
Secondly, configure your Guest OS with your own OS in mind.
 
See, windows 7 has a base requirement for a machine with:
 
- 1Ghz processor (make that around 1.5~2Ghz for 64-bit versions)
- 2GB of RAM
- 20 GB of Storage
 
 
Knowing this, it's safe to assume that based on this, you can give your Guest OS <5120 MB of RAM, 4 cores, and full GPU power (if you're using intergrated graphics, consider using less)
 
Using 2 cores vs. 4 cores is really not that big of a deal, because usually the workload isn't divided on different cores as the host OS (to my knowledge).. unless specified in task manager or in the program itself.
 
 
and you bought a core i7.. why not get the 6-core version? or better yet, a AMD FX-8150 8-core =D

---

### Post by ranger1021994 on 2012-07-13
> **Hydera5 said:**
> Due to the fact that I was advised to stay away from working with partitions and I have a decent machine I don't see the problem with running it in a VM.  I have a quad core i7, a 750GB hard drive, and 8GB of RAM.  My question is what is the recommended specs I give Ubuntu?  I want Ubuntu to run well but if it crashes I don't want it to bring the host OS down.

Thanks!

*Core : 2
*HDD : Depends on your usage but default is 20GB(dynamically allocated)
*RAM : Ubuntu works fine even on 2GB.You can increase it if you find ubuntu hanging (rare)
*About Graphics,You can manually set it because it depends on how you will be using Ubuntu.You can keep the defaults
Keep all specification low if you are already doing memory intensive work on your host OS

---

### Post by Hydera5 on 2012-07-14
Thanks for the replies everyone. The processor I have shows up as 8 cores in VMware Viewer.  So if I wanted to give Ubuntu 50% of my processor it would be 4 cores? (I guess VMware does (#of cores * 2 = core count) to get the variables in which you can dedicate to the VM)

---

### Post by uRock on 2012-07-14
Not sure about VMware, but Oracle VirtualBox has an easy to use slider.

---

