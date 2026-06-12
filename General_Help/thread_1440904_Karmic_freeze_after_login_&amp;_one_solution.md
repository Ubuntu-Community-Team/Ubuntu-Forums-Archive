---
title: "Karmic freeze after login &amp; one solution?"
date: 2010-03-28
forum: General Help
---

### Post by cd-r80 on 2010-03-28
Karmic 9.10 Xubuntu 64-bit 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 04:38:19 UTC 2010 x86_64 GNU/Linux Nvidia 173 driver.

My PC freezes often after entering user & password. Never if already logged in. I found one solution, but I cannot be sure if it helps (I have boot many times & still not sure). If someone could test if this helps?

remove usplash:

sudo nano /usr/share/initramfs-tools/conf-hooks.d/usplash
USPLASH=n
sudo update-initramfs -u


I found: [http://www.techsupportforum.com/alternative-computing/linux-support/428856-solved-ubuntu-freezes-after-login-normal-mode-but-not-recovery-mode-gnome.html](http://www.techsupportforum.com/alternative-computing/linux-support/428856-solved-ubuntu-freezes-after-login-normal-mode-but-not-recovery-mode-gnome.html)

---

