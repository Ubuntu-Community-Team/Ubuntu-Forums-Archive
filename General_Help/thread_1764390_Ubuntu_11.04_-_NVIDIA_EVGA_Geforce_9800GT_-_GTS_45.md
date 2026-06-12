---
title: "Ubuntu 11.04 - NVIDIA EVGA Geforce 9800GT - GTS 450"
date: 2011-05-21
forum: General Help
---

### Post by Tom Shaw on 2011-05-21
:o:PThe same applies to both cards.

NVIDIA EVGA Geforce 9800GT
NVIDIA EVGA Geforce GTS 450

Ubuntu 11.04 installs perfectly in 1280x1024 resolution. After installation I'm told it appears I do not have the required hardware to run Unity. I install the latest NVIDIA drivers version 270.41.19 either thru the command line apt-get install nvidia-current or thru Synaptic manager or download them from the NVIDIA web site and manually install and Ubuntu breaks completely. At this point Ubuntu fails to boot and I have to use GRUB recovery failsafe mode which sometimes also fails. Unity support tests say that my card is not blacklisted but is not supported. I've attempted several dozen fresh installs using both cards using tips I've found on Google to get the system working but all attempts have failed. I'm running a dual boot system, on one hard drive is Windows 7 the other Unbuntu 11.04. The GRUB boot manager gives me the option to boot either OS needless to say everything in Windows runs perfectly. My hardware is as follows,

Thermaltake Armor+ MX
iNTEL DP45SG QuadCore 2.66
Corsair XMS3 2x 4GB, PC12800, 1600MHz
2 Western Digital Green Caviers 500gig

---

### Post by Hedgehog1 on 2011-05-21
When you say 'fails to boot', are you by any chance seeing a black screen with a blinking cursor in the upper left?

---

### Post by Tom Shaw on 2011-05-21
That's correct. The xorg log reports the gpu could not be initialized.

---

### Post by Tom Shaw on 2011-05-21
You can add another NVIDIA card to the list, spent an hour trying my wifes NVIDIA 9500 GT with no luck. Exactly the same thing is happening with all three cards. All three work perfectly in windows all three fail miserably in Ubuntu.

---

### Post by Tom Shaw on 2011-05-21
Black screen or blank screen with a rectangle where the grub menu was.

---

### Post by blueridgedog on 2011-05-21
I have an evga 9800 gt that I bought specifically for linux and have had great success with it using the nvidia drivers.  There may be some other issue at play as the 9800 is pretty basic and well supported.

---

### Post by Tom Shaw on 2011-05-21
I had a Hauppauge WinTV-HVR-1600 Installed. I took the card out ran and installed from Additional Drivers the current NVIDIA accelerated graphics driver and it work immediately.

---

### Post by wildmanne39 on 2011-05-22
> **Tom Shaw said:**
> I had a Hauppauge WinTV-HVR-1600 Installed. I took the card out ran and installed from Additional Drivers the current NVIDIA accelerated graphics driver and it work immediately.
Hi, thats great would you please go to the top of the page and mark this thread solved be clicking on forum tools. Thank you so much.):P

---

### Post by blueridgedog on 2011-05-22
> **Tom Shaw said:**
> I had a Hauppauge WinTV-HVR-1600 Installed. I took the card out ran and installed from Additional Drivers the current NVIDIA accelerated graphics driver and it work immediately.

Curious to see the results of trying to add the tv card back in now.  It must have created some sort of conflict.

---

### Post by jcd29 on 2011-06-01
So Tom, is the GTS 450 working fine now? Proprietary drivers, Unity showing up correctly, etc?

---

### Post by AntontheGreek on 2011-08-22
the hauppage 1600 requires vmalloc set to 512 with an Nvidia card

[http://www.mythtv.org/wiki/Common_Problem:_vmalloc_too_small](http://www.mythtv.org/wiki/Common_Problem:_vmalloc_too_small)

---

