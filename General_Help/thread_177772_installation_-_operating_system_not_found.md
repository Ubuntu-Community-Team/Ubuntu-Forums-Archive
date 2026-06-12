---
title: "installation - operating system not found"
date: 2006-05-16
forum: General Help
---

### Post by ecletrik on 2006-05-16
My partition table looks like such:

100mb ext2 /boot (bootable)
4 gb swap
155gb ext3

When I install Ubuntu and reboot it just says "Operating System Not Found" so something went wrong with installing GRUB I guess.

Any help?

---

### Post by xXx 0wn3d xXx on 2006-05-16
[ Try this to restore/install grub.](http://doc.gwos.org/index.php/Restore_Grub)

---

### Post by confused57 on 2006-05-16
When your computer is booting up, if grub is installed, there will be an option that comes up something like to access Grub, press "Esc"(you only have 3 seconds to do so).  If you only have one hd, the OS kernel(s) should be located at hd0,0(hard drive #1, partition #1).

You may have to reinstall Grub, as suggested.

---

### Post by ecletrik on 2006-05-17
I did that, after installing grub (got the base system errors like normal or whatever like it says in the guide) i just turned off the computer and started it again.

Operating System Not Found

---

### Post by ecletrik on 2006-05-17
When I did the formatting it said /media/hda1 for ext2 boot swap for the swap and /media/hda3 for ext3 / (root)

what the christ.

---

### Post by MightyTuna on 2006-05-17
This may be a stupid suggestion, since I'm sure you did this (but I've done things like this before), but did you make sure that your BIOS is set to boot from the hard drive?

---

### Post by ecletrik on 2006-05-17
[QUOTE=MightyTuna]This may be a stupid suggestion, since I'm sure you did this (but I've done things like this before), but did you make sure that your BIOS is set to boot from the hard drive?[/QUOTE]

well, i took the cdrom out of the drive. boot order is floppy, cdrom, hda

---

### Post by xXx 0wn3d xXx on 2006-05-17
[QUOTE=ecletrik]well, i took the cdrom out of the drive. boot order is floppy, cdrom, hda[/QUOTE]
Could you try putting your hdd at the top of the list and then see if it works ? At worst you may be looking at a re-install. You may also be facing a corrupted disc. If none of the above works, could you redownload (if possible) the Breezy/Dapper iso and burn it to a disc ? Make sure to burn it at a low speed. (4x or lower is good)

---

### Post by confused57 on 2006-05-17
[QUOTE=ecletrik]My partition table looks like such:

100mb ext2 /boot (bootable)
4 gb swap
155gb ext3

When I install Ubuntu and reboot it just says "Operating System Not Found" so something went wrong with installing GRUB I guess.

Any help?[/QUOTE]

You may want to reinstall and let Ubuntu do the partitioning for you by selecting "Erase entire disk....."

I'm not familiar with a separate boot partition and 4 gb swap sounds like a lot of swap space.

Did you get through the entire install process, as in remove the install cd and press "enter" to complete the installation?

---

