---
title: "Won't boot into win7 after mobo swap"
date: 2009-09-22
forum: General Help
---

### Post by tanusgreystar on 2009-09-22
Hi. I have Win xp, Win7 and ubuntu on same hdd. Everything was fine until I switched mobo and now when I select win7 in grub I get a error 22 drive not found. How to I find out where my Win7 install is in terms of Linux so I can edit grub? Thanks.

---

### Post by stir-crazy on 2009-09-22
If you can get into Linux, start gparted and look at the mapping of all hard drives, and which partitions are labeled ntfs

---

### Post by tanusgreystar on 2009-09-22
dev/sda7

---

### Post by stir-crazy on 2009-09-22
Damn, sorry, thought that was mapped out like that in grub, looking at mine, see it isn't.

For example, mine is:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (loader)
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1
```

Do you have a separate /boot partition?  If so, maybe reinstalling Grub (just formatting the /boot) ought to be a quick and easy fix.  Sorry to have made you spin your wheels there.

---

### Post by tanusgreystar on 2009-09-22
Come to think of it, the only way I was able to get grub to boot win7 was when I ended up having to reinstall ubuntu and then after that, I was able to boot win7 from grub! No I don't have a separate boot partition.

---

### Post by ezsit on 2009-09-22
Then again, I thought Windows was tied to the hardware and won't run if you change the hardware drastically to reduce the possibility of people pirating the software. 

You might need to reinstall Windows and reactivate your copy. I've swapped motherboards under Windows XP and have been forced to call Microsoft to explain the need to swap a motherboard just so that I could get another reactivation number.

---

### Post by tanusgreystar on 2009-09-22
win xp is fine as well as win7. I just can't boot into 7 from grub

---

### Post by louieb on 2009-09-22
> **tanusgreystar said:**
> win xp is fine as well as win7. I just can't boot into 7 from grub

Can you boot win 7 from the XP boot menu? Thats the way it normally works.

Normally win 7 will put its boot loader in another windows install if it finds one and thats the only way it can be booted. It has no boot files in its partition so GRUB can not boot it.

---

### Post by norm7446 on 2009-09-22
Sound's like Win7 is complaining that you have changed motherboard and doesn't like what it finds now. I have never heard of a Motherboard change on a Windows system that did not require a full re-install after a motherboard change, if it did restart you would soon want to do a reinstall with all the probs therein + that is almost your 3 change points up to needing a new Windows license.

---

### Post by tanusgreystar on 2009-09-22
XP is fine with the new mobo. I just had to load the new drivers for it. I'm going to reinstall ubuntu and see if that works again. Then I'll let you know. I"ve been wanting to reinstall 7 anyway, because xp is on the primary partition and everything else is on secondaries, and I would like to phase out of win xp and replace it with 7 on the main partition.

---

### Post by openfly on 2009-09-22
Well as others alluded to from Vista onwards.. ( Not XP ) windows licensing is tied to the motherboard of the system.  If you swap motherboards you need to either somehow migrate your licensing... or buy a new license for the new board.  I am not sure what the current microsoft methodology for this sort of thing is.  

Personally I think it's just a deceptive business practice designed to cheat their customers... but that's just me.

Class action ftw.

---

