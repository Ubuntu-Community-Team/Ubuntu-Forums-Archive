---
title: "Is There Any Wat To Uninstall Last Updates?"
date: 2010-07-09
forum: General Help
---

### Post by matey3 on 2010-07-09
Hello All:

I installed the latest updates last night (It came up automatically on the screen and I clicked the Update). Now I am having problems mainly my wireless network keeps connecting/disconnecting then sometimes asks for the password/key for the router etc.

The system also got hung today and had to hard boot.

I am pretty sure one or some of the updates is responsible for this rather annoying problem, but I do not know how to undo the latest updates?
The original install could not even pick up the wireless bcs it is a RealTek RTL8191SE NIC and this particular NIC had problems with Linux drivers! It started to work by itself after the 2nd or 3rd update.



I am using Ubuntu 10.4 TLS
uname -a:
Linux ubuntu 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 08:03:28 UTC 2010 x86_64 GNU/Linux


Thanks in advance!
Regards;

---

### Post by matey3 on 2010-07-09
BTW the sudo apt-get remove update does not work?
if I do apt-get autoremove it will remove a few other python related programs which are no longer in use but not the updates.

---

### Post by BikeHelmet on 2010-07-09
Check Synaptic. It maintains a history of all the packages that get updated. You can select those packages and revert to older versions, then lock them.

---

