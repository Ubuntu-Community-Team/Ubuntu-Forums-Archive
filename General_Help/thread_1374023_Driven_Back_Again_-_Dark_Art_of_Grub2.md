---
title: "Driven Back Again - Dark Art of Grub2"
date: 2010-01-06
forum: General Help
---

### Post by Quarkrad on 2010-01-06
OK - I messed up the sound trying to get the mic to work on 9.10 and having no sound at all decided to reinstall a saved image via Clonzilla.  I have done this before - the issue is restoring Grub2.  Even put my solution on this forum.  Now it isn't working.  I have tried the following pages:

****ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7****

****[www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)[B]

****wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD****

****ubuntuforums.org/showthread.php?t=1195275****

None of them work - even though there seems to be a common thread/method.  Each time I reboot I get either sh.grub  or grub> smiling at me from the screen.  It would have bee quicker to re-install the whole thing again.  I have Ubuntu 9.10 on sda1 and winXP (which is boot) on sda2.  I keep entering the same commands via LiveCD terminal but I cannot restore grub2!!!!!!!

---

### Post by Leppie on 2010-01-06
boot with a livecd and run this command:
```
cd ~/Desktop \
&& wget 'http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.44/boot_info_script044.sh/download' \
&& chmod 755 boot_info_script044.sh \
&& sudo ./boot_info_script044.sh
```

post the RESULTS.txt

---

### Post by Quarkrad on 2010-01-06
Very sorry and I really appreciate your response but I've had to re-install.  I'm under pressure to do a few things for friends that I've recommended migration to Ubuntu and I need the system up and running.  Once I'm over this work I will reinstall my image and have another go.

---

### Post by Leppie on 2010-01-06
usually restoring grub2 isn't that much work.

---

