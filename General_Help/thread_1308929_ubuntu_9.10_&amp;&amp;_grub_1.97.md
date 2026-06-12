---
title: "ubuntu 9.10 &amp;&amp; grub 1.97"
date: 2009-11-01
forum: General Help
---

### Post by samrat1985 on 2009-11-01
I have 2 SATA HDD. I dual boot since `am a game addict`!

[FONT="Courier New"]1. SEAGATE 500GB -> partition_1 (ubuntu 9.10) & partition_2 (ntfs)
2. WDC 500GB -> partition_1 (xp) & partition_2 (ntfs) & partition_3 (ntfs)[/FONT]

I want to manually install grub to SEAGATE HDD (sdb) so that it 
boot "ubuntu" & points to "xp" through chainloader.

	ubuntu 9.10 uses new grub. When I installed ubuntu 9.10
it installed grub to WDC (sda) which earlier had ubuntu 9.04 in
a (now_deleted) partition. Currently I used FIXMBR & can only boot
into windows. 

	Before I use to do `grub-install --root-directory .....`
Now if any one can help me as to how ubuntu live cd work behind the scene
to find xp, ubuntu partitions & add them to menu.lst!!

---

### Post by samrat1985 on 2009-11-04
bump!!

---

### Post by Cushie on 2009-11-04
See:-


Your question #88430 on grub2 in ubuntu :
[https://answers.launchpad.net/ubuntu/+source/grub2/+question/88430](https://answers.launchpad.net/ubuntu/+source/grub2/+question/88430)


Still on-going but this is it!

Cushie

---

### Post by samrat1985 on 2009-11-06
love u man:) i suck at searching:(

---

