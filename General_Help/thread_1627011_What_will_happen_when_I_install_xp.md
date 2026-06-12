---
title: "What will happen when I install xp"
date: 2010-11-20
forum: General Help
---

### Post by sami8519 on 2010-11-20
Hi,

I dont want to mess with my system, so I opted to ask you first. 

Currently, I have Windows7, then I installed Ubuntu Lucid 10.04, and now want to install Windows xp all these are on a single HDD. My Questions is that; Will I find any problem in booting all three OS? Will Windows xp take over grub loader? I am waiting for your help to start the installation. Thank you.

Edit: I already made a space for windows xp and formatted it in NTFS.

Regards
Sami

---

### Post by bcbc on 2010-11-20
xp will remove grub from the MBR and also prevent win7 from booting. [http://support.microsoft.com/kb/919529](http://support.microsoft.com/kb/919529)

Restoring [grub]("http://ubuntuforums.org/showthread.php?t=1014708") is easy enough. But read the microsoft notes on how to install the win7 boot files in the xp partition - unless, I suppose you can keep booting win7 from grub.

---

### Post by sami8519 on 2010-11-20
Thanks mate. Your post is very useful.

Best Regards
Sami

---

### Post by northern lights on 2010-11-20
[http://www.virtualbox.org/]("http://www.virtualbox.org/")

---

### Post by sami8519 on 2010-11-20
> **northern lights said:**
> [http://www.virtualbox.org/](http://www.virtualbox.org/)

Thanks a lot mate. I have always wondered what virtualbox is and wanted to read about it but always forget. Maybe now is the time I know what VB actually is. Thanks again.

Regards
Sami

---

