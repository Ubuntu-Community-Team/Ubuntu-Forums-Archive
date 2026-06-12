---
title: "Kernel Panic Breezy Badger 5.10"
date: 2006-04-23
forum: General Help
---

### Post by Costac on 2006-04-23
Ladies and Gentlemen,

I have a KUbuntu Breezy badger that has been working quite well for the last 10 days(thats when I installed it).
I have a Dell Latitude C610 with a 1.2 GHz P3-M, 768MB RAM, 80GB Western Digital Scorpio hdd. I am also running the laptop on a C/Dock II docking station. Ubuntu has been quite happy on this configuration for some time.

After I got freezes/crashes when trying to standby/suspend(hibernate works perfectly) I decided to switch to ext3 to avoid fsck on every boot.
I did that (tune2fs -j /dev/hda6, since I dual boot with XP). I also updated /etx/fstab and restarted and all was well. 

This morning after I switched it on, checked my email and the switched it off it froze. So i did a hard reset and now, upon bootup i get the following:

/sbin/init: error while loading shared libraries /lib/tls/i686/cmov/libc.so.6
invalid ELF header

Kernel panic - not syncing: attempting to kill init

ANd it stays there frozen.

Any suggestions would be welcome.

---

