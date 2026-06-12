---
title: "Huge problem! Segfault at sudo!"
date: 2010-06-17
forum: General Help
---

### Post by Speedvrod on 2010-06-17
Hey all, i have a huge problem with my server. Today, i suddenly began to get segfaults on my server! Heres the commands i tried to do:
 
[EMAIL="user@vrod:/var/log$"]user@vrod:/var/log$[/EMAIL] sudo apt-get upgrade
Segmentation fault
[EMAIL="user@vrod:/var/log$"]user@vrod:/var/log$[/EMAIL] sudo apt-get update
Segmentation fault

This happens with **every **sudo command i do! I dont have local access to the server, so i would like to know if this can be done remotely? I cant establish any ssh connections anymore, but ive managed to keep a current SSH alive!
 
Please help me, this is urgent!
 
Im running 10.04 with 64 bit!
 
/vRod

---

### Post by philinux on 2010-06-17
18 months old but may help.

[http://ubuntuforums.org/showthread.php?t=995542](http://ubuntuforums.org/showthread.php?t=995542)

---

### Post by Speedvrod on 2010-06-17
Hi. Thx for your reply, heres what i got by doing that command:
 
```
Jun 17 14:09:01 vrod kernel: [449819.992388] cron[28893]: segfault at 940 ip 00007ff74bd7e4e0 sp 00007fff80a21bf0 error 4 in libpthread-2.11.1.so[7ff74bd79000+18000]
Jun 17 14:10:01 vrod kernel: [449879.839926] cron[28910]: segfault at 940 ip 00007ff74bd7e4e0 sp 00007fff80a21bf0 error 4 in libpthread-2.11.1.so[7ff74bd79000+18000]
Jun 17 14:10:01 vrod kernel: [449879.840031] cron[28909]: segfault at 940 ip 00007ff74bd7e4e0 sp 00007fff80a21bf0 error 4 in libpthread-2.11.1.so[7ff74bd79000+18000]
Jun 17 14:15:01 vrod kernel: [450179.068020] cron[28935]: segfault at 940 ip 00007ff74bd7e4e0 sp 00007fff80a21bf0 error 4 in libpthread-2.11.1.so[7ff74bd79000+18000]
Jun 17 14:15:01 vrod kernel: [450179.068035] cron[28934]: segfault at 940 ip 00007ff74bd7e4e0 sp 00007fff80a21bf0 error 4
Jun 17 14:15:01 vrod kernel: [450179.068047]  in libpthread-2.11.1.so[7ff74bd79000+18000]
Jun 17 14:17:01 vrod kernel: [450298.760690] cron[28945]: segfault at 940 ip 00007ff74bd7e4e0 sp 00007fff80a21bf0 error 4 in libpthread-2.11.1.so[7ff74bd79000+18000]
Jun 17 14:20:01 vrod kernel: [450478.298516] cron[29079]: segfault at 940 ip 00007ff74bd7e4e0 sp 00007fff80a21bf0 error 4 in libpthread-2.11.1.so[7ff74bd79000+18000]
Jun 17 14:20:01 vrod kernel: [450478.298539] cron[29078]: segfault at 940 ip 00007ff74bd7e4e0 sp 00007fff80a21bf0 error 4 in libpthread-2.11.1.so[7ff74bd79000+18000]
Jun 17 14:22:59 vrod kernel: [450656.159945] sudo[29081]: segfault at 940 ip 00007f9518b134e0 sp 00007fff4421b7f0 error 4 in libpthread-2.11.1.so[7f9518b0e000+18000]
```

---

