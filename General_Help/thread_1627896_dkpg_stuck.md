---
title: "dkpg stuck"
date: 2010-11-21
forum: General Help
---

### Post by SuperTeece on 2010-11-21
More details in my original post [here]("http://ubuntuforums.org/showthread.php?t=1627261").

Essentially I was attempting to install bcmwl-kernel-source so I could use a wmp300n as a second nic on my ubuntu server box. the install hung at update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic-pae

Now whenever I try to apt-get anything I get: E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

Running that leads straight back to the original hang point.

Ideas?

Thanks,
TC

---

### Post by SuperTeece on 2010-11-25
I have more info.

I ran sudo update-initramfs -u -v

It stops here

```
Adding module /lib/modules/2.6.35-22-generic-pae/kernel/drivers/gpu/drm/ttm/ttm.ko
```

---

### Post by SuperTeece on 2010-11-25
So my best guess is that the tool is getting stuck trying to load modules for the installed radeon 9600. This is not needed because I access the box via SSH.

How can I tell update-initramfs to skip or not do this step?

---

