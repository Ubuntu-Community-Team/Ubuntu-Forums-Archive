---
title: "Is a backup of the Windows bootloader created when Ubuntu is installed?"
date: 2011-01-21
forum: General Help
---

### Post by Capt. Hot Dog on 2011-01-21
I'm using Ubunu 10.10 64 bit.(You might see by my message "Ubuntu development release". That's because I haven't updated my profile yet. ) I installed it as a duel boot configuration with WIndows 7. Then shortly after my WIndows configuration went somewhat corrupt. (Not as a result of the duel boot, but for other reasons. ) I then needed to restore the Windows installation from factory defaults. That's OK, right? You might think I'm crazy for thinking that, but I didn't see any problem because I put the bootloader on a differerent hard drive, and that tiny 4 GB hard drive is being used for nothing but the bootloader. All operating systems reside on the 750 GB hard drive that my computer came with. 

I could boot both OSes that way, but when I needed to restore to factory defaults, I had to disconnect it so that the computer would default to the WIndows bootloader. For some reason, I had to do that in order to restore. 

I'm pretty sure that I only restored the C:\ partition, leaving all installations intact. In fact, I'm in my Linux installation right now, so I'm sure of that. I reconnected the 4 GB hard drive in order to access grub. 

Basically, the problem is that when I try to boot WIndows, it gives me an error "Boot manager not found" and gives me an option to restart. I did, and that changed nothing. It does let me boot LInux. 

I do not know where my WIndows repair disc is, so I'm basically wondering if there is any way to restore the original Windows bootloader. I'd like to keep the duel-boot if I can, but I absolutely need to be able to boot off of WIndows by Monday for school reasons. (Let's just say that it would not be good if I couldn't get my WIndows installation to boot by then) If there is a backup of WIndow's bootloader made when Ubuntu is installed, where is it stored? How can I restore it from Linux? 


Please help!

- a ridiculous username.

---

### Post by efflandt on 2011-01-21
Did you run **sudo update-grub** from Ubuntu after restoring Win7?  If there is more than one choice in the grub menu for Windows are you sure that you are booting the correct one?

When I temporarily put Ubuntu on a Dell laptop (with grub on sda4 instead of mbr) I did not pay attention to which partition was the Win7 boot partition.  So when I was going to remove Ubuntu to give the laptop to someone, I changed the boot partition from sda4 to the partition with Win7 on it.  But that did not work and I had to boot a Win7 system disk several times before Win7 would boot on its own.

I found out why when I bought a Dell desktop.  It had 3 partitions Dell Utilities (sda1), RECOVERY (sda2 marked as boot), and OS on sda3.  So it was originally actually booting from the RECOVERY partition and the Win7 partition did not have the necessary boot files.

Run the bootinfo script from [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) and if that does not enlighten you, post RESULTS.txt here and wrap it in code tags by highlighting it and clicking **#** at top of message window.

---

### Post by oldfred on 2011-01-21
Run the boot script so we can see your install.

But just like you have a liveCd to repair Ubuntu, you need  a windows repair CD.

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Repair Disc at the following links:
Windows Vista Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
Windows 7 Disc - for repairs only
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista/7 will not repair XP (they create the boot sectors differently) but can run chkdsk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

