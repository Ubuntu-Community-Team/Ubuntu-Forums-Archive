---
title: "Ubunto wont recognize my TV"
date: 2010-11-11
forum: General Help
---

### Post by Skumleren on 2010-11-11
Hello all
I have been trying to connect my TV to my ubuntu desktop for a while now.
When i start up, the image from the desktop is shown fine on the TV right up until the ubuntu startup image. At that point the image disappears and doesnt return.
GRUB and all the startup text is shown fine on the TV but after ubuntu starts, the tv just says "no signal".

Im using a ATI Radeon X800 "Old crap" craphics card.
I assume it is because my graphics card does not have the drivers for it installed properly, so i tried that through the package manager along with the catalyst control center. When i tried to open catalyst it gives the message "There was a problem initializing Catalyst Control Center linux edition. It could be caused by the following
No ATI graphics driver is installed or the ATI driver is not functioning properly
Please install the ATI driver appropriate for your ATI hardware, or configure using ATI config"
When calling aticonfig from the terminal, it says No supported adapters detected.

I have no idea where to go from here, the tv does not appear in displays either. My Medion 17' screen is properly identified in Display though (It does not say unknown or anything)

Anyways, HELP!:)

---

### Post by Sylos on 2010-11-11
Hello there.
Sadly the ATI Radeon X800 is not supported by the ATI drivers anymore and the old driver version wont run on any ubuntu higher than 8.10 (now end of life). I have the same problem with one of my graphics cards. I fear that you wont get a resolution to this.

However, I have found that if I run with the default settings (remove the packages you install through the Restricted Drivers section) then as long as the TV is turned on at boot it will display to both the monitor and TV. The resolution is wrong for the monitor and the refersh rate wrong for the TV but it does allow me to watch movies (the only thing I use it for).

Sorry to bring the bad news.

You could always pick up another supported card - you can get old Geforce FX5200s pretty cheap on ebay these days and the NVIDIA support is much better for the old cards.

Hope this helps.

---

### Post by Vigh on 2010-11-11
proprietary drivers seem to be less usable then open-source graphics, faster but nowhere near as stable, I don't use proprietary drivers unless I am 100% certain they will work properly, currently I have 2 laptops using open-source graphics, 1 desktop using open source graphics, and 1 desktop where the proprietary drivers actually work, which is pretty sad on behalf of the companies writing the driver code

---

