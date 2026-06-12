---
title: "Doubt On my Boot Options"
date: 2009-09-07
forum: General Help
---

### Post by chandru155 on 2009-09-07
My menu.lst file look like this

```
title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        b6c0d06f-ca60-4c41-9f1a-14b22ec2cd12
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=b6c0d06f-ca60-4c41-9f1a-14b22ec2cd12 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        b6c0d06f-ca60-4c41-9f1a-14b22ec2cd12
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=b6c0d06f-ca60-4c41-9f1a-14b22ec2cd12 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        b6c0d06f-ca60-4c41-9f1a-14b22ec2cd12
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=b6c0d06f-ca60-4c41-9f1a-14b22ec2cd12 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        b6c0d06f-ca60-4c41-9f1a-14b22ec2cd12
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=b6c0d06f-ca60-4c41-9f1a-14b22ec2cd12 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        b6c0d06f-ca60-4c41-9f1a-14b22ec2cd12
kernel        /boot/memtest86+.bin
quiet
```

Why there is two recovery mode? At the fresh install of ubuntu, i saw only one recovery mode. After installing softwares and drivers, i saw two. What is the use of revovery mode? to Reset Password or recover computer to previous state?

And what is the last option memtest86+? Is it used to check hard disk error or?

---

### Post by ecmatter on 2009-09-07
There's nothing wrong with your menu.lst file.  That's how it's supposed to look.

The first entry uses the latest kernel (2.6.28-15) which you downloaded via synaptic while installing software and drivers.
The second entry is recovery mode for kernel 2.6.28-15.
The third entry uses the kernel which was installed with your system (2.6.28-11). 
 The fourth entry is recovery mode for kernel 2.6.28-11.

Every now and again, a kernel update will break something.  When that happens, it's good to have the option to boot using the older kernel.

---

### Post by chandru155 on 2009-09-07
Thanks

---

