---
title: "is it possible to partition a mounted drive"
date: 2011-11-05
forum: General Help
---

### Post by dan0804smith on 2011-11-05
so i need to duel boot 

im trying to create a new partion to put windows on.

the only partion that i can take form in my main one which has about 130gb of free space.  is it possible to split this partition?

---

### Post by dan0804smith on 2011-11-05
or i could back up my wierless driver on to a flash drive.  install windows first then ubuntuu again.  any one know how to back up your wierless driver?

which option is better?

---

### Post by dan0804smith on 2011-11-05
or i could just delete my swap partition and put windows in that

---

### Post by dan0804smith on 2011-11-05
could i boot into my computer with the live cd then unmount the partion and split it?  does unmounting it delete the stuff on it?

---

### Post by prodigy_ on 2011-11-05
1) You don't mount a drive, you mount a partition.
2) You can resize (shrink) a partition but you need to unmount it first. If the partition contains root file system you'll need something else you can boot from (e.g. a Live CD). And **you really should consider making a backup first**. Unmounting a partition doesn't cause it to lose any data but resizing might.
3) I wouldn't suggest deleting the swap area, though it's up to you. (If it's big enough to be a Windows system partition, it's probably too big.)
4) You can install operating systems in any order but if you install Windows last, you'll need to reinstall Grub bootloader for dual boot:
[https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2)

P.S. All in all you sound awfully confused and you probably should read a couple of HOWTOs first to make sure you understand what you're doing. I'd suggest:
[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

