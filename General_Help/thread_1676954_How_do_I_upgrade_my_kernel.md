---
title: "How do I upgrade my kernel?"
date: 2011-01-28
forum: General Help
---

### Post by ratman1 on 2011-01-28
Hi

I have got an Ubuntu 10.10 32 bit system and am wondering how I would go about upgrading to the new 2.6.38-rc2 kernel.

Please don't say it is unsafe, I know. I just want to see if my graphics card is supported.

Thanks for any help.

---

### Post by Smart Viking on 2011-01-28
Download the kernel as a .deb file somewhere, then do
```
sudo dpkg -i kernel.deb
```

---

### Post by Halzen on 2011-01-28
> **ratman1 said:**
> Hi

I have got an Ubuntu 10.10 32 bit system and am wondering how I would go about upgrading to the new 2.6.38-rc2 kernel.

Please don't say it is unsafe, I know. I just want to see if my graphics card is supported.

Thanks for any help.

This is the method I used. If it doesn't take, try running "sudo apt-get update grub" in your terminal before rebooting at the last step. That's what finally did it for me.

- 1 - Go to this website [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) and you'll see a huge directory tree of kernels. Find the directory for the kernel you want/need and click on it.

- 2 - In each of these directories you're going to see "BUILD.LOG", "CHANGES", three items that begin with "linux-headers", two that begin with "linux-image" and one that begins with "linux-source". The "BUILD.LOG", "CHANGES", and "linux-source" are completely unimportant right now. We're only worried about "linux-headers" and "linux-image".

- 3 - Download and then install the following IN THIS ORDER: first get the linux-headers file that ends with "all.deb". Second get the linux-headers file that ends with "i386.deb" or "amd64.deb" depending upon what architecture you need. Finally get the linux-image file that ends with "i386.deb" or "amd64.deb" again depending upon what architecture you need. Honestly it doesn't really matter what order you download them in, but you need to make absolutely sure that you install them in this order.

- 4 - Reboot your computer and you're done.

---

### Post by ratman1 on 2011-01-28
> **Halzen said:**
> This is the method I used. If it doesn't take, try running "sudo apt-get update grub" in your terminal before rebooting at the last step. That's what finally did it for me.

- 1 - Go to this website [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) and you'll see a huge directory tree of kernels. Find the directory for the kernel you want/need and click on it.

- 2 - In each of these directories you're going to see "BUILD.LOG", "CHANGES", three items that begin with "linux-headers", two that begin with "linux-image" and one that begins with "linux-source". The "BUILD.LOG", "CHANGES", and "linux-source" are completely unimportant right now. We're only worried about "linux-headers" and "linux-image".

- 3 - Download and then install the following IN THIS ORDER: first get the linux-headers file that ends with "all.deb". Second get the linux-headers file that ends with "i386.deb" or "amd64.deb" depending upon what architecture you need. Finally get the linux-image file that ends with "i386.deb" or "amd64.deb" again depending upon what architecture you need. Honestly it doesn't really matter what order you download them in, but you need to make absolutely sure that you install them in this order.

- 4 - Reboot your computer and you're done.

Thanks, will do. Just wondering if using a kernel natty will muck things up on maverick. Also will this be upgraded when another later kernel gets pushed through ubuntu update?

---

### Post by Halzen on 2011-01-28
> **ratman1 said:**
> Thanks, will do. Just wondering if using a kernel natty will muck things up on maverick. Also will this be upgraded when another later kernel gets pushed through ubuntu update?

You're looking at 2.6.37? It might not hurt, but I wouldn't risk it. Natty kernels at this stage are listed as that just because they're being modified for Natty; the odds of you getting extra hardware support there are slim, so it's safest to just go with the latest stable Maverick.

---

### Post by ratman1 on 2011-01-28
Ok, I went ahead and installed the latest 2.6.38-rc2-natty ones. Stupidly I didn't check the forum and missed your comment. You were right natty kernel on maverick did screw it up. :grin:

I will install natty and see how it goes with the 2.6.38-rc2-natty kernel.

Will post back when done.

---

