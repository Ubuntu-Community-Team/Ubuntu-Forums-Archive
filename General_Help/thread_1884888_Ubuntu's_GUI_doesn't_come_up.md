---
title: "Ubuntu's GUI doesn't come up"
date: 2011-11-22
forum: General Help
---

### Post by cohenguy1 on 2011-11-22
Hi,

My ubuntu's GUI doesn't come up. I only have a command line. 
I'm using Karmic.

When the computer boots, it shows:
uslpash: setting mode 1280x1024 failed
uslpash: setting mode 1152x864 failed
uslpash: setting mode 1024x768 failed
uslpash: setting mode 800x600 failed
usplash: using mode 640x480

Then command line comes up.

startx shows: "no screens found"

I have tried editing usplash.conf to the setting:
xres=640
yres=480

and then update-initramfs but it wasn't helpful.

booting from livecd doesn't show up gui either.

I think the problem is in the graphics card, but I'm not sure.

Anyone got an idea?

Thanks.

---

### Post by jjex22 on 2011-11-22
If the live cd fails too, it sounds like the graphics card may be the problem - try removing it and running the live cd with the monitor connected to your motherboard's video output to test.

Hope it helps!

---

### Post by cohenguy1 on 2011-11-22
how do I do that?

lspci | grep VGA shows:
00:02.0 VGA compatible controller : Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller (rev 07)

I tried to remove the nvidia* packages from the apt-get but it didn't work.

---

### Post by jjex22 on 2011-11-22
Sorry, I meant check it isn't a hardware failure - as the live cd should auto detect settings that will at least display basic resolution gui from boot. Try opening the pc and removing the graphics card from the PCIe slot, then connect the monitor cable to the motherboard video output - more than likely a VGA port. and seeing if the live cd works - if it does there's a problem with the card.

If you get the same issue for the live cd as a previously working install, it's pretty much bount to be hardware related.

---

