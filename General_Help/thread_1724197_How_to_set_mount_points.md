---
title: "How to set mount points?"
date: 2011-04-08
forum: General Help
---

### Post by Bluestars on 2011-04-08
I partitoned my driver 500 gbs windows, 1 gb swap, 30 gb ubuntu, 400 gb /home.   I need to set mount point for the 30 gb one as / and mount point for the other one as /home.  how would i do this?  

Also I plan to install Ubuntu 11.04 from usb, is this an ok method?

---

### Post by mikewhatever on 2011-04-08
When the partitioning stage appears during the installation, click the 'Something else' option, select each partition and assign a mount point.

---

### Post by Bluestars on 2011-04-08
Now when I boot it asks me if I want to boot Ubuntu or Windows 7.  Usually if I pick windows it will boot.  If I pick Ubuntu it takes me to a list of Ubuntus then loads.  Now if I pick Ubuntu it takes me to an error that says windows failed to start and i need to use windows disc to repair.  if i pick windows though, windows will boot fine.

---

### Post by seawolf167 on 2011-04-08
The options you are talking about are probably the GRUB2 menu options (Ubuntu, Recovery Mode, Memtest, Windows Loader).

If you select Ubuntu you may (though with a fresh install you shouldn't) have to select the kernel you want to boot.

What is the specific error that occurs when attempting to boot Ubuntu (I'm confused as to why it says Windows failed to boot if you select Ubuntu - perhaps the mount point for / wasn't set correctly during installation)?

---

### Post by Bluestars on 2011-04-08
> **seawolf167 said:**
> The options you are talking about are probably the GRUB2 menu options (Ubuntu, Recovery Mode, Memtest, Windows Loader).

If you select Ubuntu you may (though with a fresh install you shouldn't) have to select the kernel you want to boot.

What is the specific error that occurs when attempting to boot Ubuntu (I'm confused as to why it says Windows failed to boot if you select Ubuntu - perhaps the mount point for / wasn't set correctly during installation)?

Instead of taking me to a page to pick the Ubuntu kernel it goes to a black screen with white text.  It says windows has failed to start. this may be due to a recent software or hardware change.  insert your windows disc and run windows repair.

File: Ubuntu\winboot\wubildr.mbr

status: 0x0000225

Will not load due to the application being missing or corrupt.

---

