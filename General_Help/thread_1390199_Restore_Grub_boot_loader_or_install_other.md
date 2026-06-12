---
title: "Restore Grub boot loader or install other"
date: 2010-01-25
forum: General Help
---

### Post by carlosgs91 on 2010-01-25
.

---

### Post by amsterdamharu on 2010-01-25
After installing windows the chances are grub is gone and you need to re install it again. If you have an ubuntu cd you can run that cd (live cd) and restore grub.
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Maybe grub4dos will work under windows 7, that can boot ubuntu without using grub but I am not sure.

There is a way to boot ubuntu with the windows 7 bootloader but I am not sure how to do that either.

---

### Post by oldfred on 2010-01-25
Do you want to separately boot each copy of windows from grub or let windows combine boots so that grub choose's one and then in windows boot you choose which windows. 

Much of this is on Vista but Win7 is the same.
[http://ubuntuforums.org/showthread.php?t=1279218&highlight=booting+MS+products](http://ubuntuforums.org/showthread.php?t=1279218&highlight=booting+MS+products)
louieb's suggestion:
Just a note about dual booting 2 MS products. When you install the 2nd one - the installer will put its boot loader in the partition with the boot flag on (usually the partition holding the 1st MS product). And the 2nd product can only be booted thru the boot loader in the 1st product.

To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

Vista copies boot manager to one 
[http://members.iinet.net/~herman546/p15.html#BOOTMGR_is_missing](http://members.iinet.net/~herman546/p15.html#BOOTMGR_is_missing)
Moral of the story - look on other NTFS partitions for the missing bootmgr and Boot directory.

---

