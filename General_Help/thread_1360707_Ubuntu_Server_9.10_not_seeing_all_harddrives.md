---
title: "Ubuntu Server 9.10 not seeing all harddrives"
date: 2009-12-21
forum: General Help
---

### Post by HoboJoeTLM on 2009-12-21
I'm running ubuntu server 9.10 and having an issue using a TR8M-B ([http://www.sansdigital.com/towerraid/tr8mb.html](http://www.sansdigital.com/towerraid/tr8mb.html)) external harddrive enclosure.

The problem is that ubuntu is only seeing the first harddrive when I do sudo fdisk -l.

It's connected to my computer through a 4 port sata PCI card ([http://www.newegg.com/Product/Product.aspx?Item=N82E16815280003](http://www.newegg.com/Product/Product.aspx?Item=N82E16815280003)) which is based on the Sil3114.  Although the TR8M-B box is esata, inside the box the port mulitpliers actually use sata connections which is how I have them hooked up.  The TR8M-B box uses the Sil3726 chip.  Also on the TR8M-B box there are lights for when the harddrive is working or on, which only the light for the first harddrive comes on.

I know the harddrives and box work because I had been using it on a Windows 7 install for the past 2 months.  However I used the esata connection and card that came with the box (my ubuntu server pc has no pci-express slots hence the change to a pci card).

If anyone knows why ubuntu won't see any of the harddrives besides the first one, please let me know.

---

