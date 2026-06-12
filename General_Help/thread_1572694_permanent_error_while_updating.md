---
title: "permanent error while updating"
date: 2010-09-11
forum: General Help
---

### Post by Lukas666 on 2010-09-11
Hello!

Karmic 64 bit. I've been getting this error for several weeks already, every time when the update manager launches. All other updates install fine, this is the only one that fails. Tried Google and some tips but with no luck.

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
Errors were encountered while processing:
 linux-image-2.6.31-22-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up linux-image-2.6.31-22-generic (2.6.31-22.63) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-22-generic
cpio: ./lib/brltty/brltty.sh: Cannot stat: No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.31-22-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.31-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.31-22-generic


Does any know how to fix it?
Thanks!

---

### Post by dcstar on 2010-09-11
> **Lukas666 said:**
> Hello!

Karmic 64 bit. I've been getting this error for several weeks already, every time when the update manager launches. All other updates install fine, this is the only one that fails. Tried Google and some tips but with no luck.
.........
Errors were encountered while processing:
 **linux-image-2.6.31-22-generic**


Does any know how to fix it?
Thanks!

Manually remove the package, delete the associated downloaded file in /var/cache/apt/archives and then reinstall the package.

---

### Post by Lukas666 on 2010-09-11
bump

---

