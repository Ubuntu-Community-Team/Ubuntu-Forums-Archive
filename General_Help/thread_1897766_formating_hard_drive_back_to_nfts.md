---
title: "formating hard drive back to nfts"
date: 2011-12-19
forum: General Help
---

### Post by 40ftcobb on 2011-12-19
ok so not that i dont love ubuntu,the problem lies in the fact that i love my phone more  i guess lol.
but i need to put windows back on my hp mini 110,(ubuntu also,but windows first)
i began my journey with ubuntu with screwing up my mini erasing everything recovery partition,windows,the hole shabang.
but i fixed it with a fresh install with a new usb of ubuntu 11.10.
now the problem i want to reinstall windows,i got my xp on a usb,i got my key code i ready to roll but i dont know how to format my hard drive to instal windows because windows needs to be installed on nfts,not whatever it was formatted to when ubuntu was installed.

anyone have any ideas?

---

### Post by CaptinGoogle on 2011-12-19
Do you want to keep your Ubuntu partition or completely wipe it to go back to Windows?

If you just want to go back to Windows completely then just load up your Windows installer and at it will handle the correct reformatting of the partition.

---

### Post by Buntumatic on 2011-12-19
You do not format the hard drive. At least not in Windows.
Technically you can format your hard drive, yes, and you can use it in some POSIX compliant OS. But normally you format **partitions**. One partition for Windows formatted in NTFS. Other partitions formatted as EXT4 or XFS or UTF2 or whatever you like for more advanced operating systems.

---

### Post by 40ftcobb on 2011-12-19
thanks for the replys

k i want to keep ubuntu,and partition my hd for windows install
now what i did was install another ubuntu(10.04)and i was just going to use gparted to format that partition in order to install windows.
think that will work?

---

### Post by CaptinGoogle on 2011-12-20
> **40ftcobb said:**
> thanks for the replys

k i want to keep ubuntu,and partition my hd for windows install
now what i did was install another ubuntu(10.04)and i was just going to use gparted to format that partition in order to install windows.
think that will work?
I wouldn't bother with even that. When running the Windows installer just pick whichever partition you want to override and let Windows install on that. No reformatting with Ubuntu is necessary.

---

