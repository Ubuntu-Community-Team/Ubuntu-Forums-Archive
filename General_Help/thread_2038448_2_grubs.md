---
title: "2 grubs"
date: 2012-08-06
forum: General Help
---

### Post by Ron O on 2012-08-06
Installed 12.04 64 bit on sda1 and later installed 12.04 32 bit on sda3. I want the first installation on sda1 to be my default OS only occasionally booting to the 32 bit.

I thought GRUB loaded in the boot sector of the entire drive, but now I have 2 GRUBs, one for each OS located on their respective partitions, and the system is using the 32 bit Grub on sda3, probably because it was the last OS loaded. The problem with this is that in the 32 bit GRUB, sda1 64 bit is the 5th menu entry (4th since the first is 0) listed while in the original GRUB it is the 1st. Even though I set the default in the active GRUB to load sda1 (5th entry), any kernel updates will change the sequence, no longer having the latest kernel of sda1 at the top. Also if I decide to delete sda3, the 32 bit install at a later time, I will lose my boot loader.

Is there a way to reactivate the GRUB on sda1 64 bit and not use the 2d GRUB on sda3 at all?

---

### Post by drs305 on 2012-08-06
Boot into your preferred OS. Then run:
```
sudo grub-install /dev/sda
```
This will make it the default GRUB. Don't include a partition number in the command - you want GRUB's information in the MBR and not in the partition boot record.

The controlling GRUB's main OS will always be listed first in the booting menu.

---

### Post by Ron O on 2012-08-06
Thanks for a quick response!

This sounds almost too easy, especially after reading some of the instructions posted for the GRUB Customizer application at [http://ubuntuforums.org/showthread.php?p=10340183](http://ubuntuforums.org/showthread.php?p=10340183).

I was hoping to avoid add on software of this type (with overlays and scripts) and fix it as you describe, but I have 3 questions.

1. I thought the MBR was too small to accomodate all of the GRUB menu entries and that was why GRUB gets installed on the partition(s) where the OS resides?

2. If your solution works, what happens to all the GRUB files (.cfg etc) on the 2d OS (32 bit Ubuntu)? Do they get overwritten and corrected or do they stay the same?

3. Will it still be safe to use the update-grub command from either partition, or will that mess something up?

---

### Post by drs305 on 2012-08-06
> **Ron O said:**
> 
1. I thought the MBR was too small to accomodate all of the GRUB menu entries and that was why GRUB gets installed on the partition(s) where the OS resides?
Although the command is "grub-install", it doesn't 'install' much on the MBR. It mostly just points the system to the GRUB folder, where the majority of the files are located.

> 2. If your solution works, what happens to all the GRUB files (.cfg etc) on the 2d OS (32 bit Ubuntu)? Do they get overwritten and corrected or do they stay the same?
Those files remain untouched. In fact, the contents of the grub.cfg file on the non-default OS is 'mined' for it's entries when your controlling GRUB rebuilds its menu.

One thing to watch for - if booted into your other OS, certain file operations may run 'grub-install' and change the MBR back to that OS. It isn't a common thing, but when it happens you will have to redo what you did the first time. 

> 3. Will it still be safe to use the update-grub command from either partition, or will that mess something up?
You can run the "update-grub" command from either OS, but it will only update the files on that OS's partition. In fact, you should run it so when the default GRUB 'mines' the other GRUB's grub.cfg file (see answer 1), the contents are current.

Note: Running update-grub on one OS will *not* update the files on the OS.

---

### Post by Ron O on 2012-08-06
Worked like a charm. Thanks!!  Especially since trying to unravel the documentation on GRUB2 was no small task. This not only reactivated my original GRUB but also put the original default at the top of the list which should get pushed down by future kernel updates- exactly what I was looking for. I'll tag solved.

---

