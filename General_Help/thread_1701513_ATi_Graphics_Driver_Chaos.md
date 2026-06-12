---
title: "ATi Graphics Driver Chaos"
date: 2011-03-06
forum: General Help
---

### Post by beetleman64 on 2011-03-06
I own a computer with an ATi Radeon Xpress 200 integrated graphics chip (yes, I am aware of everything that entails). Anyway, I tried installing the proprietary ATi driver using this tutorial and now I can't get any 3D effects and Flash is even worse than before.
[http://www.ubuntugamer.com/2010/10/how-to-install-the-latest-proprietary-graphics-driver-in-ubuntu/](http://www.ubuntugamer.com/2010/10/how-to-install-the-latest-proprietary-graphics-driver-in-ubuntu/)
I have run an update and it came up with a long list of updates which I installed, but to no avail.

I'm aware all this was probably a mistake so can I ask for either
a) how to reverse what I've done or
b) how to make the proprietary driver work for me (if possible)

I realise that I have been/am being quite stupid here so I thank anyone who can help in advance.

---

### Post by lithopsian on 2011-03-06
Have you tried the open source driver?  Often it is just a case of trying different driver versions until you get one that works well for you.  Have you tried the Gallium open source drivers?

---

### Post by cottfcfan on 2011-03-06
I had a look here on the ATI website and I don't think your card is supported.
[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)
If you find out differently you are best following this guide:
[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide)

---

### Post by beetleman64 on 2011-03-06
Hmm, seems you're right about the card not being supported. Failing that, anyone got any ideas on how to get back to using the open source driver (yes, I am aware of just how dim a question that is, but I seriously don't know)?

*edit: The open source driver worked acceptably well, I just thought the proprietary driver would be better. Oh, the minefield of Ubuntu graphics drivers...*

---

### Post by coffeecat on 2011-03-06
> **beetleman64 said:**
> Failing that, anyone got any ideas on how to get back to using the open source driver

Here you go:

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

Personally I'd go with the belt and braces "Problem:  Need to fully remove -fglrx and reinstall -ati from scratch" option. It won't do any harm to do everything.

Good luck with that!

---

### Post by beetleman64 on 2011-03-06
@coffeecat
Thank you so much. Things are nice again!

---

