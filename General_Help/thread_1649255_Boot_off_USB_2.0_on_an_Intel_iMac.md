---
title: "Boot off USB 2.0 on an Intel iMac"
date: 2010-12-19
forum: General Help
---

### Post by Marinozai on 2010-12-19
I have an intel iMac that will not boot off of a USB drive with Ubuntu installed (my PC netbook boots off the usb drive fine) or my external hard drive with Ubuntu installed. I heard somewhere that you cannot boot off of usb on iMacs even if they are Intel, but a Genius bar guy told me diffferent. Then why won't it work for me, and how can I make it? Thanks.

---

### Post by mcduck on 2010-12-20
Yes, you can. Just plug in the USB drive and hold down the option key while turning on the iMac.

But there's a small catch here; Macs only boot from drives with a GUID partition table. And your drive most likely has a MBR partition table instead...

edit: I'm not sure if the Disc Utility in Ubuntu is able to create GUID partition table for you, but since you have a Mac around you can use it's Disc Management tool to do this. Of course doing it will destroy all data on the drive, so you'll need to reinstall Ubuntu to the drive afterwards. And you'll probably have troubles booting the drive on other computers than Macs...

---

### Post by mcduck on 2010-12-20
...actually the article is about older PowerPC macs... :)

It's much simpler on Intel macs, as long as you prepare the drive by paritioning it using GPT. After that you can, for example, use the Startup Disc Creator that comes included in Ubuntu and everything should work fine.

---

### Post by Marinozai on 2010-12-20
> **mcduck said:**
> Yes, you can. Just plug in the USB drive and hold down the option key while turning on the iMac.

But there's a small catch here; Macs only boot from drives with a GUID partition table. And your drive most likely has a MBR partition table instead...

edit: I'm not sure if the Disc Utility in Ubuntu is able to create GUID partition table for you, but since you have a Mac around you can use it's Disc Management tool to do this. Of course doing it will destroy all data on the drive, so you'll need to reinstall Ubuntu to the drive afterwards. And you'll probably have troubles booting the drive on other computers than Macs...

Thanks. Your GUID partition table only things sounds logical, but won't it switch to MBR when I install Ubuntu on it?

---

### Post by mcduck on 2010-12-20
No, it doesn't if you don't completely repartition the drive during the install. (I can't remember if the installer has an option to use GPT instead of MBR, it might actually even have that...)

Formatting existing partitions or creating new ones will not change the partition table type.

This thread seems to have more discussion about using GPT with Ubuntu 10.10: [http://ubuntuforums.org/showthread.php?t=1622938]("http://ubuntuforums.org/showthread.php?t=1622938")

---

### Post by Marinozai on 2010-12-20
Thanks for your help. It wouldnt' boot still, but when I went back int oMac it even thought that the Linux partition was Boto Camp. It still wouldn't boot though...

---

