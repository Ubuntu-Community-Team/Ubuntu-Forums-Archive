---
title: "Just lost wireless after update"
date: 2011-03-03
forum: General Help
---

### Post by davepoth on 2011-03-03
Hi all. Just restarted after the update today and Ubuntu has lost all of the wireless functionality in the network manager. Any ideas where it might have gone?

Looking a bit deeper, it appears that my Eth1 (which was the wireless adaptor) had disappeared. I went and checked the additional drivers, and the Broadcom driver had been removed. I'm reinstalling it now. I did do some housekeeping after the update (as I always do when the Kernel bumps) so did apt-get clean, Autoremove and Autoclean.

-edit-

That worked. Odd that they got removed though.

---

