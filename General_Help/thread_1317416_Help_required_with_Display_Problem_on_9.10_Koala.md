---
title: "Help required with Display Problem on 9.10 Koala"
date: 2009-11-06
forum: General Help
---

### Post by opm595 on 2009-11-06
Hi Guy's

I've just installed 9.10 amd64, on a brand new machine and I seem to be having a real headache trying to find the right monitor drivers. The machine was advertised as having a the following basic specs:
- ASUS MOTHERBOARD:512MB NVIDIA GeForce 7050 VGA ONBOARD
- Supports Intel 45 nm multi-core processors
- FSB 1333/1066/800/533 MHz
- DDR2 800(OC)/667/533
- NVIDIA GeForce 7050 / nForce 610i
- Integrated NVIDIA CineFX 3.0 graphics
- 4 x SATA 3Gb/s with RAID function
- 8-channel High Definition Audio
- 5000hrs VRM Solid Capacitors 

However, on doing the following in a terminal:
```
~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)
```

Does this mean that I have purchased something not as advertised? I'm quiet green on this, but shouldn't a 'lspci | grep VGA' give me something in reference to Nvidia?

For the record I'm using an older style, Compaq P1220 monitor, and cannot get a resolution of more then 800 x 600.

If someone could shed some light on this or point me in the right direction as to what I should do from here, it would be very much appreciated.

Thanks in advance.
Regards,
Rob

---

### Post by PRC09 on 2009-11-06
What is the model number on the Asus motherboard,and if you do have the Nvidia on board see here:

[https://bugs.launchpad.net/ubuntu/+source/nvidia-kernel-common/+bug/195139](https://bugs.launchpad.net/ubuntu/+source/nvidia-kernel-common/+bug/195139)

The link is dated 2008 so it might not apply any more......
Hope this helps...

---

### Post by opm595 on 2009-11-10
Thanks for the reply.
Unfortunately, my suspicions were correct. The person who sold me this machine, did not include a Nvidia GeForce 7050 VGA. 
Therefore there is only what is integrated with the motherboard:
ASUS P5KPL-AM/PS

From reading a few tech reports I think I might be beating a dead horse here.
Maybe I'm just going to have to bite the bullet and purchase an Nvidia card (which the seller of this machine advertised as included. And who has, typically, vanished with no contact after I inquired about the missing Nvidia GeForce). 

Seeing I'm going to buy this video card anyway, should I stick with looking for a GeForce 7050 or has anyone have a better recommendation.

Many thanks,
Rob

---

