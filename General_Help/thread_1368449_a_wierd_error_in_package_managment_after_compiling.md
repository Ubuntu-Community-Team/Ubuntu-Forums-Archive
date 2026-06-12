---
title: "a wierd error in package managment after compiling a kernel"
date: 2009-12-30
forum: General Help
---

### Post by snir on 2009-12-30
hi everyone...this one is a bit tricky...
i've compiled a new kernel 2.6.32 with my own configuration.
the kernel booted up into initramfs and stopped there,so i used the last working kernel to get into the system and used synaptic to remove the packges..
now when im running synaptic i get 
```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

```when i type sudo dpkg --configure -a im getting:
```
sudo dpkg --configure -a
Setting up initramfs-tools (0.92bubuntu53) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-custom
Cannot find /lib/modules/2.6.32-custom
update-initramfs: failed for /boot/initrd.img-2.6.32-custom
dpkg: subprocess installed post-installation script returned error exit status 1

```any idea...?

---

### Post by taurus on 2009-12-30
Looks like you are missing the modules for that new kernel, /lib/modules/2.6.32-custom.

---

### Post by snir on 2009-12-31
ok,what should i do?

---

### Post by snir on 2010-01-02
anyone?

---

