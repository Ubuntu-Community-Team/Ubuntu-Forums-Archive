---
title: "Constant error message regarding kernel"
date: 2011-08-11
forum: General Help
---

### Post by cyberjar09 on 2011-08-11
Hi, 

I have installed Ubuntu 10.04 LTS on a flash drive and everytime I try to do an update I get the following error message:

```
Setting up linux-image-2.6.32-33-generic (2.6.32-33.72) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-33-generic
lzma: Encoder error: -2147467259
Failed to create initrd image.
dpkg: error processing linux-image-2.6.32-33-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.32-33-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Whats going on? 

also, I would like to know if I want to make clones of the flash drive, would a copy and paste suffice or do i need to use some cloning software? I have followed the instructions on [ubuntu wiki]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent") to make my casper-rw larger than 4GB by making it an ext4 partition. 

Thanks.

---

### Post by cyberjar09 on 2011-08-12
Update: I tried formatting and reinstalling Ubuntu 10.04 on the flash drive but the same error occurs again upon trying to update. This is frustrating a little. 

Please help.

---

### Post by sbraz on 2011-08-12
[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/562312](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/562312)

> lzma: Encoder error: -2147467259

which simply means that there was insufficient space on the device to write the new kernel module.

since your 4GB drive worked in the past, my guess is that it doesn't work even after reinstalling as there are too many updates to be made *at the same time*. try upgrading just some packages at the time and use apt-get clean when your drive becomes almost filled up.

---

### Post by cyberjar09 on 2011-08-12
> **sbraz said:**
> [https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/562312](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/562312)



since your 4GB drive worked in the past, my guess is that it doesn't work even after reinstalling as there are too many updates to be made *at the same time*. try upgrading just some packages at the time and use apt-get clean when your drive becomes almost filled up.
My "File System" shows 2.1 Gb free right now though.. I doubt it is a problem of insufficient storage

---

