---
title: "Newbie installing new video card"
date: 2010-05-13
forum: General Help
---

### Post by iridium21 on 2010-05-13
I'm about to install a 'new' ATI Radeon video card into a Ubuntu 10.04 computer of mine (an ASUS A7VT) that has VIA onboard graphics. My question is, how will Ubuntu deal with this? Will it automatically download the required drivers or would I be better off with a fresh install after I've put the card in?

Many thanks!

---

### Post by cascade9 on 2010-05-13
Ifyou've installed any drivers for the VIA video, then you would do best to remove them before you install the ATI card. 

Ubuntu wont automatically install the drivers for the ATI card, you will need to install them yourself, with synaptic, or jockey (System-> Administration-> Hardware drivers). 

BTW- the A7VT only has AGP and PCI slots, so your new ATI card must be AGP or PCI. PCI cards can be most anything, but as far AGP- the majority of the ATI AGP cards no longer have support from the offical ATI flxgr drivers. You might have to use the opensource ATI radeon driver, depending on what model card you have.

---

### Post by iridium21 on 2010-05-13
> **cascade9 said:**
> Ifyou've installed any drivers for the VIA video, then you would do best to remove them before you install the ATI card. 

Ubuntu wont automatically install the drivers for the ATI card, you will need to install them yourself, with synaptic, or jockey (System-> Administration-> Hardware drivers). 

BTW- the A7VT only has AGP and PCI slots, so your new ATI card must be AGP or PCI. PCI cards can be most anything, but as far AGP- the majority of the ATI AGP cards no longer have support from the offical ATI flxgr drivers. You might have to use the opensource ATI radeon driver, depending on what model card you have.

Thanks for the reply. This is on a second (old) machine that I'm trying out Ubuntu on. Yeah, the card is a Sapphire Atlantis RADEON 9000 Pro, 128 MB AGP. The PCI slot is taken by a WiFi card. Are drivers available for this ok? Also, how would I uninstall the VIA drivers because I can't see reference to them on System-> Administration-> Hardware drivers?

Thank you.

---

### Post by Talon2 on 2010-05-13
> **cascade9 said:**
> 

Ubuntu wont automatically install the drivers for the ATI card.

This statement is not necessarily true.  Ubuntu will install drivers for all ATI video chipsets that are supported by the open source driver and that amounts to a lot of chipsets.

If you are installing an older card like a 9000, you should just let Ubuntu use the open source driver which it automatically will.

---

### Post by iridium21 on 2010-05-13
> **Talon2 said:**
> This statement is not necessarily true.  Ubuntu will install drivers for all ATI video chipsets that are supported by the open source driver and that amounts to a lot of chipsets.

If you are installing an older card like a 9000, you should just let Ubuntu use the open source driver which it automatically will.

Ok, I'll try that, thank you. Now what about the VIA drivers? How do I uninstall them first?

---

### Post by Talon2 on 2010-05-13
> **iridium21 said:**
> Ok, I'll try that, thank you. Now what about the VIA drivers? How do I uninstall them first?

How did you install them?

---

### Post by iridium21 on 2010-05-13
> **Talon2 said:**
> How did you install them?

:confused: I didn't. They were installed along with Ubuntu.

---

### Post by Talon2 on 2010-05-13
> **iridium21 said:**
> :confused: I didn't. They were installed along with Ubuntu.

Then you shouldn't need to uninstall them.

---

### Post by cascade9 on 2010-05-14
> **Talon2 said:**
> This statement is not necessarily true.  Ubuntu will install drivers for all ATI video chipsets that are supported by the open source driver and that amounts to a lot of chipsets.

If you are installing an older card like a 9000, you should just let Ubuntu use the open source driver which it automatically will.

True. I meant 'ATI drivers', not the opensource drivers, you dont need to install/uninstall the open source drivers. 

Which is why you dont need to uninstall the VIA drivers iridium21, they would be the open source VIA drivers (I only even said to remove the VIA drivers because I'm sure that at some time there was binary blob drivers for the VIA video cards...its been so long since I used one that I dont know if they are still being updated or used at all).

---

