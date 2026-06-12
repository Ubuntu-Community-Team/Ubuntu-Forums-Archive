---
title: "Problem with Gateway NV79 and Meerkat"
date: 2010-09-04
forum: General Help
---

### Post by iamthez on 2010-09-04
Hi, I have a Gateway NV79 laptop, and I've tried to install a couple of the Meerkat alphas and the beta through various means including USB drive, CDROM and dist-upgrade.

Whenever I try to boot the live environment, I get to the bootloader screen, and then my display turns off, and I never see any desktop or anything else. pretty much the same thing happened when I tried the dist-upgrade thing.

Here are the specs for my laptop:


Intel® Core™ i3-350M processor (3 MB L3 cache, 2.13 GHz, DDR3 1066 MHz, 35 W), supporting Intel® 64 architecture, Intel® Smart Cache

Mobile Intel® HM55 Express Chipset

Dual-channel DDR3 SDRAM support 
Up to 4 GB of DDR3 1066 MHz memory, upgradeable to 8 GB using two soDIMM modules5

Intel® Graphics Media Accelerator HD7 (Intel® GMA HD), 128 MB of dedicated system memory, Microsoft® DirectX® 10

Broadcom wireless card (I don't know what model)

I'm pretty sure the hard drive is SATA

Optiarc 8x DVD drive

Synaptics driver for touchpad

I've never had to worry about audio drivers... so I can't help you there. I suppose it's just standard hardware.


Thanks in advance for your help.

P.S. I have no problems whatsoever with Lucid.

---

### Post by ethan1701 on 2010-10-16
Hey,
Did you ever get this solved? I have a gateway NV7915u, and have had several issues with the 64bit version of lucid.
I just upgraded to Maverick, and am having the same issues with the screen being off. I found that the system is still up and running (Caps and num locks work), so I just go through the login screen blind.
I also found that closing the computer's lid, waiting a second and reopening it will make the screen go on.
I'm going to look for or file a launchpad bug for this. Once I do, I'll update this thread with a link to it.

Adjusting screen brightness also still does not work under Maverick 64 bit on this machine. Did you also encounter that?

-Ethan

---

### Post by ethan1701 on 2010-10-16
There's a bug for this on Launchpad: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/653985](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/653985)
Please sign in, and mark that it affects you too.
Looks like the issue is with the Intel video card.

-Ethan

---

### Post by whsutton on 2010-10-23
I have the same Machine NV79 and the same problem,any luck solving this issue?

---

### Post by JackAcid on 2010-12-20
Thanks for posting the link to the bug report. I normally run with a second monitor attached, so did not know about this until I  tried to run the laptop without it.

I also found that if I chose the **linux-2.6.32-25-generic** version at the grub menu I do not have the problem. I posted that comment in the bug report, don't know if it is significant.

---

