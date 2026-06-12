---
title: "Confused about which video card I'm using"
date: 2010-05-12
forum: General Help
---

### Post by jacatone on 2010-05-12
I'm running Ubuntu 9.10 on an older Compaq Evo D310. When I do a search of my video card I get "01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 Pro Ultra TF", which is the integrated card on the motherboard, but I'm actually using an Nvidia GeForce 2 MX 400. At least that's the card my VGA monitor is connected to. How do I get Ubuntu to recognize the Nvidia card? I'd like to try installing an nvidia legacy driver for it to boost performance. Thanks.

---

### Post by 3rdalbum on 2010-05-12
> **jacatone said:**
> I'm running Ubuntu 9.10 on an older Compaq Evo D310. When I do a search of my video card I get "01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 Pro Ultra TF", which is the integrated card on the motherboard, but I'm actually using an Nvidia GeForce 2 MX 400. At least that's the card my VGA monitor is connected to. How do I get Ubuntu to recognize the Nvidia card? I'd like to try installing an nvidia legacy driver for it to boost performance. Thanks.

Turn off the onboard graphics in the computer's BIOS.

Then go to System > Administration > Hardware Drivers.

---

### Post by jacatone on 2010-05-13
Tried that already, still shows the ATI integrated video. I'm using the added Nvidia card because it works with the nvidiafb driver. Is there a way to disable the nvidiafb driver and install the nvidia-legacy one instead?

---

