---
title: "I'm getting this error everytime I try to update anything"
date: 2011-08-06
forum: General Help
---

### Post by erkaninho on 2011-08-06
E: linux-image-2.6.32-33-generic: subprocess installed post-installation script returned error exit status 2
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured

Whatever I tried to update, this happens. How can I solve it?

---

### Post by ~!geek!~ on 2011-08-06
I don't know exactly what this error means, but it seems that in the process of installing the kernel update you faced some problems. Whatever!! 
Give it a try:
I hope there are number of other linux kernel images in grub loader screen because of the previous kernel updates. Just run one of them by choosing a different older linux kernel. 
It would appear as : ubuntu 10.10 using Linux 2.6.32.xx where xx is some number like 31, 30 but not 33. Just boot your system using one of older kernels. 
After logging in, check for updates. If it works and you are able to see new kernel update, you may do it.
If you fail to do so with this kernel also, you may try google for removing the kernel update and try reinstalling the linux kernel from repository.

This post may not be of much help, but give it a try if you want to. Should not harm!!!

---

### Post by c.cobb on 2011-08-10
Got the same error today. Haven't used my PC for a while so had a lot of updates. One of the linux-image or linux-header or linux-header...generic downloads for 2.6.32-33 hung at 90% (I didn't write down which one). After removing and reinstalling the three packages a couple of times was not able to get it working. Grub2 crashed and I used the crash report to generate [Bug #824146]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/824146"). 

Update Manager shows my PC is up to date.
Synaptic Package Manager never showed any broken dependencies. 

Guess I'll just wait for kernel update 34.
FWIW,

---

### Post by erkaninho on 2011-08-13
Yeah I think we need to wait for the new kernel update.

---

