---
title: "broadcom 57780 supported in kernel 2.6.35"
date: 2010-08-15
forum: General Help
---

### Post by bprins on 2010-08-15
Hi,

Just upgraded my kernel to 2.6.35 and now my broadcom 57780 WLAN card is not recognized. Trying to reload the proprietary driver fails. 

Anybody else with this specific card got it working on 2.6.35?

Thanks.

Bas

---

### Post by ubun_two on 2010-08-15
I don't have that specific card, but I have a broadcom wireless card.

You need to apply the patches that you can find here:

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Steps I did:
1, Boot into a previous kernel and make sure that your wireless works.
2, Remove 2.6.35 through Synaptic.
3, Download and apply the patches.
4, Re-install 2.6.35 again.

---

