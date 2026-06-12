---
title: "Triple Screen on two Graphics cards."
date: 2010-11-23
forum: General Help
---

### Post by loxaXcracker on 2010-11-23
Hello.

I have an HP Pavilion a6230 that has an onboard Intel GMA X3100 and a PCI Nvidia 8500GT (512mb).

//Edit: Forgot to mention that I'm using Ubuntu 10.04

So far I had no problems with my dualscreen (LG Flatron through HDMI and an old HP 1702 monitor through DVI(VGA2DVI adapter)) using Nvidia's auto xconfigurator on just my 8500GT.

I now want to connect an a third (IBM) monitor through the VGA port on the onboard graphics card. 

My research brought me to the conclusion that it is possible to use multiple graphics cards by different manufacturers and have multiple displays (Nvidia+Intel with 3 monitors HDMI,DVI,VGA in my case)
(Please don't tell me that this is only possible with SLI and Crossfire as there people reporting doing the same thing with non SLI/CF too)


Can someone help? Should I include my current xorg.conf and "lspci -vv" output?

---

(2)

It may be possible that my motherboard chooses a primary adaptor and automatically disables the secondary. Poking around in BIOS didn't help at all, though that still doesn't mean that something can't be done about it.
If however this is true, can I use a DVI to 2x VGA splitter and still get the same effect?
Please note that I don't want my monitors to display the same content, but rather have them work as 1 big/split monitor (not 3 screens with the same view).

Thanks in advance.

---

