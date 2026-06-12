---
title: "After security update today - Not Authorized to Mount"
date: 2010-09-14
forum: General Help
---

### Post by zoomcityzoom on 2010-09-14
After applying security updates today to 10.04 LTS, I was unable to mount USB flash drives. When plugged into USB, a message would pop up saying that I was not authorized to mount the device. I was also experiencing problems when starting VMware. These issues seem to be tied to a problem with mountall 2.15.2 which was part of the security upgrade. I fixed the probelm by reverting back to mountall 2.14.

Here's how to revert back to mountall 2.14 if you need to.
```
sudo apt-get install mountall=2.14

```Then reboot and all should be well.

---

