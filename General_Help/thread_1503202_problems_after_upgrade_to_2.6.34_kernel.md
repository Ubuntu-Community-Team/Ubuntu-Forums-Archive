---
title: "problems after upgrade to 2.6.34 kernel"
date: 2010-06-06
forum: General Help
---

### Post by Cylon on 2010-06-06
I upgraded to the 2.6.34 kernel hoping it would resolve some of the boot problems I'm having on an Asus Eee PC 1201N. However, the upgrade didn't resolve the issue and I continue to get the error probing smb2 message.

While this is only a minor nuisance, apt now wants to re-install the old 2.6.32 kernel. Is there an easy way to keep this from happening?

---

### Post by lavinog on 2010-06-07
> **Cylon said:**
> I upgraded to the 2.6.34 kernel hoping it would resolve some of the boot problems I'm having on an Asus Eee PC 1201N. However, the upgrade didn't resolve the issue and I continue to get the error probing smb2 message.

While this is only a minor nuisance, apt now wants to re-install the old 2.6.32 kernel. Is there an easy way to keep this from happening?

How did you upgrade to 2.6.34?  Did you compile a new kernel or did you use a deb package?

apt is probably trying to install an update to 2.6.32 (there was a recent update)
You should be able to do the update without it overwriting the 34 kernel.  Or your can uninstall the 2.6.32 kernel.

Also if you compiled the 34 kernel, and you didn't add the ureadahead patch, you should deactivate ureadahead by renaming /etc/init/ureadahead.conf to /etc/init/ureadahead.conf.disable
and /etc/init/ureadahead-other.conf to /etc/init/ureadahead-other.conf.disable

---

