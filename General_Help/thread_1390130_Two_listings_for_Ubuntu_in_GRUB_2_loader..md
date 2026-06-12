---
title: "Two listings for Ubuntu in GRUB 2 loader."
date: 2010-01-25
forum: General Help
---

### Post by Ac30nfir3 on 2010-01-25
Just a bit of a nit-pick here. I am dual booting Ubuntu Linus 9.10 and Windows 7, and when at the GRUB 2 bootloader screen, I see two copies of Ubuntu Linux. One says 
> 
Ubuntu, Linux 2.6.31-**16**-generic

and the other says 
> 
Ubuntu, Linux 2.6.31-**14**-generic


I have a picture of what my GRUB loader looks like, so I'll post that here as well.

[img]http://img641.imageshack.us/img641/8413/grub.png[/img]

Is there any difference between which one to choose? Is this an error? Is there any way to remove one from the loader?

Thanks for the help! :)

---

### Post by scouser73 on 2010-01-25
Every time Ubuntu installs a new Linux kernel, the old one is left behind. This means that if you are regularly updating an Ubuntu system the Grub boot menu becomes longer and longer with kernels you don’t need anymore.

The old kernels are deliberately left installed and on the menu so you can boot a previous kernel if you have trouble with a new one. But if the new one works, you can safely uninstall the old kernel, which will also result in the Grub menu being cleaned up.

Follow these steps to identify and remove any old kernels.

**1** - Go to **Terminal** and paste the following command: **uname -r**
It will print the version of the Linux kernel you are running, this is the one you want to keep. It should look something like this: ***2.6.20-16-generic***

**2** - Go to **Synaptic Package Manager** via the **System > Administration** menus

**3** - Paste this: **linux-image-2** into the search box of **Synaptic Package Manager**

**4** - Once you have located the old kernels, **hightlight** them and **right-click** then select **Mark For Complete Removal** then click **Mark** and then click **Apply**

The results should show every available and installed kernel. A green box on the left indicates that the package is installed. The only linux-image you want installed is the latest one.

[COLOR="Red"]**Be careful of what you remove. Ensure that you don’t remove your current kernel, or anything that is not a linux-image. It is possible to break Ubuntu if you remove the wrong kernel.**[/COLOR]

Your computer and Grub menu should now be free of old kernels.

---

### Post by Ac30nfir3 on 2010-01-25
I will try that once I switch back to Ubuntu later, but the weird thing is, I have had no copies of Linux on my computer before this one. I installed Ubuntu from the CD and two of them appeared on the first startup (when it asked to restart and I couldn't choose Win7) This is why I was confused.

Thanks for the help though!

EDIT: Tried it, in the Synaptic Package Manager, I don't see any duplicates, and only three have the green box you were talking about. I have included a picture to show you since i don't trust myself just fiddling around in here. Still a complete noob to Linux. Thanks.

[img]http://img11.imageshack.us/img11/1403/screenshotsynapticpackah.png[/img]

---

