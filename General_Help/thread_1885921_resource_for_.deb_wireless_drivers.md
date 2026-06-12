---
title: "resource for .deb wireless drivers ?"
date: 2011-11-24
forum: General Help
---

### Post by Tone303 on 2011-11-24
Lets say i want .deb installer for a laptop that doesnt have out-of-box wireless connection functioning and cant temporarily hook up a cable to get it either because the port is physically broken.

Lets say i find out the name of the driver, is there anything else to do besides google it? is there a specific format to type it in synaptic to find it better? is there a website somewhere that collects ubuntu wireless drivers? is there a such thing as a generic one that works for most? if so where is it as .deb only?

---

### Post by Script Warlock on 2011-11-24
> **Tone303 said:**
> Lets say i want .deb installer for a laptop that doesnt have out-of-box wireless connection functioning and cant temporarily hook up a cable to get it either because the port is physically broken.

Lets say i find out the name of the driver, is there anything else to do besides google it? is there a specific format to type it in synaptic to find it better? is there a website somewhere that collects ubuntu wireless drivers? is there a such thing as a generic one that works for most? if so where is it as .deb only? this might [help]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

---

### Post by gandaran on 2011-11-24
> Lets say i want .deb installer for a laptop that doesnt have out-of-box wireless connection functioning and cant temporarily hook up a cable to get it either because the port is physically broken
and what wireless chipsets would you be talking about?
.deb packages are only available for broadcom chipsets, you can install them from synaptic or if you don't have wired internet you can still get them from [ubuntu packages]("http://packages.ubuntu.com/").
other brands like ralink, realtek and atheros are open-source drivers already built-in the linux kernel, these brands also provide the linux drivers but only on source code format, you will need to compile the drivers.

---

### Post by Tone303 on 2011-11-24
> **gandaran said:**
> and what wireless chipsets would you be talking about?
.deb packages are only available for broadcom chipsets, you can install them from synaptic or if you don't have wired internet you can still get them from [ubuntu packages]("http://packages.ubuntu.com/").
other brands like ralink, realtek and atheros are open-source drivers already built-in the linux kernel, these brands also provide the linux drivers but only on source code format, you will need to compile the drivers.


Broadcom B43

---

