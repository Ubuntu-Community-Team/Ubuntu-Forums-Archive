---
title: "Cleaning up leftover files and directories from kernel updates"
date: 2010-05-07
forum: General Help
---

### Post by The Keeper on 2010-05-07
Quite often after I've removed old kernels, apt complains that it couldn't delete /lib/modules/2.6.blahblah because it is not empty. So now I have plenty of leftover directories in /lib/modules.

In addition, in /boot partition there are still files initrd.img-2.6.blahblah and System.map-2.6.blahblah left. Which is kinda annoying as the boot partition is only 92MB.

As apt won't remove those files since no packages belonging to those kernels are installed anymore, how can I remove them safely? None of those kernels are even mentioned by Grub.

---

### Post by sylvester_0 on 2010-05-07
Have you tried
```
sudo apt-get autoremove
```?

AFAIK older kernels get removed during distribution upgrades. You could manually remove them in synaptic (search for linux-image.)

---

### Post by The Keeper on 2010-05-07
The packages have already been removed manually and autoremove does nothing. The files are still left behind, even after distro upgrades.

---

### Post by Jimtheplanner on 2010-05-07
Why not give Bleach Bit a try it's in the repos

Jim

---

### Post by The Keeper on 2010-05-07
This is a headless server, so I won't really risk it with such an obscure application. It's feature list doesn't mention kernels anyhow.

---

