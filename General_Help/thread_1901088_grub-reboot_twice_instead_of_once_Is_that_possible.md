---
title: "grub-reboot twice instead of once? Is that possible?"
date: 2011-12-27
forum: General Help
---

### Post by Sopalajo de Arrierez on 2011-12-27
Hello, friends.
   My question is easy: can grub-reboot make my computer boot to the selected option twice (or more) instead of only for the next reboot?
   This is: the next two (or "n") reboots will be redirected to de selected option, not to the default one.
   Or is there any trick or similar program that could do this?

   If necessary, I could explain why do I need this (a matter or multi-boot with several Windows operating systems), but it will be a bit complex to tell.

---

### Post by oldfred on 2011-12-28
If you were in Ubuntu you could write a script to edit grub.cfg (the file you are not supposed to edit) and change the entry for default boot.

You can install grub2's boot loader to a FAT32 or NTFS partition and use a Windows script to edit the default boot. But in the FAT32 or NTFS it will not be Ubuntu's standard boot that sudo update-grub updates. You will totally have to configure your own grub.cfg. (I do this on my USB flash drives to boot ISOs).

[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition)

Essentially the same commands to install to a grub only partition on a hard drive.
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

---

### Post by Sopalajo de Arrierez on 2012-01-17
Thanks, friend oldfred, for answering. :-)
I will check your solutions.
They have the problem of using different partitions for configuration files, but it is, of course, a possibility. Thanks a lot for your scripts ;-)

I hope, in a near future, "grub-reboot" will add some parameter like "--reboot-times=<n>" to reboot "n" times. It could be useful, as M$ Windows sometimes auto-reboots when installing Operating System updates, you know.

---

### Post by oldfred on 2012-01-17
You can also get it to auto reboot to last successful boot. So then a Windows reboot will reboot to that. But to change it you would still have to manually boot.

Reboot grub to different system default
[http://ubuntuforums.org/showthread.php?t=1310463](http://ubuntuforums.org/showthread.php?t=1310463)

---

