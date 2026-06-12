---
title: "Grub errors o kernel upgrade"
date: 2011-07-15
forum: General Help
---

### Post by nickna on 2011-07-15
Hi, I just got a kernel upgrade to 2.6.38-10-generic and it seems to have screwed up royally. 

in /boot/grub/grub.cfg it's changed

linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=3403c9dd-86ad-443d-98e5-0347c7cf8e7c ro   quiet splash vt.handoff=7

to

linux    /boot/vmlinuz-2.6.38-10-generic root=/dev/sdb1 ro   quiet splash vt.handoff=7

and missed off the initrd line. In fact the initrd image is missing completely.

Any ideas how to either fix this or force it to retry the upgrade without removing my one working kernel?

thanks,
nick

---

### Post by nickna on 2011-07-15
BTW re-installation through synaptic results in:

E: linux-image-2.6.38-10-generic: subprocess installed post-installation script returned error exit status 17

---

### Post by wildmanne39 on 2011-07-15
> **nickna said:**
> BTW re-installation through synaptic results in:

E: linux-image-2.6.38-10-generic: subprocess installed post-installation script returned error exit status 17
Hi, you might try this to help you fix your boot issue.
[http://ubuntuforums.org/showthread.php?p=10871917#post10871917](http://ubuntuforums.org/showthread.php?p=10871917#post10871917)

---

### Post by nickna on 2011-07-16
Thanks but the issue isn't actually with grub but with the upgrade process that wrote an incorrect grub conf and missed off the initrd image. 

I see a lot of people on here have had problems going to the -10 kernel so perhaps there is a real bug in the linux-generic package. The fact that un-installing the package results in the 17 exit code probably confirms this, unless anyone can tell me differently.

---

### Post by wildmanne39 on 2011-07-16
> **nickna said:**
> Thanks but the issue isn't actually with grub but with the upgrade process that wrote an incorrect grub conf and missed off the initrd image. 

I see a lot of people on here have had problems going to the -10 kernel so perhaps there is a real bug in the linux-generic package. The fact that un-installing the package results in the 17 exit code probably confirms this, unless anyone can tell me differently.
Hi, I think you are correct it has happened a lot after the last update, I just found this link that is solved for a boot issue after the last update maybe it will help you.
[http://ubuntuforums.org/showthread.php?t=1804405](http://ubuntuforums.org/showthread.php?t=1804405)

---

