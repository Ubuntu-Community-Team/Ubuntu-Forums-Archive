---
title: "I want to show only one kernel on the boot menu?"
date: 2009-11-21
forum: General Help
---

### Post by MIH1406 on 2009-11-21
Hi,

Before 9.10 I was able to show only one kernel (without memtest & recovery) using Startup manager but now many options are removed.

How do I hide older kernels, memtest and recovery options on 9.10. In other words I want only one kernel to be shown?

---

### Post by lmarmisa on 2009-11-21
You can delete the old versions of kernel easily. 

Try to use Synaptic and uninstall the old versions of the kernel named linux-image-xxx. Be very careful and do not remove the newest version!!.

Then open a terminal and type

**sudo update-grub2**

If you want to modify the grub configuration, these are the files that you can try to customize:

**/etc/defaults/grub** - general grub2 parameters
**/etc/grub.d/** - directory with grub shell scripts for the command update-grub2 
**/etc/grub.d/20_memtest86+** - script for memtest86+
**/etc/grub.d/10_linux **- script for linux entries (including recovery)

Don't forget to save a copy of every file before you touch it.

The configuration file **/boot/grub/grub.cfg** is updated according to the content of these script files by means of the command **update-grub2**.

Best regards,

Luis

---

### Post by wilee-nilee on 2009-11-21
Personally I use Ubuntu tweak for this sort of thing it also has many other uses it will clean the cache better the autoremove or autoclean, and it will load the apt/sources and keys in a easy manner.

---

### Post by MIH1406 on 2009-11-23
Where can I get Ubuntu tweak?

---

### Post by Taramar on 2009-11-23
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by scouser73 on 2009-11-23
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

### Post by Lvcoyote on 2009-11-23
> **scouser73 said:**
> Every time Ubuntu installs a new Linux kernel, the old one is left behind. This means that if you are regularly updating an Ubuntu system the Grub boot menu becomes longer and longer with kernels you don’t need anymore.

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

I tried this and the package manager did remove the old Kernel, but when I boot the old kernel is still there in the boot menu.  I read somewhere else that simply uninstalling the old kernel will remove it from the boot menu, but it's not in my case.

---

### Post by dcstar on 2009-11-23
> **Lvcoyote said:**
> I tried this and the package manager did remove the old Kernel, but when I boot the old kernel is still there in the boot menu.  I read somewhere else that simply uninstalling the old kernel will remove it from the boot menu, but it's not in my case.

```
sudo update-grub2
```

Possibly the apt stuff is still running the old update-grub command.

---

