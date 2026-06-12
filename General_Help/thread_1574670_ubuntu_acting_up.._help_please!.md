---
title: "ubuntu acting up..? help please!"
date: 2010-09-14
forum: General Help
---

### Post by StevenSteavis on 2010-09-14
Hi, I need some help.. please read:

I installed ubuntu a bit over a month ago or so. Worked fine for a couple weeks then slowly started running in to problems, mostly ubuntu became slow, started freezing, sometimes more than others. I thought I had narrowed it down to an issue with Gwibber and Thunderbird. I reinstalled Thunderbird, removed any add ons and this morning all was well. Now I started up my computer, and I run in to a load of problems.

- First ubuntu was slow/freezing in 'normal' mode again, so I ran it in recovery mode (selected via GRUB). Worked okay for a while, my gf managed to use skype for a while, although somehow using the webcam would shut down skype instantly for some strange reason.

- Then I restarted the computer to get back in to normal mode for version 2.6.32-24 again but during startup of ubuntu I got this message:

[B](..whole lotta numbers..)
Killed

mount: Mounting /dev on /root/dev failed: no such file or directory
mount: Mounting /sys on /root/sys failed: no such file or directory
mount: Mounting /proc on /root/proc failed: no such file or directory
Target filesystem doens't have /sbin/init.
No init found. Try passing init= bootarg.

Busybox v1.13.3 (ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands

(initramfs)[/B]


I tried restarting in to recovery mode of version 2.6.32-24, now I get the same message).

I restart version 2.6.32-21 and it starts but says errors were found on the disk drive. I press "F" to repair errors, system doens't seem to do anything and it automatically reboots without me pressing anything..?!

I try to run windows XP from GRUB menu. Doesn't work -> stays at a black screen. (I have windows installed on a different disk drive, I can always boot back up in to windows by selecting that as the boot drive in bios settings).

I try to start ubuntu again, I select version 2.6.32-24 again from GRUB. Now all is fine and ubuntu seems to run normal, like it did this morning. Weird!!

In disk utility it says the drive where ubuntu is installed on is healthy.


I'm new to linux / ubuntu. I would love it to get to run properly as this is getting quite annoying. Can anyone help? it's appreciated. :KS Is it a HD problem?! Software problem?!

Steven

---

### Post by 3Miro on 2010-09-14
Something (hard to tell what) corrupted the file system and hence the errors. Diagnostic tool fixed the problem when you hit "F". Hopefully this will fix the issue for good.

If you want to get Windows back on the Grub menu, you should o to terminal and type:
```
sudo update-grub
```

---

### Post by dh04000 on 2010-09-14
Actually, I got this part of the message..

"No init found. Try passing init= bootarg.

Busybox v1.13.3 (ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands

(initramfs)"


....when I tried to boot Ubuntu 10.10 beta(both netbook and desktop editions) off a usb drive recently.

I have no idea what it means..... can this be fixed for the next beta?

---

### Post by 3Miro on 2010-09-15
10.10 is not stable yet. There are bound to be problems. Try the development/testing forums for help with that one.

---

### Post by StevenSteavis on 2010-09-22
I figured out the real problem now for all my problems. I have a faulty hard disk drive. New one on the way.

---

### Post by tk189 on 2010-10-16
I have been going through these same problems for a while now.

I swapped my hard drive for a new one in the end. All was good for a few days, then WHAM! System sometimes freezes up when in use then doesn't boot or from firing it up in the morning having worked fine the previous day it doesn't boot.

This excellent post: [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099) has been invaluable to me but I have had to purge and re-install grub via the liveCD so many times I have now lost count.

Last fresh install behaved for four days yet this morning it started again.

I love ubuntu but this is literally driving me to dispair (I work from home freelance).

---

