---
title: "need help deleting ubuntu partions and keeping 7"
date: 2010-12-29
forum: General Help
---

### Post by hifonics10 on 2010-12-29
well ive decided that i wana delete ubuntu from my hdd atleast for now. but i wana keep all my windows 7 files fine can someone tell me how to go about doing that. i had things set up as duel boot  then when i installed 7 it overwrote the ubuntu's boot setup so right now i just wana get rid of it for this hdd. i have it installed on another to play with though so im not completly loose it. thanks in advance for all ur help

---

### Post by wilee-nilee on 2010-12-29
If you have windows booting staright in and working, this means no grub menu. Boot a live Ubuntu cd go to menu-system-admin-gparted, right click the swap partition and turn it off, this should remove the locks on the partitions delete them.

Use the W7 disk manager to either exspand the W7 or build more ntfs, for data if you have room.

If this is not registering just take a screen shot of gparted or the disk manager in W7 and post it.

---

### Post by hifonics10 on 2010-12-29
nvm i found a much easyer way to do it thanks though

---

