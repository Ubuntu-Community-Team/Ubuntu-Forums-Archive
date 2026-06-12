---
title: "update-initramfs from another machine"
date: 2011-01-24
forum: General Help
---

### Post by pieterberlijn on 2011-01-24
I'm finding myself in a situation where I am locked out of my machine (because of a initramfs that doesn't allow me to log in). I think I know where the problem is, but I do not know how to go about rebuilding an initrd file from another machine (especially since my second machine is running on a lower kernel version).

I have tried booting from a LiveCD, but that does not allow me to make any changes to /etc/update-initramfs/. Currently do not have a USB drive handy.

How would one go about this?

---

### Post by anglican on 2011-01-24
> **pieterberlijn said:**
> I'm finding myself in a situation where I am locked out of my machine (because of a initramfs that doesn't allow me to log in). I think I know where the problem is, but I do not know how to go about rebuilding an initrd file from another machine (especially since my second machine is running on a lower kernel version).

I have tried booting from a LiveCD, but that does not allow me to make any changes to /etc/update-initramfs/. Currently do not have a USB drive handy.

How would one go about this?I'm guessing that you're trying to modify the initrd.img on the CD rather than on your HD. To generate a new initrd using the live cd you need to mount the HD with your OS on and then chroot to the mounted filesystem and run update-initramfs.

H

---

### Post by pieterberlijn on 2011-01-24
No, the location of output can be modified with a parameter. The problem is that the input cannot. Chrooting is indeed an option, but I was hoping for a quicker fix (since the computer that needs rescuing is using encrypted volumes).

Will try the chroot process now. Thanks.

---

