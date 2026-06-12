---
title: "Remove Linux 2.6.31-14 from Grub2"
date: 2009-11-26
forum: General Help
---

### Post by chaoschief on 2009-11-26
I am a complete Ubuntu noob. I just apparently upgraded my linux kernal from Ubuntu, Linux 2.6.31-14-generic to Ubuntu, Linux 2.6.31-15-generic and there are now 3 entries, The 14, the 15 and then my Windows 7. Is there a way to remove Ubuntu, Linux 2.6.31-15-generic? I tried removing it from grub.cfg after chmodding to 644 but it is still there. How do I set it so sudo update-grub doesn't detect Ubuntu, Linux 2.6.31-15-generic and add it to the bootloader? Thanks alot guys and please help me!

---

### Post by scouser73 on 2009-11-26
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

### Post by [A]madeus on 2009-11-27
Thank you..

---

### Post by PeggySue on 2009-11-27
Editing grub.cfg is frowned upon these days.  Grub2 has a number of base files that you can edit to make it do various things.  You then run update-grub2 to produce a new config file.  These two links will help you understand the process for the next time the kernel gets updated.

[http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")
[http://ubuntuforums.org/showthread.php?t=1287602]("http://ubuntuforums.org/showthread.php?t=1287602")

I think that System | Computer Janitor will clean up the kernels when it feels they are not used.  The old versions get backed up but aren't used.  If the vmlinux and initrd files in the root directory aren't seen by grub-update then they don't appear in the start up list after a grub-update.

My advice is to follow the links rather than listen to me!!


Good luck.

---

### Post by -kg- on 2009-11-27
Do they have Startup Manager available for Karmic?  If so, that's the easiest way to go.  Just set the maximum number of old kernels to whatever you desire (I have mine set for two, just in case) and then any older kernels over the max number will automatically be dropped from the GRUB menu upon update.

If you find that you have no problem with the new kernel and want to get rid of the menu for the older one, just temporarily change the number to one, reboot, and the other one will be gone.  There are quite a few options you can play with using Startup Manager to configure GRUB; again, if it's available for Karmic and GRUB2. You will be able to find it in Synaptic.

One thing, though...Startup Manager won't physically remove the older kernels from your system, only the GRUB menu references.  You will need to use scouser73's method to completely remove the old kernels from your hard drive.

---

### Post by PeggySue on 2009-11-27
Hi Glen,

Karmic does have Startup Manager but it doesn't give you the option to set the maximum number of kernels.  (As far as I can see).  It makes changing themes easy though.  Wish I had known about it sooner.

dah di dit   dit  G3XXE

---

