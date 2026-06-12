---
title: "Revert to prvious kernel."
date: 2011-03-03
forum: General Help
---

### Post by Jonny87 on 2011-03-03
I just upgraded the kernel but it seems to be having issues with my system and as the one I was previously using seemed to work fine, I would like to remove the latest one so that the system boots straight to the previous one. I don't want to have to keep using the grub menu every time I boot.

Is it safe to do this with synaptic? If not, what is the safest way to do this?

---

### Post by An Sanct on 2011-03-03
I don't know if you can uninstall the currently used kernel in synaptic, but I know, you can edit the grub menu, making the previous kernel default.

PS. before uninstalling a kernel, make sure you aren't currently using it. And don't update to the new kernel after that.

---

### Post by gandaran on 2011-03-03
> **Jonny87 said:**
> I just upgraded the kernel but it seems to be having issues with my system and as the one I was previously using seemed to work fine, I would like to remove the latest one so that the system boots straight to the previous one. I don't want to have to keep using the grub menu every time I boot.

Is it safe to do this with synaptic? If not, what is the safest way to do this?
don't remove it, instead install 'startupmanager' from the package manager then use it to choose which kernel to boot from.
wait for the next kernel update then you can safely remove the problem one with synaptic.

---

### Post by debd on 2011-03-03
I have upgraded to a new kernel..but only after reinstalling the nvidia driver I got the gui. Now, the old kernel still shows in the grub menu.
how can i remove it?

---

### Post by gandaran on 2011-03-03
> **debd said:**
> I have upgraded to a new kernel..but only after reinstalling the nvidia driver I got the gui. Now, the old kernel still shows in the grub menu.
how can i remove it?
take note of the kernel version and use synaptic package manager to remove the kernel but you should always have an extra one installed in case something go wrong with the default boot kernel.

---

### Post by debd on 2011-03-03
> **gandaran said:**
> take note of the kernel version and use synaptic package manager to remove the kernel but you should always have an extra one installed in case something go wrong with the default boot kernel.

ya..i too thought about that. And i'll keep it.

---

### Post by Jonny87 on 2011-03-04
> **debd said:**
> I have upgraded to a new kernel..but only after reinstalling the nvidia driver I got the gui. Now, the old kernel still shows in the grub menu.
how can i remove it?
Sounds like you may have been having the same issue I was, I might try my NVIDIA driver as well and see if that fixes it for me. If not I'll prob look at using startup manager to select the default kernel as suggested above.

---

### Post by gandaran on 2011-03-04
> **Jonny87 said:**
> Sounds like you may have been having the same issue I was, I might try my NVIDIA driver as well and see if that fixes it for me. If not I'll prob look at using startup manager to select the default kernel as suggested above.
where did you get the nvidea driver? cant you use the system » administration » additional drivers? installing from additional drivers will free you from reinstalling the driver for every kernel update.

---

### Post by Jonny87 on 2011-03-05
> **gandaran said:**
> where did you get the nvidea driver? cant you use the system » administration » additional drivers? installing from additional drivers will free you from reinstalling the driver for every kernel update.

I was originally using the standard drivers in the additional drivers, but I recently installed the version off the NVIDIA which was a couple versions a head (just to try it out). May just have to go back to the standard.

---

