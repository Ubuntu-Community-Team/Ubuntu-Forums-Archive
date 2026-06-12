---
title: "Disabling Power Management"
date: 2010-09-14
forum: General Help
---

### Post by SniperX103 on 2010-09-14
Ok.  I've got a freshly installed system with Ubuntu 10.04 64-bit on it.  I'm trying to figure out how to overclock with this and I'm having some issues because my Linux skills... well to be frank they suck.  I can navigate around fine, and I'm plenty used to go through a command line.  However, I just don't know about the backbone of this OS and all the different packages to be able to tweak things the way I like (hence why I'm here now :p).

I've setup the BIOS to a very slight overclock of 3.2GHz for my i7 which shouldn't be an issue at all.  Despite what my settings are set at in the BIOS, "cat /proc/cpuinfo | grep -i Mhz" always displays ~2800.  

After some searching, I was informed that Ubuntu comes with acpi-cpufreq by default, which I believe is a "limiter" so to speak.  

Is there a good, simple way to disable this?  Through research and the little help I've gotten elsewhere, I was told to find a setting called "Scaling_driver" and set it equal to none.  However, I have not found where this might be yet.  

Please let me know if you need any more information about this, because I want to get to the bottom of this.  I'd really like to know more about Ubuntu in general as I don't want to spend $200 to finally get a 64-bit OS.

---

### Post by dcstar on 2010-09-15
> **SniperX103 said:**
> Ok.  I've got a freshly installed system with Ubuntu 10.04 64-bit on it.  I'm trying to figure out how to overclock with this and I'm having some issues because my Linux skills... well to be frank they suck.  I can navigate around fine, and I'm plenty used to go through a command line.  However, I just don't know about the backbone of this OS and all the different packages to be able to tweak things the way I like (hence why I'm here now :p).

I've setup the BIOS to a very slight overclock of 3.2GHz for my i7 which shouldn't be an issue at all.  Despite what my settings are set at in the BIOS, "cat /proc/cpuinfo | grep -i Mhz" always displays ~2800.  

After some searching, I was informed that Ubuntu comes with acpi-cpufreq by default, which I believe is a "limiter" so to speak.  
............

No it isn't. Ubuntu will display the "official" clock rate of the CPU no matter what you do to it at motherboard level.

Many posts already exist pointing this out.

---

### Post by SniperX103 on 2010-09-15
> **dcstar said:**
> No it isn't. Ubuntu will display the "official" clock rate of the CPU no matter what you do to it at motherboard level.
 
Many posts already exist pointing this out.
 
Oh. If that is the case then, is there anyway to determine what exactly the CPU is running at (i.e. whether it be through programs or command line)?
 
My apologies about searching. I had searched on Overclocking and Disabling ACPI / Power Management. 
 
Didn't think that the cpuinfo might be sticking with the standard.
 
EDIT:  Nevermind.  I'll just give a couple programs I found through Google a shot later tonight (like Perlmon).

---

