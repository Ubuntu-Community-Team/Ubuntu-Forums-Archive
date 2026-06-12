---
title: "Synaptic error after today's update..."
date: 2009-07-15
forum: General Help
---

### Post by pjalegria on 2009-07-15
Hi

After today's update i got this error:
> A instalar initramfs-tools (0.92bubuntu29) ...
update-initramfs: deferring update (trigger activated)

A processar 'triggers' para initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.30-rc3-atom
Cannot find /lib/modules/2.6.30-rc3-atom
update-initramfs: failed for /boot/initrd.img-2.6.30-rc3-atom
dpkg: subprocesso post-installation script retornou erro do status de saída 1


...and Synaptic is broken, can someone help me please...

Thanks

---

### Post by paulmerchant on 2009-07-15
I have the same problem right after today's security update. I can't do anything with Synatpic, aptitude, or apt-get. The only difference is that mine is saying that it can't find a different img:

Cannot find /lib/modules/2.6.30-rc7-sarvatt2
update-initramfs: failed for /boot/initrd.img-2.6.30-rc7-sarvatt2
dpkg: subprocess post-installation script returned error exit status 1

It looks like this is happening to those of us who have manually installed different kernels in the past.

---

### Post by paulmerchant on 2009-07-15
It looks like you have something left over from a kernel image that you installed. To fix my issue, I simply deleted a file related to that uninstalled kernel:

```
$sudo rm /var/lib/initramfs-tools/2.6.30-rc7-sarvatt2
$sudo dpkg --configure -a
```

You should be able to do the same. Simply swap out my "2.6.30-rc7-sarvatt2" with the name of the old kernel that is giving you the error.

---

### Post by pjalegria on 2009-07-15
I fix it another way... a created directory /lib/modules/2.6.30-rc3-atom :lolflag:

---

