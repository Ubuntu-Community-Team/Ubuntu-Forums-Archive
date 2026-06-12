---
title: "Lost My Grub :("
date: 2009-12-16
forum: General Help
---

### Post by hockeyhead019 on 2009-12-16
hey everybody,

Just upgraded to windows 7 (ehhh it's ok) but i lost my grub so i can't access my ubuntu system :( 

i've done some hw and read the directions on this site [Restoring Grub after Windows Upgrade/Installation]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

so my question is just is there an easier/quicker way to restore my grub than this? or does it have to be done this way? 

if so no big deal but i'm just curious haha

cheers,
Jim

---

### Post by philinux on 2009-12-16
[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

It is the only way via the livecd and using a chroot environment. The above is an alternate description.

---

### Post by hockeyhead019 on 2009-12-16
ok well i just wanted to double check that that was the only way...

thanks

cheers,
Jim

---

### Post by philinux on 2009-12-16
> **hockeyhead019 said:**
> ok well i just wanted to double check that that was the only way...

thanks

cheers,
Jim

Just for completeness. I dual boot karmic and lucid. If say lucid lost it's grub I could do a chroot from karmic without the livecd.

---

