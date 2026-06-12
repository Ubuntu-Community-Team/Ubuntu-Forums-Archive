---
title: "Quick question on dual booting"
date: 2010-11-15
forum: General Help
---

### Post by _outlawed_ on 2010-11-15
So I finally decided to test if Ubuntu works on my new desktop, and just have a quick question.

If I install Ubuntu along side Windows 7 on a 30GB partition, and turns out Ubuntu doesn't work all that great, how would I go about deleting the partition to regain the disk space onto my hard drive?

Would I need to use the gparted on the livecd, or use a Windows tool for it?

---

### Post by shadow120 on 2010-11-15
you can use gparted form the live cd

---

### Post by _outlawed_ on 2010-11-15
> **shadow120 said:**
> you can use gparted form the live cd

Awesome, thanks. :D

---

### Post by Animal X on 2010-11-15
you could use wubi.exe to just install it into the windows itself too, no need to dualboot or repartition, and if it doesnt work out just UN-install it.

---

### Post by _outlawed_ on 2010-11-15
> **Animal X said:**
> you could use wubi.exe to just install it into the windows itself too, no need to dualboot or repartition, and if it doesnt work out just UN-install it.

That could have worked too, but Wubi is slower than an actual partition install and I wanted to test the full performance capabilities.

Anyway, have just gotten done installing 10.10 x64 and everything is working great, even the ATI proprietary drivers are working good.

---

### Post by Quackers on 2010-11-16
Please note that deleting Ubuntu and its partitions will still leave grub in the mbr, which will look for partitions that aren't now there. It will fail and Windows won't boot. You will need to repair the Windows bootloader with a Windows repair/installation disc.

---

### Post by Animal X on 2011-02-13
> **Quackers said:**
> Please note that deleting Ubuntu and its partitions will still leave grub in the mbr, which will look for partitions that aren't now there. It will fail and Windows won't boot. You will need to repair the Windows bootloader with a Windows repair/installation disc.

that's odd, i've deleted ubuntu partitions before and left grub, and it still pointed to my windows. Further more i had no need for a repair disk, i just used easyBCD, and it always took care of MBR repairs no prob.

---

