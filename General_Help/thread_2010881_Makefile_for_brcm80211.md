---
title: "Makefile for brcm80211"
date: 2012-06-26
forum: General Help
---

### Post by sheeru on 2012-06-26
I need to install brcm80211 module for wifi in my dell N4010 model. Iam   using linux kernel3.2. During kernel installation i have not checked  the  brcm80211.  How to configure the make file inside the brcm80211  source directory of linux 3.2 for installing it as a kernel module?
Pls post the makefile for compiling and installing the brcm80211 driver from the kernel source.

---

### Post by dino99 on 2012-06-26
have you checked the module loaded ?

into a terminal:

lsmod

[http://askubuntu.com/questions/102181/broadcom-brcm80211-installation-from-source](http://askubuntu.com/questions/102181/broadcom-brcm80211-installation-from-source)

into synaptic, search for : broadcom
(sudo apt-get install synaptic)

---

### Post by coffeecat on 2012-06-26
@sheeru, the brcm80211 kernel module is now called brcmsmac and is already compiled into the Ubuntu 3.2 kernel. If you are using the default Ubuntu kernel 3.2 you do not have to compile anything for that wireless module. Are you using Ubuntu 12.04?

---

### Post by sheeru on 2012-06-26
> **coffeecat said:**
> @sheeru, the brcm80211 kernel module is now called brcmsmac and is already compiled into the Ubuntu 3.2 kernel. If you are using the default Ubuntu kernel 3.2 you do not have to compile anything for that wireless module. Are you using Ubuntu 12.04?

i am using ubuntu 10.10 but manually compiled and installed linux 3.2. While manual compilation i havn't selected the brcm module for creating kernel module.  So, now am stuck with modifying the makefile so as to compile the brcm as kernel module from source of linux 3.2.

---

### Post by josephmills on 2012-06-26
> **sheeru said:**
> i am using ubuntu 10.10 but manually compiled and installed linux 3.2. 

10.10 is unsupported now a days I suggest that you upgrade. as there are now NO security patches for it.

---

### Post by coffeecat on 2012-06-26
> **sheeru said:**
> i am using ubuntu 10.10 but manually compiled and installed linux 3.2. While manual compilation i havn't selected the brcm module for creating kernel module.  So, now am stuck with modifying the makefile so as to compile the brcm as kernel module from source of linux 3.2.

Ok. Since you were using the 3.2 kernel I assumed you were using a later version of Ubuntu. I agree with josephmills - 10.10 is unsupported now and it would be better to use a later supported version of Ubuntu. The module is called brcm80211 in the kernel that came with 11.04, but is called brcmsmac with the stock Ubuntu kernels for 11.10 and 12.,04. But you wouldn't want to install 11.04 anyway - that release has less than 6 months support left.

---

### Post by sheeru on 2012-06-27
> **coffeecat said:**
> Ok. Since you were using the 3.2 kernel I assumed you were using a later version of Ubuntu. I agree with josephmills - 10.10 is unsupported now and it would be better to use a later supported version of Ubuntu. The module is called brcm80211 in the kernel that came with 11.04, but is called brcmsmac with the stock Ubuntu kernels for 11.10 and 12.,04. But you wouldn't want to install 11.04 anyway - that release has less than 6 months support left.

You are right, it needs to be upgraded. But, for testing purposes, i installed the linux kernel 3.2 in ubuntu 10.10.
I have the source files of the brcm80211 driver but no proper make file. i have the default make file present in the kernel3.2

---

