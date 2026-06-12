---
title: "Script to set default OS?"
date: 2009-07-18
forum: General Help
---

### Post by vergenzt on 2009-07-18
I have my family set up with a computer that dual-boots Windows Vista and Ubuntu 9.04.  My parents prefer Vista, whereas my brother and I prefer Linux.  By their authority, they demand that we make Windows the default OS.  They want it so that when the computer boots up, it boots into Vista without them having to press Enter or anything like that.

Our problem is that we're very distractible, so when we reboot the computer, we tend to forget to stay at the computer to tell it to boot Ubuntu (we have the GRUB menu stay up for 10 seconds), so it ends up booting into Vista.

An idea that I had to solve the problem would be to have a script that you could run that would modify menu.lst to set the default to what you want, and it would boot that OS.  I'd have no trouble doing that from Ubuntu, but the problems would arise in writing the scripts for Windows, as GRUB is on an ext3 partition.

In short, is there any way that a Windows batch script could access an ext3 partition?  All it will really need to do is rename a file.  Any help on this would be greatly appreciated.

---

### Post by ~sHyLoCk~ on 2009-07-18
Boot in Ubuntu. And follow this:~

[URL="http://ubuntuforums.org/showthread.php?t=1213618"]http://ubuntuforums.org/showthread.php?t=1213618
[/URL]

---

### Post by t4thfavor on 2009-07-18
They want to script the change so that they can perform it from within ubuntu, or windows to change the default OS. Unless your /boot is on a windows readable partition you will not be able to do it. I would suggest taking some classes in concentration, as 10 seconds is not all that long. I hope you don't drive :)

---

### Post by raymondh on 2009-07-18
If your problem is distraction, why not stop the countdown by hitting the spacebar as soon as you see GRUB.  I figure you can make that into a habit.  And when you're ready, highlight the appropriate OS entry and enter?

---

### Post by vergenzt on 2009-07-18
The problem is not in choosing once the menu is there, it is waiting the three minutes that it takes for Windows Vista to shut down, and the computer to boot back up.  We usually remember about the prompt just fine, but on the rare occasion that we do forget and miss the GRUB menu, it's really aggravating.  Because it takes so long, I'm trying to set it up so you can boot either OS without it requiring run-time interaction, so you don't have to sit at the computer while it restarts.

I was doing some research, and found that GRUB can run from a fat32 partition, which is a format that Windows can read.  I may just make a separate partition for /boot in fat32 format.

As for the scripts themselves, I think I'll just make a few separate copies of menu.lst with the different defaults, and have the scripts just rename files instead of trying to modify them, as it'd be much less conducive to screwing it up that way.

---

