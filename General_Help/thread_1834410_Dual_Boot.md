---
title: "Dual Boot"
date: 2011-08-27
forum: General Help
---

### Post by ghabbaraplus on 2011-08-27
[CENTER][B]i don't speak very well in english but this is my problem:

i have a dual boot pc: ubuntu 11.04 and Win 7, but i wanna make it single boot ubuntu 11.04, how can i do it without format the pc ??
and thanks
[/B][/CENTER]

---

### Post by saltmarshlamb on 2011-08-27
remove the windows partition with a partition editor - there's one on the livecd or usb you used to install with

once you've deleted the windows partition run 
```
sudo update-grub


``` from a terminal in ubuntu

you could resize the ubuntu partition to include the unallocated space - do that with the same partition editor

if you actually installed as a wubi install then it'll be different

---

### Post by ghabbaraplus on 2011-08-27
[CENTER][COLOR=Red][B]THANKS A LOT
i'll try this now :)
[/B][/COLOR][/CENTER]

---

### Post by Mark Phelps on 2011-08-27
BEFORE you try removing the partition you need to confirm that it is NOT installed inside Win7; otherwise, deleting Win7 will delete Ubuntu as well.

Open the Win7 Disk Management tool and look at the partitions (Win7 calls them Drives). You should see a partition that Win7 doesn't recognize -- that will be your Linux partition.  That will be the partition that needs to remain.

If all you see is Windows partitions (including a System and possibly a Recovery partition as well), then you likely have a Wubi install.

---

### Post by ghabbaraplus on 2011-08-27
> **saltmarshlamb said:**
> remove the windows partition with a partition editor - there's one on the livecd or usb you used to install with

once you've deleted the windows partition run 
```
sudo update-grub


``` from a terminal in ubuntu

you could resize the ubuntu partition to include the unallocated space - do that with the same partition editor

if you actually installed as a wubi install then it'll be different



As we say in French: ça marche ! :D
Done !
thanks a lot

---

