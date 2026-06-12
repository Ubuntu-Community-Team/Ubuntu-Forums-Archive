---
title: "Change to RAID"
date: 2010-01-09
forum: General Help
---

### Post by Zilioum on 2010-01-09
I currently have a 1TB harddrive in my pc. It has three partitions: Ubuntu (500Gb), Xp(300Gb) and Win7(200Gb). Ubuntu is the primary partition and I use Grub 2 as bootloader. 
I now want to switch to a 1TB RAID 0. I already bought two 500GB Harddrives, but I'm not really sure how to go through with this:

What I would have done:
[LIST]
[*]Connect the two 500GB HD
[*]Create the RAID
[*]Copy everything from the single disk, to the RAID.
[*]Make the RAID the boot HD
[/LIST]
With this come some questions:
[LIST]
[*]Software or hardware RAID ?
[*]Is it even possible to copy a whole operating system?
[*]Wont there be problems if Ubuntu copies itself?
[*]If yes: Should I use the Ubuntu CD?
[*]How do I change the boot HD?
[/LIST]

Some help would be very appreciated, especially if someone has already done this. 

Cheers

---

### Post by mk1w86 on 2010-01-09
I have used software RAID 0,1 and 5 before and the answers to your questions below all assume you are using software RAID.

> # Software or hardware RAID ?

Unless you have proper RAID hardware (normally only found in servers and high end workstations) you would probably be better off with software RAID.

> # Is it even possible to copy a whole operating system?

Ubuntu yes, although you might have to set it up on a non raid partition and reserve the raid 0 volume for your data (I think this would be a better setup anyway).  If you want to copy Windows you might have problems although I assume you are leaving Windows XP and 7 on your current drive.  You would also have problems running Windows on the software raid volume.

> # Wont there be problems if Ubuntu copies itself?

If you are copying to a non raid partition as described above initially there might be but they should be fixable e.g. installing and configuring grub.  The problem is I don't know how you would set up raid 0 before copying Ubuntu.

> # If yes: Should I use the Ubuntu CD?

You will need it the install grub on the new hard drive.  To set up raid itself you will have to do that from the system running on your hard drive.

> # How do I change the boot HD?

If you mean you want to boot your current drive or your new raid drive you would change that from the BIOS.


I don't know if anyone else knows a better way of doing this so you can transfer your current Ubuntu installation to a raid 0 volume.  Also I am not sure if grub2 can boot from a raid 0 volume although I would have thought it would.

Personally I think the best way to run Ubuntu from a raid 0 volume would be to start from scratch with Ubuntu on the new drives and set up raid 0 during installation.  You may need the Alternate install CD to do this.  I would also still put / on a non raid partition so grub can definitely boot it and if you ever have any problems with raid you can still boot into the system to fix any problems.

If you have any more questions or want anything clarifying just ask. :D

---

### Post by falconindy on 2010-01-09
[This](http://www.mail-archive.com/grub-devel@gnu.org/msg08345.html) suggests that Grub2 will boot directly from a RAID0 array. I've just recently been fooling around with transferring OS's around (both on a VM and live on 2 computers), and it works fairly cleanly. First time around was to switch my root FS to btrfs, and the 2nd time around was on my dad's computer to switch him to RAID0. I did have some issues with permissions after the transfer, but I'm fairly sure they were my own fault. A little probing of the system logs was enough to determine what needed to be chown'd and/or chmod'd.

**Things I learned:**
* Make sure you use a robust method to transfer the data off and back (the tutorial in 'info cpio' has a solid method). You need to be able to handle symlinks and other special files intelligently.
* Your /dev directory, while created dynamically, needs to have the 'null', 'console', and 'zero' devices at boot time or else you won't boot. Proper permissions are important as well. The other tmpfs mounts (/proc and /sys) you don't need to worry about aside from creating the mount point.
* The grub install needs to be done manually. Honestly, I'm not sure how this is done as I still use grub-legacy out of sheer loathing for the unnecessary complexity added by grub2.
* Make sure to update your fstab!

Arch's wiki page on [RAID and LVM](http://wiki.archlinux.org/index.php/Installing_with_Software_RAID_or_LVM) is insanely good (just skip the parts about LVM). The tools used to create the RAID array itself are standard, and the process is well outlined.

Good luck!

---

### Post by Zilioum on 2010-01-09
Thanks for your great answers! 
> 
Personally I think the best way to run Ubuntu from a raid 0 volume would be to start from scratch with Ubuntu on the new drives and set up raid 0 during installation. I agree, but I really spent a lot of time configuring my current set up, so I dont really feel like starting from scratch again if its not absolutely necessary. Is there a way to export/import all the settings and programs from one system to another?

I think I'll just copy it onto the RAID 0 and try to get it to run.I mean, I still have a "backup" version an the old harddrive.

> I did have some issues with permissions after the transfer
What do I need to do to prevent this?

> 
You need to be able to handle symlinks and other special files intelligently.
What could happen with the "wrong" method?


> 
* Your /dev directory, while created dynamically, needs to have the 'null', 'console', and 'zero' devices at boot time or else you won't boot. Proper permissions are important as well. The other tmpfs mounts (/proc and /sys) you don't need to worry about aside from creating the mount point.
Could somebody please clarify this a bit? :oops:

---

### Post by falconindy on 2010-01-09
> **Zilioum said:**
> 
Honestly, this is one that I'm struggling with. 99% of it was covered using find piped to cpio, but then it went and kicked my cat and changed the ownership on my mpd config files. When I did this for my dad, I had the same issue with mpd as well as gdm (I don't use GDM). The only thing these two have in common is that they're both run by users of the same name (mpd and gdm, respectively).

[QUOTE=Zilioum;8637701]What could happen with the "wrong" method?
Worst case scenario, any path pointed to by a symlink is followed and the data is duplicated. You lose the symlink in the process and create a whole mess of data that you didn't want in the first place.

> **Zilioum said:**
> Could somebody please clarify this a bit? :oops:
Suppose I should do that, because I'm just going to take back what I said and suggest something else (simpler) instead. I ran into this issue because I did my backup not from a liveCD, but from the running system (and intentionally skipped /dev). Don't do this. Do the entire backup from a liveCD, where the system is stable and at its "rest state".

---

### Post by Zilioum on 2010-01-09
Thanks a lot, I think I got the main idea now. I'll just try it out within the next days and post back if I run into some trouble.

Cheers

---

