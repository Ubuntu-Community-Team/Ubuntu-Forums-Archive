---
title: "Problem installing VMware workstation"
date: 2011-07-22
forum: General Help
---

### Post by hacker_at_linux on 2011-07-22
I downloaded and installed successfully vmware workstation 7 on my computer.
but now when I run it it ask for kernal headers of linux kernal 2.6.38-10-generic , some C files it is looking for to compile its modules. I have searched the internet for the location of the files but I have not been able to. Can any one please tell me where are these linux headers stored in Ubuntu 11.04

---

### Post by RikoW on 2011-07-22
Hi ,

you can install the headers which correspond to your current generic kernel by:

```
sudo apt-get install linux-headers-generic
```

This is a meta-package and should also pull in the new headers when a kernel update is distributed.

To make sure you have all the tools to compile the vmware modules, do 

```
sudo apt-get install build-essential

```

If you now start vmware-workstation it should be able to compile all necessary kernel modules and start.

Let us now, if that was successful.

Good luck,

              Riko

---

### Post by llarsen on 2011-07-31
That didnt seem to work for me... i havent had any luck getting VMware workstation to work on Ubuntu 11.04 64bit. I followed your instructions but it told me there were no updates for it. it keeps asking for the kernel headers 2.6.38-10-generic, which i already technically have in that folder, but it doesnt work.

---

### Post by hacker_at_linux on 2011-07-31
simply doing that won't work 
there is a patch available on the internet .DO the above steps. and the install the patch vmware is then able to make all the modules
you can google for the patch is is very easily available

---

### Post by poserslipjack on 2011-07-31
Hey,

I'm with Llarson. Hacker_at_linux, I am ashamed to admit that this 'very easily available' patch has eluded me thus far. Throw us a bone?

Trying harder,
-poser

---

