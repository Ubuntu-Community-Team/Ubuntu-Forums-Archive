---
title: "Need to be able to see boot messages"
date: 2011-01-12
forum: General Help
---

### Post by jjv on 2011-01-12
Prior to performing an upgrade from 8.04 to 10.04 when I booted I was able to see the various boot messages. I really likes this as every 25 reboots it ran a full fsck on /home. Since this takes a good bit of time it let me know what it was doing.

Since upgrading to 10.04 I cannot see any of these messages. If all I have is a blank screen for several minutes I am getting nervous.

I have attempted changes to the boot line for grub but nothing seems to make any difference.

menu.lst - before upgrade

    kernel /vmlinuz-2.6.22.1.emp12 root=/dev/hd/root ro vga=792 resume2=swap:/dev/hd/hibernate quiet


menu.lst - now

   kernel /vmlinuz-2.6.32-27-generic root=/dev/hd/root ro vga=792 resume2=swap:/dev/hd/hibernate


Having or removing the "quiet" has no effect on the boot behavior.

Note: I have not yet upgraded to grub2. Currently in /boot/grub I have a symbolic link from grub.conf -> menu.lst.


I would like to get the boot time messages back before upgrading to grub2 unless someone can confirm that the upgrade will solve my issue.

Any assistance, comments, observations or suggestions are welcome.

---

