---
title: "Wubi install on XP"
date: 2010-12-18
forum: General Help
---

### Post by drcmcs on 2010-12-18
I installed via wubi on an XP system with two hard disks, the second disk for Ubuntu.  I put grub on both disks as it recommended.  Now I'm being pushed to "Grub rescue" with the message:  fd0 cannot get c/h/s values

I'm a newbie and I think it's looking for a floppy disk, but I do not have one on the system.  I've tried setting different options in the bios but cannot get past the error.

Any ideas?  (I'm not proficient with terminal commands, so please be explicit.)

Many thanks.

Don

---

### Post by Rubi1200 on 2010-12-19
Hi and welcome to the forums :)

It sounds as if you may have an unusual setup here.

To confirm what is going on and to make troubleshooting the problem easier, please boot the computer with a LiveCD, choosing to try NOT install Ubuntu.

At the live desktop, download and run the boot info script linked at the bottom of my post (instructions included).

Post the results back here to the forum and we will try and help you resolve this.

Thanks.

---

### Post by bcbc on 2010-12-19
> **drcmcs said:**
> I installed via wubi on an XP system with two hard disks, the second disk for Ubuntu.  I put grub on both disks as it recommended.  Now I'm being pushed to "Grub rescue" with the message:  fd0 cannot get c/h/s values

I'm a newbie and I think it's looking for a floppy disk, but I do not have one on the system.  I've tried setting different options in the bios but cannot get past the error.

Any ideas?  (I'm not proficient with terminal commands, so please be explicit.)

Many thanks.

Don
If you're referring to the grub screen you get when processing grub-pc updates (from Update Manager), then it is very misleading. If you installed grub to both drives then you have overwritten your windows bootloader and you need to replace them (actually just the one you boot from).

See Rubi1200's Wubi Megathread [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198) Problem #1, Solution #1 or #2. You just need to install the windows bootloader (fixmbr or bootrec.exe /fixmbr) - don't mess with the boot sectors or anything else)

---

### Post by drcmcs on 2010-12-19
> **Rubi1200 said:**
> Hi and welcome to the forums :)

It sounds as if you may have an unusual setup here.

To confirm what is going on and to make troubleshooting the problem easier, please boot the computer with a LiveCD, choosing to try NOT install Ubuntu.

At the live desktop, download and run the boot info script linked at the bottom of my post (instructions included).

Post the results back here to the forum and we will try and help you resolve this.

Thanks.
Thanks, Rubi1200.  I really feel stupid, but I'm using a Ubuntu USB and I cannot figure out the password for su.  Otherwise your directions are great!

---

### Post by drcmcs on 2010-12-19
> **bcbc said:**
> If you're referring to the grub screen you get when processing grub-pc updates (from Update Manager), then it is very misleading. If you installed grub to both drives then you have overwritten your windows bootloader and you need to replace them (actually just the one you boot from).

See Rubi1200's Wubi Megathread [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198) Problem #1, Solution #1 or #2. You just need to install the windows bootloader (fixmbr or bootrec.exe /fixmbr) - don't mess with the boot sectors or anything else)
I was not processing grub updates, in the Wubi install.  It asked which disk to put the boot on but said that if you were unsure to put it on both disks.  I selected both disks and continued the installation.  Then it booted into Grub rescue.

Many thanks.

---

### Post by bcbc on 2010-12-19
> **drcmcs said:**
> I was not processing grub updates, in the Wubi install.  It asked which disk to put the boot on but said that if you were unsure to put it on both disks.  I selected both disks and continued the installation.  Then it booted into Grub rescue.

Many thanks.

That screen only appears when you're updating grub packages - did you just run Update Manager beforehand? Because there have been updates to packages grub-pc and grub-common lately. You may not have noticed that you were updating these, but if it prompted you where to install grub that's the only way it could have happened, (unless you manually tried to reinstall grub which obviously you didn't).

That's the only way you'd ever be prompted on where to install grub on a wubi install. And the fix is as described. If you're not sure boot a live CD and run the bootinfoscript as described in the Wubi Megathread. You'll see something about Grub2 being the MBR pointing at partition #256.

---

### Post by drcmcs on 2010-12-19
I think you're exactly right.  I did run updates and then checked the two drives for the grub install.  I will try to follow your advice.  Many thanks.

---

