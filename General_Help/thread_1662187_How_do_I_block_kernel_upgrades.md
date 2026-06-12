---
title: "How do I block kernel upgrades?"
date: 2011-01-07
forum: General Help
---

### Post by arashiko28 on 2011-01-07
Yeap, as you read, I need to block kernel upgrades, reason? Kernel 2.6.35 and 2.6.36 are not compatible with my sound card, where I get little or no sound at all, so I went back to 2.6.34 and got my sound back to work. Now, how do I keep it from reminding me everyday, that I have to install these updates? I don't want to accidentally install them, perhaps I'll jump to 2.6.37 once it's ready or the 2.6.37-RC8 it's stable enough to give it a try?

---

### Post by dcstar on 2011-01-07
> **arashiko28 said:**
> Yeap, as you read, I need to block kernel upgrades, reason? Kernel 2.6.35 and 2.6.36 are not compatible with my sound card, where I get little or no sound at all, so I went back to 2.6.34 and got my sound back to work. Now, how do I keep it from reminding me everyday, that I have to install these updates? I don't want to accidentally install them, perhaps I'll jump to 2.6.37 once it's ready or the 2.6.37-RC8 it's stable enough to give it a try?

Try going into Synaptic and removing or Locking the plain "generic" kernel packages to the version that you want, these are the ones that get updated automatically with new releases.

---

### Post by hawthornso23 on 2011-01-07
Just on the sound issue for a minute - have you got
 
linux-backports-modules-alsa-lucid-generic

installed? This keeps your alsa sound modules up to date when you upgrade your kernel. On my system for some reason I had the backport alsa module for a specific (old) kernel version installed instead so my ALSA modules were not updating properly when the kernel updated.

---

### Post by arashiko28 on 2011-01-07
> **hawthornso23 said:**
> Just on the sound issue for a minute - have you got
 
linux-backports-modules-alsa-lucid-generic

installed? This keeps your alsa sound modules up to date when you upgrade your kernel. On my system for some reason I had the backport alsa module for a specific (old) kernel version installed instead so my ALSA modules were not updating properly when the kernel updated.

About that, I have none. This is a general problem with this laptop model (check at my signature) and kernel 2.6.35, I'll install and upgrade and then... experiments? :idea: let's hope it works :P

---

### Post by arashiko28 on 2011-01-08
There are no linux-backports-modules-alsa-lucid, there are for maverick and the 2.6.35.24-generic-pae. Which I installed, and still have no sound.
To add more, now I have about 7 entries at grub...

---

### Post by QLee on 2011-01-08
[QUOTE=arashiko28]...
To add more, now I have about 7 entries at grub...[/QUOTE]

Uninstall the kernel images you don't want to use and then update-grub, it will write a new grub.cfg with only the kernels still on your system. Uninstalling the kernels with the package manager will likely trigger the GRUB update automatically.

---

