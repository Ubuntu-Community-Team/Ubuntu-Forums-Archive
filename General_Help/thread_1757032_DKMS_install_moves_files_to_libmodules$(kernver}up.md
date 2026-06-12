---
title: "DKMS install moves files to /lib/modules/$(kernver}/updates/dkms"
date: 2011-05-13
forum: General Help
---

### Post by tenon on 2011-05-13
Is this normal DKMS for Ubuntu implementation?  If so, is there a doc or FAQ someone could point me to?

I was setting up DKMS for my rr174x driver.

When running the DKMS install command for the new kernel, it didn't drop the module into /lib/modules/${kernelver}/$DEST_MODULE_LOCATION as expected.

So, the new kernel didn't build with the module.

Copying the file to the right directory and running mkinitramfs gave me the results I was looking for.

```
$ pwd
/lib/modules/2.6.35-28-generic/updates/dkms
$ ls
rr174x.ko
$ sudo cp rr174x.ko ../../kernel/drivers/scsi/.
$ sudo mkinitramfs -o /boot/initrd.img-26.6.35-28-generic 2.6.35-28-generic

```
Is this a bug with this implementation of DKMS? 
Is the updates/dkms directory only intended for use with the updateManager utility when updating to a new kernel release?

Ubuntu version:  10.10
Package:  dkms
Version:  2.1.1.2-3ubuntu1.1

Kernel version:  2.6.35-22-generic

dkms.conf  (the additional sudo for the make may be redundant)
```

MAKE="sudo make -C product/rr1740pm/linux/ KERNELDIR=/lib/modules/${kernelver}/build"
CLEAN="sudo make -C product/rr1740pm/linux/ clean"
BUILT_MODULE_NAME=rr174x
DEST_MODULE_LOCATION=/kernel/drivers/scsi/
BUILT_MODULE_LOCATION=product/rr1740pm/linux/
PACKAGE_NAME=rr174x
PACKAGE_VERSION=2.4
AUTOINSTALL=yes
REMAKE_INITRD=yes

```

---

