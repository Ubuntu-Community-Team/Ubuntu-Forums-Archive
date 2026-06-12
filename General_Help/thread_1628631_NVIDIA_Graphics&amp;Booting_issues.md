---
title: "NVIDIA Graphics&amp;Booting issues"
date: 2010-11-22
forum: General Help
---

### Post by Rsjc741 on 2010-11-22
Heres the main problem in case you can elaborate without reading on:
When booting my computer, GRUB boot loader launches fine. When booting into Ubuntu 10.10, it starts to launch fine until a bit after
> Checking battery state... [OK]
After that, my screen turns a rainbow of colorful pixels with a majority being black.


More in depth:

Specifications:
Gateway 420GR- [http://support.gateway.com/s/PC/R/4053/4053sp3.shtml](http://support.gateway.com/s/PC/R/4053/4053sp3.shtml)
1278MB RAM
Pentium IV Processor @ 2.93GHz
NVIDIA GALAXY GeForce GT 240 (512MB DDR5 variant) on PCI-E 1.0 slot
Integrated RAMDAC
No internet connection (Ndiswrapper fails to install)


When using Recovery Console:
Failsafe graphics mode works wonderfully.
when trying to make changes to my graphics config in the recovery console, it does nothing and takes me back to the screen i was just on.
trying to start x-server just messes up my screen with a similar effect to the previous issue.
The x-server log states that it can find a "appropriate" driver and uses it. After reviewing the list of the cards it supports, my own is not on that list.
Everything else on the recovery console either is N/A or doesn't work. 

Installing the drivers from NVIDIA's .RUN file:
When I try and please it (sudo init, service xserver stop) it ends up giving me multiple errors.

Though I have installed Ndiswrapper and the NVIDIA driver before (without this problem), it seems now that it doesn't like to complete my requests.

I do not own a LAN cable, nor do I have the intention of breaking down and assembling my computer in a crammed area to access the internet.
buying one is also out of the question, so please, no comments about how easy this would be to install with internet. I'm fully aware of that.

If anyone can point me in the right direction, or better yet explain to me what steps to take to install my NVIDIA driver, that would be awesome.

Thanks, 
John.

Edit: pictures of the pixelation and when installing the NVIDIA driver in Terminal soon to come.

---

