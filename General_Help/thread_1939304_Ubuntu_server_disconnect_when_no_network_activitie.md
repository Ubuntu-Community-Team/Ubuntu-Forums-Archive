---
title: "Ubuntu server disconnect when no network activities"
date: 2012-03-11
forum: General Help
---

### Post by kinju on 2012-03-11
Hi all,

I have an Ubuntu Server, and when I don't use the network, it disconnects..

I have to go to the server and make :
sudo ifdown -a
sudo ifup -a

to retreive the network accessibility..

Is there is something to configure somewhere ?

Thank you all,
Kin

---

### Post by 2F4U on 2012-03-11
Is the ethernet card configured to go to sleep mode? Many modern BIOS versions have such a setting.

---

