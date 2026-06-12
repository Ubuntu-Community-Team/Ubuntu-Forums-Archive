---
title: "I deleted my kernel :("
date: 2010-11-26
forum: General Help
---

### Post by moosehadley on 2010-11-26
Hello, I did something stupid...
I uninstalled my kernel, now I can't boot back into Ubuntu to reinstall it ](*,)
What do I do now?

---

### Post by drs305 on 2010-11-26
Boot the LiveCD. 'chroot' into your normal Ubuntu partition. You can use Step 1 of the following guide: 
[_http://ubuntuforums.org/showthread.php?t=1581099_]("http://ubuntuforums.org/showthread.php?t=1581099")

Once you are at the root prompt of your Ubuntu partition, install the latest kernel. You don't use "sudo" in a *chroot* environment:```

apt-get install linux-image
```
Exit the chroot environment after you have installed linux-image and reboot. That should take care of it. 

If Grub complains during the reboot, come back and give us the details of the error.

---

### Post by Tanner1294 on 2010-11-26
I'm sorry to say, but, I'm pretty sure you have no chance of reviving Ubuntu now. The only thing I recommend is this:

Get an Ubuntu live cd, (either the one you used to install ubuntu or another one), boot it up with the live cd, and then use it to copy your documents from your hard drive to a flash drive or other storage medium. Then re-install Ubuntu altogether.

Before you do this however, If you can, wait a few days and see if anyone else in the forums knows anything about re-installing the kernel. But as far as I know, that's not possible at this point =(

---

### Post by moosehadley on 2010-11-28
> **drs305 said:**
> Boot the LiveCD. 'chroot' into your normal Ubuntu partition. You can use Step 1 of the following guide: 
[_http://ubuntuforums.org/showthread.php?t=1581099_]("http://ubuntuforums.org/showthread.php?t=1581099")

Once you are at the root prompt of your Ubuntu partition, install the latest kernel. You don't use "sudo" in a *chroot* environment:```

apt-get install linux-image
```
Exit the chroot environment after you have installed linux-image and reboot. That should take care of it. 

If Grub complains during the reboot, come back and give us the details of the error.

SOLVED:
Chrooting worked!
Thank you very much!

---

