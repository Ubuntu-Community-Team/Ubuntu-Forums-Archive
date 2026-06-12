---
title: "modem not recognised....."
date: 2010-05-07
forum: General Help
---

### Post by muctadir on 2010-05-07
i recently bought a modem. its model is HUAWEI E1550. it is not recognized by ubuntu, but with windows it is working fine. there is an odd problem too. i am dual booting XP and LUCID. if i first boot to windows and use the modem for a while and restart my pc and boot to ubuntu(without removing the modem from usb), the modem works. but the modem does not work if i directly boot in ubuntu or remove the modem and replug it at the time of restarting. i tried wvdial. it also fails to recognize the modem.

please help me. i badly need it........

---

### Post by finlost on 2010-05-07
Have you tried:
System->Administration->Hardware Drivers

---

### Post by muctadir on 2010-05-07
i got the solution. just go to this [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/546728](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/546728)

---

### Post by bumanie on 2010-05-07
I have a E620 huawei that works with kernel 2.6.32-22. Before that kernel, i had to use usb_modeswitch or the development mainline kernel from [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/")

---

