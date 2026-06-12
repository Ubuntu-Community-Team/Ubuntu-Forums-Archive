---
title: "Been thinking about duel booting Dapper with XP Profesional"
date: 2006-06-06
forum: General Help
---

### Post by justin2021 on 2006-06-06
Ok, as of right now, I have Dapper installed. I have been thinking hard about it and finally decided that I want to dual boot. The main reasons why is mainy because of games and a few other apps. Would dual booting effect how each OS would work? Such as, if I had Dapper and XP, because I have XP, would it mess up dapper? Also, would I need to delete dapper, install xp, then install dapper again? I have a 80 gig hard drive so would probablly want to give 40 to xp and 40 to ubuntu. And finally, are there any good instructions online for dual booting?

---

### Post by aysiu on 2006-06-06
Before you install anything, use a live CD for a week or two.

Then, read these two links:
[http://www.psychocats.net/ubuntu/partitioning.html](http://www.psychocats.net/ubuntu/partitioning.html)
[http://www.psychocats.net/ubuntu/windowstoubuntu.html](http://www.psychocats.net/ubuntu/windowstoubuntu.html)

---

### Post by elemental666 on 2006-06-06
Quick and dirty answers:

No having XP and Dapper installed will not effect either OS negatively (except for maybe some seek times and pagefile writes and stuff, but not really noticable to the avg joe.)

The easiest way to Dual Boot with XP and Ubuntu (this is how I do it on my machines).

*Back up anything you want to save off the existing installation
*Reboot with the XP cd, partition and format you windows partion only!  Leave the rest of the drive unpartitioned.
*Complete the Windows install
*Reboot with the Ubuntu cd, partion all your Linux partitions and finish the Ubuntu install.

notes: during the boot manager installation in Ubuntu, grub should get automatically configured to dual boot with windows (windows will overwrite the boot loader, this is why you do windows first).

There is a way to make linux and windows share the swap space.  Meaning Linux will use it as swap space and windows will use the same space for it virtual memory.  I"ve not done this though.

---

### Post by matrooswolf on 2006-06-06
If you already have Dapper installed, You could also try to install WindowsXp on a virtual machine, see this thread:

[http://www.ubuntuforums.org/showthread.php?t=183209](http://www.ubuntuforums.org/showthread.php?t=183209)

I have windows installed like this and use it for some small applications (bank, ...)

but I don't know how well it works for games ...

---

### Post by givré on 2006-06-06
[QUOTE=matrooswolf]If you already have Dapper installed, You could also try to install WindowsXp on a virtual machine, see this thread:

[http://www.ubuntuforums.org/showthread.php?t=183209](http://www.ubuntuforums.org/showthread.php?t=183209)

I have windows installed like this and use it for some small applications (bank, ...)

but I don't know how well it works for games ...[/QUOTE]
Will not work for games (the virtual graphic card does not provide 3D), but you could try wine for that [https://wiki.ubuntu.com/Wine](https://wiki.ubuntu.com/Wine) 
or cedega, if you could pay for it [http://www.transgaming.com/](http://www.transgaming.com/)

---

### Post by justin2021 on 2006-06-07
Aysiu:

   I downloaded the live version of Dapper, and for some reason it gives errors when loading and trying to mount the root file system:

hdc: ide_intr: huh? expected NULL
Buffer I/O error on device hdc

Any ideas on what this could mean?](*,)

---

### Post by aysiu on 2006-06-07
[QUOTE=justin2021]Aysiu:

   I downloaded the live version of Dapper, and for some reason it gives errors when loading and trying to mount the root file system:

hdc: ide_intr: huh? expected NULL
Buffer I/O error on device hdc

Any ideas on what this could mean?](*,)[/QUOTE] No idea. But I Googled the error, and [a bug report for it came up](http://72.14.209.104/search?q=cache:ietKRo3iQikJ:https://launchpad.net/bugs/36667+hdc:+ide_intr:+huh%3F+expected+NULL&hl=en&lr=lang_en&strip=1). Right now, Bugzilla appears to be down, but I just linked to the cached page.

---

### Post by justin2021 on 2006-06-07
Well, from reading it, I'm guessing that it is unfixable so far....

I didn't hear anything about Xubuntu in there... maybe that will work? Or perhaps another download of Ubuntu

---

