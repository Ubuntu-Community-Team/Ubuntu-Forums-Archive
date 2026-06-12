---
title: "E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct"
date: 2010-01-14
forum: General Help
---

### Post by galib_ewu36 on 2010-01-14
**I have been looking into different postings and different solutions but none of them worked to solve my problem. I am using Ubuntu 9.10 and whenever I click Synaptic Package Manager it gives me the following error**

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

**When I ran sudo dpkg --configure -a in terminal it gives me the following error.**

Setting up initramfs-tools (0.92bubuntu53) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.31-17-generic
mv: cannot move `/boot/initrd.img-2.6.31-17-generic.new' to `/boot/initrd.img-2.6.31-17-generic': No such file or directory
dpkg: subprocess installed post-installation script returned error exit status 1

[B]I cannot run even apt-get or update manager.
Please help me in this regard.
Cheers,
galib[/B]

---

### Post by grandtoubab on 2010-01-14
Check your packages:
```
sudo dpkg --audit
```

Then follow the recommendations

---

### Post by galib_ewu36 on 2010-01-14
The problem still persists, it asks me to reconfigure the initramfs-tools package but whenever I try it get stuck with the same error message.

---

### Post by wojox on 2010-01-14
Open a terminal and type 

```
ls /boot
```

What does it give you?

---

### Post by galib_ewu36 on 2010-01-14
#ls /boot 
gives me the following information
abi-2.6.28-11-generic                  initrd.img-2.6.31-17-generic.new
abi-2.6.31-17-generic                  memtest86+.bin
config-2.6.28-11-generic               System.map-2.6.28-11-generic
config-2.6.31-17-generic               System.map-2.6.31-17-generic
grub                                   vmcoreinfo-2.6.28-11-generic
initrd.img-2.6.28-11-generic           vmcoreinfo-2.6.31-17-generic
initrd.img-2.6.31-17-generic           vmlinuz-2.6.28-11-generic
initrd.img-2.6.31-17-generic.dpkg-bak  vmlinuz-2.6.31-17-generic

---

### Post by michy99 on 2010-01-14
See if this helps.```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```

---

### Post by galib_ewu36 on 2010-01-14
Sorry the same problem continues.

---

### Post by galib_ewu36 on 2010-01-14
None of the solutions worked. I am still having the same problem. Looking forward for a solution.

---

