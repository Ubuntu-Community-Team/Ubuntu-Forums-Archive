---
title: "wont boot correctly"
date: 2012-07-09
forum: General Help
---

### Post by boregard on 2012-07-09
hi all , after reinstalling precise i cant restart computer from the shutdown menu. when i select restart all i get is a black screen and have do hard shutdown a couple of times to get computer to boot. any help with this will be much appreciated. thanks

---

### Post by boregard on 2012-07-09
i found more info that might be helpful.

---

### Post by Redblade20XX on 2012-07-09
I assume that since you'll recently reinstalled you don't have a lot of personal data on the system. :)

So why don't you reinstall the system, format the entire drive and create new partitions? It's much quicker than realigning the partitions with much less headache.

- Red

---

### Post by boregard on 2012-07-09
> **Redblade20XX said:**
> I assume that since you'll recently reinstalled you don't have a lot of personal data on the system. :)

So why don't you reinstall the system, format the entire drive and create new partitions? It's much quicker than realigning the partitions with much less headache.

- Redi have reinstalled, but don't know how i should create new partitions. thanks

---

### Post by oldfred on 2012-07-09
It looks like you have an UEFI system as first partition is efi and drive is partitioned with gpt not the old MBR(msdos).

You can still use gparted with gpt drives. One advantage of gpt is all partitions are primary.

MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[http://en.wikipedia.org/wiki/Extended_boot_record](http://en.wikipedia.org/wiki/Extended_boot_record)

GPT Advantages srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

If it is not shuting down, you do need to remember the elephants to make sure everything is closed correctly. Not sure why it may not be shutting down correctly.

Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

---

### Post by boregard on 2012-07-15
i used gparted advance partition feature and selected gpt. its working now. thanks to everyone for your help. regards

---

