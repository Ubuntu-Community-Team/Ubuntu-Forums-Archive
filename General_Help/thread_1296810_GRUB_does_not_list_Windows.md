---
title: "GRUB does not list Windows"
date: 2009-10-21
forum: General Help
---

### Post by keta on 2009-10-21
I know, is that really a problem or has my PC seen the light? :mrgreen: LOL, it actually is a problem for me, even more since Ubuntu fails to load. Here's the story...

I have a PC with two hard disk drives. /dev/sda is mainly for data, whereas /dev/sdb is where Windows was installed. I installed Karmic in /dev/sdb (correctly setting partitions, right) from the alternate CD (the normal installer did not work, but that's another story), and in the last step it asked me if I wanted to install GRUB in the MBR of my first drive. I said OK, but it looks like the system loads from the second drive, so when booting up Windows was automatically loaded and I could not request for Linux.

I reinstalled everything again, but this time I told the installer to put GRUB in the MBR of the second drive. This time yes, when booting up GRUB loads :) (by the way, it's grub 1.97 beta3). The problem is that only Linux is listed, I cannot go to Windows (I hate it but I need it). How can I bypass GRUB and go on to the Windows boot loader?

Now, I have another problem which can interact with this one. After setting my wireless connection with Ndiswrapper, everything seemed to work correctly. I rebooted my system and surprise! dozens of errors show up telling me that the disk has errors, nasty things about ndiswrapper, etc., and finally stops loading. It happened twice (i.e. I have reinstalled everything from scratch twice), and I'm assuming it has to do with ndiswrapper, but I can't be sure. The result is that I can't load Ubuntu: right now I have a PC with no usable OS! #-oHow can I solve this and get into Windows if I can't get into Ubuntu?

Sorry for the long post, I thought it was vital to explain the problem. Any help will be greatly appreciated, thanks in advance!

---

### Post by keta on 2009-10-21
Half-solution found: booted with the Windows install CD, then as I was unable to find any recovery command or so, Windows started reinstalling, I exited the installation at some point and I-don't-know-how at the next reboot the Windows boot loader showed up. I cannot get into Ubuntu but at least can use my computer.

Still, it would be nice if somebody gave some hint on how could I tell GRUB that Windows is present in my hard disk.

---

### Post by compiledkernel on 2009-10-21
[http://gwos.org/udsf/doku.php/core:grub:restore?s](http://gwos.org/udsf/doku.php/core:grub:restore?s)[]=grub

---

