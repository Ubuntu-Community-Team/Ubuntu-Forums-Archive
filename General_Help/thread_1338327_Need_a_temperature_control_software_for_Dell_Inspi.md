---
title: "Need a temperature control software for Dell Inspiron 8600"
date: 2009-11-26
forum: General Help
---

### Post by anikondemand on 2009-11-26
I'm using Dell Inspiron 8600 with ubuntu 8.04.
The temperature of my laptop is rising when I login to ubuntu.

Any software to control temperature/fanspeed according to rise in temperature?

---

### Post by anikondemand on 2009-11-26
Any help?

---

### Post by SR_ELPIRATA on 2009-11-26
What exactly are you looking for?

There is a package (lm-sensors) which in some systems allows you to see the CPU temp and fan status from many of the avaible tools but is chipset dependent. But it will just inform you (far as I know) what the temp/rpms is not adjust the CPU so that it doesnt get much hotter.

The other option I've used is the CPU scaling. I have an Amd x2 CPU and there's a bios setting that allows me to scale back the CPU from within Ubuntu. Once that thing is activated in the bios you can add the CPU scaler in the panels (I had set 2, one for each core) and then you can select at which speed you want to run the CPUs. For example, this is the Amd X2 Black Edition 7750, so it runs at 2.7Ghz, thats full speed, so, whenever I wanted to reduce the temp... I would just set them both to 1.4Ghz.

In my case, my motherboard chipset didnt allow me to see the temp or rpms, far as I could adjust (in my short experience) was to scale back both cores so I knew it wasnt to produce much heat, but I didnt have a clear indicative that in fact it was happening, although in theory they were obviously.

There's a HOWTO install the lm-sensors package, just do a search.

ELP

---

### Post by anikondemand on 2009-11-27
> **SR_ELPIRATA said:**
> What exactly are you looking for?

There is a package (lm-sensors) which in some systems allows you to see the CPU temp and fan status from many of the avaible tools but is chipset dependent. But it will just inform you (far as I know) what the temp/rpms is not adjust the CPU so that it doesnt get much hotter.

The other option I've used is the CPU scaling. I have an Amd x2 CPU and there's a bios setting that allows me to scale back the CPU from within Ubuntu. Once that thing is activated in the bios you can add the CPU scaler in the panels (I had set 2, one for each core) and then you can select at which speed you want to run the CPUs. For example, this is the Amd X2 Black Edition 7750, so it runs at 2.7Ghz, thats full speed, so, whenever I wanted to reduce the temp... I would just set them both to 1.4Ghz.

In my case, my motherboard chipset didnt allow me to see the temp or rpms, far as I could adjust (in my short experience) was to scale back both cores so I knew it wasnt to produce much heat, but I didnt have a clear indicative that in fact it was happening, although in theory they were obviously.

There's a HOWTO install the lm-sensors package, just do a search.

ELP

Thanks for replying bro.

Actually I am not looking for a sensor, but for a fan controller in real time. There is a utility called Dell Inspiron Latitude/Precision fan control for Windows, which I am using in Windows to control my fan speed as per my requirement.
See [this]("http://www.diefer.de/i8kfan/index.html") link.

I just wanted to know if the same utility is available for linux.

---

