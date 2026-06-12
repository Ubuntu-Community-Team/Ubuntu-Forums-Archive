---
title: "ubuntu install questions"
date: 2006-04-24
forum: General Help
---

### Post by thunderfox933 on 2006-04-24
hey sorry for all the questions 

During the ubuntu install do install grub to the MBR or to the ubuntu partition.

---

### Post by aysiu on 2006-04-24
MBR.

Otherwise, something else has to be installed to the MBR, and if that something else is Windows, you're going to have to go through a lot of trouble to get Windows to recognizer Ubuntu and boot to it.

Grub on the MBR will almost always automatically add Windows to the boot menu, and if it doesn't, it's not as difficult to add Windows in manually.

---

### Post by thunderfox933 on 2006-04-24
ok thanks

---

### Post by pitkali on 2006-04-24
[QUOTE=aysiu]Otherwise, something else has to be installed to the MBR, and if that something else is Windows, you're going to have to go through a lot of trouble to get Windows to recognizer Ubuntu and boot to it.[/QUOTE]
Just for the record:

You can install GRUB into a linux partition and use standard IPL code for MBR. Then you set your Linux partition as a bootable one (I think that requires using primary partition for linux root filesystem).

That can be useful to have at the same time:
1. Windows
2. Linux
3. Multimedia add-on for fujitsu-siemens laptops, which installs some bits in MBR in order to allow fast boot with special key.

Regards,

---

