---
title: "Need Urgent help with Grub 2 and three OS"
date: 2010-02-14
forum: General Help
---

### Post by aviramof on 2010-02-14
i now have three is installed on my computer one is windows 7 on sdb1 two is windows server 2008 on sda3 and ubuntu 10.04 on sda1 and sda2 is swap now when i installed grub 2 on bote mbr using this commands: 

```
sudo mount /dev/sda1 /mnt && sudo mount --bind /dev /mnt/dev &&sudo mount --bind /proc /mnt/proc && sudo chroot /mnt

Code:

grub-install /dev/sda

Code:

grub-install /dev/sdb

Code:

exit

Code:

sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```

it detected seven and ubuntu but not 2008 how can i add it there?

thanks in advance.

---

### Post by aviramof on 2010-02-14
anyone?

---

### Post by oldfred on 2010-02-14
Most of the time if you have two windows install only one is bootable and that is what grub finds.

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

### Post by aviramof on 2010-02-15
Well the problem solved it seem to be that despite the fact that grub 2 did not recognize windows server 2008 but he did recognize windows 7 and when i press windows 7 there is a second dual boot menu there between windows 7 and windows server 2008 a rather unortodox solution as they but this is how it goes i should have noticed it sooner but i didn't because 
i didn't checked windows 7 entry in grub 2.

however i to think that grub 2 should have recognize windows server 2008 but that is another matter.:)

---

### Post by oldfred on 2010-02-15
See my post above for explanation, but windows designed its dual boot by moving key parts of the boot loader (PBR) to the windows partition with the boot flag. You can do a repair of the boot loader (fix boot) if you want. Grub only chainboots by jumping to the partition with windows and expects to find the boot loader there.

---

