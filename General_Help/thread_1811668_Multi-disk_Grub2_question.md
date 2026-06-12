---
title: "Multi-disk Grub2 question"
date: 2011-07-25
forum: General Help
---

### Post by ewanmjscott on 2011-07-25
I have virtualised a ubuntu 9.10 server under LVM. This cannot cope with the LVM and leaves me with 2 disks (/ on /dev/sda1 and /boot on /dev/sdb1). I have followed the procedure below and have ended up with a working system again. What I am not clear about is how, after the grub-install to /dev/sda at the end it knows about the grub files on /boot (/dev/sdb1). Is it as simple as the fact that there are symbolic links in the / filesystem - see below-  or is it more complex - and more clever - than this?


Regards
Ewan



lrwxrwxrwx  1 root root    32 Apr 28 19:49 initrd.img -> boot/initrd.img-2.6.31-14-server
lrwxrwxrwx  1 root root    29 Apr 28 19:49 vmlinuz -> boot/vmlinuz-2.6.31-14-server





Procedure:
=========



1) Go to Edit Settings and make sure the biggest disk is presented as the first disk and the /boot is presented as the second disk
  2) Boot with rescue CD
  3-1) Select the correct root device (Device to use as root file system: /dev/sda1
  3-2) Press ALT+F2 to open a console
  4) mount boot partion to /target/boot
  mount /dev/sdb1 /boot
    5) chroot /target
  6) Modify /etc/fstab to remove the logical volumes and replace with /dev/sda1 (/)
  /dev/sdb1 (/boot)
    7) Rebuild initrd
  a) Take a backup of initrd.img-(kernelversion)
  b) mkinitramfs -o /boot/initrd.img-(kernelversion)
c) grub-mkdevicemap
  d) update-grub
  e) grub-install /dev/sda

---

