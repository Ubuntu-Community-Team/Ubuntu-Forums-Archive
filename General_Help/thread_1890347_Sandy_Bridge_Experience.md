---
title: "Sandy Bridge Experience"
date: 2011-12-03
forum: General Help
---

### Post by carranty on 2011-12-03
I'm thinking of buying a new computer with a sandy bridge processor (specifically an i5 2500k).  When these first came out people couldn't boot into linux, has this changed with the newer versions?  I'm just wondering if anyone here has such a processor, and if so how they are finding it with Ubuntu (or any version of Linux).

---

### Post by 3Miro on 2011-12-03
> **carranty said:**
> I'm thinking of buying a new computer with a sandy bridge processor (specifically an i5 2500k).  When these first came out people couldn't boot into linux, has this changed with the newer versions?  I'm just wondering if anyone here has such a processor, and if so how they are finding it with Ubuntu (or any version of Linux).

Sandy Bridge comes with two components, the CPU and GPU. If you are going to use a dedicated Nvidia or ATI card, then Sandy Bridge is just like any other CPU out there. 

If you are going to use their graphics, then you need kernel at least 2.6.37 (i.e. Ubuntu 11.04 or newer). I have a Sandy Bridge laptop with Intel graphics and it runs just fine, no problems or whatsoever (on 11.04 and 11.10, 10.10 doesn't even boot).

---

### Post by Basher101 on 2011-12-03
> **carranty said:**
> I'm thinking of buying a new computer with a sandy bridge processor (specifically an i5 2500k).  When these first came out people couldn't boot into linux, has this changed with the newer versions?  I'm just wondering if anyone here has such a processor, and if so how they are finding it with Ubuntu (or any version of Linux).

I bought myself a gaming rig with:
i5 2500k CPU
MSI Z68A-GD65 (G3) Motherboard
Gigabyte GTX 570 (Overclocked, NOT the super overclocked)
Alpenföhn Himalaya CPU cooler
Corsair Vengeance 2x4 GB Dualchannel DDR3 1600 MHz CL9 RAM
Samsung 1,5 TB HDD
Be quiet! Straight Power BQT-E9 700 W Power supply

it will arrive about next week, then i will assemble it. I wont fiddle around with it much at first tho, as i still have school so i will do it at the weekend. Stay tuned..

---

### Post by carranty on 2011-12-03
> **3Miro said:**
> Sandy Bridge comes with two components, the CPU and GPU. If you are going to use a dedicated Nvidia or ATI card, then Sandy Bridge is just like any other CPU out there

Ah OK, I'll definitely be using a dedicated card.  Thanks.

---

### Post by Basher101 on 2011-12-03
> **carranty said:**
> Ah OK, I'll definitely be using a dedicated card.  Thanks.

For windows there is software that lets you use BOTH GPUs of the CPU and discrete card at the same time (its called Lucid Virtu). I have not looked if it is available for ubuntu or linux in general...also the software works only on motherboards with the Z68 chipset.

---

### Post by 3Miro on 2011-12-03
> **Basher101 said:**
> For windows there is software that lets you use BOTH GPUs of the CPU and discrete card at the same time (its called Lucid Virtu). I have not looked if it is available for ubuntu or linux in general...also the software works only on motherboards with the Z68 chipset.

Under Linux you can only use one of the card. There is some software for switching between integrated and dedicated cards, but it is experimental at best. You should just disable the integrated card from BIOS and go for the dedicated card.

---

### Post by Basher101 on 2011-12-03
> **3Miro said:**
> Under Linux you can only use one of the card. There is some software for switching between integrated and dedicated cards, but it is experimental at best. You should just disable the integrated card from BIOS and go for the dedicated card.

yes that would be the best thing for ubuntu.

The switching is quite better managed with Lucid Virtu, tho. When you plug your Video cable to your CPU video output, it will shut down the dedicated card when you do not run anything graphically demanding. If you plug your video cable to your dedicated card, it uses the CPU GPU for additional video encoding. It is a nice feature to have, also power saving, but you can always switch within the BIOS..

---

### Post by Basher101 on 2011-12-03
> **3Miro said:**
> Under Linux you can only use one of the card. There is some software for switching between integrated and dedicated cards, but it is experimental at best. You should just disable the integrated card from BIOS and go for the dedicated card.

yes that would be the best thing for ubuntu.

The switching is quite better managed with Lucid Virtu, tho. When you plug your Video cable to your CPU video output, it will shut down the dedicated card when you do not run anything graphically demanding. IF you plug your video cable to your dedicated card, it uses the CPU GPU for additional video encoding performance. It is a nice feature to have, also power saving, but you can always switch within the BIOS..

---

