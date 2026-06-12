---
title: "Suspend makes /home readonly"
date: 2009-08-25
forum: General Help
---

### Post by fishyf on 2009-08-25
Hi,
When my Jaunty installation wakes up from suspend to RAM, my home partition becomes readonly. The root file system stays writable.

My home partition is a little unusual; it is an ext4 filesystem which is encrypted using luks and resides on an SDHC card.

If the same SDHC card is used on an eee 1000, then everything works fine. However, when used on a Toshiba satelite pro, the home partition somehow becomes readonly.

To recap
The same Jaunty OS is running on a Toshiba and an eee 1000. In each case, logging in will mount home to an encrypted SDHC card.
Coming out of suspend works on the EEE, but on the Toshiba will result in home becoming read-only.

Any help would be appreciated.

---

### Post by fishyf on 2009-09-02
bump

---

