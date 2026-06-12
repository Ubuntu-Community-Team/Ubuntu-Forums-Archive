---
title: "Problem with X after a libc6 update"
date: 2010-01-23
forum: General Help
---

### Post by DL21 on 2010-01-23
Hi,
I updated ubuntu today, and a libc6 update was available, so I updated it.
The problem is that when I rebooted my PC, after the ubuntu white logo, I saw strange lines on my screen and X server wasn't booting.
I use Ubuntu 9.10 Karmic Koala.

Please help me, DL21.
(PS : Sorry if my english is bad, i'm French)

---

### Post by sergio.otero on 2010-01-23
I had the same problem with a ATI HD 3650 and fglrx ati propietary drivers 9.11 or 9.12 (don't remember)

Here's what i've made:

 * Reboot and select recovery mode
 * cd /usr/share/ati
 * sh./*fglrx*-*uninstall*.sh
 * sudo shutdown -r now

Now the system doesn't hang but there's no image, so:

 * Go to a terminal with ctrl+alt+f2
 * cd /etc/X11 => my xorg.conf is empty (i know in Ubuntu 9.10 xorg.conf may be missing, but empty??)
 * sudo mv xorg.conf xorg.conf.backup
 * sudo cp xorg.conf.ubuntu xorg.conf
 * sudo shutdown -r now

Now xserver runs in low mode, but i can login, so:

 * Download de latest ati driver (9.12)
 * Follow the instruction to install
 * Reboot

And everythings works again

I like Ubuntu, but if i didn't were an advanced user, i would have change back to Windows a long time ago. I've had too many graphic problems. 

Maybe the problems are due to a bad support from ati/amd, but the result is that basic users can't use it as "easy" as Windows.

---

