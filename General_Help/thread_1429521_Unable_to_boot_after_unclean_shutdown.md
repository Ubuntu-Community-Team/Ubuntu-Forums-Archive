---
title: "Unable to boot after unclean shutdown"
date: 2010-03-14
forum: General Help
---

### Post by kfleten on 2010-03-14
Hi

My laptop with Ubuntu 9.10, did an unclean shutdown yesterday because of low battery. Now, I'm not able to boot. My harddrive is encrypted. When I try booting, I'm asked for the encryption password. When I type this, it seems like sda1_crypt starts fine, but the system will not mount /dev/mapper/[my-directory] to /root, saying "Invalid argument". Then the system drops to initramfs.

I have tried:
1. touch /autofsck (from initramfs and systemrescuecd)
2. e2fsck and fsck (from systemrescuecd)
3. cryptsetup luksOpen /dev/sda1 cryptroot 
   fsck -y -f /dev/mapper/cryptroot  (from systemrescuecd)

So fare, no cure... Any hints ?

---

