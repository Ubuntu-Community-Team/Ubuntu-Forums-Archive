---
title: "Compiled kernel with new patch, how can I know if grub loads it ?"
date: 2011-01-24
forum: General Help
---

### Post by Mobidoy on 2011-01-24
I have modified /sound/pci/hda/patch_realtek.c to reflect changes found here [http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=ac612407932be18697b5ae9da0a80f138b8bea8e]("http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=ac612407932be18697b5ae9da0a80f138b8bea8e") so I could use my subwoofer. everything went fine but, after compilation, I have right clicked on my 2 .deb and installed thru Ubuntu Software Center (not knowing how to do it differently) :)

When I reboot, there is no way to tell if the 2.6.35-25-generic entry in my grub menu is refered to the new or old one and sadly, my subwoofer does not appear in sound preferences.

Is there a way to know if I am using the kernel with the patch or to install it under a different name ?

---

### Post by dcstar on 2011-01-25
> **Mobidoy said:**
> I have modified /sound/pci/hda/patch_realtek.c to reflect changes found here [http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=ac612407932be18697b5ae9da0a80f138b8bea8e]("http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=ac612407932be18697b5ae9da0a80f138b8bea8e") so I could use my subwoofer. everything went fine but, after compilation, I have right clicked on my 2 .deb and installed thru Ubuntu Software Center (not knowing how to do it differently) :)

When I reboot, there is no way to tell if the 2.6.35-25-generic entry in my grub menu is refered to the new or old one and sadly, my subwoofer does not appear in sound preferences.

Is there a way to know if I am using the kernel with the patch or to install it under a different name ?

You compile the .deb kernel with a **different** name.

---

