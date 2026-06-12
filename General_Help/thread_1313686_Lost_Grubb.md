---
title: "Lost Grubb"
date: 2009-11-03
forum: General Help
---

### Post by protoguy on 2009-11-03
Hi all!
I am fairly new to Ubuntu and just upgraded to 9.10.  I have Windows on my original hard drive and Ubuntu on my new hard drive.  The original hard drive crapped out and took windows down with it.  Unfortunately, the boot menu is also on the old hard drive, so now I cannot boot into Ubuntu. Can I install Grubb on the new hard drive without reformatting? Can I put grubb on a cd and install from there?

---

### Post by ranch hand on 2009-11-04
If you have a live cd you should be able to recover grub.  I am sure that you just had grub as boot/root for the MBR  on your other drive.  This can be changed.

We do need to know some things though.  What grub are you using?  With an upgrade you should still have grub-legacy.  Do you have a LiveCD of 9.04 or earlier?

---

### Post by protoguy on 2009-11-04
I have the Karmic Koala install disk. Is that the same as the LiveCD?

---

### Post by RJ12 on 2009-11-04
Does it have a option to try without installing (something like that) if so then yes. Im 99% sure it is (doubt you used alternate **TEXT** based)

---

### Post by protoguy on 2009-11-04
Yes, and I am there. It gives me an option to mount the file system, which I did. Now, can I install grub from the terminal?  I found the following under grub 2 on this webwsite, should I follow it?

[LIST=1]
[*]Reinstall GRUB 2:  
[LIST]
[*]Substitute the correct device - sda, sdb, etc. Do *not* specify a partition number. 
[/LIST]
**sudo grub-install /dev/sdX**  
[*]Verify the install (use the correct device, for example *sda*. Do *not* specify a partition):  **sudo grub-install --recheck /dev/sdX** 
[*]Exit *chroot*:  **CTRL-D** on keyboard 
[*]Unmount devices:   **sudo umount /mnt/dev** 

[LIST]
[*]If you mounted a separate /boot partition:  **sudo umount /mnt/boot** 
[/LIST]
[*]Unmount last device:  **sudo umount /mnt** 
[*]Reboot. **reboot**
[/LIST]

---

### Post by ranch hand on 2009-11-04
Should work as long as grub is not contaminated in some way.

---

### Post by protoguy on 2009-11-04
well, I ended up not using the instructions that I found. Looked to scary.  So I just pushed a bunch of buttons and switched some wires around. Works fine now...

Windows is toast though, not sure whether it was killer koala or just the hard drive going out.  Someday maybe I will know.

:lolflag:

---

### Post by ranch hand on 2009-11-05
So, at least you got something good out of it.

Sorry, just one of those folks that will not have MS on my box, couldn't resist.

---

