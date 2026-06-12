---
title: "How do I add a third monitor"
date: 2010-05-30
forum: General Help
---

### Post by darkgumby on 2010-05-30
I just installed Lucid. I have 2 video cards installed. One is an Nvidia GeForce 6800 GS. I have 2 monitors attached and both work perfectly. The 2nd card is an old Nvidia NV4 [RIVA TNT].
The 6800 is AGP, the NV4 is in a PCI slot.
I used the Nvidia X-Server Settings application to configure the working card and monitors. It does not show that the NV4 is even installed. What can I do to get the NV4 recognized and working?

---

### Post by rchille on 2010-06-01
I'm having the exact same problem but with ATI cards: one PCIe and one PCI. 

I can play with BIOS and either get the PCI card to work OR the PCIe card but not both at the same time (other monitors do not show up under System->Preference->Monitors). Doing a lspci shows both video cards though.

Anyone have suggestions on getting both cards working at the same time?

---

### Post by rchille on 2010-06-06
Just a quick follow-up:

I got most of the way there by building a xorg.conf file with the correct info for the monitors and vid cards.

---

