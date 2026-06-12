---
title: "Upgrading Ubuntu While Using Software RAID"
date: 2010-06-25
forum: General Help
---

### Post by Cerin on 2010-06-25
Is it possible to upgrade an Ubuntu install which is using software RAID?

I ask because I'm currently using Fedora, and one of my huge frustrations with the distro is that if you're using software RAID, the installer explicitly notes you can't upgrade to future versions. Instead, it requires that you wipe your entire drive and do a full reinstall to acquire the next release. I presume Ubuntu probably uses many of the same libraries to support software RAID as Fedora, so does Ubuntu also have this limitation?

Regards,
Chris

---

### Post by dcstar on 2010-06-26
> **Cerin said:**
> Is it possible to upgrade an Ubuntu install which is using software RAID?

I ask because I'm currently using Fedora, and one of my huge frustrations with the distro is that if you're using software RAID, the installer explicitly notes you can't upgrade to future versions. Instead, it requires that you wipe your entire drive and do a full reinstall to acquire the next release. I presume Ubuntu probably uses many of the same libraries to support software RAID as Fedora, so does Ubuntu also have this limitation?


What sort of RAID is in use?

---

### Post by john newbuntu on 2010-06-26
I believe some people have done it with minor issues:
[http://ubuntuforums.org/showthread.php?t=1468064](http://ubuntuforums.org/showthread.php?t=1468064)
I did a new install of Lucid and it recognized my old raid-1 array (from Karmic) without any problem.  I just had to update my mdadm.conf.

---

### Post by Cerin on 2010-06-26
> **dcstar said:**
> What sort of RAID is in use?

Good question. I'm using RAID-1.

---

