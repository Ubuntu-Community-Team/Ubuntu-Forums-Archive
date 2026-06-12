---
title: "Issues with kernel build and installation in ubuntu 10.04"
date: 2011-08-30
forum: General Help
---

### Post by codingfreak on 2011-08-30
Hi

I am trying to build and install new linux kernel 3.0.0 which I downloaded from kernel.org. I am following the tutorial [https://wiki.ubuntu.com/KernelTeam/GitKernelBuild](https://wiki.ubuntu.com/KernelTeam/GitKernelBuild).

Building kernel image is successful but when I try to updateinitramfs by giving the following command in /lib/modules I am getting the following error

```
# cd /lib/modules/
root@cf:/lib/modules# ls
2.6.32-33-generic  3.0.0-custom
root@cf:/lib/modules# sudo update-initramfs -ck 3.0.0-custom/
update-initramfs: Generating /boot/initrd.img-3.0.0-custom/
touch: cannot touch `/boot/initrd.img-3.0.0-custom/.new': No such file or directory
: 3.0.0-custom/ is not a valid kernel version
update-initramfs: failed for /boot/initrd.img-3.0.0-custom/
```Can anyone help me regarding this ?

---

### Post by codingfreak on 2011-08-31
Debian way of kernel building and installing is quite strange for me .. 

But if there is no option for a fix I should better try my hand in traditional OS like fedora or centos  .. As I see UBUNTU is not a favorite place for kernel developers and debugging.

But I still luv using it for all other development :)

---

