---
title: "Can no longer boot to Ubuntu (removed windows hard drive)"
date: 2011-02-24
forum: General Help
---

### Post by oleink on 2011-02-24
Hey I have ubuntu on 1 hard drive and had windows on the other.  Found out the other drive is failing after like 2 months.  So I removed it so I could get the serial number and return it.  I go to turn on my computer and it gets past the original boot screen and then reaches the point where it should boot to linux but instead all i get is a blinking cursor. ?

---

### Post by drascus on 2011-02-24
is the drive set to master or slave? also try booting with an ubuntu disk and make sure that the drive is set to / in gparted other wise it won't boot. It might be that grub was installed on the drive that failed. if that's the case you can use an alternate install disk to reinstall grub on the drive with ubuntu on it. hope that helps.

---

### Post by oleink on 2011-02-26
> **drascus said:**
> is the drive set to master or slave? also try booting with an ubuntu disk and make sure that the drive is set to / in gparted other wise it won't boot. It might be that grub was installed on the drive that failed. if that's the case you can use an alternate install disk to reinstall grub on the drive with ubuntu on it. hope that helps.

Thanks.  The bootloader was deleted when the windows drive was removed.  I tried to reinstall the bootloader via live cd but windows had screwed things up.  So I had to install a 2nd partition with Ubuntu to get a new bootloader.  Then what I was going to do was get all my files on the new partition.  I got them on the new partition but now when I delete the old partition, grub bootloader gets deleted again and it automatically goes to grub rescue.

---

