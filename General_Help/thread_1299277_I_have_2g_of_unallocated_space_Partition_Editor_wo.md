---
title: "I have 2g of unallocated space Partition Editor wont let me use?"
date: 2009-10-23
forum: General Help
---

### Post by PsychedelicWonders on 2009-10-23
I dont have enough room on my Windows partition to upack my new Win 7 software to make an .iso.

So I went into Ubuntu to use Partition Editor to give me just a little more room to complete my upgrade.

There are 2g worth of unallocated space (it shows grey in PE) that I can not seem to use to expand my main windows partition?

Does anyone know why I cant?

Also, there are roughly 2g worth of space available on my Ubuntu partition that I would like to steal just for purposes of the upgrade, but when I try to unmount that partition in PE, it tells me that it cant?  

So how can I also unmount that partition, strip the extra 2g's worth of space and hopefully add all 4 to the windows parition so I can finish up with my Win 7 upgrade?

---

### Post by CatKiller on 2009-10-23
> **PsychedelicWonders said:**
> Does anyone know why I cant?

Not without a screenshot or a significantly better description of your current partition layout, no.

> but when I try to unmount that partition in PE, it tells me that it cant?

If you unmount the partition that Gparted is running from, how would Gparted continue to run? Use a live environment - live cd, live, USB, Ubuntu install disc - to do your partitioning in. If you need to move a swap partition, or change an extended partition that contains your swap partition, you'll need to turn swap off.

---

