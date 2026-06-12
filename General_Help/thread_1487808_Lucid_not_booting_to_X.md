---
title: "Lucid not booting to X"
date: 2010-05-19
forum: General Help
---

### Post by sordid on 2010-05-19
Since today, I cannot start to X anymore.
Grub loads, I let it start, then after a while screen goes black, stays black, puter not responding at all, screen goes to power save.
 
I can boot to safe console though but not start X there either.
 
So far I tried Memtest (no errors found) and apt-get update and upgrade. Didn't help either. SafeX doesn't work.
 
Any advice how to fix that?
 
Cheers!

---

### Post by dino99 on 2010-05-19
what distro are you talking about ?
what graphic card ?
which driver installed ?

from grub menu, edit the boot line and add video=vesa before "quiet splash"
then boot (ctrl x)

---

### Post by sordid on 2010-05-19
Hi!
Thanks for the answer but it didn't help either.
The same symptoms - I see the Ubuntu graphic during boot, then the screen turns black and all of a sudden the hard drive turns off and screen stays black.
 
It's weird - I have problems with Lucid I never had with Karmic.

---

### Post by dino99 on 2010-05-19
> **sordid said:**
> Hi!
Thanks for the answer but it didn't help either.
The same symptoms - I see the Ubuntu graphic during boot, then the screen turns black and all of a sudden the hard drive turns off and screen stays black.
 
It's weird - I have problems with Lucid I never had with Karmic.

is it a fresh install or a dist-upgrade ? Is grub1 and menu.lst still installed ? can you boot into recovery mode and run update & install -f ?
Need info about your hardware

---

### Post by sordid on 2010-05-19
Sorry for being vague in the first post!
 
It is an upgrade but has worked ever since the upgrade on release night.
 
The VGA adapter is an Intel 82865G according to lspci.
 
It's Grub2. I did an update-grub already, to no avail.
 
I can boot to recovery console with network, that's absolutely no problem at least.

---

### Post by dino99 on 2010-05-19
from console , install this ppa:

wget deb [http://ppa.launchpad.net/guido-iodice/best-intel/ubuntu](http://ppa.launchpad.net/guido-iodice/best-intel/ubuntu) lucid main

or this one:
wget deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) lucid main 

update, upgrade, reboot

you can try to boot with i865.modeset=0 on the boot line too

---

### Post by sordid on 2010-05-19
Yay!
Thank you thank you thank you thank you!!!
You just saved my butt!
Everything running fine again.
 
I'll put a candle in my window for you!

---

