---
title: "Upgraded kernel prevents my system (10.04) to boot"
date: 2011-12-07
forum: General Help
---

### Post by khantastic on 2011-12-07
Hi

I upgraded my ubuntu 10.04 LTS using standard aptitude update and aptitude safe-upgrade. This box hadn't been upgraded for a while since it was in a development environment not connected to internet. However this is not more the case, and it needs upgrading. 

The latest working kernel is 2.6.32-22-generic. When I upgraded earlier this week I got 2.6.32-36-generic. With the new kernel the box is not able to boot. I get the following during boot:

```

mount: mounting /dev/disk/by-uuid/{disk uuid} on /root failed: Device or resource busy
mount: mounting /dev on root/dev failed: No such file or directory
mount: mounting /sys on root/sys failed: No such file or directory
mount: mounting /proc on root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg.


BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) build-in shell (ash)
Enter 'help' for a list of build-in commands.

(initramfs)

```

Trying to manually mount the harddrive in Busybox I get the same 'device or resouce busy'.

I've tried to perform e2fsck but no errors found. The root-partition is ext4.

Any suggestion on how to get this kernel to work? Is there an easy way to get an alternative kernel?

I would really like to avoid having too much custom hacking on this box since several users use it, and they have minimal linux experience. Future upgrades will be used by performing aptitude -safe-upgrade.

Any help is apprechiated. Thanks.

---

### Post by khantastic on 2011-12-12
Bump.

---

### Post by khantastic on 2011-12-22
Yesterday the kernel was upgraded to 2.6.32-37-generic. Same problem as mentioned above.

Any hints on a way forward appreachiated.

---

### Post by khantastic on 2012-01-03
bump

---

### Post by Lampi on 2012-01-03
it sounds like your rootfs uuid changed for some reason -> did you change it without changing the entry in /etc/fstab?

you can try this inside busybox:

> 
cat /proc/cmdline #root= will show you what device you're trying to boot
cat /etc/fstab    #make sure the entry for "/" fits the root= argument


Example

cat /proc/cmdline 
root=/dev/disk/by-uuid/7bd47cf3-6df0-4b34-bc37-e35086ade9b2

cat /etc/fstab
# / was on /dev/sda2 during installation
UUID=7bd47cf3-6df0-4b34-bc37-e35086ade9b2 / ext4    errors=remount-ro 0 0 

if I doesn't adjust fstab and it could work again

---

### Post by khantastic on 2012-01-03
Thanks for your reply.

I haven't changed the rootfs uuid, it still works with the old kernel. 

In grub the boot entry for working and non-working kernel have the same params (except the kernel file name of course).

---

### Post by khantastic on 2012-01-16
Bump to top.

---

