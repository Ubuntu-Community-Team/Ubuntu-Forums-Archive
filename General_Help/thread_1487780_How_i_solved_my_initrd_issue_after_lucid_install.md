---
title: "How i solved my initrd issue after lucid install"
date: 2010-05-19
forum: General Help
---

### Post by psykickuk on 2010-05-19
Hi all, I had a strange issue where my system would not boot after installing a certain selection of packages soon after a fresh install. I dont know if that was the root cause, but it was what I was doing at the time. I got Kernel Panic - Not Syncing VFS Unable to mount root fs on unknown-block(0,0). I tried several fixes, but to no avail, although I received a different error later on : Kernel Panic - Not Syncing no init found.

It sounded like a problem with my initrd images (I knew about them, not entirely sure what they do appart from important for boot). I noticed that by booting from a livecd/usb that the initrd images were too small for a proper install ~1.5MB. To fix them I took the following steps:
```

Boot into livecd/usb.
Open your ubuntu partition so it gets mounted in /media (or mount manually)
Replace 305438c2-b58c-4b45-a139-82e8d5cfb6dc with the UUID of your partition 
(tab autocomplete works wonders here):

##Prepare to chroot into your real install:##
sudo mount -t proc none /media/305438c2-b58c-4b45-a139-82e8d5cfb6dc/proc
sudo mount -o bind /dev /media/305438c2-b58c-4b45-a139-82e8d5cfb6dc/dev
sudo chroot /media/305438c2-b58c-4b45-a139-82e8d5cfb6dc
##you should now be in the root of your real install##

sudo cd /boot
sudo mv initrd.img-2.6.32-22-generic initrd.img-2.6.32-22-generic.broken
sudo mv initrd.img-2.6.32-21-generic initrd.img-2.6.32-21-generic.broken
##repeat for any other kernels you have installed##

sudo update-initramfs -c -k 2.6.32-22-generic
sudo update-initramfs -c -k 2.6.32-21-generic
##repeat for any other kernels you have installed##

sudo update-grub

```Reboot. This got me out of jail with everything working again like a charm! I had to re run sudo update-grub when I was in my real system as it did not list all OS's properly until then. I hope this helps others as I learnt a lot through this process. I still don't know what really caused it (bad shutdown?) but its good not to have to go through the whole install process again when you have it all set up as you like.

---

### Post by pablogrb on 2010-10-24
Reporting that this method still works flawlessly in a Maverick install with kernel 2.6.35-22-generic

---

