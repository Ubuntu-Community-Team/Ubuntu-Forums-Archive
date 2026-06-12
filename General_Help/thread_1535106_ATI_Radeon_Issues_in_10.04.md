---
title: "ATI Radeon Issues in 10.04"
date: 2010-07-20
forum: General Help
---

### Post by AlistairH on 2010-07-20
After my pc power supply gave up the ghost on Sunday, I've been installing 10.04 on a new machine.

I have a dual monitor setup with my main monitor capable of a resolutions of 1440x900 and my second monitor supports 1280x1024.

On my old machine, with a nVidia based card, has 9.10 and quite happily displays each monitor in it's native resolution using the propriety drivers.

My new machine has a Radeon X300/X550/X1050 Series card (as reported by Windows 7 which was installed on the machine when I got it). I'm not sure exactly which model.

I've installed 10.04 on it and, using the inbuilt drivers, can only get both screens to display something if I set the resolution of the widescreen monitor to the same as the second one, i.e 1280x1024 resulting in a distorted image. It's usable, but not ideal.

I suppose I could remove it and install the nVidia one, but I'm reluctant to do that as it is a PCI based older model and I'm not sure if 10.04 will support it, while the Radeon is PCI Express based.

My understanding is that the new drivers in 10.04 do not use xorg.conf. There certainly doesn't seem to be such a file on the system.

Before I start mucking about with the innards, does any one have any suggestions how I can get both monitors displaying their native resolutions while being able to show different content. i.e. not mirrored?

Thanks in advance.

---

### Post by techunit on 2010-07-20
Well actually the ati radion card you have installed isn't very powerfull... So purhaps you should try the nvidia card...

---

### Post by AlistairH on 2010-07-20
I don't need a powerful video card, just dual monitor capabilities. I don't play games, don't do intensive graphic work and don't use Compiz.

---

### Post by dcstar on 2010-07-21
> **AlistairH said:**
> 
.........
Before I start mucking about with the innards, does any one have any suggestions how I can get both monitors displaying their native resolutions while being able to show different content. i.e. not mirrored?

Thanks in advance.

You install the Hardware Drivers (if they are available) and then install the **fglrx-amdcccle** package.

---

### Post by cascade9 on 2010-07-21
No hardware ATI drivers for that card in 10.04, the ATI 'x-xxx' series cards had support dropped a fair while ago. 

All there is for those cards are the open source drivers. 

> **AlistairH said:**
> I suppose I could remove it and install the nVidia one, but I'm reluctant to do that as it is a PCI based older model and I'm not sure if 10.04 will support it, while the Radeon is PCI Express based.

Ubuntu 10.04 supports PCI video just fine.

---

### Post by AlistairH on 2010-07-21
OK chaps, looks like I'll have to swap the cards.

Thanks again.

---

### Post by clhsharky on 2010-07-21
AlistairH

grandr should help you, check it out
```
grandr
```

sharky

Works on ATA Radeon X550 for me

---

