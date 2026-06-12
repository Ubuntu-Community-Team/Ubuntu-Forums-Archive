---
title: "Regain partition"
date: 2010-12-15
forum: General Help
---

### Post by williammanda on 2010-12-15
I originally installed ubuntu and then installed linux mint on the same drive (250 GB). I was left with several partitions. I would now like to remove linux mint and restore to my original partitioning. How can I do this without erasing the ubuntu partition? Can I use Disk Utility? The partitions now are:
sda1 - 2GB - swap
sda2 - 127GB
sda3 - 121GB - extended
sda5 - 118GB
sda6 - 3.1GB - swap
Thanks

---

### Post by williammanda on 2010-12-15
I was reading about gparted. Can I delete sda3 partition and then resize sda2 partition to include sda3? Also do I need to be concerned about grub? Lastly, it seems that I will need to do this on the live cd of gparted?

---

### Post by mlentink on 2010-12-15
> **williammanda said:**
> I was reading about gparted. Can I delete sda3 partition and then resize sda2 partition to include sda3?
Yes you can. But since you did not include detailed partition info I do not know which is which, so check that first
> **williammanda said:**
> Also do I need to be concerned about grub?
No. Update grub after your operations to reflect the new configuration 
> **williammanda said:**
> Lastly, it seems that I will need to do this on the live cd of gparted?
Yes. GParted will not let you perform these operations on mounted volumes, so boot off of the LiveCD and make sure to unmount the internal drive and its partitions


Oh, and before I forget: did you make backups? If not, do so now. If yes, do it again, just to make sure. Believe me, I know. I learned the hard way too.

---

### Post by williammanda on 2010-12-16
I made it through the re-partitioning...deleted sda3 and resized sda2 to include sda3. Now I need some advice to tackle grub to remove the linux mint sda3, sda5 and sda6.

---

### Post by williammanda on 2010-12-16
I found this command:
sudo update-grub

I ran it and the linux mint entries in grub have been removed.

It seems I'm back to normal but during the boot up, the grub menu does show up now where it didn't before. It not an issue but something I wanted to point out.

---

### Post by mlentink on 2010-12-16
Good to here everythings is as it should be.

---

