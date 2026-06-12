---
title: "Delay in booting when 11.04 is installed thro WUBI. How to prevent Delay?"
date: 2011-06-02
forum: General Help
---

### Post by ssreddy555 on 2011-06-02
I have an internal WD 1 TB HDD installed. I made 2 almost equal primary partitions & installed Win 7(64 bit) into the first (C) partition.

Using WUBI, I installed Ubuntu 11.04 32 bit version into the same partition.

everything is ok except that it is taking too long to boot into ubuntu at the start; 

Step 1: when it starts booting, it says no wubildr & keeps searching; (it's here that all the  delay occurs; rest of the booting process is normal.)

then,

Step 2: presents the option to select the OS - Win 7 or ubuntu; 

then 

Step 3: presents the GRUB after we select ubuntu.

The boot process is normal from Step 2 onwards.

Is there a way I can hasten the boot process in Step 1 say by installing GRUB to come immediately at the start of the booting if such a thing is at all possible.

In my laptop; I have Win XP installed first;  then Jolicloud &  then thro' WUBI, ubuntu 11.04. In this case, the sequence of booting is:

1. GRUB > select Win XP
2. Select OS > ubuntu
3. GRUB again > select ubuntu.

Booting occurs at normal speed.

I  want to know is there a way I can get GRUB to come on in the beginning of boot process so that there is no delay. I think the delay is because it is unable to find the GRUB at the beginning.

Also, is it better to use 64 bit version of ubuntu 11.04 in this scenario than 32 bit? Does it make a difference for the better or worse? Some posts indicate that it's better to avoid 64 bit version.

Thank u.

---

