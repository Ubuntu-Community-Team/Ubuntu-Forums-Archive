---
title: "after resizing swap showing &quot;no device to boot&quot;!!!"
date: 2009-12-11
forum: General Help
---

### Post by shaon3343 on 2009-12-11
[B]hi there, yesterday i was using my favourite ubuntu 9.04 . In the root drive of ubuntu 9.04 there was only 160MB available space, so i wanted to resize my swap to get an ext4 partition and with a ubuntu live cd i resized my swap to 950MB from 1.9GB. after resizing i rebooted my pc and while booting it showed "no device to boot" :( :(!!! then i fixed the grub with a live cd and reboot again but there was the same thing no device to boot!!  can anyone tell me what happened there? 
( after that i've newly installed ubuntu 9.10 :D :D. and now i'm enjoying ubuntu 9.10 :P) [/B]

---

### Post by Vishnu V on 2009-12-11
I think is due to change of uuid or logical name of disk in fstab
boot from live cd.
can you post the output of 
commands
```
sudo blkid
sudo fdisk -l

```

---

### Post by shaon3343 on 2009-12-11
**thanks for reply , but its not happening now after i installed ubuntu 9.10 on ubuntu 9.04 ( because of that failure i installed the newest release). **

---

