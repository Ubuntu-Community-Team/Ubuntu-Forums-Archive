---
title: "portable USB fails configuring the updates kernels"
date: 2011-08-10
forum: General Help
---

### Post by nagyv on 2011-08-10
Hi,

I've a permanent USB running natty. Synaptic would like to upgrade the kernel packages, but it fails with cryptsetup failure. 

```

Setting up linux-image-2.6.38-10-generic (2.6.38-10.46) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.38-10-generic
cryptsetup: WARNING: failed to detect canonical device of aufs
cryptsetup: WARNING: could not determine root device from /etc/fstab
```

How can I get around this? Is it enough if I remove cryptsetup? AFAIK, my devices are not encrypted (at least /etc/crypttab) is empty).

thanks for your help

---

### Post by dcstar on 2011-08-10
> **nagyv said:**
> Hi,

I've a permanent USB running natty. Synaptic would like to upgrade the kernel packages, but it fails with cryptsetup failure. 

```

Setting up linux-image-2.6.38-10-generic (2.6.38-10.46) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.38-10-generic
cryptsetup: WARNING: failed to detect canonical device of aufs
cryptsetup: WARNING: could not determine root device from /etc/fstab
```

How can I get around this? Is it enough if I remove cryptsetup? AFAIK, my devices are not encrypted (at least /etc/crypttab) is empty).

thanks for your help

Check how much disk space you have available.

USBs created using the Startup Disk Creator with Persistence ("Reserved space") will eventually use up all the available Reserved space because the file system type does not return deleted space for reuse.

You basically have to delete the Reserved space partition and create a fresh one (until it eventually fills up).

---

### Post by nagyv on 2011-08-10
Sorry, but I think you are wrong.

I have a separate casper partition as permanent storage. The problem is simply that cryptsetup can't figure out that is has nothing to do with my setup.

---

