---
title: "Mounting ext4 filesysem in older versions of ubuntu?"
date: 2009-08-14
forum: General Help
---

### Post by rhcm123 on 2009-08-14
I've been playing around with filesysems recently, and i tried out formatting an external disk ext4. It ran really fast (espescially over USB), so i wanted to use it on my old, 8.10 server. However, i can't mount the drive, mount gives the error "mount: unknown filesystem type 'ext4'".

How do i setup ext4 support in older versions of ubuntu?

---

### Post by sdennie on 2009-08-14
At the very least you would have to upgrade to a kernel (or compile one) that supports ext4 (2.6.28 or above) and you may need to upgrade your e2fsprogs package to a version that understands ext4.

---

### Post by rhcm123 on 2009-08-15
> **sdennie said:**
> At the very least you would have to upgrade to a kernel (or compile one) that supports ext4 (2.6.28 or above) and you may need to upgrade your e2fsprogs package to a version that understands ext4.

Crap, im on 2.6.24-19. I gotta complile my own kernel now, as i can't figure out how to update the kernel via apt.

EDIT: nevermind, i found the kernel archives via apt-cache, but the latest one in the repos is 2.6.27-9, so im still making my own kernel

---

### Post by martinbaselier on 2009-08-15
You don't need to compile the kernel yourself. You can just download a newer kernel from ubuntu packages and install it. 

I think you will need this one:

[http://packages.ubuntu.com/jaunty/linux-image-2.6.28-14-server](http://packages.ubuntu.com/jaunty/linux-image-2.6.28-14-server)

---

