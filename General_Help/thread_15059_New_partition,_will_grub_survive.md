---
title: "New partition, will grub survive?"
date: 2005-02-11
forum: General Help
---

### Post by YorHel on 2005-02-11
Hi!, 

I have Ubuntu for at least a month now, and I love it! Since ubuntu is my first time with linux ever, I just want to try some other distro's. 

But I think this will be a problem, my partition table:
```

hda
 hda1 - old windows partition, haven't used for at least a month now
 unpartitioned space - about 50 GB
 hda2 - ubuntu (with grub for booting)
 hda3 (extended) - swap

```
I am thinking of partitioning that unpatitioned space, and use shared swap for both distro's.
As you can see... when I create a new partition there, hda2 will be hda3, and grub will be on hda3, which won't be bootable...

How can I make grub bootable after creating that new partition, and will ubuntu automatically use hda3 as root and hda4 as swap?

---

### Post by az on 2005-02-11
Hmm.  It depends on what partitions you create.

If you create a new hda2, then the current hda2 will become hda3 and so forth.  If you create another extended  partition, you may even get a hda2 hda4 hda5...

You will need to see what partitions are created.  Don't panic.  You can, at any time, go into the grub listing and edit the grub configuration (on-the-fly:  You have booted grub, but you have not chosen the OS you want to boot, you can edit their parameters before going ahead and booting.

Select the entry you need to edit, and press "e"
Go to the line you need to change (the root line) and edit hda2 to hda3 or whatever.
press "b" to boot.

You will need to edit the fstab of your root partition to tell it to use the proper partition for root, too!  You will need to do this beforehand.  You can change this with your new linux installation.

If you have any live cd handy, you should easily be able to get out of any trouble.

---

### Post by YorHel on 2005-02-12
ah well... I already 'fixed' the problem by 'accidently' deleting that windows partition :)

---

