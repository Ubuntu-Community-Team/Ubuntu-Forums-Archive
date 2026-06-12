---
title: "So what does this mean for me?"
date: 2010-01-06
forum: General Help
---

### Post by Zyrtec on 2010-01-06
I contacted customer support of my motherboard about getting drivers installed, and this is what they sent me...

> Dear Customer


 The A790GXM-AD3 (V1.0/V1.0A)  is used  AMD® 790GX & AMD® SB750 , so far AMD don't have any plan release any Linux driver for desktop chipset motherboard, this board fully support Windows XP/Vista/Win7.


 I can't find Linux drive when I search AMD site as below

[http://www.amd.com/us/products/desktop/chipsets/7-series-integrated/Pages/amd-790gx-chipset.aspx](http://www.amd.com/us/products/desktop/chipsets/7-series-integrated/Pages/amd-790gx-chipset.aspx)
Other than the fact they couldn't speak English very well... I'm not sure what this means for me. I installed Ubuntu last night, and everything seems fine right now. The thing is, I'm pretty new with all this computer stuff, so I'm not sure what that means when it comes to my computer and what it might do later on. Can anyone who's more tech/computer/Ubuntu savvy help me out here?

Hi WWGHA :)

---

### Post by doas777 on 2010-01-06
never had need to install chipset drivers in any linux distro. do most of your onboard devices work(network, audio, video, etc)?

---

### Post by Zyrtec on 2010-01-06
Everything seems completely normal. I dunno about the video stuff, but I'm assuming it's working fine since I have 1440x990 resolution. Audio works fine when I plug in headphones (haven't set up speakers). So yeah... seems like everything just works (which is a good thing). 

I just had no idea if this meant anything bad for me at all :P

---

### Post by doas777 on 2010-01-06
I think you're in good shape. Happy ubuntuing!

---

### Post by Zyrtec on 2010-01-06
Thank you for the reply, and the info!

---

### Post by jocko on 2010-01-06
With linux you don't need any chipset/motherboard drivers. Most things on most motherboards (disc controllers, sound cards, network cards, usb/ata/pci/agp/pci-e controllers, memory controllers, etc., etc...) have open source drivers which are already part of the kernel. If it works, you have the correct driver.

Some graphic cards (intel and older ati cards) only have open source drivers, which are installed and used by default on supported hardware. Other graphic cards (all nvidia and newer ati cards [radeon hd2xxx and up]) needs a proprietary driver to work well.

You can see if there are proprietary drivers for any of your hardware in the driver manager (System-->Administration-->Hardware drivers), which also lets you download and install appropriate drivers if there are any available.

---

