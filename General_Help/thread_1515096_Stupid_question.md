---
title: "Stupid question"
date: 2010-06-21
forum: General Help
---

### Post by primevci on 2010-06-21
I have a ati radeon 4650 AGP and when i go to slect the driver for linux it dosent show a linux driver but when i select pcie version of my card it list a driver for linux has anyone else noticed this?

---

### Post by Leppie on 2010-06-21
i'm not quite sure what you're talking about. is this about the download section on the ati page?
have you tried ubuntu's jockey? System>Administration>Hardware Drivers.

---

### Post by primevci on 2010-06-21
yeah i am running that driver.. but i think its 2 versions old... from what i read.. was jsut trying to get the latest and greatest is all jsut confuses me there is a linux driver for pcie and not agp and i jsut bought this card new...

---

### Post by warfacegod on 2010-06-21
As a general rule with ATi cards, it's best to just use the "Recommended" driver available in Hardware Drivers (Jockey).

---

### Post by Leppie on 2010-06-22
> **warfacegod said:**
> As a general rule with ATi cards, it's best to just use the "Recommended" driver available in Hardware Drivers (Jockey).
yes, the ati and nvidia drivers usually are older versions if you're looking for supported drivers. if you want the latest versions (bleeding-edge), they're most likely to be somehow incompatible and cause issues so this usually is not recommended.
if you want to use newer drivers, you could try to activate the backports repo, go to Administration>System>Software Sources>Updates. as you can see, backports are unsupported though. it means that whatever you install from there is likely to break your system, so beware.

---

