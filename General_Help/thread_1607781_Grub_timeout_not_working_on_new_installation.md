---
title: "Grub timeout not working on new installation"
date: 2010-10-28
forum: General Help
---

### Post by googlybear on 2010-10-28
Just installed kubuntu 10.4 on a netbook (dual booting with WinXP) but by default grub just boots directly into kubuntu. 

When editing /etc/default/grub I have tried setting the timeout to 10, 100 and now its at -1 (which should be sit there forever)

I then run update-grub which generates the new config

reboot and the same thing happens, it immediately boots to kubuntu. I see the menu appear for a split second, but no matter how fast i try, i cannot see to hit any button fast enough to kill the timeout so i can switch to XP.

Any thoughts / help would be very welcome.

Regards
Dave.

---

### Post by Quackers on 2010-10-28
Hold down the shift key while booting. This will bring up the grub menu. However, if it's booting directly to Ubuntu it thinks that's the only system installed, so doesn't see your XP.

---

