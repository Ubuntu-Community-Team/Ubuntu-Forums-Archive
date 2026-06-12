---
title: "Edit bootloader entries?"
date: 2010-03-31
forum: General Help
---

### Post by Skyline969 on 2010-03-31
Well, I installed Ubuntu in a dual-boot with Windows 7, and installed the bootloader (GRUB? Ubuntu newbie here...). However, I have some weird Windows XP Embedded entry! I also have a lot of different boot options for Ubuntu. All I want is my Windows 7 entry (picked up as Windows Vista) and my main Ubuntu entry. How can I edit the bootloader entries (remove some existing ones, not adding any) so I have only two on there?

---

### Post by john newbuntu on 2010-04-01
Those Ubuntu entries that you see on the Grub menu are called Kernels and each correspond to the core of your operating system.

The simplest way to remove the old ubuntu entries from grub is by using Synaptic package manager (System->admin->synaptic package manager). Mark the linux-headers-xxx and linux-image-xxx corresponding to the version that you DO NOT need for complete removal. (You can search for linux-)

Note:  DO NOT remove the kernel that you are currently using.
Then hit apply.

---

### Post by Skyline969 on 2010-04-01
> **john newbuntu said:**
> Those Ubuntu entries that you see on the Grub menu are called Kernels and each correspond to the core of your operating system.

The simplest way to remove the old ubuntu entries from grub is by using Synaptic package manager (System->admin->synaptic package manager). Mark the linux-headers-xxx and linux-image-xxx corresponding to the version that you DO NOT need for complete removal. (You can search for linux-)

Note:  DO NOT remove the kernel that you are currently using.
Then hit apply.

Hm, I could do that, but it leaves me with my primary problem - the Windows XP Embedded option that I so desperately want to get rid of. I would just delete the partition, but I don't know of its ties in with Win7, and I don't want to mess anything up.

---

### Post by scouser73 on 2010-04-01
> **Skyline969 said:**
> Hm, I could do that, but it leaves me with my primary problem - the Windows XP Embedded option that I so desperately want to get rid of. I would just delete the partition, but I don't know of its ties in with Win7, and I don't want to mess anything up.

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

### Post by QIII on 2010-04-01
To clean up your boot menu, in the terminal issue the following:

```
sudo update-grub2
```

That should get rid of both the old kernel entries and the pesky XP entry.

It may update the Vista to 7, but I'm not sure.  Remember that GRUB2 is a beta, and may not have caught up to Windows 7 yet.

If you find that you still have the XP problem, come back and we'll see what we can do.

---

