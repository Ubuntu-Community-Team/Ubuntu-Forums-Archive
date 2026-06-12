---
title: "Kubuntu 11.04 won't boot also in recovery mode"
date: 2011-08-04
forum: General Help
---

### Post by gregor171 on 2011-08-04
I had many problems with installing kubuntu 11.04 on my laptop HP Elitebook 8560p and after downloading different iso everything works well, but sistem freezeout and would not reboot also in recovery mode that would load untill Recovery menu when system won't responde.

Any ideas?
Thanks,
Greg

---

### Post by WhiteHorse on 2011-08-04
Check your bios nrpe settings

---

### Post by gregor171 on 2011-08-04
I'm not sure what would that (nrpe) be but bios was unchanged. System freeze out after working with VirtualBox.

---

### Post by gregor171 on 2011-08-04
OK This is SOLVED and I don't believe that this can be still a problem in 11.04. Somehow I was loking into log and found that system had problems sice wireless button was off.

Basically I've done 2 thinks runing Kubuntu from USB:

1.
sudo swapoff /dev/sda5
( /dev/sda5 Swap partition)
sudo mkswap /dev/sda5


2. runing kubuntu from usb, I turned wireles ON!

works now!

---

