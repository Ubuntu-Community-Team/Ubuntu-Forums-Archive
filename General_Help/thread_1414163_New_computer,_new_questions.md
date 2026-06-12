---
title: "New computer, new questions"
date: 2010-02-23
forum: General Help
---

### Post by Ken147 on 2010-02-23
Okay, I'm going to be getting an [eMachines T2984]("http://www2.dealtime.com/xPF-EMACHINES-T2984-Desktop-Computer") (close to the model, but not exactly) so I am going to be upgrading the ram to 1GB and putting a fresh install of windows XP Home.

It has a 160GB HD: I would like to make it dual-boot Win XP and Ubuntu 9.10

**Questions**

- What would I use to partition the the disk so I would have 120Gb of space for Win XP and 30Gb or Ubuntu? 

- what should I use as a boot loader?

- is there a app that lets you run Windows and linux at the same time and switch between them, and if so does it work good?



[B][SIZE=2]
[/SIZE][/B]

---

### Post by drpjkurian on 2010-02-23
> **Ken147 said:**
> Okay, I'm going to be getting an [eMachines T2984]("http://www2.dealtime.com/xPF-EMACHINES-T2984-Desktop-Computer") (close to the model, but not exactly) so I am going to be upgrading the ram to 1GB and putting a fresh install of windows XP Home.

It has a 160GB HD: I would like to make it dual-boot Win XP and Ubuntu 9.10

**Questions**

- What would I use to partition the the disk so I would have 120Gb of space for Win XP and 30Gb or Ubuntu? 

- what should I use as a boot loader?

- is there a app that lets you run Windows and linux at the same time and switch between them, and if so does it work good?



[B][SIZE=2]
[/SIZE][/B]

A1 Use partition editor of Live CD to do the partition, create an 'unallocated space' of 30 GB and Install Ubuntu by 'Selecting Install in free space'.It will be automatically installed in this 30 GB

A2 Use GRUB for Boot loader 

A3 You can try installing virtual box for running an another OS virtually in a real one say for eg in my machine I had Virtual Windows XP in Ubuntu Jaunty

---

### Post by bruno9779 on 2010-02-23
XP with new hardware = bad idea

support for XP has already been discontinued, and some ppl I know had already issues with some specific hardware.

---

### Post by tacantara on 2010-02-23
> What would I use to partition the the disk so I would have 120Gb of  space for Win XP and 30Gb or Ubuntu? 

In my brief experience with dual-booting, if you install Windows first, then install Ubuntu, the Ubuntu installer will ask you how much of the disk you want to use for the installation.

> what should I use as a boot loader?

The Ubuntu installation will automatically install the the GRUB bootloader.  When you restart your computer, you will see a screen where you can choose between Ubuntu and Windows.

>  is there a app that lets you run Windows and linux at the same time and  switch between them, and if so does it work good? 

VirtualBox is a good program to accomplish this.  Go to [www.virtualbox.org](www.virtualbox.org) and download the package from there.  You can put Windows on your laptop and run Ubuntu in the virtual machine, or vice-versa.

---

### Post by Ken147 on 2010-02-23
> **bruno9779 said:**
> XP with new hardware = bad idea

the computer that I am going to be getting is from around 2003-2004 so it already had Windows XP on it

so from reading the other posts, alls I need to do it install Windows, boot off the Unbuntu Live CD, and everything (in theory :)) should work?

---

### Post by tacantara on 2010-02-23
> **Ken147 said:**
> the computer that I am going to be getting is from around 2003-2004 so it already had Windows XP on it

so from reading the other posts, alls I need to do it install Windows, boot off the Unbuntu Live CD, and everything (in theory :)) should work?


Yes, pretty much.  I did a dual-boot setup recently on my Mom's desktop, which has Win XP.  I installed Ubuntu off the LiveCD, and it did all the partitioning and bootloader stuff automatically (with a little user intervention, to answer questions about partition size, etc.).  Make sure that you try and run Ubuntu from the LiveCD before you actually install, just to make sure that it'll work nicely with your computer's hardware (i.e. ethernet/wifi, graphics card).

---

