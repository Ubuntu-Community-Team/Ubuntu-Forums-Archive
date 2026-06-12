---
title: "reinstall Ubuntu"
date: 2009-08-09
forum: General Help
---

### Post by Piriloko on 2009-08-09
Hello everyone, I'm new here and I'm a newbie, I was reading some topics about reinstalling ubuntu, but I still have some doubts.

I follow the steps to boot the cd, chose install ubuntu and I dont know what to do to make it reinstall ubuntu. In the screen where it shows the partitions, it shows a little new partition of 2,5GB, when I click next it doesnt ask me if I want to reinstall, it prompts me with a message saying that the resizing process will take some time, so I hit back and try another way. I chose the manual resizing option, it shows the partitions from my HD, I chose to erase the ubuntu partition and hit next, but it prompts me saying that I didnot chose a root directory or something like that. So I would appreciate some help, please.

---

### Post by coldReactive on 2009-08-09
You need to choose / for the boot dropdown when manually specifying partitions.

Go back to where the partitions are and select hda or whatever and use entire disk. If you don't want to do that (IE: If you have windows dual booting) then you're going to have to google some tutorials about partitioning using the ubuntu installer.

---

### Post by Piriloko on 2009-08-09
I see, that is the problem, I have a partition with windowns, I just want to uinstall ubuntu.

If I format the ubuntu partition through windows, there is any chance of having problems when booting system? Like grub...

---

### Post by Barafu Albino Cheetah on 2009-08-09
Let me explain a bit. When you start PC, first the BIOS program starts. It is kept on special chip on the mainboard. Then it looks for MBR, which is kept at the very beginning of the drive, out of any partitions. MBR may be empty or contain a reference to the bootloader. 
If MBR is empty, BIOS looks for reference on the partition you've marked as a boot partition. 
If BIOS finds bootloader, it runs bootloader. Bootloader is a file kept on the filesystem. 
Bootloader looks for it's config and finds kernel and starts it. 

So, if you delete a partition with GRUB or reference to it - you will not be able to boot. 
try first marking you windows partition as bootable one, restart the PC and see - if Windows starts pretending it is a single OS on the system, you may safely delete another partitions. Otherwise, you should better not delete your linux partition, where /boot folder stays.

---

### Post by -kg- on 2009-08-09
OK, you're looking to do a fresh (re-)install.  You did right in choosing the Manual Installation method, you just unknowingly forgot a couple of steps in the process.

You chose to delete the original Ubuntu partition which would be correct.  After this, you need to recreate another Ubuntu partition to replace the one you just deleted.  When you're in manual partitioning mode, you must complete all steps manually; there is no automation to any of it.

The other step you need to take to to mark the new partition as "/" (that would be as a root partition).  That is the error message you got, because not only did you not re-create a new partition to replace the old (which the installer doesn't really care about), but you didn't mark a compatible partition as root (which the installer most definitely *does* care about!).

I'm assuming that you already have a swap partition.  If you're installing Jaunty 9.04, you will need do nothing else after you complete the above steps.  If you're installing an earlier version, I'm not sure, but you might need to mark the swap partition as "swap" as well.  It's been a while back since I dealt with Hardy, but I'm thinking I remember that I had to physically mark the swap partition as well as root (and /home, since I created one of those as well).  The installer will tell you if you miss something critical.

This information should get you on your way to your re-installation.  If you were intending on a re-installation without completely destroying your installation, you would go through the above process, but instead of deleting your old partition, you would just mark it as "/" (root) in manual partitioning without deleting it.  Ubuntu would re-install over the top of the old installation and preserve any software/settings that weren't in the default installation.

Good luck! :)

---

### Post by Piriloko on 2009-08-09
I will try to do this right know. I dont want to reinstall keeping my data, I've messed up things, this is why I want to reinstall it ;)

---edit

thank you very much -kg-!!!! It worked!!

---

### Post by scouser73 on 2009-08-09
If you reinstall Ubuntu every so often then I'd suggest that you back up your home folder saving you the headache of having to ajust everything to your liking, themes, settings and so on. Pybackpack is a program I use for this - [[COLOR="Red"]**Pybackpack**[/COLOR]]("http://www.ubuntugeek.com/pybackpack-a-user-friendly-file-backup-tool-for-ubuntu-linux-desktop.html").

---

