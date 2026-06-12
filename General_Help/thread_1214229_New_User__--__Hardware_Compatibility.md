---
title: "New User  --  Hardware Compatibility"
date: 2009-07-15
forum: General Help
---

### Post by +METHOS on 2009-07-15
As I am looking to reformat my Gateway FX7020 (Windows Vista Home Premium 32-bit), I recently discovered that the program I use for my business is supported/compatible with Linux  --  so I can finally make the long awaited transition to Linux for the first time! *(I have yet to reformat and install Linux.)*

I am currently running on an AMD Phenom 9600 Quad-core processor with 3 GB DDR2 Dual-Channel and an NVIDIA GeForce 8800GT -- will a 32-bit version of Linux suffice, and will I have problems finding driver support for my hardware?

As I am new to Linux, any suggestions/recommendations will be openly received and greatly appreciated.

Thank you.

---

### Post by t4thfavor on 2009-07-15
I have no issues with 64 bit, I would go that route if you ever plan on getting more ram. If not, 3gb will be just fine in a 32 bit OS.

---

### Post by coffeecat on 2009-07-15
A quick google for "Gateway FX7020" shows that its motherboard has an nvidia chipset (that's for the USB controller, SATA controller, ethernet, sound, etc), and since you also have an nvidia graphics chipset, that machine should work just fine with the hardware drivers that come with a default install.

But there's a simple way to test. Have you got yourself a live CD yet? If you have, simply boot up with the live CD and test all the hardware: ethernet connection, USB, sound, firewire (if you have firewire), and graphics of course. Plus anything else I've forgotten. Don't forget that with the live CD you'll be using the open-source 'nv' driver for the graphics, which is fine, but you won't get any fancy 3D effects - for which you'll need the proprietary driver which you can install easily and quickly once you've done a hard drive install.

One caveat: are you going to be using the onboard ethernet connection, or a wireless card? Wireless support is far better than it was a couple of years ago, but one or two chipsets are still problematic. If you are going to use wireless, test that with the live CD, and if you get any problems, just post back.

---

### Post by +METHOS on 2009-07-15
Thank you for taking the time to respond to my inquiries.

I was just going to ask about the LiveCD. I will certainly check that out first.

-Non-wireless.

Excellent forum, excellent help  --  thank you!

---

