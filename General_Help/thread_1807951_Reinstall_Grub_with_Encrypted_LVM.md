---
title: "Reinstall Grub with Encrypted LVM"
date: 2011-07-19
forum: General Help
---

### Post by hello cruel world on 2011-07-19
I need to re-install grub bootloader, as it was overwritten. The problem is the encrypted partition does not show up using boot-repair on the live_cd. I installed lvm2 and mounted them, but cannot seem to make any progress passed that. I was following this [guide]("http://ubuntuforums.org/showthread.php?t=1347375").

Here is my partitioning scheme:

partition1 - windows7
partition2 -extended
...partition3 - boot
...partition4 - crypto(lvm, ubuntu 11.04)
......partiton5 - lvmroot
......partiton6 - lvmswap
...partition7 -backtrax5
partition8 - storage

---

### Post by hello cruel world on 2011-07-20
Follow this [http://stephentanner.com/index.php/2011/05/restoring-grub-for-an-encrypted-lvm/](http://stephentanner.com/index.php/2011/05/restoring-grub-for-an-encrypted-lvm/)

solved!

---

