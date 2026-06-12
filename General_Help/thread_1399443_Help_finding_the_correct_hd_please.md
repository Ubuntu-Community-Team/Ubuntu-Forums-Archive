---
title: "Help finding the correct hd? please"
date: 2010-02-05
forum: General Help
---

### Post by fidgaf on 2010-02-05
Strange set-up, but Ubuntu insists on giving me sd and menu.lst wants dh.

I had Ubuntu booting on one hard drive and XP booting on another all running from the /boot/grub/menu.lst

It worked perfectly and looked like this inserted at the beginning of the menu.lst options:

```
title Microsoft Windows XP Proffesional
rootnoverify      (hd2,0)
savedefault      
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1
```

I have needed to install a complete virgin install of XP which involved a messy format of the old partition which changed the partition's drive letter and probably did other stuff.

XP works fine from its (new?) home.

Ubuntu works fine from its old home.

/boot/grub/menu.lst no longer allows a boot from the menu selection as it did before.

How (other than guesswork) can I find the dh name for the (new?) XP partition?

df tells me XP is on /dev/sdc5

df says Ubuntu is on (haven't a clue really) sda1 ... probably.

Meaningless to me I'm afraid.

I can see and mount all XP and Ubuntu partitions/drives in Ubuntu if that helps.

Ubuntu is bang up-to-date.


Thanks

---

### Post by fidgaf on 2010-02-06
Progress of the blind so far:

Found device.map and got this:

```
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
(hd3)	/dev/sdd
```

Best guess is the drive is hd2 so that's probably the same.

I'm guessing that hd2,0 refers to the first partition.

I've tried hd2,0 hd2,1 hd2,2 hd2,3 hd2,4 and hd2,5 (sdc5 probably means partition 5 - who knows) but none of them work.

Need something else but have no clue what.

Pulling my hair out here. :icon_frown:

---

### Post by fidgaf on 2010-02-06
Damn Microsoft.

XP was a clean fresh install on a re-formatted partition (where the old one was)and booted fine from its own hard drive.

But not from /boot/grub/menu.lst (see above).

fixmbr on XP hard drive sorted the problem and the old menu.lst works like a charm.

Back to normal now.

Phew!

:D

FYI: Ubuntu on old PATA drive, XP on SATA drive.
Total drives 2 x 500GB SATA + 2 x 80GB PATA

---

