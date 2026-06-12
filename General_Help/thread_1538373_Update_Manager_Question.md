---
title: "Update Manager Question"
date: 2010-07-25
forum: General Help
---

### Post by Dullstar on 2010-07-25
I had a Linux installation a while back, and an update to the kernel broke the wireless card driver.  I have uninstalled it because I had messed up when setting up the dual boot anyway,  but I will be reinstalling it - with the same computer, same version of Ubuntu, and same hardware except for the keyboard.

Here's what my question is.  When I look at updates, there's always a huge list.  Because of this kernel update doing what it did, is there a way I can make it so kernel updates are by default not selected for installation unless I manually select them, while not effecting anything else?

Well, while I wait for Ubuntu to install on that computer, I guess I'll watch that Mythbusters DVD I bought today on my other machine.

---

### Post by dcstar on 2010-07-25
> **Dullstar said:**
> I had a Linux installation a while back, and an update to the kernel broke the wireless card driver.  I have uninstalled it because I had messed up when setting up the dual boot anyway,  but I will be reinstalling it - with the same computer, same version of Ubuntu, and same hardware except for the keyboard.

Here's what my question is.  When I look at updates, there's always a huge list.  Because of this kernel update doing what it did, is there a way I can make it so kernel updates are by default not selected for installation unless I manually select them, while not effecting anything else?

Well, while I wait for Ubuntu to install on that computer, I guess I'll watch that Mythbusters DVD I bought today on my other machine.

You can pin any packages in Synaptic so they are not updated.

For kernels AFAIK if you remove the generic meta-packages then you will not get any new updates, but since all your old kernel versions are** still** there (and will be available in your Grub list) there is little point doing this.

---

### Post by Dullstar on 2010-07-25
> **dcstar said:**
> You can pin any packages in Synaptic so they are not updated.

Can this be done for kernels, if so, what package?

> For kernels AFAIK if you remove the generic meta-packages then you will not get any new updates, but since all your old kernel versions are** still** there (and will be available in your Grub list) there is little point doing this.

First of all, on this method, would that effect the system at all, other than no kernel updates?  Second of all, if it is safe, how would one go about doing this?

Sorry, in the time that I've had Ubuntu, I haven't had to do too much tweaking at all to get things up and running well.

I do know the old kernel versions are still there, so if a new one doesn't work right I can set the default boot option to the old one, but I'd rather not mess with vital system files, in this case the bootloader, when possible to avoid, although I will if I have to.

---

### Post by CharlesA on 2010-07-25
You can use startup manager to set which kernel you boot into by default.

How does a kernel update break yer wireless drivers? Did you need to compile them from source or something?

---

### Post by Dullstar on 2010-07-25
I don't really know why...  but according to the research my brother did, apparently the wireless driver is built into the kernel.  Using an old kernel version did solve the problem, so that appears to be the cause.  Why the update would cause this, I don't know.  But, it did.

---

### Post by CharlesA on 2010-07-25
Ah. Wireless drivers have always been iffy.

---

