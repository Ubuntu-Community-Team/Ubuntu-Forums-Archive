---
title: "[HELP] How can I repair GRUB on my eeePC ?"
date: 2009-11-24
forum: General Help
---

### Post by ViSK05 on 2009-11-24
Hi everyone!
I had some different OS on my eeePC 1000H: eeeBuntu, Crunchbang (debian) and the preinstalled Win XP. They were all working using Grub as bootloader

I deleted all the partions, keeping just the one with Win XP, and clearly grub got deleted or something.
Now when I start my eeePC it says 
"grub ... something ... error 22" 
and stops.

I would like to repair the boot loader to get WinXP going and then eventually try to install some other linux distros...
I have this other laptop with unetbootin, so could you advise me what should I download on my USB and what should I do to repair my boot loader to get WinXP going ?

Thank you :popcorn:

---

### Post by drs305 on 2009-11-24
ViSK05,

Welcome to Ubuntu and the Ubuntu forums.

If you have your Win CD this guide by talsemgeest should fix it right up:
[http://ubuntuforums.org/showthread.php?t=1014708]("http://ubuntuforums.org/showthread.php?t=1014708")

Since you are using Grub, the section on 9.04 will apply to you.

---

### Post by ViSK05 on 2009-11-24
> **drs305 said:**
> ViSK05,

Welcome to Ubuntu and the Ubuntu forums.

If you have your Win CD this guide by talsemgeest should fix it right up:
[http://ubuntuforums.org/showthread.php?t=1014708]("http://ubuntuforums.org/showthread.php?t=1014708")

Since you are using Grub, the section on 9.04 will apply to you.

ok, ty ;)
But at the moment I have just one partition with winXP on it, so am I supposed to install grub on that partition ? or should I make a new partition for linux to install grub on it? (and if yes, how?)
:-s

---

### Post by drs305 on 2009-11-25
> **ViSK05 said:**
> ok, ty ;)
But at the moment I have just one partition with winXP on it, so am I supposed to install grub on that partition ? or should I make a new partition for linux to install grub on it? (and if yes, how?)
:-s

What I meant was to follow the instructions under the 9.04 section since the grub you had installed was Grub legacy and not Grub 2. To restore Windows you wouldn't need to reinstall grub - just use the Windows CD to fix the Master Boot Record (MBR).

If you want to make a new partition to install Ubuntu on, I would recommend you get Windows working again first. Then make the Windows partition the size you want to free up some space for Ubuntu (or to make the Windows partition larger). Once you have Windows the desired size, you can use the Ubuntu LiveCD to install Ubuntu with either the "Install side by side with Windows" if Windows uses the entire disk, or "Use largest free space" option if you already have at least 8GB of unallocated/free space.

---

### Post by ViSK05 on 2009-11-25
> **drs305 said:**
> What I meant was to follow the instructions under the 9.04 section since the grub you had installed was Grub legacy and not Grub 2. To restore Windows you wouldn't need to reinstall grub - just use the Windows CD to fix the Master Boot Record (MBR).

If you want to make a new partition to install Ubuntu on, I would recommend you get Windows working again first. Then make the Windows partition the size you want to free up some space for Ubuntu (or to make the Windows partition larger). Once you have Windows the desired size, you can use the Ubuntu LiveCD to install Ubuntu with either the "Install side by side with Windows" if Windows uses the entire disk, or "Use largest free space" option if you already have at least 8GB of unallocated/free space.

"Use the Windows CD to fix" ? 
1) The eeePC dosn't have a cd drive
2) I don't have any "CD" of windows since it was pre-installed
So how can I fix windows (XP) in that case ?

( I have 80gb hdd, 40 are occupied by win partition, and 40 are unallocated ... )

---

### Post by drs305 on 2009-11-25
> **ViSK05 said:**
> "Use the Windows CD to fix" ? 
1) The eeePC dosn't have a cd drive
2) I don't have any "CD" of windows since it was pre-installed
So how can I fix windows (XP) in that case ?

( I have 80gb hdd, 40 are occupied by win partition, and 40 are unallocated ... )

There is a linux app called install-mbr that might do the work for you. Here is the link:
[http://ubuntuforums.org/archive/index.php/t-339433.html]("http://ubuntuforums.org/archive/index.php/t-339433.html")

Unfortunately, the help page referenced no longer exists. The entire command, including switches, is found in the link. 

I have not tried this command so I would do some more searching before running it. I have no doubt that it does what the link says, it's just that the thread doesn't specifically say that you will be able to boot Windows after performing it.

Let us know what you find.

---

### Post by ViSK05 on 2009-11-26
> **drs305 said:**
> There is a linux app called install-mbr that might do the work for you. Here is the link:
[http://ubuntuforums.org/archive/index.php/t-339433.html]("http://ubuntuforums.org/archive/index.php/t-339433.html")

Unfortunately, the help page referenced no longer exists. The entire command, including switches, is found in the link. 

I have not tried this command so I would do some more searching before running it. I have no doubt that it does what the link says, it's just that the thread doesn't specifically say that you will be able to boot Windows after performing it.

Let us know what you find.

I don't know how to do that ...:P
Is there anything you can put on a usb, that just installs the windows boot loader ?

---

