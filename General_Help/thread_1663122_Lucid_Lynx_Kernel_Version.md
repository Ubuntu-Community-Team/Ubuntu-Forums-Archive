---
title: "Lucid Lynx Kernel Version"
date: 2011-01-09
forum: General Help
---

### Post by bumder on 2011-01-09
I'm currently on 2.6.32-27 in Ubuntu 10.04, thinking about 'manually' installing a newer/up to date kernel.

Just wondering if anyone has done this before with success, or recommend the best way to do so?

---

### Post by QLee on 2011-01-09
This is not the recommendation you asked for but I recommend that if all your hardware is working with the standard LTS kernel you leave it be.

---

### Post by Jechem on 2011-01-09
You can add the ppa:kernel-ppa/ppa to your software sources and install what you need. I've installed the linux-headers-2.6.37-11, linux-headers-2.6.37-11-generic-pae and linux-image-2.6.37-11-generic-pae from the Synaptic Package Manager without any problem. This kernel supports my ENE SD card reader on my MSI laptop but has problems installing my video card driver. I still have the 2.6.32-27 kernel for regular use.

---

### Post by bumder on 2011-01-09
Hmm, added the ppa to update manager, but no updates are shown.

Do you have to enable unofficial updates somewhere?

---

### Post by ZebaSz on 2011-01-09
If you enable the kernel-ppa, you have to install those kernels separately. In the Software Center or Synaptic.

---

### Post by Jechem on 2011-01-09
> **bumder said:**
> Hmm, added the ppa to update manager, but no updates are shown.

Do you have to enable unofficial updates somewhere?

You have to manually select the packages on the Synaptic Manager. They don't appear on the Update Manager as these are not updates. Lucid uses the 2.6.32 kernel only. If you want to use another kernel then you would have to manually select it to install it on your system.

---

### Post by bumder on 2011-01-09
Ah, I see.

If I did install a more recent kernel, and it proved unstable, is it easy to switch back to the previous 'stable' kernel?

Thankyou

---

### Post by Jechem on 2011-01-09
Log in to the 2.6.32-27 kernel in grub before uninstalling the newer unstable kernel. You can then select the packages that you installed in the Synaptic Manager and have them uninstalled. Once you have it uninstalled you can again choose whichever kernel you want.

---

