---
title: "Installing Ubuntu over XP/Will Programs &amp; Data be Intact?"
date: 2011-08-25
forum: General Help
---

### Post by monicakm on 2011-08-25
Ubuntu sucessfully allowed me to access and rescue data on my ailing XP hdd.  I'd like to install Ubuntu on this drive, over XP.  Can't get to any options that allow me to repair this drive with the XP CD or running chkdsk.  IF I can install Ubuntu over XP will my programs and data be useable?  IOW, if I can install Ubuntu over XP and the hdd errors are corrected would Photoshop Elements run and would data associated with that program open?
I couldn't access XP by using any of the safe mode options or "last good configuration option.  I've used a USB to SATA cable system and a dock to connect my hdd to a laptop.  Both options told me the drive needed formatted.  As I said earlier, Ubuntu allowed me to access data and save it but I'd like to install Ubuntu OVER the XP install if my programs and data would remain intact.
Thanks,
Monica

---

### Post by kensclark15 on 2011-08-25
You can install Ubuntu OVER Windows but it will delete everything. Or you can select the option "Run side-by-side with Windows" and every time you start your computer you can choose what operating system to use.

---

### Post by monicakm on 2011-08-25
Thanks so much for the quick reply!  And will this side by side install will allow Ubuntu to run my programs that are already installed (via XP) or will I need to install the programs under the Ubuntu banner?  I really do like this OS but right now I need to try access a couple of programs to run their specific backups.  When all this gets straightened out, I'll install a new hdd and use Ubuntu as my OS.  Really impressed by what I've seen of it so far :)
Monica

---

### Post by kensclark15 on 2011-08-25
You will have to install them again I think. And to run Windows programs you need a program for Ubuntu called "Wine".

---

### Post by monicakm on 2011-08-25
darn.  That's what I was afraid of but was hoping I could access those programs with Ubuntu.  
Monica

---

### Post by Duncan Williams on 2011-08-25
Ubuntu correctly installed as dual boot with a correctly installed (or recently re-installed) version of windows.

Will allow you to choose either windows or ubuntu at startup (grub)

All files and programs on your windows partition are available in ubuntu.
You cannot run windows programs from ubuntu (except some using wine)
so 
to run any windows programs at full speed etc.
You need to boot into windows.

Nearly all programs used in windows have an open-source alternative available in ubuntu as a linux program.

After a couple of months using dual-boot a lot of people will either return to windows or become more familiar with linux and choose it as their main o.s.

---

### Post by Mark Phelps on 2011-08-25
Wine allows you to run SOME MS Windows programs -- but you have to install them into Ubuntu using Wine; you can't run the existing programs on your MS Windows partition.

---

### Post by walt.smith1960 on 2011-08-25
As other have said, either dual boot or run Windows in a virtual machine.  Ubuntu can see files in Windows e.g. data files but it cannot run Windows programs.

---

### Post by 3rdalbum on 2011-08-25
Also note that WINE can only successfully run probably about 20% of Windows programs - the WINE developers have an incredibly difficult task. The best strategy is to use native Linux programs wherever absolutely possible.

The point of Linux is to be a free and open-source operating system of its own right. The point of WINE is to add some degree of Windows compatibility for times when it's absolutely needed. That's why WINE is not baked into Linux. Also, the operating system OS/2 had full Windows compatibility due to cooperation with Microsoft, but as a direct result of that nobody wrote native OS/2 programs and nobody bought OS/2!

---

